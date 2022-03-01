---
title: Używanie zapytań udostępnionych w Microsoft 365 Defender zaawansowanego wyszukiwania
description: Natychmiast zacznij chować przed zagrożeniami za pomocą wstępnie zdefiniowanych i udostępnionych zapytań. Udostępniaj swoje zapytania publicznie lub organizacji.
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, wykrywanie niestandardowe, schemat, kusto, github repo, moje zapytania, zapytania udostępnione
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 06952be112f4eb28867a4a0cd4bffbee0c664b5c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021368"
---
# <a name="use-shared-queries-in-advanced-hunting"></a>Korzystanie z zapytań udostępnionych podczas zaawansowanego wyszukiwania

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender



[Zaawansowane zapytania](advanced-hunting-overview.md) myśliwskie mogą być udostępniane użytkownikom w tej samej organizacji. Możesz również znaleźć zapytania udostępnione publicznie w GitHub. Te zapytania umożliwiają szybkie prowadzenie określonych scenariuszy wyszukiwania zagrożeń bez konieczności pisania zapytań od podstaw.

![Obraz zapytań udostępnionych.](../../media/shared-query-1.png)

## <a name="save-modify-and-share-a-query"></a>Zapisywanie, modyfikowanie i udostępnianie zapytania
Nowe lub istniejące zapytanie można zapisać w taki sposób, aby było dostępne tylko dla Ciebie lub udostępnione innym użytkownikom w organizacji. 

1. Tworzenie lub modyfikowanie zapytania. 

2. Kliknij przycisk **listy rozwijanej Zapisz** zapytanie i wybierz pozycję **Zapisz jako**.
    
3. Wprowadź nazwę zapytania. 

   ![Obraz zapisywania zapytania.](../../media/shared-query-2.png)

4. Wybierz folder, w którym chcesz zapisać zapytanie.
    - **Zapytania udostępnione** — udostępnione wszystkim użytkownikom w organizacji
    - **Moje zapytania —** dostępne tylko dla Ciebie
    
5. Wybierz **Zapisz**. 

## <a name="delete-or-rename-a-query"></a>Usuwanie lub zmienianie nazwy zapytania
1. Wybierz trzy kropki z prawej strony zapytania, którego nazwę chcesz zmienić lub usunąć.

    ![Obraz zapytania wybierającego.](../../media/shared-query-3.png)

2. Wybierz **pozycję Usuń** i potwierdź usunięcie. Możesz też **wybrać pozycję Zmień** nazwę i podać nową nazwę zapytania.

## <a name="create-a-direct-link-to-a-query"></a>Tworzenie bezpośredniego linku do zapytania
Aby wygenerować link, który otwiera zapytanie bezpośrednio w zaawansowanym edytorze zapytań wyszukiwania, zakończ zapytanie i wybierz pozycję **Udostępnij link**.

## <a name="access-queries-in-the-github-repository"></a>Zapytania programu Access w GitHub repozytorium  
Firma Microsoft ds. zabezpieczeń regularnie udostępnia zaawansowane zapytania myśliwskie w [wyznaczonym repozytorium publicznym na GitHub](https://aka.ms/hunting-queries). To repozytorium jest otwarte na udziały. Aby dołączyć, [dołącz GitHub bezpłatnie](https://github.com/).

>[!tip]
>Poza tym, w celu znajdowania działań i wskaźników skojarzonych z wyłaniających się zagrożeniami, są również zapewniane zaawansowane zapytania myśliwskie firmy Microsoft. Te zapytania są udostępniane w ramach raportów analizy zagrożeń w [programie](/windows/security/threat-protection/microsoft-defender-atp/threat-analytics) Microsoft 365 Defender.


## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaw język zapytań](advanced-hunting-query-language.md)
- [Praca z wynikami zapytania](advanced-hunting-query-results.md)
- [Przeszukaj urządzenia, wiadomości e-mail, aplikacje i tożsamości](advanced-hunting-query-emails-devices.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań kwerend](advanced-hunting-best-practices.md)