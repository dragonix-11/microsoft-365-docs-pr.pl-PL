---
title: Zarządzanie programem Microsoft Defender dla punktu końcowego za pomocą usługi Intune
description: Dowiedz się, jak zarządzać usługą Microsoft Defender dla punktu końcowego za pomocą usługi Intune
keywords: po migracji, zarządzanie, operacje, konserwacja, wykorzystanie, intune, Microsoft Defender for Endpoint, edr
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
ms.topic: article
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: 290d98f3f4136cfd07b5ea5abc21988ac8d9867a
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027038"
---
# <a name="manage-microsoft-defender-for-endpoint-with-intune"></a>Zarządzanie programem Microsoft Defender dla punktu końcowego za pomocą usługi Intune

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Zalecamy używanie programu [Microsoft Endpoint Manager](/mem), który obejmuje usługę Microsoft Intune (Intune) do zarządzania funkcjami ochrony przed zagrożeniami w organizacji dla urządzeń (nazywanymi również punktami końcowymi). [Dowiedz się więcej o Endpoint Manager](/mem/endpoint-manager-overview).

W tym artykule opisano, jak znaleźć ustawienia programu Microsoft Defender dla punktu końcowego w usłudze Intune, oraz wymieniono różne zadania, które można wykonać.

## <a name="find-your-microsoft-defender-for-endpoint-settings-in-intune"></a>Znajdowanie ustawień programu Microsoft Defender dla punktu końcowego w usłudze Intune

> [!IMPORTANT]
> Aby skonfigurować ustawienia opisane w tym artykule, musisz mieć przypisaną rolę administratora globalnego lub administratora usługi w usłudze Intune. Aby dowiedzieć się więcej, **[zobacz Typy administratorów (Intune)](/mem/intune/fundamentals/users-add#types-of-administrators)**.

1. Przejdź do portalu Azure Portal ([https://portal.azure.com](https://portal.azure.com)) i zaloguj się.

2. W **obszarze Usługi Azure** wybierz pozycję **Intune**.

3. W okienku nawigacji po lewej stronie wybierz pozycję **Konfiguracja urządzenia**, a następnie w obszarze **Zarządzanie** wybierz pozycję **Profile**.

4. Wybierz istniejący profil lub utwórz nowy.

> [!TIP]
> Potrzebujesz pomocy? Zobacz **[Korzystanie z programu Microsoft Defender dla punktu końcowego w usłudze Intune](/mem/intune/protect/advanced-threat-protection#example-of-using-microsoft-defender-atp-with-intune)**.

## <a name="configure-microsoft-defender-for-endpoint-with-intune"></a>Konfigurowanie programu Microsoft Defender dla punktu końcowego za pomocą usługi Intune

W poniższej tabeli wymieniono różne zadania, które można wykonać w celu skonfigurowania programu Microsoft Defender dla punktu końcowego w usłudze Intune. Nie musisz konfigurować wszystkiego jednocześnie; wybierz zadanie, przeczytaj odpowiednie zasoby i kontynuuj.

<br/><br/>

|Zadanie|Zasoby, aby dowiedzieć się więcej|
|---|---|
|**Zarządzanie urządzeniami organizacji za pomocą usługi Intune** w celu ochrony tych urządzeń i przechowywanych na nich danych|[Ochrona urządzeń za pomocą Microsoft Intune](/mem/intune/protect/device-protect)|
|**Zintegruj usługę Microsoft Defender for Endpoint z usługą Intune** jako rozwiązanie do ochrony przed zagrożeniami na urządzeniach przenośnych <br/>*(dla urządzeń z systemem Android i urządzeń Windows 10 lub Windows 11)*|[Wymuszanie zgodności dla programu Microsoft Defender dla punktu końcowego za pomocą dostępu warunkowego w usłudze Intune](/mem/intune/protect/advanced-threat-protection)|
|**Sterowanie urządzeniami i aplikacjami,** które mogą łączyć się z pocztą e-mail i zasobami firmy, za pomocą dostępu warunkowego|[Konfigurowanie dostępu warunkowego w programie Microsoft Defender dla punktu końcowego](/microsoft-365/security/defender-endpoint/configure-conditional-access)|
|**Konfigurowanie Program antywirusowy Microsoft Defender przy** użyciu zasad konfiguracji usługodawca ([CSP zasad](/windows/client-management/mdm/policy-configuration-service-provider))|[Ograniczenia dotyczące urządzeń: Program antywirusowy Microsoft Defender](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus) <br/><br/> [Program CSP zasad — program Microsoft Defender dla punktu końcowego](/windows/client-management/mdm/policy-csp-defender)|
|**W razie potrzeby określ wykluczenia dotyczące Program antywirusowy Microsoft Defender** <br/><br/> *Ogólnie rzecz biorąc, nie należy stosować wykluczeń. Program antywirusowy Microsoft Defender obejmuje szereg automatycznych wykluczeń opartych na znanych zachowaniach systemu operacyjnego i typowych plikach zarządzania, takich jak używane w zarządzaniu przedsiębiorstwem, zarządzaniu bazami danych i innych scenariuszach dla przedsiębiorstw.*|[Zalecenia dotyczące skanowania wirusów dla Enterprise komputerów z obecnie obsługiwanymi wersjami Windows](https://support.microsoft.com/help/822158/virus-scanning-recommendations-for-enterprise-computers) <br/><br/> [Ograniczenia dotyczące urządzeń: Program antywirusowy Microsoft Defender wykluczenia dotyczące Windows 10 i Windows 11 urządzeń](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions) <br/><br/> [Konfigurowanie Program antywirusowy Microsoft Defender wykluczeń w Windows Server 2016 roku 2019 lub 2022](/windows/security/threat-protection/microsoft-defender-antivirus/configure-server-exclusions-microsoft-defender-antivirus)|
|**Konfigurowanie reguł ograniczania powierzchni ataków w** celu kierowania zachowań oprogramowania, które są często używane przez atakujących <br/><br/> *Skonfiguruj najpierw reguły ograniczania powierzchni ataków w [](/microsoft-365/security/defender-endpoint/audit-windows-defender) trybie inspekcji (przez co najmniej tydzień i do dwóch miesięcy). Możesz monitorować status za Power BI ([pobierz nasz szablon](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Attack%20Surface%20Reduction%20rules)), a następnie ustawiać te reguły jako tryb aktywny, gdy wszystko będzie gotowe.*|[Tryb inspekcji w programie Microsoft Defender dla punktu końcowego](/microsoft-365/security/defender-endpoint/audit-windows-defender) <br/><br/> [Ochrona punktu końcowego: Zmniejszenie ataków na powierzchnię](/mem/intune/protect/endpoint-protection-windows-10?toc=/intune/configuration/toc.json&bc=/intune/configuration/breadcrumb/toc.json#attack-surface-reduction) <br/><br/> [Dowiedz się więcej o zasadach ograniczania powierzchni ataków](/microsoft-365/security/defender-endpoint/attack-surface-reduction) <br/><br/> [Tech Community w blogu: Reguły zmniejszania powierzchni ataków bez zadyskonujmy — część 1](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420)|
|**Konfigurowanie filtrowania sieci w celu** blokowania połączeń wychodzących z dowolnej aplikacji do adresów IP lub domen o niskiej reputacji  <br/><br/> *Filtrowanie sieci jest również nazywane ochroną [sieci](/microsoft-365/security/defender-endpoint/network-protection).* <br/><br/> *Upewnij się, Windows 10 i Windows 11 mają zainstalowane najnowsze aktualizacje platformy zapobiegającej [złośliwym oprogramowaniem](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform).*|[Ochrona punktu końcowego: Filtrowanie sieci](/mem/intune/protect/endpoint-protection-windows-10#network-filtering) <br/><br/> [Przeglądanie zdarzeń ochrony sieci w przeglądarce Windows zdarzeń](/microsoft-365/security/defender-endpoint/evaluate-network-protection#review-network-protection-events-in-windows-event-viewer)|
|**Konfigurowanie kontrolowanego dostępu do folderu w** celu ochrony przed oprogramowaniem wymuszającym okup <br/><br/> *[Kontrolowany dostęp do folderu](/microsoft-365/security/defender-endpoint/controlled-folders) jest również określany jako ochrona antyransomware.*|[Ochrona punktu końcowego: Kontrolowany dostęp do folderu](/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/> [Włączanie kontrolowanego dostępu do folderu w usłudze Intune](/microsoft-365/security/defender-endpoint/enable-controlled-folders#intune)|
|**Konfigurowanie ochrony przed programami wykorzystującmi** w celu ochrony urządzeń organizacji przed złośliwym oprogramowaniem wykorzystującym wykorzystywanie do rozpowszechniania i infekowania innych urządzeń <br/><br/> *[Ochrona przed](/microsoft-365/security/defender-endpoint/exploit-protection) exploitami jest również nazywana exploit guardem.*|[Ochrona punktu końcowego: Microsoft Defender Exploit Guard](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-exploit-guard) <br/><br/> [Włączanie ochrony przed wykorzystywaniem luk w usłudze Intune](/microsoft-365/security/defender-endpoint/enable-exploit-protection#intune)|
|**Skonfiguruj Microsoft Defender SmartScreen**, aby chronić przed złośliwymi witrynami i plikami w Internecie. <br/><br/> *Microsoft Edge powinny być zainstalowane na urządzeniach organizacji. Aby uzyskać ochronę w przeglądarkach Google Chrome i FireFox, skonfiguruj ochronę przed wykorzystywaniem luk.*|[Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) <br/><br/> [Ograniczenia dotyczące urządzeń: Microsoft Defender SmartScreen](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-smartscreen) <br/><br/> [Ustawienia zasad dotyczące zarządzania filtrem SmartScreen w usłudze Intune](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings#mdm-settings)|
|**Skonfiguruj Zaporę Microsoft Defender,** aby blokować nieautoryzowany ruch sieciowy wychodzący do urządzeń organizacji lub wychodzący z nich|[Ochrona punktu końcowego: Zapora Microsoft Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-firewall) <br/><br/> [Zapora Microsoft Defender z zaawansowanymi zabezpieczeniami](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)|
|**Skonfiguruj szyfrowanie i funkcję BitLocker**, aby chronić informacje na urządzeniach w Twojej organizacji, na których działa Windows|[Ochrona punktu końcowego: szyfrowanie Windows](/mem/intune/protect/endpoint-protection-windows-10#windows-encryption) <br/><br/> [BitLocker dla Windows 10 i Windows 11 urządzeń](/windows/security/information-protection/bitlocker/bitlocker-overview)|
|**Konfigurowanie usługi Microsoft Defender Credential Guard w** celu ochrony przed atakami kradzieży poświadczeń|Aby uzyskać Windows 10, Windows 11, Windows Server 2016 i Windows Server 2019 oraz Windows Server 2022, zobacz Ochrona punktu końcowego[: Microsoft Defender Credential Guard](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-credential-guard) <br/><br/> Aby uzyskać informacje Windows 7 z dodatkiem SP1, Windows Server 2008 R2 z dodatkiem SP1, Windows 8.1 i Windows Server 2012 R2, zobacz Ograniczanie ataków na hasła [(PtH)](https://www.microsoft.com/download/details.aspx?id=36036) i Inne kradzieże poświadczeń, wersje 1 i 2|
|**Konfigurowanie programu Microsoft Defender Application Control w** celu wybrania, czy aplikacje na urządzeniach organizacji mają być inspekcji czy zaufane <br/><br/> *Kontrola aplikacji Microsoft Defender jest również nazywana [funkcją AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview).*|[Wdrażanie zasad aplikacji Microsoft Defender Application Control przy użyciu Microsoft Intune](/windows/security/threat-protection/windows-defender-application-control/deploy-windows-defender-application-control-policies-using-intune) <br/><br/> [Ochrona punktu końcowego: Kontrola aplikacji Microsoft Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-application-control) <br/><br/> [AppLocker CSP](/windows/client-management/mdm/applocker-csp)|
|**Skonfiguruj dostęp do kontrolek urządzeń i urządzeń peryferyjnych USB** , aby chronić urządzenia przed zagrożeniami w nieautoryzowanych urządzeniach peryferyjnych|[Sterowanie urządzeniami USB i innymi nośnikami wymiennymi za pomocą programu Microsoft Defender dla punktu końcowego i usługi Intune](/windows/security/threat-protection/device-control/control-usb-devices-using-intune)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Konfigurowanie portalu Microsoft 365 Defender sieciOwego

Jeśli jeszcze tego nie zrobiono, skonfiguruj w portalu usługi Microsoft 365 Defender wyświetlanie alertów, konfigurowanie funkcji ochrony przed zagrożeniami i wyświetlanie szczegółowych informacji o ogólnym stanie zabezpieczeń Twojej organizacji. Zobacz [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). Możesz także skonfigurować funkcje, które użytkownicy końcowi będą widzieć w portalu Microsoft 365 Defender sieci.

- [Omówienie Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [Ochrona punktu końcowego: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Następne kroki

- [Omówienie funkcji Zarządzanie zagrożeniami i lukami](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Odwiedź pulpit nawigacyjny Microsoft 365 Defender zabezpieczeń portalu](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
