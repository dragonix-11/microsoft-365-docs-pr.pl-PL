---
title: Przesyłanie strumieniowe zdarzeń Microsoft 365 Defender do konta usługi Storage
description: Dowiedz się, jak skonfigurować Microsoft 365 Defender do przesyłania strumieniowego zdarzeń zaawansowanego wyszukiwania zagrożeń do konta magazynu.
keywords: eksport danych pierwotnych, interfejs API przesyłania strumieniowego, interfejs API, usługa Event Hubs, magazyn platformy Azure, konto magazynu, zaawansowane wyszukiwanie zagrożeń, nieprzetworzone udostępnianie danych
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
ms.openlocfilehash: 0f5195e5a74395073267fd4df87f077c6a1d5f20
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66530581"
---
# <a name="configure-microsoft-365-defender-to-stream-advanced-hunting-events-to-your-storage-account"></a>Konfigurowanie Microsoft 365 Defender do przesyłania strumieniowego zdarzeń zaawansowanego wyszukiwania zagrożeń do konta magazynu

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="before-you-begin"></a>Przed rozpoczęciem

1. Utwórz [konto magazynu](/azure/storage/common/storage-account-overview) w dzierżawie.

2. Zaloguj się do [dzierżawy platformy Azure](https://ms.portal.azure.com/), przejdź do pozycji **Subskrypcje > Twoja subskrypcja > Dostawcy zasobów > Rejestrowanie w usłudze Microsoft.Insights**.

### <a name="add-contributor-permissions"></a>Dodawanie uprawnień współautora

Po utworzeniu konta magazynu należy wykonać następujące czynności:

1. Zdefiniuj użytkownika, który będzie logować się do Microsoft 365 Defender jako współautor.

    Przejdź do **pozycji Konto magazynu > Kontrola dostępu (IAM) > Dodaj** i sprawdź w obszarze **Przypisania ról**.

## <a name="enable-raw-data-streaming"></a>Włączanie przesyłania strumieniowego danych pierwotnych

1. Zaloguj się do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> jako administrator **globalny** _ lub _*_Administrator zabezpieczeń_**.

2. Przejdź do pozycji **Ustawienia** \> **Microsoft 365 Defender** \> **interfejsu API przesyłania strumieniowego**. Aby przejść bezpośrednio do strony **interfejsu API przesyłania strumieniowego** , użyj polecenia <https://security.microsoft.com/settings/mtp_settings/raw_data_export>.

3. Kliknij pozycję **Dodaj**.

4. W wyświetlonym menu wysuwowym **Dodawanie nowych ustawień interfejsu API przesyłania strumieniowego** skonfiguruj następujące ustawienia:
   1. **Nazwa**: wybierz nazwę nowych ustawień.
   2. Wybierz pozycję **Prześlij zdarzenia do usługi Azure Storage**.
   3. W **wyświetlonym polu Identyfikator zasobu konta magazynu** wpisz identyfikator **zasobu konta magazynu**. Aby uzyskać **identyfikator zasobu konta magazynu**, otwórz Azure Portal pod adresem <https://portal.azure.com>, kliknij pozycję **Konta** \> magazynu, aby przejść do karty \> właściwości, aby skopiować tekst w obszarze **Identyfikator zasobu konta magazynu**.

      :::image type="content" source="../defender-endpoint/images/storage-account-resource-id.png" alt-text="Identyfikator zasobu konta magazynu" lightbox="../defender-endpoint/images/storage-account-resource-id.png":::

   4. Po powrocie do menu wysuwanego **Dodawanie nowych ustawień interfejsu API przesyłania strumieniowego** wybierz **typy zdarzeń** , które chcesz przesyłać strumieniowo.

   Po zakończeniu kliknij pozycję **Prześlij**.

## <a name="the-schema-of-the-events-in-the-storage-account"></a>Schemat zdarzeń na koncie magazynu

- Kontener obiektów blob zostanie utworzony dla każdego typu zdarzenia:

  :::image type="content" source="../defender-endpoint/images/storage-account-event-schema.png" alt-text="Przykład kontenera obiektów blob" lightbox="../defender-endpoint/images/storage-account-event-schema.png":::

- Schemat każdego wiersza w obiektach blob to następujący kod JSON:

  ```JSON
  {
          "time": "<The time Microsoft 365 Defender received the event>"
          "tenantId": "<Your tenant ID>"
          "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
          "properties": { <Microsoft 365 Defender Advanced Hunting event as Json> }
  }
  ```

- Każdy obiekt blob zawiera wiele wierszy.

- Każdy wiersz zawiera nazwę zdarzenia, czas odebrania zdarzenia przez usługę Defender for Endpoint, dzierżawę, do której należy (będzie można pobierać zdarzenia tylko z dzierżawy), a zdarzenie w formacie JSON we właściwości o nazwie "properties".

- Aby uzyskać więcej informacji na temat schematu zdarzeń Microsoft 365 Defender, zobacz [Omówienie zaawansowanego wyszukiwania zagrożeń](../defender/advanced-hunting-overview.md).

## <a name="data-types-mapping"></a>Mapowanie typów danych

Aby uzyskać typy danych dla naszych właściwości zdarzeń, wykonaj następujące czynności:

1. Zaloguj się do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> i przejdź do **obszaru Wyszukiwanie zagrożeń** \> **zaawansowanych**. Aby przejść bezpośrednio do strony **Zaawansowane wyszukiwanie zagrożeń** , użyj <security.microsoft.com/advanced-hunting>.

2. Na karcie **Zapytanie** uruchom następujące zapytanie, aby uzyskać mapowanie typów danych dla każdego zdarzenia:

   ```text
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Oto przykład zdarzenia Informacje o urządzeniu:

  :::image type="content" source="../defender-endpoint/images/machine-info-datatype-example.png" alt-text="Przykładowe zapytanie dotyczące informacji o urządzeniu" lightbox="../defender-endpoint/images/machine-info-datatype-example.png":::

## <a name="monitoring-created-resources"></a>Monitorowanie utworzonych zasobów

Zasoby utworzone przez interfejs API przesyłania strumieniowego można monitorować przy użyciu **usługi Azure Monitor**. Aby uzyskać więcej informacji, zobacz [Monitorowanie miejsc docelowych — Azure Monitor | Microsoft Docs](/azure/azure-monitor/logs/logs-data-export?tabs=portal#monitor-destinations).

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie zaawansowanego wyszukiwania zagrożeń](../defender/advanced-hunting-overview.md)
- [interfejs API przesyłania strumieniowego Microsoft 365 Defender](streaming-api.md)
- [Przesyłanie strumieniowe zdarzeń Microsoft 365 Defender do konta usługi Azure Storage](streaming-api-storage.md)
- [Dokumentacja konta usługi Azure Storage](/azure/storage/common/storage-account-overview)
