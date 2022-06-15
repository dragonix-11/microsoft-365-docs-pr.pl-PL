---
title: Zarządzanie subskrypcjami rejestracji samoobsługowej
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: mijeffer, jmueller
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
description: Dowiedz się, jak zarządzać bezpłatnymi subskrypcjami samoobsługowej rejestracji w organizacji.
ms.date: 03/17/2021
ms.openlocfilehash: 58c58c849b72c170e0ccf10de54389bd1245bced
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102355"
---
# <a name="manage-self-service-sign-up-subscriptions"></a>Zarządzanie subskrypcjami rejestracji samoobsługowej

## <a name="what-are-self-service-sign-up-subscriptions"></a>Co to są subskrypcje rejestracji samoobsługowej?

Istnieje ograniczona liczba bezpłatnych subskrypcji samoobsługowej rejestracji dostępnych dla użytkowników w organizacji w celu zarejestrowania się. Użytkownik może zarejestrować się tylko w celu korzystania z samoobsługowej subskrypcji rejestracji. Możesz zarządzać subskrypcjami samoobsługowych rejestracji, blokując użytkownikom rejestrację i usuwając bezpłatne subskrypcje, w których użytkownicy się zarejestrowali. Aby uzyskać więcej informacji na temat rejestracji samoobsługowej i dostępnych subskrypcji, zobacz [Korzystanie z samoobsługowej rejestracji w organizacji](../../admin/misc/self-service-sign-up.md).

## <a name="view-a-list-of-self-service-sign-up-subscriptions"></a>Wyświetlanie listy subskrypcji rejestracji samoobsługowej

1. W centrum administracyjnym przejdź do strony **Rozliczenia** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Twoje produkty</a>.
2. Na karcie **Produkty** wybierz ikonę filtru, a następnie wybierz pozycję **Bezpłatna**. Zostanie wyświetlona lista wszystkich subskrypcji rejestracji samoobsługowej.

## <a name="how-are-these-subscriptions-different-from-self-service-purchase-subscriptions"></a>Czym różnią się te subskrypcje od subskrypcji samoobsługowych zakupów?

Subskrypcje samoobsługowej rejestracji są bezpłatne i są dostępne dla większej listy produktów niż samoobsługowe subskrypcje zakupu. Gdy użytkownik zarejestruje się w celu samoobsługowej subskrypcji zakupu, będzie za nią odpowiedzialny. Subskrypcje samoobsługowego zakupu są dostępne tylko dla produktów platformy Power Platform (Power BI, Power Apps i Power Automate), Project i Visio. Aby uzyskać więcej informacji, zobacz [Często zadawane pytania dotyczące samoobsługowego zakupu](self-service-purchase-faq.yml).

## <a name="block-users-from-signing-up"></a>Blokowanie użytkownikom rejestrowania się

Polecenie cmdlet [**Set-MsolCompanySettings**](/powershell/module/msonline/set-msolcompanysettings?preserve-view=true&view=azureadps-1.0) z parametrem **AllowAdHocSubscriptions** umożliwia kontrolowanie, czy użytkownicy mogą zarejestrować się w celu rejestracji samoobsługowej. Aby uzyskać więcej informacji, zobacz [如何实现 kontrolować ustawienia samoobsługowe?](/azure/active-directory/users-groups-roles/directory-self-service-signup#how-do-i-control-self-service-settings)

## <a name="delete-a-self-service-sign-up-subscription"></a>Usuwanie subskrypcji samoobsługowej rejestracji

> [!IMPORTANT]
> Usunięcie subskrypcji samoobsługowej rejestracji powoduje zablokowanie wszystkim użytkownikom dostępu do ich danych i poczty e-mail oraz usunięcie wszystkich danych i wiadomości e-mail.

1. W centrum administracyjnym przejdź do strony **Rozliczenia** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Twoje produkty</a>.
2. Na karcie **Produkty** wybierz ikonę filtru, a następnie wybierz pozycję **Bezpłatna**.
3. Wybierz subskrypcję samoobsługowej rejestracji, którą chcesz usunąć. 
4. Na stronie szczegółów subskrypcji w sekcji **Subskrypcje i ustawienia płatności** wybierz pozycję **Usuń subskrypcję**.
5. W okienku **Usuwanie subskrypcji** zaznacz pole wyboru, a następnie wybierz pozycję **Usuń subskrypcję**.

## <a name="i-have-a-self-service-sign-up-subscription-that-blocks-directory-deletion"></a>Mam subskrypcję samoobsługowej rejestracji, która blokuje usuwanie katalogu

Produkty do rejestracji samoobsługowej, dla których mogą się zarejestrować poszczególni użytkownicy, również tworzą użytkownika-gościa na potrzeby uwierzytelniania w katalogu Azure AD. Aby uniknąć utraty danych, te produkty samoobsługowe blokują usuwanie katalogów do momentu ich całkowitego usunięcia z katalogu. Mogą one zostać usunięte tylko przez administratora Azure AD. Aby uzyskać więcej informacji, zobacz [Usuwanie katalogu w Azure Active Directory](/azure/active-directory/users-groups-roles/directory-delete-howto).
