---
title: Rozwiązywanie Program antywirusowy Microsoft Defender podczas migracji z rozwiązania innej firmy
description: Rozwiązywanie typowych błędów podczas migracji do systemu Program antywirusowy Microsoft Defender
keywords: zdarzenie, kod błędu, rejestrowanie, rozwiązywanie problemów, program antywirusowy Microsoft Defender, program antywirusowy Windows Defender, migracja
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: martyav
ms.author: v-maave
ms.custom: nextgen
ms.date: 10/19/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: c1b60b66977c4f93591bce20a5cf6ace0b7fc567
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997300"
---
# <a name="troubleshoot-microsoft-defender-antivirus-while-migrating-from-a-third-party-solution"></a>Rozwiązywanie Program antywirusowy Microsoft Defender podczas migracji z rozwiązania innej firmy

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)


Pomoc możesz znaleźć tutaj, jeśli wystąpią problemy podczas migracji z rozwiązania zabezpieczeń innej firmy do Program antywirusowy Microsoft Defender.

## <a name="review-event-logs"></a>Przeglądanie dzienników zdarzeń

1. Otwórz aplikację Podgląd zdarzeń, **wybierając ikonę** wyszukiwania na pasku zadań i wyszukując podgląd *zdarzeń*.

    Informacje o Program antywirusowy Microsoft Defender można znaleźć w obszarze Dzienniki aplikacji i **usług firmy** \> **Microsoft** \>  \> Windows **Windows Defender**.

1. W tym miejscu wybierz pozycję **Otwórz pod** **operacyjną**.

    Wybranie zdarzenia w okienku szczegółów spowoduje pokazanie dodatkowych informacji o zdarzeniu w dolnym okienku, na **kartach** **Ogólne** i Szczegóły.

## <a name="microsoft-defender-antivirus-wont-start"></a>Program antywirusowy Microsoft Defender nie można uruchomić

Ten problem może się manifestować w postaci kilku różnych identyfikatorów zdarzeń, z których wszystkie mają taką samą przyczynę.

### <a name="associated-event-ids"></a>Skojarzone identyfikatory zdarzeń

Identyfikator zdarzenia|Nazwa dziennika|Opis|Źródło
---|---|---|---
15|Aplikacja|Pomyślnie Windows Defender stan aktualizacji, aby SECURITY_PRODUCT_STATE_OFF.|Centrum zabezpieczeń
5007|Microsoft-Windows-Windows Defender/Operacyjny|Program antywirusowy Windows Defender Konfiguracja uległa zmianie. Jeśli jest to nieoczekiwane zdarzenie, należy przejrzeć ustawienia, ponieważ może to być wynikiem złośliwego oprogramowania. <p> **Stara wartość:** Default\IsServiceRunning = 0x0 <p> **Nowa wartość:** HKLM\SOFTWARE\Microsoft\Windows Defender\IsServiceRunning = 0x1|Windows Defender
5010|Microsoft-Windows-Windows Defender/Operacyjny|Program antywirusowy Windows Defender skanowanie w celu oprogramowania szpiegującego i innego potencjalnie niechcianego oprogramowania jest wyłączone.|Windows Defender

### <a name="how-to-tell-if-microsoft-defender-antivirus-wont-start-because-a-third-party-antivirus-is-installed"></a>Jak stwierdzić, Program antywirusowy Microsoft Defender nie można uruchomić, ponieważ zainstalowano oprogramowanie antywirusowe innej firmy

Jeśli na urządzeniu z systemem Windows 10 lub Windows 11, jeśli nie korzystasz z programu Microsoft Defender for Endpoint i masz zainstalowane oprogramowanie antywirusowe innej firmy, program Program antywirusowy Microsoft Defender zostanie automatycznie wyłączony. Jeśli używasz programu Microsoft Defender for Endpoint z zainstalowanym oprogramowaniem antywirusowym innej firmy, Program antywirusowy Microsoft Defender zostanie uruchomienie w trybie pasywnym, o ograniczonej funkcjonalności.

> [!TIP]
> Właśnie opisany scenariusz dotyczy tylko Windows 10 i Windows 11. Inne wersje programu Windows [różnych](microsoft-defender-antivirus-compatibility.md) odpowiedzi na Program antywirusowy Microsoft Defender są uruchamiane razem z oprogramowaniem zabezpieczeń innych firm.

#### <a name="use-services-app-to-check-if-microsoft-defender-antivirus-is-turned-off"></a>Używanie aplikacji Usługi do sprawdzania, czy Program antywirusowy Microsoft Defender jest wyłączona

Aby otworzyć aplikację Usługi, wybierz **ikonę Wyszukiwania** na pasku zadań i wyszukaj *usługi*. Aplikację można również otworzyć z wiersza polecenia, wpisując *services.msc*.

Informacje o Program antywirusowy Microsoft Defender zostaną wyświetlone w aplikacji Usługi **w obszarze** \> Windows Defender **operacyjne**. Nazwa usługi antywirusowej to *Program antywirusowy Windows Defender Usługi*.

Podczas sprawdzania aplikacji może się okazać, że usługa *Program antywirusowy Windows Defender* jest ustawiona na ręczną, ale podczas próby uruchomienia tej usługi ręcznie może zostać wyświetlony komunikat z ostrzeżeniem Program antywirusowy Windows Defender *Usługa usługi na komputerze lokalnym została uruchomiona, a następnie zatrzymana. Niektóre usługi są zatrzymywane automatycznie, jeśli nie są one w użyciu przez inne usługi lub programy.*

Oznacza to, Program antywirusowy Microsoft Defender została automatycznie wyłączona, aby zachować zgodność z oprogramowaniem antywirusowym innej firmy.

#### <a name="generate-a-detailed-report"></a>Generowanie szczegółowego raportu

Szczegółowy raport o aktualnie aktywnych zasadach grupy można wygenerować, otwierając wiersz polecenia w trybie Uruchom jako **tryb** administratora, a następnie uruchamiając następujące polecenie:

```console
GPresult.exe /h gpresult.html
```

Spowoduje to wygenerowanie raportu znajdującego się *w 0./gpresult.html*. Otwórz ten plik i w zależności od tego, jak Program antywirusowy Microsoft Defender wyłączony, mogą zostać Program antywirusowy Microsoft Defender wyniki.

##### <a name="group-policy-results"></a>Wyniki zasad grupy

##### <a name="if-security-settings-are-implemented-via-group-policy-gpo-at-the-domain-or-local-level-or-though-system-center-configuration-manager-sccm"></a>Jeśli ustawienia zabezpieczeń są zaimplementowane za pośrednictwem zasad grupy (GPO) na poziomie domeny lub lokalnie albo za pośrednictwem menedżera konfiguracji programu System Center (SCCM)

W raporcie GPResults pod nagłówkiem Windows *Components/Program antywirusowy Windows Defender* może być wyświetlony następujący wpis wskazujący, że Program antywirusowy Microsoft Defender jest wyłączony.

Zasady|Ustawienie|Wygrana zapotrz. zasad grupy
---|---|---
Wyłączanie Program antywirusowy Windows Defender|Włączone|Win10-Workstations

###### <a name="if-security-settings-are-implemented-via-group-policy-preference-gpp"></a>Jeśli ustawienia zabezpieczeń są zaimplementowane za pośrednictwem preferencji zasad grupy (GPP, Group Policy Preference)

Pod nagłówkiem Element rejestru (ścieżka klucza *: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender, nazwa wartości: DisableAntiSpyware)* może zostać wyświetlony następujący wpis wskazujący, że ustawienie Program antywirusowy Microsoft Defender jest wyłączone.

DisableAntiSpyware|-
---|---
Wygrana zapotrz. zasad grupy|Win10-Workstations
Wynik: Sukces|
**Ogólne**|
Akcja|Aktualizacja
**Właściwości**|
Gałąź|HKEY_LOCAL_MACHINE
Ścieżka klucza|SOFTWARE\Policies\Microsoft\Windows Defender
Nazwa wartości|DisableAntiSpyware
Typ wartości|REG_DWORD
Dane wartości|0x1 (1)

###### <a name="if-security-settings-are-implemented-via-registry-key"></a>Jeśli ustawienia zabezpieczeń są zaimplementowane za pośrednictwem klucza rejestru

Raport może zawierać następujący tekst wskazujący, że Program antywirusowy Microsoft Defender jest wyłączony:

> Rejestr (regedit.exe)
>
> HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender DisableAntiSpyware (dword) 1 (hex)

###### <a name="if-security-settings-are-set-in-windows-or-your-windows-server-image"></a>Jeśli ustawienia zabezpieczeń są ustawione na Windows lub w Windows Server

Administrator urojania mógł skonfigurować zasady zabezpieczeń **[DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware)**, lokalnie za pośrednictwem programu *GPEdit.exe*, *LGPO.exe* lub modyfikując rejestr w sekwencji zadań. Identyfikator [zaufanego obrazu można skonfigurować](/windows-hardware/manufacture/desktop/configure-a-trusted-image-identifier-for-windows-defender) dla Program antywirusowy Microsoft Defender.

### <a name="turn-microsoft-defender-antivirus-back-on"></a>Włączanie Program antywirusowy Microsoft Defender z powrotem

Program antywirusowy Microsoft Defender zostanie automatycznie włączyć, jeśli nie jest obecnie aktywne żadne inne oprogramowanie antywirusowe. Musisz całkowicie wyłączyć oprogramowanie antywirusowe innej firmy, aby zapewnić, Program antywirusowy Microsoft Defender działać z pełną funkcjonalnością.

> [!WARNING]
> Rozwiązania sugerujące, że edytuje się wartości startowe programu *Windows Defender* dla *wdboot*, *wdfilter*, *wdnisdrv, wdnissvc* i *windefend* w programie HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services są nieobsługiwane i może wymusić ponowne obrazowanie systemu. 

Tryb pasywny jest dostępny, jeśli rozpoczynasz korzystanie z programu Microsoft Defender for Endpoint oraz oprogramowania antywirusowego innej firmy wraz z programem Program antywirusowy Microsoft Defender. Tryb pasywny umożliwia Program antywirusowy Microsoft Defender samo aktualizowanie plików, ale nie umożliwia korygowania zagrożeń. Ponadto monitorowanie zachowania za pośrednictwem [ochrony w czasie rzeczywistym](configure-real-time-protection-microsoft-defender-antivirus.md) nie jest dostępne w trybie pasywnym, chyba że wdrożono ochronę przed utratą danych w punkcie końcowym [(DLP](/microsoft-365/security/defender-endpoint/information-protection-in-windows-overview) ).

Inna funkcja, znana jako [ograniczone skanowanie okresowe](limited-periodic-scanning-microsoft-defender-antivirus.md), jest dostępna dla użytkowników końcowych, Program antywirusowy Microsoft Defender jest ustawiona na automatyczne wyłączanie. Ta funkcja umożliwia Program antywirusowy Microsoft Defender okresowe skanowanie plików razem z innym oprogramowaniem antywirusowym przy użyciu ograniczonej liczby wykryciy.

> [!IMPORTANT]
> Ograniczone skanowanie okresowe nie jest zalecane w środowiskach przedsiębiorstwa. Funkcje wykrywania, zarządzania i raportowania dostępne podczas Program antywirusowy Microsoft Defender w tym trybie są ograniczane w porównaniu z trybem aktywnym.

### <a name="see-also"></a>Zobacz też

- [Program antywirusowy Microsoft Defender zgodności](microsoft-defender-antivirus-compatibility.md)
- [Program antywirusowy Microsoft Defender w aplikacji Zabezpieczenia Windows aplikacji](microsoft-defender-security-center-antivirus.md)
