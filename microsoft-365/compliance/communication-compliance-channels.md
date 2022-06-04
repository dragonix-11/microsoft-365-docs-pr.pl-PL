---
title: Wykrywaj sygnały kanału ze zgodnością w komunikacji
description: Dowiedz się więcej o wykrywaniu sygnałów kanałów ze zgodnością z komunikacją.
keywords: Microsoft 365, Microsoft Purview, zgodność, zgodność z komunikacją
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
ms.openlocfilehash: b60337226a12f7395b4a5664b5a11b0d88ed4790
ms.sourcegitcommit: c216ffa5da8f431e4380bb133a234ae7d94144c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2022
ms.locfileid: "65893377"
---
# <a name="detect-channel-signals-with-communication-compliance"></a>Wykrywaj sygnały kanału ze zgodnością w komunikacji

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Dzięki zasadom zgodności komunikacji można skanować komunikaty na co najmniej jednej z następujących platform komunikacyjnych jako grupa lub jako źródła autonomiczne. Oryginalne komunikaty przechwycone na tych platformach są przechowywane w oryginalnej lokalizacji platformy zgodnie z [zasadami przechowywania i przechowywania](/microsoft-365/compliance/information-governance) w organizacji. Kopie komunikatów używanych przez zasady zgodności komunikacji do analizy i badania są przechowywane tak długo, jak długo obowiązują zasady, nawet jeśli użytkownicy opuszczają organizację, a ich skrzynki pocztowe zostaną usunięte. Po usunięciu zasad komunikacji zostaną również usunięte kopie komunikatów skojarzonych z zasadami.

## <a name="microsoft-teams"></a>Microsoft Teams

Komunikację czatu zarówno w publicznych, jak i prywatnych kanałach usługi Microsoft Teams oraz poszczególnych czatach można skanować. Gdy użytkownicy są przypisani do zasad zgodności komunikacji z wybranym zakresem usługi Microsoft Teams, komunikacja czatów dla użytkowników jest automatycznie monitorowana we wszystkich aplikacjach Microsoft Teams, w których użytkownicy są członkami. Pokrycie usługi Microsoft Teams jest automatycznie uwzględniane dla wstępnie zdefiniowanych szablonów zasad i jest domyślnie wybierane w szablonie zasad niestandardowych. Przetwarzanie czatów aplikacji Teams zgodnych z warunkami zasad zgodności komunikacji może potrwać do 48 godzin.

W przypadku prywatnych czatów i kanałów prywatnych zasady zgodności komunikacji obsługują [kanały udostępnione](/MicrosoftTeams/shared-channels) i nowoczesne skanowanie załączników. Obsługa kanałów udostępnionych w usłudze Teams jest obsługiwana automatycznie i nie wymaga dodatkowych zmian konfiguracji zgodności komunikacji. Poniższa tabela zawiera podsumowanie zachowania zgodności komunikacji podczas udostępniania kanałów usługi Teams grupom i użytkownikom:

|**Scenariusz**|**Zachowanie zgodności z komunikacją**|
|:-----------|:------------------------------------|
| **Udostępnianie kanału zespołowi wewnętrznej** | Zasady zgodności komunikacji mają zastosowanie do użytkowników w zakresie i wszystkich komunikatów w kanale udostępnionym |
| **Udostępnianie kanału zespołowi zewnętrznego** | Zasady zgodności komunikacji mają zastosowanie do wewnętrznych użytkowników i komunikatów w zakresie w kanale udostępnionym dla organizacji wewnętrznej |

Nowoczesne załączniki to pliki pochodzące z witryn [usługi OneDrive](/onedrive/plan-onedrive-enterprise#modern-attachments) lub [SharePoint](/sharepoint/dev/solution-guidance/modern-experience-customizations) , które są zawarte w komunikatach usługi Teams. Tekst jest automatycznie wyodrębniany z tych załączników na potrzeby zautomatyzowanego przetwarzania i potencjalnych dopasowań z warunkami i klasyfikatorami zasad zgodności aktywnej komunikacji. Nie ma żadnej dodatkowej konfiguracji niezbędnej do nowoczesnego wykrywania i przetwarzania załączników. Tekst jest wyodrębniany tylko dla załączników pasujących do warunków zasad. Tekst nie jest wyodrębniany dla załączników dla komunikatów z dopasowaniami zasad, nawet jeśli załącznik ma również dopasowanie zasad.

Nowoczesne skanowanie załączników jest obsługiwane dla następujących typów plików:

- Microsoft Word (.docx)
- Microsoft Excel (.xlsx)
- Microsoft PowerPoint (.pptx)
- Tekst (.txt)
- Format dokumentu przenośnego (.pdf)

Wyodrębniony tekst dla nowoczesnych załączników jest dołączony do skojarzonego komunikatu na pulpicie nawigacyjnym **Oczekujące** alerty dla zasad. Wyodrębniony tekst załącznika nosi nazwę pliku załącznika (i rozszerzenie formatu) oraz rozszerzenie .txt. Na przykład wyodrębniony tekst załącznika o nazwie *ContosoBusinessPlan.docx* będzie wyświetlany jako *ContosoBusinessPlan.docx.txt* na pulpicie nawigacyjnym **Oczekujące** alerty dla zasad.

Wybierz wyodrębniony tekst załącznika, aby wyświetlić szczegóły w widokach *Źródło* i *Zwykły tekst* . Po przejrzeniu można rozpoznać tekst załącznika lub podjąć działania za pomocą kontrolek paska poleceń. Możesz również pobrać załącznik do przeglądu poza procesem przeglądu zgodności komunikacji.

Użyj następujących konfiguracji zarządzania grupami, aby nadzorować czaty poszczególnych użytkowników i komunikację kanałów w usłudze Teams:

- **W przypadku komunikacji czatu w usłudze Teams:** Przypisz poszczególnych użytkowników lub przypisz [grupę dystrybucyjną](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) do zasad zgodności komunikacji. To ustawienie dotyczy relacji "jeden do jednego" lub "jeden do wielu" między użytkownikami i czatami.
- **W przypadku komunikacji w usłudze Teams Channel:** Przypisz do zasad zgodności komunikacji każdy kanał usługi Microsoft Teams lub grupę platformy Microsoft 365, którą chcesz zeskanować, zawierającą określonego użytkownika. Jeśli dodasz tego samego użytkownika do innych kanałów usługi Microsoft Teams lub grup platformy Microsoft 365, pamiętaj, aby dodać te nowe kanały i grupy do zasad zgodności komunikacji. Jeśli którykolwiek z członków kanału jest nadzorowanym użytkownikiem w ramach zasad, a kierunek *ruchu przychodzącego* jest skonfigurowany w zasadach, wszystkie komunikaty wysyłane w kanale podlegają przeglądowi i potencjalnym dopasowaniom zasad (nawet w przypadku użytkowników w kanale, którzy nie są jawnie nadzorowani). Na przykład użytkownik A jest właścicielem lub członkiem kanału. Użytkownik B i użytkownik C są członkami tego samego kanału i używają języka zgodnego z nieodpowiednimi zasadami zawartości, które nadzorują tylko użytkownika A. Użytkownik B i użytkownik C tworzą dopasowania zasad dla konwersacji w kanale, mimo że nie są bezpośrednio nadzorowane w zasadach nieodpowiedniej zawartości. Konwersacje aplikacji Teams między użytkownikiem B a użytkownikiem C, które znajdują się poza kanałem zawierającym użytkownika A, nie podlegają nieodpowiednim zasadom zawartości obejmującym użytkownika A. Aby wykluczyć członków kanału z nadzoru, gdy inni członkowie kanału są jawnie nadzorowane, wyłącz ustawienie Kierunek komunikacji *przychodzącej* w odpowiednich zasadach zgodności komunikacji.
- **W przypadku komunikacji czatu w usłudze Teams z hybrydowymi środowiskami poczty e-mail**: zgodność komunikacji może monitorować wiadomości czatu dla użytkowników organizacji z lokalnym wdrożeniem programu Exchange lub zewnętrznym dostawcą poczty e-mail, który włączył usługę Microsoft Teams. Należy utworzyć grupę dystrybucyjną dla użytkowników z lokalnymi lub zewnętrznymi skrzynkami pocztowymi do monitorowania. Podczas tworzenia zasad zgodności komunikacji przypiszesz tę grupę dystrybucyjną jako wybór **nadzorowanych użytkowników i grup** w kreatorze zasad. Aby uzyskać więcej informacji na temat wymagań i ograniczeń dotyczących włączania magazynu w chmurze i obsługi usługi Teams dla użytkowników lokalnych, zobacz [Wyszukiwanie danych czatu w usłudze Teams dla użytkowników lokalnych](search-cloud-based-mailboxes-for-on-premises-users.md).

## <a name="exchange-email"></a>Poczta e-mail programu Exchange

Skrzynki pocztowe hostowane w usłudze Exchange Online w ramach subskrypcji usługi Microsoft 365 lub Office 365 kwalifikują się do skanowania wiadomości. Przetwarzanie wiadomości e-mail i załączników programu Exchange zgodnych z warunkami zasad zgodności komunikacji może potrwać około 24 godzin. Obsługiwane typy załączników dla zgodności komunikacji są takie same jak [typy plików obsługiwane w przypadku inspekcji zawartości reguł przepływu poczty programu Exchange](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection).

## <a name="yammer"></a>Yammer

Prywatne wiadomości i publiczne konwersacje oraz skojarzone załączniki w społecznościach usługi Yammer można skanować. Po dodaniu użytkownika do zasad zgodności komunikacji, które obejmują usługę Yammer jako zdefiniowany kanał, komunikacja między wszystkimi społecznościami usługi Yammer, do których należy użytkownik, jest uwzględniana w procesie skanowania. Przetwarzanie czatów i załączników usługi Yammer zgodnych z warunkami zasad zgodności komunikacji może potrwać do 24 godzin. 

Usługa Yammer musi być w [trybie natywnym](/yammer/configure-your-yammer-network/overview-native-mode) , aby zasady zgodności komunikacji monitorowały komunikację i załączniki usługi Yammer. W trybie natywnym wszyscy użytkownicy usługi Yammer znajdują się w usłudze Azure Active Directory (AAD), wszystkie grupy to grupy usługi Office 365, a wszystkie pliki są przechowywane w usłudze SharePoint Online.

## <a name="skype-for-business-online"></a>Skype dla firm Online

Komunikacja czatu i skojarzone załączniki w usłudze Skype dla firm Online mogą być nadzorowane. Przetwarzanie czatów usługi Skype dla firm Online pasujących do warunków zasad zgodności komunikacji może potrwać do 24 godzin. Nadzorowane konwersacje na czacie pochodzą z [poprzednich konwersacji zapisanych w usłudze Skype dla firm Online](https://support.office.com/article/Find-a-previous-Skype-for-Business-conversation-18892eba-5f18-4281-8c87-fd48bd72e6a2).  

Użyj następującej konfiguracji zarządzania grupami, aby nadzorować komunikację z czatami użytkowników w usłudze Skype dla firm Online:

- **W przypadku komunikacji czatu w usłudze Skype dla firm Online**: przypisz poszczególnych użytkowników lub przypisz [grupę dystrybucyjną](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) do zasad zgodności komunikacji. To ustawienie dotyczy relacji "jeden do jednego" lub "jeden do wielu" między użytkownikami i czatami.

## <a name="third-party-sources"></a>Źródła innych firm

Możesz skanować komunikację pod kątem danych zaimportowanych do skrzynek pocztowych w organizacji platformy Microsoft 365 ze źródeł innych firm, takich jak [Instant Bloomberg](archive-instant-bloomberg-data.md), [Slack](archive-slack-data.md), [Zoom](archive-zoommeetings-data.md), SMS i wiele innych. Aby uzyskać pełną listę łączników obsługiwanych w zakresie zgodności z komunikacją, zobacz [Archiwum danych innych firm](archiving-third-party-data.md).

Przed przypisaniem łącznika do zasad zgodności komunikacji należy skonfigurować łącznik innej firmy dla organizacji platformy Microsoft 365. Sekcja **Źródła innych firm** kreatora zasad zgodności komunikacji wyświetla tylko obecnie skonfigurowane łączniki innych firm.
