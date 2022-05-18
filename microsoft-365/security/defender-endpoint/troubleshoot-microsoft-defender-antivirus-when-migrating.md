---
title: Rozwiąż problemy z programem antywirusowym Microsoft Defender podczas migracji z rozwiązania innej firmy
description: Rozwiązywanie typowych błędów podczas migracji do Program antywirusowy Microsoft Defender
keywords: zdarzenie, kod błędu, rejestrowanie, rozwiązywanie problemów, program antywirusowy microsoft defender, program antywirusowy Windows Defender, migracja
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: martyav
ms.author: v-maave
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 5e0db56306b1e56ee0ab21d2c3728f30a8c47ec8
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2022
ms.locfileid: "65468245"
---
# <a name="troubleshoot-microsoft-defender-antivirus-while-migrating-from-a-third-party-solution"></a>Rozwiąż problemy z programem antywirusowym Microsoft Defender podczas migracji z rozwiązania innej firmy

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Program antywirusowy Microsoft Defender](https://www.microsoft.com/windows/comprehensive-security)

**Platformy**
- System Windows

Pomoc można znaleźć tutaj, jeśli napotkasz problemy podczas migracji z rozwiązania zabezpieczeń innej firmy do Program antywirusowy Microsoft Defender.

## <a name="review-event-logs"></a>Przeglądanie dzienników zdarzeń

1. Otwórz aplikację Podgląd zdarzeń, wybierając ikonę **Wyszukaj** na pasku zadań i wyszukując *podgląd zdarzeń*.

    Informacje o Program antywirusowy Microsoft Defender można znaleźć w obszarze **Dzienniki** \> aplikacji i usług **Microsoft** \> **Windows** \> **Windows Defender**.

1. W tym miejscu wybierz pozycję **Otwórz** poniżej **pozycji Operacje**.

    Wybranie zdarzenia w okienku szczegółów spowoduje wyświetlenie dodatkowych informacji o zdarzeniu w dolnym okienku na kartach **Ogólne** i **Szczegóły** .

## <a name="microsoft-defender-antivirus-wont-start"></a>Program antywirusowy Microsoft Defender nie zostanie uruchomiona

Ten problem może objawiać się w postaci kilku różnych identyfikatorów zdarzeń, z których wszystkie mają tę samą przyczynę.

### <a name="associated-event-ids"></a>Skojarzone identyfikatory zdarzeń

Identyfikator zdarzenia|Nazwa dziennika|Opis|Źródło
---|---|---|---
15|Aplikacja|Zaktualizowano stan Windows Defender pomyślnie do SECURITY_PRODUCT_STATE_OFF.|Security Center
5007|Microsoft-Windows-Windows Defender/Operational|Program antywirusowy Windows Defender Konfiguracja została zmieniona. Jeśli jest to nieoczekiwane zdarzenie, należy przejrzeć ustawienia, ponieważ może to być wynikiem złośliwego oprogramowania. <p> **Stara wartość:** Default\IsServiceRunning = 0x0 <p> **Nowa wartość:** HKLM\SOFTWARE\Microsoft\Windows Defender\IsServiceRunning = 0x1|Windows Defender
5010|Microsoft-Windows-Windows Defender/Operational|Program antywirusowy Windows Defender skanowanie pod kątem programów szpiegujących i innych potencjalnie niechcianych programów jest wyłączone.|Windows Defender

### <a name="how-to-tell-if-microsoft-defender-antivirus-wont-start-because-a-third-party-antivirus-is-installed"></a>Jak sprawdzić, czy Program antywirusowy Microsoft Defender nie zostanie uruchomiona, ponieważ zainstalowano program antywirusowy innej firmy

Jeśli na urządzeniu Windows 10 lub Windows 11 nie używasz Ochrona punktu końcowego w usłudze Microsoft Defender i masz zainstalowany program antywirusowy innej firmy, Program antywirusowy Microsoft Defender zostać automatycznie wyłączone. Jeśli używasz Ochrona punktu końcowego w usłudze Microsoft Defender z zainstalowanym programem antywirusowym innej firmy, Program antywirusowy Microsoft Defender rozpocznie się w trybie pasywnym z ograniczoną funkcjonalnością.

> [!TIP]
> Opisany scenariusz dotyczy tylko Windows 10 i Windows 11. Inne wersje Windows mają [różne odpowiedzi na](microsoft-defender-antivirus-compatibility.md) Program antywirusowy Microsoft Defender uruchamiane wraz z oprogramowaniem zabezpieczającym innych firm.

#### <a name="use-services-app-to-check-if-microsoft-defender-antivirus-is-turned-off"></a>Użyj aplikacji Usługi, aby sprawdzić, czy Program antywirusowy Microsoft Defender jest wyłączona

Aby otworzyć aplikację Usługi, wybierz ikonę **Wyszukaj** na pasku zadań i wyszukaj *usługi*. Aplikację można również otworzyć z poziomu wiersza polecenia, wpisując plik *services.msc*.

Informacje o Program antywirusowy Microsoft Defender zostaną wyświetlone w aplikacji Usługi w obszarze **Windows Defender** \> **Operacyjny**. Nazwa usługi antywirusowej to *Program antywirusowy Windows Defender Service*.

Podczas sprawdzania aplikacji może się okazać, że *usługa Program antywirusowy Windows Defender* jest ustawiona na ręczną, ale podczas próby ręcznego uruchomienia tej usługi zostanie *wyświetlone ostrzeżenie z informacją The Program antywirusowy Windows Defender  Usługa usługi na komputerze lokalnym została uruchomiona, a następnie zatrzymana. Niektóre usługi są zatrzymywane automatycznie, jeśli nie są używane przez inne usługi lub programy.*

Oznacza to, że Program antywirusowy Microsoft Defender została automatycznie wyłączona w celu zachowania zgodności z programem antywirusowym innej firmy.

#### <a name="generate-a-detailed-report"></a>Generowanie szczegółowego raportu

Możesz wygenerować szczegółowy raport dotyczący aktualnie aktywnych zasad grupy, otwierając wiersz polecenia w trybie **Uruchom jako administrator** , a następnie wprowadzając następujące polecenie:

```console
GPresult.exe /h gpresult.html
```

Spowoduje to wygenerowanie raportu znajdującego się pod adresem *./gpresult.html*. Otwórz ten plik i mogą zostać wyświetlone następujące wyniki w zależności od sposobu wyłączenia Program antywirusowy Microsoft Defender.

##### <a name="group-policy-results"></a>Wyniki zasad grupy

##### <a name="if-security-settings-are-implemented-via-group-policy-gpo-at-the-domain-or-local-level-or-though-system-center-configuration-manager-sccm"></a>Jeśli ustawienia zabezpieczeń są implementowane za pośrednictwem zasad grupy (GPO) na poziomie domeny lub lokalnej, lub programu System Center Configuration Manager (SCCM)

W raporcie GPResults pod nagłówkiem *Windows Components/Program antywirusowy Windows Defender* może zostać wyświetlony następujący wpis wskazujący, że Program antywirusowy Microsoft Defender jest wyłączona.

Zasad|Ustawienie|Zwycięski obiekt zasad grupy
---|---|---
Wyłącz Program antywirusowy Windows Defender|Włączone|Win10-Workstations

###### <a name="if-security-settings-are-implemented-via-group-policy-preference-gpp"></a>Jeśli ustawienia zabezpieczeń są implementowane za pośrednictwem preferencji zasad grupy (GPP)

W obszarze *nagłówka Element rejestru (Ścieżka klucza: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender, Nazwa wartości: DisableAntiSpyware) może zostać wyświetlony* następujący wpis wskazujący, że Program antywirusowy Microsoft Defender jest wyłączona.

DisableAntiSpyware|-
---|---
Zwycięski obiekt zasad grupy|Win10-Workstations
Wynik: Powodzenie|
**Ogólne**|
Akcja|Aktualizacja
**Właściwości**|
Gałęzi|HKEY_LOCAL_MACHINE
Ścieżka klucza|SOFTWARE\Policies\Microsoft\Windows Defender
Nazwa wartości|DisableAntiSpyware
Typ wartości|REG_DWORD
Dane wartości|0x1 (1)

###### <a name="if-security-settings-are-implemented-via-registry-key"></a>Jeśli ustawienia zabezpieczeń są implementowane za pośrednictwem klucza rejestru

Raport może zawierać następujący tekst wskazujący, że Program antywirusowy Microsoft Defender jest wyłączona:

> Rejestr (regedit.exe)
>
> HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender DisableAntiSpyware (dword) 1 (szesnastkowa)

###### <a name="if-security-settings-are-set-in-windows-or-your-windows-server-image"></a>Jeśli ustawienia zabezpieczeń są ustawione w Windows lub obrazie serwera Windows

Administrator wyobrażający sobie mógł ustawić zasady zabezpieczeń **[DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware)** lokalnie za pośrednictwem *GPEdit.exe*, *LGPO.exe* lub przez zmodyfikowanie rejestru w sekwencji zadań. Możesz [skonfigurować identyfikator zaufanego obrazu](/windows-hardware/manufacture/desktop/configure-a-trusted-image-identifier-for-windows-defender) dla Program antywirusowy Microsoft Defender.

### <a name="turn-microsoft-defender-antivirus-back-on"></a>Włącz ponownie Program antywirusowy Microsoft Defender

Program antywirusowy Microsoft Defender włączy się automatycznie, jeśli żaden inny program antywirusowy nie jest obecnie aktywny. Musisz całkowicie wyłączyć program antywirusowy innej firmy, aby upewnić się, że Program antywirusowy Microsoft Defender można uruchamiać z pełną funkcjonalnością.

> [!WARNING]
> Rozwiązania sugerujące edytowanie wartości początkowych *Windows Defender* dla *wdboot*, *wdfilter*, *wdnisdrv*, *wdnissvc* i *windefend* w HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services są nieobsługiwane i mogą wymusić ponowne obrazowanie systemu.

Tryb pasywny jest dostępny, jeśli zaczniesz korzystać z Ochrona punktu końcowego w usłudze Microsoft Defender i oprogramowania antywirusowego innej firmy wraz z Program antywirusowy Microsoft Defender. Tryb pasywny umożliwia Program antywirusowy Microsoft Defender skanowanie plików i aktualizowanie samych plików, ale nie koryguje zagrożeń. Ponadto monitorowanie zachowania za pośrednictwem [ochrony w czasie rzeczywistym](configure-real-time-protection-microsoft-defender-antivirus.md) nie jest dostępne w trybie pasywnym, chyba że wdrożono [ochronę przed utratą danych punktu końcowego (DLP](/microsoft-365/security/defender-endpoint/information-protection-in-windows-overview) ).

Inna funkcja, znana jako [ograniczone skanowanie okresowe](limited-periodic-scanning-microsoft-defender-antivirus.md), jest dostępna dla użytkowników końcowych, gdy Program antywirusowy Microsoft Defender jest ustawiona na automatyczne wyłączanie. Ta funkcja umożliwia Program antywirusowy Microsoft Defender okresowe skanowanie plików wraz z oprogramowaniem antywirusowym innych firm przy użyciu ograniczonej liczby wykryć.

> [!IMPORTANT]
> Ograniczone okresowe skanowanie nie jest zalecane w środowiskach przedsiębiorstwa. Możliwości wykrywania, zarządzania i raportowania dostępne podczas uruchamiania Program antywirusowy Microsoft Defender w tym trybie są ograniczone w porównaniu z trybem aktywnym.

> [!TIP]
> Jeśli szukasz informacji dotyczących programu antywirusowego dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)


### <a name="see-also"></a>Zobacz też

- [zgodność Program antywirusowy Microsoft Defender](microsoft-defender-antivirus-compatibility.md)
- [Program antywirusowy Microsoft Defender w aplikacji Zabezpieczenia Windows](microsoft-defender-security-center-antivirus.md)
