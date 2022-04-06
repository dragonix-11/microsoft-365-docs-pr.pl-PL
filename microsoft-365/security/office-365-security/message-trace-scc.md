---
title: Śledzenie wiadomości w portalu Microsoft 365 Defender wiadomości
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: 3e64f99d-ac33-4aba-91c5-9cb4ca476803
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą użyć linku do śledzenia wiadomości w portalu Microsoft 365 Defender, aby dowiedzieć się, co się stało z wiadomościami.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d09470e37c066202d49d7d79788c12853ed42e21
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679747"
---
# <a name="message-trace-in-the-microsoft-365-defender-portal"></a>Śledzenie wiadomości w portalu Microsoft 365 Defender wiadomości

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Śledzenie wiadomości śledzi wiadomości e-mail przemieszczając się po Exchange Online organizacji. Możesz określić, czy wiadomość została odebrana, odrzucona, odroczona lub doręczona przez usługę. Pokazano też, jakie działania zostały wykonane w wiadomości przed jej ostatecznym stanem.

Za pomocą informacji śledzenia wiadomości możesz skutecznie odpowiadać na pytania użytkowników dotyczące tego, co się stało z wiadomościami, rozwiązywać problemy z przepływem poczty e-mail i sprawdzać poprawność zmian zasad.

> [!NOTE]
> Śledzenie wiadomości w portalu Microsoft 365 Defender to tylko przejście do śledzenia wiadomości w centrum Exchange administracyjnego. Aby uzyskać więcej informacji, zobacz [Śledzenie wiadomości w nowoczesnym centrum Exchange administracyjnego](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Aby korzystać z śledzenia **wiadomości, musisz** być członkiem grup ról Zarządzanie  **organizacją, Zarządzanie** zgodnością **Exchange Online Pomocy technicznej**. Aby uzyskać więcej informacji, zobacz [Uprawnienia w aplikacji Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Uwagi**: Członkostwo w odpowiedniej Azure Active Directory grupy w grupie centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia i uprawnienia do innych funkcji w aplikacji  Microsoft 365. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../../admin/add-users/about-admin-roles.md).

- Maksymalna liczba wiadomości wyświetlanych w wynikach śledzenia wiadomości zależy od wybranego typu raportu (szczegóły można znaleźć w sekcji Wybieranie typu raportu[](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac#choose-report-type)). Polecenie [cmdlet Get-HistoricalSearch](/powershell/module/exchange/get-historicalsearch) w programie Exchange Online PowerShell lub autonomicznym programie PowerShell usługi EOP zwraca wszystkie wiadomości w wynikach.

## <a name="open-message-trace"></a>Otwieranie śledzenia wiadomości

W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>, przejdź do tematu Współpraca za **& e-mail** \> **Exchange śledzenie wiadomości**. Aby przejść bezpośrednio do strony śledzenia wiadomości, użyj .<https://admin.exchange.microsoft.com/#/messagetrace>

W tym momencie zostanie otwarte okno śledzenia wiadomości w Programie śledzenia wiadomości. Aby uzyskać więcej informacji, zobacz [Śledzenie wiadomości w nowoczesnym centrum Exchange administracyjnego](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac).
