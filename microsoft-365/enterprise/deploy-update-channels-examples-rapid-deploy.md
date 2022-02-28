---
title: Przykład szerokiego wdrożenia najnowszych wersji
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
ms.date: 07/21/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
ms.custom: ''
description: Sposób, w jaki organizacja wdrażaca najnowszą wersję korzysta z kanałów Windows 10 i Microsoft 365 aplikacji.
ms.openlocfilehash: 6b0226a226742a89dc65ca0d32792db03c77e465
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984988"
---
# <a name="example-of-broad-deployment-for-the-latest-releases"></a>Przykład szerokiego wdrożenia najnowszych wersji

Ten przykład konfiguracji kanału dotyczy organizacji, która w celu dopasowania do tych priorytetów biznesowych korzysta z szybkiego wdrażania najnowszych wersji:

- Zapewnij ciągłość działania aplikacji i usług firmy Microsoft.
- Maksymalizuj bezpieczeństwo urządzeń, usług i danych za pomocą najnowszych funkcji i poprawek od firmy Microsoft.
- Maksymalizuj produktywność użytkowników za pomocą najnowszych funkcji firmy Microsoft.

Te cele przekładają się na zadanie IT, czyli znalezienie równowagi między szybkim wdrożeniem produkcyjnym a wczesnym weryfikacją za pomocą reprezentatywnego podzestawu użytkowników i urządzeń w celu weryfikacji funkcjonalności przed wdrożeniem na szeroką skalę.

W naszej przykładowej organizacji jest 5000 pracowników w budynkich na całym świecie w Europie, Azja, Azji i Ameryce Północnej i Południowej. 70% pracowników korzysta z Microsoft 365 E3, a reszta organizacji korzysta z Microsoft 365 E5.

>[!Note]
>Ten przykład został zaprojektowany tak, aby pokazać, jak można używać etapów i grup wdrażania, które mogą działać dla organizacji o wielu typach i rozmiarach.
>

Infrastruktura it tej organizacji: 

- Jest w dużym stopniu wa, Windows, Aplikacje Microsoft 365 usług w chmurze firmy Microsoft stanowi 60% zainstalowanej bazy. Kilka starszych systemów pozostaje po dużej wieloletniej pracy nad uproszczeniem i usprawnieniu infrastruktury informatycznej.
- Jest utrzymywana przez wysoce doświadczony personel i ma za zadanie utrzymanie wydajności pracy i bezpieczeństwa użytkowników i ich urządzeń przez śledzenie potencjalnych użytkowników firmy Microsoft w ich wydaniach.

## <a name="deployment-and-update-stages"></a>Etapy wdrażania i aktualizacji

W zależności od celów wdrażania najnowszej wersji w tej przykładowej organizacji jest używany dwuetapowy proces wdrażania.

1. **Użyj wdrożenia w wersji zapoznawczej lub pilotażowej:** Sprawdzanie poprawności danych i iteratorów dla wczesnych użytkowników, personelu IT, użytkowników z konfiguracją reprezentacyjną i personelu szkoleniowego. 

   Wcześnie użytkownicy, personel IT, użytkownicy z konfiguracjami reprezentacyjni mogą sprawdzać funkcjonalność z innymi aplikacjami i na urządzeniach, zanim nowe funkcje będą dostępne w pozostałej części organizacji.

   Menedżerowie zmian mogą wcześniej zaglądać do nowych funkcji przed ich rozpowszechnienia. Mogą planować wiadomości i ich stosowanie.

   Pracownicy szkoleniowi mogą planować nowe kursy wewnętrzne lub aktualizować istniejące kursy dla nowych funkcji przed ich rozpowszechnienia.

2. **Wdrożenie produkcyjne:** Wdaj wszystkich pozostałych użytkowników według regionu, działu lub innej metody wdrażania.

## <a name="deployment-configuration-for-windows-10"></a>Konfiguracja wdrażania dla Windows 10

Ogólnym celem jest wykonanie szerokiego wdrożenia najnowszej wersji Semi-Annual kanału po weryfikacji kanału wersji zapoznawczej zmian wprowadzonych przez grupę reprezentatywnych użytkowników i ich urządzeń.

Zobacz [Windows 10 wdrażania](/windows/deployment/), aby uzyskać więcej informacji na Windows 10 metod i strategii wdrażania.

| Scena | Kanał | Grupa Wdrażania |
|:-------|:-------|:-----|
| Pilot |  **Kanał wersji zapoznawczej**  <ul><li>Zastosowanie: Wdrożenie aktualizacji funkcji dla personelu IT i wczesnych użytkowników na potrzeby weryfikacji na urządzeniach reprezentujących i konfiguracjach (językach, aplikacjach innych firm). </li><li> Stan: w pełni zgodne i obsługiwane dla klientów komercyjnych i nie są one wliczane do twoich umów pomocy technicznej. </li></ul> | **Win10ReleasePreviewChannel** (nazwa przykładowa) <br><br> Członkowie to grupy zawierające: <ul><li> Windows z różnych działów i lokalizacji </li><li> Personel z konfiguracjami, które wymagają sprawdzania poprawności </li><li> Administratorzy IT i personel wdrożeniowy IT </li><li> Zmień menedżerów </li><li> Wewnętrzny personel szkoleniowy </li></ul> |
| Produkcja |  **Półroczny kanał**  <ul><li>Cel: szerokie wdrożenie najnowszych aktualizacji funkcji dla pozostałych osób w organizacji. </li><li> Stan: w pełni zgodne i obsługiwane. </li></ul> | **Win10SemiAnnualChannel** (nazwa przykładowa) <br><br> Członkowie to wszyscy użytkownicy, którzy nie znajdują się w grupie Win10ReleasePreviewChannel. |
||||

W tej organizacji najlepiej jest wdrażać ład w kanale wersji zapoznawczej w taki sam sposób jak w przypadku wdrażania wersji Semi-Annual Channel, takich jak aktualizacja Windows czy Windows Server Update Services, i że w przypadku aktualizacji w obu kanałach zastosowano te same zasady.

Proces aktualizacji bieżących:

1. Zmiany kanału wersji zapoznawczej są wdrażane w grupie wdrożenia Win10ReleasePreviewChannel (nazwa przykładowa).
2. Członkowie grupy Win10ReleasePreviewChannel potwierdzają, że zmiany w kanale wersji Zapoznawczej dotyczą personelu wdrażania IT, który może przekazać opinię firmie Microsoft i poczekać na kolejne zmiany w kanale wersji zapoznawczej na dodatkowe sprawdzanie poprawności.
3. Semi-Annual zmiany funkcji kanału są wdrażane w grupie wdrożenia Win10SemiAnnualChannel. 

>[!Note]
>Mimo że kanał Semi-Annual jest zalecanym kanałem, dział IT powinien skorzystać z narzędzi do zarządzania i określić, kiedy wdrożyć najnowszą wersję kanału Semi-Annual w organizacji, a następnie wdrażać ją w falach.
>

## <a name="deployment-configuration-for-microsoft-365-apps"></a>Konfiguracja wdrażania dla Aplikacje Microsoft 365

Ogólnym celem jest wdrożenie szerokiego wdrożenia najnowszej wersji w bieżącym kanale po weryfikacji zmian w bieżącym kanale (wersja Preview) przez grupę użytkowników reprezentatywnych.

Zobacz [Aplikacje Microsoft 365 wdrażania](/deployoffice/plan-office-365-proplus), aby uzyskać więcej informacji Aplikacje Microsoft 365 metod i strategii wdrażania.

| Scena | Kanał | Grupa Wdrażania |
|:-------|:-------|:-----|
| Pilot |  **Bieżący kanał (wersja Preview)** <ul><li> Cel: {give a group of representative users sneakek of new Aplikacje Microsoft 365 features} Deployment of feature updates as soon as are tested with Current Channel (Preview) users and are production-ready. </li><li> Stan: w pełni zgodne i obsługiwane.</li><li> Jak często: Aktualizacje 2–3 razy w każdym miesiącu. </li></ul> | **AppsCurrentChannelPreview** (nazwa przykładu) <br><br> Członkowie to grupy zawierające: <ul><li> Office aplikacji dla różnych działów i lokalizacji </li><li> Personel z konfiguracjami, które wymagają sprawdzania poprawności </li><li> Administratorzy IT i personel wdrożeniowy IT </li><li> Zmień menedżerów </li><li> Wewnętrzny personel szkoleniowy </li></ul>|
| Produkcja | **Bieżący kanał** <ul><li> Cel: szerokie wdrożenie najnowszych aktualizacji funkcji dla pozostałych osób w organizacji. </li><li> Stan: w pełni zgodne i obsługiwane. </li></ul> |  **AppsCurrentChannel** (nazwa przykładowa) <br><br> Członkowie to wszyscy użytkownicy, którzy nie znajdują się w grupie AppsCurrentChannelPreview. |
|||

Proces aktualizacji bieżących:

1. Zmiany w bieżącym kanale (wersja Preview) są wdrażane w grupie wdrożenia AppsCurrentChannelPreview.
2. Członkowie grupy AppsCurrentChannelPreview potwierdzają, że zmiany w bieżącym kanale (wersja Preview) pracują dla pracowników wdrożeń IT, którzy mogą przekazać opinię firmie Microsoft i poczekać na następne wydanie bieżącego kanału (wersja Preview) na dodatkową weryfikację.
3. Zmiany w bieżącym kanale są wdrażane w grupie wdrażania AppsCurrentChannel. 

## <a name="visual-summary"></a>Podsumowanie wizualne

Poniżej znajdują się produkty, ich kanały i grupy wdrożeń używane przez tę przykładową organizację. 

![Grupy wdrażania służące do szerokiego wdrażania najnowszych wersji.](../media/deploy-update-channels-examples-rapid-deploy/group-summary.png)

## <a name="see-also"></a>Zobacz też

[Konfiguracje przykładowego wdrożenia i aktualizowania kanału](deploy-update-channels-examples.md)

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Przewodniki laboratorium testowego](m365-enterprise-test-lab-guides.md)