---
title: Infrastruktura IT i potrzeby biznesowe firmy Contoso
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
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Poznaj podstawową strukturę lokalnej infrastruktury IT firmy Contoso oraz sposób zaspokajania potrzeb biznesowych firmy przez Microsoft 365 dla przedsiębiorstw.
ms.openlocfilehash: 5dc47898aa0499bc4b62d22d37689d872116a9e7
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101364"
---
# <a name="contoso-it-infrastructure-and-business-needs"></a>Infrastruktura IT i potrzeby biznesowe firmy Contoso

Firma Contoso przechodzi z lokalnej, scentralizowanej infrastruktury IT do konfiguracji uwzględniającej chmurę, która obejmuje obciążenia i aplikacje związane z wydajnością osobistą w chmurze.

## <a name="existing-contoso-it-infrastructure"></a>Istniejąca infrastruktura IT firmy Contoso

Firma Contoso używa głównie scentralizowanej lokalnej infrastruktury IT z centrami danych aplikacji w siedzibie głównej w Paryżu.

Oto siedziba firmy z centrami danych aplikacji, DMZ i Internetem.

![Istniejąca infrastruktura IT firmy Contoso.](../media/contoso-infra-needs/contoso-infra-needs-fig1.png)

Host lokalnych centrów danych aplikacji: 

- Niestandardowe aplikacje biznesowe korzystające z SQL Server i innych baz danych systemu Linux.
- Zestaw starszych serwerów SharePoint.
- Serwery na poziomie organizacji i zespołu dla magazynu plików.

Ponadto każde regionalne biuro centrum obsługuje zestaw serwerów z podobnym zestawem aplikacji. Te serwery są pod kontrolą regionalnych działów IT.

Wyszukiwanie w aplikacjach i danych tych oddzielnych wielo geograficznych centrów danych nadal stanowi wyzwanie.

W centrum DMZ siedziby firmy Contoso różne zestawy serwerów zapewniają:

- Hosting dla publicznej witryny internetowej firmy Contoso, z której klienci mogą zamawiać produkty, części, materiały i usługi.
- Hosting dla ekstranetu partnerskiego firmy Contoso na potrzeby komunikacji i współpracy między partnerami.
- Wirtualna sieć prywatna (VPN) oparta na dostępie zdalnym do intranetu firmy Contoso i internetowego serwera proxy dla pracowników w siedzibie głównej w Paryżu.

## <a name="contoso-business-needs"></a>Potrzeby biznesowe firmy Contoso

Potrzeby biznesowe firmy Contoso dzielą się na pięć głównych kategorii:

**Wydajność**

- Ułatwianie współpracy

  Zastąp współpracę opartą na wiadomościach e-mail i udziałach plików modelem online, który umożliwia zmiany dokumentów w czasie rzeczywistym, łatwiejsze spotkania online i przechwycone wątki konwersacji.
- Zwiększanie produktywności pracowników zdalnych i mobilnych

  Wielu pracowników pracujących w domu lub w terenie zastępuje wąskie gardło rozwiązanie sieci VPN wydajnym dostępem do danych i zasobów firmy Contoso w chmurze.
- Zwiększanie kreatywności i innowacji

  Skorzystaj z najnowszych metod uczenia wizualnego i programowania pomysłów, w tym pisma odręcznego i wizualizacji 3D.

**Zabezpieczenia**

- Zarządzanie tożsamościami i dostępem

  Wymuszaj uwierzytelnianie wieloskładnikowe i inne formy uwierzytelniania oraz chroń poświadczenia konta użytkownika i administratora.

- Ochrona przed zagrożeniami

  Ochrona przed zewnętrznymi zagrożeniami bezpieczeństwa, w tym złośliwym oprogramowaniem poczty e-mail i systemu operacyjnego.

- Ochrona informacji

  Zablokuj dostęp do zasobów cyfrowych o wysokiej wartości i zaszyfruj ich wartości, takie jak dane klientów, specyfikacje projektowe i produkcyjne oraz informacje o pracownikach.

- Zarządzanie zabezpieczeniami

  Monitorowanie stanu zabezpieczeń oraz wykrywanie zagrożeń i reagowanie na nie w czasie rzeczywistym.

**Dostęp zdalny i mobilny oraz partnerzy biznesowi**

- Zwiększanie bezpieczeństwa pracowników zdalnych i mobilnych

  Zaimplementuj funkcję "przynieś własne urządzenie" (BYOD) i zarządzanie urządzeniami należącymi do firmy, aby zapewnić bezpieczny dostęp, poprawne zachowanie aplikacji i ochronę danych firmy.

- Zmniejszanie infrastruktury dostępu zdalnego dla pracowników

  Zmniejsz koszty konserwacji i obsługi technicznej oraz zwiększ wydajność rozwiązania dostępu zdalnego, przenosząc często dostępne zasoby do chmury.

- Zapewnianie lepszej łączności i mniejsze obciążenie dla transakcji typu "business-to-susiness" (B2B)

  Zastąp starzejącą się i kosztowną ekstranet partnera rozwiązaniem opartym na chmurze, które korzysta z uwierzytelniania federacyjnego.

**Zgodność**

- Przestrzegaj regionalnych wymogów prawnych

  Zapewnianie zgodności z przepisami branżowymi i regionalnymi dotyczącymi przechowywania danych, szyfrowania, prywatności danych i przepisów dotyczących danych osobowych, takich jak ogólne rozporządzenie o ochronie danych (RODO) dla Unii Europejskiej.

**Zarządzanie**

- Mniejsze obciążenie it na potrzeby zarządzania oprogramowaniem uruchomionym na komputerach klienckich i urządzeniach

  Automatyzowanie instalacji aktualizacji systemu operacyjnego Windows i Aplikacje Microsoft 365 dla przedsiębiorstw w całej organizacji.

## <a name="mapping-contoso-business-needs-to-microsoft-365-for-enterprise"></a>Mapowanie potrzeb firmy Contoso do Microsoft 365 dla przedsiębiorstw

Dział IT firmy Contoso określił następujące mapowanie potrzeb biznesowych, aby Microsoft 365 E5 funkcje przed wdrożeniem:


| Kategoria | Potrzeba biznesowa | Microsoft 365 dla produktów lub funkcji przedsiębiorstwa |
|:-------|:-----|:-----|
| Wydajność |  |  |
|  | Ułatwianie współpracy | Microsoft Teams, SharePoint, OneDrive |
|  | Zwiększanie produktywności pracowników zdalnych i mobilnych | Microsoft 365 obciążeń i danych opartych na chmurze |
|  | Zwiększanie kreatywności i innowacji | Windows Ink, Cortana at Work, PowerPoint |
| Bezpieczeństwo |  |  |
|  | Zarządzanie dostępem & tożsamości | Dedykowane konta administratorów globalnych z usługami Azure AD Multi-Factor Authentication (MFA) i Azure AD Privileged Identity Management (PIM) <br> Uwierzytelnianie wieloskładnikowe dla wszystkich kont użytkowników <br> Dostęp warunkowy <br> Czytelnik zabezpieczeń <br> Windows Hello <br> Windows Credential Guard |
|  | Ochrona przed zagrożeniami | Zaawansowana analiza zagrożeń <br> Windows Defender <br> Ochrona usługi Office 365 w usłudze Defender <br> Ochrona usługi Office 365 w usłudze Microsoft Defender <br> Microsoft 365 badanie zagrożeń i reagowanie na nie <br> |
|  | Ochrona informacji | Azure Information Protection <br> Ochrona przed utratą danych (DLP) <br> Windows Information Protection (WIP) <br> Microsoft Defender for Cloud Apps <br> Microsoft Intune |
|  | Zarządzanie zabezpieczeniami | Microsoft Defender for Cloud  <br> Windows Defender Security Center |
| Dostęp zdalny i mobilny oraz partnerzy biznesowi |  |  |
|  | Lepsze zabezpieczenia dla pracowników zdalnych i mobilnych | Microsoft Intune |
|  | Zmniejszanie infrastruktury dostępu zdalnego dla pracowników | Microsoft 365 obciążeń i danych opartych na chmurze |
|  | Zwiększanie łączności i mniejsze obciążenie transakcji B2B | Uwierzytelnianie federacyjne i zasoby oparte na chmurze |
| Zgodność |  |  |
|  | Przestrzegaj regionalnych wymogów prawnych | Funkcje RODO w Microsoft 365 |
| Zarządzanie |  |  |
|  | Mniejsze obciążenie it na potrzeby instalowania aktualizacji klienta | aktualizacje Windows 10 Enterprise <br> aktualizacje Aplikacje Microsoft 365 dla przedsiębiorstw |
||||

## <a name="next-step"></a>Następny krok

Dowiedz się więcej [o sieci lokalnej](contoso-networking.md) firmy Contoso Corporation oraz o tym, jak została ona zoptymalizowana pod kątem dostępu i opóźnień w Microsoft 365 zasobów opartych na chmurze.

## <a name="see-also"></a>Zobacz też

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Przewodniki po laboratorium testowym](m365-enterprise-test-lab-guides.md)
