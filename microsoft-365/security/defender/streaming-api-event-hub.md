---
title: Przesyłanie strumieniowe Microsoft 365 Defender do centrum zdarzeń Azure
description: Dowiedz się, jak skonfigurować usługę Microsoft 365 Defender przesyłania strumieniowego wydarzeń zaawansowanego chłonia do Centrum wydarzeń.
keywords: nieprzetworzone eksportowanie danych, interfejs API przesyłania strumieniowego, interfejs API, Centrum wydarzeń Azure, magazyn platformy Azure, konto magazynu, zaawansowane szukanie, pierwotne udostępnianie danych
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
ms.openlocfilehash: 064ce5f796d59994b9d7ec4c3403711b1d683e56
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500480"
---
# <a name="configure-microsoft-365-defender-to-stream-advanced-hunting-events-to-your-azure-event-hub"></a>Skonfiguruj Microsoft 365 Defender, aby przesyłać strumieniowo wydarzenia z łowiectwo do Centrum wydarzeń Azure

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="before-you-begin"></a>Przed rozpoczęciem

1. Utwórz centrum [zdarzeń w](/azure/event-hubs/) dzierżawie.

2. Zaloguj się do dzierżawy platformy [Azure](https://ms.portal.azure.com/), przejdź do strony Subskrypcje **> usługi > Resource Providers** (Dostawcy zasobów> Zarejestruj się w witrynie Microsoft.Szczegółowe informacje.

3. Utwórz przestrzeń nazw centrum zdarzeń, przejdź do obszaru Centrum zdarzeń **> Dodaj** i wybierz warstwę cenową, jednostki przepływności i automatyczne inflate odpowiednie dla oczekiwanego obciążenia. Aby uzyskać więcej informacji, zobacz [Ceny w Centrum wydarzeń](https://azure.microsoft.com/pricing/details/event-hubs/).

### <a name="add-contributor-permissions"></a>Dodawanie uprawnień współautora

Po utworzeniu przestrzeni nazw Centrum zdarzeń należy:

1. Zdefiniuj użytkownika, który będzie logować się do Microsoft 365 Defender współautora.

2. Jeśli łączysz się z aplikacją, dodaj podmiot zabezpieczeń usługi rejestracji aplikacji jako czytelnik, odbiorcy danych centrum zdarzeń platformy Azure (można to również zrobić na poziomie Grupa zasobów lub Subskrypcja).

    Przejdź do **obszaru przestrzeni nazw Centrum > (IAM, Access Control) i > Dodaj** i zweryfikuj w **obszarze Przypisania ról**.

## <a name="enable-raw-data-streaming"></a>Włączanie przesyłania strumieniowego nieprzetworzonych danych

1. Zaloguj się <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">do Microsoft 365 Defender jako</a> ***Administrator globalny** _ lub _*_Administrator zabezpieczeń_**.

2. Przejdź do strony [ustawień interfejsu API przesyłania strumieniowego](https://security.microsoft.com/settings/mtp_settings/raw_data_export).

3. Kliknij pozycję **Dodaj**.

4. Wybierz nazwę nowych ustawień.

5. Wybierz pozycję **Przekaż wydarzenia do Centrum zdarzeń Azure**.

6. Możesz wybrać, czy chcesz wyeksportować dane zdarzenia do pojedynczego Centrum zdarzeń, czy wyeksportować każdą tabelę zdarzeń do innego centrum zdarzeń w przestrzeni nazw Centrum zdarzeń.

7. Aby wyeksportować dane zdarzenia do pojedynczego Centrum zdarzeń, wprowadź nazwę centrum  zdarzeń oraz identyfikator **zasobu Centrum zdarzeń**.

   Aby uzyskać identyfikator **zasobu Centrum** zdarzeń, przejdź do strony przestrzeni nazw centrum zdarzeń Azure na karcie **AzureProperties** [](https://ms.portal.azure.com/) >  > skopiuj tekst w obszarze **Identyfikator zasobu**:

   :::image type="content" source="../defender-endpoint/images/event-hub-resource-id.png" alt-text="Identyfikator zasobu Centrum zdarzeń" lightbox="../defender-endpoint/images/event-hub-resource-id.png":::

8. Przejdź do [obsługiwanego typu Microsoft 365 Defender w interfejsie API przesyłania strumieniowego](supported-event-types.md) zdarzeń, aby sprawdzić stan obsługi typów zdarzeń w interfejsie API przesyłania strumieniowego Microsoft 365 strumieniowego.

9. Wybierz zdarzenia, które chcesz przesyłać strumieniowo, i kliknij pozycję **Zapisz**.

## <a name="the-schema-of-the-events-in-azure-event-hub"></a>Schemat zdarzeń w Centrum zdarzeń Azure

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

- Każda wiadomość Centrum zdarzeń w Centrum zdarzeń Azure zawiera listę rekordów.

- Każdy rekord zawiera nazwę zdarzenia, Microsoft 365 Defender otrzymano zdarzenie, dzierżawę, do której należy (zostaną odebrane tylko zdarzenia z dzierżawy) oraz zdarzenie w formacie JSON we właściwości o nazwie "**properties**".

- Aby uzyskać więcej informacji na temat schematu Microsoft 365 Defender, zobacz Omówienie wyszukiwania [zaawansowanego](advanced-hunting-overview.md).

- W przypadku wyszukiwania zaawansowanego tabela **DeviceInfo** zawiera kolumnę o nazwie **MachineGroup** , która zawiera grupę urządzenia. Tutaj każde zdarzenie również będzie udekorowane tą kolumną.

## <a name="data-types-mapping"></a>Mapowanie typów danych

Aby uzyskać typy danych dla właściwości zdarzenia, wykonaj następujące czynności:

1. Zaloguj się, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">aby Microsoft 365 Defender</a> i przejdź do [strony Zaawansowane szukanie](https://security.microsoft.com/hunting-package).

2. Uruchom następujące zapytanie, aby uzyskać mapowanie typów danych dla każdego zdarzenia:

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Oto przykład zdarzenia Informacje o urządzeniu:

  :::image type="content" source="../defender-endpoint/images/machine-info-datatype-example.png" alt-text="Przykładowe zapytanie dotyczące informacji o urządzeniu" lightbox="../defender-endpoint/images/machine-info-datatype-example.png":::

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie wyszukiwania zaawansowanego](advanced-hunting-overview.md)
- [Microsoft 365 Defender interfejsu API przesyłania strumieniowego](streaming-api.md)
- [Obsługiwane Microsoft 365 Defender zdarzeń w interfejsie API przesyłania strumieniowego zdarzeń](supported-event-types.md)
- [Przesyłanie strumieniowe Microsoft 365 Defender do konta magazynu platformy Azure](streaming-api-storage.md)
- [Dokumentacja centrum wydarzeń platformy Azure](/azure/event-hubs/)
- [Rozwiązywanie problemów z łącznością — Azure Event Hub](/azure/event-hubs/troubleshooting-guide)
