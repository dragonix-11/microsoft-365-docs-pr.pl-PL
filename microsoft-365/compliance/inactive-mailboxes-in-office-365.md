---
title: Dowiedz się więcej o nieaktywnych skrzynkach pocztowych
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 1fbd74e8-7a60-4157-afe8-fe79f05d2038
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się, jak zachować zawartość skrzynki pocztowej dla byłych pracowników, przekształcając skrzynkę pocztową w nieaktywną skrzynkę pocztową.
ms.openlocfilehash: 981675f64015e0320805e2be8e955cbd6d98769a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627222"
---
# <a name="learn-about-inactive-mailboxes"></a>Dowiedz się więcej o nieaktywnych skrzynkach pocztowych

Organizacja może wymagać zachowania poczty e-mail byłych pracowników po opuszczeniu organizacji. W zależności od wymagań dotyczących przechowywania w organizacji może być konieczne zachowanie zawartości skrzynki pocztowej przez kilka miesięcy lub lat po zakończeniu zatrudnienia lub może być konieczne zachowanie zawartości skrzynki pocztowej na czas nieokreślony. Niezależnie od tego, jak długo trzeba zachować pocztę e-mail, możesz utworzyć nieaktywne skrzynki pocztowe, aby zachować skrzynkę pocztową byłych pracowników.

## <a name="what-are-inactive-mailboxes"></a>Co to są nieaktywne skrzynki pocztowe?

Gdy pracownik opuszcza organizację (lub przechodzi na dłuższy urlop), możesz usunąć jego konto platformy Microsoft 365. Dane skrzynki pocztowej pracownika są przechowywane przez 30 dni po usunięciu konta. W tym okresie nadal można odzyskać dane skrzynki pocztowej, cofając usunięcie konta. Po 30 dniach dane zostaną trwale usunięte.

Jeśli jednak do skrzynki pocztowej zostanie zastosowana blokada przed usunięciem konta platformy Microsoft 365, skrzynka pocztowa zostanie przekonwertowana na nieaktywną skrzynkę pocztową. Poniższe sekcje zawierają informacje o blokadach, które można zastosować w przypadku przechowywania i zbierania elektronicznych materiałów dowodowych platformy Microsoft 365.

Nieaktywne skrzynki pocztowe są przydatne, gdy organizacja musi zachować zawartość skrzynki pocztowej byłych pracowników z przyczyn prawnych lub innych. Mimo że dowolny typ blokady wymieniony w tym dokumencie wymusi nieaktywność skrzynki pocztowej po usunięciu obiektu użytkownika, zalecamy wykonanie tej czynności przez zastosowanie zasad przechowywania lub etykiet przechowywania platformy Microsoft 365, [potwierdzenie zastosowania blokady](#confirming-a-hold-is-applied-to-a-mailbox), a następnie usunięcie odpowiedniego konta platformy Microsoft 365. W tym momencie zawartość nieaktywnej skrzynki pocztowej jest przechowywana przez czas trwania okresu przechowywania określonego przed usunięciem konta użytkownika. Nadal można odzyskać odpowiednie konto użytkownika przez okres 30 dni, jednak po 30 dniach skrzynka pocztowa jest przechowywana w usłudze Microsoft 365 jako nieaktywna skrzynka pocztowa do momentu usunięcia zasad przechowywania lub etykiet przechowywania.

> [!IMPORTANT]
> Jak wspomniano wcześniej, zalecamy użycie przechowywania platformy Microsoft 365 w celu utworzenia nieaktywnej skrzynki pocztowej:
> - In-Place Blokady w centrum administracyjnym programu Exchange są teraz wycofywane. Od 1 lipca 2020 r. nie można utworzyć nowych blokad In-Place w Exchange Online. Od 1 października 2020 r. nie można już zmienić czasu trwania blokady miejscowej. Każdą nieaktywną skrzynkę pocztową z zastosowaną blokadą In-Place można usunąć tylko przez usunięcie blokady In-Place. Istniejące nieaktywne skrzynki pocztowe znajdujące się w In-Place Blokada będą nadal zachowywane do momentu usunięcia blokady. Aby uzyskać więcej informacji na temat wycofywania In-Place, zobacz [Wycofywanie starszych narzędzi zbierania elektronicznych materiałów dowodowych](legacy-ediscovery-retirement.md).
> 
> - [Blokada postępowania sądowego](create-a-litigation-hold.md) pozostaje obsługiwana jako alternatywna metoda przechowywania zawartości w skrzynce pocztowej i uniemożliwiania jej działania po usunięciu konta użytkownika. Jednak jako starsza technologia zalecamy użycie przechowywania na platformie Microsoft 365.

Jeśli istnieje wiele blokad tej samej zawartości, [zasada przechowywania ma zastosowanie](retention.md#the-principles-of-retention-or-what-takes-precedence) , a zawartość jest przechowywana przez najdłuższy okres.

### <a name="confirming-a-hold-is-applied-to-a-mailbox"></a>Potwierdzanie zastosowania blokady do skrzynki pocztowej

Niezależnie od tego, czy stosujesz zasady przechowywania platformy Microsoft 365, etykiety przechowywania, blokadę zbierania elektronicznych materiałów dowodowych, blokadę postępowania sądowego czy istniejącą blokadę In-Place, możesz potwierdzić, że blokada została pomyślnie zastosowana do skrzynki pocztowej przy użyciu programu PowerShell. Jeśli blokada została ostatnio skonfigurowana, może być konieczne poczekanie na zastosowanie jej do skrzynki pocztowej.

Aby zapobiec przypadkowemu lub niezamierzonemu usunięciu, zalecamy potwierdzenie blokady przed usunięciem konta użytkownika. Jeśli blokada nie zostanie zastosowana, skrzynka pocztowa nie zostanie przekonwertowana na nieaktywną skrzynkę pocztową.

Aby uzyskać instrukcje, zobacz [How to identify the type of hold placed on an Exchange Online mailbox (Jak zidentyfikować typ blokady umieszczonej w Exchange Online skrzynce pocztowej](identify-a-hold-on-an-exchange-online-mailbox.md)).

## <a name="inactive-mailboxes-and-microsoft-365-retention"></a>Nieaktywne skrzynki pocztowe i przechowywanie usługi Microsoft 365

Jeśli zasady przechowywania usługi Microsoft 365 zostaną zastosowane do skrzynki pocztowej lub co najmniej jeden element poczty e-mail w skrzynce pocztowej ma zastosowaną etykietę przechowywania, a następnie zostanie usunięte konto użytkownika platformy Microsoft 365, skrzynka pocztowa zostanie przekonwertowana na nieaktywną skrzynkę pocztową. Aby utworzyć nieaktywną skrzynkę pocztową:

- Ustawienia przechowywania muszą być skonfigurowane tak [, aby zachować zawartość lub zachować, a następnie usunąć zawartość](retention-settings.md#settings-for-retaining-and-deleting-content). Jeśli akcja przechowywania jest skonfigurowana do usuwania tylko zawartości, skrzynka pocztowa nie stanie się nieaktywna po usunięciu konta użytkownika. W przypadku nieaktywnych skrzynek pocztowych zalecamy użycie opcji zachowaj, a następnie usuń.

- Ustawienia przechowywania muszą być stosowane do [lokalizacji przechowywania](retention-settings.md#locations) skojarzonej ze skrzynką pocztową programu Exchange:
    - Poczta e-mail programu Exchange
    - Grupy Microsoft 365
    - Skype dla firm
    - Foldery publiczne programu Exchange
    - Komunikaty kanału usługi Teams
    - Czaty w usłudze Teams
    - Komunikaty kanału prywatnego usługi Teams
    - Komunikaty społeczności usługi Yammer
    - Komunikaty użytkowników usługi Yammer

Aby uzyskać więcej informacji na temat przechowywania przez firmę Microsoft, zobacz [Informacje o zasadach przechowywania i etykietach przechowywania](retention.md).

Jeśli przechowywanie usługi Microsoft 365 jest używane do tworzenia nieaktywnej skrzynki pocztowej, ustawienia przechowywania z zasad przechowywania lub etykiet przechowywania będą nadal stosowane do nieaktywnej skrzynki pocztowej. Oznacza to, że jeśli ustawienia przechowywania są skonfigurowane do przechowywania, a następnie usuwania zawartości, elementy zostaną przeniesione do folderu Elementy możliwe do odzyskania po upływie czasu przechowywania, a następnie ostatecznie czyszczone z nieaktywnej skrzynki pocztowej. Jeśli ustawienia przechowywania nie są skonfigurowane do usuwania elementów, elementy, które nie zostały trwale usunięte przez użytkownika (zanim skrzynka pocztowa została nieaktywna) nie zostaną przeniesione do folderu Elementy możliwe do odzyskania i zostaną zachowane przez czas nieokreślony, gdy skrzynka pocztowa stanie się nieaktywna.

> [!TIP]
> Możesz użyć właściwości *ComplianceTagHoldApplied* , aby określić, czy skrzynka pocztowa ma elementy, które mają co najmniej jedną etykietę przechowywania zastosowaną do przechowywania lub przechowywania, a następnie usuwania zawartości. Aby uzyskać więcej informacji, zobacz [Identyfikowanie zablokowanych skrzynek pocztowych, ponieważ etykieta przechowywania została zastosowana do folderu lub elementu](identify-a-hold-on-an-exchange-online-mailbox.md#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item).

### <a name="using-adaptive-policy-scopes-to-manage-retention-of-inactive-mailboxes"></a>Zarządzanie przechowywaniem nieaktywnych skrzynek pocztowych przy użyciu zakresów zasad adaptacyjnych

Dzięki [adaptacyjnym zakresom zasad](retention.md#adaptive-or-static-policy-scopes-for-retention) można zastosować ustawienia przechowywania w szczególności do nieaktywnych skrzynek pocztowych. Zalety tej konfiguracji obejmują:

- Możesz spełnić wymagania organizacji dotyczące przepisów lub zasad, które wymagają różnych okresów przechowywania dla aktywnych pracowników i byłych pracowników.

- Ustawienia przechowywania można skonfigurować tak, aby zachować zawartość skrzynki pocztowej tylko tak długo, jak to konieczne, aby spełnić wymagania organizacji dotyczące byłych pracowników.

- Można szybko zidentyfikować zasady przechowywania przypisane do nieaktywnych skrzynek pocztowych w organizacji, co ułatwia zmianę ustawień przechowywania w razie potrzeby. 

- Łatwiej jest trwale usunąć nieaktywną skrzynkę pocztową, ponieważ można ją usunąć z zasad, [konfigurując zakres adaptacyjny](retention-settings.md#to-configure-an-adaptive-scope) , aby ją wykluczyć, na podstawie atrybutów lub właściwości nieaktywnej skrzynki pocztowej. W przeciwnym razie należy użyć [Exchange Online programu PowerShell](delete-an-inactive-mailbox.md#remove-an-inactive-mailbox-from-a-retention-policy) przed [usunięciem skrzynki pocztowej](delete-an-inactive-mailbox.md#before-you-delete-an-inactive-mailbox).

> [!NOTE]
> W zależności od konfiguracji zakresu zasad adaptacyjnych nieaktywne skrzynki pocztowe mogą być dołączane lub nie.  Aby w szczególności określić element docelowy lub wykluczyć nieaktywne skrzynki pocztowe z zakresu zasad adaptacyjnych, zobacz [informacje o konfiguracji dla poczty e-mail programu Exchange i folderów publicznych programu Exchange](retention-settings.md#locations).

### <a name="using-static-policy-scopes-and-inactive-mailboxes"></a>Używanie zakresów zasad statycznych i nieaktywnych skrzynek pocztowych

Jeśli nie używasz [zakresów zasad adaptacyjnych](retention.md#adaptive-or-static-policy-scopes-for-retention) z przechowywaniem platformy Microsoft 365, a zamiast tego używasz [zakresu statycznego](retention.md#adaptive-or-static-policy-scopes-for-retention), rozważ następujące kwestie:

- Zakresy zasad statycznych obejmują nieaktywne skrzynki pocztowe w przypadku korzystania z domyślnej konfiguracji **Wszyscy adresaci** , ale nie są obsługiwane w [przypadku określonych wklęsłych lub wykluczeń](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions). Jeśli jednak uwzględnisz lub wykluczysz adresata, który ma aktywną skrzynkę pocztową w momencie zastosowania zasad, a skrzynka pocztowa później stanie się nieaktywna, ustawienia przechowywania będą nadal stosowane lub wykluczane. W tym scenariuszu nadal obowiązują [określone limity dołączania i wykluczeń](retention-limits.md) .
    
    > [!NOTE]
    > Oznacza to również, że wszystkie nowe ustawienia przechowywania platformy Microsoft 365 korzystające z zakresu statycznego, który jest stosowany do domyślnego wyboru **Wszystkich adresatów** , będą automatycznie uwzględniać wszystkie istniejące nieaktywne skrzynki pocztowe.

- Jeśli zmienisz domyślny wybór **opcji Wszyscy adresaci** w celu uwzględnienia określonych adresatów, ustawienia przechowywania zasad nie będą już stosowane do żadnych nieaktywnych skrzynek pocztowych, które teraz kwalifikują się do automatycznego usunięcia.

- Jeśli chcesz zwolnić zasady przechowywania stosowane do nieaktywnej skrzynki pocztowej, zobacz [Zwalnianie zasad przechowywania](retention.md#releasing-a-policy-for-retention).

> [!CAUTION]
> Jeśli używasz przechowywania usługi Microsoft 365 do nieaktywnej skrzynki pocztowej, nie zmieniaj ani nie usuwaj głównej nazwy użytkownika (UPN) dla skrzynki pocztowej przed usunięciem odpowiedniego konta użytkownika. Ponadto nie zmieniaj podstawowego adresu SMTP (pochodzącego od nazwy UPN) ani nie usuwaj tego adresu e-mail z listy dodatkowych adresów SMTP skojarzonych ze skrzynką pocztową przed nieaktywną skrzynką pocztową.
> 
> Jeśli zmienisz nazwę UPN lub adresy e-mail (które zostały przypisane do skrzynki pocztowej w momencie zastosowania ustawień przechowywania), a następnie usuniesz konto użytkownika, aby skrzynka pocztowa była nieaktywna, nie będzie można usunąć nieaktywnej skrzynki pocztowej, jeśli nie będzie już konieczne jej zachowanie. Dzieje się tak dlatego, że nie można usunąć nieaktywnej skrzynki pocztowej z zasad przy użyciu nazwy UPN lub adresu e-mail (w celu zidentyfikowania nieaktywnej skrzynki pocztowej), która różni się od tych, które istniały podczas początkowego stosowania ustawień przechowywania do skrzynki pocztowej. Aby uzyskać więcej informacji na temat usuwania nieaktywnych skrzynek pocztowych, zobacz [Usuwanie nieaktywnej skrzynki pocztowej w Office 365](delete-an-inactive-mailbox.md).

## <a name="inactive-mailboxes-and-ediscovery-case-holds"></a>Nieaktywne skrzynki pocztowe i sprawa zbierania elektronicznych materiałów dowodowych są przechowywane

Jeśli blokada skojarzona z [przypadkiem zbierania elektronicznych](./get-started-core-ediscovery.md) materiałów dowodowych w portal zgodności Microsoft Purview zostanie umieszczona w skrzynce pocztowej, a następnie skrzynka pocztowa lub konto użytkownika zostaną usunięte, skrzynka pocztowa stanie się nieaktywną skrzynką pocztową. Nie zalecamy jednak używania blokad zbierania elektronicznych materiałów dowodowych w celu nieaktywności skrzynki pocztowej. Dzieje się tak dlatego, że sprawy zbierania elektronicznych materiałów dowodowych są przeznaczone dla konkretnych, ograniczonych czasowo spraw związanych z problemem prawnym. W pewnym momencie sprawa prawna prawdopodobnie zakończy się, a blokady związane ze sprawą zostaną usunięte, a sprawa zbierania elektronicznych materiałów dowodowych zostanie zamknięta. W rzeczywistości, jeśli blokada umieszczona w nieaktywnej skrzynce pocztowej jest skojarzona ze sprawą zbierania elektronicznych materiałów dowodowych, a następnie blokada zostanie zwolniona lub sprawa zbierania elektronicznych materiałów dowodowych zostanie zamknięta (lub usunięta), nieaktywna skrzynka pocztowa zostanie trwale usunięta. Ponadto nie można utworzyć blokady zbierania elektronicznych materiałów dowodowych na podstawie czasu. Oznacza to, że zawartość w nieaktywnej skrzynce pocztowej jest przechowywana na zawsze lub do momentu usunięcia blokady i usunięcia nieaktywnej skrzynki pocztowej. W związku z tym zalecamy używanie przechowywania platformy Microsoft 365 dla nieaktywnych skrzynek pocztowych.

Aby uzyskać więcej informacji na temat różnic między blokadami zbierania elektronicznych materiałów dowodowych a przechowywaniem w usłudze Microsoft 365, zobacz [Kiedy używać zasad przechowywania i etykiet przechowywania lub blokad zbierania elektronicznych materiałów dowodowych](retention.md#when-to-use-retention-policies-and-retention-labels-or-ediscovery-holds).

## <a name="inactive-mailboxes-and-auto-expanding-archives"></a>Nieaktywne skrzynki pocztowe i automatycznie rozwijające się archiwa

Nie można odzyskać ani przywrócić nieaktywnej skrzynki pocztowej skonfigurowanej przy użyciu automatycznie rozwijającego się archiwum. W sytuacjach, w których konieczne jest odzyskanie danych z nieaktywnej skrzynki pocztowej z automatycznie rozszerzającym się archiwum, zalecamy wyeksportowanie danych ze skrzynki pocztowej przy użyciu narzędzia do wyszukiwania zawartości, a następnie zaimportowanie ich do innej skrzynki pocztowej. Aby uzyskać instrukcje krok po kroku dotyczące przeszukiwania nieaktywnej skrzynki pocztowej i eksportowania wyników wyszukiwania, zobacz:

- [Wyszukiwanie zawartości](content-search.md)

- [Eksportowanie wyników wyszukiwania zawartości](export-search-results.md)

## <a name="inactive-mailboxes-and-exchange-mrm-retention-policies"></a>Nieaktywne skrzynki pocztowe i zasady przechowywania programu Exchange MRM

Zastosowanie zasad przechowywania programu Exchange (funkcja Zarządzanie rekordami obsługi komunikatów lub MRM w Exchange Online) nie powoduje utworzenia nieaktywnej skrzynki pocztowej po usunięciu konta użytkownika.

Jeśli jednak te zasady przechowywania mrm zostały zastosowane do skrzynki pocztowej przed jej nieaktywnym działaniem, wszelkie zasady usuwania (tagi przechowywania mrm skonfigurowane za pomocą akcji **Usuń** ) będą nadal przetwarzane w nieaktywnej skrzynce pocztowej. Oznacza to, że elementy oznaczone zasadami usuwania mrm zostaną przeniesione do [folderu Elementy możliwe do odzyskania](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) po upływie okresu przechowywania. Te elementy są usuwane z nieaktywnej skrzynki pocztowej po wygaśnięciu czasu przechowywania. Jeśli czas przechowywania nie zostanie określony dla nieaktywnej skrzynki pocztowej, elementy w folderze Odzyskiwanie elementów zostaną zachowane przez czas nieokreślony.

Z drugiej strony wszystkie zasady archiwum (tagi przechowywania mrm skonfigurowane za pomocą akcji **MoveToArchive** ), które są uwzględnione w zasadach przechowywania mrm przypisanych do nieaktywnej skrzynki pocztowej, są ignorowane. Oznacza to, że elementy w nieaktywnej skrzynce pocztowej oznaczone zasadami archiwum pozostają w podstawowej skrzynce pocztowej po upływie okresu przechowywania. Nie są one przenoszone do skrzynki pocztowej archiwum ani do folderu Elementy możliwe do odzyskania w skrzynce pocztowej archiwum. Zostaną one zachowane na czas nieokreślony.

## <a name="next-steps"></a>Następne kroki

Aby sprawić, by skrzynka pocztowa była nieaktywna i zarządzać nią, na przykład odzyskiwaniem, przywracaniem i usuwaniem, zobacz [Tworzenie nieaktywnych skrzynek pocztowych i zarządzanie nimi](create-and-manage-inactive-mailboxes.md).
