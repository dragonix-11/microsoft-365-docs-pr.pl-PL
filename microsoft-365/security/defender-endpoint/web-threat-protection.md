---
title: Ochrona organizacji przed zagrożeniami w sieci Web
description: Dowiedz się więcej o ochronie sieci Web w programie Microsoft Defender dla punktu końcowego i o tym, jak może chronić Twoją organizację.
keywords: ochrona sieci Web, ochrona przed zagrożeniami internetowymi, przeglądanie Internetu, zabezpieczenia, wyłudzanie informacji, złośliwe oprogramowanie, exploit, witryny internetowe, ochrona sieci, Edge, Internet Explorer, Chrome, Firefox, przeglądarka internetowa
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 398fdb8bbfb5bba59fce83e24e7d6cdd496e90bd
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997366"
---
# <a name="protect-your-organization-against-web-threats"></a>Ochrona organizacji przed zagrożeniami w sieci Web

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

Ochrona przed zagrożeniami internetowymi jest częścią [ochrony sieci Web w](web-protection-overview.md) programie Defender dla punktu końcowego. Korzysta on [z ochrony sieci](network-protection.md) w celu zabezpieczania urządzeń przed zagrożeniami internetowymi. Dzięki integracji z przeglądarkami Microsoft Edge i popularnymi przeglądarkami innych firm, np. Chrome i Firefox, ochrona przed zagrożeniami internetowymi zatrzymuje zagrożenia internetowe bez serwera proxy sieci Web i może chronić urządzenia, gdy są one z dala od komputera lub w środowisku lokalnym. Ochrona przed zagrożeniami internetowymi umożliwia zatrzymanie dostępu do witryn wyłudzających informacje, wektorów złośliwego oprogramowania, witryn wykorzystujących luki w witrynach, witryn niezaufanych lub o niskiej reputacji, a także witryn zablokowanych na niestandardowej liście [wskaźników](manage-indicators.md).

> [!NOTE]
> Otrzymywanie nowych wskaźników niestandardowych przez urządzenia może potrwać do godziny.

## <a name="prerequisites"></a>Wymagania wstępne

Ochrona sieci Web korzysta z ochrony sieci w celu zapewnienia zabezpieczeń przeglądania Internetu Microsoft Edge internetowych innych firm.

Aby włączyć ochronę sieci na urządzeniach:

- Edytuj plan bazowy zabezpieczeń usługi Defender for Endpoint w obszarze **Web & Network Protection** , aby włączyć ochronę sieci przed jej wdrożeniem lub ponownego wdrożeniem. [Informacje na temat przeglądania i przypisywania planu bazowego zabezpieczeń programu Defender for Endpoint](configure-machines-security-baseline.md#review-and-assign-the-microsoft-defender-for-endpoint-security-baseline)
- Włącz ochronę sieci przy użyciu konfiguracji urządzenia usługi Intune, programu SCCM, zasady grupy lub rozwiązania MDM. [Dowiedz się więcej o włączaniu ochrony sieci](enable-network-protection.md)

> [!NOTE]
> Jeśli ustawisz ochronę sieci na **Tylko inspekcja**, blokowanie będzie niedostępne. Ponadto będzie można wykrywać i rejestrować próby uzyskania dostępu tylko do złośliwych i niechcianych witryn internetowych Microsoft Edge sieci Web.

## <a name="configure-web-threat-protection"></a>Konfigurowanie ochrony przed zagrożeniami internetowymi

Poniżej opisano procedurę konfigurowania ochrony przed zagrożeniami sieci Web przy użyciu Microsoft Endpoint Manager administracyjnego.

1. Przejdź do Microsoft Endpoint Manager administracyjnego ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się.
 
2. Wybierz **pozycję Zmniejszenie powierzchni ataków** \> **na zabezpieczenia punktów końcowych**, a następnie wybierz **pozycję + Utwórz zasady**.

3. Wybierz platformę, na przykład Windows 10 **lub nowszą**, wybierz profil **ochrony sieci Web**, a następnie wybierz pozycję **Utwórz**. 

4. Na karcie **Podstawy** określ nazwę i opis, a następnie wybierz przycisk **Dalej**.

5. Na karcie **Ustawienia konfiguracji** rozwiń pozycję **Ochrona sieci Web**, określ ustawienia, a następnie wybierz pozycję **Dalej**.

   - Ustaw **opcję Włącz ochronę sieci** **na wartość Włączone,** aby włączyć ochronę sieci Web. Ewentualnie możesz ustawić ochronę sieci na wartość **Tryb inspekcji** , aby zobaczyć, jak będzie działać w Twoim środowisku. W trybie inspekcji ochrona sieci nie uniemożliwia użytkownikom odwiedzania witryn ani domen, ale śledzi wykrywanie jako zdarzenia. 
   - Aby chronić użytkowników przed potencjalnymi wyłudzaniem informacji i złośliwym oprogramowaniem, wyłącz opcję Wymagaj filtru **SmartScreen** dla filtru Starsza wersja Microsoft Edge na **tak**.
   - Aby uniemożliwić użytkownikom pomijanie ostrzeżeń o potencjalnie złośliwych witrynach, ustaw dla ustawienia Zablokuj **złośliwy dostęp do witryny** wartość **Tak**.
   - Aby uniemożliwić użytkownikom pomijanie ostrzeżeń i pobieranie nieskonwertowanych plików, ustaw dla ustawienia Zablokuj pobieranie **niesprawdzonych** plików tl **Tak**. 

6. Jeśli w **organizacji na karcie Tagi zakresu** są używane tagi zakresów, wybierz pozycję **+ Wybierz tagi zakresów**, a następnie wybierz pozycję **Dalej**. (Jeśli nie używasz tagów zakresów, wybierz pozycję **Dalej**). Aby dowiedzieć się więcej o tagach zakresów, zobacz Używanie kontroli dostępu opartej na rolach [(RBAC, role based access control) i tagów zakresów dla rozpowszechnianych informacji IT](/mem/intune/fundamentals/scope-tags).

7. Na karcie **Zadania określ** użytkowników i urządzenia, na których mają być odbierane zasady ochrony sieci Web, a następnie wybierz pozycję **Dalej**.

8. Na karcie **Recenzja + tworzenie** przejrzyj ustawienia zasad, a następnie wybierz pozycję **Utwórz**.

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie ochrony sieci Web](web-protection-overview.md)
- [Ochrona przed zagrożeniami internetowymi](web-threat-protection.md)
- [Monitorowanie zabezpieczeń sieci Web](web-protection-monitoring.md)
- [Reagowanie na zagrożenia w sieci Web](web-protection-response.md)
- [Ochrona sieci](network-protection.md)
