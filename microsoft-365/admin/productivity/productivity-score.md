---
title: Wynik produktywności firmy Microsoft
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
monikerRange: o365-worldwide
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
- MOE150
description: Dowiedz się, jak ocena produktywności firmy Microsoft odzwierciedla wyniki pomiarów osób i technologii oraz ich porównanie z organizacjami o podobnej wielkości.
ms.openlocfilehash: 24a84c3780ec3787b76f78acbe9c0c109a27c639
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327073"
---
# <a name="microsoft-productivity-score"></a>Wynik produktywności firmy Microsoft 

Wynik produktywności pomaga w przekształceniu cyfrowym dzięki szczegółowej informacji na temat sposobu, w jaki Twoja organizacja korzysta Microsoft 365 i technologii, które ją obsługują. Wyniki Twojej organizacji odzwierciedlają pomiary doświadczenia osób i technologii i mogą być porównywane z poziomami odniesienia organizacji o podobnej wielkości co Twoja.

Zapewniają:

- **Metryki** , które pomogą Ci zobaczyć, w którym miejscu jesteś na drodze cyfrowej transformacji.
- **Szczegółowe informacje** informacji o danych, które ułatwiają zidentyfikowanie możliwości zwiększających produktywność i zadowolenie w organizacji.
- **Zalecane działania**, które można podjąć, aby pomóc Twojej organizacji w efektywnym Microsoft 365 produktach.

Zapewniamy metryki, szczegółowe informacje i zalecenia w dwóch obszarach: 

- **Środowisko osób:** Określa sposób działania organizacji przy Microsoft 365, takich jak współpraca nad zawartością, mobilność, komunikacja, spotkania i praca zespołowa.  

    W przypadku każdej z wymienionych kategorii korzystamy z badań publicznych w celu określenia najlepszych rozwiązań i powiązanych korzyści w postaci skuteczności organizacyjnej. Na przykład badania Forrester pokazują, że gdy inne osoby współpracują i udostępniają zawartość w chmurze (zamiast wysyłać załączniki pocztą e-mail), mogą zaoszczędzić do 100 minut w tygodniu. Ponadto określenie wykorzystania tych najlepszych praktyk w Twojej organizacji jest określanie, w którym miejscu twoja organizacja się znajduje. 

- **Środowisko technologii:** Twoja organizacja zależy od niezawodnej i wydajnej technologii, a także od efektywnego wykorzystania Microsoft 365. [Analiza punktu](https://aka.ms/endpointanalytics) końcowego pomaga zrozumieć, jaki wpływ na twoją organizację mogą wpłynąć problemy z wydajnością i kondycją sprzętu i oprogramowania. Kondycja aplikacji platformy Microsoft 365 pomaga zrozumieć, czy na urządzeniach w Twojej organizacji są Microsoft 365 w polecanych kanałach.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby [uzyskać omówienie i szczegóły wymagań wstępnych](/mem/analytics/overview) , zobacz Co to jest analiza punktu końcowego. Aby dowiedzieć się więcej Microsoft 365 informacji o łączności sieciowej, przeczytaj [omówienie łączności sieciowej](../../enterprise/microsoft-365-networking-overview.md).

Aby dane dotyczące użytkowników obsługiły, potrzebny jest Microsoft 365 dla firm lub Office 365 dla subskrypcji enterprise. Aby uzyskać dane analizy punktu końcowego dla Twojej dzierżawy, musisz dodać Microsoft Intune do subskrypcji. Usługa Intune pomaga chronić dane twojej organizacji, zarządzając urządzeniami i aplikacjami. Po zainstalowaniu usługi Intune możesz włączyć analizę punktów końcowych w środowisku usługi Intune. Aby dowiedzieć się więcej Microsoft Intune na ten temat, zapoznaj się z Microsoft Intune [dokumentacją](/mem/intune/). 

> [!NOTE]
> Do uzyskania funkcji wyników produktywności nie jest wymagana licencja na usługę Workplace Analytics.

Wynik produktywności jest dostępny tylko w centrum administracyjne platformy Microsoft 365 i może być dostępny tylko dla informatyków, którzy pełnią jedną z następujących ról:  

- Administrator globalny
- Administratorzy serwera Exchange
- Administrator programu SharePoint
- Administrator programu Skype dla firm
- Administrator aplikacji Teams
- Czytnik globalny
- Czytelnik raportów
- Czytnik raportów podsumowujących użycie

> [!NOTE]
> Tylko specjalista IT z rolą administratora globalnego może utworzyć konto lub wybrać w dzierżawie ocenę produktywności.

Model kontroli dostępu oparty na rolach dla wyników produktywności ułatwia organizacjom dalsze przekształcanie cyfrowe w ramach programu Microsoft 365 dzięki elastyczności przypisywania ról informatykom w organizacji.

Firma Microsoft dba o ochronę prywatności użytkowników. W [tym dokumencie](privacy.md)  zachowania poufności informacji wyjaśniono kontrolki, które zapewniamy administratorowi IT w Twojej organizacji, aby zagwarantować, że dane będą możliwe do działania, bez naruszania zaufania, które umieszczasz w firmie Microsoft.

Dostęp do wyników można uzyskać z Administracja Microsoft 365 w obszarze **RaportyProductivity** >  Score.
  
## <a name="how-the-score-is-calculated"></a>Sposób obliczania wyniku

Twój wynik produktywności jest oparty na połączonych wynikach osób i technologii w kategoriach. Każda kategoria jest jednakowo ważona (łącznie wynosi 100 punktów). Najwyższa możliwa wartość wyników produktywności to 800.

### <a name="score-categories"></a>Kategorie wyników 

- Komunikacja (100 punktów)
- Spotkania (100 punktów)
- Współpraca nad zawartością (100 punktów)
- Praca zespołowa (100 punktów)
- Mobilność (100 punktów)
- Analiza punktu końcowego (100 punktów)
- Łączność sieciowa (100 punktów)
- Aplikacje Microsoft 365 kondycji (100 punktów)
- **Łącznie możliwe = 800 punktów**
 
W każdej kategorii wyników określamy znaczenie kluczowych wskaźników dla sposobu używania przez Twoją organizację Microsoft 365 w jej kierunku transformacji cyfrowej. Zapewniamy 28-dniowe i 180-dniowe widoki kluczowych działań. Oferujemy również metryki obsługi, które nie są częścią obliczeń wyników, ale są ważne, aby pomóc Ci w zidentyfikowaniu podstawowych statystyk użycia i konfiguracji, które możesz rozwiązać.

### <a name="products-included-in-productivity-score"></a>Produkty uwzględnione w ocenach produktywności 

Wynik produktywności obejmuje dane z Exchange, SharePoint, OneDrive, Teams, Word, Excel, PowerPoint, OneNote, Outlook, Yammer i Skype.

Wyniki organizacji są aktualizowane codziennie i odzwierciedlają akcje użytkowników wykonane w ostatnich 28 (w tym bieżącym dniu).

## <a name="interpreting-your-organizations-productivity-score"></a>Interpretowanie wyników organizacji dotyczącej produktywności 

Strona główna Wynik produktywności zawiera łączny wynik i historię wyników organizacji oraz podstawową analizę każdej kategorii.

:::image type="content" source="../../media/prodscore-landing.png" alt-text="Strona Wyników produktywności w raportach.":::

**Wynik organizacji jest wyświetlany** jako wartość procentowa i w punktach. Możesz zobaczyć punkty w liczniku oraz maksymalną możliwą liczbę punktów w mianowniku.

**Peer benchmarks** allow you to compare your organization's score with organization like yours. Peer benchmark for the people experiences categories is calculated as the average of measures within a set of similar organizations. Zestaw organizacji składa się z organizacji z Twojego regionu, które mają podobną liczbę licencjonowanych użytkowników, typy licencji, branżę i prawo Microsoft 365.

> [!NOTE]
> Firma Microsoft używa danych wewnętrznych do określenia branży, na która jest mapna organizacja. Dzierżawy w organizacji nadrzędnej są mapowane na tę samą branżę, co organizacja nadrzędna. Organizacje nie mogą wyświetlać ani modyfikować mapowań branży.

Punkt odniesienia do analizy punktów końcowych zawiera cele dotyczące wydajności uruchamiania urządzenia i zalecaną konfigurację oprogramowania opartą na zagregowanych wartościach mediany we wszystkich dzierżawach.

W przypadku łączności sieciowej zalecany punkt odniesienia wynosi 80 punktów.

Sekcja **Podział wyników zawiera** zestawienie wyników produktywności z punktami odniesienia według osób i obszarów doświadczenia technologicznego.

Historia wyników pokazuje, jak zmienił się twój wynik w poszczególnych kategoriach w ciągu ostatnich sześciu miesięcy.

Obszary **Środowisko osób i** **Technologia zawierają** podstawowe informacje o kategoriach w tych obszarach. Możesz wybrać każdą kategorię, aby wyświetlić bardziej szczegółowe informacje.

## <a name="category-details-pages"></a>Strony szczegółów kategorii

Strona szczegółów każdej kategorii zawiera podstawowe metryki szczegółowej i obsługi technicznej, a także pokrewne badania i działania, które można podjąć, aby wspierać zmiany w organizacji. Badania wspierają ważność i racracyjność podstawowych informacji dla każdej kategorii. Aby uzyskać więcej informacji, [przeczytaj raport Forrester](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE2PBrb).

Strony szczegółów są:
- [Współpraca nad zawartością — środowisko osób](content-collaboration.md)
- [Komunikacja — środowisko osób](communication.md)
- [Spotkania — środowisko osób](meetings.md)
- [Mobilność — środowisko osób](mobility.md)
- [Praca zespołowa — środowisko osób](teamwork.md)
- [Aplikacje Microsoft 365 kondycji — środowisko technologii](apps-health.md)
- [Analiza punktu końcowego](/mem/analytics/productivity-score)

## <a name="business-continuity-special-report"></a>Raport specjalny zapewnia ciągłość działania

Raport ciągłości działania to raport analizy pracy w ograniczonym czasie dostępny dla wszystkich klientów usługi Microsoft 365, aby pomóc im w prowadzenia organizacji w tym trudnym czasie.  

Ten raport pomaga organizacjom zrozumieć: 

- Zmiana na pracę zdalną wpływa na współpracę i komunikację. 

- Wpływ na równowagę między pracą a życiem prywatnym w zależności od dostosowania osób do pracy w domu. 

- Czy spotkania zdalne obsługują efektywne podejmowanie decyzji.

[Dowiedz się więcej o raporcie ciągłości działania firmy](/Workplace-Analytics/tutorials/bcrps)

[Dowiedz się więcej o aplikacji Microsoft Graph](/graph/)

> [!NOTE]
> Użytkownicy mają również możliwość uzyskania szczegółowych informacji o produktywności z [pulpitu nawigacyjnego do usługi MyAnalytics](/workplace-analytics/myanalytics/use/dashboard-2).


## <a name="we-want-to-hear-from-you"></a>Chcemy usłyszeć Od Ciebie

Podziel się swoimi pomysłami na temat wyników produktywności i pomysłami na to, jak je ulepszyć. Skorzystaj z **sekcji Opinii** w obrębie produktu i/lub kontaktuj się z zespołem do zespołu productivity score w prodscorefeedback@microsoft.com.

## <a name="related-content"></a>Zawartość pokrewna

[Monitorowanie Microsoft 365 za pomocą raportów](../../admin/activity-reports/activity-reports.md) (artykuł)\
[Włączanie Microsoft 365 użycia](../../admin/usage-analytics/enable-usage-analytics.md) (artykuł)\
[Omówienie centrum administracyjne platformy Microsoft 365](Omówienie centrum administracyjne platformy Microsoft 365](.. /admin-overview/admin-center-overview.md) (wideo)