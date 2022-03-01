---
title: Informacje dotyczące ochrony przed utratą danych
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: ''
ms.collection:
- M365-security-compliance
- SPO_Content
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ROBOTS: NOINDEX, NOFOLLOW
feedback_system: None
description: materiały referencyjne dotyczące ochrony przed utratą danych
ms.openlocfilehash: 0c7fe1d3ccf1b74641be1d05506f1cc53b743218
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63014923"
---
# <a name="data-loss-prevention-reference"></a>Informacje dotyczące ochrony przed utratą danych

> [!IMPORTANT]
> Ten temat nie jest już głównym zasobem do Microsoft 365 ochrony przed utratą danych (DLP). Zestaw zawartości DLP jest aktualizowany i ma strukturę restrukcyjną. Tematy omawiane w tym artykule zostaną poruszane w nowych, zaktualizowanych artykułach. Aby uzyskać więcej informacji na temat ochrony przed utratą danych, zobacz [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md).

<!-- this topic needs to be split into smaller, more coherent ones. It is confusing as it is. -->
<!-- move this note to a more appropriate place, no topic should start with a note -->
> [!NOTE]
> Funkcje ochrony przed utratą danych zostały ostatnio dodane do wiadomości czatu Microsoft Teams i kanałów dla użytkowników z licencją na usługę Office 365 Advanced Compliance, która jest dostępna jako opcja autonomiczna i jest zawarta w Office 365 E5 oraz Zgodność platformy Microsoft 365 E5. Aby dowiedzieć się więcej o wymaganiach licencjonowania, zobacz [Microsoft 365 Tenant-Level licencjonowania usług firmy Microsoft](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance).



<!-- MOVED TO LEARN ABOUT To comply with business standards and industry regulations, organizations must protect sensitive information and prevent its inadvertent disclosure. Sensitive information can include financial data or personally identifiable information (PII) such as credit card numbers, social security numbers, or health records. With a data loss prevention (DLP) policy in the Office 365 Security &amp; Compliance Center, you can identify, monitor, and automatically protect sensitive information across Office 365.

With a DLP policy, you can:

- **Identify sensitive information across many locations, such as Exchange Online, SharePoint Online, OneDrive for Business, and Microsoft Teams.**

    For example, you can identify any document containing a credit card number that's stored in any OneDrive for Business site, or you can monitor just the OneDrive sites of specific people.

- **Prevent the accidental sharing of sensitive information**.

    For example, you can identify any document or email containing a health record that's shared with people outside your organization, and then automatically block access to that document or block the email from being sent.

- **Monitor and protect sensitive information in the desktop versions of Excel, PowerPoint, and Word.**

    Just like in Exchange Online, SharePoint Online, and OneDrive for Business, these Office desktop programs include the same capabilities to identify sensitive information and apply DLP policies. DLP provides continuous monitoring when people share content in these Office programs.

- **Help users learn how to stay compliant without interrupting their workflow.**

    You can educate your users about DLP policies and help them remain compliant without blocking their work. For example, if a user tries to share a document containing sensitive information, a DLP policy can both send them an email notification and show them a policy tip in the context of the document library that allows them to override the policy if they have a business justification. The same policy tips also appear in Outlook on the web, Outlook, Excel, PowerPoint, and Word.

- **View DLP alerts and reports showing content that matches your organization’s DLP policies.**

    To view alerts and metadata related to your DLP policies you can use the [DLP Alerts Management Dashboard](dlp-configure-view-alerts-policies.md). You can also view policy match reports to assess how your organization is complying with a DLP policy. If a DLP policy allows users to override a policy tip and report a false positive, you can also view what users have reported

-->
## <a name="create-and-manage-dlp-policies"></a>Tworzenie zasad DLP i zarządzanie nimi

Zasady DLP tworzysz i zarządzasz na stronie Ochrona przed utratą danych w centrum Microsoft 365 zgodności.

![Stronie ochrony przed utratą danych w Centrum Office 365 zgodności &amp; zabezpieczeń.](../media/943fd01c-d7aa-43a9-846d-0561321a405e.png)

<!-- MOVED TO LEARN ABOUT ## What a DLP policy contains

A DLP policy contains a few basic things:

- Where to protect the content: **locations** such as Exchange Online, SharePoint Online, and OneDrive for Business sites, as well as Microsoft Teams chat and channel messages.

- When and how to protect the content by enforcing **rules** comprised of:

  - **Conditions** the content must match before the rule is enforced. For example, a rule might be configured to look only for content containing Social Security numbers that's been shared with people outside your organization.

  - **Actions** that you want the rule to take automatically when content matching the conditions is found. For example, a rule might be configured to block access to a document and send both the user and compliance officer an email notification.

You can use a rule to meet a specific protection requirement, and then use a DLP policy to group together common protection requirements, such as all of the rules needed to comply with a specific regulation.

For example, you might have a DLP policy that helps you detect the presence of information subject to the Health Insurance Portability and Accountability Act (HIPAA). This DLP policy could help protect HIPAA data (the what) across all SharePoint Online sites and all OneDrive for Business sites (the where) by finding any document containing this sensitive information that's shared with people outside your organization (the conditions) and then blocking access to the document and sending a notification (the actions). These requirements are stored as individual rules and grouped together as a DLP policy to simplify management and reporting.

![Diagram shows that DLP policy contains locations and rules.](../media/c006860c-2d00-42cb-aaa4-5b5638d139f7.png) -->

<!-- MOVED TO LEARN ABOUT ### Locations

DLP policies are applied to sensitive items across Microsoft 365 locations and can be further scoped as detailed in this table.


|Location | Include/exclude by|
|---------|---------|
|Exchange email| distribution groups|
|SharePoint sites |sites |
|OneDrive accounts |accounts |
|Teams chat and channel messages |accounts |
|Windows 10 devices |user or group |
|Microsoft Cloud App Security |instance |
 -->

<!-- moved to dlp-policy-reference.md
If you choose to include specific distribution groups in Exchange, the DLP policy will be scoped only to the members of that group. Similarly excluding a distribution group will exclude all the members of that distribution group from policy evaluation. You can choose to scope a policy to the members of distribution lists, dynamic distribution groups, and security groups. A DLP policy can contain no more than 50 such inclusions and exclusions.

If you choose to include or exclude specific SharePoint sites, a DLP policy can contain no more than 100 such inclusions and exclusions. Although this limit exists, you can exceed this limit by applying either an org-wide policy or a policy that applies to entire locations.

If you choose to include or exclude specific OneDrive accounts or groups, a DLP policy can contain no more than 100 user accounts or 50 groups as inclusion or exclusion.

### Rules

> [!NOTE]
> The default behavior of a DLP policy, when there is no alert configured, is not to alert or trigger. This applies only to default information types. For custom information types, the system will alert even if there is no action defined in the policy.

Rules are what enforce your business requirements on your organization's content. A policy contains one or more rules, and each rule consists of conditions and actions. For each rule, when the conditions are met, the actions are taken automatically. Rules are executed sequentially, starting with the highest-priority rule in each policy.

A rule also provides options to notify users (with policy tips and email notifications) and admins (with email incident reports) that content has matched the rule.

Here are the components of a rule, each explained below.

![Sections of the DLP rule editor.](../media/1859d504-b9c2-45ed-961b-a0092251acc2.png)

#### Conditions

Conditions are important because they determine what types of information you're looking for, and when to take an action. For example, you might choose to ignore content containing passport numbers unless the content contains more than 10 such numbers and is shared with people outside your organization.

Conditions focus on the **content**, such as what types of sensitive information you're looking for, and also on the **context**, such as who the document is shared with. You can use conditions to assign different actions to different risk levels. For example, sensitive content shared internally might be lower risk and require fewer actions than sensitive content shared with people outside the organization.

![List showing available DLP conditions.](../media/0fa43f90-d007-4506-ae93-43e8424fe103.png)

The conditions now available can determine if:

- Content contains a type of sensitive information.

- Content contains a label. For more information, see the below section [Using a retention label as a condition in a DLP policy](#using-a-retention-label-as-a-condition-in-a-dlp-policy).

- Content is shared with people outside or inside your organization.

  > [!NOTE]
  > Users who have non-guest accounts in a host organization's Active Directory or Azure Active Directory tenant are considered as people inside the organization.

#### Types of sensitive information

A DLP policy can help protect sensitive information, which is defined as a **sensitive information type**. Microsoft 365 includes definitions for many common sensitive information types across many different regions that are ready for you to use, such as a credit card number, bank account numbers, national ID numbers, and passport numbers.

![List of available sensitive information types.](../media/3eaa9911-bc94-44be-902f-363dbf3b07fe.png)

When a DLP policy looks for a sensitive information type such as a credit card number, it doesn't simply look for a 16-digit number. Each sensitive information type is defined and detected by using a combination of:

- Keywords.

- Internal functions to validate checksums or composition.

- Evaluation of regular expressions to find pattern matches.

- Other content examination.

This helps DLP detection achieve a high degree of accuracy while reducing the number of false positives that can interrupt peoples' work.

#### Actions

When content matches a condition in a rule, you can apply actions to automatically protect the content.

![List of available DLP actions.](../media/8aef17fc-1e99-4ac7-adfc-0f2c9c1a0697.png)

With the actions now available, you can:

- **Restrict access to the content** Depending on your need, you can restrict access to content in three ways:

  1. Restrict access to content for everyone.
  2. Restrict access to content for people outside the organization.
  3. Restrict access to "Anyone with the link."

  For site content, this means that permissions for the document are restricted for everyone except the primary site collection administrator, document owner, and person who last modified the document. These people can remove the sensitive information from the document or take other remedial action. When the document is in compliance, the original permissions are automatically restored. When access to a document is blocked, the document appears with a special policy tip icon in the library on the site.

  ![Policy tip showing access to document is blocked.](../media/b6cefed3-d212-43d7-8534-4b92b26ebd50.png)

  For email content, this action blocks the message from being sent. Depending on how the DLP rule is configured, the sender sees an NDR or (if the rule uses a notification) a policy tip and/or email notification.

  ![Warning that unauthorized recipients must be removed from the message.](../media/302f9994-912d-41e7-861f-8a4539b3c285.png)

#### User notifications and user overrides

You can use notifications and overrides to educate your users about DLP policies and help them remain compliant without blocking their work. For example, if a user tries to share a document containing sensitive information, a DLP policy can both send them an email notification and show them a policy tip in the context of the document library that allows them to override the policy if they have a business justification.

![User notifications and user overrides sections of DLP rule editor.](../media/37b560d4-6e4e-489e-9134-d4b9daf60296.png)

The email can notify the person who sent, shared, or last modified the content and, for site content, the primary site collection administrator and document owner. In addition, you can add or remove whomever you choose from the email notification.

In addition to sending an email notification, a user notification displays a policy tip:

- In Outlook and Outlook on the web.

- For the document on a SharePoint Online or OneDrive for Business site.

- In Excel, PowerPoint, and Word, when the document is stored on a site included in a DLP policy.

The email notification and policy tip explain why content conflicts with a DLP policy. If you choose, the email notification and policy tip can allow users to override a rule by reporting a false positive or providing a business justification. This can help you educate users about your DLP policies and enforce them without preventing people from doing their work. Information about overrides and false positives is also logged for reporting (see below about the DLP reports) and included in the incident reports (next section), so that the compliance officer can regularly review this information.

Here's what a policy tip looks like in a OneDrive for Business account.

![Policy tip for a document in a OneDrive account.](../media/f9834d35-94f0-4511-8555-0fe69855ce6d.png)

 To learn more about user notifications and policy tips in DLP policies, see [Use notifications and policy tips](use-notifications-and-policy-tips.md).

#### Alerts and Incident reports

When a rule is matched, you can send an alert email to your compliance officer (or any person(s) you choose) with details of the alert. This alert email will carry a link of the [DLP Alerts Management Dashboard](dlp-configure-view-alerts-policies.md) which the compliance officer can go to view the details of alert and events. The dashboard contains details of the event that triggered the alert along with details of the DLP policy matched and the sensitive content detected.

In addition, you can also send an incident report with details of the event. This report includes information about the item that was matched, the actual content that matched the rule, and the name of the person who last modified the content. For email messages, the report also includes as an attachment the original message that matches a DLP policy.

> [!div class="mx-imgBorder"]
> ![Page for configuring incident reports.](../media/Alerts-and-incident-report.png)

DLP scans email differently from items in SharePoint Online or OneDrive for Business. In SharePoint Online and OneDrive for Business, DLP scans existing items as well as new ones and generates an alert and incident report whenever a match is found. In Exchange Online, DLP only scans new email messages and generates a report if there is a policy match. DLP ***does not*** scan or match previously existing email items that are stored in a mailbox or archive.

## Grouping and logical operators

Often your DLP policy has a straightforward requirement, such as to identify all content that contains a U.S. Social Security Number. However, in other scenarios, your DLP policy might need to identify more loosely defined data.

For example, to identify content subject to the U.S. Health Insurance Act (HIPAA), you need to look for:

- Content that contains specific types of sensitive information, such as a U.S. Social Security Number or Drug Enforcement Agency (DEA) Number.

    AND

- Content that's more difficult to identify, such as communications about a patient's care or descriptions of medical services provided. Identifying this content requires matching keywords from very large keyword lists, such as the International Classification of Diseases (ICD-9-CM or ICD-10-CM).

You can easily identify such loosely defined data by using grouping and logical operators (AND, OR). When you create a DLP policy, you can:

- Group sensitive information types.

- Choose the logical operator between the sensitive information types within a group and between the groups themselves.

### Choosing the operator within a group

Within a group, you can choose whether any or all of the conditions in that group must be satisfied for the content to match the rule.

![Group showing the operators within the group.](../media/6a12f1e8-112d-48ee-9a73-82b3dd0542e7.png)

### Adding a group

You can quickly add a group, which can have its own conditions and operator within that group.

![Add group button.](../media/5f72f292-d1f3-4f11-a911-a9f71e10abf6.png)

### Choosing the operator between groups

Between groups, you can choose whether the conditions in just one group or all of the groups must be satisfied for the content to match the rule.

For example, the built-in **U.S. HIPAA** policy has a rule that uses an **AND** operator between the groups so that it identifies content that contains:

- from the group **PII Identifiers** (at least one SSN number **OR** DEA number)

    **AND**

- from the group **Medical Terms** (at least one ICD-9-CM keyword **OR** ICD-10-CM keyword)

![Groups showing the operator between groups.](../media/354aa77f-569c-4847-9dfe-605ee2bb28d1.png)

## The priority by which rules are processed

When you create rules in a policy, each rule is assigned a priority in the order in which it's created — meaning, the rule created first has first priority, the rule created second has second priority, and so on.

> [!div class="mx-imgBorder"]
> ![Rules in priority order.](../media/dlp-rules-in-priority-order.png)

After you have set up more than one DLP policy, you can change the priority of one or more policies. To do that, select a policy, choose **Edit policy**, and use the **Priority** list to specify its priority.

> [!div class="mx-imgBorder"]
> ![Set priority for a policy.](../media/dlp-set-policy-priority.png)

When content is evaluated against rules, the rules are processed in priority order. If content matches multiple rules, the rules are processed in priority order and the most restrictive action is enforced. For example, if content matches all of the following rules, Rule 3 is enforced because it's the highest priority, most restrictive rule:

- Rule 1: only notifies users

- Rule 2: notifies users, restricts access, and allows user overrides

- Rule 3: notifies users, restricts access, and does not allow user overrides

- Rule 4: only notifies users

- Rule 5: restricts access

- Rule 6: notifies users, restricts access, and does not allow user overrides

In this example, note that matches for all of the rules are recorded in the audit logs and shown in the DLP reports, even though only the most restrictive rule is enforced.

Regarding policy tips, note that:

- Only the policy tip from the highest priority, most restrictive rule will be shown. For example, a policy tip from a rule that blocks access to content will be shown over a policy tip from a rule that simply sends a notification. This prevents people from seeing a cascade of policy tips.

- If the policy tips in the most restrictive rule allow people to override the rule, then overriding this rule also overrides any other rules that the content matched.

-->

## <a name="tuning-rules-to-make-them-easier-or-harder-to-match"></a>Dostosowywanie reguł w celu ich łatwiejszego lub trudniejszego dopasowania

Gdy inne osoby tworzą i włączają swoje zasady ochrony przed zasadami ochrony przed prywatnością, czasami mogą one rozwiązać następujące problemy:

- Zbyt duża zawartość, która **nie zawiera informacji** poufnych, jest taka inna niż w przypadku reguł, czyli zbyt wielu wyników fałszywie dodatnich.

- Zbyt mała zawartość, **w przypadku których są** poufne informacje, jest taka jak w przypadku reguł. Innymi słowy, działania zabezpieczające nie są wymuszane na informacjach poufnych.

Aby rozwiązać te problemy, możesz dostosować reguły, dostosowując liczbę wystąpień i dokładność dopasowania, aby utrudnić lub ułatwić dopasowywanie zawartości do reguł. Każdy typ informacji poufnych użyty w  reguły ma zarówno liczbę wystąpień, jak i dokładność dopasowania.

### <a name="instance-count"></a>Liczba wystąpień

Liczba wystąpień oznacza po prostu to, ile wystąpień określonego typu informacji poufnych musi się znajdować, aby zawartość spełniała ta reguła. Na przykład zawartość jest odpowiada pokazanej poniżej regułie, jeśli między 1 a 9 unikatowymi wartościami w Stanach Zjednoczonych lub Wielkiej Brytanii numery paszportów.

> [!NOTE]
> Liczba wystąpień uwzględnia tylko **unikatowe dopasowania** dla typów informacji poufnych i słów kluczowych. Jeśli na przykład wiadomość e-mail zawiera 10 wystąpień tego samego numeru karty kredytowej, te 10 wystąpień jest liczone jako jedno wystąpienie numeru karty kredytowej.

Aby dostrajać reguły za pomocą liczby wystąpień, można łatwo uzyskać wskazówki:

- Aby łatwiej dopasować regułę, zmniejsz liczbę **min** i/lub zwiększ liczbę **maksymalną** . Możesz również ustawić wartość **max** **na dowolną,** usuwając wartość liczbową.

- Aby trudniej dopasować regułę, zwiększ liczbę **minut** .

Zazwyczaj w  regułach o mniejszej liczby wystąpień (na przykład 1–9) używa się mniej restrykcyjnych akcji, takich jak wysyłanie powiadomień użytkowników. W  regułach o większej liczby wystąpień (na przykład 10-any) można stosować bardziej restrykcyjne akcje, takie jak ograniczanie dostępu do zawartości bez zezwalania na zastępowanie zawartości.

![Wystąpienie zlicza się w edytorze reguł.](../media/e7ea3c12-72c5-4bb3-9590-c924c665e84d.png)

### <a name="match-accuracy"></a>Dokładność dopasowania

Jak opisano powyżej, typ informacji poufnych jest definiowany i wykrywany przy użyciu połączenia różnych rodzajów dowodów. Często typ informacji poufnych jest definiowany przez wiele takich kombinacji, nazywanych wzorcami. Wzorzec, który wymaga mniejszej liczby dowodów, ma mniejszą dokładność dopasowania (czyli poziom ufności), natomiast wzorzec wymagający więcej dowodów zapewnia większą dokładność dopasowania (czyli poziom ufności). Aby dowiedzieć się więcej o rzeczywistych wzorcach i poziomach ufności używanych przez wszystkie poufne typy informacji, zobacz Definicje encji [typu informacji poufnych](sensitive-information-type-entity-definitions.md).

Na przykład typ informacji poufnych o nazwie Numer karty kredytowej jest definiowany przez dwa wzorce:

- Wzorzec z pewnością 65%, który wymaga:

  - Liczba w formacie numeru karty kredytowej.

  - Liczba przechodząca przez te sumy.

- Wzorzec z pewnością na poziomie 85%, który wymaga:

  - Liczba w formacie numeru karty kredytowej.

  - Liczba przechodząca przez te sumy.

  - Słowo kluczowe lub data wygaśnięcia w odpowiednim formacie.

Tych poziomów ufności (lub dokładności dopasowania) można używać w swoich zasadach. Zazwyczaj w  regułach o mniejszej dokładności dopasowania używasz mniej restrykcyjnych akcji, takich jak wysyłanie powiadomień użytkowników. W  regułach o większej dokładności dopasowań można także stosować bardziej restrykcyjne akcje, takie jak ograniczanie dostępu do zawartości bez zezwalania na zastępowanie zawartości.

Ważne jest, aby zrozumieć, że w przypadku zidentyfikowania w zawartości określonego typu informacji poufnych, na przykład numeru karty kredytowej, zwracany jest tylko pojedynczy poziom ufności:

- Jeśli wszystkie dopasowania mają jeden wzorzec, zwracany jest poziom ufności tego wzorca.

- Jeśli istnieją dopasowania dla więcej niż jednego wzorca (czyli istnieją dopasowania z dwoma różnymi poziomami ufności), zwracany jest poziom ufności wyższy niż którykolwiek z pojedynczych wzorców. To kłopotliwa część. Na przykład w przypadku karty kredytowej, jeśli zostaną dopasowane wzorce 65% i 85%, poziom ufności zwrócony dla tego typu informacji poufnych jest większy niż 90%, ponieważ więcej dowodów oznacza większą pewność.

Jeśli więc chcesz utworzyć dwie wzajemnie wykluczające się reguły dla kart kredytowych: jedną dla dokładności dopasowania na poziomie 65%, a jedną dla dokładności dopasowania na poziomie 85%, zakresy dokładności dopasowania będą wyglądać tak. Pierwsza reguła wybiera tylko dopasowania do wzorca 65%. Druga reguła wybiera dopasowania z co **najmniej jednym 85**% dopasowaniem i potencjalnie może  mieć inne dopasowania o niższym poziomie ufności.

![Dwie reguły z różnymi zakresami w celu zapewnienia dokładności dopasowania.](../media/21bdfe36-7a91-4347-8098-11809a92f9a4.png)

Oto wskazówki dotyczące tworzenia reguł o różnych dokładnościach dopasowania:

- Najniższy poziom ufności zazwyczaj stosuje tę samą wartość dla **wartości min** i **maksimum** (nie zakres).

- Najwyższy poziom ufności zazwyczaj należy do przedziału od nieco powyżej do 100.

- Poziom ufności w przedziale zazwyczaj wynosi od tuż powyżej dolnego do tuż poniżej wyższego poziomu ufności.

## <a name="using-a-retention-label-as-a-condition-in-a-dlp-policy"></a>Używanie etykiety przechowywania jako warunku zasad DLP

W przypadku używania wcześniej utworzonej [i opublikowanej](retention.md#retention-labels) etykiety przechowywania jako warunku zasad DLP należy pamiętać o kilku rzeczach:

- Etykieta przechowywania należy utworzyć i opublikować przed podjęciem próby użycia jej jako warunku w zasadach DLP.
- Synchronizacja opublikowanych etykiet przechowywania może potrwać od jednego do siedmiu dni. Aby uzyskać więcej informacji, [](create-apply-retention-labels.md#when-retention-labels-become-available-to-apply) zobacz Gdy etykiety przechowywania stają się dostępne w celu zastosowania etykiet przechowywania opublikowanych w zasadach [](apply-retention-labels-automatically.md#how-long-it-takes-for-retention-labels-to-take-effect) przechowywania oraz Jak długo etykiety przechowywania są stosowane w przypadku etykiet przechowywania publikowanych automatycznie.
- Używanie etykiety przechowywania w zasadach **jest obsługiwane tylko w przypadku elementów w SharePoint i OneDrive***.

  ![Etykiety jako warunek.](../media/5b1752b4-a129-4a88-b010-8dcf8a38bb09.png)

  Etykiety przechowywania warto używać w zasadach ochrony przed zasadami DLP, jeśli istnieją elementy, które są w trakcie przechowywania i stosowania do nich innych kontrolek, na przykład:

  - Opublikowano etykietę przechowywania o nazwie rok **2018**, która w przypadku stosowania do dokumentów podatkowych z roku 2018 przechowywanych w programie SharePoint zachowuje je przez 10 lat, a następnie je zutylizuje. Ponadto nie chcesz, aby te elementy były udostępniane poza organizacją, co możesz zrobić przy użyciu zasad DLP.

  > [!IMPORTANT]
  > Ten błąd zostanie podany, jeśli jako warunek zasad DLP określisz etykietę przechowywania i dołączysz również jako lokalizację etykietę przechowywania Exchange i/lub Teams: "Ochrona zawartości oznaczonej etykietą w wiadomościach e-mail i wiadomościach zespołów nie jest obsługiwana **. Usuń etykietę poniżej lub wyłącz Exchange i Teams jako lokalizację".** Jest tak, ponieważ Exchange nie ocenia metadanych etykiet podczas przesyłania i dostarczania wiadomości.

### <a name="using-a-sensitivity-label-as-a-condition-in-a-dlp-policy"></a>Używanie etykiety wrażliwości jako warunku zasad DLP

[Dowiedz się więcej](./dlp-sensitivity-label-as-condition.md) o używaniu etykiety wrażliwości jako warunku w zasadach DLP.

### <a name="how-this-feature-relates-to-other-features"></a>Relacja tej funkcji z innymi funkcjami

Do zawartości zawierającej poufne informacje można stosować kilka funkcji:

- [Etykieta przechowywania i zasady przechowywania mogą](retention.md) wymuszać **akcje przechowywania** dla tej zawartości.

- Zasady DLP mogą wymuszać **akcje** ochrony przed tą zawartością. Ponadto przed rozpoczęciem tych akcji zasady DLP mogą wymagać, aby oprócz zawartości zawierającej etykietę zostały spełnione inne warunki.

![Diagram funkcji, które można stosować do informacji poufnych.](../media/dd410f97-a3a3-455c-a1e9-7ed8ae6893d6.png)

Pamiętaj, że zasady DLP mają bogatszą funkcję wykrywania niż etykieta lub zasady przechowywania stosowane do informacji poufnych. Zasady DLP mogą wymuszać akcje zabezpieczające przed zawartością zawierającą informacje poufne, a jeśli poufne informacje zostaną usunięte z tej zawartości, takie działania zabezpieczające zostaną cofnięte przy następnym skanowaniu zawartości. Jednak w przypadku zastosowania zasad przechowywania lub etykiety do zawartości zawierającej informacje poufne jest to akcja razowa, która nie zostanie cofnięta, nawet jeśli poufne informacje zostaną usunięte.

Używając etykiety jako warunku zasad DLP, można wymusić zarówno akcje przechowywania, jak i ochrony dla zawartości, które są na tej etykiecie. Zawartość zawierającą etykietę przypomina właśnie zawartość zawierającą informacje poufne — zarówno etykieta, jak i typ informacji poufnych są właściwościami używanymi do klasyfikowania zawartości, dzięki czemu można wymusić działania na tej zawartości.

![Diagram zasad DLP z użyciem etykiety jako warunku.](../media/4538fd8f-fb74-4743-bc22-a5de33adfebb.png)

## <a name="simple-settings-vs-advanced-settings"></a>Ustawienia proste a ustawienia zaawansowane

Podczas tworzenia zasad DLP możesz wybrać proste lub zaawansowane ustawienia:

- **Proste ustawienia** ułatwiają tworzenie najpopularniejszych zasad DLP bez używania edytora reguł do tworzenia i modyfikowania reguł.

- **Ustawienia zaawansowane** zapewniają pełną kontrolę nad każdym ustawieniem zasad DLP za pomocą edytora reguł.

W tej samej technologii proste ustawienia i ustawienia zaawansowane działają dokładnie tak samo, wymuszając reguły złożone z warunków i akcji — tylko przy użyciu prostych ustawień nie widzisz edytora reguł. Jest to szybki sposób na utworzenie zasad DLP.

### <a name="simple-settings"></a>Proste ustawienia

Na razie najbardziej typowe scenariusze ochrony przed naruszeniem zasad DLP to tworzenie zasad chroniących zawartość zawierającą poufne informacje przed udostępnianiu osobom spoza organizacji oraz podejmowanie automatycznych działań naprawczych, takich jak ograniczanie dostępu do zawartości, wysyłanie powiadomień użytkowników końcowych lub administratorów oraz inspekcja zdarzenia w celu późniejszego badania. Zapobieganie niezamierzonemu ujawnianiu informacji poufnych przez użytkowników.

Aby uprościć osiągnięcia tego celu, podczas tworzenia zasad DLP możesz wybrać **pozycję Użyj prostych ustawień**. Te ustawienia zapewniają wszystko, co potrzebne do wdrożenia najpopularniejszych zasad DLP bez konieczności wejścia do edytora reguł.

![Opcje DLP dla ustawień prostych i zaawansowanych.](../media/33c93824-ead5-43b6-9c3e-fd1630c92a7d.png)

### <a name="advanced-settings"></a>Ustawienia zaawansowane

Jeśli chcesz utworzyć bardziej dostosowane zasady ochrony przed zasadami DLP, możesz wybrać pozycję **Użyj ustawień zaawansowanych**.

Ustawienia zaawansowane są obecne za pomocą edytora reguł, w którym masz pełną kontrolę nad każdą możliwą opcją, w tym liczbę wystąpień i dokładność dopasowania (poziom ufności) dla każdej reguły.

Aby szybko przejść do sekcji, kliknij element w górnym okienku nawigacji edytora reguł, aby przejść do tej sekcji poniżej.

![Górne menu nawigacji edytora reguł DLP.](../media/c527b97f-ca53-4c79-ad19-1a63be8a8ecc.png)

## <a name="dlp-policy-templates"></a>Szablony zasad DLP

Pierwszym krokiem podczas tworzenia zasad DLP jest wybranie informacji do ochrony. Rozpoczynając od szablonu DLP, możesz zapisać pracę nad tworzeniem nowego zestawu reguł od podstaw i dowiedzieć się, które typy informacji powinny być domyślnie uwzględniane. Następnie można dodawać i modyfikować te wymagania, aby precyzyjnie dostosować regułę do wymagań specyficznych dla organizacji.

Wstępnie skonfigurowany szablon zasad DLP może ułatwić wykrywanie konkretnych typów informacji poufnych, takich jak dane HIPAA, dane PCI-DSS, dane Gramm-Leach-Bliley Act, a nawet informacje umożliwiające identyfikację użytkownika specyficzne dla lokalizacji (P.I). Aby ułatwić znajdowanie i ochronę typowych typów informacji poufnych, szablony zasad zawarte w programie Microsoft 365 już zawierają najbardziej typowe typy informacji poufnych niezbędne do rozpoczęcia pracy.

![Lista szablonów zasad ochrony przed utratą danych z fokusem na szablonie dla amerykańskiej ustawy o ochronie przed utratą danych.](../media/791b2403-430b-4987-8643-cc20abbd8148.png)

Twoja organizacja może mieć także własne, specyficzne wymagania, w którym w takim przypadku możesz utworzyć zasady DLP od podstaw, wybierając opcję **Zasady** niestandardowe. Zasady niestandardowe są puste i nie zawierają żadnych wstępnie obowiązujących reguł.

<!-- ## Roll out DLP policies gradually with test mode

rehomed to Plan for DLP

When you create your DLP policies, you should consider rolling them out gradually to assess their impact and test their effectiveness before fully enforcing them. For example, you don't want a new DLP policy to unintentionally block access to thousands of documents that people require access to in order to get their work done.

If you're creating DLP policies with a large potential impact, we recommend following this sequence:

1. **Start in test mode without Policy Tips** and then use the DLP reports and any incident reports to assess the impact. You can use DLP reports to view the number, location, type, and severity of policy matches. Based on the results, you can fine tune the rules as needed. In test mode, DLP policies will not impact the productivity of people working in your organization.

2. **Move to Test mode with notifications and Policy Tips** so that you can begin to teach users about your compliance policies and prepare them for the rules that are going to be applied. At this stage, you can also ask users to report false positives so that you can further refine the rules.

3. **Start full enforcement on the policies** so that the actions in the rules are applied and the content's protected. Continue to monitor the DLP reports and any incident reports or notifications to make sure that the results are what you intend.

    ![Options for using test mode and turning on policy.](../media/49fafaac-c6cb-41de-99c4-c43c3e380c3a.png)

    You can turn off a DLP policy at any time, which affects all rules in the policy. However, each rule can also be turned off individually by toggling its status in the rule editor.

    ![Options for turning off a rule in a policy.](../media/f7b258ff-1b8b-4127-b580-83c6492f2bef.png)

    You can also change the priority of multiple rules in a policy. To do that, open a policy for editing. In a row for a rule, choose the ellipses (**...**), and then choose an option, such as **Move down** or **Bring to last**.

    > [!div class="mx-imgBorder"]
    > ![Set rule priority.](../media/dlp-set-rule-priority.png)-->

## <a name="dlp-reports"></a>Raporty DLP

Po utworzeniu i włączeniu zasad DLP należy sprawdzić, czy działają zgodnie z twoimi zamiarami, i pomóc w zachowania zgodności. Dzięki raportom DLP możesz szybko wyświetlać liczbę reguł i zasad DLP w czasie oraz liczbę wyników fałszywie dodatnich i zastępować. W przypadku każdego raportu można filtrować dopasowania według lokalizacji, ramy czasowe, a nawet zawęzić je do konkretnych zasad, reguł lub akcji.

Dzięki raportom DLP możesz uzyskać szczegółowe informacje biznesowe oraz:

- Skoncentruj się na określonych okresach czasu i poznaj przyczyny kolekcji i trendów.

- Odnajdowanie procesów biznesowych naruszających zasady zgodności organizacji.

- Zrozumienie jakiegokolwiek wpływu biznesowego zasad DLP.

Ponadto przy użyciu raportów funkcji DLP można precyzyjnie dostosować zasady DLP podczas ich uruchamiania.

![Pulpit nawigacyjny Raporty w Centrum zabezpieczeń i zgodności.](../media/6d741252-a0ce-4429-95ba-6c857ecc9a7e.png)

## <a name="how-dlp-policies-work"></a>Jak działają zasady DLP

Rozwiązanie DLP wykrywa informacje poufne za pomocą szczegółowej analizy zawartości (nie tylko prostego skanowania tekstu). W tej dogłębnej analizie zawartości są używane dopasowania słów kluczowych, dopasowania słowników, oceny wyrażeń regularnych, funkcji wewnętrznych i innych metod wykrywania zawartości, która jest taka, jak w przypadku zasad DLP. Potencjalnie tylko niewielka część danych jest uznawana za poróżnianą. Zasady DLP mogą identyfikować, monitorować i automatycznie chronić te dane bez utrudniania i wpływu na osoby, które pracują z pozostałą zawartością.

### <a name="policies-are-synced"></a>Zasady są synchronizowane

Po utworzeniu zasad DLP &amp; w Centrum zgodności zabezpieczeń są one przechowywane w centralnym magazynie zasad, a następnie synchronizowane z różnymi źródłami zawartości, w tym:

- Exchange Online, a następnie do Outlook w sieci Web i Outlook.

- OneDrive dla Firm witryn internetowych.

- SharePoint witryny online.

- Office programów klasycznych (Excel, PowerPoint i Word).

- Microsoft Teams kanałów i wiadomości czatu.

Po zsynchronizowaniu zasad z właściwymi lokalizacjami zaczyna ona oceniać zawartość i wymuszać akcje.
<!-- what is the time delay for first deployment of a policy and what is the sync schedule? -->

### <a name="policy-evaluation-in-onedrive-for-business-and-sharepoint-online-sites"></a>Ocena zasad w witrynach OneDrive dla Firm i SharePoint Online

We wszystkich witrynach SharePoint Online i witrynach OneDrive dla Firm dokumenty stale się zmieniają — są stale tworzone, edytowane, udostępniane i tak dalej. Oznacza to, że dokumenty mogą być w dowolnym momencie w konflikcie lub być zgodne z zasadami DLP. Na przykład osoba może przekazać do witryny zespołu dokument, który nie zawiera informacji poufnych, ale później inna osoba może edytować ten sam dokument i dodawać do niego informacje poufne.

Z tego powodu zasady DLP często sprawdzają dokumenty pod czyjąś zasadą w tle. Można to powiedzieć jako asynchroniczne ocenianie zasad.
<!-- what is the frequency? looks like it is tied to the search crawl schedule -->

#### <a name="how-it-works"></a>Jak to działa

Gdy inne osoby dodają lub zmieniają dokumenty w swoich witrynach, wyszukiwarka skanuje zawartość, aby można było ją później wyszukać. W takim przypadku zawartość jest również skanowana w celu sprawdzenia, czy jest udostępniana. Wszelkie odnalezione informacje poufne są bezpiecznie przechowywane w indeksie wyszukiwania, dzięki czemu tylko zespół zgodności może uzyskać do nich dostęp, ale nie typowy użytkownicy. Wszystkie włączone zasady DLP są uruchamiane w tle (asynchronicznie), a także często wyszukuje zawartość, która jest taka jak zasada, i stosuje akcje w celu ich ochrony przed przypadkowymi wyciekami.

![Diagram przedstawiający sposób asynchronicznego oceniania zawartości przez zasady DLP.](../media/bdf73099-039a-4909-ae89-ac12c41992ba.png)

<!-- conflict with a DLP policy is bad wording -->
Na koniec dokumenty mogą być w konflikcie z zasadami DLP, ale mogą również być zgodne z zasadami DLP. Jeśli na przykład ktoś doda numery kart kredytowych do dokumentu, może to spowodować, że zasady DLP automatycznie blokują dostęp do dokumentu. Jeśli jednak ta osoba później usunie poufne informacje, akcja (w tym przypadku zablokowanie) zostanie automatycznie cofnięona podczas następnego oceny dokumentu pod względem zasad.

W przypadku zasad DLP jest szacowana dowolna zawartość, która może zostać zindeksowana. Aby uzyskać więcej informacji o domyślnych typach plików, zobacz Domyślne rozszerzenia nazw plików przeszukanych i typy plików analizowanych w [programie SharePoint Server](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types).

> [!NOTE]
> Aby zapobiec udostępnianiu dokumentów przed rozpoczęciem analizy przez zasady DLP, udostępnianie nowych plików w programie SharePoint można zablokować do momentu zindeksowania ich zawartości. Aby uzyskać szczegółowe informacje, zobacz Domyślne oznaczanie nowych [plików jako poufnych](/sharepoint/sensitive-by-default) .

### <a name="policy-evaluation-in-exchange-online-outlook-and-outlook-on-the-web"></a>Ocena zasad w Exchange Online, Outlook i Outlook w sieci Web

Po utworzeniu zasad DLP, które obejmują usługę Exchange Online jako lokalizację, zasady te są synchronizowane z Centrum zgodności zabezpieczeń usługi Office 365 &amp; do programu Exchange Online, a następnie z Exchange Online do Outlook w sieci Web i Outlook.

Podczas tworzenia wiadomości w programie Outlook może wyświetlić porady dotyczące zasad, gdy tworzona zawartość jest szacowana pod względem zasad DLP. Po wysłaniu wiadomość jest oceniana pod względem zasad DLP jako normalnego fragmentu przepływu poczty, razem z regułami przepływu poczty e-mail programu Exchange (nazywanymi również regułami transportu) i zasadami DLP utworzonymi w centrum administracyjnym usługi <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange</a>. Zasady DLP skanują zarówno wiadomość, jak i wszystkie załączniki.

### <a name="policy-evaluation-in-the-office-desktop-programs"></a>Ocena zasad w programach Office komputerowych

<!-- same capability to identify sensitive information line conflates sensitive information types and such -->
Excel, PowerPoint i Word mają tę samą funkcję identyfikowania informacji poufnych i stosowania zasad DLP, co w usługach SharePoint Online i OneDrive dla Firm. Te Office synchronizują swoje zasady DLP bezpośrednio z centralnego magazynu zasad, a następnie nieustannie oceniają zawartość pod względem zasad DLP, gdy osoby pracują z dokumentami otwieranym z witryny zawartej w zasadach DLP.

Ocena zasad DLP w aplikacji Office nie ma wpływu na wydajność programów ani na produktywność osób pracujących nad zawartością. Jeśli pracują nad dużym dokumentem lub komputer użytkownika jest zajęty, może mi potrwać kilka sekund, aż pojawi się porada o zasadach.

### <a name="policy-evaluation-in-microsoft-teams"></a>Ocena zasad w programie Microsoft Teams
 <!--what do you mean that it's synched to user accounts?  I thought DLP policies were applied to locations not users like sensitivity labels are  -->

Po utworzeniu zasad DLP, które obejmują usługę Microsoft Teams jako lokalizację, zasady te są synchronizowane z Centrum zgodności zabezpieczeń usługi Office 365 &amp; z kontami użytkowników oraz Microsoft Teams kanałami i wiadomościami czatu. W zależności od konfiguracji zasad DLP, gdy ktoś próbuje udostępnić poufne informacje na czacie Microsoft Teams lub wiadomości w kanale, wiadomość może zostać zablokowana lub odwołana. Ponadto dokumenty zawierające informacje poufne i udostępniane gościom (użytkownikom zewnętrznym) nie będą otwierane dla tych użytkowników. Aby dowiedzieć się więcej, zobacz [Zapobieganie utracie danych i Microsoft Teams](dlp-microsoft-teams.md).

## <a name="permissions"></a>Uprawnienia

Domyślnie administratorzy globalni, administratorzy zabezpieczeń i administratorzy zgodności mają dostęp do tworzenia i stosowania zasad DLP. Pozostali członkowie zespołu zgodności, którzy będą tworzyć zasady DLP, muszą mieć uprawnienia do Centrum &amp; zgodności zabezpieczeń. Domyślnie administrator &amp; dzierżawy będzie miał dostęp do tej lokalizacji i może udzielać służbom zgodności z przepisami i innym osobom dostępu do Centrum zgodności zabezpieczeń bez nadawania im wszystkich uprawnień administratora dzierżawy. W tym celu zalecamy:

1. Utwórz grupę w u Microsoft 365 i dodaj do niego pracowników do tego zespołu pracowników do zgodności.

2. Utwórz grupę ról na **stronie Uprawnienia** w Centrum zgodności &amp; zabezpieczeń.

3. Podczas tworzenia grupy ról użyj sekcji **Wybieranie ról** , aby dodać następującą rolę do grupy ról: Zarządzanie **zgodnością DLP**.

4. Za pomocą **sekcji Wybieranie** członków dodaj do Microsoft 365 ról utworzoną wcześniej grupę ról.

Możesz również utworzyć grupę ról z uprawnieniami tylko do wyświetlania zasad DLP i raportów DLP, przy użyciu roli Zarządzanie zgodnością **DLP** tylko do wyświetlania.

Aby uzyskać więcej informacji, zobacz [Zapewnianie użytkownikom dostępu do centrum Office 365 zgodności](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).

Te uprawnienia są wymagane tylko do tworzenia i stosowania zasad DLP. Wymuszanie zasad nie wymaga dostępu do zawartości.

## <a name="find-the-dlp-cmdlets"></a>Znajdowanie polecenia cmdlet DLP

Aby korzystać z większości funkcji cmdlet w Centrum &amp; zgodności zabezpieczeń, należy:

1. [Połączenie do Centrum Office 365 zgodności zabezpieczeń &amp; przy użyciu zdalnej obsługi programu PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. Użyj dowolnego z tych [cmdlet cmdlet policy-and-compliance-dlp](/powershell/module/exchange/export-dlppolicycollection).

Raporty DLP wymagają jednak ściągania danych z Microsoft 365 danych, w tym Exchange Online. Z tego powodu polecenia cmdlet dla raportów DLP są dostępne w programie **Exchange Online PowerShell — nie w programie &amp; PowerShell Centrum zgodności zabezpieczeń**. W związku z tym, aby korzystać z funkcji cmdlet na potrzeby raportów funkcji DLP, należy:

1. [Połączenie użyć Exchange Online zdalnej pracy z programem PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Użyj dowolnego z tych funkcji cmdlet dla raportów funkcji DLP:

    - [Get-DlpDetectionsReport](/powershell/module/exchange/Get-DlpDetectionsReport)

    - [Get-DlpDetailReport](/powershell/module/exchange/Get-DlpDetailReport)

## <a name="more-information"></a>Więcej informacji

- [Tworzenie zasad DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md)

- [Wysyłanie powiadomień i wyświetlanie porad dotyczących zasad DLP](use-notifications-and-policy-tips.md)

- [Tworzenie zasad DLP w celu ochrony dokumentów za pomocą fci lub innych właściwości](protect-documents-that-have-fci-or-other-properties.md)

- [Szablony zasad DLP](what-the-dlp-policy-templates-include.md)

- [Definicje jednostki typu informacji poufnych](sensitive-information-type-entity-definitions.md)

- [Funkcje typów informacji poufnych](sit-functions.md)

- [Tworzenie niestandardowego typu informacji poufnych](create-a-custom-sensitive-information-type.md)
