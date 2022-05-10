---
title: Dokumentacja reguł zmniejszania obszaru podatnego na ataki
description: Wyświetla szczegółowe informacje o regułach zmniejszania obszaru ataków na podstawie reguł.
keywords: Reguły zmniejszania obszaru ataków, ASR, reguły asr, biodra, system zapobiegania włamaniom do hostów, reguły ochrony, reguły antyeksploatowania, antyeksploatacja, reguły wykorzystujące luki w zabezpieczeniach, reguły zapobiegania zakażeniom, Ochrona punktu końcowego w usłudze Microsoft Defender, konfigurowanie reguł asr, opis reguł asr
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
ms.openlocfilehash: 2f76a8ec53d6f7c809ed9f6612f2c8abf7388d1b
ms.sourcegitcommit: f723ebbc56db8013598a88b0d7f13214d9d3eb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2022
ms.locfileid: "65294783"
---
# <a name="attack-surface-reduction-rules-reference"></a>Dokumentacja reguł zmniejszania obszaru podatnego na ataki

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Program antywirusowy Microsoft Defender

**Platformy:**

- System Windows

Ten artykuł zawiera informacje o regułach zmniejszania ataków:

- [Obsługiwane wersje systemu operacyjnego](#supported-operating-systems)
- [Obsługiwane systemy zarządzania konfiguracją](#supported-configuration-management-systems)
- [Szczegóły alertu i powiadomienia dla reguły](#per-rule-alert-and-notification-details)
- [Macierz reguł i identyfikatorów GUID usługi ASR](#asr-rules-and-guids-matrix)
- [Tryby reguł usługi ASR](#asr-rule-modes)
- [Opisy reguł](#per-rule-descriptions)
  - Opisy reguł
  - Nazwy reguł systemu zarządzania konfiguracją

## <a name="supported-operating-systems"></a>Obsługiwane systemy operacyjne

Poniższa tabela zawiera listę obsługiwanych systemów operacyjnych dla reguł, które są obecnie udostępniane do ogólnej dostępności. Reguły są wymienione w kolejności alfabetycznej w tej tabeli.

> [!Note]
>
> O ile nie wskazano inaczej, minimalna kompilacja&nbsp; Windows 10 to wersja 1709 (RS3, kompilacja 16299) lub nowsza; minimalna kompilacja&nbsp; Windows Server to wersja 1809 lub nowsza.
>
> Reguły zmniejszania obszaru ataków w Windows&nbsp; Server2012R2&nbsp;&nbsp; i Windows&nbsp; Server2016&nbsp; są dostępne dla urządzeń dołączonych przy użyciu nowoczesnego ujednoliconego pakietu rozwiązań. Aby uzyskać więcej informacji, zobacz [New functionality in the modern unified solution for Windows Server 2012 R2 and 2016 Preview (Nowe funkcje w nowoczesnym ujednoliconym rozwiązaniu dla Windows Server 2012 R2 i 2016 Preview](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)).

| Nazwa reguły| &nbsp;Windows 11 <br>i<br> &nbsp;Windows 10 | &nbsp;Windows Server <br> 2022 <br>i<br>  &nbsp;Windows Server <br> 2019 | Serwer z systemem Windows | &nbsp;Windows Server <br> 2016 <br> <sup>[[1, 2](#fn1)]<sup></sup> | &nbsp;Windows Server <br> 2012R2&nbsp; <br> <sup>[[1, 2](#fn1)]<sup></sup> |
|:---|:---:|:---:|:---:|:---:|:---:|
| [Blokowanie nadużyć wobec wykorzystywanych, narażonych na zagrożenia podpisanych kierowców](#block-abuse-of-exploited-vulnerable-signed-drivers) | T | T | T <br> wersja 1803 (półroczny kanał) lub nowszy | T | T |
| [Zablokuj programowi Adobe Reader tworzenie procesów podrzędnych](#block-adobe-reader-from-creating-child-processes) | Wersja Y 1809 lub nowsza | T | T | T | T |
| [Blokowanie tworzenia procesów podrzędnych przez wszystkie aplikacje Office](#block-all-office-applications-from-creating-child-processes) | T | T | T | T | T |
| [Blokuj kradzież poświadczeń z podsystemu Windows lokalnego urzędu zabezpieczeń (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | T <br> wersja 1803 lub nowsza | T | T | T | T |
| [Blokuj zawartość wykonywalną z klienta poczty e-mail i poczty internetowej](#block-executable-content-from-email-client-and-webmail) | T | T | T | T | T |
| [Blokuj uruchamianie plików wykonywalnych, chyba że spełniają kryterium występowania, wieku lub listy zaufanych](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | T <br> wersja 1803 lub nowsza | T | T | T | T |
| [Blokuj wykonywanie potencjalnie zaciemnionych skryptów](#block-execution-of-potentially-obfuscated-scripts) | T | T | T | T | T |
| [Blokowanie uruchamiania pobranej zawartości wykonywalnej w języku JavaScript lub VBScript](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | T | T | T | N | N |
| [Blokowanie tworzenia zawartości wykonywalnej przez aplikacje Office](#block-office-applications-from-creating-executable-content) | T | T | T | T | T |
| [Blokuj Office aplikacjom wstrzykiwanie kodu do innych procesów](#block-office-applications-from-injecting-code-into-other-processes)  | T | T | T | T | T |
| [Blokowanie tworzenia procesów podrzędnych przez aplikację komunikacji Office](#block-office-communication-application-from-creating-child-processes) | T | T | T | T | T |
| [Blokuj trwałość za pośrednictwem subskrypcji zdarzeń WMI](#block-persistence-through-wmi-event-subscription) <br> \*_Wykluczenia plików i folderów nie są obsługiwane._ | T <br> wersja 1903 (kompilacja 18362) lub nowsza | T | T <br> wersja 1903 (kompilacja 18362) lub nowsza | N | N |
| [Blokuj tworzenie procesów pochodzących z poleceń PSExec i WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) | T <br> wersja 1803 lub nowsza | T | T | T | T |
| [Blokuj niezaufane i niepodpisane procesy uruchamiane z portu USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | T | T | T | T | T |
| [Blokuj wywołania interfejsu API Win32 z makr Office](#block-win32-api-calls-from-office-macros) | T | T | T | N | N |
| [Korzystanie z zaawansowanej ochrony przed oprogramowaniem wymuszającym okup](#use-advanced-protection-against-ransomware) | T <br> wersja 1803 lub nowsza | T | T | T | T |

(<a id="fn1">1</a>) Odnosi się do nowoczesnego ujednoliconego rozwiązania dla Windows Server 2012 i 2016 roku. Aby uzyskać więcej informacji, zobacz [Dołączanie serwerów Windows do usługi Defender for Endpoint](configure-server-endpoints.md).

(<a id="fn1">2</a>) W przypadku Windows&nbsp; Server 2016 i Windows&nbsp; Server 2012R2&nbsp; minimalna wymagana wersja Microsoft Endpoint Configuration Manager to wersja 2111.

## <a name="supported-configuration-management-systems"></a>Obsługiwane systemy zarządzania konfiguracją

Poniżej tej tabeli znajdują się linki do informacji o wersjach systemu zarządzania konfiguracją, do których odwołuje się ta tabela.

|Nazwa reguły | Intune | Microsoft Endpoint Manager |Microsoft Endpoint Configuration Manager |<sup>zasady grupy[[1](#fn1)]<sup></sup> | PowerShell<sup>[[1](#fn1)]<sup></sup>  |
|---|:---:|:---:|:---:|:---:|:---:|
|[Blokowanie nadużyć wobec wykorzystywanych, narażonych na zagrożenia podpisanych kierowców](#block-abuse-of-exploited-vulnerable-signed-drivers) | T  | Y MEM OMA-URI |   | T  |  T  |
|[Zablokuj programowi Adobe Reader tworzenie procesów podrzędnych](#block-adobe-reader-from-creating-child-processes) | T |   |  | T  | T  |
|[Blokowanie tworzenia procesów podrzędnych przez wszystkie aplikacje Office](#block-all-office-applications-from-creating-child-processes) | T |   |T <br><br> CB 1710 | T  | T  |
|[Blokuj kradzież poświadczeń z podsystemu Windows lokalnego urzędu zabezpieczeń (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | T  |   | T <br><br>CB 1802 | T  | T  |
|[Blokuj zawartość wykonywalną z klienta poczty e-mail i poczty internetowej](#block-executable-content-from-email-client-and-webmail) | T |  |T <br><br> CB 1710 | T | T  |
|[Blokuj uruchamianie plików wykonywalnych, chyba że spełniają kryterium występowania, wieku lub listy zaufanych](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | T |   | T <br><br> CB 1802 |  T |  T |
|[Blokuj wykonywanie potencjalnie zaciemnionych skryptów](#block-execution-of-potentially-obfuscated-scripts) | T |   |  T  <br><br> CB 1710 | T  | T  |
|[Blokowanie uruchamiania pobranej zawartości wykonywalnej w języku JavaScript lub VBScript](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | T |   | T <br><br> CB 1710 | T  | T  |
|[Blokowanie tworzenia zawartości wykonywalnej przez aplikacje Office](#block-office-applications-from-creating-executable-content) | T |  |T <br><br> CB 1710 | T  | T  |
|[Blokuj Office aplikacjom wstrzykiwanie kodu do innych procesów](#block-office-applications-from-injecting-code-into-other-processes) | T |  | T <br><br> CB 1710 | T  | T  |
|[Blokowanie tworzenia procesów podrzędnych przez aplikację komunikacji Office](#block-office-communication-application-from-creating-child-processes) | T |  |T <br><br> CB 1710 | T  | T  |
|[Blokuj trwałość za pośrednictwem subskrypcji zdarzeń WMI](#block-persistence-through-wmi-event-subscription) |  |  |  |T   | T  |
|[Blokuj tworzenie procesów pochodzących z poleceń PSExec i WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) | T |   |   |  T | T  |
|[Blokuj niezaufane i niepodpisane procesy uruchamiane z portu USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | T |   |T <br><br> CB 1802  | T  | T  |
|[Blokuj wywołania interfejsu API Win32 z makr Office](#block-win32-api-calls-from-office-macros) | T |   | T <br><br> CB 1710  | T  |  T |
|[Korzystanie z zaawansowanej ochrony przed oprogramowaniem wymuszającym okup](#use-advanced-protection-against-ransomware) | T |   | T <br><br> CB 1802 | T  | T  |

  (<a id="fn1">1</a>) Reguły zmniejszania obszaru ataków można skonfigurować dla każdej reguły przy użyciu identyfikatora GUID dowolnej reguły.

- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)
- [Configuration Manager CB 1802](/configmgr/core/servers/manage/updates)
- [Microsoft Endpoint Manager CB 1710](/configmgr/core/servers/manage/updates)
- [System Center Configuration Manager (SCCM) CB 1710](/configmgr/core/servers/manage/updates) <br>_Program SCCM jest teraz Microsoft Endpoint Configuration Manager._

## <a name="per-rule-alert-and-notification-details"></a>Szczegóły alertu i powiadomienia dla reguły

Powiadomienia wyskakujące są generowane dla wszystkich reguł w trybie bloku. Reguły w żadnym innym trybie nie będą generować wyskakujących powiadomień

W przypadku reguł z określonym stanem reguły:

- Reguły usługi ASR z \<ASR Rule, Rule State\> kombinacjami służą do wyskakujących alertów (wyskakujących powiadomień) na Ochrona punktu końcowego w usłudze Microsoft Defender tylko dla urządzeń na wysokim poziomie bloków w chmurze. Urządzenia nie na wysokim poziomie bloków w chmurze nie będą generować alertów dla żadnych kombinacji <asr rule, rule state>
- EDR alerty są generowane dla reguł usługi ASR w określonych stanach, ale tylko dla urządzeń na wysokim poziomie bloku chmury.

| Nazwa reguły: | Stan reguły: | Generuje alerty w EDR? <br> (Tak&nbsp;\|&nbsp;Nie) | Generuje powiadomienia wyskakujące? <br> (Tak&nbsp;\|&nbsp;Nie) |
|---|:---:|:---:|:---:|
|   |   |  _Tylko w przypadku urządzeń na wysokim poziomie bloków w chmurze_ | _Tylko w trybie bloku_ |
|[Blokowanie nadużyć wobec wykorzystywanych, narażonych na zagrożenia podpisanych kierowców](#block-abuse-of-exploited-vulnerable-signed-drivers) |   | N  | T |
|[Zablokuj programowi Adobe Reader tworzenie procesów podrzędnych](#block-adobe-reader-from-creating-child-processes) | Blokuj  | T <br> Wymaga urządzenia na wysokim poziomie bloków w chmurze  | T <br> Wymaga urządzenia na wysokim poziomie bloków w chmurze |
|[Blokowanie tworzenia procesów podrzędnych przez wszystkie aplikacje Office](#block-all-office-applications-from-creating-child-processes) |   | N | T |
|[Blokuj kradzież poświadczeń z podsystemu Windows lokalnego urzędu zabezpieczeń (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) |   | N | T |
|[Blokuj zawartość wykonywalną z klienta poczty e-mail i poczty internetowej](#block-executable-content-from-email-client-and-webmail) |   | T <br> Wymaga urządzenia na wysokim poziomie bloków w chmurze | T <br> Wymaga urządzenia na wysokim poziomie bloków w chmurze |
|[Blokuj uruchamianie plików wykonywalnych, chyba że spełniają kryterium występowania, wieku lub listy zaufanych](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) |   | N | T |
|[Blokuj wykonywanie potencjalnie zaciemnionych skryptów](#block-execution-of-potentially-obfuscated-scripts) |  AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Wymaga urządzenia na wysokim poziomie bloków w chmurze  | N \| Y <br> Wymaga urządzenia na wysokim poziomie bloków w chmurze |
|[Blokowanie uruchamiania pobranej zawartości wykonywalnej w języku JavaScript lub VBScript](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | Blokuj | T <br> Wymaga urządzenia na wysokim poziomie bloków w chmurze  | T <br> Wymaga urządzenia na wysokim poziomie bloków w chmurze |
|[Blokowanie tworzenia zawartości wykonywalnej przez aplikacje Office](#block-office-applications-from-creating-executable-content) |   | N | T |
|[Blokuj Office aplikacjom wstrzykiwanie kodu do innych procesów](#block-office-applications-from-injecting-code-into-other-processes)  |   | N | T |
|[Blokowanie tworzenia procesów podrzędnych przez aplikację komunikacji Office](#block-office-communication-application-from-creating-child-processes) |  |  N | T |
|[Blokuj trwałość za pośrednictwem subskrypcji zdarzeń WMI](#block-persistence-through-wmi-event-subscription) |  AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Wymaga urządzenia na wysokim poziomie bloków w chmurze  | N \| Y <br> Wymaga urządzenia na wysokim poziomie bloków w chmurze |
|[Blokuj tworzenie procesów pochodzących z poleceń PSExec i WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) |   | N | T |
|[Blokuj niezaufane i niepodpisane procesy uruchamiane z portu USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Wymaga urządzenia na wysokim poziomie bloków w chmurze  | N \| Y <br> Wymaga urządzenia na wysokim poziomie bloków w chmurze |
|[Blokuj wywołania interfejsu API Win32 z makr Office](#block-win32-api-calls-from-office-macros) |   | N | T |
|[Korzystanie z zaawansowanej ochrony przed oprogramowaniem wymuszającym okup](#use-advanced-protection-against-ransomware) | AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Wymaga urządzenia na wysokim poziomie bloków w chmurze  | N \| Y <br> Wymaga urządzenia na wysokim poziomie bloków w chmurze |
  
## <a name="asr-rules-and-guids-matrix"></a>Macierz reguł i identyfikatorów GUID usługi ASR

| Nazwa reguły | Identyfikator GUID reguły |
|:-----|:-----|
| Blokowanie nadużyć wobec wykorzystywanych, narażonych na zagrożenia podpisanych kierowców | 56a863a9-875e-4185-98a7-b882c64b5ce5 |
| Zablokuj programowi Adobe Reader tworzenie procesów podrzędnych | 7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c |
| Blokowanie tworzenia procesów podrzędnych przez wszystkie aplikacje Office | d4f940ab-401b-4efc-aadc-ad5f3c50688a |
| Blokuj kradzież poświadczeń z podsystemu Windows lokalnego urzędu zabezpieczeń (lsass.exe) | 9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2 |
| Blokuj zawartość wykonywalną z klienta poczty e-mail i poczty internetowej | be9ba2d9-53ea-4cdc-84e5-9b1eeee46550 |
| Blokuj uruchamianie plików wykonywalnych, chyba że spełniają kryterium występowania, wieku lub listy zaufanych | 01443614-cd74-433a-b99e-2ecdc07bfc25 |
| Blokuj wykonywanie potencjalnie zaciemnionych skryptów | 5beb7efe-fd9a-4556-801d-275e5ffc04cc |
| Blokowanie uruchamiania pobranej zawartości wykonywalnej w języku JavaScript lub VBScript | d3e037e1-3eb8-44c8-a917-57927947596d |
| Blokowanie tworzenia zawartości wykonywalnej przez aplikacje Office | 3b576869-a4ec-4529-8536-b80a7769e899 |
| Blokuj Office aplikacjom wstrzykiwanie kodu do innych procesów | 75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84 |
| Blokowanie tworzenia procesów podrzędnych przez aplikację komunikacji Office | 26190899-1602-49e8-8b27-eb1d0a1ce869 |
| Blokuj trwałość za pośrednictwem subskrypcji zdarzeń WMI <br>* Wykluczenia plików i folderów nie są obsługiwane. | e6db77e5-3df2-4cf1-b95a-636979351e5b |
| Blokuj tworzenie procesów pochodzących z poleceń PSExec i WMI | d1e49aac-8f56-4280-b9ba-993a6d77406c |
| Blokuj niezaufane i niepodpisane procesy uruchamiane z portu USB | b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4 |
| Blokuj wywołania interfejsu API Win32 z makr Office | 92e97fa1-2edf-4476-bdd6-9dd0b4dddc7b |
| Korzystanie z zaawansowanej ochrony przed oprogramowaniem wymuszającym okup | c1db55ab-c21a-4637-bb3f-a12568109d35 |

## <a name="asr-rule-modes"></a>Tryby reguł usługi ASR

- **Nie skonfigurowano** lub **wyłącz**: jest to stan, w którym reguła usługi ASR nie została włączona lub została wyłączona. Kod dla tego stanu = 0.
- **Blokuj**: jest to stan, w którym jest włączona reguła usługi ASR. Kod dla tego stanu to 1.
- **Inspekcja**: jest to stan, w którym reguła usługi ASR jest oceniana pod kątem jej wpływu na organizację lub środowisko, w którym została wdrożona. Kod dla tego stanu to 2.
- **Ostrzec** Jest to stan, w którym reguła usługi ASR jest włączona i wyświetla powiadomienie użytkownikowi końcowemu, ale umożliwia użytkownikowi końcowemu obejście bloku. Kod dla tego stanu to 6.

_Tryb ostrzeżenia_ to typ trybu bloku, który ostrzega użytkowników o potencjalnie ryzykownych akcjach. Użytkownicy mogą pominąć komunikat ostrzegawczy bloku i zezwolić na akcję bazową. Użytkownicy mogą wybrać przycisk **OK** , aby wymusić blok, lub wybrać opcję obejścia — **Odblokuj** — za pośrednictwem wyskakujących powiadomień wyskakujących użytkownika końcowego, które jest generowane w czasie blokowania. Po odblokowaniu ostrzeżenia operacja jest dozwolona do czasu następnego wystąpienia komunikatu ostrzegawczego, w którym to czasie użytkownik końcowy będzie musiał ponownie sformułować akcję.

Jeśli przycisk zezwalania zostanie kliknięty, blok zostanie pominięty przez 24 godziny. Po 24 godzinach użytkownik końcowy będzie musiał ponownie zezwolić na blok. Tryb ostrzegania dla reguł usługi ASR jest obsługiwany tylko dla urządzeń RS5+ (1809+). Jeśli obejście zostanie przypisane do reguł usługi ASR na urządzeniach ze starszymi wersjami, reguła będzie w trybie zablokowanym.

Możesz również ustawić regułę w trybie ostrzeżenia za pośrednictwem programu PowerShell, określając AttackSurfaceReductionRules_Actions jako "Ostrzegaj". Przykład:

```powershell
-command "& {&'Add-MpPreference' -AttackSurfaceReductionRules_Ids 56a863a9-875e-4185-98a7-b882c64b5ce5 -AttackSurfaceReductionRules_Actions Warn"} 
```

## <a name="per-rule-descriptions"></a>Opisy reguł

### <a name="block-abuse-of-exploited-vulnerable-signed-drivers"></a>Blokowanie nadużyć wobec wykorzystywanych, narażonych na zagrożenia podpisanych kierowców

Ta reguła uniemożliwia aplikacji zapisanie na dysku wrażliwego sterownika podpisanego. W środowisku naturalnym, wrażliwe sterowniki podpisane mogą być wykorzystywane przez aplikacje \- lokalne _, które mają wystarczające uprawnienia_\-, aby uzyskać dostęp do jądra. Wrażliwe sterowniki podpisane umożliwiają osobom atakującym wyłączanie lub obchodzenie rozwiązań zabezpieczeń, co ostatecznie prowadzi do naruszenia zabezpieczeń systemu.

Reguła **Blokuj nadużywanie wykorzystywanych sterowników podpisanych przez luki w zabezpieczeniach** nie blokuje załadowania sterownika już istniejącego w systemie.

> [!NOTE]
>
> Tę regułę można skonfigurować przy użyciu identyfikatora OMA-URI MEM. Zobacz [MEM OMA-URI](enable-attack-surface-reduction.md#mem) , aby skonfigurować reguły niestandardowe.
>
> Tę regułę można również skonfigurować przy użyciu programu [PowerShell](enable-attack-surface-reduction.md#powershell).
>
> Aby zbadać sterownik, użyj tej witryny sieci Web, aby [przesłać sterownik do analizy](https://www.microsoft.com/en-us/wdsi/driversubmission).

<!--The above link is the 'only link' that exists for having drivers examined. The 'en-us' component is required to make the link work. Any alterations to this link will result in a 404.
-->

nazwa Intune: `Block abuse of exploited vulnerable signed drivers` (jeszcze niedostępna)

nazwa Configuration Manager: Nie jest jeszcze dostępna
  
IDENTYFIKATOR GUID:  `56a863a9-875e-4185-98a7-b882c64b5ce5`

<!-- Hide this intro with no subsequent list items
Advanced hunting action type:
-->

<!-- 
Dependencies: none provided by engineering
-->

### <a name="block-adobe-reader-from-creating-child-processes"></a>Zablokuj programowi Adobe Reader tworzenie procesów podrzędnych

Ta reguła zapobiega atakom, blokując programowi Adobe Reader tworzenie procesów.

Poprzez inżynierię społeczną lub luki w zabezpieczeniach złośliwe oprogramowanie może pobierać i uruchamiać ładunki oraz wyrwać się z programu Adobe Reader. Blokując generowanie procesów podrzędnych przez program Adobe Reader, złośliwe oprogramowanie próbujące użyć go jako wektora nie może się rozprzestrzeniać.

nazwa Intune:`Process creation from Adobe Reader (beta)`

nazwa Configuration Manager: Nie jest jeszcze dostępna

IDENTYFIKATOR GUID: `7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c`

Zaawansowany typ akcji wyszukiwania zagrożeń:

- AsrAdobeReaderChildProcessAudited
- AsrAdobeReaderChildProcessBlocked

Zależności: MDAV

### <a name="block-all-office-applications-from-creating-child-processes"></a>Blokowanie tworzenia procesów podrzędnych przez wszystkie aplikacje Office

Ta reguła uniemożliwia Office aplikacjom tworzenie procesów podrzędnych. aplikacje Office obejmują programy Word, Excel, PowerPoint, OneNote i Access.

Tworzenie złośliwych procesów podrzędnych jest typową strategią złośliwego oprogramowania. Złośliwe oprogramowanie, które nadużywa Office jako wektor, często uruchamia makra VBA i wykorzystuje kod do pobierania i próby uruchomienia większej liczby ładunków. Jednak niektóre uzasadnione aplikacje biznesowe mogą również generować procesy podrzędne dla niegroźnych celów; na przykład zduplikowanie wiersza polecenia lub użycie programu PowerShell do skonfigurowania ustawień rejestru.

nazwa Intune:`Office apps launching child processes`

nazwa Configuration Manager:`Block Office application from creating child processes`

IDENTYFIKATOR GUID: `d4f940ab-401b-4efc-aadc-ad5f3c50688a`

Zaawansowany typ akcji wyszukiwania zagrożeń:

- AsrOfficeChildProcessAudited
- AsrOfficeChildProcessBlocked

Zależności: MDAV

### <a name="block-credential-stealing-from-the-windows-local-security-authority-subsystem"></a>Blokuj kradzież poświadczeń z podsystemu Windows lokalnego urzędu zabezpieczeń

Ta reguła pomaga zapobiegać kradzieży poświadczeń przez zablokowanie usługi podsystemu lokalnego urzędu zabezpieczeń (LSASS).

Usługa LSASS uwierzytelnia użytkowników, którzy logują się na komputerze Windows. Funkcja Microsoft Defender Credential Guard w Windows zwykle uniemożliwia próby wyodrębnienia poświadczeń z usługi LSASS. Jednak niektóre organizacje nie mogą włączyć funkcji Credential Guard na wszystkich swoich komputerach z powodu problemów ze zgodnością z niestandardowymi sterownikami kart inteligentnych lub innymi programami, które ładują się do lokalnego urzędu zabezpieczeń (LSA). W takich przypadkach osoby atakujące mogą używać narzędzi hack, takich jak Mimikatz, aby zeskrobać hasła zwykłego tekstu i skróty NTLM z LSASS.

> [!NOTE]
> W niektórych aplikacjach kod wylicza wszystkie uruchomione procesy i próbuje je otworzyć z wyczerpującymi uprawnieniami. Ta reguła nie zezwala na akcję otwierania procesu aplikacji i rejestruje szczegóły w dzienniku zdarzeń zabezpieczeń. Ta reguła może generować dużo szumu. Jeśli masz aplikację, która po prostu wylicza usługę LSASS, ale nie ma rzeczywistego wpływu na funkcjonalność, nie ma potrzeby dodawania jej do listy wykluczeń. Sam wpis dziennika zdarzeń nie musi wskazywać na złośliwe zagrożenie.
  
> [!IMPORTANT]
> Domyślny stan reguły zmniejszania obszaru podatnego na ataki (ASR) "Blokuj kradzież poświadczeń z podsystemu Windows lokalnego urzędu zabezpieczeń (lsass.exe)" zmieni się z **Nieskonfigurowane** na **Skonfigurowano**, a tryb domyślny ustawiony na **Blokuj**. Wszystkie inne reguły usługi ASR pozostaną w stanie domyślnym: **Nieskonfigurowane**. Dodatkowa logika filtrowania została już włączona do reguły w celu zmniejszenia liczby powiadomień użytkowników końcowych. Klienci mogą skonfigurować regułę w trybach **Inspekcja**, **Ostrzeżenie** lub **Wyłączone** , co spowoduje zastąpienie trybu domyślnego. Funkcjonalność tej reguły jest taka sama, niezależnie od tego, czy reguła jest skonfigurowana w trybie domyślnym, czy też w trybie blokuj ręcznie.

nazwa Intune:`Flag credential stealing from the Windows local security authority subsystem`

nazwa Configuration Manager:`Block credential stealing from the Windows local security authority subsystem`

IDENTYFIKATOR GUID: `9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2`

Zaawansowany typ akcji wyszukiwania zagrożeń:

- AsrLsassCredentialTheftAudited
- AsrLsassCredentialTheftBlocked

Zależności: MDAV

### <a name="block-executable-content-from-email-client-and-webmail"></a>Blokuj zawartość wykonywalną z klienta poczty e-mail i poczty internetowej

Ta reguła blokuje uruchamianie następujących typów plików z poczty e-mail otwartej w aplikacji microsoft Outlook lub Outlook.com i innych popularnych dostawców poczty internetowej:

- Pliki wykonywalne (takie jak .exe, .dll lub scr)
- Pliki skryptów (takie jak plik programu PowerShell ps, Visual Basic vbs lub plik .js JavaScript)

nazwa Intune:`Execution of executable content (exe, dll, ps, js, vbs, etc.) dropped from email (webmail/mail client) (no exceptions)`

nazwa Microsoft Endpoint Manager:`Block executable content from email client and webmail`

IDENTYFIKATOR GUID: `be9ba2d9-53ea-4cdc-84e5-9b1eeee46550`

Zaawansowany typ akcji wyszukiwania zagrożeń:

- AsrExecutableEmailContentAudited
- AsrExecutableEmailContentBlocked

Zależności: MDAV

> [!NOTE]
> Reguła **Blokuj zawartość wykonywalną z klienta poczty e-mail i poczty internetowej** ma następujące alternatywne opisy, w zależności od używanej aplikacji:
>
> - Intune (profile konfiguracji): wykonywanie zawartości wykonywalnej (np. dll, ps, js, vbs itp.) porzucone z poczty e-mail (poczta internetowa/klient poczty) (bez wyjątków).
> - Endpoint Manager: blokuj pobieranie zawartości wykonywalnej z klientów poczty e-mail i poczty internetowej.
> - zasady grupy: blokuj zawartość wykonywalną z klienta poczty e-mail i poczty internetowej.

### <a name="block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion"></a>Blokuj uruchamianie plików wykonywalnych, chyba że spełniają kryterium występowania, wieku lub listy zaufanych

Ta reguła blokuje uruchamianie plików wykonywalnych, takich jak .exe, .dll lub scr. W związku z tym uruchamianie niezaufanych lub nieznanych plików wykonywalnych może być ryzykowne, ponieważ początkowo nie jest jasne, czy pliki są złośliwe.

> [!IMPORTANT]
> Aby korzystać z tej [reguły, należy włączyć ochronę dostarczaną przez chmurę](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) .
>
> Reguła **Blokuj uruchamianie plików wykonywalnych, chyba że spełniają kryterium występowania, wieku lub listy zaufanej** z identyfikatorem GUID `01443614-cd74-433a-b99e-2ecdc07bfc25` , jest własnością firmy Microsoft i nie jest określane przez administratorów. Ta reguła używa ochrony dostarczanej w chmurze do regularnego aktualizowania listy zaufanych.
>
> Można określić poszczególne pliki lub foldery (przy użyciu ścieżek folderów lub w pełni kwalifikowanych nazw zasobów), ale nie można określić, do których reguł lub wykluczeń mają zastosowanie.

nazwa Intune:`Executables that don't meet a prevalence, age, or trusted list criteria`

nazwa Configuration Manager:`Block executable files from running unless they meet a prevalence, age, or trusted list criteria`

IDENTYFIKATOR GUID: `01443614-cd74-433a-b99e-2ecdc07bfc25`

Zaawansowany typ akcji wyszukiwania zagrożeń:

- AsrUntrustedExecutableAudited
- AsrUntrustedExecutableBlocked

Zależności: MDAV, Cloud Protection

### <a name="block-execution-of-potentially-obfuscated-scripts"></a>Blokuj wykonywanie potencjalnie zaciemnionych skryptów

Ta reguła wykrywa podejrzane właściwości w zaciemnionym skryptze.

Zaciemnianie skryptów jest powszechną techniką używaną zarówno przez autorów złośliwego oprogramowania, jak i uzasadnione aplikacje w celu ukrycia własności intelektualnej lub skrócenia czasu ładowania skryptów. Autorzy złośliwego oprogramowania używają również zaciemniania, aby utrudnić odczytywanie złośliwego kodu, co uniemożliwia ścisłą kontrolę przez ludzi i oprogramowanie zabezpieczające.

nazwa Intune:`Obfuscated js/vbs/ps/macro code`

nazwa Configuration Manager:`Block execution of potentially obfuscated scripts`

IDENTYFIKATOR GUID: `5beb7efe-fd9a-4556-801d-275e5ffc04cc`

Zaawansowany typ akcji wyszukiwania zagrożeń:

- AsrObfuscatedScriptAudited
- AsrObfuscatedScriptBlocked

Zależności: MDAV, AMSI

### <a name="block-javascript-or-vbscript-from-launching-downloaded-executable-content"></a>Blokowanie uruchamiania pobranej zawartości wykonywalnej w języku JavaScript lub VBScript

Ta reguła uniemożliwia skryptom uruchamianie potencjalnie złośliwej pobranej zawartości. Złośliwe oprogramowanie napisane w języku JavaScript lub VBScript często działa jako narzędzie do pobierania i uruchamiania innego złośliwego oprogramowania z Internetu.

Chociaż nie jest to typowe, aplikacje biznesowe czasami używają skryptów do pobierania i uruchamiania instalatorów.

nazwa Intune:`js/vbs executing payload downloaded from Internet (no exceptions)`

nazwa Configuration Manager:`Block JavaScript or VBScript from launching downloaded executable content`

IDENTYFIKATOR GUID: `d3e037e1-3eb8-44c8-a917-57927947596d`

Zaawansowany typ akcji wyszukiwania zagrożeń:

- AsrScriptExecutableDownloadAudited
- AsrScriptExecutableDownloadBlocked

Zależności: MDAV, AMSI

### <a name="block-office-applications-from-creating-executable-content"></a>Blokowanie tworzenia zawartości wykonywalnej przez aplikacje Office

Ta reguła uniemożliwia Office aplikacjom, w tym programom Word, Excel i PowerPoint, tworzenie potencjalnie złośliwej zawartości wykonywalnej przez blokowanie zapisu złośliwego kodu na dysku.

Złośliwe oprogramowanie, które nadużywa Office jako wektor, może próbować wyrwać się z Office i zapisać złośliwe składniki na dysku. Te złośliwe składniki przetrwałyby ponowne uruchomienie komputera i utrwaliłyby się w systemie. W związku z tym ta reguła broni się przed powszechną techniką trwałości.

nazwa Intune:`Office apps/macros creating executable content`

Nazwa SCCM: `Block Office applications from creating executable content`

IDENTYFIKATOR GUID: `3b576869-a4ec-4529-8536-b80a7769e899`

Zaawansowany typ akcji wyszukiwania zagrożeń:

- AsrExecutableOfficeContentAudited
- AsrExecutableOfficeContentBlocked

Zależności: MDAV, RPC

### <a name="block-office-applications-from-injecting-code-into-other-processes"></a>Blokuj Office aplikacjom wstrzykiwanie kodu do innych procesów

Ta reguła blokuje próby wstrzyknięcia kodu z Office aplikacji do innych procesów.

Osoby atakujące mogą próbować użyć aplikacji Office do migrowania złośliwego kodu do innych procesów poprzez wstrzyknięcie kodu, aby kod mógł zostać zamapowany jako czysty proces.

Nie ma znanych uzasadnionych celów biznesowych do wstrzykiwania kodu.

Ta reguła dotyczy programów Word, Excel i PowerPoint.

nazwa Intune:`Office apps injecting code into other processes (no exceptions)`

nazwa Configuration Manager:`Block Office applications from injecting code into other processes`

IDENTYFIKATOR GUID: `75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84`

Zaawansowany typ akcji wyszukiwania zagrożeń:

- AsrOfficeProcessInjectionAudited
- AsrOfficeProcessInjectionBlocked

Zależności: MDAV

### <a name="block-office-communication-application-from-creating-child-processes"></a>Blokowanie tworzenia procesów podrzędnych przez aplikację komunikacji Office

Ta reguła uniemożliwia Outlook tworzenie procesów podrzędnych, a jednocześnie zezwala na prawidłowe funkcje Outlook.

Ta reguła chroni przed atakami inżynierii społecznej i zapobiega wykorzystywaniu luk w zabezpieczeniach kodu w Outlook. Chroni również przed [Outlook regułami i formami wykorzystującymi luki w zabezpieczeniach](https://blogs.technet.microsoft.com/office365security/defending-against-rules-and-forms-injection/), których osoby atakujące mogą używać, gdy poświadczenia użytkownika zostaną naruszone.

> [!NOTE]
> Ta reguła blokuje wskazówki dotyczące zasad DLP i etykietki narzędzi w Outlook. Ta reguła ma zastosowanie tylko do Outlook i Outlook.com.

nazwa Intune:`Process creation from Office communication products (beta)`

nazwa Configuration Manager: niedostępna

IDENTYFIKATOR GUID: `26190899-1602-49e8-8b27-eb1d0a1ce869`

Zaawansowany typ akcji wyszukiwania zagrożeń:

- AsrOfficeCommAppChildProcessAudited
- AsrOfficeCommAppChildProcessBlocked

Zależności: MDAV

### <a name="block-persistence-through-wmi-event-subscription"></a>Blokuj trwałość za pośrednictwem subskrypcji zdarzeń WMI

Ta reguła uniemożliwia złośliwemu oprogramowaniu nadużywanie usługi WMI w celu uzyskania trwałości na urządzeniu.

> [!IMPORTANT]
> Wykluczenia plików i folderów nie mają zastosowania do tej reguły zmniejszania obszaru ataków.

Zagrożenia bez plików stosują różne taktyki, aby pozostać w ukryciu, aby uniknąć bycia widocznym w systemie plików i uzyskać okresową kontrolę nad wykonywaniem. Niektóre zagrożenia mogą nadużywać repozytorium WMI i modelu zdarzeń, aby pozostać w ukryciu.

nazwa Intune: niedostępna

nazwa Configuration Manager: niedostępna

IDENTYFIKATOR GUID: `e6db77e5-3df2-4cf1-b95a-636979351e5b`

Zaawansowany typ akcji wyszukiwania zagrożeń:

- AsrPersistenceThroughWmiAudited
- AsrPersistenceThroughWmiBlocked

Zależności: MDAV, RPC

### <a name="block-process-creations-originating-from-psexec-and-wmi-commands"></a>Blokuj tworzenie procesów pochodzących z poleceń PSExec i WMI

Ta reguła blokuje uruchamianie procesów utworzonych za pośrednictwem programu [PsExec](/sysinternals/downloads/psexec) i [usługi WMI](/windows/win32/wmisdk/about-wmi) . Zarówno program PsExec, jak i usługa WMI mogą zdalnie wykonywać kod, więc istnieje ryzyko, że złośliwe oprogramowanie nadużywa tej funkcji do celów dowodzenia i kontroli lub rozprzestrzeniania infekcji w sieci organizacji.

> [!WARNING]
> Tej reguły należy używać tylko wtedy, gdy zarządzasz urządzeniami za pomocą [Intune](/intune) lub innego rozwiązania MDM. Ta reguła jest niezgodna z zarządzaniem za pośrednictwem [Microsoft Endpoint Configuration Manager](/configmgr), ponieważ ta reguła blokuje polecenia usługi WMI, których klient Configuration Manager używa do poprawnego działania.

nazwa Intune:`Process creation from PSExec and WMI commands`

nazwa Configuration Manager: Nie dotyczy

IDENTYFIKATOR GUID: `d1e49aac-8f56-4280-b9ba-993a6d77406c`

Zaawansowany typ akcji wyszukiwania zagrożeń:

- AsrPsexecWmiChildProcessAudited
- AsrPsexecWmiChildProcessBlocked

Zależności: MDAV

### <a name="block-untrusted-and-unsigned-processes-that-run-from-usb"></a>Blokuj niezaufane i niepodpisane procesy uruchamiane z portu USB

Dzięki tej regule administratorzy mogą uniemożliwić uruchamianie niezapisanych lub niezaufanych plików wykonywalnych z dysków wymiennych USB, w tym kart SD. Zablokowane typy plików obejmują pliki wykonywalne (takie jak .exe, .dll lub scr)

nazwa Intune:`Untrusted and unsigned processes that run from USB`

nazwa Configuration Manager:`Block untrusted and unsigned processes that run from USB`

IDENTYFIKATOR GUID: `b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4`

Zaawansowany typ akcji wyszukiwania zagrożeń:

- AsrUntrustedUsbProcessAudited
- AsrUntrustedUsbProcessBlocked

Zależności: MDAV

### <a name="block-win32-api-calls-from-office-macros"></a>Blokuj wywołania interfejsu API Win32 z makr Office

Ta reguła uniemożliwia makra VBA wywoływanie interfejsów API Win32.

Office VBA włącza wywołania interfejsu API Win32. Złośliwe oprogramowanie może nadużywać tej funkcji, na przykład [wywoływania interfejsów API Win32 w celu uruchomienia złośliwego kodu powłoki](https://www.microsoft.com/security/blog/2018/09/12/office-vba-amsi-parting-the-veil-on-malicious-macros/) bez pisania czegokolwiek bezpośrednio na dysku. Większość organizacji nie polega na możliwości wywoływania interfejsów API Win32 w ich codziennym funkcjonowaniu, nawet jeśli używają makr w inny sposób.

Obsługiwane systemy operacyjne:

- [Windows 10, wersja 1709](/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Server, wersja 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)

nazwa Intune:`Win32 imports from Office macro code`

nazwa Configuration Manager:`Block Win32 API calls from Office macros`

IDENTYFIKATOR GUID: `92e97fa1-2edf-4476-bdd6-9dd0b4dddc7b`

Zaawansowany typ akcji wyszukiwania zagrożeń:

- AsrOfficeMacroWin32ApiCallsAudited
- AsrOfficeMacroWin32ApiCallsBlocked

Zależności: MDAV, AMSI

### <a name="use-advanced-protection-against-ransomware"></a>Korzystanie z zaawansowanej ochrony przed oprogramowaniem wymuszającym okup

Ta reguła zapewnia dodatkową warstwę ochrony przed oprogramowaniem wymuszającym okup. Używa zarówno heurystyki klienta, jak i chmury, aby określić, czy plik przypomina oprogramowanie wymuszające okup. Ta reguła nie blokuje plików o co najmniej jednej z następujących cech:

- Plik został już uznany za bez szwanku w chmurze firmy Microsoft.
- Plik jest prawidłowym podpisanym plikiem.
- Plik jest wystarczająco rozpowszechniony, aby nie być uważanym za oprogramowanie wymuszające okup.

Reguła ma tendencję do błądzić po stronie ostrożności, aby zapobiec ransomware.

> [!NOTE]
> Aby korzystać z tej [reguły, należy włączyć ochronę dostarczaną przez chmurę](enable-cloud-protection-microsoft-defender-antivirus.md) .

nazwa Intune:`Advanced ransomware protection`

nazwa Configuration Manager:`Use advanced protection against ransomware`

IDENTYFIKATOR GUID: `c1db55ab-c21a-4637-bb3f-a12568109d35`

Zaawansowany typ akcji wyszukiwania zagrożeń:

- AsrRansomwareAudited
- AsrRansomwareBlocked

Zależności: MDAV, Cloud Protection
