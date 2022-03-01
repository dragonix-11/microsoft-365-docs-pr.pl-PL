---
title: Ocenianie ochrony sieci
description: Zobacz, jak działa ochrona sieci, testując typowe scenariusze, przez które jest chronina.
keywords: Ochrona sieci, wykorzystywanie, złośliwa witryna internetowa, ip, domena, domeny, ocenianie, testowanie, pokaz
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
ms.topic: conceptual
author: dansimp
ms.author: dansimp
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365solution-scenario
ms.date: ''
ms.openlocfilehash: fb46d0c03aaaaad016ca13be5bfa26a19887794c
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63014709"
---
# <a name="evaluate-network-protection"></a>Ocenianie ochrony sieci

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[Ochrona sieci](network-protection.md) pomaga zapobiegać używaniu przez pracowników dowolnej aplikacji w celu uzyskania dostępu do niebezpiecznych domen, które mogą czynami wyłudzania informacji, oszustwami i złośliwą zawartością w Internecie.

Ten artykuł ułatwia ocenę ochrony sieci przez włączenie tej funkcji i pokierowanie Cię do witryny testowej. Witryny w tym artykule oceniania są złośliwe. Są to specjalnie tworzone witryny internetowe, które podszywają się pod złośliwe oprogramowanie. Witryna zreplikuje zachowanie, które działo się, jeśli użytkownik odwiedzi złośliwą witrynę lub domenę.

> [!TIP]
> Możesz również odwiedzić witrynę internetową scenariuszy pokazu programu Microsoft Defender w [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) , aby sprawdzić, jak działają inne funkcje ochrony.

> [!NOTE]
> Witryna pokazowa usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

## <a name="enable-network-protection-in-audit-mode"></a>Włączanie ochrony sieci w trybie inspekcji

Włącz ochronę sieci w trybie inspekcji, aby sprawdzić, które adresy IP i domeny zostałyby zablokowane. Możesz się upewnić, że nie wpływa on na aplikacje biznesowe, lub dowiedzieć się, jak często występują bloki.

1. Wpisz **tekst powershell** w menu Start kliknij prawym **przyciskiem myszy Windows PowerShell** a następnie wybierz **polecenie Uruchom jako administrator**
2. Wprowadź następujące polecenie cmdlet:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection AuditMode
    ```

### <a name="visit-a-fake-malicious-domain"></a>Odwiedź (fałszywy) złośliwy domenę

1. Otwórz program Internet Explorer, Google Chrome lub dowolną inną przeglądarkę.

2. Przejdź do witryny [https://smartscreentestratings2.net](https://smartscreentestratings2.net).

    Połączenie sieciowe będzie dozwolone i zostanie wyświetlony komunikat testowy.
    
    ![Przykładowe powiadomienie z komunikatem Połączenie zablokowane: Administrator IT Zabezpieczenia Windows zablokował to połączenie sieciowe. Skontaktuj się z działem pomocy technicznej IT.](images/np-notif.png)

> [!NOTE]
> Połączenia sieciowe mogą być pomyślne, nawet jeśli witryna jest blokowana przez ochronę sieci. Aby dowiedzieć się więcej, zobacz [Ochrona sieci i trójkierunkowy uścisk dłoni TCP](network-protection.md#network-protection-and-the-tcp-three-way-handshake).

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Przeglądanie zdarzeń ochrony sieci w przeglądarce Windows zdarzeń

Aby przejrzeć aplikacje, które zostałyby zablokowane, otwórz podgląd zdarzeń i przefiltruj identyfikator zdarzenia 1125 w dzienniku operacyjnym firmy Microsoft-Windows-Windows Defender-operacyjnym. W poniższej tabeli wymieniono wszystkie zdarzenia ochrony sieci.

| Identyfikator zdarzenia | Provide/Source | Opis |
|---|---|---|
| 5007 | Windows Defender (operacyjne) | Zdarzenie w przypadku zmiany ustawień |
| 1125 | Windows Defender (operacyjne) | Zdarzenie w przypadku inspekcji połączenia sieciowego |
| 1126 | Windows Defender (operacyjne) | Zdarzenie, gdy połączenie sieciowe jest zablokowane |

## <a name="see-also"></a>Zobacz też

- [Ochrona sieci](network-protection.md)

- [Ochrona sieci i trójkierunkowy uścisk dłoni protokołu TCP](network-protection.md#network-protection-and-the-tcp-three-way-handshake)

- [Włączanie ochrony sieci](enable-network-protection.md)

- [Rozwiązywanie problemów z ochroną sieci](troubleshoot-np.md)
