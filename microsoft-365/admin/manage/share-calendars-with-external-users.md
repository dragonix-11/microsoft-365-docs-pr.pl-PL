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
description: Włącz udostępnianie kalendarza w Centrum administracyjne platformy Microsoft 365, aby użytkownicy mogli udostępniać swoje kalendarze wszystkim osobom w organizacji lub poza nią.
ms.openlocfilehash: b3ca1d4f2a6ef24a6958b4fe805ccf617c0984e7
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043149"
---
# <a name="share-microsoft-365-calendars-with-external-users"></a>Udostępnianie kalendarzy Microsoft 365 użytkownikom zewnętrznym

Czasami użytkownicy muszą zaplanować spotkania z osobami spoza organizacji. Aby uprościć proces znajdowania typowych czasów spotkań, Microsoft 365 umożliwia udostępnianie kalendarzy tym osobom. Są to osoby, które muszą wyświetlać bezpłatne i pracowite czasy dla użytkowników w organizacji, ale nie mają kont użytkowników w organizacji Microsoft 365.

Udostępnianie kalendarza można włączyć dla wszystkich użytkowników w organizacji w Centrum administracyjne platformy Microsoft 365. Po włączeniu udostępniania użytkownicy mogą używać Outlook Web App do udostępniania kalendarzy wszystkim osobom w organizacji lub poza nią. Osoby w organizacji mogą wyświetlać kalendarz udostępniony wraz z własnym kalendarzem. Do osób spoza organizacji zostanie wysłany adres URL, za pomocą którego będą one mogły wyświetlić kalendarz. Użytkownicy w organizacji decydują, kiedy udostępniać i ile udostępniać.

> [!NOTE]
> Jeśli chcesz udostępnić kalendarze organizacji używającej programu Exchange Server 2013 (rozwiązania lokalnego), administrator serwera Exchange musi skonfigurować relację uwierzytelniania z chmurą. Jest to nazywane federacją i musi spełniać minimalne wymagania dotyczące oprogramowania. Aby uzyskać więcej informacji, zobacz [Udostępnianie](/exchange/sharing-exchange-2013-help).
  
## <a name="enable-calendar-sharing-using-the-microsoft-365-admin-center"></a>Włączanie udostępniania kalendarza przy użyciu Centrum administracyjne platformy Microsoft 365

1. Zaloguj się jako **administrator globalny** w centrum administracyjnym, przejdź do **Ustawienia** \> **ustawień organizacji**, a następnie na <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">karcie **Usługi**</a> wybierz pozycję **Kalendarz**.
  
3. Na stronie **Kalendarz** wybierz, czy chcesz zezwolić użytkownikom na udostępnianie kalendarzy osobom spoza organizacji, które mają Microsoft 365, czy Exchange. Określ, czy chcesz zezwolić anonimowym użytkownikom (użytkownikom bez poświadczeń) na dostęp do kalendarzy za pośrednictwem zaproszenia e-mail.

4. Wybierz typ informacji kalendarza, które mają być dostępne dla użytkowników. Możesz zezwolić na wszystkie informacje lub ograniczyć je tylko do czasu lub czasu, tematu i lokalizacji.

## <a name="external-sharing-sync-interval"></a>Interwał synchronizacji udostępniania zewnętrznego

Obecnie nie jest obsługiwane natychmiastowe synchronizowanie udostępniania poza dzierżawą. Chociaż można udostępniać te konfiguracje, synchronizacja będzie odbywać się okresowo. Istnieją dwa typy udostępniania między dzierżawami:

1. **Microsoft 365 do innego użytkownika Microsoft 365 (jeśli udostępnianie zewnętrzne jest włączone)**: tworzony jest w pełni udostępniony kalendarz, ale synchronizacja będzie odbywać się co około trzy godziny. Natychmiastowa synchronizacja zostanie ostatecznie włączona dla tej konfiguracji.

2. **Microsoft 365 do użytkownika Outlook.com**: jeśli udostępnianie zewnętrzne jest wyłączone, udostępnianie innym Microsoft 365 użytkownikowi również należy do tej grupy. Podczas udostępniania jest generowany adres URL ICS, którego adresat może dodać do dowolnej usługi kalendarza. W przypadku subskrypcji ICS usługa kalendarza adresata wybiera, kiedy zsynchronizować subskrypcję ICS, aby otrzymywać nowe aktualizacje. Jeśli adresatem jest Outlook.com lub użytkownik Microsoft 365, synchronizacja odbywa się co około trzy godziny.

## <a name="invite-people-to-access-calendars"></a>Zapraszanie osób do uzyskiwania dostępu do kalendarzy

Po włączeniu udostępniania właściciele kalendarzy mogą rozszerzyć zaproszenia do określonych użytkowników.

1. Otwórz [Outlook w sieci Web](https://outlook.office365.com).

2. W górnej części strony wybierz narzędzie do uruchamiania aplikacji i wybierz pozycję **Kalendarz**. Domyślnie kalendarz podstawowy nosi nazwę "Calendar". Jeśli utworzono inne kalendarze, możesz wybrać jeden z nich do udostępnienia. Nie można udostępniać kalendarzy należących do innych osób.

3. Wprowadź imię i nazwisko lub adres e-mail osoby, której chcesz udostępnić kalendarz, w polu **Wyślij zaproszenie do udostępniania w wiadomości e-mail** .

4. Wybierz, ile informacji chcesz wyświetlić dla tej osoby:

     - **Może wyświetlać, kiedy jestem zajęty** , pozwala osobie zobaczyć, kiedy jesteś zajęty, ale nie zawiera szczegółów, takich jak lokalizacja zdarzenia.

     - **Możliwość wyświetlania tytułów i lokalizacji** pozwala osobie zobaczyć, kiedy jesteś zajęty, a także tytuł i lokalizację zdarzeń.

     - **Możliwość wyświetlenia wszystkich szczegółów** umożliwia osobie wyświetlenie wszystkich szczegółów zdarzeń.

     - **Możliwość edycji** umożliwia osobie wyświetlenie wszystkich szczegółów zdarzeń i edytowanie kalendarza (dostępnego tylko podczas udostępniania osobom w organizacji).

5. Wybierz pozycję **Udostępnij**. 

## <a name="related-content"></a>Zawartość pokrewna

[Włączanie lub wyłączanie udostępniania zewnętrznego dla witryny](/sharepoint/change-external-sharing-site) (artykuł)\
[Omówienie Centrum administracyjne platformy Microsoft 365](../admin-overview/admin-center-overview.md) (wideo)\
[Zarządzanie pocztą e-mail i kalendarzami](/admin) (strona linku)

