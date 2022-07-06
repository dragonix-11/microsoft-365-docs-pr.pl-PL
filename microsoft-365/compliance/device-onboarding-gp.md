---
title: Dołączanie urządzeń z systemami Windows 10 i Windows 11 za pomocą zasad grupy
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
description: Użyj zasady grupy, aby wdrożyć pakiet konfiguracji na urządzeniach Windows 10 i Windows 11, aby były dołączane do usługi.
ms.openlocfilehash: 6c8c70d1bfdf3de0bc3848069a22b8610d445e42
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623258"
---
# <a name="onboard-windows-10-devices-and-windows-11-using-group-policy"></a>Dołączanie urządzeń Windows 10 i Windows 11 przy użyciu zasady grupy 

**Dotyczy:**

- [Ochrona przed utratą danych punktu końcowego (DLP)](./endpoint-dlp-learn-about.md)
- [Zarządzanie ryzykiem wewnętrznym](insider-risk-management.md)
- Zasady grupy

> [!NOTE]
> Aby wdrożyć pakiet przy użyciu aktualizacji zasady grupy (GP), musisz być w systemie Windows Server 2008 R2 lub nowszym.

> W systemie Windows Server 2019 może być konieczne zastąpienie nt authority\well-known-system-account nt authority\system pliku XML, który tworzy preferencja zasady grupy.

## <a name="onboard-devices-using-group-policy"></a>Dołączanie urządzeń przy użyciu zasady grupy

1. Otwórz [Centrum zgodności](https://compliance.microsoft.com).

2. W okienku nawigacji wybierz pozycję **Ustawienia** > **Dołączanie urządzenia**.

3. W polu **Metoda wdrażania** wybierz pozycję **Zasady grupy**.

4. Kliknij **pozycję Pobierz pakiet** i zapisz plik .zip.

5. Wyodrębnij zawartość pliku .zip do udostępnionej lokalizacji tylko do odczytu, do których może uzyskiwać dostęp urządzenie. Powinien istnieć folder o nazwie *OptionalParamsPolicy* i plik *DeviceComplianceLocalOnboardingScript.cmd*.

6. Otwórz [konsolę zarządzania zasady grupy](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC), kliknij prawym przyciskiem myszy obiekt zasady grupy , który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

7. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera**, **preferencje**, a następnie **ustawienia panelu sterowania**.

8. Kliknij prawym przyciskiem myszy **pozycję Zaplanowane zadania**, wskaż pozycję **Nowe**, a następnie kliknij pozycję **Zadanie natychmiastowe (co najmniej system Windows 7).**

9. W **wyświetlonym oknie Zadanie** przejdź do karty **Ogólne** . W obszarze **Opcje zabezpieczeń** kliknij pozycję **Zmień użytkownika lub grupę** i wpisz SYSTEM, a następnie kliknij pozycję **Sprawdź nazwy** , a następnie **przycisk OK**. NT AUTHORITY\SYSTEM jest wyświetlany jako konto użytkownika, które będzie uruchamiane jako zadanie.

10. Wybierz pozycję **Uruchom, czy użytkownik jest zalogowany, czy nie** , i zaznacz pole wyboru **Uruchom z najwyższymi uprawnieniami** .

11. Przejdź do karty **Akcje** i kliknij pozycję **Nowy...** Upewnij się, że w polu **Akcja** wybrano **opcję Uruchom program**. Wprowadź nazwę pliku i lokalizację udostępnionego pliku *WindowsDefenderATPOnboardingScript.cmd* .

12. Kliknij **przycisk OK** i zamknij wszystkie otwarte okna kontrolera GPMC.

## <a name="offboard-devices-using-group-policy"></a>Odłączanie urządzeń przy użyciu zasady grupy
Ze względów bezpieczeństwa pakiet używany do odłączenia urządzeń wygaśnie 30 dni po pobraniu. Wygasłe pakiety odłączania wysyłane do urządzenia zostaną odrzucone. Podczas pobierania pakietu odłączania otrzymasz powiadomienie o dacie wygaśnięcia pakietów i zostanie on również uwzględniony w nazwie pakietu.

> [!NOTE]
> Zasady dołączania i odłączania nie mogą być wdrażane na tym samym urządzeniu w tym samym czasie, w przeciwnym razie spowoduje to nieprzewidywalne kolizje.

1. Pobierz pakiet odłączania z [portal zgodności Microsoft Purview](https://compliance.microsoft.com/compliancesettings/deviceonboarding).

2. W okienku nawigacji wybierz pozycję **Ustawienia** > **//Odłączanie dołączania** >  urządzenia.

3. W polu **Metoda wdrażania** wybierz pozycję **Zasady grupy**.

4. Kliknij **pozycję Pobierz pakiet** i zapisz plik .zip.

5. Wyodrębnij zawartość pliku .zip do udostępnionej lokalizacji tylko do odczytu, do których może uzyskiwać dostęp urządzenie. Powinien istnieć plik o nazwie *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

6. Otwórz [konsolę zarządzania zasady grupy](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC), kliknij prawym przyciskiem myszy obiekt zasady grupy , który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

7. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera,** **preferencje**, a następnie **ustawienia panelu sterowania**.

8. Kliknij prawym przyciskiem myszy **pozycję Zaplanowane zadania**, wskaż pozycję **Nowe**, a następnie kliknij pozycję **Natychmiastowe zadanie**.

9. W **wyświetlonym oknie Zadanie** przejdź do karty **Ogólne** . Wybierz lokalne konto użytkownika SYSTEMU (BUILTIN\SYSTEM) w obszarze **Opcje zabezpieczeń**.

10. Wybierz pozycję **Uruchom, czy użytkownik jest zalogowany, czy nie** , i zaznacz pole wyboru **Uruchom z najwyższymi uprawnieniami** .

11. Przejdź do karty **Akcje** i kliknij pozycję **Nowy...**. Upewnij się, że w polu **Akcja** wybrano **opcję Uruchom program**. Wprowadź nazwę pliku i lokalizację udostępnionego pliku  *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd* .

12. Kliknij **przycisk OK** i zamknij wszystkie otwarte okna kontrolera GPMC.

> [!IMPORTANT]
> Odłączanie powoduje, że urządzenie przestaje wysyłać dane czujnika do portalu, ale dane z urządzenia.


## <a name="monitor-device-configuration"></a>Monitorowanie konfiguracji urządzenia
W przypadku zasady grupy nie można monitorować wdrażania zasad na urządzeniach. Monitorowanie można przeprowadzić bezpośrednio w portalu lub przy użyciu różnych narzędzi wdrażania.

## <a name="monitor-devices-using-the-portal"></a>Monitorowanie urządzeń przy użyciu portalu
1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portal zgodności Microsoft Purview</a>.
2. Kliknij pozycję **Urządzenia** , aby wyświetlić listę.
3. Sprawdź, czy urządzenia są wyświetlane.

> [!NOTE]
> Na **liście Urządzenia** może upłynąć kilka dni. Obejmuje to czas dystrybucji zasad na urządzeniu, czas potrzebny na zalogowanie użytkownika oraz czas potrzebny na rozpoczęcie raportowania przez punkt końcowy.


## <a name="related-topics"></a>Tematy pokrewne
- [Dołączanie urządzeń Windows 10 i Windows 11 przy użyciu programu Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Dołączanie urządzeń z systemami Windows 10 i Windows 11 przy użyciu narzędzi do zarządzania urządzeniami przenośnymi](device-onboarding-mdm.md)
- [Dołączanie urządzeń z systemami Windows 10 i Windows 11 przy użyciu skryptu lokalnego](device-onboarding-script.md)
- [Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI)](device-onboarding-vdi.md)
- [Uruchamianie testu wykrywania na nowo dołączonych urządzeniach Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Rozwiązywanie problemów z dołączaniem zaawansowanej ochrony przed zagrożeniami w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
