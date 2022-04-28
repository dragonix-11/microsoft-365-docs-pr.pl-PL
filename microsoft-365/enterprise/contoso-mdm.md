---
title: Zarządzanie urządzeniami przenośnymi dla firmy Contoso
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Dowiedz się, jak firma Contoso używa Microsoft Intune w Microsoft 365 dla przedsiębiorstw do zarządzania urządzeniami i aplikacjami, które na nich działają.
ms.openlocfilehash: c321fc9bdaf27577e32d934aa771c92d1a0bdd79
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092696"
---
# <a name="mobile-device-management-for-contoso"></a>Zarządzanie urządzeniami przenośnymi dla firmy Contoso

Microsoft 365 dla przedsiębiorstw obejmuje Intune i zestaw usług platformy Azure, które obsługują zarządzanie urządzeniami przenośnymi i aplikacjami oraz zabezpieczenia.

Firma Contoso ma wielu pracowników z obsługą urządzeń przenośnych. Niektóre z nich mają biura w lokalizacjach firmy Contoso, a niektóre nie mają biur. Firma Contoso potrzebowała sposobu na zapewnienie produktywności pracowników, ale zapewnienie bezpieczeństwa urządzeń, danych firmy Contoso przechowywanych na tych urządzeniach i zachowania aplikacji.

## <a name="plan"></a>Plan

Firma Contoso zidentyfikowała następujące przypadki użycia Intune zarządzania urządzeniami przenośnymi dla Microsoft 365 dla przedsiębiorstw:

- Chroń Exchange Online wiadomości e-mail i dane, aby można było bezpiecznie uzyskiwać do nich dostęp przez urządzenia przenośne.
- Zaimplementuj program BYOD (bring-your-own-device) dla pracowników firmy Contoso.
- Wystawiaj pracownikom firmy Contoso telefony należące do organizacji i tablety udostępnione o ograniczonym użyciu.

Firma Contoso nie używa Intune do:

- Zezwalaj pracownikom na bezpieczny dostęp do Microsoft 365 z niezarządzanego kiosku publicznego.
- Ochrona lokalnej poczty e-mail i danych, aby można było bezpiecznie uzyskiwać do nich dostęp przez urządzenia przenośne, ponieważ nie ma lokalnych serwerów Exchange firmy Microsoft.

## <a name="deploy"></a>Wdrażanie

W ten sposób firma Contoso skonfiguruje infrastrukturę zarządzania urządzeniami przenośnymi:

- Ustaw Intune jako urząd usługi Mobile Zarządzanie urządzeniami (MDM) i użyj Intune na platformie Azure do administrowania zawartością i zarządzania urządzeniami
- Utworzono grupy Azure Active Directory (Azure AD) dla urządzeń na potrzeby rejestracji i ustawień Intune oraz zasad dostępu warunkowego opartego na urządzeniach

  Aby uzyskać więcej informacji, zobacz [Zasady dostępu warunkowego firmy Contoso](contoso-identity.md#conditional-access-policies-for-zero-trust-identity-and-device-access).

- Włączono platformę urządzeń Firmy Apple do obsługi pracowników przy użyciu tabletów iPad, komputerów iMac i iPhone oraz firmowych telefonów iPhone
- Utworzono zasady warunków i postanowień specyficznych dla firmy Contoso, które są widoczne podczas instalacji Portal firmy dla firmy Contoso na urządzeniach przenośnych
- W przypadku urządzeń, które nie są zarejestrowane, zaimplementowano zestaw zasad zarządzania aplikacjami mobilnymi (MAM) w celu wymagania uwierzytelniania w celu uzyskania dostępu do usług Microsoft 365
- Utworzono zasady Intune, które wymuszają:
  - Dozwolone aplikacje.
  - Szyfrowanie urządzenia, aby zapobiec nieautoryzowanemu dostępowi.
  - Sześciocyfrowy numer PIN lub hasło.
  - Okres braku aktywności i limitu czasu.
  - Ochrona przed oprogramowaniem antywirusowym i złośliwym oprogramowaniem oraz aktualizacje sygnatur z Windows Defender na urządzeniach Windows 10.
  - Automatyczne aktualizacje na urządzeniach Windows 10, które zawierają najnowsze aktualizacje zabezpieczeń.
  - Wypychanie certyfikatów do urządzeń zarządzanych.
  - Wyraźne rozdzielenie danych biznesowych i osobowych. Użytkownicy lub administratorzy mogą selektywnie czyścić dane firmowe z urządzenia, pozostawiając nietknięte dane osobowe, takie jak zdjęcia, osobiste konta e-mail i pliki osobiste.

Firma Contoso zarejestrowała wdrożone komputery oraz firmowe smartfony i tablety, dodając je do odpowiednich Intune grup urządzeń. Ustanowili również program BYOD dla pracowników do rejestrowania swoich urządzeń osobistych. Zarejestrowane urządzenia otrzymują zasady Intune, które powodują zarządzanie i zabezpieczanie urządzeń oraz ich aplikacji. Urządzenia, które nie są zarejestrowane, mają zasady zarządzania aplikacjami mobilnymi (MAM), które określają dozwolone aplikacje.

Oto architektura wdrażania zarządzania urządzeniami przenośnymi firmy Contoso.

![Infrastruktura wdrażania zarządzania urządzeniami przenośnymi firmy Contoso.](../media/contoso-mdm/contoso-mdm-fig1.png)

## <a name="next-step"></a>Następny krok

Dowiedz się, jak firma Contoso korzysta z [funkcji ochrony informacji](contoso-info-protect.md) Microsoft 365 dla przedsiębiorstw w celu klasyfikowania, identyfikowania i ochrony kluczowych zasobów cyfrowych w całej organizacji.

## <a name="see-also"></a>Zobacz też

[Zarządzanie urządzeniami dla Microsoft 365](device-management-roadmap-microsoft-365.md)

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Przewodniki po laboratorium testowym](m365-enterprise-test-lab-guides.md)

