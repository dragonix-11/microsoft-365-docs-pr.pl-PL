---
title: Tożsamość firmy Contoso Corporation
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
description: W jaki sposób firma Contoso wykorzystuje tożsamość jako usługę (IDaaS) i udostępnia uwierzytelnianie w chmurze dla swoich pracowników oraz uwierzytelnianie federowane dla swoich partnerów i klientów.
ms.openlocfilehash: 1e1fb2a74c3c3b491ddfda2b0b88e4ad11926a5a
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63015963"
---
# <a name="identity-for-the-contoso-corporation"></a>Tożsamość firmy Contoso Corporation

Firma Microsoft udostępnia usługę Identity jako usługę (IDaaS) w swoich ofertach chmury za pośrednictwem usługi Azure Active Directory (Azure AD). Aby można było Microsoft 365 dla przedsiębiorstw, rozwiązanie Contoso IDaaS musiało używać swojego lokalnego dostawcy tożsamości i uwzględnić uwierzytelnianie federowane z istniejącymi zaufanymi dostawcami tożsamości innych firm.

## <a name="the-contoso-active-directory-domain-services-forest"></a>Las Usługi domenowe w usłudze Active Directory Contoso

Contoso używa pojedynczego lasu Usługi domenowe w usłudze Active Directory (AD DS) dla domeny contosocom\. z siedmioma poddomenami, po jednym dla każdego regionu świata. W siedzibie głównej, oddziałach regionalnych i oddziałach satelitarnych są dostępne kontrolery domen do lokalnego uwierzytelniania i autoryzacji.

Oto las Contoso z domenami regionalnymi dla różnych części świata, które zawierają centrum regionalne.

:::image type="content" alt-text="Las i domeny Firmy Contoso na całym świecie." source="../media/contoso-identity/contoso-identity-fig1.png" lightbox="../media/contoso-identity/contoso-identity-fig1.png":::
 
Firma Contoso postanowiła używać kont i grup w lesie contosocom\. na potrzeby uwierzytelniania i autoryzacji swoich Microsoft 365 i usług.

## <a name="the-contoso-federated-authentication-infrastructure"></a>Infrastruktura federacji uwierzytelniania firmy Contoso

Firma Contoso zezwala na:

- Klienci mogą logować się do publicznej witryny internetowej firmy za pomocą kont Microsoft, Facebook lub Google Mail.
- Dostawcy i partnerzy mogą logować się do ekstranetu partnera firmy za pomocą kont usług LinkedIn, Salesforce lub Google Mail.

Oto dmZ contosoowe zawierające publiczną witrynę sieci Web, ekstranet partnera i zestaw serwerów usług feder ogólnodostępnych Active Directory (AD FS). DMZ jest połączony z Internetem, który zawiera klientów, partnerów i usługi internetowe.

![Obsługa firmy Contoso na potrzeby uwierzytelniania federeracyjną dla klientów i partnerów.](../media/contoso-identity/contoso-identity-fig2.png)
 
Serwery usług AD FS w dmz ułatwiają uwierzytelnianie poświadczeń klienta przez dostawców tożsamości w celu uzyskania dostępu do publicznej witryny sieci Web i poświadczeń partnera w celu uzyskania dostępu do ekstranetu partnera.

Firma Contoso postanowiła zachować tę infrastrukturę i przeznaczyć ją na uwierzytelnianie klientów i partnerów. Architekci tożsamości firmy Contoso analizują konwersję tej infrastruktury na rozwiązania [B2B](/azure/active-directory/b2b/hybrid-organizations) i [B2C](/azure/active-directory-b2c/solution-articles) usługi Azure AD.

## <a name="hybrid-identity-with-password-hash-synchronization-for-cloud-based-authentication"></a>Tożsamość hybrydowa z synchronizacją skrótów haseł dla uwierzytelniania w chmurze

Firma Contoso chciała używać swojego lokalnego lasu AD DS na Microsoft 365 zasobów w chmurze. Zdecydowano się na zastosowanie synchronizacji skrótów haseł (PHS).

Funkcja PHS synchronizuje lokalne las AD DS z dzierżawą usługi Azure AD swojej subskrypcji usługi Microsoft 365 dla przedsiębiorstw, kopiując konta użytkowników i grup oraz skróty wersji haseł kont użytkowników.

Aby wykonać synchronizację katalogów, firma Contoso wdrożyła narzędzie do synchronizacji Połączenie Azure AD na serwerze w centrum danych w Paryżu.

Oto serwer, na którym jest uruchomiony program Azure AD Połączenie, który sonduje las AD DS Contoso w celu zmiany, a następnie synchronizuje te zmiany z dzierżawą usługi Azure AD.

![Infrastruktura synchronizacji katalogów PHS firmy Contoso.](../media/contoso-identity/contoso-identity-fig4.png)
 
## <a name="conditional-access-policies-for-zero-trust-identity-and-device-access"></a>Zasady dostępu warunkowego dla tożsamości zerowym zaufaniem i dostępu do urządzeń

Firma Contoso utworzyła zestaw zasad dostępu warunkowego usług Azure AD [i Intune dla](../security/office-365-security/identity-access-policies.md) trzech poziomów ochrony:

- *Ochrona punktem* początkowym dotyczy wszystkich kont użytkowników.
- *Enterprise* ochrony dotyczą kierownictwa wyższego szczebla i kadry kierowniczej wyższego szczebla.
- *Wyspecjalizowane zabezpieczenia* są stosowane do konkretnych użytkowników działów finansowych, prawnych i badawczych, którzy mają dostęp do ściśle uregulowanych danych.

Oto wynikowy zestaw zasad dostępu warunkowego i tożsamości firmy Contoso dla urządzenia.

:::image type="content" alt-text="Zasady dostępu warunkowego firmy Contoso dotyczące tożsamości i urządzenia." source="../media/contoso-identity/contoso-identity-fig5.png" lightbox="../media/contoso-identity/contoso-identity-fig5.png":::
 
## <a name="next-step"></a>Następny krok

Dowiedz się, jak firma Contoso używa swojej Microsoft Endpoint Configuration Manager sieci w celu [wdrażania](contoso-win10.md) i Windows 10 Enterprise bieżącej wersji w całej organizacji.

## <a name="see-also"></a>Zobacz też

[Wdrażanie tożsamości dla usługi Microsoft 365](deploy-identity-solution-overview.md)

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Przewodniki laboratorium testowego](m365-enterprise-test-lab-guides.md)