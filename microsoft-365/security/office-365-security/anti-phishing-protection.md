---
title: Ochrona przed wyłudzaniem informacji
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 75af74b2-c7ea-4556-a912-8c48e07271d3
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- TopSMBIssues
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się więcej o funkcjach ochrony przed wyłudzaniem informacji w programach Exchange Online Protection (EOP) i Microsoft Defender for Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 81cd2870ff3471fbd535415229b3ced20bba1fbf
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "62998801"
---
# <a name="anti-phishing-protection-in-microsoft-365"></a>Ochrona przed wyłudzaniem informacji w programie Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

*Wyłudzanie* informacji jest atakiem poczty e-mail, który próbuje ukraść poufne informacje w wiadomościach, które wydają się pochodzić od zaufanych lub zaufanych nadawców. Istnieją określone kategorie wyłudzania informacji. Przykład:

- **W wyłudzaniu** informacji używana jest specyficzna, dostosowana zawartość, która jest specjalnie dostosowana do docelowych adresatów (zwykle jest to po rozpoznaniu adresatów przez atakującego).

- **Whaling** jest przeznaczony dla kadry kierowniczej lub innych celów o wysokiej wartości w organizacji, aby osiągnąć maksymalny efekt.

- W przypadku biznesowego naruszenia zabezpieczeń poczty e-mail (**BEC, Business Email Compromise)** użyto u zaufanych nadawców (dla klientów, klientów, zaufanych partnerów itp.), aby nakłaniać adresatów do zatwierdzania płatności, przenoszenia środków lub ujawniania danych klientów. Dowiedz się więcej, oglądając [ten klip wideo](https://www.youtube.com/watch?v=8Kn31h9HwIQ&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=2).

- **Oprogramowanie wymuszające** okup, które szyfruje dane i żąda płatności w celu odszyfrowania ich prawie zawsze zaczyna się od wiadomości wyłudzających informacje. Ochrona przed wyłudzaniem informacji nie może ułatwić odszyfrowywania zaszyfrowanych plików, ale może pomóc w wykryciu początkowych wiadomości wyłudzających informacje, które są skojarzone z kampanią oprogramowania wymuszającego okup. Aby uzyskać więcej informacji na temat odzyskiwania po atakach oprogramowania wymuszającego okup, zobacz Odzyskiwanie po atakach oprogramowania [wymuszającego okup w programie Microsoft 365](recover-from-ransomware.md).

Wraz z coraz większą złożonością ataków przeszkolone użytkownikom mogą identyfikować zaawansowane wiadomości służące do wyłudzania informacji. Na szczęście Exchange Online Protection (EOP) i dodatkowe funkcje programu Microsoft Defender dla systemu Office 365 mogą pomóc.

## <a name="anti-phishing-protection-in-eop"></a>Ochrona przed wyłudzaniem informacji w uchcie EOP

Usługa EOP (czyli organizacje, Microsoft 365 bez programu Microsoft Defender dla systemu Office 365) zawiera funkcje, które pomagają chronić twoją organizację przed zagrożeniami wyłudzania informacji:

- **Fałszerość**: Używaj szczegółowych informacji o analizie podszywających się pod nadawców, aby przeglądać wykrytych fałszywych nadawców w wiadomościach z domen zewnętrznych i wewnętrznych oraz ręcznie zezwalać na wykrytych nadawców lub zablokować ich. Aby uzyskać więcej informacji, zobacz [Spoof intelligence insight in EOP (Spoof intelligence insight in EOP](learn-about-spoof-intelligence.md)).

- Zasady ochrony przed wyłudzaniem informacji w uchwale **EOP**: Włączanie lub wyłączanie ochrony przed fałszerami, włączanie i wyłączanie identyfikacji nieuwierzytanych nadawców w programie Outlook oraz określanie akcji dla zablokowanych sfałszowanych nadawców. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w u usługi EOP](configure-anti-phishing-policies-eop.md).

- Zezwalanie na spoofed nadawców lub blokowanie ich na liście zezwalania **/** blokowania dzierżawy: Gdy zastąpisz werdykt w analizie fałszowania, fałszywy nadawca stanie się ręcznym wpisem zezwalania lub blokowania, który pojawia się tylko na karcie Fałsz na liście zezwalania/blokowania dzierżawy. Możesz również ręcznie utworzyć zezwalanie na nadawców lub blokować ich wpisy podszywają się pod nadawców, zanim zostaną one wykryte przez sfałszowaną inteligencję. Aby uzyskać więcej informacji, zobacz [Zarządzanie listą zezwalania/blokowania dzierżawy w u usługi EOP](tenant-allow-block-list.md).

- Niejawne uwierzytelnianie wiadomości e-mail **: Program** EOP rozszerza możliwości standardowych testów uwierzytelniania poczty e-mail dla poczty przychodzącej ([SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) i [DMARC](use-dmarc-to-validate-email.md) z reputacją nadawcy, historią nadawcy, historią adresatów, analizą zachowania i innymi zaawansowanymi technikami, które ułatwiają identyfikowanie nadawców pozyskanych). Aby uzyskać więcej informacji, zobacz [Uwierzytelnianie pocztą e-mail w programie Microsoft 365](email-validation-and-authentication.md).

## <a name="additional-anti-phishing-protection-in-microsoft-defender-for-office-365"></a>Dodatkowa ochrona przed wyłudzaniem informacji w programie Microsoft Defender dla Office 365

Program Microsoft Defender for Office 365 zawiera dodatkowe i bardziej zaawansowane funkcje ochrony przed wyłudzaniem informacji:

- **Zasady ochrony przed wyłudzaniem** informacji w programie Microsoft Defender dla Office 365: Konfigurowanie ustawień ochrony przed personifikacji dla określonych nadawców i domen nadawców wiadomości, ustawień analizy skrzynek pocztowych i dostosowywanych zaawansowanych progów wyłudzania informacji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla Office 365](configure-mdo-anti-phishing-policies.md). Aby uzyskać więcej informacji na temat różnic między zasadami ochrony przed wyłudzaniem informacji w u usługi EOP a zasadami ochrony przed wyłudzaniem informacji w programie Defender dla programu Office 365, zobacz Zasady ochrony przed wyłudzaniem informacji w [programie Microsoft 365](set-up-anti-phishing-policies.md).
- **Widoki kampanii**: Uczenie maszynowe i inne narzędzia heuristyczne identyfikują i analizują wiadomości, które są związane ze skoordynowanymi atakami wyłudzania informacji w całej usłudze i organizacji. Aby uzyskać więcej informacji, zobacz [Widoki kampanii w programie Microsoft Defender dla Office 365](campaigns.md).
- **Szkolenie symulacyjne w** zakresie ataków: administratorzy mogą tworzyć fałszywe wiadomości wyłudzania informacji i wysyłać je do użytkowników wewnętrznych jako narzędzie edukacyjne. Aby uzyskać więcej informacji, zobacz [Symulowanie ataku służącego do wyłudzania informacji](attack-simulation-training.md).

## <a name="other-anti-phishing-resources"></a>Inne zasoby ochrony przed wyłudzaniem informacji

- Dla użytkowników końcowych: Chroń [się przed wyłudzaniem informacji i innymi oszustwami internetowymi](https://support.microsoft.com/office/be0de46a-29cd-4c59-aaaf-136cf177d593).

- [Jak Microsoft 365 sprawdza adres Od, aby zapobiec wyłudzaniu informacji](how-office-365-validates-the-from-address.md).
