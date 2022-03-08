---
title: Wymagania dotyczące Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: W przypadku dostawców usług zarządzanych (MSP) uzyskaj listę wymagań dotyczących Microsoft 365 Lighthouse.
ms.openlocfilehash: 51dd2404f03dc58d5975a37c386ba9c8f1333763
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327255"
---
# <a name="requirements-for-microsoft-365-lighthouse"></a>Wymagania dotyczące Microsoft 365 Lighthouse

Microsoft 365 Lighthouse to portal administracyjny, który ułatwia zarządzanym dostawcom usług (MSP) zabezpieczanie urządzeń, danych i użytkowników oraz zarządzanie nimi w skali dla klientów małych i średnich firm.  

Aby korzystać z usługi Lighthouse, msP muszą być zarejestrowani w programie Dostawca rozwiązań w chmurze (CSP) jako pośredni odsprzedawca lub bezpośredni partner ds. rachunku.  

Ponadto każda dzierżawa klienta programu MSP musi zakwalifikować się do usługi Lighthouse, spełniając następujące wymagania: 
 
- Uprawnienia administratora delegowanego (DAP, Delegated Admin Privileges) lub Szczegółowe uprawnienia administratora delegowanego (GDAP) dla programu MSP 
- Co najmniej jedna Microsoft 365 Business Premium lub Microsoft 365 E3 licencji 
- Mniej niż 1000 licencjonowanych użytkowników  

## <a name="requirements-for-enablingdevice-management"></a>Wymagania dotyczące włączania zarządzania urządzeniami

Aby wyświetlić urządzenia dzierżawy klienta na stronach zarządzania urządzeniami, program MSP musi:

- Zarejestruj wszystkie urządzenia klienta w Microsoft Endpoint Manager (MEM).Aby uzyskać więcej informacji, zobacz [Rejestrowanie urządzeń w u Microsoft Intune](/mem/intune/enrollment/).
- Przypisz zasady zgodności do wszystkich urządzeń klientów.Aby uzyskać więcej informacji, [zobacz Tworzenie zasad zgodności w programie Microsoft Intune](/mem/intune/protect/create-compliance-policy). 

## <a name="requirements-for-enabling-usermanagement"></a>Wymagania dotyczące włączania zarządzania użytkownikami 

Aby dane klienta były wyświetlane w raportach na stronach zarządzania użytkownikami, w tym w przypadku użytkowników ryzykownych, uwierzytelniania wieloskładnikowego i resetowania hasła, dzierżawy klientów muszą mieć licencje na usługę Azure Active Directory Premium P1 lub nowsze. Azure AD — wersja Premium P1 jest dołączony do Microsoft 365 Business Premium i Microsoft 365 E3.   

## <a name="requirements-for-enablingthreat-management"></a>Wymagania dotyczące włączania zarządzania zagrożeniami 

Aby wyświetlać urządzenia i zagrożenia w dzierżawie klientów na stronach zarządzania zagrożeniami, musisz zarejestrować wszystkie urządzenia dzierżawcy klienta w programie Microsoft Endpoint Manager (MEM) i chronić je, uruchamiając program Program antywirusowy Microsoft Defender.  

Aby uzyskać więcej informacji, zobacz [Rejestrowanie urządzeń w u Microsoft Intune](/mem/intune/enrollment/).  

Program antywirusowy Microsoft Defender stanowi część systemu Windows i jest domyślnie włączona na urządzeniach z systemem Windows 10.  

> [!NOTE] 
> Jeśli korzystasz z rozwiązania antywirusowego firmy innym niż Microsoft i nie Program antywirusowy Microsoft Defender, Program antywirusowy Microsoft Defender zostanie automatycznie wyłączona. Po odinstalowaniu rozwiązania antywirusowego, które nie jest Program antywirusowy Microsoft Defender firmy Microsoft, zostanie automatycznie aktywowane w celu ochrony twoich Windows przed zagrożeniami.    

## <a name="related-content"></a>Zawartość pokrewna

[Konfigurowanie Microsoft 365 Lighthouse zabezpieczeń portalu](m365-lighthouse-configure-portal-security.md) (artykuł)\
[Microsoft 365 Lighthouse strona zgodności urządzenia](m365-lighthouse-device-compliance-page-overview.md) (artykuł)\
[Microsoft 365 Lighthouse omówienie strony Użytkownicy](m365-lighthouse-users-page-overview.md) (artykuł)\
[Microsoft 365 Lighthouse zarządzanie zagrożeniami — omówienie](m365-lighthouse-threat-management-page-overview.md) (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)

