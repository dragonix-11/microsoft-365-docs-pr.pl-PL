---
title: Planowanie konfiguracji subskrypcji Microsoft 365 dla Firm
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
description: Dowiedz się więcej o wymaganiach i zagadnieniach związanych z przejściem do Microsoft 365 dla firm.
ms.openlocfilehash: a5f777a411f82de30c1d7dc69f07f92eadbbedce
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2022
ms.locfileid: "65317477"
---
# <a name="plan-your-setup-of-microsoft-365-for-business"></a>Planowanie konfiguracji subskrypcji Microsoft 365 dla Firm

Ten artykuł dotyczy osób, które subskrybują Microsoft 365 dla planu biznesowego.
  
Przed przeniesieniem organizacji do Microsoft 365 istnieją wymagania, które należy spełnić, informacje, które musisz mieć pod ręką i decyzje, które musisz podjąć.

## <a name="overview-of-microsoft-365-for-business-setup"></a>Omówienie konfiguracji Microsoft 365 dla firm

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Vjso?autoplay=false]

Gratulujemy decyzji o przeniesieniu firmy do chmury za pomocą Microsoft 365! Niezależnie od tego, czy masz jedną osobę w swojej firmie, czy 20 lat, wykonanie małego planowania pomoże Ci w jak największym wykorzystać Microsoft 365 dla biznesu.

## <a name="info-to-have-on-hand-before-you-run-the-setup-wizard"></a>Informacje, które należy mieć pod ręką przed uruchomieniem kreatora instalacji

Gdy wszystko będzie gotowe do uruchomienia kreatora konfiguracji i przeniesienia domeny do Microsoft 365, oto informacje, które należy mieć pod ręką:
  
- Lista osób, które chcesz dodać do Microsoft 365. Nawet jeśli dodano je już do Microsoft 365, jeśli aktualizujesz informacje o domenie, musisz wprowadzić ich nazwy tutaj.

- Jak powiadomisz pracowników o identyfikatorze użytkownika i haśle, aby mogli się zalogować. Czy przekażesz im informacje telefonicznie? Czy wyślesz je na ich prywatny adres e-mail? Nie będą mieli dostępu do poczty e-mail, więc nie możesz jej użyć.

- Jeśli masz nazwę domeny organizacji (na przykład contoso.com) **i** planujesz korzystanie z poczty e-mail firmy Microsoft, musisz wiedzieć, gdzie twoja domena jest zarejestrowana i mieć informacje o logowaniu.

## <a name="what-happens-when-you-run-the-microsoft-365-setup-wizard"></a>Co się stanie po uruchomieniu kreatora konfiguracji Microsoft 365

Kreator instalacji przeprowadzi Cię przez proces instalowania aplikacji Microsoft 365 na komputerze, dodawania i weryfikowania domeny, dodawania użytkowników i przypisywania do nich licencji oraz łączenia domeny.

> [!NOTE]
> Jeśli musisz [przypisać role administratora w Microsoft 365 dla firm](../add-users/assign-admin-roles.md) do użytkowników dodanych w kreatorze, możesz to zrobić później na stronie **Użytkownicy**. 
  
Jeśli kreator konfiguracji nie zostanie ukończony, możesz wykonać zadania konfiguracji w dowolnym momencie z [poziomu centrum](https://go.microsoft.com/fwlink/p/?linkid=2024339) >  **administracyjnegoSetup**. W tym miejscu możesz migrować wiadomości e-mail i kontakty z innej usługi poczty e-mail, zmieniać domenę konta administratora, zarządzać informacjami rozliczeniowymi, dodawać lub usuwać użytkowników, resetować hasła i wykonywać inne funkcje biznesowe. Aby uzyskać więcej informacji na temat różnic między kreatorem instalacji a stroną **Instalatora**, zobacz [Różnice między kreatorem konfiguracji Microsoft 365 a stroną Instalatora](o365-setup-wizard-and-setup-page.md).

Jeśli utkniesz w którymkolwiek momencie, zadzwoń do nas. [Jesteśmy tutaj, aby pomóc!](../../business-video/get-help-support.md).
  
## <a name="when-not-to-use-the-setup-wizard-active-directory-synchronization-and-hybrid-environments"></a>Kiedy nie używać Kreatora konfiguracji: Synchronizacja z usługą Active Directory i środowiska hybrydowe

Istnieje kilka scenariuszy, które obejmują migrowanie danych lub użytkowników ze środowisk lokalnych lub konfigurowanie systemu hybrydowego, który obejmuje synchronizację katalogów. Jeśli jesteś w jednej z kategorii, postępuj zgodnie z instrukcjami w następujących artykułach:
  
- Aby skonfigurować synchronizację katalogów z lokalna usługa Active Directory, zobacz [Konfigurowanie synchronizacji katalogów dla Microsoft 365](../../enterprise/set-up-directory-synchronization.md) i zrozumienie różnych modeli tożsamości w Microsoft 365, zobacz [Wdrażanie infrastruktury tożsamości dla Microsoft 365 ](../../enterprise/deploy-identity-solution-overview.md).

- Aby skonfigurować hybrydową Exchange, pełny zestaw instrukcji, które przeprowadzą Cię przez różne sposoby konfigurowania hybrydowej wymiany (w tym konfigurowania rekordów DNS) można znaleźć tutaj: [Exchange Server Asystent wdrażania](/exchange/exchange-deployment-assistant)

- Aby skonfigurować wdrożenie hybrydowe programu SharePoint, a zwłaszcza wyszukiwanie hybrydowe i funkcje hybrydowe witryn, zobacz [Wyszukiwanie hybrydowe w programie SharePoint](/SharePoint/hybrid/hybrid-search-in-sharepoint).

## <a name="move-to-microsoft-365-all-at-once-or-in-stages"></a>Przechodzenie do Microsoft 365 wszystkich naraz lub etapach

- **Czy chcesz przenieść organizację do Microsoft 365 wszystkich jednocześnie?** Jeśli tak, od razu zaplanuj przeniesienie domeny do Microsoft 365. Zacznij od uruchomienia kreatora konfiguracji Microsoft 365. Zostanie wyświetlony monit o skonfigurowanie domeny.

- **Czy chcesz przejść do Microsoft 365 stopniowo?** Jeśli chcesz przejść do Microsoft 365 etapami, pomiń uruchamianie kreatora konfiguracji Microsoft 365 i rozważ wdrożenie funkcji Microsoft 365 w następującej kolejności:

    1. [Dodaj pracowników do Microsoft 365, aby](../add-users/add-users.md) mogli pobierać i instalować aplikacje Office.

    2. [Pobierz i zainstaluj aplikacje pakietu Office](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658), aby korzystać z aplikacji Word, Excel i PowerPoint na komputerze i urządzeniach.

    3. [Skonfiguruj Microsoft Teams](#plan-for-teams) do użycia na potrzeby spotkań.

    4. [Przenieś zawartość do magazynu w chmurze Microsoft 365](set-up-file-storage-and-sharing.md) (witryny zespołu OneDrive lub SharePoint).

    5. Gdy wszystko będzie gotowe, w [centrum administracyjnym](https://go.microsoft.com/fwlink/p/?linkid=2024339) wybierz pozycję **Instalator** w okienku nawigacji po lewej stronie i użyj strony **Instalatora** , aby [przenieść domenę i wiadomość e-mail](add-domain.md).

## <a name="check-that-your-devices-meet-system-requirements"></a>Sprawdzanie, czy urządzenia spełniają wymagania systemowe

Każda osoba w organizacji może zainstalować pakiet aplikacji Office 2016 (Word, Excel, PowerPoint itd.) na maksymalnie pięciu komputerach PC i Mac. Zobacz wymagania dotyczące systemu i komputera związane z instalowaniem [pakietów Office 2016](https://go.microsoft.com/fwlink/?LinkId=534827) dla firm.
  
Aplikacje mobilne można instalować na urządzeniach iOS, Android i Windows. Aby znaleźć informacje dotyczące obsługiwanych urządzeń przenośnych i przeglądarek, zobacz [Wymagania systemowe pakietu Office](https://go.microsoft.com/fwlink/?LinkId=534827).
  
## <a name="plan-for-email"></a>Planowanie korzystania z poczty e-mail

Jeśli planujesz przejście z istniejącej usługi poczty e-mail do Microsoft 365, przełączenie zwykle trwa dwa dni.
  
### <a name="plan-for-email-downtime"></a>Planowanie przestoju poczty e-mail
  
Jeśli zamierzasz użyć Microsoft 365 dla wiadomości e-mail:
  
- Aby przenieść służbowy adres e-mail (na przykład *rob\@ contoso.com*) z innej usługi poczty e-mail do Microsoft 365, musisz skierować pocztę do nowej skrzynki pocztowej Microsoft 365. W tym celu wybierz pozycję **Migruj dane użytkowników** na stronie **Konfiguracja** , gdzie przeprowadzimy Cię przez aktualizacje, które należy wprowadzić na hoście domeny, krok po kroku.

- Po zaktualizowaniu hosta domeny zmiany są zazwyczaj wprowadzane w ciągu godziny lub dwóch. Należy jednak pamiętać, że aktualizacja zmian w Internecie może czasami potrwać do 72 godzin.

- Ponieważ może wystąpić przestój poczty e-mail, zalecamy przejście na pocztę e-mail firmy Microsoft w godzinach wieczornych lub weekendowych w przypadku otrzymywania mniejszej liczby wiadomości e-mail.

### <a name="plan-to-move-your-existing-email-contacts-and-calendar"></a>Planowanie przeniesienia wiadomości e-mail, kontaktów i kalendarza
  
Jeśli zamierzasz używać Microsoft 365 dla swojego konta e-mail, możesz zabrać ze sobą istniejące wiadomości e-mail, kontakty i kalendarz. Strona **Konfiguracja** ułatwia przenoszenie istniejących wiadomości e-mail i kontaktów w większości scenariuszy. Oferujemy również przewodniki przenoszenia skrzynek pocztowych krok po kroku.
  
|**Ile jest skrzynek pocztowych?**|**Zalecenie**|
|:-----|:-----|
|Tylko kilka  <br/> |Jeśli nie chcesz migrować skrzynek pocztowych przy użyciu strony **Konfiguracja** , możesz zezwolić właścicielom skrzynek pocztowych na migrowanie własnych wiadomości e-mail i kontaktów. Zobacz [Migrowanie poczty e-mail i kontaktów do Microsoft 365 dla firm](migrate-email-and-contacts-admin.md).  <br/> |
|Więcej  <br/> |Jeśli migrujesz z usługi Gmail, zobacz [Migrate G Suite mailboxes to Microsoft 365 (Migrowanie skrzynek pocztowych pakietu G Suite do Microsoft 365](/Exchange/mailbox-migration/migrating-imap-mailboxes/migrate-g-suite-mailboxes)).  <br/> Jeśli przeprowadzasz migrację z innego dostawcy poczty e-mail, w tym Exchange, zobacz [Sposoby migracji wielu kont e-mail do Microsoft 365](/Exchange/mailbox-migration/mailbox-migration).  <br/> |

## <a name="plan-for-file-storage-and-migration"></a>Planowanie przechowywania i migrowania plików

Microsoft 365 zapewnia magazyn w chmurze dla użytkowników indywidualnych, małych organizacji i przedsiębiorstw. Aby uzyskać wskazówki dotyczące miejsca przechowywania, zobacz [Gdzie można przechowywać dokumenty w Microsoft 365](https://support.microsoft.com/office/d18d21a0-1f9f-4f6c-ac45-d52afa0a4a2e).
  
- **Możesz przenieść setki plików** do [OneDrive](https://support.microsoft.com/office/45114744-6D42-45CD-8975-F9617819BDEB) lub do [witryny zespołu SharePoint](https://support.microsoft.com/office/da549fb1-1fcb-4167-87d0-4693e93cb7a0#__toc384119242). Możesz przekazywać do 100 plików jednocześnie. Unikaj przekazywania plików o rozmiarze przekraczającym 2 GB (taki jest domyślny maksymalny rozmiar plików).
  
- **Jeśli chcesz przenieść kilka tysięcy plików** do magazynu Microsoft 365, zapoznaj się z [SharePoint Limity online](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits). Zalecamy skorzystanie z narzędzia do migracji lub z usług [partnera](https://go.microsoft.com/fwlink/?linkid=391089) w celu ułatwienia migracji. Aby uzyskać informacje na temat migrowania dużej liczby plików, zobacz [Podręcznik migrowania dla użytkowników usługi SharePoint Online i OneDrive](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).
  
## <a name="plan-for-teams"></a>Planowanie Teams

Możesz użyć Microsoft Teams do nawiązywania połączeń z innymi osobami w organizacji, które korzystają z Twojej subskrypcji. Jeśli na przykład organizacja ma 10 osób, możesz do siebie dzwonić i przekazywać wiadomości błyskawiczne przy użyciu Teams bez żadnej specjalnej konfiguracji. Aby uzyskać więcej informacji, zobacz [Wprowadzenie z Microsoft Teams](/MicrosoftTeams/get-started-with-teams-quick-start).

W przypadku większych organizacji lub jeśli zaczynasz od Skype dla firm, wdrożeń lokalnych lub hybrydowych, zobacz [Jak wdrożyć Microsoft Teams](/MicrosoftTeams/how-to-roll-out-teams).
  
## <a name="plan-for-integration-with-active-directory-or-other-software"></a>Planowanie integracji z usługą Active Directory i innym oprogramowaniem

- **Chcesz przeprowadzić integrację z lokalną usługą Active Directory?** Możesz zintegrować lokalna usługa Active Directory z Microsoft 365 przy użyciu Azure Active Directory Połączenie. Aby uzyskać instrukcje, zobacz [Konfigurowanie synchronizacji katalogów dla Microsoft 365](../../enterprise/set-up-directory-synchronization.md).
  
- **Czy chcesz zintegrować Microsoft 365 z oprogramowaniem innych firm?** Jeśli chcesz zintegrować Microsoft 365 z innym oprogramowaniem w organizacji, zalecamy [zatrudnienie partnera](https://go.microsoft.com/fwlink/?linkid=391089), który pomoże Ci we wdrożeniu.
  
## <a name="do-you-want-someone-to-help-you-set-up-microsoft-365"></a>Czy chcesz, aby ktoś pomógł Ci skonfigurować Microsoft 365?

- **Jeśli masz mniej niż 50 pracowników:**

  - **Poproś o pomoc, a zadzwonimy do Ciebie**. Po zakupie Microsoft 365 możesz uzyskać dostęp do centrum administracyjnego (nie musisz uruchamiać instalatora, aby się do niego dostać). W dolnej części centrum administracyjnego wybierz pozycję **Potrzebujesz pomocy?** Opisz problem, a zadzwonimy do Ciebie. 
  - **Skontaktuj [się z Microsoft 365 pomocy technicznej dla firm](../../business-video/get-help-support.md), aby uzyskać odpowiedzi na pytania**. We're here to help! 
  - **Rozważ skorzystanie z usług [partnera firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=391089)**. Jeśli brakuje Ci czasu lub masz zaawansowane wymagania (takie jak przenoszenie tysięcy plików do Microsoft 365 magazynu w chmurze lub integracja z innym oprogramowaniem), doświadczony partner może być bardzo pomocny. 

- **Jeśli masz więcej niż 50 pracowników**, [Centrum wdrażania FastTrack](https://go.microsoft.com/fwlink/?LinkId=517115) pomoże Ci w przeprowadzeniu wdrożenia.

## <a name="see-also"></a>Zobacz też

[Najlepsze rozwiązania dotyczące zabezpieczania Microsoft 365 dla planów biznesowych](../security-and-compliance/secure-your-business-data.md)
