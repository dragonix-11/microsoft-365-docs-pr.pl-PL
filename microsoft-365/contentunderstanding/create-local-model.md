---
title: Tworzenie modelu w lokalnej witrynie SharePoint przy użyciu usługi Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Dowiedz się, jak utworzyć model lokalny w lokalnej witrynie SharePoint przy użyciu SharePoint Syntex.
ms.openlocfilehash: bcd3f1f086af3982cb4a3ecc5fe754cf82f09a70
ms.sourcegitcommit: e624221597480295b799d56568c4f6f56d40b41d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2022
ms.locfileid: "65535387"
---
# <a name="create-a-model-on-a-local-sharepoint-site-with-microsoft-sharepoint-syntex"></a>Tworzenie modelu w lokalnej witrynie SharePoint przy użyciu usługi Microsoft SharePoint Syntex

SharePoint Syntex udostępnia teraz opcję tworzenia i trenowania modeli lokalnie we własnej SharePoint lokacji. Tych modeli można używać tylko w witrynie, w której zostały utworzone. 

Aktywując klasyfikację i wyodrębnianie dokumentów w lokacji SharePoint, SharePoint Syntex umożliwia klasyfikowanie plików w bibliotekach dokumentów, wyodrębnianie informacji z nowych plików i automatyzowanie działań na podstawie wyodrębnionych informacji.

Po aktywowaniu tworzenia modelu lokalnego do witryny zostaną dodane następujące listy i biblioteki:

- Biblioteka dokumentów modeli
- Biblioteka dokumentów plików szkoleniowych
- Lista szablonów objaśnień
- Lista użycia modelu

Ta funkcja jest dostępna tylko do tworzenia [modeli interpretacji dokumentów](apply-a-model.md) i [wstępnie utworzonych modeli](prebuilt-models.md). 

## <a name="create-a-model-on-a-local-site"></a>Tworzenie modelu w witrynie lokalnej

1. W bibliotece dokumentów SharePoint wybierz pliki, które chcesz przeanalizować, a następnie wybierz pozycję **Klasyfikowanie i wyodrębnianie**.

    ![Zrzut ekranu przedstawiający bibliotekę dokumentów SharePoint z wyróżnioną opcją Klasyfikowanie i wyodrębnianie.](../media/content-understanding/local-model-classify-and-extract-option.png) 

2. Przy pierwszym użyciu tej funkcji aktywujesz SharePoint Syntex w witrynie. Zostanie wyświetlony następujący komunikat.

    ![Zrzut ekranu przedstawiający stronę Informacje o klasyfikacji i wyodrębnianiu dokumentów aktywuj.](../media/content-understanding/local-model-first-run-activate-message.png) 

    > [!NOTE]
    > Musisz mieć uprawnienie Zarządzaj witryną sieci Web, aby wykonywać zadania administracyjne i zarządzać zawartością witryny. Byłby to właściciel witryny. Po aktywowaniu funkcji każda osoba z uprawnieniem Zarządzaj listami będzie mogła tworzyć modele i zarządzać nimi.

3. Wybierz pozycję **Aktywuj** , aby kontynuować. Zostanie wyświetlony następujący komunikat.

    ![Zrzut ekranu przedstawiający komunikat Dotyczący klasyfikacji i wyodrębniania uaktywnionego dokumentu z opcją Utwórz model.](../media/content-understanding/local-model-activated-message.png) 

4. Wybierz **pozycję Utwórz model**.

5. Na panelu **Tworzenie modelu** wpisz nazwę modelu, wybierz typ modelu, a następnie wybierz pozycję **Utwórz**.

    ![Zrzut ekranu przedstawiający panel Tworzenie modelu.](../media/content-understanding/local-model-create-a-model.png) 

6. Przejdź do [trenowania modelu interpretacji dokumentów](apply-a-model.md) lub [skonfigurowania wstępnie utworzonego modelu](prebuilt-models.md) przy użyciu wybranych plików.

7. Po zakończeniu zostanie otwarty panel **Dodaj do biblioteki** .

    ![Zrzut ekranu przedstawiający panel Dodawanie do biblioteki przedstawiający zastosowane witryny i biblioteki.](../media/content-understanding/local-model-add-to-library-panel.png) 

8. Na panelu **Dodaj do biblioteki** zobaczysz nazwę witryny SharePoint i bibliotekę dokumentów, do których zostanie zastosowany model. Jeśli chcesz zastosować model do innej biblioteki, wybierz pozycję **Powrót do bibliotek** i wybierz bibliotekę, która ma być używana. Następnie wybierz pozycję **Dodaj**.

9. Na stronie głównej modelu w sekcji **Where the model is applied on this site (Gdzie model jest stosowany w tej witrynie** ) można zobaczyć biblioteki, które mają zastosowany model. Aby zastosować model do innych bibliotek w witrynie, wybierz pozycję **Zastosuj model**. 

    ![Zrzut ekranu przedstawiający stronę główną modelu z sekcją Where the model is applied on the site (Gdzie model jest stosowany w witrynie).](../media/content-understanding/local-model-home-page.png) 

