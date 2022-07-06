---
title: Używaj inspekcji udostępniania w dzienniku inspekcji
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Administracja mogą dowiedzieć się, jak używać inspekcji udostępniania w dzienniku inspekcji platformy Microsoft 365 do identyfikowania zasobów udostępnionych użytkownikom spoza organizacji.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1eb780f79d0dc5beaab3afcc52261bf9a4ccc25b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625968"
---
# <a name="use-sharing-auditing-in-the-audit-log"></a>Używaj inspekcji udostępniania w dzienniku inspekcji

Udostępnianie jest kluczowym działaniem w usłudze SharePoint Online i OneDrive dla Firm i jest szeroko stosowane w organizacjach. Administratorzy mogą używać inspekcji udostępniania w dzienniku inspekcji, aby określić sposób używania udostępniania w organizacji. 
  
## <a name="the-sharepoint-sharing-schema"></a>Schemat udostępniania programu SharePoint

Udostępnianie zdarzeń (bez zdarzeń związanych z zasadami udostępniania i udostępnianiem linków) różni się od zdarzeń związanych z plikami i folderami w jeden podstawowy sposób: jeden użytkownik wykonuje akcję, która ma wpływ na innego użytkownika. Na przykład gdy zasób Użytkownik A daje użytkownikowi B dostęp do pliku. W tym przykładzie użytkownik A jest  *działającym użytkownikiem*  , a użytkownik B jest  *użytkownikiem docelowym*. W schemacie plików programu SharePoint akcja działającego użytkownika ma wpływ tylko na sam plik. Gdy użytkownik A otworzy plik, jedynymi informacjami potrzebnymi w zdarzeniu **FileAccessed** jest działający użytkownik. Aby rozwiązać tę różnicę, istnieje oddzielny schemat nazywany  *schematem udostępniania programu SharePoint*, który przechwytuje więcej informacji na temat udostępniania zdarzeń. Dzięki temu administratorzy mają wgląd w to, kto udostępnił zasób i użytkownikowi, któremu został udostępniony zasób. 
  
Schemat udostępniania zawiera dwa dodatkowe pola w rekordzie inspekcji związane ze zdarzeniami udostępniania: 
  
- **TargetUserOrGroupType:** Określa, czy docelowy użytkownik lub grupa jest członkiem, gościem, programem SharePointGroup, grupą zabezpieczeń lub partnerem.

- **TargetUserOrGroupName:** Przechowuje nazwę UPN lub nazwę użytkownika lub grupy docelowej, którym został udostępniony zasób (użytkownik B w poprzednim przykładzie). 

Te dwa pola oprócz innych właściwości ze schematu dziennika inspekcji, takich jak Użytkownik, Operacja i Data, mogą zawierać pełną historię o tym,  *który*  *użytkownik udostępnił jaki*  zasób  *komu*  i  *kiedy*. 
  
Istnieje inna właściwość schematu, która jest ważna dla scenariusza udostępniania. Podczas eksportowania wyników wyszukiwania dziennika inspekcji **kolumna AuditData** w wyeksportowanym pliku CSV przechowuje informacje o zdarzeniach udostępniania. Na przykład gdy użytkownik udostępnia witrynę innemu użytkownikowi, jest to realizowane przez dodanie użytkownika docelowego do grupy programu SharePoint. **Kolumna AuditData** przechwytuje te informacje, aby zapewnić kontekst dla administratorów. Zobacz [Krok 2](#step-2-use-the-powerquery-editor-to-format-the-exported-audit-log) , aby uzyskać instrukcje dotyczące analizowania informacji w kolumnie **AuditData** .

## <a name="sharepoint-sharing-events"></a>Zdarzenia udostępniania programu SharePoint

Udostępnianie jest definiowane przez to, kiedy użytkownik ( *działający* użytkownik) chce udostępnić zasób innemu użytkownikowi (użytkownikowi *docelowemu* ). Rekordy inspekcji związane z udostępnianiem zasobu użytkownikowi zewnętrznemu (użytkownikowi spoza organizacji, który nie ma konta gościa w usłudze Azure Active Directory w organizacji) są identyfikowane przez następujące zdarzenia, które są rejestrowane w dzienniku inspekcji:

- **SharingInvitationCreated:** Użytkownik w organizacji próbował udostępnić zasób (prawdopodobnie lokację) użytkownikowi zewnętrznemu. Spowoduje to wysłanie zaproszenia do udostępniania zewnętrznego do użytkownika docelowego. W tym momencie nie udzielono dostępu do zasobu.

- **SharingInvitationAccepted:** Użytkownik zewnętrzny zaakceptował zaproszenie do udostępniania wysłane przez działającego użytkownika i ma teraz dostęp do zasobu.

- **AnonymousLinkCreated:** Dla zasobu jest tworzone łącze anonimowe (nazywane również łączem "Każdy"). Ponieważ można utworzyć, a następnie skopiować link anonimowy, uzasadnione jest założenie, że każdy dokument z linkiem anonimowym został udostępniony użytkownikowi docelowemu.

- **AnonymousLinkUsed:** Jak sama nazwa wskazuje, to zdarzenie jest rejestrowane, gdy link anonimowy jest używany do uzyskiwania dostępu do zasobu. 

- **SecureLinkCreated:** Użytkownik utworzył "link konkretnych osób", aby udostępnić zasób określonej osobie. Ten użytkownik docelowy może być osobą zewnętrzną w twojej organizacji. Osoba, której zasób jest współużytkowany, jest identyfikowana w rekordzie inspekcji zdarzenia **AddedToSecureLink** . Sygnatury czasowe dla tych dwóch zdarzeń są niemal identyczne.

- **DodanoToSecureLink:** Użytkownik został dodany do określonego linku osób. Użyj pola **TargetUserOrGroupName** w tym zdarzeniu, aby zidentyfikować użytkownika dodane do odpowiedniego linku określonych osób. Ten użytkownik docelowy może być osobą zewnętrzną w twojej organizacji.

## <a name="sharing-auditing-work-flow"></a>Udostępnianie przepływu pracy inspekcji
  
Gdy użytkownik (działający użytkownik) chce udostępnić zasób innemu użytkownikowi (użytkownikowi docelowemu), program SharePoint (lub OneDrive dla Firm) najpierw sprawdza, czy adres e-mail użytkownika docelowego jest już skojarzony z kontem użytkownika w katalogu organizacji. Jeśli użytkownik docelowy znajduje się w katalogu (i ma odpowiednie konto użytkownika-gościa), program SharePoint wykonuje następujące czynności:
  
-  Natychmiast przypisuje użytkownikowi docelowemu uprawnienia dostępu do zasobu, dodając użytkownika docelowego do odpowiedniej grupy programu SharePoint i rejestruje zdarzenie **AddedToGroup** . 
    
- Wysyła powiadomienie o udostępnianiu na adres e-mail użytkownika docelowego.
    
- Rejestruje zdarzenie **SharingSet** . To zdarzenie ma przyjazną nazwę "Udostępniony plik, folder lub witryna" w obszarze **Udostępnianie i uzyskiwanie dostępu do działań żądania** w selektorze działań narzędzia wyszukiwania dzienników inspekcji. Zobacz zrzut ekranu w [kroku 1](#step-1-search-for-sharing-events-and-export-the-results-to-a-csv-file). 
    
Jeśli konto użytkownika docelowego nie znajduje się w katalogu, program SharePoint wykonuje następujące czynności: 
    
   - Rejestruje jedno z następujących zdarzeń w oparciu o sposób udostępniania zasobu:
   
      - **AnonymousLinkCreated**
   
      - **SecureLinkCreated**
   
      - **DodanoToSecureLink** 

      - **SharingInvitationCreated** (to zdarzenie jest rejestrowane tylko wtedy, gdy udostępniony zasób jest witryną)
    
   - Gdy użytkownik docelowy zaakceptuje wysłane do niego zaproszenie do udostępniania (klikając link w zaproszeniu), program SharePoint rejestruje zdarzenie **SharingInvitationAccepted** i przypisuje użytkownikowi docelowemu uprawnienia dostępu do zasobu. Jeśli użytkownik docelowy otrzymuje link anonimowy, zdarzenie **AnonymousLinkUsed** jest rejestrowane po tym, jak użytkownik docelowy użyje linku w celu uzyskania dostępu do zasobu. W przypadku bezpiecznych łączy zdarzenie **FileAccessed** jest rejestrowane, gdy użytkownik zewnętrzny używa linku w celu uzyskania dostępu do zasobu.

Rejestrowane są również dodatkowe informacje o użytkowniku docelowym, takie jak tożsamość użytkownika, do któremu jest zaproszenie, i użytkownik, który akceptuje zaproszenie. W pewnym przypadku ci użytkownicy (lub adresy e-mail) mogą się różnić. 

## <a name="how-to-identify-resources-shared-with-external-users"></a>Jak identyfikować zasoby udostępnione użytkownikom zewnętrznym

Typowym wymaganiem dla administratorów jest utworzenie listy wszystkich zasobów, które zostały udostępnione użytkownikom spoza organizacji. Korzystając z inspekcji udostępniania w Office 365, administratorzy mogą wygenerować tę listę. W tym artykule wyjaśniono, jak to zrobić.
  
### <a name="step-1-search-for-sharing-events-and-export-the-results-to-a-csv-file"></a>Krok 1. Wyszukiwanie zdarzeń udostępniania i eksportowanie wyników do pliku CSV

Pierwszym krokiem jest przeszukanie dziennika inspekcji pod kątem udostępniania zdarzeń. Aby uzyskać więcej informacji (w tym wymagane uprawnienia) na temat przeszukiwania dziennika inspekcji, zobacz [Przeszukiwanie dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md).
  
1. Przejdź do <https://compliance.microsoft.com>.

2. Zaloguj się przy użyciu konta służbowego.

3. W okienku po lewej stronie portal zgodności Microsoft Purview kliknij pozycję **Inspekcja**.

    Zostanie wyświetlona strona **Inspekcja** .

4. W obszarze **Działania** kliknij pozycję **Udostępnianie i dostęp do działań żądań** , aby wyszukać zdarzenia związane z udostępnianiem. 

    ![W obszarze Działania wybierz pozycję Udostępnianie i dostęp do działań żądań.](../media/46bb25b7-1eb2-4adf-903a-cc9ab58639f9.png)
  
5. Wybierz zakres dat i godzin, aby znaleźć zdarzenia udostępniania, które wystąpiły w tym okresie. 

6. Kliknij pozycję **Wyszukaj** , aby uruchomić wyszukiwanie. 

7. Po zakończeniu wyszukiwania i wyświetleniu wyników kliknij pozycję **Eksportuj wyniki** \> **Pobierz wszystkie wyniki**.

    Po wybraniu opcji eksportu w dolnej części okna zostanie wyświetlony komunikat z monitem o otwarcie lub zapisanie pliku CSV.

8. Kliknij **pozycję Zapisz** \> **jako** i zapisz plik CSV w folderze na komputerze lokalnym. 

### <a name="step-2-use-the-powerquery-editor-to-format-the-exported-audit-log"></a>Krok 2. Formatowanie wyeksportowanego dziennika inspekcji za pomocą Edytora PowerQuery

Następnym krokiem jest użycie funkcji przekształcania JSON w Edytor Power Query w programie Excel, aby podzielić każdą właściwość w kolumnie **AuditData** (składającej się z wielowładnego obiektu JSON) na własną kolumnę. Umożliwia to filtrowanie kolumn w celu wyświetlenia rekordów związanych z udostępnianiem

Aby uzyskać instrukcje krok po kroku, zobacz "Krok 2: Formatowanie wyeksportowanego dziennika inspekcji przy użyciu Edytor Power Query" w temacie [Eksportowanie, konfigurowanie i wyświetlanie rekordów dziennika inspekcji](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor).

### <a name="step-3-filter-the-csv-file-for-resources-shared-with-external-users"></a>Krok 3. Filtrowanie pliku CSV pod kątem zasobów udostępnionych użytkownikom zewnętrznym

Następnym krokiem jest odfiltrowanie pliku CSV pod kątem różnych zdarzeń związanych z udostępnianiem, które zostały wcześniej opisane w sekcji [Udostępnianie zdarzeń programu SharePoint](#sharepoint-sharing-events) . Alternatywnie można filtrować kolumnę **TargetUserOrGroupType** , aby wyświetlić wszystkie rekordy, w których wartość tej właściwości to **Gość**. 

Po wykonaniu instrukcji w poprzednim kroku, aby przygotować plik CSV przy użyciu edytora PowerQuery, wykonaj następujące czynności:
    
1. Otwórz plik programu Excel utworzony w kroku 2. 

2. Na karcie **Narzędzia** główne kliknij pozycję **Sortuj & Filtr**, a następnie kliknij pozycję **Filtruj**.
    
3. Na liście rozwijanej **Sortuj & Filtr** w kolumnie **Operacje** wyczyść wszystkie zaznaczenia, a następnie wybierz co najmniej jedno z następujących zdarzeń związanych z udostępnianiem, a następnie kliknij przycisk **OK**.
 
   - **SharingInvitationCreated**
   
   - **AnonymousLinkCreated**
   
   - **SecureLinkCreated**
   
   - **DodanoToSecureLink** 
    
    Program Excel wyświetla wiersze wybranych zdarzeń.
    
4. Przejdź do kolumny o nazwie **TargetUserOrGroupType** i wybierz ją. 
    
5. Na liście rozwijanej **Sortuj & Filtr wyczyść** wszystkie zaznaczenia, a następnie wybierz pozycję **TargetUserOrGroupType:Guest** i kliknij przycisk **OK**.
    
    Teraz program Excel wyświetla wiersze do udostępniania zdarzeń i miejsca, w których użytkownik docelowy znajduje się poza organizacją, ponieważ użytkownicy zewnętrzni są identyfikowane przez wartość **TargetUserOrGroupType:Guest**. 
  
> [!TIP]
> W przypadku wyświetlanych rekordów inspekcji kolumna **ObjectId** identyfikuje zasób, który został udostępniony użytkownikowi docelowemu; na przykład  `ObjectId:https:\/\/contoso-my.sharepoint.com\/personal\/sarad_contoso_com\/Documents\/Southwater Proposal.docx`.
