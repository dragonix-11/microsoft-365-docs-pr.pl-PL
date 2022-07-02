---
title: Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender po początkowej konfiguracji lub migracji
description: Po przejściu na Ochrona punktu końcowego w usłudze Microsoft Defender następnym krokiem jest zarządzanie funkcjami ochrony przed zagrożeniami
keywords: po migracji, zarządzanie, operacje, konserwacja, wykorzystanie, Ochrona punktu końcowego w usłudze Microsoft Defender, edr
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
ms.topic: conceptual
ms.date: 07/01/2022
ms.reviewer: chventou
ms.openlocfilehash: d00de67b52f521042d5595320346f875f8c89c9e
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607570"
---
# <a name="manage-microsoft-defender-for-endpoint-after-initial-setup-or-migration"></a>Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender po początkowej konfiguracji lub migracji

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Po skonfigurowaniu i skonfigurowaniu Ochrona punktu końcowego w usłudze Microsoft Defender następnym krokiem jest zarządzanie funkcjami i możliwościami. Zalecamy zarządzanie urządzeniami i ustawieniami zabezpieczeń organizacji przy użyciu usługi [Microsoft Endpoint Manager](/mem/endpoint-manager-overview), w tym [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) i [Configuration Manager punktu końcowego firmy Microsoft](/mem/configmgr/core/understand/introduction). Można jednak użyć innych narzędzi/metod, takich jak [zasady grupy Objects w usłudze Azure Active Directory Domain Services](/azure/active-directory-domain-services/manage-group-policy).

W poniższej tabeli wymieniono różne narzędzia/metody, których można użyć, z linkami, aby dowiedzieć się więcej.

|Narzędzie/metoda|Opis|
|---|---|
|**[Szczegółowe informacje dotyczące pulpitu nawigacyjnego zarządzania zagrożeniami i lukami w zabezpieczeniach](/windows/security/threat-protection/microsoft-defender-atp/tvm-dashboard-insights)** w [portalu Microsoft 365 Defender](https://security.microsoft.com/)|Pulpit nawigacyjny zarządzania lukami w zabezpieczeniach & zapewnia praktyczne informacje, których zespół ds. operacji zabezpieczeń może użyć w celu zmniejszenia narażenia i poprawy stanu bezpieczeństwa organizacji. <br/><br/> Zobacz [Zarządzanie lukami w zabezpieczeniach & zagrożeń](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt) i [Omówienie Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use).|
|**[Microsoft Intune](/mem/intune/fundamentals/what-is-intune)** (zalecane)|Microsoft Intune (Intune), składnik Endpoint Manager [firmy Microsoft](/mem/endpoint-manager-overview), koncentruje się na zarządzaniu urządzeniami przenośnymi (MDM) i zarządzaniu aplikacjami mobilnymi (MAM). Dzięki Intune możesz kontrolować sposób używania urządzeń organizacji, w tym telefonów komórkowych, tabletów i laptopów. Można również skonfigurować określone zasady do kontrolowania aplikacji. <br/><br/> Zobacz [Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu Intune](manage-mde-post-migration-intune.md).|
|**[Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction)**|Microsoft Endpoint Manager (Configuration Manager), wcześniej znany jako System Center Configuration Manager, jest składnikiem [microsoft Endpoint Manager](/mem/endpoint-manager-overview). Configuration Manager to zaawansowane narzędzie do zarządzania użytkownikami, urządzeniami i oprogramowaniem. <br/><br/> Zobacz [Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender za pomocą Configuration Manager](manage-mde-post-migration-configuration-manager.md).|
|**[obiekty zasady grupy w usłudze Azure Active Directory Domain Services](/azure/active-directory-domain-services/manage-group-policy)**|[Usługa Azure Active Directory Domain Services](/azure/active-directory-domain-services/overview) obejmuje wbudowane obiekty zasady grupy dla użytkowników i urządzeń. Możesz dostosować wbudowane obiekty zasady grupy zgodnie z potrzebami środowiska, a także utworzyć niestandardowe obiekty zasady grupy i jednostki organizacyjne . <br/><br/> Zobacz [Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender za pomocą obiektów zasady grupy](manage-mde-post-migration-group-policy-objects.md).|
|**[PowerShell, WMI i MPCmdRun.exe](manage-mde-post-migration-other-tools.md)**|*Zalecamy używanie usługi Microsoft Endpoint Manager (w tym Intune i Configuration Manager) do zarządzania funkcjami ochrony przed zagrożeniami na urządzeniach organizacji. Można jednak skonfigurować niektóre ustawienia, takie jak ustawienia programu antywirusowego Microsoft Defender na poszczególnych urządzeniach (punktach końcowych) przy użyciu programu PowerShell, usługi WMI lub narzędzia MPCmdRun.exe.* <br/><br/> Program PowerShell umożliwia zarządzanie programem antywirusowym Microsoft Defender, ochroną przed lukami w zabezpieczeniach i regułami zmniejszania obszaru ataków. Zobacz [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu programu PowerShell](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-powershell). <br/><br/> Instrumentacja zarządzania windows (WMI) umożliwia zarządzanie programem antywirusowym Microsoft Defender i wykluczeniami. Zobacz [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender za pomocą usługi WMI](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi). <br/><br/> Do zarządzania programem antywirusowym Microsoft Defender i wykluczeń oraz weryfikowania połączeń między siecią a chmurą można użyć narzędzia Microsoft Malware Protection Command-Line Utility (MPCmdRun.exe). Zobacz [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender za pomocą MPCmdRun.exe](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe).|


## <a name="see-also"></a>Zobacz też

- [Rozwiązywanie problemów z wynikami fałszywie pozytywnymi/negatywnymi w ochronie punktu końcowego w usłudze Microsoft Defender](defender-endpoint-false-positives-negatives.md)
