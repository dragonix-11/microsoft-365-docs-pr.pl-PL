---
title: Zaawansowane indeksowanie danych przetwarzających
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
description: Po dodaniu do sprawy Advanced eDiscovery wszelkie treści uważane za częściowo zindeksowane są ponownie przetwarzane w celu w pełni możliwego wyszukiwania.
ms.openlocfilehash: 1c43f55f399f69d58e05c073e688170d53480b42
ms.sourcegitcommit: efb333ce0772265da91632110acba39acfbe0bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2021
ms.locfileid: "62996847"
---
# <a name="advanced-indexing-of-custodian-data"></a>Zaawansowane indeksowanie danych przetwarzających

Po dodaniu do sprawy Advanced eDiscovery zawartości uważanej za częściowo zindeksowane lub błędy indeksowania jest ponownie indeksowana. Ten proces ponownego indeksowania nosi *nazwę Indeksowanie zaawansowane*. Istnieje wiele powodów, dla których zawartość jest częściowo indeksowana lub występują błędy indeksowania. Dotyczy to plików obrazów lub informacji o obecności obrazów w pliku, nieobsługiwanych typów plików lub limitów indeksowania o rozmiarze pliku. W SharePoint pliki indeksowania zaawansowanego są uruchamiane tylko dla elementów oznaczonych jako częściowo indeksowane lub z błędami indeksowania. W Exchange e-mail, które mają załączniki w obrazach, nie są oznaczane jako częściowo indeksowane ani z błędami indeksowania. Oznacza to, że te pliki nie zostaną ponownie zindeksowane przez proces indeksowania zaawansowanego.

Aby dowiedzieć się więcej o przetwarzaniu pomocy technicznej i elementach częściowo indeksowanych, zobacz:

- [Typy plików obsługiwane w programie Advanced eDiscovery](supported-filetypes-ediscovery20.md)

- [Częściowo indeksowane elementy na zbierania elektronicznych materiałów dowodowych](partially-indexed-items-in-content-search.md)

- [Formaty plików indeksowane przez Exchange wyszukiwania](/exchange/file-formats-indexed-by-exchange-search-exchange-2013-help)

- [Domyślne rozszerzenia nazw plików przeszukanych i typy plików analizowanych w programie SharePoint Server](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)

## <a name="viewing-advanced-indexing-results"></a>Wyświetlanie wyników indeksowania zaawansowanego

Po zakończeniu procesu indeksowania zaawansowanego możesz lepiej zrozumieć skuteczność ponownego przetwarzania.  W widoku Wyniki indeksowania zaawansowanego na karcie  Przetwarzanie dla sprawy na wykresie jest wymieniona liczba elementów dodanych do indeksu *hybrydowego*.  Indeks hybrydowy to miejsce, Advanced eDiscovery przechowywaną zawartość.

Ten widok zawiera również liczbę elementów wymagających rozwiązywania problemów i inny wykres błędów według typu pliku. Więcej informacji można znaleźć w następujących artykułach:

- [Rozwiązywanie problemów podczas przetwarzania danych](error-remediation-when-processing-data-in-advanced-ediscovery.md)

- [Rozwiązywanie problemów z jednym elementem](single-item-error-remediation.md)

## <a name="updating-the-advanced-index-for-custodians"></a>Aktualizowanie indeksu zaawansowanego dla zatrzymań

Po dodaniu do sprawy Advanced eDiscovery ponownego przetwarzania wszystkich częściowo indeksowanych elementów. Jednak w momencie upływu czasu elementy częściowo indeksowane mogą być dodawane do skrzynki pocztowej użytkownika lub do OneDrive konta.  W razie potrzeby można zaktualizować indeks dla określonego opiekuna. Aby uzyskać więcej informacji, zobacz [Zarządzanie opiekunami w Advanced eDiscovery przypadku](manage-new-custodians.md#reindex-custodian-data). Indeks można także zaktualizować dla wszystkich opiekunów w przypadku, klikając **indeks** Aktualizuj na **karcie** Przetwarzanie.

> [!NOTE]
> Aktualizowanie indeksów bazoerowych jest procesem długotrwałym. Zaleca się, aby w przypadku każdego przypadku nie aktualizować indeksów więcej niż raz dziennie.
