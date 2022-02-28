---
title: Rozwiązywanie problemów z jednym elementem
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
description: Możesz naprawić błąd przetwarzania w dokumencie w zestawie recenzji w programie Advanced eDiscovery bez konieczności śledzenia zbiorczego procesu rozwiązywania problemów z błędami.
ms.openlocfilehash: c816ef1e3fd28299bb316e51aa434a8f08d544a0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987770"
---
# <a name="single-item-error-remediation-in-advanced-ediscovery"></a>Rozwiązywanie problemów z jednym elementem w programie Advanced eDiscovery

Rozwiązywanie problemów ze Advanced eDiscovery umożliwia użytkownikom korygowanie problemów z danymi, które uniemożliwiają Advanced eDiscovery prawidłowego przetwarzania zawartości. Na przykład pliki chronione hasłem nie mogą być przetwarzane, ponieważ są one zablokowane lub zaszyfrowane. Wcześniej za pomocą tego przepływu pracy można było zbiorczo naprawiać tylko [błędy](error-remediation-when-processing-data-in-advanced-ediscovery.md). Czasami jednak korygowanie błędów w wielu plikach nie ma sensu, gdy nie masz pewności, czy któryś z tych plików nie odpowiada badasz przypadku. Korygowanie błędów przed sprawdzeniem metadanych pliku (na przykład lokalizacji pliku lub osób, które miały dostęp) w celu podjęcia od góry decyzji dotyczących czasu reakcji może być także sensowne. Nowa funkcja o nazwie  rozwiązywanie problemów z pojedynczym elementem umożliwia menedżerom zbierania elektronicznych materiałów dowodowych wyświetlanie metadanych plików z błędem przetwarzania i, jeśli to konieczne, rozwiązywanie tego błędu bezpośrednio w zestawie recenzji. W tym artykule omówiono identyfikowanie, ignorowanie i korygowanie plików z błędami przetwarzania w zestawie recenzji.

## <a name="identify-documents-with-errors"></a>Identyfikowanie dokumentów z błędami

Dokumenty z błędami przetwarzania w zestawie recenzji są teraz identyfikowane (na banerze). Możesz rozwiązać ten problem lub zignorować go. Poniższy zrzut ekranu przedstawia baner błędu przetwarzania dla dokumentu programu Word w zestawie recenzji chronionym hasłem. Można również wyświetlić metadane plików dokumentów z błędami przetwarzania.

![Transparent wyświetlany dla dokumentu z błędem przetwarzania.](../media/SIERimage1.png)

Dokumenty, w których wystąpiły błędy przetwarzania, można również wyszukiwać przy użyciu warunku **Stan** przetwarzania podczas wykonywania zapytań [dotyczących dokumentów w zestawie recenzji](review-set-search.md).

![Użyj warunku Stan przetwarzania w celu wyszukiwania dokumentów o błędach.](../media/SIERimage2.png)

### <a name="ignore-errors"></a>Ignoruj błędy

Błąd przetwarzania można zignorować, klikając pozycję **Ignoruj** na banerze błędu przetwarzania. Gdy zignorujesz błąd, dokument zostanie usunięty z przepływu pracy rozwiązywania [problemów z błędami zbiorczym](error-remediation-when-processing-data-in-advanced-ediscovery.md). Gdy błąd zostanie zignorowany, baner dokumentu zmieni kolor i będzie wskazywać, że błąd przetwarzania został zignorowany. W dowolnym momencie możesz przywrócić decyzję o zignorowania błędu, klikając pozycję **Przywróć**.

![Kliknij przycisk Ignoruj, aby zignorować błąd przetwarzania.](../media/SIERimage3.png)

Możesz również wyszukać wszystkie dokumenty, w których wystąpił błąd przetwarzania, który został zignorowany, używając warunku ignorowanych błędów przetwarzania podczas wykonywania zapytań dotyczących dokumentów w zestawie recenzji.

![Użyj warunku przetwarzania zignorowanych, aby wyszukać zignorowane dokumenty błędów.](../media/SIERimage4.png)

## <a name="remediate-a-document-with-errors"></a>Rozwiązywanie problemów z dokumentem z błędami

Czasami może być wymagane usunięcie błędu przetwarzania w dokumentach (przez usunięcie hasła, odszyfrowanie zaszyfrowanego pliku lub odzyskanie uszkodzonego dokumentu), a następnie dodanie usuniętego dokumentu do zestawu recenzji. Dzięki temu można przejrzeć i wyeksportować dokument błędu razem z innymi dokumentami w zestawie recenzji. 

Aby rozwiązać ten krok w celu rozwiązania problemów z jednym dokumentem, wykonaj następujące czynności:

1. Kliknij **pozycję** **PobierzPobierz** >  oryginał, aby pobrać kopię pliku na komputer lokalny.

   ![Pobierz dokument z błędem przetwarzania.](../media/SIERimage5.png)

2. Rozwiązywanie problemów z błędem w pliku w trybie offline. W przypadku zaszyfrowanych plików wymagałoby to oprogramowania do odszyfrowywania w celu usunięcia ochrony hasłem: podania hasła i zapisania pliku lub użycia pęku haseł. Po zakończeniu rozwiązywania problemów z plikiem przejdź do następnego kroku.

3. W zestawie recenzji wybierz plik z komunikatem o błędzie przetwarzania, który został zaradczy, a następnie kliknij pozycję **Działania naprawcze**.

   ![Kliknij pozycję Działania naprawcze w banerze dokumentu z błędem przetwarzania.](../media/SIERimage6.png)


4. Kliknij **przycisk** Przeglądaj, przejdź do lokalizacji pliku usuniętego na komputerze lokalnym, a następnie wybierz ten plik.

   ![Kliknij przycisk Przeglądaj i wybierz plik zaradczy na komputerze lokalnym.](../media/SIERimage7.png)

    Po wybraniu pliku, który został naprawiony, jest on automatycznie przekazywany do zestawu recenzji. Możesz śledzić stan przetwarzania pliku.

    ![Zostanie wyświetlony stan procesu rozwiązywania problemów.](../media/SIERimage8.png)

   Po zakończeniu przetwarzania możesz wyświetlić dokument zaradczy.

    ![Usunięte pliki możesz wyświetlić w natywnym formacie w zestawie recenzji.](../media/SIERimage9.png)

Aby uzyskać więcej informacji na temat działań naprawczych w dokumencie, zobacz Co [się dzieje w przypadku rozwiązywania problemów z plikami](error-remediation-when-processing-data-in-advanced-ediscovery.md#what-happens-when-files-are-remediated).

## <a name="search-for-remediated-documents"></a>Wyszukiwanie dokumentów zaradczych

Możesz wyszukać wszystkie dokumenty w zestawie recenzji, których działania naprawcze zostały rozwiązane, używając  warunku Słowa kluczowe i określając następującą parę właściwość:wartość: **IsFromErrorRemediation:true**. Ta właściwość jest również dostępna w pliku ładowania eksportu podczas eksportowania dokumentów z zestawu recenzji.
