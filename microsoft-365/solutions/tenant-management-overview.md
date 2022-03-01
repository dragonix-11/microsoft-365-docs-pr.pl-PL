---
title: Zarządzanie dzierżawą w Microsoft 365 przedsiębiorstwa
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- m365solution-overview
- tenant-management
ms.custom:
- Ent_Solutions
description: Omówienie planowania, wdrażania i bieżącej pracy Microsoft 365 dzierżaw.
ms.openlocfilehash: 7a9545800c3f5f08b8094290c4173b4368caff4d
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/10/2022
ms.locfileid: "63011276"
---
# <a name="tenant-management-for-microsoft-365-for-enterprise"></a>Zarządzanie dzierżawą w Microsoft 365 przedsiębiorstwa

Utworzenie ścieżki do transformacji cyfrowej organizacji za pomocą przetwarzania w chmurze wymaga firmowej platformy, na której pracownicy mogą polegać na produktywności, współpracy, wydajności, prywatności, zgodności i zabezpieczeniach.

Prawidłowa konfiguracja dzierżaw Microsoft 365 udostępnia odpowiednią podstawę, dzięki temu pracownicy mogą skoncentrować się na pracy, a dział IT skupić się na rozwiązaniach, które zapewniają dodatkową wartość biznesową.

To rozwiązanie umożliwia proces konfiguracji tej podstawy w poniższych krokach:

1. Określanie dzierżaw
2. Optymalizowanie sieci
3. Synchronizowanie tożsamości i wymuszanie bezpiecznego logowania
4. Migrowanie Windows komputerach, Office klientów oraz lokalnych Office serwerach i danych
5. Wdrażanie zarządzania urządzeniami i aplikacją

Najpierw jednak poślijmy chwilę, aby zrozumieć, czym jest dzierżawa i jak wygląda dzierżawa, która zapewnia firmową podstawę.

## <a name="a-microsoft-365-tenant-defined"></a>Zdefiniowana Microsoft 365 dzierżawy

Dzierżawa Microsoft 365 to dedykowane wystąpienie usług firmy Microsoft 365 danych organizacji przechowywanych w określonej lokalizacji domyślnej, takiej jak Europa lub Ameryka Północna. Ta lokalizacja jest określana podczas tworzenia dzierżawy dla organizacji. Każda Microsoft 365 jest odrębna, unikatowa i odrębna od wszystkich Microsoft 365 dzierżaw. Dzierżawę usługi Microsoft 365 tworzy się, kupując jeden lub więcej produktów firmy Microsoft, takich jak Microsoft 365 E3 lub E5, oraz zestaw licencji dla każdego z nich.

Dzierżawa Microsoft 365 obejmuje również dzierżawę usługi Azure Active Directory (Azure AD), która jest dedykowanym wystąpieniem usługi Azure AD przeznaczonym dla kont użytkowników, grup i innych obiektów. Każda dzierżawa usługi Azure AD jest odrębna, unikatowa i odrębna od wszystkich innych dzierżaw usługi Azure AD. Twoja organizacja może mieć wiele dzierżaw usługi Azure AD, które można skonfigurować z subskrypcjami usługi Azure, Microsoft 365 dzierżawy mogą używać tylko jednej dzierżawy usługi Azure AD, która została utworzona podczas tworzenia dzierżawy.

Oto przykład:

![Przykład Microsoft 365 dzierżawy usługi Azure AD.](../media/tenant-management-overview/tenant-management-example-tenant.png)

*Zarządzanie dzierżawą* to planowanie, wdrażanie i bieżąca obsługa dzierżaw Microsoft 365 dzierżaw.

## <a name="attributes-of-a-well-designed-and-operating-tenant"></a>Atrybuty dobrze zaprojektowanej i działającej dzierżawy

Oprócz poprawnej nazwy i lokalizacji dzierżawy istnieją dodatkowe elementy do zaplanowania,&mdash; wdrożenia i zarządzania, aby zapewnić użytkownikom możliwości aplikacji biurowych w chmurze, takich jak Microsoft Teams i Exchange Online&mdash; są efektywne, bezpieczne i wydajne.

Oto elementy:

- Masz poprawny zestaw produktów (subskrypcji) i licencji.
  - Zestaw produktów odpowiada potrzebom Twojej firmy, it i zabezpieczeń.
  - Istnieje odpowiednia liczba licencji dla pracowników i przewiduje się zmiany w personelu.
- W przypadku sieci:
  - Skonfigurowano prawidłowe nazwy domen DNS.
  - W przypadku sieci przedsiębiorstwa zoptymalizowano ruch sieciowy do sieci firmy Microsoft dla pracowników lokalnych.
  - Zoptymalizowano ruch sieciowy dla pracowników zdalnych korzystających z klienta VPN.
- Zsynchronizowano konta użytkowników (Usługi domenowe w usłudze Active Directory AD DS), grupy i inne obiekty.
  - Konta dzierżawy usługi Azure AD są mapowane na Exchange Online pocztowe z prawidłowymi domenami DNS dla adresów e-mail.
  - Do kont użytkowników zostały przypisane odpowiednie licencje z odpowiednich kupionych produktów (na przykład Microsoft 365 E3 lub E5).
- Skonfigurowano silne zarządzanie tożsamością i dostępem.
  - Wymagane jest bezpieczne logowanie użytkownika przy użyciu uwierzytelniania wieloskładnikowego (MFA, passwordless).
  - Zasady dostępu warunkowego wymuszają wymagania dotyczące logowania i ograniczenia związane z wyższym poziomem zabezpieczeń.
- Lokalne serwery Office i ich dane zostały zmigrowane do aplikacji w chmurze lub używane w konfiguracji hybrydowej.
- Do zarządzania urządzeniami używasz wbudowanej w usługę Intune lub pakietu Basic Mobility and Security Microsoft 365.
  - Urządzenia należące do Twojej organizacji są zarejestrowane i zarządzane.
  - Aplikacjami dla urządzeń osobistych zarządza się.

Oto przykład dzierżawy usługi Microsoft 365 ze wszystkimi tymi elementami.

![Przykład Microsoft 365 dzierżawy.](../media/tenant-management-overview/tenant-management-tenant-config.png)

Na poniższej ilustracji dzierżawa Microsoft 365 zawiera:

- Produkty i licencje dla usług Microsoft 365 E3 i E5.
- Microsoft 365 aplikacje zwiększające produktywność.
- Intune z zarejestrowanymi urządzeniami oraz zasadami aplikacji i urządzeń.
- Dzierżawa usługi Azure AD z zsynchronizowanym kontem użytkownika (nie są wyświetlane grupy i inne obiekty katalogu), domeny i zasady dostępu warunkowego.

## <a name="tenant-capabilities-for-microsoft-365-for-enterprise"></a>Możliwości dzierżawy usługi Microsoft 365 przedsiębiorstwa

W poniższych sekcjach i tabelach przedstawiono najważniejsze funkcje i licencjonowanie dla kroków w tym rozwiązaniu.

### <a name="tenant"></a>Dzierżawca

|Funkcja lub funkcja|Opis|Licencjonowanie|
|---|---|---|
|Wiele dzierżaw|Każda Microsoft 365 jest odrębna, unikatowa i odrębna od wszystkich Microsoft 365 dzierżaw. W przypadku wielu dzierżaw istnieją ograniczenia i dodatkowe zagadnienia związane z zarządzaniem nimi i świadczeniem usług użytkownikom.|Microsoft 365 E3 lub E5|
|Migracja skrzynek pocztowych między dzierżawami|Administratorzy dzierżawy mogą przenosić skrzynki pocztowe między dzierżawami z minimalnymi zależnościami infrastruktury w ich systemach lokalnych. W ten sposób usuniesz konieczność przenoszenia się ze skrzynek pocztowych i do skrzynek pocztowych.|Microsoft 365 E3 lub E5|
|Multi-Geo|Dzierżawa może przechowywać dane w spoczynku w innych lokalizacjach geograficznych centrum danych wybranych w celu spełnienia wymagań dotyczących przechowywania danych.|Microsoft 365 E3 lub E5|
|Przenoszenie podstawowych danych do nowego geolokalizacji centrum danych|W związku z tym, że firma Microsoft dodaje nowe lokalizacje geograficzne centrum danych w celu dodatkowych zasobów obliczeniowych i obliczeniowych, możesz zażądać przeniesienia geolokalizacji centrum danych dla przechowywania danych w lokalizacji geograficznej dla swoich podstawowych danych klienta.|Microsoft 365 E3 lub E5|
||||

### <a name="networking"></a>Sieci

|Funkcja lub funkcja|Opis|Licencjonowanie|
|---|---|---|
|Sieć Szczegółowe informacje|Metryki wydajności sieci zebrane z Twojej dzierżawy usługi Microsoft 365 ułatwiają projektowanie obwodów sieci dla lokalizacji biura.|Microsoft 365 E3 lub E5|
|Automatyzowanie aktualizacji punktów końcowych|Automatyzowanie konfiguracji i bieżących aktualizacji dla Microsoft 365 końcowych w plikach PAC klienta oraz urządzeniach sieciowych i usługach.|Microsoft 365 E3 lub E5|
||||

### <a name="identity"></a>Tożsamości

|Funkcja lub funkcja|Opis|Licencjonowanie|
|---|---|---|
|Synchronizowanie danych lokalnych Usługi domenowe w usłudze Active Directory (AD DS) z dzierżawą usługi Azure AD|Skorzystaj z lokalnego dostawcy tożsamości dla kont użytkowników, grup i innych obiektów.|Microsoft 365 E3 lub E5|
|Uwierzytelniania wieloskładnikowego wymuszane przy użyciu domyślnych ustawień zabezpieczeń|Chroń przed naruszoną tożsamością i urządzeniami, wymagając drugiej formy uwierzytelniania dla logowania. Ustawienia domyślne zabezpieczeń wymagają uwierzytelniania MFA dla wszystkich kont użytkowników.|Microsoft 365 E3 lub E5|
|Uwierzytelniania wieloskładnikowego z dostępem warunkowym|Wymaganie uwierzytelniania WIELOSKŁADNIKOWEGO na podstawie atrybutów logowania przy użyciu zasad dostępu warunkowego.|Microsoft 365 E3 lub E5|
|Uwierzytelniania wieloskładnikowego z dostępem warunkowym opartym na czynniku ryzyka|Wymagaj uwierzytelniania wieloskładnikowego na podstawie ryzyka związanego z logowaniem użytkownika za pomocą programu Microsoft Defender for Identity.|Microsoft 365 E5 lub E3 z Azure AD — wersja Premium P2 licencji|
|Self-Service resetowania hasła (SSPR)|Zezwalaj użytkownikom na resetowanie lub odblokowywanie swoich haseł lub kont.|Microsoft 365 E3 lub E5|
||||

### <a name="migration"></a>Migracja

|Funkcja lub funkcja|Opis|Licencjonowanie|
|---|---|---|
|Migrowanie do Windows 10|Przemigruj urządzenia z systemem Windows 7 lub Windows 8.1 do Windows 10 Enterprise.|Windows 10 Enterprise licencji dołączonych do Microsoft 365 E3 lub E5|
|Migrowanie do Aplikacje Microsoft 365 dla przedsiębiorstw|Przemigruj Office klienckich, takich jak Word PowerPoint, do wersji zainstalowanych z chmury zaktualizowanych o nowe funkcje.|Microsoft 365 E3 lub E5|
|Migrowanie danych i serwerów lokalnych do Microsoft 365|Przemigruj Exchange pocztowe, witryny SharePoint i usługi Skype dla firm Online do Microsoft 365 usług w chmurze.|Microsoft 365 E3 lub E5|
||||

### <a name="device-and-app-management"></a>Zarządzanie urządzeniami i aplikacją

|Funkcja lub funkcja|Opis|Licencjonowanie|
|---|---|---|
|Microsoft Intune|Usługa oparta na chmurze, która zapewnia zarządzanie urządzeniami przenośnymi (MDM) i zarządzanie aplikacjami mobilnymi (MAM) w celu kontrolowania sposobu stosowania aplikacji organizacji i urządzeń, w tym telefonów komórkowych, tabletów i laptopów.|Microsoft 365 E3 lub E5|
|Podstawowa mobilność i zabezpieczenia|Zabezpieczaj urządzenia przenośne użytkowników, takie jak telefony iPhone, tablety iPad, urządzenia z systemem Android Windows telefonach komórkowych za pomocą tej wbudowanej usługi i zarządzanie nimi.|Microsoft 365 E3 lub E5|
||||

## <a name="next-steps"></a>Następne kroki

Skorzystaj z tych kroków, aby skonfigurować dzierżawy usługi i zarządzać Microsoft 365 dzierżawami.

1. [Określanie dzierżaw](tenant-management-tenants.md)
2. [Optymalizowanie sieci](tenant-management-networking.md)
3. [Synchronizowanie tożsamości i wymuszanie bezpiecznego logowania](tenant-management-identity.md)
4. [Migrowanie lokalnych serwerów Office i danych](tenant-management-migration.md)
5. [Wdrażanie zarządzania urządzeniami i aplikacją](tenant-management-device-management.md)

[![Kroki wdrażania dzierżawy Microsoft 365 i zarządzania nimi.](../media/tenant-management-overview/tenant-management-step-grid.png)](tenant-management-tenants.md)

W każdym kroku opisano opcje wdrażania, podsumowano wyniki i bieżące zadania konserwacji.

Aby dowiedzieć się, jak fikcyjna, ale reprezentatywna organizacja wielonarodowa wdrożyła elementy Microsoft 365 dzierżawie firmy Contoso, zobacz analizę [przypadku firmy Contoso](../enterprise/contoso-case-study.md).
