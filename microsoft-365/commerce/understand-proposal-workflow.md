---
title: Omówienie przepływu pracy propozycji
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: presharm, jmueller
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_purchase
- AdminSurgePortfolio
search.appverid: MET150
description: Dowiedz się więcej o propozycjach ułatwiających zakup produktów i usług firmy Microsoft.
ROBOTS: NOINDEX
ms.date: 04/28/2022
ms.openlocfilehash: e54b68b5090287d7a61e9dea70726b7ec9e83c72
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66485984"
---
# <a name="understand-the-microsoft-proposal-workflow"></a>Omówienie przepływu pracy propozycji firmy Microsoft

Propozycja jest formalną ofertą firmy Microsoft dla Twojej organizacji w celu zakupu produktów i usług firmy Microsoft. Pracujesz bezpośrednio z przedstawicielem firmy Microsoft, aby określić określone produkty, usługi i warunki swojej propozycji.

Przedstawiciel firmy Microsoft opracowuje propozycję zawierającą omówione przez Ciebie i Twojego przedstawiciela elementy. Przedstawiciel wysyła wiadomość e-mail z linkiem do witryny Azure Marketplace Portal. Witryna zawiera propozycję przygotowaną specjalnie dla Ciebie i Twojej organizacji.

Po otrzymaniu wiadomości e-mail z powiadomieniem postępuj zgodnie z linkiem do witryny propozycji. Po zalogowaniu się do witryny możesz rozpocząć proces przeglądu propozycji.

## <a name="prerequisites-for-buying-items-with-a-proposal"></a>Wymagania wstępne dotyczące kupowania przedmiotów z propozycją

Aby można było kupić elementy na potrzeby propozycji, musisz mieć konto rozliczeniowe i umowę z firmą Microsoft.

### <a name="billing-account"></a>Konto rozliczeniowe

Konto rozliczeniowe służy do zarządzania ustawieniami konta, fakturami, profilami rozliczeniowymi oraz produktami i usługami. Jeśli nie masz jeszcze konta rozliczeniowego, przedstawiciel firmy Microsoft utworze je dla Ciebie. W przeciwnym razie korzystają z istniejącego konta rozliczeniowego dla Twojej organizacji, o ile masz uprawnienia do korzystania z tego konta rozliczeniowego.

Uprawnienia konta rozliczeniowego są zarządzane przez właściciela konta rozliczeniowego. Administratorzy globalni mogą przypisywać się do roli właściciela konta rozliczeniowego, a następnie tworzyć innych użytkowników rozliczeń właścicieli kont.

Aby uzyskać więcej informacji na temat kont rozliczeniowych, zobacz [Zarządzanie kontami rozliczeniowymi](manage-billing-accounts.md).

### <a name="microsoft-customer-agreement"></a>Umowa z Klientem Microsoft

Umowa z Klientem Microsoft (MCA) umożliwia organizacji kupowanie produktów i usług firmy Microsoft. Aby uzyskać więcej informacji, zobacz [Umowa z Klientem Microsoft](https://www.microsoft.com/Licensing/how-to-buy/microsoft-customer-agreement).

## <a name="permissions-needed-to-sign-an-agreement-or-pay-for-items"></a>Uprawnienia wymagane do podpisania umowy lub płacenia za elementy

Aby pomyślnie podpisać umowę lub kupić produkty i usługi, musisz być właścicielem konta rozliczeniowego lub współautorem konta rozliczeniowego. Jeśli jesteś administratorem globalnym, ale nie masz jednej z tych ról, możesz przypisać role do siebie. Jeśli nie jesteś administratorem globalnym, poproś administratora globalnego lub właściciela konta rozliczeniowego o przypisanie ci jednej z ról.

Role właściciela konta rozliczeniowego i współautora konta rozliczeniowego są przypisywane przy użyciu jednej z następujących metod.

### <a name="assign-roles-in-the-microsoft-365-admin-center"></a>Przypisywanie ról w Centrum administracyjne platformy Microsoft 365

1. W Centrum administracyjne platformy Microsoft 365 przejdź do  >  strony<a href="https://go.microsoft.com/fwlink/p/?linkid=2084771" target="_blank">Rozliczenia kont rozliczeniowych</a>.
2. Na stronie **Konta rozliczeniowe** w sekcji **Role konta rozliczeniowego** wybierz pozycję **Przypisz role**.
3. W okienku **Przypisywanie ról** wyszukaj imię i nazwisko osoby, do której chcesz przypisać rolę.
4. Zaznacz pole dla nazwy roli, którą ma mieć dana osoba, a następnie wybierz pozycję **Przypisz**.

### <a name="assign-roles-in-the-azure-portal"></a>Przypisywanie ról w Azure Portal

1. W Azure Portal przejdź do strony <a href="https://portal.azure.com/#blade/Microsoft_Azure_GTM/ModernBillingMenuBlade/Overview" target="_blank">Kontrola dostępu (IAM</a>).
2. Na stronie **Kontrola dostępu (IAM)** wybierz pozycję **Dodaj**.
3. W okienku **Dodawanie uprawnień** wybierz **rolę, która** ma zostać przypisana do użytkownika.
4. Wybierz użytkownika, a następnie wybierz pozycję **Zapisz**.

Aby uzyskać więcej informacji na temat ról konta rozliczeniowego, zobacz [Omówienie dostępu do kont rozliczeniowych](manage-billing-accounts.md#understand-access-to-billing-accounts).

Jeśli jest to nowe konto rozliczeniowe i nikt nie zaakceptował umowy, automatycznie stajesz się właścicielem konta rozliczeniowego, pod warunkiem, że:

- Czy osoba wymieniona w propozycji **lub**
- Jesteś już [administratorem globalnym usługi Azure Active Directory](/azure/active-directory/roles/permissions-reference#global-administrator) dla twojej organizacji

## <a name="what-is-the-overall-workflow"></a>Jaki jest ogólny przepływ pracy?

Ogólny przepływ pracy propozycji wygląda następująco:

- Przedstawiciel firmy Microsoft tworzy propozycję i wysyła do Ciebie link w wiadomości e-mail.
- Użyj linku, aby przejść do strony logowania propozycji.
- Przejrzyj informacje organizacji.
- Przejrzyj propozycję, zaakceptuj umowę MCA w razie potrzeby i zakończ proces wyewidencjonowania.
  > [!IMPORTANT]
  > Musisz mieć uprawnienia do podpisania umowy MCA w imieniu swojej organizacji. Jeśli nie masz tego autorytetu, to ktoś, kto to robi, musi wykonać ten krok.
- Po zakończeniu wyewidencjonowania otrzymasz dodatkowe linki do konfigurowania produktów i usług.

## <a name="proposal-terms"></a>Terminy propozycji

Poniższa tabela zawiera terminy i definicje, które pojawiają się w propozycji i w witrynie propozycji.

| Okres | Definicja |
|---|---|
| Konto rozliczeniowe | Konto używane do zarządzania ustawieniami konta, fakturami, formami płatności i produktami. |
| Profil rozliczeniowy | Informacje o organizacji, które umożliwiają dostosowywanie elementów zawartych na fakturze oraz sposobu płacenia za faktury. Profil rozliczeniowy zawiera nazwę konta rozliczeniowego, formy płatności używane dla określonego profilu rozliczeniowego, informacje kontaktowe, ustawienia faktury i uprawnienia, które umożliwiają zmianę profilu rozliczeniowego, płacenie rachunków oraz kupowanie produktów i usług. |
| Istniejące umowy | Każda umowa zawarta już z firmą Microsoft przez Twoją organizację. Może to obejmować między innymi Enterprise Agreement, umowę o świadczenie usług & produktów firmy Microsoft lub Umowa z Klientem Microsoft. |
| Umowa z Klientem Microsoft (MCA) | Umowa określająca warunki i postanowienia konta posiadanego przez organizację z firmą Microsoft. |
| Przedstawiciel firmy Microsoft | Autoryzowany przedstawiciel firmy Microsoft, który przygotowuje propozycję dla Ciebie i Twojej organizacji. |
| Organizacji | Jednostka prawna, która korzysta z produktów, technologii lub usług firmy Microsoft. |
| Przygotowane przez | Adres e-mail przedstawiciela firmy Microsoft, który przygotował propozycję. |
| Terminy uzupełniające | Poprawki umowy MCA zawierające terminy specyficzne dla Twojej organizacji. Aby zaakceptować warunki uzupełniające, należy użyć programu DocuSign do zarejestrowania podpisu elektronicznego. |

## <a name="step-1-review-organization-information"></a>Krok 1. Przeglądanie informacji o organizacji

Po zalogowaniu się najpierw przejrzyj informacje organizacji.

### <a name="your-organization"></a>Twoja organizacja

W sekcji **Twoja organizacja** zostanie wyświetlone skojarzone z nim konto rozliczeniowe. Informacje o koncie rozliczeniowym są pobierane z istniejącego konta rozliczeniowego lub tworzone przez przedstawiciela firmy Microsoft. Jeśli Twoja organizacja jest podmiotem stowarzyszonym innej organizacji, zostanie również wyświetlona sekcja **Organizacja potencjalnych** użytkowników z nazwą i adresem tej organizacji.

Jeśli twoja organizacja po raz pierwszy nawiązuje relację handlową z firmą Microsoft i nie podpisano jeszcze umowy MCA, jeśli informacje w **organizacji Twojej organizacji** lub **organizacji potencjalnego klienta** są nieprawidłowe, skontaktuj się z przedstawicielem, aby wprowadzić zmiany. Po zaakceptowaniu umowy MCA możesz przejrzeć i zmienić adres organizacji oraz informacje kontaktowe na stronie [Konta rozliczeniowe](https://go.microsoft.com/fwlink/p/?linkid=2084771) w Centrum administracyjne platformy Microsoft 365. Jeśli nazwa organizacji zmieni się, otwórz żądanie usługi, aby je zaktualizować. [Dowiedz się, jak otworzyć żądanie obsługi](../admin/get-help-support.md).

### <a name="your-information"></a>Twoje informacje

Jeśli jesteś nowym klientem, wprowadź swoje imię i nazwisko, adres e-mail i numer telefonu w obszarze **Twoje informacje**, a następnie wybierz pozycję **Zapisz**. Jeśli jesteś istniejącym klientem, sprawdź, czy twoje informacje są poprawne. Aby wprowadzić jakiekolwiek poprawki, wybierz pozycję **Edytuj**, wprowadź niezbędne zmiany, a następnie wybierz pozycję **Zapisz**.

Gdy wszystko będzie gotowe, wybierz pozycję **Kontynuuj** , aby przejść do następnego kroku.

## <a name="step-2-review-proposal"></a>Krok 2. Przegląd propozycji

Propozycja zawiera szczegóły elementów omówionych z przedstawicielem firmy Microsoft. Możesz przesłać wiadomość e-mail z linkiem do propozycji, aby udostępnić ją innym uczestnikom projektu w organizacji. Każda osoba korzystająca z linku ma widok propozycji tylko do odczytu.

Jeśli chcesz wprowadzić jakiekolwiek zmiany w propozycji po przejrzeniu, skontaktuj się z przedstawicielem firmy Microsoft.

### <a name="proposal-contents"></a>Zawartość propozycji

Wniosek zawiera następujące informacje:

| Sekcji | Opis |
|---|---|
| Nazwa organizacji | Nazwa organizacji, dla której została przygotowana propozycja. |
| Ważność do daty | Data wygaśnięcia oferty propozycji. Jeśli przegapisz tę datę wygaśnięcia, skontaktuj się z przedstawicielem firmy Microsoft, aby poinformować go, że nadal interesuje Cię propozycja. |
| Waluta | Waluta używana do obliczania kosztu pozycji w propozycji. |
| Przygotowane do | Nazwa konta rozliczeniowego, adres, kontaktowy adres e-mail i numer telefonu osoby, która zażądała propozycji. |
| Przygotowane przez | Adres e-mail przedstawiciela firmy Microsoft, który przygotował propozycję. |
| Podsumowanie | Przedstawia sumę częściową skojarzoną z propozycją. W razie potrzeby zostanie również wyświetlony kurs wymiany walut (FX), który jest używany do obliczania kosztów. |
| Elementy wiersza propozycji | Ta sekcja zawiera ilość, cenę jednostkową i sumę częściową wszystkich elementów uwzględnionych w propozycji. |
| Następny krok | Ta sekcja wskazuje niezbędną akcję, którą należy wykonać. |

Aby podpisać mca, wybierz przycisk w obszarze **Następny krok**. Jeśli musisz podpisać warunki uzupełniające, link przeprowadzi Cię do witryny DocuSign, gdzie wykonasz kroki w celu podpisania dokumentu.

Po podpisaniu wszelkich niezbędnych umów lub postanowień uzupełniających wybierz pozycję **Przejdź do wyewidencjonowania**.

## <a name="step-3-checkout"></a>Krok 3. Wyewidencjonuj

Strona wyewidencjonowania zawiera następujące sekcje:

### <a name="sold-to"></a>Nabywca

W tej sekcji przedstawiono konto rozliczeniowe używane dla propozycji. Jeśli chcesz zmienić jakiekolwiek informacje, wybierz link **Edytuj** . Możesz również użyć linku **Edytuj** , aby dodać identyfikator podatkowy organizacji. Identyfikator podatkowy musi być powiązany z krajem wymienionym w sekcji **Sprzedane do** . Jeśli masz zwolnienie z podatku, musisz otworzyć bilet pomocy technicznej, aby zażądać statusu zwolnionego z podatku.

Aby dowiedzieć się więcej na temat identyfikatorów podatkowych i sposobu ubiegania się o status zwolnienia z podatku, zobacz [Informacje o podatku](billing-and-payments/tax-information.md).

### <a name="billed-to"></a>Rozliczane

W tej sekcji przedstawiono profil rozliczeniowy używany do określania elementów uwzględnionych na fakturze oraz sposobu płacenia faktur. W każdym cyklu rozliczeniowym otrzymujesz oddzielną fakturę dla każdego profilu rozliczeniowego. Płacisz za faktury za pomocą czeku lub przelewu bankowego albo przedpłaty za platformę Azure. Jeśli nie masz jeszcze profilu rozliczeniowego, przedstawiciel firmy Microsoft utworze go dla Ciebie. Podczas wyewidencjonowania możesz wybrać inny profil rozliczeniowy, jeśli go masz, zmienić nazwę profilu rozliczeniowego lub dodać p.o. Numer. Możesz również utworzyć nowy profil rozliczeniowy.

Aby uzyskać informacje o profilach rozliczeniowych, zobacz [Zarządzanie profilami rozliczeniowymi](billing-and-payments/manage-billing-profiles.md).

### <a name="proposal-items-in-this-order"></a>Elementy propozycji w tej kolejności

W tej sekcji przedstawiono listę wszystkich elementów uwzględnionych w propozycji. Lista może zawierać co najmniej jedną z następujących kategorii:

- **Terminy uzupełniające** Lista wszelkich poprawek do umowy MCA, które zawierają warunki dla Twojej organizacji. Na przykład ta lista może zawierać terminy HIPAA lub RODO.
- **Kup teraz** Lista elementów, za które płacisz podczas wyewidencjonowania na końcu przepływu pracy akceptacji propozycji.
- **Rabaty (stosowane do przyszłych opłat)** Lista rabatów, które otrzymujesz w ramach propozycji.
- **Zawarte** Lista elementów uwzględnionych w pakiecie propozycji bez dodatkowych opłat. Niektóre z tych elementów mogą mieć skojarzony koszt w przyszłości.

> [!NOTE]
> Twoja propozycja może obejmować subskrypcje z przyszłą datą rozpoczęcia. Aby uzyskać więcej informacji, zobacz [Understand invoicing for future start dates (Omówienie fakturowania dla przyszłych dat rozpoczęcia](billing-and-payments/future-start-date.md)).

### <a name="summary"></a>Podsumowanie

W tej sekcji przedstawiono liczbę płatnych elementów, sumę częściową, szacowane podatki i łączną kwotę zamówienia.

Aby złożyć zamówienie, wybierz pozycję **Umieść zamówienie** lub **Zaakceptuj zamówienie miejsca umowy&amp;**.

Po złożeniu zamówienia otrzymasz potwierdzenie z kolejnymi krokami do wykonania. Jeśli zakupiono plan platformy Azure, następnym krokiem jest skonfigurowanie konta rozliczeniowego w Azure Portal.

## <a name="step-4-set-up-your-new-billing-account-azure-customers-only"></a>Krok 4. Konfigurowanie nowego konta rozliczeniowego (tylko klienci platformy Azure)

Jeśli jesteś nowym klientem i kupiłeś produkty platformy Azure w ramach propozycji, następnym krokiem jest skonfigurowanie nowego konta rozliczeniowego. Aby dowiedzieć się, jak to zrobić, zobacz [Konfigurowanie konta rozliczeniowego dla Umowa z Klientem Microsoft](/azure/cost-management-billing/manage/mca-setup-account).

Jeśli jesteś istniejącym klientem platformy Azure z Enterprise Agreement i podpisujesz umowę MCA po raz pierwszy, następnym krokiem jest zapoznanie się ze zmianami między umowami i sposobem wykonywania zadań przy użyciu nowego konta rozliczeniowego. Aby dowiedzieć się więcej, zobacz [Wykonywanie zadań Enterprise Agreement na koncie rozliczeniowym dla Umowa z Klientem Microsoft](/azure/cost-management-billing/manage/mca-enterprise-operations).

## <a name="understand-invoicing"></a>Omówienie fakturowania

Po wyewidencjonowaniu i zakończeniu zamówienia początkowa faktura zostanie wysłana w ciągu 24–48 godzin. Następnie otrzymujesz faktury około 5 dnia każdego miesiąca. Faktura miesięczna zawiera opłaty z poprzedniego miesiąca. Jeśli masz jakiekolwiek środki na swoje konto, są one odejmowane od środków pieniężnych profilu rozliczeniowego i stosowane do salda faktury. Pozostałe saldo po zastosowaniu środków to należne saldo. Masz 30 dni od daty rozliczenia, aby zapłacić fakturę.

Instrukcje dotyczące płatności dotyczące miejsca wysyłania czeków lub przelewów są zawarte w kopii faktury w formacie PDF. Aby wyświetlić lub pobrać fakturę, zobacz [Wyświetlanie rachunku lub faktury](billing-and-payments/view-your-bill-or-invoice.md).
