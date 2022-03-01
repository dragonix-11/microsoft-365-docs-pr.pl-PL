---
title: Urządzenia w Windows 10 Windows 11 urządzeń przez zasady grupy
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Użyj zasady grupy, aby wdrożyć pakiet konfiguracji na Windows 10 i Windows 11 urządzeń, tak aby były one dołączane do usługi.
ms.openlocfilehash: fbba73fcf15ee9f71c4caacc57155a64e6cb9e9c
ms.sourcegitcommit: 8eca41cd21280ffcb1f50cafce7a934e5544f302
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2021
ms.locfileid: "62999367"
---
# <a name="onboard-windows-10-devices-and-windows-11-using-group-policy"></a>Urządzenia Windows 10 i urządzenia Windows 11 przy użyciu zasady grupy 

**Dotyczy:**

- [Microsoft 365 punktu końcowego ochrony przed utratą danych (DLP)](./endpoint-dlp-learn-about.md)
- [Zarządzanie ryzykiem w niejawnym programie testów](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)
- zasady grupy

> [!NOTE]
> Aby wdrożyć zasady grupy GP, musisz korzystać z programu Windows Server 2008 R2 lub nowszego.

> W Windows Server 2019 może być konieczne zastąpienie NT AUTHORITY\Well-Known-System-Account na NT AUTHORITY\SYSTEM pliku XML, który tworzy zasady grupy preferencji systemu.

## <a name="onboard-devices-using-group-policy"></a>Urządzenia wyniesiene przy użyciu zasady grupy

1. Otwórz [Centrum zgodności](https://compliance.microsoft.com).

2. W okienku nawigacji wybierz pozycję **Ustawienia** >  **Wniezienie urządzenia**.

3. W polu **Metoda wdrażania** wybierz pozycję **Zasady grupy**.

4. Kliknij **pozycję Pobierz pakiet** i zapisz .zip pliku.

5. Wyodrębnianie zawartości pliku .zip do udostępnionej lokalizacji tylko do odczytu, do której dostęp jest możliwy na urządzeniu. Powinien mieć folder o nazwie *OptionalParamsPolicy* i plik *DeviceComplianceLocalOnboardingScript.cmd*.

6. Otwórz [konsolę zasady grupy zarządzania](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC), kliknij prawym przyciskiem myszy obiekt zasady grupy obiekt (GPO), który chcesz skonfigurować, a następnie kliknij polecenie **Edytuj**.

7. W **edytorze zasady grupy zarządzaniem** przejdź do opcji Konfiguracja **komputera,** Preferencje **, a** następnie **Ustawienia Panelu sterowania**.

8. Kliknij prawym przyciskiem **myszy pozycję Zaplanowane zadania**, wskaż pozycję **Nowe**, a następnie kliknij pozycję **Zadanie natychmiastowe (co najmniej Windows 7).**

9. W **oknie** Zadanie, które zostanie otwarte, przejdź do **karty** Ogólne. W **obszarze Opcje zabezpieczeń** kliknij **pozycję Zmień użytkownika lub grupę** i wpisz SYSTEM, a następnie kliknij pozycję **Sprawdź nazwy** , a następnie kliknij **przycisk OK**. Nt AUTHORITY\SYSTEM pojawi się jako konto użytkownika, jako które będzie działać zadanie.

10. Zaznacz **pole wyboru Uruchom** niezależnie od tego, czy użytkownik jest zalogowany, i zaznacz **pole wyboru Uruchom z najwyższymi uprawnieniami** .

11. Przejdź do karty **Akcje** i kliknij pozycję **Nowy.** Upewnij się **, że w** polu Akcja jest wybrana opcja **Uruchom program.** Wprowadź nazwę i lokalizację udostępnionego pliku *WindowsDefenderATPOnboardingScript.cmd* .

12. Kliknij **przycisk OK** i zamknij wszystkie otwarte okna GPMC.

## <a name="offboard-devices-using-group-policy"></a>Urządzenia wye korzystające z zasady grupy
Ze względów bezpieczeństwa pakiet używany do odsyłania urządzeń wygasną po 30 dniach od daty jego pobrania. Pakiety wynoszące wygasłe wysłane na urządzenie zostaną odrzucone. Podczas pobierania pakietu wynegocjowego zostaniesz o nim powiadomiony(-a) o dacie wygaśnięcia pakietów, a także w nazwie pakietu.

> [!NOTE]
> Zasad wnoszeń i wynoszeń nie można wdrażać jednocześnie na tym samym urządzeniu, w przeciwnym razie spowoduje to nieprzewidywalne błędy.

1. Uzyskaj pakiet wywęszania z [Centrum zgodności firmy Microsoft](https://compliance.microsoft.com/compliancesettings/deviceonboarding).

2. W okienku nawigacji wybierz pozycję **Ustawienia** > **//Device onboardingOffboarding** > .

3. W polu **Metoda wdrażania** wybierz pozycję **Zasady grupy**.

4. Kliknij **pozycję Pobierz pakiet** i zapisz .zip pliku.

5. Wyodrębnianie zawartości pliku .zip do udostępnionej lokalizacji tylko do odczytu, do której dostęp jest możliwy na urządzeniu. Plik powinien mieć nazwę *: DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

6. Otwórz [konsolę zasady grupy zarządzania](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC), kliknij prawym przyciskiem myszy obiekt zasady grupy obiekt (GPO), który chcesz skonfigurować, a następnie kliknij polecenie **Edytuj**.

7. W **oknie zasady grupy zarządzania** przejdź do opcji Konfiguracja komputera **,** Preferencje **, a** następnie **Ustawienia Panelu sterowania**.

8. Kliknij prawym przyciskiem myszy **pozycję Zaplanowane zadania**, wskaż pozycję **Nowe**, a następnie kliknij pozycję **Zadanie natychmiastowe**.

9. W **oknie** Zadanie, które zostanie otwarte, przejdź do **karty** Ogólne. Wybierz lokalne konto użytkownika SYSTEMU (BUILTIN\SYSTEM) w **obszarze Opcje zabezpieczeń**.

10. Zaznacz **pole wyboru Uruchom** niezależnie od tego, czy użytkownik jest zalogowany, i zaznacz **pole wyboru Uruchom z najwyższymi** uprawnieniami.

11. Przejdź do karty **Akcje** i kliknij pozycję **Nowy...**. Upewnij się **, że w** polu Akcja jest wybrana opcja **Uruchom program.** Wprowadź nazwę i lokalizację udostępnionego  *pliku DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd* .

12. Kliknij **przycisk OK** i zamknij wszystkie otwarte okna GPMC.

> [!IMPORTANT]
> Wynosze powoduje, że urządzenie przestaje wysyłać dane czujnika do portalu, ale dane z urządzenia.


## <a name="monitor-device-configuration"></a>Monitorowanie konfiguracji urządzenia
Dzięki zasady grupy nie ma opcji monitorowania wdrażania zasad na urządzeniach. Monitorowanie można monitorować bezpośrednio w portalu lub przy użyciu różnych narzędzi wdrożeniowych.

## <a name="monitor-devices-using-the-portal"></a>Monitorowanie urządzeń za pomocą portalu
1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a>.
2. Kliknij **listę Urządzenia** .
3. Sprawdź, czy urządzenia są wyświetlane.

> [!NOTE]
> Może mi potrwać kilka dni, aby urządzenia zaczynały być wyświetlane na **liście Urządzenia**. Obejmuje to czas, przez który zasady mają być rozpowszechniane na urządzeniu, czas, który zajmuje zanim użytkownik się zaloguje, oraz czas, przez który punkt końcowy ma rozpocząć raportowanie.


## <a name="related-topics"></a>Tematy pokrewne
- [Urządzenia Windows 10 i Windows 11 urządzeń używających Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Dołączanie Windows 10 i Windows 11 urządzeń za pomocą narzędzi do zarządzania urządzeniami przenośnymi](device-onboarding-mdm.md)
- [Dołączanie Windows 10 i Windows 11 urządzeń przy użyciu skryptu lokalnego](device-onboarding-script.md)
- [Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI, Non-persistent Virtual Desktop Infrastructure)](device-onboarding-vdi.md)
- [Uruchamianie testu wykrywania na nowo w urządzeniu z uruchomionym programem Microsoft Defender dla urządzeń z punktami końcowymi](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Rozwiązywanie problemów z dołączaniem do zaawansowanej ochrony przed zagrożeniami w u programie Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)