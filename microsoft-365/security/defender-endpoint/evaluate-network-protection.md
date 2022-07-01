---
title: Oceń ochronę sieci
description: Zobacz, jak działa ochrona sieci, testując typowe scenariusze, przed jakimi się chroni.
keywords: Ochrona sieci, luki w zabezpieczeniach, złośliwa witryna internetowa, adres IP, domena, domeny, ocena, testowanie, pokaz
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
ms.collection:
- M365-security-compliance
ms.date: ''
ms.openlocfilehash: 2826c623437760d86aad54e4aa36900bdad68082
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603951"
---
# <a name="evaluate-network-protection"></a>Oceń ochronę sieci

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[Ochrona sieci](network-protection.md) pomaga uniemożliwić pracownikom korzystanie z dowolnej aplikacji w celu uzyskania dostępu do niebezpiecznych domen, które mogą hostować wyłudzanie informacji, luki w zabezpieczeniach i inną złośliwą zawartość w Internecie.

Ten artykuł pomaga ocenić ochronę sieci, włączając funkcję i prowadząc do lokacji testowej. Witryny w tym artykule ewaluacji nie są złośliwe. Są to specjalnie utworzone witryny internetowe, które udają złośliwe. Lokacja będzie replikować zachowanie, które miałoby miejsce, gdyby użytkownik odwiedził złośliwą witrynę lub domenę.

> [!TIP]
> Możesz również odwiedzić witrynę internetową scenariuszy demonstracyjnych usługi Microsoft Defender pod adresem [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) , aby zobaczyć, jak działają inne funkcje ochrony.

> [!NOTE]
> Witryna demonstracyjna usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

## <a name="enable-network-protection-in-audit-mode"></a>Włączanie ochrony sieci w trybie inspekcji

Włącz ochronę sieci w trybie inspekcji, aby zobaczyć, które adresy IP i domeny zostałyby zablokowane. Możesz upewnić się, że nie ma to wpływu na aplikacje biznesowe lub zorientować się, jak często występują bloki.

1. Wpisz **program PowerShell** w menu Start, kliknij prawym przyciskiem myszy **Windows PowerShell** i wybierz pozycję **Uruchom jako administrator**
2. Wprowadź następujące polecenie cmdlet:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection AuditMode
    ```

### <a name="visit-a-fake-malicious-domain"></a>Odwiedź (fałszywą) złośliwą domenę

1. Otwórz program Internet Explorer, Przeglądarkę Google Chrome lub dowolną inną wybraną przeglądarkę.

2. Przejdź do witryny [https://smartscreentestratings2.net](https://smartscreentestratings2.net).

    Połączenie sieciowe będzie dozwolone i zostanie wyświetlony komunikat testowy.
    
    :::image type="content" source="images/np-notif.png" alt-text="Powiadomienie o zablokowaniu połączenia" lightbox="images/np-notif.png":::

> [!NOTE]
> Połączenia sieciowe mogą zakończyć się pomyślnie, nawet jeśli lokacja jest zablokowana przez ochronę sieci. Aby dowiedzieć się więcej, zobacz [Ochrona sieci i uzgadnianie trójstopnie protokołu TCP](network-protection.md#network-protection-and-the-tcp-three-way-handshake).

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Przejrzyj zdarzenia ochrony sieci w systemie Windows Podgląd zdarzeń

Aby przejrzeć aplikacje, które zostałyby zablokowane, otwórz Podgląd zdarzeń i odfiltruj identyfikator zdarzenia 1125 w dzienniku Microsoft-Windows-Windows Defender/Operational. W poniższej tabeli wymieniono wszystkie zdarzenia ochrony sieci.

| Identyfikator zdarzenia | Podaj/źródło | Opis |
|---|---|---|
| 5007 | Windows Defender (operacyjne) | Zdarzenie po zmianie ustawień |
| 1125 | Windows Defender (operacyjne) | Zdarzenie, gdy połączenie sieciowe jest poddawane inspekcji |
| 1126 | Windows Defender (operacyjne) | Zdarzenie, gdy połączenie sieciowe jest zablokowane |

## <a name="see-also"></a>Zobacz też

- [Ochrona sieci](network-protection.md)

- [Ochrona sieci i trójstopnie uzgadnianie protokołu TCP](network-protection.md#network-protection-and-the-tcp-three-way-handshake)

- [Włączanie ochrony sieci](enable-network-protection.md)

- [Rozwiązywanie problemów z ochroną sieci](troubleshoot-np.md)
