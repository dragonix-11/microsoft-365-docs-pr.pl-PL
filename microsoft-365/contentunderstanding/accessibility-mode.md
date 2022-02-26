---
title: SharePoint Syntex tryb ułatwień dostępu
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.localizationpriority: medium
description: Dowiedz się, jak używać trybu ułatwień dostępu podczas szkolenia modelu w programie SharePoint Syntex.
ms.openlocfilehash: 6a27615e0b676fdcefb617d76a206d9f47c6f882
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973793"
---
# <a name="sharepoint-syntex-accessibility-mode"></a>SharePoint Syntex tryb ułatwień dostępu

W [SharePoint Syntex](index.md) użytkownicy mogą włączać tryb ułatwień dostępu na wszystkich etapach szkoleń modelu (etykieta, szkolenie, test) podczas pracy z przykładami dokumentów. Korzystanie z trybu ułatwień dostępu ułatwia użytkownikom o słabym wzroku korzystanie z klawiatury podczas nawigowania i oznaczania elementów w przeglądarce dokumentów.

Ułatwia to użytkownikom poruszanie się po tekście w przeglądarce dokumentów i odsłuchianie narracji nie tylko wybranych wartości, ale również akcji (takich jak oznaczanie lub usuwanie etykiet z zaznaczonego tekstu) oraz przewidywanie wartości etykiet w ramach szkolenie modelu z dodatkowych dokumentów przykładowych. 


![Tryb ułatwień dostępu.](../media/content-understanding/accessibility-mode.png)

## <a name="requirements"></a>Wymagania

Aby odsłuchać dźwięk narracji, włącz aplikację Narrator w ustawieniach [Narratora](https://support.microsoft.com/windows/complete-guide-to-narrator-e4397a0d-ef4f-b386-d8ae-c172f109bdb1) w Windows 10 systemie.

![Włącz Narratora.](../media/content-understanding/narrator-settings.png)

## <a name="labeling-for-keyboard-users"></a>Etykiety dla użytkowników klawiatury

W przypadku użytkowników klawiatury korzystających z trybu ułatwień dostępu, jeśli w przeglądarce jest oznaczany tekst etykietą w przykładowym dokumencie, można użyć następujących klawiszy:

- Tab. Powoduje przejście do przodu i zaznaczenie następnego wyrazu.
- Tab + Shift: powoduje przejście wstecz i zaznaczenie poprzedniego wyrazu.
- Wprowadź: Etykieta lub usunięcie etykiety z zaznaczonego wyrazu.
- Strzałka w prawo: umożliwia przejście do przodu między poszczególnymi znakami w zaznaczonym wyrazie.
- Strzałka w lewo: Umożliwia przejście do tyłu między poszczególnymi znakami w zaznaczonym wyrazie.

> [!NOTE]
> W przypadku oznaczania wielu wyrazów jedną etykietą musisz o etykiecie każdy wyraz.


## <a name="narration"></a>Narracja

W przypadku użytkowników Narratora korzystających z trybu ułatwień dostępu użyj tej samej nawigacji za pomocą klawiatury opisanej dla użytkowników klawiatury, aby przejść przez przykładowy dokument w przeglądarce.

Podczas nawigowania między przykładami dokumentów i wartościami ciągów etykiet Narrator wyświetla użytkownikowi następujące monity audio:

- Gdy będziesz poruszać się po przeglądarce dokumentów za pomocą klawiatury, w części audio Narratora zostanie odczytany wybrany ciąg.
- W ramach zaznaczonego ciągu audio Narrator audio będzie odczytywać poszczególne znaki w ciągu podczas ich zaznaczania za pomocą klawiszy strzałek w lewo i w prawo.
- Jeśli wybierzesz ciąg, który został oznaczony etykietą, Narrator odczyta wartość, a następnie "etykieta".  Jeśli na przykład etykieta ma wartość "Contoso", będzie to wartość "Kosztoso z etykietą". 
- Jeśli na karcie szkolenie wybierzesz w przeglądarce dokumentów ciąg, który został już przewidywany, w obszarze Audio Narratora zostanie odczytana wartość, a następnie "przewidywana". Dzieje się tak, gdy szkolenie przewiduje wartość w pliku, która nie jest taka, jaka została oznaczona przez użytkownika.
- Jeśli na karcie szkolenie wybierzesz w przeglądarce dokumentów ciąg, który został oznaczony i prognozowany, w obszarze audio Narratora zostanie odczytana wartość, a następnie "etykieta i prognozowanie". Dzieje się tak, gdy szkolenie zakończyło się pomyślnie i istnieje dopasowanie między przewidywaną wartością a etykietą użytkownika.

Po oznaczeniu ciągu znaków lub usunięciu etykiety w przeglądarce dźwięk Narratora będzie ostrzegał o zapisaniu zmian przed zakończeniem.

## <a name="see-also"></a>Zobacz też

[Tworzenie wyodrębnianego](create-an-extractor.md)

[Tworzenie klasyfikatora](create-a-classifier.md)










 


  
  



