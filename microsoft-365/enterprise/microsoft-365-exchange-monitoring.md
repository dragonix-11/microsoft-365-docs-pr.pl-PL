---
title: Exchange Online monitorowanie Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: admindeeplinkMAC
f1.keywords:
- NOCSH
description: Monitorowanie Exchange Online informacji o incydentach e-mail i poradach dotyczących poczty e-mail w Microsoft 365.
ms.openlocfilehash: 07d43a6f61ffe3e38f927d47e09d0a9685925f73
ms.sourcegitcommit: 0ae89b71b202aceabd5061f0d5b46d030d93e931
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2022
ms.locfileid: "64520732"
---
# <a name="exchange-online-monitoring-for-microsoft-365"></a>Exchange Online monitorowanie Microsoft 365

Exchange Online monitorowanie obsługuje następujące scenariusze na poziomie organizacji:

- **Klienci poczty e-mail**: Możesz wyświetlić kondycję następujących klientów poczty e-mail na podstawie aktywności odczytywania wiadomości e-mail:

  - Outlook pulpitu
  - Outlook on the web
  - Natywne klienci poczty systemów iOS i Android
  - Outlook dla urządzeń przenośnych w systemach iOS i Android
  - Outlook klienta komputera Mac

   W przypadku tych klientów możesz sprawdzić liczbę aktywnych użytkowników w ciągu ostatnich 30 minut na podstawie liczby odczytanych wiadomości e-mail oraz zdarzeń i porad na pulpicie nawigacyjnym. Te dane są porównywane z tym samym interwałem w zeszłym tygodniu, aby sprawdzić, czy występuje problem.

   >[!Note]
   > Liczba aktywnych użytkowników jest mierzona za pomocą jednego działania, na przykład gdy użytkownik czyta wiadomość e-mail. Jest to tylko konto dla ostatnich 30 minut aktywności.

- **Łączność** z aplikacją: Szacowana łączność opiera się na procencie pomyślnego, częściowego połączenia między urządzeniami organizacji i Exchange Online i może obejmować problemy poza kontrolą firmy Microsoft. Aby dowiedzieć się więcej, [zobacz Microsoft 365 łączności.](microsoft-365-connectivity-optics.md)

- **Uwierzytelnianie podstawowe i nowoczesne** uwierzytelnianie: liczba użytkowników pomyślnie zweryfikowana w Exchange Online usługi.

- **Przepływ poczty** e-mail: Liczba wiadomości pomyślnie dostarczonych do skrzynki pocztowej bez żadnego opóźnienia po dotarniu wiadomości do Microsoft 365 sieci.

- **Otwórz Outlook sieci Web**: Liczba użytkowników, którzy się zalogowali i zaczęli pracę Outlook w sieci Web.
  
Oto przykład scenariuszy dla aplikacji na poziomie organizacji Exchange Online głównym pulpicie nawigacyjnym.

![Scenariusze monitorowania danych Exchange Online organizacji.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-org-scenarios.png)

W przypadku takich scenariuszy najważniejsze informacje obejmują ostatnie 30 minut na głównym pulpicie nawigacyjnym. W szczegółowych widokach każdego z tych scenariuszy można wyświetlić trend prawie w czasie rzeczywistym dla siedmiu dni oraz zagregowaną wartość 30-minutową w porównaniu z poprzednim tygodniem.

![Przykład monitorowania kondycji Exchange dostarczania poczty.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-scenario-example.png)

Zauważysz zdarzenia lub powiadomienia utworzone dla Twojej organizacji z komunikatem "Problem pochodzenia" w komunikacji otagowanych jako "Twoja organizacja". Są to powiadomienia indywidualnie kierowane do Twojej organizacji z problemami, które wymagają Twojej uwagi na środki zaradcze i rozwiązanie problemu. Aby uzyskać więcej informacji o różnych typach problemów, które są tworzone i przekazywane w kondycji usługi w celu informowania organizacji o potencjalnym wpływie, zobacz następujące artykuły:

- [Alerty usługi dla użycia skrzynek pocztowych](microsoft-365-mailbox-utilization-service-alerts.md)

- [Alerty usługi dotyczące opóźnień źródła MRS](microsoft-365-mrs-source-delays-service-alerts.md)

- [Alerty usługi dotyczące wiadomości oczekujących na dostarczenie do adresatów zewnętrznych](microsoft-365-external-recipient-service-alerts.md)

## <a name="priority-accounts-monitoring-scenarios"></a>Scenariusze monitorowania kont priorytetowych

Dzięki Exchange Online konta priorytetu możesz sprawdzić kondycję następujących scenariuszy po skonfigurowaniu kont [priorytetów](/microsoft-365/admin/setup/priority-accounts):

- Exchange licencji

- Przestrzeń dyskowa wydzielona dla skrzynki pocztowej

- Limit wiadomości

- Podfoldery na folder

- Hierarchia folderów

- Elementy odzyskiwalne

Scenariusz Exchange licencjonowania sprawdza, czy konto o priorytecie nie może się zalogować z powodu problemów z nieprawidłową licencją, na które administrator dzierżawy może rozwiązać problem.

Pozostałe pięć scenariuszy powyżej sprawdza, czy skrzynka pocztowa Twojego konta priorytetu jest bliska osiągnięciu wartości lub osiągnięto limity opisane w Exchange Online [limitach](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#mailbox-storage-limits).

W tych scenariuszach można wyświetlić aktywne i rozwiązane porady i zdarzenia dotyczące kont priorytetowych. Informacje umożliwiające identyfikację dla kont priorytetowych będą wyświetlane w szczegółach porady lub zdarzenia wraz z zaleceniami. Oto przykład ze strony Kondycja **> Kondycja usługi > Exchange Online**.

:::image type="content" source="../media/microsoft-365-exchange-monitoring/exchange-priority-accounts-example.png" alt-text="Przykład aktywnych i rozwiązanych porad i zdarzeń mających wpływ na Twoje konta priorytetowe":::

W okienku konta, którego dotyczy problem, **kolumna Stan** zawiera następujące wartości:

- Rozwiązano: Problem powodujący, że porada lub zdarzenie zostało rozwiązane w przypadku konta priorytetu. Nie ma już problemu. 

- Aktywny: Problem powodujący, że trwa porada lub zdarzenie dla konta priorytetu. Problem nadal występuje. 

- Opóźnione: Problem powodujący, że porada lub zdarzenie nie zostało rozwiązane dla konta priorytetu w ciągu 96 godzin, więc została zawieszona. Problem nadal występuje. 

Oto przykład.

:::image type="content" source="../media/microsoft-365-exchange-monitoring/exchange-status-column-example.png" alt-text="Przykład kolumny stanu w okienku konta, którego dotyczy problem":::

Porada lub zdarzenie zostanie rozwiązane, gdy żadne konta nie pozostaną w **stanie** Aktywne.

## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="1-the-active-user-count-in-the-dashboard-for-each-client-appears-to-be-low-we-have-a-lot-of-active-licenses-assigned-to-users-what-does-this-mean"></a>1. Liczba aktywnych użytkowników na pulpicie nawigacyjnym dla każdego klienta jest niewielka. Do użytkowników jest przypisanych wiele aktywnych licencji. Co to oznacza?

Liczba aktywnych użytkowników wyświetlana w funkcji monitorowania jest oparta na 30-minutowym oknie, w którym użytkownicy wykonali czynności przedstawione w funkcji. Nie należy tego mylić z liczbami użycia. Aby wyświetlić numery użycia, użyj raportów aktywności w Centrum administracyjne platformy Microsoft 365 (<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">**ReportsUsage**</a> > ).

### <a name="2-where-is-the-data-instrumented-for-the-scenarios-that-show-activity-trends"></a>2. Gdzie są na przyrządach danych scenariusze, które pokazują trendy aktywności?

Dane są wykorzystywane na instrumentach w Exchange Online danych. Jeśli występuje błąd, który występuje, zanim żądanie dotrze Exchange Online lub występuje błąd w programie Exchange Online, zobaczysz upuszczenie w sygnału aktywności.
