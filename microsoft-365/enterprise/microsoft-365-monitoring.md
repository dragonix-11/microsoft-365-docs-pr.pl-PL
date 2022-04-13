---
title: Monitorowanie usługi Microsoft 365
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
description: Użyj monitorowania Microsoft 365, aby uzyskać informacje o zdarzeniach lub poradach w Microsoft 365.
ms.openlocfilehash: 47f54859d7dd0973814a0ad9229a902bddcb8587
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824846"
---
# <a name="learn-about-microsoft-365-monitoring"></a>Dowiedz się więcej o monitorowaniu Microsoft 365

Pulpity nawigacyjne w [Centrum administracyjne platformy Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339) umożliwiają monitorowanie kondycji różnych usługi firmy Microsoft dla subskrypcji Microsoft 365 organizacji. Ta funkcja została początkowo uruchomiona z Exchange Online, a teraz została rozszerzona na inne usługi firmy Microsoft, takie jak Microsoft Teams, Aplikacje Microsoft 365 i więcej usług w przyszłości. Monitorowanie udostępnia informacje o zdarzeniach i poradach zbieranych w następujących kategoriach:

- **Infrastruktura**. Wykryto problem w infrastrukturze Microsoft 365, której właścicielem jest firma Microsoft, w celu zapewnienia regularnych aktualizacji i rozwiązania problemu. Na przykład użytkownicy nie mogą uzyskać dostępu do Exchange Online z powodu problemów z Exchange lub inną infrastrukturą chmury Microsoft 365.

- **Infrastruktura innej firmy**. Problem jest wykrywany w infrastrukturze innej firmy, w której organizacja podjęła zależność i wymaga działania organizacji w celu rozwiązania problemu. Na przykład transakcje uwierzytelniania użytkowników są ograniczane przez dostawcę usług tokenów zabezpieczających (STS) innej firmy, który uniemożliwia użytkownikom nawiązywanie połączenia z Exchange Online.

- **Infrastruktura klienta**. Problem jest wykrywany w infrastrukturze organizacji i wymaga działania organizacji w celu rozwiązania problemu. Na przykład użytkownicy nie mogą uzyskać dostępu do Exchange Online, ponieważ nie mogą uzyskać tokenu uwierzytelniania od dostawcy usługi STS hostowanego przez organizację z powodu wygasłego certyfikatu.

Oto przykład strony **Kondycja usługi** w Centrum administracyjne platformy Microsoft 365, która jest dostępna w obszarze **Kondycja** >  **Kondycja usługi** dla scenariuszy organizacji i scenariuszy [kont priorytetowych](../admin/setup/priority-accounts.md).

![Strona Kondycja usługi w Centrum administracyjne platformy Microsoft 365.](../media/microsoft-365-exchange-monitoring/service-health-dashboard-example.png)

**Problemy w organizacji** będą identyfikowane i używane przez monitorowanie na poziomie organizacji i monitorowanie konta priorytetowego.

Wartość kolumny **Kondycja** **w obszarze Problemy w organizacji** wskazuje, czy infrastruktura organizacji lub oprogramowanie innych firm wpływa na środowisko kondycji usługi użytkowników i/lub kont priorytetowych organizacji w Exchange Online. Porady lub zdarzenia wymagają rozwiązania twoich działań.

Wartość kolumny **Kondycja** w obszarze **Kondycja usługi firmy Microsoft** wskazuje, że usługa jest w dobrej kondycji lub zawiera porady lub zdarzenia oparte na usługach w chmurze obsługiwanych przez firmę Microsoft.

Oto przykład strony monitorowania Exchange Online w Centrum administracyjne platformy Microsoft 365, która pokazuje kondycję scenariuszy konta na poziomie organizacji i priorytetów dostępnych w obszarze **Kondycja** >  **Kondycja usługi** >  **Exchange Online**.

![Scenariusze na poziomie organizacji dotyczące monitorowania Exchange Online.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-org-scenarios.png)

Na stronie listy scenariuszy możesz sprawdzić, czy usługa firmy Microsoft jest w dobrej kondycji, czy nie, oraz czy istnieją jakieś powiązane zdarzenia lub porady. Na przykład dzięki monitorowaniu Exchange Online można przyjrzeć się kondycji usługi pod kątem konkretnych scenariuszy poczty e-mail i wyświetlić sygnały niemal w czasie rzeczywistym, aby określić wpływ scenariusza na poziomie organizacji. Możesz również zobaczyć kondycję scenariuszy kont priorytetowych, jeśli są dostępne.

## <a name="requirements-for-monitoring"></a>Wymagania dotyczące monitorowania

Ta wersja zapoznawcza jest włączona dla klientów, którzy spełniają następujące wymagania:

- Twoja organizacja musi mieć liczbę licencji co najmniej 5000 z jednego lub kombinacji tych produktów: Office 365 E3, Microsoft 365 E3, Office 365 E5 lub Microsoft 365 E5.

   Na przykład organizacja może mieć 3000 licencji Office 365 E3 i 2500 Microsoft 365 E5, co daje łącznie 5500 licencji z kwalifikujących się produktów.

- Organizacja musi mieć co najmniej 50 aktywnych użytkowników miesięcznie dla co najmniej jednej podstawowej usługi Microsoft 365, w tym Microsoft Teams, OneDrive dla Firm, SharePoint Online, Exchange Online i Office aplikacji.

- Każda rola z uprawnieniami na poziomie pulpitu nawigacyjnego usługi Service Health może uzyskiwać dostęp do Exchange Online Monitorowanie. Aby uzyskać więcej informacji, zobacz [Jak sprawdzić kondycję usługi Microsoft 365](view-service-health.md).

## <a name="additional-monitoring-for-microsoft-services"></a>Dodatkowe monitorowanie usługi firmy Microsoft

Monitorowanie specyficzne dla usługi jest również włączone dla następujących usługi firmy Microsoft. Wybierz odpowiedni link, aby dowiedzieć się więcej na temat monitorowania dla tej usługi.

- [Exchange Online](microsoft-365-exchange-monitoring.md)

- [Aplikacje Microsoft 365](microsoft-365-apps-monitoring.md)

- [Microsoft Teams](microsoft-365-teams-monitoring.md)

## <a name="send-us-feedback"></a>Wyślij nam opinię

Istnieją dwa sposoby przekazywania opinii:

- Użyj opcji **Przekaż opinię** dostępnej na każdej stronie Centrum administracyjne platformy Microsoft 365.

- Prześlij opinię przy użyciu **Czy ten wpis jest pomocny? link do określonego zdarzenia lub porady.

  !["Czy ten wpis jest pomocny?" link do określonego zdarzenia lub porady.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-example-incident-feedback.png)

## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="1-why-dont-i-see-view-link-under-organizational-monitoring-column-in-the-microsoft-365-admin-center-inside-service-health"></a>1. Dlaczego nie widzę linku "view" w kolumnie Monitorowanie organizacyjne w Centrum administracyjne platformy Microsoft 365 w usłudze Service Health?

Najpierw upewnij się, że włączono nowe centrum administracyjne na stronie **głównej** [Centrum administracyjne platformy Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339).

Następnie upewnij się, że spełniasz oba następujące wymagania:

- Twoja organizacja musi mieć liczbę licencji wynoszącą co najmniej 5000 z jednego lub kombinacji tych produktów: Office 365 E3, Microsoft 365 E3, Office 365 E5 lub Microsoft 365 E5.

- Organizacja musi mieć co najmniej 50 aktywnych użytkowników miesięcznie dla co najmniej jednej podstawowej usługi Microsoft 365, w tym Microsoft Teams, OneDrive dla Firm, SharePoint Online, Exchange Online i Office aplikacji.

Jeśli liczba licencji w organizacji spadnie poniżej 5000 użytkowników, a liczba aktywnych użytkowników miesięcznie spadnie poniżej 50 użytkowników w podstawowych usługach, monitorowanie Exchange Online nie zostanie włączone, dopóki te wymagania nie zostaną spełnione.

### <a name="2-will-there-be-other-monitoring-scenarios-for-other-services-in-future"></a>2. Czy w przyszłości będą dostępne inne scenariusze monitorowania dla innych usług?

Tak. Mamy teraz jeszcze kilka usług w publicznej wersji zapoznawczej. Będziemy nadal pracować nad rozszerzeniem śladu na inne usługi.

### <a name="3-what-is-the-plan-for-general-availability-of-this-experience"></a>3. Jaki jest plan ogólnej dostępności tego środowiska?

Plan firmy Microsoft polega na zebraniu opinii na temat środowiska wersji zapoznawczej, a następnie zdefiniowaniu naszego planu pod kątem ogólnej dostępności.

### <a name="4-is-this-a-free-included-or-paid-extra-feature"></a>4. Czy jest to bezpłatna (dołączona) czy płatna (dodatkowa) funkcja?

Jest to bezpłatna funkcja dostępna w wersji zapoznawczej i dostępna tylko dla klientów spełniających określone wymagania 1. Nie ma płatnej opcji otrzymywania tej zawartości.

### <a name="5-how-do-i-provide-feedback"></a>5. Jak mogę przekazać opinię?

Aby uzyskać ogólną opinię, użyj ikony **Przekaż opinię** w prawym dolnym rogu strony monitorowania.

Aby uzyskać opinię na temat zdarzeń lub porad, użyj wpisu **Czy ten wpis jest pomocny? Link.

### <a name="6-are-there-any-privacy-concerns"></a>6. Czy istnieją jakiekolwiek obawy dotyczące prywatności?

Monitorowanie koncentruje się na metadanych usługi i zawartość użytkownika nie jest monitorowana.
