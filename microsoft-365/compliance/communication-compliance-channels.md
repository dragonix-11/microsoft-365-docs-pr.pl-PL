---
title: Wykrywaj sygnały kanału ze zgodnością w komunikacji
description: Dowiedz się więcej o wykrywaniu sygnałów kanału ze zgodnością komunikacji.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 35bd11ac88859c3e587771552a02097a2f090a44
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2022
ms.locfileid: "63712889"
---
# <a name="detect-channel-signals-with-communication-compliance"></a>Wykrywaj sygnały kanału ze zgodnością w komunikacji

Za pomocą zasad zgodności komunikacji możesz skanować wiadomości na co najmniej jednej z poniższych platform komunikacyjnych jako grupę lub jako autonomiczne źródła. Oryginalne wiadomości przechwycone na tych platformach są zachowywane w pierwotnej lokalizacji platformy zgodnie z zasadami przechowywania i przechowywania [w organizacji](/microsoft-365/compliance/information-governance). Kopie wiadomości używanych przez zasady zgodności komunikacji podczas analizy i analizy są zachowywane przez okres przechowywania zasad, nawet jeśli użytkownicy opuszczają organizację i ich skrzynki pocztowe są usuwane. Usunięcie zasad komunikacji również wiąże się z usunięciem kopii wiadomości skojarzonych z zasadami.

## <a name="microsoft-teams"></a>Microsoft Teams

Komunikację na czacie zarówno w publicznych, Microsoft Teams prywatnych, jak i na poszczególnych czatach można skanować. Gdy użytkownikom przypisano zasady zgodności komunikacji z wybranym zakresem Microsoft Teams, komunikacja na czacie jest automatycznie monitorowana na wszystkich platformach Microsoft Teams których są ich członkami. Microsoft Teams jest automatycznie uwzględniane dla wstępnie zdefiniowanych szablonów zasad i jest domyślnie wybrane w szablonie zasad niestandardowych. Teams czatów spełniających warunki zasad zgodności komunikacji może potrwać do 48 godzin.

W przypadku czatu prywatnego i kanałów prywatnych zasady zgodności komunikacji obsługują [udostępnione kanały](/MicrosoftTeams/shared-channels) i nowoczesne skanowanie załączników. Kanały udostępnione obsługiwane w Teams są obsługiwane automatycznie i nie wymagają dodatkowych zmian w konfiguracji zgodności komunikacji. W poniższej tabeli podsumowano zachowanie zgodności komunikacji podczas Teams kanałów komunikacji z grupami i użytkownikami:

|**Scenariusz**|**Zachowanie zgodności komunikacji**|
|:-----------|:------------------------------------|
| **Udostępnianie kanału zespołowi wewnętrzneowi** | Zasady zgodności komunikacji dotyczą użytkowników w zakresie oraz wszystkich wiadomości w kanale udostępnionym |
| **Udostępnianie kanału zespołowi zewnętrzneowi** | Zasady zgodności komunikacji dotyczą wewnętrznych użytkowników i wiadomości w kanale udostępnionym organizacji wewnętrznej. |

Nowoczesne załączniki to pliki ze źródeł [OneDrive](/onedrive/plan-onedrive-enterprise#modern-attachments) lub [SharePoint](/sharepoint/dev/solution-guidance/modern-experience-customizations), które są zawarte w Teams wiadomościach. Tekst jest automatycznie wyodrębniony z tych załączników w celu automatycznego przetwarzania i potencjalnego dopasowania do warunków aktywnych zasad zgodności komunikacji i klasyfikatorów. Nowoczesne wykrywanie i przetwarzanie załączników nie wymaga żadnej dodatkowej konfiguracji. Tekst jest wyodrębniony tylko dla załączników spełniających warunki zasad. W przypadku wiadomości z dopasowaniami zasad tekst nie jest wyodrębniony dla załączników, nawet jeśli załącznik ma również zgodne zasady.

Nowoczesne skanowanie załączników jest obsługiwane w przypadku następujących typów plików:

- Microsoft Word (.docx)
- Microsoft Excel (.xlsx)
- Microsoft PowerPoint (.pptx)
- Tekst (.txt)
- Portable Document Format (.pdf)

Wyodrębniony tekst dla nowoczesnych załączników jest dołączony do skojarzonej wiadomości na  pulpicie nawigacyjnym Alerty oczekujące dla zasad. Wyodrębniony tekst załącznika ma nazwę jako nazwa pliku załącznika (i rozszerzenie formatu) oraz rozszerzenie .txt załącznika. Na przykład wyodrębniony tekst załącznika o *nazwieContosoBusinessPlan.docx* będzie wyświetlany jakoContosoBusinessPlan.docx.txtna pulpicie nawigacyjnym ** Alerty oczekujące dla zasad.

Zaznacz wyodrębniony tekst załącznika, aby wyświetlić szczegółowe informacje w *widokach Źródło* i *Zwykły tekst* . Po przejrzeniu możesz rozpoznać tekst załącznika lub podjąć w związku z tym akcję za pomocą kontrolek paska poleceń. Możesz również pobrać załącznik w celu przejrzenia poza procesem sprawdzania zgodności komunikacji.

Nadzór nad poszczególnymi czatami użytkowników i komunikacją na kanałach w sieciach za pomocą następujących konfiguracji zarządzania Teams:

- **Aby Teams na czacie:** Przypisz poszczególnych użytkowników lub przypisz grupę [dystrybucyjną](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) do zasad zgodności komunikacji. To ustawienie jest dla relacji jeden-do-jednego lub jeden-do-wielu z innymi użytkownikami/czatami.
- **Na Teams komunikacji w kanale:** Przypisz do każdego kanału Microsoft Teams lub grupy Microsoft 365, którą chcesz przeskanować, zawierającej określonego użytkownika, do zasad zgodności komunikacji. Jeśli dodasz tego samego użytkownika do innych kanałów Microsoft Teams lub grup Microsoft 365, dodaj te nowe kanały i grupy do zasad zgodności komunikacji. Jeśli którykolwiek członek kanału jest nadzorowany przez zasady i kierunek ruchu przychodzącego  jest skonfigurowany w zasadach, wszystkie wiadomości wysłane w ramach kanału podlegają przeglądowi i potencjalnym dopasowaniam zasad (nawet w przypadku użytkowników w kanale, którzy nie są jawnie nadzorowane). Na przykład użytkownik A jest właścicielem lub członkiem kanału. Użytkownicy B i User C są członkami tego samego kanału i używają języka zgodnego z nieodpowiednimi zasadami zawartości, które nadzorują tylko użytkownika A. Użytkownicy B i User C tworzą dopasowania zasad dla konwersacji w kanale, mimo że nie są one bezpośrednio nadzorowane przy użyciu nieodpowiednich zasad zawartości. Teams między użytkownikiem B a użytkownikiem C, które znajdują się poza kanałem, w którym znajduje się użytkownik A, nie będą podlegały nieodpowiednim zasadom zawartości, które obejmują użytkownika A. Aby wykluczyć członków kanału z nadzorów, gdy inni członkowie kanału są jawnie nadzorowane, wyłącz ustawienie kierunku komunikacji przychodzącej w obowiązujących zasadach zgodności komunikacji.
- **W Teams** komunikacji za pomocą czatu z hybrydowymi środowiskami poczty e-mail: Zgodność komunikacji może monitorować wiadomości czatu dla użytkowników w organizacjach, które mają wdrożenie lokalne programu Exchange lub zewnętrznego dostawcę poczty e-mail, który włączył Microsoft Teams. Należy utworzyć grupę dystrybucyjną dla użytkowników, którzy mają lokalne lub zewnętrzne skrzynki pocztowe do monitorowania. Podczas tworzenia zasad zgodności komunikacji ta grupa dystrybucyjna zostanie przypisana jako wybór Nadzór nad  użytkownikami i grupami w kreatorze zasad. Aby uzyskać więcej informacji o wymaganiach i ograniczeniach dotyczących włączania magazynu opartego na chmurze i obsługi Teams użytkowników lokalnych, zobacz Wyszukiwanie danych czatu Teams użytkowników [lokalnych](search-cloud-based-mailboxes-for-on-premises-users.md).

## <a name="exchange-email"></a>Exchange-mail

Skrzynki pocztowe hostowane Exchange Online w ramach Twojej subskrypcji usługi Microsoft 365 lub Office 365 można skanować wiadomości. Exchange e-mail i załączniki spełniające warunki zasad zgodności komunikacji mogą potrwać do 24 godzin. Obsługiwane typy załączników w celu zapewnienia zgodności komunikacji są takie same jak typy plików obsługiwane w przypadku Exchange inspekcji [zawartości reguły przepływu poczty e-mail](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection).

## <a name="yammer"></a>Yammer

Wiadomości prywatne, konwersacje publiczne i skojarzone załączniki w Yammer można skanować. Po dodaniu użytkownika do zasad zgodności komunikacji, które obejmują Yammer jako kanał zdefiniowany, w procesie skanowania jest uwzględniana komunikacja ze wszystkich społeczności Yammer, których jest członkiem. Yammer czatów i załączników spełniających warunki zasad zgodności komunikacji może potrwać do 24 godzin. 

Yammer być w trybie [natywnym](/yammer/configure-your-yammer-network/overview-native-mode), aby zasady zgodności komunikacji Yammer komunikacji i załączników. W trybie natywnym Yammer są w trybie Azure Active Directory (AAD), wszystkie grupy są Office 365 grupy, a wszystkie pliki są przechowywane w u SharePoint Online.

## <a name="skype-for-business-online"></a>Skype dla firm Online

Wiadomości na czacie i skojarzone z nimi załączniki w aplikacji Skype dla firm Online mogą być nadzorowane. Skype dla firm czatów online spełniających warunki zasad zgodności komunikacji może potrwać do 24 godzin. Nadzorowane konwersacje na czacie pochodzą z [poprzednich konwersacji zapisanych w u Skype dla firm Online](https://support.office.com/article/Find-a-previous-Skype-for-Business-conversation-18892eba-5f18-4281-8c87-fd48bd72e6a2).  

Należy korzystać z następującej konfiguracji zarządzania grupą w celu nadzór nad komunikacją za pomocą czatu użytkownika w u Skype dla firm Online:

- **Na Skype dla firm komunikacji za pośrednictwem czatu online**: Przypisz poszczególnych użytkowników lub przypisz grupę [dystrybucyjną](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) do zasad zgodności komunikacji. To ustawienie jest dla relacji jeden-do-jednego lub jeden-do-wielu z innymi użytkownikami/czatami.

## <a name="third-party-sources"></a>Źródła innych firm

Możesz skanować komunikację w poszukiwaniu danych zaimportowanych do skrzynek pocztowych w Twojej organizacji Microsoft 365 z innych źródeł, takich jak [Instant Bloomberg](archive-instant-bloomberg-data.md), [Slack](archive-slack-data.md), [Zoom](archive-zoommeetings-data.md), SMS i wiele innych. Aby uzyskać pełną listę łączników obsługiwanych w zakresie zgodności komunikacji, zobacz Archiwizowanie [danych innych firm](archiving-third-party-data.md).

Musisz skonfigurować łącznik innej firmy dla swojej organizacji Microsoft 365, aby można było przypisać łącznik do zasad zgodności komunikacji. Sekcja **Źródła innych firm** w kreatorze zasad zgodności komunikacji zawiera tylko obecnie skonfigurowane łączniki innych firm.
