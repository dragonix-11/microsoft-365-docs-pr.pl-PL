---
title: Przesyłanie strumieniowe zdarzeń programu Microsoft Defender dla punktu końcowego do Storage konta usługi
description: Dowiedz się, jak skonfigurować usługę Microsoft Defender dla punktu końcowego w celu przesyłania strumieniowego wydarzeń zaawansowanego chłonia na Twoje Storage konto.
keywords: nieprzetworzone eksportowanie danych, interfejs API przesyłania strumieniowego, interfejs API, centrum wydarzeń, magazyn platformy Azure, konto magazynu, zaawansowane szukanie, pierwotne udostępnianie danych
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
ms.custom: api
ms.openlocfilehash: a9db98456cc971b4ac4179cd4f3460dfe2137b91
ms.sourcegitcommit: cde34d38bdfb6335b980f1c48c6b218da6a64bf8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/20/2022
ms.locfileid: "63013311"
---
# <a name="configure-microsoft-defender-for-endpoint-to-stream-advanced-hunting-events-to-your-storage-account"></a>Konfigurowanie programu Microsoft Defender dla punktu końcowego w celu przesyłania strumieniowego wydarzeń zaawansowanego chłonia na Storage konto

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="before-you-begin"></a>Przed rozpoczęciem

1. Utwórz Storage [w](/azure/storage/common/storage-account-overview) dzierżawie.

2. Zaloguj się do dzierżawy platformy [Azure](https://ms.portal.azure.com/), przejdź do strony Subskrypcje > usługi > Resource Providers (Dostawcy zasobów> zarejestruj się w witrynie **Microsoft.insights**.

## <a name="enable-raw-data-streaming"></a>Włączanie przesyłania strumieniowego nieprzetworzonych danych

1. Zaloguj się [Microsoft 365 Defender](https://security.microsoft.com) ***Administrator globalny** _ lub _*_Administrator zabezpieczeń_**.

2. Przejdź na [stronę Ustawienia eksportu danych w](https://security.microsoft.com/interoperability/dataexport) aplikacji Microsoft 365 Defender.

3. Kliknij pozycję **Dodaj ustawienia eksportu danych**.

4. Wybierz nazwę nowych ustawień.

5. Wybierz **pozycję Przekaż zdarzenia do usługi Azure Storage**.

6. Wpisz swój **Storage zasobu klienta**. Aby uzyskać identyfikator zasobu Storage **konta, przejdź** do strony konta usługi Storage na karcie Właściwości portalu [Azure](https://ms.portal.azure.com/) \> \> i skopiuj tekst w obszarze identyfikator Storage **zasobu konta**:

   :::image type="content" alt-text="Obraz zasobu Centrum zdarzeń identyfikator1." source="images/storage-account-resource-id.png" lightbox="images/storage-account-resource-id.png":::

7. Wybierz zdarzenia, które chcesz przesyłać strumieniowo, i kliknij pozycję **Zapisz**.

## <a name="the-schema-of-the-events-in-the-storage-account"></a>Schemat zdarzeń na koncie Storage klienta

- Dla każdego typu zdarzenia zostanie utworzony kontener obiektów blob:

  :::image type="content" alt-text="Obraz zasobu Centrum zdarzeń o identyfikatorze 2." source="images/storage-account-event-schema.png" lightbox="images/storage-account-event-schema.png":::

- Schemat każdego wiersza w obiekcie blob to następujący kod JSON:

  ```json
  {
      "time": "<The time WDATP received the event>"
      "tenantId": "<Your tenant ID>"
      "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
      "properties": { <WDATP Advanced Hunting event as Json> }
  }
  ```

- Każdy obiekt blob zawiera wiele wierszy.

- Każdy wiersz zawiera nazwę zdarzenia, czas, gdy program Defender for Endpoint odebrał zdarzenie, dzierżawa, do której należy (zostaną odebrane tylko zdarzenia z dzierżawy) oraz zdarzenie w formacie JSON we właściwości o nazwie "properties".

- Aby uzyskać więcej informacji na temat schematu programu Microsoft Defender dla zdarzeń punktu końcowego, zobacz Omówienie [zaawansowanego](advanced-hunting-overview.md) wyszukiwania.

- W przypadku wyszukiwania zaawansowanego tabela **DeviceInfo** zawiera kolumnę o nazwie **MachineGroup** , która zawiera grupę urządzenia. Tutaj każde zdarzenie również będzie udekorowane tą kolumną. Aby [uzyskać więcej informacji,](machine-groups.md) zobacz Grupy urządzeń.

## <a name="data-types-mapping"></a>Mapowanie typów danych

Aby uzyskać typy danych dla naszych właściwości zdarzeń, wykonaj następujące czynności:

1. Zaloguj się, [aby Microsoft 365 Defender](https://security.microsoft.com) i przejdź do [strony Zaawansowane szukanie](https://security.microsoft.com/hunting-package).

2. Uruchom następujące zapytanie, aby uzyskać mapowanie typów danych dla każdego zdarzenia:

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Oto przykład zdarzenia Informacje o urządzeniu:

  ![Obraz zasobu Centrum zdarzeń IDENTYFIKATOR3.](images/data-types-mapping-query.png)

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie wyszukiwania zaawansowanego](advanced-hunting-overview.md)
- [Microsoft Defender for Endpoint Streaming API](raw-data-export.md)
- [Przesyłanie strumieniowe programu Microsoft Defender dla zdarzeń punktu końcowego do konta magazynu platformy Azure](raw-data-export-storage.md)
- [Dokumentacja Storage konta usługi Azure](/azure/storage/common/storage-account-overview)
