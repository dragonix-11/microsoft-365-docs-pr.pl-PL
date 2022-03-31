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
ms.openlocfilehash: 059890bd6a79ced1f7121e973b070790dffd8db9
ms.sourcegitcommit: 601ab9ad2b624e3b5e04eed927a08884c885c72a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2022
ms.locfileid: "64403616"
---
# <a name="azure-active-directory-setup-guides"></a>Azure Active Directory konfiguracji

Azure Active Directory usługi Azure AD ułatwiają zarządzanie organizacją i zabezpieczanie jej. Te przewodniki konfiguracji pomogą w łatwej integracji tych funkcji. W poniższych sekcjach krótko opiszemy przewodniki konfiguracji i udostępnimy linki do tych przewodników.

## <a name="who-are-these-setup-guides-for"></a>KtoTo czy te przewodniki konfiguracji mają na celu?

Te przewodniki konfiguracji są przeznaczone dla małych i średnich organizacji, w których zwykle nie ma dedykowanego zespołu tożsamości. Aby z nich korzystać, nie musisz być ekspertem ds. tożsamości.

## <a name="what-to-expect-and-what-youll-need"></a>Czego można oczekiwać i czego potrzebujesz

Przewodniki konfiguracji ułatwiają skonfigurowanie podstawowych funkcji usługi Azure AD. Jeśli musisz skonfigurować bardziej zaawansowaną konfigurację, przewodnik konfiguracji wskaże odpowiednią lokalizację w portalu usługi Azure AD.

### <a name="required-permissions"></a>Wymagane uprawnienia

Musisz być członkiem następujących ról administracyjnych:

- administrator globalny: umożliwia stosowanie zintegrowanych narzędzi z przewodnikami konfiguracji do zmieniania danych Microsoft 365 organizacji.

- Czytnik globalny: umożliwia wyświetlanie przewodników konfiguracji, ale nie pozwala na wprowadzanie zmian w dzierżawie.

## <a name="identity-security-for-teams"></a>Zabezpieczenia tożsamości dla Teams

Azure Active Directory (Azure AD) to oparta na chmurze usługa zarządzania tożsamościami i dostępem, która ułatwia Twoim pracownikom logowanie się do aplikacji i usług oraz uzyskiwanie do nich dostępu.
Ten wykaz zawiera kilka podstawowych funkcji zabezpieczeń, których można użyć, aby zapewnić bezpieczeństwo użytkownikom i wydajniej korzystać z Teams.

### <a name="licensing"></a>Licencjonowanie

Do korzystania z funkcji zabezpieczeń w tym wykazie jest wymagana licencja Azure Active Directory P2.

[Otwieranie wykazu zabezpieczeń tożsamości Teams tożsamości](https://aka.ms/teamsidentity)

## <a name="azure-active-directory-deployment"></a>Azure Active Directory wdrażania  

Przewodnik Azure Active Directory konfiguracji pomoże Ci skonfigurować najbardziej typowe funkcje usługi Azure AD w zalecanej kolejności. Przewodnik konfiguracji jest podzielony na trzy sekcje: **Initial**, **Core** i **Advanced**. W każdej sekcji zaleca się włączenie zestawu funkcji.

Przewodniki konfiguracji zawierają listę kontrolną zadań, które należy wykonać, i możesz śledzić postęp ich wykonywania w miarę wykonywania przewodników. W razie potrzeby przewodniki będą również zawierały linki do innych przewodników konfiguracji.

[Otwórz Azure Active Directory konfiguracji](https://go.microsoft.com/fwlink/p/?linkid=2183427).

## <a name="add-or-sync-users-to-your-microsoft-account"></a>Dodawanie użytkowników do konta Microsoft lub synchronizowanie ich z kontem Microsoft  

Ten przewodnik ułatwia skonfigurowanie kont użytkowników na platformie Azure Microsoft 365. W zależności od środowiska i potrzeb możesz wybrać opcję dodawania użytkowników pojedynczo, migrowania katalogu lokalnego za pomocą synchronizacji w chmurze usługi Azure AD lub usługi Azure AD Połączenie albo rozwiązywania istniejących problemów z synchronizacją.

### <a name="licensing"></a>Licencjonowanie

Korzystanie Azure Active Directory synchronizacji jest bezpłatne i dostępne we wszystkich Microsoft 365 subskrypcji.

[Otwórz przewodnik konfiguracji Dodawania lub synchronizowania użytkowników](https://go.microsoft.com/fwlink/?linkid=2183349).

## <a name="add-a-cloud-app-to-microsoft-365"></a>Dodawanie aplikacji w chmurze do Microsoft 365 

Ten przewodnik ma na celu pomoc w dodadaniu aplikacji w chmurze do Microsoft 365. W przewodniku możesz dodać aplikację do swojej dzierżawy, dodać użytkowników do aplikacji, przypisać role i nie tylko.  Jeśli aplikacja obsługuje funkcję logowania Sign-On (SSO), również ta konfiguracja zostanie przez nas przejdę przez ten proces.

### <a name="licensing"></a>Licencjonowanie

Każda płatna subskrypcja usługi Microsoft 365 jest wyposażona w bezpłatną subskrypcję usługi Azure AD. Za pomocą usługi Azure AD możesz zarządzać swoimi aplikacjami, a także tworzyć konta użytkowników i grup oraz zarządzać nimi.

[Otwieranie przewodnika po konfiguracji dodawania Microsoft 365 chmury](https://aka.ms/AzureAppSetup)

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

## <a name="the-passwordless-setup-guide"></a>Przewodnik konfiguracji bez haseł

Przewodnik konfiguracji bez haseł ma na celu pomoc w określeniu najlepszej metody bez haseł dla Twojego środowiska. Metody te obejmują klucze zabezpieczeń, Windows Hello dla firm i Microsoft Authenticator aplikacji. Jeśli to Windows Hello dla firm, możesz to zrobić w sekcji. Przewodnik zadaje pytania, aby ułatwić tworzenie planu krok po kroku.

### <a name="licensing"></a>Licencjonowanie

Każda płatna subskrypcja usługi Microsoft 365 jest wyposażona w bezpłatną subskrypcję usługi Azure AD. Za pomocą usługi Azure AD możesz zarządzać swoimi aplikacjami, a także tworzyć konta użytkowników i grup oraz zarządzać nimi.

[Otwórz przewodnik konfiguracji bez haseł](https://go.microsoft.com/fwlink/?linkid=2183427).
