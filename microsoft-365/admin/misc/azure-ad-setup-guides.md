---
title: Azure Active Directory konfiguracji
ms.author: Kwekua
author: Kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
description: Dowiedz się więcej o przewodnikach konfiguracji Azure Active Directory.
ms.openlocfilehash: 0150e88f6e5fc4f7a77ecfcecbc61395bf015c51
ms.sourcegitcommit: b6ab10ba95e4b986065c51179ead3810cc1e2a85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2021
ms.locfileid: "63017850"
---
# <a name="azure-active-directory-setup-guides"></a>Azure Active Directory konfiguracji

Azure Active Directory usługi Azure AD ułatwiają zarządzanie organizacją i zabezpieczanie jej. Te przewodniki konfiguracji pomogą w łatwej integracji tych funkcji. W poniższych sekcjach krótko opiszemy przewodniki konfiguracji i udostępnimy linki do tych przewodników.

## <a name="who-are-these-setup-guides-for"></a>KtoTo czy te przewodniki konfiguracji mają na celu?

Te przewodniki konfiguracji są przeznaczone dla małych i średnich organizacji, w których zwykle nie ma dedykowanego zespołu tożsamości. Aby z nich korzystać, nie musisz być ekspertem ds. tożsamości.

## <a name="what-to-expect-and-what-youll-need"></a>Czego można oczekiwać i czego potrzebujesz

Przewodniki konfiguracji ułatwiają skonfigurowanie podstawowych funkcji usługi Azure AD. Jeśli musisz skonfigurować bardziej zaawansowaną konfigurację, przewodnik konfiguracji wskaże odpowiednią lokalizację w portalu usługi Azure AD.

### <a name="required-permissions"></a>Wymagane uprawnienia

Musisz być członkiem następujących ról administratora:

- Administrator globalny: umożliwia korzystanie ze zintegrowanych narzędzi w przewodnikach konfiguracji w celu zmiany danych Microsoft 365 organizacji.

- Czytnik globalny: umożliwia wyświetlanie przewodników konfiguracji, ale nie pozwala na wprowadzanie zmian w dzierżawie.

## <a name="azure-active-directory-deployment"></a>Azure Active Directory wdrażania  

Przewodnik Azure Active Directory konfiguracji pomoże Ci skonfigurować najbardziej typowe funkcje usługi Azure AD w zalecanej kolejności. Przewodnik konfiguracji jest podzielony na trzy sekcje: **Initial**, **Core** i **Advanced**. W każdej sekcji zaleca się włączenie zestawu funkcji.

Przewodniki konfiguracji zawierają listę kontrolną zadań, które należy wykonać, i możesz śledzić postęp ich wykonywania w miarę wykonywania przewodników. W razie potrzeby przewodniki będą również zawierały linki do innych przewodników konfiguracji.

[Otwórz Azure Active Directory konfiguracji](https://go.microsoft.com/fwlink/p/?linkid=2183427).

## <a name="add-or-sync-users-to-your-microsoft-account"></a>Dodawanie użytkowników do konta Microsoft lub synchronizowanie ich z kontem Microsoft  

Ten przewodnik ułatwia konfigurowanie kont użytkowników na platformie Azure i w Microsoft 365. W zależności od środowiska i potrzeb możesz wybrać opcję dodawania użytkowników pojedynczo, migrowania katalogu lokalnego za pomocą synchronizacji w chmurze usługi Azure AD lub usługi Azure AD Połączenie albo rozwiązywania istniejących problemów z synchronizacją.

[Otwórz przewodnik konfiguracji Dodawania lub synchronizowania użytkowników](https://go.microsoft.com/fwlink/?linkid=2183349).

### <a name="licensing"></a>Licencjonowanie

Korzystanie Azure Active Directory synchronizacji jest bezpłatne i dostępne we wszystkich Microsoft 365 subskrypcji.

## <a name="azure-self-service-password-reset-sspr-guide"></a>Przewodnik Self-Service resetowania hasła usługi Azure (SSPR)

Ten przewodnik konfiguracji ma na celu pomoc w włączeniu i skonfigurowaniu samodzielnego resetowania hasła. Przewodnik konfiguracji zawiera zalecane opcje, w tym informacje dotyczące zapisu hasła i powiadomień administratora.

### <a name="licensing"></a>Licencjonowanie

Program SSPR wymaga jednej z następujących licencji:

- Azure Active Directory P1 lub P2

- Microsoft 365 Business Premium

- Microsoft 365 Enterprise E3 lub E5  

- Enterprise Mobility and Security E3 lub E5

[Otwórz przewodnik konfiguracji samodzielnego resetowania hasła](https://go.microsoft.com/fwlink/p/?linkid=2183284).

## <a name="multi-factor-authentication-mfa"></a>Uwierzytelnianie wieloskładnikowe

Ten przewodnik zawiera bieżący stan uwierzytelniania wieloskładnikowego i ułatwia administratorom IT wybranie najlepszej opcji uwierzytelniania wieloskładnikowego spełniającej wymagania organizacji. Następnie pomożemy w konfigurowaniu i wymuszaniu wybranej metody uwierzytelniania MFA dla organizacji.

### <a name="licensing"></a>Licencjonowanie

Dostęp warunkowy wymaga licencji Azure Active Directory P1 lub P2, wartości domyślne zabezpieczeń i uwierzytelniania wieloskładnikowego na użytkownika są bezpłatne i są dostępne Microsoft 365 subskrypcji.

[Otwieranie przewodnika uwierzytelniania wieloskładnikowego](https://go.microsoft.com/fwlink/?linkid=2183506)

### <a name="the-passwordless-setup-guide"></a>Przewodnik konfiguracji bez haseł

Przewodnik konfiguracji bez haseł ma na celu pomoc w określeniu najlepszej metody bez haseł dla Twojego środowiska. Metody te obejmują klucze zabezpieczeń, Windows Hello dla firm i aplikację Microsoft Authenticator firm. Jeśli polecane jest Windows Hello dla firm, istnieje sekcja, która zawiera wskazówki dotyczące różnych opcji. Przewodnik zadaje pytania, aby ułatwić tworzenie planu krok po kroku.

[Otwórz przewodnik konfiguracji bez haseł](https://go.microsoft.com/fwlink/?linkid=2183427).
