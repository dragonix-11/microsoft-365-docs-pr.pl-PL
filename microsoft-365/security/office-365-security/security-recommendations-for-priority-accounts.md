---
title: Zalecenia dotyczące zabezpieczeń dla kont priorytetów w Microsoft 365, kont priorytetowych, kont priorytetowych w Office 365, kont priorytetowych w Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.date: ''
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-protecthve
ms.custom: ''
description: Administratorzy mogą dowiedzieć się, jak podnieść poziom ustawień zabezpieczeń i używać raportów, alertów i badań dotyczących kont priorytetowych w organizacjach Microsoft 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 99e4726af1226e044715d33e92a176c9292b49ab
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873385"
---
# <a name="security-recommendations-for-priority-accounts-in-microsoft-365"></a>Zalecenia dotyczące zabezpieczeń dla kont priorytetowych na platformie Microsoft 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy:**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Nie wszystkie konta użytkowników mają dostęp do tych samych informacji firmowych. Niektóre konta mają dostęp do poufnych informacji, takich jak dane finansowe, informacje o rozwoju produktu, dostęp partnera do krytycznych systemów kompilacji i nie tylko. W przypadku naruszenia zabezpieczeń konta, które mają dostęp do wysoce poufnych informacji, stanowią poważne zagrożenie. Nazywamy te typy _kont kontami priorytetowymi_. Konta priorytetowe obejmują (ale nie są ograniczone do) dyrektorów generalnych, dyrektorów ciso, dyrektorów finansowych, kont administratora infrastruktury, kont systemowych kompilacji i innych.

W przypadku osób atakujących zwykłe ataki phishingowe, które rzutują losową sieć dla zwykłych lub nieznanych użytkowników, są nieefektywne. Z drugiej strony ataki polegające na _wyłudzaniu informacji_ lub _atakach wielorybniczych_ , które są celem kont priorytetowych, są bardzo satysfakcjonujące dla osób atakujących. Dlatego konta priorytetów wymagają silniejszej niż zwykła ochrona, aby zapobiec naruszeniu zabezpieczeń konta.

Microsoft 365 i Ochrona usługi Office 365 w usłudze Microsoft Defender zawierają kilka kluczowych funkcji, które zapewniają dodatkowe warstwy zabezpieczeń dla kont priorytetów. W tym artykule opisano te możliwości i sposób ich używania.

:::image type="content" source="../../media/security-recommendations-for-priority-users.png" alt-text="Podsumowanie zaleceń dotyczących zabezpieczeń w formularzu ikony" lightbox="../../media/security-recommendations-for-priority-users.png":::

|Zadanie|Wszystkie plany Office 365 Enterprise|Microsoft 365 E3|Microsoft 365 E5|
|---|:---:|:---:|:---:|
|[Zwiększanie zabezpieczeń logowania dla kont priorytetowych](#increase-sign-in-security-for-priority-accounts)|![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Używanie ścisłych wstępnie ustawionych zasad zabezpieczeń dla kont priorytetów](#use-strict-preset-security-policies-for-priority-accounts)|![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Stosowanie tagów użytkowników do kont priorytetowych](#apply-user-tags-to-priority-accounts)|||![Zawarte](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Monitorowanie kont priorytetów w alertach, raportach i wykrywaniu](#monitor-priority-accounts-in-alerts-reports-and-detections)|||![Zawarte](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Szkolenie użytkowników](#train-users)|![Zawarte.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Zawarte](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Zawarte](../../media/d238e041-6854-4a78-9141-049224df0795.png)|

> [!NOTE]
> Aby uzyskać informacje na temat zabezpieczania _kont uprzywilejowanych_ (kont administratorów), zobacz [ten temat](/security/compass/critical-impact-accounts).

## <a name="increase-sign-in-security-for-priority-accounts"></a>Zwiększanie zabezpieczeń logowania dla kont priorytetowych

Konta priorytetowe wymagają zwiększonych zabezpieczeń logowania. Możesz zwiększyć ich bezpieczeństwo logowania, wymagając uwierzytelniania wieloskładnikowego (MFA) i wyłączając starsze protokoły uwierzytelniania.

Aby uzyskać instrukcje, zobacz [Krok 1. Zwiększ bezpieczeństwo logowania dla pracowników zdalnych za pomocą uwierzytelniania wieloskładnikowego](../../solutions/empower-people-to-work-remotely-secure-sign-in.md). Chociaż ten artykuł dotyczy pracowników zdalnych, te same pojęcia dotyczą użytkowników o priorytecie.

**Uwaga**: zdecydowanie zalecamy globalne wyłączenie starszych protokołów uwierzytelniania dla wszystkich użytkowników o priorytecie zgodnie z opisem w poprzednim artykule. Jeśli wymagania biznesowe uniemożliwiają to, Exchange Online oferuje następujące kontrolki ułatwiające ograniczenie zakresu starszych protokołów uwierzytelniania:

- Zasady [uwierzytelniania](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online) i [reguły dostępu klienta](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules) w Exchange Online umożliwiają blokowanie lub zezwalanie na uwierzytelnianie podstawowe i starsze protokoły uwierzytelniania, takie jak POP3, IMAP4 i uwierzytelniony protokół SMTP dla określonych użytkowników.

- Dostęp POP3 i IMAP4 można wyłączyć w poszczególnych skrzynkach pocztowych. Uwierzytelniony protokół SMTP można wyłączyć na poziomie organizacji i włączyć go w określonych skrzynkach pocztowych, które nadal tego wymagają. Aby uzyskać instrukcje, zobacz następujące artykuły:
  - [Włączanie lub wyłączanie dostępu POP3 lub IMAP4 dla użytkownika](/exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access)
  - [Włączanie lub wyłączanie przesyłania uwierzytelnionego klienta SMTP (SMTP AUTH)](/exchange/clients-and-mobile-in-exchange-online/authenticated-client-smtp-submission)

Warto również zauważyć, że uwierzytelnianie podstawowe jest w trakcie wycofywania w Exchange Online dla usług Exchange Web Services (EWS), Exchange ActiveSync, POP3, IMAP4 i zdalnego programu PowerShell. Aby uzyskać szczegółowe informacje, zobacz ten [wpis w blogu](https://developer.microsoft.com/office/blogs/deferred-end-of-support-date-for-basic-authentication-in-exchange-online/).

## <a name="use-strict-preset-security-policies-for-priority-accounts"></a>Używanie ścisłych wstępnie ustawionych zasad zabezpieczeń dla kont priorytetów

Użytkownicy priorytetowi wymagają bardziej rygorystycznych akcji dla różnych zabezpieczeń dostępnych w Exchange Online Protection (EOP) i Ochrona usługi Office 365 w usłudze Defender.

Na przykład zamiast dostarczać wiadomości sklasyfikowane jako spam do folderu Wiadomości-śmieci, należy poddać te same wiadomości kwarantannie, jeśli są one przeznaczone dla kont priorytetowych.

To rygorystyczne podejście można zaimplementować w przypadku kont priorytetowych przy użyciu profilu Ścisłe w wstępnie ustawionych zasadach zabezpieczeń.

Wstępnie ustawione zasady zabezpieczeń to wygodna i centralna lokalizacja umożliwiająca stosowanie zalecanych przez nas ustawień zasad ścisłych dla wszystkich zabezpieczeń w ramach EOP i Ochrona usługi Office 365 w usłudze Defender. Aby uzyskać więcej informacji, zobacz [Preset security policies in EOP and Ochrona usługi Office 365 w usłudze Microsoft Defender (Ustawienia wstępne zasad zabezpieczeń w usłudze EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender](preset-security-policies.md)).

Aby uzyskać szczegółowe informacje o tym, jak ustawienia zasad ścisłych różnią się od ustawień domyślnych i standardowych zasad, zobacz [Zalecane ustawienia dotyczące EOP i zabezpieczeń Ochrona usługi Office 365 w usłudze Microsoft Defender](recommended-settings-for-eop-and-office365.md).

## <a name="apply-user-tags-to-priority-accounts"></a>Stosowanie tagów użytkowników do kont priorytetowych

Tagi użytkowników w Ochrona usługi Office 365 w usłudze Microsoft Defender planie 2 (w ramach Microsoft 365 E5 lub subskrypcji dodatku) to sposób szybkiego identyfikowania i klasyfikowania określonych użytkowników lub grup użytkowników w raportach i badaniach zdarzeń.

**Konta priorytetowe** to typ wbudowanego tagu użytkownika (znanego jako _tag systemowy_), którego można użyć do identyfikowania zdarzeń i alertów obejmujących konta priorytetowe. Aby uzyskać więcej informacji na temat **kont priorytetowych**, zobacz [Zarządzanie kontami priorytetów i monitorowanie ich](../../admin/setup/priority-accounts.md).

Można również tworzyć tagi niestandardowe w celu dalszego identyfikowania i klasyfikowania kont priorytetów. Aby uzyskać więcej informacji, zobacz [Tagi użytkowników](user-tags.md). **Kontami priorytetów** (tagami systemowymi) można zarządzać w tym samym interfejsie co niestandardowe tagi użytkowników.

## <a name="monitor-priority-accounts-in-alerts-reports-and-detections"></a>Monitorowanie kont priorytetów w alertach, raportach i wykrywaniu

Po zabezpieczeniu i otagowaniu priorytetowych użytkowników możesz użyć dostępnych raportów, alertów i badań w ramach EOP i Ochrona usługi Office 365 w usłudze Defender, aby szybko identyfikować zdarzenia lub wykrycia obejmujące konta priorytetowe. Funkcje obsługujące tagi użytkowników zostały opisane w poniższej tabeli.

|Funkcja|Opis|
|---|---|
|Alerty|Tagi użytkowników, których dotyczy problem, są widoczne i dostępne jako filtry na stronie **Alerty** w portalu Microsoft 365 Defender. Aby uzyskać więcej informacji, zobacz [Wyświetlanie alertów](../../compliance/alert-policies.md#viewing-alerts).|
|Explorer <p> Wykrywanie w czasie rzeczywistym|W **Eksploratorze** (Ochrona usługi Office 365 w usłudze Defender planie 2) lub **wykrywaniu w czasie rzeczywistym** (Ochrona usługi Office 365 w usłudze Defender planie 1) tagi użytkowników są widoczne w widoku siatki poczty e-mail i wysuwanej oknie wysuwnym Szczegóły wiadomości e-mail. Tagi użytkowników są również dostępne jako właściwość z możliwością filtrowania. Aby uzyskać więcej informacji, zobacz  [Tagi w Eksploratorze](threat-explorer.md#tags-in-threat-explorer).|
|Widoki kampanii|Tagi użytkowników są jedną z wielu właściwości filtrowalnych w widokach kampanii w Ochrona usługi Office 365 w usłudze Microsoft Defender planie 2. Aby uzyskać więcej informacji, zobacz [Widoki kampanii](campaigns.md).|
|Raport o stanie ochrony przed zagrożeniami|W praktycznie wszystkich widokach i tabelach szczegółów w **raporcie o stanie ochrony przed zagrożeniami** można filtrować wyniki według **kont priorytetów**. Aby uzyskać więcej informacji, zobacz [Raport o stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report).|
|Problemy z pocztą e-mail dotyczące raportów kont priorytetowych|Raport **Problemy z pocztą e-mail dla kont priorytetowych** w centrum administracyjnym Exchange (EAC) zawiera informacje o niedostarczonych i opóźnionych komunikatach dla **kont priorytetowych**. Aby uzyskać więcej informacji, zobacz [Problemy z pocztą e-mail dla raportu kont priorytetowych](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report).|

## <a name="train-users"></a>Szkolenie użytkowników

Szkolenie użytkowników z kontami o priorytecie może pomóc zaoszczędzić tym użytkownikom i zespołowi ds. operacji zabezpieczeń dużo czasu i frustracji. Doświadczeni użytkownicy są mniej skłonni do otwierania załączników lub klikania linków w wątpliwych wiadomościach e-mail i są bardziej skłonni do unikania podejrzanych witryn internetowych.

[Podręcznik kampanii cyberbezpieczeństwa](https://www.belfercenter.org/CyberPlaybook) Harvard Kennedy School zawiera doskonałe wskazówki dotyczące ustanawiania silnej kultury świadomości bezpieczeństwa w organizacji, w tym szkolenia użytkowników do identyfikowania ataków wyłudzających informacje.

Microsoft 365 udostępnia następujące zasoby ułatwiające informowanie użytkowników w organizacji:

|Koncepcja|Zasoby|Opis|
|---|---|---|
|Microsoft 365|[Dostosowywalne ścieżki szkoleniowe](/office365/customlearning/)|Te zasoby mogą pomóc w zebraniu szkoleń dla użytkowników w organizacji.|
|Centrum zabezpieczeń platformy Microsoft 365|[moduł Edukacja: Zabezpieczanie organizacji za pomocą wbudowanych, inteligentnych zabezpieczeń z Microsoft 365](/learn/modules/security-with-microsoft-365)|Ten moduł umożliwia opisanie sposobu współdziałania funkcji zabezpieczeń Microsoft 365 oraz przedstawienie korzyści wynikających z tych funkcji zabezpieczeń.|
|Uwierzytelnianie wieloskładnikowe|[Weryfikacja dwuetapowa: Jaka jest dodatkowa strona weryfikacji?](/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time)|Ten artykuł pomaga użytkownikom końcowym zrozumieć, czym jest uwierzytelnianie wieloskładnikowe i dlaczego jest używane w organizacji.|
|Trenowanie symulacji ataków|[Wprowadzenie do szkolenia z symulacji ataku](attack-simulation-training-get-started.md)|Trenowanie symulacji ataków w planie Ochrona usługi Office 365 w usłudze Microsoft Defender 2 umożliwia administratorowi konfigurowanie, uruchamianie i śledzenie symulowanych ataków phishingowych na określone grupy użytkowników.|

Ponadto firma Microsoft zaleca użytkownikom podjęcie działań opisanych w tym artykule: [Ochrona konta i urządzeń przed hakerami i złośliwym oprogramowaniem](https://support.microsoft.com/office/066d6216-a56b-4f90-9af3-b3a1e9a327d6). Te akcje obejmują:

- Używanie silnych haseł
- Ochrona urządzeń
- Włączanie funkcji zabezpieczeń na komputerach Windows i Mac (w przypadku urządzeń niezarządzanych)

## <a name="see-also"></a>Zobacz też

[Ogłoszenie priorytetu ochrony konta w Ochrona usługi Office 365 w usłudze Microsoft Defender](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/announcing-priority-account-protection-in-microsoft-defender-for/ba-p/1696385)
