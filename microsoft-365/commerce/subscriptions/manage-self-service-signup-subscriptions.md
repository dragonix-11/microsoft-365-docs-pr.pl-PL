---
title: Zarządzanie subskrypcjami z możliwością samodzielnego rejestracji
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: jkinma, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
- AdminSurgePortfolio
search.appverid: MET150
description: Dowiedz się, jak zarządzać bezpłatnymi subskrypcjami samodzielnego rejestracji w organizacji.
ms.date: 03/17/2021
ms.openlocfilehash: be93a09ca63a4ee24945438be59b725e7d41911c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328389"
---
# <a name="manage-self-service-sign-up-subscriptions"></a>Zarządzanie subskrypcjami z możliwością samodzielnego rejestracji

## <a name="what-are-self-service-sign-up-subscriptions"></a>Co to są subskrypcje do samodzielnego rejestracji?

Istnieje ograniczona liczba bezpłatnych subskrypcji do samodzielnego rejestracji, w ramach których użytkownicy w Twojej organizacji mogą samodzielnie je zarejestrować. Użytkownik może samodzielnie utworzyć konto i korzystać z własnej subskrypcji. Samodzielne rejestracje można samodzielnie zarejestrować. Aby uzyskać więcej informacji na temat samodzielnego rejestracji i dostępnych subskrypcji, zobacz Korzystanie z funkcji samodzielnego rejestracji [w organizacji](../../admin/misc/self-service-sign-up.md).

## <a name="view-a-list-of-self-service-sign-up-subscriptions"></a>Wyświetlanie listy subskrypcji z samodzielnym logowaniem

1. W centrum administracyjnym przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">RozliczeniaZgody</a>  >  produktów.
2. Na karcie **Produkty** wybierz ikonę filtru, a następnie wybierz pozycję **Bezpłatna**. Zostanie wyświetlona lista wszystkich subskrypcji w ramach samodzielnego rejestracji.

## <a name="how-are-these-subscriptions-different-from-self-service-purchase-subscriptions"></a>Czym różnią się te subskrypcje od subskrypcji zakupu samoobsługowego?

Samodzielne subskrypcje są bezpłatne i są dostępne dla większej listy produktów niż subskrypcje zakupu samoobsługowego. Gdy użytkownik załozył konto w ramach subskrypcji zakupu samoobsługowego, odpowiada za niego. Subskrypcje zakupu samoobsługowego są dostępne tylko dla produktów platformy Power (Power BI, Power Apps i Power Automate), Project i Visio. Aby uzyskać więcej informacji, zobacz [Często zadawane pytania dotyczące zakupu samoobsługi](self-service-purchase-faq.yml).

## <a name="block-users-from-signing-up"></a>Blokowanie użytkownikom rejestracji

Za pomocą polecenia cmdlet [**Set-MsolCompanySettings**](/powershell/module/msonline/set-msolcompanysettings?preserve-view=true&view=azureadps-1.0) z parametrem **AllowAdHocSubscriptions** można kontrolować, czy użytkownicy mogą samodzielnie utworzyć konta w ramach subskrypcji usługi self-sign-up. Aby uzyskać więcej informacji, [zobacz Jak kontrolować ustawienia samoobsługi?](/azure/active-directory/users-groups-roles/directory-self-service-signup#how-do-i-control-self-service-settings)

## <a name="delete-a-self-service-sign-up-subscription"></a>Usuwanie subskrypcji z samodzielnym logowaniem

> [!IMPORTANT]
> Po usunięciu subskrypcji samoobsługowej możesz zablokować wszystkim użytkownikom dostęp do ich danych i poczty e-mail oraz usunąć wszystkie dane i pocztę e-mail.

1. W centrum administracyjnym przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">RozliczeniaZgody</a>  >  produktów.
2. Na karcie **Produkty** wybierz ikonę filtru, a następnie wybierz pozycję **Bezpłatna**.
3. Wybierz subskrypcję samodzielnego rejestracji, którą chcesz usunąć. 
4. Na stronie szczegółów subskrypcji w sekcji **Subskrypcje i ustawienia płatności** wybierz pozycję **Usuń subskrypcję**.
5. W **okienku Usuń** subskrypcję zaznacz pole wyboru, a następnie wybierz pozycję **Usuń subskrypcję**.

## <a name="i-have-a-self-service-sign-up-subscription-that-blocks-directory-deletion"></a>Mam subskrypcję samoobsługowego konta, która blokuje usuwanie katalogów

Produkty do samodzielnego tworzenia kont, dla których poszczegłoni użytkownicy mogą tworzyć konta, również tworzą użytkownika gościa na celu uwierzytelniania w katalogu usługi Azure AD. Aby uniknąć utraty danych, produkty samoobsługowe blokują usuwanie katalogów do momentu ich całkowitego usunięcia z katalogu. Mogą zostać usunięte tylko przez administratora usługi Azure AD. Aby uzyskać więcej informacji, [zobacz Usuwanie katalogu w programie Azure Active Directory](/azure/active-directory/users-groups-roles/directory-delete-howto).
