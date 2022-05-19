---
title: Konfigurowanie możliwości zautomatyzowanego badania i korygowania
description: Skonfiguruj możliwości zautomatyzowanego badania i korygowania w Ochrona punktu końcowego w usłudze Microsoft Defender.
keywords: konfigurowanie, konfigurowanie, automatyzacja, badanie, wykrywanie, alerty, korygowanie, reagowanie
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: how-to
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.openlocfilehash: 7e94cd14f392eb47a9b747cfb5e5f846f03fdc63
ms.sourcegitcommit: e624221597480295b799d56568c4f6f56d40b41d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2022
ms.locfileid: "65535763"
---
# <a name="configure-automated-investigation-and-remediation-capabilities-in-microsoft-defender-for-endpoint"></a>Konfigurowanie możliwości zautomatyzowanego badania i korygowania w Ochrona punktu końcowego w usłudze Microsoft Defender

**Dotyczy:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft Defender dla Firm](../defender-business/mdb-overview.md)

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Jeśli Twoja organizacja korzysta z [usługi Defender for Endpoint](/windows/security/threat-protection/) (lub [Defender for Business](../defender-business/mdb-overview.md)), [zautomatyzowane funkcje badania i korygowania](/microsoft-365/security/defender-endpoint/automated-investigations) mogą zaoszczędzić czas i nakład pracy zespołu ds. operacji zabezpieczeń. Jak opisano w [tym wpisie w blogu](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/enhance-your-soc-with-microsoft-defender-atp-automatic/ba-p/848946), te możliwości naśladują idealne kroki wykonywane przez analityka zabezpieczeń w celu zbadania i skorygowania zagrożeń. [Dowiedz się więcej o zautomatyzowanym badaniu i korygowaniu](/microsoft-365/security/defender-endpoint/automated-investigations).

Aby skonfigurować automatyczne badanie i korygowanie:

1. [Włącz funkcje](#turn-on-automated-investigation-and-remediation); I
2. [Konfigurowanie grup urządzeń](#set-up-device-groups).

## <a name="turn-on-automated-investigation-and-remediation"></a>Włączanie zautomatyzowanego badania i korygowania

1. Jako administrator globalny lub administrator zabezpieczeń przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz **pozycję Ustawienia**.

3. Wybierz pozycję **Punkty końcowe**, a następnie wybierz pozycję **Funkcje zaawansowane**.

4. Włącz zarówno **automatyczne badanie,** jak i **automatyczne rozwiązywanie alertów**.

## <a name="set-up-device-groups"></a>Konfiguruj grupy urządzeń

> [!NOTE]
> Ta procedura nie ma zastosowania do usługi Defender dla Firm.

1. W portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) na stronie **Ustawienia** w obszarze **Uprawnienia** wybierz pozycję **Grupy urządzeń**.

2. Wybierz pozycję **+ Dodaj grupę urządzeń**.

3. Utwórz co najmniej jedną grupę urządzeń w następujący sposób:

   - Określ nazwę i opis grupy urządzeń.
   - Na **liście Poziom automatyzacji** wybierz poziom, taki jak **Pełny — automatycznie koryguj zagrożenia**. Poziom automatyzacji określa, czy akcje korygowania są wykonywane automatycznie, czy tylko po zatwierdzeniu. Aby dowiedzieć się więcej, zobacz [Poziomy automatyzacji w zautomatyzowanym badaniu i korygowaniu](automation-levels.md).
   - W sekcji **Członkowie** użyj co najmniej jednego warunku, aby zidentyfikować i uwzględnić urządzenia.
   - Na karcie **Dostęp użytkownika** wybierz [grupy Azure Active Directory](/azure/active-directory/fundamentals/active-directory-manage-groups?context=azure/active-directory/users-groups-roles/context/ugr-context), które powinny mieć dostęp do tworzonej grupy urządzeń.

4. Po zakończeniu konfigurowania grupy urządzeń wybierz pozycję **Gotowe** .

## <a name="next-steps"></a>Następne kroki

- [Odwiedź Centrum akcji, aby wyświetlić oczekujące i ukończone akcje korygowania](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)
- [Przeglądanie i zatwierdzanie oczekujących akcji](/microsoft-365/security/defender-endpoint/manage-auto-investigation)

## <a name="see-also"></a>Zobacz też

- [Rozwiązywanie problemów z wynikami fałszywie pozytywnymi/negatywnymi w ochronie punktu końcowego w usłudze Microsoft Defender](defender-endpoint-false-positives-negatives.md)
