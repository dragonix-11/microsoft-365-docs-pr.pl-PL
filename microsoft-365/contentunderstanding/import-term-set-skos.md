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
ms.custom: admindeeplinkSPO
search.appverid: ''
ms.localizationpriority: high
ms.openlocfilehash: c7a23b8da32f5ae9132a41661a1141f34df48a6b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318203"
---
# <a name="import-a-term-set-using-a-skos-based-format"></a>Importowanie zestawu terminów przy użyciu formatu opartego na SKOS

Zestawy terminów można zaimportować przy użyciu formatu opartego na SKOS. Aby uzyskać szczegółowe informacje na temat tego formatu, SharePoint informacje o formacie [taksonomii SKOS](skos-format-reference.md). Ta funkcja wymaga licencji [SharePoint Syntex](index.md) licencji.

Zalecamy przechowywanie plików importu na mniej niż 20 000 terminów. Większe pliki mogą zwiększyć czas sprawdzania poprawności i importu.

1. W centrum SharePoint rozwiń pozycję **Usługi zawartości**, a następnie wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185073" target="_blank">**Magazyn okresów**</a>.

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
