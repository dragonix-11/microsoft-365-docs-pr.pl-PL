---
title: Używanie zapytań udostępnionych w Microsoft 365 Defender zaawansowanego wyszukiwania
description: Natychmiast zacznij chować przed zagrożeniami za pomocą wstępnie zdefiniowanych i udostępnionych zapytań. Udostępniaj swoje zapytania publicznie lub organizacji.
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, wykrywanie niestandardowe, schemat, kusto, github repo, moje zapytania, zapytania udostępnione
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
ms.openlocfilehash: 96db917808094487039a13740cba80ad751f062f
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755506"
---
# <a name="use-shared-queries-in-advanced-hunting"></a>Korzystanie z zapytań udostępnionych podczas zaawansowanego wyszukiwania

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender



[Zaawansowane zapytania](advanced-hunting-overview.md) myśliwskie mogą być udostępniane użytkownikom w tej samej organizacji. Możesz również znaleźć zapytania udostępnione publicznie w GitHub. Te zapytania umożliwiają szybkie prowadzenie określonych scenariuszy wyszukiwania zagrożeń bez konieczności pisania zapytań od podstaw.

:::image type="content" source="../../media/shared-query-1.png" alt-text="Informacje dotyczące zapytań udostępnionych w portalu Microsoft 365 Defender sieci Microsoft 365 Defender." lightbox="../../media/shared-query-1.png":::

## <a name="save-modify-and-share-a-query"></a>Zapisywanie, modyfikowanie i udostępnianie zapytania
Nowe lub istniejące zapytanie można zapisać w taki sposób, aby było dostępne tylko dla Ciebie lub udostępnione innym użytkownikom w organizacji. 

1. Tworzenie lub modyfikowanie zapytania. 

2. Kliknij przycisk **listy rozwijanej Zapisz** zapytanie i wybierz pozycję **Zapisz jako**.
    
3. Wprowadź nazwę zapytania. 

   :::image type="content" source="../../media/shared-query-2.png" alt-text="Nowe zapytanie, które niebawem zostanie zapisane w portalu Microsoft 365 Defender." lightbox="../../media/shared-query-2.png":::

4. Wybierz folder, w którym chcesz zapisać zapytanie.
    - **Zapytania udostępnione** — udostępnione wszystkim użytkownikom w organizacji
    - **Moje zapytania —** dostępne tylko dla Ciebie
    
5. Wybierz **Zapisz**. 

## <a name="delete-or-rename-a-query"></a>Usuwanie lub zmienianie nazwy zapytania
1. Wybierz trzy kropki z prawej strony zapytania, którego nazwę chcesz zmienić lub usunąć.

    :::image type="content" source="../../media/shared-query-3.png" alt-text="Opcje dla zapytania udostępnionego na stronie zaawansowanego wyszukiwania w portalu Microsoft 365 Defender zaawansowanego" lightbox="../../media/shared-query-3.png":::

2. Wybierz **pozycję Usuń** i potwierdź usunięcie. Możesz też **wybrać pozycję Zmień** nazwę i podać nową nazwę zapytania.

## <a name="create-a-direct-link-to-a-query"></a>Tworzenie bezpośredniego linku do zapytania
Aby wygenerować link, który otwiera zapytanie bezpośrednio w zaawansowanym edytorze zapytań wyszukiwania, zakończ zapytanie i wybierz pozycję **Udostępnij link**.

## <a name="access-queries-in-the-github-repository"></a>Zapytania programu Access w GitHub repozytorium  
Firma Microsoft ds. zabezpieczeń regularnie udostępnia zaawansowane zapytania myśliwskie w [wyznaczonym repozytorium publicznym na GitHub](https://aka.ms/hunting-queries). To repozytorium jest otwarte na udziały. Aby dołączyć, [dołącz GitHub bezpłatnie](https://github.com/).

>[!tip]
>Poza tym, w celu znajdowania działań i wskaźników skojarzonych z wyłaniających się zagrożeniami, są również zapewniane zaawansowane zapytania myśliwskie firmy Microsoft. Te zapytania są udostępniane w ramach raportów analizy zagrożeń w [programie](/windows/security/threat-protection/microsoft-defender-atp/threat-analytics) Microsoft 365 Defender.


## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Nauka języka zapytań](advanced-hunting-query-language.md)
- [Praca z wynikami zapytań](advanced-hunting-query-results.md)
- [Wyszukiwanie zagrożeń na urządzeniach, w wiadomościach e-mail, aplikacjach i tożsamościach](advanced-hunting-query-emails-devices.md)
- [Analiza schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań dla zapytań](advanced-hunting-best-practices.md)