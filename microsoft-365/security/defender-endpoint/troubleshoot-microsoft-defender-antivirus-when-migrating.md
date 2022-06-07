---
title: Rozwiąż problemy z programem antywirusowym Microsoft Defender podczas migracji z rozwiązania innej firmy
description: Rozwiązywanie typowych błędów podczas migracji do programu antywirusowego Microsoft Defender
keywords: zdarzenie, kod błędu, rejestrowanie, rozwiązywanie problemów, program antywirusowy microsoft defender, program antywirusowy Windows Defender, migracja
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: martyav
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: c1fe1713909395c1c30af8089664e70598e91721
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2022
ms.locfileid: "65923173"
---
# <a name="troubleshoot-microsoft-defender-antivirus-while-migrating-from-a-third-party-solution"></a>Rozwiąż problemy z programem antywirusowym Microsoft Defender podczas migracji z rozwiązania innej firmy

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Program antywirusowy Microsoft Defender](https://www.microsoft.com/windows/comprehensive-security)

**Platformy**
- System Windows

Pomoc można znaleźć tutaj, jeśli wystąpią problemy podczas migracji z rozwiązania zabezpieczeń innej firmy do programu antywirusowego Microsoft Defender.

## <a name="review-event-logs"></a>Przeglądanie dzienników zdarzeń

1. Otwórz aplikację Podgląd zdarzeń, wybierając ikonę **Wyszukaj** na pasku zadań i wyszukując *podgląd zdarzeń*.

    Informacje o programie antywirusowym Microsoft Defender można znaleźć w obszarze  **Dzienniki** \> aplikacji i usług **Microsoft** \> **Windows** \> **Defender**.

1. W tym miejscu wybierz pozycję **Otwórz** poniżej **pozycji Operacje**.

    Wybranie zdarzenia w okienku szczegółów spowoduje wyświetlenie dodatkowych informacji o zdarzeniu w dolnym okienku na kartach **Ogólne** i **Szczegóły** .

## <a name="microsoft-defender-antivirus-wont-start"></a>Program antywirusowy Microsoft Defender nie zostanie uruchomiony

Ten problem może objawiać się w postaci kilku różnych identyfikatorów zdarzeń, z których wszystkie mają tę samą przyczynę.

### <a name="associated-event-ids"></a>Skojarzone identyfikatory zdarzeń

Identyfikator zdarzenia|Nazwa dziennika|Opis|Źródło
---|---|---|---
15|Aplikacja|Pomyślnie zaktualizowano stan usługi Windows Defender, aby SECURITY_PRODUCT_STATE_OFF.|Security Center
5007|Microsoft-Windows-Windows Defender/Operational|Konfiguracja programu antywirusowego Windows Defender została zmieniona. Jeśli jest to nieoczekiwane zdarzenie, należy przejrzeć ustawienia, ponieważ może to być wynikiem złośliwego oprogramowania. <p> **Stara wartość:** Default\IsServiceRunning = 0x0 <p> **Nowa wartość:** HKLM\SOFTWARE\Microsoft\Windows Defender\IsServiceRunning = 0x1|Windows Defender
5010|Microsoft-Windows-Windows Defender/Operational|Skanowanie programu antywirusowego Windows Defender pod kątem programów szpiegujących i innych potencjalnie niechcianych programów jest wyłączone.|Windows Defender

### <a name="how-to-tell-if-microsoft-defender-antivirus-wont-start-because-a-third-party-antivirus-is-installed"></a>Jak sprawdzić, czy program antywirusowy Microsoft Defender nie zostanie uruchomiony, ponieważ zainstalowano program antywirusowy innej firmy

Jeśli na urządzeniu z systemem Windows 10 lub Windows 11 nie używasz usługi Microsoft Defender dla punktu końcowego i masz zainstalowany program antywirusowy innej firmy, program antywirusowy Microsoft Defender zostanie automatycznie wyłączony. Jeśli używasz usługi Microsoft Defender for Endpoint z zainstalowanym programem antywirusowym innej firmy, program antywirusowy Microsoft Defender zostanie uruchomiony w trybie pasywnym z ograniczoną funkcjonalnością.

> [!TIP]
> Opisany scenariusz dotyczy tylko systemów Windows 10 i Windows 11. Inne wersje systemu Windows mają [różne odpowiedzi na oprogramowanie antywirusowe](microsoft-defender-antivirus-compatibility.md) Microsoft Defender uruchamiane wraz z oprogramowaniem zabezpieczającym innych firm.

#### <a name="use-services-app-to-check-if-microsoft-defender-antivirus-is-turned-off"></a>Sprawdzanie, czy program antywirusowy Microsoft Defender jest wyłączony za pomocą aplikacji Usługi

Aby otworzyć aplikację Usługi, wybierz ikonę **Wyszukaj** na pasku zadań i wyszukaj *usługi*. Aplikację można również otworzyć z poziomu wiersza polecenia, wpisując plik *services.msc*.

Informacje o programie antywirusowym Microsoft Defender zostaną wyświetlone w aplikacji Usługi w obszarze **Windows Defender** \> **Operational**. Nazwa usługi antywirusowej to *Windows Defender Antivirus Service*.

Podczas sprawdzania aplikacji może się okazać, że *usługa antywirusowa Windows Defender* jest ustawiona na ręczną, ale podczas próby ręcznego uruchomienia tej usługi zostanie wyświetlone ostrzeżenie z informacją: *Usługa antywirusowa Windows Defender na komputerze lokalnym została uruchomiona, a następnie zatrzymana. Niektóre usługi są zatrzymywane automatycznie, jeśli nie są używane przez inne usługi lub programy.*

Oznacza to, że program antywirusowy Microsoft Defender został automatycznie wyłączony w celu zachowania zgodności z programem antywirusowym innej firmy.

#### <a name="generate-a-detailed-report"></a>Generowanie szczegółowego raportu

Możesz wygenerować szczegółowy raport dotyczący aktualnie aktywnych zasad grupy, otwierając wiersz polecenia w trybie **Uruchom jako administrator** , a następnie wprowadzając następujące polecenie:

```console
GPresult.exe /h gpresult.html
```

Spowoduje to wygenerowanie raportu znajdującego się pod adresem *./gpresult.html*. Otwórz ten plik i mogą zostać wyświetlone następujące wyniki, w zależności od tego, jak program antywirusowy Microsoft Defender został wyłączony.

##### <a name="group-policy-results"></a>Wyniki zasad grupy

##### <a name="if-security-settings-are-implemented-via-group-policy-gpo-at-the-domain-or-local-level-or-though-system-center-configuration-manager-sccm"></a>Jeśli ustawienia zabezpieczeń są implementowane za pośrednictwem zasad grupy (GPO) na poziomie domeny lub lokalnej, lub programu System Center Configuration Manager (SCCM)

W raporcie GPResults pod nagłówkiem *Składniki systemu Windows/program antywirusowy Windows Defender* może zostać wyświetlony następujący wpis wskazujący, że program antywirusowy Microsoft Defender jest wyłączony.

Zasad|Ustawienie|Zwycięski obiekt zasad grupy
---|---|---
Wyłączanie programu antywirusowego Windows Defender|Włączone|Win10-Workstations

###### <a name="if-security-settings-are-implemented-via-group-policy-preference-gpp"></a>Jeśli ustawienia zabezpieczeń są implementowane za pośrednictwem preferencji zasad grupy (GPP)

W obszarze *nagłówka Element rejestru (ścieżka klucza: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender, nazwa wartości: DisableAntiSpyware) może zostać wyświetlony* następujący wpis wskazujący, że program antywirusowy Microsoft Defender jest wyłączony.

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

Raport może zawierać następujący tekst wskazujący, że program antywirusowy Microsoft Defender jest wyłączony:

> Rejestr (regedit.exe)
>
> HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender DisableAntiSpyware (dword) 1 (szesnastkowa)

###### <a name="if-security-settings-are-set-in-windows-or-your-windows-server-image"></a>Jeśli ustawienia zabezpieczeń są ustawione w systemie Windows lub obrazie systemu Windows Server

Administrator wyobrażający sobie mógł ustawić zasady zabezpieczeń **[DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware)** lokalnie za pośrednictwem *GPEdit.exe*, *LGPO.exe* lub przez zmodyfikowanie rejestru w sekwencji zadań. Możesz [skonfigurować identyfikator zaufanego obrazu](/windows-hardware/manufacture/desktop/configure-a-trusted-image-identifier-for-windows-defender) dla programu antywirusowego Microsoft Defender.

### <a name="turn-microsoft-defender-antivirus-back-on"></a>Włączanie programu antywirusowego Microsoft Defender

Program antywirusowy Microsoft Defender zostanie automatycznie włączony, jeśli żaden inny program antywirusowy nie jest obecnie aktywny. Należy całkowicie wyłączyć program antywirusowy innej firmy, aby upewnić się, że program antywirusowy Microsoft Defender może działać z pełną funkcjonalnością.

> [!WARNING]
> Rozwiązania sugerujące edytowanie wartości początkowych *usługi Windows Defender* dla *wdboot*, *wdfilter*, *wdnisdrv*, *wdnissvc* i *windefend* w HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services są nieobsługiwane i mogą wymusić ponowne obrazowanie systemu.

Tryb pasywny jest dostępny, jeśli zaczniesz korzystać z usługi Microsoft Defender for Endpoint i oprogramowania antywirusowego innej firmy wraz z programem antywirusowym Microsoft Defender. Tryb pasywny umożliwia programowi antywirusowemu Microsoft Defender skanowanie plików i aktualizowanie samych plików, ale nie koryguje zagrożeń. Ponadto monitorowanie zachowania za pośrednictwem [ochrony w czasie rzeczywistym](configure-real-time-protection-microsoft-defender-antivirus.md) nie jest dostępne w trybie pasywnym, chyba że wdrożono [ochronę przed utratą danych punktu końcowego (DLP](/microsoft-365/security/defender-endpoint/information-protection-in-windows-overview) ).

Inna funkcja, znana jako [ograniczone skanowanie okresowe](limited-periodic-scanning-microsoft-defender-antivirus.md), jest dostępna dla użytkowników końcowych, gdy program antywirusowy Microsoft Defender jest ustawiony na automatyczne wyłączanie. Ta funkcja umożliwia programowi antywirusowemu Microsoft Defender okresowe skanowanie plików wraz z oprogramowaniem antywirusowym innych firm przy użyciu ograniczonej liczby wykryć.

> [!IMPORTANT]
> Ograniczone okresowe skanowanie nie jest zalecane w środowiskach przedsiębiorstwa. Możliwości wykrywania, zarządzania i raportowania dostępne podczas uruchamiania programu antywirusowego Microsoft Defender w tym trybie są ograniczone w porównaniu z trybem aktywnym.

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

- [Zgodność programu antywirusowego Microsoft Defender](microsoft-defender-antivirus-compatibility.md)
- [Program antywirusowy Microsoft Defender w aplikacji Zabezpieczenia systemu Windows](microsoft-defender-security-center-antivirus.md)
