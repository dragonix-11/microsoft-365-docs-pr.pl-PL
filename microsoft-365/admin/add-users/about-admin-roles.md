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
description: Role administratora, takie jak administrator usługi, są powiązane z funkcjami biznesowymi i zapewniają uprawnienia do wykonywania określonych zadań w centrum administracyjnym.
ms.openlocfilehash: 8a1df118b5dfe1ad484f3a8048cce9cf748ab54b
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64937672"
---
# <a name="about-admin-roles"></a>Role administratora — informacje

Subskrypcje usług Microsoft 365 lub Office 365 zawierają zestaw ról administratora, które można przypisać użytkownikom w organizacji przy użyciu aplikacji <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365</a>. Każda rola administratora jest powiązana z typowymi funkcjami biznesowymi i zapewnia osobom w Twojej organizacji uprawnienia do wykonywania określonych zadań w centrum administracyjnym.

<a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a> pozwala zarządzać rolami usług Azure AD i Microsoft Intune. Te role są jednak podzbiorem ról dostępnych w portalu usługi Azure AD i w centrum administracyjnym usługi Intune.

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej kroków opisanych w tym temacie, rozważ [współpracę ze specjalistą ds. małych firm firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej Ty i Twoi pracownicy uzyskujecie całodobowy dostęp do wsparcia ze strony specjalistów ds. małych firm w miarę rozwoju firmy — od dołączania do codziennego użytku.

## <a name="watch-what-is-an-admin"></a>Obejrzyj: Kim jest administrator?

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1SRc0]

1. Po zalogowaniu na platformie Microsoft 365 wybierz uruchamianie aplikacji. Jeśli zostanie wyświetlony przycisk Administrator, oznacza to, że jesteś administratorem.
1. Wybierz pozycję **Administrator**, aby przejść do centrum administracyjnego platformy Microsoft 365.
1. W lewym okienku nawigacji wybierz pozycję **Użytkownicy** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Aktywni użytkownicy**</a>.
1. Wybierz osobę, którą chcesz uczynić administratorem. Szczegóły użytkownika zostaną wyświetlone w prawym oknie dialogowym.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Szukasz pełnej listy szczegółowych opisów ról usługi Azure AD, którymi można zarządzać w <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjnym platformy Microsoft 365</a>? Zobacz Uprawnienia ról administratora w Azure Active Directory. [Wbudowane role w usłudze Azure AD](/azure/active-directory/roles/permissions-reference).

Szukasz pełnej listy szczegółowych opisów ról usługi Intune, którymi można zarządzać w <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjnym usługi Microsoft 365</a>?  Zapoznaj się z [kontrolą dostępu opartą na rolach (RBAC) w usłudze Microsoft Intune](/mem/intune/fundamentals/role-based-access-control).

Aby uzyskać więcej informacji na temat przypisywania ról w <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjnym platformy Microsoft 365</a>, zobacz artykuł [Przypisywanie ról administratora](assign-admin-roles.md).

## <a name="security-guidelines-for-assigning-roles"></a>Wskazówki dotyczące zabezpieczeń w ramach przypisywania ról

Ze względu na to, że administratorzy mają dostęp do poufnych danych i plików, zalecamy wykonanie poniższych wskazówek w celu zapewnienia bezpieczeństwa danych w Twojej organizacji.

| Zalecenie                  | Dlaczego jest to ważne?                 |
| :------------------- | :------------------- |
| Posiadanie 2–4 administratorów globalnych  | Ponieważ hasło administratora globalnego może być zresetowane tylko przez innego administratora globalnego, zalecamy, aby w organizacji byli co najmniej 2 administratorzy globalni na wypadek zablokowania konta. Jednak administrator globalny ma prawie nieograniczony dostęp do ustawień organizacji oraz do większości danych, dlatego zalecamy, żeby liczba administratorów globalnych nie przekraczała 4, ponieważ stanowi to zagrożenie bezpieczeństwa. |
| Przypisywanie możliwie *najbardziej ograniczonej* roli    | Przypisywanie *najbardziej ograniczonej* roli oznacza zapewnienie administratorom dostępu tylko w takim zakresie, jakiego potrzebują do wykonywania swojej pracy. Jeśli na przykład chcesz, aby ktoś mógł resetować hasła pracowników, nie musisz przypisywać nieograniczonej roli administratora globalnego. Zamiast tego należy przypisać ograniczoną rolę administratora, na przykład administratora haseł lub administratora pomocy technicznej.  Dzięki temu Twoje dane będą bezpieczne.                 |
| Wymóg uwierzytelniania wieloskładnikowego dla administratorów                  |    Dobrym pomysłem jest wymaganie uwierzytelniania wieloskładnikowego dla wszystkich użytkowników, ale administratorzy powinni mieć obowiązek logowania się za pomocą uwierzytelniania wieloskładnikowego. Uwierzytelnienie wieloskładnikowe wymaga od użytkowników użycia drugiej metody poświadczenia ich tożsamości celem potwierdzenia, że to naprawdę oni. Administratorzy mogą mieć dostęp do wielu danych klientów i pracowników, a w przypadku wymogu uwierzytelniania wieloskładnikowego nawet złamane hasło administratora staje się bezużyteczne bez drugiej formy identyfikacji.  <br><br>Gdy włączysz uwierzytelnianie wieloskładnikowe, przy następnym logowaniu użytkownik będzie musiał podać alternatywny adres e-mail oraz numer telefonu na potrzeby odzyskiwania konta.  <br> [Konfigurowanie uwierzytelniania wieloskładnikowego](../security-and-compliance/set-up-multi-factor-authentication.md)          |

Jeśli w centrum administracyjnym zostanie wyświetlony komunikat z informacją, że nie masz uprawnień do edytowania danego ustawienia lub strony, jest to spowodowane tym, że masz przypisaną rolę bez tego uprawnienia.

## <a name="commonly-used-microsoft-365-admin-center-roles"></a>Często używane role centrum administracyjnego platformy Microsoft 365

W centrum administracyjnym usługi Microsoft 365 możesz przejść do pozycji <a href="https://go.microsoft.com/fwlink/p/?linkid=2097861" target="_blank">**Przypisania roli**</a>, a następnie wybrać dowolną rolę, aby otworzyć jej okienko szczegółów. Wybierz kartę **Uprawnienia**, aby wyświetlić szczegółową listę uprawnień administratorów, którym została przypisana dana rola. Wybierz kartę **Przypisani** lub **Przypisani administratorzy**, aby dodać użytkowników do ról.

Prawdopodobnie w Twojej organizacji potrzebne będzie przypisanie jedynie następujących ról. Domyślnie najpierw pokazujemy role, które wykorzystuje większość organizacji. Jeśli nie możesz znaleźć jakiejś roli, przejdź na koniec listy i wybierz **Wyświetl wszystko wg kategorii**. (Aby uzyskać szczegółowe informacje, w tym polecenia cmdlet skojarzone z rolą, zobacz [role wbudowane usługi Azure AD](/azure/active-directory/roles/permissions-reference)).

|Rola administratora     |Komu powinna być przypisana ta rola?  |
|---------|---------|
|Administrator rozliczeń     |   Przypisz rolę administratora rozliczeń użytkownikom, którzy dokonywali zakupów, zarządzali subskrypcjami i żądaniami obsługi oraz monitorowali kondycję usługi. <br><br> Administratorzy rozliczeń mogą również:<br> — Zarządzać wszystkimi aspektami rozliczeń <br> — Tworzyć bilety pomocy technicznej i zarządzać nimi w witrynie Azure Portal <br>  |
|Administrator programu Exchange     |   Rolę administratora programu Exchange należy przypisać użytkownikom, którzy muszą wyświetlać skrzynki pocztowe użytkowników, grupy Microsoft 365 i usługę Exchange Online oraz zarządzać nimi. <br><br> Administratorzy programu Exchange mogą również:<br> - Odzyskiwać usunięte elementy w skrzynce pocztowej użytkownika <br> - Konfigurować pełnomocników „Wyślij jako” i „Wyślij w imieniu” <br>  |
|Administrator globalny     |   Rolę administratora globalnego należy przypisać użytkownikom, którzy potrzebują globalnego dostępu do większości funkcji zarządzania i danych w usługach online firmy Microsoft. <br><br> Nadanie zbyt dużej licznie użytkowników globalnego dostępu stwarza zagrożenie bezpieczeństwa, dlatego zalecamy od 2 do 4 administratorów globalnych. <br><br> Tylko administratorzy globalni mogą:<br> - Resetować hasła wszystkich użytkowników <br> - Dodawać domeny i zarządzać nimi <br> - Odblokować innego administratora globalnego <br> <br> **Uwaga:** osoba tworząca konto w usługach online firmy Microsoft automatycznie zostaje administratorem globalnym. |
|Czytelnik globalny    |   Rolę czytelnika globalnego należy przypisać użytkownikom, którzy muszą wyświetlać funkcje i ustawienia administratora w centrach administratora, które są widoczne dla administratora globalnego. Administrator globalnego czytelnika nie może edytować żadnych ustawień.   |
|Administrator grup     |   Rolę administratora grup należy przypisywać użytkownikom, którzy muszą zarządzać wszystkimi grupami w centrach administracyjnych, w tym w centrum administracyjnym platformy Microsoft 365 i portalu Azure Active Directory. <br><br> Administratorzy grup mogą:<br> - Tworzyć, edytować, usuwać i przywracać grupy usługi Microsoft 365 <br> - Tworzyć i aktualizować zasady tworzenia, wygasania i nazewnictwa grup <br> - Tworzyć, edytować, usuwać i przywracać grupy zabezpieczeń Azure Active Directory| 
|Administrator pomocy technicznej     |   Rolę administratora pomocy technicznej należy przypisywać użytkownikom, którzy muszą mieć możliwość:<br> - Resetowania haseł <br> - Wymuszania wylogowywania użytkowników <br> - Zarządzania żądaniami obsługi <br> - Monitorowania kondycji usługi <br> <br> **Uwaga**: administrator pomocy technicznej może zapewniać pomoc tylko użytkownikom, którzy nie są administratorami, a także użytkownikom z przypisanymi następującymi rolami: czytelnik katalogów, zapraszający gości, administrator pomocy technicznej, czytelnik centrum wiadomości i czytelnik raportów.      |
|Administrator licencji    |   Przypisz rolę administratora licencji do użytkowników, którzy muszą przypisywać licencje użytkownikom i usuwać je oraz edytować ich lokalizację użytkowania. <br/><br/> Administratorzy licencji mogą również: <br> - Ponownie przetwarzać przypisania licencji dla licencjonowania grupowego <br> - Przypisywać licencje produktu grupom dla licencjonowania grupowego  |
|Administrator aplikacji pakietu Office    |   Rolę administratora aplikacji pakietu Office należy przypisywać użytkownikom, którzy muszą mieć możliwość: <br> - Korzystania z usługi zasad w chmurze pakietu Office do tworzenia zasad opartych na chmurze dla pakietu Office i zarządzania nimi <br> - Tworzenia żądań obsługi i zarządzania nimi <br> - Zarządzania zawartością Co nowego w aplikacjach pakietu Office, która jest widoczna dla użytkowników   <br> - Monitorowanie kondycji usługi  |
|Administrator haseł  |   Przypisz rolę administratora haseł do użytkownika, który musi resetować hasła dla osób niebędących administratorami oraz dla administratorów haseł.   |
|Czytelnik Centrum wiadomości |   Rolę czytelnika Centrum wiadomości należy przypisywać użytkownikom, którzy muszą mieć możliwość: <br> - Monitorowania powiadomień w centrum wiadomości <br> - Uzyskiwania cotygodniowego podsumowania wiadomości e-mail z wpisów i aktualizacji w Centrum wiadomości <br> - Udostępniania wpisów w Centrum wiadomości <br> - Dostępu tylko do odczytu do usług Azure AD, takich jak użytkownicy i grupy|
|Administrator platformy Power |   Rolę administratora platformy Power należy przypisywać użytkownikom, którzy muszą mieć możliwość: <br> - Zarządzania wszystkimi funkcjami administratora w usługach Power Apps, Power Automate i ochroną przed utratą danych w Microsoft Purview <br> - Tworzenia żądań obsługi i zarządzania nimi <br> - Monitorowanie kondycji usługi  |
|Czytelnik raportów |   Rolę czytelnika raportów należy przypisywać użytkownikom, którzy muszą mieć możliwość: <br> — Wyświetlania dane użycia i raportów aktywności w centrum administracyjnym platformy Microsoft 365 <br> — Uzyskiwania dostępu do pakietu zawartości wrażania usługi Power BI <br> - Uzyskiwania dostępu do raportów logowania i aktywności w usłudze Azure AD <br> - Wyświetlania danych zwróconych przez interfejs API raportowania usługi Microsoft Graph|
|Administrator pomocy technicznej usługi   |   Przypisz rolę administratora pomocy technicznej usługi jako dodatkową rolę administratorom lub użytkownikom, którzy muszą wykonywać następujące czynności oprócz zwykłej roli administratora: <br> - Otwieranie żądań obsługi i zarządzanie nimi <br> - Wyświetlanie i udostępnianie wpisów w centrum wiadomości <br> - Monitorowanie kondycji usługi   |
|Administrator programu SharePoint    |   Rolę administratora programu SharePoint należy przypisywać użytkownikom, którzy potrzebują dostępu do centrum administratora usługi SharePoint Online oraz możliwości zarządzania. <br><br>Administratorzy programu SharePoint mogą również: <br> - Tworzyć i usuwać witryny <br> - Zarządzać zbiorami witryn oraz ustawieniami globalnymi programu SharePoint   |
|Administrator aplikacji Teams    |   Rolę administratora aplikacji Teams należy przypisywać użytkownikom, którzy potrzebują dostępu do centrum administratora aplikacji Teams oraz możliwości zarządzania. <br><br>Administratorzy aplikacji Teams mogą również: <br> - Zarządzać ustawieniami <br> - Zarządzać mostkami konferencyjnymi <br> - Zarządzać ustawieniami dla całej organizacji, w tym dotyczącymi federacji, aktualizowania zespołów oraz ustawień klientów aplikacji Teams   |
|Administrator użytkowników     |    Rolę administratora użytkowników należy przypisywać użytkownikom, którzy muszą móc wykonywać następujące działania dla wszystkich użytkowników: <br> - Dodawanie użytkowników i grup <br> - Przypisywanie licencji <br> - Zarządzanie właściwościami większości użytkowników <br> - Tworzenie widoków użytkowników i zarządzanie nimi <br> - Aktualizowanie zasad wygasania hasła <br> - Zarządzania żądaniami obsługi <br> - Monitorowanie kondycji usługi <br><br>  Administrator użytkowników może także wykonywać następujące czynności dla użytkowników, którzy nie są administratorami, i dla użytkowników z przypisanymi następującymi rolami: czytelnik katalogów, zapraszanie gości, administrator pomocy technicznej, czytelnik centrum wiadomości, czytelnik raportów: <br> - Zarządzanie nazwami użytkowników<br> - Usuwanie i przywracanie użytkowników<br> - Resetowanie haseł <br> - Wymuszanie wylogowywania użytkowników <br> - Aktualizowanie kluczy urządzeń (FIDO)   |

## <a name="delegated-administration-for-microsoft-partners"></a>Administracja delegowana dla partnerów firmy Microsoft

Jeśli pracujesz z partnerem firmy Microsoft, możesz przypisać mu role administratora. Z kolei on może przypisać użytkownikom w Twojej firmie — lub swojej — role administratora. Być może chcesz, aby zrobił to partner, jeśli na przykład konfiguruje on za Ciebie organizację online i zarządza nią.
  
Partner może przypisywać następujące role: 
  
- Uprawnienia **agenta administratora** równoważne administratorowi globalnemu z wyjątkiem zarządzania uwierzytelnianiem wieloskładnikowym za pośrednictwem Centrum partnerskiego.

- Uprawnienia **agenta pomocy technicznej** równoważne z uprawnieniami administratora pomocy technicznej.

Zanim partner będzie mógł przypisywać te role użytkownikom, musisz dodać tego partnera jako administratora delegowanego do swojego konta. Ten proces jest inicjowany przez partnera autoryzowanego. Partner wysyła do Ciebie wiadomość e-mail z pytaniem, czy chcesz nadać mu uprawnienia do działania jako administrator delegowany. Aby uzyskać instrukcje, zobacz [Autoryzowanie i usuwanie relacji partnerskich](../misc/add-partner.md).
  
## <a name="related-content"></a>Zawartość pokrewna

[Przypisywanie ról administratora](assign-admin-roles.md) (artykuł)\
[Role usługi Azure AD w centrum administracyjnym platformy Microsoft 365](azure-ad-roles-in-the-mac.md) (artykuł)\
[Raporty aktywności w centrum administracyjnym platformy Microsoft 365](../activity-reports/activity-reports.md) (artykuł)\
[Rola administratora usługi Exchange Online](about-exchange-online-admin-role.md)(artykuł)
