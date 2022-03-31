---
title: Microsoft 365 monitorowanie
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: mediumn
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: admindeeplinkMAC
f1.keywords:
- NOCSH
description: Monitorowanie Microsoft 365 uzyskać informacje na temat zdarzeń lub porad dotyczących Microsoft 365.
ms.openlocfilehash: 2d78bcae258730e1b48c7d6cc77fa5ae2b200b07
ms.sourcegitcommit: 0ae89b71b202aceabd5061f0d5b46d030d93e931
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2022
ms.locfileid: "64520859"
---
# <a name="learn-about-microsoft-365-monitoring"></a>Dowiedz się więcej Microsoft 365 monitorowanie

Za pomocą pulpitów nawigacyjnych w [](https://go.microsoft.com/fwlink/p/?linkid=2024339) Centrum administracyjne platformy Microsoft 365 można monitorować kondycję różnych usługi firmy Microsoft subskrypcji usługi Microsoft 365 organizacji. Ta funkcja została początkowo uruchomiona wraz z Exchange Online, a teraz została rozwinięta o inne funkcje usługi firmy Microsoft, takie jak Microsoft Teams, Aplikacje Microsoft 365 i nie tylko, w przyszłości. Monitorowanie zapewnia informacje o incydentach i poradach zbieranych w następujących kategoriach:

- **Infrastruktura**. Problem jest wykrywany w infrastrukturze Microsoft 365 firmy Microsoft do regularnego dostarczania aktualizacji i rozwiązywania problemu. Na przykład użytkownicy nie mogą uzyskać dostępu do Exchange Online ze względu na problemy z Exchange lub inną Microsoft 365 w chmurze.

- **Infrastruktura innych firm**. Problem jest wykrywany w infrastrukturze innych firm, od której Twoja organizacja korzysta z zależności i wymaga od organizacji działania w celu rozwiązania problemu. Na przykład transakcje uwierzytelniania użytkowników są ograniczane przez zewnętrznego dostawcę usługi tokenu zabezpieczającego (STS), który uniemożliwia użytkownikom łączenie się z usługą Exchange Online.

- **Infrastruktura klientów**. Problem jest wykrywany w infrastrukturze organizacji i wymaga od organizacji działania w celu rozwiązania problemu. Na przykład użytkownicy nie mogą uzyskać dostępu do Exchange Online ponieważ nie mogą uzyskać tokenu uwierzytelniania od dostawcy STS hostowanej przez Twoją organizację z powodu wygasłego certyfikatu.

Oto przykład strony Kondycja usługi w Centrum administracyjne platformy Microsoft 365 kondycji,  >  która jest dostępna w kondycji **Kondycja usługi** scenariuszy organizacji i scenariuszy kont [priorytetowych](../admin/setup/priority-accounts.md).

![Strona Kondycja usługi w Centrum administracyjne platformy Microsoft 365.](../media/microsoft-365-exchange-monitoring/service-health-dashboard-example.png)

**Problemy w Twojej organizacji będą** identyfikowane i używane przez monitorowanie na poziomie organizacji oraz monitorowanie priorytetu konta.

Wartość kolumny Kondycja w obszarze  Problemy w organizacji wskazuje, czy infrastruktura organizacji lub oprogramowanie innych firm wpływa na kondycję usług użytkowników i/lub priorytetów kont organizacji w Exchange Online. W przypadku porad i zdarzeń wymagane jest rozwiązanie twoich działań.

Wartość kolumny Kondycja w obszarze Kondycja usługi firmy **Microsoft** wskazuje, że usługa jest w dobrej kondycji bądź zawiera doradcy lub zdarzenia oparte na usługach w chmurze posiadanych przez firmę Microsoft.

Oto przykład strony monitorowania usługi Exchange Online w aplikacji Centrum administracyjne platformy Microsoft 365 > , która pokazuje kondycję scenariuszy konta na poziomie organizacji i priorytetów dostępnych na stronie Kondycja **Kondycja usługi** >  **Exchange Online**.

![Scenariusze monitorowania danych Exchange Online organizacji.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-org-scenarios.png)

Na stronie listy scenariuszy możesz sprawdzić, czy usługa firmy Microsoft jest w dobrej kondycji i czy są skojarzone zdarzenia lub doradcy. Na przykład dzięki Exchange Online możesz sprawdzić kondycję usługi pod tematem określonych scenariuszy poczty e-mail i wyświetlić sygnały w czasie rzeczywistym, aby ustalić wpływ scenariusza na poziomie organizacji. Możesz także sprawdzić kondycję scenariuszy kont priorytetowych, jeśli są dostępne.

## <a name="requirements-for-monitoring"></a>Wymagania dotyczące monitorowania

Ta wersja Preview jest włączona dla klientów, którzy spełniają następujące wymagania:

- Twoja organizacja musi mieć liczbę licencji co najmniej 5000 na jednym lub w kombinacji tych produktów: Office 365 E3, Microsoft 365 E3, Office 365 E5 lub Microsoft 365 E5.

   Na przykład organizacja może mieć 3000 Office 365 E3 licencji i 2500 Microsoft 365 E5, co łącznie 5500 licencji z kwalifikujących się produktów.

- Twoja organizacja musi mieć co najmniej 50 aktywnych użytkowników miesięcznie dla jednej lub większej liczby podstawowych usług Microsoft 365, takich jak aplikacje Microsoft Teams, OneDrive dla Firm, SharePoint Online, Exchange Online i Office.

- Każda rola z uprawnieniami na poziomie pulpitu nawigacyjnego kondycji usługi może mieć Exchange Online monitorowanie. Aby uzyskać więcej informacji, zobacz [Jak sprawdzić kondycję usługi Microsoft 365](view-service-health.md).

## <a name="additional-monitoring-for-microsoft-services"></a>Dodatkowe monitorowanie usługi firmy Microsoft

Monitorowanie specyficzne dla usługi jest również włączane dla następujących usługi firmy Microsoft. Wybierz odpowiedni link, aby dowiedzieć się więcej na temat monitorowania dla tej usługi.

- [Exchange Online](microsoft-365-exchange-monitoring.md)

- [Aplikacje Microsoft 365](microsoft-365-apps-monitoring.md)

- [Microsoft Teams](microsoft-365-teams-monitoring.md)

## <a name="send-us-feedback"></a>Prześlij nam opinię

Opinie można przekazać na dwa sposoby:

- Użyj opcji **Opinie** dostępnej na każdej stronie Centrum administracyjne platformy Microsoft 365.

- Prześlij opinię za pomocą **Czy ten wpis jest pomocny? link do określonego zdarzenia lub porady.

  !["Czy ten wpis jest przydatny?" link do określonego zdarzenia lub porady.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-example-incident-feedback.png)

## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="1-why-dont-i-see-view-link-under-organizational-monitoring-column-in-the-microsoft-365-admin-center-inside-service-health"></a>1. Dlaczego nie widzę linku "Wyświetlanie" w kolumnie Monitorowanie organizacji w Centrum administracyjne platformy Microsoft 365 kondycji usługi?

Najpierw upewnij się, że nowe centrum administracyjne jest **włączone na stronie** głównej [Centrum administracyjne platformy Microsoft 365.](https://go.microsoft.com/fwlink/p/?linkid=2024339)

Następnie upewnij się, że są spełnione oba poniższe wymagania:

- Twoja organizacja musi mieć liczbę licencji co najmniej 5000 licencji na jeden produkt lub kombinację tych produktów: Office 365 E3, Microsoft 365 E3, Office 365 E5 lub Microsoft 365 E5.

- Twoja organizacja musi mieć co najmniej 50 aktywnych użytkowników miesięcznie dla jednej lub większej liczby podstawowych usług Microsoft 365, takich jak aplikacje Microsoft Teams, OneDrive dla Firm, SharePoint Online, Exchange Online i Office.

Jeśli liczba licencji dla organizacji spadnie poniżej 5000 użytkowników, Exchange Online użytkownicy co miesiąc są aktywni poniżej 50 użytkowników w usługach podstawowych, monitorowanie usługi Exchange Online nie zostanie włączone do momentu, gdy te wymagania zostaną spełnione.

### <a name="2-will-there-be-other-monitoring-scenarios-for-other-services-in-future"></a>2. Czy w przyszłości będą dostępne inne scenariusze monitorowania dla innych usług?

Tak. Teraz dostępnych jest jeszcze kilka innych usług w publicznej wersji zapoznawczej. Będziemy nadal pracować nad rozszerzeniem miejsca zajmowanego przez inne usługi.

### <a name="3-what-is-the-plan-for-general-availability-of-this-experience"></a>3. Jaki jest plan ogólnej dostępności tego programu?

Plan firmy Microsoft to zbieranie opinii na temat funkcji wersji Preview, a następnie definiowanie naszego planu pod celu ogólnego działania firmy Microsoft.

### <a name="4-is-this-a-free-included-or-paid-extra-feature"></a>4. Czy jest to bezpłatna (w zestawie) czy płatna (dodatkowa) funkcja?

Jest to bezpłatna funkcja, która jest w wersji zapoznawczej i dostępna tylko dla klientów, którzy spełniają wymagania określone w pytaniu 1. Nie ma płatnej opcji odbierania tej zawartości.

### <a name="5-how-do-i-provide-feedback"></a>5. Jak mogę przekazać opinię?

Aby uzyskać opinię ogólną,  użyj ikony Opinie w prawym dolnym rogu strony monitorowania.

Aby uzyskać opinię na temat zdarzeń lub porad, skorzystaj z **Czy ten wpis jest pomocny? .

### <a name="6-are-there-any-privacy-concerns"></a>6. Czy istnieją jakieś problemy dotyczące prywatności?

Monitorowanie dotyczy metadanych usługi i zawartości użytkownika, które nie są monitorowane.
