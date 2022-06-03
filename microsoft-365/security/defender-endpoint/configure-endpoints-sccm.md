---
title: Dołączanie urządzeń Windows przy użyciu Configuration Manager
description: Użyj Configuration Manager, aby wdrożyć pakiet konfiguracji na urządzeniach, aby były one dołączane do usługi Defender for Endpoint.
keywords: dołączanie urządzeń przy użyciu programu sccm, zarządzania urządzeniami, konfigurowania urządzeń Ochrona punktu końcowego w usłudze Microsoft Defender
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
ms.openlocfilehash: d60d01bd2a77d992110f85967196390f3dceae3d
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873715"
---
# <a name="onboard-windows-devices-using-configuration-manager"></a>Dołączanie urządzeń Windows przy użyciu Configuration Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Endpoint Configuration Manager bieżąca gałąź
- System Center 2012 R2 Configuration Manager

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointssccm-abovefoldlink)


Za pomocą Configuration Manager można dołączyć punkty końcowe do usługi Ochrona punktu końcowego w usłudze Microsoft Defender. 

Istnieje kilka opcji dołączania urządzeń przy użyciu Configuration Manager:
- [Dołączanie urządzeń przy użyciu System Center Configuration Manager](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection)
- [Dołączanie dzierżawy](/mem/configmgr/tenant-attach/)



W przypadku Windows Server 2012 R2 i Windows Server 2016 — po wykonaniu kroków dołączania należy [skonfigurować i zaktualizować klientów System Center Endpoint Protection](onboard-downlevel.md#configure-and-update-system-center-endpoint-protection-clients).

> [!NOTE]
> Usługa Defender for Endpoint nie obsługuje dołączania w fazie [OOBE (Out-Of-Box Experience).](/windows-hardware/test/assessments/out-of-box-experience) Upewnij się, że użytkownicy ukończyli program OOBE po uruchomieniu Windows instalacji lub uaktualnienia.
>
> Należy pamiętać, że istnieje możliwość utworzenia reguły wykrywania w aplikacji Configuration Manager w celu ciągłego sprawdzania, czy urządzenie zostało dołączone. Aplikacja jest innym typem obiektu niż pakiet i program.
> Jeśli urządzenie nie zostało jeszcze dołączone (z powodu oczekującego ukończenia OOBE lub z jakiejkolwiek innej przyczyny), Configuration Manager spróbuje ponownie dołączyć urządzenie, dopóki reguła nie wykryje zmiany stanu.
>
> To zachowanie można osiągnąć, tworząc regułę wykrywania, sprawdzając, czy wartość rejestru "OnboardingState" (typu REG_DWORD) = 1.
> Ta wartość rejestru znajduje się w obszarze "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status".
Aby uzyskać więcej informacji, zobacz [Konfigurowanie metod wykrywania w System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682159\(v=technet.10\)#step-4-configure-detection-methods-to-indicate-the-presence-of-the-deployment-type).

### <a name="configure-sample-collection-settings"></a>Konfigurowanie ustawień przykładowej kolekcji

Dla każdego urządzenia można ustawić wartość konfiguracji, aby określić, czy przykłady mogą być zbierane z urządzenia podczas przesyłania żądania za pośrednictwem Microsoft 365 Defender w celu przesłania pliku do głębokiej analizy.

> [!NOTE]
> Te ustawienia konfiguracji są zwykle wykonywane za pośrednictwem Configuration Manager.

Możesz ustawić regułę zgodności dla elementu konfiguracji w Configuration Manager, aby zmienić ustawienie przykładowego udziału na urządzeniu.

Ta reguła powinna być elementem konfiguracji reguły zgodności *korygującej* , który ustawia wartość klucza rejestru na urządzeniach docelowych, aby upewnić się, że są reklamowane.

Konfiguracja jest ustawiana za pomocą następującego wpisu klucza rejestru:

```text
Path: "HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection"
Name: "AllowSampleCollection"
Value: 0 or 1
```

Gdzie typ klucza to D-WORD. Możliwe wartości to:

- 0: Nie zezwala na udostępnianie przykładów z tego urządzenia
- 1: Umożliwia udostępnianie wszystkich typów plików z tego urządzenia

Wartość domyślna w przypadku, gdy klucz rejestru nie istnieje, to 1.

Aby uzyskać więcej informacji na temat zgodności System Center Configuration Manager, zobacz [Wprowadzenie do ustawień zgodności w System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682139\(v=technet.10\)).

## <a name="other-recommended-configuration-settings"></a>Inne zalecane ustawienia konfiguracji

Po dołączeniu urządzeń do usługi ważne jest, aby skorzystać z dołączonych możliwości ochrony przed zagrożeniami, włączając je przy użyciu następujących zalecanych ustawień konfiguracji.

### <a name="device-collection-configuration"></a>Konfiguracja kolekcji urządzeń

Jeśli używasz programu Endpoint Configuration Manager w wersji 2002 lub nowszej, możesz rozszerzyć wdrożenie o serwery lub klientów niższego poziomu.

### <a name="next-generation-protection-configuration"></a>Konfiguracja ochrony następnej generacji

Zalecane są następujące ustawienia konfiguracji:

#### <a name="scan"></a>Skanowania

- Skanuj wymienne urządzenia magazynujące, takie jak dyski USB: Tak

#### <a name="real-time-protection"></a>Ochrona w czasie rzeczywistym

- Włącz monitorowanie behawioralne: Tak
- Włącz ochronę przed potencjalnie niepożądanymi aplikacjami podczas pobierania i przed instalacją: Tak

#### <a name="cloud-protection-service"></a>Usługa Cloud Protection

- Typ członkostwa w usłudze Cloud Protection: członkostwo zaawansowane

#### <a name="attack-surface-reduction"></a>Zmniejszanie obszaru podatnego na ataki

Skonfiguruj wszystkie dostępne reguły na wartość Inspekcja.

> [!NOTE]
> Zablokowanie tych działań może przerwać uzasadnione procesy biznesowe. Najlepszym podejściem jest ustawienie wszystkich elementów do inspekcji, określenie, które z nich można bezpiecznie włączyć, a następnie włączenie tych ustawień w punktach końcowych, które nie mają wykrywania fałszywie dodatniego.

#### <a name="network-protection"></a>Ochrona sieci

Przed włączeniem ochrony sieci w trybie inspekcji lub bloku upewnij się, że zainstalowano aktualizację platformy ochrony przed złośliwym kodem, którą można uzyskać na [stronie pomocy technicznej](https://support.microsoft.com/help/4560203/windows-defender-anti-malware-platform-binaries-are-missing).

#### <a name="controlled-folder-access"></a>Kontrolowany dostęp do folderu

Włącz funkcję w trybie inspekcji przez co najmniej 30 dni. Po tym okresie przejrzyj wykrycia i utwórz listę aplikacji, które mogą zapisywać w chronionych katalogach.

Aby uzyskać więcej informacji, zobacz [Evaluate controlled folder access (Ocena kontrolowanego dostępu do folderów).](evaluate-controlled-folder-access.md)

## <a name="run-a-detection-test-to-verify-onboarding"></a>Uruchamianie testu wykrywania w celu zweryfikowania dołączania

Po dołączeniu urządzenia można uruchomić test wykrywania, aby sprawdzić, czy urządzenie jest prawidłowo dołączone do usługi. Aby uzyskać więcej informacji, zobacz [Uruchamianie testu wykrywania na nowo dołączonym urządzeniu Ochrona punktu końcowego w usłudze Microsoft Defender](run-detection-test.md).

## <a name="offboard-devices-using-configuration-manager"></a>Odłączanie urządzeń przy użyciu Configuration Manager

Ze względów bezpieczeństwa pakiet używany do odłączenia urządzeń wygaśnie 30 dni po pobraniu. Wygasłe pakiety odłączania wysyłane do urządzenia zostaną odrzucone. Podczas pobierania pakietu odłączania otrzymasz powiadomienie o dacie wygaśnięcia pakietów i zostanie on również uwzględniony w nazwie pakietu.

> [!NOTE]
> Zasady dołączania i odłączania nie mogą być wdrażane na tym samym urządzeniu w tym samym czasie, w przeciwnym razie spowoduje to nieprzewidywalne kolizje.

### <a name="offboard-devices-using-microsoft-endpoint-manager-current-branch"></a>Odłączanie urządzeń przy użyciu Microsoft Endpoint Manager bieżącej gałęzi

Jeśli używasz Microsoft Endpoint Manager bieżącej gałęzi, zobacz [Tworzenie pliku konfiguracji odłączania](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#create-an-offboarding-configuration-file).

### <a name="offboard-devices-using-system-center-2012-r2-configuration-manager"></a>Odłączanie urządzeń przy użyciu Configuration Manager System Center 2012 R2

1. Pobierz pakiet odłączania z <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>:
    1. W okienku nawigacji wybierz pozycję **Ustawienia** \> **Punkty końcowe** \> **Odłączanie zarządzania urządzeniami**\>.  
    1. Wybierz Windows 10 lub Windows 11 jako system operacyjny.
    1. W polu **Metoda wdrażania** wybierz pozycję **System Center Configuration Manager 2012/2012 R2/1511/1602**.
    1. Wybierz pozycję **Pobierz pakiet** i zapisz plik .zip.

2. Wyodrębnij zawartość pliku .zip do udostępnionej lokalizacji tylko do odczytu, do których mogą uzyskać dostęp administratorzy sieci, którzy wdrożą pakiet. Powinien istnieć plik o nazwie *WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

3. Wdróż pakiet, wykonując kroki opisane [w artykule Packages and Programs in System Center 2012 R2 Configuration Manager article (Pakiety i programy) w artykule Configuration Manager 2012 R2](/previous-versions/system-center/system-center-2012-R2/gg699369\(v=technet.10\)).

   Wybierz wstępnie zdefiniowaną kolekcję urządzeń do wdrożenia pakietu.

> [!IMPORTANT]
> Odłączanie powoduje, że urządzenie przestaje wysyłać dane czujnika do portalu, ale dane z urządzenia, w tym odwołanie do wszelkich alertów, które miał, zostaną zachowane przez maksymalnie 6 miesięcy.

## <a name="monitor-device-configuration"></a>Monitorowanie konfiguracji urządzenia

Jeśli używasz Microsoft Endpoint Manager bieżącej gałęzi, użyj wbudowanego pulpitu nawigacyjnego usługi Defender for Endpoint w konsoli Configuration Manager. Aby uzyskać więcej informacji, zobacz [Defender for Endpoint — Monitor](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#monitor).

Jeśli używasz Configuration Manager System Center 2012 R2, monitorowanie składa się z dwóch części:

1. Potwierdzanie, że pakiet konfiguracji został poprawnie wdrożony i jest uruchomiony (lub został pomyślnie uruchomiony) na urządzeniach w sieci.

2. Sprawdzanie, czy urządzenia są zgodne z usługą Defender for Endpoint (dzięki temu urządzenie może ukończyć proces dołączania i nadal raportować dane do usługi).

### <a name="confirm-the-configuration-package-has-been-correctly-deployed"></a>Upewnij się, że pakiet konfiguracji został poprawnie wdrożony

1. W konsoli Configuration Manager kliknij pozycję **Monitorowanie** w dolnej części okienka nawigacji.

2. Wybierz pozycję **Przegląd** , a następnie **pozycję Wdrożenia**.

3. Wybierz wdrożenie z nazwą pakietu.

4. Przejrzyj wskaźniki stanu w obszarze **Statystyki ukończenia** i **Stan zawartości**.

    Jeśli istnieją wdrożenia zakończone niepowodzeniem (urządzenia z **błędem**, **wymaganiami, które nie zostały spełnione** lub **stanem Niepowodzenie**), może być konieczne rozwiązanie problemów z urządzeniami. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z dołączaniem Ochrona punktu końcowego w usłudze Microsoft Defender](troubleshoot-onboarding.md).

    :::image type="content" source="images/sccm-deployment.png" alt-text="Configuration Manager pokazujący pomyślne wdrożenie bez błędów" lightbox="images/sccm-deployment.png":::

### <a name="check-that-the-devices-are-compliant-with-the-microsoft-defender-for-endpoint-service"></a>Sprawdź, czy urządzenia są zgodne z usługą Ochrona punktu końcowego w usłudze Microsoft Defender

Aby monitorować wdrożenie, można ustawić regułę zgodności dla elementu konfiguracji w System Center 2012 R2 Configuration Manager.

Ta reguła powinna być elementem konfiguracji reguły zgodności *nie korygującej* , który monitoruje wartość klucza rejestru na urządzeniach docelowych.

Monitoruj następujący wpis klucza rejestru:

```console
Path: "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status"
Name: "OnboardingState"
Value: "1"
```

Aby uzyskać więcej informacji, zobacz [Wprowadzenie do ustawień zgodności w System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682139\(v=technet.10\)).

## <a name="related-topics"></a>Tematy pokrewne
- [Dołącz urządzenia z systemem Windows przy użyciu zasad grupy](configure-endpoints-gp.md)
- [Dołącz urządzenia z systemem Windows przy użyciu narzędzi do zarządzania urządzeniami przenośnymi](configure-endpoints-mdm.md)
- [Dołącz urządzenia z systemem Windows przy użyciu skryptu lokalnego](configure-endpoints-script.md)
- [Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI)](configure-endpoints-vdi.md)
- [Uruchamianie testu wykrywania na nowo dołączonym urządzeniu Ochrona punktu końcowego w usłudze Microsoft Defender](run-detection-test.md)
- [Rozwiązywanie problemów z dołączaniem Ochrona punktu końcowego w usłudze Microsoft Defender](troubleshoot-onboarding.md)
