---
title: Przesyłanie strumieniowe usługi Microsoft Defender dla zdarzeń punktu końcowego do centrum zdarzeń platformy Azure
description: Dowiedz się, jak skonfigurować usługę Microsoft Defender for Endpoint w celu przesyłania strumieniowego wydarzeń zaawansowanego chłonia do Centrum wydarzeń.
keywords: nieprzetworzone eksportowanie danych, interfejs API przesyłania strumieniowego, interfejs API, centrum wydarzeń platformy Azure, magazyn platformy Azure, konto magazynu, zaawansowane szukanie, pierwotne udostępnianie danych
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
ms.openlocfilehash: b1d313ed2980f84318a590df55e0a8d8e7b152ab
ms.sourcegitcommit: cde34d38bdfb6335b980f1c48c6b218da6a64bf8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/20/2022
ms.locfileid: "63013347"
---
# <a name="configure-microsoft-defender-for-endpoint-to-stream-advanced-hunting-events-to-your-azure-event-hubs"></a>Konfigurowanie programu Microsoft Defender dla punktu końcowego w celu przesyłania strumieniowego wydarzeń zaawansowanego chłonia do Centrum wydarzeń platformy Azure

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="before-you-begin"></a>Przed rozpoczęciem

1. Utwórz centrum [zdarzeń w](/azure/event-hubs/) dzierżawie.

2. Zaloguj się do dzierżawy platformy [Azure](https://ms.portal.azure.com/), przejdź do strony Subskrypcje > usługi > Resource Providers (Dostawcy zasobów> zarejestruj się w witrynie **Microsoft.insights**.

## <a name="enable-raw-data-streaming"></a>Włączanie przesyłania strumieniowego nieprzetworzonych danych

1. Zaloguj się do centrum [Microsoft 365 Defender](https://security.microsoft.com) ***Administrator globalny** _ lub _*_Administrator zabezpieczeń_**.

2. Przejdź do strony [ustawień eksportu danych w](https://security.microsoft.com/interoperability/dataexport) portalu usługi Microsoft Defender.

3. Kliknij pozycję **Dodaj ustawienia eksportu danych**.

4. Wybierz nazwę nowych ustawień.

5. Wybierz **pozycję Przekaż wydarzenia do Centrum zdarzeń Azure**.

6. Wpisz nazwę **Centrum zdarzeń i** identyfikator **zasobu Centrum zdarzeń**.

   Aby uzyskać identyfikator zasobu **Centrum** zdarzeń, przejdź do strony przestrzeni nazw Centrum zdarzeń Azure na karcie właściwości usługi [Azure](https://ms.portal.azure.com/) > \> i skopiuj tekst w obszarze **Identyfikator zasobu**:

   :::image type="content" alt-text="Obraz zasobu Centrum zdarzeń Identyfikator1." source="images/event-hub-resource-id.png" lightbox="images/event-hub-resource-id.png":::

7. Wybierz zdarzenia, które chcesz przesyłać strumieniowo, i kliknij pozycję **Zapisz**.

## <a name="the-schema-of-the-events-in-azure-event-hubs"></a>Schemat zdarzeń w Centrum zdarzeń Azure

```json
{
    "records": [
                    {
                        "time": "<The time WDATP received the event>"
                        "tenantId": "<The Id of the tenant that the event belongs to>"
                        "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
                        "properties": { <WDATP Advanced Hunting event as Json> }
                    }
                    ...
                ]
}
```

- Każda wiadomość centrum zdarzeń w Centrum zdarzeń Azure zawiera listę rekordów.

- Każdy rekord zawiera nazwę zdarzenia, czas, gdy usługa Microsoft Defender for Endpoint odebrała zdarzenie, dzierżawa, do której należy (zostaną odebrane tylko zdarzenia z dzierżawy) oraz zdarzenie w formacie JSON we właściwości o nazwie "**properties**".

- Aby uzyskać więcej informacji na temat schematu programu Microsoft Defender dla zdarzeń punktu końcowego, zobacz Omówienie [zaawansowanego](advanced-hunting-overview.md) wyszukiwania.

- W przypadku wyszukiwania zaawansowanego tabela **DeviceInfo** zawiera kolumnę o nazwie **MachineGroup** , która zawiera grupę urządzenia. Tutaj każde zdarzenie również będzie udekorowane tą kolumną. Aby [uzyskać więcej informacji,](machine-groups.md) zobacz Grupy urządzeń.

## <a name="data-types-mapping"></a>Mapowanie typów danych

Aby uzyskać typy danych dla właściwości zdarzenia, wykonaj następujące czynności:

1. Zaloguj się, [aby Microsoft 365 Defender](https://security.microsoft.com) i przejdź do [strony Zaawansowane szukanie](https://security.microsoft.com/hunting-package).

2. Uruchom następujące zapytanie, aby uzyskać mapowanie typów danych dla każdego zdarzenia:

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType 
   ```

- Oto przykład zdarzenia Informacje o urządzeniu:

  ![Obraz zasobu centrum zdarzeń Identyfikator2.](images/machine-info-datatype-example.png)

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie wyszukiwania zaawansowanego](advanced-hunting-overview.md)
- [Microsoft Defender for Endpoint streaming API](raw-data-export.md)
- [Przesyłanie strumieniowe programu Microsoft Defender dla zdarzeń punktu końcowego do konta magazynu platformy Azure](raw-data-export-storage.md)
- [Dokumentacja centrum wydarzeń azure](/azure/event-hubs/)
- [Rozwiązywanie problemów z łącznością — Azure Event Hubs](/azure/event-hubs/troubleshooting-guide)
