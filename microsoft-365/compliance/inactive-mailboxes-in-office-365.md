---
title: Informacje o nieaktywnych skrzynkach pocztowych
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
ms.openlocfilehash: 72d048bc99876c0f252feffe3159d3ce01303028
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010645"
---
# <a name="learn-about-inactive-mailboxes"></a>Informacje o nieaktywnych skrzynkach pocztowych

Być może po opuszczeniu organizacji będzie konieczne zachowanie poczty e-mail byłych pracowników. W zależności od wymagań przechowywania w organizacji może być konieczne zachowanie zawartości skrzynki pocztowej przez kilka miesięcy lub lat po zakończeniu zatrudnienia lub zachowanie zawartości skrzynki pocztowej przez czas nieograniczony. Niezależnie od tego, jak długo chcesz przechowywać wiadomości e-mail, możesz utworzyć nieaktywne skrzynki pocztowe, aby zachować skrzynki pocztowe byłych pracowników.

## <a name="what-are-inactive-mailboxes"></a>Co to są nieaktywne skrzynki pocztowe?

Gdy pracownik odchodzi z organizacji (lub przechodzi na dłuższy czas nieobecności), możesz usunąć jego Microsoft 365 konta. Dane skrzynki pocztowej pracownika są zachowywane przez 30 dni od usunięcia konta. W tym okresie nadal można odzyskać dane skrzynki pocztowej, przywracając konto. Po 30 dniach dane zostaną trwale usunięte.

Jeśli jednak do skrzynki pocztowej zastosowano hold przed usunięciem konta Microsoft 365, zostanie ona przekonwertowana na nieaktywną skrzynkę pocztową. Poniższe sekcje zawierają informacje o blokadych, które można stosować przy Microsoft 365 przechowywania i zbierania elektronicznych materiałów dowodowych.

Nieaktywne skrzynki pocztowe są przydatne, gdy organizacja musi zachować zawartość skrzynek pocztowych byłych pracowników ze względów prawnych lub z innych powodów. Wszelkie typy blokowania wymienione w tym dokumencie wymuszają nieaktywność skrzynki pocztowej po usunięciu obiektu użytkownika, jednak zalecamy zastosowanie zasad przechowywania lub etykiet przechowywania programu [Microsoft 365, potwierdzenia](#confirming-a-hold-is-applied-to-a-mailbox) zastosowania hold'a, Microsoft 365 następnie usunięcie odpowiedniego konta programu Microsoft 365. W tym momencie zawartość nieaktywnej skrzynki pocztowej jest zachowywana przez okres przechowywania określony przed usunięciem konta użytkownika. Nadal można odzyskać odpowiednie konto użytkownika przez 30 dni, jednak po 30 dniach skrzynka pocztowa jest zachowywana w programie Microsoft 365 jako nieaktywna skrzynka pocztowa do momentu usunięcia zasad przechowywania lub etykiet przechowywania.

> [!IMPORTANT]
> Jak wspomniano wcześniej, zalecamy używanie przechowywania Microsoft 365 do tworzenia nieaktywnych skrzynek pocztowych:
> - In-Place w centrum administracyjnym usługi Exchange zostały wycofane. Od 1 lipca 2020 r. nie można utworzyć nowych In-Place w programie Exchange Online. Od 1 października 2020 r. nie można już zmieniać czasu trwania blokady w miejscu. Nieaktywną skrzynkę pocztową, do In-Place wstrzymywanie wiadomości, można usunąć tylko przez usunięcie In-Place wiadomości. Istniejące nieaktywne skrzynki pocztowe, In-Place wstrzymają, będą zachowywane do momentu usunięcia go. Aby uzyskać więcej informacji na In-Place wycofanie, zobacz Wycofanie starszych narzędzi [zbierania elektronicznych materiałów dowodowych](legacy-ediscovery-retirement.md).
> 
> - [Zawieszenie w procesów](create-a-litigation-hold.md) sądowych jest obsługiwane jako metoda alternatywna w celu przechowywania zawartości w skrzynce pocztowej i jej nieaktywności po usunięciu konta użytkownika. Jednak w przypadku starszej technologii zalecamy używanie przechowywania Microsoft 365 przechowywania.

W przypadku wielu blokady w tej samej zawartości obowiązuje zasada przechowywania [](retention.md#the-principles-of-retention-or-what-takes-precedence) i zawartość jest zachowywana przez najdłuższy okres.

### <a name="confirming-a-hold-is-applied-to-a-mailbox"></a>Potwierdzanie zastosowania wstrzymywania do skrzynki pocztowej

Niezależnie od tego, czy zastosujemy zasady przechowywania Microsoft 365, etykiety przechowywania, zbierania elektronicznych materiałów dowodowych, Zawieszenie w związku z postępowaniem sądowym, czy masz istniejące zawieszenie w związku z In-Place, możesz sprawdzić, czy zawieszenie zostało pomyślnie zastosowane do skrzynki pocztowej za pomocą programu PowerShell. Jeśli ostatnio skonfigurowano hold, może być konieczne zaczekaj, aż zostanie on zastosowany do skrzynki pocztowej.

Aby zapobiec przypadkowemu lub niezamierzonemu usunięciu, zalecamy potwierdzenie wstrzymywania przed usunięciem konta użytkownika. Jeśli to nie zostanie zastosowane, skrzynka pocztowa nie zostanie przekonwertowana na nieaktywną skrzynkę pocztową.

Aby uzyskać instrukcje, [zobacz Jak zidentyfikować typy blokowania umieszczonego w Exchange Online pocztowej](identify-a-hold-on-an-exchange-online-mailbox.md).

## <a name="inactive-mailboxes-and-microsoft-365-retention"></a>Nieaktywne skrzynki pocztowe i Microsoft 365 przechowywania

Jeśli zasady przechowywania usługi Microsoft 365 zostały zastosowane do skrzynki pocztowej lub co najmniej jeden element poczty e-mail w skrzynce pocztowej ma etykietę przechowywania, Microsoft 365 konto użytkownika zostanie usunięte, skrzynka pocztowa zostanie przekonwertowana na nieaktywną skrzynkę pocztową. Aby nieaktywne skrzynki pocztowe zostały utworzone:

- Ustawienia przechowywania należy skonfigurować tak, aby [zachowywać zawartość lub zachowywać zawartość, a następnie ją usuwać](retention-settings.md#settings-for-retaining-and-deleting-content). Jeśli akcja przechowywania jest skonfigurowana tak, aby usuwać tylko zawartość, skrzynka pocztowa nie stanie się nieaktywna po usunięciu konta użytkownika. W przypadku nieaktywnych skrzynek pocztowych zalecamy używanie opcji zachowaj, a następnie usuń.

- Ustawienia przechowywania należy stosować do lokalizacji [przechowywania skojarzonej](retention-settings.md#locations) z skrzynką pocztową usługi Exchange pocztowej:
    - Exchange-mail
    - Microsoft 365 grupy
    - Skype dla firm
    - Exchange folderów publicznych
    - Teams wiadomości na kanale
    - Teams czatów
    - Teams wiadomości z kanału prywatnego
    - Yammer wiadomości od społeczności
    - Yammer wiadomości od użytkowników

Aby uzyskać więcej informacji na temat przechowywania przez firmę Microsoft, zobacz [Informacje o zasadach przechowywania i etykietach przechowywania](retention.md).

Jeśli Microsoft 365 przechowywania jest używane do tworzenia nieaktywnych skrzynek pocztowych, ustawienia przechowywania z zasad przechowywania lub etykiet przechowywania będą nadal stosowane do nieaktywnej skrzynki pocztowej. Oznacza to, że jeśli w ustawieniach przechowywania skonfigurowano przechowywanie i usuwanie zawartości, elementy zostaną przeniesione do folderu Elementy do odzyskania po wygaśnięciu czasu trwania przechowywania, a następnie później usunięte z nieaktywnej skrzynki pocztowej. Jeśli ustawienia przechowywania nie zostały skonfigurowane jako elementy usunięte, elementy, które nie zostały trwale usunięte przez użytkownika (zanim skrzynka pocztowa została nieaktywna), nie zostaną przeniesione do folderu Elementy do odzyskania i będą przechowywane przez czas nieograniczony, gdy skrzynka pocztowa stanie się nieaktywna.

> [!TIP]
> Właściwość *ComplianceTagHoldApplied* pozwala określić, czy skrzynka pocztowa ma elementy, do których zastosowano co najmniej jedną etykietę przechowywania w celu zachowania, czy przechowywania i usuwania zawartości. Aby uzyskać więcej informacji, zobacz [Identyfikowanie skrzynek pocztowych w holdie, ponieważ etykieta przechowywania została zastosowana do folderu lub elementu](identify-a-hold-on-an-exchange-online-mailbox.md#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item).

### <a name="using-adaptive-policy-scopes-to-manage-retention-of-inactive-mailboxes"></a>Korzystanie z adaptacyjnych zakresów zasad w celu zarządzania przechowywaniem nieaktywnych skrzynek pocztowych

W [przypadku adaptacyjnych zakresów zasad](retention.md#adaptive-or-static-policy-scopes-for-retention) możesz zastosować ustawienia przechowywania konkretnie do nieaktywnych skrzynek pocztowych. Zalety tej konfiguracji to:

- Możesz spełnić przepisy lub zasady organizacji, które wymagają różnych okresów przechowywania dla aktywnych pracowników i byłych pracowników.

- Ustawienia przechowywania można skonfigurować w taki sposób, aby zawartość skrzynki pocztowej była zachowywana tylko przez okres niezbędny do spełnienia wymagań organizacji dla byłych pracowników.

- Możesz szybko określić zasady przechowywania przypisane do nieaktywnych skrzynek pocztowych w Twojej organizacji, co ułatwi w razie potrzeby zmianę ustawień przechowywania. 

- Łatwiej jest trwale usunąć nieaktywną skrzynkę pocztową, ponieważ można ją usunąć z zasad[](retention-settings.md#to-configure-an-adaptive-scope), konfigurując adaptacyjny zakres w celu jej wykluczenia na podstawie atrybutów lub właściwości nieaktywnej skrzynki pocztowej. W przeciwnym razie należy użyć [programu Exchange Online PowerShell](delete-an-inactive-mailbox.md#remove-an-inactive-mailbox-from-a-retention-policy) przed [usunięciem skrzynki pocztowej](delete-an-inactive-mailbox.md#before-you-delete-an-inactive-mailbox).

> [!NOTE]
> W zależności od konfiguracji adaptacyjnego zakresu zasad nieaktywne skrzynki pocztowe mogą być uwzględniane lub nie.  Aby w szczególności kierować lub wykluczać nieaktywne skrzynki pocztowe z adaptacyjnego zakresu zasad, zobacz informacje o Exchange e-mail i folderach [Exchange publicznych](retention-settings.md#locations).

### <a name="using-static-policy-scopes-and-inactive-mailboxes"></a>Używanie zakresów statycznych zasad i nieaktywnych skrzynek pocztowych

Jeśli nie używasz zakresów [adaptacyjnych zasad z przechowywaniem](retention.md#adaptive-or-static-policy-scopes-for-retention) Microsoft 365[, a zamiast](retention.md#adaptive-or-static-policy-scopes-for-retention) tego użyj zakresu statycznego, rozważ następujące kwestie:

- Zakresy statycznych zasad obejmują nieaktywne skrzynki pocztowe,  jeśli używasz domyślnej konfiguracji Wszyscy adresaci, ale nie są obsługiwani w przypadku określonych dołączeń [lub wykluczeń](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions). Jeśli jednak uwzględnisz lub wykluczysz adresata, który ma aktywną skrzynkę pocztową w momencie stosowania zasad, a skrzynka pocztowa zostanie później nieaktywna, ustawienia przechowywania będą nadal stosowane lub wykluczane. W tym scenariuszu [obowiązują określone limity dołączania i wykluczeń](retention-limits.md) .
    
    > [!NOTE]
    > Oznacza to również, że Microsoft 365 nowych ustawień przechowywania przy użyciu zakresu statycznego zastosowanego do domyślnego wyboru Wszyscy adresaci  będą automatycznie uwzględniać wszystkie istniejące nieaktywne skrzynki pocztowe.

- Jeśli zmienisz domyślną pozycję Wszyscy adresaci tak, aby uwzględniali konkretnych adresatów, ustawienia przechowywania tych zasad nie będą już stosowane do żadnych nieaktywnych skrzynek pocztowych, które stają się teraz uprawnione do automatycznego usuwania.

- Jeśli chcesz zwolnić zasady przechowywania, które są stosowane do nieaktywnej skrzynki pocztowej, zobacz [Zwalnianie zasad przechowywania](retention.md#releasing-a-policy-for-retention).

> [!CAUTION]
> Gdy używasz przechowywania Microsoft 365, aby nieaktywnych skrzynek pocztowych, nie zmieniaj ani nie usuwaj głównej nazwy użytkownika (UPN) skrzynki pocztowej przed usunięciem odpowiedniego konta użytkownika. Ponadto nie zmieniaj podstawowego adresu SMTP (pochodzących z głównej sieci pocztowej) ani nie usuwaj tego adresu e-mail z listy pomocniczych adresów SMTP skojarzonych ze skrzynką pocztową, zanim zdez będzie to nieaktywność skrzynki pocztowej.
> 
> Jeśli zmienisz upn lub adresy e-mail (które były przypisane do skrzynki pocztowej w momencie stosowania ustawień przechowywania), a następnie usuniesz konto użytkownika w celu jej nieaktywności, nie będzie można usunąć nieaktywnej skrzynki pocztowej, jeśli nie będzie już konieczne jej zachowywanie. Dzieje się tak, ponieważ nie można usunąć nieaktywnej skrzynki pocztowej z zasad przy użyciu upn lub adresu e-mail (w celu zidentyfikowania nieaktywnej skrzynki pocztowej) innej niż ta, która istniała, gdy ustawienia przechowywania zostały początkowo zastosowane do skrzynki pocztowej. Aby uzyskać więcej informacji na temat usuwania nieaktywnych skrzynek pocztowych, zobacz [Usuwanie nieaktywnej skrzynki pocztowej w programie Office 365](delete-an-inactive-mailbox.md).

## <a name="inactive-mailboxes-and-ediscovery-case-holds"></a>Nieaktywne skrzynki pocztowe i zbierania elektronicznych materiałów dowodowych

Jeśli w skrzynce pocztowej zostanie umieszczona w skrzynce pocztowej skojarzona ze sprawą zbierania elektronicznych materiałów dowodowych w programie Centrum zgodności platformy Microsoft 365, a następnie skrzynka pocztowa lub konto użytkownika zostanie usunięte, stanie się ona nieaktywną skrzynką pocztową.[](./get-started-core-ediscovery.md) Nie zalecamy jednak używania funkcji zbierania elektronicznych materiałów dowodowych w celu nieaktywności skrzynki pocztowej. Jest tak dlatego, że sprawy zbierania elektronicznych materiałów dowodowych są przeznaczone dla określonych spraw związanych z problemami prawnie. W pewnym momencie sprawa sądowa prawdopodobnie zakończy się, a blokady skojarzone z tą sprawą zostaną usunięte, a sprawa zbierania elektronicznych materiałów dowodowych zostanie zamknięta. W rzeczywistości jeśli z sprawę zbierania elektronicznych materiałów dowodowych zostanie skojarzona nieaktywna skrzynka pocztowa umieszczona w zbierania elektronicznych materiałów dowodowych, wówczas sprawa zbierania elektronicznych materiałów dowodowych zostanie zamknięta (lub usunięta), nieaktywna skrzynka pocztowa zostanie trwale usunięta. Ponadto nie można utworzyć opartego na czasie zbierania elektronicznych materiałów dowodowych. Oznacza to, że zawartość nieaktywnej skrzynki pocztowej jest zachowywana w nieskończoność lub do momentu usunięcia zawieszonego konta i usunięcia nieaktywnej skrzynki pocztowej. W związku z tym zalecamy przechowywanie Microsoft 365 nieaktywnych skrzynek pocztowych.

Aby uzyskać więcej informacji na temat różnic między przechowywaniem zbierania elektronicznych materiałów dowodowych Microsoft 365 przechowywania, zobacz Kiedy używać zasad przechowywania i etykiet przechowywania lub zbierania [elektronicznych materiałów dowodowych](retention.md#when-to-use-retention-policies-and-retention-labels-or-ediscovery-holds).

## <a name="inactive-mailboxes-and-auto-expanding-archives"></a>Nieaktywne skrzynki pocztowe i automatyczne rozwijanie archiwów

Nie można odzyskać ani przywrócić nieaktywnej skrzynki pocztowej skonfigurowanej przy użyciu archiwum rozszerzające się automatycznie. W sytuacjach, w których konieczne jest odzyskanie danych z nieaktywnej skrzynki pocztowej z archiwum rozwijanej automatycznie, zalecamy wyeksportowanie danych ze skrzynki pocztowej przy użyciu narzędzia do przeszukiwania zawartości, a następnie zaimportowanie ich do innej skrzynki pocztowej. Aby uzyskać instrukcje krok po kroku dotyczące wyszukiwania nieaktywnej skrzynki pocztowej i eksportowania wyników wyszukiwania, zobacz:

- [Przeszukiwanie zawartości](content-search.md)

- [Eksportowanie wyników wyszukiwania zawartości](export-search-results.md)

## <a name="inactive-mailboxes-and-exchange-mrm-retention-policies"></a>Nieaktywne skrzynki pocztowe i Exchange przechowywania MRM

Stosowanie zasad Exchange przechowywania (funkcji Zarządzanie rekordami wiadomości lub MRM w programie Exchange Online) nie powoduje utworzenia nieaktywnej skrzynki pocztowej po usunięciu konta użytkownika.

Jeśli jednak te zasady przechowywania MRM zostały zastosowane do skrzynki pocztowej przed jej nieaktywnym działaniem, wszelkie zasady usuwania (tagi przechowywania MRM  skonfigurowane przy użyciu akcji Usuń) będą nadal przetwarzane w nieaktywnej skrzynce pocztowej. Oznacza to, że elementy otagowane przy użyciu zasad usuwania mrm zostaną przeniesione do [folderu](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) Elementy do odzyskania po wygaśnięciu okresu przechowywania. Te elementy są czyszowane z nieaktywnej skrzynki pocztowej po wygaśnięciu czasu trwania blokowania. Jeśli nie określono czasu trwania zawieszania dla nieaktywnej skrzynki pocztowej, elementy w folderze Odzyskiwanie elementów będą zachowywane przez czas nieograniczony.

Natomiast wszelkie zasady archiwizacji (tagi przechowywania MRM skonfigurowane za pomocą akcji **MoveToArchive** ) zawarte w zasadach przechowywania MRM przypisanych do nieaktywnej skrzynki pocztowej są ignorowane. Oznacza to, że elementy w nieaktywnej skrzynce pocztowej otagowane przy użyciu zasad archiwizacji pozostają w podstawowej skrzynce pocztowej po wygaśnięciu okresu przechowywania. Nie są one przenoszone do archiwaowej skrzynki pocztowej ani do folderu Elementy do odzyskania w archiwaowej skrzynce pocztowej. Będą one przechowywane przez czas nieograniczony.

## <a name="next-steps"></a>Następne kroki

Aby nieaktywnych skrzynek pocztowych i zarządzać nimi, na przykład odzyskiwaniem, przywracaniem i usuwaniem, zobacz Tworzenie nieaktywnych skrzynek [pocztowych i zarządzanie nimi](create-and-manage-inactive-mailboxes.md).
