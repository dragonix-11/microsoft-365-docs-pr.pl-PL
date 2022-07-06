---
title: Twórz zasady DLP na podstawie szablonu
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: how-to
f1_keywords:
- ms.o365.cc.NewPolicyFromTemplate
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
ms.custom:
- seo-marvel-mar2020
- admindeeplinkCOMPLIANCE
description: W tym artykule dowiesz się, jak tworzyć zasady DLP przy użyciu jednego z szablonów zawartych w Office 365.
ms.openlocfilehash: 67d21d3e5a057960a4d3fa92bfaa709345cf38ff
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624592"
---
# <a name="create-a-dlp-policy-from-a-template"></a>Twórz zasady DLP na podstawie szablonu

Najprostszym, najbardziej typowym sposobem rozpoczęcia pracy z zasadami DLP jest użycie jednego z szablonów zawartych w portal zgodności Microsoft Purview. Możesz użyć jednego z tych szablonów w następującym stanie, w jakim jest, lub dostosować reguły w celu spełnienia określonych wymagań dotyczących zgodności organizacji.

Platforma Microsoft 365 zawiera ponad 40 gotowych do użycia szablonów, które mogą pomóc w spełnieniu szerokiego zakresu typowych wymagań dotyczących zasad regulacyjnych i biznesowych. Zobacz; [Szablony zasad](dlp-policy-reference.md#policy-templates) dla pełnej listy. 

Szablon można dostosować, modyfikując dowolne z istniejących reguł lub dodając nowe. Możesz na przykład dodać nowe typy poufnych informacji do reguły, zmodyfikować liczby w regule, aby utrudnić lub ułatwić wyzwalanie, umożliwić użytkownikom zastąpienie akcji w regule przez podanie uzasadnienia biznesowego lub zmianę sposobu wysyłania powiadomień i raportów o zdarzeniach. Szablon zasad DLP jest elastycznym punktem wyjścia dla wielu typowych scenariuszy zgodności.

Możesz również wybrać szablon niestandardowy, który nie ma reguł domyślnych, i skonfigurować zasady DLP od podstaw, aby spełnić określone wymagania dotyczące zgodności dla organizacji.

## <a name="permissions"></a>Uprawnienia

Członkowie zespołu ds. zgodności, którzy będą tworzyć zasady DLP, potrzebują uprawnień do Centrum zgodności. Domyślnie administrator dzierżawy będzie miał dostęp, aby zapewnić dostęp funkcjonariuszom ds. zgodności i innym osobom. Wykonaj następujące czynności:
  
1. Utwórz grupę na platformie Microsoft 365 i dodaj do niej funkcjonariuszy ds. zgodności.
    
2. Utwórz grupę ról na stronie **Uprawnienia** portal zgodności Microsoft Purview. 

3. Podczas tworzenia grupy ról użyj sekcji **Wybierz role** , aby dodać następującą rolę do grupy ról: **Zarządzanie zgodnością DLP**.
    
4. Użyj sekcji **Wybieranie członków** , aby dodać utworzoną wcześniej grupę platformy Microsoft 365 do grupy ról.

Użyj roli **Zarządzanie zgodnością DLP tylko do wyświetlania** , aby utworzyć grupę ról z uprawnieniami tylko do wyświetlania do zasad DLP i raportów DLP.

Aby uzyskać więcej informacji, zobacz [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md).
  
Te uprawnienia są wymagane do utworzenia i zastosowania zasad DLP, aby nie wymuszać zasad.

### <a name="roles-and-role-groups-in-preview"></a>Role i grupy ról w wersji zapoznawczej

W wersji zapoznawczej dostępne są role i grupy ról, które można przetestować, aby dostosować mechanizmy kontroli dostępu.

Oto lista odpowiednich ról. Aby dowiedzieć się więcej na ich temat, zobacz [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md)

- Information Protection Administracja
- analityk Information Protection
- badacz Information Protection
- czytelnik Information Protection

Oto lista odpowiednich grup ról. Aby dowiedzieć się więcej na ten temat, zobacz [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md)

- Information Protection
- administratorzy Information Protection
- analitycy Information Protection
- Information Protection śledczy
- czytniki Information Protection

### <a name="create-the-dlp-policy-from-a-template"></a>Tworzenie zasad DLP na podstawie szablonu

1. Zaloguj się do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portal zgodności Microsoft Purview</a>.

2. W portal zgodności Microsoft Purview \> lewej nawigacji \> Rozwiązania **Zasady** \> **zapobiegania** \> **utracie** \> danych **+ Tworzenie zasad**.

3. Wybierz szablon zasad DLP, który chroni typy poufnych informacji, których potrzebujesz \> **Dalej**.

4. Nadaj zasadom \> nazwę **Dalej**.
 
<!--In this example, you'll select **Privacy** \> **U.S. Personally Identifiable Information (PII) Data** because it already includes most of the types of sensitive information that you want to protect - you'll add a couple later.

    When you select a template, you can read the description on the right to learn what types of sensitive information the template protects.

    ![Page for choosing a DLP policy template.](../media/775266f6-ad87-4080-8d7c-97f2e7403b30.png)-->

5. Aby wybrać lokalizacje, które mają być chronione przez zasady DLP, i zaakceptować zakres domyślny dla każdej lokalizacji lub dostosować zakres. Zobacz [Lokalizacje](dlp-policy-reference.md#locations) dla opcji określania zakresu.

6. Wybierz przycisk \> **Dalej**.
 
1. Wykonaj jeden z następujących kroków:

   - Wybierz pozycję **Wszystkie lokalizacje w Office 365** \> **Dalej**.
   - Wybierz **pozycję Pozwól mi wybrać określone lokalizacje** \> **Dalej**. W tym przykładzie wybierz tę opcję.

   Aby dołączyć lub wykluczyć całą lokalizację, taką jak wszystkie konta poczty e-mail programu Exchange lub wszystkie konta usługi OneDrive, włącz lub wyłącz **stan** tej lokalizacji.

   Aby uwzględnić tylko określone witryny programu SharePoint lub konta OneDrive dla Firm, przełącz pozycję **Stan** na włączone, a następnie kliknij linki w obszarze **Dołącz**, aby wybrać określone witryny lub konta. Po zastosowaniu zasad do lokacji reguły skonfigurowane w tych zasadach są automatycznie stosowane do wszystkich podwitryn tej witryny.

   ![Opcje lokalizacji, w których można zastosować zasady DLP.](../media/all-locations.png)

   W tym przykładzie, aby chronić poufne informacje przechowywane na wszystkich kontach OneDrive dla Firm, wyłącz **stan** zarówno dla poczty **e-mail programu Exchange**, jak i **witryn programu SharePoint**, a następnie pozostaw **stan** włączony dla **kont usługi OneDrive**.

7. Wybierz **pozycję Przejrzyj i dostosuj ustawienia domyślne z szablonu** \> **Dalej**.

8. Szablon zasad DLP zawiera wstępnie zdefiniowane reguły z warunkami i akcjami, które wykrywają określone typy informacji poufnych i działają na nich. Możesz edytować, usuwać lub wyłączać dowolne z istniejących reguł lub dodawać nowe. Po zakończeniu kliknij przycisk **Dalej**.

    ![Reguły rozwinięte w szablonie zasad interfejsu UŻYTKOWNIKA w Stanach Zjednoczonych.](../media/3bc9f1b6-f8ad-4334-863a-24448bb87687.png)

9. Wybierz, aby wykryć, kiedy ta zawartość jest współużytkowana w organizacji lub poza nią, jeśli wybrano dowolną z następujących lokalizacji:
    1. Exchange
    1. SharePoint
    1. OneDrive
    1. Wiadomości na czacie i kanale w usłudze Teams 

10. Wybierz przycisk **Dalej**.

11. Jeśli chcesz, na stronie **Akcje ochrony** możesz dostosować powiadomienia o poradach dotyczących zasad i wiadomości e-mail z powiadomieniami. Włącz opcję **Gdy zawartość jest zgodna z warunkami zasad, pokaż użytkownikom wskazówki dotyczące zasad i wyślij im powiadomienie e-mail**, a następnie wybierz pozycję **Dostosuj poradę i wiadomość e-mail**.
12. Wybierz przycisk **Dalej**.


<!--    In this example, the U.S. PII Data template includes two predefined rules:

   - **Low volume of content detected U.S. PII** This rule looks for files containing between 1 and 10 occurrences of each of three types of sensitive information (ITIN, SSN, and U.S. passport numbers), where the files are shared with people outside the organization. If found, the rule sends an email notification to the primary site collection administrator, document owner, and person who last modified the document.

   - **High volume of content detected U.S. PII** This rule looks for files containing 10 or more occurrences of each of the same three sensitive information types, where the files are shared with people outside the organization. If found, this action also sends an email notification, plus it restricts access to the file. For content in a OneDrive for Business account, this means that permissions for the document are restricted for everyone except the primary site collection administrator, document owner, and person who last modified the document.

    To meet your organization's specific requirements, you may want to make the rules easier to trigger, so that a single occurrence of sensitive information is enough to block access for external users. After looking at these rules, you understand that you don't need low and high count rules—you need only a single rule that blocks access if any occurrence of sensitive information is found.

    So you expand the rule named **Low volume of content detected U.S. PII** \> **Delete rule**.

    ![Delete rule button.](../media/bc36f7d2-0fae-4af1-92e8-95ba51077b12.png)

9. Now, in this example, you need to add two sensitive information types (U.S. bank account numbers and U.S. driver's license numbers), allow people to override a rule, and change the count to any occurrence. You can do all of this by editing one rule, so select **High volume of content detected U.S. PII** \> **Edit rule**.

    ![Edit rule button.](../media/eaf54067-4945-4c98-8dd6-fb2c5d6de075.png)

10. To add a sensitive information type, in the **Conditions** section \> **Add or change types**. Then, under **Add or change types** \> choose **Add** \> select **U.S. Bank Account Number** and **U.S. Driver's License Number** \> **Add** \> **Done**.

    ![Option to Add or change types.](../media/c6c3ae86-f7db-40a8-a6e4-db11692024be.png)

    ![Add or change types pane.](../media/fdbb96af-b914-4a6c-a97b-bbd014689965.png)

11. To change the count (the number of instances of sensitive information required to trigger the rule), under **Instance count** \> choose the **min** value for each type \> enter 1. The minimum count cannot be empty. The maximum count can be empty; an empty **max** value convert to **any**.

    When finished, the min count for all of the sensitive information types should be **1** and the max count should be **any**. In other words, any occurrence of this type of sensitive information will satisfy this condition.

    ![Instance counts for sensitive information types.](../media/5c6e08cb-59a9-4558-b54b-d899836d4737.png)

12. For the final customization, you don't want your DLP policies to block people from doing their work when they have a valid business justification or encounter a false positive, so you want the user notification to include options to override the blocking action.

    In the **User notifications** section, you can see that email notifications and policy tips are turned on by default for this rule in the template.

    In the **User overrides** section, you can see that overrides for a business justification are turned on, but overrides to report false positives are not. Choose **Override the rule automatically if they report it as a false positive**.

    ![User notifications section and User overrides section.](../media/62720e7a-a939-4c03-b414-67748f3d64a0.png)

13. At the top of the rule editor, change the name of this rule from the default **High volume of content detected U.S. PII** to **Any content detected with U.S. PII** because it's now triggered by any occurrence of its sensitive information types.

14. At the bottom of the rule editor \> **Save**.

15. Review the conditions and actions for this rule \> **Next**.

    On the right, notice the **Status** switch for the rule. If you turn off an entire policy, all rules contained in the policy are also turned off. However, here you can turn off a specific rule without turning off the entire policy. This can be useful when you need to investigate a rule that is generating a large number of false positives.

16. On the next page, read and understand the following, and then choose whether to turn on the rule or test it out first \> **Next**.

     Before you create your DLP policies, you should consider rolling them out gradually to assess their impact and test their effectiveness before you fully enforce them. For example, you don't want a new DLP policy to unintentionally block access to thousands of documents that people require to get their work done.

    If you're creating DLP policies with a large potential impact, we recommend following this sequence:

17. Start in test mode without Policy Tips and then use the DLP reports to assess the impact. You can use DLP reports to view the number, location, type, and severity of policy matches. Based on the results, you can fine tune the rules as needed. In test mode, DLP policies will not impact the productivity of people working in your organization.

18. Move to Test mode with notifications and Policy Tips so that you can begin to teach users about your compliance policies and prepare them for the rules that are going to be applied. At this stage, you can also ask users to report false positives so that you can further refine the rules.

19. Turn on the policies so that the rules are enforced and the content's protected. Continue to monitor the DLP reports and any incident reports or notifications to make sure that the results are what you intend.

    ![Options for using test mode and turning on policy.](../media/49fafaac-c6cb-41de-99c4-c43c3e380c3a.png)

20. Review your settings for this policy \> choose **Create**.

After you create and turn on a DLP policy, it's deployed to any content sources that it includes, such as SharePoint Online sites or OneDrive for Business accounts, where the policy begins automatically enforcing its rules on that content.


## Example: Identify sensitive information across all OneDrive for Business sites and restrict access for people outside your organization

OneDrive for Business accounts make it easy for people across your organization to collaborate and share documents. But a common concern for compliance officers is that sensitive information stored in OneDrive for Business accounts may be inadvertently shared with people outside your organization. A DLP policy can help mitigate this risk.

In this example, you'll create a DLP policy that identifies U.S. PII data, which includes Individual Taxpayer Identification Numbers (ITIN), Social Security Numbers, and U.S. passport numbers. You'll get started by using a template, and then you'll modify the template to meet your organization's compliance requirements—specifically, you'll:

- Add a couple of types of sensitive information—U.S. bank account numbers and U.S. driver's license numbers—so that the DLP policy protects even more of your sensitive data.

- Make the policy more sensitive, so that a single occurrence of sensitive information is enough to restrict access for external users.

- Allow users to override the actions by providing a business justification or reporting a false positive. This way, your DLP policy won't prevent people in your organization from getting their work done, provided they have a valid business reason for sharing the sensitive information.


## View the status of a DLP policy

At any time, you can view the status of your DLP policies on the **Policy** page in the **Data loss prevention** section of the Microsoft Purview compliance portal. Here you can find important information, such as whether a policy was successfully enabled or disabled, or whether the policy is in test mode.

Here are the different statuses and what they mean.

<br>

****

|Status|Explanation|
|---|---|
|**Turning on...**|The policy is being deployed to the content sources that it includes. The policy is not yet enforced on all sources.|
|**Testing, with notifications**|The policy is in test mode. The actions in a rule are not applied, but policy matches are collected and can be viewed by using the DLP reports. Notifications about policy matches are sent to the specified recipients.|
|**Testing, without notifications**|The policy is in test mode. The actions in a rule are not applied, but policy matches are collected and can be viewed by using the DLP reports. Notifications about policy matches are not sent to the specified recipients.|
|**On**|The policy is active and enforced. The policy was successfully deployed to all its content sources.|
|**Turning off...**|The policy is being removed from the content sources that it includes. The policy may still be active and enforced on some sources. Turning off a policy may take up to 45 minutes.|
|**Off**|The policy is not active and not enforced. The settings for the policy (sources, keywords, duration, etc) are saved.|
|**Deleting...**|The policy is in the process of being deleted. The policy is not active and not enforced. It normally takes an hour for a policy to delete.|
|

## Turn off a DLP policy

You can edit or turn off a DLP policy at any time. Turning off a policy disables all of the rules in the policy.

To edit or turn off a DLP policy, on the **Policy** page \> select the policy \> **Edit policy**.

![Edit policy button.](../media/ce319e92-0519-44fe-9507-45a409eaefe4.png)

In addition, you can turn off each rule individually by editing the policy and then toggling off the **Status** of that rule, as described above.

## More information

- [Learn about data loss prevention](dlp-learn-about-dlp.md)
- [Send notifications and show policy tips for DLP policies](use-notifications-and-policy-tips.md)
- [Create a DLP policy to protect documents with FCI or other properties](protect-documents-that-have-fci-or-other-properties.md)
- [What the DLP policy templates include](what-the-dlp-policy-templates-include.md)
- [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md)
