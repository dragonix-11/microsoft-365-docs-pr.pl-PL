---
title: Omówienie wstępnie utworzonych modeli w usłudze Microsoft SharePoint Syntex
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
description: Dowiedz się więcej o wstępnie utworzonych modelach w usłudze Microsoft SharePoint Syntex.
ms.openlocfilehash: d43a608885864f5c81a8938010a0a52a2c4998a6
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64916232"
---
# <a name="prebuilt-models-overview-in-microsoft-sharepoint-syntex"></a>Omówienie wstępnie utworzonych modeli w usłudze Microsoft SharePoint Syntex

Oprócz [zrozumienia modeli](document-understanding-overview.md) dokumentów i [modeli przetwarzania formularzy](form-processing-overview.md) SharePoint Syntex udostępnia wstępnie utworzone modele do automatyzacji wyodrębniania informacji.

Wstępnie utworzone modele są wstępnie wytrenowane do rozpoznawania dokumentów i informacji strukturalnych w dokumentach. Zamiast tworzyć nowy model niestandardowy od podstaw, można iterować na istniejącym wstępnie wytrenowanym modelu w celu dodania konkretnych pól odpowiadających potrzebom organizacji. 

Wstępnie utworzone modele używają optycznego rozpoznawania znaków (OCR) w połączeniu z modelami uczenia głębokiego w celu identyfikowania i wyodrębniania wstępnie zdefiniowanych pól tekstu i danych wspólnych dla określonych typów dokumentów. Zacznij od przeanalizowania jednego z plików względem wstępnie utworzonego modelu. Następnie wybierz wykryte pola, które mają sens dla Twojego celu. Jeśli model nie wykryje potrzebnych pól, możesz przeanalizować je ponownie przy użyciu innego pliku.

Podobnie jak w przypadku modeli interpretacji dokumentów, wstępnie utworzone modele są tworzone i zarządzane w [centrum zawartości](create-a-content-center.md). Po zastosowaniu do biblioteki dokumentów SharePoint model jest skojarzony z typem zawartości i zawiera kolumny do przechowywania wyodrębnianych informacji. 

Po opublikowaniu modelu użyj centrum zawartości, aby zastosować go do dowolnej biblioteki dokumentów SharePoint, do których masz dostęp.  

## <a name="requirements"></a>Wymagania

- Obsługiwane formaty plików: JPEG, PNG, BMP, TIFF i PDF (osadzone tekstem lub zeskanowane).

- Obsługiwane języki: obecnie obsługiwane są tylko faktury w języku angielskim z Stany Zjednoczone. Obsługiwane są wpływy ze sprzedaży w języku angielskim z Australii, Kanady, Stany Zjednoczone, Wielkiej Brytanii i Indii.

- Osadzone w tekście pliki PDF najlepiej eliminują możliwość błędu podczas wyodrębniania znaków i lokalizacji.

- W przypadku formatów PDF i TIFF można przetworzyć maksymalnie 2000 stron.

- Rozmiar pliku musi być mniejszy niż 50 MB.

- Wymiary obrazu muszą mieć od 50 x 50 pikseli do 10 000 x 10 000 pikseli.

- Wymiary formatu PDF mają rozmiar do 17 x 17 cali, co odpowiada rozmiarowi papieru legalnego lub A3 lub mniejszemu.

- Całkowity rozmiar danych treningowych wynosi 500 stron lub mniej.

### <a name="file-limitations"></a>Ograniczenia dotyczące plików

Zwróć uwagę na następujące różnice dotyczące Microsoft Office plików tekstowych i plików zeskanowanych za pomocą protokołu OCR (PDF, obraz lub TIFF):

- Office pliki: obcięte przy użyciu 64 000 znaków (gdy są uruchamiane względem plików w bibliotece dokumentów).

- Pliki zeskanowane przez protokół OCR: istnieje limit 20 stron.  

## <a name="model-considerations"></a>Zagadnienia dotyczące modelu

- Jeśli co najmniej dwa wstępnie utworzone modele zostaną zastosowane do tej samej biblioteki, plik zostanie sklasyfikowany przy użyciu modelu o najwyższej średniej ufności. Wyodrębnione jednostki będą pochodzić tylko z zastosowanego modelu.

- Jeśli wstępnie utworzony model zostanie zastosowany do biblioteki, która ma model zrozumienia dokumentów, plik zostanie sklasyfikowany przy użyciu modelu zrozumienia dokumentu i wszystkich wytrenowanych wyodrębniaczy dla tego modelu. Jeśli istnieją puste kolumny zgodne ze wstępnie utworzonym modelem, kolumny zostaną wypełnione przy użyciu wyodrębnionych wartości.

- Jeśli wstępnie utworzony model zostanie zastosowany do biblioteki, która ma niestandardowy model przetwarzania formularzy, plik zostanie sklasyfikowany przy użyciu wstępnie utworzonego modelu i wszystkich wykrytych wyodrębniaczy dla tego modelu. Jeśli istnieją puste kolumny zgodne z modelem przetwarzania formularzy, kolumny zostaną wypełnione przy użyciu wyodrębnionych wartości.

- Stosowanie więcej niż jednego niestandardowego modelu przetwarzania formularzy do biblioteki nie jest obsługiwane.


## <a name="see-also"></a>Zobacz też

[Wyodrębnianie informacji z faktur lub paragonów przy użyciu wstępnie utworzonego modelu](prebuilt-overview.md)
 

