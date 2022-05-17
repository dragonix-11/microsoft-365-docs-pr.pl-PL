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
description: Administratorzy mogą dowiedzieć się więcej o funkcjach ochrony przed wyłudzaniem informacji w Exchange Online Protection (EOP) i Ochrona usługi Office 365 w usłudze Microsoft Defender.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8d62d2a32342aa6d409e49d790af717b1ccf7d61
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438756"
---
# <a name="anti-phishing-protection-in-microsoft-365"></a>Ochrona przed wyłudzaniem informacji w Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

*Phishing* to atak e-mail, który próbuje ukraść poufne informacje w wiadomościach, które wydają się pochodzić od legalnych lub zaufanych nadawców. Istnieją określone kategorie wyłudzania informacji. Przykład:

- **Wyłudzanie informacji w spear** używa ukierunkowanej, dostosowanej zawartości, która jest specjalnie dostosowana do docelowych adresatów (zazwyczaj po rekonesansie adresatów przez osobę atakującą).

- **Wielorybnictwo** jest skierowane do kadry kierowniczej lub innych celów o wysokiej wartości w organizacji, aby uzyskać maksymalny efekt.

- **Naruszenie zabezpieczeń poczty e-mail w firmie (BEC)** używa sfałszowanych zaufanych nadawców (urzędników finansowych, klientów, zaufanych partnerów itp.), aby nakłonić odbiorców do zatwierdzania płatności, przekazywania funduszy lub ujawniania danych klientów. Dowiedz się więcej, oglądając [ten film wideo](https://www.youtube.com/watch?v=8Kn31h9HwIQ&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=2).

- **Oprogramowanie wymuszające** okup, które szyfruje dane i żąda płatności w celu ich odszyfrowania, prawie zawsze zaczyna się od wiadomości wyłudzających informacje. Ochrona przed wyłudzaniem informacji nie może pomóc w odszyfrowywaniu zaszyfrowanych plików, ale może pomóc w wykrywaniu początkowych wiadomości wyłudzających informacje skojarzonych z kampanią ransomware. Aby uzyskać więcej informacji na temat odzyskiwania po ataku wymuszającym okup, zobacz [Odzyskiwanie po ataku wymuszającym okup w Microsoft 365](recover-from-ransomware.md).

Wraz z rosnącą złożonością ataków wytrenowanym użytkownikom nawet trudno jest zidentyfikować zaawansowane wiadomości wyłudzające informacje. Na szczęście Exchange Online Protection (EOP) i dodatkowe funkcje w Ochrona usługi Office 365 w usłudze Microsoft Defender mogą pomóc.

## <a name="anti-phishing-protection-in-eop"></a>Ochrona przed wyłudzaniem informacji w ramach EOP

EOP (czyli Microsoft 365 organizacji bez Ochrona usługi Office 365 w usłudze Microsoft Defender) zawiera funkcje, które mogą pomóc chronić organizację przed zagrożeniami wyłudzania informacji:

- **Analiza fałszowania**: użyj analizy fałszowania, aby przejrzeć wykrytych sfałszowanych nadawców w komunikatach z domen zewnętrznych i wewnętrznych oraz ręcznie zezwolić lub zablokować wykrytych nadawców. Aby uzyskać więcej informacji, zobacz [Spoof intelligence insight in EOP (Fałszowanie analizy w ramach EOP](learn-about-spoof-intelligence.md)).

- **Zasady ochrony przed wyłudzaniem informacji w ramach operacji EOP**: włącza lub wyłącza analizę fałszowania, włącza lub wyłącza nieuwierzytelnione wskaźniki nadawcy w Outlook i określa akcję zablokowanych sfałszowanych nadawców. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w ramach EOP](configure-anti-phishing-policies-eop.md).

- **Zezwalaj lub blokuj sfałszowanych nadawców na liście dozwolonych/blokowych dzierżawy**: Po zastąpieniu werdyktu w analizie analizy fałszowania sfałszowany nadawca staje się ręcznym wpisem zezwalającym lub blokowym, który pojawia się tylko na karcie **Fałszowanie** na liście dozwolonych/zablokowanych dzierżawców. Możesz również ręcznie utworzyć wpisy zezwalania lub blokowania dla nadawców podszywania się, zanim zostaną wykryte przez analizę fałszowania. Aby uzyskać więcej informacji, zobacz [Manage the Tenant Allow/Block List in EOP (Zarządzanie listą dozwolonych/zablokowanych dzierżaw w ramach operacji EOP](tenant-allow-block-list.md)).

- **Niejawne uwierzytelnianie poczty e-mail**: funkcja EOP rozszerza standardowe kontrole uwierzytelniania poczty e-mail dla przychodzącej poczty e-mail ([SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) i [DMARC](use-dmarc-to-validate-email.md) z reputacją nadawcy, historią nadawcy, historią adresatów, analizą behawioralną i innymi zaawansowanymi technikami ułatwiającymi identyfikację sfałszowanych nadawców). Aby uzyskać więcej informacji, zobacz [Uwierzytelnianie za pomocą poczty e-mail w Microsoft 365](email-validation-and-authentication.md).

## <a name="additional-anti-phishing-protection-in-microsoft-defender-for-office-365"></a>Dodatkowa ochrona przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender

Ochrona usługi Office 365 w usłudze Microsoft Defender zawiera dodatkowe i bardziej zaawansowane funkcje ochrony przed wyłudzaniem informacji:

- **Zasady ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender**: skonfiguruj ustawienia ochrony przed personifikacją dla określonych domen nadawców i nadawców wiadomości, ustawień analizy skrzynki pocztowej i dostosowywalnych zaawansowanych progów wyłudzania informacji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-mdo-anti-phishing-policies.md). Aby uzyskać więcej informacji na temat różnic między zasadami ochrony przed wyłudzaniem informacji w ramach EOP i zasadami ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender, zobacz [Zasady ochrony przed wyłudzaniem informacji w Microsoft 365](set-up-anti-phishing-policies.md).
- **Widoki kampanii**: Uczenie maszynowe i inne heurystyki identyfikują i analizują komunikaty, które biorą udział w skoordynowanych atakach phishingowych na całą usługę i organizację. Aby uzyskać więcej informacji, zobacz [Widoki kampanii w Ochrona usługi Office 365 w usłudze Microsoft Defender](campaigns.md).
- **Trenowanie symulacji ataków**: administratorzy mogą tworzyć fałszywe wiadomości phishingowe i wysyłać je do użytkowników wewnętrznych jako narzędzie edukacyjne. Aby uzyskać więcej informacji, zobacz [Symulowanie ataku wyłudzania informacji](attack-simulation-training.md).

## <a name="other-anti-phishing-resources"></a>Inne zasoby chroniące przed wyłudzaniem informacji

- Dla użytkowników końcowych: [ochrona przed wyłudzaniem informacji i innymi formami oszustw online](https://support.microsoft.com/office/be0de46a-29cd-4c59-aaaf-136cf177d593).

- [Jak Microsoft 365 sprawdza poprawność adresu Od, aby zapobiec wyłudzaniu informacji](how-office-365-validates-the-from-address.md).
