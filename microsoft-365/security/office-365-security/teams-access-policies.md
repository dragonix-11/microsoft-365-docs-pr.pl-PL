---
title: Zalecane Teams firmowe — Microsoft 365 dla przedsiębiorstw | Microsoft Docs
description: W tym artykule opisano zasady zalecenia firmy Microsoft dotyczące sposobu zabezpieczania Teams i dostępu do plików.
author: MicrosoftHeidi
manager: serdars
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.author: heidip
ms.date: 09/30/2020
ms.reviewer: anmorgan
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: b659853d9323b4a1503cd75cff66a83cbd06e85e
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682906"
---
# <a name="policy-recommendations-for-securing-teams-chats-groups-and-files"></a>Zalecenia dotyczące zasad dotyczące zabezpieczania Teams czatów, grup i plików

W tym artykule opisano, jak wdrożyć zalecane zasady dostępu do urządzeń i tożsamości bez zaufania w celu ochrony Microsoft Teams czatów, grup i zawartości, takiej jak pliki i kalendarze. Ten przewodnik opiera się na wspólnych zasadach dostępu do [tożsamości](identity-access-policies.md) i urządzeń oraz zawiera dodatkowe informacje Teams specyficzne dla urządzenia. Ponieważ Teams z innymi naszymi produktami, zobacz też Zalecenia dotyczące zasad [](sharepoint-file-access-policies.md) dotyczące SharePoint witryn i plików oraz Zalecenia dotyczące zasad dotyczące [zabezpieczania poczty e-mail](secure-email-recommended-policies.md).

Zalecenia te są oparte na trzech różnych warstwach zabezpieczeń i ochrony dla Teams, które można stosować w zależności od stopnia szczegółowości Twoich potrzeb: punktu początkowego, przedsiębiorstwa i wyspecjalizowanego zabezpieczeń. Więcej informacji o tych warstwach zabezpieczeń i zalecanych zasadach można znaleźć w te zaleceniach w konfiguracjach tożsamości [i dostępu do urządzeń](microsoft-365-policies-configurations.md).

Więcej zaleceń dotyczących wdrażania Teams tym artykule pominiesz w konkretnych okolicznościach uwierzytelniania, w tym dla użytkowników spoza organizacji. Aby zapewnić pełne środowisko zabezpieczeń, należy postępować zgodnie z tymi wskazówkami.

## <a name="getting-started-with-teams-before-other-dependent-services"></a>Wprowadzenie do usługi Teams przed innymi usługami zależnmi

Aby rozpocząć pracę z usługami zależnych, nie Microsoft Teams. Wszystkie te usługi działają "po prostu działają". Musisz jednak przygotować się do zarządzania następującymi elementami związanymi z usługą:

- Microsoft 365 grupy
- SharePoint witryn zespołu
- OneDrive dla Firm
- Exchange skrzynki pocztowe
- Przesyłanie strumieniowe klipów wideo i planów usługi Planner (jeśli te usługi są włączone)

## <a name="updating-common-policies-to-include-teams"></a>Aktualizowanie wspólnych zasad w celu ich Teams

Aby chronić czat, grupy i zawartość w Teams, na poniższym diagramie pokazano zasady, które należy aktualizować na przykładach typowych zasad dostępu do urządzeń i tożsamości. Przy każdej aktualizacji zasad upewnij się, że Teams usługi zależne są uwzględnione w przypisaniu aplikacji w chmurze.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png" alt-text="Podsumowanie aktualizacji zasad w celu ochrony dostępu do usług Teams i ich usług zależnych." lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png":::

Te usługi to usługi zależne, które należy uwzględnić przy przypisywaniu aplikacji w chmurze dla Teams:

- Microsoft Teams
- SharePoint i OneDrive dla Firm
- Exchange Online
- Skype dla firm Online
- Microsoft Stream (nagrania ze spotkań)
- Microsoft Planner (zadania usługi Planner i dane planu)

W poniższej tabeli wymieniono [zasady, które](identity-access-policies.md) trzeba ponownie wyświetlać, oraz linki do poszczególnych zasad we wspólnych zasadach dostępu do tożsamości i urządzeń, które mają szerszy zestaw zasad dla wszystkich Office aplikacji.

|Poziom ochrony|Policies (zasady)|Więcej informacji na temat Teams implementacji|
|---|---|---|
|**Punkt początkowy**|[Wymagaj uwierzytelniania wieloskładnikowego, gdy ryzyko logowania *jest średnie* lub *wysokie*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Upewnij się Teams że aplikacje i usługi zależne są uwzględnione na liście aplikacji. Teams do rozważenia są również reguły dostępu gościa i dostępu zewnętrznego, dowiedz się więcej o tych zasadach w dalszej części tego artykułu.|
||[Blokowanie klientów, którzy nie obsługują nowoczesnego uwierzytelniania](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Przypisywanie Teams w chmurze także usług zależnych.|
||[Zmiana hasła przez użytkowników o wysokim poziomie ryzyka](identity-access-policies.md#high-risk-users-must-change-password)|Wymusza Teams użytkowników na zmianie hasła podczas logowania się w przypadku wykrycia dla ich konta aktywności o wysokim poziomie ryzyka. Upewnij się Teams że aplikacje i usługi zależne są uwzględnione na liście aplikacji.|
||[Stosowanie zasad ochrony danych aplikacji](identity-access-policies.md#apply-app-data-protection-policies)|Upewnij się Teams że aplikacje i usługi zależne są uwzględnione na liście aplikacji. Zaktualizuj zasady dla każdej platformy (iOS, Android, Windows).|
|**Enterprise**|[Wymagaj uwierzytelniania wieloskładnikowego, gdy ryzyko logowania *jest niskie, średnie* lub *wysokie*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Teams do rozważenia są również reguły dostępu gościa i dostępu zewnętrznego, dowiedz się więcej o tych zasadach w dalszej części tego artykułu. Te Teams i usługi zależne.|
||[Definiowanie zasad zgodności urządzeń](identity-access-policies.md#define-device-compliance-policies)|Te Teams i usługi zależne.|
||[Wymaganie zgodności komputerów i *urządzeń* przenośnych](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Te Teams i usługi zależne.|
|**Wyspecjalizowane zabezpieczenia**|[*Zawsze wymagaj* uwierzytelniania wieloskładnikowego](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Bez względu na tożsamość użytkownika uwierzytelniania wieloskładnikowego będzie używane przez Twoją organizację. Te Teams i usługi zależne. |

## <a name="teams-dependent-services-architecture"></a>Teams architektury usług zależnych

Na poniższym diagramie pokazano usługi, na których Teams korzysta. Aby uzyskać więcej informacji i ilustracji, zobacz Microsoft Teams i powiązane usługi zwiększające produktywność w Microsoft 365 [dla architektów IT](../../solutions/productivity-illustrations.md).

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png" alt-text="Diagram przedstawiający Teams zależności między SharePoint, OneDrive dla Firm i Exchange." lightbox="../../media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png":::

## <a name="guest-and-external-access-for-teams"></a>Dostęp gościa i dostępu zewnętrznego do Teams

Microsoft Teams zdefiniuje następujące typy dostępu:

- **Dostęp gościa** korzysta z konta B2B w usłudze Azure AD dla gościa lub użytkownika zewnętrznego, które można dodać jako członka zespołu i mieć wszystkie uprawnienia dostępu do komunikacji i zasobów zespołu.

- **Dostęp zewnętrzny** jest dla użytkownika zewnętrznego, który nie ma konta B2B usługi Azure AD. Dostęp zewnętrzny może obejmować zaproszenia i uczestnictwo w połączeniach, czatach i spotkaniach, ale nie obejmuje członkostwa w zespole ani dostępu do zasobów zespołu.

Zasady dostępu warunkowego dotyczą tylko dostępu gościa Teams ponieważ istnieje odpowiednie konto B2B usługi Azure AD.

<!--
In Azure AD, guest and external users are the same. The user type for both of these is Guest. Guest users are B2B users. Microsoft Teams differentiates between guest users and external users in the app. While it's important to understand how each of these are treated in Teams, both types of users are B2B users in Azure AD and the recommended policies for B2B users apply to both.

-->

Aby uzyskać zalecane zasady umożliwiające dostęp dla gości i użytkowników zewnętrznych przy użyciu konta B2B usługi Azure AD, zobacz Zasady zezwalania na dostęp do konta [B2B](identity-access-policies-guest-access.md) i gościa.

### <a name="guest-access-in-teams"></a>Dostęp dla gości w aplikacji Teams

Oprócz zasad dla użytkowników wewnętrznych w firmie lub organizacji administratorzy mogą umożliwić dostęp gościa do zasobów usługi Teams oraz na interakcję z osobami wewnętrznymi w zakresie konwersacji grupowych, czatu i spotkań grupowych.

Aby uzyskać więcej informacji na temat dostępu gościa i sposobu jego wdrażania, zobacz Teams [dostępu gościa](/microsoftteams/guest-access).

### <a name="external-access-in-teams"></a>Dostęp zewnętrzny w programie Teams

Dostęp zewnętrzny jest czasami mylony z dostępem gości, dlatego należy pamiętać, że te dwa mechanizmy dostępu nieumiejętne to różne typy dostępu.

Dostęp zewnętrzny umożliwia użytkownikom Teams z całej domeny zewnętrznej znajdowanie, dzwonienie, rozmawianie i konfigurowanie spotkań z użytkownikami w Teams. Teams administratorzy konfigurują dostęp zewnętrzny na poziomie organizacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie dostępem zewnętrznym w programie Microsoft Teams](/microsoftteams/manage-external-access).

Użytkownicy z dostępem zewnętrznym mają mniejszy dostęp i funkcjonalność niż osoby dodane za pośrednictwem dostępu gościa. Na przykład użytkownicy dostępu zewnętrznego mogą czatować z użytkownikami wewnętrznymi Teams ale nie mogą uzyskać dostępu do kanałów, plików ani innych zasobów zespołu.

Dostęp zewnętrzny nie korzysta z kont użytkowników B2B usługi Azure AD i dlatego nie korzysta z zasad dostępu warunkowego.

## <a name="teams-policies"></a>Teams zasad

Poza wymienionymi powyżej zasadami wspólnymi istnieją Teams, które można i należy skonfigurować do zarządzania różnymi funkcjami Teams funkcjonalności.

### <a name="teams-and-channels-policies"></a>Teams i kanałów

Teams i kanały to dwa często używane elementy w aplikacji Microsoft Teams. Istnieją zasady, które można stosować, aby kontrolować, co użytkownicy mogą, a czego nie mogą robić w przypadku korzystania z zespołów i kanałów. Mimo że możesz utworzyć zespół globalny, jeśli Twoja organizacja ma nie więcej niż 5000 użytkowników, prawdopodobnie pomocne może okazać się utworzenie mniejszych zespołów i kanałów do określonych celów, zgodnie z potrzebami Twojej organizacji.

Zalecane jest zmienianie zasad domyślnych lub tworzenie zasad niestandardowych. Aby dowiedzieć się więcej na temat zarządzania zasadami, kliknij ten link: Zarządzanie zasadami zespołów w aplikacji [Microsoft Teams](/microsoftteams/teams-policies).

### <a name="messaging-policies"></a>Zasady obsługi wiadomości

Wiadomościami lub czatami można również zarządzać za pomocą domyślnych zasad globalnych lub za pośrednictwem zasad niestandardowych, co może ułatwić użytkownikom komunikowanie się ze sobą w sposób odpowiedni do potrzeb organizacji. Te informacje można przejrzeć na stronie [Zarządzanie zasadami obsługi wiadomości w Teams](/microsoftteams/messaging-policies-in-teams).

### <a name="meeting-policies"></a>Zasady spotkania

Żadna dyskusja Teams nie zostanie ukończona bez planowania i implementowania zasad wokół Teams spotkań. Spotkania to podstawowy składnik programu Teams, umożliwiający formalnie spotykanie się i przedstawianie wielu użytkownikom jednocześnie, a także udostępnianie zawartości związanej ze spotkaniem. Ustawianie odpowiednich zasad dla organizacji wokół spotkań jest bardzo ważne.

Aby uzyskać więcej informacji, zapoznaj się [z tematem Zarządzanie zasadami spotkań w programie Teams](/microsoftteams/meeting-policies-in-teams).

### <a name="app-permission-policies"></a>Zasady uprawnień aplikacji

Teams umożliwia również korzystanie z aplikacji w różnych miejscach, takich jak kanały lub czaty osobiste. Zasady dotyczące tego, jakie aplikacje można dodawać i których można używać, i gdzie, mają kluczowe znaczenie dla konserwacji zabezpieczonego również środowiska z bogatym zawartością.

Aby uzyskać więcej informacji na temat zasad uprawnień aplikacji, zobacz [Zarządzanie zasadami uprawnień aplikacji w programie Microsoft Teams](/microsoftteams/teams-app-permission-policies).

## <a name="next-steps"></a>Następne kroki

![Krok 4. Zasady dotyczące aplikacji Microsoft 365 chmurze.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png)

Skonfiguruj zasady dostępu warunkowego dla:

- [Exchange Online](secure-email-recommended-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)