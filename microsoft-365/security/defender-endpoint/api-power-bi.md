---
title: Ochrona punktu końcowego w usłudze Microsoft Defender interfejsów API do Power BI
ms.reviewer: ''
description: Tworzenie raportu analizy biznesowej (Power Business Intelligence) na Ochrona punktu końcowego w usłudze Microsoft Defender API.
keywords: api, obsługiwane api, Power BI, raporty
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 4cad6fd5188745773ce561d1db697989598a1dc5
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472160"
---
# <a name="create-custom-reports-using-power-bi"></a>Tworzenie raportów niestandardowych przy użyciu Power BI

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


- Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

W tej sekcji dowiesz się, jak utworzyć raport Power BI usługi Defender dla interfejsów API punktów końcowych.

W pierwszym przykładzie pokazano, jak połączyć program Power BI z interfejsem API zaawansowanego wyszukiwania, a drugi przykład przedstawia połączenie z naszymi interfejsami API OData, takimi jak akcje komputera lub alerty.

## <a name="connect-power-bi-to-advanced-hunting-api"></a>Połączenie Power BI interfejsu API zaawansowanego wyszukiwania

- Otwórz program Microsoft Power BI.

- Kliknij **pozycję Pobierz puste** \> **zapytanie danych**.

  :::image type="content" source="images/power-bi-create-blank-query.png" alt-text="Opcja Puste zapytanie w obszarze pozycji menu Pobierz dane" lightbox="images/power-bi-create-blank-query.png":::

- Kliknij **Edytor zaawansowany**.

  :::image type="content" source="images/power-bi-open-advanced-editor.png" alt-text="Element Edytor zaawansowany menu" lightbox="images/power-bi-open-advanced-editor.png":::

- Skopiuj poniższe polecenie i wklej je w edytorze:

```
    let
        AdvancedHuntingQuery = "DeviceEvents | where ActionType contains 'Anti' | limit 20",

        HuntingUrl = "https://api.securitycenter.microsoft.com/api/advancedqueries",

        Response = Json.Document(Web.Contents(HuntingUrl, [Query=[key=AdvancedHuntingQuery]])),

        TypeMap = #table(
            { "Type", "PowerBiType" },
            {
                { "Double",   Double.Type },
                { "Int64",    Int64.Type },
                { "Int32",    Int32.Type },
                { "Int16",    Int16.Type },
                { "UInt64",   Number.Type },
                { "UInt32",   Number.Type },
                { "UInt16",   Number.Type },
                { "Byte",     Byte.Type },
                { "Single",   Single.Type },
                { "Decimal",  Decimal.Type },
                { "TimeSpan", Duration.Type },
                { "DateTime", DateTimeZone.Type },
                { "String",   Text.Type },
                { "Boolean",  Logical.Type },
                { "SByte",    Logical.Type },
                { "Guid",     Text.Type }
            }),

        Schema = Table.FromRecords(Response[Schema]),
        TypedSchema = Table.Join(Table.SelectColumns(Schema, {"Name", "Type"}), {"Type"}, TypeMap , {"Type"}),
        Results = Response[Results],
        Rows = Table.FromRecords(Results, Schema[Name]),
        Table = Table.TransformColumnTypes(Rows, Table.ToList(TypedSchema, (c) => {c{0}, c{2}}))

    in Table
```

- Kliknij **przycisk Gotowe**.

- Kliknij **pozycję Edytuj poświadczenia**.

    :::image type="content" source="images/power-bi-edit-credentials.png" alt-text="Element menu Edytuj poświadczenia" lightbox="images/power-bi-edit-credentials.png":::
    

- Wybierz **pozycję Konto organizacji** \> **Zaloguj się**.

    :::image type="content" source="images/power-bi-set-credentials-organizational.png" alt-text="The Sign in option in the Organizational account menu item" lightbox="images/power-bi-set-credentials-organizational.png":::

- Wprowadź poświadczenia i poczekaj na zalogowanie się.

- Kliknij **przycisk Połączenie**.

    :::image type="content" source="images/power-bi-set-credentials-organizational-cont.png" alt-text="The sign-in confirmation message in the Organizational account menu item" lightbox="images/power-bi-set-credentials-organizational-cont.png":::

- Teraz wyniki zapytania zostaną wyświetlone w postaci tabeli i będzie można zacząć tworzyć na jej podstawie wizualizacje.

- Możesz zduplikować tę tabelę, zmienić jej nazwę i edytować wewnątrz zapytanie zaawansowanego wyszukiwania, aby uzyskać dowolne dane.

## <a name="connect-power-bi-to-odata-apis"></a>Połączenie Power BI interfejsów API OData

- Jedyna różnica w  względem powyższego przykładu to zapytanie wewnątrz edytora.

- Skopiuj poniższe polecenie i wklej je w edytorze, aby przeciągnąć **wszystkie akcje komputera** z Twojej organizacji:

```
    let

        Query = "MachineActions",

        Source = OData.Feed("https://api.securitycenter.microsoft.com/api/" & Query, null, [Implementation="2.0", MoreColumns=true])
    in
        Source
```

- W przypadku alertów **i komputerów** możesz to **zrobić tak samo**.
- Możesz również używać zapytań OData do filtrowania zapytań — zobacz [Korzystanie z zapytań OData](exposed-apis-odata-samples.md).

## <a name="power-bi-dashboard-samples-in-github"></a>Power BI pulpitu nawigacyjnego w programie GitHub

Aby uzyskać więcej informacji, [zobacz Power BI szablonów raportów](https://github.com/microsoft/MicrosoftDefenderATP-PowerBI).

## <a name="sample-reports"></a>Przykładowe raporty

Wyświetl Ochrona punktu końcowego w usłudze Microsoft Defender Power BI przykładowe raporty. Aby uzyskać więcej informacji, zobacz [Przeglądanie przykładowych kodów](/samples/browse/?products=mdatp).

## <a name="related-topics"></a>Tematy pokrewne

- [Interfejsy API usługi Defender dla punktów końcowych](apis-intro.md)
- [Interfejs API zaawansowanego wyszukiwania zagrożeń](run-advanced-query-api.md)
- [Używanie zapytań OData](exposed-apis-odata-samples.md)
