---
title: Udostępnianie kalendarzy użytkownikom zewnętrznym
f1.keywords:
- NOCSH
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
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd
description: Włącz udostępnianie kalendarza w centrum administracyjne platformy Microsoft 365, aby użytkownicy mogą udostępniać swoje kalendarze wszystkim osobom w organizacji i poza nią.
ms.openlocfilehash: 00ae4b96c54ae6b1471a90f598b9f96821947db3
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017866"
---
# <a name="share-calendars-with-external-users"></a>Udostępnianie kalendarzy użytkownikom zewnętrznym

Czasami użytkownicy muszą planować spotkania z osobami spoza organizacji. Aby uprościć proces znajdowania typowych godzin spotkań, Microsoft 365 udostępnić kalendarze tym osobom. Są to osoby, które muszą wyświetlić informacje o czasie wolnym i zajętym użytkowników w organizacji, ale nie mają kont użytkowników w Twojej organizacji Microsoft 365 organizacji.

Możesz włączyć udostępnianie kalendarza dla wszystkich użytkowników w organizacji w centrum administracyjne platformy Microsoft 365. Po włączeniu udostępniania użytkownicy mogą za pomocą funkcji Outlook Web App udostępniać swoje kalendarze wszystkim osobom w organizacji i poza nią. Osoby w organizacji mogą wyświetlać kalendarz udostępniony wraz z własnym kalendarzem. Do osób spoza organizacji zostanie wysłany adres URL, za pomocą którego będą one mogły wyświetlić kalendarz. Użytkownicy w Twojej organizacji decydują, kiedy i ile informacji udostępnić.

> [!NOTE]
> Jeśli chcesz udostępnić kalendarze organizacji używającej programu Exchange Server 2013 (rozwiązania lokalnego), administrator serwera Exchange musi skonfigurować relację uwierzytelniania z chmurą. Jest to nazywane federacją i musi spełniać minimalne wymagania dotyczące oprogramowania. Aby uzyskać więcej informacji, zobacz [Udostępnianie](/exchange/sharing-exchange-2013-help).
  
## <a name="enable-calendar-sharing-using-the-microsoft-365-admin-center"></a>Włączanie udostępniania kalendarza przy użyciu centrum administracyjne platformy Microsoft 365

1. W centrum administracyjnym przejdź do pozycji **Ustawienia** \> **organizacji i na** <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**karcie Usługi** wybierz</a> pozycję **Kalendarz**.
  
3. Na **stronie Kalendarz** wybierz, czy chcesz, aby użytkownicy udostępniali swoje kalendarze osobom spoza organizacji, które mają Microsoft 365 lub Exchange. Określ, czy użytkownicy anonimowi (użytkownicy bez poświadczeń) mają mieć dostęp do kalendarzy za pośrednictwem zaproszenia pocztą e-mail.

4. Wybierz typ informacji kalendarza, które mają być dostępne dla użytkowników. Możesz zezwolić na wszystkie informacje lub ograniczyć je tylko do czasu lub tylko do czasu, tematu i lokalizacji.

## <a name="external-sharing-sync-interval"></a>Interwał synchronizacji udostępniania zewnętrznego

Błyskawiczna synchronizacja udostępniania poza dzierżawą nie jest obecnie obsługiwana. Chociaż udostępnianie jest możliwe w tych konfiguracjach, synchronizacja będzie okresowo odbywać się. Istnieją dwa typy udostępniania między dzierżawami:

1. **Microsoft 365 użytkownika Microsoft 365 (** jeśli udostępnianie zewnętrzne jest włączone): Jest tworzony w pełni udostępniony kalendarz, ale synchronizacja będzie się odbywać w przybliżeniu co trzy godziny. Błyskawiczna synchronizacja zostanie ostatecznie włączona dla tej konfiguracji.

2. **Microsoft 365 do użytkownika usługi Outlook.com**: Jeśli udostępnianie zewnętrzne jest wyłączone, udostępnianie inowi przez innego użytkownika Microsoft 365 również należy do tej grupy. Adres URL pliku ICS jest generowany podczas udostępniania, za pomocą którego adresat może dodać go do dowolnej usługi kalendarza. W przypadku subskrypcji ICS usługa kalendarza adresata wybiera, kiedy zsynchronizować subskrypcję ICS, aby otrzymać nowe aktualizacje. Jeśli adresat jest użytkownikiem usługi Outlook.com lub Microsoft 365, synchronizacja będzie się odbywać w przybliżeniu co trzy godziny.

## <a name="invite-people-to-access-calendars"></a>Zapraszanie osób do uzyskiwania dostępu do kalendarzy

Po włączeniu udostępniania właściciele kalendarza mogą rozszerzyć zaproszenia o poszczególnych użytkowników. Aby uzyskać instrukcje, [zobacz Udostępnianie kalendarza w Outlook Web App](https://support.microsoft.com/office/7ecef8ae-139c-40d9-bae2-a23977ee58d5).

## <a name="related-content"></a>Zawartość pokrewna

[Włączanie lub wyłączanie udostępniania zewnętrznego dla witryny](/sharepoint/change-external-sharing-site) (artykuł)\
[Omówienie centrum administracyjne platformy Microsoft 365](../admin-overview/admin-center-overview.md) (wideo)\
[Zarządzanie pocztą e-mail i kalendarzami](/admin) (strona linku)

