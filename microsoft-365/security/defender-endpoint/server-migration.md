---
title: Scenariusze migracji z serwera dla nowej wersji programu Microsoft Defender dla punktu końcowego
description: Ten artykuł zawiera omówienie sposobu migrowania serwerów z poprzedniego rozwiązania opartego na programie MMA do bieżącego pakietu rozwiązania ujednoliconego programu Defender for Endpoint.
keywords: migrowanie serwera, serwera, 2012r2, 2016, migracja serwera, zarządzanie urządzeniami, konfigurowanie programu Microsoft Defender dla serwerów punktów końcowych, dołączanie programu Microsoft Defender dla serwerów punktów końcowych
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
ms.author: macapara
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1a78d99650015aa0da92e35787a164b5c5a07b71
ms.sourcegitcommit: cde34d38bdfb6335b980f1c48c6b218da6a64bf8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/20/2022
ms.locfileid: "63013310"
---
# <a name="server-migration-scenarios-from-the-previous-mma-based-microsoft-defender-for-endpoint-solution"></a>Scenariusze migracji z serwera z poprzedniego rozwiązania opartego na programie Microsoft Defender for Endpoint opartego na programie MMA

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- Windows Server 2012 R2
- System Windows Server 2016
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

> [!NOTE]
> Przed przystąpieniem Program antywirusowy Microsoft Defender uaktualnianie zawsze upewnij się Windows Server 2016 że dane są w pełni zaktualizowane. Aby otrzymywać regularne ulepszenia i poprawki dotyczące składnika czujnika EDR, upewnij się, Windows, że jest stosowana lub zatwierdzona aktualizacja [KB5005292](https://go.microsoft.com/fwlink/?linkid=2168277). Aby dodatkowo aktualizować składniki ochrony, zapoznaj się z informacjami [na Program antywirusowy Microsoft Defender i stosowaniem linii bazowych](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions).

Poniższe instrukcje dotyczą nowego pakietu ujednoliconego rozwiązania i instalatora programu Microsoft Defender for Endpoint Windows Server 2012 R2 i Windows Server 2016. Ten artykuł zawiera szczegółowe instrukcje dotyczące różnych możliwych scenariuszy migracji, od poprzedniego do bieżącego rozwiązania. Te kroki wysokiego poziomu są w zamierzeniu wskazówkami dotyczącymi dostosowania narzędzi do wdrażania i konfiguracji dostępnych w Twoim środowisku.

> [!NOTE]
> Uaktualnienia systemu operacyjnego z zainstalowanym programem Microsoft Defender for Endpoint nie są obsługiwane. Przed uaktualnieniem odinstaluj program, a następnie odinstaluj go.

> [!NOTE]
> Podczas wyświetlania wersji zapoznawczej Microsoft Endpoint Configuration Manager pełną automatyzację i integrację w celu przeprowadzenia automatycznego uaktualnienia będą dostępne w nowszej wersji mecm. W wersji 2107 z najnowszym pakietem zbiorczym poprawki możesz użyć węzła programu Endpoint Protection do konfiguracji, zasady grupy, Programu PowerShell, programu Microsoft Endpoint Manager dołączania dzierżawy lub konfiguracji lokalnej. Ponadto możesz wykorzystać istniejące funkcje w programie Microsoft Endpoint Configuration Manager w celu zautomatyzowania czynności ręcznego uaktualniania, czyli metod opisanych poniżej.


## <a name="installer-script"></a>Skrypt Instalatora

Aby ułatwić uaktualnienia, Microsoft Endpoint Configuration Manager lub program Microsoft Defender dla chmury nie jest w użyciu lub nie jest jeszcze dostępny do przeprowadzenia uaktualnienia, możesz użyć [tego skryptu uaktualniania](https://github.com/microsoft/mdefordownlevelserver). Pomaga w automatyzowanie następujących wymaganych czynności:

1. Usuń obszar roboczy usługi OMS programu Microsoft Defender dla punktu końcowego (OPCJONALNIE).
2. Usuń System Center Endpoint Protection, jeśli został zainstalowany.
3. W razie potrzeby pobierz i zainstaluj (Windows Server 2012 R2). [](configure-server-endpoints.md#prerequisites)
4. Zainstaluj program Microsoft Defender dla punktu końcowego.
5. Zastosuj skrypt dołączania do **używania w zasady grupy** pobranych z [Microsoft 365 Defender](https://security.microsoft.com).

Aby użyć skryptu, pobierz go do katalogu instalacji, w którym również umieszczono pakiety instalacji i dołączania (zobacz [Konfigurowanie punktów końcowych serwera](configure-server-endpoints.md).

PRZYKŁAD: .\install.ps1 -RemoveMMA <YOUR_WORKSPACE_ID> -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd"

## <a name="microsoft-endpoint-configuration-manager-migration-scenarios"></a>Microsoft Endpoint Configuration Manager scenariuszy migracji 

### <a name="you-are-currently-using-microsoft-endpoint-configuration-manager-to-manage-your-servers-including-system-center-endpoint-protection-scep-and-are-running-the-microsoft-monitoring-agent-mma-based-sensor-you-want-to-upgrade-to-the-microsoft-defender-for-endpoint-unified-solution-preview"></a>Obecnie używasz oprogramowania Microsoft Endpoint Configuration Manager do zarządzania serwerami, w tym System Center Endpoint Protection (SCEP) i korzystasz z czujnika opartego na Microsoft Monitoring Agent MMA. Chcesz uaktualnić program Microsoft Defender for Endpoint do wersji Preview rozwiązania **ujednoliconego**.

>[!NOTE]
>Musisz mieć wersję Microsoft Endpoint Configuration Manager 2107.


Kroki migracji: 

1. W pełni zaktualizuj komputer, w tym Program antywirusowy Microsoft Defender (Windows Server 2016).
2. Utwórz nową kolekcję z regułami członkostwa, aby dołączyć komputery do migrowania.
3. [Utwórz aplikację,](/mem/configmgr/apps/deploy-use/create-applications) aby wykonać następujące zadania: 
   1. Usuń konfigurację obszaru roboczego programu MMA dla programu Microsoft Defender dla punktu końcowego. Zobacz [Usuwanie obszaru roboczego przy użyciu programu PowerShell](/azure/azure-monitor/agents/agent-manage). Ten krok jest opcjonalny. Poprzedni czujnik EDR przestanie działać, gdy nowy czujnik stanie się aktywny (pamiętaj, że może to potrwać kilka godzin).
   2. Odinstaluj SCEPT.
   3. Zainstaluj [wymagania wstępne, jeśli](configure-server-endpoints.md#prerequisites) to konieczne.
   4. Zainstaluj program Microsoft Defender for Endpoint (zobacz [Konfigurowanie punktów końcowych serwera](configure-server-endpoints.md).
   5. Zastosuj skrypt dołączania do **używania w zasady grupy** pobranych z [Microsoft 365 Defender](https://security.microsoft.com). 

   > [!TIP]
   > Możesz użyć skryptu [instalatora](server-migration.md#installer-script) jako części aplikacji w celu zautomatyzowania powyższych kroków.
4. Wdeksuj aplikację w nowej kolekcji.
5. Utwórz i/lub przypisz (istniejące) zasady Endpoint Protection do kolekcji.
6. Stosowanie aktualizacji.

### <a name="you-are-currently-using-microsoft-endpoint-configuration-manager-to-manage-your-servers-are-running-a-non-microsoft-antivirus-solution-and-the-mma-based-sensor-you-want-to-upgrade-to-the-new-microsoft-defender-for-endpoint"></a>Obecnie zarządzasz serwerami Microsoft Endpoint Configuration Manager, korzystasz z rozwiązania antywirusowego firm innych niż Microsoft oraz czujnika opartego na narzędziu MMA. Chcesz uaktualnić program Microsoft Defender for Endpoint do nowej wersji.

Kroki migracji:

1. W pełni zaktualizuj komputer, w tym Program antywirusowy Microsoft Defender (Windows Server 2016).
2. Utwórz nową kolekcję z regułami członkostwa, aby dołączyć komputery do migrowania. 
3. Upewnij się, że zarządzanie oprogramowaniem antywirusowym innej firmy nie wypycha już oprogramowania antywirusowego do tych komputerów.*
4. Tworzenie zasad w węźle Endpoint Protection MECM i przekieruj je do nowo utworzonej kolekcji*.
5. Utwórz aplikację, aby wykonać następujące zadania:
   1. Usuń konfigurację obszaru roboczego programu MMA dla programu Microsoft Defender dla punktu końcowego. Zobacz [Usuwanie obszaru roboczego przy użyciu programu PowerShell](/azure/azure-monitor/agents/agent-manage). Ten krok jest opcjonalny. Poprzedni czujnik EDR przestanie działać, gdy nowy czujnik stanie się aktywny (pamiętaj, że może to potrwać kilka godzin).
   2. Zainstaluj [wymagania wstępne, jeśli](configure-server-endpoints.md#prerequisites) to konieczne.
   3. Zainstaluj program Microsoft Defender for Endpoint dla pakietu Windows Server 2012 R2 i 2016 i **włącz tryb pasywny**. Zobacz [Instalowanie Program antywirusowy Microsoft Defender przy użyciu wiersza polecenia](configure-server-endpoints.md#install-microsoft-defender-for-endpoint-using-the-command-line).
   4. Zastosuj skrypt dołączania do **używania w zasady grupy** pobranych z [Microsoft 365 Defender](https://security.microsoft.com).
6. Stosowanie aktualizacji.
7. Usuń oprogramowanie antywirusowe innych firm, używając konsoli oprogramowania antywirusowego innego niż Microsoft lub używając programu Microsoft Endpoint Configuration Manager w razie potrzeby. Upewnij się, że usuwasz konfigurację trybu pasywnego.*

> [!TIP]
> Aby zautomatyzować [powyższe kroki](server-migration.md#installer script) , możesz użyć skryptu installer jako części aplikacji. Aby włączyć tryb pasywny, zastosuj flagę -Pasywne. Na przykład:\install.ps1 -RemoveMMA <YOUR_WORKSPACE_ID> -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd" -Passive

*Te kroki mają zastosowanie tylko wtedy, gdy zamierzasz zastąpić rozwiązanie antywirusowe inne niż firmy Microsoft. Zobacz [razem lepiej: Program antywirusowy Microsoft Defender i Microsoft Defender for Endpoint](why-use-microsoft-defender-antivirus.md).

Aby przenieść komputer poza tryb pasywny, ustaw następujący klawisz na 0:

Ścieżka: HKLM\SOFTWARE\Policies\Microsoft\Windows Nazwa zaawansowanej ochrony przed zagrożeniami: ForceDefenderPassiveMode Type: REG_DWORD Wartość: 0


## <a name="other-migration-scenarios"></a>Inne scenariusze migracji

### <a name="you-have-a-server-that-has-been-onboarded-using-the-mma-based-microsoft-defender-for-endpoint-it-has-scep-installed-windows-server-2012-r2-or-microsoft-defender-antivirus-windows-server-2016-this-machine-is-not-managed-through-microsoft-defender-for-cloud-microsoft-endpoint-manager-or-microsoft-endpoint-configuration-manager"></a>Masz serwer, który został wnoszony za pomocą programu Microsoft Defender for Endpoint opartego na programie MMA. Ma zainstalowany SCEPT (Windows Server 2012 R2) lub Program antywirusowy Microsoft Defender (Windows Server 2016). Ten komputer nie **jest zarządzany** za pośrednictwem programu Microsoft Defender dla Microsoft Endpoint Manager, Microsoft Endpoint Configuration Manager.

1. W pełni zaktualizuj komputer, w tym Program antywirusowy Microsoft Defender (Windows Server 2016).
2. Usuń konfigurację obszaru roboczego programu MMA dla programu Microsoft Defender dla punktu końcowego. Zobacz [Usuwanie obszaru roboczego przy użyciu programu PowerShell](/azure/azure-monitor/agents/agent-manage).
3. Odinstaluj System Center Endpoint Protection (Windows Server 2012 R2).
4. Zainstaluj [wymagania wstępne, jeśli](configure-server-endpoints.md#prerequisites) to konieczne. 
5. Zainstaluj program Microsoft Defender for Endpoint (zobacz [Konfigurowanie punktów końcowych serwera](configure-server-endpoints.md)).
6. Zastosuj skrypt dołączania do **używania w zasady grupy** pobranych z [Microsoft 365 Defender](https://security.microsoft.com). 
7. Stosowanie aktualizacji.
8. Tworzenie i stosowanie zasad przy zasady grupy, programie PowerShell lub rozwiązaniu do zarządzania innych firm.

> [!TIP]
> Za pomocą skryptu instalatora można zautomatyzować powyższe czynności.

### <a name="you-have-a-server-on-which-you-want-to-install-microsoft-defender-for-endpoint-it-has-a-non-microsoft-endpoint-protection-or-endpoint-detection-and-response-solution-installed-you-do-not-intend-to-use-microsoft-endpoint-configuration-manager-or-microsoft-defender-for-cloud-you-use-your-own-deployment-mechanism"></a>Masz serwer, na którym chcesz zainstalować usługę Microsoft Defender for Endpoint. Ma on zainstalowaną ochronę punktu końcowego innego niż wykrywanie i reagowanie w punktach końcowych firmy Microsoft. Użytkownik nie zamierza używać programu Microsoft Endpoint Configuration Manager ani programu Microsoft Defender dla chmury. Używasz własnego mechanizmu wdrażania. 

1. W pełni zaktualizuj komputer, w tym Program antywirusowy Microsoft Defender (Windows Server 2016).
2. Zainstaluj program Microsoft Defender for Endpoint dla pakietu Windows Server 2012 R2 & 2016 i włącz **tryb pasywny**. Zobacz [Instalowanie Program antywirusowy Microsoft Defender przy użyciu wiersza polecenia](configure-server-endpoints.md#install-microsoft-defender-for-endpoint-using-the-command-line).
3. Zastosuj skrypt dołączania, odpowiedni do Twojego środowiska, [pobrany z Microsoft 365 Defender](https://security.microsoft.com). 
4. Usuń rozwiązanie punktu końcowego innego niż firmy Microsoft lub wykrywanie i reagowanie w punktach końcowych i usuń tryb pasywny.*
5. Stosowanie aktualizacji.
6. Tworzenie i stosowanie zasad przy zasady grupy, programie PowerShell lub rozwiązaniu do zarządzania innych firm.

> [!TIP]
> Za pomocą skryptu [instalatora można](server-migration.md#installer-script) zautomatyzować kroki od 1 do 4. Aby włączyć tryb pasywny, zastosuj flagę -Pasywne, co zapewni, że program antywirusowy Defender przejdzie w tryb pasywny przed dodaniem do trybu pasywnego i nie zakłóci działania rozwiązania ochrony przed złośliwym oprogramowaniem firmy Microsoft. Następnie, aby po dojściu do obsługi funkcji programu EDR, takich jak program EDR Block, upewnić się, że program antywirusowy Defender pozostaje w trybie pasywnym. PRZYKŁAD: `.\install.ps1 -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd" -Passive`


*Ten krok ma zastosowanie tylko wtedy, gdy zamierzasz zastąpić rozwiązanie antywirusowe inne niż firmy Microsoft. Zalecamy używanie programu Program antywirusowy Microsoft Defender, dostępnego w programie Microsoft Defender for Endpoint, w celu zapewnienia pełnego zestawu możliwości. Zobacz [razem lepiej: Program antywirusowy Microsoft Defender i Microsoft Defender for Endpoint](why-use-microsoft-defender-antivirus.md).

Aby przenieść komputer poza tryb pasywny, ustaw następujący klawisz na 0:

Ścieżka: HKLM\SOFTWARE\Policies\Microsoft\Windows Nazwa zaawansowanej ochrony przed zagrożeniami: ForceDefenderPassiveMode Type: REG_DWORD Wartość: 0


## <a name="microsoft-defender-for-cloud-scenarios"></a>Scenariusze dotyczące programu Microsoft Defender w chmurze

### <a name="youre-using-microsoft-defender-for-cloud-the-microsoft-monitoring-agent-mma-andor-microsoft-antimalware-for-azure-scep-are-installed-and-you-want-to-upgrade"></a>Używasz programu Microsoft Defender dla chmury. Zainstalowany Microsoft Monitoring Agent (MMA) i/lub Microsoft Antimalware dla platformy Azure (SCEPT) i chcesz dokonać uaktualnienia.
Jeśli używasz programu Microsoft Defender dla chmury, możesz skorzystać z automatycznego procesu uaktualniania. Zobacz [Chroninie punktów końcowych za pomocą zintegrowanej usługi Defender dla chmury i rozwiązania EDR: Microsoft Defender for Endpoint](/azure/security-center/security-center-wdatp#enable-the-microsoft-defender-for-endpoint-integration).

## <a name="group-policy-configuration"></a>zasady grupy konfiguracji
W przypadku zasady grupy przy użyciu programu zasady grupy upewnij się, że używasz najnowszych plików ADMX w centralnym magazynie, aby uzyskać dostęp do właściwych opcji zasad programu Defender dla punktu końcowego. Informacje na [temat tworzenia i](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) zarządzania centralną magazynem witryn zasady grupy administracyjnego w programie Windows oraz pobierania najnowszych plików do używania z **Windows 10.**
