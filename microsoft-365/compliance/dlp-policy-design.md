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
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Dowiedz się, jak zaprojektować zasady ochrony przed utratą danych (DLP)
ms.openlocfilehash: af09197784607dd6c8f8d939f4d091b365d51799
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760608"
---
# <a name="design-a-data-loss-prevention-policy"></a>Projektowanie zasad ochrony przed utratą danych

Poświęcenie czasu na zaprojektowanie zasad przed jego zaimplementowaniem spowoduje szybsze uzyskanie żądanych wyników i zmniejszenie liczby niezamierzonych problemów niż utworzenie ich, a następnie dostrajanie tylko przez próbę i błąd. Udokumentowanie projektów zasad pomoże Ci również w komunikacji, przeglądach zasad, rozwiązywaniu problemów i dalszym dostrajaniu.

<!--, but excessive tuning to get the intended results can be time consuming.

 if you have to do a lot of tuning to get a policy to yield the intended results can be time consuming .-->

Jeśli dopiero zaczynasz Microsoft 365 DLP, warto zapoznać się z tymi artykułami przed rozpoczęciem projektowania zasad:

- [Dowiedz się więcej o zapobieganiu utracie danych](dlp-learn-about-dlp.md#learn-about-data-loss-prevention) — w tym artykule przedstawiono dziedzinę zapobiegania utracie danych i implementację DLP firmy Microsoft
- [Planowanie zapobiegania utracie danych (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp) — korzystając z tego artykułu, wykonasz następujące czynności:
  - [Identyfikowanie uczestników projektu](dlp-overview-plan-for-dlp.md#identify-stakeholders)
  - [Opis kategorii informacji poufnych w celu ochrony](dlp-overview-plan-for-dlp.md#describe-the-categories-of-sensitive-information-to-protect)
  - [Ustawianie celów i strategii](dlp-overview-plan-for-dlp.md#set-goals-and-strategy)
- [Dokumentacja zasad ochrony przed utratą danych](dlp-policy-reference.md#data-loss-prevention-policy-reference) — w tym artykule przedstawiono wszystkie składniki zasad DLP i sposób, w jaki każdy z nich wpływa na zachowanie zasad

## <a name="policy-design-overview"></a>Omówienie projektu zasad

[Projektowanie zasad](#policy-design-process) polega głównie na jasnym [zdefiniowaniu potrzeb biznesowych, udokumentowaniu ich w instrukcji intencji zasad,](#define-intent-for-the-policy) a następnie [mapowaniu tych potrzeb na konfigurację zasad](#map-business-needs-to-policy-configuration). Użyjesz decyzji podjętych w fazie planowania, aby poinformować o niektórych decyzjach dotyczących projektowania zasad.

### <a name="define-intent-for-the-policy"></a>Definiowanie intencji dla zasad

Powinno być możliwe podsumowanie intencji biznesowych dla wszystkich zasad w jednej instrukcji. Opracowanie tej instrukcji będzie prowadzić konwersacje w organizacji, a po pełnym wyjaśnieniu ta instrukcja bezpośrednio łączy zasady z celem biznesowym i udostępnia plan projektowania zasad. Kroki opisane w artykule [Planowanie zapobiegania utracie danych (DLP)](dlp-overview-plan-for-dlp.md#overview-of-planning-process) pomogą Ci rozpocząć pracę z instrukcją intencji zasad.

Pamiętaj z [przeglądu konfiguracji zasad DLP](dlp-learn-about-dlp.md#dlp-policy-configuration-overview) , że wszystkie zasady DLP wymagają:

- Wybieranie tego, co chcesz monitorować
- Wybieranie miejsca, które chcesz monitorować
- Wybierz warunki, które muszą być dopasowane, aby zasady miały być stosowane do elementu
- Wybierz akcję do wykonania po spełnieniu warunków zasad

Oto przykładowy fikcyjny pierwszy projekt instrukcji intencji, która zawiera odpowiedzi na wszystkie cztery pytania:

*"Jesteśmy organizacją z siedzibą w USA i musimy wykrywać Office dokumentów zawierających poufne informacje o służbie zdrowia objęte hippa, które są przechowywane w OneDrive/SharePoint i chronić przed informacjami udostępnianymi w Teams wiadomościach czatu i kanału oraz ograniczyć wszystkim możliwość udostępniania ich nieautoryzowanym osobom trzecim".*

Podczas opracowywania projektu zasad prawdopodobnie zmodyfikujesz i rozszerzysz instrukcję.

### <a name="map-business-needs-to-policy-configuration"></a>Mapowanie potrzeb biznesowych na konfigurację zasad

Przeprowadźmy podział przykładowej instrukcji roboczej i zamapujmy ją na punkty konfiguracji zasad DLP.

|Instrukcja  |Udzielono odpowiedzi na pytanie dotyczące konfiguracji i mapowanie konfiguracji  |
|---------|---------|
| "Jesteśmy organizacją z siedzibą w USA i musimy wykryć Office dokumenty zawierające poufne informacje o służbie zdrowia objęte hippa ...  |- **Co monitorować**: Office dokumentacji, użyj szablonu [amerykańskiej ustawy o ubezpieczeniach zdrowotnych (HIPAA)](what-the-dlp-policy-templates-include.md#us-health-insurance-act-hipaa) </br>- **Warunki dopasowania**: (wstępnie skonfigurowane, ale edytowalne) — element zawiera numer US SSN i Drug Enforcement Agency (DEA), Międzynarodową Klasyfikację Chorób (ICD-9-CM), Międzynarodową Klasyfikację Chorób (ICD-10-CM), zawartość jest udostępniana osobom spoza mojej organizacji  </br> — prowadzi konwersacje w celu wyjaśnienia progu wyzwalania wykrywania, takiego jak [poziomy ufności](sensitive-information-type-learn-about.md#more-on-confidence-levels) i [liczba wystąpień](dlp-policy-reference.md#content-contains) (nazywana tolerancją przecieków).|
|... są przechowywane w OneDrive/SharePoint i chronią przed udostępnianiem tych informacji Teams wiadomościach czatu i kanału... |- **Gdzie monitorować**: [określanie zakresu lokalizacji przez uwzględnienie](dlp-policy-reference.md#locations) lub wykluczenie witryn OneDrive i SharePoint oraz Teams kont czatów/kanałów lub grup dystrybucyjnych. |
|... i ograniczyć wszystkim możliwość udostępniania tych elementów nieautoryzowanym osobom trzecim".  | - **Akcje do wykonania**: [dodaj](dlp-policy-reference.md#actions) *pozycję Ogranicz dostęp lub zaszyfruj zawartość w Microsoft 365 lokalizacjach* </br> — prowadzi konwersację na temat działań, które należy wykonać po wyzwoleniu zasad, w tym działań ochronnych, takich jak ograniczenia udostępniania, akcje uświadamiające, takie jak powiadomienia i alerty, oraz akcje upodmiotowienia użytkowników, takie jak zezwalanie na zastępowanie akcji blokującej przez użytkownika |

Ten przykład nie obejmuje wszystkich punktów konfiguracji zasad DLP. Należy go rozszerzyć. Ale powinno to skłonić Cię do myślenia we właściwym kierunku podczas opracowywania własnych instrukcji intencji zasad DLP.

> [!IMPORTANT]
> Należy pamiętać, że wybrane lokalizacje mają wpływ na to, czy można używać typów informacji poufnych, etykiet poufności i etykiet przechowywania, a także dostępnych akcji. Zobacz [Dokumentacja zasad ochrony przed utratą danych](dlp-policy-reference.md#data-loss-prevention-policy-reference).

## <a name="policy-design-process"></a>Proces projektowania zasad

1. Wykonaj kroki opisane w [temacie Plan for data loss prevention (DLP) (Planowanie zapobiegania utracie danych)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp) — korzystając z tego artykułu, wykonasz następujące czynności:
   1. [Identyfikowanie uczestników projektu](dlp-overview-plan-for-dlp.md#identify-stakeholders)
   1. [Opis kategorii informacji poufnych w celu ochrony](dlp-overview-plan-for-dlp.md#describe-the-categories-of-sensitive-information-to-protect)
   1. [Ustawianie celów i strategii](dlp-overview-plan-for-dlp.md#set-goals-and-strategy)
   1. [Definiowanie planu wdrażania zasad](dlp-overview-plan-for-dlp.md#policy-deployment)

2. Zapoznaj się z [dokumentacją zasad ochrony przed utratą danych](dlp-policy-reference.md#data-loss-prevention-policy-reference) , aby poznać wszystkie składniki zasad DLP i sposób, w jaki każdy z nich wpływa na zachowanie zasad.

3. Zapoznaj się z informacjami [o tym, co zawierają szablony zasad DLP](what-the-dlp-policy-templates-include.md#what-the-dlp-policy-templates-include).

4. Opracuj instrukcję intencji zasad z kluczowymi uczestnikami projektu. Zapoznaj się z przykładem we wcześniejszej części tego artykułu.

5. Określ, w jaki sposób te zasady pasują do ogólnej strategii zasad DLP.

   > [!IMPORTANT]
   > Nie można zmienić nazw zasad po ich utworzeniu. Jeśli musisz zmienić nazwę zasad, musisz utworzyć nową z żądaną nazwą i wycofać starą. Dlatego zdecyduj o strukturze nazewnictwa, która będzie teraz używana przez wszystkie zasady.

6. Zamapuj elementy w instrukcji intencji zasad na opcje konfiguracji.

7. Zdecyduj, od którego szablonu zasad zaczniesz, wstępnie zdefiniowany lub niestandardowy.

8. Zapoznaj się z szablonem i zmontuj wszystkie wymagane informacje przed utworzeniem zasad. Prawdopodobnie okaże się, że istnieją pewne punkty konfiguracji, które nie są objęte instrukcją intencji zasad. Tak jest ok. Wstecz do uczestników projektu, aby spełnić wymagania dotyczące brakujących punktów konfiguracji.

9. Udokumentuj konfigurację wszystkich ustawień zasad i przejrzyj je u uczestników projektu. Możesz ponownie użyć mapowania instrukcji intencji zasad na punkty konfiguracji, które są teraz w pełni uzupełnione.

10. [Utwórz wersje robocze](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy) zasad i zapoznaj się z planem [wdrażania zasad](dlp-overview-plan-for-dlp.md#policy-deployment) .

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

- [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Planowanie zapobiegania utracie danych (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [Dokumentacja zasad ochrony przed utratą danych](dlp-policy-reference.md#data-loss-prevention-policy-reference)
- [Dokumentacja dotycząca porad dotyczących zasad ochrony przed utratą danych](dlp-policy-tips-reference.md#data-loss-prevention-policy-tips-reference)
- [Twórz, testuj i dostrajaj zasady DLP](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)