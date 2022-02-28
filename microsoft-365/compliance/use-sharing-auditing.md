---
title: Korzystanie z inspekcji udostępniania w dzienniku inspekcji
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- MOE150
- BCS160
- MET150
ms.collection:
- M365-security-compliance
- SPO_Content
ms.assetid: 50bbf89f-7870-4c2a-ae14-42635e0cfc01
description: Administrator może dowiedzieć się, jak za pomocą inspekcji udostępniania Microsoft 365 dziennika inspekcji w celu identyfikowania zasobów udostępnionych użytkownikom spoza organizacji.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ff05b655617608332b4b838e07a6af55e8b4d010
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987270"
---
# <a name="use-sharing-auditing-in-the-audit-log"></a>Korzystanie z inspekcji udostępniania w dzienniku inspekcji

Udostępnianie to kluczowa aktywność w usługach online SharePoint i OneDrive dla Firm, która jest powszechnie stosowana w organizacjach. Administratorzy mogą za pomocą inspekcji udostępniania w dzienniku inspekcji określać sposób używania udostępniania w organizacji. 
  
## <a name="the-sharepoint-sharing-schema"></a>Schemat SharePoint udostępniania

Zdarzenia udostępniania (nie dotyczy to zdarzeń związanych z zasadami udostępniania i linkami udostępniania) różnią się od zdarzeń związanych z plikami i folderami w jeden sposób podstawowy: jeden użytkownik wykonuje akcję, która ma wpływ na innego użytkownika. Na przykład gdy zasób Użytkownik A zapewnia użytkownikowi B dostęp do pliku. W tym przykładzie użytkownik A jest użytkownikiem  *pełniącym funkcję użytkownika*  , a użytkownik B jest  *użytkownikiem docelowym*. W SharePoint pliku działanie użytkownika ma wpływ tylko na sam plik. Gdy użytkownik A otwiera plik, jedyne informacje potrzebne w zdarzeniu **FileAccessed** to użytkownik działający. Aby odróżnić tę różnicę, istnieje osobny schemat, nazywany schematem udostępniania *SharePoint, który* zawiera więcej informacji na temat zdarzeń udostępniania. Dzięki temu administratorzy mają wgląd w współużytkowanie zasobu i użytkownika, dla których został udostępniony. 
  
Schemat udostępniania udostępnia dwa dodatkowe pola w rekordzie inspekcji dotyczące zdarzeń udostępniania: 
  
- **TargetUserOrGroupType:** Określa, czy użytkownik lub grupa docelowa jest członkiem, gościem, grupą programu SharePoint, grupą zabezpieczeń lub partnerem.

- **TargetUserOrGroupName:** Przechowuje nazwę UPN lub nazwę użytkownika docelowego albo grupy, dla których udostępniono zasób (w poprzednim przykładzie jest to użytkownik B). 

Te dwa pola, oprócz innych właściwości ze schematu dziennika inspekcji, takich jak Użytkownik, Operacja i Data, mogą opowiedzieć całą historię tego, który  użytkownik udostępnił,  komu i *kiedy.* 
  
Istnieje kolejna właściwość schematu, która jest ważna dla historii udostępniania. Podczas eksportowania wyników przeszukiwania dziennika inspekcji w kolumnie **Dane** inspekcji w wyeksportowanych plikach CSV są przechowywane informacje o zdarzeniach udostępniania. Na przykład w przypadku, gdy użytkownik udostępnia witrynę inowi użytkownikowi, jest to możliwe dzięki dodaniu użytkownika docelowego do SharePoint grupy. Kolumna **Dane inspekcji** zawiera te informacje, aby zapewnić kontekst dla administratorów. Zobacz [Krok 2](#step-2-use-the-powerquery-editor-to-format-the-exported-audit-log) , aby uzyskać instrukcje dotyczące analizowania informacji w kolumnie **Dane** inspekcji.

## <a name="sharepoint-sharing-events"></a>SharePoint zdarzeń udostępniania

Udostępnianie jest określane przez to, kiedy użytkownik (pełniący funkcję użytkownika) chce udostępnić zasób inowi użytkownikowi (*użytkownikowi* doceloweowi). Rekordy inspekcji związane z udostępnianiem zasobu użytkownikowi zewnętrzneowi (użytkownikowi spoza organizacji, który nie ma konta gościa w programie Azure Active Directory organizacji) są identyfikowane przez następujące zdarzenia rejestrowane w dzienniku inspekcji:

- **SharingInvitationCreated:** Użytkownik w Twojej organizacji próbował udostępnić zasób (prawdopodobnie witrynę) użytkownikowi zewnętrzneowi. W wyniku tego zaproszenie do udostępniania zewnętrznego zostanie wysłane do użytkownika docelowego. W tym momencie nie zostanie przyznany dostęp do zasobu.

- **SharingInvitationAccepted:** Użytkownik zewnętrzny zaakceptował zaproszenie do udostępniania wysłane przez jego działanie i ma teraz dostęp do zasobu.

- **AnonymousLinkCreated:** Dla zasobu jest tworzony link anonimowy (nazywany również linkiem "Każdy"). Ponieważ link anonimowy można utworzyć, a następnie skopiować, można przyjąć, że każdy dokument, który ma link anonimowy, został udostępniony użytkownikowi doceloweowi.

- **AnonymousLinkUsed:** Jak wskazuje nazwa, to zdarzenie jest rejestrowane, gdy dostęp do zasobu jest używany link anonimowy. 

- **SecureLinkCreated:** Użytkownik utworzył "link do konkretnych osób", aby udostępnić zasób konkretnej osobie. Ten użytkownik docelowy może być osobą  zewnętrznej organizacji. Osoba, której udostępniono zasób, jest identyfikowana w rekordzie inspekcji dla zdarzenia **AddedToSecureLink** . Sygnatury czasowe tych dwóch zdarzeń są niemal identyczne.

- **AddedToSecureLink:** Dodano użytkownika do linku do konkretnych osób. Użyj pola **TargetUserOrGroupName** w tym zdarzeniu, aby zidentyfikować użytkownika dodanego do odpowiedniego linku do określonych osób. Ten użytkownik docelowy może być osobą  zewnętrznej organizacji.

## <a name="sharing-auditing-work-flow"></a>Udostępnianie przepływu pracy inspekcji
  
Gdy użytkownik (użytkownik pełniący funkcję użytkownika) chce udostępnić zasób inowi użytkownikowi (użytkownikowi doceloweowi), program SharePoint (lub OneDrive dla Firm) najpierw sprawdza, czy adres e-mail użytkownika docelowego jest już skojarzony z kontem użytkownika w katalogu organizacji. Jeśli użytkownik docelowy znajduje się w katalogu (i ma odpowiednie konto użytkownika gościa), SharePoint następujące czynności:
  
-  Natychmiast przypisuje użytkownikowi docelowego uprawnienia dostępu do zasobu, dodając użytkownika docelowego do odpowiedniej grupy SharePoint i loguje **zdarzenie AddedToGroup**. 
    
- Wysyła powiadomienie o udostępnieniu na adres e-mail użytkownika docelowego.
    
- Zapisuje zdarzenie **SharingSet** . To zdarzenie ma przyjazną nazwę "Udostępniony plik, folder lub witryna" w obszarze  Działania udostępniania i żądania dostępu w s wyboru działań narzędzia do przeszukiwania dziennika inspekcji. Zobacz zrzut ekranu w [kroku 1](#step-1-search-for-sharing-events-and-export-the-results-to-a-csv-file). 
    
Jeśli konto użytkownika docelowego nie znajduje się w katalogu, SharePoint następujące czynności: 
    
   - Dzienniki jednego z następujących zdarzeń, zależnie od sposobu współużytknia zasobu:
   
      - **AnonymousLinkCreated**
   
      - **SecureLinkCreated**
   
      - **AddedToSecureLink** 

      - **SharingInvitationCreated** (to zdarzenie jest rejestrowane tylko wtedy, gdy zasób udostępniony jest witryną)
    
   - Gdy użytkownik docelowy zaakceptuje zaproszenie do udostępniania, które zostało do niego wysłane (klikając link w zaproszeniu), program SharePoint rejestruje zdarzenie **SharingInvitationAccepted** i przypisuje użytkownikowi doceloweowi uprawnienia dostępu do zasobu. Jeśli użytkownik docelowy zostanie wysłany link anonimowy, zdarzenie **AnonymousLinkUsed** zostanie zarejestrowane, gdy użytkownik docelowy użyje tego linku w celu uzyskania dostępu do zasobu. W przypadku bezpiecznych linków zdarzenie **FileAccessed** jest rejestrowane, gdy użytkownik zewnętrzny używa linku w celu uzyskania dostępu do zasobu.

Rejestrowane są również dodatkowe informacje o użytkowniku docelowym, takie jak tożsamość użytkownika, do którego jest wysłane zaproszenie, i użytkownika, który zaakceptował zaproszenie. W niektórych przypadkach ci użytkownicy (lub adresy e-mail) mogą się różnić. 

## <a name="how-to-identify-resources-shared-with-external-users"></a>Jak zidentyfikować zasoby udostępnione użytkownikom zewnętrznym

Często wymagane jest, aby administratorzy tworzyli listę wszystkich zasobów udostępnionych użytkownikom spoza organizacji. Korzystając z inspekcji udostępniania w programie Office 365, administratorzy mogą generować tę listę. W tym artykule wyjaśniono, jak to zrobić.
  
### <a name="step-1-search-for-sharing-events-and-export-the-results-to-a-csv-file"></a>Krok 1. Wyszukiwanie zdarzeń udostępniania i eksportowanie wyników do pliku CSV

Pierwszym krokiem jest przeszukanie dziennika inspekcji pod celu wyszukania zdarzeń udostępniania. Aby uzyskać więcej informacji (w tym wymaganych uprawnień) na temat przeszukiwania dziennika inspekcji, zobacz [Przeszukiwanie dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md).
  
1. Przejdź do <https://compliance.microsoft.com>.

2. Zaloguj się przy użyciu konta służbowego.

3. W lewym okienku okna Centrum zgodności platformy Microsoft 365 pozycję **Inspekcja**.

    Zostanie **wyświetlona** strona Inspekcja.

4. W **obszarze Działania** kliknij **pozycję Działania udostępniania i żądania dostępu,** aby wyszukać zdarzenia związane z udostępnianiem. 

    ![W obszarze Działania wybierz pozycję Działania udostępniania i żądania dostępu.](../media/46bb25b7-1eb2-4adf-903a-cc9ab58639f9.png)
  
5. Wybierz zakres dat i godzin, aby znaleźć zdarzenia udostępniania, które wystąpiły w tym okresie. 

6. Kliknij **pozycję** Wyszukaj, aby uruchomić wyszukiwanie. 

7. Po zakończeniu wyszukiwania i wyświetlaniu wyników kliknij pozycję Eksportuj **wyniki Pobierz** \> **wszystkie wyniki**.

    Po wybraniu opcji eksportu w dolnej części okna zostanie wyświetlony monit o otwarcie lub zapisanie pliku CSV.

8. Kliknij **pozycję** \> **Zapisz zapisz jako** i zapisz plik CSV w folderze na komputerze lokalnym. 

### <a name="step-2-use-the-powerquery-editor-to-format-the-exported-audit-log"></a>Krok 2. Formatowanie wyeksportowanego dziennika inspekcji za pomocą edytora PowerQuery

Następnym krokiem jest podzielenie każdej właściwości w kolumnie **Dane** inspekcji (która składa się z wielowłaściowego obiektu JSON) w Edytorze dodatku Power Query w programie Excel na własną kolumnę przy użyciu funkcji przekształcania JSON. Umożliwia to filtrowanie kolumn w celu wyświetlenia rekordów związanych z udostępnianiem.

Aby uzyskać instrukcje krok po kroku, zobacz "Krok 2. Formatowanie wyeksportowanego dziennika inspekcji przy użyciu Edytora dodatku Power Query" w temacie Eksportowanie, konfigurowanie i [wyświetlanie rekordów dziennika inspekcji](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor).

### <a name="step-3-filter-the-csv-file-for-resources-shared-with-external-users"></a>Krok 3. Filtrowanie pliku CSV pod celu filtrowania zasobów udostępnionych użytkownikom zewnętrznym

Następnym krokiem jest przefiltrenie pliku CSV pod celu filtrowania poszczególnych zdarzeń związanych z udostępnianiem, które opisano SharePoint [udostępniania](#sharepoint-sharing-events). Kolumnę **TargetUserOrGroupType** można również filtrować, aby wyświetlić wszystkie rekordy, w których wartość tej właściwości to **Gość**. 

Po zastosowaniu się do instrukcji z poprzedniego kroku w celu przygotowania pliku CSV przy użyciu edytora PowerQuery wykonaj następujące czynności:
    
1. Otwórz Excel utworzony w kroku 2. 

2. Na karcie **Narzędzia** główne kliknij pozycję **Sortuj & filtru**, a następnie kliknij pozycję **Filtruj**.
    
3. Na **liście rozwijanej Sortowanie &** w kolumnie Operacje wyczyść wszystkie zaznaczenia,  zaznacz co najmniej jedno z następujących zdarzeń związanych z udostępnianiem, a następnie kliknij przycisk **OK**.
 
   - **SharingInvitationCreated**
   
   - **AnonymousLinkCreated**
   
   - **SecureLinkCreated**
   
   - **AddedToSecureLink** 
    
    Excel wierszy wybranych zdarzeń.
    
4. Przejdź do kolumny o nazwie **TargetUserOrGroupType** i zaznacz ją. 
    
5. Na liście **rozwijanej Sortowanie &** wyczyść wszystkie zaznaczenia, wybierz pozycję **TargetUserOrGroupType:Guest** i kliknij przycisk **OK**.
    
    Teraz Excel wyświetlane są wiersze zdarzeń udostępniania ORAZ miejsce, w którym użytkownik docelowy znajduje się poza organizacją, ponieważ użytkownicy zewnętrzni są identyfikowani za pomocą wartości **TargetUserOrGroupType:Guest**. 
  
> [!TIP]
> W przypadku wyświetlanych rekordów inspekcji kolumna **ObjectId** określa zasób udostępniony użytkownikowi doceloweowi. na przykład  `ObjectId:https:\/\/contoso-my.sharepoint.com\/personal\/sarad_contoso_com\/Documents\/Southwater Proposal.docx`.
