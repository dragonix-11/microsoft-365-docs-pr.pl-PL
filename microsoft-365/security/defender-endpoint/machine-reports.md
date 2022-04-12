---
title: Raport dotyczący kondycji i zgodności urządzeń w Ochrona punktu końcowego w usłudze Microsoft Defender
description: Śledzenie wykrywania stanu kondycji urządzenia, stanu oprogramowania antywirusowego, platformy systemu operacyjnego i wersji Windows 10 przy użyciu raportu kondycji i zgodności urządzenia
keywords: stan kondycji, program antywirusowy, platforma systemu operacyjnego, wersja systemu Windows 10, wersja, kondycja, zgodność, stan
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
ms.openlocfilehash: d171db0d5009cc32c34c3bf95da907221f275410
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789277"
---
# <a name="device-health-and-compliance-report-in-microsoft-defender-for-endpoint"></a>Raport dotyczący kondycji i zgodności urządzeń w Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Program antywirusowy Microsoft Defender 

**Platformy**
- System Windows
- Mac OS
- Linux
- iOS
- Android

Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Raport o stanie urządzeń zawiera ogólne informacje o urządzeniach w organizacji. Raport zawiera popularne informacje pokazujące stan kondycji czujnika, stan programu antywirusowego, platformy systemu operacyjnego oraz wersje Windows 10 (i Windows 11).

Pulpit nawigacyjny jest podzielony na dwie sekcje:

:::image type="content" source="images/device-reports.png" alt-text="Raport urządzenia" lightbox="images/device-reports.png":::


<br>

****

|Sekcji|Opis|
|---|---|
|1|Trendy dotyczące urządzeń|
|2|Podsumowanie urządzenia (bieżący dzień)|
|||

## <a name="device-trends"></a>Trendy dotyczące urządzeń

Domyślnie trendy urządzeń wyświetlają informacje o urządzeniu z 30-dniowego okresu kończącego się w ostatnim pełnym dniu. Aby uzyskać lepsze spojrzenie na trendy występujące w organizacji, możesz dostosować okres raportowania, dostosowując pokazany okres. Aby dostosować okres, wybierz zakres czasu z opcji listy rozwijanej:

- 30 dni
- Trzy miesiące
- Sześć miesięcy
- Niestandardowe

> [!NOTE]
> Te filtry są stosowane tylko w sekcji trendy urządzeń. Nie ma to wpływu na sekcję podsumowania urządzenia.

## <a name="device-summary"></a>Podsumowanie urządzenia

Trendy dotyczące urządzeń pokazują popularne informacje o urządzeniu, ale podsumowanie urządzenia pokazuje informacje o urządzeniu o zakresie do bieżącego dnia.

> [!NOTE]
> Dane odzwierciedlone w sekcji podsumowania mają zakres do 180 dni przed bieżącą datą. Jeśli na przykład dzisiejsza data to 27 marca 2019 r., dane w sekcji podsumowania będą odzwierciedlać liczby od 28 września 2018 r. do 27 marca 2019 r.
>
> Filtr zastosowany do sekcji trendy nie jest stosowany w sekcji podsumowania.

Sekcja trendów urządzeń umożliwia przechodzenie do listy urządzeń przy użyciu odpowiedniego filtru. Na przykład kliknięcie paska Nieaktywne na karcie Stan kondycji czujnika spowoduje wyświetlenie listy urządzeń z wynikami pokazującymi tylko urządzenia, których stan czujnika jest nieaktywny.

## <a name="device-attributes"></a>Atrybuty urządzenia

Raport składa się z kart, które wyświetlają następujące atrybuty urządzenia:

- **Stan kondycji**: pokazuje informacje o stanie czujnika na urządzeniach, zapewniając zagregowany widok urządzeń, które są aktywne, występują zaburzenia komunikacji, nieaktywne lub nie są widoczne żadne dane czujnika.
- **Stan programu antywirusowego dla aktywnych urządzeń Windows 10**: pokazuje liczbę urządzeń i stan Program antywirusowy Microsoft Defender.
- **Platformy systemu operacyjnego**: pokazuje dystrybucję platform systemu operacyjnego, które istnieją w organizacji.
- **Windows 10 wersje**: pokazuje dystrybucję urządzeń Windows 10 i ich wersji w organizacji.

## <a name="filter-data"></a>Filtrowanie danych

Użyj podanych filtrów, aby dołączyć lub wykluczyć urządzenia z określonymi atrybutami.

Możesz wybrać wiele filtrów do zastosowania z atrybutów urządzenia.

> [!NOTE]
> Te filtry dotyczą **wszystkich** kart w raporcie.

Aby na przykład pokazać dane dotyczące urządzeń Windows 10 z aktywnym stanem kondycji czujnika:

1. W obszarze **Filtry > Stan kondycji czujnika > Aktywny**.
2. Następnie wybierz pozycję **Platformy systemu operacyjnego > Windows 10**.
3. Wybierz pozycję **Zastosuj**.

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)

## <a name="related-topic"></a>Temat pokrewny

- [Raport ochrony przed zagrożeniami](threat-protection-reports.md)
