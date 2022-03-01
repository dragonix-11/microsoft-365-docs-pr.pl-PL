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
ms.openlocfilehash: 22985d1fd6e79693a526c8ec008e189593543ae6
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021284"
---
# <a name="exchange-online-monitoring-for-microsoft-365"></a>Exchange Online monitorowanie Microsoft 365

Za pomocą Exchange Online monitorowania w centrum administracyjne platformy Microsoft 365 możesz monitorować <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank"></a> kondycję usługi Exchange dla subskrypcji usługi Microsoft 365 twojej organizacji. Exchange Online udostępnia informacje na temat zdarzeń i porad zbieranych w tych kategoriach:

- **Infrastruktura**: problem jest wykrywany w infrastrukturze Microsoft 365 firmy Microsoft do regularnego dostarczania aktualizacji i rozwiązywania tego problemu. Na przykład użytkownicy nie mogą uzyskać dostępu Exchange Online z powodu problemów z Exchange lub inną Microsoft 365 w chmurze.
- **Infrastruktura innych firm**: Problem jest wykrywany w infrastrukturze innych firm, od której Twoja organizacja korzysta jako zależność i wymaga od organizacji działania w celu rozwiązania problemu. Na przykład transakcje uwierzytelniania użytkowników są ograniczane przez zewnętrznego dostawcę usługi tokenu zabezpieczającego (STS), który uniemożliwia użytkownikom łączenie się z usługą Exchange Online.
- **Infrastruktura klientów**: Problem jest wykrywany w infrastrukturze organizacji i wymaga od organizacji działania w celu rozwiązania problemu. Na przykład użytkownicy nie mogą uzyskać Exchange Online, ponieważ nie mogą uzyskać tokenu uwierzytelniania od dostawcy STS hostowanej przez Twoją organizację z powodu wygasłego certyfikatu.

Oto przykład strony Kondycja usługi  w centrum administracyjne platformy Microsoft 365 kondycji usługi dostępnej w > Kondycja usługi  dla scenariuszy [konta organizacji i priorytetu](../admin/setup/priority-accounts.md).

![Strona Kondycja usługi w centrum administracyjne platformy Microsoft 365.](../media/microsoft-365-exchange-monitoring/service-health-dashboard-example.png)

**Problemy w Twojej organizacji będą** identyfikowane i używane przez monitorowanie na poziomie organizacji oraz monitorowanie priorytetu konta.

Wartość kolumny Kondycja w obszarze  Problemy w organizacji wskazuje, czy infrastruktura organizacji lub oprogramowanie innych firm wpływa na kondycję usług użytkowników i/lub priorytetów kont organizacji w Exchange Online. W przypadku porad i zdarzeń wymagane *jest* rozwiązanie twoich działań.

Wartość kolumny Kondycja w obszarze Kondycja usługi firmy **Microsoft** wskazuje, że usługa jest w dobrej kondycji bądź zawiera doradcy lub zdarzenia oparte na usługach w chmurze posiadanych przez firmę Microsoft.

Oto przykład strony monitorowania usługi Exchange Online w programie centrum administracyjne platformy Microsoft 365, która przedstawia kondycję scenariuszy konta na poziomie organizacji i priorytetu dostępnych na stronie Kondycja > Kondycja **usługi** > Exchange Online.

![Strona Exchange Online monitorowanie w centrum administracyjne platformy Microsoft 365.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-example.png)

Na stronie **Exchange Online** monitorowanie możesz sprawdzić, czy Exchange Online jest w dobrej kondycji i czy są skojarzone zdarzenia lub doradcy. Dzięki Exchange Online możesz sprawdzić kondycję usługi pod uwagę w określonych scenariuszach poczty e-mail i wyświetlić niemal sygnały w czasie rzeczywistym, aby ustalić wpływ scenariusza na poziomie organizacji. Możesz również sprawdzić kondycję scenariuszy konta priorytetowego.

## <a name="requirements"></a>Wymagania

Ta wersja Preview jest włączona dla klientów, którzy spełniają następujące wymagania:

- Twoja organizacja musi mieć liczbę licencji w wysokości co najmniej 5000 licencji na jednym lub w kombinacji tych produktów: Office 365 E3, Microsoft 365 E3, Office 365 E5, Microsoft 365 E5.

  Na przykład organizacja może mieć 3000 Office 365 E3 licencji i 2500 Microsoft 365 E5, co łącznie 5500 licencji z kwalifikujących się produktów.

- Twoja organizacja musi mieć co najmniej 50 aktywnych użytkowników miesięcznie dla jednej lub większej liczby podstawowych usług Microsoft 365, takich jak aplikacje Microsoft Teams, OneDrive dla Firm, SharePoint Online, Exchange Online i Office.

- Każda rola z uprawnieniami na poziomie pulpitu nawigacyjnego kondycji usługi może mieć Exchange Online monitorowanie. Aby uzyskać więcej informacji, zobacz [Jak sprawdzić kondycję usługi Microsoft 365](view-service-health.md).

## <a name="organization-level-scenarios"></a>Scenariusze na poziomie organizacji

Monitorowanie Exchange Online obsługuje następujące scenariusze:

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

  ![Przykład monitorowania kondycji Exchange dostarczania poczty.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-scenario-example.png)

W przypadku takich scenariuszy najważniejsze informacje obejmują ostatnie 30 minut na głównym pulpicie nawigacyjnym. W szczegółowych widokach każdego z tych scenariuszy można wyświetlić trend prawie w czasie rzeczywistym dla siedmiu dni oraz zagregowaną wartość 30-minutową w porównaniu z poprzednim tygodniem.

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

W tych scenariuszach można wyświetlić aktywne i rozwiązane porady i zdarzenia dotyczące kont priorytetowych. Informacje umożliwiające identyfikację dla kont priorytetowych będą wyświetlane w szczegółach porady lub zdarzenia wraz z zaleceniami. Oto przykład ze strony Kondycja > **Kondycja usługi > Exchange Online**.

:::image type="content" source="../media/microsoft-365-exchange-monitoring/exchange-priority-accounts-example.png" alt-text="Przykład aktywnych i rozwiązanych porad i zdarzeń mających wpływ na Twoje konta priorytetowe":::

W okienku konta, którego dotyczy problem, **kolumna Stan** zawiera następujące wartości:

- Rozwiązano: Problem powodujący, że porada lub zdarzenie zostało rozwiązane w przypadku konta priorytetu. Nie ma już problemu. 

- Aktywny: Problem powodujący, że trwa porada lub zdarzenie dla konta priorytetu. Problem nadal występuje. 

- Opóźnione: problem powodujący, że porada lub zdarzenie nie zostało rozwiązane dla konta priorytetu w ciągu 96 godzin, więc została zawieszona. Problem nadal występuje. 

Oto przykład.

:::image type="content" source="../media/microsoft-365-exchange-monitoring/exchange-status-column-example.png" alt-text="Przykład kolumny stanu w okienku konta, którego dotyczy problem":::

Porada lub zdarzenie zostanie rozwiązane, gdy żadne konta nie pozostaną w **stanie** Aktywne. 

## <a name="send-us-feedback"></a>Prześlij nam opinię

Opinie można przekazać na dwa sposoby:

- Użyj opcji **Opinie** dostępnej na każdej stronie centrum administracyjne platformy Microsoft 365.

- Prześlij opinię, używając **linku Czy ten wpis jest pomocny?** dla określonego zdarzenia lub porady.

  !["Czy ten wpis jest przydatny?" link do określonego zdarzenia lub porady.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-example-incident-feedback.png)

## <a name="frequently-asked-questions"></a>Często zadawane pytania

#### <a name="1-why-dont-i-see-exchange-online-monitoring-under-health-in-the-microsoft-365-admin-center"></a>1. Dlaczego nie widzę "monitorowanie danych Exchange Online" w obszarze Kondycja w centrum administracyjne platformy Microsoft 365? 

Najpierw upewnij się, że nowe centrum administracyjne jest **włączone na stronie** głównej <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365.</a>

Następnie upewnij się, że są spełnione oba poniższe wymagania:

- Twoja organizacja musi mieć liczbę licencji co najmniej 5000 licencji na jeden produkt lub kombinację tych produktów: Office 365 E3, Microsoft 365 E3, Office 365 E5, Microsoft 365 E5.

- Twoja organizacja musi mieć co najmniej 50 aktywnych użytkowników miesięcznie dla jednej lub większej liczby podstawowych usług Microsoft 365, takich jak aplikacje Microsoft Teams, OneDrive dla Firm, SharePoint Online, Exchange Online i Office.

Jeśli liczba licencji dla organizacji spadnie poniżej 5000 użytkowników, Exchange Online użytkownicy co miesiąc są aktywni poniżej 50 użytkowników w usługach podstawowych, monitorowanie usługi Exchange Online nie zostanie włączone do momentu, gdy te wymagania zostaną spełnione.

#### <a name="2-the-active-user-count-in-the-dashboard-for-each-client-appears-to-be-low-we-have-a-lot-of-active-licenses-assigned-to-users-what-does-this-mean"></a>2. Liczba aktywnych użytkowników na pulpicie nawigacyjnym dla każdego klienta jest niewielka. Do użytkowników jest przypisanych wiele aktywnych licencji. Co to oznacza?

Liczba aktywnych użytkowników wyświetlana w funkcji monitorowania jest oparta na 30-minutowym oknie, w którym użytkownicy wykonali czynności przedstawione w funkcji. Nie należy tego mylić z liczbami użycia. Aby wyświetlić numery użycia, użyj raportów aktywności w centrum administracyjne platformy Microsoft 365 (<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">**ReportsUsage**</a> > ).

#### <a name="3-will-there-be-other-monitoring-scenarios-for-other-services-such-as-teams-and-sharepoint"></a>3. Czy istnieją inne scenariusze monitorowania dla innych usług, takich jak Teams i SharePoint?

Firma Microsoft integruje to środowisko bezpośrednio z pulpitu nawigacyjnego kondycji usługi w centrum administracyjne platformy Microsoft 365. Zapewni to firmie Microsoft możliwość rozszerzenia scenariuszy monitorowania dla innych usług, co zostanie ogłoszone, gdy zostaną ogłoszone wiadomości do udostępnienia.

#### <a name="4-what-is-the-plan-for-general-availability-of-this-experience"></a>4. Jaki jest plan ogólnej dostępności tego miejsca?

Firma Microsoft s zintegrowano Exchange Online monitorowanie bezpośrednio na pulpicie <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**nawigacyjnym kondycji**</a> usług w centrum administracyjne platformy Microsoft 365.

Dzięki temu nowemu zintegrowanemu systemowi pracy firma Microsoft planuje zbieranie opinii, a następnie definiowanie naszego planu ogólnego działania w zakresie dostępności.

#### <a name="5-is-this-a-free-included-or-paid-extra-feature"></a>5. Czy jest to bezpłatna (w zestawie) czy płatna (dodatkowa) funkcja? 

Jest to bezpłatna funkcja, która jest w wersji zapoznawczej i dostępna tylko dla klientów, którzy spełniają wymagania określone w pytaniu 1. Nie ma płatnej opcji odbierania tej zawartości.

#### <a name="6-how-do-i-provide-feedback"></a>6. Jak mogę przekazać opinię?

Aby uzyskać opinię ogólną,  użyj ikony Opinie w prawym dolnym rogu strony **Exchange Online monitorowanie.** 

Aby uzyskać opinię na temat zdarzeń lub porad, użyj **linku Czy ten wpis jest pomocny?**

#### <a name="7-where-is-the-data-instrumented-for-the-scenarios-that-show-activity-trends"></a>7. Gdzie są na przyrządach danych scenariusze, które pokazują trendy aktywności?

Dane są wykorzystywane na instrumentach w Exchange Online danych. Jeśli występuje błąd, który występuje, zanim żądanie dotrze Exchange Online lub występuje błąd w programie Exchange Online, zobaczysz upuszczenie sygnału aktywności.

#### <a name="8-are-there-any-privacy-concerns"></a>8. Czy istnieją jakieś problemy dotyczące prywatności?

Monitorowanie jest monitorowane pod kątem metadanych usługi i zawartości użytkownika.

## <a name="see-also"></a>Zobacz też

- [Jak sprawdzić Microsoft 365 kondycji usługi](view-service-health.md) 

- [Exchange Online ograniczenia](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#mailbox-storage-limits)

- [Zarządzanie kontami priorytetów i monitorowanie ich](/microsoft-365/admin/setup/priority-accounts)

- [Korzystanie z kont priorytetowych w programie Microsoft 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/using-priority-accounts-in-microsoft-365/ba-p/1873314)

- [Alerty usługi dotyczące użycia skrzynek pocztowych Exchange Online monitorowanie](microsoft-365-mailbox-utilization-service-alerts.md)

- [Alerty usługi dotyczące opóźnień źródła MRS w Exchange Online sieci](microsoft-365-mrs-source-delays-service-alerts.md)
