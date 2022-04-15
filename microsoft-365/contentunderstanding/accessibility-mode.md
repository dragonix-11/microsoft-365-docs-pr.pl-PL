---
title: Tryb ułatwień dostępu w SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.localizationpriority: medium
description: Dowiedz się, jak używać trybu funkcji ułatwień dostępu podczas trenowania i pracy z modelami w SharePoint Syntex.
ms.openlocfilehash: 567abb862af27457c1eb9395e32bf68d98446887
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882335"
---
# <a name="accessibility-mode-in-sharepoint-syntex"></a>Tryb ułatwień dostępu w SharePoint Syntex

W [SharePoint Syntex](index.md) użytkownicy mogą włączyć tryb ułatwień dostępu na wszystkich etapach trenowania modelu (etykieta, trenowanie, testowanie) podczas pracy z przykładami dokumentów. Korzystanie z trybu ułatwień dostępu może pomóc użytkownikom o niskim zasięgu wzroku mieć łatwiejszą dostępność klawiatury podczas nawigacji i etykietowania elementów w przeglądarce dokumentów.

Ułatwia to użytkownikom korzystanie z klawiatur w celu nawigowania po tekście w przeglądarce dokumentów oraz rozpoznawania narracji nie tylko wybranych wartości, ale także akcji (takich jak etykietowanie lub usuwanie etykiet z zaznaczonego tekstu) lub przewidywanych wartości etykiet podczas trenowania modelu z dodatkowymi przykładowymi dokumentami. 


![Tryb ułatwień dostępu.](../media/content-understanding/accessibility-mode.png)

## <a name="requirements"></a>Wymagania

Aby usłyszeć dźwięk narracji, włącz [aplikację Narratora](https://support.microsoft.com/windows/complete-guide-to-narrator-e4397a0d-ef4f-b386-d8ae-c172f109bdb1) w ustawieniach narratora w systemie Windows 10.

![Włącz narratora.](../media/content-understanding/narrator-settings.png)

## <a name="labeling-for-keyboard-users"></a>Etykietowanie dla użytkowników klawiatury

W przypadku użytkowników klawiatury korzystających z trybu ułatwień dostępu w przypadku etykietowania tekstu w przykładowym dokumencie w przeglądarce można użyć następujących klawiszy:

- Karta: przenosi cię do przodu i wybiera następne słowo.
- Tab + Shift: przenosi cię do tyłu i wybiera poprzednie słowo.
- Wprowadź: Etykieta lub usuwa etykietę z wybranego wyrazu.
- Strzałka w prawo: przenosi cię do przodu przez poszczególne znaki w wybranym słowie.
- Strzałka w lewo: przenosi cię do tyłu przez poszczególne znaki w wybranym słowie.

> [!NOTE]
> W przypadku etykietowania wielu wyrazów dla pojedynczej etykiety należy oznaczyć każde słowo etykietą.


## <a name="narration"></a>Narracji

W przypadku użytkowników Narratora korzystających z trybu ułatwień dostępu użyj tej samej nawigacji klawiaturowej opisanej dla użytkowników klawiatury, aby przejść przez przykładowy dokument w przeglądarce.

Gdy nawigujesz po przykładowych dokumentach i wartościach ciągów etykiet, Narrator przekaże użytkownikowi następujące monity dźwiękowe:

- Gdy użyjesz klawiatury do nawigowania po podglądzie dokumentów, dźwięk Narratora będzie określać wybrany ciąg.
- W wybranym ciągu dźwięk Narratora będzie określał każdy znak w ciągu podczas ich wybierania przy użyciu klawiszy strzałek w lewo lub w prawo.
- Jeśli wybierzesz ciąg, który został oznaczony etykietą, Narrator będzie określał wartość, a następnie "etykietą".  Jeśli na przykład wartość etykiety to "Contoso", zostanie ona oznaczona jako "Costoso labeled". 
- Jeśli na karcie trenowania wybierzesz w przeglądarce dokumentów ciąg, który został tylko przewidywany, dźwięk Narratora będzie określał wartość, a następnie "przewidywany". Dzieje się tak, gdy trenowanie przewiduje wartość w pliku, która nie odpowiada temu, co zostało oznaczone przez użytkownika.
- Jeśli na karcie trenowania wybierzesz ciąg w przeglądarce dokumentów, który został oznaczony etykietą i przewidywany, dźwięk Narratora będzie określał wartość, a następnie "etykietą i przewidywaną". Dzieje się tak, gdy szkolenie zakończy się pomyślnie i występuje dopasowanie między przewidywaną wartością a etykietą użytkownika.

Po oznaczeniu ciągu lub usunięciu etykiety w przeglądarce dźwięk Narratora ostrzega o zapisaniu zmian przed zakończeniem pracy.

## <a name="see-also"></a>Zobacz też

[Tworzenie wyodrębniacza](create-an-extractor.md)

[Tworzenie klasyfikatora](create-a-classifier.md)










 


  
  



