---
title: Na urządzeniach Windows przy użyciu Menedżer konfiguracji
description: Użyj Menedżer konfiguracji, aby wdrożyć pakiet konfiguracji na urządzeniach, aby były one dołączane do usługi Defender for Endpoint.
keywords: urządzenia onboard przy użyciu programu sccm, zarządzanie urządzeniami, konfigurowanie programu Microsoft Defender dla urządzeń z punktami końcowymi
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
ms.date: 09/22/2021
ms.technology: mde
ms.openlocfilehash: b506cf15e2d08568633533ba29af5e2f809c2134
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998104"
---
# <a name="onboard-windows-devices-using-configuration-manager"></a>Na urządzeniach Windows przy użyciu Menedżer konfiguracji

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Endpoint Configuration Manager bieżąca gałąź
- System Center 2012 R2 Menedżer konfiguracji

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointssccm-abovefoldlink)


Za pomocą programu Menedżer konfiguracji punktów końcowych można dodać do usługi Microsoft Defender for Endpoint. 

Dostępnych jest kilka opcji, których można używać do korzystania z urządzeń Menedżer konfiguracji:
- [Urządzenia wyniesiene przy użyciu System Center Configuration Manager](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection)
- [Dołączanie dzierżawy](/mem/configmgr/tenant-attach/)



Na Windows Server 2012 R2 i Windows Server 2016 — po wykonaniu kroków dołączania musisz skonfigurować i zaktualizować [System Center Endpoint Protection klientów](onboard-downlevel.md#configure-and-update-system-center-endpoint-protection-clients).

> [!NOTE]
> Program Defender for Endpoint nie obsługuje dołączania w fazie ["Out-of-Box Experience" (OOBE](https://answers.microsoft.com/windows/wiki/windows_10/how-to-complete-the-windows-10-out-of-box/47e3f943-f000-45e3-8c5c-9d85a1a0cf87) ). Upewnij się, że użytkownicy zakończyli działanie programu OOBE po Windows instalacji lub uaktualnieniu.
>
> W aplikacji mobilnej można utworzyć regułę wykrywania w celu ciągłego sprawdzania Menedżer konfiguracji czy urządzenie zostało w nim włoone. Aplikacja to inny typ obiektu niż pakiet i program.
> Jeśli urządzenie nie zostało jeszcze naniesone (ze względu na oczekiwanie na ukończenie zadania WOOBE lub z dowolnego innego powodu), program Menedżer konfiguracji spróbuje ponownie wniesieć urządzenie, dopóki reguła nie wykryje zmiany statusu.
>
> Takie działanie można osiągnąć, tworząc sprawdzanie reguły wykrywania, jeśli wartość rejestru "OnboardingState" (wartość typu REG_DWORD) = 1.
> Ta wartość rejestru znajduje się w folderze "HKLM\SOFTWARE\Microsoft\Windows Threat Protection\Status".
Aby uzyskać więcej informacji, zobacz Konfigurowanie metod wykrywania [w programie System Center 2012 R2 Menedżer konfiguracji](/previous-versions/system-center/system-center-2012-R2/gg682159\(v=technet.10\)#step-4-configure-detection-methods-to-indicate-the-presence-of-the-deployment-type).

### <a name="configure-sample-collection-settings"></a>Konfigurowanie ustawień kolekcji przykładowych

Dla każdego urządzenia możesz ustawić wartość konfiguracji, aby określić, czy próbki mogą być pobierane z urządzenia w przypadku złożenia żądania za pośrednictwem programu Microsoft 365 Defender w celu przesłania pliku do dogłębnej analizy.

> [!NOTE]
> Te ustawienia konfiguracji są zwykle wykonywane za pośrednictwem Menedżer konfiguracji.

Możesz ustawić regułę zgodności dla elementu konfiguracji w programie Menedżer konfiguracji, aby zmienić przykładowe ustawienie udostępniania na urządzeniu.

Ta reguła powinna dotyczyć  elementu konfiguracji reguły zgodności, który ustawia wartość klucza rejestru na docelowych urządzeniach w celu upewninia się, że jest to skarga.

Konfigurację można skonfigurować za pomocą następującego wpisu klucza rejestru:

```text
Path: "HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection"
Name: "AllowSampleCollection"
Value: 0 or 1
```

Gdzie typ klucza to D-WORD. Dopuszczalne wartości:

- 0. Nie zezwala na przykładowe udostępnianie z tego urządzenia
- 1. Umożliwia udostępnianie wszystkich typów plików z tego urządzenia

Wartość domyślna w przypadku, gdy klucz rejestru nie istnieje, to 1.

Aby uzyskać więcej informacji na System Center Configuration Manager zgodności, zobacz Wprowadzenie do ustawień zgodności w [programie System Center 2012 R2 Menedżer konfiguracji](/previous-versions/system-center/system-center-2012-R2/gg682139\(v=technet.10\)).

## <a name="other-recommended-configuration-settings"></a>Inne zalecane ustawienia konfiguracji

Po dojechania urządzeń do usługi ważne jest, aby korzystać z zawartych w nich możliwości ochrony przed zagrożeniami, włączając je z następującymi zalecanymi ustawieniami konfiguracji.

### <a name="device-collection-configuration"></a>Konfiguracja kolekcji urządzeń

Jeśli korzystasz z programu Endpoint Menedżer konfiguracji w wersji 2002 lub nowszej, możesz poszerzyć wdrożenie tak, aby uwzględniało serwery lub klientów  down-level.

### <a name="next-generation-protection-configuration"></a>Konfiguracja ochrony następnej generacji

Zalecane są następujące ustawienia konfiguracji:

#### <a name="scan"></a>Skanowanie

- Skanowanie wymiennych urządzeń magazynujących, takich jak dyski USB: Tak

#### <a name="real-time-protection"></a>Ochrona w czasie rzeczywistym

- Włączanie monitorowania zachowania: Tak
- Włączanie ochrony przed potencjalnie niechcianymi aplikacjami podczas pobierania i przed instalacją: Tak

#### <a name="cloud-protection-service"></a>Usługa ochrony w chmurze

- Typ członkostwa w usłudze Cloud Protection: Członkostwo zaawansowane

#### <a name="attack-surface-reduction"></a>Zmniejszenie powierzchni ataków

Skonfiguruj wszystkie dostępne reguły do inspekcji.

> [!NOTE]
> Zablokowanie tych działań może przerwać legalne procesy biznesowe. Najlepszym rozwiązaniem jest ustawienie wszystkich funkcji inspekcji, określenie tych, które można bezpiecznie włączyć, a następnie włączenie tych ustawień dla punktów końcowych, które nie mają wykrywanie wyników fałszywie dodatnich.

#### <a name="network-protection"></a>Ochrona sieci

Przed włączeniem ochrony sieci w trybie inspekcji lub blokowania upewnij się, że zainstalowano aktualizację platformy ochrony przed złośliwym oprogramowaniem, którą można uzyskać na [stronie pomocy technicznej](https://support.microsoft.com/help/4560203/windows-defender-anti-malware-platform-binaries-are-missing).

#### <a name="controlled-folder-access"></a>Kontrolowany dostęp do folderu

Włącz funkcję w trybie inspekcji przez co najmniej 30 dni. Po upływie tego okresu przejrzyj wykrywanie i utwórz listę aplikacji, które mogą pisać w chronionych katalogach.

Aby uzyskać więcej informacji, zobacz [Szacowanie kontrolowanego dostępu do folderu](evaluate-controlled-folder-access.md).

## <a name="run-a-detection-test-to-verify-onboarding"></a>Uruchamianie testu wykrywania w celu zweryfikowania do uruchomienia

Po włoceniu urządzenia możesz uruchomić test wykrywania w celu sprawdzenia, czy urządzenie jest prawidłowo podłączone do usługi. Aby uzyskać więcej informacji, zobacz Uruchamianie testu wykrywania na nowo włodarzony [program Microsoft Defender dla urządzenia końcowego](run-detection-test.md).

## <a name="offboard-devices-using-configuration-manager"></a>Urządzenia wye korzystające z Menedżer konfiguracji

Ze względów bezpieczeństwa pakiet używany na urządzeniach offboardowych wygaśnie po 30 dniach od daty jego pobrania. Pakiety wynoszące wygasłe wysłane na urządzenie zostaną odrzucone. Podczas pobierania pakietu wynegocjowego będziesz o nich powiadamiać o dacie wygaśnięcia pakietów oraz o tym, że zostanie on także uwzględniony w nazwie pakietu.

> [!NOTE]
> Zasad wnoszeń i wynoszeń nie można wdrażać jednocześnie na tym samym urządzeniu, w przeciwnym razie spowoduje to nieprzewidywalne błędy.

### <a name="offboard-devices-using-microsoft-endpoint-manager-current-branch"></a>Urządzenia wye korzystające Microsoft Endpoint Manager bieżącej gałęzi

Jeśli używasz bieżącej Microsoft Endpoint Manager, [zobacz Tworzenie pliku konfiguracji wye dołączania](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#create-an-offboarding-configuration-file).

### <a name="offboard-devices-using-system-center-2012-r2-configuration-manager"></a>Urządzenia przenośne korzystające z System Center 2012 R2 Menedżer konfiguracji

1. Pobierz pakiet wynos ze <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender:</a>
    1. W okienku nawigacji **wybierz pozycję Ustawienia** \> **Punkty końcowe** \> **Zarządzanie urządzeniami** \>**: wyczyszczycie**.  
    1. Wybierz Windows 10 lub Windows 11 jako system operacyjny.
    1. W polu **Metoda wdrażania** wybierz System Center Configuration Manager **2012-2012 R2/1511/1602**.
    1. Wybierz **pozycję Pobierz pakiet** i zapisz .zip pliku.

2. Wyodrębnianie zawartości pliku .zip do udostępnionej lokalizacji tylko do odczytu, do której dostęp mogą uzyskać administratorzy sieci, którzy wdrożyą pakiet. Plik powinien mieć nazwę *: WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

3. Wdeksuj pakiet, korzystając z procedury opisanej w artykule pakiety i programy [System Center 2012 R2 Menedżer konfiguracji](/previous-versions/system-center/system-center-2012-R2/gg699369\(v=technet.10\)) pakietu.

   Wybierz wstępnie zdefiniowaną kolekcję urządzeń, w których chcesz wdrożyć pakiet.

> [!IMPORTANT]
> Wynoszenie powoduje, że urządzenie przestaje wysyłać dane czujnika do portalu, ale dane z urządzenia, w tym odwołania do wszelkich posiadanych alertów, będą przechowywane przez maksymalnie 6 miesięcy.

## <a name="monitor-device-configuration"></a>Monitorowanie konfiguracji urządzenia

Jeśli korzystasz z bieżącej Microsoft Endpoint Manager, użyj wbudowanego pulpitu nawigacyjnego programu Defender for Endpoint w konsoli Menedżer konfiguracji sieci Web. Aby uzyskać więcej informacji, zobacz [Defender for Endpoint — Monitor](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#monitor).

Jeśli używasz programu System Center 2012 R2 Menedżer konfiguracji, monitorowanie składa się z dwóch części:

1. Potwierdzanie, że pakiet konfiguracji został poprawnie wdrożony i działa (lub został pomyślnie uruchomiony) na urządzeniach w sieci.

2. Sprawdzanie, czy urządzenia są zgodne z usługą Defender for Endpoint (dzięki temu urządzenie może ukończyć proces dołączania i może nadal raportować dane do usługi).

### <a name="confirm-the-configuration-package-has-been-correctly-deployed"></a>Upewnij się, że pakiet konfiguracji został poprawnie wdrożony

1. W konsoli Menedżer konfiguracji nawigacji kliknij pozycję **Monitorowanie** w dolnej części okienka nawigacji.

2. Wybierz **pozycję Omówienie** , a **następnie Pozycję Wdrożenia**.

3. Wybierz wdrożenie z nazwą pakietu.

4. Przejrzyj wskaźniki stanu w obszarze **Statystyka ukończenia** i **Stan zawartości**.

    W przypadku wdrożeń nieudanych (urządzeń z błędem **, wymagań** lub stanu niepowodzeniem **) może** być konieczne rozwiązanie problemów z urządzeniami. Aby uzyskać więcej informacji, zobacz Rozwiązywanie [problemów z dołączaniem do programu Microsoft Defender dla punktów końcowych](troubleshoot-onboarding.md).

    ![Menedżer konfiguracji pokazuje pomyślne wdrożenie bez błędów.](images/sccm-deployment.png)

### <a name="check-that-the-devices-are-compliant-with-the-microsoft-defender-for-endpoint-service"></a>Sprawdzanie, czy urządzenia są zgodne z usługą Microsoft Defender for Endpoint

Możesz ustawić regułę zgodności dla elementu konfiguracji w programie System Center 2012 R2 Menedżer konfiguracji monitorowanie wdrożenia.

Ta reguła powinna *być elementem* konfiguracji reguły zgodności, który nie naprawia działania, który monitoruje wartość klucza rejestru na urządzeniach docelowych.

Monitoruj następujący wpis klucza rejestru:

```console
Path: "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status"
Name: "OnboardingState"
Value: "1"
```

Aby uzyskać więcej informacji, [zobacz Wprowadzenie do ustawień zgodności w programie System Center 2012 R2 Menedżer konfiguracji](/previous-versions/system-center/system-center-2012-R2/gg682139\(v=technet.10\)).

## <a name="related-topics"></a>Tematy pokrewne
- [Na urządzeniach Windows przy użyciu aplikacji zasady grupy](configure-endpoints-gp.md)
- [Na urządzeniach Windows urządzeniach przenośnych za pomocą narzędzi do zarządzania urządzeniami przenośnymi](configure-endpoints-mdm.md)
- [Dołączanie Windows przy użyciu skryptu lokalnego](configure-endpoints-script.md)
- [Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI, Non-persistent Virtual Desktop Infrastructure)](configure-endpoints-vdi.md)
- [Uruchamianie testu wykrywania na nowo w urządzeniu z uruchomionym programem Microsoft Defender dla punktu końcowego](run-detection-test.md)
- [Rozwiązywanie problemów z dołączaniem do programu Microsoft Defender for Endpoint](troubleshoot-onboarding.md)
