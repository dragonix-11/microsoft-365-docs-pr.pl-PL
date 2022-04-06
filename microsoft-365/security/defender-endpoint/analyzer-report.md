---
title: Opis raportu w formacie HTML analizatora klienta
description: Dowiedz się, jak analizować raport Ochrona punktu końcowego w usłudze Microsoft Defender analizatora klienta w formacie HTML
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
ms.openlocfilehash: 1f843c62d44ed7c25f07568cc0ee92709fb080a7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468904"
---
# <a name="understand-the-client-analyzer-html-report"></a>Opis raportu w formacie HTML analizatora klienta

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Analizator klienta tworzy raport w formacie HTML. Dowiedz się, jak przeglądać raport w celu zidentyfikowania potencjalnych problemów z czujnikami, które mogą pomóc w ich rozwiązaniu.

Opis raportu można zrozumieć w poniższym przykładzie.

 Przykładowe dane wyjściowe analizatora na komputerze, który został naniesony do wygasłego identyfikatora organizacji, i nie można osiągnąć jednego z wymaganych adresów URL Ochrona punktu końcowego w usłudze Microsoft Defender URL:

:::image type="content" source="images/147cbcf0f7b6f0ff65d200bf3e4674cb.png" alt-text="Strona wyników analizatora klienta MDE" lightbox="images/147cbcf0f7b6f0ff65d200bf3e4674cb.png":::

- Na górze do odwołania są wymienione wersja skryptu i środowisko uruchomieniowe skryptu
- Sekcja **Informacje o urządzeniu** zawiera podstawowe identyfikatory systemu operacyjnego i urządzenia w celu unikatowego zidentyfikowania urządzenia, na którym działa analizator.
- Szczegóły **zabezpieczeń punktu końcowego** zawierają ogólne informacje Ochrona punktu końcowego w usłudze Microsoft Defender związanych z procesami, w tym Program antywirusowy Microsoft Defender procesem czujnika. Jeśli ważne procesy nie są w trybie online zgodnie z oczekiwaniami, kolor zmieni się na czerwony.
  
-   Szczegóły **zabezpieczeń punktu końcowego** zawierają ogólne informacje Ochrona punktu końcowego w usłudze Microsoft Defender związanych z procesami, w tym Program antywirusowy Microsoft Defender procesem czujnika. Jeśli ważne procesy nie są w trybie online zgodnie z oczekiwaniami, kolor zmieni się na czerwony.

    :::image type="content" source="images/85f56004dc6bd1679c3d2c063e36cb80.png" alt-text="Strona Sprawdzanie wyników podsumowania" lightbox="images/85f56004dc6bd1679c3d2c063e36cb80.png":::

-   W **podsumowaniu sprawdź** wyniki będziesz mieć zagregowaną liczbę błędów, ostrzeżeń lub zdarzeń informacyjnych wykrytych przez analizatora.

-   W **szczegółowych wynikach** zostanie wyświetlona lista (posortowana według istotności) z wynikami i wskazówkami na podstawie obserwacji wykonanych przez analizatora.

## <a name="open-a-support-ticket-to-microsoft-and-include-the-analyzer-results"></a>Otwórz bilet pomocy technicznej do firmy Microsoft i dołącz wyniki analizatora

Aby uwzględnić pliki wyników analizatora [podczas](contact-support.md#open-a-service-request) otwierania biletu pomocy technicznej, użyj sekcji Załączniki  i uwzględnij `MDEClientAnalyzerResult.zip` plik:

:::image type="content" source="images/508c189656c3deb3b239daf811e33741.png" alt-text="Monit o załącznik" lightbox="images/508c189656c3deb3b239daf811e33741.png":::

> [!NOTE]
> Jeśli rozmiar pliku jest większy niż 25 MB, inżynier pomocy technicznej przydzielony do sprawy udostępni dedykowany bezpieczny obszar roboczy do przekazywania dużych plików do analizy.
