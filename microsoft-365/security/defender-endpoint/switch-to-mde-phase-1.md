---
title: Przełączanie do Ochrona punktu końcowego w usłudze Microsoft Defender — przygotowanie
description: Przygotuj się do przejścia na Ochrona punktu końcowego w usłudze Microsoft Defender. Zaktualizuj urządzenia i skonfiguruj połączenia sieciowe.
keywords: migracja, Ochrona punktu końcowego w usłudze Microsoft Defender, najlepsze rozwiązania
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
- m365solution-migratetomdatp
- m365solution-mcafeemigrate
- m365solution-symantecmigrate
ms.topic: article
ms.custom:
- migrationguides
- admindeeplinkDEFENDER
ms.date: 04/01/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: c08ab1c96adc2b9d83cc6869573f2f0dbe75ac78
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782924"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-1-prepare"></a>Przełączanie do Ochrona punktu końcowego w usłudze Microsoft Defender — faza 1: przygotowanie

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

| ![Faza 1. Przygotowanie.](images/phase-diagrams/prepare.png#lightbox)<br/>Faza 1. Przygotowanie | [![Faza 2. Konfiguracja](images/phase-diagrams/setup.png#lightbox)](switch-to-mde-phase-2.md)<br/>[Faza 2. Konfiguracja](switch-to-mde-phase-2.md) | [![Faza 3. Dołączenie](images/phase-diagrams/onboard.png#lightbox)](switch-to-mde-phase-3.md)<br/>[Faza 3. Dołączenie](switch-to-mde-phase-3.md) |
|--|--|--|
|*Jesteś tutaj!*| | |

**Witamy w fazie przygotowywania [przełączania do usługi Defender for Endpoint](switch-to-mde-overview.md#the-migration-process)**.

Ta faza migracji obejmuje następujące kroki:

1. [Pobieranie i wdrażanie aktualizacji na urządzeniach organizacji](#get-and-deploy-updates-across-your-organizations-devices)
2. [Pobierz usługę Defender dla punktu końcowego](#get-microsoft-defender-for-endpoint).
3. [Udzielanie dostępu do portalu Microsoft 365 Defender](#grant-access-to-the-microsoft-365-defender-portal).
4. [Konfigurowanie ustawień serwera proxy urządzenia i łączności z Internetem](#configure-device-proxy-and-internet-connectivity-settings).

## <a name="get-and-deploy-updates-across-your-organizations-devices"></a>Pobieranie i wdrażanie aktualizacji na urządzeniach organizacji

Najlepszym rozwiązaniem jest aktualizowanie urządzeń i punktów końcowych organizacji. Upewnij się, że istniejące rozwiązanie ochrony punktu końcowego i oprogramowania antywirusowego jest aktualne, a systemy operacyjne i aplikacje w organizacji również mają najnowsze aktualizacje. Teraz może to pomóc w zapobieganiu problemom w późniejszym czasie podczas migracji do usługi Defender for Endpoint i Program antywirusowy Microsoft Defender.

### <a name="make-sure-your-existing-solution-is-up-to-date"></a>Upewnij się, że istniejące rozwiązanie jest aktualne

Aktualizuj istniejące rozwiązanie ochrony punktów końcowych i upewnij się, że urządzenia organizacji mają najnowsze aktualizacje zabezpieczeń.

Potrzebujesz pomocy? Zapoznaj się z dokumentacją dostawcy rozwiązań.

### <a name="make-sure-your-organizations-devices-are-up-to-date"></a>Upewnij się, że urządzenia organizacji są aktualne

Potrzebujesz pomocy przy aktualizowaniu urządzeń organizacji? Zobacz następujące zasoby:

|OS|Zasób|
|---|---|
|System Windows|[Microsoft Update](https://www.update.microsoft.com)|
|macOS|[Jak zaktualizować oprogramowanie na komputerze Mac](https://support.apple.com/HT201541)|
|iOS|[Aktualizowanie iPhone, iPad lub iPoda touch](https://support.apple.com/HT204204)|
|Android|[Sprawdzanie, & zaktualizować wersję systemu Android](https://support.google.com/android/answer/7680439)|
|Linux|[Linux 101: aktualizowanie systemu](https://www.linux.com/training-tutorials/linux-101-updating-your-system)|

## <a name="get-microsoft-defender-for-endpoint"></a>Uzyskiwanie Ochrona punktu końcowego w usłudze Microsoft Defender

Po zaktualizowaniu urządzeń organizacji następnym krokiem jest pobranie usługi Defender for Endpoint, przypisanie licencji i upewnienie się, że usługa jest aprowizowana.

1. Kup lub wypróbuj usługę Defender for Endpoint już dziś. [Rozpocznij bezpłatną wersję próbną lub poproś o ofertę](https://aka.ms/mdatp).

2. Sprawdź, czy licencje są prawidłowo aprowizowane. [Sprawdź stan licencji](production-deployment.md#check-license-state).

3. Skonfiguruj dedykowane wystąpienie usługi Defender for Endpoint w chmurze. Zobacz [Konfiguracja punktu końcowego w usłudze Defender: Konfiguracja dzierżawy](production-deployment.md#tenant-configuration).

4. Jeśli punkty końcowe (takie jak urządzenia) w organizacji używają serwera proxy do uzyskiwania dostępu do Internetu, zobacz [Defender for Endpoint setup: Network configuration (Konfiguracja sieci w usłudze Defender for Endpoint).](production-deployment.md#network-configuration)

W tym momencie możesz udzielić dostępu administratorom zabezpieczeń i operatorom zabezpieczeń, którzy będą korzystać z <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>.

> [!NOTE]
> Portal Microsoft 365 Defender jest czasami nazywany portalem usługi Defender for Endpoint i można uzyskać do niej dostęp pod adresem <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a>. Były Centrum zabezpieczeń usługi Microsoft Defender (https://securitycenter.windows.com) wkrótce nastąpi przekierowanie do portalu Microsoft 365 Defender. Aby dowiedzieć się więcej, zobacz [omówienie portalu Microsoft 365 Defender](portal-overview.md).

## <a name="grant-access-to-the-microsoft-365-defender-portal"></a>Udzielanie dostępu do portalu Microsoft 365 Defender

Portal <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender to miejsce</a>, w którym uzyskujesz dostęp do funkcji i możliwości usługi Defender for Endpoint oraz je konfigurujesz. Aby dowiedzieć się więcej, zobacz [Omówienie portalu Microsoft 365 Defender](use.md).

Uprawnienia do portalu Microsoft 365 Defender można udzielić przy użyciu uprawnień podstawowych lub kontroli dostępu opartej na rolach (RBAC). Zalecamy użycie kontroli RBAC, aby mieć bardziej szczegółową kontrolę nad uprawnieniami.

1. Planowanie ról i uprawnień dla administratorów zabezpieczeń i operatorów zabezpieczeń. Zobacz [Kontrola dostępu oparta na rolach](prepare-deployment.md#role-based-access-control).

2. Skonfiguruj i skonfiguruj kontrolę dostępu opartą na rolach. Zalecamy używanie [Intune](/mem/intune/fundamentals/what-is-intune) do konfigurowania kontroli dostępu opartej na rolach, zwłaszcza jeśli organizacja używa kombinacji urządzeń z systemem Windows 10, macOS, iOS i Android. Zobacz [konfigurowanie kontroli dostępu opartej na rolach przy użyciu Intune](/mem/intune/fundamentals/role-based-access-control).

    Jeśli Twoja organizacja wymaga metody innej niż Intune, wybierz jedną z następujących opcji:

    - [Menedżer konfiguracji](/mem/configmgr/core/servers/deploy/configure/configure-role-based-administration)

    - [Zaawansowane zarządzanie zasady grupy](/microsoft-desktop-optimization-pack/agpm)
    
    - [Windows Admin Center](/windows-server/manage/windows-admin-center/overview)

3. Udzielanie dostępu do portalu Microsoft 365 Defender. (Potrzebujesz pomocy? Zobacz [Zarządzanie dostępem do portalu przy użyciu kontroli dostępu opartej na rolach](rbac.md).

## <a name="configure-device-proxy-and-internet-connectivity-settings"></a>Konfigurowanie ustawień serwera proxy urządzenia i łączności z Internetem

Aby włączyć komunikację między urządzeniami i usługą Defender for Endpoint, skonfiguruj ustawienia serwera proxy i Internetu. Poniższa tabela zawiera linki do zasobów, których można użyć do konfigurowania ustawień serwera proxy i Internetu dla różnych systemów operacyjnych i możliwości:

|Możliwości|System operacyjny|Zasoby|
|---|---|---|
|[Wykrywanie i reagowanie na punkty końcowe](overview-endpoint-detection-response.md) (EDR)|[Windows 10](/windows/release-health/release-information) lub nowsze<br/><br/>Windows Server 2022 <br/><br/>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/><br/>[Windows Server 1803 lub nowszy](/windows-server/get-started/whats-new-in-windows-server-1803)<br/><br/>[Windows Server 2016*](/windows/release-health/status-windows-10-1607-and-windows-server-2016)<br/><br/>[Windows Server 2012 R2*](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)|[Konfigurowanie ustawień serwera proxy maszyny i łączności internetowej](configure-proxy-internet.md)|
|EDR [Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<br/><br/>[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows 7 z dodatkiem SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)|[Konfigurowanie ustawień serwera proxy i łączności z Internetem](onboard-downlevel.md#configure-proxy-and-internet-connectivity-settings)|
|EDR|macOS (zobacz [Wymagania systemowe](microsoft-defender-endpoint-mac.md)|[Defender for Endpoint w systemie macOS: Połączenia sieciowe](microsoft-defender-endpoint-mac.md#network-connections)|
|[Program antywirusowy Microsoft Defender](microsoft-defender-antivirus-in-windows-10.md)|[Windows 10](/windows/release-health/release-information) <br/><br/> [Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/><br/> Windows Server 2022 <br/><br/> [Windows Server 1803 lub nowszy](/windows-server/get-started/whats-new-in-windows-server-1803) <br/><br/> [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)<br/><br/>[Windows Server 2012 R2*](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)|[Skonfiguruj i zweryfikuj połączenia sieciowe programu antywirusowego Microsoft Defender](configure-network-connections-microsoft-defender-antivirus.md)|
|Antivirus|macOS (zobacz [Wymagania systemowe](microsoft-defender-endpoint-mac.md)|[Defender for Endpoint w systemie macOS: Połączenia sieciowe](microsoft-defender-endpoint-mac.md#network-connections)|
|Antivirus|Linux (zobacz [Wymagania systemowe](microsoft-defender-endpoint-linux.md#system-requirements))|[Defender for Endpoint w systemie Linux: połączenia sieciowe](microsoft-defender-endpoint-linux.md#network-connections)|

*Wymaga instalacji nowoczesnego, ujednoliconego rozwiązania dla Windows Server 2012 R2 i 2016. Aby uzyskać więcej informacji, zobacz [Dołączanie serwerów Windows do usługi Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/configure-server-endpoints).

## <a name="next-step"></a>Następny krok

**Gratulacje**! Ukończono fazę **przygotowywania** [przełączania do usługi Defender for Endpoint](switch-to-mde-overview.md#the-migration-process)!

- [Przejdź do konfigurowania usługi Defender dla punktu końcowego](switch-to-mde-phase-2.md).
