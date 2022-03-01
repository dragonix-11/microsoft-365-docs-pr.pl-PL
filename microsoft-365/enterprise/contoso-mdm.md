---
title: Zarządzanie urządzeniami przenośnymi dla firmy Contoso
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Dowiedz się, jak firma Contoso Microsoft Intune w Microsoft 365 dla przedsiębiorstw do zarządzania jego urządzeniami i aplikacjami, które na nich działają.
ms.openlocfilehash: dedda98083dd5a27c4c7721b5ae8e5dc1fed4bad
ms.sourcegitcommit: 07405a81513d1c63071a128b9d5070d3a3bfe1cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006584"
---
# <a name="mobile-device-management-for-contoso"></a>Zarządzanie urządzeniami przenośnymi dla firmy Contoso

Microsoft 365 dla przedsiębiorstw obejmuje usługę Intune i zestaw usług Azure, które obsługują zarządzanie urządzeniami przenośnymi i aplikacjami oraz zabezpieczenia.

Firma Contoso ma wielu pracowników z włączoną obsługą urządzeń przenośnych. Niektóre z nich mają biura w lokalizacjach firmy Contoso, a inne nie mają biur. Firma Contoso potrzebowała sposobu zapewnienia pracownikowi produktywności, ale przy zachowaniu urządzeń, danych firmy Contoso przechowywanych na tych urządzeniach oraz zachowania aplikacji.

## <a name="plan"></a>Planowanie

Firma Contoso zidentyfikował następujące przypadki zarządzania urządzeniami przenośnymi w usłudze Intune w Microsoft 365 przedsiębiorstwie:

- Chroń Exchange Online e-mail i dane, aby można było bezpiecznie uzyskiwać do nich dostęp na urządzeniach przenośnych.
- Wdrożenie programu bring-your-own-device (BYOD) dla pracowników firmy Contoso.
- Dziel się z pracownikami firmy Contoso telefonami i tabletami udostępnioni o ograniczonym użyciu.

Firma Contoso nie używa usługi Intune do:

- Umożliwia pracownikom bezpieczny dostęp do Microsoft 365 z niezamówionych publicznych kiosków.
- Chroń lokalną pocztę e-mail i dane, aby były one bezpiecznie dostępne na urządzeniach przenośnych, ponieważ nie ma żadnych lokalnych serwerów Exchange firmy Microsoft.

## <a name="deploy"></a>Wdrażanie

W ten sposób firma Contoso skonfiguruje swoją infrastrukturę zarządzania urządzeniami przenośnymi:

- Ustaw usługę Intune jako urząd zarządzania urządzeniami przenośnymi (MDM), a za pomocą usługi Intune na platformie Azure zarządzaj zawartością i urządzeniami
- Utworzono Azure Active Directory (Azure AD) dla urządzeń do rejestracji, ustawień usługi Intune i zasad dostępu warunkowego opartych na urządzeniach

  Aby uzyskać więcej informacji, zobacz [Zasady dostępu warunkowego firmy Contoso](contoso-identity.md#conditional-access-policies-for-zero-trust-identity-and-device-access).

- Włączono platformę urządzeń firmy Apple, aby wspierać pracowników za pomocą tabletów iPad, komputerów iMac i telefonów iPhone oraz telefonów iPhone należących do firmy
- Utworzono zasady dotyczące warunków i postanowień specyficznych dla firmy Contoso, które są widoczne podczas instalacji pakietu Portal firmy dla firmy Contoso na urządzeniach przenośnych
- W przypadku urządzeń, które nie zostały zarejestrowane, zaimplementowano zestaw zasad zarządzania aplikacjami przenośnymi (MAM), aby wymagać uwierzytelniania na Microsoft 365 usługach mobilnych
- Utworzono zasady usługi Intune wymuszane:
  - Dozwolone aplikacje.
  - Szyfrowanie urządzeń w celu zapobiegania nieautoryzowanemu dostępowi.
  - Sześciocyfrowy numer PIN lub hasło.
  - Okres braku aktywności.
  - Ochrona antywirusowa i złośliwego oprogramowania oraz aktualizacje podpisu Windows Defender na Windows 10 urządzeniach.
  - Aktualizacje automatyczne na Windows 10, które zawierają najnowsze aktualizacje zabezpieczeń.
  - Wypychanie certyfikatów na urządzenia zarządzane.
  - Przejrzyste wyciągi danych służbowych i osobistych. Użytkownicy lub administratorzy mogą selektywnie wyczyścić dane firmowe z urządzenia, pozostawiając bez zmian dane osobiste, takie jak obrazy, osobiste konta e-mail i pliki osobiste.

Firma Contoso wdrożyła komputery PC oraz firmowe smartfony i tablety, dodając je do odpowiednich grup urządzeń usługi Intune. Nawiązyli oni również program BYOD, który umożliwia pracownikom zarejestrowanie swoich osobistych urządzeń. Zarejestrowane urządzenia otrzymują zasady usługi Intune, co skutkować zastosowaniem urządzeń zarządzanych i zabezpieczonych oraz ich aplikacji. Urządzenia, które nie zostały zarejestrowane, mają zasady zarządzania aplikacjami mobilnymi (MAM), które określają dozwolone aplikacje.

Oto architektura wdrażania firmy Contoso dla urządzeń przenośnych.

![Infrastruktura wdrażania urządzeń przenośnych firmy Contoso.](../media/contoso-mdm/contoso-mdm-fig1.png)

## <a name="next-step"></a>Następny krok

Dowiedz się, jak firma Contoso używa funkcji [ochrony](contoso-info-protect.md) informacji firmy Microsoft 365 dla przedsiębiorstw do klasyfikowania, identyfikowania i ochrony ważnych zasobów cyfrowych w organizacji.

## <a name="see-also"></a>Zobacz też

[Zarządzanie urządzeniami dla Microsoft 365](device-management-roadmap-microsoft-365.md)

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Przewodniki laboratorium testowego](m365-enterprise-test-lab-guides.md)

