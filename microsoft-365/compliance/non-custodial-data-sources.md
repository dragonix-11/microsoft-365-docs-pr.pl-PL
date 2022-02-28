---
title: Dodawanie niepowiązywnych źródeł danych do sprawy Advanced eDiscovery przypadku
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
description: Możesz dodać niechbowe źródła danych do sprawy Advanced eDiscovery i umieścić w źródle danych hold. Niepowiązywne źródła danych są ponownie indeksowane, więc każda zawartość oznaczona jako częściowo zindeksowana jest ponownie przetwarzana w celu jej pełnego i szybkiego przeszukiwania.
ms.openlocfilehash: a4702ebdfbd41b2541c51380a1d44dd133d506c9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987272"
---
# <a name="add-non-custodial-data-sources-to-an-advanced-ediscovery-case"></a>Dodawanie niepowiązywnych źródeł danych do sprawy Advanced eDiscovery przypadku

W Advanced eDiscovery przypadkach nie zawsze spełnia ono Twoje potrzeby skojarzenia źródła danych Microsoft 365 ze współpracownikiem w tej sytuacji. Być może trzeba będzie jednak skojarzyć te dane ze sprawą, aby można było ją przeszukać, dodać do zestawu recenzji oraz przeanalizować i przejrzeć. Funkcja w programie Advanced eDiscovery jest nazywana źródłami danych bez przechowywania danych i umożliwia dodawanie danych do sprawy bez konieczności kojarzenia ich ze współpracownikiem. Dotyczy to również tych samych funkcji Advanced eDiscovery danych o niedobłędnych danych, które są dostępne dla danych skojarzonych z przechowywania. Dwie najbardziej przydatne rzeczy, które można zastosować do danych niebędące właściwościami przechowawczymi, są umieszczanie ich w hold i przetwarzanie ich przy użyciu [indeksowania zaawansowanego](indexing-custodian-data.md).

## <a name="add-a-non-custodial-data-source"></a>Dodawanie źródła danych, które nie może być źródłem danych, które nie jest zabłędne

Wykonaj poniższe czynności, aby dodać źródła danych, które nie są zbędne, i zarządzać nimi w Advanced eDiscovery przypadku.

1. Na **Advanced eDiscovery** głównej kliknij sprawę, do której chcesz dodać dane.

2. Kliknij **kartę Źródła** danych, a następnie kliknij pozycję **Dodaj źródło** **danychDdaj** >  lokalizacje danych.

3. Na **stronie wysuwu** Nowe niechcące lokalizacje danych wybierz źródła danych, które chcesz dodać do sprawy. Możesz dodać wiele skrzynek pocztowych i witryn, rozwijając sekcje SharePoint lub **Exchange, a** następnie klikając pozycję **Edytuj**.

   ![Dodaj SharePoint i skrzynki Exchange jako niezabędowe źródła danych.](../media/NonCustodialDataSources1.png)

   - **SharePoint** — kliknij pozycję **Edytuj,** aby dodać witryny. Wybierz witrynę na liście lub możesz ją wyszukać, wpisując adres URL witryny na pasku wyszukiwania. Wybierz witryny, które chcesz dodać jako nieuwierzyskie źródła danych, a następnie kliknij przycisk **Dodaj**.

   - **Exchange** — kliknij pozycję **Edytuj,** aby dodać skrzynki pocztowe. Wpisz nazwę lub alias (co najmniej trzy znaki) w polu wyszukiwania skrzynek pocztowych lub grup dystrybucyjnych. Zaznacz skrzynki pocztowe, które chcesz dodać jako nieuchybne źródła danych, a następnie kliknij przycisk **Dodaj**.

   > [!NOTE]
   > Za pomocą **sekcji SharePoint i** **Exchange** można dodawać witryny i skrzynki pocztowe skojarzone z zespołem lub grupą Yammer jako niedyskojarzone źródła danych. Musisz oddzielnie dodać skrzynkę pocztową i witrynę skojarzoną z zespołem Yammer grupy.<br/><br/> Ponadto dodawanie adresu URL witryny głównej (`https://contoso-my.sharepoint.com/personal/`na przykład lub`https://contoso-my.sharepoint.com/`) jako SharePoint źródła danych nie jest obsługiwane. Musisz dodać konkretne witryny.

4. Po dodaniu niebędące odimkowo źródła danych możesz umieścić te lokalizacje w agonii. Zaznacz lub usuń **zaznaczenie pola wyboru** Przytrzymaj obok źródła danych, aby umieścić je w miejscu wstrzymywania.

5. Aby **dodać** źródła danych do sprawy,  kliknij przycisk Dodaj u dołu strony wysuwu Nowe lokalizacje danych niebędące dostępem do danych.

   Każde dodane przez Ciebie źródło danych bez niedobłędnych danych znajduje się na **stronie Źródła** danych. Źródła danych, które nie są zbędne, są identyfikowane przez **wartość Lokalizacja** danych w **kolumnie Typ** źródła.

   ![Na karcie Źródła danych mogą być niezabędne źródła danych.](../media/NonCustodialDataSources2.png)

Po dodaniu do sprawy niebędące źródłem danych, które nie są niedobczasowe, zostanie utworzone zadanie o nazwie *Ponowne* indeksowanie danych niebędące odimkowo i wyświetlone na karcie Zadania sprawy. Po utworzeniu zadania zostanie ponownie zindeksowany proces indeksowania zaawansowanego w inicjatorze i źródła danych.

## <a name="manage-the-hold-for-non-custodial-data-sources"></a>Zarządzanie wstrzymywaniami źródeł danych, które nie są zbędne

Po utworzeniu wstrzymywania źródła danych, które nie są przeziębowe źródłem danych, są automatycznie tworzone zasady przechowywania, które zawierają niepowiązywne źródła danych dla sprawy. Po umieścić inne, niechcące źródła danych, są one dodawane do tych zasad przechowywania.

1. Otwórz Advanced eDiscovery i wybierz **kartę Wstrzymaj**.

2. Kliknij **pozycję NCDSHold-\<GUID\>**, gdzie wartość identyfikatora GUID jest unikatowa w przypadku.

   Na wysuwanych stronie są wyświetlane informacje i statystyki dotyczące źródeł danych, które nie są zbędne w wstrzymaniu.

   ![Statystyka jest wyświetlana na stronie wysuwu dla niechbowych źródeł danych.](../media/NonCustodialDataSourcesHoldFlyout.png)

3. Kliknij **pozycję Edytuj wstrzymaj** , aby wyświetlić źródła danych, dla których nie zależy od tego, które źródła danych są umieszczone w a holdie, i wykonać następujące zadania zarządzania:

   - Na **stronie Lokalizacje** możesz zwolnić niebędące źródłem danych, usuwając je z zawieszonego miejsca. Zwolnienie źródła danych nie powoduje usunięcia z sprawy źródła danych, dla których nie ma informacji o niedopuszczaniu. Usuwa ona tylko hold, które zostało umieszczone w źródle danych.

   - Na stronie **Zapytanie** możesz edytować wstrzymanie w celu utworzenia opartego na zapytaniu hold, które jest stosowane do wszystkich źródeł danych, które nie są przechwycowe.
