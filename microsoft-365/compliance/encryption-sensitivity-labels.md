---
title: Ograniczanie dostępu do zawartości przy użyciu etykiet poufności w celu zastosowania szyfrowania
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Skonfiguruj etykiety poufności na potrzeby szyfrowania, które chroni dane, ograniczając dostęp i użycie.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 0ec60e573d5c05c4a30e74f235ffae5983de03dc
ms.sourcegitcommit: 5c9137f98e688ab23c144e75687399e390bb2601
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2022
ms.locfileid: "64705413"
---
# <a name="restrict-access-to-content-by-using-sensitivity-labels-to-apply-encryption"></a>Ogranicz dostęp do zawartości przy użyciu etykiet poufności w celu zastosowania szyfrowania

>*[Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Podczas tworzenia etykiety poufności można ograniczyć dostęp do zawartości, do którą zostanie zastosowana etykieta. Na przykład za pomocą ustawień szyfrowania etykiety poufności można chronić zawartość, aby:

- Tylko użytkownicy w organizacji mogą otworzyć poufny dokument lub wiadomość e-mail.
- Tylko użytkownicy w dziale marketingu mogą edytować i drukować dokument lub wiadomość e-mail z ogłoszeniem o promocji, podczas gdy wszyscy inni użytkownicy w organizacji mogą go tylko odczytać.
- Użytkownicy nie mogą przesyłać dalej wiadomości e-mail ani kopiować z niej informacji zawierających wiadomości o reorganizacji wewnętrznej.
- Nie można otworzyć bieżącego cennika wysyłanego do partnerów biznesowych po określonej dacie.

Gdy dokument lub wiadomość e-mail jest szyfrowana, dostęp do zawartości jest ograniczony, dzięki czemu:

- Może być odszyfrowywany tylko przez użytkowników autoryzowanych przez ustawienia szyfrowania etykiety.
- Pozostaje zaszyfrowany bez względu na to, gdzie się znajduje, wewnątrz lub na zewnątrz organizacji, nawet jeśli nazwa pliku została zmieniona.
- Jest szyfrowany zarówno w spoczynku (na przykład na koncie OneDrive), jak i podczas przesyłania (na przykład wiadomości e-mail przechodzące przez Internet).

Na koniec, jako administrator, podczas konfigurowania etykiety poufności w celu zastosowania szyfrowania można wybrać jedną z następujących opcji:

- **Przypisz teraz uprawnienia**, aby określić dokładnie, którzy użytkownicy uzyskują uprawnienia do zawartości z tą etykietą.
- **Zezwalaj użytkownikom na przypisywanie uprawnień** podczas stosowania etykiety do zawartości. Dzięki temu możesz zezwolić osobom w organizacji na pewną elastyczność, która może wymagać współpracy i wykonania pracy.

Ustawienia szyfrowania są dostępne podczas [tworzenia etykiety poufności](create-sensitivity-labels.md) w Centrum zgodności platformy Microsoft 365. Możesz również użyć starszego portalu, Centrum zgodności & zabezpieczeń.

## <a name="understand-how-the-encryption-works"></a>Informacje o tym, jak działa szyfrowanie

Szyfrowanie korzysta z usługi Azure Rights Management (Azure RMS) z usługi Azure Information Protection. To rozwiązanie ochrony używa zasad szyfrowania, tożsamości i autoryzacji. Aby dowiedzieć się więcej, zobacz [Co to jest usługa Azure Rights Management?](/azure/information-protection/what-is-azure-rms) z dokumentacji usługi Azure Information Protection. 

W przypadku korzystania z tego rozwiązania szyfrowania funkcja **superużytkownika** zapewnia, że autoryzowane osoby i usługi zawsze będą mogły odczytywać i sprawdzać dane, które zostały zaszyfrowane dla Twojej organizacji. W razie potrzeby można usunąć lub zmienić szyfrowanie. Aby uzyskać więcej informacji, zobacz [Konfigurowanie superużytkowania dla usługi Azure Information Protection i odnajdywania lub odzyskiwania danych](/azure/information-protection/configure-super-users).

## <a name="important-prerequisites"></a>Ważne wymagania wstępne

Przed użyciem szyfrowania może być konieczne wykonywanie pewnych zadań konfiguracji. Podczas konfigurowania ustawień szyfrowania nie ma możliwości sprawdzenia, czy te wymagania wstępne zostały spełnione.

- Aktywowanie ochrony z usługi Azure Information Protection
    
    Aby etykiety poufności miały zastosowanie szyfrowania, należy aktywować usługę ochrony (Azure Rights Management) z usługi Azure Information Protection dla dzierżawy. W nowszych dzierżawach jest to ustawienie domyślne, ale może być konieczne ręczne aktywowanie usługi. Aby uzyskać więcej informacji, zobacz [Aktywowanie usługi ochrony z usługi Azure Information Protection](/azure/information-protection/activate-service).

- Sprawdzanie wymagań sieciowych
    
    Może być konieczne wprowadzenie pewnych zmian na urządzeniach sieciowych, takich jak zapory. Aby uzyskać szczegółowe informacje, zobacz [Zapory i infrastruktura sieci](/azure/information-protection/requirements#firewalls-and-network-infrastructure) z dokumentacji usługi Azure Information Protection.

- Konfigurowanie Exchange dla usługi Azure Information Protection
    
    Exchange nie trzeba konfigurować dla usługi Azure Information Protection, aby użytkownicy mogli stosować etykiety w Outlook w celu szyfrowania wiadomości e-mail. Jednak dopóki Exchange nie zostanie skonfigurowana dla usługi Azure Information Protection, nie uzyskasz pełnej funkcjonalności korzystania z ochrony usługi Azure Rights Management z Exchange.
    
    Na przykład użytkownicy nie mogą wyświetlać zaszyfrowanych wiadomości e-mail na telefonach komórkowych lub za pomocą Outlook w sieci Web, szyfrowane wiadomości e-mail nie mogą być indeksowane do wyszukiwania i nie można skonfigurować Exchange Online DLP na potrzeby ochrony usługi Rights Management. 
    
    Aby upewnić się, że Exchange może obsługiwać te dodatkowe scenariusze, zobacz następujące kwestie:
    
    - Aby uzyskać Exchange Online, zobacz instrukcje dotyczące [Exchange Online: Konfiguracja usługi IRM](/azure/information-protection/configure-office365#exchangeonline-irm-configuration).
    - Aby Exchange lokalnie, należy wdrożyć [łącznik usługi RMS i skonfigurować serwery Exchange](/azure/information-protection/deploy-rms-connector). 

## <a name="how-to-configure-a-label-for-encryption"></a>Jak skonfigurować etykietę na potrzeby szyfrowania

1. Postępuj zgodnie z ogólnymi instrukcjami, aby [utworzyć lub edytować etykietę poufności](create-sensitivity-labels.md#create-and-configure-sensitivity-labels) i upewnij się, że dla zakresu etykiety wybrano opcję **Pliki & wiadomości e-mail** : 
    
    ![Opcje zakresu etykiet poufności dla plików i wiadomości e-mail.](../media/filesandemails-scope-options-sensitivity-label.png)

2. Następnie na stronie **Wybieranie ustawień ochrony plików i wiadomości e-mail** upewnij się, że **wybrano pozycję Szyfruj pliki i wiadomości e-mail**
    
    ![Opcje ochrony etykiet poufności dla plików i wiadomości e-mail.](../media/protection-options-sensitivity-label.png)

4.  Na stronie **Szyfrowanie** wybierz jedną z następujących opcji:
    
    - **Usuń szyfrowanie, jeśli plik jest zaszyfrowany**: ta opcja jest obsługiwana tylko przez klienta ujednoliconego etykietowania na platformie Azure Information Protection. Po wybraniu tej opcji i użyciu wbudowanego etykietowania etykieta może nie być wyświetlana w aplikacjach lub wyświetlana i nie wprowadzać żadnych zmian szyfrowania.
        
        Aby uzyskać więcej informacji na temat tego scenariusza, zobacz [sekcję Co się stanie z istniejącym szyfrowaniem po zastosowaniu etykiety](#what-happens-to-existing-encryption-when-a-labels-applied) . Ważne jest, aby zrozumieć, że to ustawienie może spowodować powstanie etykiety poufności, którą użytkownicy mogą nie być w stanie zastosować, gdy nie mają wystarczających uprawnień.
    
    - **Konfigurowanie ustawień szyfrowania**: włącza szyfrowanie i sprawia, że ustawienia szyfrowania są widoczne:
        
        ![Opcje etykiet poufności na potrzeby szyfrowania.](../media/encrytion-options-sensitivity-label.png)
        
        Instrukcje dotyczące tych ustawień znajdują się w [następującej sekcji Konfigurowanie ustawień szyfrowania](#configure-encryption-settings) .

### <a name="what-happens-to-existing-encryption-when-a-labels-applied"></a>Co się stanie z istniejącym szyfrowaniem po zastosowaniu etykiety

Jeśli etykieta poufności jest stosowana do niezaszyfrowanej zawartości, wynikiem opcji szyfrowania, które można wybrać, jest objaśnianie samodzielne. Jeśli na przykład nie **wybrano opcji Szyfruj pliki i wiadomości e-mail**, zawartość pozostaje niezaszyfrowana.

Jednak zawartość może być już zaszyfrowana. Na przykład inny użytkownik mógł zastosować:

- Ich własne uprawnienia, które obejmują uprawnienia zdefiniowane przez użytkownika po wyświetleniu monitu przez etykietę, uprawnienia niestandardowe klienta usługi Azure Information Protection oraz ochronę dokumentu **z ograniczonym dostępem** z poziomu aplikacja pakietu Office.
- Szablon ochrony usługi Azure Rights Management, który szyfruje zawartość niezależnie od etykiety. Ta kategoria obejmuje reguły przepływu poczty, które stosują szyfrowanie przy użyciu ochrony praw.
- Etykieta, która stosuje szyfrowanie z uprawnieniami przypisanymi przez administratora.

W poniższej tabeli określono, co dzieje się z istniejącym szyfrowaniem w przypadku zastosowania etykiety poufności do tej zawartości:

| | Szyfrowanie: nie zaznaczono | Szyfrowanie: skonfigurowane | Szyfrowanie: usuwanie <sup>\*</sup> |
|:-----|:-----|:-----|:-----|
|**Uprawnienia określone przez użytkownika**|Oryginalne szyfrowanie jest zachowywane|Zastosowano nowe szyfrowanie etykiet|Oryginalne szyfrowanie jest usuwane|
|**Szablon ochrony**|Oryginalne szyfrowanie jest zachowywane|Zastosowano nowe szyfrowanie etykiet|Oryginalne szyfrowanie jest usuwane|
|**Etykieta z uprawnieniami zdefiniowanymi przez administratora**|Oryginalne szyfrowanie jest usuwane|Zastosowano nowe szyfrowanie etykiet|Oryginalne szyfrowanie jest usuwane|

**Przypisie:**

<sup>\*</sup>Obsługiwane przez klienta ujednoliconego etykietowania platformy Azure Information Protection

W przypadkach, gdy nowe szyfrowanie etykiet jest stosowane lub oryginalne szyfrowanie jest usuwane, dzieje się tak tylko wtedy, gdy użytkownik stosujący etykietę ma prawo użytkowania lub rolę, która obsługuje tę akcję:

- [Prawo użycia](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) — eksport lub pełna kontrola.
- Rola [wystawcy usługi Rights Management, właściciela usługi Rights Management](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) lub [administratora](/azure/information-protection/configure-super-users).

Jeśli użytkownik nie ma jednego z tych praw lub ról, nie można zastosować etykiety, a więc oryginalne szyfrowanie zostanie zachowane. Użytkownik widzi następujący komunikat: **Nie masz uprawnień do wprowadzenia tej zmiany w etykiecie poufności. Skontaktuj się z właścicielem zawartości.**

Na przykład osoba, która stosuje pozycję Nie przesyłaj dalej do wiadomości e-mail, może ponownie oznaczać wątek w celu zastąpienia szyfrowania lub usunięcia go, ponieważ jest właścicielem usługi Rights Management dla wiadomości e-mail. Jednak z wyjątkiem superużytków adresaci tej wiadomości e-mail nie mogą jej ponownie oznaczać, ponieważ nie mają wymaganych praw użytkowania.

#### <a name="email-attachments-for-encrypted-email-messages"></a>Załączniki wiadomości e-mail dla zaszyfrowanych wiadomości e-mail

Gdy wiadomość e-mail jest szyfrowana za pomocą dowolnej metody, wszystkie niezaszyfrowane Office dokumenty dołączone do wiadomości e-mail automatycznie dziedziczą te same ustawienia szyfrowania.

Dokumenty, które są już zaszyfrowane, a następnie dodawane jako załączniki, zawsze zachowują oryginalne szyfrowanie.

## <a name="configure-encryption-settings"></a>Konfigurowanie ustawień szyfrowania

Po wybraniu pozycji **Konfiguruj ustawienia szyfrowania** na stronie **Szyfrowanie** , aby utworzyć lub edytować etykietę poufności, wybierz jedną z następujących opcji:

- **Przypisz teraz uprawnienia**, aby można było dokładnie określić, którzy użytkownicy uzyskują uprawnienia do zawartości z zastosowanymi etykietami. Aby uzyskać więcej informacji, zobacz następną sekcję [Przypisywanie uprawnień teraz](#assign-permissions-now).
- **Zezwalaj użytkownikom na przypisywanie uprawnień** , gdy użytkownicy zastosują etykietę do zawartości. Dzięki tej opcji możesz zezwolić osobom w organizacji na pewną elastyczność, która może wymagać współpracy i wykonania pracy. Aby uzyskać więcej informacji, zobacz sekcję [Zezwalaj użytkownikom na przypisywanie uprawnień](#let-users-assign-permissions) na tej stronie.

Jeśli na przykład masz etykietę poufności o nazwie **Wysoce poufne** , która zostanie zastosowana do najbardziej poufnej zawartości, możesz zdecydować teraz, kto otrzyma uprawnienia jakiego typu do tej zawartości.

Alternatywnie, jeśli masz etykietę poufności o nazwie **Kontrakty biznesowe**, a przepływ pracy organizacji wymaga, aby użytkownicy współpracowali nad tą zawartością z różnymi osobami ad hoc, możesz zezwolić użytkownikom na decydowanie, kto otrzymuje uprawnienia podczas przypisywania etykiety. Ta elastyczność ułatwia zarówno produktywność użytkowników, jak i zmniejsza liczbę żądań administratorów dotyczących aktualizacji lub tworzenia nowych etykiet poufności w celu rozwiązania określonych scenariuszy.

Określ, czy chcesz teraz przypisać uprawnienia, czy zezwolić użytkownikom na przypisywanie uprawnień:

![Opcja dodawania uprawnień zdefiniowanych przez użytkownika lub administratora.](../media/sensitivity-label-user-or-admin-defined-permissions.png)

## <a name="assign-permissions-now"></a>Przypisz teraz uprawnienia

Użyj następujących opcji, aby kontrolować, kto może uzyskiwać dostęp do poczty e-mail lub dokumentów, do których jest stosowana ta etykieta. Można:

- **Zezwalaj na wygaśnięcie dostępu do zawartości oznaczonej etykietą** w określonym dniu lub po określonej liczbie dni po zastosowaniu etykiety. Po tym czasie użytkownicy nie będą mogli otworzyć oznaczonego elementu. Jeśli określisz datę, będzie ona obowiązywać o północy w tej dacie w bieżącej strefie czasowej. (Należy pamiętać, że niektórzy klienci poczty e-mail mogą nie wymuszać wygaśnięcia i wyświetlać wiadomości e-mail po dacie wygaśnięcia ze względu na mechanizmy buforowania).

- **Zezwalaj na dostęp w trybie offline** nigdy, zawsze lub przez określoną liczbę dni po zastosowaniu etykiety. Jeśli ograniczysz dostęp w trybie offline do wartości nigdy lub do kilku dni, po osiągnięciu tego progu użytkownicy muszą zostać ponownie uwierzytelnieni, a ich dostęp zostanie zarejestrowany. Aby uzyskać więcej informacji, zobacz następną sekcję dotyczącą licencji użycia usługi Rights Management.

Ustawienia kontroli dostępu do zaszyfrowanej zawartości:

![Ustawienia uprawnień zdefiniowanych przez administratora.](../media/sensitivity-encryption-settings-for-admin-defined-permissions.png)

### <a name="rights-management-use-license-for-offline-access"></a>Licencja na korzystanie z usługi Rights Management na potrzeby dostępu w trybie offline

Gdy użytkownik otworzy dokument lub wiadomość e-mail chronioną przez szyfrowanie z usługi Azure Rights Management, użytkownikowi zostanie udzielona licencja na korzystanie z usługi Azure Rights Management. Ta licencja użycia to certyfikat zawierający prawa użytkowania dokumentu lub wiadomości e-mail użytkownika oraz klucz szyfrowania, który był używany do szyfrowania zawartości. Licencja użytkowania zawiera również datę wygaśnięcia, jeśli została ustawiona i jak długo licencja użytkowania jest ważna.

Jeśli nie ustawiono daty wygaśnięcia, domyślny okres ważności licencji użycia dzierżawy wynosi 30 dni. Na czas trwania licencji użytkowania użytkownik nie jest ponownie uwierzytelniony ani ponownie autoryzowany dla zawartości. Ten proces umożliwia użytkownikowi dalsze otwieranie chronionego dokumentu lub wiadomości e-mail bez połączenia z Internetem. Gdy okres ważności licencji użytkowania wygaśnie, następnym razem, gdy użytkownik uzyskuje dostęp do chronionego dokumentu lub wiadomości e-mail, użytkownik musi zostać ponownie uwierzytelniony i ponownie uwierzytelniony.

Oprócz ponownego uwierzytelniania ustawienia szyfrowania i członkostwo w grupach użytkowników są ponownie oceniane. Oznacza to, że użytkownicy mogą doświadczyć różnych wyników dostępu dla tego samego dokumentu lub wiadomości e-mail, jeśli w ustawieniach szyfrowania lub członkostwie w grupie nastąpiły zmiany od momentu ostatniego uzyskania dostępu do zawartości.

Aby dowiedzieć się, jak zmienić domyślne ustawienie 30-dniowe, zobacz [Licencja użycia usługi Rights Management](/azure/information-protection/configure-usage-rights#rights-management-use-license).

### <a name="assign-permissions-to-specific-users-or-groups"></a>Przypisywanie uprawnień do określonych użytkowników lub grup

Możesz przyznać uprawnienia określonym osobom, aby tylko oni mogli wchodzić w interakcje z zawartością oznaczoną etykietą:

1. Najpierw dodaj użytkowników lub grupy, do których zostaną przypisane uprawnienia do zawartości oznaczonej etykietą.

2. Następnie wybierz uprawnienia, które użytkownicy powinni mieć dla zawartości oznaczonej etykietą.

Przypisywanie uprawnień:

![Opcje przypisywania uprawnień użytkownikom.](../media/Sensitivity-Assign-permissions-settings.png)

#### <a name="add-users-or-groups"></a>Dodawanie użytkowników lub grup

Podczas przypisywania uprawnień można wybrać następujące opcje:

- Wszyscy w organizacji (wszyscy członkowie dzierżawy). To ustawienie wyklucza konta gościa.

- Wszyscy uwierzytelnieni użytkownicy. Przed wybraniem tego ustawienia upewnij się, że znasz [wymagania i ograniczenia](#requirements-and-limitations-for-add-any-authenticated-users) tego ustawienia.

- Dowolny konkretny użytkownik lub grupa zabezpieczeń z obsługą poczty e-mail, grupa dystrybucyjna lub grupa Microsoft 365 ([wcześniej grupa Office 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601)) w usłudze Azure AD. Grupa Microsoft 365 może mieć członkostwo statyczne lub [dynamiczne](/azure/active-directory/users-groups-roles/groups-create-rule). Należy pamiętać, że nie można używać [dynamicznej grupy dystrybucyjnej z Exchange](/Exchange/recipients/dynamic-distribution-groups/dynamic-distribution-groups), ponieważ ten typ grupy nie jest synchronizowany z usługą Azure AD i nie można używać grupy zabezpieczeń, która nie jest włączona przy użyciu poczty e-mail.
    
    Chociaż można określić grupy zawierające kontakty pocztowe jako wygodną metodę udzielania dostępu wielu osobom spoza organizacji, obecnie istnieje znany problem z tą konfiguracją. Aby uzyskać więcej informacji, zobacz [Kontakty poczty w grupach mają sporadyczny dostęp do zaszyfrowanej zawartości](/office365/troubleshoot/sensitivity-labels/mail-contacts-lose-access-encrypted-content).

- Dowolny adres e-mail lub domena. Użyj tej opcji, aby określić wszystkich użytkowników w innej organizacji, którzy korzystają z usługi Azure AD, wprowadzając dowolną nazwę domeny z tej organizacji. Możesz również użyć tej opcji dla dostawców społecznościowych, wprowadzając ich nazwę domeny, taką jak **gmail.com**, **hotmail.com** lub **outlook.com**.

    > [!NOTE]
    > Jeśli określisz domenę z organizacji korzystającej z usługi Azure AD, nie możesz ograniczyć dostępu do tej określonej domeny. Zamiast tego wszystkie zweryfikowane domeny w usłudze Azure AD są automatycznie uwzględniane dla dzierżawy, która jest właścicielem określonej nazwy domeny.

Po wybraniu wszystkich użytkowników i grup w organizacji lub przeglądaniu katalogu użytkownicy lub grupy muszą mieć adres e-mail.

Najlepszym rozwiązaniem jest użycie grup, a nie użytkowników. Ta strategia sprawia, że konfiguracja jest prostsza.

##### <a name="requirements-and-limitations-for-add-any-authenticated-users"></a>Wymagania i ograniczenia dotyczące "Dodawania uwierzytelnionych użytkowników"

To ustawienie nie ogranicza tego, kto może uzyskiwać dostęp do zawartości szyfrowanej przez etykietę, jednocześnie szyfrując zawartość i udostępniając opcje ograniczające sposób użycia zawartości (uprawnienia) i uzyskiwania do niej dostępu (wygaśnięcie i dostęp w trybie offline). Jednak aplikacja otwierająca zaszyfrowaną zawartość musi być w stanie obsługiwać używane uwierzytelnianie. Z tego powodu federacyjni dostawcy usług społecznościowych, tacy jak Google, i jednorazowe uwierzytelnianie kodem dostępu działają tylko w przypadku poczty e-mail i tylko wtedy, gdy używasz Exchange Online. Konta Microsoft mogą być używane z aplikacjami Office 365 i [przeglądarką usługi Azure Information Protection](https://portal.azurerms.com/#/download).

> [!NOTE]
> Rozważ użycie tego ustawienia z [integracją SharePoint i OneDrive z usługą Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview), gdy etykiety poufności są [włączone dla plików Office w SharePoint i OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

Niektóre typowe scenariusze dla wszystkich ustawień uwierzytelnionych użytkowników:

- Nie masz nic przeciwko temu, kto wyświetla zawartość, ale chcesz ograniczyć sposób jej użycia. Na przykład nie chcesz, aby zawartość była edytowana, kopiowana ani drukowana.
- Nie musisz ograniczać tego, kto uzyskuje dostęp do zawartości, ale chcesz mieć możliwość potwierdzenia, kto ją otworzy.
- Musisz wymagać, aby zawartość była szyfrowana w spoczynku i przesyłana, ale nie wymaga kontroli dostępu.

#### <a name="choose-permissions"></a>Wybieranie uprawnień

Po wybraniu uprawnień, które mają być dozwolone dla tych użytkowników lub grup, możesz wybrać jedną z następujących opcji:

- [Wstępnie zdefiniowany poziom uprawnień](/azure/information-protection/configure-usage-rights#rights-included-in-permissions-levels) z wstępnie ustawioną grupą praw, taką jak Co-Author lub Recenzent.
- Uprawnienia niestandardowe, w których wybierasz co najmniej jedno prawo użytkowania.

Aby uzyskać więcej informacji, które pomogą Ci wybrać odpowiednie uprawnienia, zobacz [Prawa do użycia i opisy](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions).  

![Opcje wyboru uprawnień wstępnych lub niestandardowych.](../media/Sensitivity-Choose-permissions-settings.png)

Należy pamiętać, że ta sama etykieta może przyznać różne uprawnienia różnym użytkownikom. Na przykład pojedyncza etykieta może przypisać niektórych użytkowników jako recenzentów i innego użytkownika jako współautora, jak pokazano na poniższym zrzucie ekranu.

W tym celu dodaj użytkowników lub grupy, przypisz im uprawnienia i zapisz te ustawienia. Następnie powtórz te kroki, dodając użytkowników i przypisując im uprawnienia, zapisując ustawienia za każdym razem. Tę konfigurację można powtarzać tak często, jak to konieczne, aby zdefiniować różne uprawnienia dla różnych użytkowników.

![Różni użytkownicy z różnymi uprawnieniami.](../media/Sensitivity-Multiple-users-permissions.png)

#### <a name="rights-management-issuer-user-applying-the-sensitivity-label-always-has-full-control"></a>Wystawca usługi Rights Management (użytkownik stosujący etykietę poufności) zawsze ma pełną kontrolę

Szyfrowanie etykiety poufności używa usługi Azure Rights Management z usługi Azure Information Protection. Gdy użytkownik stosuje etykietę poufności w celu ochrony dokumentu lub wiadomości e-mail przy użyciu szyfrowania, ten użytkownik staje się wystawcą usługi Rights Management dla tej zawartości.

Wystawcy usługi Rights Management zawsze otrzymuje uprawnienia pełnej kontroli dla dokumentu lub wiadomości e-mail, a ponadto:

- Jeśli ustawienia szyfrowania obejmują datę wygaśnięcia, wystawcy usługi Rights Management nadal może otworzyć i edytować dokument lub wiadomość e-mail po tej dacie.
- Wystawca usługi Rights Management zawsze może uzyskać dostęp do dokumentu lub wiadomości e-mail w trybie offline.
- Wystawca usługi Rights Management nadal może otworzyć dokument po jego odwołaniu.

Aby uzyskać więcej informacji, zobacz [Wystawcę usługi Rights Management i właściciela usługi Rights Management](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner).

### <a name="double-key-encryption"></a>Podwójne szyfrowanie kluczy

> [!NOTE]
> Ta funkcja jest obecnie obsługiwana tylko przez klienta ujednoliconego etykietowania usługi Azure Information Protection.

Wybierz tę opcję dopiero po skonfigurowaniu usługi podwójnego szyfrowania kluczy i musisz użyć tego szyfrowania podwójnym kluczem dla plików, które będą miały tę etykietę. Po skonfigurowaniu i zapisaniu etykiety nie będzie można jej edytować.

Aby uzyskać więcej informacji, wymagania wstępne i instrukcje konfiguracji, zobacz [Podwójne szyfrowanie kluczy (DKE).](double-key-encryption.md)

## <a name="let-users-assign-permissions"></a>Zezwalaj użytkownikom na przypisywanie uprawnień

> [!IMPORTANT]
> Nie wszyscy klienci etykietowania obsługują wszystkie opcje, które umożliwiają użytkownikom przypisywanie własnych uprawnień. Skorzystaj z tej sekcji, aby dowiedzieć się więcej.

Następujące opcje umożliwiają użytkownikom przypisywanie uprawnień, gdy ręcznie zastosują etykietę poufności do zawartości:

- W Outlook użytkownik może wybrać ograniczenia równoważne opcji [Nie przesyłaj dalej](/azure/information-protection/configure-usage-rights#do-not-forward-option-for-emails) lub [Tylko szyfrowanie](/azure/information-protection/configure-usage-rights#encrypt-only-option-for-emails) dla wybranych adresatów.
    
    Opcja Nie przesyłaj dalej jest obsługiwana przez wszystkich klientów poczty e-mail, którzy obsługują etykiety poufności. Jednak zastosowanie opcji **Encrypt-Only** z etykietą poufności jest nowszą wersją obsługiwaną tylko przez wbudowane etykietowanie, a nie klienta ujednoliconego etykietowania usługi Azure Information Protection. W przypadku klientów poczty e-mail, którzy nie obsługują tej funkcji, etykieta nie będzie widoczna.
    
    Aby sprawdzić minimalne wersje aplikacji Outlook, które używają wbudowanego etykietowania do obsługi stosowania opcji Encrypt-Only z etykietą poufności, użyj [tabeli możliwości dla Outlook](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-outlook) i **wiersza Zezwalaj użytkownikom na przypisywanie uprawnień: — Tylko szyfrowanie**.

- W programach Word, PowerPoint i Excel użytkownik jest monitowany o wybranie własnych uprawnień dla określonych użytkowników, grup lub organizacji.

    Ta opcja jest obsługiwana przez klienta ujednoliconego etykietowania usługi Azure Information Protection oraz przez niektóre aplikacje korzystające z wbudowanego etykietowania. W przypadku aplikacji, które nie obsługują tej możliwości, etykieta nie będzie widoczna dla użytkowników lub etykieta jest widoczna dla spójności, ale nie można jej zastosować z komunikatem objaśnienia dla użytkowników.
    
    Aby sprawdzić, które aplikacje korzystające z wbudowanego etykietowania obsługują tę opcję, użyj [tabeli możliwości programu Word, Excel i PowerPoint](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) oraz **wiersza Zezwalaj użytkownikom na przypisywanie uprawnień: — Monituj użytkowników**.

Gdy opcje są obsługiwane, użyj poniższej tabeli, aby określić, kiedy użytkownicy zobaczą etykietę poufności:

|Ustawienie |Etykieta widoczna w Outlook|Etykieta widoczna w programie Word, Excel, PowerPoint|
|:-----|:-----|:-----|:-----|
|**W Outlook wymuszaj ograniczenia za pomocą opcji Nie przesyłaj dalej lub Encrypt-Only**|Tak |Nie |
|**W programie Word PowerPoint i Excel monituj użytkowników o określenie uprawnień**|Nie |Tak|

Po wybraniu obu ustawień etykieta jest widoczna zarówno w Outlook, jak i w programie Word, Excel i PowerPoint.

Etykieta poufności, która umożliwia użytkownikom przypisywanie uprawnień, musi być stosowana do zawartości ręcznie przez użytkowników; nie może być automatycznie stosowany ani używany jako zalecana etykieta.

Konfigurowanie uprawnień przypisanych przez użytkownika:

![Ustawienia szyfrowania dla uprawnień zdefiniowanych przez użytkownika.](../media/sensitivity-encryption-settings-for-user-defined-permissions.png)

### <a name="outlook-restrictions"></a>ograniczenia Outlook

W Outlook, gdy użytkownik stosuje etykietę poufności, która umożliwia mu przypisywanie uprawnień do wiadomości, możesz wybrać **opcję Nie przesyłaj dalej** lub **Tylko szyfrowanie**. W górnej części komunikatu zostanie wyświetlona nazwa etykiety i opis, co wskazuje, że zawartość jest chroniona. W przeciwieństwie do programu Word, PowerPoint i Excel (zobacz [następną sekcję](#word-powerpoint-and-excel-permissions)), użytkownicy nie są monitowane o wybranie określonych uprawnień.

![Etykieta poufności zastosowana do komunikatu w Outlook.](../media/sensitivity-label-outlook-protection-applied.png)

Gdy któraś z tych opcji zostanie zastosowana do wiadomości e-mail, wiadomość e-mail zostanie zaszyfrowana, a adresaci muszą zostać uwierzytelnieni. Następnie adresaci automatycznie mają ograniczone prawa użytkowania:

- **Nie przesyłaj dalej**: adresaci nie mogą przesyłać dalej wiadomości e-mail, drukować jej ani kopiować. Na przykład w kliencie Outlook przycisk Prześlij dalej jest niedostępny, opcje menu Zapisz jako i Drukuj nie są dostępne i nie można dodawać ani zmieniać adresatów w polach Do, DW lub BCC.
    
    Aby uzyskać więcej informacji na temat działania tej opcji, zobacz [Nie przesyłaj dalej opcji wiadomości e-mail](/azure/information-protection/configure-usage-rights#do-not-forward-option-for-emails).

- **Tylko szyfrowanie**: adresaci mają wszystkie prawa użytkowania z wyjątkiem opcji Zapisz jako, Eksportuj i Pełna kontrola. Ta kombinacja praw użytkowania oznacza, że adresaci nie mają żadnych ograniczeń, z wyjątkiem tego, że nie mogą usunąć ochrony. Na przykład adresat może skopiować wiadomość e-mail, wydrukować ją i przesłać dalej.
    
    Aby uzyskać więcej informacji na temat działania tej opcji, zobacz [Opcja tylko szyfrowania dla wiadomości e-mail](/azure/information-protection/configure-usage-rights#encrypt-only-option-for-emails).

Niezaszyfrowane Office dokumenty dołączone do wiadomości e-mail automatycznie dziedziczą te same ograniczenia. W przypadku pozycji Nie przesyłaj dalej prawa użytkowania stosowane do tych dokumentów to Edytuj zawartość, Edytuj; Zapisz; Wyświetl, Otwórz, Odczyt; i Zezwalaj na makra. Jeśli użytkownik chce mieć inne prawa użytkowania załącznika lub załącznik nie jest dokumentem Office, który obsługuje tę dziedziczoną ochronę, użytkownik musi zaszyfrować plik przed dołączeniem go do wiadomości e-mail.

### <a name="word-powerpoint-and-excel-permissions"></a>Uprawnienia programu Word, PowerPoint i Excel

W programie Word, PowerPoint i Excel, gdy użytkownik zastosuje etykietę poufności, która umożliwia mu przypisanie uprawnień do dokumentu, zostanie wyświetlony monit o określenie ich wyboru użytkowników i uprawnień po zastosowaniu szyfrowania.

Na przykład w przypadku klienta ujednoliconego etykietowania usługi Azure Information Protection, chyba że [włączono współtworzenie](sensitivity-labels-coauthoring.md), użytkownicy mogą:

- Wybierz poziom uprawnień, taki jak Przeglądarka (która przypisuje uprawnienie Tylko widok) lub Co-Author (który przypisuje uprawnienia Widok, Edycja, Kopiuj i Drukuj).
- Wybierz użytkowników, grupy lub organizacje. Może to obejmować osoby zarówno w organizacji, jak i poza nią.
- Ustaw datę wygaśnięcia, po której wybrani użytkownicy nie będą mogli uzyskać dostępu do zawartości. Aby uzyskać więcej informacji, zobacz powyższą sekcję [Licencja użycia usługi Rights Management na potrzeby dostępu w trybie offline](#rights-management-use-license-for-offline-access).

![Opcje ochrony użytkownika przy użyciu uprawnień niestandardowych.](../media/sensitivity-aip-custom-permissions-dialog.png)

W przypadku etykietowania wbudowanego i klienta ujednoliconego etykietowania usługi Azure Information Protection, gdy [jest włączone współtworzenie](sensitivity-labels-coauthoring.md), użytkownicy widzą to samo okno dialogowe, tak jak w przypadku wybrania następujących opcji:

- Windows: Karta **Plik** > **InfoProtect** >  **DocumentRestrict** >  **AccessRestricted Access** > 

- macOS: **karta Przeglądanie** > **ProtectionPermissionsRestricted** >  >  **Access**

> [!TIP]
> Jeśli użytkownicy byli zaznajomieni z konfigurowaniem uprawnień niestandardowych przy użyciu klienta ujednoliconego etykietowania usługi Azure Information Protection przed [włączeniem współtworzenia](sensitivity-labels-coauthoring.md), warto przejrzeć mapowanie poziomów uprawnień na indywidualne prawa użytkowania: [Prawa uwzględnione na poziomach uprawnień](/azure/information-protection/configure-usage-rights#rights-included-in-permissions-levels).

## <a name="example-configurations-for-the-encryption-settings"></a>Przykładowe konfiguracje ustawień szyfrowania

Dla każdego poniższego przykładu wykonaj konfigurację na stronie **Szyfrowanie** po wybraniu opcji **Konfiguruj ustawienia szyfrowania** :

![Zastosuj opcję szyfrowania w kreatorze etykiet poufności.](../media/apply-encryption-option.png)

### <a name="example-1-label-that-applies-do-not-forward-to-send-an-encrypted-email-to-a-gmail-account"></a>Przykład 1: Etykieta, która ma zastosowanie Nie przesyłaj dalej w celu wysyłania zaszyfrowanej wiadomości e-mail na konto Gmail

Ta etykieta jest wyświetlana tylko w Outlook i Outlook w sieci Web i należy użyć Exchange Online. Poproś użytkowników, aby wybrali tę etykietę, gdy będą musieli wysłać zaszyfrowaną wiadomość e-mail do osób korzystających z konta Gmail (lub dowolnego innego konta e-mail spoza organizacji).

Użytkownicy wpiszą adres e-mail Gmail w polu **Do** .  Następnie wybierają etykietę, a opcja Nie przesyłaj dalej jest automatycznie dodawana do wiadomości e-mail. W rezultacie adresaci nie mogą przesyłać dalej wiadomości e-mail ani drukować jej, kopiować ani zapisywać wiadomości e-mail poza skrzynką pocztową przy użyciu opcji **Zapisz jako** .

1. Na stronie **Szyfrowanie** : Aby **przypisać uprawnienia teraz lub zezwolić użytkownikom na podjęcie decyzji?** wybierz pozycję **Zezwalaj użytkownikom na przypisywanie uprawnień podczas stosowania etykiety**.

2. Zaznacz pole wyboru: **W Outlook wymuś ograniczenia równoważne opcji Nie przesyłaj dalej**.

3. Jeśli to pole jest zaznaczone, wyczyść pole wyboru: **w programie Word PowerPoint i Excel monituj użytkowników o określenie uprawnień**.

4. Wybierz pozycję **Dalej** i zakończ konfigurację.

### <a name="example-2-label-that-restricts-read-only-permission-to-all-users-in-another-organization"></a>Przykład 2: Etykieta ograniczająca uprawnienia tylko do odczytu dla wszystkich użytkowników w innej organizacji

Ta etykieta jest odpowiednia do udostępniania bardzo poufnych dokumentów jako tylko do odczytu, a dokumenty zawsze wymagają połączenia internetowego, aby je wyświetlić.

Ta etykieta nie jest odpowiednia dla wiadomości e-mail.

1. Na stronie **Szyfrowanie** : Aby **przypisać uprawnienia teraz lub zezwolić użytkownikom na podjęcie decyzji?** wybierz pozycję **Przypisz uprawnienia teraz**.

2. W obszarze **Zezwalaj na dostęp w trybie offline** wybierz pozycję **Nigdy**.

3. Wybierz pozycję **Przypisz uprawnienia**.

4. W okienku **Przypisywanie uprawnień** wybierz pozycję **Dodaj określone adresy e-mail lub domeny**.

5. W polu tekstowym wprowadź nazwę domeny z innej organizacji, na przykład **fabrikam.com**. Następnie wybierz pozycję **Dodaj**.

6. Wybierz **pozycję Wybierz uprawnienia**.

7. W okienku **Wybierz uprawnienia** wybierz pole rozwijane, wybierz pozycję **Podgląd**, a następnie wybierz pozycję **Zapisz**.

8. W okienku **Przypisywanie uprawnień** wybierz pozycję **Zapisz**.

9. Na stronie **Szyfrowanie** wybierz pozycję **Dalej** i zakończ konfigurację.

### <a name="example-3-add-external-users-to-an-existing-label-that-encrypts-content"></a>Przykład 3. Dodawanie użytkowników zewnętrznych do istniejącej etykiety, która szyfruje zawartość

Nowi użytkownicy, których dodasz, będą mogli otwierać dokumenty i wiadomości e-mail, które zostały już chronione za pomocą tej etykiety. Uprawnienia przyznawane tym użytkownikom mogą różnić się od uprawnień istniejących użytkowników.

1. Na stronie **Szyfrowanie** : Aby **przypisać uprawnienia teraz, czy zezwolić użytkownikom na podjęcie decyzji?** upewnij się, że teraz wybrano opcję **Przypisz uprawnienia** .

2. Wybierz pozycję **Przypisz uprawnienia**.

3. W okienku **Przypisywanie uprawnień** wybierz pozycję **Dodaj określone adresy e-mail lub domeny**.

4. W polu tekstowym wprowadź adres e-mail pierwszego użytkownika (lub grupy), który chcesz dodać, a następnie wybierz pozycję **Dodaj**.

5. Wybierz **pozycję Wybierz uprawnienia**.

6. W okienku **Wybierz uprawnienia** wybierz uprawnienia tego użytkownika (lub grupy), a następnie wybierz pozycję **Zapisz**.

7. W okienku **Przypisywanie uprawnień** powtórz kroki od 3 do 6 dla każdego użytkownika (lub grupy), który chcesz dodać do tej etykiety. Następnie kliknij przycisk **Zapisz**.

8. Na stronie **Szyfrowanie** wybierz pozycję **Dalej** i zakończ konfigurację.

### <a name="example-4-label-that-encrypts-content-but-doesnt-restrict-who-can-access-it"></a>Przykład 4: Etykieta, która szyfruje zawartość, ale nie ogranicza tego, kto może uzyskać do niej dostęp

Ta konfiguracja ma tę zaletę, że nie trzeba określać użytkowników, grup ani domen w celu szyfrowania wiadomości e-mail lub dokumentu. Zawartość będzie nadal szyfrowana i nadal można określić prawa użytkowania, datę wygaśnięcia i dostęp w trybie offline.

Ta konfiguracja jest używana tylko wtedy, gdy nie trzeba ograniczać tego, kto może otworzyć chroniony dokument lub wiadomość e-mail. [Więcej informacji na temat tego ustawienia](#requirements-and-limitations-for-add-any-authenticated-users)

1. Na stronie **Szyfrowanie** : Aby **przypisać uprawnienia teraz, czy zezwolić użytkownikom na podjęcie decyzji?** upewnij się, że teraz wybrano opcję **Przypisz uprawnienia** .

2. Skonfiguruj ustawienia dostępu **użytkownika do zawartości wygasa** i **zezwalaj na dostęp w trybie offline** zgodnie z wymaganiami.

3. Wybierz pozycję **Przypisz uprawnienia**.

4. W okienku **Przypisywanie uprawnień** wybierz pozycję **Dodaj wszystkich uwierzytelnionych użytkowników**.

    W obszarze **Użytkownicy i grupy** zobaczysz automatycznie **dodawanych uwierzytelnionych użytkowników** . Nie można zmienić tej wartości, tylko ją usunąć, co spowoduje anulowanie wyboru **Dodaj uwierzytelnionych użytkowników** .

5. Wybierz **pozycję Wybierz uprawnienia**.

6. W okienku **Wybierz uprawnienia** wybierz pole rozwijane, wybierz odpowiednie uprawnienia, a następnie wybierz pozycję **Zapisz**.

7. W okienku **Przypisywanie uprawnień** wybierz pozycję **Zapisz**.

8. Na stronie **Szyfrowanie** wybierz pozycję **Dalej** i zakończ konfigurację.

## <a name="considerations-for-encrypted-content"></a>Zagadnienia dotyczące zaszyfrowanej zawartości

Szyfrowanie najbardziej poufnych dokumentów i wiadomości e-mail pomaga zagwarantować, że tylko autoryzowane osoby będą mogły uzyskiwać dostęp do tych danych. Należy jednak wziąć pod uwagę pewne kwestie:

- Jeśli Twoja organizacja nie [włączyła etykiet poufności dla plików Office w SharePoint i OneDrive](sensitivity-labels-sharepoint-onedrive-files.md):

  - Wyszukiwanie, wykrywanie elektroniczne i Delve nie będą działać w przypadku zaszyfrowanych plików.
  - Zasady DLP działają dla metadanych tych zaszyfrowanych plików (w tym informacji o etykietach przechowywania), ale nie dla zawartości tych plików (takich jak numery kart kredytowych w plikach).
  - Użytkownicy nie mogą otwierać zaszyfrowanych plików przy użyciu Office w sieci Web. Gdy etykiety poufności dla plików Office w SharePoint i OneDrive są włączone, użytkownicy mogą używać Office w sieci Web do otwierania zaszyfrowanych plików, z [pewnymi ograniczeniami](sensitivity-labels-sharepoint-onedrive-files.md#limitations), które obejmują szyfrowanie zastosowane przy użyciu klucza lokalnego (znanego jako "hold your own key" lub HYOK), [podwójne szyfrowanie kluczy](#double-key-encryption) i szyfrowanie, które zostało zastosowane niezależnie od etykiety poufności.

- Jeśli udostępniasz zaszyfrowane dokumenty osobom spoza organizacji, może być konieczne utworzenie kont gościa i zmodyfikowanie zasad dostępu warunkowego. Aby uzyskać więcej informacji, zobacz [Udostępnianie zaszyfrowanych dokumentów użytkownikom zewnętrznym](sensitivity-labels-office-apps.md#support-for-external-users-and-labeled-content).

- Gdy autoryzowani użytkownicy otwierają zaszyfrowane dokumenty w swoich aplikacjach Office, widzą nazwę etykiety i opis na żółtym pasku komunikatów w górnej części aplikacji. Gdy uprawnienia szyfrowania rozciągają się na osoby spoza organizacji, dokładnie przejrzyj nazwy etykiet i opisy, które będą widoczne na tym pasku komunikatów po otwarciu dokumentu.

- Aby wielu użytkowników mogło edytować zaszyfrowany plik w tym samym czasie, wszyscy użytkownicy muszą używać Office dla sieci web lub [włączono współtworzenie plików zaszyfrowanych za pomocą etykiet poufności](sensitivity-labels-coauthoring.md), a wszyscy użytkownicy mają [Office aplikacje obsługujące tę funkcję](sensitivity-labels-coauthoring.md#prerequisites). Jeśli tak nie jest, a plik jest już otwarty:

  - W aplikacjach Office (Windows, Mac, Android i iOS) użytkownicy widzą komunikat **Plik w użyciu** z nazwiskiem osoby, która wyewidencjonowała plik. Następnie mogą wyświetlać kopię tylko do odczytu lub zapisywać i edytować kopię pliku oraz otrzymywać powiadomienia, gdy plik jest dostępny.
  - W Office dla sieci web użytkownicy widzą komunikat o błędzie, że nie mogą edytować dokumentu z innymi osobami. Następnie mogą wybrać pozycję **Otwórz w widoku do czytania**.

- Funkcja [automatycznego zapisywania](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) w aplikacjach Office dla systemów iOS i Android jest wyłączona dla zaszyfrowanych plików. Ta funkcja jest również wyłączona dla zaszyfrowanych plików na komputerach Windows i Mac, jeśli nie [włączono współtworzenia plików zaszyfrowanych za pomocą etykiet poufności](sensitivity-labels-coauthoring.md). Użytkownicy widzą komunikat, że plik ma ograniczone uprawnienia, które muszą zostać usunięte przed włączeniem automatycznego zapisywania.

- Otwieranie zaszyfrowanych plików w aplikacjach Office (Windows, Mac, Android i iOS może potrwać dłużej.

- Jeśli etykieta, która stosuje szyfrowanie, zostanie dodana przy użyciu aplikacja pakietu Office, gdy dokument zostanie [wyewidencjonowany w SharePoint](https://support.microsoft.com/office/check-out-check-in-or-discard-changes-to-files-in-a-library-7e2c12a9-a874-4393-9511-1378a700f6de), a następnie użytkownik odrzuci wyewidencjonowanie, dokument pozostanie oznaczony etykietą i zaszyfrowany.

- Jeśli [nie włączono współtworzenia plików zaszyfrowanych przy użyciu etykiet poufności](sensitivity-labels-coauthoring.md), następujące akcje dla zaszyfrowanych plików nie są obsługiwane przez aplikacje Office (Windows, Mac, Android i iOS), a użytkownicy widzą komunikat o błędzie informujący o tym, że wystąpił problem. Jednak SharePoint funkcje mogą być używane jako alternatywa:

  - Wyświetlanie, przywracanie i zapisywanie kopii poprzednich wersji. Alternatywnie użytkownicy mogą wykonywać te akcje przy użyciu Office w sieci Web podczas [włączania i konfigurowania przechowywania wersji dla listy lub biblioteki](https://support.office.com/article/enable-and-configure-versioning-for-a-list-or-library-1555d642-23ee-446a-990a-bcab618c7a37).
  - Zmień nazwę lub lokalizację plików. Alternatywnie użytkownicy mogą [zmienić nazwę pliku, folderu lub linku w bibliotece dokumentów](https://support.microsoft.com/office/rename-a-file-folder-or-link-in-a-document-library-bc493c1a-921f-4bc1-a7f6-985ce11bb185) w SharePoint.

Aby uzyskać najlepsze środowisko współpracy dla plików zaszyfrowanych za pomocą etykiety poufności, zalecamy używanie [etykiet poufności dla plików Office w SharePoint i OneDrive](sensitivity-labels-sharepoint-onedrive-files.md) i Office dla sieci web.



## <a name="next-steps"></a>Następne kroki

Chcesz udostępnić dokumenty oznaczone etykietami i zaszyfrowane osobom spoza organizacji?  Zobacz [Udostępnianie zaszyfrowanych dokumentów użytkownikom zewnętrznym](sensitivity-labels-office-apps.md#sharing-encrypted-documents-with-external-users).
