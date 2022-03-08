---
title: Zarządzanie licencjami dla urządzeń
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: shegu, nicholak
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
description: Dowiedz się, jak przypisywać licencje do grup do używania z urządzeniami.
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
- okr_SMB
search.appverid: MET150
ms.date: 08/27/2021
ms.openlocfilehash: fd452cb52a1c65a59e478fb80438ac95a57e8bf6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63311791"
---
# <a name="manage-licenses-for-devices"></a>Zarządzanie licencjami dla urządzeń

Jeśli masz Aplikacje Microsoft 365 dla przedsiębiorstw (urządzenie) lub urządzenie Aplikacje Microsoft 365 dla wersji Education (urządzenie), możesz przypisywać licencje do urządzeń przy użyciu grup usługi Azure AD. Jeśli urządzenie ma licencję, każda osoba korzystająca z tego urządzenia może używać aplikacji Aplikacje Microsoft 365 dla przedsiębiorstw (wcześniej Office 365 ProPlus). Załóżmy na przykład, że masz 20 laptopów i tabletów, z których mogą korzystać osoby w Twojej organizacji. Gdy przypiszesz licencję do każdego urządzenia, każda osoba logująca się na jednym z tych urządzeń będzie Aplikacje Microsoft 365 dla przedsiębiorstw urządzenia bez konieczności korzystania z własnej licencji.

> [!IMPORTANT]
> Licencjonowanie oparte na urządzeniach Aplikacje Microsoft 365 dla przedsiębiorstw jest dostępne tylko jako licencja dodatkowa dla niektórych klientów komercyjnych, a niektórych klientów edukacyjnych. W przypadku klientów komercyjnych licencja jest Aplikacje Microsoft 365 dla przedsiębiorstw *(urządzenie) i* jest dostępna tylko w ramach Enterprise Agreement/Enterprise Agreement subskrypcji. W przypadku klientów edukacyjnych licencja jest Aplikacje Microsoft 365 *education (urządzenie)* i jest dostępna tylko w ramach rejestracji do rozwiązań edukacyjnych (EES). Aby uzyskać więcej informacji, przeczytaj wpis w blogu na [temat dostępności dla edukacji](https://educationblog.microsoft.com/2019/08/attention-it-administrators-announcing-office-365-proplus-device-based-subscription-for-education). Aby uzyskać informacje o dostępności komercyjnej, skontaktuj się z przedstawicielem konta Microsoft.

Aby rozpocząć, należy utworzyć grupę w centrum Azure Active Directory administracyjnego, a następnie przypisać urządzenia do grupy. Aby dowiedzieć się więcej o licencjonowaniu urządzeń, w tym o wymaganiach dotyczących urządzeń, typach grup, których można używać, oraz o tym, jak skonfigurować program Aplikacje Microsoft 365 dla przedsiębiorstw do korzystania z licencjonowania urządzeń, zobacz Licencjonowanie oparte na urządzeniach dla [Aplikacje Microsoft 365 dla przedsiębiorstw.](/deployoffice/device-based-licensing)

> [!IMPORTANT]
> Aby wykonać zadania z tego artykułu, musisz być administratorem globalnym.

## <a name="assign-licenses-to-devices"></a>Przypisywanie licencji do urządzeń

Przypisując licencje do grupy, licencje są przypisywane do wszystkich urządzeń w grupie. Możesz przypisać tylko jedną subskrypcję do jednej grupy.

1. W centrum administracyjne platformy Microsoft 365 przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">BillingLicenses</a> > .
2. Na stronie **Licencje wybierz** pozycję Aplikacje Microsoft 365 **dla edukacji (urządzenie)** **lub Aplikacje Microsoft 365 dla przedsiębiorstw (urządzenie)**.
3. Na następnej stronie wybierz subskrypcję, a następnie wybierz pozycję **Przypisz licencje**.
4. W **okienku Przypisywanie licencji** do grupy zacznij wpisywać nazwę grupy, a następnie wybierz ją z wyników, aby dodać ją do listy.
5. Wybierz **pozycję Przypisz**, a następnie wybierz **pozycję Zamknij**.

## <a name="unassign-licenses-from-devices"></a>Nieprzypisuj licencje na urządzeniach

Usunięcie licencji z grupy powoduje usunięcie licencji ze wszystkich urządzeń w grupie. Wszystkie aplikacje i skojarzone z nimi dane są wówczas tylko do odczytu.

1. W centrum administracyjnym przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">BillingLicenses</a> > .
2. Na stronie **Licencje wybierz** pozycję Aplikacje Microsoft 365 **dla edukacji (urządzenie)** **lub Aplikacje Microsoft 365 dla przedsiębiorstw (urządzenie)**.
3. Na następnej stronie wybierz subskrypcję, wybierz pozycję z trzema kropkami (więcej akcji), a następnie wybierz pozycję **Cofniesz przypisanie licencji**.
4. W **oknie dialogowym Nieprzypisz licencje** wybierz pozycję **Nieprzypisz**.
