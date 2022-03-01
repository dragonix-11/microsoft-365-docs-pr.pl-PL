---
title: Aplikacje Microsoft 365 dla przedsiębiorstw
description: Jak wdrożyć Aplikacje Microsoft 365, jak je aktualizować i jak zarządzać ustawieniami
keywords: historia zmian
ms.service: m365-md
ms.sitesec: library
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 19ad7cfa3459b67b41a9d85994f960255aeeeb02
ms.sourcegitcommit: babc2dad1c0e08a9237dbe4956ffd21c0214db83
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2022
ms.locfileid: "63013823"
---
# <a name="microsoft-365-apps-for-enterprise"></a>Aplikacje usługi Microsoft 365 dla przedsiębiorstw

## <a name="initial-deployment"></a>Wdrożenie początkowe

Microsoft Managed Desktop się, że Aplikacje Microsoft 365 dla przedsiębiorstw (64-bitowa) są instalowane jako część obrazu na wszystkich [urządzeniach programowych](../service-description/device-list.md). Po dostarczyć urządzenie powinny być obecne wszystkie następujące aplikacje:

- Word
- Excel
- PowerPoint
- Outlook
- Publisher
- Access
- Skype dla firm
- OneNote

Ta metoda minimalizuje wpływ na sieć i gwarantuje, że użytkownicy będą produktywni od razu po otrzymaniu urządzenia. Następnie wdrażamy więcej zasad na urządzeniach zarządzanych, aby skonfigurować aplikacje do użycia.

> [!NOTE]
> Microsoft Teams jest wdrażana niezależnie Aplikacje Microsoft 365 dla przedsiębiorstw i nie jest uwzględniana w obrazie bazowym.

### <a name="available-deployment-to-users"></a>Wdrożenie dostępne dla użytkowników

Jeśli użytkownik z jakiegokolwiek powodu nie Aplikacje Microsoft 365 urządzenia, możesz użyć pakietu w celu zwrócenia urządzenia do stanu oczekiwanego. Dodaj użytkownika do grupy **Modern Workplace-Office-Office365_Install**, a aplikacje staną się dla nich dostępne w Portal firmy.

### <a name="microsoft-365-apps-for-enterprise-32-bit"></a>Aplikacje Microsoft 365 dla przedsiębiorstw (32-bitowa)

Microsoft Managed Desktop nie obsługuje wdrażania 32-bitowej wersji pakietu Aplikacje Microsoft 365 dla przedsiębiorstw.

## <a name="updates-to-microsoft-365-apps"></a>Aktualizacje Aplikacje Microsoft 365

Aplikacje Microsoft 365 są ustawione do aktualizacji w miesięcznym [Enterprise miesięcznym](/deployoffice/overview-update-channels#monthly-enterprise-channel-overview). Takie rozwiązanie zapewnia użytkownikom nowe funkcje Office użytkowników co miesiąc, ale w przewidywalnym harmonogramie wersji będą oni otrzymywać co miesiąc tylko jedną aktualizację. Aktualizacje są wydane w drugi wtorek miesiąca. mogą one obejmować aktualizacje funkcji, zabezpieczeń i jakości. Te aktualizacje występują automatycznie i są pobierane bezpośrednio z Office CDN dla tego określonego kanału.

Microsoft Managed Desktop poszczególne wersje są schodkami w celu zidentyfikowania potencjalnych problemów w Twoim środowisku. Ukończymy projekt 28 dni po wydaniu z grupy produktów Microsoft 365 App. Microsoft Managed Desktop planowania aktualizacji wydań dla różnych grup, aby umożliwić sprawdzanie poprawności i testowanie w następujący sposób:

- Test: zero dni
- Pierwszy: zero dni
- Szybkie: trzy dni
- Szerokie: siedem dni

Microsoft Managed Desktop ustawia siedmiodniowy [termin aktualizacji](/deployoffice/configure-update-settings-microsoft-365-apps) dla urządzeń. Gdy aktualizacja będzie dostępna, musi zostać zainstalowana w ciągu siedmiu dni. Użytkownicy [są powiadomieni](/deployoffice/end-user-update-notifications-microsoft-365-apps#notifications-your-users-see-when-you-set-an-update-deadline-for-microsoft-365-apps) o wymaganiach aktualizacji w kilku lokalizacjach: aplikacja na pasku zadań na 12 godzin przed terminem ostatecznym otrzymuje ostrzeżenie z 15 minut przed terminem. Aby aktualizacja Aplikacje Microsoft 365, wszystkie Aplikacje Microsoft 365 należy zamknąć.

### <a name="pausing-or-rolling-back-an-update"></a>Wsłuchiwanie lub wycofywanie aktualizacji

Jeśli z jakiegokolwiek powodu chcesz wstrzymać lub wycofać aktualizację Microsoft 365 aplikacji, zachęć administratora do pomocy [](../working-with-managed-desktop/admin-support.md) technicznej za pośrednictwem portalu Microsoft Managed Desktop sieci.

W trakcie wydania Microsoft Managed Desktop błędy wszystkich Aplikacje Microsoft 365. Jeśli między nową a poprzednią wersjią widać znaczną różnicę w jakości, możemy skontaktować się z Tobą za pośrednictwem portalu Microsoft Managed Desktop administracyjnego.

W zależności od ważności:

- Zapytaj, czy chcesz wstrzymać wydanie, czy
- Informuj o tym, że zostały podjęte działania w celu załagodniania problemu.

### <a name="delivery-optimization"></a>Optymalizacja dostarczania

Optymalizacja dostarczania to technologia dystrybucji w komunikacji równorzędnej dostępna w programie Windows 10. Umożliwia on urządzeniam udostępnianie przez Internet zawartości, na przykład aktualizacji, pobranych od firmy Microsoft. Optymalizacja dostarczania w Usa może zmniejszyć przepustowość sieci, ponieważ urządzenie może pobierać część aktualizacji z innego urządzenia w swojej sieci lokalnej, zamiast pobierać aktualizację całkowicie od firmy Microsoft.

[Optymalizacja](/deployoffice/delivery-optimization) dostarczania jest domyślnie włączona na urządzeniach z systemem Windows 10 Enterprise lub Windows 10 Education wydaniach.

## <a name="settings-managed-by-microsoft-managed-desktop"></a>Ustawienia zarządzane przez firmę Microsoft Managed Desktop

Firma Microsoft zarządza niektórymi ustawieniami w ramach usługi. Microsoft Managed Desktop nie zarządza planem bazowym Office zabezpieczeń. Możesz jednak ustawić je samodzielnie, korzystając z wskazówek w sekcji Zarządzanie Ustawienia [zarządzasz](#settings-you-manage).

### <a name="update-settings"></a>Aktualizowanie ustawień

Microsoft Managed Desktop obsługuje wszystkie [ustawienia aktualizacji dla](/deployoffice/configure-update-settings-microsoft-365-apps) urządzeń zarządzanych i należy je zmodyfikować.

| Ustawienie | Wartość domyślna | Opis |
| ------ | ------ | ------ |
| Konfigurowanie automatycznego nasyłania aktualizacji | Włączone | Te zasady są skonfigurowane w celu zapewnienia, że Office urządzeniach przenośnych mogą być zawsze aktualne z chmury. |
| Ustawianie terminu ostatecznego, kiedy należy stosować aktualizacje | Siedem dni | Zasady **UpdateDeadline** służą do konfigurowania okresu prolongaty, który użytkownicy mają przed wykonaniem aktualizacji na urządzeniu. Te zasady dotyczące terminów ostatecznych powodują również [powiadomienie](/deployoffice/end-user-update-notifications-microsoft-365-apps#notifications-your-users-see-when-you-set-an-update-deadline-for-microsoft-365-apps) użytkownika o zmianach wymaganych na jego urządzeniu. |
| Odroczenie aktualizacji na urządzeniu na okres | Zobacz opis | Te zasady są skonfigurowane inaczej dla każdej grupy urządzeń do zarządzania aktualizacjami. Jest ona wymagana do Microsoft Managed Desktop celu osiągnięcia celów aktualizacji: <ul> <li> Test: zero dni </li> <li>Pierwszy: zero dni</li><li>Szybkie siedem dni</li><li>Szeroki: 21 dni</li></ul> |
| Aktualizowanie ustawień powiadomień | False (Fałsz | Ustawienie "Ukryj powiadomienia o aktualizacjach" ma ustawioną wartość Fałsz na Microsoft Managed Desktop, aby zapewnić użytkownikom najlepsze środowisko aktualizacji, [](/deployoffice/end-user-update-notifications-microsoft-365-apps#notifications-your-users-see-when-you-set-an-update-deadline-for-microsoft-365-apps) powiadamiając ich o wymaganych aktualizacjach.|
| Określanie lokalizacji wyszukiwania aktualizacji | Miesięczny Enterprise kanału | W celu osiągnięcia harmonogramu aktualizacji **są** używane kombinacje zasad **UpdatePath i UpdateChannel** . Te zasady zostały tak ustawione, aby zapewnić, że wszystkie Office będą otrzymywać aktualizacje bezpośrednio z CDN miesięcznego Enterprise channel.|
| Określanie wersji docelowej Aplikacje Microsoft 365 | Zobacz opis | Zasady Wersja docelowa są czasami używane przez program Microsoft Managed Desktop do wycofywania lub przypinania określonej wersji pakietu Office.|
| Ukrywanie opcji włączania lub wyłączania aktualizacji Office automatycznych | Włączone | To ustawienie jest wymagane, aby Microsoft Managed Desktop cele aktualizacji dla aplikacji Microsoft 365. |
| Ustawienia pierwszego uruchomienia | Zobacz opis | Istnieje kilka ustawień, które wpływają na zachowanie po pierwszym uruchomieniu Office. |
| Zaakceptowanie postanowień licencyjnych w imieniu użytkownika końcowego | Wyłączone | Gdy użytkownik po raz pierwszy otwiera aplikację Microsoft 365, jest wyświetlany monit o zaakceptowanie postanowień licencyjnych. Jeśli chcesz zaakceptować postanowienia licencyjne w imieniu użytkowników, zachowuj wniosek o pomoc techniczną do zespołu Microsoft Managed Desktop Operations i poproś o włączeniu tego ustawienia. |
| Pomijanie Outlook pola wyboru dla urządzenia przenośnego | Wyłączone | Gdy użytkownik po raz pierwszy Outlook aplikację, jest wyświetlany monit o zainstalowanie aplikacji Outlook Mobile. Jeśli nie chcesz, aby użytkownicy widzili to pole wyboru, zachowuj wniosek o pomoc techniczną do zespołu Microsoft Managed Desktop Operations i poproś o włączeniu tego ustawienia dla Twoich urządzeń. |

## <a name="other-settings"></a>Inne ustawienia

Istnieją inne Microsoft 365 aplikacji, które Microsoft Managed Desktop opcjonalnie skonfigurować w Twoim imieniu.

| Ustawienie | Wartość domyślna | Opis |
| ------ | ------ | ------ |
| Wyłączanie osobistych OneDrive | Wyłączone | Niektóre organizacje martwią się o to, że użytkownicy mają dostęp zarówno do plików firmowych, jak i osobistych na swoich urządzeniach. Możesz złożyć wniosek o pomoc techniczną do zespołu Microsoft Managed Desktop Operations i poprosić o włączeniu tego ustawienia. |

## <a name="settings-you-manage"></a>Ustawienia zarządzasz

Istnieje wiele innych zasad, Microsoft Managed Desktop nie są jeszcze ustawione w ramach naszej usługi. Te zasady można skonfigurować przy użyciu usługi Microsoft Intune, która korzysta Office [zasad chmury](/DeployOffice/overview-office-cloud-policy-service#how-the-policy-configuration-is-applied). Aby ustawić te zasady, wykonaj następujące czynności:

1. Zaloguj się do centrum administracyjnego programu Microsoft Endpoint Manager.
1. Wybierz **pozycję Aplikacje**.
1. Wybierz **pozycję Zasady dla Office a** następnie wybierz pozycję **Utwórz**.
1. Na **stronie Tworzenie** konfiguracji zasad wykonaj następujące czynności:
    - Wprowadź nazwę.
    - Opcjonalnie podaj opis.
    - W **obszarze przypisania określ**, czy te zasady mają zastosowanie do wszystkich użytkowników usługi Aplikacje Microsoft 365 dla przedsiębiorstw, czy tylko do użytkowników anonimowych dostępu do dokumentów przy użyciu Office dla sieci web.
    - Wybierz AAD **zabezpieczeń,** która jest przypisana do konfiguracji zasad. Każda konfiguracja zasad może być przypisana tylko do jednej grupy. Do każdej grupy można przypisać tylko jedną konfigurację zasad.
    - Skonfiguruj ustawienia zasad, które mają być uwzględnione w konfiguracji zasad. Możesz wyszukać nazwę ustawienia zasad, aby znaleźć ustawienie zasad, które chcesz skonfigurować. Możesz również filtrować, czy zasady są zalecanym planem bazowym zabezpieczeń i czy zostały skonfigurowane. Kolumna platformy wskazuje, czy zasady są stosowane do Aplikacje Microsoft 365 dla przedsiębiorstw dla Windows, Office dla sieci web lub wszystkich.
1. Po wybraniu opcji wybierz pozycję **Utwórz**.

> [!NOTE]
> Office konfiguracji obsługują tylko wdrażanie oparte na użytkownikach
