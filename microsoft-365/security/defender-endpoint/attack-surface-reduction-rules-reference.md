---
title: Informacje dotyczące reguł zmniejszania powierzchni ataków
description: Zawiera szczegółowe informacje na temat reguł ograniczania powierzchni ataków z jedną regułą.
keywords: Reguły ograniczania powierzchni ataków, ASR, reguły asr, hips, host intrusion prevention system, reguły ochrony, reguły ochrony przed wirusami, ochrona przed wirusami, zasady ochrony przed nadużyciami, reguły zapobiegania powstawaniu wirusów, program Microsoft Defender for Endpoint, konfigurowanie reguł ASR, opis reguły ASR
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar,
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.date: 02/04/2022
ms.openlocfilehash: f6672bfe090458de9ffecae77b656b6f4a8a912d
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2022
ms.locfileid: "63014797"
---
# <a name="attack-surface-reduction-rules-reference"></a>Informacje dotyczące reguł zmniejszania powierzchni ataków

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Ten artykuł zawiera informacje na temat reguł ograniczania ataków:

- [Obsługiwane wersje systemu operacyjnego](#supported-operating-systems)
- [Obsługiwane systemy zarządzania konfiguracją](#supported-configuration-management-systems)
- [Alerty i szczegóły powiadomień dotyczące  per-rule](#per-rule-alert-and-notification-details)
- [Opisy dla poszczególnych reguł](#per-rule-descriptions)
  - Opisy reguł
  - Identyfikatory GUID
  - Nazwy reguł systemu zarządzania konfiguracją

## <a name="public-preview-supported-operating-systems"></a>Publiczna wersja zapoznawcza: Obsługiwane systemy operacyjne

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wypuszczonych produktów, które mogą zostać znacząco zmodyfikowane przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

W poniższej tabeli wymieniono obsługiwane systemy operacyjne dla reguł zmniejszania powierzchni ataków, które są obecnie wstępną wersjią produktu. Reguły są wyświetlane w kolejności alfabetycznej. Jeśli nie zaznaczono inaczej, minimalna kompilacja Windows&nbsp; 10 to wersja 1709 (RS3, kompilacja 16299) lub nowsza. Minimalna kompilacja Windows&nbsp; Server to wersja 1809 lub nowsza.

> [!NOTE]
> Reguły zmniejszania powierzchni ataków w programach Windows&nbsp; Server2012R2&nbsp;&nbsp; i Windows&nbsp; Server2016&nbsp; są dostępne dla urządzeń podłączonych przy użyciu nowoczesnego, ujednoliconego pakietu rozwiązań. Aby uzyskać więcej informacji, zobacz Nowe funkcje w nowoczesnym, ujednoliconym rozwiązaniu dla wersji [Windows Server 2012 R2 i 2016 Preview](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).
>

| Nazwa reguły | &nbsp;Windows Server 2016 <sup>[[1](#fn1)]<sup></sup> | &nbsp;Windows Server 2012 R2 <sup>[[1](#fn1)]<sup></sup> |
|---|:---:|:---:|
|[Blokowanie nadużyć wykorzystywania w celu wykorzystania podpisanych sterowników](#block-abuse-of-exploited-vulnerable-signed-drivers) | T | T |
|[Blokowanie tworzenia procesów podrzędnych przez program Adobe Reader](#block-adobe-reader-from-creating-child-processes) | T | T |
|[Blokowanie tworzenia procesów Office przez wszystkie aplikacje](#block-all-office-applications-from-creating-child-processes) | T | T |
|[Blokowanie wykradania poświadczeń z podsystemu Windows Security Authority (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | T | T |
|[Blokowanie pliku wykonywalnego zawartości z klienta poczty e-mail i poczty internetowej](#block-executable-content-from-email-client-and-webmail) | T | T |
|[Blokuj uruchamianie plików wykonywalnych, jeśli nie spełniają one kryterium listy zaufanej, jego wieku lub wieku.](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | T | T |
|[Blokowanie wykonywania potencjalnie obcofkowanych skryptów](#block-execution-of-potentially-obfuscated-scripts) | T | T |
|[Blokowanie uruchamiania pobranej zawartości wykonywalnego kodu JavaScript lub VBScript](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | T | N |
|[Blokowanie Office tworzenia zawartości wykonywalnego przez aplikacje](#block-office-applications-from-creating-executable-content) | T | T |
|[Blokowanie Office aplikacji ze insektowania kodu do innych procesów](#block-office-applications-from-injecting-code-into-other-processes)  | T | T |
|[Blokowanie Office komunikacji z tworzeniem procesów podrzędnych](#block-office-communication-application-from-creating-child-processes) | T | T |
|[Blokowanie utrwaloności za pośrednictwem subskrypcji zdarzeń usługi WMI](#block-persistence-through-wmi-event-subscription) \* _Wykluczenia plików i folderów nie są obsługiwane._ | N | N |
|[Blokowanie procesów pochodzących z poleceń PSExec i WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) | T | T |
|[Blokowanie niezaufanych i niepodpisanych procesów uruchamianych z usb](#block-untrusted-and-unsigned-processes-that-run-from-usb) | T | T |
|[Blokowanie wywołań interfejsu API Win32 Office makr](#block-win32-api-calls-from-office-macros) | N | N |
|[Korzystanie z zaawansowanej ochrony przed oprogramowaniem wymuszającym okup](#use-advanced-protection-against-ransomware) | T | T |
|  |  |  |

(<a id="fn1">1</a>) Odwołuje się do nowoczesnego, ujednoliconego rozwiązania dla Windows Server 2012 i 2016. Aby uzyskać więcej informacji, [zobacz Onboard Windows Servers to the Defender for Endpoint service](configure-server-endpoints.md) (Wewnechaj serwery serwerów do usługi Defender for Endpoint).

_Zakończ publiczną podgląd: obsługiwane systemy operacyjne_

## <a name="supported-operating-systems"></a>Obsługiwane systemy operacyjne

W poniższej tabeli wymieniono obsługiwane systemy operacyjne dla reguł, które są obecnie ogólnie dostępne. Reguły są wyświetlane w kolejności alfabetycznej.

> [!Note]
>
> Jeśli nie zaznaczono inaczej, minimalna kompilacja Windows&nbsp; 10 to wersja 1709 (RS3, kompilacja 16299) lub nowsza. Minimalna kompilacja Windows&nbsp; Server to wersja 1809 lub nowsza.
>

|Nazwa reguły|&nbsp;Windows 10|&nbsp;Windows Server 2019|&nbsp;Windows Server|
|---|:---:|:---:|:---:|
|[Blokowanie nadużyć wykorzystywania w celu wykorzystania podpisanych sterowników](#block-abuse-of-exploited-vulnerable-signed-drivers) | T | T | T <br><br> wersja 1803 (kanał półroczny) lub nowsza |
|[Blokowanie tworzenia procesów podrzędnych przez program Adobe Reader](#block-adobe-reader-from-creating-child-processes) | Y w wersji 1809 lub nowszej | T | T  <br><br> |
|[Blokowanie tworzenia procesów Office przez wszystkie aplikacje](#block-all-office-applications-from-creating-child-processes) | T | T | T <br><br> |
|[Blokowanie wykradania poświadczeń z podsystemu Windows Security Authority (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | Y w wersji 1803 lub nowszej | T <br><br> | T <br><br> |
|[Blokowanie pliku wykonywalnego zawartości z klienta poczty e-mail i poczty internetowej](#block-executable-content-from-email-client-and-webmail) | T | T <br><br> | T <br><br> |
|[Blokuj uruchamianie plików wykonywalnych, jeśli nie spełniają one kryterium listy zaufanej, jego wieku lub wieku.](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | Y w wersji 1803 lub nowszej | T <br><br> | T <br><br> |
|[Blokowanie wykonywania potencjalnie obcofkowanych skryptów](#block-execution-of-potentially-obfuscated-scripts) | T | T <br><br> | T <br><br> |
|[Blokowanie uruchamiania pobranej zawartości wykonywalnego kodu JavaScript lub VBScript](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | T | T <br><br> | T <br><br> |
|[Blokowanie Office tworzenia zawartości wykonywalnego przez aplikacje](#block-office-applications-from-creating-executable-content) | T | T <br><br> | T <br><br> |
|[Blokowanie Office aplikacji ze insektowania kodu do innych procesów](#block-office-applications-from-injecting-code-into-other-processes)  | T | T <br><br> | T <br><br> |
|[Blokowanie Office komunikacji z tworzeniem procesów podrzędnych](#block-office-communication-application-from-creating-child-processes) | T | T <br><br> | T <br><br> |
|[Blokowanie utrwaloności za pośrednictwem subskrypcji zdarzeń usługi WMI](#block-persistence-through-wmi-event-subscription) <br><br> \*_Wykluczenia plików i folderów nie są obsługiwane._ | Y w wersji 1903 (kompilacja 18362) lub nowszej| T | T <br><br> wersja 1903 (kompilacja 18362) lub nowsza |
|[Blokowanie procesów pochodzących z poleceń PSExec i WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) | Y w wersji 1803 lub nowszej | T <br><br> | T <br><br>  |
|[Blokowanie niezaufanych i niepodpisanych procesów uruchamianych z usb](#block-untrusted-and-unsigned-processes-that-run-from-usb) | T | T <br><br> | T <br><br> |
|[Blokowanie wywołań interfejsu API Win32 Office makr](#block-win32-api-calls-from-office-macros) | T | T <br><br> | T <br><br> |
|[Korzystanie z zaawansowanej ochrony przed oprogramowaniem wymuszającym okup](#use-advanced-protection-against-ransomware) | Y w wersji 1803 lub nowszej | T <br><br> | T <br><br> |
|  |  |  |  |

## <a name="supported-configuration-management-systems"></a>Obsługiwane systemy zarządzania konfiguracją

Poniżej tej tabeli znajdują się linki do informacji o wersjach systemu zarządzania konfiguracją, do których odwołuje się ta tabela.

|Nazwa reguły | Intune | Microsoft Endpoint Manager |Microsoft Endpoint Configuration Manager |<sup>zasady grupy[[1](#fn1)]<sup></sup> | PowerShell<sup>[[1](#fn1)]<sup></sup>  |
|---|:---:|:---:|:---:|:---:|:---:|
|[Blokowanie nadużyć wykorzystywania w celu wykorzystania podpisanych sterowników](#block-abuse-of-exploited-vulnerable-signed-drivers) | T  | Y MEM OMA-URI |   | T  |  T |
|[Blokowanie tworzenia procesów podrzędnych przez program Adobe Reader](#block-adobe-reader-from-creating-child-processes) | T |   | T | T  | T  |
|[Blokowanie tworzenia procesów Office przez wszystkie aplikacje](#block-all-office-applications-from-creating-child-processes) | T |   |T <br><br> CB 1710 | T  | T  |
|[Blokowanie wykradania poświadczeń z podsystemu Windows Security Authority (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | T  |   | T <br><br>CB 1802 | T  | T  |
|[Blokowanie pliku wykonywalnego zawartości z klienta poczty e-mail i poczty internetowej](#block-executable-content-from-email-client-and-webmail) | T |  |T <br><br> CB 1710 | T | T  |
|[Blokuj uruchamianie plików wykonywalnych, jeśli nie spełniają one kryterium listy zaufanej, jego wieku lub wieku.](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | T |   | T <br><br> CB 1802 |  T |  T |
|[Blokowanie wykonywania potencjalnie obcofkowanych skryptów](#block-execution-of-potentially-obfuscated-scripts) | T |   |  T  <br><br> CB 1710 | T  | T  |
|[Blokowanie uruchamiania pobranej zawartości wykonywalnego kodu JavaScript lub VBScript](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | T |   | T <br><br> CB 1710 | T  | T  |
|[Blokowanie Office tworzenia zawartości wykonywalnego przez aplikacje](#block-office-applications-from-creating-executable-content) | T |  |T <br><br> CB 1710 | T  | T  |
|[Blokowanie Office aplikacji ze insektowania kodu do innych procesów](#block-office-applications-from-injecting-code-into-other-processes) | T |  | T <br><br> CB 1710 | T  | T  |
|[Blokowanie Office komunikacji z tworzeniem procesów podrzędnych](#block-office-communication-application-from-creating-child-processes) | T |  |T <br><br> CB 1710 | T  | T  |
|[Blokowanie utrwaloności za pośrednictwem subskrypcji zdarzeń usługi WMI](#block-persistence-through-wmi-event-subscription) |  |  |  |T   | T  |
|[Blokowanie procesów pochodzących z poleceń PSExec i WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) | T |   |   |  T | T  |
|[Blokowanie niezaufanych i niepodpisanych procesów uruchamianych z usb](#block-untrusted-and-unsigned-processes-that-run-from-usb) | T |   |T <br><br> CB 1802  | T  | T  |
|[Blokowanie wywołań interfejsu API Win32 Office makr](#block-win32-api-calls-from-office-macros) | T |   | T <br><br> CB 1710  | T  |  T |
|[Korzystanie z zaawansowanej ochrony przed oprogramowaniem wymuszającym okup](#use-advanced-protection-against-ransomware) | T |   | T <br><br> CB 1802 | T  | T  |
|  |  |  |  |  |  |

  (<a id="fn1">1</a>) Możesz konfigurować reguły ograniczania powierzchni ataków z każdą regułą przy użyciu identyfikatora GUID dowolnej reguły.

- [Menedżer konfiguracji CB 1710](/configmgr/core/servers/manage/updates)
- [Menedżer konfiguracji CB 1802](/configmgr/core/servers/manage/updates)
- [Microsoft Endpoint Manager CB 1710](/configmgr/core/servers/manage/updates)
- [System Center Configuration Manager (SCCM) CB 1710](/configmgr/core/servers/manage/updates) <br>_Już nie można Microsoft Endpoint Configuration Manager._

## <a name="per-rule-alert-and-notification-details"></a>Alerty dotyczące reguły i szczegóły powiadomień

Dla wszystkich reguł w trybie blokowania są generowane wyskakujące powiadomienia. Reguły w żadnym innym trybie nie będą generować wyskakujące powiadomienia

W przypadku reguł z określonym "województwem reguły":

- Reguły ASR z kombinacjami \<ASR Rule, Rule State\> są używane do powierzchni alertów (powiadomień toastowych) w usłudze Microsoft Defender dla punktu końcowego tylko dla urządzeń na poziomie bloków chmury o wysokim poziomie chmury. Urządzenia, które nie są na wysokim poziomie bloków chmury, nie będą generować alertów <reguł asr, reguł i kombinacji> reguł
- EDR alerty są generowane dla reguł ASR w określonych stanach, ale tylko dla urządzeń o wysokim poziomie bloków chmury.

| Nazwa reguły: | Stan reguły: | Generuje alerty w programie EDR? <br> (Tak)&nbsp;\|&nbsp;Nie) | Generuje wyskakujące powiadomienia? <br> (Tak)&nbsp;\|&nbsp;Nie) |
|---|:---:|:---:|:---:|
|   |   |  _Tylko dla urządzeń na poziomie bloków wysokiego chmury_ | _Tylko w trybie blokowania_ |
|[Blokowanie nadużyć wykorzystywania w celu wykorzystania podpisanych sterowników](#block-abuse-of-exploited-vulnerable-signed-drivers) |   | N  | T |
|[Blokowanie tworzenia procesów podrzędnych przez program Adobe Reader](#block-adobe-reader-from-creating-child-processes) | Blokuj  | T <br> Wymaga urządzenia na poziomie bloków wysokiego chmury  | T <br> Wymaga urządzenia na poziomie bloków wysokiego chmury |
|[Blokowanie tworzenia procesów Office przez wszystkie aplikacje](#block-all-office-applications-from-creating-child-processes) |   | N | T |
|[Blokowanie wykradania poświadczeń z podsystemu Windows Security Authority (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) |   | N | T |
|[Blokowanie pliku wykonywalnego zawartości z klienta poczty e-mail i poczty internetowej](#block-executable-content-from-email-client-and-webmail) |   | T <br> Wymaga urządzenia na poziomie bloków wysokiego chmury | T <br> Wymaga urządzenia na poziomie bloków wysokiego chmury |
|[Blokuj uruchamianie plików wykonywalnych, jeśli nie spełniają one kryterium listy zaufanej, jego wieku lub wieku.](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) |   | N | T |
|[Blokowanie wykonywania potencjalnie obcofkowanych skryptów](#block-execution-of-potentially-obfuscated-scripts) |  AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Wymaga urządzenia na poziomie bloków wysokiego chmury  | N \| Y <br> Wymaga urządzenia na poziomie bloków wysokiego chmury |
|[Blokowanie uruchamiania pobranej zawartości wykonywalnego kodu JavaScript lub VBScript](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | Blokuj | T <br> Wymaga urządzenia na poziomie bloków wysokiego chmury  | T <br> Wymaga urządzenia na poziomie bloków wysokiego chmury |
|[Blokowanie Office tworzenia zawartości wykonywalnego przez aplikacje](#block-office-applications-from-creating-executable-content) |   | N | T |
|[Blokowanie Office aplikacji ze insektowania kodu do innych procesów](#block-office-applications-from-injecting-code-into-other-processes)  |   | N | T |
|[Blokowanie Office komunikacji z tworzeniem procesów podrzędnych](#block-office-communication-application-from-creating-child-processes) |  |  N | T |
|[Blokowanie utrwaloności za pośrednictwem subskrypcji zdarzeń usługi WMI](#block-persistence-through-wmi-event-subscription) |  AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Wymaga urządzenia na poziomie bloków wysokiego chmury  | N \| Y <br> Wymaga urządzenia na poziomie bloków wysokiego chmury |
|[Blokowanie procesów pochodzących z poleceń PSExec i WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) |   | N | T |
|[Blokowanie niezaufanych i niepodpisanych procesów uruchamianych z usb](#block-untrusted-and-unsigned-processes-that-run-from-usb) | AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Wymaga urządzenia na poziomie bloków wysokiego chmury  | N \| Y <br> Wymaga urządzenia na poziomie bloków wysokiego chmury |
|[Blokowanie wywołań interfejsu API Win32 Office makr](#block-win32-api-calls-from-office-macros) |   | N | T |
|[Korzystanie z zaawansowanej ochrony przed oprogramowaniem wymuszającym okup](#use-advanced-protection-against-ransomware) | AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Wymaga urządzenia na poziomie bloków wysokiego chmury  | N \| Y <br> Wymaga urządzenia na poziomie bloków wysokiego chmury |
|   |   |   |   |
  
## <a name="asr-rule-modes"></a>Tryby reguły ASR

- **Nieskonfigurowane** **lub Wyłączone**: jest to stan, w którym reguła asR nie została włączona lub została wyłączona. Kod dla tego stanu = 0.
- **Blok**: jest to stan, w którym jest włączona reguła ASR. Kod dla tego stanu to 1.
- **Inspekcja**: jest to stan, w którym jest szacowana reguła asr pod względem jej wpływu na organizację lub środowisko, w którym jest wdrażana. Kod dla tego stanu to 2.
- **Ostrzegaj** Jest to stan, w którym reguła asR jest włączona i zawiera powiadomienie dla użytkownika końcowego, ale zezwala użytkownikowi końcowemu na ominięcie bloku. Kod dla tego stanu to 6.

_Tryb ostrzegania_ to typ trybu blokowania, który ostrzega użytkowników o potencjalnie ryzykownych akcjach. Użytkownicy mogą pominąć komunikat ostrzegawczy o bloku i zezwolić na akcję podstawową. Użytkownicy mogą wybrać **przycisk OK** , aby wymusić blokadę, lub wybrać opcję **obejścia — Odblokuj** — za pośrednictwem wyskakujących powiadomień wyskakujących dla użytkownika końcowego generowanych w momencie blokowania. Po odblokowaniu ostrzeżenia operacja jest dozwolona do chwili kolejnego wystąpienia komunikatu ostrzegawczego, kiedy to użytkownik końcowy będzie musiał ponownie sformułować akcję.

Po kliknięciu przycisku zezwalania blok będzie pomijany przez 24 godziny. Po upływie 24 godzin użytkownik końcowy będzie musiał ponownie zezwolić na zablokowanie. Tryb ostrzegania dla reguł ASR jest obsługiwany tylko dla urządzeń RS5+ (1809+). Jeśli do reguł ASR na urządzeniach ze starszymi wersjami zostanie przypisana reguła obejścia, reguła będzie w trybie zablokowanym.

Możesz również ustawić regułę w trybie ostrzegania za pośrednictwem programu PowerShell, po prostu AttackSurfaceReductionRules_Actions jako "Ostrzegaj". Przykład:

```powershell
-command "& {&'Add-MpPreference' -AttackSurfaceReductionRules_Ids 56a863a9-875e-4185-98a7-b882c64b5ce5 -AttackSurfaceReductionRules_Actions Warn"} 
```

## <a name="per-rule-descriptions"></a>Na opisy reguł

### <a name="block-abuse-of-exploited-vulnerable-signed-drivers"></a>Blokowanie nadużyć wykorzystywania w celu wykorzystania podpisanych sterowników

Ta reguła zapobiega napisaniu przez aplikację sterownika, który jest podatny na dostęp do dysku. Lokalne aplikacje, które mają wystarczające uprawnienia do uzyskiwania dostępu do tego kernel, \-  \- mogą korzystać ze sterowników, które są wild- i podpisane. Narażone na podpisane sterowniki umożliwiają atakującym wyłączenie lub obejście rozwiązań zabezpieczeń, co ostatecznie prowadzi do naruszenia bezpieczeństwa systemu.

Reguła **Blokuj nadużycie wykorzystywania narażonych** na zagrożenia podpisanych sterowników nie blokuje ładowania sterownika, który już istnieje w systemie.

> [!NOTE]
>
> Tę regułę można skonfigurować przy użyciu narzędzia OMA-URI MEM. Zobacz [MEM OMA-URI](enable-attack-surface-reduction.md#mem) , aby uzyskać informacje na temat konfigurowania reguł niestandardowych.
>
> Tę regułę można także skonfigurować przy użyciu programu [PowerShell](enable-attack-surface-reduction.md#powershell).
>
> Aby zbadać sterownik, użyj tej witryny sieci Web, aby [przesłać sterownik do analizy](https://www.microsoft.com/en-us/wdsi/driversubmission).

<!--The above link is the 'only link' that exists for having drivers examined. The 'en-us' component is required to make the link work. Any alterations to this link will result in a 404.
-->

Nazwa usługi Intune: `Block abuse of exploited vulnerable signed drivers` (jeszcze niedostępne)

Menedżer konfiguracji: Jeszcze niedostępne
  
Identyfikator GUID:  `56a863a9-875e-4185-98a7-b882c64b5ce5`

<!-- Hide this intro with no subsequent list items
Advanced hunting action type:
-->

<!-- 
Dependencies:
-->

### <a name="block-adobe-reader-from-creating-child-processes"></a>Blokowanie tworzenia procesów podrzędnych przez program Adobe Reader

Ta reguła zapobiega atakom, blokując proces tworzenia procesów przez program Adobe Reader.

W ramach technik społecznościowych lub luk w zabezpieczeniach złośliwe oprogramowanie może pobierać i uruchamiać łady, a także wymykać się z programu Adobe Reader. Blokując procesy podrzędne generowane przez program Adobe Reader, nie można rozpowszechniać złośliwego oprogramowania próbującego użyć go jako wektora.

Nazwa usługi Intune: `Process creation from Adobe Reader (beta)`

Menedżer konfiguracji: Jeszcze niedostępne

Identyfikator GUID: `7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c`

Zaawansowany typ akcji chłoniania:

- AsrAdobeReaderChildProcessAudited
- AsrAdobeReaderChildProcessBlocked

Zależności: MDAV

### <a name="block-all-office-applications-from-creating-child-processes"></a>Blokowanie tworzenia procesów Office przez wszystkie aplikacje

Ta reguła blokuje Office tworzenia procesów podrzędnych przez aplikacje. Office obejmują programy Word, Excel, PowerPoint, OneNote i Access.

Tworzenie złośliwych procesów dzieci to często strategia złośliwego oprogramowania. Złośliwe oprogramowanie, które wykorzystujące Office w wektorze często uruchamia makra VBA i wykorzystuje kod do pobierania i próby uruchomienia większej liczby plików. Jednak niektóre legalne aplikacje firmowe mogą również generować procesy podrzędne w celu ich zasyłowania. na przykład w celu skonfigurowania ustawień rejestru za pomocą wiersza polecenia lub programu PowerShell.

Nazwa usługi Intune: `Office apps launching child processes`

Menedżer konfiguracji: `Block Office application from creating child processes`

Identyfikator GUID: `d4f940ab-401b-4efc-aadc-ad5f3c50688a`

Zaawansowany typ akcji chłoniania:

- AsrOfficeChildProcessAudited
- AsrOfficeChildProcessBlocked

Zależności: MDAV

### <a name="block-credential-stealing-from-the-windows-local-security-authority-subsystem"></a>Blokowanie kradzieży poświadczeń z podsystemu Windows Security Authority

Ta reguła pomaga zapobiec kradzieży poświadczeń, blokując usługę podsystemu Local Security Authority (LSASS).

LSASS uwierzytelnia użytkowników, którzy logują się na Windows komputerze. Ochrona poświadczeń programu Microsoft Defender Windows zazwyczaj uniemożliwia próbie wyodrębnienia poświadczeń z usługi LSASS. Jednak niektóre organizacje nie mogą włączyć funkcji Credential Guard na wszystkich swoich komputerach ze względu na problemy ze zgodnością z niestandardowymi sterownikami kart inteligentnych lub innymi programami, które są ładowane do lokalnego urzędu zabezpieczeń (LSA). W takich przypadkach atakujący mogą używać narzędzi do łamania, takich jak Mimikatz, do ześmiecania haseł w postaci czytelnego tekstu i skrótów NTLM z LSASS.

> [!NOTE]
> W niektórych aplikacjach kod ten wylicza wszystkie uruchomione procesy i próbuje je otwierać ze wszystkimi uprawnieniami. Ta reguła odrzuca otwartą akcję otwierania procesu aplikacji i zapisuje szczegóły w dzienniku zdarzeń zabezpieczeń. Ta reguła może generuje mnóstwo szumów. Jeśli masz aplikację, która po prostu wylicza LSASS, ale nie ma rzeczywistego wpływu na funkcjonalność, nie musisz dodawać jej do listy wykluczeń. Sam wpis w dzienniku zdarzeń nie musi wskazywać na złośliwe zagrożenie.
  
> [!IMPORTANT]
> Domyślny stan reguły zmniejszania powierzchni ataków (ASR, Attack Surface Reduction) "Blokuj kradzież poświadczeń z podsystemu Windows Local Security Authority (lsass.exe)" zmieni się z Nieskonfigurowany na  Skonfigurowany, a tryb domyślny **ustawiony na Zablokuj**. Wszystkie pozostałe reguły asr pozostaną w stanie domyślnym: **Nieskonfigurowane**. Dodatkowa logika filtrowania została już włączona do reguły w celu zmniejszenia powiadomień użytkowników końcowych. Klienci mogą skonfigurować tryb **inspekcji, ostrzegania** lub wyłączenia, co spowoduje zastąpienie trybu domyślnego.  Funkcjonalność tej reguły jest taka sama niezależnie od tego, czy reguła jest skonfigurowana w trybie domyślnym, czy też tryb blokowania jest włączany ręcznie.  

Nazwa usługi Intune: `Flag credential stealing from the Windows local security authority subsystem`

Menedżer konfiguracji: `Block credential stealing from the Windows local security authority subsystem`

Identyfikator GUID: `9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2`

Zaawansowany typ akcji chłoniania:

- AsrLsassCredentialTheftAudited
- AsrLsassCredentialTheftBlocked

Zależności: MDAV

### <a name="block-executable-content-from-email-client-and-webmail"></a>Blokowanie pliku wykonywalnego zawartości z klienta poczty e-mail i poczty internetowej

Ta reguła blokuje uruchamianie następujących typów plików z wiadomości e-mail otwieranych w aplikacji Microsoft Outlook lub Outlook.com i innych popularnych dostawców poczty internetowej:

- Pliki wykonywalne (na przykład .exe, .dll lub scr)
- Pliki skryptów (na przykład pliki programu PowerShell ps, Visual Basic vbs lub plik .js JavaScript)

Nazwa usługi Intune: `Execution of executable content (exe, dll, ps, js, vbs, etc.) dropped from email (webmail/mail client) (no exceptions)`

Microsoft Endpoint Manager:`Block executable content from email client and webmail`

Identyfikator GUID: `be9ba2d9-53ea-4cdc-84e5-9b1eeee46550`

Zaawansowany typ akcji chłoniania:

- AsrExecutableEmailContentAudited
- AsrExecutableEmailContentBlocked

Zależności: MDAV

> [!NOTE]
> Reguła **Blokuj zawartość wykonywaną z klienta poczty e-mail** i poczty internetowej ma następujące opisy alternatywne, w zależności od tego, której aplikacji używasz:
>
> - Intune (Profile konfiguracji): Wykonywanie zawartości wykonywanej (exe, dll, ps, js, vbs itp.) nie jest wykonywane z poczty e-mail (klient poczty internetowej/poczty) (bez wyjątków).
> - Endpoint Manager: Blokuj plik wykonywalny pobierania zawartości z klientów poczty e-mail i poczty internetowej.
> - zasady grupy: Blokuj wykonywaną zawartość z klienta poczty e-mail i poczty internetowej.

### <a name="block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion"></a>Blokuj uruchamianie plików wykonywalnych, jeśli nie spełniają one kryterium listy zaufanej, jego wieku lub wieku.

Ta reguła blokuje uruchamianie plików wykonywalnych, takich .exe, .dll lub scr. Dlatego uruchamianie niezaufanych lub nieznanych plików wykonywalnych może być ryzykowne, ponieważ początkowo nie można wyczyścić plików, które są złośliwe.

> [!IMPORTANT]
> Aby użyć [tej reguły, należy włączyć ochronę w](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) chmurze.
>
> Reguła **Blokuj uruchamianie plików** wykonywalnych, jeśli nie spełniają one określonego kryterium listy wskazanego jako wiek lub zaufany, a identyfikator GUID `01443614-cd74-433a-b99e-2ecdc07bfc25` należy do firmy Microsoft i nie jest określony przez administratorów. Ta reguła korzysta z ochrony chmurowej w celu regularnego aktualizowania listy zaufanych.
>
> Możesz określić poszczególne pliki lub foldery (używając ścieżek folderów lub w pełni kwalifikowanych nazw zasobów), ale nie możesz określić, których reguł lub wykluczeń należy użyć.

Nazwa usługi Intune: `Executables that don't meet a prevalence, age, or trusted list criteria`

Menedżer konfiguracji: `Block executable files from running unless they meet a prevalence, age, or trusted list criteria`

Identyfikator GUID: `01443614-cd74-433a-b99e-2ecdc07bfc25`

Zaawansowany typ akcji chłoniania:

- AsrUntrustedExecutableAudited
- AsrUntrustedExecutableBlocked

Zależności: MDAV, Ochrona w chmurze

### <a name="block-execution-of-potentially-obfuscated-scripts"></a>Blokowanie wykonywania potencjalnie obcofkowanych skryptów

Ta reguła wykrywa podejrzane właściwości w scenariuszu obwiedni.

Wykorzystanie skryptów to technika często stosowana zarówno do ukrywania własności intelektualnej, jak i używania aplikacji w celu ukrycia własności intelektualnej i zmniejszenia czasu ładowania skryptów. Autorzy złośliwego oprogramowania używają także funkcji zaszytania, aby utrudnić odczytywanie złośliwego kodu, co zapobiega kontroli osób ludzkich i oprogramowania zabezpieczającego.

Nazwa usługi Intune: `Obfuscated js/vbs/ps/macro code`

Menedżer konfiguracji: `Block execution of potentially obfuscated scripts`

Identyfikator GUID: `5beb7efe-fd9a-4556-801d-275e5ffc04cc`

Zaawansowany typ akcji chłoniania:

- AsrObfuscatedScriptAudited
- AsrObfuscatedScriptBlocked

Zależności: MDAV, AMSI

### <a name="block-javascript-or-vbscript-from-launching-downloaded-executable-content"></a>Blokowanie uruchamiania pobranej zawartości wykonywalnego kodu JavaScript lub VBScript

Ta reguła zapobiega uruchamianiu potencjalnie złośliwej pobranej zawartości przez skrypty. Złośliwe oprogramowanie napisane w języku JavaScript lub VBScript często działa jako narzędzie do pobierania w celu pobierania i uruchamiania innego złośliwego oprogramowania z Internetu.

Mimo że nie jest to typowe, aplikacje firmowe czasami używają skryptów do pobierania i uruchamiania instalatorów.

Nazwa usługi Intune: `js/vbs executing payload downloaded from Internet (no exceptions)`

Menedżer konfiguracji: `Block JavaScript or VBScript from launching downloaded executable content`

Identyfikator GUID: `d3e037e1-3eb8-44c8-a917-57927947596d`

Zaawansowany typ akcji chłoniania:

- AsrScriptExecutableDownloadAudited
- AsrScriptExecutableDownloadBlocked

Zależności: MDAV, AMSI

### <a name="block-office-applications-from-creating-executable-content"></a>Blokowanie Office tworzenia zawartości wykonywalnego przez aplikacje

Ta reguła zapobiega tworzeniu potencjalnie złośliwej zawartości wykonywanej przez Office, w tym programów Word, Excel i PowerPoint, przez blokowanie złośliwego kodu na dysku.

Złośliwe oprogramowanie, które Office w formacie wektorowym, może próbować się Office i zapisywać złośliwe składniki na dysku. Te złośliwe składniki mogą wystarczyć po ponownym uruchomieniu komputera i są zachowywane w systemie. Dlatego ta reguła będzie chronić się przed wspólną techniką utrwaloności.

Nazwa usługi Intune: `Office apps/macros creating executable content`

Nazwa sccm: `Block Office applications from creating executable content`

Identyfikator GUID: `3b576869-a4ec-4529-8536-b80a7769e899`

Zaawansowany typ akcji chłoniania:

- AsrExecutableOfficeContentAudited
- AsrExecutableOfficeContentBlocked

Zależności: MDAV, RPC

### <a name="block-office-applications-from-injecting-code-into-other-processes"></a>Blokowanie Office aplikacji ze insektowania kodu do innych procesów

Ta reguła blokuje próby podania kodu z Office do innych procesów.

Atakujący mogą próbować używać aplikacji Office w celu przeprowadzenia migracji złośliwego kodu do innych procesów poprzez wykorzystanie kodu, więc kod może zostać maskowanie jako czystego procesu.

Nie ma żadnych znanych uzasadnionych celów biznesowych do stosowania podania kodu.

Ta reguła dotyczy programu Word, Excel i PowerPoint.

Nazwa usługi Intune: `Office apps injecting code into other processes (no exceptions)`

Menedżer konfiguracji: `Block Office applications from injecting code into other processes`

Identyfikator GUID: `75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84`

Zaawansowany typ akcji chłoniania:

- AsrOfficeProcessInjectionAudited
- AsrOfficeProcessInjectionBlocked

Zależności: MDAV

### <a name="block-office-communication-application-from-creating-child-processes"></a>Blokowanie Office komunikacji z tworzeniem procesów podrzędnych

Ta reguła zapobiega Outlook procesom podrzędnym, jednocześnie pozwalając na tworzenie legalnych Outlook funkcji.

Ta reguła chroni przed atakami ze strony inżynierów społecznościowych i zapobiega wykorzystywaniu luk w zabezpieczeniach kodu w Outlook. Chroni także przed Outlook i [](https://blogs.technet.microsoft.com/office365security/defending-against-rules-and-forms-injection/) wykorzystywaniem formularzy przez atakujących w przypadku naruszenia poświadczeń użytkownika.

> [!NOTE]
> Ta reguła blokuje porady dotyczące zasad DLP i porady dotyczące narzędzi w programie Outlook. Ta reguła dotyczy tylko Outlook i Outlook.com.

Nazwa usługi Intune: `Process creation from Office communication products (beta)`

Menedżer konfiguracji: Niedostępne

Identyfikator GUID: `26190899-1602-49e8-8b27-eb1d0a1ce869`

Zaawansowany typ akcji chłoniania:

- AsrOfficeCommAppChildProcessAudited
- AsrOfficeCommAppChildProcessBlocked

Zależności: MDAV

### <a name="block-persistence-through-wmi-event-subscription"></a>Blokowanie utrwaloności za pośrednictwem subskrypcji zdarzeń usługi WMI

Ta reguła zapobiega nadużywaniu funkcji WMI przez złośliwe oprogramowanie do osiągnięcia poziomu uporczywości na urządzeniu.

> [!IMPORTANT]
> Wykluczenia plików i folderów nie mają zastosowania do tej reguły ograniczania powierzchni ataków.

Zagrożenia bez plików wykorzystują różne taktyki służące do ukrywania się, aby nie być widocznym w systemie plików i aby zyskać okresową kontrolę wykonywania. Niektóre zagrożenia mogą nadużyć dla repozytorium WMI i modelu zdarzeń w celu ukrycia.

Nazwa usługi Intune: Niedostępne

Menedżer konfiguracji: Niedostępne

Identyfikator GUID: `e6db77e5-3df2-4cf1-b95a-636979351e5b`

Zaawansowany typ akcji chłoniania:

- AsrPersistenceThroughWmiAudited
- AsrPersistenceThroughWmiBlocked

Zależności: MDAV, RPC

### <a name="block-process-creations-originating-from-psexec-and-wmi-commands"></a>Blokowanie procesów pochodzących z poleceń PSExec i WMI

Ta reguła blokuje uruchamianie procesów utworzonych za pośrednictwem programu [PsExec](/sysinternals/downloads/psexec) [i aplikacji WMI](/windows/win32/wmisdk/about-wmi) . Zarówno PsExec, jak i WMI, mogą zdalnie wykonywać kod, dlatego istnieje ryzyko, że złośliwe oprogramowanie będzie używać tej funkcji w celu poleceń i kontroli lub rozpowszechniania zainfekowania sieci organizacji.

> [!WARNING]
> Tej reguły należy używać tylko wtedy, gdy zarządzasz urządzeniami za pomocą usługi [Intune](/intune) lub innego rozwiązania MDM. Ta reguła jest niezgodna z zarządzaniem za pośrednictwem programu [Microsoft Endpoint Configuration Manager](/configmgr) ponieważ blokuje poprawne działanie Menedżer konfiguracji WMI.

Nazwa usługi Intune: `Process creation from PSExec and WMI commands`

Menedżer konfiguracji: Nie dotyczy

Identyfikator GUID: `d1e49aac-8f56-4280-b9ba-993a6d77406c`

Zaawansowany typ akcji chłoniania:

- AsrPsexecWmiChildProcessAudited
- AsrPsexecWmiChildProcessBlocked

Zależności: MDAV

### <a name="block-untrusted-and-unsigned-processes-that-run-from-usb"></a>Blokowanie niezaufanych i niepodpisanych procesów uruchamianych z usb

Przy użyciu tej reguły administratorzy mogą zapobiec uruchamianiu niepodpisanych lub niezaufanych plików wykonywalnych z wymiennych dysków USB, w tym kart SD. Blokowane typy plików obejmują pliki wykonywalne (na przykład .exe, .dll lub scr)

Nazwa usługi Intune: `Untrusted and unsigned processes that run from USB`

Menedżer konfiguracji: `Block untrusted and unsigned processes that run from USB`

Identyfikator GUID: `b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4`

Zaawansowany typ akcji chłoniania:

- AsrUntrustedUsbProcessAudited
- AsrUntrustedUsbProcessBlocked

Zależności: MDAV

### <a name="block-win32-api-calls-from-office-macros"></a>Blokowanie wywołań interfejsu API Win32 Office makr

Ta reguła zapobiega wywoływaniu przez makra VBA interfejsów API Win32.

Office VBA włącza wywołania interfejsu API Win32. Złośliwe oprogramowanie może używać tej funkcji, na przykład wywoływania interfejsów [API Win32](https://www.microsoft.com/security/blog/2018/09/12/office-vba-amsi-parting-the-veil-on-malicious-macros/) w celu uruchomienia złośliwego kodu powłoki bez zapisywania niczego bezpośrednio na dysku. Większość organizacji nie polega na możliwości dzwonienia do interfejsów API Win32 w ich codziennie działającej, nawet jeśli używają makr w inny sposób.

Obsługiwane systemy operacyjne:

- [Windows 10, wersja 1709](/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Server, wersja 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Menedżer konfiguracji CB 1710](/configmgr/core/servers/manage/updates)

Nazwa usługi Intune: `Win32 imports from Office macro code`

Menedżer konfiguracji: `Block Win32 API calls from Office macros`

Identyfikator GUID: `92e97fa1-2edf-4476-bdd6-9dd0b4dddc7b`

Zaawansowany typ akcji chłoniania:

- AsrOfficeMacroWin32ApiCallsAudited
- AsrOfficeMacroWin32ApiCallsBlocked

Zależności: MDAV, AMSI

### <a name="use-advanced-protection-against-ransomware"></a>Korzystanie z zaawansowanej ochrony przed oprogramowaniem wymuszającym okup

Ta reguła zapewnia dodatkową warstwę ochrony przed oprogramowaniem wymuszającym okup. Używa on zarówno heuristics klienta, jak i chmury, aby określić, czy plik przypominający oprogramowanie wymuszające okup. Ta reguła nie powoduje blokowania plików, które mają co najmniej jedną z następujących cech:

- Plik ten został już znaleziony jako nieuchmurny w chmurze firmy Microsoft.
- Plik jest prawidłowym podpisanym plikiem.
- Plik jest na tyle rozpowszechniony, że nie można go uznać za oprogramowanie wymuszające okup.

Reguła zwykle ma błąd z boku ostrożności, aby zapobiec wymuszaniu okupu.

> [!NOTE]
> Aby użyć [tej reguły, należy włączyć ochronę w](enable-cloud-protection-microsoft-defender-antivirus.md) chmurze.

Nazwa usługi Intune: `Advanced ransomware protection`

Menedżer konfiguracji: `Use advanced protection against ransomware`

Identyfikator GUID: `c1db55ab-c21a-4637-bb3f-a12568109d35`

Zaawansowany typ akcji chłoniania:

- AsrRansomwareAudited
- AsrRansomwareBlocked

Zależności: MDAV, Ochrona w chmurze
