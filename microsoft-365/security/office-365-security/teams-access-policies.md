---
title: Zalecane zasady Teams — Microsoft 365 dla | przedsiębiorstwa Microsoft Docs
description: W tym artykule opisano zasady dotyczące zaleceń firmy Microsoft dotyczących zabezpieczania Teams komunikacji i dostępu do plików.
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
ms.openlocfilehash: 25f70d3ccdf11daa6a52d16b66d612c04ab8876a
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131179"
---
# <a name="policy-recommendations-for-securing-teams-chats-groups-and-files"></a>Zalecenia dotyczące zasad dotyczące zabezpieczania czatów, grup i plików Teams

W tym artykule opisano sposób implementowania zalecanych Zero Trust zasad dostępu do tożsamości i urządzeń w celu ochrony Microsoft Teams czatów, grup i zawartości, takich jak pliki i kalendarze. Te wskazówki bazują na [typowych zasadach dostępu do tożsamości i urządzeń](identity-access-policies.md) z dodatkowymi informacjami, które są Teams specyficzne. Ponieważ Teams integruje się z innymi produktami, zobacz również [zalecenia dotyczące zasad dotyczące zabezpieczania witryn i plików SharePoint](sharepoint-file-access-policies.md) oraz [zalecenia dotyczące zasad dotyczące zabezpieczania poczty e-mail](secure-email-recommended-policies.md).

Te zalecenia są oparte na trzech różnych warstwach zabezpieczeń i ochrony dla Teams, które mogą być stosowane w oparciu o stopień szczegółowości twoich potrzeb: punkt początkowy, przedsiębiorstwo i wyspecjalizowane zabezpieczenia. Więcej informacji na temat tych warstw zabezpieczeń i zalecanych zasad, do których odnoszą się te zalecenia, można znaleźć w [temacie Konfiguracje tożsamości i dostępu do urządzeń](microsoft-365-policies-configurations.md).

Więcej zaleceń dotyczących wdrażania Teams znajduje się w tym artykule, aby uwzględnić konkretne okoliczności uwierzytelniania, w tym dla użytkowników spoza organizacji. Aby uzyskać pełne środowisko zabezpieczeń, należy postępować zgodnie z poniższymi wskazówkami.

## <a name="getting-started-with-teams-before-other-dependent-services"></a>Wprowadzenie do Teams przed innymi usługami zależnymi

Nie musisz włączać usług zależnych, aby rozpocząć pracę z Microsoft Teams. Wszystkie te usługi będą "po prostu działać". Należy jednak przygotować się do zarządzania następującymi elementami związanymi z usługą:

- Grupy platformy Microsoft 365
- witryny zespołu SharePoint
- OneDrive dla Firm
- skrzynki pocztowe Exchange
- Przesyłanie strumieniowe filmów wideo i planów planisty (jeśli te usługi są włączone)

## <a name="updating-common-policies-to-include-teams"></a>Aktualizowanie typowych zasad w celu uwzględnienia Teams

Aby chronić czat, grupy i zawartość w Teams, na poniższym diagramie przedstawiono zasady do zaktualizowania na podstawie typowych zasad dostępu do tożsamości i urządzeń. Dla każdej aktualizacji zasad upewnij się, że usługi Teams i zależne są uwzględniane w przypisywaniu aplikacji w chmurze.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png" alt-text="Podsumowanie aktualizacji zasad dotyczących ochrony dostępu do Teams i jej usług zależnych" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png":::

Te usługi są usługami zależnymi, które należy uwzględnić w przypisywaniu aplikacji w chmurze dla Teams:

- Microsoft Teams
- SharePoint i OneDrive dla Firm
- Exchange Online
- Skype dla firm Online
- Microsoft Stream (nagrania spotkań)
- Microsoft Planner (zadania planisty i dane planu)

W tej tabeli wymieniono zasady, które należy ponownie przeanalizować, i linki do poszczególnych zasad w [typowych zasadach dostępu do tożsamości i urządzeń](identity-access-policies.md), które mają szerszy zestaw zasad dla wszystkich Office aplikacji.

|Poziom ochrony|Policies (zasady)|Więcej informacji na temat implementacji Teams|
|---|---|---|
|**Punkt początkowy**|[Wymagaj uwierzytelniania wieloskładnikowego, gdy ryzyko logowania jest *średnie* lub *wysokie*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Upewnij się, Teams i usługi zależne znajdują się na liście aplikacji. Teams ma również reguły dostępu gościa i dostępu zewnętrznego, dowiesz się więcej o tych regułach w dalszej części tego artykułu.|
||[Blokuj klientów, którzy nie obsługują nowoczesnego uwierzytelniania](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Dołączanie Teams i usług zależnych do przypisywania aplikacji w chmurze.|
||[Użytkownicy wysokiego ryzyka muszą zmienić hasło](identity-access-policies.md#high-risk-users-must-change-password)|Wymusza Teams użytkowników do zmiany hasła podczas logowania, jeśli zostanie wykryte działanie wysokiego ryzyka dla ich konta. Upewnij się, Teams i usługi zależne znajdują się na liście aplikacji.|
||[Stosowanie zasad ochrony danych aplikacji](identity-access-policies.md#apply-app-data-protection-policies)|Upewnij się, Teams i usługi zależne znajdują się na liście aplikacji. Zaktualizuj zasady dla każdej platformy (iOS, Android, Windows).|
|**Enterprise**|[Wymagaj uwierzytelniania wieloskładnikowego, gdy ryzyko logowania jest *niskie*, *średnie* lub *wysokie*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Teams ma również reguły dostępu gościa i dostępu zewnętrznego, dowiesz się więcej o tych regułach w dalszej części tego artykułu. Uwzględnij Teams i usługi zależne w tych zasadach.|
||[Definiowanie zasad zgodności urządzeń](identity-access-policies.md#define-device-compliance-policies)|Uwzględnij Teams i usługi zależne w tych zasadach.|
||[Wymagaj zgodnych komputerów *i* urządzeń przenośnych](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Uwzględnij Teams i usługi zależne w tych zasadach.|
|**Wyspecjalizowane zabezpieczenia**|[*Zawsze* wymagaj uwierzytelniania wieloskładnikowego](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Niezależnie od tożsamości użytkownika uwierzytelnianie wieloskładnikowe będzie używane przez organizację. Uwzględnij Teams i usługi zależne w tych zasadach. |

## <a name="teams-dependent-services-architecture"></a>architektura usług zależnych Teams

Aby uzyskać więcej informacji, na poniższym diagramie przedstawiono usługi, na których Teams polega. Aby uzyskać więcej informacji i ilustracji, zobacz [Microsoft Teams i powiązane usługi produktywności w Microsoft 365 dla architektów IT](../../solutions/productivity-illustrations.md).

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png" alt-text="Diagram przedstawiający zależności Teams od SharePoint, OneDrive dla Firm i Exchange" lightbox="../../media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png":::

## <a name="guest-and-external-access-for-teams"></a>Dostęp gościa i dostępu zewnętrznego dla Teams

Microsoft Teams definiuje następujące typy dostępu:

- **Dostęp gościa** używa konta Azure AD B2B dla gościa lub użytkownika zewnętrznego, który może zostać dodany jako członek zespołu i ma uprawnienia dostępu do komunikacji i zasobów zespołu.

- **Dostęp zewnętrzny** jest przeznaczony dla użytkownika zewnętrznego, który nie ma konta Azure AD B2B. Dostęp zewnętrzny może obejmować zaproszenia i uczestnictwo w rozmowach, czatach i spotkaniach, ale nie obejmuje członkostwa w zespole ani dostępu do zasobów zespołu.

Zasady dostępu warunkowego mają zastosowanie tylko do dostępu gościa w Teams, ponieważ istnieje odpowiedni Azure AD konta B2B.

<!--
In Azure AD, guest and external users are the same. The user type for both of these is Guest. Guest users are B2B users. Microsoft Teams differentiates between guest users and external users in the app. While it's important to understand how each of these are treated in Teams, both types of users are B2B users in Azure AD and the recommended policies for B2B users apply to both.

-->

Aby uzyskać zalecane zasady zezwalające na dostęp dla użytkowników-gości i użytkowników zewnętrznych z kontem Azure AD B2B, zobacz [Zasady zezwalania na dostęp gościa i zewnętrznego konta B2B](identity-access-policies-guest-access.md).

### <a name="guest-access-in-teams"></a>Dostęp gościa w Teams

Oprócz zasad dla użytkowników, którzy są wewnętrzni dla Twojej firmy lub organizacji, administratorzy mogą zezwolić na dostęp gościa, aby umożliwić osobom spoza firmy lub organizacji dostęp do Teams zasobów i interakcję z osobami wewnętrznymi w przypadku takich elementów jak rozmowy grupowe, czaty i spotkania.

Aby uzyskać więcej informacji na temat dostępu gościa i sposobu jego implementacji, zobacz [Teams dostępu gościa](/microsoftteams/guest-access).

### <a name="external-access-in-teams"></a>Dostęp zewnętrzny w Teams

Dostęp zewnętrzny jest czasami mylony z dostępem gościa, dlatego ważne jest, aby mieć pewność, że te dwa mechanizmy dostępu nieinternacjonalne są różnymi typami dostępu.

Dostęp zewnętrzny umożliwia Teams użytkownikom z całej domeny zewnętrznej znajdowanie, wywoływanie, czatowanie i konfigurowanie spotkań z użytkownikami w Teams. Teams administratorzy konfigurują dostęp zewnętrzny na poziomie organizacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie dostępem zewnętrznym w Microsoft Teams](/microsoftteams/manage-external-access).

Użytkownicy dostępu zewnętrznego mają mniejszy dostęp i funkcje niż osoba, która została dodana za pośrednictwem dostępu gościa. Na przykład użytkownicy dostępu zewnętrznego mogą rozmawiać z użytkownikami wewnętrznymi przy użyciu Teams, ale nie mogą uzyskiwać dostępu do kanałów zespołu, plików ani innych zasobów.

Dostęp zewnętrzny nie używa Azure AD kont użytkowników B2B i dlatego nie używa zasad dostępu warunkowego.

## <a name="teams-policies"></a>zasady Teams

Poza typowymi zasadami wymienionymi powyżej istnieją zasady specyficzne dla Teams, które mogą i powinny być skonfigurowane do zarządzania różnymi funkcjami Teams.

### <a name="teams-and-channels-policies"></a>zasady Teams i kanałów

Teams i kanały są dwoma często używanymi elementami w Microsoft Teams i istnieją zasady, które można wprowadzić, aby kontrolować, co użytkownicy mogą, a czego nie mogą robić w przypadku korzystania z zespołów i kanałów. Jeśli twoja organizacja ma co najmniej 5000 użytkowników, możesz utworzyć globalny zespół, ale prawdopodobnie warto mieć mniejsze zespoły i kanały do określonych celów, zgodnie z potrzebami organizacji.

Zaleca się zmianę zasad domyślnych lub tworzenie zasad niestandardowych. Więcej informacji na temat zarządzania zasadami można znaleźć pod tym linkiem: [Zarządzanie zasadami zespołów w Microsoft Teams](/microsoftteams/teams-policies).

### <a name="messaging-policies"></a>Zasady obsługi komunikatów

Obsługa wiadomości lub czatów może być również zarządzana za pośrednictwem domyślnych zasad globalnych lub za pośrednictwem zasad niestandardowych, co może pomóc użytkownikom komunikować się ze sobą w sposób odpowiedni dla Twojej organizacji. Te informacje można przejrzeć na stronie [Zarządzanie zasadami obsługi komunikatów w Teams](/microsoftteams/messaging-policies-in-teams).

### <a name="meeting-policies"></a>Zasady spotkań

Żadna dyskusja na temat Teams nie byłaby kompletna bez planowania i wdrażania zasad dotyczących Teams spotkań. Spotkania są istotnym elementem Teams, dzięki czemu użytkownicy mogą formalnie spotykać się i prezentować wielu użytkownikom jednocześnie oraz udostępniać zawartość istotną dla spotkania. Ustawienie odpowiednich zasad organizacji wokół spotkań jest niezbędne.

Aby uzyskać więcej informacji, zobacz [Zarządzanie zasadami spotkań w Teams](/microsoftteams/meeting-policies-in-teams).

### <a name="app-permission-policies"></a>Zasady uprawnień aplikacji

Teams umożliwia również korzystanie z aplikacji w różnych miejscach, takich jak kanały lub czaty osobiste. Posiadanie zasad dotyczących tego, które aplikacje można dodawać i używać oraz gdzie, jest niezbędne do utrzymania środowiska bogatego w zawartość, które jest również bezpieczne.

Aby uzyskać więcej informacji na temat zasad uprawnień aplikacji, zobacz [Zarządzanie zasadami uprawnień aplikacji w Microsoft Teams](/microsoftteams/teams-app-permission-policies).

## <a name="next-steps"></a>Następne kroki

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="Krok 4. Zasady dotyczące aplikacji w chmurze Microsoft 365" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

Skonfiguruj zasady dostępu warunkowego dla:

- [Exchange Online](secure-email-recommended-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
