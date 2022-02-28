---
title: Wdrażanie przepisów dotyczących ochrony danych osobowych za pomocą aplikacji Microsoft 365
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/22/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-overview
ms.custom: admindeeplinkCOMPLIANCE
description: Skonfiguruj ochronę informacji w programie Microsoft 365 na temat przepisów o ochronie prywatności danych, takich jak RODO i California Consumer Privacy Act (POCHA), w tym Microsoft Teams, SharePoint i poczty e-mail.
ms.openlocfilehash: 92314529cf6ca3ec318b181eb367bab81b9b81a0
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990505"
---
# <a name="deploy-information-protection-for-data-privacy-regulations-with-microsoft-365"></a>Wdrażanie przepisów dotyczących ochrony danych osobowych za pomocą aplikacji Microsoft 365

Twoja organizacja może podlegać regionalnym regulacjom dotyczącym prywatności danych, które wymagają ochrony i zarządzania prawami oraz możliwością kontroli nad informacjami osobistymi przechowywanymi w infrastrukturze informatycznej, w tym zarówno lokalnym, jak i w chmurze. Najlepszym przykładem rozporządzenia o ochronie prywatności danych jest Ogólne Rozporządzenie o Ochronie Danych (RODO) Unii Europejskiej. Niezastosowanie się do przepisów o ochronie prywatności danych może spowodować poważne konsekwencje.

Przykładowe typy danych w programach Microsoft 365 obejmują sesje czatu w programach Microsoft Teams, wiadomości e-mail Exchange wiadomości e-mail oraz pliki w SharePoint i OneDrive. To rozwiązanie zawiera wskazówki dotyczące oceny ryzyka i podjęcia odpowiednich działań w celu ochrony danych osobowych w Microsoft 365. Obejmuje to identyfikowanie informacji osobistych w celu ochrony i reagowania na incydenty dotyczące prywatności danych, a także zarządzania tym incydentami.

![Co to jest ochrona informacji w przypadku przepisów o ochronie prywatności danych.](../media/information-protection-deploy/information-protection-data-privacy-regulations-overview.png#lightbox)

Podano też dodatkowe informacje dotyczące korzystania z funkcji kontroli Microsoft 365, urządzeń i zagrożeń w celu ochrony prywatności danych.

Obejrzyj ten klip wideo, aby uzyskać omówienie procesu wdrażania.
<br>
<br>
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4NHCQ]

Te Microsoft 365 funkcje pomagają spełnić kryteria ochrony informacji.

| Funkcja lub funkcja | Opis | Licencjonowanie |
|:-------|:-----|:-------|
| Menedżer zgodności | Zarządzaj działaniami zgodności z przepisami, uzyskaj ogólną ocenę bieżącej konfiguracji zgodności i znajdź zalecenia dotyczące ulepszeń. Jest to narzędzie do oceny ryzyka oparte na przepływie pracy w Centrum zgodności platformy Microsoft 365. | Microsoft 365 E3 i E5 |
| Usługa Microsoft Defender dla Office 365 | Chroń swoje Microsoft 365 i dane— takie jak wiadomości e-mail, dokumenty Office i narzędzia do współpracy — przed atakami. | Microsoft 365 E3 i E5 |
| Etykiety wrażliwości | Klasyfikowanie i chronienie danych organizacji bez utrudniania użytkownikom produktywności i możliwości współpracy. Umieszczaj etykiety na różnych poziomach ochrony w wiadomościach e-mail, plikach i witrynach. | Microsoft 365 E3 i E5 |
| Ochrona przed utratą danych (DLP) | Wykrywaj, ostrzegaj i blokuj ryzykowne, przypadkowe lub nieodpowiednie udostępnianie danych zawierających informacje osobiste zarówno wewnątrz, jak i na zewnątrz. | Microsoft 365 E3 i E5 |
| Zasady i etykiety przechowywania danych | Wdrażanie kontroli zarządzania informacjami. Mogą one obejmować określanie, jak długo mają być przechowywać dane (na przykład dane osobowe klientów) zgodnie z zasadami organizacji lub przepisami dotyczącymi danych. | Microsoft 365 E3 i E5 |
| Szyfrowanie wiadomości e-mail | Ochrona danych osobowych przez wysyłanie i odbieranie zaszyfrowanych wiadomości e-mail między osobami w organizacji i poza nią. | Microsoft 365 E3 i E5 |
||||

## <a name="organization-of-the-guidance-in-this-solution"></a>Organizacja wskazówek dotyczących tego rozwiązania

Aby ułatwić zrozumienie dostępnych narzędzi Microsoft 365 w celu spełnienia jednego lub większej liczby przepisów związanych z prywatnością, te wskazówki są podzielone na sekcje.

![Kroki wdrażania ochrony informacji w celu ochrony danych osobowych.](../media/information-protection-deploy/information-protection-data-privacy-regulations-steps.png)

Każda z tych sekcji odpowiada osobnemu artykułowi w tym rozwiązaniu.

> [!NOTE]
> Jeśli znasz już obowiązki w zakresie ochrony prywatności danych i są one wykonywane na istniejącym planie, możesz skupić się na wskazówkach Zapobiegaj, Chroń, Zachowaj i Zbadaj.

> [!IMPORTANT]
> Użycie się do tych wskazówek nie musi oznaczać zgodności z każdym rozporządzeniem o ochronie prywatności danych, zwłaszcza pod uwagę liczbę kroków wymaganych poza kontekstem tych funkcji. Użytkownik jest odpowiedzialny za zapewnienie zgodności z przepisami oraz skonsultowanie się ze swoimi zespołami ds. prawnych i zgodności z przepisami lub szukanie wskazówek i porad ze strony innych firm, które nie będą zgodne ze standardami.

## <a name="plan-assess-data-privacy-risks-and-identify-sensitive-items"></a>Plan: ocenianie zagrożeń związanych z prywatnością danych i identyfikowanie elementów poufnych

Ocena przepisów dotyczących prywatności danych i zagrożeń, których podlega Twoja organizacja, jest pierwszym krokiem do wykonania przed rozpoczęciem wdrażania ulepszeń, na przykład konfigurowania funkcji w Microsoft 365. Te prace mogą obejmować ogólną ocenę gotowości lub identyfikację określonych typów informacji poufnych, które podlegają mechanizmom kontroli prawnej, których musi przestrzegać Twoja organizacja.

Aby uzyskać więcej informacji, zobacz [Ocenianie zagrożeń związanych z prywatnością danych i identyfikowanie elementów poufnych](information-protection-deploy-assess.md).

## <a name="track-run-risk-assessments-and-check-your-compliance-score"></a>Śledzenie: przeprowadzanie oceny ryzyka i sprawdzanie wyniku zgodności

Menedżer zgodności, dostępny w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365, zapewnia</a> wbudowaną możliwość śledzenia działań udoskonalania i zarządzania nimi w ogólnym zakresie, a także działań związanych z wieloma przepisami dotyczącymi prywatności danych, które mają zastosowanie do Ciebie.

Można korzystać z wbudowanych szablonów oceniania, które są specyficzne dla poszczególnych przepisów, w których można śledzić czynności do poszczególnych szablonów oceniań, a także wyświetlać określone mechanizmy kontroli prawnej i powiązać je z określonymi działaniami.

Aby uzyskać więcej informacji, zobacz [Zarządzanie działaniami udoskonalania za pomocą Menedżera zgodności](information-protection-deploy-compliance.md).

## <a name="prevent-protect-personal-data"></a>Zapobieganie: Ochrona danych osobowych

Microsoft 365 funkcje tożsamości, urządzenia i ochrony przed zagrożeniami, których można użyć w celu zapewnienia zgodności z przepisami dotyczącymi prywatności danych.

Aby uzyskać więcej informacji, zobacz [Korzystanie z ochrony tożsamości, urządzenia i zagrożeń na podstawie przepisów dotyczących prywatności danych](information-protection-deploy-identity-device-threat.md).

W tym artykule krótko opisano zasady ochrony prywatności danych w tych obszarach oraz przedstawiono listę powiązanych rozwiązań Microsoft 365 oraz linki do dodatkowych informacji, które pomogą Ci w rozwiązaniu wszelkich wymagań implementacji.

## <a name="protect-information-subject-to-data-privacy-regulation"></a>Ochrona informacji podlegających rozporządzeniem o ochronie prywatności danych

Przepisy dotyczące ochrony prywatności danych określają szereg kontrolek ochrony informacji osobistych, które mogą być stosowane w Twoim środowisku, w tym ponad 40 kontrolek ochrony informacji w ramach tylko czterech przepisów dotyczących prywatności danych owanych w naszym przykładowym zestawie RODO, California Consumer Protection Act (HIPAA), HIPAA-HITECH (United States Health Care Privacy Act) oraz brazylijskiej ustawy o ochronie danych (LGPD).

Aby uzyskać więcej informacji, zobacz [Ochrona informacji podlegających rozporządzeniem o ochronie prywatności danych w Twojej organizacji](information-protection-deploy-protect-information.md).

W tym artykule są podane główne schematy kontroli, których można użyć w celu zaspokojenia potrzeb w zakresie ochrony informacji w celu ochrony prywatności danych w organizacji.

## <a name="retain-govern-information-subject-to-data-privacy-regulation"></a>Zachowanie: reguluj informacje objęte przepisami o ochronie prywatności danych

Przepisy dotyczące prywatności danych nazywają się mechanizmami kontroli zarządzania informacjami osobistymi, które mogą być stosowane w Twoim środowisku, w tym ponad 24 mechanizmy kontroli nad czterema przepisami dotyczącymi prywatności danych w naszym przykładowym zestawie rodo, HIPAA, HIPAA-HITECH i LGPD.

Aby uzyskać więcej informacji, zobacz [Temat informacji podlegających rozporządzeniem o ochronie prywatności danych w Twojej organizacji](information-protection-deploy-govern.md).

&mdash;Mimo że przepisy dotyczące prywatności danych mogą być niejasne w zakresie zarządzania informacjami, takich jak celowe przechowywanie,&mdash; usuwanie i archiwizowanie, w tym artykule wskazany jest podstawowy schemat kontroli, który umożliwia korzystanie z zasad zarządzania informacjami w celu ochrony prywatności danych w organizacji.

## <a name="investigate-monitor-investigate-and-respond-to-data-privacy-incidents"></a>Badanie: Monitorowanie i badanie zdarzeń dotyczących prywatności danych oraz odpowiadanie na nie

Dostępne są Microsoft 365, które ułatwiają monitorowanie i badanie zdarzeń związanych z prywatnością danych oraz reagowanie na nie w ramach organizacji w ramach operacyjnych funkcji pokrewnych.

Posiadanie procesów, procedur i innej dokumentacji dotyczącej korzystania z tych funkcji może być ważne w celu przedstawiania zgodności z przepisami organom regulacyjną.

Aby uzyskać więcej informacji, zobacz [Monitorowanie zdarzeń dotyczących prywatności danych](information-protection-deploy-monitor-respond.md) i odpowiadanie na nie w organizacji.

## <a name="training-for-administrators"></a>Szkolenia dla administratorów

Te moduły szkoleniowe w witrynie Microsoft Learn ułatwiają poznanie możliwości ważnych dla ochrony informacji.


#### <a name="information-protection"></a>Ochrona informacji

|Szkolenie:|Ochrona informacji przedsiębiorstwa za pomocą Microsoft 365|
|:---|:---|
|![Teams do szkolenia na temat ochrony informacji.](../media/protect-enterprise-information-microsoft-365.svg)|Ochrona i zabezpieczanie informacji organizacji jest trudnym zadaniem niż kiedykolwiek wcześniej. W ścieżce nauki Ochrona informacji przedsiębiorstwa za pomocą etykiet Microsoft 365 omówiono, jak chronić poufne informacje przed przypadkowym usunięciem lub błędem, odnajdować i klasyfikować dane, jak je chronić etykietami wrażliwości, jak monitorować i analizować informacje poufne, aby chronić je przed ich utratą. Ta ścieżka nauki może ułatwić Ci przygotowanie się do Microsoft 365 certyfikatu: skojarzeń administratora zabezpieczeń i Microsoft 365 certyfikowanych: Enterprise certyfikacji dla specjalistów administracji.<br><br>1 godz. — ścieżka Edukacja - 5 modułów|

> [!div class="nextstepaction"]
> [Rozpoczynanie >](/learn/modules/m365-security-info-overview/introduction/)

#### <a name="identity-and-access"></a>Tożsamość i dostęp

|Szkolenie:|Ochrona tożsamości i dostępu za pomocą Azure Active Directory|
|:---|:---|
|![Ikona szkolenia w zakresie tożsamości i dostępu.](../media/protect-identity-and-access-with-microsoft-365.svg)|Ścieżka nauki Tożsamości i programu Access obejmuje najnowsze technologie tożsamości i dostępu, narzędzia do wzmacniania uwierzytelniania oraz wskazówki dotyczące ochrony tożsamości w organizacji. Technologie dostępu i tożsamości firmy Microsoft umożliwiają zabezpieczanie tożsamości organizacji (zarówno lokalnie, jak i w chmurze) oraz zapewnianie użytkownikom możliwości bezpiecznej pracy z dowolnego miejsca. Ta ścieżka nauki może ułatwić Ci przygotowanie się do Microsoft 365 certyfikatu: skojarzeń administratora zabezpieczeń i Microsoft 365 certyfikowanych: Enterprise certyfikacji eksperta administracji.<br><br>2 godz. 52 min - ścieżka Edukacja - 6 modułów|

> [!div class="nextstepaction"]
> [Rozpoczynanie >](/learn/modules/m365-identity-overview/introduction/)