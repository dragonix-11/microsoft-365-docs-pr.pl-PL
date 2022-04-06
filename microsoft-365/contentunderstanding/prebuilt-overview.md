---
title: Omówienie wbudowanych modeli w aplikacji Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.customer: intro-overview
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Dowiedz się więcej o wbudowanych modelach w aplikacji Microsoft SharePoint Syntex.
ms.openlocfilehash: 1146e4947392ce0e0848632e55f22e5b8b8d2d91
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569053"
---
# <a name="prebuilt-models-overview-in-microsoft-sharepoint-syntex"></a>Omówienie wbudowanych modeli w aplikacji Microsoft SharePoint Syntex

Oprócz [zrozumienia modeli dokumentów](document-understanding-overview.md) i modeli przetwarzania formularzy [firma SharePoint Syntex](form-processing-overview.md) wstępnie utworzonych modeli w celu zautomatyzowania wyodrębniania informacji.

Wbudowane modele są wstępnie przeszkolone w zakresie rozpoznawania dokumentów i strukturalnych informacji w dokumentach. Zamiast tworzyć nowy model niestandardowy od podstaw, możesz dodać do istniejącego wstępnie przeszkolonego modelu określone pola, które będą dopasowane do potrzeb Twojej organizacji. 

W modelach gotowych jest używane optyczne rozpoznawanie znaków (OCR) w połączeniu z modelami uczenia szczegółowego w celu identyfikowania i wyodrębniania wstępnie zdefiniowanych pól tekstowych i danych wspólnych dla określonych typów dokumentów. Należy rozpocząć od przeanalizowania jednego z plików na podstawie utworzonego modelu. Następnie wybierz wykryte pola, które są sensowne dla Twojego przeznaczenia. Jeśli model nie wykryje potrzebnych pól, możesz ponownie przeanalizować je przy użyciu innego pliku.

Podobnie jak w przypadku dokumentów opis modeli, w centrum zawartości są tworzone i zarządzane wstępnie [utworzone modele](create-a-content-center.md). Po zastosowaniu do biblioteki SharePoint dokumentów model jest skojarzony z typem zawartości i ma kolumny do przechowywania wyodrębnianych informacji. 

Po opublikowaniu modelu zastosuj go do dowolnej biblioteki SharePoint dokumentów, do których masz dostęp.  

## <a name="requirements"></a>Wymagania

- Obsługiwane formaty plików: JPEG, PNG, BMP, TIFF i PDF (osadzone w tekście lub skanowane).

- Obsługiwane języki: obecnie obsługiwane są tylko faktury Stany Zjednoczone języka angielskiego. Obsługiwane są potwierdzenia sprzedaży w języku angielskim z Australii, Kanady, Stany Zjednoczone, Wielkiej Brytanii i Indii.

- Osadzone w tekście pliki PDF najlepiej wyeliminować możliwość błędu wyodrębniania znaków i lokalizacji.

- W przypadku plików PDF i TIFF można przetwarzać maksymalnie 2000 stron.

- Rozmiar pliku musi być mniejszy niż 50 MB.

- Wymiary obrazu muszą mieć od 50 x 50 pikseli do 10 000 x 10 000 pikseli.

- Wymiary pliku PDF nie mogą być większe niż 17 x 17 cali, co odpowiada rozmiarowi papieru legalne lub A3 lub mniejszego.

- Całkowity rozmiar danych szkoleniowych nie może być mniejszy niż 500 stron.

### <a name="file-limitations"></a>Ograniczenia dotyczące plików

Zwróć uwagę na następujące różnice Microsoft Office plików tekstowych i plików zeskanowanych za pomocą rozpoznawania znaków OCR (PDF, obraz lub TIFF):

- Office: obcięte z 64 000 znaków (podczas uruchamiania z plikami w bibliotece dokumentów).

- Pliki skanowane zaybko:  limit strony wynosi 20.  

## <a name="model-considerations"></a>Zagadnienia dotyczące modelu

- Jeśli do tej samej biblioteki zastosowano co najmniej dwa wbudowane modele, plik zostanie sklasyfikowany przy użyciu modelu o największej średniej ufności. Wyodrębnione jednostki będą pochodzić tylko z zastosowanego modelu.

- Jeśli do biblioteki, która ma model zrozumienia dokumentu, zastosowano model wstępny, plik jest klasyfikowany przy użyciu modelu rozumienia dokumentu i dowolnych przeszkolonych wyodrębniaczy dla tego modelu. Jeśli istnieją puste kolumny zgodne ze wstępnie utworzonym modelem, kolumny zostaną wypełnione przy użyciu tych wyodrębnianych wartości.

- Jeśli model wstępny zostanie zastosowany do biblioteki, która ma niestandardowy model przetwarzania formularzy, plik zostanie sklasyfikowany przy użyciu modelu wstępnie utworzonego i wszystkich wykrytych wyodrębniaczy dla tego modelu. Jeśli istnieją puste kolumny zgodne z modelem przetwarzania formularzy, kolumny zostaną wypełnione przy użyciu tych wyodrębnianych wartości.

- Stosowanie więcej niż jednego modelu przetwarzania formularzy niestandardowych do biblioteki nie jest obsługiwane.


## <a name="see-also"></a>Zobacz też

[Wyodrębnianie informacji z faktur lub pokwitowania za pomocą wbudowanego modelu](prebuilt-overview.md)
 

