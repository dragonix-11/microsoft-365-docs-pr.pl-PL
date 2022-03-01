---
title: Microsoft 365 planu wdrażania Zerowe zaufanie
f1.keywords:
- deploy zero trust
- zero trust strategy
ms.author: bcarter
author: brendacarter
manager: dansimp
audience: Admin
description: Dowiedz się, jak wdrożyć w środowisku zabezpieczenia Microsoft 365 zerowego zaufania w celu obrony przed zagrożeniami i ochrony poufnych danych.
ms.topic: tutorial
ms.prod: m365-security
ms.technology: m365d
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- m365solution-zerotrust
- m365solution-overview
- M365-security-compliance
ms.openlocfilehash: 9b37e353af74b7a01c0647f99b149f5fac0ae8a3
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/10/2022
ms.locfileid: "63011273"
---
# <a name="microsoft-365-zero-trust-deployment-plan"></a>Microsoft 365 planu wdrażania Zerowe zaufanie

Ten artykuł zawiera plan wdrażania na rzecz budowania zabezpieczeń **zerowego** zaufania za pomocą Microsoft 365. Zero zaufania to nowy model zabezpieczeń, który zakłada naruszenie i sprawdza każde żądanie, tak jakby pochodziło z sieci niepod kontroli. Niezależnie od tego, skąd pochodzi żądanie lub do jakiego zasobu uzyskuje dostęp, w modelu zerowego zaufania uczy nas, jak "nigdy nie ufać, zawsze weryfikować".


## <a name="zero-trust-security-architecture"></a>Architektura zabezpieczeń Zero Trust

Podejście Zerowe zaufanie obejmuje całe cyfrowe rynku i służy jako zintegrowana strategia bezpieczeństwa. 

Na poniższej ilustracji przedstawiono podstawowe elementy współtworące poziom zerowego zaufania.

<!---
[![Zero Trust security architecture](../media/zero-trust/zero-trust-architecture.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/zero-trust/zero-trust-architecture.png)
-->

:::image type="content" source="../media/zero-trust/zero-trust-architecture.png" alt-text="Architektura zabezpieczeń Zero Trust" lightbox="../media/zero-trust/zero-trust-architecture.png":::



Na ilustracji:
- Wymuszanie zasad zabezpieczeń stanowi centrum architektury zerowego zaufania. Obejmuje to uwierzytelnianie wieloskładnikowe z dostępem warunkowym, które uwzględnia ryzyko związane z kontem użytkownika, stan urządzenia i inne ustawione kryteria i zasady.
- Tożsamości, urządzenia, dane, aplikacje, sieć i inne składniki infrastruktury są skonfigurowane z odpowiednim zabezpieczeniem. Zasady skonfigurowane dla każdego z tych składników są skoordynowane z ogólną strategią zerowego zaufania. Na przykład zasady dotyczące urządzeń określają kryteria dla urządzeń o dobrej kondycji, a zasady dostępu warunkowego wymagają urządzeń o dobrej kondycji w celu uzyskiwania dostępu do określonych aplikacji i danych.
- Ochrona przed zagrożeniami i inteligencja monitoruje środowisko, monitoruje bieżące czynniki ryzyka oraz automatycznie podejmuje działania w celu rozwiązywania ataków.

<!---
For more information about this architecture, including deployment objectives for your entire digital estate, see [Zero Trust Rapid Modernization Plan (RaMP)](https://review.docs.microsoft.com/security/zero-trust/zero-trust-ramp-overview?branch=zt-content-prototype). 
-->

Aby uzyskać więcej informacji na temat zerowego zaufania, zobacz Centrum wskazówek [_**dotyczących zerowego zaufania firmy Microsoft**_](/security/zero-trust).

## <a name="deploying-zero-trust-for-microsoft-365"></a>Wdrażanie zerowego zaufania dla Microsoft 365

Microsoft 365 została celowo zbudowana z wielu funkcji zabezpieczeń i ochrony informacji, które ułatwiają tworzenie środowiska zerowym zaufaniem. Wiele z funkcji można rozszerzyć, aby chronić dostęp do innych aplikacji SaaS, z których korzysta Twoja organizacja, oraz danych w tych aplikacjach.

Ta ilustracja przedstawia sposób wdrażania funkcji zerowego zaufania. Ta praca jest podzielone na jednostki pracy, które można skonfigurować razem, od dołu do góry i od góry w celu zapewnienia, że praca wymaga wymaganej pracy jest ukończona.


:::image type="content" source="../media/zero-trust/m365-zero-trust-deployment-stack.png" alt-text="Microsoft 365 stosu wdrażania Bez zaufania" lightbox="../media/zero-trust/m365-zero-trust-deployment-stack.png":::

Na poniższej ilustracji:
- Poziom Zerowe zaufanie zaczyna się od podstaw: tożsamości i ochrony urządzeń. 
- Funkcje ochrony przed zagrożeniami są wbudowane w tę podstawę w celu zapewnienia monitorowania i korygowania zagrożeń bezpieczeństwa w czasie rzeczywistym. 
- Ochrona informacji i zarządzanie zapewnia zaawansowane mechanizmy kontroli ukierunkowane na określone typy danych w celu ochrony najcenniejszych informacji i zapewnienia zgodności ze standardami zgodności, w tym ochrony informacji osobistych.

## <a name="step-1-configure-zero-trust-identity-and-device-access-protection--starting-point-policies"></a>Krok nr 1. Konfigurowanie ochrony dostępu do urządzeń i tożsamości zerowym zaufaniem — zasady od początku

Pierwszym krokiem jest skonfigurowanie tożsamości i ochrony dostępu do urządzeń przez skonfigurowanie programu Zero Trust Foundation. 


:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-1b.png" alt-text="Konfigurowanie ochrony dostępu do urządzeń i tożsamości bez zaufania" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-1b.png":::



Aby to [**_zrobić, przejdź_**](office-365-security/microsoft-365-policies-configurations.md) do tematu Ochrona dostępu do urządzeń i tożsamości bez zaufania. W tej serii artykułów opisano zestaw konfiguracji wymagań wstępnych dotyczących tożsamości i dostępu do urządzeń oraz zestaw reguł dostępu warunkowego programu Azure Active Directory (Azure AD), usługi Microsoft Intune i innych zasad, które zabezpieczą dostęp do Microsoft 365  dla usług i aplikacji w chmurze przedsiębiorstwa, innych usług SaaS oraz aplikacji lokalnych opublikowanych przy użyciu serwera proxy aplikacji Azure AD.



|Zawiera  |Wymagania wstępne  |Nie zawiera  |
|---------|---------|---------|
|Zalecane zasady dostępu do urządzeń i tożsamości dla trzech poziomów ochrony:<br>— punkt początkowy<br>- Enterprise (zalecane)<br>- Specjalistyczne<br><br>Dodatkowe zalecenia dotyczące:<br>- Użytkownicy zewnętrzni (goście)<br>— Microsoft Teams<br>— SharePoint online<br>- Microsoft Defender dla aplikacji w chmurze| Microsoft E3 lub E5<br><br>Azure Active Directory w jednym z tych trybów:<br>- Tylko w chmurze<br>- Tryb hybrydowy z uwierzytelnianiem funkcji synchronizacji skrótów haseł (PHS, Password Hash Sync)<br>— Tryb hybrydowy z uwierzytelnianiem pass-through (PTA)<br>- Federowany     |Rejestracja urządzeń dla zasad wymagających urządzeń zarządzanych. Zobacz "Zarządzanie punktami końcowymi za pomocą usługi Intune", aby zarejestrować urządzenia |
| | | |

Zacznij od wdrożenia warstwy punktu początkowego. Te zasady nie wymagają rejestrowania urządzeń do zarządzania. 


:::image type="content" source="../media/zero-trust/identity-access-starting-point-tier.png" alt-text="Zasady zerowego zaufania w zakresie tożsamości i dostępu do urządzeń — warstwa początkowa" lightbox="../media/zero-trust/identity-access-starting-point-tier.png":::


## <a name="step-2-manage-endpoints-with-intune"></a>Krok nr 2. Zarządzanie punktami końcowymi za pomocą usługi Intune

Następnie zarejestruj urządzenia do zarządzania i zacznij ich chronić za pomocą bardziej zaawansowanych kontrolek. 

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-2.png" alt-text="Zarządzanie punktami końcowymi za pomocą usługi Intune" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-2.png":::


Aby to [**_zrobić, przejdź_**](../solutions/manage-devices-with-intune-overview.md) do tematu Zarządzanie urządzeniami za pomocą usługi Intune, aby uzyskać wskazówki wstępne. 


|Zawiera  |Wymagania wstępne  |Nie zawiera  |
|---------|---------|---------|
|Zarejestruj urządzenia za pomocą usługi Intune<br>— Urządzenia firmowe<br>- Automatyczny/automatyczny<br>— rejestracja<br><br>Konfigurowanie zasad<br>- Zasady ochrony aplikacji<br>- Zasady zgodności<br>- Zasady dotyczące profilów urządzeń | Rejestrowanie punktów końcowych w usłudze Azure AD     | Konfigurowanie funkcji ochrony informacji, w tym:<br>- Typy informacji poufnych<br>- Etykiety<br>- Zasady DLP<br>Aby uzyskać te możliwości, zobacz Krok 5. Ochrona danych i zarządzania danymi (w dalszej części tego artykułu).       |
|    |         |         |

## <a name="step-3-add-zero-trust-identity-and-device-access-protection--enterprise-policies"></a>Krok nr 3. Dodawanie zasad zerowego zaufania w zakresie tożsamości i dostępu do urządzeń Enterprise urządzenia

Po zarejestrowaniu urządzeń w zarządzaniu można teraz zaimplementować pełny zestaw zalecanych zasad dostępu do urządzeń i tożsamości zerowego zaufania, wymagających zgodności urządzeń.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png" alt-text="Zasady zerowego zaufania w zakresie tożsamości i dostępu dzięki zarządzaniu urządzeniami" lightbox="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png":::

Wróć do [**_wspólnych zasad dostępu do urządzeń_**](office-365-security/identity-access-policies.md) i tożsamości oraz dodaj zasady w Enterprise danych.  

:::image type="content" source="../media/zero-trust/identity-access-enterprise-tier.png" alt-text="Zasady zerowego zaufania w zakresie tożsamości i dostępu — Enterprise (zalecana) warstwa" lightbox="../media/zero-trust/identity-access-enterprise-tier.png":::

## <a name="step-4-evaluate-pilot-and-deploy-microsoft-365-defender"></a>Krok nr 4. Ocenianie, wdrożenie pilotażowe i wdrażanie Microsoft 365 Defender

Microsoft 365 Defender to rozwiązanie do rozszerzonego wykrywania i odpowiedzi (XDR, extended detection and response), które automatycznie zbiera, koreluje i analizuje dane sygnału, zagrożeń i alertów z całego środowiska usługi Microsoft 365, w tym punktu końcowego, poczty e-mail, aplikacji i tożsamości.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-defender.png" alt-text="Dodawanie Microsoft 365 Defender do architektury zerowego zaufania" lightbox="../media/zero-trust/m365-zero-trust-architecture-defender.png":::

Przejdź do [**_tematu Ocena i Microsoft 365 Defender_**](defender/eval-overview.md), aby uzyskać przewodnik metodyczny dotyczący wdrażania pilotażowego i wdrażania Microsoft 365 Defender składników. 

|Zawiera  |Wymagania wstępne  |Nie zawiera  |
|---------|---------|---------|
| Skonfiguruj środowisko oceny i pilotażu dla wszystkich składników:<br>- Defender for Identity<br>- Defender for Office 365<br>- Defender for Endpoint<br>- Microsoft Defender dla aplikacji w chmurze<br><br>Ochrona przed zagrożeniami<br><br> Badanie zagrożeń i reagowanie na nie   | Zapoznaj się z wskazówkami, aby przeczytać o wymaganiach dotyczących architektury poszczególnych składników Microsoft 365 Defender.        | Usługa Azure AD Identity Protection nie jest uwzględniona w tym przewodniku po rozwiązaniu. Został on uwzględniony w Kroku 1: Konfigurowanie ochrony dostępu do urządzeń i tożsamości bez zaufania.        |
|    |         |         |

## <a name="step-5-protect-and-govern-sensitive-data"></a>Krok nr 5. Ochrona danych poufnych i ich ochrona

Wdrożenie Microsoft Information Protection (MIP) w celu odnajdowania, klasyfikowania i ochrony informacji poufnych niezależnie od miejsca życia lub podróży.

Funkcje miP są zawarte w funkcji zgodności Microsoft 365 i zapewniają narzędzia do poznania danych, ochrony danych i zapobiegania utracie danych.


:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-info-protect.png" alt-text="Funkcje ochrony informacji chronią dane za pośrednictwem wymuszania zasad" lightbox="../media/zero-trust/m365-zero-trust-architecture-info-protect.png":::

Mimo że ta praca jest reprezentowana w górnej części stosu wdrażania przedstawionego wcześniej w tym artykule, możesz rozpocząć tę pracę w dowolnym momencie. 

Microsoft Information Protection zapewnia ramę, proces i możliwości, których można użyć do zrealizowania określonych celów biznesowych.

![Microsoft Information Protection (MIP)](../media/zero-trust/mip-solution-overview.png)

Aby uzyskać więcej informacji na temat planowania i wdrażania ochrony informacji, zobacz [**_Wdrażanie Microsoft Information Protection informacji_**](../compliance/information-protection-solution.md). 

W przypadku wdrażania ochrony informacji dla przepisów o ochronie prywatności danych w tym przewodniku po rozwiązaniu odano zalecaną ramę dla całego [**_procesu: wdrażanie_**](../solutions/information-protection-deploy.md) ochrony informacji dla przepisów dotyczących prywatności danych za pomocą Microsoft 365.