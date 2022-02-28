---
title: Konfigurowanie inspekcji zaawansowanej w programie Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-audit
- m365initiative-compliance
- m365solution-scenario
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: W tym artykule opisano, jak skonfigurować inspekcję zaawansowaną w celu przeprowadzania dochodzenia sądowego w przypadku naruszenia kont użytkowników lub badania innych zdarzeń związanych z zabezpieczeniami.
ms.openlocfilehash: 34ae98eaafcc3eeb3d6a25a457f017999b8c6078
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984963"
---
# <a name="set-up-advanced-audit-in-microsoft-365"></a>Konfigurowanie inspekcji zaawansowanej w programie Microsoft 365

Jeśli Organizacja ma subskrypcję i licencjonowanie użytkowników końcowych obsługujące inspekcję zaawansowaną, wykonaj poniższe czynności, aby skonfigurować dodatkowe funkcje i korzystać z nich w ramach inspekcji zaawansowanej.

![Przepływ pracy do skonfigurowania inspekcji zaawansowanej.](../media/AdvancedAuditWorkflow.png)

## <a name="step-1-set-up-advanced-audit-for-users"></a>Krok 1. Konfigurowanie inspekcji zaawansowanej dla użytkowników

Zaawansowane funkcje inspekcji, takie jak możliwość rejestrować ważne zdarzenia, takie jak MailItemsAccessed i Send, wymagają odpowiedniej licencji usługi E5 przypisanej do użytkowników. Ponadto dla tych użytkowników musi być włączony plan usługi/aplikacji zaawansowanej inspekcji. Aby sprawdzić, czy aplikacja Advanced Auditing (Zaawansowana inspekcja) jest przypisana do użytkowników, wykonaj następujące czynności dla każdego użytkownika:

1. W centrum administracyjne platformy Microsoft 365 przejdź do **tematu** <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**UżytkownicyAktywowanie**</a> >  użytkowników i wybierz użytkownika.

2. Na stronie wysuwu właściwości użytkownika kliknij pozycję **Licencje i aplikacje**.

3. W sekcji **Licencje sprawdź** , czy użytkownikowi przypisano licencję E5 lub że przypisano mu odpowiednią licencję dodatkową. Aby uzyskać listę licencji, które obsługują inspekcję zaawansowaną, zobacz [Zaawansowane wymagania dotyczące licencjonowania inspekcji](auditing-solutions-overview.md#advanced-audit-1).

4. Rozwiń **sekcję** Aplikacje i sprawdź, czy **jest zaznaczone Microsoft 365 zaawansowanej** inspekcji.

5. Jeśli pole wyboru nie jest zaznaczone, zaznacz je, a następnie kliknij pozycję **Zapisz zmiany.**

   Rejestrowanie rekordów inspekcji dla rekordów mailItemsAccessed i Send rozpocznie się w ciągu 24 godzin. Aby rozpocząć rejestrowanie dwóch innych zdarzeń inspekcji zaawansowanej, należy wykonać krok 3: SearchQueryInitiatedExchange i SearchQueryInitiatedSharePoint.

W przypadku organizacji, które przypisują licencje do grup użytkowników przy użyciu licencjonowania grupowego, musisz wyłączyć przypisywanie licencji dla grupy Microsoft 365 zaawansowanej inspekcji. Po zapisaniu zmian sprawdź, czy funkcja Microsoft 365 jest wyłączona dla grupy. Następnie ponownie włącz przypisanie licencji dla grupy. Aby uzyskać instrukcje dotyczące licencjonowania opartego na grupach, zobacz Przypisywanie licencji użytkownikom według [członkostwa w Azure Active Directory](/azure/active-directory/users-groups-roles/licensing-groups-assign).

Ponadto, jeśli dostosowano akcje skrzynek pocztowych, które są rejestrowane w skrzynkach pocztowych użytkowników lub udostępnionych skrzynkach pocztowych, żadne nowe zdarzenia inspekcji zaawansowanej wydane przez firmę Microsoft nie będą automatycznie rejestrowane w tych skrzynkach pocztowych. Aby uzyskać informacje na temat zmieniania akcji skrzynki pocztowej, które są rejestrowane w dzienniku inspekcji dla każdego typu logowania, zobacz sekcję "Zmienianie lub przywracanie rejestrowanych domyślnie akcji skrzynki pocztowej" w tece Zarządzanie inspekcją [skrzynki pocztowej](enable-mailbox-auditing.md#change-or-restore-mailbox-actions-logged-by-default).

## <a name="step-2-enable-advanced-audit-events"></a>Krok 2. Włączanie zdarzeń inspekcji zaawansowanej

Podczas wyszukiwania użytkowników w usługach Exchange Online i SharePoint Online należy włączyć dwa zdarzenia inspekcji zaawansowanej (SearchQueryInitiatedExchange i SearchQueryInitiatedSharePoint). Aby włączyć inspekcję tych dwóch zdarzeń dla użytkowników, uruchom następujące polecenie (dla każdego użytkownika) w [programie Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Set-Mailbox <user> -AuditOwner @{Add="SearchQueryInitiated"}
```

W środowisku wielolokalowym należy uruchomić poprzednie polecenie **Set-Mailbox** w lesie, w którym znajduje się skrzynka pocztowa użytkownika. Aby określić lokalizację skrzynki pocztowej użytkownika, uruchom następujące polecenie: 

```powershell
Get-Mailbox <user identity> | FL MailboxLocations
```

Jeśli polecenie umożliwiające inspekcję zapytań wyszukiwania było wcześniej uruchamiane w lesie innym niż skrzynka pocztowa użytkownika, należy usunąć wartość SearchQueryInitiated `Set-Mailbox -AuditOwner @{Remove="SearchQueryInitiated"}` ze skrzynki pocztowej użytkownika, uruchamiając go, a następnie dodać do skrzynki pocztowej użytkownika w lesie, w którym znajduje się skrzynka pocztowa użytkownika.

## <a name="step-3-set-up-audit-retention-policies"></a>Krok 3. Konfigurowanie zasad przechowywania inspekcji

Poza zasadami domyślnymi, które zachowują rekordy inspekcji usług Exchange, SharePoint i Azure AD przez jeden rok, możesz utworzyć dodatkowe zasady przechowywania dziennika inspekcji, aby spełnić wymagania zespołów ds. zabezpieczeń organizacji, it i zgodności. Aby uzyskać więcej informacji, zobacz [Zarządzanie zasadami przechowywania dziennika inspekcji](audit-log-retention-policies.md).

## <a name="step-4-search-for-advanced-audit-events"></a>Krok 4. Wyszukiwanie zdarzeń zaawansowanej inspekcji

Po skonfigurowaniu dla organizacji inspekcji zaawansowanej możesz wyszukiwać istotne zdarzenia zaawansowanej inspekcji i inne działania podczas prowadzenia dochodzenia sądowego. Po zakończeniu wykonywania kroków 1 i 2 możesz wyszukać w dzienniku inspekcji zdarzenia zaawansowanej inspekcji i inne działania w ramach dochodzenia sądowego w sprawie naruszonych kont oraz innych rodzajów badań zabezpieczeń lub zgodności. Aby uzyskać więcej informacji na temat prowadzenia dochodzenia sądowego w sprawie naruszonych kont użytkowników przy użyciu zdarzenia MailItemsAccessed Advanced Audit, zobacz Badanie naruszonych kont za pomocą inspekcji [zaawansowanej](mailitemsaccessed-forensics-investigations.md).
