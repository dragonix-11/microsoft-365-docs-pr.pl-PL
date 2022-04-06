---
title: Przesyłanie strumieniowe Microsoft 365 Defender do konta Storage
description: Dowiedz się, jak skonfigurować usługę Microsoft 365 Defender przesyłania strumieniowego wydarzeń zaawansowanego chłonia na Storage konto.
keywords: nieprzetworzone eksportowanie danych, interfejs API przesyłania strumieniowego, interfejs API, centrum wydarzeń, magazyn platformy Azure, konto magazynu, zaawansowane szukanie, pierwotne udostępnianie danych
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: ed62807c0efc7003bab8fc725c2753c3d91ef1d6
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64501228"
---
# <a name="configure-microsoft-365-defender-to-stream-advanced-hunting-events-to-your-storage-account"></a>Skonfiguruj Microsoft 365 Defender, aby przesyłać strumieniowo wydarzenia z zaawansowanego chłonia do Storage konta

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="before-you-begin"></a>Przed rozpoczęciem

1. Utwórz Storage [w](/azure/storage/common/storage-account-overview) dzierżawie.

2. Zaloguj się do dzierżawy platformy [Azure](https://ms.portal.azure.com/), przejdź do strony Subskrypcje **> usługi > Resource Providers** (Dostawcy zasobów> Zarejestruj się w witrynie Microsoft.Szczegółowe informacje.

## <a name="enable-raw-data-streaming"></a>Włączanie przesyłania strumieniowego nieprzetworzonych danych

1. Zaloguj się <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> ***Administrator globalny** _ lub _*_Administrator zabezpieczeń_**.

2. Przejdź do **Ustawienia** \> **Microsoft 365 Defender** \> **Streaming API**. Aby przejść bezpośrednio do strony **interfejsu API przesyłania strumieniowego**, użyj .<https://security.microsoft.com/settings/mtp_settings/raw_data_export>

3. Kliknij pozycję **Dodaj**.

4. W **wyświetlonym wysuwanych menu dodaj nowe ustawienia interfejsu API** przesyłania strumieniowego skonfiguruj następujące ustawienia:
   1. **Nazwa**: wybierz nazwę nowych ustawień.
   2. Wybierz **pozycję Przekaż zdarzenia do usługi Azure Storage**.
   3. W **wyświetlonym Storage Identyfikator** zasobu klienta wpisz swój Storage **zasobu konta**. Aby uzyskać identyfikator **Storage konta**, <https://portal.azure.com>otwórz Azure Portal stronie ,  \> \> kliknij pozycję konta Storage, przejdź do karty właściwości i skopiuj tekst w obszarze **Storage Identyfikator zasobu konta**.

      :::image type="content" source="../defender-endpoint/images/storage-account-resource-id.png" alt-text="Identyfikator Storage zasobu klienta" lightbox="../defender-endpoint/images/storage-account-resource-id.png":::

   4. W menu **wysuwanego menu Dodaj nowe ustawienia interfejsu API przesyłania strumieniowego** wybierz **typy** zdarzeń, które chcesz przesyłać strumieniowo.

   Po zakończeniu kliknij pozycję **Prześlij**.

## <a name="the-schema-of-the-events-in-the-storage-account"></a>Schemat zdarzeń na koncie Storage klienta

- Dla każdego typu zdarzenia zostanie utworzony kontener obiektów blob:

  :::image type="content" source="../defender-endpoint/images/storage-account-event-schema.png" alt-text="Przykład kontenera obiektów blob" lightbox="../defender-endpoint/images/storage-account-event-schema.png":::

- Schemat każdego wiersza w obiekcie blob to następujący kod JSON:

  ```JSON
  {
          "time": "<The time Microsoft 365 Defender received the event>"
          "tenantId": "<Your tenant ID>"
          "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
          "properties": { <Microsoft 365 Defender Advanced Hunting event as Json> }
  }
  ```

- Każdy obiekt blob zawiera wiele wierszy.

- Każdy wiersz zawiera nazwę zdarzenia, czas, gdy program Defender for Endpoint odebrał zdarzenie, dzierżawa, do której należy (zostaną odebrane tylko zdarzenia z dzierżawy) oraz zdarzenie w formacie JSON we właściwości o nazwie "properties".

- Aby uzyskać więcej informacji na temat schematu Microsoft 365 Defender, zobacz Omówienie wyszukiwania [zaawansowanego](../defender/advanced-hunting-overview.md).

## <a name="data-types-mapping"></a>Mapowanie typów danych

Aby uzyskać typy danych dla naszych właściwości zdarzeń, wykonaj następujące czynności:

1. Zaloguj się, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">aby Microsoft 365 Defender</a> i przejdź do wyszukiwania **zaawansowanego myśliwego**\>. Aby przejść bezpośrednio do strony **zaawansowanego wyszukiwania** , użyj <security.microsoft.com/advanced-hunting>.

2. Na karcie **Zapytanie** uruchom następujące zapytanie, aby uzyskać mapowanie typów danych dla każdego zdarzenia:

   ```text
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Oto przykład zdarzenia Informacje o urządzeniu:

  :::image type="content" source="../defender-endpoint/images/machine-info-datatype-example.png" alt-text="Przykładowe zapytanie z informacjami o urządzeniu" lightbox="../defender-endpoint/images/machine-info-datatype-example.png":::

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie wyszukiwania zaawansowanego](../defender/advanced-hunting-overview.md)
- [Microsoft 365 Defender interfejsu API przesyłania strumieniowego](streaming-api.md)
- [Przesyłanie strumieniowe Microsoft 365 Defender do konta magazynu platformy Azure](streaming-api-storage.md)
- [Dokumentacja Storage konta usługi Azure](/azure/storage/common/storage-account-overview)
