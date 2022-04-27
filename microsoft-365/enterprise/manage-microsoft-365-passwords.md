---
title: Zarządzanie hasłami Microsoft 365 konta użytkownika
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: Dowiedz się, jak zarządzać hasłami Microsoft 365 konta użytkownika.
ms.openlocfilehash: 689f88c2380f0655af70cea08404ed7163fa1239
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094399"
---
# <a name="manage-microsoft-365-user-account-passwords"></a>Zarządzanie hasłami Microsoft 365 konta użytkownika

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

W zależności od konfiguracji tożsamości można zarządzać Microsoft 365 hasłami kont użytkowników na kilka różnych sposobów. Kontami użytkowników można zarządzać w [Centrum administracyjne platformy Microsoft 365](/admin), w Active Directory Domain Services (AD DS) lub w centrum administracyjnym Azure Active Directory (Azure AD).

## <a name="plan-for-where-and-how-you-will-manage-your-user-account-passwords"></a>Planowanie miejsca i sposobu zarządzania hasłami konta użytkownika

Miejsce i sposób zarządzania kontami użytkowników zależy od modelu tożsamości, którego chcesz użyć dla Microsoft 365. Te dwa modele są tylko w chmurze i hybrydowe.
  
### <a name="cloud-only"></a>Tylko w chmurze

Hasłami kont użytkowników zarządza się w:

- [Centrum administracyjne platformy Microsoft 365](/admin)
- Centrum administracyjne usługi Azure AD
    
### <a name="hybrid"></a>Hybrydowa

W przypadku tożsamości hybrydowej hasła są przechowywane w usługach AD DS, dlatego do zarządzania hasłami kont użytkowników należy użyć lokalnych narzędzi usług AD DS. Nawet w przypadku korzystania z synchronizacji skrótów haseł (PHS), w której usługa Azure AD przechowuje wersję skrótową już skrótowej wersji w usługach AD DS, ty i użytkownicy muszą zarządzać swoimi hasłami w usługach AD DS.

Dzięki [funkcji zapisywania zwrotnego haseł](#pw_writeback) użytkownicy mogą zmieniać swoje hasła usług AD DS za pośrednictwem usługi Azure AD.

## <a name="prevent-bad-passwords"></a>Zapobieganie nieprawidłowym hasłom

Wszyscy użytkownicy powinni używać [wskazówek firmy Microsoft dotyczących haseł](https://www.microsoft.com/research/publication/password-guidance) do tworzenia haseł kont użytkowników.

Aby uniemożliwić użytkownikom tworzenie łatwo określonego hasła, użyj ochrony haseł usługi Azure AD, która używa zarówno globalnej listy zakazanych haseł, jak i opcjonalnej niestandardowej listy zakazanych haseł. Można na przykład określić terminy specyficzne dla twojej organizacji, takie jak:

- Marki
- Nazwy produktów
- Lokalizacje (na przykład siedziba firmy)
- Warunki wewnętrzne specyficzne dla firmy
- Skróty, które mają określone znaczenie firmy

Możesz zakazać używania nieprawidłowych haseł [w chmurze](/azure/active-directory/authentication/concept-password-ban-bad) i [lokalnych usług AD DS](/azure/active-directory/authentication/concept-password-ban-bad-on-premises).

## <a name="simplify-user-sign-in"></a>Uproszczenie logowania użytkownika

Bezproblemowe logowanie jedno Sign-On krotne usługi Azure AD (Azure AD Seamless SSO) współpracuje z usługami PHS i uwierzytelnianiem Pass-Through (PTA), aby umożliwić użytkownikom logowanie się do usług korzystających z kont użytkowników usługi Azure AD bez konieczności wpisywania haseł, a w wielu przypadkach ich nazw użytkowników. Zapewnia to użytkownikom łatwiejszy dostęp do aplikacji opartych na chmurze, takich jak Office 365, bez konieczności używania dodatkowych składników lokalnych, takich jak serwery federacyjne tożsamości.

Bezproblemowe logowanie jednokrotne usługi Azure AD można skonfigurować za pomocą narzędzia Połączenie usługi Azure AD. Zapoznaj [się z instrukcjami dotyczącymi konfigurowania bezproblemowego logowania jednokrotnego usługi Azure AD](/azure/active-directory/connect/active-directory-aadconnect-sso-quick-start).

<a name="pw_writeback"></a>
## <a name="simplify-password-updates-to-ad-ds"></a>Uproszczenie aktualizacji haseł w usługach AD DS

Dzięki funkcji zapisywania zwrotnego haseł można zezwolić użytkownikom na resetowanie haseł za pośrednictwem usługi Azure AD, która jest następnie replikowana do usług AD DS. Użytkownicy nie muszą uzyskiwać dostępu do lokalnych usług AD DS w celu zaktualizowania swoich haseł. Jest to przydatne dla użytkowników mobilnych lub zdalnych, którzy nie mają połączenia dostępu zdalnego z siecią lokalną.

Zapisywanie zwrotne haseł jest wymagane do pełnego wykorzystania możliwości usługi Azure AD Identity Protection, takich jak wymaganie od użytkowników zmiany haseł lokalnych w przypadku wykrycia wysokiego ryzyka naruszenia zabezpieczeń konta.

Aby uzyskać dodatkowe informacje i instrukcje konfiguracji, zobacz [Samoobsługowe resetowanie hasła w usłudze Azure AD z zapisywaniem zwrotnym haseł](/azure/active-directory/active-directory-passwords-writeback).

>[!Note]
>Uaktualnij do najnowszej wersji usługi Azure AD Połączenie, aby zapewnić najlepsze możliwe środowisko i nowe funkcje w miarę ich wdrażania. Aby uzyskać więcej informacji, zobacz [Instalacja niestandardowa usługi Azure AD Połączenie](/azure/active-directory/connect/active-directory-aadconnect-get-started-custom).
>

## <a name="simplify-password-resets"></a>Upraszczanie resetowania haseł

Samoobsługowe resetowanie haseł umożliwia użytkownikom resetowanie lub odblokowywanie haseł lub kont. Aby otrzymywać alerty o niewłaściwym lub niewłaściwym użyciu, możesz użyć szczegółowych raportów, które śledzą, kiedy użytkownicy uzyskują dostęp do systemu, wraz z powiadomieniami. Przed wdrożeniem resetowania hasła należy włączyć [funkcję zapisywania zwrotnego haseł](#pw_writeback) .

Zapoznaj się z [instrukcjami dotyczącymi wdrażania resetowania haseł](/azure/active-directory/authentication/howto-sspr-deployment).