---
title: Microsoft 365 Defender strefie czasowej
description: Użyj informacji zawartych w tym miejscu, aby skonfigurować Microsoft 365 Defender strefie czasowej i wyświetlić informacje o licencji.
keywords: settings, Microsoft Defender, intelligence threat intelligence, Ochrona punktu końcowego w usłudze Microsoft Defender, time zone, utc, local time, license
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: adf693bded45dcb44abd8d1e7892e5edc7b65585
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467164"
---
# <a name="microsoft-365-defender-time-zone-settings"></a>Microsoft 365 Defender strefie czasowej

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)


> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-settings-abovefoldlink)

Użyj menu **Strefa czasowa** , aby skonfigurować strefę czasową i wyświetlić informacje o licencji.
:::image type="content" source="images/atp-time-zone.png" alt-text="Ustawienia strefy czasowej-1" lightbox="images/atp-time-zone.png":::

## <a name="time-zone-settings"></a>Ustawienia strefy czasowej

Ważny jest aspekt czasu podczas oceny i analizy postrzeganej oraz rzeczywistych cyberataków.

Cyberforensic investigations often rely on time stamps to piece together the sequence of events. Ważne jest, aby Twój system odzwierciedlał prawidłowe ustawienia strefy czasowej.

Ochrona punktu końcowego w usłudze Microsoft Defender uniwersalny czas koordynowany (UTC) lub czas lokalny.

Bieżące ustawienie strefy czasowej jest wyświetlane w Ochrona punktu końcowego w usłudze Microsoft Defender czasowej. Wyświetlaną strefę czasową można zmienić w menu **Strefa czasowa** .

:::image type="content" source="images/atp-time-zone-menu.png" alt-text="Ustawienia strefy czasowej-2" lightbox="images/atp-time-zone-menu.png":::

### <a name="utc-time-zone"></a>Strefa czasowa UTC

Ochrona punktu końcowego w usłudze Microsoft Defender czasu UTC.

Ustawienie czasu Ochrona punktu końcowego w usłudze Microsoft Defender utc spowoduje wyświetlanie wszystkich sygnatur czasowych systemu (alertów, wydarzeń i innych) w czasie UTC dla wszystkich użytkowników. Może to ułatwić analitykom zabezpieczeń pracującym w różnych miejscach na świecie używanie tych samych sygnatur czasowych podczas badania zdarzeń.

### <a name="local-time-zone"></a>Lokalna strefa czasowa

Możesz zdecydować, czy Ochrona punktu końcowego w usłudze Microsoft Defender ustawienia lokalnej strefy czasowej. Wszystkie alerty i zdarzenia będą wyświetlane przy użyciu lokalnej strefy czasowej.

Lokalna strefa czasowa jest  pochodzić z ustawień regionalnych urządzenia. Zmiana ustawień regionalnych spowoduje również zmianę Ochrona punktu końcowego w usłudze Microsoft Defender czasowej. Wybranie tego ustawienia oznacza, że sygnatury czasowe wyświetlane w Ochrona punktu końcowego w usłudze Microsoft Defender zostaną dostosowane do czasu lokalnego dla wszystkich Ochrona punktu końcowego w usłudze Microsoft Defender użytkowników. Analitycy zlokalizowani w różnych lokalizacjach globalnych będą teraz widzieć alerty Ochrona punktu końcowego w usłudze Microsoft Defender zgodnie z ich ustawieniami regionalnymi.

Wybranie czasu lokalnego może być przydatne, jeśli analitycy znajdują się w jednym miejscu. W tym przypadku łatwiej jest skorelować zdarzenia z czasem lokalnym, na przykład, gdy użytkownik lokalny kliknął link do podejrzanej wiadomości e-mail.

### <a name="set-the-time-zone"></a>Ustawianie strefy czasowej

Strefa Ochrona punktu końcowego w usłudze Microsoft Defender jest domyślnie ustawiona na czas UTC. Ustawienie strefy czasowej zmienia również godziny dla wszystkich Ochrona punktu końcowego w usłudze Microsoft Defender widoków.

Aby ustawić strefę czasową:

1. Kliknij menu **Strefa czasowa** .
   :::image type="content" source="images/atp-time-zone.png" alt-text="Ustawienia strefy czasowej-3" lightbox="images/atp-time-zone.png":::
1. Wybierz wskaźnik **czasu UTC strefy czasowej** .
1. Wybierz **czas UTC strefy** czasowej lub lokalną strefę czasową, na przykład -7:00.

### <a name="regional-settings"></a>Ustawienia regionalne

Aby zastosować różne formaty daty dla przeglądarki Ochrona punktu końcowego w usłudze Microsoft Defender, użyj ustawień regionalnych dla przeglądarki Internet Explorer (IE) i programu Microsoft Edge (Edge). Jeśli korzystasz z innej przeglądarki, takiej jak Google Chrome, wykonaj wymagane czynności, aby zmienić ustawienia daty i daty dla tej przeglądarki. 

#### <a name="internet-explorer-ie-and-microsoft-edge"></a>Internet Explorer (IE) i Microsoft Edge

IE i Microsoft Edge z **ustawień regionu** skonfigurowanych w opcji **Zegary,** język i region w Panelu sterowania. 

#### <a name="known-issues-with-regional-formats"></a>Znane problemy dotyczące formatów regionalnych

##### <a name="date-and-time-formats"></a>Formaty daty i godziny

Istnieją pewne znane problemy dotyczące formatów daty i godziny. Jeśli skonfigurujesz ustawienia regionalne na inne niż obsługiwane formaty, portal może nie odzwierciedlać ustawień poprawnie.

Obsługiwane są następujące formaty daty i godziny:

- Format daty yy-mm-dd
- Format daty dd/MM/yyyy
- Format godziny gg:mm:ss (format 12-godzinny)

Następujące formaty daty i godziny nie są obecnie obsługiwane:

- Format daty yyyy-MM-dd
- Format daty dd-MMM-yy
- Format daty dd/MM/yy
- Format daty yy-MM-dd
- Format daty z formatem yy. Będzie pokazywać tylko yyyy.
- Format godziny HH:mm:ss (format 24-godzinny)

##### <a name="decimal-symbol-used-in-numbers"></a>Symbol dziesiętny używany w liczbach

Używany symbol dziesiętny jest zawsze kropką, nawet jeśli w ustawieniach **formatu liczb** w **ustawieniach Region jest wybrany przecinek** . Na przykład 15,5K jest wyświetlane jako 15,5K.
