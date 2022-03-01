---
title: Przejrzyj uprawnienia administracyjne partnerów
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: jamitche, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
search.appverid: MET150
description: Dowiedz się, jak przejrzeć listę certyfikowanych przez firmę Microsoft dostawców rozwiązań (partnerów), aby ustalić, jakie uprawnienia administratora mają, i jak usunąć te uprawnienia.
ms.date: 12/03/2021
ms.openlocfilehash: 7dc0a52526da1f0da9cd85b438b6f30b798c2dfa
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996273"
---
# <a name="review-partner-administrative-privileges"></a>Przejrzyj uprawnienia administracyjne partnerów

Jeśli masz certyfikowanego przez firmę Microsoft dostawcę rozwiązań w chmurze (odsprzedawcę), zalecamy przeprowadzenie kwartalnego przeglądu przypisanych im delegowanych uprawnień administracyjnych .DAP. Upewnij się, że Twoja organizacja chce, aby ten partner miał dostęp do danych Twojej organizacji i do zakupów w Twoim imieniu.

> [!IMPORTANT]
> Udzielenie dowolnego partnerowi programu DAP, czyli uprawnień administratora globalnego, może stanowić zagrożenie bezpieczeństwa. Zbyt wielu administratorów globalnych może stanowić również zagrożenie bezpieczeństwa. [Dowiedz się więcej o uprawnieniach delegowanych w celu kierowania ostatniej aktywności](https://www.microsoft.com/security/blog/2021/10/25/nobelium-targeting-delegated-administrative-privileges-to-facilitate-broader-attacks/).

Gdy zaakceptujesz umowę daP od partnera odsprzedawcy, będzie mieć możliwość przypisania roli administratora globalnego Twojej organizacji do swoich pracowników. Rola administratora globalnego zapewnia pracownikom tego partnera dostęp do danych osobistych i innych informacji poufnych. Ponadto nadaje mu uprawnienia do działań w ramach całej dzierżawy, takich jak:

- Zmienianie haseł użytkowników
- Dodawanie użytkowników z kontami e-mail
- Dodawanie domen sieci Web skojarzonych z organizacją i zarządzanie nimi

Gdy funkcja DAP jest włączona, nie masz kontroli nad liczbą administratorów globalnych, których może dodać Twój partner. Możesz tylko udzielić lub odrzucić dostępu do konta przez partnera dap (administratora globalnego).

## <a name="review-and-remove-roles-from-partners"></a>Przeglądanie ról partnerów i usuwanie ich

1. W centrum administracyjne platformy Microsoft 365 przejdź do strony relacje strony **Ustawienia** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2074649" target="_blank">Partner</a>. Partnerzy z programem DAP **mają administratora globalnego** na liście w kolumnie **Role** .
2. Aby usunąć rolę administratora globalnego partnera, znajdź nazwę partnera, którego chcesz usunąć.
3. Wybierz wiersz z typem **relacji Reseller****.**
4. Na stronie szczegółów partnera wybierz pozycję Usuń **role**, a następnie wybierz pozycję **Tak**.

> [!NOTE]
>
> - Jeśli usuniesz z partnera rolę administratora globalnego daP, zalecamy skontaktowanie się z nim w celu omówienia przyszłego dostarczania usług. Na przykład możesz utworzyć konto użytkownika z niższymi uprawnieniami i udostępnić te informacje o koncie partnerowi. Dowiedz się więcej o [dodawaniu użytkowników](../admin/add-users/add-users.md) i [przypisywaniu ról administratora](../admin/add-users/assign-admin-roles.md).
> - Nawet po usunięciu roli administratora globalnego partner nadal może dokupić Twoje konto. Zalecamy skontaktowanie się z partnerem w celu usunięcia tej możliwości w Centrum partnerskim.

## <a name="related-content"></a>Zawartość pokrewna

[Zarządzanie relacjami partnerów](manage-partners.md) (artykuł)\
[Role administratorów](../admin/add-users/about-admin-roles.md) (artykuł)\ Informacje
[Uprawnienia administratora delegowanego w usłudze Azure AD](/partner-center/customers-revoke-admin-privileges#delegated-admin-privileges-in-azure-ad) (artykuł)
