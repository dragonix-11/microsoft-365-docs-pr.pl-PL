---
title: Korzystanie z narzędzia do eksportowania zbierania elektronicznych materiałów dowodowych w przeglądarce Microsoft Edge
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
description: Musisz włączyć obsługę technologii ClickOnce, aby używać najnowszej wersji przeglądarki Microsoft Edge do pobierania wyników wyszukiwania z usługi Content Search i eDiscovery w centrum zabezpieczeń i zgodności.
ms.openlocfilehash: f93ab1da1b76d435cc1ce684aa459b4c131dfff8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630394"
---
# <a name="use-the-ediscovery-export-tool-in-microsoft-edge"></a>Korzystanie z narzędzia do eksportowania zbierania elektronicznych materiałów dowodowych w przeglądarce Microsoft Edge

W wyniku ostatnich zmian w najnowszej wersji przeglądarki Microsoft Edge obsługa technologii ClickOnce nie jest już domyślnie włączona. Aby kontynuować korzystanie z narzędzia do eksportowania zbierania elektronicznych materiałów dowodowych do pobierania wyników wyszukiwania zawartości lub zbierania elektronicznych materiałów dowodowych, musisz użyć programu [Microsoft Internet Explorer](https://support.microsoft.com/help/17621/internet-explorer-downloads) lub włączyć obsługę technologii ClickOnce w najnowszej wersji przeglądarki Microsoft Edge.

## <a name="enable-clickonce-support-in-microsoft-edge"></a>Włączanie obsługi technologii ClickOnce w przeglądarce Microsoft Edge

1. W przeglądarce Microsoft Edge przejdź do **edge://flags/#edge-click-once**.

2. Jeśli istniejąca wartość jest ustawiona na **wartość Domyślna** lub **Wyłączona** na liście rozwijanej, zmień ją na **Włączone**.

   ![Wybierz pozycję Włączone z listy rozwijanej.](../media/ClickOnceimage1.png)

3. Przewiń w dół do dołu okna przeglądarki i kliknij przycisk **Uruchom ponownie** , aby ponownie uruchomić przeglądarkę Edge.

   ![Kliknij przycisk Uruchom ponownie.](../media/ClickOnceimage2.png)

**Uwaga:** Organizacje mogą używać zasady grupy, aby wyłączyć obsługę technologii ClickOnce. Aby sprawdzić, czy istnieją zasady organizacyjne dotyczące obsługi technologii ClickOnce, przejdź do **edge://policy**. Poniższy zrzut ekranu pokazuje, że clickonce jest włączone w całej organizacji. Jeśli ta wartość zasad jest ustawiona na **wartość false**, należy skontaktować się z administratorem w organizacji.

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

- [Jak włączyć flagi eksperymentu w przeglądarce Microsoft Edge](https://microsoftedgesupport.microsoft.com/hc/articles/360034075294-How-to-enable-experiment-flags-in-Microsoft-Edge-Insider-channels)
