---
title: Ręczne przesyłanie danych między dwoma kontami
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
ms.assetid: 7dc5d983-84b2-4802-bef0-602ae1780a42
description: Dowiedz się, jak ręcznie przenieść dane między dwoma Microsoft 365 kontami użytkowników w przypadku zmiany planu lub nazwy firmy albo połączonej wielu subskrypcji w jedną.
ms.openlocfilehash: 7d6cb9e055fd27e8f9b0a26e7ff4bfffa97421ae
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316719"
---
# <a name="transfer-data-manually-between-two-accounts"></a>Ręczne przesyłanie danych między dwoma kontami

Przygotuj się do zakasania zakasań i zasłaniania nieco czasu: przeniesienie danych między dwoma kontami Microsoft 365 jest ręcznym, skomplikowanym i czasochłonnym procesem. Nie jest to zautomatyzowany ani obsługiwany proces. Na początek.
  
> [!CAUTION]
> Może minął czas, w którym poczta e-mail, Skype dla firm i publiczna witryna internetowa hostowana Microsoft 365 nie będzie działać. Użytkownicy otrzymają nowe nazwy użytkowników i hasła, a także będą musieli zresetować ustawienia Outlook.

**Dane należy przesyłać ręcznie, korzystając z instrukcji podanych w tym temacie, jeśli ma zastosowanie jedna z następujących sytuacji:**
  
- Musisz zmienić plan na plan w innej rodzinie usług.

- Zmieniono nazwę firmy i zdecydowano się utworzyć nową subskrypcję i przeprowadzić migrację danych, ponieważ chcesz używać innych początkowych nazw domen.

- Musisz połączyć wiele subskrypcji w jedną nową.

> [!IMPORTANT]
> Jeśli musisz zmienić plan [](../../commerce/subscriptions/switch-to-a-different-plan.md) subskrypcji i możesz użyć kreatora Przełącz plany lub chcesz przenieść się do nowego planu subskrypcji w tej samej rodzinie subskrypcji, nawet jeśli kreator Przełącz plany nie działa, nie musisz ręcznie przenosić danych i nie ma czasu na zwalnianie czasu.

|**Zadania**|**Kroki**|
|:-----|:-----|
|Kup plan, do którego chcesz przejść.  <br/> |Podczas rejestracji możesz podać nazwę firmy, która będzie używać w początkowych nazwach  *domen:*  twojafirma .onmicrosoft.com,  *twojafirma*  -public.sharepoint.com i  *twojafirma*  .sharepoint.com. Musisz użyć innej nazwy  *firmy*  niż w przypadku wszystkich istniejących subskrypcji.  <br/> > [!NOTE]> Anulowanie subskrypcji zwykle trwa co najmniej kilka miesięcy po anulowaniu subskrypcji w celu zwolnienia początkowych nazw domen, w których jest używana  *twojafirma*  z naszych systemów. Nawet jeśli planujesz zapisać wszystkie dane ze starej Microsoft 365 subskrypcji i anulować ją, wartość starej firmy nie będzie od  razu dostępna do użycia w nowej subskrypcji.           |
|Usuń domenę niestandardową ze starej Microsoft 365 subskrypcji.  <br/> | Wykonaj wymagane [czynności przed usunięciem domeny](remove-a-domain.md) , aby usunąć nazwę domeny z adresów e-mail użytkowników i usunąć rekordy DNS dla poczty e-mail i programu Lync dla domeny niestandardowej. Jeśli publicznie hostuje się w Microsoft 365 sieci Web, musisz również usunąć rekord CNAME, który na to wskazuje.  <br/> > [!IMPORTANT]> Po usunięciu rekordu MX rozsyłania poczty e-mail do tej domeny niestandardowej poczta e-mail przestanie działać do momentu dodania domeny do nowego konta, skonfigurowania nowego rekordu MX i skonfigurowania użytkowników. Po usunięciu rekordów DNS dla programu Lync program ten przestanie działać. Po usunięciu rekordu CNAME, który wskazuje publiczną witrynę sieci Web, nie będzie on dostępny.           [Usuń domenę](remove-a-domain.md) .  <br/> |
|Skonfiguruj domenę niestandardową dla nowej subskrypcji i skonfiguruj użytkowników.  <br/> | Skonfiguruj nową subskrypcję, w tym tworzenie wymaganych rekordów DNS dla domeny niestandardowej.  <br/>  Utwórz użytkowników z adresami e-mail w domenie niestandardowej.  <br/> |
|Przenoszenie danych ze starej subskrypcji do nowej.  <br/> | Zaloguj się do obu kont w osobnych oknach przeglądarki:  <br/>  Kliknij prawym przyciskiem myszy ikonę przeglądarki i otwórz dwa prywatne okna przeglądarki. Możesz użyć różnych poświadczeń w obu oknach, aby zalogować się na obu kontach.  <br/> [Przenoszenie ustawień administracyjnych między subskrypcjami](#email) <br/> [Przenoszenie danych i struktury witryny zespołu](#transfer-team-site-structure-and-data) <br/> [Przenoszenie publicznej witryny internetowej między subskrypcjami](#transfer-a-public-website-between-subscriptions) <br/> [Przenoszenie ustawień administracyjnych między subskrypcjami](#email) <br/> |
|Anuluj subskrypcję planu, który chcesz z nim zrobić, dzwoniąc do pomocy technicznej firmy Microsoft w celu Microsoft 365.  <br/> | Sprawdź, czy nowa subskrypcja działa i czy wszystkie dane zostały przeniesione.  <br/>  [Skontaktuj się z działem obsługi](../../business-video/get-help-support.md) klienta, aby anulować starą subskrypcję.  <br/> |

## <a name="transfer-administrative-settings-between-subscriptions"></a>Przenoszenie ustawień administracyjnych między subskrypcjami

Przejdź do następujących stron na poszczególnych kontach i skonfiguruj nowe konto na podstawie ustawień starego konta.
  
W przypadku przenoszenia danych z usługi Microsoft 365 do usługi Microsoft 365 Midsize Business lub Microsoft 365 Enterprise strony administratorów mają inną strukturę. Obejrzyj klip [wideo: Wprowadzenie Microsoft 365 Enterprise](../index.yml) i przejdź do następujących miejsc, aby sprawdzić ustawienia administratora.
  
Dla Microsoft 365 Enterprise i Microsoft 365 Midsize Business:
  
|**Lokalizacja**|**Cel**|
|:-----|:-----|
|**Administrator** \>  \> Microsoft 365 **ustawień usługi** <br/> |Wybierz poszczególne karty, aby uzyskać dostęp do ustawień poczty, witryn, programu Lync, oprogramowania użytkownika, haseł, społeczności, zarządzania prawami i urządzeń przenośnych.  <br/> |
|**Administrator** \> **Exchange** <br/> | Exchange Online ustawienia  <br/> |
|**Administrator** \> **SharePoint** <br/> | SharePoint online  <br/> |
|**Administrator** \> **Skype dla firm** <br/> |Dodatkowe Skype dla firm ustawienia  <br/> |

Dla Microsoft 365 Small Business
  
|**Lokalizacja**|**Cel**|
|:-----|:-----|
|**Administrator** \> **Zarządzanie ustawieniami dla całej organizacji** <br/> |Ustawienia administracyjne  <br/> |

## <a name="transfer-a-public-website-between-subscriptions"></a>Przenoszenie publicznej witryny internetowej między subskrypcjami

Jeśli masz publiczną witrynę internetową hostowaną w Microsoft 365, musisz ją zapisać i utworzyć ponownie w nowej subskrypcji.
  
> [!NOTE]
> Jeśli Twoja publiczna witryna sieci Web jest hostowana u dostawcy hostingu DNS, nie są wymagane żadne zmiany. Przejście nie będzie mieć wpływu na to.
  
Aby zapisać zawartość biblioteki dokumentów lub listy ze środowiska usługi SharePoint Online w udziałach plików lub na komputerze lokalnym, zobacz Ręczna migracja zawartości SharePoint [zawartości w trybie online](/sharepoint/troubleshoot/migration-tool/content-manual-migration).
  
> [!NOTE]
> Aplikacja do migracji witryny publicznej nie może przenosić danych do innej subskrypcji.
  
## <a name="transfer-team-site-structure-and-data"></a>Przenoszenie danych i struktury witryny zespołu

Istnieje kilka sposobów zapisywania lub przenoszenia danych witryny zespołu:
  
- Możesz zapisać starą witrynę jako szablon i zaimportować szablon do nowej witryny.

- Aby przenieść dokumenty, najpierw utwórz ręcznie hierarchię w nowej witrynie. Następnie możesz otworzyć jednocześnie obie SharePoint zespołu, otworzyć obie biblioteki dokumentów za pomocą Eksploratora Windows, a następnie skopiować i wkleić dokumenty. Zobacz [Klip wideo: kopiowanie i przenoszenie plików biblioteki za pomocą funkcji Otwórz w Eksploratorze](https://support.microsoft.com/office/d18d21a0-1f9f-4f6c-ac45-d52afa0a4a2e).

- Aby przenieść dane listy, zapisz [szablon](https://support.microsoft.com/office/c3884ad1-bc49-44b8-b3d6-3bc6a01eb393) listy i użyj zapisanego szablonu, aby ponownie utworzyć listę w nowej witrynie.

- Aby zapisać zawartość biblioteki dokumentów lub listy ze środowiska usługi SharePoint Online (witryny usługi OneDrive dla Firm lub witryn zespołu) w udziałach plików lub na komputerze lokalnym, zobacz Informacje na temat ręcznej migracji zawartości usługi SharePoint [Online](/sharepoint/troubleshoot/migration-tool/content-manual-migration).

## <a name="transfer-users-data-between-subscriptions"></a>Przenoszenie danych użytkowników między subskrypcjami

### <a name="email"></a>Adres e-mail:

Poproś użytkowników o [przeniesienie wiadomości e-mail, kontaktów, zadań](https://support.microsoft.com/office/0996ece3-57c6-49bc-977b-0d1892e2aacc) i informacji kalendarza po skonfigurowaniu nowej subskrypcji. Do swoich starych wiadomości e-mail można uzyskać dostęp, używając początkowej nazwy użytkownika, na przykład sue@contoso.onmicrosoft.com.
  
### <a name="onedrive-for-business-data"></a>OneDrive dla Firm danych:

Poproś użytkowników o skopiowanie/OneDrive dla Firm [zawartości](https://support.microsoft.com/office/59b1de2b-519e-4d3a-8f45-51647cf291cd) na komputerze, a następnie dodanie jej z powrotem do ich nowej subskrypcji.

### <a name="onenote"></a>OneNote 

Poproś użytkowników o [kopię zapasową OneNote](https://support.microsoft.com/office/back-up-notes-f58b34b0-611d-435e-87fa-7942a1767af4?ui=en-us&rs=en-us&ad=us) i przywracanie notatek z [kopii](https://support.microsoft.com/en-us/office/restore-notes-from-a-backup-5daf9cb0-6769-4998-a5de-f044fdd0d831?ui=en-us&rs=en-us&ad=us) zapasowej do ich nowych subskrypcji.
