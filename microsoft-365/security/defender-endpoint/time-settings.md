---
title: Microsoft 365 Defender strefie czasowej
description: Użyj informacji zawartych w tym miejscu, aby skonfigurować Microsoft 365 Defender strefie czasowej i wyświetlić informacje o licencji.
keywords: ustawienia, Microsoft Defender, inteligencja zagrożeń dotyczących bezpieczeństwa i prywatności, Program Microsoft Defender for Endpoint, strefa czasowa, utc, czas lokalny, licencja
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
ms.openlocfilehash: 4353bbfc0ce11c4a767ca599ecb23a1ab4f77a56
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010431"
---
# <a name="microsoft-365-defender-time-zone-settings"></a>Microsoft 365 Defender strefie czasowej

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)


> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-settings-abovefoldlink)

Użyj menu **Strefa czasowa** ikona1 ![ustawień strefy czasowej.](images/atp-time-zone.png) aby skonfigurować strefę czasową i wyświetlić informacje o licencji.

## <a name="time-zone-settings"></a>Ustawienia strefy czasowej

Ważny jest aspekt czasu podczas oceny i analizy postrzeganej oraz rzeczywistych cyberataków.

Cyberforensic investigations often rely on time stamps to piece together the sequence of events. Ważne jest, aby Twój system odzwierciedlał prawidłowe ustawienia strefy czasowej.

Program Microsoft Defender for Endpoint może wyświetlać uniwersalny czas koordynowany (UTC) lub czas lokalny.

Bieżące ustawienie strefy czasowej jest widoczne w ustawieniach usługi Microsoft Defender. Wyświetlaną strefę czasową można zmienić w menu **Strefa czasowa** w **Ustawienia > zabezpieczeń**.

### <a name="utc-time-zone"></a>Strefa czasowa UTC

Program Microsoft Defender for Endpoint używa domyślnie czasu UTC.

Ustawienie strefy czasowej programu Microsoft Defender dla punktu końcowego na CZAS UTC spowoduje wyświetlanie wszystkich sygnatur czasowych systemu (alertów, zdarzeń i innych) w czasie UTC dla wszystkich użytkowników. Może to ułatwić analitykom zabezpieczeń pracującym w różnych miejscach na świecie używanie tych samych sygnatur czasowych podczas badania zdarzeń.

### <a name="local-time-zone"></a>Lokalna strefa czasowa

Możesz zdecydować, czy usługa Microsoft Defender for Endpoint ma korzystać z ustawień lokalnej strefy czasowej. Wszystkie alerty i zdarzenia będą wyświetlane przy użyciu lokalnej strefy czasowej.

Lokalna strefa czasowa jest  pochodzić z ustawień regionalnych urządzenia. Zmiana ustawień regionalnych spowoduje również zmianę strefy czasowej programu Microsoft Defender for Endpoint. Wybranie tego ustawienia oznacza, że sygnatury czasowe wyświetlane w programie Microsoft Defender for Endpoint zostaną dostosowane do czasu lokalnego dla wszystkich użytkowników programu Microsoft Defender dla użytkowników punktu końcowego. Analitycy zlokalizowani w różnych lokalizacjach globalnych będą teraz widzieć alerty programu Microsoft Defender for Endpoint zgodnie z ich ustawieniami regionalnymi.

Wybranie czasu lokalnego może być przydatne, jeśli analitycy znajdują się w jednym miejscu. W tym przypadku łatwiej jest skorelować zdarzenia z czasem lokalnym, na przykład, gdy użytkownik lokalny kliknął link do podejrzanej wiadomości e-mail.

### <a name="set-the-time-zone"></a>Ustawianie strefy czasowej

Strefa czasowa programu Microsoft Defender for Endpoint jest domyślnie ustawiona na czas UTC. Ustawienie strefy czasowej zmienia również godziny dla wszystkich widoków programu Microsoft Defender dla punktów końcowych.

Aby ustawić strefę czasową:

1. Kliknij menu **Ustawienia** w Microsoft 365 Defender [Strefy](https://security.microsoft.com/) ![czasowej portalu 3](images/atp-time-zone.png).
2. Wybierz **pozycję Centrum zabezpieczeń**.
3. Wybierz **pozycję Strefa czasowa** i ustaw strefę czasową na czas UTC lub lokalną strefę czasową.

### <a name="regional-settings"></a>Ustawienia regionalne

Aby zastosować różne formaty daty dla programu Microsoft Defender dla punktu końcowego, użyj ustawień regionalnych dla przeglądarki Internet Explorer (IE) i programu Microsoft Edge (Edge). Jeśli korzystasz z innej przeglądarki, takiej jak Google Chrome, wykonaj wymagane czynności, aby zmienić ustawienia daty i daty dla tej przeglądarki. 

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
