---
title: Korzystanie z narzędzia eksportu zbierania elektronicznych materiałów dowodowych w Microsoft Edge
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Musisz włączyć obsługę ClickOnce, aby używać najnowszej wersji Microsoft Edge do pobierania wyników wyszukiwania z usługi Content Search i eDiscovery w centrum zabezpieczeń i zgodności.
ms.openlocfilehash: 13556b08a0eaec5ed11bdaf09014a3988cd56829
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092442"
---
# <a name="use-the-ediscovery-export-tool-in-microsoft-edge"></a>Korzystanie z narzędzia eksportu zbierania elektronicznych materiałów dowodowych w Microsoft Edge

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

W wyniku ostatnich zmian w najnowszej wersji Microsoft Edge obsługa ClickOnce nie jest już domyślnie włączona. Aby kontynuować korzystanie z narzędzia eksportu zbierania elektronicznych materiałów dowodowych do pobierania wyników wyszukiwania zawartości lub zbierania elektronicznych materiałów dowodowych, należy użyć programu [Microsoft Internet Explorer](https://support.microsoft.com/help/17621/internet-explorer-downloads) lub włączyć obsługę ClickOnce w najnowszej wersji Microsoft Edge.

## <a name="enable-clickonce-support-in-microsoft-edge"></a>Włączanie obsługi ClickOnce w Microsoft Edge

1. W Microsoft Edge przejdź do **edge://flags/#edge-click-once**.

2. Jeśli istniejąca wartość jest ustawiona na **wartość Domyślna** lub **Wyłączona** na liście rozwijanej, zmień ją na **Włączone**.

   ![Wybierz pozycję Włączone z listy rozwijanej.](../media/ClickOnceimage1.png)

3. Przewiń w dół do dołu okna przeglądarki i kliknij przycisk **Uruchom ponownie** , aby ponownie uruchomić przeglądarkę Edge.

   ![Kliknij przycisk Uruchom ponownie.](../media/ClickOnceimage2.png)

**Uwaga:** Organizacje mogą używać zasady grupy, aby wyłączyć obsługę ClickOnce. Aby sprawdzić, czy istnieją zasady organizacyjne dotyczące ClickOnce pomocy technicznej, przejdź do **edge://policy**. Poniższy zrzut ekranu pokazuje, że ClickOnce jest włączona w całej organizacji. Jeśli ta wartość zasad jest ustawiona na **wartość false**, należy skontaktować się z administratorem w organizacji.

![Lista zasad organizacyjnych usługi Edge.](../media/ClickOnceimage3.png)

## <a name="install-and-run-the-ediscovery-export-tool"></a>Instalowanie i uruchamianie narzędzia eksportu zbierania elektronicznych materiałów dowodowych

1. Kliknij **pozycję Pobierz wyniki** na stronie wysuwanej eksportu w wyszukiwaniu zawartości lub w przypadku zbierania elektronicznych materiałów dowodowych.

   ![Kliknij pozycję Pobierz wyniki na stronie wysuwanej, aby pobrać wyniki wyszukiwania.](../media/ClickOnceExport1.png)

2. Zostanie wyświetlony monit z potwierdzeniem uruchomienia narzędzia Kliknij **przycisk Otwórz**.

   ![Kliknij przycisk Otwórz, aby uruchomić narzędzie eksportu zbierania elektronicznych materiałów dowodowych.](../media/ClickOnceimage4.png)

   Jeśli narzędzie eksportu zbierania elektronicznych materiałów dowodowych nie jest zainstalowane, zostanie wyświetlony monit z ostrzeżeniem o zabezpieczeniach. 

   ![Kliknij pozycję Zainstaluj, aby zainstalować narzędzie eksportu zbierania elektronicznych materiałów dowodowych.](../media/ClickOnceimage5.png)

3. Kliknij przycisk **Zainstaluj**. Po zainstalowaniu narzędzie eksportu zostanie uruchomione automatycznie.

Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Eksportowanie wyników wyszukiwania zawartości](export-search-results.md)

- [Jak włączyć flagi eksperymentu w Microsoft Edge](https://microsoftedgesupport.microsoft.com/hc/articles/360034075294-How-to-enable-experiment-flags-in-Microsoft-Edge-Insider-channels)
