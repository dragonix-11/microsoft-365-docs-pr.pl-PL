---
title: Co się stanie z moimi danymi i z moim dostępem po zakończeniu subskrypcji?
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: jkinma, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid: MET150
description: 'Dowiedz się, co się stanie z Twoimi danymi, gdy subskrypcja usługi Microsoft 365 dla firm wygaśnie, zostanie wyłączona lub gdy ją anulujesz. '
ms.date: 09/16/2021
ms.openlocfilehash: 8baebd55217dd5cd38228cca26a7504e5021f06b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322187"
---
# <a name="what-happens-to-my-data-and-access-when-my-microsoft-365-for-business-subscription-ends"></a>Co się stanie z moimi danymi i z moim dostępem po zakończeniu subskrypcji usługi Microsoft 365 dla firm?

Gdy kończy się Twoja subskrypcja — wygasa lub postanawiasz ją anulować — Twój dostęp do aplikacji i usług Microsoft 365 i Twoje dane klienta przechodzą przez wiele stanów, zanim subskrypcja zostanie w pełni wyłączona lub *usunięta*. Wiedza, jak przebiega ten proces, umożliwi Ci przywrócenie aktywnego stanu subskrypcji, zanim będzie za późno, lub — jeśli opuszczasz usługę Microsoft 365 — wykonanie kopii zapasowych danych przed ich ostatecznym usunięciem.

Przeczytaj te ważne informacje przed skontaktowaniem się z [pomocą techniczną platformy Microsoft 365](../../admin/get-help-support.md).

> [!NOTE]
> W przypadku niektórych subskrypcji możesz anulować subskrypcję tylko przez ograniczony czas po zakupie lub odnowieniu subskrypcji. Jeśli termin anulowania już minął, wyłącz rozliczanie cykliczne, aby anulować subskrypcję na koniec okresu jej trwania.
  
## <a name="what-happens-to-data-when-a-subscription-expires"></a>Co się dzieje z danymi po wygaśnięciu subskrypcji?

- Jeśli Twoja subskrypcja wygasa, przechodzi ona przez następujące etapy: Wygasła / Wyłączona / Usunięta. Etap „Wygasła” rozpoczyna się natychmiast po dacie zakończenia subskrypcji.
- Jeśli wyłączysz rozliczenia cykliczne w Twojej rocznej subskrypcji, przejdzie ona przez te same etapy, co wygasła subskrypcja. Rozpoczęcie pierwszego etapu przypada po upływie roku jeśli chodzi o subskrypcję roczną. Nie rozpoczyna się on od dnia wyłączenia ustawienia rozliczeń cyklicznych subskrypcji.
- Jeśli anulujesz subskrypcję miesięczną, zostanie ona natychmiast wyłączona (w dniu anulowania). Oznacza to, że użytkownicy natychmiast utracą dostęp do zasobów platformy Microsoft 365 i tylko administratorzy będą mieli dostęp do danych przez następne 90 dni.

W poniższej tabeli wyjaśniono, czego można oczekiwać po wygaśnięciu płatnej subskrypcji platformy Microsoft 365 dla firm.

| Aktywny | Wygasła <br/>(30 dni\*) | Wyłączona <br/>(90 dni\*) | Deleted |
|------------------------------------------------------------------------|------------------------------------------------------------------------------|------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| *Dane dostępne dla wszystkich*                                               | *Dane dostępne dla wszystkich*                                                     | *Dane dostępne tylko dla administratorów*                                             | **Dane usunięte<br/> dla Azure Active Directory są usuwane, jeśli nie są wykorzystywane przez inne usługi** |
| Użytkownicy mają normalny dostęp do platformy Microsoft 365, plików i aplikacji   | Użytkownicy mają normalny dostęp do platformy Microsoft 365, plików i aplikacji              | Użytkownicy nie mogą uzyskać dostępu do platformy Microsoft 365, plików ani aplikacji                        | Użytkownicy nie mogą uzyskać dostępu do platformy Microsoft 365, plików ani aplikacji                                     |
| Administratorzy mają normalny dostęp do platformy Microsoft 365, danych i aplikacji pakietu Office | Administratorzy mogą uzyskać dostęp do centrum administracyjnego                                           | Administratorzy mogą uzyskać dostęp do centrum administracyjnego, ale nie mogą przypisywać licencji użytkownikom       | Administratorzy mogą uzyskać dostęp do centrum administracyjnego, aby kupić inne subskrypcje i zarządzać nimi             |
|                                                                        | Administratorzy globalni lub administratorzy rozliczeń mogą ponownie aktywować subskrypcję w centrum administracyjnym | Administratorzy globalni lub administratorzy rozliczeń mogą ponownie aktywować subskrypcję w centrum administracyjnym |                                                                                           |

*Obowiązuje w przypadku większości ofert w większości krajów i regionów.
  
> [!NOTE]
>
> **Co to są „dane klienta”?** Dane klienta, zgodnie z definicją w [warunkach świadczenia usług online firmy Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=613649), to wszystkie dane, w tym wszystkie pliki tekstowe, dźwiękowe lub obrazy, które są dostarczane do firmy Microsoft przez klienta lub w jego imieniu w ramach korzystania przez niego z usług Microsoft 365. Aby dowiedzieć się więcej na temat ochrony danych klientów, zobacz sekcję [Wprowadzenie do usługi Service Trust Portal firmy Microsoft](../../compliance/get-started-with-service-trust-portal.md).

## <a name="what-happens-if-i-cancel-a-subscription"></a>Co się dzieje w przypadku anulowania subskrypcji?

Jeśli anulujesz subskrypcję przed datą zakończenia okresu, to subskrypcja ta pominie stan „Wygasła” i zostanie przeniesiona bezpośrednio do stanu wyłączenia, który dla większości subskrypcji w większości krajów i regionów trwa 90 dni. Zalecamy, aby przed anulowaniem [utworzyć kopię zapasową danych](back-up-data-before-switching-plans.md), niemniej jednak jako administrator nadal możesz uzyskać dostęp do danych organizacji i utworzyć ich kopię zapasową, gdy subskrypcja znajduje się w etapie „Wyłączona”. Wszelkie pozostawione dane klienta mogą zostać usunięte po upływie 90 dni i zostaną usunięte nie później niż 180 dni po dniu anulowania.
  
Oto, czego może oczekiwać administrator i użytkownicy w przypadku anulowania subskrypcji. 
  
- **Dostęp administratora** Administratorzy nadal mogą logować się i korzystać z centrum administracyjnego oraz kupować inne subskrypcje zgodnie z potrzebami. Jako administrator globalny lub administrator rozliczeń masz 90 dni na [ponowne aktywowanie subskrypcji](reactivate-your-subscription.md) wraz ze wszystkimi nienaruszonymi danymi.

- **Dostęp użytkowników** Użytkownicy nie będą mogli korzystać z usług, takich jak OneDrive dla Firm, ani uzyskać dostępu do danych klientów — na przykład poczty e-mail lub dokumentów w witrynach zespołu. Aplikacje pakietu Office, takie jak Word i Excel, przejdą w tryb tylko do odczytu o ograniczonej funkcjonalności i będą w nich wyświetlane [powiadomienia Produkt bez licencji](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380).

Aby dowiedzieć się, jak anulować subskrypcję, zobacz sekcję[Anulowanie subskrypcji](cancel-your-subscription.md).
  
> [!IMPORTANT]
> Jeśli chcesz usunąć dane subskrypcji przed zakończeniem etapu „Wyłączona”, możesz [zamknąć konto](../close-your-account.md).
  
> [!NOTE]
>
> Jeśli kategorycznie usuniesz subskrypcję, pominie ona etapy „Wygasła” i „Wyłączona”, a dane programu SharePoint Online i zawartość, w tym OneDrive, zostaną natychmiast usunięte.

## <a name="what-are-my-options-if-my-subscription-is-about-to-expire"></a>Jakie są opcje, gdy zbliża się termin wygaśnięcia subskrypcji?

Gdy subskrypcja jest aktywna, Ty i Twoi użytkownicy końcowi macie normalny dostęp do danych, usług takich jak poczta e-mail i OneDrive dla Firm, oraz aplikacji pakietu Office. Jako administrator otrzymasz serię powiadomień pocztą e-mail i w centrum administracyjnym, gdy zbliża się data wygaśnięcia subskrypcji.
  
Zanim subskrypcja faktycznie osiągnie datę wygaśnięcia, dostępnych jest kilka opcji:
  
- **Włączenie rozliczania cyklicznego dla subskrypcji.**
  - Jeśli **rozliczanie cykliczne** jest już włączone, nie musisz podejmować żadnych działań. Twoja subskrypcja jest rozliczana automatycznie i opłaty są naliczane za dodatkowy rok lub miesiąc, w zależności od bieżącej częstotliwości płatności. Jeśli z jakiegoś powodu **rozliczanie cykliczne** zostało wyłączone, możesz zawsze [włączyć rozliczanie cykliczne](renew-your-subscription.md) raz jeszcze.
  - Jeśli zakup aplikacji Microsoft 365 dla firm został dokonany przy użyciu karty przedpłaty, możesz [włączyć Rozliczanie cykliczne](renew-your-subscription.md) dla swojej subskrypcji.
  - Jeśli jesteś klientem otwartego programu licencjonowania zbiorowego i korzystasz z przedpłaconej, rocznej subskrypcji, skontaktuj się ze swoim partnerem w celu zakupu nowego klucza produktu. Instrukcję aktywacji klucza otrzymasz pocztą e-mail w [Centrum usług licencjonowania zbiorowego](https://go.microsoft.com/fwlink/p/?LinkID=282016). Aby dowiedzieć się, jak znaleźć nowego partnera lub partnera, z którym współpracowano w przeszłości, zobacz [Znajdowanie partnera lub odsprzedawcy](../../admin/manage/find-your-partner-or-reseller.md).
  - Jeśli masz aplikacje Microsoft 365 dla firm, zobacz [Zarządzanie rozliczaniem cyklicznym w ramach subskrypcji](renew-your-subscription.md).
- **Pozwolenie na wygaśnięcie subskrypcji.**
  - Jeśli płacisz za pomocą karty kredytowej lub faktury i nie chcesz kontynuować swojej subskrypcji, [wyłącz Rozliczanie cykliczne](renew-your-subscription.md). Twoja subskrypcja kończy się wraz z datą wygaśnięcia i możesz zignorować wszystkie powiązane powiadomienia e-mail.
  - Jeśli jesteś klientem otwartego programu licencjonowania zbiorowego i współpracujesz z partnerem, możesz pozwolić, aby Twoja subskrypcja wygasła, nie podejmując żadnego działania.
  - Jeśli jesteś klientem usługi Microsoft 365 Business Standard, który opłacił subskrypcję z góry i aktywował ją przy użyciu klucza produktu, możesz pozwolić, aby Twoja subskrypcja wygasła bez podejmowania żadnych działań.
- **Anulowanie przed datą wygaśnięcia subskrypcji.** Aby uzyskać szczegółowe informacje, zobacz [Anulowanie subskrypcji](cancel-your-subscription.md).

## <a name="what-happens-after-my-subscription-expires"></a>Co się dzieje, gdy subskrypcja wygaśnie?

Jeśli subskrypcja wygaśnie, przechodzi przez wiele stanów, zanim zostanie ostatecznie usunięta. Dzięki temu, jako administrator masz czas na ponowną aktywację, jeśli chcesz kontynuować korzystanie z usługi lub na wykonanie kopii zapasowej danych, jeśli nie chcesz już korzystać z subskrypcji.
  
Oto, czego można oczekiwać w każdym stanie subskrypcji.
  
### <a name="state-expired"></a>Stan: wygasła

**Czego można oczekiwać:** Etap „Wygasła” trwa 30 dni dla większości subskrypcji, w tym subskrypcji zakupionych za pośrednictwem [Microsoft Open](https://go.microsoft.com/fwlink/p/?LinkID=613298), w większości krajów i regionów. W przypadku produktów licencjonowania zbiorowego, z wyjątkiem programu Microsoft Open, etap „Wygasła” trwa 90 dni.

W tym etapie użytkownicy mają normalny dostęp do portalu platformy Microsoft 365, aplikacji pakietu Office i usług, takich jak poczta e-mail i usługa SharePoint Online.
  
Jako administrator, nadal masz dostęp do centrum administracyjnego. Nie martw się — administratorzy globalni lub administratorzy rozliczeń mogą [ponownie aktywować](reactivate-your-subscription.md) subskrypcję i nadal korzystać z Microsoft 365. Jeśli nie aktywujesz subskrypcji ponownie, [wykonaj kopię zapasową danych](back-up-data-before-switching-plans.md).
  
### <a name="state-disabled"></a>Stan: wyłączona

**Czego można oczekiwać:** Jeśli nie aktywujesz ponownie subskrypcji na etapie wygasłym, przechodzi ona do etapu „Wyłączona”, który dla większości subskrypcji w większości krajów i regionów trwa 90 dni. W przypadku produktów licencjonowania zbiorowego etap „Wyłączona” trwa 30 dni.

W tym stanie dostęp do usług ulega znacznemu ograniczeniu. Użytkownicy nie mogą się logować ani uzyskiwać dostępu do usług, takich jak poczta e-mail lub usługa SharePoint Online. Aplikacje pakietu Office przejdą w tryb tylko do odczytu o ograniczonej funkcjonalności i będą w nich wyświetlane [powiadomienia Produkt bez licencji](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380). Nadal możesz zalogować się i przejść do centrum administracyjnego, ale nie możesz przypisywać licencji użytkownikom. Twoje dane klienta, w tym wszystkie dane użytkowników, poczta e-mail i pliki w witrynach zespołów, są dostępne wyłącznie dla Ciebie i innych administratorów.

Jako administrator globalny lub administrator rozliczeń, możesz[ponownie aktywować subskrypcję](reactivate-your-subscription.md) i nadal korzystać bez zmian z usługi Microsoft 365 oraz wszystkich danych klienta. Jeśli nie zdecydujesz się na ponowną aktywację, [utwórz kopię zapasową danych](back-up-data-before-switching-plans.md).

### <a name="state-deleted"></a>Stan: usunięta
  
**Czego można oczekiwać:** Jeśli nie aktywujesz ponownie subskrypcji po jej wygaśnięciu lub wyłączeniu, subskrypcja zostanie usunięta.
  
Administratorzy i użytkownicy nie mają już dostępu do usług ani aplikacji pakietu Office udostępnionych w ramach subskrypcji. Wszystkie dane klienta — od danych użytkowników po dokumenty i wiadomości e-mail — zostaną trwale i nieodwracalnie usunięte.
  
W tym momencie nie można ponownie aktywować subskrypcji. Jednak jako administrator globalny lub administrator rozliczeń, nadal możesz uzyskać dostęp do centrum administracyjnego, aby zarządzać innymi subskrypcjami lub kupować nowe subskrypcje w celu zaspokojenia potrzeb biznesowych.
  
> [!NOTE]
>
> - Dodanie nowej subskrypcji tego samego typu, która została usunięta, nie powoduje przywrócenia danych skojarzonych z usuniętą subskrypcją.
> - Jeśli licencja usługi CSP zostanie zawieszona, nie będzie obowiązywał 30-dniowy etap wygaśnięcia, a usługi zostaną natychmiast wyłączone. Jeśli dzierżawa nie zostanie ponownie aktywowana przez dodanie nowej licencji, dane zostaną usunięte po 90 dniach.

### <a name="what-happens-when-my-trial-ends"></a>Co się dzieje z chwilą wygaśnięcia mojej wersji próbnej?

Po zakończeniu okresu próbnego nie możesz bezpłatnie korzystać z platformy Microsoft 365. Dostępnych jest kilka opcji:

- **Kup Microsoft 365.** Gdy wersja próbna wygasa, przechodzi ona do etapu „Wygasła”, dając Ci 30 dni (dla większości wersji próbnych w większości krajów i regionów) na zakup Microsoft 365. Aby dowiedzieć się, jak przekształcić wersję próbną w płatną subskrypcję, zobacz [Kupowanie subskrypcji z bezpłatnej wersji próbnej](../try-or-buy-microsoft-365.md#buy-a-subscription-from-your-free-trial).
- **Przedłużenie okresu próbnego**. Potrzebujesz więcej czasu na ocenę platformy Microsoft 365? W niektórych przypadkach możesz [przedłużyć okres próbny](../extend-your-trial.md).
- **Anulowanie wersji próbnej lub pozwolenie na jej wygaśnięcie.** Jeśli nie zdecydujesz się na zakup usługi Microsoft 365, możesz pozwolić, aby wersja próbna wygasła lub możesz [ją anulować](cancel-your-subscription.md). Utwórz kopię zapasową wszystkich danych, które chcesz zachować. Wkrótce po 30-dniowym etapie wygaśnięcia informacje i dane konta wersji próbnej zostaną trwale usunięte.

> [!NOTE]
>
> Informacje podane na tej stronie podlegają zasadom określonym w [Zastrzeżeniu dotyczącym zasad firmy Microsoft oraz Powiadomieniu o zmianach](https://go.microsoft.com/fwlink/p/?LinkId=613651). Co jakiś czas wracaj do tej witryny, aby przejrzeć wszelkie zmiany.

## <a name="related-content"></a>Zawartość pokrewna

[Anulowanie subskrypcji](./cancel-your-subscription.md) (artykuł)\
[Odnowa subskrypcji platformy Microsoft 365 dla firm](./renew-your-subscription.md) (artykuł)\
[Ponowne aktywowanie subskrypcji](./reactivate-your-subscription.md) (artykuł)
