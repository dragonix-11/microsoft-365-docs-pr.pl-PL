---
title: Konfigurowanie funkcji automatycznego badania i reagowania na Microsoft 365 Defender
description: Konfigurowanie automatycznego badania i reagowania dzięki funkcji samooceny w programie Microsoft 365 Defender
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
ms.openlocfilehash: 0e38dc36ca85425c033d2b8fd4828043b4043f1a
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499424"
---
# <a name="configure-automated-investigation-and-response-capabilities-in-microsoft-365-defender"></a>Konfigurowanie funkcji automatycznego badania i reagowania na Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Microsoft 365 Defender [zaawansowane funkcje automatycznego](m365d-autoir.md) badania i reakcji, które mogą zaoszczędzić czas i wysiłku Twojego zespołu związanego z operacjami zabezpieczającymi. W [przypadku samodzielnej ochrony](m365d-autoir.md#how-automated-investigation-and-self-healing-works) te funkcje odpowiadają czynnościom, które analityk zabezpieczeń miałby wykonać w celu zbadania zagrożeń i reagowania na nie, tylko szybciej i z większą możliwością skalowania.

W tym artykule opisano sposób konfigurowania automatycznego badania i odpowiedzi <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender za pomocą</a> tych kroków:

1. [Przejrzyj wymagania wstępne](#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender).
2. [Przejrzyj lub zmień poziom automatyzacji grup urządzeń](#review-or-change-the-automation-level-for-device-groups).
3. [Przejrzyj zasady zabezpieczeń i alertów w programie Office 365](#review-your-security-and-alert-policies-in-office-365).
4. [Upewnij się Microsoft 365 Defender że jest włączona](#make-sure-microsoft-365-defender-is-turned-on).

Następnie po skonfigurowaniu wszystkich czynności można wyświetlać działania naprawcze i zarządzać nimi [w Centrum akcji](m365d-autoir-actions.md).

## <a name="prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender"></a>Wymagania wstępne dotyczące automatycznego badania i reagowania w Microsoft 365 Defender

<br>

****

|Wymaganie|Szczegóły|
|---|---|
|Wymagania dotyczące subskrypcji|Jedna z tych subskrypcji: <ul><li>Microsoft 365 E5</li><li>Microsoft 365 A5</li><li>Microsoft 365 E3 pomocą Zabezpieczenia platformy Microsoft 365 E5 dodatku</li><li>Microsoft 365 A3 pomocą dodatku Microsoft 365 A5 Security</li><li>Office 365 E5 plus Enterprise Mobility + Security E5 oraz Windows E5</li></ul> <p> Zobacz [Microsoft 365 Defender dotyczące licencjonowania](./prerequisites.md#licensing-requirements).|
|Wymagania dotyczące sieci|<ul><li>[Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp) włączone</li><li>[Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security) skonfigurowane</li><li>[Microsoft Defender for Identity integracji z usługą](/cloud-app-security/mdi-integration)</li></ul>|
|Windows wymagań dotyczących urządzenia|<ul><li>Windows 11</li><li>Windows 10, wersja 1709 lub nowsza (zobacz [Windows o wersji](/windows/release-information/))</li><li>Skonfigurowano następujące usługi ochrony przed zagrożeniami:<ul><li>[Ochrona punktu końcowego w usłudze Microsoft Defender](../defender-endpoint/configure-endpoints.md)</li><li>[Program antywirusowy Microsoft Defender](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features)</li></ul></li></ul>|
|Ochrona zawartości wiadomości e-mail Office plików|[Ochrona usługi Office 365 w usłudze Microsoft Defender](/microsoft-365/security/office-365-security/defender-for-office-365#configure-atp-policies) skonfigurowane|
|Uprawnienia|Aby skonfigurować funkcje automatycznego badania i odpowiedzi, musisz mieć przypisaną rolę administratora globalnego lub administratora zabezpieczeń w programie Azure Active Directory (<https://portal.azure.com>) lub w Centrum administracyjne platformy Microsoft 365 (<https://admin.microsoft.com>). <p> Aby uzyskać uprawnienia wymagane do pracy z automatycznymi możliwościami badania i odpowiedzi, takimi jak przeglądanie, zatwierdzanie lub odrzucanie akcji oczekujących, zobacz Wymagane uprawnienia dla zadań [Centrum akcji](m365d-action-center.md#required-permissions-for-action-center-tasks).|
|

## <a name="review-or-change-the-automation-level-for-device-groups"></a>Przeglądanie lub zmienianie poziomu automatyzacji grup urządzeń

To, czy są uruchamiane automatyczne badania i czy akcje naprawcze są podejmowane automatycznie, czy tylko po zatwierdzeniu twoich urządzeń, zależą od określonych ustawień, takich jak zasady grupy urządzeń organizacji. Zapoznaj się ze skonfigurowanym poziomem automatyzacji dla zasad grupy urządzeń.

1. Przejdź do Microsoft 365 Defender konta ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. Przejdź do **Ustawienia** >  **EndpointsDevice** >  **grupy w** obszarze **Uprawnienia**.

3. Przejrzyj zasady grupy urządzeń. W szczególności przyjrzyj się kolumnie **Poziom automatyzacji** . Zalecamy automatyczne **korygowanie zagrożeń za pomocą pełnego zestawu.**  Aby uzyskać potrzebny poziom automatyzacji, może być konieczne utworzenie lub edytowanie grup urządzeń. Aby uzyskać pomoc na temat tego zadania, zobacz następujące artykuły:
   - [Jak są korygowane zagrożenia](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations#how-threats-are-remediated)
   - [Tworzenie grup urządzeń i zarządzanie nimi](/windows/security/threat-protection/microsoft-defender-atp/machine-groups)

## <a name="review-your-security-and-alert-policies-in-office-365"></a>Przeglądanie zasad zabezpieczeń i alertów w programie Office 365

Firma Microsoft udostępnia wbudowane [zasady alertów,](../../compliance/alert-policies.md) które ułatwiają identyfikowanie pewnych zagrożeń. Te czynniki ryzyka obejmują Exchange uprawnień administratora, aktywność złośliwego oprogramowania, potencjalne zagrożenia zewnętrzne i wewnętrzne oraz zagrożenia związane z zarządzaniem informacjami. Niektóre alerty mogą [wyzwalać automatyczne badanie i reagowanie Office 365](../office-365-security/office-365-air.md). Upewnij się, [Ochrona usługi Office 365 w usłudze Defender](../office-365-security/defender-for-office-365.md) skonfigurowane poprawnie.

Niektóre alerty i zasady zabezpieczeń mogą wyzwolić zautomatyzowane badania, jednak żadne akcje naprawcze nie są podejmowane automatycznie w przypadku wiadomości e-mail *i zawartości*. Zamiast tego wszystkie działania naprawcze dotyczące poczty e-mail i zawartości poczty e-mail oczekują na zatwierdzenie przez zespół operacji zabezpieczeń w [Centrum akcji](m365d-action-center.md).

Ustawienia zabezpieczeń w aplikacji Office 365 chronią pocztę e-mail i zawartość. Aby wyświetlić lub zmienić te ustawienia, postępuj zgodnie ze wskazówkami w te [sposób: Ochrona przed zagrożeniami](../office-365-security/protect-against-threats.md).

1. W portalu <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender przejdź</a> do **strony Zasady i & zasad** \> **zagrożeń**.

2. Upewnij się, że skonfigurowano wszystkie poniższe zasady. Aby uzyskać pomoc i zalecenia, zobacz [Ochrona przed zagrożeniami](/microsoft-365/security/office-365-security/protect-against-threats).
   - [Ochrona przed złośliwym oprogramowaniem](../office-365-security/protect-against-threats.md#part-1---anti-malware-protection-in-eop)
   - [Ochrona przed wyłudzaniem informacji](../office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
   - [Sejf załączników](../office-365-security/protect-against-threats.md#safe-attachments-policies-in-microsoft-defender-for-office-365)
   - [Bezpieczne linki](../office-365-security/protect-against-threats.md#safe-links-policies-in-microsoft-defender-for-office-365)
   - [Ochrona przed spamem](../office-365-security/protect-against-threats.md#part-3---anti-spam-protection-in-eop)

3. Upewnij się [Sejf że załączniki wiadomości SharePoint, OneDrive i](../office-365-security/mdo-for-spo-odb-and-teams.md) załączniki Microsoft Teams włączone.

4. Upewnij się, że automatyczne czyszczenie zerowej godziny [(ZAP) w programie Exchange Online](../office-365-security/zero-hour-auto-purge.md) jest w mocy.

5. (Ten krok jest opcjonalny). Przejrzyj swoje [Office 365 alertów](../../compliance/alert-policies.md) w Centrum zgodności platformy Microsoft 365 ([https://compliance.microsoft.com/compliancepolicies](https://compliance.microsoft.com/compliancepolicies)). Kilka domyślnych zasad alertów należy do kategorii Zarządzanie zagrożeniami. Niektóre z tych alertów mogą wyzwalać automatyczne badanie i reagowanie. Aby dowiedzieć się więcej, zobacz [Domyślne zasady alertów](../../compliance/alert-policies.md#default-alert-policies).

## <a name="make-sure-microsoft-365-defender-is-turned-on"></a>Upewnij się Microsoft 365 Defender że jest włączona

:::image type="content" source="../../media/mtp-enable/mtp-on.png" alt-text="Lewe okienko nawigacji w portalu Microsoft 365 Defender gdy Microsoft 365 Defender jest włączone" lightbox="../../media/mtp-enable/mtp-on.png":::

1. Logowanie się do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender-</a>

2. W okienku nawigacji odszukaj pozycję Alerty **&,** **Łów** i Centrum  akcji, jak pokazano na powyższym obrazie.
   - Jeśli zobaczysz **alerty o &****,** myśliwce i **centrum** akcji, Microsoft 365 Defender włączone. Zobacz [sekcję Przeglądanie lub zmienianie poziomu automatyzacji grup](#review-or-change-the-automation-level-for-device-groups) urządzeń w tym artykule.
   - Jeśli nie widzisz *zdarzenia***, Centrum** akcji lub Łów **, Microsoft 365 Defender** być włączone. W takim przypadku [odwiedź Centrum akcji](m365d-action-center.md).

> [!TIP]
> Potrzebujesz pomocy? Zobacz [Włączanie Microsoft 365 Defender](m365d-enable.md).

## <a name="next-steps"></a>Następne kroki

- [Działania naprawcze w programie Microsoft 365 Defender](m365d-remediation-actions.md)
- [Odwiedź Centrum akcji](m365d-action-center.md)
