---
title: Rozwiązywanie problemów z narzędziami do raportowania dla Program antywirusowy Microsoft Defender
description: Identyfikowanie i rozwiązywanie typowych problemów podczas próby zgłaszania w Program antywirusowy Microsoft Defender stanu ochrony w aktualizacji zgodności
keywords: rozwiązywanie problemów, błąd, poprawka, aktualizacja zgodności, oms, monitorowanie, raport, Program antywirusowy Microsoft Defender
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
ms.openlocfilehash: e17f50eb02fa6fbc3c34526ca064543b7afbdea2
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997266"
---
# <a name="troubleshoot-microsoft-defender-antivirus-reporting-in-update-compliance"></a>Rozwiązywanie problemów Program antywirusowy Microsoft Defender raportów w zakresie zgodności aktualizacji

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!IMPORTANT]
> 31 marca 2020 r. funkcja raportowania Program antywirusowy Microsoft Defender zgodności aktualizacji zostanie usunięta. Możesz nadal definiować i przeglądać zasady zgodności zabezpieczeń przy [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager), co umożliwia precyzyjniejszą kontrolę nad funkcjami i aktualizacjami zabezpieczeń.

Możesz korzystać z usługi Program antywirusowy Microsoft Defender zgodnością. Zobaczysz stan licencji E3, B, F1, VL i licencji Pro zbiorowe. Jednak w przypadku licencji E5 musisz użyć portalu [programu Microsoft Defender dla punktu końcowego](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Aby dowiedzieć się więcej o opcjach licencjonowania, [Windows 10 opcje licencjonowania produktu](https://www.microsoft.com/licensing/product-licensing/windows10.aspx).

Gdy korzystasz z usługi [Windows Analytics Update Compliance](/windows/deployment/update/update-compliance-using#wdav-assessment), aby uzyskać raportowanie stanu ochrony urządzeń lub punktów końcowych w Twojej sieci, które korzystają z usługi Program antywirusowy Microsoft Defender, mogą wystąpić problemy lub problemy.

Zazwyczaj najbardziej typowe wskaźniki problemu to:

- Widzisz tylko niewielką liczbę lub podzbiór wszystkich urządzeń, na których oczekiwano
- Nie widać żadnych urządzeń
- Raporty i informacje, które widzisz, są nieaktualne (starsze niż kilka dni)

Aby uzyskać typowe kody błędów i identyfikatory zdarzeń związane z usługą Program antywirusowy Microsoft Defender, które nie są związane z zgodnością z aktualizacją, zobacz Program antywirusowy Microsoft Defender [zdarzeń](troubleshoot-microsoft-defender-antivirus.md).

Rozwiązywanie tych problemów można rozwiązać w trzech krokach:

1. Potwierdzanie, że zostały spełnione wszystkie wymagania wstępne
2. Sprawdzanie łączności z usługą Windows Defender w chmurze
3. Przesyłanie dzienników pomocy technicznej

> [!IMPORTANT]
> Zwykle pojawianie się urządzeń w zakresie zgodności aktualizacji trwa 3 dni.

## <a name="confirm-prerequisites"></a>Potwierdź wymagania wstępne

Aby urządzenia prawidłowo były wyświetlane w zgodności z aktualizacją, musisz spełnić pewne wymagania wstępne dotyczące usługi zgodności aktualizacji oraz dla nowych Program antywirusowy Microsoft Defender:

>[!div class="checklist"]
>
> - Punkty końcowe są używania Program antywirusowy Microsoft Defender jako jedynej aplikacji ochrony antywirusowej. [Korzystanie z dowolnej innej aplikacji antywirusowej spowoduje Program antywirusowy Microsoft Defender się,](microsoft-defender-antivirus-compatibility.md) a punkt końcowy nie zostanie zgłoszony w zgodności aktualizacji.
> - [Włączona jest ochrona w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md).
> - Punkty końcowe mogą [łączyć się z chmurą Program antywirusowy Microsoft Defender danych](configure-network-connections-microsoft-defender-antivirus.md#validate-connections-between-your-network-and-the-cloud)
> - Jeśli punkt końcowy jest uruchomiony Windows 10 wersji 1607 lub wcześniejszej, Windows 10 dla danych diagnostycznych należy ustawić [poziom Rozszerzony](/windows/configuration/configure-windows-diagnostic-data-in-your-organization#enhanced-level).
> - Mi zostały 3 dni, od momentu, gdy zostały spełnione wszystkie wymagania

"Możesz korzystać z usługi Program antywirusowy Microsoft Defender zgodnością. Zobaczysz stan licencji E3, B, F1, VL i licencji Pro zbiorowe. Jednak w przypadku licencji E5 musisz użyć portalu programu Microsoft Defender for Endpoint (/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Aby dowiedzieć się więcej o opcjach licencjonowania, Windows 10 opcje licencjonowania produktu"

Jeśli wszystkie powyższe wymagania wstępne zostały spełnione, może być konieczne zapoznanie się z następnym krokiem w celu zebrania informacji diagnostycznych i wysłania ich do nas.

> [!div class="nextstepaction"]
> [Zbieranie danych diagnostycznych na potrzeby rozwiązywania problemów ze zgodnością aktualizacji](collect-diagnostic-data.md)


## <a name="related-topics"></a>Tematy pokrewne

- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Wdrażanie Program antywirusowy Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
