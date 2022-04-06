---
title: Plan wdrożenia platformy Microsoft 365 Zero Trust
f1.keywords:
- deploy zero trust
- zero trust strategy
ms.author: bcarter
author: brendacarter
manager: dansimp
audience: Admin
description: Dowiedz się, jak wdrożyć zabezpieczenia Microsoft 365 Zero Trust w środowisku w celu ochrony przed zagrożeniami i ochrony poufnych danych.
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
ms.openlocfilehash: f8ffdcb817763589dfb43f7389bc44b7a28459f2
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473062"
---
# <a name="microsoft-365-zero-trust-deployment-plan"></a>Plan wdrożenia platformy Microsoft 365 Zero Trust

Ten artykuł zawiera plan wdrażania w zakresie budowania **Zero Trust** zabezpieczeń za pomocą Microsoft 365. Zero Trust to nowy model zabezpieczeń, który zakłada naruszenie i sprawdza, czy każde żądanie pochodziło z sieci, która jest kontrolowana. Niezależnie od tego, skąd pochodzi żądanie lub do jakiego zasobu uzyskuje dostęp, w modelu Zero Trust w celu uzyskania informacji "nigdy nie ufaj, zawsze się sprawdza".


## <a name="zero-trust-security-architecture"></a>Zero Trust zabezpieczeń

Rozbudowane Zero Trust całego rynku cyfrowego i służy jako zintegrowana strategia bezpieczeństwa. 

Na poniższej ilustracji przedstawiono podstawowe elementy współtworące Zero Trust.

:::image type="content" source="../media/zero-trust/zero-trust-architecture.png" alt-text="Architektura Zero Trust zabezpieczeń" lightbox="../media/zero-trust/zero-trust-architecture.png":::

Na ilustracji:
- Wymuszanie zasad zabezpieczeń stanowi centrum Zero Trust zabezpieczeń. Obejmuje to uwierzytelnianie wieloskładnikowe z dostępem warunkowym, które uwzględnia ryzyko związane z kontem użytkownika, stan urządzenia i inne ustawione kryteria i zasady.
- Tożsamości, urządzenia, dane, aplikacje, sieć i inne składniki infrastruktury są skonfigurowane z odpowiednim zabezpieczeniem. Zasady skonfigurowane dla każdego z tych składników są skoordynowane z ogólną Zero Trust strategii. Na przykład zasady dotyczące urządzeń określają kryteria dla urządzeń o dobrej kondycji, a zasady dostępu warunkowego wymagają urządzeń o dobrej kondycji w celu uzyskiwania dostępu do określonych aplikacji i danych.
- Ochrona przed zagrożeniami i inteligencja monitoruje środowisko, monitoruje bieżące czynniki ryzyka oraz automatycznie podejmuje działania w celu rozwiązywania ataków.

<!---
For more information about this architecture, including deployment objectives for your entire digital estate, see [Zero Trust Rapid Modernization Plan (RaMP)](https://review.docs.microsoft.com/security/zero-trust/zero-trust-ramp-overview?branch=zt-content-prototype). 
-->

Aby uzyskać więcej informacji Zero Trust, zobacz Centrum Zero Trust [_**firmy Microsoft**_](/security/zero-trust).

## <a name="deploying-zero-trust-for-microsoft-365"></a>Wdrażanie usługi Zero Trust dla Microsoft 365

Microsoft 365 została celowo zbudowana z wielu funkcji zabezpieczeń i ochrony informacji, które ułatwiają Zero Trust w środowisku. Wiele z funkcji można rozszerzyć, aby chronić dostęp do innych aplikacji SaaS, z których korzysta Twoja organizacja, oraz danych w tych aplikacjach.

Ta ilustracja przedstawia pracę nad wdrażaniem Zero Trust możliwości. Ta praca jest podzielone na jednostki pracy, które można skonfigurować razem, od dołu do góry i od góry w celu zapewnienia, że praca wymaga wymaganej pracy jest ukończona.


:::image type="content" source="../media/zero-trust/m365-zero-trust-deployment-stack.png" alt-text="Stos Microsoft 365 Zero Trust wdrażania" lightbox="../media/zero-trust/m365-zero-trust-deployment-stack.png":::

Na poniższej ilustracji:
- Zero Trust się od podstaw tożsamości i ochrony urządzeń. 
- Funkcje ochrony przed zagrożeniami są wbudowane w tę podstawę w celu zapewnienia monitorowania i korygowania zagrożeń bezpieczeństwa w czasie rzeczywistym. 
- Ochrona informacji i zarządzanie zapewnia zaawansowane mechanizmy kontroli ukierunkowane na określone typy danych w celu ochrony najcenniejszych informacji i zapewnienia zgodności ze standardami zgodności, w tym ochrony informacji osobistych.

## <a name="step-1-configure-zero-trust-identity-and-device-access-protection--starting-point-policies"></a>Krok nr 1. Konfigurowanie Zero Trust tożsamości i ochrony dostępu do urządzeń — zasady punktu początkowego

Pierwszym krokiem jest zbudowanie podstaw Zero Trust przez skonfigurowanie tożsamości i ochrony dostępu do urządzeń. 


:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-1b.png" alt-text="Proces konfigurowania tożsamości Zero Trust ochrony dostępu do urządzeń" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-1b.png":::



Aby to [**_Zero Trust_**](office-365-security/microsoft-365-policies-configurations.md), przejdź do tematu Ochrona tożsamości i dostępu do urządzenia, aby uzyskać wskazówki wstępne. W tej serii artykułów opisano zestaw konfiguracji wymagań wstępnych dotyczących tożsamości i dostępu do urządzeń oraz zestaw reguł dostępu warunkowego programu Azure Active Directory (Azure AD), usługi Microsoft Intune i innych zasad, które zabezpieczą dostęp do Microsoft 365  dla usług i aplikacji w chmurze przedsiębiorstwa, innych usług SaaS oraz aplikacji lokalnych opublikowanych w usłudze Azure AD serwer proxy aplikacji.



|Zawiera  |Wymagania wstępne  |Nie zawiera  |
|---------|---------|---------|
|Zalecane zasady dostępu do urządzeń i tożsamości dla trzech poziomów ochrony:<br>— punkt początkowy<br>- Enterprise (zalecane)<br>- Specjalistyczne<br><br>Dodatkowe zalecenia dotyczące:<br>- Użytkownicy zewnętrzni (goście)<br>— Microsoft Teams<br>— SharePoint online<br>— Microsoft Defender for Cloud Apps| Microsoft E3 lub E5<br><br>Azure Active Directory w jednym z tych trybów:<br>- Tylko w chmurze<br>- Tryb hybrydowy z uwierzytelnianiem funkcji synchronizacji skrótów haseł (PHS, Password Hash Sync)<br>— Tryb hybrydowy z uwierzytelnianiem pass-through (PTA)<br>- Federowany     |Rejestracja urządzeń dla zasad wymagających urządzeń zarządzanych. Zobacz "Zarządzanie punktami końcowymi za pomocą Intune", aby zarejestrować urządzenia. |
| | | |

Zacznij od wdrożenia warstwy punktu początkowego. Te zasady nie wymagają rejestrowania urządzeń do zarządzania. 


:::image type="content" source="../media/zero-trust/identity-access-starting-point-tier.png" alt-text="Zasady Zero Trust dostępu do urządzeń i tożsamości — warstwa punktowa" lightbox="../media/zero-trust/identity-access-starting-point-tier.png":::


## <a name="step-2-manage-endpoints-with-intune"></a>Krok nr 2. Zarządzanie punktami końcowymi za pomocą Intune

Następnie zarejestruj urządzenia do zarządzania i zacznij ich chronić za pomocą bardziej zaawansowanych kontrolek. 

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-2.png" alt-text="Element Zarządzanie punktami końcowymi Intune punktami końcowymi" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-2.png":::


Przejdź do [**_tematu Zarządzanie urządzeniami za Intune_**](../solutions/manage-devices-with-intune-overview.md), aby uzyskać wskazówki wstępne, aby to zrobić. 


|Zawiera  |Wymagania wstępne  |Nie zawiera  |
|---------|---------|---------|
|Zarejestruj urządzenia za pomocą Intune<br>— Urządzenia firmowe<br>- Automatyczny/automatyczny<br>— rejestracja<br><br>Konfigurowanie zasad<br>- Zasady ochrony aplikacji<br>- Zasady zgodności<br>- Zasady dotyczące profilów urządzeń | Rejestrowanie punktów końcowych w usłudze Azure AD     | Konfigurowanie funkcji ochrony informacji, w tym:<br>- Typy informacji poufnych<br>- Etykiety<br>- Zasady DLP<br>Aby uzyskać te możliwości, zobacz Krok 5. Ochrona danych i zarządzania danymi (w dalszej części tego artykułu).       |
|    |         |         |

## <a name="step-3-add-zero-trust-identity-and-device-access-protection--enterprise-policies"></a>Krok nr 3. Dodawanie Zero Trust tożsamości i ochrony dostępu do urządzeń — Enterprise zasad

Po zarejestrowaniu urządzeń w zarządzaniu można teraz zaimplementować pełny zestaw zalecanych zasad dostępu do Zero Trust tożsamości i urządzeń wymagające urządzeń zgodnych.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png" alt-text="Zasady Zero Trust dostępu i tożsamości za pomocą zarządzania urządzeniami" lightbox="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png":::

Wróć do [**_wspólnych zasad dostępu do urządzeń_**](office-365-security/identity-access-policies.md) i tożsamości oraz dodaj zasady w Enterprise danych.  

:::image type="content" source="../media/zero-trust/identity-access-enterprise-tier.png" alt-text="Zasady Zero Trust dostępu i tożsamości — Enterprise (zalecane) warstwy" lightbox="../media/zero-trust/identity-access-enterprise-tier.png":::

## <a name="step-4-evaluate-pilot-and-deploy-microsoft-365-defender"></a>Krok nr 4. Ocenianie, wdrożenie pilotażowe i wdrażanie Microsoft 365 Defender

Microsoft 365 Defender to rozwiązanie do rozszerzonego wykrywania i odpowiedzi (XDR, extended detection and response), które automatycznie zbiera, koreluje i analizuje dane sygnału, zagrożeń i alertów z całego środowiska usługi Microsoft 365, w tym punktu końcowego, poczty e-mail, aplikacji i tożsamości.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-defender.png" alt-text="Proces dodawania nowych Microsoft 365 Defender do Zero Trust danych" lightbox="../media/zero-trust/m365-zero-trust-architecture-defender.png":::

Przejdź do [**_tematu Ocena i Microsoft 365 Defender_**](defender/eval-overview.md), aby uzyskać przewodnik metodyczny dotyczący wdrażania pilotażowego i wdrażania Microsoft 365 Defender składników. 

|Zawiera  |Wymagania wstępne  |Nie zawiera  |
|---------|---------|---------|
| Skonfiguruj środowisko oceny i pilotażu dla wszystkich składników:<br>- Defender for Identity<br>— Ochrona usługi Office 365 w usłudze Defender<br>- Defender for Endpoint<br>— Microsoft Defender for Cloud Apps<br><br>Ochrona przed zagrożeniami<br><br> Badanie zagrożeń i odpowiadanie na nie   | Zapoznaj się z wskazówkami, aby przeczytać o wymaganiach dotyczących architektury poszczególnych składników Microsoft 365 Defender.        | Usługa Azure AD Identity Protection nie jest uwzględniona w tym przewodniku po rozwiązaniu. Został on uwzględniony w Kroku 1: Konfigurowanie Zero Trust tożsamości i ochrony dostępu do urządzeń.        |
|    |         |         |

## <a name="step-5-protect-and-govern-sensitive-data"></a>Krok nr 5. Ochrona danych poufnych i ich ochrona

Wdrożenie Microsoft Information Protection (MIP) w celu odnajdowania, klasyfikowania i ochrony informacji poufnych niezależnie od miejsca życia lub podróży.

Funkcje miP są zawarte w funkcji zgodności Microsoft 365 i zapewniają narzędzia do poznania danych, ochrony danych i zapobiegania utracie danych.


:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-info-protect.png" alt-text="Funkcje ochrony informacji chroniące dane za pośrednictwem wymuszania zasad" lightbox="../media/zero-trust/m365-zero-trust-architecture-info-protect.png":::

Mimo że ta praca jest reprezentowana w górnej części stosu wdrażania przedstawionego wcześniej w tym artykule, możesz rozpocząć tę pracę w dowolnym momencie. 

Microsoft Information Protection zapewnia ramę, proces i możliwości, których można użyć do zrealizowania określonych celów biznesowych.

:::image type="content" source="../media/zero-trust/mip-solution-overview.png" alt-text="The Microsoft Information Protection (MIP) framework" lightbox="../media/zero-trust/mip-solution-overview.png":::


Aby uzyskać więcej informacji na temat planowania i wdrażania ochrony informacji, zobacz [**_Wdrażanie Microsoft Information Protection informacji_**](../compliance/information-protection-solution.md). 

W przypadku wdrażania ochrony informacji dla przepisów o ochronie prywatności danych w tym przewodniku po rozwiązaniu odano zalecaną ramę dla całego [**_procesu: wdrażanie_**](../solutions/information-protection-deploy.md) ochrony informacji dla przepisów dotyczących prywatności danych za pomocą Microsoft 365.