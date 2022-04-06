---
title: Zalecane Microsoft Defender for Cloud Apps dla aplikacji SaaS — Microsoft 365 Enterprise | Microsoft Docs
description: W tym artykule opisano zalecane zasady integracji z usługą Microsoft Defender for Cloud Apps.
author: BrendaCarter
manager: laurawi
ms.topic: article
audience: Admin
ms.author: bcarter
ms.date: 03/22/2021
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
ms.prod: m365-security
ms.openlocfilehash: 7cda1669b4f8441d13f92b09d7390e31f4add529
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472292"
---
# <a name="recommended-microsoft-defender-for-cloud-apps-policies-for-saas-apps"></a>Zalecane Microsoft Defender for Cloud Apps dla aplikacji SaaS

Microsoft Defender for Cloud Apps na podstawie zasad dostępu warunkowego usługi Azure AD w celu umożliwienia monitorowania w czasie rzeczywistym i kontrolowania szczegółowych działań w aplikacjach SaaS, takich jak blokowanie pobierania, przekazywania, kopiowania i wklejania oraz drukowania. Ta funkcja dodaje zabezpieczenia do sesji, które niosą ze sobą ryzyko naturalne, na przykład gdy zasoby firmowe są dostępne z urządzeń nieza zarządzaniem lub przez użytkowników gości.

Defender dla Chmury integruje się również natywnie z usługą Microsoft Information Protection, zapewniając inspekcję zawartości w czasie rzeczywistym w celu znalezienia poufnych danych na podstawie typów informacji poufnych i etykiet wrażliwości oraz do podjęcia odpowiednich działań.

Wskazówki te zawierają zalecenia dotyczące tych scenariuszy:

- Wniesienie aplikacji SaaS do zarządzania it
- Dostosowywanie ochrony dla określonych aplikacji SaaS
- Konfigurowanie ochrony przed utratą danych (DLP) w celu zapewnienia zgodności z przepisami dotyczącymi ochrony danych

## <a name="bring-saas-apps-into-it-management"></a>Wniesienie aplikacji SaaS do zarządzania it

Pierwszym krokiem korzystania z aplikacji Defender dla Chmury do zarządzania aplikacjami SaaS jest ich odnajdowanie, a następnie dodanie ich do dzierżawy usługi Azure AD. Jeśli potrzebujesz pomocy w odnajdowaniach, zobacz [Odnajdowanie aplikacji SaaS i zarządzanie nimi w swojej sieci](/cloud-app-security/tutorial-shadow-it). Po odnalezioniu aplikacji [dodaj je do dzierżawy usługi Azure AD](/azure/active-directory/manage-apps/add-application-portal).

Możesz zacząć zarządzać tymi procesami, wykonując następujące czynności:

1. Najpierw w usłudze Azure AD utwórz nowe zasady dostępu warunkowego i skonfiguruj je tak, aby "Używanie kontrolki aplikacji dostępu warunkowego". To nastąpi przekierowywanie żądania do Defender dla Chmury Apps. Możesz utworzyć jedną politykę i dodać do nich wszystkie aplikacje SaaS.
1. Następnie na stronie Defender dla Chmury utwórz zasady sesji. Utwórz jedną zasady dla każdej kontrolki, którą chcesz zastosować.

Uprawnienia do aplikacji SaaS są zazwyczaj oparte na potrzebie biznesowej dotyczącej dostępu do aplikacji. Te uprawnienia mogą być bardzo dynamiczne. Zasady Defender dla Chmury aplikacji zapewniają ochronę danych aplikacji niezależnie od tego, czy użytkownicy są przypisani do grupy usługi Azure AD skojarzonej z punktem początkowym, przedsiębiorstwem, czy wyspecjalizowaną ochroną zabezpieczeń.

Aby chronić dane w zbiorze aplikacji SaaS, na poniższym diagramie przedstawiono niezbędne zasady dostępu warunkowego usługi Azure AD oraz sugerowane zasady, które można utworzyć w Defender dla Chmury Apps. W tym przykładzie zasady utworzone w aplikacji Defender dla Chmury są stosowane do wszystkich aplikacji SaaS, które zarządzasz. Te elementy zaprojektowano tak, aby stosować odpowiednie kontrolki w zależności od tego, czy urządzenia są zarządzane, oraz etykiety wrażliwości, które już zostały zastosowane do plików.

:::image type="content" source="../../media/microsoft-365-policies-configurations/mcas-manage-saas-apps-2.png" alt-text="Zasady zarządzania aplikacjami SaaS w aplikacji Defender dla Chmury Apps" lightbox="../../media/microsoft-365-policies-configurations/mcas-manage-saas-apps-2.png":::

W poniższej tabeli wymieniono nowe zasady dostępu warunkowego, które musisz utworzyć w usłudze Azure AD.

|Poziom ochrony|Zasady|Więcej informacji|
|---|---|---|
|Wszystkie poziomy ochrony|[Używanie kontrolki aplikacji dostępu warunkowego w Defender dla Chmury Aplikacje](/cloud-app-security/proxy-deployment-aad#configure-integration-with-azure-ad)|To skonfiguruje usługę IdP (Azure AD) do współpracy z Defender dla Chmury usługami.|
||||

W następnej tabeli pokazano przykładowe zasady przedstawione powyżej, które można utworzyć w celu ochrony wszystkich aplikacji SaaS. Koniecznie oceniaj cele swojej firmy, zabezpieczeń i zgodności, a następnie twórz zasady, które zapewniają najbardziej odpowiednią ochronę środowiska.

|Poziom ochrony|Zasady|
|---|---|
|Punkt początkowy|Monitorowanie ruchu z urządzeń nieza zarządzania <p> Dodawanie ochrony do pobierania plików z urządzeń niezawiązyanych|
|Enterprise|Blokowanie pobierania plików oznaczonych poufnymi lub sklasyfikowanych z urządzeń niezamanektowanych (zapewnia to dostęp tylko do przeglądarek)|
|Wyspecjalizowane zabezpieczenia|Blokowanie pobierania plików oznaczonych jako klasyfikowane ze wszystkich urządzeń (zapewnia to dostęp tylko do przeglądarek)|
|||

Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania kontroli aplikacji z dostępem warunkowym, zobacz Wdrażanie kontroli aplikacji dostępu warunkowego [dla polecanych aplikacji](/cloud-app-security/proxy-deployment-aad). Ten artykuł zawiera kroki tworzenia niezbędnych zasad dostępu warunkowego w usłudze Azure AD i testowania aplikacji SaaS.

Aby uzyskać więcej informacji, zobacz [Chroninie aplikacji za Microsoft Defender for Cloud Apps kontrola aplikacji dostępu warunkowego](/cloud-app-security/proxy-intro-aad).

## <a name="tune-protection-for-specific-saas-apps"></a>Dostosowywanie ochrony dla określonych aplikacji SaaS

Możesz zechcieć zastosować dodatkowe mechanizmy monitorowania i sterowania do określonych aplikacji SaaS w Twoim środowisku. Defender dla Chmury pozwala to osiągnąć. Jeśli na przykład aplikacja, na przykład Box, jest intensywnie używana w środowisku, warto zastosować dodatkowe kontrolki. Jeśli natomiast Twój dział prawny lub finansowy używa konkretnej aplikacji SaaS do przechowywania poufnych danych biznesowych, możesz dodatkowo chronić te aplikacje.

Na przykład możesz chronić środowisko box za pomocą następujących typów wbudowanych szablonów zasad wykrywania anomaly:

- Aktywność z anonimowych adresów IP
- Aktywność z kraju rzadkoszego
- Działania z podejrzanych adresów IP
- Niemożliwa podróż
- Działanie wykonane przez zakończonego użytkownika (wymaga AAD identyfikatora)
- Wykrywanie złośliwego oprogramowania
- Wiele nieudanych prób logowania
- Aktywność oprogramowania wymuszającego okup
- Ryzykowna aplikacja Oauth
- Nietypowe działania w zakresie udostępniania plików

To są przykłady. Regularnie dodawane są dodatkowe szablony zasad. Aby uzyskać przykłady stosowania dodatkowej ochrony do określonych aplikacji, zobacz [Chronienie połączonych aplikacji](/cloud-app-security/protect-connected-apps).

[Sposób Defender dla Chmury aplikacji](/cloud-app-security/protect-box) pomaga chronić środowisko boxa przedstawia typy kontrolek, które mogą pomóc chronić dane biznesowe w uścisce Box i innych aplikacjach przy użyciu poufnych danych.

## <a name="configure-data-loss-prevention-dlp-to-help-comply-with-data-protection-regulations"></a>Konfigurowanie ochrony przed utratą danych (DLP) w celu zapewnienia zgodności z przepisami dotyczącymi ochrony danych

Defender dla Chmury Aplikacje mogą być cennym narzędziem do konfigurowania ochrony przepisów dotyczących zgodności z przepisami. W takim przypadku tworzy się określone zasady w celu wyszukiwania konkretnych danych, których dotyczą przepisy, i konfigurowania poszczególnych zasad w celu podjęcia odpowiednich działań.

Na poniższej ilustracji i w poniższej tabeli przedstawiono kilka przykładów zasad, które można skonfigurować tak, aby zapewnić zgodność z Ogólnym rozporządzeniem o ochronie danych (RODO). W tych przykładach zasady obejmują określone dane. W zależności od wrażliwości danych każda zasada jest skonfigurowana do odpowiednich działań.

:::image type="content" source="../../media/microsoft-365-policies-configurations/mcas-dlp.png" alt-text="Strona Defender dla Chmury ochrony przed utratą danych w aplikacjach firmy Defender dla Chmury Apps" lightbox="../../media/microsoft-365-policies-configurations/mcas-dlp.png":::

|Poziom ochrony|Przykładowe zasady|
|---|---|
|Punkt początkowy|Alert, gdy pliki zawierające ten typ informacji poufnych ("Numer karty kredytowej") są udostępniane poza organizacją <p> >pobierania plików zawierających ten typ informacji poufnych ("Numer karty kredytowej") na urządzeniach niezawiązywanych|
|Enterprise|Ochrona plików pobieranych z tego typu informacji poufnych ("Numer karty kredytowej") na urządzeniach zarządzanych <p> Blokowanie pobierania plików zawierających informacje poufne tego typu (numer karty kredytowej) na urządzeniach niezawiązywanych <p> Alert, gdy plik z tymi etykietami zostanie przekazany do aplikacji OneDrive dla Firm lub Box (dane klienta, dział kadr: dane płac, zasoby ludzkie, dane pracowników)|
|Wyspecjalizowane zabezpieczenia|Alert, gdy pliki z tą etykietą ("Wysoce klasyfikowane") są pobierane na urządzenia zarządzane <p> Blokowanie pobierania plików o tej etykiecie ("Wysoce klasyfikowane") na urządzeniach niezawiązywanych|
|||

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji na temat Defender dla Chmury aplikacji, zobacz Microsoft Defender for Cloud Apps [dokumentacji](//cloud-app-security/).
