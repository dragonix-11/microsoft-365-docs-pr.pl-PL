---
title: Planowanie konfiguracji usługi Microsoft 365 dla firm
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
- Adm_O365_Setup
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
search.appverid:
- MET150
- MOE150
ms.assetid: eb926624-018b-4486-bf11-5fba6ee4d645
description: Poznaj wymagania i zagadnienia związane z przejściem do Microsoft 365 dla firm.
ms.openlocfilehash: 831b8c20363e8c8d2339fe05edcd949ffc8c2cbb
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63013898"
---
# <a name="plan-your-setup-of-microsoft-365-for-business"></a>Planowanie konfiguracji usługi Microsoft 365 dla firm

Ten artykuł jest dla osób, które subskrybują plan Microsoft 365 dla firm.
  
Przed przeniesieniem organizacji do programu Microsoft 365 muszą być spełnione wymagania, informacje, które trzeba mieć pod ręką, oraz decyzje, które trzeba podjąć.

## <a name="overview-of-microsoft-365-business-premium-setup"></a>Omówienie Microsoft 365 Business Premium konfiguracji

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4jZwg?autoplay=false]

Gratulujemy decyzji o przeniesienia Twojej firmy do chmury z Microsoft 365! Niezależnie od tego, czy masz w firmie jedną osobę, czy 20 osób, planowanie pomoże Ci w najlepiej Microsoft 365 Business Premium.

## <a name="info-to-have-on-hand-before-you-run-the-setup-wizard"></a>Informacje do przygotowania przed uruchomieniem kreatora konfiguracji

Gdy wszystko będzie gotowe do uruchomienia kreatora konfiguracji i przeniesienia domeny do usługi Microsoft 365, potrzebne Ci będą informacje:
  
- Lista osób, które chcesz dodać do Microsoft 365. Nawet jeśli już dodano ich do Microsoft 365, jeśli aktualizujesz informacje o domenie, musisz wprowadzić ich nazwy w tym miejscu.

- Sposób powiadomienia pracowników o identyfikatorze użytkownika i hasłach w celu zalogowania się. Czy przekażesz im informacje telefonicznie? Czy wyślesz je na ich prywatny adres e-mail? Nie będzie mieć dostępu do swojej poczty e-mail, więc nie możesz go użyć.

- Jeśli masz nazwę domeny dla swojej organizacji (na przykład **contoso.com) i** planujesz korzystać z poczty e-mail firmy Microsoft, musisz wiedzieć, gdzie jest zarejestrowana Twoja domena, i mieć informacje logowania.

## <a name="what-happens-when-you-run-the-microsoft-365-setup-wizard"></a>Co się dzieje po uruchomieniu Microsoft 365 konfiguracji

Kreator konfiguracji przeprowadzi Cię przez proces instalacji aplikacji pakietu Microsoft 365 na komputerze, dodawania i weryfikowania domeny, dodawania użytkowników i przypisywania im licencji oraz łączenia Twojej domeny.

> [!NOTE]
> Jeśli chcesz przypisać role administratora w [Microsoft 365](../add-users/assign-admin-roles.md) dla firm użytkownikom, których dodasz w kreatorze, możesz to zrobić później na **stronie Użytkownicy**. 
  
Jeśli nie zakończysz pracy z kreatorem konfiguracji, możesz w dowolnym momencie wykonać zadania konfigurkowe z centrum **administracyjnegoSetup**[](https://go.microsoft.com/fwlink/p/?linkid=2024339) > . W tym miejscu możesz przeprowadzić migrację poczty e-mail i kontaktów z innej usługi poczty e-mail, zmienić domenę swojego konta administratora, zarządzać informacjami rozliczeniowymi, dodawać lub usuwać użytkowników, resetować hasła i robić inne funkcje biznesowe. Aby uzyskać więcej informacji na temat różnic między kreatorem konfiguracji a  stroną Konfiguracja, zobacz Różnice Microsoft 365 [kreatora konfiguracji a stroną Konfiguracja](o365-setup-wizard-and-setup-page.md).

Jeśli utkniesz w którymkolwiek momencie, zadzwoń do nas. [Jesteśmy tu, aby Ci pomóc.](../../business-video/get-help-support.md)
  
## <a name="when-not-to-use-the-setup-wizard-active-directory-synchronization-and-hybrid-environments"></a>Kiedy nie używać Kreatora konfiguracji: Synchronizacja z usługą Active Directory i środowiska hybrydowe

Istnieje kilka scenariuszy, które obejmują migrowanie danych lub użytkowników ze środowisk lokalnych lub konfigurowanie systemu hybrydowego, który obejmuje synchronizację katalogów. Jeśli należysz do jednej z tych kategorii, postępuj zgodnie z instrukcjami podanymi w tych artykułach:
  
- Aby skonfigurować synchronizację katalogów z lokalną usługą Active Directory, zobacz Konfigurowanie synchronizacji katalogów dla usługi [Microsoft 365](../../enterprise/set-up-directory-synchronization.md). Aby poznać różne modele tożsamości w usłudze Microsoft 365, zobacz Wdrażanie infrastruktury tożsamości dla usługi [Microsoft 365](../../enterprise/deploy-identity-solution-overview.md).

- Pełen zestaw instrukcji, które przeprowadzą Cię przez różne sposoby konfigurowania hybrydowego programu Exchange (w tym konfigurowanie rekordów DNS), można znaleźć tutaj: [Asystent wdrażania programu Exchange Server](/exchange/exchange-deployment-assistant)

- Aby skonfigurować wdrożenie hybrydowe programu SharePoint, a zwłaszcza wyszukiwanie hybrydowe i funkcje hybrydowe witryn, zobacz [Wyszukiwanie hybrydowe w programie SharePoint](/SharePoint/hybrid/hybrid-search-in-sharepoint).

## <a name="move-to-microsoft-365-all-at-once-or-in-stages"></a>Przejście do Microsoft 365 jednocześnie lub etapami

- **Chcesz przenieść swoją organizację do Microsoft 365 jednocześnie?** Jeśli tak, zaplanuj od razu przeniesienie domeny do usługi Microsoft 365 usługi. Zacznij od uruchomienia Microsoft 365 konfiguracji konta; zostanie wyświetlony monit o skonfigurowanie domeny.

- **Chcesz przejść do tej Microsoft 365 stopniowo?** Jeśli chcesz przejść do programu Microsoft 365 etapami, pomiń uruchomienie kreatora konfiguracji programu Microsoft 365 i rozważ Microsoft 365 nowych funkcji w następującej kolejności:

    1. [Dodaj pracowników do Microsoft 365](../add-users/add-users.md), aby oni mogą pobierać i instalować Office aplikacji.

    2. [Pobierz i zainstaluj aplikacje pakietu Office](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658), aby korzystać z aplikacji Word, Excel i PowerPoint na komputerze i urządzeniach.

    3. [Skonfiguruj Microsoft Teams](#plan-for-teams) do używania na spotkaniach.

    4. [Przenieś zawartość do magazynu Microsoft 365 w chmurze (OneDrive](set-up-file-storage-and-sharing.md) lub SharePoint witryn zespołu).

    5. Gdy wszystko będzie gotowe, w centrum administracyjnym [](https://go.microsoft.com/fwlink/p/?linkid=2024339)wybierz pozycję Konfiguracja w  lewym okienku nawigacji, a następnie użyj strony Konfiguracja, aby przenieść domenę i [pocztę e-mail](add-domain.md).

## <a name="check-that-your-devices-meet-system-requirements"></a>Sprawdzanie, czy urządzenia spełniają wymagania systemowe

Każda osoba w organizacji może zainstalować pakiet aplikacji Office 2016 (Word, Excel, PowerPoint i tak dalej) na maksymalnie pięciu komputerach PC i Mac. Zobacz wymagania dotyczące systemu i komputera związane z instalowaniem [pakietów Office 2016](https://go.microsoft.com/fwlink/?LinkId=534827) dla firm.
  
Aplikacje mobilne można instalować na urządzeniach z systemem iOS, Android Windows urządzeniach. Aby znaleźć informacje dotyczące obsługiwanych urządzeń przenośnych i przeglądarek, zobacz [Wymagania systemowe pakietu Office](https://go.microsoft.com/fwlink/?LinkId=534827).
  
## <a name="plan-for-email"></a>Planowanie korzystania z poczty e-mail

Jeśli planujesz zmianę obecnej usługi poczty e-mail na Microsoft 365, przełączenie trwa zazwyczaj dwa dni.
  
### <a name="plan-for-email-downtime"></a>Planowanie przestoju poczty e-mail
  
Jeśli zamierzasz używać poczty e-Microsoft 365 e-mail:
  
- Aby przenieść firmowy adres e-mail (*\@* na przykład piotr contoso.com) z innej usługi poczty e-mail do programu Microsoft 365, musisz skierować pocztę do nowej skrzynki Microsoft 365 pocztowej. Możesz to zrobić, wybierając  pozycję Migruj dane użytkowników  na stronie Konfiguracja, gdzie poprowadziMy Cię przez proces aktualizacji, które musisz wprowadzić na hoście domeny, krok po kroku.

- Po zaktualizowaniu hosta domeny zmiany są zazwyczaj wprowadzane w ciągu godziny lub dwóch. Należy jednak pamiętać, że aktualizacja zmian w Internecie może potrwać do 72 godzin.

- Ponieważ mogą wystąpić przerwy w działaniu poczty e-mail, zalecamy zmianę planu na pocztę e-mail firmy Microsoft wieczorem lub w weekend, gdy otrzymujesz mniej wiadomości e-mail.

### <a name="plan-to-move-your-existing-email-contacts-and-calendar"></a>Planowanie przeniesienia wiadomości e-mail, kontaktów i kalendarza
  
Jeśli zamierzasz używać programu Microsoft 365 e-mail, możesz zabrać ze sobą istniejące wiadomości e-mail, kontakty i kalendarz. Strona **Konfiguracja** ułatwia przenoszenie istniejących wiadomości e-mail i kontaktów w większości scenariuszy. Oferujemy również przewodniki przenoszenia skrzynek pocztowych krok po kroku.
  
|**Ile jest skrzynek pocztowych?**|**Zalecenie**|
|:-----|:-----|
|Tylko kilka  <br/> |Jeśli nie chcesz przeprowadzać migracji skrzynek pocztowych  za pomocą strony Konfiguracja, możesz pozwolić właścicielom skrzynek pocztowych na migrowanie własnych wiadomości e-mail i kontaktów. Zobacz [Migrowanie wiadomości e-mail i kontaktów Microsoft 365 dla firm](migrate-email-and-contacts-admin.md).  <br/> |
|Więcej  <br/> |Jeśli przeprowadzasz migrację z usługi Gmail, zobacz Migrowanie skrzynek pocztowych usługi [G Suite do usługi Microsoft 365](/Exchange/mailbox-migration/migrating-imap-mailboxes/migrate-g-suite-mailboxes).  <br/> Jeśli przeprowadzasz migrację od innego dostawcy poczty e-mail, w tym Exchange, zobacz Sposoby migrowania wielu kont e-mail [do Microsoft 365](/Exchange/mailbox-migration/mailbox-migration).  <br/> |

## <a name="plan-for-file-storage-and-migration"></a>Planowanie przechowywania i migrowania plików

Microsoft 365 magazyn w chmurze dla użytkowników indywidualnych, małych organizacji i przedsiębiorstw. Aby uzyskać wskazówki dotyczące miejsca przechowywania dokumentów, zobacz Gdzie [można przechowywać dokumenty w Microsoft 365](https://support.microsoft.com/office/d18d21a0-1f9f-4f6c-ac45-d52afa0a4a2e).
  
- **Możesz przenieść setki plików do** [OneDrive lub](https://support.microsoft.com/office/45114744-6D42-45CD-8975-F9617819BDEB) do SharePoint [zespołu](https://support.microsoft.com/office/da549fb1-1fcb-4167-87d0-4693e93cb7a0#__toc384119242). Możesz przekazywać do 100 plików jednocześnie. Unikaj przekazywania plików o rozmiarze przekraczającym 2 GB (taki jest domyślny maksymalny rozmiar plików).
  
- **Jeśli chcesz przenieść kilka tysięcy plików** do magazynu Microsoft 365, zapoznaj się z SharePoint [ograniczeniami online](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits). Zalecamy skorzystanie z narzędzia do migracji lub z usług [partnera](https://go.microsoft.com/fwlink/?linkid=391089) w celu ułatwienia migracji. Aby uzyskać informacje na temat migrowania dużej liczby plików, zobacz [Podręcznik migrowania dla użytkowników usługi SharePoint Online i OneDrive](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).
  
## <a name="plan-for-teams"></a>Planowanie Teams

Możesz użyć Microsoft Teams, aby dzwonić do innych osób w organizacji, które korzystają z Twojej subskrypcji. Jeśli na przykład w organizacji jest 10 osób, możesz do siebie dzwonić i korzystać z wiadomości błyskawicznych przy Teams bez żadnej specjalnej konfiguracji. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do Microsoft Teams](/MicrosoftTeams/get-started-with-teams-quick-start).

W przypadku większych organizacji lub, jeśli rozpoczynasz Skype dla firm, wdrożenia lokalne lub hybrydowe, zobacz Jak [wdrożyć](/MicrosoftTeams/how-to-roll-out-teams) Microsoft Teams.
  
## <a name="plan-for-integration-with-active-directory-or-other-software"></a>Planowanie integracji z usługą Active Directory i innym oprogramowaniem

- **Chcesz przeprowadzić integrację z lokalną usługą Active Directory?** Lokalną usługę Active Directory możesz zintegrować z usługą Microsoft 365, używając programu Azure Active Directory Połączenie. Aby uzyskać instrukcje, [zobacz Konfigurowanie synchronizacji katalogów dla Microsoft 365](../../enterprise/set-up-directory-synchronization.md).
  
- **Chcesz zintegrować program Microsoft 365 oprogramowaniem wykonanym przez inne firmy?** Jeśli chcesz zintegrować usługę Microsoft 365 innym oprogramowaniem w organizacji, zalecamy skorzystanie z usług [partnera](https://go.microsoft.com/fwlink/?linkid=391089), który pomoże Ci w wdrożeniu.
  
## <a name="do-you-want-someone-to-help-you-set-up-microsoft-365"></a>Czy chcesz, aby ktoś pomógł Ci w Microsoft 365?

- **Jeśli masz mniej niż 50 pracowników:**

  - **Poproś o pomoc, a zadzwonimy do Ciebie**. Po zakupie Microsoft 365 dostęp do centrum administracyjnego (nie musisz uruchamiać instalatora, aby uzyskać do niego dostęp). U dołu centrum administracyjnego wybierz pozycję **Potrzebujesz pomocy?** Opisz problem, a zadzwonimy do Ciebie. 
  - **W [razie Microsoft 365 skontaktuj](../../business-video/get-help-support.md) się z pomocą techniczną dla firm**. We're here to help! 
  - **Rozważ skorzystanie z usług [partnera firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=391089)**. Jeśli masz niewiele czasu lub masz zaawansowane wymagania (na przykład przeniesienie tysięcy plików do magazynu w chmurze Microsoft 365 integrowanie się z innym oprogramowaniem), doświadczony partner może być bardzo pomocny. 

- **Jeśli masz więcej niż 50 pracowników**, [Centrum wdrażania FastTrack](https://go.microsoft.com/fwlink/?LinkId=517115) pomoże Ci w przeprowadzeniu wdrożenia.