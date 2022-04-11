---
title: Używanie zapytań udostępnionych w Microsoft 365 Defender zaawansowanego wyszukiwania zagrożeń
description: Natychmiast rozpocznij wyszukiwanie zagrożeń za pomocą wstępnie zdefiniowanych i udostępnionych zapytań. Udostępniaj zapytania publicznie lub organizacji.
keywords: zaawansowane wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, wykrywanie zagrożeń cybernetycznych, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, wykrywanie niestandardowe, schemat, kusto, repozytorium github, moje zapytania, zapytania udostępnione
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 2e86d733304eeaa0e5e16f3ce1bfde87c21258d4
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2022
ms.locfileid: "64761619"
---
# <a name="use-shared-queries-in-advanced-hunting"></a>Używanie zapytań udostępnionych w zaawansowanym wyszukiwaniu zagrożeń

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

[Zaawansowane zapytania dotyczące wyszukiwania zagrożeń](advanced-hunting-overview.md) mogą być udostępniane użytkownikom w tej samej organizacji. Możesz również zapisywać zapytania, które są dostępne tylko dla Ciebie. Możesz również znaleźć zapytania społeczności, które są udostępniane publicznie na GitHub. Te zapisane zapytania umożliwiają szybkie realizowanie konkretnych scenariuszy wyszukiwania zagrożeń bez konieczności pisania zapytań od podstaw.

Na karcie Zapytania w zaawansowanym wyszukiwaniu można znaleźć menu **rozwijane dla zapytań udostępnionych**, **Moje zapytania** i **Community zapytań**. Możesz wybrać strzałkę skierowaną w dół, aby rozwinąć menu.


:::image type="content" source="../../media/advanced-hunting-shared-queries-1.png" alt-text="Zapytania udostępnione, Moje zapytania i zapytania Community w portalu Microsoft 365 Defender" lightbox="../../media/advanced-hunting-shared-queries-1.png":::



## <a name="save-modify-and-share-a-query"></a>Zapisywanie, modyfikowanie i udostępnianie zapytania
Możesz zapisać nowe lub istniejące zapytanie, aby było dostępne tylko dla Ciebie lub udostępnione innym użytkownikom w organizacji. 

1. Utwórz lub zmodyfikuj zapytanie. 

2. Kliknij przycisk listy rozwijanej **Zapisz zapytanie** i wybierz pozycję **Zapisz jako**.
    
3. Wprowadź nazwę zapytania. 

   :::image type="content" source="../../media/shared-query-2.png" alt-text="Nowe zapytanie, które ma zostać zapisane w portalu Microsoft 365 Defender" lightbox="../../media/shared-query-2.png":::

4. Wybierz folder, w którym chcesz zapisać zapytanie.
    - **Zapytania udostępnione** — udostępnione wszystkim użytkownikom w organizacji
    - **Moje zapytania** — dostępne tylko dla Ciebie
    
5. Wybierz **Zapisz**. 

## <a name="delete-or-rename-a-query"></a>Usuwanie lub zmienianie nazwy zapytania
1. Wybierz trzy kropki po prawej stronie zapytania, które chcesz zmienić lub usunąć.

    :::image type="content" source="../../media/advanced-hunting-del-save-query.png" alt-text="Zmienianie nazwy lub usuwanie zapytania na stronie Zaawansowane wyszukiwanie zagrożeń w portalu Microsoft 365 Defender" lightbox="../../media/advanced-hunting-del-save-query.png":::

2. Wybierz pozycję **Usuń** i potwierdź usunięcie. Możesz też wybrać pozycję **Zmień nazwę** i podaj nową nazwę zapytania.

## <a name="create-a-direct-link-to-a-query"></a>Tworzenie bezpośredniego linku do zapytania
Aby wygenerować link, który otwiera zapytanie bezpośrednio w edytorze zaawansowanych zapytań wyszukiwania zagrożeń, sfinalizuj zapytanie i wybierz pozycję **Udostępnij link**.

## <a name="access-community-queries-in-the-github-repo"></a>Uzyskiwanie dostępu do zapytań społeczności w repozytorium GitHub  
Badacze zabezpieczeń firmy Microsoft regularnie udostępniają zaawansowane zapytania dotyczące wyszukiwania zagrożeń w [wyznaczonym repozytorium publicznym na GitHub](https://github.com/Azure/Azure-Sentinel/tree/master/Hunting%20Queries/Microsoft%20365%20Defender). Udziały w tym repozytorium są przeglądane przed opublikowaniem. Aby współtworzyć, [dołącz do GitHub bezpłatnie](https://github.com/).

Te zapytania można łatwo znaleźć również w menu rozwijanym **Community zapytań**.

:::image type="content" source="../../media/advanced-hunting-shared-queries-2.png" alt-text="Community zapytań uporządkowanych według folderów w portalu Microsoft 365 Defender" lightbox="../../media/advanced-hunting-shared-queries-2.png":::

Community zapytania są pogrupowane w foldery, takie jak *Kampanie*, *Zbieranie*, *Unikanie obrony* i tym podobne. Dalsze informacje na temat zapytania są udostępniane jako komentarze w wierszu w samym zapytaniu. 

>[!tip]
>Badacze zabezpieczeń firmy Microsoft udostępniają również zaawansowane zapytania dotyczące zagrożeń, których można użyć do lokalizowania działań i wskaźników związanych z pojawiającym się zagrożeniami. Te zapytania są udostępniane w ramach raportów [analizy zagrożeń](/windows/security/threat-protection/microsoft-defender-atp/threat-analytics) w Microsoft 365 Defender.


## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
- [Nauka języka zapytań](advanced-hunting-query-language.md)
- [Praca z wynikami zapytań](advanced-hunting-query-results.md)
- [Wyszukiwanie zagrożeń na urządzeniach, w wiadomościach e-mail, aplikacjach i tożsamościach](advanced-hunting-query-emails-devices.md)
- [Analiza schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań dla zapytań](advanced-hunting-best-practices.md)