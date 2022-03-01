---
title: Środowisko pierwszego uruchomienia z programem Autopilot i stroną stanu rejestracji
description: Jak wdrożyć środowisko espa i używane ustawienia oraz zmiany konfiguracji
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: 813355d57f24f9cafcb97b73b5fde641800634ec
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016031"
---
# <a name="first-run-experience-with-autopilot-and-the-enrollment-status-page"></a>Środowisko pierwszego uruchomienia z programem Autopilot i stroną stanu rejestracji

Microsoft Managed Desktop korzysta zarówno z rozwiązania [Windows,](/windows/deployment/windows-autopilot/windows-autopilot) jak i strony stanu rejestracji Microsoft Intune ([ESP)](/windows/deployment/windows-autopilot/enrollment-status) firmy Microsoft Intune, aby zapewnić użytkownikom najlepsze możliwe środowisko pierwszego uruchomienia.

## <a name="initial-deployment"></a>Wdrożenie początkowe

Aby zapewnić obsługę esp, należy zarejestrować urządzenia w Microsoft Managed Desktop serwisie. Aby uzyskać więcej informacji na temat rejestracji, [zobacz Rejestrowanie nowych urządzeń samodzielnie](../get-started/register-devices-self.md) lub Procedura rejestrowania urządzeń [przez partnerów](../get-started/register-devices-partner.md).
Strony stanu rejestracji i rozwiązania Autopilot dla wdrożenia wstępnie inicjowania obsługi administracyjnej są domyślnie włączone Microsoft Managed Desktop.

## <a name="autopilot-profile-settings"></a>Ustawienia profilu rozwiązania Autopilot

Microsoft Managed Desktop te ustawienia są używane w profilu rozwiązania Autopilot używanym na urządzeniach użytkowników:

| Ustawienie | Value |
| ----- | ----- |
| Tryb wdrażania | Sterowane przez użytkownika |
| Dołącz do usługi Azure AD jako | Dołączyć do usługi Azure AD |
| Język (region) | Wybór użytkownika |
| Automatyczne konfigurowanie klawiatury | Nie |
| Postanowienia licencyjne dotyczące oprogramowania firmy Microsoft | Ukryj |
| Ustawienia prywatności | Ukryj |
| Ukrywanie opcji zmiany konta | Pokaż |
| Typ konta użytkownika| Standard |
| Zezwalaj na białe wyechiwnie (OOBE) | Tak |
| Stosowanie szablonu nazwy urządzenia | Tak |
| Wprowadź nazwę | `MMD-%RAND:11%` |

## <a name="enrollment-status-page-settings"></a>Ustawienia strony stanu rejestracji

Microsoft Managed Desktop korzysta z tych ustawień na stronie stanu rejestracji:

| Ustawienie | Value |
| ------ | ------ |
| Pokazywanie postępu konfiguracji aplikacji i profilu | Tak |
| Wyświetlanie błędu, gdy instalacja trwa dłużej niż określona liczba minut | 60 |
| Wyświetlanie niestandardowego komunikatu w przypadku wystąpienia błędu limitu czasu | Nie |
| Zezwalaj użytkownikom na zbieranie dzienników dotyczących błędów instalacji| Tak |
| Pokazywanie strony tylko na urządzeniach aprowizowanych przez środowisko "out-of-box" (OOBE) | Tak |
| Blokowanie używania urządzenia do momentu zainstalowania wszystkich aplikacji i profilów | Tak |
| Zezwalaj użytkownikom na resetowanie urządzenia w przypadku wystąpienia błędu instalacji | Tak |
| Zezwalaj użytkownikom na używanie urządzenia w przypadku wystąpienia błędu instalacji | Tak |
| Zablokuj korzystanie z urządzenia do momentu zainstalowania tych wymaganych aplikacji, jeśli zostaną one przypisane do użytkownika/urządzenia <ul><li> Nowoczesne miejsce pracy — korekta czasu</li><li>Nowoczesne miejsce pracy — biblioteka klientów</li></ul> | Tak |

Środowisko strony stanu rejestracji występuje w trzech fazach. Aby uzyskać więcej informacji, zobacz [Informacje o śledzeniu strony stanu rejestracji](/mem/intune/enrollment/windows-enrollment-status#enrollment-status-page-tracking-information).

Środowisko będzie przebiegać w następujący sposób:

1. Środowisko autopilota jest uruchamiane i użytkownik wprowadza swoje poświadczenia.
2. Urządzenie otworzy stronę Stan rejestracji i przejdzie przez etapy Przygotowanie urządzenia i Konfiguracja urządzenia. Trzeci krok (Konfiguracja konta) jest *obecnie* pomijany w konfiguracji usługi Microsoft Managed Desktop ponieważ esp.użytkownika jest wyłączony. Urządzenie zostanie uruchomione ponownie.
3. Po ponownym uruchomieniu urządzenia zostanie otwarta Windows logowania z innym **użytkownikiem**.
4. Użytkownicy ponownie wpiszą swoje poświadczenia i pulpit zostanie otwarty.

> [!NOTE]
> Aplikacje Win32 są wdrażane podczas espazy, tylko jeśli Windows 10 ma wersję 1903 lub nowszą.

![Strona startowa konfiguracji rozwiązania Autopilot z fazami "przygotowanie urządzenia" i "konfigurowanie urządzenia".](../../media/mmd-autopilot-screenshot.png)

## <a name="additional-prerequisites-for-autopilot-for-pre-provisioned-deployment"></a>Dodatkowe wymagania wstępne rozwiązania Autopilot dla wdrożenia z wstępnie inicjowaniem obsługi administracyjnej

- Urządzenie musi mieć połączenie z siecią przewodową.
- Jeśli masz urządzenia zarejestrowane za pośrednictwem portalu Microsoft Managed Desktop przed sierpniem 2020 r., wyrejestrować je i ponownie zarejestrować.
- Urządzenia muszą mieć obraz fabryczny, który zawiera zainstalowaną aktualizację skumulowaną z listopada 2020 r. [19H1/19H2 2020.11C](https://support.microsoft.com/topic/november-19-2020-kb4586819-os-builds-18362-1237-and-18363-1237-preview-25cbb849-74af-b8b8-29b8-68aa925e8cc3) lub [20H1 2020.11C](https://support.microsoft.com/topic/november-30-2020-kb4586853-os-builds-19041-662-and-19042-662-preview-8fb07fb8-a7dd-ea62-d65e-3305da09f92e), albo musi zostać ponownie zainstalowany z najnowszym obrazem Microsoft Managed Desktop.
- Urządzenia fizyczne muszą obsługiwać wiadomości TPM 2.0 i atestowania urządzeń. Maszyny wirtualne nie są obsługiwane. W procesie wstępnej obsługi administracyjnej są Windows funkcje automatycznego rozwiązania Autopilot, dlatego jest wymagany moduł TPM 2.0. Proces atestowania TPM wymaga również dostępu do zestawu adresów URL HTTPS, które są unikatowe dla każdego dostawcy TPM. Aby uzyskać więcej informacji, zobacz wpis Tryb samodzielnego wdrażania rozwiązania Autopilot i Wstępnie aprowowane wdrażanie rozwiązania Autopilot w Windows [sieci z programem Autopilot](/mem/autopilot/networking-requirements#tpm).

## <a name="sequence-of-events-in-autopilot-for-pre-provisioned-deployment"></a>Sekwencja zdarzeń w rozwiązaniach Autopilot w celu wdrożenia z wstępnie inicjowaniem obsługi administracyjnej

1. Administrator IT może w razie potrzeby ponownie zaimportować lub zresetować urządzenie.
2. Administrator IT zainspiruje urządzenie, dotrze do urządzenia i naciska klawisz Windows pięć razy.
3. Administrator IT wybiera pozycję Windows inicjowania obsługi rozwiązania Autopilot, a następnie wybiera pozycję **Kontynuuj**. Na ekranie Windows konfiguracji rozwiązania Autopilot zostaną wyświetlone informacje o urządzeniu.
4. Administrator IT wybiera pozycję **Inicjowanie obsługi administracyjnej** , aby rozpocząć proces inicjowania obsługi.
5. Urządzenie uruchamia protokół ESP i przechodzi przez fazy przygotowywania i konfigurowania urządzeń. Na etapie konfiguracji urządzenia będzie wyświetlany komunikat Instalacja aplikacji **x z x** (w zależności od dokładnej konfiguracji profilu ESP).
6. Krok konfiguracji konta jest obecnie pomijany w konfiguracji Microsoft Managed Desktop, ponieważ jest wyłączany użytkownik esp.
7. Urządzenie zostanie uruchomione ponownie.

Po ponownym uruchomieniu urządzenia zostanie na nim zielony ekran statusu z przyciskiem **Reseal** .

> [!IMPORTANT]
> Znane problemy:
>
> - Funkcja ESP nie uruchamia się ponownie po uruchomieniu rozwiązania Autopilot z wstępnie obsługiną funkcją ponownego wdrożenia.
> - Nazwa urządzenia nie jest zmieniana przez rozwiązania Autopilot w celu wdrożenia z wstępnie inicjowaniem obsługi administracyjnej. Nazwa urządzenia zostanie zmieniona tylko po zakończeniu przepływu użytkownika ESP.

## <a name="change-to-autopilot-and-enrollment-status-page-settings"></a>Zmiana na ustawienia rozwiązania Autopilot i strony stanu rejestracji

Jeśli konfiguracja używana przez program Microsoft Managed Desktop nie odpowiada Twoim potrzebom, możesz utworzyć zgłoszenie do pomocy technicznej za pośrednictwem [portalu administracyjnego](https://portal.azure.com/). Oto kilka przykładów typów konfiguracji, które mogą być potrzebne:

### <a name="autopilot-settings-change"></a>Zmiana ustawień rozwiązania Autopilot

Możesz poprosić o inny szablon nazwy urządzenia. Nie możesz jednak zmienić trybu wdrażania, dołączyć do usługi Azure AD Jako, prywatności Ustawienia lub Typu konta użytkownika.

### <a name="enrollment-status-page-settings-change"></a>Zmiana ustawień strony stanu rejestracji

- Dłuższa liczba minut dla ustawienia "Pokaż błąd, gdy instalacja trwa dłużej niż określona liczba minut".
- Zostanie wyświetlony komunikat o błędzie.
- Dodawanie lub usuwanie aplikacji w ustawieniu "Blokowanie używania urządzeń do momentu zainstalowania tych wymaganych aplikacji, jeśli zostaną przypisane do użytkownika/urządzenia".

## <a name="required-applications"></a>Wymagane aplikacje

- Musisz kierować aplikacje do grup urządzeń *Nowoczesne miejsce pracy* Test, Pierwsze, Szybkie i Ogólne. Aplikacje muszą zostać zainstalowane w kontekście "systemowym". Zanim przypiszesz je do wszystkich grup, upewnij się, że ukończono testowanie przy użyciu espa w grupie Test.
- Żadne aplikacje nie powinny wymagać ponownego uruchomienia urządzenia. Zalecamy, aby podczas tworzenia pakietu aplikacji dla aplikacji ustawić ustawienie "Nic nie robisz", jeśli urządzenie wymaga ponownego uruchomienia.
- Ogranicz wymagane aplikacje tylko do podstawowych aplikacji, których użytkownik potrzebuje natychmiast po zalogowaniu się na urządzeniu.
- Zachowaj całkowity rozmiar wszystkich aplikacji łącznie poniżej 1 GB, aby uniknąć limitów czasu na etapie instalacji aplikacji.
- Najlepiej, jeśli aplikacje nie powinny mieć żadnych zależności. Jeśli masz aplikacje, które *muszą* mieć zależności, upewnij się, że konfigurujesz, testujesz i sprawdzasz je w ramach oceny espazy.
- Microsoft Teams nie może być uwzględniona w esp.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Procedura rozpoczynania pracy z Microsoft Managed Desktop

1. Portalu [administracyjnego programu](access-admin-portal.md) Access.
1. [Dodaj i zweryfikuj kontakty administratora w portalu administracyjnym](add-admin-contacts.md).
1. [Dostosuj ustawienia po rejestracji](conditional-access.md).
1. Wdrażanie i [przypisywanie Intune — Portal firmy](company-portal.md).
1. [Przypisywanie licencji](assign-licenses.md).
1. [Wdychuj aplikacje](deploy-apps.md).
1. [Konfigurowanie urządzeń](set-up-devices.md).
1. Skonfiguruj środowisko pierwszego uruchomienia za pomocą rozwiązania Autopilot i strony stanu rejestracji (w tym artykule).
1. [Włączanie funkcji pomocy technicznej dla użytkowników](enable-support.md).
1. [Przygotuj użytkowników do korzystania z urządzeń](get-started-devices.md).
1. [Wprowadzenie do sterowania aplikacją](get-started-app-control.md).
