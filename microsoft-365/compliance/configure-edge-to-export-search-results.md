---
title: Używanie narzędzia eDiscovery Export Tool w programie Microsoft Edge
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Aby pobierać wyniki ClickOnce Microsoft Edge z wyszukiwania i zbierania elektronicznych materiałów dowodowych w Centrum zabezpieczeń i zgodności, musisz włączyć obsługę zbierania elektronicznych materiałów dowodowych przy użyciu najnowszej wersji programu Microsoft Edge.
ms.openlocfilehash: bd42ebffce326e4abe4943ff4187fc2bd960ff65
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2021
ms.locfileid: "62959540"
---
# <a name="use-the-ediscovery-export-tool-in-microsoft-edge"></a>Używanie narzędzia eDiscovery Export Tool w programie Microsoft Edge

W wyniku ostatnich zmian w najnowszej wersji pakietu Microsoft Edge obsługa ClickOnce jest już domyślnie włączona. Aby nadal pobierać wyniki wyszukiwania zawartości lub wyszukiwania zbierania elektronicznych materiałów dowodowych za pomocą narzędzia eDiscovery Export Tool, należy użyć programu [Microsoft Internet Explorer](https://support.microsoft.com/help/17621/internet-explorer-downloads) lub włączyć obsługę programu ClickOnce w najnowszej wersji programu Microsoft Edge.

## <a name="enable-clickonce-support-in-microsoft-edge"></a>Włączanie ClickOnce technicznej w Microsoft Edge

1. W Microsoft Edge **przejdź do edge://flags/#edge-click-once**.

2. Jeśli istniejąca wartość jest ustawiona na wartość  **Domyślna** lub Wyłączona na liście rozwijanej, zmień ją na **Włączono**.

   ![Z listy rozwijanej wybierz pozycję Włączone.](../media/ClickOnceimage1.png)

3. Przewiń w dół do dołu okna przeglądarki i kliknij pozycję Uruchom **ponownie, aby ponownie** uruchomić przeglądarkę Edge.

   ![Kliknij pozycję Uruchom ponownie.](../media/ClickOnceimage2.png)

**Uwaga:** Organizacje mogą używać programu zasady grupy w celu wyłączenia ClickOnce technicznej. Aby sprawdzić, czy istnieją zasady organizacji dotyczące ClickOnce, przejdź do **edge://policy**. Poniższy zrzut ekranu przedstawia, ClickOnce w całej organizacji. Jeśli ta wartość zasad jest ustawiona na **fałsz**, skontaktuj się z administratorem w twojej organizacji.

![Lista zasad organizacji w edge.](../media/ClickOnceimage3.png)

## <a name="install-and-run-the-ediscovery-export-tool"></a>Instalowanie i uruchamianie narzędzia eDiscovery Export Tool

1. Kliknij **pozycję Pobierz wyniki** na stronie wysuwanego eksportu w przeszukiwaniu zawartości lub w przypadku sprawy zbierania elektronicznych materiałów dowodowych.

   ![Kliknij pozycję Pobierz wyniki na wysuwanych stronie, aby pobrać wyniki wyszukiwania.](../media/ClickOnceExport1.png)

2. Zostanie wyświetlony monit z potwierdzeniem uruchomienia narzędzia i kliknij przycisk **Otwórz**.

   ![Kliknij przycisk Otwórz, aby uruchomić narzędzie eDiscovery Export Tool.](../media/ClickOnceimage4.png)

   Jeśli narzędzie eDiscovery Export Tool nie jest zainstalowane, zostanie wyświetlony monit z ostrzeżeniem o zabezpieczeniach. 

   ![Kliknij przycisk Zainstaluj, aby zainstalować narzędzie eDiscovery Export Tool.](../media/ClickOnceimage5.png)

3. Kliknij przycisk **Zainstaluj**. Po jej zainstalowaniu narzędzie do eksportowania zostanie automatycznie uruchomić.

Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Eksportowanie wyników wyszukiwania zawartości](export-search-results.md)

- [Jak włączyć flagi eksperymentów w Microsoft Edge](https://microsoftedgesupport.microsoft.com/hc/articles/360034075294-How-to-enable-experiment-flags-in-Microsoft-Edge-Insider-channels)
