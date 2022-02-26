---
title: Informacje dotyczące ról administratora w centrum administracyjnym platformy Microsoft 365
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
- adminvideo
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: da585eea-f576-4f55-a1e0-87090b6aaa9d
description: Role administratorów, takie jak mapowanie administratora usługi na funkcje biznesowe i nadaj uprawnienia do wykonywania określonych zadań w centrum administracyjnym.
ms.openlocfilehash: 5bea496ca24f3aef97a780d48c74b84aaa46176b
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "62973824"
---
# <a name="about-admin-roles"></a>Role administratora — informacje

Microsoft 365 lub Office 365 zawiera zestaw ról administratora, które można przypisać użytkownikom w organizacji przy użyciu aplikacji <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365</a>. Każda rola administratora jest powiązana z typowymi funkcjami biznesowymi i zapewnia osobom w Twojej organizacji uprawnienia do wykonywania określonych zadań w centrum administracyjnym.

Centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365</a> umożliwia zarządzanie rolami i rolami Microsoft Intune Azure AD. Te role to jednak podzbiór ról dostępnych w portalu usługi Azure AD i centrum administracyjnym usługi Intune.

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej czynności opisanej w tym temacie, rozważ współpracę z specjalistą [ds. małej firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej Ty i Twoi pracownicy możecie uzyskać całodobowy dostęp do małych ekspertów biznesowych, gdy rozwijasz swoją firmę, od dołączania do codziennego użytku.

## <a name="watch-what-is-an-admin"></a>Obejrzyj: Co to jest administrator?

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1SRc0]

1. Po zalogowaniu Microsoft 365 wybierz uruchamianie aplikacji. Jeśli widzisz przycisk Administrator, to jesteś administratorem.
1. Wybierz **pozycję Administrator**, aby przejść do centrum administracyjne platformy Microsoft 365.
1. W lewym okienku nawigacji wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**UżytkownicyAktywowanie**</a> >  użytkowników.
1. Wybierz osobę, którą chcesz uczynić administratorem. Szczegóły użytkownika zostaną wyświetlone w prawym oknie dialogowym.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Szukasz pełnej listy szczegółowych opisów ról w usłudze Azure AD, które można zarządzać <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">w centrum administracyjne platformy Microsoft 365?</a> Zobacz Uprawnienia ról administratora w Azure Active Directory. [Wbudowane role w usłudze Azure AD](/azure/active-directory/roles/permissions-reference).

Szukasz pełnej listy szczegółowych opisów ról w usłudze Intune, które możesz zarządzać <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">w centrum administracyjne platformy Microsoft 365?</a>  Zobacz Kontrola [dostępu oparta na rolach (RBAC, Role based access control) wraz z Microsoft Intune](/mem/intune/fundamentals/role-based-access-control).

Aby uzyskać więcej informacji na temat przypisywania ról <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">w centrum administracyjne platformy Microsoft 365,</a> zobacz [Przypisywanie ról administratora](assign-admin-roles.md).

## <a name="security-guidelines-for-assigning-roles"></a>Wskazówki dotyczące zabezpieczeń dotyczące przypisywania ról

Ze względu na to, że administratorzy mają dostęp do poufnych danych i plików, zalecamy wykonanie poniższych wskazówek w celu zapewnienia bezpieczeństwa danych w Twojej organizacji.

| Zalecenie                  | Dlaczego jest to ważne?                 |
| :------------------- | :------------------- |
| Posiadanie 2–4 administratorów globalnych  | Ponieważ hasło administratora globalnego może być zresetowane tylko przez innego administratora globalnego, zalecamy, aby w organizacji byli co najmniej 2 administratorzy globalni na wypadek zablokowania konta. Jednak administrator globalny ma prawie nieograniczony dostęp do ustawień organizacji oraz do większości danych, dlatego zalecamy, żeby liczba administratorów globalnych nie przekraczała 4, ponieważ stanowi to zagrożenie bezpieczeństwa. |
| Przypisywanie możliwie *najbardziej ograniczonej* roli    | Przypisywanie *najbardziej ograniczonej* roli oznacza zapewnienie administratorom dostępu tylko w takim zakresie, jakiego potrzebują do wykonywania swojej pracy. Jeśli na przykład chcesz, aby ktoś mógł resetować hasła pracowników, nie musisz przypisywać nieograniczonej roli administratora globalnego. Zamiast tego należy przypisać ograniczoną rolę administratora, na przykład administratora haseł lub administratora pomocy technicznej.  Dzięki temu Twoje dane będą bezpieczne.                 |
| Wymóg uwierzytelniania wieloskładnikowego dla administratorów                  |    Dobrym pomysłem jest wymaganie uwierzytelniania wieloskładnikowego dla wszystkich użytkowników, ale administratorzy powinni mieć obowiązek logowania się za pomocą uwierzytelniania wieloskładnikowego. Uwierzytelnienie wieloskładnikowe wymaga od użytkowników użycia drugiej metody poświadczenia ich tożsamości celem potwierdzenia, że to naprawdę oni. Administratorzy mogą mieć dostęp do wielu danych klientów i pracowników, a w przypadku wymogu uwierzytelniania wieloskładnikowego nawet złamane hasło administratora staje się bezużyteczne bez drugiej formy identyfikacji.  <br><br>Gdy włączysz uwierzytelnianie wieloskładnikowe, przy następnym logowaniu użytkownik będzie musiał podać alternatywny adres e-mail oraz numer telefonu na potrzeby odzyskiwania konta.  <br> [Konfigurowanie uwierzytelniania wieloskładnikowego](../security-and-compliance/set-up-multi-factor-authentication.md)          |

Jeśli w centrum administracyjnym zostanie wyświetlony komunikat z informacją, że nie masz uprawnień do edytowania danego ustawienia lub strony, jest to spowodowane tym, że masz przypisaną rolę bez tego uprawnienia.

## <a name="commonly-used-microsoft-365-admin-center-roles"></a>Często używane centrum administracyjne platformy Microsoft 365 ról

W centrum administracyjne platformy Microsoft 365 możesz przejść <a href="https://go.microsoft.com/fwlink/p/?linkid=2097861" target="_blank">**do przypisań**</a> ról, a następnie wybrać dowolną rolę, aby otworzyć jej okienko szczegółów. Wybierz **kartę Uprawnienia** , aby wyświetlić szczegółową listę administratorów przypisanych do tej roli. Wybierz **kartę Przypisani** lub **Przypisani administratorzy** , aby dodać użytkowników do ról.

Prawdopodobnie w Twojej organizacji potrzebne będzie przypisanie jedynie następujących ról. Domyślnie najpierw pokazujemy role, które wykorzystuje większość organizacji. Jeśli nie możesz znaleźć roli, przejdź na dół listy i wybierz pozycję **Pokaż wszystko według kategorii**. (Aby uzyskać szczegółowe informacje, w tym polecenia cmdlet skojarzone z rolą, zobacz Wbudowane role w usłudze [Azure AD](/azure/active-directory/roles/permissions-reference)).

|Rola administratora     |Komu powinna być przypisana ta rola?  |
|---------|---------|
|Administrator rozliczeń     |   Przypisz rolę administratora rozliczeń użytkownikom, którzy dokonają zakupów, zarządzaj subskrypcjami i żądaniami usług oraz monitorują kondycję usługi. <br><br> Administratorzy rozliczeń mogą również:<br> — Zarządzanie wszystkimi aspektami rozliczeń <br> - Tworzenie biletów pomocy technicznej i zarządzanie nimi w portalu Azure Portal <br>  |
|Administrator programu Exchange     |   Przypisz Exchange administratorów użytkownikom, którzy muszą wyświetlać skrzynki pocztowe poczty e-mail, grupy Microsoft 365 i zarządzać nimi Exchange Online. <br><br> Administratorzy programu Exchange mogą również:<br> - Odzyskiwać usunięte elementy w skrzynce pocztowej użytkownika <br> - Konfigurować pełnomocników „Wyślij jako” i „Wyślij w imieniu” <br>  |
|Administrator globalny     |   Rolę administratora globalnego należy przypisać użytkownikom, którzy potrzebują globalnego dostępu do większości funkcji zarządzania i danych w usługach online firmy Microsoft. <br><br> Nadanie zbyt dużej licznie użytkowników globalnego dostępu stwarza zagrożenie bezpieczeństwa, dlatego zalecamy od 2 do 4 administratorów globalnych. <br><br> Tylko administratorzy globalni mogą:<br> - Resetować hasła wszystkich użytkowników <br> - Dodawać domeny i zarządzać nimi <br> - Odblokowanie innego administratora globalnego <br> <br> **Uwaga:** osoba tworząca konto w usługach online firmy Microsoft automatycznie zostaje administratorem globalnym. |
|Czytelnik globalny    |   Rolę czytelnika globalnego należy przypisać użytkownikom, którzy muszą móc wyświetlać funkcje i ustawienia administratora w centrach administratora, które widoczne są dla administratora globalnego. Czytelnik globalny nie może edytować żadnych ustawień.   |
|Administrator grup     |   Przypisz rolę administratora grup użytkownikom, którzy muszą zarządzać wszystkimi ustawieniami grup w centrach aadministracyjnym, w tym w portalu centrum administracyjne platformy Microsoft 365 i Azure Active Directory grupy. <br><br> Administratorzy grup mogą:<br> — Tworzenie, edytowanie, usuwanie i przywracanie Microsoft 365 grupy <br> - Tworzyć i aktualizować zasady tworzenia, wygasania i nazewnictwa grup <br> - Tworzyć, edytować, usuwać i przywracać grupy zabezpieczeń Azure Active Directory| 
|Administrator pomocy technicznej     |   Rolę administratora pomocy technicznej należy przypisywać użytkownikom, którzy muszą mieć możliwość:<br> - Resetowania haseł <br> - Wymuszania wylogowywania użytkowników <br> - Zarządzania żądaniami obsługi <br> - Monitorowania kondycji usługi <br> <br> **Uwaga**: administrator pomocy technicznej może zapewniać pomoc tylko użytkownikom, którzy nie są administratorami, a także użytkownikom z przypisanymi następującymi rolami: czytelnik katalogów, zapraszający gości, administrator pomocy technicznej, czytelnik centrum wiadomości i czytelnik raportów.      |
|Administrator licencji    |   Przypisz rolę administratora licencji do użytkowników, którzy muszą przypisywać licencje użytkownikom i usuwać je oraz edytować ich lokalizację użytkowania. <br/><br/> Administratorzy licencji mogą również: <br> - Ponowne przetwarzanie przypisań licencji na licencjonowanie grupowe <br> — Przypisywanie licencji produktu grupom na licencjonowanie grupowe  |
|Administrator aplikacji pakietu Office    |   Rolę administratora aplikacji pakietu Office należy przypisywać użytkownikom, którzy muszą mieć możliwość: <br> - Korzystania z usługi zasad w chmurze pakietu Office do tworzenia zasad opartych na chmurze dla pakietu Office i zarządzania nimi <br> - Tworzenia żądań obsługi i zarządzania nimi <br> — Zarządzanie zawartością Co nowego, która jest widzina przez użytkowników w Office aplikacji   <br> - Monitorowanie kondycji usługi  |
|Administrator haseł  |   Przypisz rolę administratora haseł do użytkownika, który musi zresetować hasła dla osób niebędących administratorami oraz administratorów haseł.   |
|Czytelnik Centrum wiadomości |   Przypisz rolę czytnika centrum wiadomości do użytkowników, którzy muszą wykonać następujące czynności: <br> - Monitorowanie powiadomień w centrum wiadomości <br> - Uzyskaj cotygodniowe podsumowanie wiadomości e-mail z wpisów i aktualizacji w Centrum wiadomości <br> - Udostępnianie wpisów w Centrum wiadomości <br> - Mieć dostęp tylko do odczytu do usług Azure AD, takich jak użytkownicy i grupy|
|Administrator platformy Power Platform |   Przypisz rolę administratora platformy Power Platform użytkownikom, którzy muszą wykonać następujące czynności: <br> - Zarządzanie wszystkimi funkcjami administratora w celu Power Apps, Power Automate i ochrony przed utratą danych <br> - Tworzenia żądań obsługi i zarządzania nimi <br> - Monitorowanie kondycji usługi  |
|Czytelnik raportów |   Przypisz rolę czytelnika Raporty użytkownikom, którzy muszą wykonać następujące czynności: <br> — Wyświetlać dane użycia i raporty aktywności w centrum administracyjne platformy Microsoft 365 <br> — Uzyskiwanie dostępu do pakietu Power BI zawartości <br> - Uzyskaj dostęp do raportów logowania i aktywności w usłudze Azure AD <br> - Wyświetlanie danych zwróconych przez interfejs API raportowania Graph Microsoft|
|Administrator pomocy technicznej usługi   |   Przypisz rolę administratora pomocy technicznej usługi jako dodatkową rolę administratorom lub użytkownikom, którzy oprócz zwykłych ról administratora muszą wykonać następujące czynności: <br> - Otwieranie żądań obsługi i zarządzanie nimi <br> - Wyświetlanie i udostępnianie wpisów w centrum wiadomości <br> - Monitorowanie kondycji usługi   |
|Administrator programu SharePoint    |   Rolę administratora programu SharePoint należy przypisywać użytkownikom, którzy potrzebują dostępu do centrum administratora usługi SharePoint Online oraz możliwości zarządzania. <br><br>Administratorzy programu SharePoint mogą również: <br> - Tworzyć i usuwać witryny <br> - Zarządzać zbiorami witryn oraz ustawieniami globalnymi programu SharePoint   |
|Teams administratora    |   Przypisz Teams administratorów użytkownikom, którzy muszą mieć dostęp do centrum administracyjnego firmy i Teams zarządzanie nimi. <br><br>Teams może również: <br> - Zarządzać ustawieniami <br> - Zarządzać mostkami konferencyjnymi <br> - Zarządzać ustawieniami dla całej organizacji, w tym dotyczącymi federacji, aktualizowania zespołów oraz ustawień klientów aplikacji Teams   |
|Administrator użytkowników     |    Rolę administratora użytkowników należy przypisywać użytkownikom, którzy muszą móc wykonywać następujące działania dla wszystkich użytkowników: <br> - Dodawanie użytkowników i grup <br> - Przypisywanie licencji <br> - Zarządzanie właściwościami większości użytkowników <br> - Tworzenie widoków użytkowników i zarządzanie nimi <br> - Aktualizowanie zasad wygasania hasła <br> - Zarządzania żądaniami obsługi <br> - Monitorowanie kondycji usługi <br><br>  Administrator użytkowników może także wykonywać następujące czynności dla użytkowników, którzy nie są administratorami, i dla użytkowników z przypisanymi następującymi rolami: czytelnik katalogów, zapraszanie gości, administrator pomocy technicznej, czytelnik centrum wiadomości, czytelnik raportów: <br> - Zarządzanie nazwami użytkowników<br> - Usuwanie i przywracanie użytkowników<br> - Resetowanie haseł <br> - Wymuszanie wylogowywania użytkowników <br> - Aktualizowanie kluczy urządzeń (FIDO)   |

## <a name="delegated-administration-for-microsoft-partners"></a>Administracja delegowana dla partnerów firmy Microsoft

Jeśli pracujesz z partnerem firmy Microsoft, możesz przypisać mu role administratora. Z kolei one mogą przypisywać użytkowników w firmie lub w firmie, role administratora. Możesz chcieć, aby partner to zrobił, na przykład w sytuacji, gdy konfiguruje za Ciebie Twoją organizację online i zarządza nią.
  
Partner może przypisywać następujące role: 
  
- **Agent administracyjny** Uprawnienia równoważne administratorowi globalneowi z wyjątkiem zarządzania uwierzytelnianiem wieloskładnikowym za pośrednictwem Centrum partnerskiego.

- **Agent pomocy technicznej** Uprawnienia równoważne z uprawnieniami administratora pomocy technicznej.

Zanim Partner będzie mógł przypisywać te role do użytkowników, musisz dodać go jako administratora delegowanego do swojego konta. Ten proces jest inicjowany przez autoryzowanego partnera. Musi wysłać Ci wiadomość e-mail z prośbą o nadanie uprawnień administratora delegowanego. Aby uzyskać instrukcje, zobacz [Autoryzowanie i usuwanie relacji partnerskich](../misc/add-partner.md).
  
## <a name="related-content"></a>Zawartość pokrewna

[Przypisywanie ról administratora](assign-admin-roles.md) (artykuł)\
[Role usługi Azure AD w centrum administracyjne platformy Microsoft 365](azure-ad-roles-in-the-mac.md) (artykuł)\
[Raporty aktywności w centrum administracyjne platformy Microsoft 365](../activity-reports/activity-reports.md) (artykuł)\
[Exchange Online roli administratora](about-exchange-online-admin-role.md) (artykuł)
