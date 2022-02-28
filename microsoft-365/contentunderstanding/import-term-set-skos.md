---
title: Importowanie zestawu terminów przy użyciu formatu opartego na SKOS
description: Dowiedz się, jak importować zestawy terminów przy użyciu formatu opartego na SKOS
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.service: ''
ms.collection: enabler-strategic
search.appverid: ''
ms.localizationpriority: high
ms.openlocfilehash: 6f472754484d7bb41485b94d65689009d2c615fd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985097"
---
# <a name="import-a-term-set-using-a-skos-based-format"></a>Importowanie zestawu terminów przy użyciu formatu opartego na SKOS

Zestawy terminów można zaimportować przy użyciu formatu opartego na SKOS. Aby uzyskać szczegółowe informacje na temat tego formatu, SharePoint informacje o formacie [taksonomii SKOS](skos-format-reference.md). Ta funkcja wymaga licencji [SharePoint Syntex](index.md) licencji.

Zalecamy przechowywanie plików importu na mniej niż 20 000 terminów. Większe pliki mogą zwiększyć czas sprawdzania poprawności i importu.

1. W centrum SharePoint rozwiń pozycję **Usługi zawartości**, a następnie kliknij pozycję **Magazyn okresów**.

2. Wybierz grupę terminy, do której chcesz zaimportować zestaw terminów.

3. Na pasku poleceń kliknij pozycję **Importuj zestaw terminy**.

4. Jeśli chcesz pobrać przykładowy plik do użycia jako szablon, kliknij plik **sample-metadata.ttl** , aby pobrać przykładowy plik w formacie opartym na SKOS.

5. Utwórz plik importu zawierający zestawy terminów& które chcesz zaimportować.

6. W **obszarze Format** pliku wybierz **pozycję SKOS (*.ttl)**.

7. Kliknij **przycisk Przeglądaj** i przejdź do pliku importu i dodaj go.

8. Kliknij **pozycję Importuj**. Nie zamykaj panelu do momentu zakończenia importowania.

Po pomyślnym zaimportowaniu pliku zostanie wyświetlony komunikat o sukcesie, a magazyn terminów zostanie odświeżony i będzie można przejść do nowo utworzonych zestawów okresów.

## <a name="see-also"></a>Zobacz też

[Wprowadzenie do zarządzanych metadanych](/sharepoint/managed-metadata)

[Omówienie opisów dokumentów](document-understanding-overview.md)

[Importowanie zestawów okresów (poziom witryny)](https://support.microsoft.com/office/168fbc86-7fce-4288-9a1f-b83fc3921c18)
