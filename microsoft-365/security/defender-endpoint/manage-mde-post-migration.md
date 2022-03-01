---
title: Zarządzanie programem Microsoft Defender dla punktu końcowego po migracji
description: Po przełączeniu się do programu Microsoft Defender dla punktu końcowego następnym krokiem jest zarządzanie funkcjami ochrony przed zagrożeniami
keywords: po migracji, zarządzanie, operacje, konserwacja, wykorzystanie, Usługa Microsoft Defender dla punktu końcowego, edr
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
ms.topic: conceptual
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: 2be934da8a87e02ead5c395097d90ccde46cb9d7
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2021
ms.locfileid: "62996829"
---
# <a name="manage-microsoft-defender-for-endpoint-post-migration"></a>Zarządzanie usługą Microsoft Defender dla punktu końcowego po migracji

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Kolejnym krokiem po przeniesionej z poprzedniej ochrony punktu końcowego i rozwiązania antywirusowego do programu Microsoft Defender for Endpoint jest zarządzanie funkcjami i możliwościami. Do zarządzania [urządzeniami i ustawieniami](/mem/endpoint-manager-overview) zabezpieczeń organizacji zalecamy [Microsoft Endpoint Manager, które](/mem/configmgr/core/understand/introduction) obejmują funkcje [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) i Microsoft Endpoint Configuration Manager. Można jednak użyć innych narzędzi/metod, takich [jak obiekty zasady grupy w Azure Active Directory domenowych](/azure/active-directory-domain-services/manage-group-policy).

W poniższej tabeli wymieniono różne narzędzia i metody, których możesz użyć, oraz linki, które pozwalają dowiedzieć się więcej.

<br/><br/>

|Narzędzie/metoda|Opis|
|---|---|
|**[Analiza zagrożeń i zarządzanie lukami w zabezpieczeniach pulpitu nawigacyjnego](/windows/security/threat-protection/microsoft-defender-atp/tvm-dashboard-insights)** w [portalu Microsoft 365 Defender](https://security.microsoft.com/) informacje|Pulpit nawigacyjny & zarządzanie lukami w zabezpieczeniach zagrożenia udostępnia informacje, za pomocą których Twój zespół operacji zabezpieczeń może ograniczyć ekspozycję na nią i poprawić poziom bezpieczeństwa Twojej organizacji. <br/><br/> Zobacz [informacje & zarządzanie lukami w zabezpieczeniach](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt) [i Omówienie Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use).|
|**[Microsoft Intune](/mem/intune/fundamentals/what-is-intune)** (zalecane)|Microsoft Intune (Intune), składnik programu [Microsoft Endpoint Manager](/mem/endpoint-manager-overview), dotyczy zarządzania urządzeniami przenośnymi (MDM) i zarządzania aplikacjami mobilnymi (MAM). Za pomocą usługi Intune możesz kontrolować sposób korzystania z urządzeń organizacji, w tym telefonów komórkowych, tabletów i laptopów. Możesz również skonfigurować określone zasady w celu kontrolowania aplikacji. <br/><br/> Zobacz [Zarządzanie programem Microsoft Defender dla punktu końcowego za pomocą usługi Intune](manage-mde-post-migration-intune.md).|
|**[Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction)**|Microsoft Endpoint Manager (Menedżer konfiguracji), dawniej znany jako System Center Configuration Manager, to składnik programu [Microsoft Endpoint Manager](/mem/endpoint-manager-overview). Menedżer konfiguracji to zaawansowane narzędzie do zarządzania użytkownikami, urządzeniami i oprogramowaniem. <br/><br/> Zobacz [Zarządzanie programem Microsoft Defender dla punktu końcowego za pomocą Menedżer konfiguracji](manage-mde-post-migration-configuration-manager.md).|
|**[zasady grupy obiektów w Azure Active Directory domenowych](/azure/active-directory-domain-services/manage-group-policy)**|[Azure Active Directory domen](/azure/active-directory-domain-services/overview) zawiera wbudowane obiekty zasady grupy dla użytkowników i urządzeń. Możesz dostosować wbudowane obiekty zasady grupy zgodnie z potrzebami środowiska, a także utworzyć niestandardowe obiekty zasady grupy obiekty i jednostki organizacyjne. <br/><br/> Zobacz [Zarządzanie programem Microsoft Defender dla punktu końcowego zasady grupy obiektów](manage-mde-post-migration-group-policy-objects.md).|
|**[PowerShell, WMI i MPCmdRun.exe](manage-mde-post-migration-other-tools.md)**|*Do zarządzania funkcjami ochrony przed zagrożeniami na urządzeniach organizacji zalecamy Microsoft Endpoint Manager (która obejmuje usługi Intune i Menedżer konfiguracji). Jednak niektóre ustawienia, takie jak ustawienia Program antywirusowy Microsoft Defender (punktów końcowych) na poszczególnych urządzeniach, można skonfigurować za pomocą programu PowerShell, WMI lub narzędzia MPCmdRun.exe urządzenia.* <br/><br/> Za pomocą programu PowerShell można zarządzać regułami Program antywirusowy Microsoft Defender, wykorzystywania ochrony i zmniejszania powierzchni ataków. Zobacz [Konfigurowanie programu Microsoft Defender dla punktu końcowego za pomocą programu PowerShell](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-powershell). <br/><br/> Do zarządzania Windows i wykluczeń możesz używać instrumentacji zarządzania danymi (WMI, Program antywirusowy Microsoft Defender Management Instrumentation). Zobacz [Konfigurowanie programu Microsoft Defender dla punktu końcowego przy użyciu usługi WMI](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi). <br/><br/> Narzędzie Microsoft Malware Protection Command-Line Utility (MPCmdRun.exe) umożliwia zarządzanie Program antywirusowy Microsoft Defender i wykluczeń, a także weryfikowanie połączeń między siecią a chmurą. Zobacz [Konfigurowanie programu Microsoft Defender dla punktu końcowego za pomocą MPCmdRun.exe](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe).|


## <a name="see-also"></a>Zobacz też

- [Adres dodatnich/ujemnych wyników fałszywie dodatnich w programie Microsoft Defender dla punktu końcowego](defender-endpoint-false-positives-negatives.md)
