---
title: Dołączanie Windows przy użyciu skryptu lokalnego
description: Użyj skryptu lokalnego, aby wdrożyć pakiet konfiguracji na urządzeniach, aby włączyć dołączanie urządzeń do usługi.
keywords: konfigurowanie urządzeń przy użyciu skryptu lokalnego, zarządzanie urządzeniami, konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender urządzenia
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1ea1661a89585d46aa5fc234f6f88be66512c1be
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468704"
---
# <a name="onboard-windows-devices-using-a-local-script"></a>Dołączanie Windows przy użyciu skryptu lokalnego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

Możesz także ręcznie włączyć poszczególne urządzenia do programu Defender for Endpoint. Warto to zrobić w pierwszej kolejności podczas testowania usługi przed zatwierdzeniem do korzystania ze wszystkich urządzeń w Twojej sieci.

> [!IMPORTANT]
> Ten skrypt został zoptymalizowany pod kątem używania na maksymalnie dziesięciu urządzeniach.
> Lokalne skrypty to specjalna metoda dołączania do oceniania Ochrona punktu końcowego w usłudze Microsoft Defender.
> Częstotliwość raportowania danych jest ustawiana wyżej niż w przypadku innych metod dołączania przy dołączaniu przy użyciu skryptu lokalnego.
> To ustawienie jest używane na potrzeby oceny i nie jest zwykle używane we wdrożeniach produkcyjnych. Z tego powodu istnieją obawy dotyczące wpływu na ochronę środowiska, dlatego zalecamy ograniczenie liczby wdrożeń korzystających z skryptów lokalnych do dziesięciu.
> Jeśli wdrażasz w środowisku produkcyjnym w sposób opisany wcześniej, użyj innych [](configure-endpoints.md) opcji wdrożenia, takich jak zasady grupy lub Microsoft Endpoint Configuration Manager.

Zapoznaj się z [plikiem PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.pdf) [Visio](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.vsdx) aby zobaczyć różne ścieżki wdrożenia programu Defender dla punktu końcowego. 

## <a name="onboard-devices"></a>Dołączanie urządzeń 

1.  Otwórz plik konfiguracji GP .zip pliku (*WindowsDefenderATPOnboardingPackage.zip*), który został pobrany z kreatora dołączania usługi. Możesz również pobrać pakiet z <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender:</a>

    1. W okienku nawigacji wybierz pozycję **Ustawienia** >  **EndpointsDevice** >  **managementOnboarding** > .


Zapoznaj się z [plikiem PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) aby zobaczyć różne ścieżki wdrożenia programu Defender dla punktu końcowego.

1. Otwórz plik konfiguracji GP .zip pliku (*WindowsDefenderATPOnboardingPackage.zip*), który został pobrany z kreatora dołączania usługi. Możesz również pobrać pakiet z <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender:</a>
    1. W okienku nawigacji **wybierz pozycję Ustawienia** \> **Punkty końcowe** \> **Dołączanie** \> **urządzeń do zarządzania urządzeniami**.
    2. Wybierz Windows 10 lub Windows 11 jako system operacyjny.
    3. W polu **Metoda wdrażania** wybierz pozycję **Skrypt lokalny**.
    4. Kliknij **pozycję Pobierz pakiet** i zapisz .zip pliku.

2. Wyodrębnij zawartość pakietu konfiguracyjne do lokalizacji na urządzeniu, które chcesz wdobyć (na przykład do pulpitu). Plik powinien mieć nazwę *WindowsDefenderATPLocalOnboardingScript.cmd*.

3. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień na urządzeniu i uruchom skrypt:
   1. Przejdź do **przycisku Start** i wpisz **cmd**.
   2. Kliknij prawym przyciskiem myszy **pozycję Wiersz polecenia i** wybierz **pozycję Uruchom jako administrator**.

    :::image type="content" source="images/run-as-admin.png" alt-text="Okno z menu Start z poleceniami Uruchom jako administrator" lightbox="images/run-as-admin.png":::

4.  Wpisz lokalizację pliku skryptu. Jeśli plik został skopiowany na pulpit, wpisz: *%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd*

5.  Naciśnij klawisz **Enter** lub kliknij przycisk **OK**.

Aby uzyskać informacje na temat sposobu ręcznego sprawdzania, czy urządzenie jest zgodne, i poprawnie raportuje dane czujnika, zobacz Rozwiązywanie Ochrona punktu końcowego w usłudze Microsoft Defender problemów z [dołączaniem](troubleshoot-onboarding.md).

> [!TIP]
> Po włoceniu urządzenia możesz uruchomić test wykrywania w celu sprawdzenia, czy urządzenie jest prawidłowo podłączone do usługi. Aby uzyskać więcej informacji, [zobacz Uruchamianie testu wykrywania dla nowo dodanego Ochrona punktu końcowego w usłudze Microsoft Defender końcowego](run-detection-test.md).

## <a name="configure-sample-collection-settings"></a>Konfigurowanie ustawień kolekcji przykładowych

Dla każdego urządzenia możesz ustawić wartość konfiguracji, aby określić, czy próbki mogą być pobierane z urządzenia w przypadku złożenia żądania za pośrednictwem programu Microsoft 365 Defender w celu przesłania pliku do dogłębnej analizy.

Możesz ręcznie skonfigurować przykładowe ustawienie udostępniania na urządzeniu, używając programu *regedit* lub tworząc i uruchamiając *plik reg* .

Konfigurację można skonfigurować za pomocą następującego wpisu klucza rejestru:

```console
Path: "HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection"
Name: "AllowSampleCollection"
Value: 0 or 1
```

Gdzie nazwa jest typem D-WORD. Dopuszczalne wartości:

- 0 — nie zezwala na przykładowe udostępnianie z tego urządzenia
- 1. Umożliwia udostępnianie wszystkich typów plików z tego urządzenia

Wartość domyślna w przypadku, gdy klucz rejestru nie istnieje, to 1.

## <a name="run-a-detection-test-to-verify-onboarding"></a>Uruchamianie testu wykrywania w celu zweryfikowania do uruchomienia

Po włoceniu urządzenia możesz uruchomić test wykrywania w celu sprawdzenia, czy urządzenie jest prawidłowo podłączone do usługi. Aby uzyskać więcej informacji, [zobacz Uruchamianie testu](run-detection-test.md) wykrywania na nowo Ochrona punktu końcowego w usłudze Microsoft Defender urządzeniach.

## <a name="offboard-devices-using-a-local-script"></a>Urządzenia wye korzystające ze skryptu lokalnego

Ze względów bezpieczeństwa pakiet używany na urządzeniach offboardowych wygaśnie po 30 dniach od daty jego pobrania. Pakiety wynoszące wygasłe wysłane na urządzenie zostaną odrzucone. Podczas pobierania pakietu wynegocjowego zostaniesz o nim powiadomiony(-a) o dacie wygaśnięcia pakietów, a także w nazwie pakietu.

> [!NOTE]
> Zasad wnoszeń i wynoszeń nie można wdrażać jednocześnie na tym samym urządzeniu, w przeciwnym razie spowoduje to nieprzewidywalne błędy.

1. Pobierz pakiet wynos ze <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender:</a>
    1. W okienku nawigacji wybierz pozycję **Ustawienia** \> **Punkty końcowe** \> **Zarządzanie urządzeniami** \> **(Wyczyszczycie**).
    2. Wybierz Windows 10 lub Windows 11 jako system operacyjny.
    3. W polu **Metoda wdrażania** wybierz pozycję **Skrypt lokalny**.
    4. Kliknij **pozycję Pobierz pakiet** i zapisz .zip pliku.

2. Wyodrębnianie zawartości pliku .zip do udostępnionej lokalizacji tylko do odczytu, do której mogą uzyskiwać dostęp urządzenia. Plik powinien mieć nazwę *: WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

3. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień na urządzeniu i uruchom skrypt:
   1. Przejdź do **przycisku Start** i wpisz **cmd**.
   2. Kliknij prawym przyciskiem myszy **pozycję Wiersz polecenia i** wybierz **pozycję Uruchom jako administrator**.

      :::image type="content" source="images/run-as-admin.png" alt-text="Menu Windows menu Start z opcją Uruchom jako administrator" lightbox="images/run-as-admin.png":::

4. Wpisz lokalizację pliku skryptu. Jeśli plik został skopiowany na pulpit, wpisz: *%userprofile%\Desktop\WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*

5. Naciśnij klawisz **Enter** lub kliknij przycisk **OK**.

> [!IMPORTANT]
> Wynoszenie powoduje, że urządzenie przestaje wysyłać dane czujnika do portalu, ale dane z urządzenia, w tym odwołania do wszelkich posiadanych alertów, będą przechowywane przez maksymalnie 6 miesięcy.

## <a name="monitor-device-configuration"></a>Monitorowanie konfiguracji urządzenia

Możesz wykonać różne kroki weryfikacji opisane w [tece](troubleshoot-onboarding.md) Rozwiązywanie problemów z dołączaniem, aby sprawdzić, czy skrypt został pomyślnie ukończony i czy agent jest uruchomiony.

Monitorowanie można również monitorować bezpośrednio w portalu lub przy użyciu różnych narzędzi wdrożeniowych.

### <a name="monitor-devices-using-the-portal"></a>Monitorowanie urządzeń za pomocą portalu

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender witryny</a>.
2. Kliknij pozycję **Spis urządzeń**.
3. Sprawdź, czy urządzenia są wyświetlane.

## <a name="related-topics"></a>Tematy pokrewne
- [Na urządzeniach Windows przy użyciu aplikacji zasady grupy](configure-endpoints-gp.md)
- [Na urządzeniach Windows urządzeniach przy użyciu Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [Na urządzeniach Windows przenośnych za pomocą narzędzi mobilnych Zarządzanie urządzeniami urządzeniach przenośnych](configure-endpoints-mdm.md)
- [Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI)](configure-endpoints-vdi.md)
- [Uruchamianie testu wykrywania na nowo włodowym Ochrona punktu końcowego w usłudze Microsoft Defender urządzenia](run-detection-test.md)
- [Rozwiązywanie Ochrona punktu końcowego w usłudze Microsoft Defender problemów z dołączaniem](troubleshoot-onboarding.md)
