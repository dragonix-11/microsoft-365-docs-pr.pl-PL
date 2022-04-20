---
title: Konfigurowanie możliwości zautomatyzowanego badania i reagowania w Microsoft 365 Defender
description: Konfigurowanie automatycznego badania i reagowania przy użyciu samonaprawiania w Microsoft 365 Defender
search.appverid: MET150
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
f1.keywords: CSH
ms.technology: m365d
ms.openlocfilehash: 51efeb57c6670f9c798fa254bb0a6242b30c5700
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64944376"
---
# <a name="configure-automated-investigation-and-response-capabilities-in-microsoft-365-defender"></a>Konfigurowanie możliwości zautomatyzowanego badania i reagowania w Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Microsoft 365 Defender obejmuje zaawansowane [funkcje zautomatyzowanego badania i reagowania](m365d-autoir.md), które pozwalają zaoszczędzić zespołowi ds. operacji zabezpieczeń dużo czasu i wysiłku. Dzięki [samonaprawianiu](m365d-autoir.md#how-automated-investigation-and-self-healing-works) te możliwości naśladują kroki, które analityk zabezpieczeń podejmie w celu zbadania zagrożeń i reagowania na nie, tylko szybciej i z większą możliwością skalowania.

W tym artykule opisano sposób konfigurowania zautomatyzowanego badania i reagowania w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, wykonując następujące kroki:

1. [Zapoznaj się z wymaganiami wstępnymi](#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender).
2. [Przejrzyj lub zmień poziom automatyzacji dla grup urządzeń](#review-or-change-the-automation-level-for-device-groups).
3. [Przejrzyj zasady zabezpieczeń i alertów w Office 365](#review-your-security-and-alert-policies-in-office-365).
4. [Upewnij się, że Microsoft 365 Defender jest włączona](#make-sure-microsoft-365-defender-is-turned-on).

Następnie po skonfigurowaniu można [wyświetlać akcje korygowania i zarządzać nimi w centrum akcji](m365d-autoir-actions.md).

## <a name="prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender"></a>Wymagania wstępne dotyczące zautomatyzowanego badania i reagowania w Microsoft 365 Defender

<br>

****

|Wymóg|Szczegóły|
|---|---|
|Wymagania dotyczące subskrypcji|Jedna z tych subskrypcji: <ul><li>Microsoft 365 E5</li><li>Microsoft 365 A5</li><li>Microsoft 365 E3 z dodatkiem Zabezpieczenia platformy Microsoft 365 E5</li><li>Microsoft 365 A3 z dodatkiem Microsoft 365 A5 Security</li><li>Office 365 E5 plus Enterprise Mobility + Security E5 plus Windows E5</li></ul> <p> Zobacz [Microsoft 365 Defender wymagania dotyczące licencjonowania](./prerequisites.md#licensing-requirements).|
|Wymagania dotyczące sieci|<ul><li>[Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp) włączone</li><li>[Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security) skonfigurowane</li><li>[integracja Microsoft Defender for Identity](/cloud-app-security/mdi-integration)</li></ul>|
|wymagania dotyczące urządzeń Windows|<ul><li>Windows 11</li><li>Windows 10 zainstalowana wersja 1709 lub nowsza (zobacz [informacje o wersji Windows](/windows/release-information/))</li><li>Skonfigurowano następujące usługi ochrony przed zagrożeniami:<ul><li>[Ochrona punktu końcowego w usłudze Microsoft Defender](../defender-endpoint/configure-endpoints.md)</li><li>[Program antywirusowy Microsoft Defender](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features)</li></ul></li></ul>|
|Ochrona zawartości poczty e-mail i plików Office|[Ochrona usługi Office 365 w usłudze Microsoft Defender](/microsoft-365/security/office-365-security/defender-for-office-365#configure-atp-policies) skonfigurowane|
|Uprawnienia|Aby skonfigurować możliwości zautomatyzowanego badania i reagowania, musisz mieć przypisaną rolę administratora globalnego lub administratora zabezpieczeń w Azure Active Directory (<https://portal.azure.com>) lub w Centrum administracyjne platformy Microsoft 365 (<https://admin.microsoft.com>). <p> Aby uzyskać uprawnienia wymagane do pracy z funkcjami zautomatyzowanego badania i reagowania, takimi jak przeglądanie, zatwierdzanie lub odrzucanie oczekujących akcji, zobacz [Wymagane uprawnienia do zadań centrum akcji](m365d-action-center.md#required-permissions-for-action-center-tasks).|
|

## <a name="review-or-change-the-automation-level-for-device-groups"></a>Przejrzyj lub zmień poziom automatyzacji dla grup urządzeń

To, czy są uruchamiane zautomatyzowane badania i czy akcje korygowania są wykonywane automatycznie, czy tylko po zatwierdzeniu urządzeń, zależą od pewnych ustawień, takich jak zasady grupy urządzeń w organizacji. Przejrzyj skonfigurowany poziom automatyzacji dla zasad grupy urządzeń.

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. Przejdź do **obszaru** >  Ustawienia **EndpointsDevice** >  **groups (Grupy urządzeń**) w obszarze **Uprawnienia**.

3. Przejrzyj zasady grupy urządzeń. W szczególności przyjrzyj się kolumnie **poziom automatyzacji** . Zalecamy automatyczne **korygowanie zagrożeń** przy użyciu funkcji Pełna.  Może być konieczne utworzenie lub edytowanie grup urządzeń w celu uzyskania żądanego poziomu automatyzacji. Aby uzyskać pomoc dotyczącą tego zadania, zobacz następujące artykuły:
   - [Jak są korygowane zagrożenia](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations#how-threats-are-remediated)
   - [Twórz grupy urządzeń i zarządzaj nimi](/windows/security/threat-protection/microsoft-defender-atp/machine-groups)

## <a name="review-your-security-and-alert-policies-in-office-365"></a>Przejrzyj zasady zabezpieczeń i alertów w Office 365

Firma Microsoft udostępnia wbudowane [zasady alertów](../../compliance/alert-policies.md) , które ułatwiają identyfikowanie pewnych zagrożeń. Te zagrożenia obejmują Exchange nadużywanie uprawnień administratora, działanie złośliwego oprogramowania, potencjalne zagrożenia zewnętrzne i wewnętrzne oraz zagrożenia związane z ładem informacyjnym. Niektóre alerty mogą wyzwalać [automatyczne badanie i reagowanie w Office 365](../office-365-security/office-365-air.md). Upewnij się, że funkcje [Ochrona usługi Office 365 w usłudze Defender](../office-365-security/defender-for-office-365.md) są poprawnie skonfigurowane.

Mimo że niektóre alerty i zasady zabezpieczeń mogą wyzwalać zautomatyzowane badania, *żadne akcje korygowania nie są wykonywane automatycznie dla poczty e-mail i zawartości*. Zamiast tego wszystkie akcje korygowania zawartości poczty e-mail i wiadomości e-mail czekają na zatwierdzenie przez zespół ds. operacji zabezpieczeń w [Centrum akcji](m365d-action-center.md).

Ustawienia zabezpieczeń w Office 365 pomagają chronić pocztę e-mail i zawartość. Aby wyświetlić lub zmienić te ustawienia, postępuj zgodnie ze wskazówkami w [temacie Ochrona przed zagrożeniami](../office-365-security/protect-against-threats.md).

1. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender przejdź do obszaru</a> **Zasady & Zasady** \> **dotyczące zagrożeń**.

2. Upewnij się, że skonfigurowano wszystkie poniższe zasady. Aby uzyskać pomoc i zalecenia, zobacz [Ochrona przed zagrożeniami](/microsoft-365/security/office-365-security/protect-against-threats).
   - [Ochrona przed złośliwym oprogramowaniem](../office-365-security/protect-against-threats.md#part-1---anti-malware-protection-in-eop)
   - [Ochrona przed wyłudzaniem informacji](../office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
   - [załączniki Sejf](../office-365-security/protect-against-threats.md#safe-attachments-policies-in-microsoft-defender-for-office-365)
   - [Bezpieczne linki](../office-365-security/protect-against-threats.md#safe-links-policies-in-microsoft-defender-for-office-365)
   - [Ochrona przed spamem](../office-365-security/protect-against-threats.md#part-3---anti-spam-protection-in-eop)

3. Upewnij się[, że Sejf załączniki dla SharePoint, OneDrive i Microsoft Teams](../office-365-security/mdo-for-spo-odb-and-teams.md) są włączone.

4. Upewnij się, że automatyczne [przeczyszczanie zerogodzin (ZAP) w Exchange Online](../office-365-security/zero-hour-auto-purge.md) obowiązuje.

5. (Ten krok jest opcjonalny). Przejrzyj [zasady alertów Office 365](../../compliance/alert-policies.md) w portalu zgodności usługi Microsoft Purview ([https://compliance.microsoft.com/compliancepolicies](https://compliance.microsoft.com/compliancepolicies)). Kilka domyślnych zasad alertów znajduje się w kategorii Zarządzanie zagrożeniami. Niektóre z tych alertów mogą wyzwalać automatyczne badanie i reagowanie. Aby dowiedzieć się więcej, zobacz [Domyślne zasady alertów](../../compliance/alert-policies.md#default-alert-policies).

## <a name="make-sure-microsoft-365-defender-is-turned-on"></a>Upewnij się, że Microsoft 365 Defender jest włączona

:::image type="content" source="../../media/mtp-enable/mtp-on.png" alt-text="Okienko nawigacji po lewej stronie w portalu Microsoft 365 Defender po włączeniu Microsoft 365 Defender" lightbox="../../media/mtp-enable/mtp-on.png":::

1. Zaloguj się do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>

2. W okienku nawigacji poszukaj pozycji **Zdarzenia & Alerty**, **Wyszukiwanie zagrożeń** i **Centrum akcji** , jak pokazano na poprzedniej ilustracji.
   - Jeśli widzisz **zdarzenia & alerty**, **wyszukiwanie zagrożeń** i **centrum akcji**, Microsoft 365 Defender jest włączona. Zobacz sekcję [Przeglądanie lub zmienianie poziomu automatyzacji dla grup urządzeń](#review-or-change-the-automation-level-for-device-groups) w tym artykule.
   - Jeśli *nie* widzisz **pozycji Incydenty**, **Centrum akcji** lub **Wyszukiwanie zagrożeń**, Microsoft 365 Defender mogą nie zostać włączone. W tym przypadku [odwiedź centrum akcji](m365d-action-center.md).

> [!TIP]
> Potrzebujesz pomocy? Zobacz [Włączanie Microsoft 365 Defender](m365d-enable.md).

## <a name="next-steps"></a>Następne kroki

- [Akcje korygowania w Microsoft 365 Defender](m365d-remediation-actions.md)
- [Odwiedź centrum akcji](m365d-action-center.md)
