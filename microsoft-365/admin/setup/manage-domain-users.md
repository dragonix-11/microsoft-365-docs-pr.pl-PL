---
title: Synchronizowanie użytkowników domeny z Microsoft 365
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: Synchronizowanie użytkowników kontrolowanych domeną z usługą Microsoft 365 dla firm.
ms.openlocfilehash: e49a3095cff77692e58d1b70ca1169dc8fd4802a
ms.sourcegitcommit: bcea69bacd1b48827bd60af2880909593a1609a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010419"
---
# <a name="synchronize-domain-users-to-microsoft-365"></a>Synchronizowanie użytkowników domeny z Microsoft 365

## <a name="1-prepare-for-directory-synchronization"></a>1. Przygotowywanie do synchronizacji katalogów 

Przed zsynchronizowaniem użytkowników i komputerów z lokalnej domeny usługi Active Directory zapoznaj się z tematem Przygotowywanie do synchronizacji katalogów [z Microsoft 365](../../enterprise/prepare-for-directory-synchronization.md). W szczególności:

   - Upewnij się, że w katalogu nie występują duplikaty następujących atrybutów: **mail**, **proxyAddresses** i **userPrincipalName**. Te wartości muszą być unikatowe, a wszelkie duplikaty muszą zostać usunięte.
   
   - Zalecamy skonfigurowanie atrybutu **userPrincipalName** (UPN) dla każdego konta użytkownika lokalnego w celu dopasowania go do podstawowego adresu e-mail odpowiadającego licencjonowanemu Microsoft 365 użytkownika. Na przykład: *mary.shelley@contoso.com* zamiast *mary@contoso.local*
   
   - Jeśli domena usługi Active Directory kończy się sufiksem nie routowalnym, takim jak *.local* lub *lan*, a nie sufiksem routowalnym dla Internetu, takim jak *com* lub *org*, najpierw dostosuj sufiks upn lokalnych kont użytkowników, tak jak to opisano w tece Przygotowywanie domeny nie [routowalnej do synchronizacji katalogów](../../enterprise/prepare-a-non-routable-domain-for-directory-synchronization.md). 

Uruchomienie **programu IdFix** w kroku 4 (4) poniżej spowoduje również upewninie się, że lokalna usługa Active Directory jest gotowa do synchronizacji katalogów.

## <a name="2-install-and-configure-azure-ad-connect"></a>2. Instalowanie i konfigurowanie usługi Azure AD Połączenie

Aby zsynchronizować użytkowników, grupy i kontakty z lokalnej usługi Active Directory z usługą Azure Active Directory, zainstaluj Azure Active Directory Połączenie i skonfiguruj synchronizację katalogów. 

 1. W centrum [administracyjnym wybierz](https://go.microsoft.com/fwlink/p/?linkid=2024339) pozycję **Konfiguracja w** lewym okienku narracji.

 2. W **obszarze Logowanie i zabezpieczenia wybierz** pozycję **Dodaj lub zsynchronizuj użytkowników z kontem Microsoft**.

 3. Na stronie **Dodawanie użytkowników do konta Microsoft** lub synchronizowanie ich z tym kontem wybierz pozycję **Wprowadzenie**.

 4. W pierwszym kroku uruchom narzędzie IdFix, aby przygotować się do synchronizacji katalogów.

 5. Postępuj zgodnie z instrukcjami kreatora, aby pobrać usługę Azure AD Połączenie i używać jej do synchronizowania użytkowników kontrolowanych przez domenę w celu Microsoft 365.


Aby [dowiedzieć się więcej, zobacz Konfigurowanie Microsoft 365](../../enterprise/set-up-directory-synchronization.md) katalogów.

Podczas konfigurowania opcji dla usługi Azure AD Połączenie zalecamy włączenie synchronizacji **haseł, bezproblemowego** logowania pojedynczego i funkcji zapisu hasła, która jest również obsługiwana w  usłudze Microsoft 365 dla firm.

> [!NOTE]
> Istnieje kilka dodatkowych kroków zapisu hasła poza polem wyboru w usłudze Azure AD Połączenie. Aby uzyskać więcej informacji, zobacz [Jak skonfigurować pisanie hasła](/azure/active-directory/authentication/howto-sspr-writeback). 

Jeśli chcesz również zarządzać urządzeniami z systemem Windows 10 przyłączony do domeny, zobacz Włączanie zarządzania przyłączone do domeny Windows 10 przez usługę [Microsoft 365 Business Premium](manage-windows-devices.md) w celu skonfigurowania hybrydowego dołączenia usługi Azure AD.
