---
title: Przeglądanie uprawnień administracyjnych partnera
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
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
description: Dowiedz się, jak przejrzeć listę certyfikowanych przez firmę Microsoft dostawców rozwiązań (partnerów), aby określić, jakie mają uprawnienia administratora i jak usunąć te uprawnienia.
ms.date: 12/03/2021
ms.openlocfilehash: eefbe2c8b70afee9c1e24e4335a73488906bf844
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490702"
---
# <a name="review-microsoft-certified-cloud-solution-provider-partner-administrative-privileges"></a>Zapoznaj się z uprawnieniami administracyjnymi partnera dostawcy rozwiązań w chmurze certyfikowanych przez firmę Microsoft

Jeśli masz certyfikowanego przez firmę Microsoft dostawcę rozwiązań w chmurze (partnera odsprzedawcy), zalecamy przeprowadzenie kwartalnego przeglądu delegowanych uprawnień administracyjnych (DAP) przypisanych do nich. Upewnij się, że Twoja organizacja chce, aby ten partner miał dostęp do danych organizacji i dokonywać zakupów w Twoim imieniu.

> [!IMPORTANT]
> Udzielenie dap, które obejmują uprawnienia administratora globalnego, każdemu partnerowi może stanowić zagrożenie dla bezpieczeństwa. Zbyt wielu administratorów globalnych jest również zagrożeniem dla bezpieczeństwa. [Dowiedz się więcej na temat ostatnich działań ukierunkowanych na delegowane uprawnienia](https://www.microsoft.com/security/blog/2021/10/25/nobelium-targeting-delegated-administrative-privileges-to-facilitate-broader-attacks/).

Po zaakceptowaniu umowy DAP od partnera odsprzedawcy mogą oni przypisać rolę administratora globalnego twojej organizacji do swoich pracowników. Rola administratora globalnego zapewnia pracownikom partnera dostęp do danych osobowych pracowników i innych poufnych informacji. Daje im to również uprawnienia do podejmowania akcji w całej dzierżawie, takich jak następujące akcje:

- Zmienianie haseł użytkowników
- Dodawanie użytkowników przy użyciu kont e-mail
- Dodawanie domen internetowych skojarzonych z organizacją i zarządzanie nimi

Po włączeniu protokołu DAP nie masz kontroli nad liczbą administratorów globalnych, których partner może dodać. Możesz udzielić lub odmówić dostępu partnera dap (administrator globalny) do konta.

## <a name="review-and-remove-roles-from-partners"></a>Przeglądanie i usuwanie ról od partnerów

1. W Centrum administracyjne platformy Microsoft 365 przejdź do strony **Ustawienia** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2074649" target="_blank">relacji partnerów</a>. Partnerzy z dap mają **administratora globalnego** wymienione w kolumnie **Role** .
2. Aby usunąć rolę administratora globalnego z partnera, znajdź nazwę partnera, którego chcesz usunąć.
3. Wybierz wiersz z **odsprzedawcą** jako **typ relacji**.
4. Na stronie szczegółów partnera wybierz pozycję **Usuń role**, a następnie wybierz pozycję **Tak**.

> [!NOTE]
>
> - Jeśli usuniesz rolę administratora globalnego (DAP) z partnera, zalecamy skontaktowanie się z nim w celu omówienia przyszłego dostarczania usługi. Możesz na przykład utworzyć konto użytkownika z niższymi uprawnieniami i udostępnić te informacje o koncie partnerowi. Dowiedz się więcej o [dodawaniu użytkowników](../admin/add-users/add-users.md) i [przypisywaniu ról administratora](../admin/add-users/assign-admin-roles.md).
> - Nawet po usunięciu roli administratora globalnego partner może nadal dokonywać zakupów w Twoim imieniu. Zalecamy skontaktowanie się z partnerem, aby poprosić go o usunięcie tej możliwości w Centrum partnerskim.

## <a name="related-content"></a>Zawartość pokrewna

[Zarządzanie relacjami z partnerami](manage-partners.md) (artykuł)\
[Informacje o rolach administratora](../admin/add-users/about-admin-roles.md) (artykuł)\
[Delegowane uprawnienia administratora w Azure AD](/partner-center/customers-revoke-admin-privileges#delegated-admin-privileges-in-azure-ad) (artykuł)
