---
title: Recenzja
description: Przejrzyj sekcję po dojecheniu.
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 3bb6ef605d360e259ef9fa91ed51da35506a2942
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988390"
---
# <a name="step-6-review-your-selections-to-create-your-package"></a>Krok 6. Przejrzyj wybrane opcje, aby utworzyć pakiet.

1. Na tej karcie usługa wyświetla szczegóły testu i uruchamia szybki test kompletności.

    Komunikat **Sprawdzanie poprawności zakończyło** się **pomyślnie lub** Sprawdzanie poprawności nie powiodło się i wskazuje, czy możesz przejść do następnych kroków, czy nie.

2. Przejrzyj szczegóły testu, a jeśli tak, kliknij **przycisk** Utwórz.

    :::image type="content" alt-text="Sprawdzanie poprawności widoku." source="Media/validation.png" lightbox="Media/validation.png":::

3. Spowoduje to dołocie pakietu do środowiska Test Base. Jeśli pakiet zostanie utworzony pomyślnie, zostanie wyzwolony zautomatyzowany test, który sprawdza, czy pakiet można pomyślnie wykonać na platformie Azure.

    ![Wynik pomyślny.](Media/successful.png)

    > [!NOTE]
    > Otrzymasz powiadomienie z portalu Azure Portal w celu powiadomienia o sukcesie lub niepowodzeniu weryfikacji pakietu.
    >
    > Pamiętaj, że ten proces może potrwać do 24 godzin, dlatego prawdopodobnie u limitu czasu Twojej strony internetowej zostanie u limit czasu, jeśli nie jesteś na niej aktywny, dlatego powiadomienie nie poinformuje Cię o ukończeniu tego uruchomienia na żądanie.

    - Peradventure to się dzieje, możesz wyświetlić stan pakietu na karcie **Zarządzanie pakietami** .

      :::image type="content" alt-text="Obraz zarządzania pakietami." source="Media/managepackages.png" lightbox="Media/managepackages.png":::

    - W celu pomyślnego przetestowania ich wyniki można sprawdzić za pośrednictwem stron  Podsumowanie testów **, Wyniki** aktualizacji zabezpieczeń i Wyniki aktualizacji funkcji w zaplanowanych interwałach, często rozpoczynając kilka dni od przekazania.
  
    - W przypadku testów nieudanych należy przekazać nowy pakiet. 

      Dzienniki testów można **pobrać do dalszej** analizy **z wyników aktualizacji** zabezpieczeń i **stron wyników aktualizacji** funkcji.

    - W przypadku powtarzających się błędów w testach skontaktuj się testbasepreview@microsoft.com ze szczegółami błędu.

## <a name="next-steps"></a>Następne kroki

Zapoznaj się z naszymi wytycznymi dotyczącymi zawartości, korzystając z poniższego linku.

> [!div class="nextstepaction"]
> [Następny krok](contentguideline.md)
