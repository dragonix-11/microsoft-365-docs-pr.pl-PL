---
title: Wprowadzenie do DLP dla usługi Power BI
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
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Przygotowywanie i wdrażanie DLP w lokalizacjach usługi PowerBI.
ms.openlocfilehash: e94ab7bce1fefc7ab370425a269f6e304aee165f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641852"
---
# <a name="get-started-with-data-loss-prevention-policies-for-power-bi-preview"></a>Wprowadzenie do zasad ochrony przed utratą danych dla Power BI (wersja zapoznawcza)

Aby ułatwić organizacjom wykrywanie i ochronę poufnych danych, [zasady ochrony przed utratą danych (DLP) w usłudze Microsoft Purview obsługują](/microsoft-365/compliance/dlp-learn-about-dlp) usługę Power BI. Gdy zestaw danych usługi PowerBI spełnia kryteria zasad DLP, można wyzwolić alert wyjaśniający charakter poufnej zawartości. Ten alert jest również zarejestrowany na karcie **Alerty** dotyczące ochrony przed utratą danych w portalu zgodności firmy Microsoft na potrzeby monitorowania i zarządzania przez administratorów. Ponadto alerty e-mail mogą być wysyłane do administratorów i określonych użytkowników.

## <a name="considerations-and-limitations"></a>Zagadnienia i ograniczenia

- Zasady DLP mają zastosowanie do obszarów roboczych. Obsługiwane są tylko obszary robocze hostowane w pojemnościach Premium Gen2. Aby uzyskać więcej informacji, zobacz [Co to jest Power BI Premium Gen2?](/power-bi/enterprise/service-premium-gen2-what-is).
- Obciążenia ewaluacji zestawu danych DLP mają wpływ na pojemność. Pomiary obciążeń oceny DLP nie są obsługiwane.
- Obsługiwane są zarówno obszary robocze klasyczne, jak i nowe środowisko, o ile są hostowane w pojemnościach Premium Gen2.
- Musisz utworzyć niestandardowe zasady niestandardowe DLP dla usługi Power BI. Szablony DLP nie są obsługiwane.
- Zasady DLP stosowane do lokalizacji DLP obsługują etykiety poufności i typy informacji poufnych jako warunki. 
- Zasady DLP dla usługi Power BI nie są obsługiwane w przypadku przykładowych zestawów danych, [zestawów danych przesyłania strumieniowego](/power-bi/connect-data/service-real-time-streaming) ani zestawów danych łączących się ze źródłem danych za pośrednictwem [trybu DirectQuery](/power-bi/connect-data/desktop-use-directquery) lub [połączenia na żywo](/power-bi/connect-data/desktop-directquery-about#live-connections).
- Zasady DLP dla usługi Power BI nie są obsługiwane w suwerennych chmurach.

## <a name="licensing-and-permissions"></a>Licencjonowanie i uprawnienia

### <a name="skusubscriptions-licensing"></a>Licencjonowanie jednostek SKU/subskrypcji

Przed rozpoczęciem pracy z usługą DLP dla usługi Power BI należy potwierdzić [subskrypcję platformy Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1). Aby uzyskać pełne wskazówki dotyczące licencjonowania, zobacz [Wskazówki dotyczące zabezpieczeń & zgodności z usługą Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

### <a name="permissions"></a>Uprawnienia

Dane z usługi DLP dla usługi Power BI można wyświetlić w [Eksploratorze działań](/microsoft-365/compliance/data-classification-activity-explorer). Istnieją cztery role, które udzielają uprawnień do Eksploratora działań; konto używane do uzyskiwania dostępu do danych musi być członkiem dowolnego z nich.

- Administrator globalny
- Administrator zgodności
- Administrator zabezpieczeń
- Administrator danych zgodności

## <a name="how-dlp-policies-for-power-bi-work"></a>Jak działają zasady DLP dla usługi Power BI

Zasady DLP można zdefiniować w sekcji zapobiegania utracie danych w portalu zgodności. Zobacz [Projektowanie zasad ochrony przed utratą danych](dlp-policy-design.md#design-a-data-loss-prevention-policy). W zasadach określasz etykiety poufności, które chcesz wykryć. Należy również określić akcje, które będą wykonywane, gdy zasady wykryje zestaw danych, który ma zastosowaną określoną etykietę poufności. Zasady DLP obsługują dwie akcje usługi Power BI:

- Powiadomienie użytkownika za pośrednictwem wskazówek dotyczących zasad.
- Alerty. Alerty mogą być wysyłane pocztą e-mail do administratorów i użytkowników. Ponadto administratorzy mogą monitorować alerty i zarządzać nimi na karcie **Alerty** w Centrum zgodności. 

Gdy zestaw danych jest oceniany przez DLP i odpowiada warunkom w zasadach DLP, zostaną zastosowane akcje zdefiniowane w zasadach. Zestaw danych jest oceniany, gdy zestaw danych jest:

- Publikowania
- Ponownie opublikować
- Odświeżanie na żądanie
- Zaplanowane odświeżanie

>[!NOTE]
> Ocena DLP zestawu danych nie występuje, jeśli jedno z następujących elementów ma wartość true:
> - Inicjatorem zdarzenia jest jednostka usługi.
> - Właściciel zestawu danych jest jednostką usługi lub użytkownikiem B2B.

### <a name="what-happens-when-a-dataset-matches-a-dlp-policy"></a>Co się dzieje, gdy zestaw danych jest zgodny z zasadami DLP

Gdy zestaw danych jest zgodny z zasadami DLP:

- Jeśli zasady mają skonfigurowane powiadomienie użytkownika, zostaną one oznaczone w usługa Power BI ikoną osłony, aby wskazać, że są zgodne z zasadami DLP.

    ![Zrzut ekranu przedstawiający znaczek porad dotyczących zasad dla zestawu danych na listach.](../media/dlp-power-bi-policy-tip-on-dataset.png)

    Otwórz stronę szczegółów zestawu danych, aby wyświetlić poradę dotyczącą zasad, która wyjaśnia dopasowanie zasad i sposób obsługi wykrytego typu informacji poufnych.

    ![Zrzut ekranu przedstawiający poradę dotyczącą zasad na stronie szczegółów zestawu danych.](../media/dlp-power-bi-policy-tip-in-dataset-details.png)

    >[!NOTE]
    > Jeśli ukrysz poradę dotyczącą zasad, nie zostanie ona usunięta. Zostanie on wyświetlony przy następnej wizycie na stronie.

- Jeśli alerty są włączone w zasadach, alert zostanie zapisany na karcie **Alerty** dlp w Centrum zgodności i (jeśli zostanie skonfigurowany) wiadomość e-mail zostanie wysłana do administratorów i/lub określonych użytkowników. Na poniższej ilustracji przedstawiono kartę Alerty w sekcji zapobiegania **utracie** danych w portal zgodności Microsoft Purview.

    ![Zrzut ekranu przedstawiający kartę Alerty w centrum zgodności.](../media/dlp-power-bi-alerts-tab.png)

## <a name="configure-a-dlp-policy-for-power-bi"></a>Konfigurowanie zasad DLP dla usługi Power BI

Postępuj zgodnie z procedurami w [temacie Tworzenie, testowanie i dostrajanie zasad DLP](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy) oraz używanie szablonu niestandardowego.

> [!IMPORTANT]
> Po wybraniu lokalizacji dla zasad DLP dla usługi Power BI wybierz tylko lokalizację usługi Power BI. Nie wybieraj żadnych innych lokalizacji, ta konfiguracja nie jest obsługiwana. 

<!--1. Log into the [Microsoft Purview compliance portal](https://compliance.microsoft.com).

1. Choose the **Data loss prevention** solution in the navigation pane, select the **Policies** tab, choose **Create policy**.

    ![Screenshot of D L P create policy page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-create.png)

1. Choose the **Custom** category and then the **Custom policy** template.
    
    >[!NOTE]
    >No other categories or templates are currently supported.

    ![Screenshot of D L P choose custom policy page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-choose-custom.png)
 
    When done, click **Next**.

1. Name the policy and provide a meaningful description.

    ![Screenshot of D L P policy name description section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-name-description.png)
 
    When done, click **Next**.

1. Enable Power BI as a location for the DLP policy. **Disable all other locations**. Currently, DLP policies for Power BI must specify Power BI as the sole location.

    ![Screenshot of D L P choose location page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-choose-location.png)

    By default the policy will apply to all workspaces. Alternatively, you can specify particular workspaces to include in the policy as well as workspaces to exclude from the policy.
    >[!NOTE]
    > DLP actions are supported only for workspaces hosted in Premium Gen2 capacities.

    If you select **Choose workspaces** or **Exclude workspaces**, a dialog will allow you to create a list of included (or excluded) workspaces. You must specify workspaces by workspace object ID. Click the info icon for information about how to find workspace object IDs.

    ![Screenshot of D L P choose workspaces dialog.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-choose-workspaces.png)
 
    After enabling Power BI as a DLP location for the policy and choosing which workspaces the policy will apply to, click **Next**.

1. The **Define policy settings** page appears. Choose **Create or customize advanced DLP rules** to begin defining your policy.

    ![Screenshot of D L P create advanced rule page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-create-advanced-rule.png)
 
    When done, click **Next**.

1. On the **Customize advanced DLP rules** page, you can either start creating a new rule or choose an existing rule to edit. Click **Create rule**.

    ![Screenshot of D L P create rule page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-create-rule.png)


1. The **Create rule** page appears. On the create rule page, provide a name and description for the rule, and then configure the other sections, which are described following the image below.

    ![Screenshot of D L P create rule form.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-create-rule-form.png)
 
### Conditions

In the condition section, you define the conditions under which the policy will apply to a dataset. Conditions are created in groups. Groups make it possible to construct complex conditions.

1. Open the conditions section, choose **Add condition** and then **Content contains**.

    ![Screenshot of D L P add conditions content contains section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-add-conditions-content-contains.png)
 
    This opens the first group (named Default – you can change this).

1. Choose **Add**, and then **Sensitivity labels**.
        
    >[!NOTE]
    > Sensitive info types are currently not supported.
    
    ![Screenshot of D L P add conditions section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-add-conditions.png)
 
    When you choose **Sensitivity labels**, you will be able to choose a particular sensitivity label from a list that will appear.

    You can add additional sensitivity labels to the group. To the right of the group name, you can specify **Any of these** or **All of these**. This determines whether matches on all or any of the labels is required for the condition to hold. Make sure **Any of these** is selected, since datasets can’t have more than one label applied.

    The image below shows a group (Default) that contains two sensitivity label conditions. The logic Any of these means that a match on any one of the sensitivity labels in the group constitutes “true” for that group.

    ![Screenshot of D L P conditions group section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-condition-group.png) 
 
    You can create more than one group, and you can control the logic between the groups with **AND** or **OR** logic. 

    The image below shows a rule containing two groups, joined by **OR** logic.

    ![Screenshot of rule with two groups.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-content-contains.png) 
 
### Exceptions

If the sensitivity label of the dataset matches any of the defined exceptions, the rule won’t be applied to the dataset. 

Exceptions are configured in the same way as conditions, described above.
    
![Screenshot of D L P exceptions section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-exceptions-section.png)
 
### Actions

Protection actions are currently unavailable for Power BI DLP policies.

![Screenshot of D L P policy actions section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-actions-section.png)


### User notifications

The user notifications section is where you configure your policy tip. Turn on the toggle, select the **Notify users in Office 365 service with a policy tip** and **Policy tips** checkboxes, and write your policy tip in the text box.

![Screenshot of D L P user notification section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-user-notification.png)
 
### User overrides
 
User overrides are currently unavailable for Power BI DLP policies.

![Screenshot of D L P user overrides section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-user-overrides-section.png) 
 
### Incident reports

Assign a severity level that will be shown in alerts generated from this policy. Enable (default) or disable email notification to admins, specify users or groups for email notification, and configure the details about when notification will occur.

![Screenshot of D L P incident report section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-incidence-report.png)
   
### Additional options

![Screenshot of D L P additional options section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-additional-options.png)
 
## Monitor and manage policy alerts

Log into the Microsoft Purview compliance portal and navigate to **Data loss prevention > Alerts**.

![Screenshot of D L P Alerts tab.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-alerts-tab.png)

Click on an alert to start drilling down to its details and to see management options.
-->
## <a name="next-steps"></a>Następne kroki

- [Dowiedz się więcej o ochronie przed utratą danych](/microsoft-365/compliance/dlp-learn-about-dlp)
- [Etykiety poufności w usłudze Power BI](/power-bi/enterprise/service-security-sensitivity-label-overview)
- [Schemat inspekcji etykiet poufności w usłudze Power BI](/power-bi/enterprise/service-security-sensitivity-label-audit-schema)
