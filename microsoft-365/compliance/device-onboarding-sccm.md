---
title: Dołączanie urządzeń Windows 10 i Windows 11 przy użyciu Configuration Manager
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Użyj Configuration Manager, aby wdrożyć pakiet konfiguracji na urządzeniach, aby były one dołączane do usługi.
ms.openlocfilehash: 2cca9cc073ca08c7fabb19511a4253e4a682057a
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760718"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-configuration-manager"></a>Dołączanie urządzeń Windows 10 i Windows 11 przy użyciu Configuration Manager

**Dotyczy:**

- [Microsoft 365 ochrona przed utratą danych punktu końcowego (DLP)](./endpoint-dlp-learn-about.md)
- [Zarządzanie ryzykiem wewnętrznym](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

### <a name="onboard-devices-using-system-center-configuration-manager"></a>Dołączanie urządzeń przy użyciu System Center Configuration Manager

1. Pobierz pakiet konfiguracji .zip plik (*DeviceComplianceOnboardingPackage.zip*) z [Centrum zgodności firmy Microsoft](https://compliance.microsoft.com/).

2. W okienku nawigacji wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ustawienia**</a> >  **Device OnboardingOnboarding** > .

3. W polu **Metoda wdrażania** wybierz pozycję **Microsoft Endpoint Configuration Manager 2012/2012 R2/1511/1602**.

4. Wybierz pozycję **Pobierz pakiet** i zapisz plik .zip.

5. Wyodrębnij zawartość pliku .zip do udostępnionej lokalizacji tylko do odczytu, do których mogą uzyskać dostęp administratorzy sieci, którzy wdrożą pakiet. Powinien istnieć plik o nazwie *DeviceComplianceOnboardingScript.cmd*.

6. Wdróż pakiet, wykonując kroki opisane [w artykule Packages and Programs in System Center 2012 R2 Configuration Manager article (Pakiety i programy) w artykule Configuration Manager 2012 R2](/previous-versions/system-center/system-center-2012-R2/gg699369(v=technet.10)).

7. Wybierz wstępnie zdefiniowaną kolekcję urządzeń do wdrożenia pakietu.

> [!NOTE]
> Microsoft 365 ochrona informacji nie obsługuje dołączania w fazie [OOBE (Out-Of-Box Experience).](https://answers.microsoft.com/en-us/windows/wiki/windows_10/how-to-complete-the-windows-10-out-of-box/47e3f943-f000-45e3-8c5c-9d85a1a0cf87) Upewnij się, że użytkownicy ukończyli program OOBE po uruchomieniu Windows instalacji lub uaktualnienia.

> [!TIP]
> Po dołączeniu urządzenia można uruchomić test wykrywania, aby sprawdzić, czy urządzenie jest prawidłowo dołączone do usługi. Aby uzyskać więcej informacji, zobacz [Uruchamianie testu wykrywania na nowo dołączonym urządzeniu Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test).
>
> Należy pamiętać, że istnieje możliwość utworzenia reguły wykrywania w aplikacji Configuration Manager w celu ciągłego sprawdzania, czy urządzenie zostało dołączone. Aplikacja jest innym typem obiektu niż pakiet i program.
> Jeśli urządzenie nie zostało jeszcze dołączone (z powodu oczekującego ukończenia OOBE lub z jakiejkolwiek innej przyczyny), Configuration Manager spróbuje ponownie dołączyć urządzenie, dopóki reguła nie wykryje zmiany stanu.
>
> To zachowanie można osiągnąć, tworząc regułę wykrywania, sprawdzając, czy wartość rejestru "OnboardingState" (typu REG_DWORD) = 1.
> Ta wartość rejestru znajduje się w obszarze "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status".
Aby uzyskać więcej informacji, zobacz [Konfigurowanie metod wykrywania w System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682159(v=technet.10)#step-4-configure-detection-methods-to-indicate-the-presence-of-the-deployment-type).

### <a name="configure-sample-collection-settings"></a>Konfigurowanie ustawień przykładowej kolekcji

Dla każdego urządzenia można ustawić wartość konfiguracji, aby określić, czy przykłady mogą być zbierane z urządzenia, gdy żądanie jest wysyłane za pośrednictwem Centrum zabezpieczeń usługi Microsoft Defender w celu przesłania pliku do głębokiej analizy.

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

Gdzie:

Typ klucza to D-WORD.

Możliwe wartości to:

- 0 — nie zezwala na udostępnianie przykładów z tego urządzenia
- 1 — umożliwia udostępnianie wszystkich typów plików z tego urządzenia

Wartość domyślna w przypadku, gdy klucz rejestru nie istnieje, to 1.

Aby uzyskać więcej informacji na temat zgodności System Center Configuration Manager, zobacz [Wprowadzenie do ustawień zgodności w System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682139(v=technet.10)).


## <a name="other-recommended-configuration-settings"></a>Inne zalecane ustawienia konfiguracji

Po dołączeniu urządzeń do usługi ważne jest, aby skorzystać z dołączonych możliwości ochrony przed zagrożeniami, włączając je przy użyciu następujących zalecanych ustawień konfiguracji.

### <a name="device-collection-configuration"></a>Konfiguracja kolekcji urządzeń

Jeśli używasz programu Endpoint Configuration Manager w wersji 2002 lub nowszej, możesz rozszerzyć wdrożenie o serwery lub klientów niższego poziomu.

### <a name="next-generation-protection-configuration"></a>Konfiguracja ochrony następnej generacji

Zalecane są następujące ustawienia konfiguracji:

**Skanowania**

- Skanuj wymienne urządzenia magazynujące, takie jak dyski USB: Tak

**Ochrona w czasie rzeczywistym**

- Włącz monitorowanie behawioralne: Tak
- Włącz ochronę przed potencjalnie niepożądanymi aplikacjami podczas pobierania i przed instalacją: Tak

**Usługa Cloud Protection**

- Typ członkostwa w usłudze Cloud Protection: członkostwo zaawansowane

**Zmniejszanie obszaru podatnego na ataki** Skonfiguruj wszystkie dostępne reguły na wartość Inspekcja.

> [!NOTE]
> Zablokowanie tych działań może przerwać uzasadnione procesy biznesowe. Najlepszym podejściem jest ustawienie wszystkich elementów do inspekcji, określenie, które z nich można bezpiecznie włączyć, a następnie włączenie tych ustawień w punktach końcowych, które nie mają wykrywania fałszywie dodatniego.

**Ochrona sieci**

Przed włączeniem ochrony sieci w trybie inspekcji lub bloku upewnij się, że zainstalowano aktualizację platformy ochrony przed złośliwym kodem, którą można uzyskać na [stronie pomocy technicznej](https://support.microsoft.com/en-us/help/4560203/windows-defender-anti-malware-platform-binaries-are-missing).

**Kontrolowany dostęp do folderu**

Włącz funkcję w trybie inspekcji przez co najmniej 30 dni. Po tym okresie przejrzyj wykrycia i utwórz listę aplikacji, które mogą zapisywać w chronionych katalogach.

Aby uzyskać więcej informacji, zobacz [Evaluate controlled folder access (Ocena kontrolowanego dostępu do folderów).](/windows/security/threat-protection/microsoft-defender-atp/evaluate-controlled-folder-access)

## <a name="offboard-devices-using-configuration-manager"></a>Odłączanie urządzeń przy użyciu Configuration Manager

Ze względów bezpieczeństwa pakiet używany do odłączenia urządzeń wygaśnie 30 dni po pobraniu. Wygasłe pakiety odłączania wysyłane do urządzenia zostaną odrzucone. Podczas pobierania pakietu odłączania otrzymasz powiadomienie o dacie wygaśnięcia pakietów i zostanie on również uwzględniony w nazwie pakietu.

> [!NOTE]
> Zasady dołączania i odłączania nie mogą być wdrażane na tym samym urządzeniu w tym samym czasie, w przeciwnym razie spowoduje to nieprzewidywalne kolizje.

### <a name="offboard-devices-using-microsoft-endpoint-configuration-manager-current-branch"></a>Odłączanie urządzeń przy użyciu Microsoft Endpoint Configuration Manager bieżącej gałęzi

Jeśli używasz Microsoft Endpoint Configuration Manager bieżącej gałęzi, zobacz [Tworzenie pliku konfiguracji odłączania](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#create-an-offboarding-configuration-file).

### <a name="offboard-devices-using-system-center-2012-r2-configuration-manager"></a>Odłączanie urządzeń przy użyciu Configuration Manager System Center 2012 R2

1. Pobierz pakiet odłączania z <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a>:

2. W okienku nawigacji wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ustawienia**</a> >   **Device onboardingOffboarding**> .

3. Wybierz Windows 10 jako system operacyjny.

4. W polu **Metoda wdrażania** wybierz pozycję **Microsoft Endpoint Configuration Manager 2012/2012 R2/1511/1602**.

5. Wybierz pozycję **Pobierz pakiet** i zapisz plik .zip.

6. Wyodrębnij zawartość pliku .zip do udostępnionej lokalizacji tylko do odczytu, do których mogą uzyskać dostęp administratorzy sieci, którzy wdrożą pakiet. Powinien istnieć plik o nazwie *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

7. Wdróż pakiet, wykonując kroki opisane [w artykule Packages and Programs in System Center 2012 R2 Configuration Manager article (Pakiety i programy) w artykule Configuration Manager 2012 R2](/previous-versions/system-center/system-center-2012-R2/gg699369(v=technet.10)).

8. Wybierz wstępnie zdefiniowaną kolekcję urządzeń do wdrożenia pakietu.

> [!IMPORTANT]
> Odłączanie powoduje, że urządzenie przestaje wysyłać dane czujnika do portalu, ale dane z urządzenia, w tym odwołanie do wszelkich alertów, które miał, zostaną zachowane przez maksymalnie 6 miesięcy.

## <a name="monitor-device-configuration"></a>Monitorowanie konfiguracji urządzenia

Jeśli używasz Microsoft Endpoint Configuration Manager bieżącej gałęzi, użyj wbudowanego pulpitu nawigacyjnego Ochrona punktu końcowego w usłudze Microsoft Defender w konsoli Configuration Manager. Aby uzyskać więcej informacji, zobacz [Zaawansowana ochrona przed zagrożeniami w usłudze Microsoft Defender — monitorowanie](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#monitor).

Jeśli używasz Configuration Manager System Center 2012 R2, monitorowanie składa się z dwóch części:

1. Potwierdzanie, że pakiet konfiguracji został poprawnie wdrożony i jest uruchomiony (lub został pomyślnie uruchomiony) na urządzeniach w sieci.

2. Sprawdzanie, czy urządzenia są zgodne z usługą dołączania urządzeń Microsoft 365 (dzięki temu urządzenie może ukończyć proces dołączania i nadal raportować dane do usługi).

### <a name="confirm-the-configuration-package-has-been-correctly-deployed"></a>Upewnij się, że pakiet konfiguracji został poprawnie wdrożony

1. W konsoli Configuration Manager kliknij pozycję **Monitorowanie** w dolnej części okienka nawigacji.

2. Wybierz pozycję **Przegląd** , a następnie **pozycję Wdrożenia**.

3. Wybierz wdrożenie z nazwą pakietu.

4. Przejrzyj wskaźniki stanu w obszarze **Statystyki ukończenia** i **Stan zawartości**.

    Jeśli istnieją wdrożenia zakończone niepowodzeniem (urządzenia z **błędem**, **wymaganiami, które nie zostały spełnione** lub **stanem Niepowodzenie**), może być konieczne rozwiązanie problemów z urządzeniami. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z dołączaniem zaawansowanej ochrony przed zagrożeniami w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding).

    ![Configuration Manager pokazano pomyślne wdrożenie bez błędów.](../media/sccm-deployment.png)

### <a name="check-that-the-devices-are-compliant-with-the-microsoft-365-endpoint-data-loss-prevention-service"></a>Sprawdź, czy urządzenia są zgodne z usługą zapobiegania utracie danych punktu końcowego Microsoft 365

Aby monitorować wdrożenie, można ustawić regułę zgodności dla elementu konfiguracji w System Center 2012 R2 Configuration Manager.

> [!NOTE]
> Ta procedura i wpis rejestru mają zastosowanie do punktu końcowego DLP oraz usługi Defender for Endpoint.

Ta reguła powinna być elementem konfiguracji reguły zgodności *nie korygującej* , który monitoruje wartość klucza rejestru na urządzeniach docelowych.

Monitoruj następujący wpis klucza rejestru:

```text
Path: "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status"
Name: "OnboardingState"
Value: "1"
```

Aby uzyskać więcej informacji, zobacz [Wprowadzenie do ustawień zgodności w System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682139(v=technet.10)).

## <a name="related-topics"></a>Tematy pokrewne

- [Dołączanie urządzeń Windows 10 i Windows 11 przy użyciu zasady grupy](device-onboarding-gp.md)
- [Dołączanie urządzeń z systemami Windows 10 i Windows 11 przy użyciu narzędzi do zarządzania urządzeniami przenośnymi](device-onboarding-mdm.md)
- [Dołączanie urządzeń z systemami Windows 10 i Windows 11 przy użyciu skryptu lokalnego](device-onboarding-script.md)
- [Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI)](device-onboarding-vdi.md)
- [Uruchamianie testu wykrywania na nowo dołączonym urządzeniu Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Rozwiązywanie problemów z dołączaniem zaawansowanej ochrony przed zagrożeniami w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
