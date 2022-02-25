---
title: Analiza niezawodności
description: ''
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 06e1446ca290439c9e6689f4461c825438cf6aaf
ms.sourcegitcommit: cebbdd393dcfd93ff43a1ab66ad70115853f83e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2021
ms.locfileid: "62959212"
---
# <a name="reliability-insights"></a>Analiza niezawodności

Ten widok zawiera podsumowanie kondycji urządzeń zarządzanych. Aby wyświetlić dane dotyczące niezawodności, wybierz **kartę Niezawodność** .


![Okienko niezawodności: niezawodność na różnych urządzeniach w lewym górnym rogu, wykres niezawodności w czasie w prawym górnym rogu, górna tabela problemów na dole. Przyciski Pomocy i opinii w prawym dolnym rogu.](../../media/insights_reliability.png)

Sekcja **Niezawodność** na różnych urządzeniach zawiera krótkie podsumowanie kondycji wdrożenia w ciągu ostatnich 14 dni, raportuje wartość procentową urządzeń uznanych za "w dobrej kondycji" i średni czas obserwowany od ostatniej zgłoszonej awarii. 

 
Wykres **Niezawodność w czasie po** prawej stronie raportuje liczbę urządzeń z błędami krytycznymi oraz łączną liczbę obserwowanych błędów krytycznych w czasie.

Sekcja **Najważniejsze problemy** zawiera szczegółowe informacje o wykrytych problemach, które wpływają na co najmniej 5% zarządzanych urządzeń. Zgłoszone szczegóły obejmują:

- Typ problemu
    - Awarie aplikacji, w których aplikacja przestaje działać lub nieoczekiwanie przestaje działać
    - Aplikacja zawiesza się, gdy aplikacja przestaje odpowiadać na dane wejściowe
    - Błędy krytyczne, które występują Windows przypadku wystąpienia problemu, którego nie można odzyskać
- Liczba urządzeń, na które wpływa ten sam problem
- Procent urządzeń zarządzanych, których liczba reprezentuje
- Całkowita liczba wystąpień konkretnego problemu
- Składnik oprogramowania, który wydaje się być źródłem problemu
- Kategoria wykrytego problemu:
    - Przeglądarka (Edge, Chrome, IE)
    - Nieznany (składniki innych niż firmy Microsoft)
    - Sterownik (audio, grafika lub inne sterowniki)
    - Productivity (Slack, G-Suites, Microsoft Office i jego dodatki lub rozszerzenia, Teams)
    - Multimedia (obraz, muzyka lub aplikacje wideo)
    - Zabezpieczenia (Windows składników zabezpieczeń)
- Bieżący stan operacji Microsoft Managed Desktop sprawdza i rekultywuje problem

