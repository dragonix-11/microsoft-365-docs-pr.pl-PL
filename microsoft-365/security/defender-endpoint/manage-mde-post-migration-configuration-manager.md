---
title: Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu Configuration Manager
description: Dowiedz się, jak zarządzać Ochrona punktu końcowego w usłudze Microsoft Defender za pomocą Configuration Manager
keywords: po migracji, zarządzanie, operacje, konserwacja, wykorzystanie, Configuration Manager, Ochrona punktu końcowego w usłudze Microsoft Defender, edr
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
- m365initiative-defender-endpoint
ms.topic: article
ms.date: 07/01/2022
ms.reviewer: chventou
ms.openlocfilehash: b253fe7dad271684f5c0e927ec162ea4e993df29
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607394"
---
# <a name="manage-microsoft-defender-for-endpoint-with-configuration-manager"></a>Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu Configuration Manager

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Zalecamy korzystanie z usługi [Microsoft Endpoint Manager](/mem), która obejmuje [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) (Intune) i [Configuration Manager punktu końcowego firmy Microsoft](/mem/configmgr/core/understand/introduction) (Configuration Manager ), aby zarządzać funkcjami ochrony przed zagrożeniami w organizacji dla urządzeń (nazywanych również punktami końcowymi).

- [Dowiedz się więcej o Endpoint Manager](/mem/endpoint-manager-overview)
- [Współzarządzaj Ochrona punktu końcowego w usłudze Microsoft Defender na urządzeniach Windows 10 i Windows 11 przy użyciu Configuration Manager i Intune](manage-mde-post-migration-intune.md)

## <a name="configure-microsoft-defender-for-endpoint-with-configuration-manager"></a>Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu Configuration Manager

|Zadanie|Zasoby, aby dowiedzieć się więcej|
|---|---|
|**Zainstaluj konsolę Configuration Manager**, jeśli jeszcze jej nie masz <br/><br/> *Jeśli nie masz jeszcze konsoli Configuration Manger, użyj tych zasobów, aby pobrać bity i zainstalować je.*|[Pobieranie nośnika instalacyjnego](/mem/configmgr/core/servers/deploy/install/get-install-media) <br/><br/> [Instalowanie konsoli Configuration Manager](/mem/configmgr/core/servers/deploy/install/install-consoles)|
|**Dołączanie urządzeń do Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu Configuration Manager** <br/><br/> *Jeśli urządzenia (lub punkty końcowe) nie zostały jeszcze dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender, możesz to zrobić za pomocą Configuration Manager.*|[Dołączanie do Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu Configuration Manager](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection#about-onboarding-to-atp-with-configuration-manager)|
|**Zarządzanie zasadami ochrony przed złośliwym kodem i zabezpieczeniami zapory systemu Windows** dla komputerów klienckich (punktów końcowych) <br/><br/> *Skonfiguruj funkcje ochrony punktu końcowego, w tym Ochrona punktu końcowego w usłudze Microsoft Defender, ochronę przed lukami w zabezpieczeniach, kontrolę aplikacji, oprogramowanie chroniące przed złośliwym kodem, ustawienia zapory i inne.*|[Configuration Manager: Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection)|
|**Wybieranie metod aktualizowania aktualizacji oprogramowania chroniącego przed złośliwym kodem** na urządzeniach organizacji <br/><br/> *Dzięki programowi Endpoint Protection w Configuration Manager możesz wybrać jedną z kilku metod, aby zapewnić aktualność definicji oprogramowania chroniącego przed złośliwym kodem na urządzeniach organizacji.*|[Konfigurowanie aktualizacji definicji dla programu Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-definition-updates) <br/><br/> [Dostarczanie aktualizacji definicji przy użyciu Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-definitions-configmgr)|
|**Włącz ochronę sieci,** aby uniemożliwić pracownikom korzystanie z aplikacji, które mają złośliwą zawartość w Internecie <br/><br/> *Zalecamy używanie [najpierw trybu inspekcji](/microsoft-365/security/defender-endpoint/evaluate-network-protection) do ochrony sieci w środowisku testowym, aby sprawdzić, które aplikacje zostaną zablokowane przed wdrożeniem.*|[Włączanie ochrony sieci za pomocą Configuration Manager](/microsoft-365/security/defender-endpoint/enable-network-protection#microsoft-endpoint-configuration-manager)|
|**Konfigurowanie kontrolowanego dostępu do folderów** w celu ochrony przed oprogramowaniem wymuszającym okup <br/><br/> *Kontrolowany dostęp do folderów jest również określany jako ochrona przed złośliwym oprogramowaniem.*|[Ochrona punktu końcowego: kontrolowany dostęp do folderów](/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/> [Włączanie kontrolowanego dostępu do folderów w usłudze Microsoft Endpoint Configuration Manage](/microsoft-365/security/defender-endpoint/enable-controlled-folders#microsoft-endpoint-configuration-manager)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Konfigurowanie portalu Microsoft 365 Defender

Jeśli jeszcze tego nie zrobiono, skonfiguruj portal Microsoft 365 Defender w celu wyświetlania alertów, konfigurowania funkcji ochrony przed zagrożeniami i wyświetlania szczegółowych informacji o ogólnej kondycji zabezpieczeń organizacji. Zobacz Podczas wykrywania i zatrzymywania ataku alerty, takie jak "początkowy alert dostępu", zostały wyzwolone i wyświetlone w [portalu Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). Możesz również skonfigurować, czy i jakie funkcje użytkownicy końcowi mogą wyświetlać w portalu Microsoft 365 Defender.

- [Omówienie Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [Ochrona punktu końcowego: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Następne kroki

- [Omówienie Zarządzanie zagrożeniami i lukami](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Odwiedź pulpit nawigacyjny operacji zabezpieczeń portalu Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender za pomocą Intune](manage-mde-post-migration-intune.md)
