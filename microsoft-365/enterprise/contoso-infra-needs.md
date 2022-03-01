---
title: Infrastruktura i potrzeby biznesowe firmy Contoso
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
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Zrozumienie podstawowej struktury lokalnej infrastruktury IT firmy Contoso i sposobu, w jaki potrzeby biznesowe firmy są spełnione Microsoft 365 przedsiębiorstwa.
ms.openlocfilehash: 94118a66f7bb1468a8f27816151a3b4d087b5703
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006543"
---
# <a name="contoso-it-infrastructure-and-business-needs"></a>Infrastruktura i potrzeby biznesowe firmy Contoso

Firma Contoso przechodzi z lokalnej scentralizowanej infrastruktury IT na konfigurację uwzględnianą w chmurze, która obejmuje osobiste obciążenia i aplikacje zwiększające produktywność w chmurze.

## <a name="existing-contoso-it-infrastructure"></a>Istniejąca infrastruktura it firmy Contoso

Firma Contoso używa głównie scentralizowanej lokalnej infrastruktury IT, która ma centra danych aplikacji w siedzibie głównej w Paryżu.

Oto biuro w siedzibie głównej z centrami danych aplikacji, DMZ i Internetem.

![Istniejąca infrastruktura it firmy Contoso.](../media/contoso-infra-needs/contoso-infra-needs-fig1.png)

Host lokalnych centrów danych aplikacji: 

- Niestandardowe aplikacje biznesowe, które korzystają z SQL Server i innych baz danych systemu Linux.
- Zestaw starszych serwerów SharePoint serwerach.
- Serwery na poziomie organizacji i zespołu do przechowywania plików.

Ponadto każdy oddział centrum regionalnego obsługuje zestaw serwerów o podobnym zestawie aplikacji. Te serwery są pod kontrolą regionalnych działów IT.

Wyszukiwanie danych i aplikacji w tych osobnych wielo geograficznych centrach danych nadal stanowi wyzwanie.

W siedzibie głównej firmy Contoso DMZ różne zestawy serwerów zapewniają:

- Hosting publicznej witryny sieci Web Contoso, z której klienci mogą zamówić produkty, części, dostawy i usługi.
- Hosting dla ekstranetu partnerów Contoso do komunikacji i współpracy partnerów.
- Zdalny dostęp wirtualny sieci prywatnej (VPN) do intranetu firmy Contoso i serwera proxy sieci Web dla pracowników w siedzibie głównej w Paryżu.

## <a name="contoso-business-needs"></a>Potrzeby biznesowe firmy Contoso

Potrzeby biznesowe firmy Contoso można podzielone na pięć głównych kategorii:

**Produktywność**

- Ułatwianie współpracy

  Zastąp współpracę za pomocą poczty e-mail i udostępniania plików modelem online, który umożliwia zmiany w czasie rzeczywistym w dokumentach, łatwiejsze spotkania online i przechwytywanie wątków konwersacji.
- Zwiększenie produktywności pracowników zdalnych i mobilnych

  Gdy wielu pracowników pracuje w domu lub w terenie, zastąp wąskie gardłem rozwiązanie sieci VPN na sprawny dostęp do danych i zasobów firmy Contoso w chmurze.
- Zwiększanie kreatywności i innowacyjności

  Skorzystaj z najnowszych metod uczenia wizualnego i opracowywania pomysłów, w tym uwierzytelniania odręcznego i wizualizacji 3D.

**Zabezpieczenia**

- Zarządzanie tożsamością i dostępem

  Wymuszaj wieloskładnikowe i inne formy uwierzytelniania oraz chroń poświadczenia konta użytkownika i administratora.

- Ochrona przed zagrożeniami

  Ochrona przed zagrożeniami bezpieczeństwa zewnętrznego, w tym wiadomościami e-mail i złośliwym oprogramowaniem systemowym.

- Ochrona informacji

  Blokowanie dostępu do zasobów cyfrowych o wysokiej wartości, takich jak dane klientów, specyfikacje dotyczące projektu i produkcji oraz informacje o pracownikach, oraz szyfrowanie tych zasobów.

- Zarządzanie zabezpieczeniami

  Monitoruj stan zabezpieczeń oraz wykrywaj zagrożenia i odpowiadaj na nie w czasie rzeczywistym.

**Dostęp zdalny i mobilny oraz partnerzy biznesowi**

- Poprawa zabezpieczeń pracowników zdalnych i mobilnych

  Wdrożenie własnego urządzenia (BYOD) i firmowego zarządzania urządzeniami w celu zapewnienia zabezpieczonego dostępu, prawidłowego działania aplikacji i firmowej ochrony danych.

- Zmniejszanie infrastruktury dostępu zdalnego dla pracowników

  Przenoszenie często używanych zasobów do chmury pozwala obniżyć koszty konserwacji i obsługi technicznej oraz zwiększyć wydajność rozwiązania do dostępu zdalnego.

- Lepsza łączność i mniejsze obciążenie związane z transakcjami między firmami (B2B)

  Zastąp starzejący się i kosztowny ekstranet partnera rozwiązaniem opartym na chmurze, które korzysta z uwierzytelniania federjącego.

**Zgodność**

- Należy przestrzegać regionalnych wymagań prawnych

  Zapewnij zgodność z branżą i przepisami regionalnymi dotyczącymi przechowywania, szyfrowania, prywatności danych i przepisów dotyczących danych osobowych, takich jak Ogólne Rozporządzenie o Ochronie Danych (RODO) dla Unii Europejskiej.

**Zarządzanie**

- Niższe obciążenie systemu IT związane z zarządzaniem oprogramowaniem uruchomionym na komputerach i urządzeniach klienckich

  Zautomatyzuj instalowanie aktualizacji Windows systemu operacyjnego i Aplikacje Microsoft 365 dla przedsiębiorstw w całej organizacji.

## <a name="mapping-contoso-business-needs-to-microsoft-365-for-enterprise"></a>Mapowanie firmy Contoso na potrzeby Microsoft 365 przedsiębiorstwa

Dział it firmy Contoso ustalił następujące mapowanie potrzeb biznesowych do Microsoft 365 E5 funkcji przed wdrożeniem:


| Kategoria | Potrzeby biznesowe | Microsoft 365 produktów lub funkcji dla przedsiębiorstw |
|:-------|:-----|:-----|
| Produktywność |  |  |
|  | Ułatwianie współpracy | Microsoft Teams, SharePoint, OneDrive |
|  | Zwiększenie produktywności pracowników zdalnych i mobilnych | Microsoft 365 obciążenia pracą i danymi w chmurze |
|  | Zwiększanie kreatywności i innowacyjności | Windows Ink, Cortana w pracy, PowerPoint |
| Bezpieczeństwo |  |  |
|  | Zarządzanie & dostępem do tożsamości | Dedykowane konta administratora globalnego z uwierzytelnianiem wieloskładnikowym (MFA) usługi Azure AD i usługą Azure AD Privileged Identity Management (PIM) <br> Uwierzytelniania wieloskładnikowego dla wszystkich kont użytkowników <br> Dostęp warunkowy <br> Czytnik zabezpieczeń <br> Windows Hello <br> Windows Credential Guard |
|  | Ochrona przed zagrożeniami | Zaawansowana analiza zagrożeń <br> Windows Defender <br> Defender for Office 365 <br> Usługa Microsoft Defender dla Office 365 <br> Microsoft 365 i reagowanie na zagrożenia <br> |
|  | Ochrona informacji | Azure Information Protection <br> Ochrona przed utratą danych (DLP) <br> Windows informacji (WIP) <br> Usługa Microsoft Defender dla aplikacji w chmurze <br> Microsoft Intune |
|  | Zarządzanie zabezpieczeniami | Microsoft Defender dla chmury  <br> Windows Defender zabezpieczeń |
| Dostęp zdalny i mobilny oraz partnerzy biznesowi |  |  |
|  | Lepsze zabezpieczenia dla pracowników zdalnych i mobilnych | Microsoft Intune |
|  | Zmniejszanie infrastruktury dostępu zdalnego dla pracowników | Microsoft 365 obciążenia pracą i danymi w chmurze |
|  | Poprawa łączności i mniejsze obciążenie związane z transakcjami B2B | Uwierzytelnianie federowane i zasoby oparte na chmurze |
| Zgodność |  |  |
|  | Należy przestrzegać regionalnych wymagań prawnych | Funkcje RODO w programie Microsoft 365 |
| Zarządzanie |  |  |
|  | Niższe obciążenie systemu it związane z instalowaniem aktualizacji klientów | Windows 10 Enterprise aktualizacji <br> Aplikacje Microsoft 365 dla przedsiębiorstw aktualizacji |
||||

## <a name="next-step"></a>Następny krok

Dowiedz się więcej o sieci [lokalnej](contoso-networking.md) firmy Contoso Corporation oraz o tym, jak została zoptymalizowana pod kątem dostępu i opóźnień do Microsoft 365 opartych na chmurze.

## <a name="see-also"></a>Zobacz też

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Przewodniki laboratorium testowego](m365-enterprise-test-lab-guides.md)
