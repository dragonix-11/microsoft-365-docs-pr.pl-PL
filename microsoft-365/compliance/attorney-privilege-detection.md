---
title: Konfigurowanie wykrywania uprawnień klienta obsługi klienta w programie Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Korzystaj z modelu wykrywania uprawnień klienta obsługi klienta, aby podczas przeglądania zawartości w Advanced eDiscovery przypadku korzystać z wykrywania zawartości opartej na uczeniu maszynowym.
ms.openlocfilehash: 5e8a9e1ef0cf8cd8375cd6ce9a0b4d210840e838
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021290"
---
# <a name="set-up-attorney-client-privilege-detection-in-advanced-ediscovery"></a>Konfigurowanie wykrywania uprawnień klienta obsługi klienta w programie Advanced eDiscovery

Głównym i kosztowowym aspektem etapu przeglądu każdego procesu zbierania elektronicznych materiałów dowodowych jest recenzowanie dokumentów pod względem zawartości uprzywilejowanych. Advanced eDiscovery umożliwia wykrywanie zawartości uprzywilejowanych w opartym na uczeniu maszynowym, aby ten proces był wydajniejszy. Ta funkcja jest *nazywana wykrywaniem uprawnień klienta-klienta*.

## <a name="how-does-it-work"></a>Jak to działa?

Po włączeniu wykrywania uprawnień obsługi klienta podczas analizowania danych w zestawie reenzentów wszystkie dokumenty w zestawie reenzentów będą przetwarzane przez [](analyzing-data-in-review-set.md) model wykrywania uprawnień klienta-klienta. Model wygląda na dwie rzeczy:

- Zawartość z uprawnieniami — w modelu jest używane uczenie maszynowe w celu określenia prawdopodobieństwa, że dokument zawiera zawartość, która ma charakter prawny.

- Uczestnicy — w ramach konfigurowania wykrywania uprawnień klienta prawniowego należy przesłać listę pełnomocników do organizacji. Następnie w modelu porównano uczestników dokumentu z listą prawniową w celu ustalenia, czy w dokumencie jest co najmniej jeden uczestnik prawni.

Model tworzy następujące trzy właściwości dla każdego dokumentu:

- **AttorneyClientPrivilegeScore:** Prawdopodobieństwo, że dokument ma charakter prawny; Wartości wyników to między **0** a **1**.

- **HasAttorato:** Ta właściwość ma wartość **True (Prawda),** jeśli jeden z uczestników dokumentu znajduje się na liście pełnomocników. w przeciwnym razie wartość jest **fałszywa**. Wartość ta jest również ustawiona **na** fałsz, jeśli organizacja nie przesłała listy prawniowej.

- **IsPrivilege:** Ta właściwość ma wartość **True** (Prawda), jeśli wartość dla właściwości **AttorneyClientPrivilegeScore** przekracza próg  lub jeśli w dokumencie jest uczestnikiem pełnomocnictwa; w przeciwnym razie ustawiono wartość **false (fałsz**).

Te właściwości (i odpowiadające im wartości) są dodawane do metadanych plików dokumentów w zestawie recenzji, jak pokazano na poniższym zrzucie ekranu:

![Właściwości uprawnień klienta-klienta przedstawione w metadanych pliku.](../media/AeDAttorneyClientPrivilegeMetadata.png)

Te trzy właściwości można również przeszukiwać w ramach zestawu recenzji. Aby uzyskać więcej informacji, zobacz [Wykonywanie zapytań dotyczących danych w zestawie recenzji](review-set-search.md).

## <a name="set-up-the-attorney-client-privilege-detection-model"></a>Konfigurowanie modelu wykrywania uprawnień klienta obsługi klienta

Aby włączyć model wykrywania uprawnień klienta obsługi klienta, organizacja musi włączyć tę funkcję, a następnie przesłać jej listę prawniową.

### <a name="step-1-turn-on-attorney-client-privilege-detection"></a>Krok 1. Włączanie wykrywania uprawnień prawni-klienta

Osoba pełniąca rolę administratora zbierania elektronicznych materiałów dowodowych w organizacji (członka podgrupy Administrator zbierania elektronicznych materiałów dowodowych w grupie ról Menedżer zbierania elektronicznych materiałów dowodowych) musi udostępnić ten model w twoich Advanced eDiscovery przypadku.

1. W Centrum zgodności platformy Microsoft 365 przejdź do strony [Advanced eDiscovery](https://go.microsoft.com/fwlink/p/?linkid=2173764), a następnie kliknij pozycję **Advanced eDiscovery ustawienia**.

   ![Wybierz Advanced eDiscovery ustawienia](..\media\HistoricalVersions1.png)

2. Na stronie **Ustawienia** wybierz kartę Analiza, a następnie  włącz przełącznik Wykrywanie uprawnień klienta-klienta **.**

   ![Kliknij przełącznik, aby włączyć wykrywanie uprawnień klienta-obsługi klienta](..\media\TurnOnAttorneyClientPrivilegeDetection.png)

3. Kliknij **przycisk Zapisz** , aby zapisać zmianę.

### <a name="step-2-upload-a-list-of-attorneys-optional"></a>Krok 2. Upload listę pełnomocników (opcjonalnie)

Aby w pełni wykorzystać model wykrywania uprawnień klienta obsługi klienta i użyć opisanych wcześniej wyników wykrywania  funkcji Ma lub  Potencjalnie uprzywilejowany, przekaż listę adresów e-mail osób chętnych i pracowników prawnych, którzy pracują w Twojej organizacji.

Aby przekazać listę prawnią do użytku przez model wykrywania uprawnień prawni-klienta:

1. Utwórz plik .csv (bez wiersza nagłówka) i dodaj w osobnym wierszu adresy e-mail wszystkich odpowiednich osób. Zapisz ten plik na komputerze lokalnym.

2. Na stronie Advanced eDiscovery **Ustawienia** wybierz **kartę** Analiza.

   Zostanie **wyświetlona strona Uprawnienia klienta prawniczka** i przełącznik  Wykrywanie uprawnień klienta-prawniczka zostanie włączony.

   ![Strona wysuuwana z uprawnieniami klienta obsługi klienta](..\media\AeDUploadAttorneyList1.png)

3. Wybierz **pozycję Wybierz** plik, a następnie znajdź i .csv utworzony w kroku 1.

4. Wybierz **pozycję Zapisz** , aby przekazać listę pełnomocników.

## <a name="use-the-attorney-client-privilege-detection-model"></a>Korzystanie z modelu wykrywania uprawnień klienta obsługi klienta

Postępuj zgodnie z instrukcjami w tej sekcji, aby użyć wykrywania uprawnień klienta prawniowego do dokumentów w zestawie recenzji.

### <a name="step-1-create-a-smart-tag-group-with-attorney-client-privilege-detection-model"></a>Krok 1. Tworzenie grupy tagów inteligentnych z modelem wykrywania uprawnień klienta-obsługi klienta

Jednym z podstawowych sposobów przeglądania wyników procesu sprawdzania prawa do obsługi klienta jest użycie grupy tagów inteligentnych. Grupa tagów inteligentnych wskazuje wyniki wykrywania uprawnień prawni-klienta oraz wyświetla wyniki w wierszu obok tagów w grupie tagów inteligentnych. Umożliwia to szybkie identyfikowanie potencjalnie uprzywilejowanych dokumentów podczas przeglądania dokumentu. Ponadto za pomocą tagów w grupie tagów inteligentnych można oznaczać dokumenty jako dokumenty z uprawnieniami lub bez uprawnień. Aby uzyskać więcej informacji na temat tagów inteligentnych, zobacz [Konfigurowanie tagów inteligentnych w aplikacji Advanced eDiscovery](smart-tags.md).

1. W zestawie recenzji zawierającym dokumenty, które zostały przeanalizowane w kroku 1, wybierz pozycję Zarządzaj  zestawem recenzji, a następnie wybierz pozycję **Zarządzaj tagami**.

2. W **obszarze** Tagi wybierz pozycję rozwijane obok przycisku **Dodaj** grupę, a następnie wybierz pozycję **Dodaj grupę tagów inteligentnych**.

   ![Wybierz pozycję "Dodaj grupę tagów inteligentnych".](../media/AeDCreateSmartTag.png)

3. Na **stronie Wybierz model tagu inteligentnego** wybierz pozycję **Wybierz** obok opcji **Pełnomocnictwo-klient**.

   Zostanie wyświetlona grupa **tagów o nazwie Pełnomocnictwo-klient** . Zawiera ona dwa tagi podrzędne o nazwach **Dodatnia** i Ujemna **, które** odpowiadają możliwym wynikom uzyskanemu w modelu.

   ![Grupa smart tagów prawnicza klient-klient.](../media/AeDAttorneyClientSmartTagGroup.png)

3. Zmień nazwę grupy tagów i tagów odpowiednio do potrzeb recenzji. Można na przykład zmienić nazwę Dodatni **na "** z **uprawnieniami** " i "Ujemny **"** **na "Nieuwiązytowany"**.

### <a name="step-2-analyze-a-review-set"></a>Krok 2. Analizowanie zestawu recenzji

Podczas analizowania dokumentów w zestawie recenzji zostanie również uruchomiony model wykrywania uprawnień klienta-klienta, a odpowiadające im właściwości (opisane w temacie Jak to działa [?](#how-does-it-work)) zostaną dodane do każdego dokumentu w zestawie recenzji. Aby uzyskać więcej informacji na temat analizowania danych w zestawie recenzji, zobacz [Analizowanie danych w zestawie recenzji w programie Advanced eDiscovery](analyzing-data-in-review-set.md).

### <a name="step-3-use-the-smart-tag-group-for-review-of-privileged-content"></a>Krok 3. Przeglądanie zawartości z uprawnieniami za pomocą grupy tagów inteligentnych

Kolejnym krokiem po przeanalizowaniu zestawu recenzji i skonfigurowaniu tagów inteligentnych jest przejrzenie dokumentów. Jeśli model ustali, że dokument ma potencjalnie uprawnienia, odpowiedni tag inteligentny w **panelu** Otagowanie będzie wskazywać na następujące wyniki uzyskane w wyniku wykrywania uprawnień obsługi klienta-klienta:

- Jeśli dokument zawiera zawartość, która może mieć charakter prawny, etykieta Zawartość  prawnie jest wyświetlana obok odpowiadającego mu tagu inteligentnego (który w tym przypadku jest domyślnym **tagiem Dodatni**).

- Jeśli w dokumencie znajduje się uczestnik, który został znaleziony na liście prawnich organizacji, etykieta  Prawniczka jest wyświetlana obok odpowiadającego mu tagu inteligentnego (który w tym przypadku jest również domyślnym tagiem **Dodatni**).

- Jeśli dokument zawiera treści, które mogą mieć charakter prawny i zawiera uczestnika, który został znaleziony z listy pełnomocników,  wyświetlana jest  zarówno zawartość prawnie, jak i etykiety prawne. 

Jeśli w modelu stwierdzisz, że dokument nie zawiera zawartości, która jest z natury legalna lub nie zawiera uczestnika z listy prawnej, ta etykieta nie jest wyświetlana w panelu otagowania.

Na przykład poniższe zrzuty ekranu pokazują dwa dokumenty. Pierwszy z nich zawiera treści, które są z natury prawnej i zawiera uczestnika, który znalazł się na liście pełnomocników. Drugi nie zawiera żadnych etykiet i dlatego nie są wyświetlane żadne etykiety.

![Dokument z etykietami zawartości prawnej i prawnej.](../media/AeDTaggingPanelLegalContentAttorney.png)

![Dokument bez żadnych etykiet.](../media/AeDTaggingPanelNegative.png)

Po przejrzeniu dokumentu w celu sprawdzenia, czy zawiera on zawartość z odpowiednimi uprawnieniami, możesz oznaczyć dokument odpowiednim tagiem.
