---
title: Zarządzanie Microsoft 365 hasłami do kont użytkowników
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Dowiedz się, jak zarządzać hasłami Microsoft 365 użytkowników.
ms.openlocfilehash: 6a0d4298f3d6c46ab067795bccf01123605ce1aa
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977609"
---
# <a name="manage-microsoft-365-user-account-passwords"></a>Zarządzanie Microsoft 365 hasłami do kont użytkowników

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Hasłami do Microsoft 365 użytkownika można zarządzać na kilka różnych sposobów, w zależności od konfiguracji tożsamości. Kontami użytkowników można zarządzać w centrum [centrum administracyjne platformy Microsoft 365](/admin), Usługi domenowe w usłudze Active Directory (AD DS) lub w centrum administracyjnym usługi Azure Active Directory (Azure AD).

## <a name="plan-for-where-and-how-you-will-manage-your-user-account-passwords"></a>Planowanie miejsca i sposobu zarządzania hasłami do konta użytkownika

Miejsce i sposób zarządzania kontami użytkowników zależy od modelu tożsamości, którego chcesz używać na Microsoft 365. Oba modele są oparte tylko na chmurze i hybrydowe.
  
### <a name="cloud-only"></a>Tylko w chmurze

Hasłami do konta użytkownika zarządza się w:

- [The centrum administracyjne platformy Microsoft 365](/admin)
- Centrum administracyjne usługi Azure AD
    
### <a name="hybrid"></a>Hybrydowe

Dzięki tożsamości hybrydowej hasła są przechowywane w AD DS, więc do zarządzania hasłami kont użytkowników należy używać lokalnych narzędzi AD DS użytkowników. Nawet w przypadku korzystania z funkcji synchronizacji skrótów haseł (PHS), w której usługa Azure AD przechowuje już skróty wersji już z hasztagami w programie AD DS, Ty i użytkownicy możecie zarządzać hasłami w AD DS.

[Zapisując hasło](#pw_writeback), użytkownicy mogą zmieniać swoje hasła AD DS azure AD.

## <a name="prevent-bad-passwords"></a>Zapobieganie złym hasłom

Wszyscy użytkownicy powinni tworzyć hasła do swoich kont użytkowników za pomocą wskazówek firmy [Microsoft](https://www.microsoft.com/research/publication/password-guidance) dotyczących haseł.

Aby uniemożliwić użytkownikom tworzenie łatwego do ustalenia hasła, użyj usługi Azure AD Password Protection, która używa zarówno globalnej listy zablokowanych haseł, jak i opcjonalnej niestandardowej listy zablokowanych haseł, którą możesz określić. Możesz na przykład określić terminy specyficzne dla Twojej organizacji, takie jak:

- Nazwy marek
- Nazwy produktów
- Lokalizacje (na przykład siedziba firmy)
- Postanowienia wewnętrzne dotyczące konkretnej firmy
- Skróty, które mają określone znaczenie firmowe

Możesz zakazać złych haseł [w chmurze](/azure/active-directory/authentication/concept-password-ban-bad) i dla użytkowników [lokalnych, AD DS](/azure/active-directory/authentication/concept-password-ban-bad-on-premises).

## <a name="simplify-user-sign-in"></a>Upraszczanie logowania użytkownika

Bezproblemowe logowanie jednokrotne w usłudze Azure Sign-On AD (bezproblemowe logowanie jednokrotne usługi Azure AD) współpracuje z uwierzytelnianiem PTA (PHS) i usługą Pass-Through, aby umożliwić użytkownikom logowanie się do usług, które korzystają z kont użytkowników usługi Azure AD, bez konieczności wpisywania haseł, a w wielu przypadkach także ich nazw użytkowników. Zapewnia to Twoim użytkownikom łatwiejszy dostęp do aplikacji opartych na chmurze, takich jak Office 365, bez konieczności wytłaniania żadnych dodatkowych lokalnych składników, takich jak serwery federujące tożsamości.

Bezproblemowe logowanie jednokrotne usługi Azure AD jest konfigurowane za pomocą narzędzia do logowania jednokrotnego Połączenie Azure AD. Zobacz [instrukcje dotyczące konfigurowania bezproblemowego logowania jednokrotnego usługi Azure AD](/azure/active-directory/connect/active-directory-aadconnect-sso-quick-start).

<a name="pw_writeback"></a>
## <a name="simplify-password-updates-to-ad-ds"></a>Upraszczaj aktualizacje haseł AD DS

Dzięki zapisywaniu hasła możesz zezwolić użytkownikom na resetowanie ich haseł za pośrednictwem usługi Azure AD, która jest następnie replikowana do AD DS. Użytkownicy nie muszą mieć dostępu do swoich lokalnych AD DS, aby zaktualizować swoje hasła. Jest to przydatne dla użytkowników mobilnych lub zdalnych, którzy nie mają połączenia dostępu zdalnego z siecią lokalną.

Aby w pełni korzystać z funkcji usługi Azure AD Identity Protection, takich jak wymaganie od użytkowników zmiany haseł lokalnych w przypadku wykrycia wysokiego ryzyka naruszenia konta, jest wymagane zwrotne pisanie haseł.

Aby uzyskać dodatkowe informacje i instrukcje konfiguracji, zobacz Usługa [Azure AD SSPR z zapisem hasła](/azure/active-directory/active-directory-passwords-writeback).

>[!Note]
>Uaktualnij usługę Azure AD do najnowszej wersji Połączenie, aby zapewnić najlepsze możliwe środowisko i nowe funkcje w miarę ich wersji. Aby uzyskać więcej informacji, zobacz [Niestandardowa instalacja usługi Azure AD Połączenie](/azure/active-directory/connect/active-directory-aadconnect-get-started-custom).
>

## <a name="simplify-password-resets"></a>Upraszczanie resetowania hasła

Funkcja samodzielnego resetowania hasła (SSPR) pozwala użytkownikom resetować i odblokowywać swoje hasła lub konta. Aby ostrzegać Cię o błędach lub nadużyciach, możesz skorzystać ze szczegółowego raportowania, które śledzi dostęp użytkowników do systemu, wraz z powiadomieniami. Aby wdrożyć [resetowanie hasła](#pw_writeback) , należy włączyć funkcję zapisu hasła.

Zobacz [instrukcje dotyczące wycofywania resetowania hasła](/azure/active-directory/authentication/howto-sspr-deployment).