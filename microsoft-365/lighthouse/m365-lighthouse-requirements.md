---
title: Wymagania dotyczące portalu Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: crimora
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
description: W przypadku dostawców usług zarządzanych uzyskaj listę wymagań dotyczących używania Microsoft 365 Lighthouse.
ms.openlocfilehash: 27d5440b70916ebdb3b761ac4308d3b97ccb27da
ms.sourcegitcommit: f181e110cdb983788a86f30d5bb018e53c83e64d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2022
ms.locfileid: "66057779"
---
# <a name="requirements-for-microsoft-365-lighthouse"></a>Wymagania dotyczące portalu Microsoft 365 Lighthouse

Microsoft 365 Lighthouse jest portalem administracyjnym, który ułatwia dostawcom usług zarządzanych zabezpieczanie urządzeń, danych i użytkowników na dużą skalę oraz zarządzanie nimi dla klientów małych i średnich firm (SMB).

Aby korzystać z usługi Lighthouse, dostawcy msps muszą być zarejestrowani w programie Dostawca rozwiązań w chmurze (CSP) jako odsprzedawca pośredni lub partner rozliczeń bezpośrednich.

Ponadto każda dzierżawa klienta MSP musi kwalifikować się do aplikacji Lighthouse, spełniając następujące wymagania:

- Aby można było zarządzać dzierżawą klienta, musi mieć skonfigurowany dostęp delegowany dla dostawcy usług zarządzanych (MSP).
- Musi mieć co najmniej jedną licencję Microsoft 365 Business Premium, Microsoft 365 E3, Microsoft 365 E5, Windows 365 Business lub Microsoft Defender dla Firm
- Nie może mieć więcej niż 2500 licencjonowanych użytkowników

Aby dołączyć klientów do usługi Lighthouse, wymagane są szczegółowe uprawnienia administratora delegowanego (GDAP) oraz relacja pośredniego odsprzedawcy lub relacja delegowane uprawnienia administratora (DAP). Jeśli dap i GDAP współistnieją w dzierżawie klienta, uprawnienia GDAP mają pierwszeństwo dla techników MSP w grupach zabezpieczeń z obsługą protokołu GDAP. Wkrótce klienci z relacjami tylko Z GDAP (bez pośrednich relacji odsprzedawców) będą mogli dołączyć do usługi Lighthouse.

## <a name="requirements-for-enabling-device-management"></a>Wymagania dotyczące włączania zarządzania urządzeniami

Aby wyświetlić urządzenia dzierżawy klienta na stronach zarządzania urządzeniami, msp musi:

- Zarejestruj wszystkie urządzenia klienta w Microsoft Endpoint Manager (MEM). Aby uzyskać więcej informacji, zobacz [Rejestrowanie urządzeń w Microsoft Intune](/mem/intune/enrollment/).
- Przypisz zasady zgodności do wszystkich urządzeń klientów. Aby uzyskać więcej informacji, zobacz [Tworzenie zasad zgodności w Microsoft Intune](/mem/intune/protect/create-compliance-policy).

## <a name="requirements-for-enabling-user-management"></a>Wymagania dotyczące włączania zarządzania użytkownikami

Aby dane klientów były wyświetlane w raportach na stronach zarządzania użytkownikami, w tym ryzykownych użytkowników, uwierzytelnianie wieloskładnikowe i resetowanie hasła, dzierżawcy klienta muszą mieć licencje na Azure Active Directory — wersja Premium P1 lub nowsze. Azure AD — wersja Premium P1 jest dołączony do Microsoft 365 Business Premium i Microsoft 365 E3. Azure AD — wersja Premium P2 jest dołączony do Microsoft 365 E5.

## <a name="requirements-for-enabling-threat-management"></a>Wymagania dotyczące włączania zarządzania zagrożeniami

Aby wyświetlić urządzenia dzierżawy klienta i zagrożenia na stronach zarządzania zagrożeniami, należy zarejestrować wszystkie urządzenia dzierżawy klienta w Microsoft Endpoint Manager (MEM) i chronić je, uruchamiając Program antywirusowy Microsoft Defender.

Aby uzyskać więcej informacji, zobacz [Rejestrowanie urządzeń w Microsoft Intune](/mem/intune/enrollment/).

Program antywirusowy Microsoft Defender jest częścią systemu operacyjnego Windows i jest domyślnie włączona na urządzeniach z systemem Windows 10.

> [!NOTE]
> Jeśli używasz rozwiązania antywirusowego innego niż Microsoft, a nie Program antywirusowy Microsoft Defender, Program antywirusowy Microsoft Defender jest automatycznie wyłączona. Po odinstalowaniu rozwiązania antywirusowego innego niż Microsoft Program antywirusowy Microsoft Defender jest automatycznie aktywowany w celu ochrony urządzeń Windows przed zagrożeniami.

## <a name="related-content"></a>Zawartość pokrewna

[Konfigurowanie zabezpieczeń portalu Microsoft 365 Lighthouse](m365-lighthouse-configure-portal-security.md) (artykuł)\
[Omówienie strony Zgodność urządzeń w Microsoft 365 Lighthouse](m365-lighthouse-device-compliance-page-overview.md) (artykuł)\
[Omówienie strony Użytkownicy w Microsoft 365 Lighthouse](m365-lighthouse-users-page-overview.md) (artykuł)\
[Omówienie strony Zarządzanie zagrożeniami w Microsoft 365 Lighthouse](m365-lighthouse-threat-management-page-overview.md) (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)
