---
title: Przesyłanie strumieniowe zdarzeń Ochrona punktu końcowego w usłudze Microsoft Defender do konta Storage
description: Dowiedz się, jak skonfigurować Ochrona punktu końcowego w usłudze Microsoft Defender do przesyłania strumieniowego zdarzeń zaawansowanego wyszukiwania zagrożeń do konta Storage.
keywords: eksport danych pierwotnych, interfejs API przesyłania strumieniowego, interfejs API, usługa Event Hubs, magazyn platformy Azure, konto magazynu, zaawansowane wyszukiwanie zagrożeń, nieprzetworzone udostępnianie danych
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
ms.openlocfilehash: d5d4917e2464964da819af0a06f0b8e4883dfea9
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783892"
---
# <a name="configure-microsoft-defender-for-endpoint-to-stream-advanced-hunting-events-to-your-storage-account"></a>Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender do przesyłania strumieniowego zdarzeń zaawansowanego wyszukiwania zagrożeń do konta Storage

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

> Chcesz poznać usługę Defender for Endpoint? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="before-you-begin"></a>Przed rozpoczęciem

1. Utwórz [konto Storage](/azure/storage/common/storage-account-overview) w dzierżawie.

2. Zaloguj się do [dzierżawy platformy Azure](https://ms.portal.azure.com/), przejdź do **obszaru Subskrypcje > Twoja subskrypcja > Dostawcy zasobów > Rejestrowanie w witrynie Microsoft.insights**.

## <a name="enable-raw-data-streaming"></a>Włączanie przesyłania strumieniowego danych pierwotnych

1. Zaloguj się do [Microsoft 365 Defender](https://security.microsoft.com) jako administrator **globalny** _ lub _*_Administrator zabezpieczeń_**.

2. Przejdź do [strony Ustawienia eksportu danych](https://security.microsoft.com/interoperability/dataexport) w Microsoft 365 Defender.

3. Kliknij pozycję **Dodaj ustawienia eksportu danych**.

4. Wybierz nazwę nowych ustawień.

5. Wybierz pozycję **Prześlij zdarzenia do usługi Azure Storage**.

6. Wpisz identyfikator **zasobu konta Storage**. Aby uzyskać **identyfikator zasobu konta Storage**, przejdź do strony konta Storage na karcie \> właściwości [Azure Portal](https://ms.portal.azure.com/) \> skopiuj tekst w obszarze **identyfikator zasobu konta Storage**:

   :::image type="content" source="images/storage-account-resource-id.png" alt-text="Usługa Event Hubs z identyfikatorem zasobu1" lightbox="images/storage-account-resource-id.png":::

7. Wybierz zdarzenia, które chcesz przesyłać strumieniowo, a następnie kliknij przycisk **Zapisz**.

## <a name="the-schema-of-the-events-in-the-storage-account"></a>Schemat zdarzeń na koncie Storage

- Kontener obiektów blob zostanie utworzony dla każdego typu zdarzenia:

  :::image type="content" source="images/storage-account-event-schema.png" alt-text="Usługa Event Hubs z identyfikatorem zasobu2" lightbox="images/storage-account-event-schema.png":::

- Schemat każdego wiersza w obiektach blob to następujący kod JSON:

  ```json
  {
    "time": "<The time WDATP received the event>"
    "tenantId": "<Your tenant ID>"
    "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
    "properties": { <WDATP Advanced Hunting event as Json> }
  }
  ```

- Każdy obiekt blob zawiera wiele wierszy.

- Każdy wiersz zawiera nazwę zdarzenia, czas odebrania zdarzenia przez usługę Defender for Endpoint, dzierżawę, do której należy (będzie można pobierać zdarzenia tylko z dzierżawy), a zdarzenie w formacie JSON we właściwości o nazwie "properties".

- Aby uzyskać więcej informacji na temat schematu zdarzeń Ochrona punktu końcowego w usłudze Microsoft Defender, zobacz [Omówienie zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md).

- W obszarze Zaawansowane wyszukiwanie zagrożeń tabela **DeviceInfo** zawiera kolumnę o nazwie **MachineGroup** zawierającą grupę urządzenia. W tym miejscu każde wydarzenie zostanie również ozdobione tą kolumną. Aby uzyskać więcej informacji, zobacz [Grupy urządzeń](machine-groups.md) .

## <a name="data-types-mapping"></a>Mapowanie typów danych

Aby uzyskać typy danych dla naszych właściwości zdarzeń, wykonaj następujące czynności:

1. Zaloguj się do [Microsoft 365 Defender](https://security.microsoft.com) i przejdź do [strony Zaawansowane wyszukiwanie zagrożeń](https://security.microsoft.com/hunting-package).

2. Uruchom następujące zapytanie, aby uzyskać mapowanie typów danych dla każdego zdarzenia:

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Oto przykład zdarzenia Informacje o urządzeniu:

  :::image type="content" source="images/data-types-mapping-query.png" alt-text="Usługa Event Hubs z identyfikatorem zasobu3" lightbox="images/data-types-mapping-query.png":::

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
- [interfejs API przesyłania strumieniowego Ochrona punktu końcowego w usłudze Microsoft Defender](raw-data-export.md)
- [Przesyłanie strumieniowe zdarzeń Ochrona punktu końcowego w usłudze Microsoft Defender do konta usługi Azure Storage](raw-data-export-storage.md)
- [Dokumentacja konta usługi Azure Storage](/azure/storage/common/storage-account-overview)
