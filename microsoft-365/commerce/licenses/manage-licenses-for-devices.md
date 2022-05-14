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
description: Dowiedz się, jak przypisywać licencje do grup do użytku z urządzeniami.
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
- okr_SMB
search.appverid: MET150
ms.date: 05/12/2022
ms.openlocfilehash: 5603fd947abdfbc6bede01fe7545a5a0fa99a67d
ms.sourcegitcommit: 4e7ff69f4d7d27c2d419f763cfcb069e3b0d0d9f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2022
ms.locfileid: "65403277"
---
# <a name="manage-licenses-for-devices"></a>Zarządzanie licencjami dla urządzeń

Jeśli masz Aplikacje Microsoft 365 dla przedsiębiorstw (urządzenie) lub Aplikacje Microsoft 365 for Education (urządzenie), możesz przypisać licencje do urządzeń przy użyciu grup Azure AD. Jeśli urządzenie ma licencję, każdy, kto korzysta z tego urządzenia, może używać Aplikacje Microsoft 365 dla przedsiębiorstw (wcześniej nazwanego Office 365 ProPlus). Załóżmy na przykład, że masz 20 laptopów i tabletów używanych przez osoby w organizacji. Po przypisaniu licencji do każdego urządzenia każda osoba logująca się do jednego z urządzeń używa Aplikacje Microsoft 365 dla przedsiębiorstw bez konieczności posiadania własnej licencji.

> [!IMPORTANT]
> Licencjonowanie oparte na urządzeniach dla Aplikacje Microsoft 365 dla przedsiębiorstw jest dostępne tylko jako licencja dodatkowa dla niektórych klientów komercyjnych i niektórych klientów edukacyjnych. W przypadku klientów komercyjnych licencja jest *Aplikacje Microsoft 365 dla przedsiębiorstw (urządzenie)* i jest dostępna tylko za pośrednictwem subskrypcji Enterprise Agreement/Enterprise Agreement. W przypadku klientów edukacyjnych licencja jest *Aplikacje Microsoft 365 dla usługi Education (urządzenie)* i jest dostępna tylko za pośrednictwem usługi Enrollment for Education Solutions (EES). Aby uzyskać więcej informacji, przeczytaj wpis w blogu na temat [dostępności edukacji](https://educationblog.microsoft.com/2019/08/attention-it-administrators-announcing-office-365-proplus-device-based-subscription-for-education). Aby uzyskać dostępność komercyjną, skontaktuj się z przedstawicielem konta Microsoft.

Aby rozpocząć, należy utworzyć grupę w centrum administracyjnym Azure Active Directory, a następnie przypisać urządzenia do grupy. Aby dowiedzieć się więcej na temat licencjonowania urządzeń, w tym wymagań dotyczących urządzeń, typów grup, których można użyć, oraz sposobu konfigurowania Aplikacje Microsoft 365 dla przedsiębiorstw do korzystania z licencjonowania urządzeń, zobacz [Licencjonowanie oparte na urządzeniach dla Aplikacje Microsoft 365 dla przedsiębiorstw](/deployoffice/device-based-licensing).

> [!IMPORTANT]
> Aby wykonać zadania opisane w tym artykule, musisz być administratorem globalnym.

## <a name="assign-licenses-to-devices"></a>Przypisywanie licencji do urządzeń

Po przypisaniu licencji do grupy licencje są przypisywane do wszystkich urządzeń w grupie. Do dowolnej pojedynczej grupy można przypisać tylko jedną subskrypcję.

1. W Centrum administracyjne platformy Microsoft 365 przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">RozliczeniaLicenses</a> > .
2. Na stronie **Licencje** wybierz pozycję **Aplikacje Microsoft 365 for Education (urządzenie)** lub **Aplikacje Microsoft 365 dla przedsiębiorstw (urządzenie).**.
3. Na następnej stronie wybierz subskrypcję, a następnie wybierz pozycję **Przypisz licencje**.
4. W okienku **Przypisywanie licencji do grupy** rozpocznij wpisywanie nazwy grupy, a następnie wybierz ją z wyników, aby dodać ją do listy.
5. Wybierz pozycję **Przypisz**, a następnie wybierz pozycję **Zamknij**.

## <a name="unassign-licenses-from-devices"></a>Anulowanie przypisywania licencji z urządzeń

Po anulowaniu przypisania licencji z grupy należy usunąć licencje ze wszystkich urządzeń w grupie. Następnie wszystkie aplikacje i skojarzone z nimi dane są tylko do odczytu.

1. W centrum administracyjnym przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">RozliczeniaLicenses</a> > .
2. Na stronie **Licencje** wybierz pozycję **Aplikacje Microsoft 365 for Education (urządzenie)** lub **Aplikacje Microsoft 365 dla przedsiębiorstw (urządzenie).**.
3. Na następnej stronie wybierz subskrypcję, wybierz trzy kropki (więcej akcji), a następnie wybierz pozycję **Usuń przypisanie licencji**.
4. W oknie dialogowym **Anulowanie przypisania licencji** wybierz pozycję **Usuń przypisanie**.
