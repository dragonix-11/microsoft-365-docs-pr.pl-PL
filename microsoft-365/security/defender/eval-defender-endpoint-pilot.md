---
title: Pilotaż programu Microsoft Defender dla punktu końcowego
description: Dowiedz się, jak uruchomić pilotaż usługi Microsoft Defender for Endpoint(MDE), w tym jak zweryfikować grupę pilotażową i sprawdzić możliwości.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: v-jweston
author: jweston-1
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 4fff094b06dfa265f9fc44c568216582083ce1d9
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755467"
---
# <a name="pilot-microsoft-defender-for-endpoint"></a>Pilotaż programu Microsoft Defender dla punktu końcowego

Ten artykuł zawiera przewodnik po procesie uruchamiania pilotażu programu Microsoft Defender dla punktu końcowego. 

Aby skonfigurować pilotaż programu Microsoft Defender for Endpoint, należy wykonać poniższe czynności. 

:::image type="content" source="../../media/defender/m365-defender-endpoint-pilot-steps.png" alt-text="Procedura dodawania usługi Microsoft Defender for Identity do środowiska oceny usługi Microsoft Defender" lightbox="../../media/defender/m365-defender-endpoint-pilot-steps.png":::

- Krok nr 1. Zweryfikuj grupę pilotażową
- Krok nr 2. Wypróbuj możliwości

Podczas pilotażu programu Microsoft Defender dla punktu końcowego możesz zdecydować się na kilka urządzeń do usługi przed dodaniem do usługi całej organizacji.  

Następnie możesz wypróbować dostępne funkcje, takie jak przeprowadzanie symulacyjnych ataków i zobaczyć, jak program Defender for Endpoint pokazuje złośliwe działania i umożliwia przeprowadzanie wydajnej odpowiedzi. 

## <a name="step-1-verify-pilot-group"></a>Krok nr 1. Zweryfikuj grupę pilotażową
Po wykonaniu kroków dołączania opisanych w sekcji Włączanie [](eval-defender-endpoint-enable-eval.md) oceny urządzenia powinny być wymienione na liście Spis urządzeń mniej więcej po godzinie. 

Gdy zobaczysz urządzenia, które są już na swoim urządzeniu, możesz dalej korzystać z funkcji wypróbowania. 

## <a name="step-2-try-out-capabilities"></a>Krok nr 2. Wypróbuj możliwości
Po zakończeniu dołączania do usługi niektórych urządzeń i sprawdzeniu, że raportują one do usługi, zapoznaj się z produktem, wypisz zaawansowane funkcje, które są dostępne od razu.

W trakcie pilotażu możesz łatwo rozpocząć pracę z wypróbowaniem niektórych funkcji, aby zobaczyć produkt w działaniu bez konieczności skomplikowanych czynności konfiguracyjnych.

Zacznijmy od sprawdzenia pulpitów nawigacyjnych.

### <a name="view-the-device-inventory"></a>Wyświetlanie spisu urządzeń
W spisie urządzeń jest wyświetlona lista punktów końcowych, urządzeń sieciowych i urządzeń IoT w Twojej sieci. Udostępnia nie tylko widok urządzeń w Twojej sieci, ale również udostępnia szczegółowe informacje na ich temat, takie jak domena, poziom ryzyka, platforma systemu operacyjnego i inne szczegóły, aby ułatwić identyfikację najbardziej ryzykownych urządzeń.

### <a name="view-the-threat-and-vulnerability-management-dashboard"></a>Wyświetlanie pulpitu nawigacyjnego zarządzanie lukami w zabezpieczeniach i zagrożenia 
Zagrożenia i zarządzanie lukami w zabezpieczeniach pomagają skupić się na brakach, które stanowią najpilniejsze i największe ryzyko dla organizacji. Z pulpitu nawigacyjnego możesz uzyskać wysoki widok wyników ekspozycji w organizacji, wyników bezpiecznego działania firmy Microsoft dla urządzeń, rozpowszechniania informacji na urządzeniach, najlepszych zaleceń dotyczących zabezpieczeń, najbardziej narażonego oprogramowania, najlepszych działań naprawczych i najlepiej ujawnionych danych dotyczących urządzeń. 

### <a name="run-a-simulation"></a>Uruchamianie symulacyjnej
Program Microsoft Defender for Endpoint oferuje [scenariusze ataków "Zrób to samodzielnie"](https://securitycenter.windows.com/tutorials) , które można uruchomić na urządzeniach pilotażowych.  Każdy dokument zawiera informacje o systemach operacyjnych i wymaganiach aplikacji, a także szczegółowe instrukcje dotyczące scenariusza ataków. Te skrypty są bezpieczne, udokumentowane i łatwe w użyciu. Te scenariusze będą odzwierciedlać funkcje programu Defender dla punktu końcowego i będą przechodzić przez środowisko badania.

Aby uruchomić dowolną z podanych symulowań, potrzebujesz co najmniej [jednego urządzenia uruchamianego na urządzeniu.](../defender-endpoint/onboard-configure.md)

1. W **samouczkach** >  & **PomocySimulacji** wybierz jeden z dostępnych scenariuszy ataków, które chcesz symulować:

   - **Scenariusz 1. Dokument jest przenoszony przez backdoor** — symuluje dostarczanie dokumentu o przeznaczycie społecznościowym. W dokumencie jest uruchamiany specjalnie przygotowany backdoor, który zapewnia atakującym kontrolę.

   - **Scenariusz 2. Skrypt programu PowerShell** w atakach bez plików — symulowany jest atak bez pliku, który jest opierany na programie PowerShell, i pokazuje zmniejszenie powierzchni ataków i wykrywanie urządzeń wykrywania złośliwej aktywności pamięci.

   - **Scenariusz 3. Zautomatyzowane** reagowanie na incydenty — wyzwala zautomatyzowane badanie, które automatycznie wykrywa i rekultywuje artefakty naruszenia w celu skalowania wydajności reakcji na incydenty.

2. Pobierz i przeczytaj odpowiedni dokument instruktażowy odpowiedni dla wybranego scenariusza.

3. Pobierz plik symulacji lub skopiuj skrypt symulacji, przechodząc do części **HelpSimulations** >  & samouczków. Możesz pobrać plik lub skrypt na urządzenie testowe, ale nie jest to obowiązkowe.

4. Uruchom plik symulacyjnej lub skrypt na urządzeniu testowym zgodnie z instrukcjami w dokumencie instruktażu.

> [!NOTE]
> Pliki symulacyjne lub skrypty symulowają działania ataków, ale w rzeczywistości są wyszkodliwe i nie będą uszkodzić ani nie łamania urządzenia testowego.

## <a name="next-steps"></a>Następne kroki
[Ocenianie usługi Microsoft Defender dla aplikacji w chmurze](eval-defender-mcas-overview.md)

Powrót do omówieniem [Szacowanie programu Microsoft Defender dla punktu końcowego](eval-defender-endpoint-overview.md)

Wróć do przeglądu projektów [oceniania i Microsoft 365 Defender](eval-overview.md)
