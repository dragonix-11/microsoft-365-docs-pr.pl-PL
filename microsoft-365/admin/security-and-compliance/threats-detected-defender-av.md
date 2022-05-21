---
title: Zagrożenia wykryte przez program antywirusowy Microsoft Defender
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid: MET150
description: Dowiedz się, jak Program antywirusowy Microsoft Defender chroni urządzenia Windows przed zagrożeniami oprogramowania, takimi jak wirusy, złośliwe oprogramowanie i programy szpiegujące.
ms.openlocfilehash: 796edb343745e19267f901b736ca19217b0e4f01
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2022
ms.locfileid: "65620909"
---
# <a name="overview-of-threat-protection-by-microsoft-defender-antivirus"></a>Omówienie ochrony przed zagrożeniami według Program antywirusowy Microsoft Defender

Program antywirusowy Microsoft Defender chroni urządzenia Windows przed zagrożeniami oprogramowania, takimi jak wirusy, złośliwe oprogramowanie i programy szpiegujące.

- Wirusy zwykle rozprzestrzeniają się przez dołączenie kodu do innych plików na urządzeniu lub w sieci i mogą powodować nieprawidłowe działanie zainfekowanych programów.
- Złośliwe oprogramowanie obejmuje złośliwe pliki, aplikacje i kod, które mogą powodować uszkodzenia i zakłócać normalne korzystanie z urządzeń. Ponadto złośliwe oprogramowanie może zezwalać na nieautoryzowany dostęp, korzystać z zasobów systemowych, kraść hasła i informacje o koncie, blokować cię z komputera i prosić o okup i nie tylko.
- Programy szpiegujące zbierają dane, takie jak działanie przeglądania internetu, i wysyłają dane do serwerów zdalnych.
 
Aby zapewnić ochronę przed zagrożeniami, Program antywirusowy Microsoft Defender używa kilku metod. Te metody obejmują ochronę dostarczaną przez chmurę, ochronę w czasie rzeczywistym i dedykowane aktualizacje ochrony.

- Ochrona dostarczana przez chmurę pomaga w niemal natychmiastowym wykrywaniu i blokowaniu nowych i pojawiających się zagrożeń.
- Zawsze włączone skanowanie używa monitorowania zachowań plików i procesów oraz innych technik (znanych również jako *ochrona w czasie rzeczywistym*).
- Dedykowane aktualizacje ochrony są oparte na uczeniu maszynowym, ludzkiej i zautomatyzowanej analizie danych big data oraz szczegółowych badaniach nad odpornością na zagrożenia. 

Aby dowiedzieć się więcej o złośliwym oprogramowaniu i Program antywirusowy Microsoft Defender, zobacz następujące artykuły: 

- [Opis złośliwego oprogramowania & innych zagrożeń](/windows/security/threat-protection/intelligence/understanding-malware)
- [Jak firma Microsoft identyfikuje złośliwe oprogramowanie i potencjalnie niechciane aplikacje](/windows/security/threat-protection/intelligence/criteria)
- [Ochrona nowej generacji w Windows 10](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10)

## <a name="what-happens-when-a-non-microsoft-antivirus-solution-is-used"></a>Co się stanie, gdy jest używane rozwiązanie antywirusowe firmy innej niż Microsoft? 

Program antywirusowy Microsoft Defender jest częścią systemu operacyjnego i jest włączona na urządzeniach z systemem Windows 10. Jeśli jednak używasz rozwiązania antywirusowego innego niż Microsoft i nie używasz [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection), Program antywirusowy Microsoft Defender automatycznie przechodzi w tryb wyłączony.  

W trybie wyłączonym użytkownicy i klienci nadal mogą używać Program antywirusowy Microsoft Defender do skanowania zaplanowanego lub na żądanie w celu identyfikowania zagrożeń, jednak Program antywirusowy Microsoft Defender nie będzie już:

- być używana jako domyślna aplikacja antywirusowa.
- aktywnie skanuj pliki pod kątem zagrożeń.
- korygowanie lub rozwiązywanie zagrożeń.

Jeśli odinstalujesz rozwiązanie antywirusowe inne niż Microsoft, Program antywirusowy Microsoft Defender automatycznie przejdzie w tryb aktywny, aby chronić urządzenia Windows przed zagrożeniami.

> [!TIP]
> - Jeśli używasz Microsoft 365, rozważ użycie Program antywirusowy Microsoft Defender jako podstawowego rozwiązania antywirusowego. Integracja może zapewnić lepszą ochronę. Zobacz [Razem Lepiej: Program antywirusowy Microsoft Defender i Office 365](/windows/security/threat-protection/microsoft-defender-antivirus/office-365-microsoft-defender-antivirus).
> - Upewnij się, że Program antywirusowy Microsoft Defender na bieżąco, nawet jeśli używasz rozwiązania antywirusowego firmy innej niż Microsoft.

## <a name="what-to-expect-when-threats-are-detected"></a>Czego można oczekiwać po wykryciu zagrożeń

Gdy zagrożenia zostaną wykryte przez Program antywirusowy Microsoft Defender, zostaną wykonane następujące czynności:

- Użytkownicy otrzymują [powiadomienia w Windows](https://support.microsoft.com/windows/8942c744-6198-fe56-4639-34320cf9444e). 
- Wykrycia są wymienione w [aplikacji Zabezpieczenia Windows](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) na stronie **Historia ochrony**.  
- Jeśli [zabezpieczono urządzenia Windows 10](../setup/secure-win-10-pcs.md) i [zarejestrowano je w Intune](/mem/intune/enrollment/windows-enrollment-methods), a organizacja ma zarejestrowane co najmniej 800 urządzeń, na stronie **Zagrożenia i oprogramowanie antywirusowe** zostaną wyświetlone informacje na temat wykrywania zagrożeń i szczegółowych informacji na <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a>.**Program antywirusowy Microsoft Defender** kartę na stronie **głównej** (lub w okienku nawigacji, wybierając pozycję **HealthThreats** >  & antivirus).

    Jeśli organizacja ma ponad 800 urządzeń zarejestrowanych w Intune, zostanie wyświetlony monit o wyświetlenie wykrywania zagrożeń i szczegółowych informacji z [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) zamiast na stronie **Zagrożenia i oprogramowanie antywirusowe**.
 
    > [!NOTE]
    > Karta **Program antywirusowy Microsoft Defender** oraz strona **Zagrożenia i oprogramowanie antywirusowe** są wdrażane etapami, więc możesz nie mieć do nich natychmiastowego dostępu.

W większości przypadków użytkownicy nie muszą podejmować żadnych dalszych działań. Gdy tylko na urządzeniu zostanie wykryty złośliwy plik lub program, Program antywirusowy Microsoft Defender go zablokuje i uniemożliwi jego uruchomienie. Ponadto nowo wykryte zagrożenia są dodawane do aparatu antywirusowego i ochrony przed złośliwym kodem, dzięki czemu inne urządzenia i użytkownicy są również chronieni.  

Jeśli użytkownik musi wykonać akcję, taką jak zatwierdzenie usunięcia złośliwego pliku, zobaczy to w otrzymywanym powiadomieniu. Aby dowiedzieć się więcej na temat akcji wykonywanych Program antywirusowy Microsoft Defender w imieniu użytkownika lub akcji, które użytkownicy mogą podjąć, zobacz [Historia ochrony](https://support.microsoft.com/office/f1e5fd95-09b4-46d1-b8c7-1059a1e09708). Aby dowiedzieć się, jak zarządzać wykrywaniem zagrożeń jako specjalista IT/administrator, zobacz [Przegląd wykrytych zagrożeń i podjęcie akcji](../../business-premium/m365bp-review-threats-take-action.md).

Aby dowiedzieć się więcej o różnych zagrożeniach, odwiedź <a href="https://www.microsoft.com/wdsi/threats" target="_blank">witrynę Microsoft Security Intelligence Threats</a>, w której można wykonać następujące akcje: 

- Wyświetl bieżące informacje o najważniejszych zagrożeniach.
- Wyświetlanie najnowszych zagrożeń dla określonego regionu.
- Wyszukaj w encyklopedii zagrożeń szczegółowe informacje o konkretnym zagrożeniu.

## <a name="related-content"></a>Zawartość pokrewna

[Zabezpieczanie urządzeń Windows](/misc/m365bp-secure-windows-devices) (artykuł)\
[Ocena Program antywirusowy Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/evaluate-microsoft-defender-antivirus) (artykuł)\
[Jak włączyć ochronę antywirusową w czasie rzeczywistym i dostarczaną przez chmurę](/mem/intune/user-help/turn-on-defender-windows#turn-on-real-time-and-cloud-delivered-protection) (artykuł)\
[Jak włączyć i używać Program antywirusowy Microsoft Defender z aplikacji Zabezpieczenia Windows](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-security-center-antivirus) (artykuł)\
[Jak włączyć Program antywirusowy Microsoft Defender przy użyciu zasady grupy](/mem/intune/user-help/turn-on-defender-windows#turn-on-windows-defender) (artykuł)\
[Jak zaktualizować definicje programu antywirusowego](/mem/intune/user-help/turn-on-defender-windows#update-your-antivirus-definitions) (artykuł)\
[Jak przesłać złośliwe oprogramowanie i nie złośliwe oprogramowanie do firmy Microsoft w celu analizy](/microsoft-365/security/office-365-security/submitting-malware-and-non-malware-to-microsoft-for-analysis) (artykuł)