---
title: Projektowanie zasad ochrony przed utratą danych
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Dowiedz się, jak zaprojektować zasady ochrony przed utratą danych (DLP, Data Loss Prevention)
ms.openlocfilehash: 5cfea5add3a1790e8a30359e48ca1c94ca83f671
ms.sourcegitcommit: b6ab10ba95e4b986065c51179ead3810cc1e2a85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017849"
---
# <a name="design-a-data-loss-prevention-policy"></a>Projektowanie zasad ochrony przed utratą danych

Utworzenie zasad przed wdrożeniem pozwoli uzyskać odpowiednie wyniki szybciej i z mniejszą liczbą niezamierzonych problemów niż tworzenie i następnie dostosowywanie tylko według wersji próbnej i błędów. Dokumentowanie projektów zasad pomoże również w komunikacji, przeglądaniu zasad, rozwiązywaniu problemów i dalszym dostosowywaniu.

<!--, but excessive tuning to get the intended results can be time consuming.

 if you have to do a lot of tuning to get a policy to yield the intended results can be time consuming .-->

Jeśli nie masz wiedzy Microsoft 365 zasad DLP, warto przejść do tych artykułów przed rozpoczęciem projektowania zasad:

- [Informacje na temat ochrony przed utratą](dlp-learn-about-dlp.md#learn-about-data-loss-prevention) danych — ten artykuł zawiera wprowadzenie do dyscypliny ochrony przed utratą danych i wdrożenia ochrony przed utratą danych przez firmę Microsoft
- [Planowanie ochrony przed utratą danych (DLP, data loss prevention)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp) — pracując w tym artykule, możesz:
    - [Identyfikowanie uczestników projektu](dlp-overview-plan-for-dlp.md#identify-stakeholders)
    - [Opis kategorii informacji poufnych, które mają być chronine](dlp-overview-plan-for-dlp.md#describe-the-categories-of-sensitive-information-to-protect)
    - [Ustawianie celów i strategii](dlp-overview-plan-for-dlp.md#set-goals-and-strategy)
- [Informacje dotyczące zasad ochrony](dlp-policy-reference.md#data-loss-prevention-policy-reference) przed utratą danych — w tym artykule opisano wszystkie składniki zasad DLP oraz wpływ każdej z nich na ich zachowanie

## <a name="policy-design-overview"></a>Omówienie projektowania zasad

[Zaprojektowanie zasad](#policy-design-process) ma na celu przede wszystkim jasne zdefiniowanie potrzeb biznesowych, dokumentowanie ich w deklaracji celów zasad, [a](#define-intent-for-the-policy) następnie mapowanie tych potrzeb [na konfigurację zasad](#map-business-needs-to-policy-configuration). Niektóre z decyzji dotyczących projektu zasad będą podejmowane na etapie planowania. 

### <a name="define-intent-for-the-policy"></a>Definiowanie intencji zasad 

Powinno być możliwe podsumowanie celów biznesowych dla każdej zasady w jednej instrukcji. Opracowanie tej instrukcji będzie prowadzić konwersacje w organizacji, a gdy zostanie całkowicie uregulowana, ta instrukcja bezpośrednio łączy zasady z celem biznesowym i zawiera przewodnik dotyczący projektowania zasad. Czynności opisane w artykule Planowanie na rzecz ochrony przed [utratą danych (DLP)](dlp-overview-plan-for-dlp.md#overview-of-planning-process) pomogą Ci w rozpoczynaniu pracy nad oświadczeniem o przeznacie zasad.  

Pamiętaj w [przeglądzie konfiguracji zasad DLP,](dlp-learn-about-dlp.md#dlp-policy-configuration-overview) że wszystkie zasady DLP wymagają:

- Wybierz, co chcesz monitorować
- Wybierz, gdzie chcesz monitorować
- Wybieranie warunków, które muszą być zgodne z zasadami, które mają zostać zastosowane do elementu
- Wybieranie akcji do podjęcia po spełnionej warunki zasad 

Oto przykład fikcyjnej pierwszej wersji roboczej deklaracji dotyczącej intencji, która zawiera odpowiedzi na wszystkie cztery pytania: 

*"Jesteśmy organizacją w Stanach Zjednoczonych i musimy wykrywać dokumenty firmy Office zawierające informacje poufnej opieki zdrowotnej objęte ustawą HIPPA, które są przechowywane w programie OneDrive/SharePoint, i chronić się przed udostępnianiem tych informacji w wiadomościach na czacie i w kanałach firmy Teams oraz uniemożliwić wszystkim użytkownikom udostępnianie ich nieautoryzowanym osobom trzecim".* 

Podczas opracowywania projektu zasad prawdopodobnie zmodyfikuje się i rozszerzy instrukcja.

### <a name="map-business-needs-to-policy-configuration"></a>Mapowanie firmy na potrzeby konfiguracji zasad

Rozbijmy przykładową instrukcje roboczą i zamapujmy ją na punkty konfiguracji zasad DLP.

|Instrukcja  |Odpowiedź na pytanie dotyczące konfiguracji i mapowanie konfiguracji  |
|---------|---------|
| "Jesteśmy organizacją w Stanach Zjednoczonych i musimy wykrywać dokumenty Office, które zawierają informacje poufnej opieki zdrowotnej objęte ustawą HIPPA...  |- **Co należy monitorować**: Office, użyj szablonu [USTAWY HIPAA (Health Insurance Act)](what-the-dlp-policy-templates-include.md#us-health-insurance-act-hipaa) Stanów Zjednoczonych </br>- Warunki **dopasowania: (** wstępnie skonfigurowane, ale edytowalne) — element zawiera numer Amerykańskiej Federacji Amerykańskiej i Agencji Wymuszania Dokumentów (DEA), klasyfikację międzynarodowa klasyfikacji jeśli jednakowy (ICD-9-CM), klasyfikację międzynarodowa procentów od osób (ICD-10-CM), a zawartość jest udostępniana osobom spoza mojej organizacji  </br> — dyskuje konwersacje w celu objaśniania progu wyzwalania [wykrywania, takiego](sensitive-information-type-learn-about.md#more-on-confidence-levels) jak poziomy ufności [, i liczby](dlp-policy-reference.md#content-contains) wystąpień (nazywanych wyciekami).|
|... które są przechowywane w czacie OneDrive/SharePoint i chronią przed Teams wiadomościami na czacie i w kanałach... |- **Gdzie monitorować**: [Określanie](dlp-policy-reference.md#locations) zakresu lokalizacji przez OneDrive i SharePoint czatów i Teams lub grup dystrybucyjnych. |
|... i uniemożliwić wszystkim użytkownikom udostępnianie tych elementów nieautoryzowanym osobom trzecim".  | - **Akcje do podjęcia**: [Należy dodać pozycję](dlp-policy-reference.md#actions) *Ogranicz dostęp lub zaszyfrować zawartość w Microsoft 365 lokalizacjach* </br> - dyskutuje o tym, jakie działania należy podjąć po wyzwoleniu zasady, w tym działania zabezpieczające, takie jak ograniczenia udostępniania, akcje informacyjne, takie jak powiadomienia i alerty, oraz akcje uprawnienia użytkownika, takie jak zezwalanie na zastępowanie akcji blokowania przez użytkownika |

W tym przykładzie nie obejmuje wszystkich punktów konfiguracji zasad DLP, ale trzeba je rozszerzyć. Jednak podczas opracowywania własnych instrukcje dotyczące zasad DLP powinno być to odpowiednie dla Ciebie.

> [!IMPORTANT]
> Należy pamiętać, że wybierane lokalizacje mają wpływ na to, czy można używać typów informacji poufnych, etykiet wrażliwości i etykiet przechowywania, a także dostępnych akcji. Zobacz Informacje [dotyczące zasad ochrony przed utratą danych](dlp-policy-reference.md#data-loss-prevention-policy-reference).

## <a name="policy-design-process"></a>Proces projektowania zasad

1. Wykonaj następujące czynności:
    1. [Planowanie ochrony przed utratą danych (DLP, data loss prevention)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp) — pracując w tym artykule, możesz:
        1. [Identyfikowanie uczestników projektu](dlp-overview-plan-for-dlp.md#identify-stakeholders)
        1. [Opis kategorii informacji poufnych, które mają być chronine](dlp-overview-plan-for-dlp.md#describe-the-categories-of-sensitive-information-to-protect)
        1. [Ustawianie celów i strategii](dlp-overview-plan-for-dlp.md#set-goals-and-strategy)
        1. [Definiowanie planu wdrażania zasad](dlp-overview-plan-for-dlp.md#policy-deployment)

1. Zapoznaj się z odwołaniami [](dlp-policy-reference.md#data-loss-prevention-policy-reference) do zasad ochrony przed utratą danych, aby zrozumieć wszystkie składniki zasad DLP i sposób, w jaki każda z nich wpływa na ich działanie.

1. Zapoznaj się z [szablonami zasad DLP](what-the-dlp-policy-templates-include.md#what-the-dlp-policy-templates-include).

1. Opracuj oświadczenie o przeznaczyniu zasad z kluczowymi uczestnikami projektu. Skorzystaj z przykładu we wcześniejszej wersji tego artykułu.

1. Określ, jak te zasady są dopasowane do ogólnej strategii zasad DLP.

> [!IMPORTANT]
> Po utworzeniu zasad nie można ich zmienić. Jeśli musisz zmienić nazwę zasad, musisz utworzyć nową o odpowiedniej nazwie i wycofać starą. Zdecyduj więc, jaka struktura nazewnictwa będzie teraz używać wszystkich Twoich zasad. 

6. Zamapuj elementy w instrukcji dotyczącej zasad na opcje konfiguracji.

7. Zdecyduj, od którego szablonu zasad chcesz zacząć, wstępnie zdefiniowanego lub niestandardowego.

8. Przed utworzeniem zasad przejdź przez szablon i zbierz wszystkie wymagane informacje. Prawdopodobnie znajdziesz w nim pewne punkty konfiguracyjne, które nie zostały uwzględnione w twoich zamiarach zasad. Tak jest ok. Wróć do uczestników projektu, aby uściślić wymagania dotyczące brakujących punktów konfiguracji. 

9. Udokumentuj konfigurację wszystkich ustawień zasad i przejrzyj je wraz z uczestnikami projektu. Możesz ponownie użyć mapowania deklaracji deklaracji zasad na punkty konfiguracji, które są obecnie w pełni naładowane.

10. [Utwórz projekt](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy) zasad i wróć do [planu wdrażania](dlp-overview-plan-for-dlp.md#policy-deployment) zasad.

<!--## Policy design examples

|Customer business needs description  | approach  |
|---------|---------|
|**Contoso Bank** is in a highly regulated industry and has  many different types of sensitive items in many different locations. </br> - knows which types of sensitive information are top priority. </br> - must minimize business disruption as policies are rolled out. </br> -  has IT resources and can hire experts to help plan, design deploy </br> - has a premier support contract with Microsoft| - Take the time to understand what regulations they must comply with and how they are going to comply. </br> -Take the time to understand the better together value of the Microsoft 365 Information Protection stack </br> - Develop sensitivity labeling scheme for prioritized items and apply </br> - Involve business process owners </br>- Design/code policies, deploy in test mode, train users </br>- repeat|
|**TailSpin Toys** doesn’t know what they have or where it is, and have little to no resource depth. They use Teams, OneDrive for Business and Exchange extensively.     |- Start with simple policies on the prioritized locations. </br>- Monitor what gets identified </br>- Apply sensitivity labels accordingly </br>- Refine policies, train users       |
|**Fabrikam** is a small startup and wants to protect its intellectual property, and must move quickly. They are willing to dedicate some resources, but can't afford to hire outside experts. </br>- Sensitive items are all in Microsoft 365 OneDrive for Business/SharePoint </br>- Adoption of OneDrive for Business and SharePoint is slow, employees/shadow IT use DropBox and Google drive to share/store items </br>- Employees value speed of work over data protection discipline </br>- Customer splurged and bought all 18 employees new Windows 10 devices     |- Take advantage of the default DLP policy in Teams </br>- Use restricted by default setting for SharePoint items </br>- Deploy policies that prevent external sharing </br>- Deploy policies to prioritized locations </br>- Deploy policies to Windows 10 devices </br>- Block uploads to non-OneDrive for Business cloud storage      |


1. For example:
    1. Identify your volume thresholds that your company deems to be low-risk (leakage tolerance), perhaps from unintentional sharing and is an opportunity to educate users and the threshold that is concerning or high-risk for your company that may need immediate attention.
    - example volume: “Low risk” for Contoso is 1 credit card number, perhaps it was a personal card that was shared carelessly
    - example volume: “High risk” for Contoso is 2 or more credit card numbers. It doesn’t feel like a common scenario that an employee would engage in accidentally



–   For each of the sensitive information types listed out, list out **who should have access to that data when it’s generated** and **what type of activities should be allowable with that data**


  <!--(Perhaps this is where we can provide some basic categories, templates, activities and actions that are supported by Microsoft. Some of these items are not discoverable until you are deeper within a policy creation flow. If we provide, we should time stamp it for “last updated” or “as of xx/xx/xxx”)
–   (Show table with parent-child relationships between categories, templates and sensitive info types that Microsoft supports) Should be gathered from GA Compliance environment-->

<!--


> [!TIP] The more locations you include ensures broader application of the policy and more consistent coverage. If you include locations that are mostly used for internal collaboration, the responsiveness of collaboration may be impacted.


- whether the protective actions you need are supported throught the associated location or if you need to compromise to extend coverage
    - also usefule for identifying the most restrictive actions available 
    - (we shouldn't mention here that the "content contains" condition is the primary staple for a DLP policy and should be utilized as a starting point for policy creation. The other workload-specific conditions can be ustilized as an extended or granular control of company's DLP policy. Useful for when "too much" data is being restricted and known sensitive data typically falls under certain conditions.)
    - (We can mention here that their quantitative goal such as "protect X% of data across all locations while maintaining x productivity" can be monitored throught alerts or reports. If protection is too high of working against their established goals, they can come back to policy and tweak their conditions/actions)
- Finally, you should have a union of what, hwo and when to be covered which will easily map to generating a live policy via Microsoft DLP. 
- 
5. At this stage you should asses how you should start this policy. ***LINK OUT TO DEPLOYING A POLICY COVERED IN THE PLANNING TOPIC TOO***
    - Test: your company is very large, conservative or the actions established are pretty restrictive
    - Test w/ notifications: same as above, but you get to test out investigation cadence or volume
    - Live: immediately start this policy in your environment. Useful for when data protection is needed immediately, such as a reactive policy creation, or if you're confident in your planning, or if the risk is low (liek audit actions, etc.)
    - keep it off:
-->

<!--## Policy Design Examples

Here are some examples of more detailed policy intent statement to configuration mappings.

*We are a national healthcare provider based in the U.S. We need to protect our patient’s personal information and prevent it from egressing outside of our company’s borders. We want to limit access to our patient’s personal information to only authorized personnel, like our physicians and billing department from our on-premises devices. We've determined that any single instance of any of each information type in any item is not a data risk, but it is a risk when two or more occur in a single item. We have a Microsoft 365 E5 subscription and want to protect all locations and first party apps that are available to us because we can’t afford to have any data leaks. If an event occurs or is prevented, we want to alert our compliance admin and educate our end-users where necessary.*

|Statement  |Configuration question answered and configuration mapping  |
|---------|---------|
| We are a national healthcare provider based in the U.S. We need to protect our patient’s personal information...|- **What to monitor**: All available item types, use the [U.S. Health Insurance Act (HIPAA)](what-the-dlp-policy-templates-include.md#us-health-insurance-act-hipaa) template. </br>- **Conditions for a match**: (preconfigured but editable) - item contains full names, physical addresses, driver's license number, U.S. SSN
| ...and prevent it from egressing outside of our company’s borders... |- **Actions to take**: Block anyone outside the organization from accessing items, block unintentional sharing by internal users with anyone outside the org.|
|...We want to limit access to our patient’s personal information to only authorized personnel, like our physicians and billing department from our on-premises devices...| - **Actions to take**: - Block access to items, block all activities (upload to cloud, copy to clipboard, copy to USB, copy to network share, access by restricted app, print, copy/move via Bluetooth, copy/move via remote desktop) from Windows devices.  </br> - **Where to monitor**: in all Microsoft 365 locations
| ...We've determined that any single instance of any of each information type in any item is not a data risk, but it is a risk when two or more occur in a single item....| - **Conditions for a match**: (preconfigured but editable) any single item contains more than one of these or any two or more of these:  Full Name, U.S. Social Security Number, Drug Enforcement Agency (DEA) number, International Classification of Diseases (ICD-9-CM), International Classification of Diseases (ICD-10-CM), Physical Address, U.S. driver's license number. For example, two instanced of Full Name or one instance of a U.S. Social Security Number along with one instance of Drug Enforcement Agency (DEA) number will trigger a match.

   , content is shared with people outside my organization  </br> - drives conversations to clarify the triggering threshold for detection like [confidence levels](sensitive-information-type-learn-about.md#more-on-confidence-levels), and [instance count](dlp-policy-reference.md#content-contains) (called leakage tolerance).|
|...that are stored in OneDrive/SharePoint and protect against that information being shared Teams chat and channel messages... |- **Where to monitor**:  [Location scoping](dlp-policy-reference.md#locations) by including or excluding OneDrive and SharePoint sites and Teams chat/channel accounts or distribution groups. |
|...and restrict everyone from sharing those items with unauthorized third parties."  | - **Actions to take**: [You add](dlp-policy-reference.md#actions) *Restrict access or encrypt the content in Microsoft 365 locations* </br> - drives conversation on what actions to take when a policy is triggered including protective actions like sharing restrictions, awareness actions like notifications and alerts, and user empowerment actions like allow user overrides of a blocking action |

-->


## <a name="see-also"></a>Zobacz też

- [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Planowanie ochrony przed utratą danych (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [Informacje dotyczące zasad ochrony przed utratą danych](dlp-policy-reference.md#data-loss-prevention-policy-reference)
- [Porady dotyczące zasad ochrony przed utratą danych](dlp-policy-tips-reference.md#data-loss-prevention-policy-tips-reference)
- [Tworzenie, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)