---
title: przewodniki konfiguracji Azure Active Directory
ms.author: Kwekua
author: Kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
description: Dowiedz się więcej o przewodnikach konfiguracji dla Azure Active Directory.
ms.openlocfilehash: 58f7ed9a20580db742a773cb8a7874137f0cfc4c
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128417"
---
# <a name="azure-active-directory-setup-guides"></a>przewodniki konfiguracji Azure Active Directory

funkcje Azure Active Directory (Azure AD) ułatwiają zarządzanie organizacją i jej zabezpieczanie. Te przewodniki konfiguracji ułatwią integrację tych funkcji w prosty sposób. W poniższych sekcjach krótko opiszemy przewodniki konfiguracji i udostępnimy linki do przewodników.

## <a name="who-are-these-setup-guides-for"></a>KtoTo są te przewodniki konfiguracji?

Te przewodniki konfiguracji są przeznaczone dla małych i średnich organizacji, które zazwyczaj nie mają dedykowanego zespołu ds. tożsamości. Nie musisz być ekspertem od tożsamości, aby z nich korzystać.

## <a name="what-to-expect-and-what-youll-need"></a>Czego się spodziewać i czego będziesz potrzebować

Przewodniki konfiguracji ułatwiają konfigurowanie podstawowych funkcji Azure AD. Jeśli musisz skonfigurować bardziej zaawansowaną konfigurację, przewodnik konfiguracji wskaże odpowiednią lokalizację w portalu Azure AD.

### <a name="required-permissions"></a>Wymagane uprawnienia

Musisz być członkiem następujących ról administracyjnych:

- administrator globalny: umożliwia używanie zintegrowanych narzędzi w przewodnikach konfiguracji w celu wprowadzania zmian w organizacji Microsoft 365.

- Czytelnik globalny: umożliwia wyświetlanie przewodników konfiguracji, ale nie wprowadzanie zmian w dzierżawie.

## <a name="identity-security-for-teams"></a>Zabezpieczenia tożsamości dla Teams

Azure Active Directory (Azure AD) to oparta na chmurze usługa zarządzania tożsamościami i dostępem, która pomaga pracownikom logować się i uzyskiwać dostęp do aplikacji i usług.
Ten wykaz zawiera kilka podstawowych funkcji zabezpieczeń, których można użyć, aby zapewnić użytkownikom bezpieczeństwo i najbardziej produktywny czas korzystania z Teams.

### <a name="licensing"></a>Licencjonowanie

Licencja Azure Active Directory P2 jest wymagana do korzystania z funkcji zabezpieczeń w tym wykazie.

[Otwieranie zabezpieczeń tożsamości dla wykazu Teams](https://aka.ms/teamsidentity)

## <a name="identity-governance"></a>Zarządzanie tożsamościami

Ten wykaz kreatorów ma na celu ułatwienie klientom Azure Active Directory funkcji P2, w tym przeglądów dostępu (AR), Privileged Identity Management (PIM) i zarządzania uprawnieniami (ELM). W przypadku usług PIM i ELM oferujemy wyselekcjonowaną listę dokumentów oraz wskaźnik do centrum administracyjnego Azure Active Directory, gdzie administrator może skonfigurować tę funkcję. W przypadku ar oferujemy w pełni zautomatyzowane środowisko, które umożliwia administratorom wybór spośród dwóch szablonów. Te szablony obejmują jeden, który umożliwia właścicielom grup zatwierdzanie użycia gościa we wszystkich grupach Microsoft 365. Są to najważniejsze zasady używane obecnie przez klientów.  

Następnie oferujemy szablon testowy, w którym administrator jest recenzentem gości dla wybranej przez nich grupy. Jeśli dzierżawa ma już przegląd obejmujący wszystkich użytkowników-gości Microsoft 365 grup, administrator zostanie skierowany do centrum administracyjnego Azure Active Directory, aby zarządzać istniejącym przeglądem i nie będzie zautomatyzowanego środowiska.

[Otwórz przewodnik konfiguracji ładu tożsamości](https://go.microsoft.com/fwlink/p/?linkid=386330)

> [!NOTE]
> Azure Active Directory licencja P2 jest wymagana do korzystania z funkcji zabezpieczeń w tym wykazie.

## <a name="azure-active-directory-deployment"></a>wdrożenie Azure Active Directory  

Przewodnik konfiguracji Azure Active Directory pomoże Ci skonfigurować najbardziej typowe funkcje Azure AD w zalecanej kolejności. Przewodnik konfiguracji jest podzielony na trzy sekcje: **Initial**, **Core** i **Advanced**. Każda sekcja zaleca zestaw funkcji, które należy włączyć.

Przewodniki konfiguracji zawierają listę kontrolną zadań, które należy wykonać, i możesz śledzić postęp podczas przechodzenia przez przewodniki. Przewodniki będą również w razie potrzeby łączyć się z innymi przewodnikami konfiguracji.

[Otwórz przewodnik konfiguracji Azure Active Directory](https://go.microsoft.com/fwlink/p/?linkid=2183427).

## <a name="add-or-sync-users-to-your-microsoft-account"></a>Dodawanie lub synchronizowanie użytkowników do konta Microsoft  

Ten przewodnik ułatwia konfigurowanie kont użytkowników na platformie Azure i Microsoft 365. W zależności od środowiska i potrzeb możesz indywidualnie dodawać użytkowników, migrować katalog lokalny za pomocą Azure AD synchronizacji w chmurze lub Azure AD Połączenie lub rozwiązywać istniejące problemy z synchronizacją.

### <a name="licensing"></a>Licencjonowanie

Korzystanie z Azure Active Directory narzędzi synchronizacji jest bezpłatne i dołączone do wszystkich Microsoft 365 subskrypcji.

[Otwórz przewodnik konfiguracji Dodawanie lub synchronizowanie użytkowników](https://go.microsoft.com/fwlink/?linkid=2183349).

## <a name="secure-your-cloud-apps-with-single-sign-on-sso"></a>Zabezpieczanie aplikacji w chmurze przy użyciu logowania jednokrotnego

Ten przewodnik ma na celu ułatwienie dodawania aplikacji w chmurze do Microsoft 365. W naszym przewodniku możesz dodać aplikację do dzierżawy, dodać użytkowników do aplikacji, przypisać role i nie tylko.  Jeśli aplikacja obsługuje logowanie jednokrotne (Single Sign-On), przeprowadzimy Cię również przez tę konfigurację.

### <a name="licensing"></a>Licencjonowanie

Każda płatna subskrypcja Microsoft 365 ma bezpłatną subskrypcję do Azure AD. Za pomocą Azure AD można zarządzać aplikacjami oraz tworzyć konta użytkowników i grup oraz zarządzać nimi.

[Otwórz przewodnik konfigurowania dodawania aplikacji w chmurze do Microsoft 365](https://aka.ms/AzureAppSetup)

## <a name="azure-self-service-password-reset-sspr-guide"></a>Przewodnik po resetowaniu haseł w usłudze Azure Self-Service

Ten przewodnik konfiguracji ma na celu ułatwienie włączania i konfigurowania samoobsługowego resetowania haseł. Przewodnik konfiguracji przeprowadzi Cię przez zalecane opcje, w tym zapisywanie zwrotne haseł i powiadomienia administratora.

### <a name="licensing"></a>Licencjonowanie

Samoobsługowe resetowanie hasła wymaga jednej z następujących licencji:

- Azure Active Directory P1 lub P2

- Microsoft 365 Business Premium

- Microsoft 365 Enterprise E3 lub E5  

- Enterprise Mobility and Security E3 lub E5

[Otwórz samoobsługowy przewodnik konfiguracji resetowania haseł](https://go.microsoft.com/fwlink/p/?linkid=2183284).

## <a name="multi-factor-authentication-mfa"></a>Uwierzytelnianie wieloskładnikowe (MFA)

Ten przewodnik zawiera bieżący stan uwierzytelniania wieloskładnikowego i pomaga administratorom IT wybrać najlepszą opcję uwierzytelniania wieloskładnikowego spełniającą wymagania organizacji. Następnie pomagamy w konfigurowaniu i wymuszaniu wybranej metody uwierzytelniania wieloskładnikowego dla organizacji.

### <a name="licensing"></a>Licencjonowanie

Dostęp warunkowy wymaga licencji Azure Active Directory P1 lub P2, ustawienia domyślne zabezpieczeń i uwierzytelnianie wieloskładnikowe dla poszczególnych użytkowników są bezpłatne i dołączone do wszystkich subskrypcji Microsoft 365.

[Otwórz przewodnik uwierzytelniania wieloskładnikowego (MFA)](https://go.microsoft.com/fwlink/?linkid=2183506)

## <a name="the-passwordless-setup-guide"></a>Przewodnik konfiguracji bez hasła

Przewodnik konfiguracji bez hasła ma na celu ułatwienie określenia najlepszej metody bez hasła dla środowiska. Metody te obejmują klucze zabezpieczeń, Windows Hello dla firm i aplikację Microsoft Authenticator. Jeśli zalecenie jest Windows Hello dla firm, istnieje sekcja, która przeprowadzi Cię przez różne opcje. Przewodnik zawiera pytania ułatwiające utworzenie planu krok po kroku.

### <a name="licensing"></a>Licencjonowanie

Każda płatna subskrypcja Microsoft 365 ma bezpłatną subskrypcję do Azure AD. Za pomocą Azure AD można zarządzać aplikacjami oraz tworzyć konta użytkowników i grup oraz zarządzać nimi.

[Otwórz przewodnik konfiguracji bez hasła](https://go.microsoft.com/fwlink/?linkid=2183427).
