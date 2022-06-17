---
title: Ochrona danych organizacji za pomocą kontroli urządzenia
description: Monitorowanie zabezpieczeń danych organizacji za pomocą raportów kontroli urządzeń.
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.author: deniseb
author: denisebmsft
ms.reviewer: dansimp
ms.topic: article
manager: dansimp
audience: ITPro
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 6fe93be2ec244628f2bf2195eb453307235ea06f
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/16/2022
ms.locfileid: "66129190"
---
# <a name="device-control-report"></a>Raport kontroli urządzenia

**Dotyczy:** 
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

Ochrona punktu końcowego w usłudze Microsoft Defender kontrola urządzenia chroni przed utratą danych przez monitorowanie i kontrolowanie użycia nośników przez urządzenia w organizacji, takie jak korzystanie z wymiennych urządzeń pamięci masowej i dysków USB.

Raport kontroli urządzenia umożliwia wyświetlanie zdarzeń związanych z użyciem multimediów. Takie zdarzenia obejmują:

- **Zdarzenia inspekcji:** Przedstawia liczbę zdarzeń inspekcji występujących po nawiązaniu połączenia z nośnikiem zewnętrznym.
- **Zdarzenia zasad:** Pokazuje liczbę zdarzeń zasad występujących po wyzwoleniu zasad sterowania urządzeniami.

> [!NOTE]
> Zdarzenie inspekcji do śledzenia użycia multimediów jest domyślnie włączone dla urządzeń dołączonych do Ochrona punktu końcowego w usłudze Microsoft Defender.

## <a name="understanding-the-audit-events"></a>Omówienie zdarzeń inspekcji

Zdarzenia inspekcji obejmują:

- **Instalowanie i odinstalowywanie dysku USB:** Przeprowadź inspekcję zdarzeń generowanych podczas instalowania lub odinstalowyowania dysku USB.
- **PnP:** Plug and Play zdarzenia inspekcji są generowane po połączeniu magazynu wymiennego, drukarki lub nośnika Bluetooth.
- **Kontrola dostępu do magazynu wymiennego:** Zdarzenia są generowane po wyzwoleniu zasad kontroli dostępu magazynu wymiennego. Może to być inspekcja, blokowanie lub zezwalanie.

## <a name="monitor-device-control-security"></a>Monitorowanie zabezpieczeń sterowania urządzeniami

Kontrola urządzeń w usłudze Defender for Endpoint umożliwia administratorom zabezpieczeń korzystanie z narzędzi, które umożliwiają im śledzenie zabezpieczeń kontroli urządzeń w organizacji za pośrednictwem raportów. Raport kontroli urządzenia można znaleźć w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Przejdź do pozycji **Raporty** > **ogólne** > **raporty zabezpieczeń**. Znajdź kartę **Kontrolka urządzenia** i wybierz link, aby otworzyć raport. 

Karta Ochrona urządzenia na pulpicie **nawigacyjnym Raporty** pokazuje liczbę zdarzeń inspekcji generowanych przez typ nośnika w ciągu ostatnich 180 dni.

Przycisk **Wyświetl szczegóły** zawiera więcej danych użycia multimediów na stronie **raportu kontroli urządzenia** .

Strona zawiera pulpit nawigacyjny z zagregowaną liczbą zdarzeń na typ oraz listę zdarzeń i pokazuje 500 zdarzeń na stronę, ale administratorzy mogą przewijać w dół, aby wyświetlić więcej zdarzeń i filtrować zakres czasu, nazwę klasy multimediów i identyfikator urządzenia.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Detaileddevicecontrolreport.png" alt-text="Strona Szczegóły raportu kontrolki urządzenia w portalu Microsoft 365 Defender" lightbox="images/Detaileddevicecontrolreport.png":::

Po wybraniu zdarzenia zostanie wyświetlony wysuwany komunikat zawierający więcej informacji:

- **Szczegóły ogólne:** Data, tryb akcji, zasady i dostęp do tego zdarzenia.
- **Informacje o multimediach:** Informacje o nośniku obejmują nazwę nośnika, nazwę klasy, identyfikator GUID klasy, identyfikator urządzenia, identyfikator dostawcy, numer seryjny i typ magistrali.
- **Szczegóły lokalizacji:** Nazwa urządzenia, użytkownik i identyfikator urządzenia MDATP.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/devicecontrolreportfilter.png" alt-text="Strona Filtruj w raporcie kontroli urządzenia" lightbox="images/devicecontrolreportfilter.png":::

Aby wyświetlić działania w czasie rzeczywistym dla tego nośnika w całej organizacji, wybierz przycisk **Otwórz zaawansowane wyszukiwanie zagrożeń** . Obejmuje to osadzone, wstępnie zdefiniowane zapytanie.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Devicecontrolreportquery.png" alt-text="Strona Zapytanie w raporcie kontroli urządzenia" lightbox="images/Devicecontrolreportquery.png":::

Aby wyświetlić zabezpieczenia urządzenia, wybierz przycisk **Otwórz stronę urządzenia** na wysuwanym urządzeniu. Ten przycisk otwiera stronę jednostki urządzenia.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Devicesecuritypage.png" alt-text="Strona Jednostki urządzenia" lightbox="images/Devicesecuritypage.png":::

## <a name="reporting-delays"></a>Raportowanie opóźnień

Może wystąpić opóźnienie do 12 godzin od momentu nawiązania połączenia z nośnikiem do momentu, w którym zdarzenie zostanie odzwierciedlone na karcie lub na liście domen.
