---
title: Zagrożenia wykrywane przez Program antywirusowy Microsoft Defender
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
description: Dowiedz się Program antywirusowy Microsoft Defender, jak chronić urządzenia Windows przed zagrożeniami oprogramowania, takimi jak wirusy, złośliwe oprogramowanie i oprogramowanie szpiegujące.
ms.openlocfilehash: c11ce9a2f38f1ecb7f47cd5b74e710d92c8ffbe0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63325659"
---
# <a name="threats-detected-by-microsoft-defender-antivirus"></a>Zagrożenia wykrywane przez Program antywirusowy Microsoft Defender

Program antywirusowy Microsoft Defender chroni urządzenia Windows przed zagrożeniami oprogramowania, takimi jak wirusy, złośliwe oprogramowanie i oprogramowanie szpiegujące.

- Wirusy zwykle rozpowszechniają się przez dołączenie ich kodu do innych plików na urządzeniu lub w sieci i mogą spowodować nieprawidłowe działanie zainfekowanych programów.
- Złośliwe oprogramowanie zawiera złośliwe pliki, aplikacje i kod, które mogą powodować uszkodzenia i zakłócać normalne korzystanie z urządzeń. Ponadto złośliwe oprogramowanie pozwala na nieautoryzowany dostęp, korzystać z zasobów systemowych, ukraść hasła i informacje o koncie, zablokować Cię przed komputerem i poprosić o ransom i nie tylko.
- Program szpiegujący zbiera dane, takie jak aktywność przeglądania Internetu, i wysyła dane do serwerów zdalnych.
 
Aby zapewnić ochronę przed zagrożeniami, Program antywirusowy Microsoft Defender kilka metod. Metody te obejmują ochronę w chmurze, ochronę w czasie rzeczywistym i dedykowane aktualizacje ochrony.

- Ochrona dostarczana w chmurze pomaga natychmiast wykrywać i blokować nowe i wyłaniające się zagrożenia.
- W skanach zawsze przysyłanych jest używane monitorowanie zachowania plików i procesów oraz inne techniki (nazywane także ochroną *w czasie rzeczywistym*).
- Dedykowane aktualizacje ochrony są oparte na uczeniem maszynowym, analizie danych big-data przez ludzi oraz szczegółowej badań odporność na zagrożenia. 

Aby dowiedzieć się więcej o złośliwym Program antywirusowy Microsoft Defender, zobacz następujące artykuły: 

- [Opis złośliwego & innych zagrożeń](/windows/security/threat-protection/intelligence/understanding-malware)
- [Sposób, w jaki firma Microsoft identyfikuje złośliwe oprogramowanie i potencjalnie niechciane aplikacje](/windows/security/threat-protection/intelligence/criteria)
- [Ochrona następnej generacji w Windows 10](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10)

## <a name="what-happens-when-a-non-microsoft-antivirus-solution-is-used"></a>Co się dzieje, gdy jest używane rozwiązanie antywirusowe inne niż firmy Microsoft? 

Program antywirusowy Microsoft Defender jest częścią systemu operacyjnego i jest włączana na urządzeniach z systemem Windows 10. Jeśli jednak korzystasz z rozwiązania niebędące programem antywirusowym firmy Microsoft i nie korzystasz z programu [Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection), program Program antywirusowy Microsoft Defender przejdzie w tryb wyłączony.  

W trybie wyłączonym użytkownicy i klienci mogą nadal Program antywirusowy Microsoft Defender w zaplanowanych lub na żądanie skanach w celu zidentyfikowania zagrożeń, jednak Program antywirusowy Microsoft Defender nie będą już:

- być używana jako domyślna aplikacja antywirusowa.
- aktywnie skanuj pliki w poszukiwaniu zagrożeń.
- rozwiązywanie lub rozwiązywanie zagrożeń.

Jeśli odinstalujesz rozwiązanie antywirusowe inne niż firmy Microsoft, program Program antywirusowy Microsoft Defender automatycznie przejdź do trybu aktywnego, aby chronić Twoje urządzenia Windows przed zagrożeniami.

> [!TIP]
> - Jeśli korzystasz z programu Microsoft 365, rozważ użycie programu Program antywirusowy Microsoft Defender jako podstawowego rozwiązania antywirusowego. Integracja może zapewnić lepszą ochronę. Zobacz [Razem lepiej: Program antywirusowy Microsoft Defender i Office 365](/windows/security/threat-protection/microsoft-defender-antivirus/office-365-microsoft-defender-antivirus).
> - Pamiętaj, aby Program antywirusowy Microsoft Defender aktualne, nawet jeśli używasz rozwiązania antywirusowego firmy innym niż Microsoft.

## <a name="what-to-expect-when-threats-are-detected"></a>Czego można oczekiwać w przypadku wykrycia zagrożeń

W przypadku wykrycia zagrożeń przez Program antywirusowy Microsoft Defender są one wykrywane w następujący sposób:

- Użytkownicy otrzymują [powiadomienia w Windows](https://support.microsoft.com/windows/8942c744-6198-fe56-4639-34320cf9444e). 
- Wykrywanie jest wyświetlane w aplikacji [Zabezpieczenia Windows](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) na stronie **Historia** ochrony.  
- Jeśli twoje urządzenia z systemem [Windows 10 zostały](../setup/secure-win-10-pcs.md) zabezpieczone i zarejestrowane w usłudze [Intune](/mem/intune/enrollment/windows-enrollment-methods), Windows 10 twoja organizacja ma zarejestrowanych co najmniej 800 urządzeń, wykrywanie zagrożeń i szczegółowe informacje będą dostępne w aplikacji <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365</a> na stronie Zagrożenia i oprogramowanie antywirusowe,  **do której możesz uzyskać dostęp z Program antywirusowy Microsoft Defender** kartę na stronie **głównej** (lub w okienku nawigacji, wybierając pozycję **HealthThreats** >  & antivirus).

    Jeśli w usłudze Intune jest zarejestrowanych ponad 800 urządzeń, zostanie wyświetlony monit o wyświetlanie wykrywania zagrożeń i szczegółowych informacji z usługi [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) zamiast ze strony Zagrożenia **i oprogramowanie antywirusowe**.
 
    > [!NOTE]
    > Strona **Program antywirusowy Microsoft Defender** oraz Zagrożenia i **oprogramowanie antywirusowe** są etapami, więc możesz nie mieć do nich natychmiastowego dostępu.

W większości przypadków użytkownicy nie muszą nic więcej zrobić. Po wykryciu złośliwego pliku lub programu na urządzeniu Program antywirusowy Microsoft Defender i zapobiega jego uruchomieniu. Ponadto nowe wykryte zagrożenia są dodawane do aparatu antywirusowego i ochrony przed złośliwym oprogramowaniem, dzięki czemu inne urządzenia i użytkownicy są także chronione.  

Jeśli użytkownik musi podjąć akcję, na przykład zatwierdzenie usunięcia złośliwego pliku, zobaczy to w powiadomieniu, które otrzyma. Aby dowiedzieć się więcej o akcjach Program antywirusowy Microsoft Defender w imieniu użytkownika lub czynnościach, które użytkownicy muszą podjąć, zobacz [Historia ochrony](https://support.microsoft.com/office/f1e5fd95-09b4-46d1-b8c7-1059a1e09708). Aby dowiedzieć się, jak zarządzać wykrywaniem zagrożeń jako specjalista IT/administrator, zobacz Przeglądanie wykrytych [zagrożeń i działanie](review-threats-take-action.md).

Aby dowiedzieć się więcej o różnych zagrożeniach, odwiedź <a href="https://www.microsoft.com/wdsi/threats" target="_blank">witrynę Microsoft Security Intelligence Zagrożenia</a>, w której możesz wykonywać następujące czynności: 

- Wyświetl bieżące informacje o najlepszych zagrożeniach.
- Wyświetl najnowsze zagrożenia dla określonego regionu.
- Wyszukaj w encyclopedia zagrożeń szczegóły dotyczące określonego zagrożenia.

## <a name="related-content"></a>Zawartość pokrewna

[Zabezpieczanie Windows urządzeniach](/misc/m365bp-secure-windows-devices) (artykuł)\
[Szacowanie Program antywirusowy Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/evaluate-microsoft-defender-antivirus) (artykuł)\
[Jak włączyć ochronę antywirusową w czasie rzeczywistym i w](/mem/intune/user-help/turn-on-defender-windows#turn-on-real-time-and-cloud-delivered-protection) chmurze (artykuł)\
[Jak włączyć i używać Program antywirusowy Microsoft Defender z aplikacji Zabezpieczenia Windows (](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-security-center-antivirus)artykuł)\
[Jak włączyć Program antywirusowy Microsoft Defender przy użyciu zasady grupy](/mem/intune/user-help/turn-on-defender-windows#turn-on-windows-defender) (artykuł)\
[Jak zaktualizować definicje oprogramowania antywirusowego](/mem/intune/user-help/turn-on-defender-windows#update-your-antivirus-definitions) (artykuł)\
[Jak przesłać do firmy Microsoft](/microsoft-365/security/office-365-security/submitting-malware-and-non-malware-to-microsoft-for-analysis) analizę złośliwego oprogramowania i oprogramowania, które nie jest złośliwym oprogramowaniem (artykuł)