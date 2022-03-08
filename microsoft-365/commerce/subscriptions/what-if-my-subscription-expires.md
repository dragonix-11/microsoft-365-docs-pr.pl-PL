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
description: Dowiedz się, co się stanie z Twoimi danymi, gdy Microsoft 365 subskrypcji usługi dla firm wygaśnie, zostanie wyłączona lub jeśli ją anulujesz.
ms.date: 09/16/2021
ms.openlocfilehash: 8baebd55217dd5cd38228cca26a7504e5021f06b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322187"
---
# <a name="what-happens-to-my-data-and-access-when-my-microsoft-365-for-business-subscription-ends"></a>Co się stanie z moimi danymi i z moim dostępem po zakończeniu Microsoft 365 subskrypcji usługi dla firm?

Jeśli kończy się Twoja subskrypcja Microsoft 365 — wygasa lub postanawiasz ją anulować — Twój dostęp do usług, aplikacji i danych klienta przechodzi przez wiele stanów, zanim subskrypcja zostanie w pełni wyłączona lub *usunięta*. Jeśli wiesz o tym postępie, będziesz mieć lepsze umiejętności, aby przywrócić aktywny stan subskrypcji, zanim będzie za późno, lub — jeśli opuszczasz usługę Microsoft 365 — kopii zapasowej danych przed ich ostatecznym usunięciem.

Przeczytaj te ważne informacje przed kontaktem z [Microsoft 365 pomocy technicznej](../../admin/get-help-support.md).

> [!NOTE]
> W przypadku niektórych subskrypcji możesz anulować subskrypcję tylko przez ograniczony czas po zakupie lub odnowieniu subskrypcji. Jeśli okno anulowania już minęło, wyłącz rozliczanie cykliczne, aby anulować subskrypcję na koniec okresu jej zakończenia.
  
## <a name="what-happens-to-data-when-a-subscription-expires"></a>Co się dzieje z danymi po wygaśnięciu subskrypcji?

- Jeśli Twoja subskrypcja wygasa, przebiega ona przez następujące etapy: Wygasła / Wyłączona / Usunięta. Etap Wygasły rozpoczyna się natychmiast po dacie zakończenia subskrypcji.
- Jeśli wyłączysz rozliczenia cykliczne w twojej rocznej subskrypcji, będą to te same etapy, co w przypadku wygasłej subskrypcji. Rozpoczęcie pierwszego etapu to rocznica rocznej subskrypcji, która nie rozpoczyna się od dnia wyłączenia ustawienia rozliczeń cyklicznych subskrypcji.
- Jeśli anulujesz subskrypcję miesięczną, zostanie ona natychmiast wyłączona (w dniu anulowania). Oznacza to, że użytkownicy natychmiast Microsoft 365 dostęp do zasobów firmy i tylko administratorzy mają dostęp do danych przez następne 90 dni.

W poniższej tabeli wyjaśniono, czego można oczekiwać po wygaśnięciu Microsoft 365 dla firm.

| Aktywny | Wygasła <br/>(30 dni\*) | Wyłączone <br/>(90 dni\*) | Deleted |
|------------------------------------------------------------------------|------------------------------------------------------------------------------|------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| *Dane dostępne dla wszystkich*                                               | *Dane dostępne dla wszystkich*                                                     | *Dane dostępne tylko dla administratorów*                                             | **Dane usunięte<br/> Azure Active Directory są usuwane, jeśli nie są wykorzystywane przez inne usługi** |
| Użytkownicy mają normalny dostęp do Microsoft 365, plików i aplikacji   | Użytkownicy mają normalny dostęp do Microsoft 365, plików i aplikacji              | Użytkownicy nie mogą uzyskać dostępu Microsoft 365, plików ani aplikacji                        | Użytkownicy nie mogą uzyskać dostępu Microsoft 365, plików ani aplikacji                                     |
| Administratorzy mają normalny dostęp do Microsoft 365, danych i Office aplikacji | Administratorzy mogą uzyskać dostęp do centrum administracyjnego                                           | Administratorzy mogą uzyskać dostęp do centrum administracyjnego, ale nie mogą przypisywać licencji użytkownikom       | Administratorzy mogą uzyskać dostęp do centrum administracyjnego, aby kupić inne subskrypcje i zarządzać nimi             |
|                                                                        | Administratorzy globalni lub administratorzy rozliczeń mogą ponownie aktywować subskrypcję w centrum administracyjnym | Administratorzy globalni lub administratorzy rozliczeń mogą ponownie aktywować subskrypcję w centrum administracyjnym |                                                                                           |

*W przypadku większości ofert w większości krajów i regionów.
  
> [!NOTE]
>
> **Co to są "dane klienta"?** Dane klienta, zgodnie z definicją w warunkach świadczenia usług [online firmy Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=613649), odnoszą się do wszystkich danych, w tym do wszystkich plików tekstowych, dźwiękowych lub obrazów dostarczonych firmie Microsoft przez klienta lub w jego imieniu w ramach korzystania przez klienta z usług firmy Microsoft 365. Aby dowiedzieć się więcej o ochronie danych klientów, zobacz Wprowadzenie do [Portalu zaufania usług firmy Microsoft](../../compliance/get-started-with-service-trust-portal.md).

## <a name="what-happens-if-i-cancel-a-subscription"></a>Co się dzieje w przypadku anulowania subskrypcji?

Jeśli anulujesz subskrypcję przed datą zakończenia jej okresu, etap Wygasły zostanie pominięty i zostanie przeniesiony bezpośrednio do etapu Wyłączona, który dla większości subskrypcji w większości krajów i regionów wynosi 90 dni. Zalecamy, aby przed [](back-up-data-before-switching-plans.md) anulowaniem utworzyć kopię zapasową danych, ale jako administrator nadal możesz uzyskać dostęp do danych organizacji i utworzyć ich kopię zapasową, gdy jest to etap Wyłączony. Wszelkie pozostawione dane klienta mogą zostać usunięte po upływie 90 dni i zostaną usunięte nie później niż 180 dni po dniu anulowania.
  
Oto, czego możesz oczekiwać dla Ciebie i Twoich użytkowników w przypadku anulowania subskrypcji.
  
- **Dostęp administratora** Administratorzy nadal mogą logować się i korzystać z centrum administracyjnego oraz kupować inne subskrypcje zgodnie z potrzebami. Jako administrator globalny lub administrator rozliczeń masz 90 dni na [ponowne aktywowanie subskrypcji](reactivate-your-subscription.md) wraz ze wszystkimi nienaruszonymi danymi.

- **Dostęp użytkowników** Użytkownicy nie będą mogli korzystać z usług, takich jak OneDrive dla Firm, ani uzyskać dostępu do danych klientów — na przykład poczty e-mail lub dokumentów w witrynach  zespołu. Aplikacje pakietu Office, takie jak Word i Excel, przejdą w tryb tylko do odczytu o ograniczonej funkcjonalności i będą w nich wyświetlane [powiadomienia Produkt bez licencji](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380).

Aby dowiedzieć się, jak anulować, zobacz [Anulowanie subskrypcji](cancel-your-subscription.md).
  
> [!IMPORTANT]
> Jeśli chcesz, aby dane Twojej subskrypcji zostały usunięte przed końcem typowego etapu Wyłączenia, [możesz zamknąć swoje konto](../close-your-account.md).
  
> [!NOTE]
>
> Jeśli jawnie usuniesz subskrypcję, pomija ona etapy Wygasłe i Wyłączone oraz SharePoint i zawartość usługi Online, w tym OneDrive, są natychmiast usuwane.

## <a name="what-are-my-options-if-my-subscription-is-about-to-expire"></a>Jakie są opcje, jeśli moja subskrypcja nie będzie już wygasać?

Gdy subskrypcja jest aktywna, Ty i Twoi użytkownicy końcowi możecie mieć normalny dostęp do swoich danych, usług, takich jak poczta e-mail i OneDrive dla Firm oraz Office aplikacji. Jako administrator otrzymasz szereg powiadomień pocztą e-mail i w centrum administracyjnym, gdy zbliża się data wygaśnięcia subskrypcji.
  
Zanim subskrypcja faktycznie osiągnie datę wygaśnięcia, dostępnych jest kilka opcji:
  
- **Włącz rozliczenia cykliczne dla subskrypcji.**
  - Jeśli **Rozliczanie** cykliczne jest już włączone, nie musisz nic więcej zrobić. Subskrypcja jest rozliczana automatycznie i naliczana jest opłata za dodatkowy rok lub miesiąc, w zależności od bieżącej częstotliwości płatności. Jeśli z jakiegokolwiek powodu Rozliczanie cykliczne **jest wyłączone,** zawsze możesz ponownie włączyć Rozliczanie [cykliczne](renew-your-subscription.md).
  - Jeśli zakupiono subskrypcję Aplikacje Microsoft 365 dla firm kartą przedpłaconą, możesz włączyć Rozliczanie [cykliczne](renew-your-subscription.md) dla subskrypcji.
  - Jeśli jesteś klientem otwartego programu licencjonowania zbiorowego i masz przedpłaconą, jednoroczną subskrypcję, skontaktuj się ze swoim partnerem, aby kupić nowy klucz produktu. W centrum Volume Licensing Service Center otrzymasz instrukcje aktywowania klucza za pośrednictwem poczty [e-mail](https://go.microsoft.com/fwlink/p/?LinkID=282016). Aby dowiedzieć się, jak znaleźć nowego partnera lub partnera, z nim współpracowałeś w przeszłości, zobacz Znajdowanie [partnera lub odsprzedawcy](../../admin/manage/find-your-partner-or-reseller.md).
  - Jeśli masz Aplikacje Microsoft 365 dla firm, zobacz [Zarządzanie rozliczaniem cyklicznym subskrypcji](renew-your-subscription.md).
- **Poczekaj na wygaśnięcie subskrypcji.**
  - Jeśli płacisz za pomocą karty kredytowej lub faktury i nie chcesz kontynuować swojej subskrypcji, [wyłącz Rozliczanie cykliczne](renew-your-subscription.md). Twoja subskrypcja kończy się wraz z datą wygaśnięcia i możesz zignorować wszystkie powiązane powiadomienia e-mail.
  - Jeśli jesteś klientem otwartego programu licencjonowania zbiorowego i współpracujesz z partnerem, możesz pozwolić, aby Twoja subskrypcja wygasła, nie podejmowanie żadnych działań.
  - Jeśli jesteś klientem usługi Microsoft 365 Business Standard, który opłacono z góry za subskrypcję i aktywowano ją przy użyciu klucza produktu, możesz pozwolić, aby Twoja subskrypcja wygasła, nie podejmowanie żadnych działań.
- **Anulowanie przed wygaśnięciem subskrypcji.** Aby uzyskać szczegółowe informacje, [zobacz Anulowanie subskrypcji](cancel-your-subscription.md).

## <a name="what-happens-after-my-subscription-expires"></a>Co się dzieje po wygaśnięciu subskrypcji?

Jeśli subskrypcja wygaśnie, przechodzi przez wiele stanów, zanim zostanie ostatecznie usunięta. Dzięki temu, jako administrator, masz czas na ponowną aktywację, jeśli chcesz kontynuować usługę, lub na kopię zapasową danych, jeśli nie chcesz już mieć subskrypcji.
  
Oto, czego możesz się spodziewać, gdy Twoja subskrypcja znajduje się w każdym stanie.
  
### <a name="state-expired"></a>Stan: wygasła

**Czego można oczekiwać:** W przypadku większości subskrypcji, w tym subskrypcji kupionych za pośrednictwem programu [Microsoft Open](https://go.microsoft.com/fwlink/p/?LinkID=613298), w większości krajów i regionów etap Wygasła trwa 30 dni. W przypadku produktów licencjonowania zbiorowego, z wyjątkiem programu Microsoft Open, etap Wygasły trwa 90 dni.

W tym stanie użytkownicy mają normalny dostęp do portalu Microsoft 365, aplikacji Office i usług, takich jak poczta e-mail i SharePoint Online.
  
Jako administrator, nadal masz dostęp do centrum administracyjnego. Nie martw się — administratorzy globalni lub administratorzy rozliczeń mogą [ponownie aktywować](reactivate-your-subscription.md) subskrypcję i nadal korzystać z Microsoft 365. Jeśli nie aktywujesz jej ponownie, [zachówij swoje dane na kopii zapasowej](back-up-data-before-switching-plans.md).
  
### <a name="state-disabled"></a>Stan: Wyłączone

**Czego można oczekiwać:** Jeśli nie aktywujesz ponownie subskrypcji na etapie wygasłym, przechodzi ona do etapu Wyłączona, który dla większości subskrypcji w większości krajów i regionów trwa 90 dni. W przypadku produktów licencjonowania zbiorowego etap Wyłączony trwa 30 dni.

W tym stanie dostęp do sieci znacznie się zmniejsza. Użytkownicy nie mogą się zalogować ani korzystać z usług, takich jak poczta e-mail SharePoint online. Office aplikacje przejdą w tryb tylko do odczytu o ograniczonej funkcjonalności i będą w tych aplikacjach wyświetlane powiadomienia Produkt bez [licencji](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380). Nadal możesz zalogować się i przejść do centrum administracyjnego, ale nie możesz przypisywać licencji użytkownikom. Twoje dane klienta, w tym wszystkie dane użytkowników, wiadomości e-mail i pliki w witrynach  zespołu, są dostępne tylko dla Ciebie i innych administratorów.

Jako administrator globalny lub administrator rozliczeń, możesz ponownie [](reactivate-your-subscription.md) aktywować subskrypcję i nadal korzystać Microsoft 365 wszystkich danych klienta bez zmian. Jeśli nie zdecydujesz się na ponowną aktywację, [możesz wrócić do kopii zapasowej swoich danych](back-up-data-before-switching-plans.md).

### <a name="state-deleted"></a>Stan: Usunięto
  
**Czego można oczekiwać:** Jeśli nie aktywuj ponownie subskrypcji po jej wygaśnięciu lub wyłączeniu, subskrypcja zostanie usunięta.
  
Administratorzy i użytkownicy nie mają już dostępu do usług Office aplikacji w ramach subskrypcji. Wszystkie dane klienta — od danych użytkowników po dokumenty i wiadomości e-mail — są trwale usuwane i nie można ich usunąć.
  
W tym momencie nie można ponownie aktywować subskrypcji. Jednak jako administrator globalny lub administrator rozliczeń, nadal możesz uzyskać dostęp do centrum administracyjnego, aby zarządzać innymi subskrypcjami lub kupować nowe subskrypcje w celu zaspokojenia potrzeb biznesowych.
  
> [!NOTE]
>
> - Dodanie nowej subskrypcji tego samego typu, który został usunięty, nie powoduje przywrócenia danych, które były skojarzone z usuniętą subskrypcją.
> - Jeśli licencja usługi CSP zostanie zawieszona, nie ma 30-dniowego etapu wygasłego i usługi zostaną natychmiast wyłączone. Jeśli dzierżawa nie zostanie ponownie aktywowana przez dodanie nowej licencji, dane zostaną usunięte po 90 dniach.

### <a name="what-happens-when-my-trial-ends"></a>Co się dzieje po zakończeniu okresu próbnego?

Po zakończeniu okresu próbnego nie możesz dalej korzystać Microsoft 365 bezpłatnie. Dostępnych jest kilka opcji:

- **Kup Microsoft 365.** Gdy wersja próbna wygasa, przechodzi ona do etapu Wygasła, dając Ci 30 dni (dla większości wersji próbnych w większości krajów i regionów) na zakup Microsoft 365. Aby dowiedzieć się, jak przekształcić wersję próbną w płatną subskrypcję, zobacz [Kupowanie subskrypcji z bezpłatnej wersji próbnej](../try-or-buy-microsoft-365.md#buy-a-subscription-from-your-free-trial).
- **Przedłużenie okresu próbnego.** Potrzebujesz więcej czasu na ocenę platformy Microsoft 365? W niektórych przypadkach można przedłużyć [okres próbny](../extend-your-trial.md).
- **Anulowanie wersji próbnej lub pozwolić na jej wygaśnięcie.** Jeśli nie zdecydujesz się na zakup Microsoft 365, możesz pozwolić, aby wersja próbna wygasła lub [możesz ją anulować](cancel-your-subscription.md). Należy wrócić do kopii zapasowej wszystkich danych, które chcesz zachować. Wkrótce po 30-dniowym etapie wygaśnięcia informacje i dane konta wersji próbnej zostaną trwale usunięte.

> [!NOTE]
>
> Informacje na tej stronie podlegają zasadom zastrzeżenia i powiadomienia o zmianach [dotyczących zasad firmy Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=613651). Okresowo wracaj do tej witryny, aby przejrzeć wszelkie zmiany.

## <a name="related-content"></a>Zawartość pokrewna

[Anulowanie subskrypcji](./cancel-your-subscription.md) (artykuł)\
[Odnawianie Microsoft 365 dla firm](./renew-your-subscription.md) (artykuł)\
[Ponowne aktywowanie subskrypcji](./reactivate-your-subscription.md) (artykuł)
