---
title: Zarządzanie zgodą użytkownika na aplikacje w aplikacji Microsoft 365
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 7e453a40-66df-44ab-92a1-96786cb7fb34
description: Dowiedz się więcej na temat zgody użytkowników na aplikacje i sposobu ich włączanie w celu umożliwienia aplikacjom innych firm uzyskiwania dostępu do danych Microsoft 365 użytkowników.
ms.openlocfilehash: d9a07eb333b0abdb3cb6a890ac2de3d19ad3685b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984977"
---
# <a name="managing-user-consent-to-apps-in-microsoft-365"></a>Zarządzanie zgodą użytkownika na aplikacje w aplikacji Microsoft 365

To ustawienie określa, czy użytkownicy mogą udzielić zgody aplikacjom korzystającym z Połączenie OpenID Połączenie OAuth 2.0 do logowania i żądań dostępu do danych. Aplikację można utworzyć z poziomu twojej organizacji lub może pochodzić od innej Office 365 lub innej firmy.

Jeśli to ustawienie jest włączyć, te aplikacje będą pytać użytkowników o uprawnienia do uzyskiwania dostępu do danych organizacji i użytkownicy mogą wybrać, czy chcesz na to zezwolić. Jeśli wyłączysz to ustawienie, administratorzy muszą wyrazić zgodę na te aplikacje, zanim użytkownicy będą ich używać. W takim przypadku rozważ skonfigurowanie przepływu pracy zgody administratora w portalu Azure Portal, aby użytkownicy mogą wysłać żądanie zatwierdzenia przez administratora do używania dowolnej zablokowanej aplikacji.

Użytkownik może nadać dostęp tylko dla aplikacji, które posiada i które uzyskują dostęp do jego informacji usługi Office 365. Nie może nadać aplikacji dostępu do informacji żadnego innego użytkownika.

## <a name="turning-user-consent-on-or-off"></a>Włączanie lub wyłączanie zgody użytkownika

Poniżej opisano, jak można włączyć lub wyłączyć uprawnienia użytkownika dotyczące aplikacji.

1. W centrum administracyjnym przejdź do strony  >  \> Ustawienia Ustawienia [organizacjiUsługi](https://go.microsoft.com/fwlink/p/?linkid=2053743), a następnie wybierz pozycję Zgoda **użytkownika na aplikacje**.

2. Na stronie **Użytkownik wyrażaj zgodę na** aplikacje wybierz opcję, aby włączyć lub wyłączyć zgodę użytkownika.

## <a name="related-content"></a>Zawartość pokrewna 

[Konfigurowanie przepływu pracy zgody administratora](/azure/active-directory/manage-apps/configure-admin-consent-workflow) (artykuł)\
[Zarządzanie zgodą na aplikacje i ocenianie żądań zgody](/azure/active-directory/manage-apps/manage-consent-requests) (artykuł)