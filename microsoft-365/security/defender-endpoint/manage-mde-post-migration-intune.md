---
title: Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu Intune
description: Dowiedz się, jak zarządzać Ochrona punktu końcowego w usłudze Microsoft Defender za pomocą Intune
keywords: po migracji, zarządzanie, operacje, konserwacja, wykorzystanie, usługa Intune, Ochrona punktu końcowego w usłudze Microsoft Defender, edr
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
ms.topic: article
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: 05fb01b411b1b32eeac763f3c364b29e29f5d8f5
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603709"
---
# <a name="manage-microsoft-defender-for-endpoint-with-intune"></a>Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender za pomocą Intune

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Zalecamy używanie usługi [Microsoft Endpoint Manager](/mem), która obejmuje Microsoft Intune (Intune) do zarządzania funkcjami ochrony przed zagrożeniami w organizacji dla urządzeń (nazywanych również punktami końcowymi). [Dowiedz się więcej o Endpoint Manager](/mem/endpoint-manager-overview).

W tym artykule opisano sposób znajdowania ustawień Ochrona punktu końcowego w usłudze Microsoft Defender w Intune i wymieniono różne zadania, które można wykonać.

## <a name="find-your-microsoft-defender-for-endpoint-settings-in-intune"></a>Znajdowanie ustawień Ochrona punktu końcowego w usłudze Microsoft Defender w Intune

> [!IMPORTANT]
> Aby skonfigurować ustawienia opisane w tym artykule, musisz mieć przypisaną rolę administratora globalnego lub administratora usługi Intune. Aby dowiedzieć się więcej, zobacz **[Typy administratorów (Intune)](/mem/intune/fundamentals/users-add#types-of-administrators)**.

1. Przejdź do Azure Portal ([https://portal.azure.com](https://portal.azure.com)) i zaloguj się.

2. W obszarze **Usługi platformy Azure** wybierz **pozycję Intune**.

3. W okienku nawigacji po lewej stronie wybierz pozycję **Konfiguracja urządzenia**, a następnie w obszarze **Zarządzanie** wybierz pozycję **Profile**.

4. Wybierz istniejący profil lub utwórz nowy.

> [!TIP]
> Potrzebujesz pomocy? Zobacz **[Używanie Ochrona punktu końcowego w usłudze Microsoft Defender z Intune](/mem/intune/protect/advanced-threat-protection#example-of-using-microsoft-defender-atp-with-intune)**.

## <a name="configure-microsoft-defender-for-endpoint-with-intune"></a>Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu Intune

W poniższej tabeli wymieniono różne zadania, które można wykonać w celu skonfigurowania Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu Intune. Nie musisz konfigurować wszystkiego jednocześnie; wybierz zadanie, odczytaj odpowiednie zasoby, a następnie kontynuuj.

<br/><br/>

|Zadanie|Zasoby, aby dowiedzieć się więcej|
|---|---|
|**Zarządzanie urządzeniami organizacji przy użyciu Intune** w celu ochrony przechowywanych na nich urządzeń i danych|[Ochrona urządzeń za pomocą Microsoft Intune](/mem/intune/protect/device-protect)|
|**Integrowanie Ochrona punktu końcowego w usłudze Microsoft Defender z Intune** jako rozwiązaniem mobile threat defense <br/>*(w przypadku urządzeń z systemem Android i urządzeń z systemem Windows 10 lub Windows 11)*|[Wymuszanie zgodności Ochrona punktu końcowego w usłudze Microsoft Defender z dostępem warunkowym w Intune](/mem/intune/protect/advanced-threat-protection)|
|**Używanie dostępu warunkowego** do kontrolowania urządzeń i aplikacji, które mogą łączyć się z twoją pocztą e-mail i zasobami firmy|[Konfigurowanie dostępu warunkowego w Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/configure-conditional-access)|
|**Konfigurowanie ustawień programu antywirusowego Microsoft Defender** przy użyciu dostawcy usług konfiguracji zasad ([Dostawca CSP zasad](/windows/client-management/mdm/policy-configuration-service-provider))|[Ograniczenia dotyczące urządzeń: Program antywirusowy Microsoft Defender](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus) <br/><br/> [Dostawca CSP zasad — Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/client-management/mdm/policy-csp-defender)|
|**W razie potrzeby określ wykluczenia dla programu antywirusowego Microsoft Defender** <br/><br/> *Ogólnie rzecz biorąc, nie należy stosować wykluczeń. Program antywirusowy Microsoft Defender zawiera szereg automatycznych wykluczeń opartych na znanych zachowaniach systemu operacyjnego i typowych plikach zarządzania, takich jak te używane w scenariuszach zarządzania przedsiębiorstwem, zarządzania bazami danych i innych scenariuszach przedsiębiorstwa.*|[Zalecenia dotyczące skanowania wirusów dla komputerów z systemem Enterprise z aktualnie obsługiwanymi wersjami systemu Windows](https://support.microsoft.com/help/822158/virus-scanning-recommendations-for-enterprise-computers) <br/><br/> [Ograniczenia dotyczące urządzeń: Wykluczenia programu antywirusowego Microsoft Defender dla urządzeń Windows 10 i Windows 11](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions) <br/><br/> [Konfigurowanie wykluczeń programu antywirusowego Microsoft Defender w Windows Server 2016 lub 2019 lub 2022 r.](/windows/security/threat-protection/microsoft-defender-antivirus/configure-server-exclusions-microsoft-defender-antivirus)|
|**Skonfiguruj reguły zmniejszania obszaru ataków** w celu ukierunkowania zachowań oprogramowania, które są często nadużywane przez osoby atakujące <br/><br/> *Najpierw skonfiguruj reguły zmniejszania obszaru ataków w [trybie inspekcji](/microsoft-365/security/defender-endpoint/audit-windows-defender) (przez co najmniej tydzień i maksymalnie dwa miesiące). Możesz monitorować stan przy użyciu usługi Power BI ([pobierz nasz szablon](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Attack%20Surface%20Reduction%20rules)), a następnie ustawić te reguły na tryb aktywny, gdy wszystko będzie gotowe.*|[Tryb inspekcji w Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/audit-windows-defender) <br/><br/> [Ochrona punktu końcowego: zmniejszanie obszaru podatnego na ataki](/mem/intune/protect/endpoint-protection-windows-10?toc=/intune/configuration/toc.json&bc=/intune/configuration/breadcrumb/toc.json#attack-surface-reduction) <br/><br/> [Dowiedz się więcej o regułach zmniejszania obszaru ataków](/microsoft-365/security/defender-endpoint/attack-surface-reduction) <br/><br/> [Wpis w blogu społeczności technicznej: Demistyfikacja reguł zmniejszania obszaru podatnego na ataki — część 1](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420)|
|**Konfigurowanie filtrowania sieci** w celu blokowania połączeń wychodzących z dowolnej aplikacji do adresów IP lub domen o niskiej reputacji  <br/><br/> *Filtrowanie sieci jest również nazywane [ochroną sieci](/microsoft-365/security/defender-endpoint/network-protection).* <br/><br/> *Upewnij się, że urządzenia Windows 10 i Windows 11 mają zainstalowane najnowsze [aktualizacje platformy ochrony przed złośliwym kodem](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform).*|[Ochrona punktu końcowego: filtrowanie sieci](/mem/intune/protect/endpoint-protection-windows-10#network-filtering) <br/><br/> [Przejrzyj zdarzenia ochrony sieci w systemie Windows Podgląd zdarzeń](/microsoft-365/security/defender-endpoint/evaluate-network-protection#review-network-protection-events-in-windows-event-viewer)|
|**Konfigurowanie kontrolowanego dostępu do folderów** w celu ochrony przed oprogramowaniem wymuszającym okup <br/><br/> *[Kontrolowany dostęp do folderów](/microsoft-365/security/defender-endpoint/controlled-folders) jest również określany jako ochrona przed złośliwym oprogramowaniem.*|[Ochrona punktu końcowego: kontrolowany dostęp do folderów](/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/> [Włączanie kontrolowanego dostępu do folderów w Intune](/microsoft-365/security/defender-endpoint/enable-controlled-folders#intune)|
|**Konfigurowanie ochrony przed lukami w zabezpieczeniach** w celu ochrony urządzeń organizacji przed złośliwym oprogramowaniem wykorzystującym luki w zabezpieczeniach do rozprzestrzeniania i infekowania innych urządzeń <br/><br/> *[Ochrona przed lukami](/microsoft-365/security/defender-endpoint/exploit-protection) w zabezpieczeniach jest również określana jako Exploit Guard.*|[Ochrona punktu końcowego: Microsoft Defender Exploit Guard](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-exploit-guard) <br/><br/> [Włączanie ochrony przed lukami w zabezpieczeniach w Intune](/microsoft-365/security/defender-endpoint/enable-exploit-protection#intune)|
|**Skonfiguruj filtr Microsoft Defender SmartScreen** w celu ochrony przed złośliwymi witrynami i plikami w Internecie. <br/><br/> *Przeglądarka Microsoft Edge powinna być zainstalowana na urządzeniach organizacji. Aby uzyskać ochronę w przeglądarkach Google Chrome i FireFox, skonfiguruj ochronę przed lukami w zabezpieczeniach.*|[Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) <br/><br/> [Ograniczenia dotyczące urządzeń: Microsoft Defender SmartScreen](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-smartscreen) <br/><br/> [Ustawienia zasad zarządzania filtrem SmartScreen w Intune](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings#mdm-settings)|
|**Konfigurowanie Zapora Microsoft Defender** do blokowania nieautoryzowanego ruchu sieciowego przepływającego do lub z urządzeń organizacji|[Ochrona punktu końcowego: Zapora Microsoft Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-firewall) <br/><br/> [Zapora Microsoft Defender z zabezpieczeniami zaawansowanymi](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)|
|**Konfigurowanie szyfrowania i BitLocker** w celu ochrony informacji na urządzeniach organizacji z systemem Windows|[Ochrona punktu końcowego: Szyfrowanie systemu Windows](/mem/intune/protect/endpoint-protection-windows-10#windows-encryption) <br/><br/> [BitLocker dla urządzeń Windows 10 i Windows 11](/windows/security/information-protection/bitlocker/bitlocker-overview)|
|**Konfigurowanie funkcji Microsoft Defender Credential Guard** w celu ochrony przed atakami kradzieży poświadczeń|Aby uzyskać Windows 10, Windows 11, Windows Server 2016 i Windows Server 2019 i Windows Server 2022, zobacz [Ochrona punktu końcowego: Microsoft Defender Credential Guard](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-credential-guard) <br/><br/> W przypadku systemów Windows 7 z dodatkiem SP1, Windows Server 2008 R2 z dodatkiem SP1, Windows 8.1 i Windows Server 2012 R2 zobacz [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft, Versions 1 and 2](https://www.microsoft.com/download/details.aspx?id=36036)|
|**Konfigurowanie kontroli aplikacji usługi Microsoft Defender** w celu wybrania, czy aplikacje mają być poddane inspekcji, czy ufać na urządzeniach organizacji <br/><br/> *Kontrolka aplikacji usługi Microsoft Defender jest również nazywana [funkcją AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview).*|[Wdrażanie zasad kontroli aplikacji w usłudze Microsoft Defender przy użyciu Microsoft Intune](/windows/security/threat-protection/windows-defender-application-control/deploy-windows-defender-application-control-policies-using-intune) <br/><br/> [Ochrona punktu końcowego: Kontrola aplikacji w usłudze Microsoft Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-application-control) <br/><br/> [AppLocker CSP](/windows/client-management/mdm/applocker-csp)|
|**Konfigurowanie kontroli urządzeń i dostępu urządzeń peryferyjnych USB** w celu zapobiegania zagrożeniom w nieautoryzowanych urządzeniach peryferyjnych przed naruszeniem urządzeń|[Sterowanie urządzeniami USB i innymi nośnikami wymiennymi przy użyciu Ochrona punktu końcowego w usłudze Microsoft Defender i Intune](/windows/security/threat-protection/device-control/control-usb-devices-using-intune)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Konfigurowanie portalu Microsoft 365 Defender

Jeśli jeszcze tego nie zrobiono, skonfiguruj portal Microsoft 365 Defender w celu wyświetlania alertów, konfigurowania funkcji ochrony przed zagrożeniami i wyświetlania szczegółowych informacji o ogólnej kondycji zabezpieczeń organizacji. Zobacz [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). Możesz również skonfigurować, czy i jakie funkcje użytkownicy końcowi mogą wyświetlać w portalu Microsoft 365 Defender.

- [Omówienie Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [Ochrona punktu końcowego: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Następne kroki

- [Omówienie Zarządzanie zagrożeniami i lukami](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Odwiedź pulpit nawigacyjny operacji zabezpieczeń portalu Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
