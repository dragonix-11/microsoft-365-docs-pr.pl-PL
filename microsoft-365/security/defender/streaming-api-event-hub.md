---
title: Przesyłanie strumieniowe zdarzeń Microsoft 365 Defender do Azure Event Hubs
description: Dowiedz się, jak skonfigurować Microsoft 365 Defender do przesyłania strumieniowego zdarzeń zaawansowanego wyszukiwania zagrożeń do usługi Event Hubs.
keywords: eksport danych pierwotnych, interfejs API przesyłania strumieniowego, interfejs API, Azure Event Hubs, magazyn platformy Azure, konto magazynu, zaawansowane wyszukiwanie zagrożeń, udostępnianie danych pierwotnych
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
ms.openlocfilehash: 9cae28cc69d67bb18058e2c81cd8235ffce79997
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754405"
---
# <a name="configure-microsoft-365-defender-to-stream-advanced-hunting-events-to-your-azure-event-hub"></a>Konfigurowanie Microsoft 365 Defender do przesyłania strumieniowego zdarzeń zaawansowanego wyszukiwania zagrożeń do usługi Azure Event Hub

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="prerequisites"></a>Wymagania wstępne

Przed skonfigurowaniem Microsoft 365 Defender do przesyłania strumieniowego danych do usługi Event Hubs upewnij się, że zostały spełnione następujące wymagania wstępne:

1. Tworzenie usługi Event Hubs (aby uzyskać informacje, zobacz [Konfigurowanie usługi Event Hubs](configure-event-hub.md#set-up-event-hubs)).

2. Tworzenie przestrzeni nazw usługi Event Hubs (aby uzyskać informacje, zobacz [Konfigurowanie przestrzeni nazw usługi Event Hubs](configure-event-hub.md#set-up-event-hubs-namespace)).

3. Dodaj uprawnienia do jednostki, która ma uprawnienia **współautora** , aby ta jednostka mogła eksportować dane do usługi Event Hubs. Aby uzyskać więcej informacji na temat dodawania uprawnień, zobacz [Dodawanie uprawnień](configure-event-hub.md#add-permissions)

> [!NOTE]
> Interfejs API przesyłania strumieniowego można zintegrować za pośrednictwem usługi Event Hubs lub konta usługi Azure Storage.

## <a name="enable-raw-data-streaming"></a>Włączanie przesyłania strumieniowego danych pierwotnych

1. Zaloguj się do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a> jako administrator **globalny** _ lub _*_Administrator zabezpieczeń_**.

2. Przejdź do [strony ustawienia interfejsu API przesyłania strumieniowego](https://security.microsoft.com/settings/mtp_settings/raw_data_export).

3. Kliknij pozycję **Dodaj**.

4. Wybierz nazwę nowych ustawień.

5. Wybierz pozycję **Prześlij zdarzenia do usługi Azure Event Hub**.

6. Możesz wybrać, czy chcesz wyeksportować dane zdarzeń do pojedynczego centrum zdarzeń, czy wyeksportować każdą tabelę zdarzeń do innej usługi Event Hubs w przestrzeni nazw usługi Event Hubs.

7. Aby wyeksportować dane zdarzeń do pojedynczego centrum zdarzeń, wprowadź **nazwę centrum zdarzeń** i **identyfikator zasobu centrum zdarzeń**.

   Aby uzyskać **identyfikator zasobu centrum zdarzeń**, przejdź do strony przestrzeni nazw Azure Event Hubs na karcie **Właściwości** [platformy Azure](https://ms.portal.azure.com/) > , > skopiować tekst w obszarze **Identyfikator zasobu**:

   :::image type="content" source="../defender-endpoint/images/event-hub-resource-id.png" alt-text="Identyfikator zasobu centrum zdarzeń" lightbox="../defender-endpoint/images/event-hub-resource-id.png":::

8. Przejdź do obszaru [Obsługiwane typy zdarzeń Microsoft 365 Defender w interfejsie API przesyłania strumieniowego zdarzeń](supported-event-types.md), aby przejrzeć stan obsługi typów zdarzeń w interfejsie API przesyłania strumieniowego Microsoft 365.

9. Wybierz zdarzenia, które chcesz przesyłać strumieniowo, a następnie kliknij przycisk **Zapisz**.

## <a name="the-schema-of-the-events-in-azure-event-hub"></a>Schemat zdarzeń w usłudze Azure Event Hub

```JSON
{
   "records": [
               {
                  "time": "<The time Microsoft 365 Defender received the event>"
                  "tenantId": "<The Id of the tenant that the event belongs to>"
                  "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
                  "properties": { <Microsoft 365 Defender Advanced Hunting event as Json> }
               }
               ...
            ]
}
```

- Każdy komunikat usługi Event Hubs w Azure Event Hubs zawiera listę rekordów.

- Każdy rekord zawiera nazwę zdarzenia, czas Microsoft 365 Defender odebrania zdarzenia, dzierżawę, do której należy (otrzymasz tylko zdarzenia z dzierżawy), a zdarzenie w formacie JSON we właściwości o nazwie "**właściwości**".

- Aby uzyskać więcej informacji na temat schematu zdarzeń Microsoft 365 Defender, zobacz [Omówienie zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md).

- W obszarze Zaawansowane wyszukiwanie zagrożeń tabela **DeviceInfo** zawiera kolumnę o nazwie **MachineGroup** zawierającą grupę urządzenia. W tym miejscu każde wydarzenie zostanie również ozdobione tą kolumną.

## <a name="data-types-mapping"></a>Mapowanie typów danych

Aby uzyskać typy danych dla właściwości zdarzeń, wykonaj następujące kroki:

1. Zaloguj się do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> i przejdź do [strony Zaawansowane wyszukiwanie zagrożeń](https://security.microsoft.com/hunting-package).

2. Uruchom następujące zapytanie, aby uzyskać mapowanie typów danych dla każdego zdarzenia:

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Oto przykład zdarzenia Informacje o urządzeniu:

  :::image type="content" source="../defender-endpoint/images/machine-info-datatype-example.png" alt-text="Przykładowe zapytanie dotyczące informacji o urządzeniu" lightbox="../defender-endpoint/images/machine-info-datatype-example.png":::

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
- [interfejs API przesyłania strumieniowego Microsoft 365 Defender](streaming-api.md)
- [Obsługiwane typy zdarzeń Microsoft 365 Defender w interfejsie API przesyłania strumieniowego zdarzeń](supported-event-types.md)
- [Przesyłanie strumieniowe zdarzeń Microsoft 365 Defender do konta usługi Azure Storage](streaming-api-storage.md)
- [dokumentacja Azure Event Hubs](/azure/event-hubs/)
- [Rozwiązywanie problemów z łącznością — Azure Event Hubs](/azure/event-hubs/troubleshooting-guide)
