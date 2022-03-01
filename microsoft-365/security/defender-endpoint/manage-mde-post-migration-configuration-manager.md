---
title: Zarządzanie programem Microsoft Defender dla punktu końcowego przy użyciu Menedżer konfiguracji
description: Dowiedz się, jak zarządzać usługą Microsoft Defender for Endpoint za pomocą programu Menedżer konfiguracji
keywords: po migracji, zarządzanie, operacje, konserwacja, wykorzystanie, Menedżer konfiguracji, Microsoft Defender for Endpoint, edr
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
- m365initiative-defender-endpoint
ms.topic: article
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: 40bac47a4c22e3a8706ed4b38b479fff5d500410
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027062"
---
# <a name="manage-microsoft-defender-for-endpoint-with-configuration-manager"></a>Zarządzanie programem Microsoft Defender for Endpoint za pomocą Menedżer konfiguracji

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


Zalecamy korzystanie [z usługi Microsoft Endpoint Manager](/mem), która obejmuje usługi [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) (Intune) i [Microsoft Endpoint Configuration Manager (Menedżer konfiguracji](/mem/configmgr/core/understand/introduction)) do zarządzania funkcjami ochrony przed zagrożeniami organizacji dla urządzeń ( określane również jako punkty końcowe).

- [Dowiedz się więcej o Endpoint Manager](/mem/endpoint-manager-overview)
- [Współ zarządzanie usługą Microsoft Defender for Endpoint na Windows 10 i Windows 11 za pomocą usługi Menedżer konfiguracji i Intune](manage-mde-post-migration-intune.md)

## <a name="configure-microsoft-defender-for-endpoint-with-configuration-manager"></a>Konfigurowanie programu Microsoft Defender dla punktu końcowego za pomocą Menedżer konfiguracji

<br/><br/>

|Zadanie|Zasoby, aby dowiedzieć się więcej|
|---|---|
|**Zainstaluj konsolę Menedżer konfiguracji,** jeśli jeszcze jej nie masz <br/><br/> *Jeśli nie masz jeszcze konsoli Menedżer konfiguracji, skorzystaj z tych zasobów, aby pobrać i zainstalować tę konsolę.*|[Pobierz nośnik instalacyjny](/mem/configmgr/core/servers/deploy/install/get-install-media) <br/><br/> [Zainstaluj konsolę Menedżer konfiguracji](/mem/configmgr/core/servers/deploy/install/install-consoles)|
|**Używanie Menedżer konfiguracji do urządzeń w programie** Microsoft Defender for Endpoint <br/><br/> *Jeśli masz urządzenia (lub punkty końcowe), które nie zostały jeszcze podłączone do programu Microsoft Defender for Endpoint, możesz to zrobić za pomocą programu Menedżer konfiguracji.*|[Dołączanie do programu Microsoft Defender dla punktu końcowego za pomocą Menedżer konfiguracji](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection#about-onboarding-to-atp-with-configuration-manager)|
|**Zarządzanie zasadami ochrony przed złośliwym kodem i Windows zabezpieczeń zapory** dla komputerów klienckich (punktów końcowych) <br/><br/> *Skonfiguruj funkcje ochrony punktu końcowego, takie jak program Microsoft Defender for Endpoint, ochrona przed lukami, kontrola aplikacji, ochrona przed złośliwym oprogramowaniem, ustawienia zapory i nie tylko.*|[Menedżer konfiguracji: Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection)|
|**Wybieranie metod aktualizacji ochrony przed złośliwym oprogramowaniem** na urządzeniach w organizacji <br/><br/> *Dzięki Endpoint Protection w Menedżer konfiguracji możesz wybrać jedną z kilku metod, aby zapewnić aktualne definicje ochrony przed złośliwym oprogramowaniem na urządzeniach organizacji.*|[Konfigurowanie aktualizacji definicji dla Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-definition-updates) <br/><br/> [Dostarczanie aktualizacji Menedżer konfiguracji za pomocą funkcji aktualizacji definicji](/mem/configmgr/protect/deploy-use/endpoint-definitions-configmgr)|
|**Włączanie ochrony sieci w** celu uniemożliwinia pracownikom korzystania z aplikacji zawierających złośliwą zawartość w Internecie <br/><br/> *Zalecamy używanie [najpierw trybu inspekcji](/microsoft-365/security/defender-endpoint/evaluate-network-protection) w celu ochrony sieci w środowisku testowym, aby sprawdzić, które aplikacje mogą być blokowane przed ich rozpoczęciem.*|[Włączanie ochrony sieci za pomocą Menedżer konfiguracji](/microsoft-365/security/defender-endpoint/enable-network-protection#microsoft-endpoint-configuration-manager)|
|**Konfigurowanie kontrolowanego dostępu do folderu w** celu ochrony przed oprogramowaniem wymuszającym okup <br/><br/> *Kontrolowany dostęp do folderu jest również określany jako ochrona antyransomware.*|[Ochrona punktu końcowego: Kontrolowany dostęp do folderu](/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/> [Włączanie kontrolowanego dostępu do folderu w zarządzaniu konfiguracją punktu końcowego firmy Microsoft](/microsoft-365/security/defender-endpoint/enable-controlled-folders#microsoft-endpoint-configuration-manager)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Konfigurowanie portalu Microsoft 365 Defender sieciOwego

Jeśli jeszcze tego nie zrobiono, skonfiguruj w portalu usługi Microsoft 365 Defender wyświetlanie alertów, konfigurowanie funkcji ochrony przed zagrożeniami i wyświetlanie szczegółowych informacji o ogólnym stanie zabezpieczeń Twojej organizacji. Zobacz Podczas wykrycia i zatrzymania ataków, alerty, takie jak "alert dostępu początkowego", zostały wyzwolone i pojawiły się w Microsoft 365 Defender [portalu](/microsoft-365/security/defender/microsoft-365-defender). Możesz także skonfigurować funkcje, które użytkownicy końcowi będą widzieć w portalu Microsoft 365 Defender sieci.

- [Omówienie Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [Ochrona punktu końcowego: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Następne kroki

- [Omówienie funkcji Zarządzanie zagrożeniami i lukami](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Odwiedź pulpit nawigacyjny Microsoft 365 Defender zabezpieczeń portalu](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [Zarządzanie programem Microsoft Defender dla punktu końcowego za pomocą usługi Intune](manage-mde-post-migration-intune.md)
