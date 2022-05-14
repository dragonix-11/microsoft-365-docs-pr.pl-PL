---
title: Rozwiązywanie problemów z narzędziami raportowania dla Program antywirusowy Microsoft Defender
description: Identyfikowanie i rozwiązywanie typowych problemów podczas próby zgłaszania stanu ochrony Program antywirusowy Microsoft Defender w obszarze Zgodność aktualizacji
keywords: rozwiązywanie problemów, błąd, poprawka, aktualizowanie zgodności, oms, monitorowanie, raport, Program antywirusowy Microsoft Defender
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: bf65bb13ab45d127bf2302464f1948437e1fe02d
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65417979"
---
# <a name="troubleshoot-microsoft-defender-antivirus-reporting-in-update-compliance"></a>Rozwiąż problemy z raportowaniem programu antywirusowego Microsoft Defender w obszarze Zgodność aktualizacji

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

> [!IMPORTANT]
> 31 marca 2020 r. funkcja raportowania Program antywirusowy Microsoft Defender zgodności aktualizacji zostanie usunięta. Możesz nadal definiować i przeglądać zasady zgodności zabezpieczeń przy użyciu [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager), co umożliwia precyzyjniejszą kontrolę nad funkcjami zabezpieczeń i aktualizacjami.

Możesz użyć Program antywirusowy Microsoft Defender ze zgodnością aktualizacji. Zobaczysz stan licencji E3, B, F1, VL i Pro. Jednak w przypadku licencji E5 należy użyć [portalu Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Aby dowiedzieć się więcej na temat opcji licencjonowania, zobacz [Windows 10 opcje licencjonowania produktów](https://www.microsoft.com/licensing/product-licensing/windows10.aspx).

W przypadku korzystania z [Windows Analytics Update Compliance w celu uzyskania raportowania stanu ochrony urządzeń lub punktów końcowych w sieci korzystających](/windows/deployment/update/update-compliance-using#wdav-assessment) z Program antywirusowy Microsoft Defender mogą wystąpić problemy lub problemy.

Zazwyczaj najczęstszymi wskaźnikami problemu są:

- Zobaczysz tylko niewielką liczbę lub podzestaw wszystkich urządzeń, które miały być widoczne
- W ogóle nie widać żadnych urządzeń
- Widoczne raporty i informacje są nieaktualne (starsze niż kilka dni)

Aby uzyskać typowe kody błędów i identyfikatory zdarzeń związane z usługą Program antywirusowy Microsoft Defender, które nie są związane ze zgodnością aktualizacji, zobacz [Program antywirusowy Microsoft Defender zdarzenia](troubleshoot-microsoft-defender-antivirus.md).

Aby rozwiązać te problemy, należy wykonać trzy kroki:

1. Upewnij się, że spełniono wszystkie wymagania wstępne
2. Sprawdzanie łączności z usługą Windows Defender w chmurze
3. Przesyłanie dzienników pomocy technicznej

> [!IMPORTANT]
> Rozpoczęcie wyświetlania urządzeń w obszarze Zgodność aktualizacji zwykle trwa 3 dni.

## <a name="confirm-prerequisites"></a>Potwierdzanie wymagań wstępnych

Aby urządzenia były prawidłowo wyświetlane w usłudze Update Compliance, należy spełnić pewne wymagania wstępne dotyczące zarówno usługi Update Compliance, jak i Program antywirusowy Microsoft Defender:

>[!div class="checklist"]
>
> - Punkty końcowe używają Program antywirusowy Microsoft Defender jako jedynej aplikacji ochrony antywirusowej. [Użycie dowolnej innej aplikacji antywirusowej spowoduje wyłączenie Program antywirusowy Microsoft Defender,](microsoft-defender-antivirus-compatibility.md) a punkt końcowy nie będzie zgłaszany w obszarze Zgodność aktualizacji.
> - [Włączono ochronę dostarczaną przez chmurę](enable-cloud-protection-microsoft-defender-antivirus.md).
> - Punkty końcowe mogą [łączyć się z chmurą Program antywirusowy Microsoft Defender](configure-network-connections-microsoft-defender-antivirus.md#validate-connections-between-your-network-and-the-cloud)
> - Jeśli punkt końcowy jest uruchomiony Windows 10 wersji 1607 lub starszej, [Windows 10 dane diagnostyczne muszą być ustawione na poziom rozszerzony](/windows/configuration/configure-windows-diagnostic-data-in-your-organization#enhanced-level).
> - Minęły 3 dni od spełnienia wszystkich wymagań

"Można użyć Program antywirusowy Microsoft Defender ze zgodnością aktualizacji. Zobaczysz stan licencji E3, B, F1, VL i Pro. Jednak w przypadku licencji E5 należy użyć portalu Ochrona punktu końcowego w usłudze Microsoft Defender (/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Aby dowiedzieć się więcej o opcjach licencjonowania, zobacz Windows 10 opcje licencjonowania produktów"

Jeśli powyższe wymagania wstępne zostały spełnione, może być konieczne przejście do następnego kroku, aby zebrać informacje diagnostyczne i wysłać je do nas.

> [!div class="nextstepaction"]
> [Zbieranie danych diagnostycznych na potrzeby rozwiązywania problemów z zgodnością aktualizacji](collect-diagnostic-data.md)

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)

## <a name="related-topics"></a>Tematy pokrewne

- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Wdrażanie Program antywirusowy Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
