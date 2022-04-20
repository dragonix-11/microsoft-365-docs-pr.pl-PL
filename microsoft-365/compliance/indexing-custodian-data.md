---
title: Zaawansowane indeksowanie danych opiekuna
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
description: Po dodaniu opiekuna do sprawy zbierania elektronicznych materiałów dowodowych (Premium) każda zawartość, która została uznana za częściowo indeksowana, jest ponownie przetwarzana, aby była w pełni przeszukiwalna.
ms.openlocfilehash: 8b7dbbb13b9a667a7b5a50a5535634414c0caec5
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993627"
---
# <a name="advanced-indexing-of-custodian-data"></a>Zaawansowane indeksowanie danych opiekuna

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Po dodaniu opiekuna do sprawy zbierania elektronicznych materiałów dowodowych (Premium) każda zawartość, która została uznana za częściowo indeksowana lub miała błędy indeksowania, zostanie ponownie wyświetlona. Ten proces ponownego indeksowania jest nazywany *indeksowaniem zaawansowanym*. Istnieje wiele powodów, dla których zawartość jest częściowo indeksowana lub ma błędy indeksowania. Obejmuje to pliki obrazów lub obecność obrazów w pliku, nieobsługiwanych typów plików lub limity indeksowania rozmiaru pliku. W przypadku plików SharePoint zaawansowane indeksowanie działa tylko na elementach, które są oznaczone jako częściowo indeksowane lub mają błędy indeksowania. W Exchange wiadomości e-mail z załącznikami obrazów nie są oznaczone jako częściowo indeksowane lub z błędami indeksowania. Oznacza to, że te pliki nie zostaną ponownie wygenerowane przez proces indeksowania zaawansowanego.

Aby dowiedzieć się więcej na temat obsługi przetwarzania i częściowo indeksowanych elementów, zobacz:

- [Obsługiwane typy plików zbierania elektronicznych materiałów dowodowych (Premium)](supported-filetypes-ediscovery20.md)

- [Częściowo zaindeksowane elementy w środowisku zbierania elektronicznych materiałów dowodowych](partially-indexed-items-in-content-search.md)

- [Formaty plików indeksowane przez Exchange Search](/exchange/file-formats-indexed-by-exchange-search-exchange-2013-help)

- [Domyślne rozszerzenia nazw plików przeszukanych i analizowane typy plików na serwerze SharePoint](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)

## <a name="viewing-advanced-indexing-results"></a>Wyświetlanie zaawansowanych wyników indeksowania

Po zakończeniu procesu indeksowania zaawansowanego można zrozumieć skuteczność ponownego przetwarzania.  W widoku Zaawansowane wyniki indeksowania na karcie **Przetwarzanie** dla przypadku wykres zawiera listę elementów dodanych do *indeksu hybrydowego*.  Indeks hybrydowy to miejsce, w którym funkcja zbierania elektronicznych materiałów dowodowych (Premium) przechowuje ponownie przetworzoną zawartość.

Ten widok zawiera również liczbę elementów, które wymagają korygowania, oraz inny wykres błędów według typu pliku. Więcej informacji można znaleźć w następujących artykułach:

- [Korygowanie błędów podczas przetwarzania danych](error-remediation-when-processing-data-in-advanced-ediscovery.md)

- [Korygowanie błędu pojedynczego elementu](single-item-error-remediation.md)

## <a name="updating-the-advanced-index-for-custodians"></a>Aktualizowanie indeksu zaawansowanego dla opiekunów

Po dodaniu opiekuna do sprawy zbierania elektronicznych materiałów dowodowych (Premium) wszystkie częściowo indeksowane elementy są ponownie przetwarzane. Jednak w miarę upływu czasu do skrzynki pocztowej użytkownika lub konta OneDrive można dodać więcej częściowo indeksowanych elementów.  W razie potrzeby można zaktualizować indeks dla określonego opiekuna. Aby uzyskać więcej informacji, zobacz [Zarządzanie opiekunami w sprawie zbierania elektronicznych materiałów dowodowych (Premium](manage-new-custodians.md#reindex-custodian-data)). Możesz również zaktualizować indeks dla wszystkich opiekunów w jednym przypadku, klikając **indeks Aktualizacji** na karcie **Przetwarzanie** .

> [!NOTE]
> Aktualizowanie indeksów opiekunów jest długotrwałym procesem. Zaleca się, aby w danym przypadku nie aktualizować indeksów więcej niż raz dziennie.
