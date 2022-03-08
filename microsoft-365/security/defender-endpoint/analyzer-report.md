---
title: Opis raportu w formacie HTML analizatora klienta
description: Dowiedz się, jak analizować raport HTML analizatora klienta punktu końcowego programu Microsoft Defender
keywords: Raport analizatora klienta, raport html, analizator klienta
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: ab6a23d1f2c8893a86fb6432ab9fece95a10006c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322887"
---
# <a name="understand-the-client-analyzer-html-report"></a>Opis raportu w formacie HTML analizatora klienta

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Analizator klienta tworzy raport w formacie HTML. Dowiedz się, jak przeglądać raport w celu zidentyfikowania potencjalnych problemów z czujnikami, które mogą pomóc w ich rozwiązaniu.

Opis raportu można zrozumieć w poniższym przykładzie.

 Przykładowe dane wyjściowe analizatora na komputerze, na który wdano identyfikator organizacji wygasł, i nie można uzyskać dostępu do jednego z wymaganych adresów URL punktu końcowego programu Microsoft Defender:

![Obraz wyniku analizatora klienta.](images/147cbcf0f7b6f0ff65d200bf3e4674cb.png)

- Na górze do odwołania są wymienione wersja skryptu i środowisko uruchomieniowe skryptu
- Sekcja **Informacje o urządzeniu** zawiera podstawowe identyfikatory systemu operacyjnego i urządzenia w celu unikatowego zidentyfikowania urządzenia, na którym działa analizator.
- Szczegóły **zabezpieczeń punktu końcowego** zawierają ogólne informacje o programie Microsoft Defender dla procesów związanych z punktem końcowym, w tym Program antywirusowy Microsoft Defender i procesu czujnika. Jeśli ważne procesy nie są w trybie online zgodnie z oczekiwaniami, kolor zmieni się na czerwony.

  ![Obraz szczegółowego wyniku analizatora klienta](images/85f56004dc6bd1679c3d2c063e36cb80.png)

-   Szczegóły **zabezpieczeń punktu końcowego** zawierają ogólne informacje o programie Microsoft Defender dla procesów związanych z punktem końcowym, w tym Program antywirusowy Microsoft Defender i procesu czujnika. Jeśli ważne procesy nie są w trybie online zgodnie z oczekiwaniami, kolor zmieni się na czerwony.

  ![Obraz szczegółowego wyniku analizatora klienta.](images/85f56004dc6bd1679c3d2c063e36cb80.png)

-   W **podsumowaniu Sprawdź** wyniki zobaczysz zagregowaną liczbę błędów, ostrzeżeń lub zdarzeń informacyjnych wykrytych przez analizatora.

-   W **szczegółowych wynikach** zostanie wyświetlona lista (posortowana według istotności) z wynikami i wskazówkami opartymi na obserwacjach wykonanych przez analizatora.

## <a name="open-a-support-ticket-to-microsoft-and-include-the-analyzer-results"></a>Otwórz bilet pomocy technicznej do firmy Microsoft i dołącz wyniki analizatora

Aby uwzględnić pliki wyników analizatora [podczas](contact-support.md#open-a-service-request) otwierania biletu pomocy technicznej, użyj sekcji Załączniki  i uwzględnij `MDEClientAnalyzerResult.zip` plik:

![Obraz monitu o załącznik.](images/508c189656c3deb3b239daf811e33741.png)

> [!NOTE]
> Jeśli rozmiar pliku jest większy niż 25 MB, inżynier pomocy technicznej przydzielony do sprawy udostępni dedykowany bezpieczny obszar roboczy do przekazywania dużych plików do analizy.
