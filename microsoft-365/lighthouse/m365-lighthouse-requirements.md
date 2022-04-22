---
title: Wymagania dotyczące portalu Microsoft 365 Lighthouse
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
description: W przypadku dostawców usług zarządzanych uzyskaj listę wymagań dotyczących używania Microsoft 365 Lighthouse.
ms.openlocfilehash: 06d5c5bb0de76ecc8ba9fc28677f480f5f4d5561
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2022
ms.locfileid: "65023266"
---
# <a name="requirements-for-microsoft-365-lighthouse"></a>Wymagania dotyczące portalu Microsoft 365 Lighthouse

Microsoft 365 Lighthouse jest portalem administracyjnym, który ułatwia dostawcom usług zarządzanych zabezpieczanie urządzeń, danych i użytkowników na dużą skalę oraz zarządzanie nimi dla klientów małych i średnich firm (SMB).

Aby korzystać z usługi Lighthouse, dostawcy msps muszą być zarejestrowani w programie Dostawca rozwiązań w chmurze (CSP) jako odsprzedawca pośredni lub partner rozliczeń bezpośrednich.

Ponadto każda dzierżawa klienta MSP musi kwalifikować się do aplikacji Lighthouse, spełniając następujące wymagania:

- Aby można było zarządzać dzierżawą klienta, musi mieć skonfigurowany dostęp delegowany dla dostawcy usług zarządzanych (MSP).
- Musi mieć co najmniej jedną licencję Microsoft 365 Business Premium, Microsoft 365 E3 lub Windows 365 Business
- Nie może mieć więcej niż 1000 licencjonowanych użytkowników

*Uprawnienia administratora delegowanego (DAP) są wymagane do dołączenia klientów do usługi Lighthouse. Zalecamy również ustanowienie szczegółowych uprawnień administratora delegowanego (GDAP) z klientami, aby umożliwić bezpieczniejszy dostęp delegowany. Chociaż dap i GDAP współistnieją, GDAP będzie mieć pierwszeństwo dla klientów, gdzie oba modele są w miejscu. Wkrótce klienci z zaledwie GDAP (i bez dap) będą mogli dołączyć do lighthouse.

## <a name="requirements-for-enabling-device-management"></a>Wymagania dotyczące włączania zarządzania urządzeniami

Aby wyświetlić urządzenia dzierżawy klienta na stronach zarządzania urządzeniami, msp musi:

- Zarejestruj wszystkie urządzenia klienta w Microsoft Endpoint Manager (MEM). Aby uzyskać więcej informacji, zobacz [Rejestrowanie urządzeń w Microsoft Intune](/mem/intune/enrollment/).
- Przypisz zasady zgodności do wszystkich urządzeń klientów. Aby uzyskać więcej informacji, zobacz [Tworzenie zasad zgodności w Microsoft Intune](/mem/intune/protect/create-compliance-policy).

## <a name="requirements-for-enabling-user-management"></a>Wymagania dotyczące włączania zarządzania użytkownikami

Aby dane klientów były wyświetlane w raportach na stronach zarządzania użytkownikami, w tym ryzykownych użytkowników, uwierzytelnianie wieloskładnikowe i resetowanie hasła, dzierżawcy klienta muszą mieć licencje na Azure Active Directory — wersja Premium P1 lub nowsze. Azure AD — wersja Premium P1 jest dołączony do Microsoft 365 Business Premium i Microsoft 365 E3.

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
