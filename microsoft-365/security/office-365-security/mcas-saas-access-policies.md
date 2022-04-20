---
title: Zalecane zasady Microsoft Defender for Cloud Apps dla aplikacji SaaS — Microsoft 365 Enterprise | Microsoft Docs
description: W tym artykule opisano zalecane zasady integracji z Microsoft Defender for Cloud Apps.
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
ms.openlocfilehash: a53666c58c8a9cc5793d160c428bc96ea322b274
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945544"
---
# <a name="recommended-microsoft-defender-for-cloud-apps-policies-for-saas-apps"></a>Zalecane zasady Microsoft Defender for Cloud Apps dla aplikacji SaaS

Microsoft Defender for Cloud Apps opiera się na zasadach dostępu warunkowego usługi Azure AD, aby umożliwić monitorowanie w czasie rzeczywistym i kontrolę szczegółowych akcji za pomocą aplikacji SaaS, takich jak blokowanie pobierania, przekazywania, kopiowania i wklejania oraz drukowania. Ta funkcja dodaje zabezpieczenia do sesji, które wiążą się z nieodłącznym ryzykiem, na przykład wtedy, gdy dostęp do zasobów firmy jest uzyskiwany z urządzeń niezarządzanych lub przez użytkowników-gości.

Defender dla Chmury Apps integruje się również natywnie z usługą Microsoft Purview Information Protection, zapewniając inspekcję zawartości w czasie rzeczywistym w celu znalezienia poufnych danych na podstawie poufnych typów informacji i etykiet poufności oraz podjęcia odpowiednich działań.

Te wskazówki obejmują zalecenia dotyczące następujących scenariuszy:

- Wprowadzanie aplikacji SaaS do zarządzania IT
- Dostrajanie ochrony dla określonych aplikacji SaaS
- Konfigurowanie ochrony przed utratą danych (DLP) w usłudze Microsoft Purview w celu zapewnienia zgodności z przepisami dotyczącymi ochrony danych

## <a name="bring-saas-apps-into-it-management"></a>Wprowadzanie aplikacji SaaS do zarządzania IT

Pierwszym krokiem przy użyciu usługi Defender dla Chmury Apps do zarządzania aplikacjami SaaS jest ich odnalezienie, a następnie dodanie ich do dzierżawy usługi Azure AD. Jeśli potrzebujesz pomocy dotyczącej odnajdywania, zobacz [Odnajdywanie aplikacji SaaS i zarządzanie nimi w sieci](/cloud-app-security/tutorial-shadow-it). Po odnalezieniu aplikacji [dodaj je do dzierżawy usługi Azure AD](/azure/active-directory/manage-apps/add-application-portal).

Możesz zacząć nimi zarządzać, wykonując następujące czynności:

1. Najpierw w usłudze Azure AD utwórz nowe zasady dostępu warunkowego i skonfiguruj je tak, aby "Używać kontroli aplikacji dostępu warunkowego". Spowoduje to przekierowanie żądania do Defender dla Chmury Apps. Możesz utworzyć jedną zasadę i dodać wszystkie aplikacje SaaS do tych zasad.
1. Następnie w Defender dla Chmury Apps utwórz zasady sesji. Utwórz jedną zasadę dla każdej kontrolki, którą chcesz zastosować.

Uprawnienia do aplikacji SaaS są zwykle oparte na potrzebach biznesowych dostępu do aplikacji. Te uprawnienia mogą być wysoce dynamiczne. Korzystanie z zasad Defender dla Chmury Apps zapewnia ochronę danych aplikacji niezależnie od tego, czy użytkownicy są przypisani do grupy usługi Azure AD skojarzonej z punktem początkowym, przedsiębiorstwem czy wyspecjalizowaną ochroną zabezpieczeń.

Aby chronić dane w kolekcji aplikacji SaaS, na poniższym diagramie przedstawiono niezbędne zasady dostępu warunkowego usługi Azure AD oraz sugerowane zasady, które można utworzyć w usłudze Defender dla Chmury Apps. W tym przykładzie zasady utworzone w usłudze Defender dla Chmury Apps mają zastosowanie do wszystkich aplikacji SaaS, które zarządzasz. Są one przeznaczone do stosowania odpowiednich kontrolek w zależności od tego, czy urządzenia są zarządzane, a także etykiety poufności, które są już stosowane do plików.

:::image type="content" source="../../media/microsoft-365-policies-configurations/mcas-manage-saas-apps-2.png" alt-text="Zasady zarządzania aplikacjami SaaS w usłudze Defender dla Chmury Apps" lightbox="../../media/microsoft-365-policies-configurations/mcas-manage-saas-apps-2.png":::

W poniższej tabeli wymieniono nowe zasady dostępu warunkowego, które należy utworzyć w usłudze Azure AD.

|Poziom ochrony|Zasad|Więcej informacji|
|---|---|---|
|Wszystkie poziomy ochrony|[Używanie kontroli dostępu warunkowego w aplikacjach Defender dla Chmury](/cloud-app-security/proxy-deployment-aad#configure-integration-with-azure-ad)|Spowoduje to skonfigurowanie dostawcy tożsamości (Azure AD) do pracy z aplikacjami Defender dla Chmury.|
||||

W następnej tabeli wymieniono przykładowe zasady przedstawione powyżej, które można utworzyć w celu ochrony wszystkich aplikacji SaaS. Pamiętaj o ocenie własnych celów biznesowych, zabezpieczeń i zgodności, a następnie o utworzeniu zasad zapewniających najbardziej odpowiednią ochronę środowiska.

|Poziom ochrony|Zasad|
|---|---|
|Punkt początkowy|Monitorowanie ruchu z urządzeń niezarządzanych <p> Dodawanie ochrony do pobierania plików z urządzeń niezarządzanych|
|Enterprise|Blokuj pobieranie plików oznaczonych etykietą poufną lub sklasyfikowaną z urządzeń niezarządzanych (zapewnia to dostęp tylko do przeglądarki)|
|Wyspecjalizowane zabezpieczenia|Blokuj pobieranie plików oznaczonych etykietą sklasyfikowaną ze wszystkich urządzeń (zapewnia to dostęp tylko do przeglądarki)|
|||

Aby uzyskać kompleksowe instrukcje dotyczące konfigurowania kontroli aplikacji dostępu warunkowego, zobacz [Wdrażanie kontroli aplikacji dostępu warunkowego dla polecanych aplikacji](/cloud-app-security/proxy-deployment-aad). W tym artykule przedstawiono proces tworzenia niezbędnych zasad dostępu warunkowego w usłudze Azure AD i testowania aplikacji SaaS.

Aby uzyskać więcej informacji, zobacz [Protect apps with Microsoft Defender for Cloud Apps Conditional Access App Control (Ochrona aplikacji za pomocą Microsoft Defender for Cloud Apps kontroli aplikacji dostępu warunkowego](/cloud-app-security/proxy-intro-aad)).

## <a name="tune-protection-for-specific-saas-apps"></a>Dostrajanie ochrony dla określonych aplikacji SaaS

Możesz zastosować dodatkowe kontrolki i monitorowanie do określonych aplikacji SaaS w środowisku. Defender dla Chmury Apps pozwala to osiągnąć. Jeśli na przykład aplikacja taka jak Box jest intensywnie używana w twoim środowisku, warto zastosować dodatkowe kontrolki. Jeśli też dział prawny lub finansowy używa określonej aplikacji SaaS do przechowywania poufnych danych biznesowych, możesz zastosować dodatkową ochronę tych aplikacji.

Na przykład możesz chronić środowisko box za pomocą tego typu wbudowanych szablonów zasad wykrywania anomalii:

- Działanie z anonimowych adresów IP
- Aktywność z rzadkiego kraju
- Działanie z podejrzanych adresów IP
- Niemożliwa podróż
- Działanie wykonywane przez użytkownika zakończone (wymaga AAD jako dostawcy tożsamości)
- Wykrywanie złośliwego oprogramowania
- Wiele nieudanych prób logowania
- Działanie wymuszające okup
- Ryzykowna aplikacja Oauth
- Nietypowe działanie udziału plików

Oto przykłady. Dodatkowe szablony zasad są regularnie dodawane. Przykłady stosowania dodatkowej ochrony do określonych aplikacji można znaleźć w temacie [Ochrona połączonych aplikacji](/cloud-app-security/protect-connected-apps).

[Sposób, w jaki Defender dla Chmury Apps pomaga chronić środowisko box](/cloud-app-security/protect-box), pokazuje typy kontrolek, które mogą pomóc w ochronie danych biznesowych w usłudze Box i innych aplikacjach przy użyciu poufnych danych.

## <a name="configure-data-loss-prevention-dlp-to-help-comply-with-data-protection-regulations"></a>Konfigurowanie ochrony przed utratą danych (DLP) w celu zapewnienia zgodności z przepisami dotyczącymi ochrony danych

Defender dla Chmury Aplikacje mogą być cennym narzędziem do konfigurowania ochrony przepisów dotyczących zgodności. W takim przypadku utworzysz określone zasady w celu wyszukania konkretnych danych, których dotyczy rozporządzenie, i skonfigurowania poszczególnych zasad w celu podjęcia odpowiednich działań.

Poniższa ilustracja i tabela zawierają kilka przykładów zasad, które można skonfigurować w celu zapewnienia zgodności z ogólnym rozporządzeniem o ochronie danych (RODO). W tych przykładach zasady poszukają konkretnych danych. Na podstawie poufności danych każda zasada jest skonfigurowana do podejmowania odpowiednich działań.

:::image type="content" source="../../media/microsoft-365-policies-configurations/mcas-dlp.png" alt-text="Strona zasady Defender dla Chmury Apps dotyczące zapobiegania utracie danych" lightbox="../../media/microsoft-365-policies-configurations/mcas-dlp.png":::

|Poziom ochrony|Przykładowe zasady|
|---|---|
|Punkt początkowy|Alert, gdy pliki zawierające ten typ informacji poufnych ("Numer karty kredytowej") są udostępniane poza organizacją <p> >Blokuj pobieranie plików zawierających ten typ informacji poufnych ("Numer karty kredytowej") na urządzenia niezarządzane|
|Enterprise|Ochrona plików zawierających ten typ informacji poufnych ("Numer karty kredytowej") na urządzeniach zarządzanych <p> Blokuj pobieranie plików zawierających ten typ informacji poufnych ("Numer karty kredytowej") na urządzenia niezarządzane <p> Alert po przekazaniu pliku z tymi etykietami do OneDrive dla Firm lub Box (dane klienta, zasoby ludzkie: dane wynagrodzeń, zasoby ludzkie, dane pracowników)|
|Wyspecjalizowane zabezpieczenia|Alert, gdy pliki z tą etykietą ("Wysoce sklasyfikowane") są pobierane na urządzenia zarządzane <p> Blokuj pobieranie plików z tą etykietą ("Wysoce sklasyfikowane") na urządzenia niezarządzane|
|||

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji na temat korzystania z aplikacji Defender dla Chmury, zobacz [dokumentację Microsoft Defender for Cloud Apps](//cloud-app-security/).
