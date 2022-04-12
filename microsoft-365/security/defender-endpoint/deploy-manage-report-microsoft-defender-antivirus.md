---
title: Wdrażanie i raportowanie Program antywirusowy Microsoft Defender oraz zarządzanie nimi
description: Program antywirusowy Microsoft Defender można wdrażać i zarządzać nimi za pomocą Intune, Microsoft Endpoint Configuration Manager, zasady grupy, programu PowerShell lub usługi WMI
keywords: wdrażanie, zarządzanie, aktualizowanie, ochrona, Program antywirusowy Microsoft Defender
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 4e0d249f7805c47be55ec42f3362ca1952c20ca3
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788507"
---
# <a name="deploy-manage-and-report-on-microsoft-defender-antivirus"></a>Wdrażanie i raportowanie Program antywirusowy Microsoft Defender oraz zarządzanie nimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender 

**Platformy**
- System Windows

Możesz wdrażać i raportować Program antywirusowy Microsoft Defender oraz zarządzać nimi na wiele sposobów.

Ponieważ klient Program antywirusowy Microsoft Defender jest zainstalowany jako podstawowa część Windows 10 i Windows 11, tradycyjne wdrożenie klienta w punktach końcowych nie ma zastosowania.

Jednak w większości przypadków nadal trzeba będzie włączyć usługę ochrony w punktach końcowych przy użyciu Microsoft Intune, Microsoft Endpoint Configuration Manager, Microsoft Defender dla Chmury lub zasady grupy  Obiekty opisane w poniższej tabeli.

Zostaną również wyświetlone dodatkowe linki do następujących elementów:

- Zarządzanie ochroną Program antywirusowy Microsoft Defender, w tym zarządzanie aktualizacjami produktów i ochrony
- Raportowanie ochrony Program antywirusowy Microsoft Defender

> [!IMPORTANT]
> W większości przypadków Windows 10 lub Windows 11 wyłączy Program antywirusowy Microsoft Defender, jeśli znajdzie inny uruchomiony i aktualny produkt antywirusowy. Należy wyłączyć lub odinstalować produkty antywirusowe innych firm, zanim Program antywirusowy Microsoft Defender będzie działać. Jeśli ponownie włączysz lub zainstalujesz produkty antywirusowe innych firm, Windows 10 lub Windows 11 automatycznie wyłączy Program antywirusowy Microsoft Defender.

Narzędzie|Opcje wdrażania (<a href="#fn2" id="ref2">2</a>)|Opcje zarządzania (konfiguracja w całej sieci i wdrożenie zasad lub planu bazowego) ([3](#fn3))|Opcje raportowania
---|---|---|---
Microsoft Intune|[Dodawanie ustawień ochrony punktu końcowego w Intune](/intune/endpoint-protection-configure)|[Konfigurowanie ustawień ograniczeń urządzenia w Intune](/intune/device-restrictions-configure)| [Zarządzanie urządzeniami przy użyciu konsoli Intune](/intune/device-management)
Microsoft Endpoint Manager ([1](#fn1))|Użyj roli [Endpoint Protection punkt systemu lokacji][] i [włącz Endpoint Protection z niestandardowymi ustawieniami klienta][]|W przypadku [domyślnych i dostosowanych zasad ochrony przed złośliwym kodem][] i [zarządzania klientami][]|Z domyślnym obszarem roboczym [Configuration Manager Monitorowanie][] i [alertami e-mail][]
zasady grupy i Active Directory (przyłączone do domeny)|Użyj obiektu zasady grupy, aby wdrożyć zmiany konfiguracji i upewnić się, że Program antywirusowy Microsoft Defender jest włączona.|Użyj obiektów zasady grupy (GPO), aby [Skonfigurować opcje aktualizacji dla Program antywirusowy Microsoft Defender][] i [Konfigurowanie funkcji Windows Defender][]|Raportowanie punktów końcowych nie jest dostępne w przypadku zasady grupy. Możesz wygenerować listę [Zasad grupy, aby określić, czy nie zastosowano żadnych ustawień lub zasad][]
PowerShell|Wdrażanie przy użyciu zasady grupy, Microsoft Endpoint Configuration Manager lub ręcznie w poszczególnych punktach końcowych.|Użyj poleceń cmdlet [Set-MpPreference] i [Update-MpSignature] dostępnych w module Defender.|Użyj odpowiednich poleceń cmdlet [Get- dostępnych w module Defender][]
Instrumentacja zarządzania Windows|Wdrażanie przy użyciu zasady grupy, Microsoft Endpoint Configuration Manager lub ręcznie w poszczególnych punktach końcowych.|Użyj metody [Set klasy MSFT_MpPreference][] i metody [Update klasy MSFT_MpSignature][]|Użyj klasy [MSFT_MpComputerStatus][] i metody get skojarzonych klas w [dostawcy WMIv2 Windows Defender][]
Microsoft Azure|Wdróż Microsoft Antimalware dla platformy Azure w [Azure Portal przy użyciu Visual Studio konfiguracji maszyny wirtualnej lub przy użyciu poleceń cmdlet Azure PowerShell](/azure/security/azure-security-antimalware#antimalware-deployment-scenarios). Program [Endpoint Protection można również zainstalować w Microsoft Defender dla Chmury*](/azure/security-center/security-center-install-endpoint-protection)|Konfigurowanie [Microsoft Antimalware dla Virtual Machines i Cloud Services przy użyciu poleceń cmdlet Azure PowerShell](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) lub [używanie przykładów kodu](https://gallery.technet.microsoft.com/Antimalware-For-Azure-5ce70efe)|Użyj [Microsoft Antimalware dla Virtual Machines i Cloud Services z poleceniami cmdlet Azure PowerShell](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets), aby włączyć monitorowanie. Możesz również przejrzeć raporty użycia w Azure Active Directory, aby określić podejrzane działania, w tym raport [Prawdopodobnie zainfekowane urządzenia][] i skonfigurować narzędzie SIEM do raportowania [Program antywirusowy Microsoft Defender zdarzeń][] i dodać to narzędzie jako aplikację w AAD.

1. <span id="fn1" />Dostępność niektórych funkcji i funkcji, szczególnie związanych z ochroną dostarczaną przez chmurę, różni się między Microsoft Endpoint Manager (Current Branch) i System Center 2012 Configuration Manager. W tej bibliotece skupiliśmy się na Windows 10, Windows 11, Windows Server 2016 i Microsoft Endpoint Manager (Current Branch). Aby zapoznać się z tabelą opisującą główne różnice, zobacz [Use Microsoft cloud-provided protection in Program antywirusowy Microsoft Defender (Korzystanie z ochrony firmy Microsoft w chmurze w Program antywirusowy Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)). [(Wróć do tabeli)](#ref2)

2. <span id="fn2" />W Windows 10 i Windows 11 Program antywirusowy Microsoft Defender jest składnikiem dostępnym bez instalowania lub wdrażania dodatkowego klienta lub usługi. Zostanie ona automatycznie włączona, gdy produkty antywirusowe innych firm zostaną odinstalowane lub nieaktualne (z wyjątkiem Windows Server 2016). Tradycyjne wdrożenie nie jest zatem wymagane. Wdrożenie w tym miejscu odnosi się do zapewnienia, że składnik Program antywirusowy Microsoft Defender jest dostępny i włączony w punktach końcowych lub serwerach. [(Wróć do tabeli)](#ref2)

3. <span id="fn3" />Konfiguracja funkcji i ochrony, w tym konfigurowanie aktualizacji produktów i ochrony, opisano w sekcji [Konfigurowanie funkcji Program antywirusowy Microsoft Defender](configure-notifications-microsoft-defender-antivirus.md) w tej bibliotece. [(Wróć do tabeli)](#ref2)

## <a name="in-this-section"></a>W tej sekcji

Temat | Opis
---|---
[Wdrażanie i włączanie ochrony Program antywirusowy Microsoft Defender](deploy-microsoft-defender-antivirus.md) | Chociaż klient jest instalowany jako podstawowa część Windows 10 lub Windows 11, a tradycyjne wdrożenie nie ma zastosowania, nadal trzeba będzie włączyć klienta w punktach końcowych przy użyciu Microsoft Endpoint Configuration Manager, Microsoft Intune lub zasady grupy obiektów.
[Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender i stosowanie planów bazowych](manage-updates-baselines-microsoft-defender-antivirus.md) | Istnieją dwie części do aktualizowania Program antywirusowy Microsoft Defender: aktualizowanie klienta w punktach końcowych (aktualizacje produktów) i aktualizowanie analizy zabezpieczeń (aktualizacje ochrony). Analizę zabezpieczeń można aktualizować na wiele sposobów przy użyciu Microsoft Endpoint Configuration Manager, zasady grupy, programu PowerShell i usługi WMI.
[Monitorowanie i raportowanie ochrony Program antywirusowy Microsoft Defender](report-monitor-microsoft-defender-antivirus.md) | Możesz użyć Microsoft Intune, Microsoft Endpoint Configuration Manager, dodatku Update Compliance dla pakietu Microsoft Operations Management Suite lub produktu SIEM innej firmy (korzystając z dzienników zdarzeń Windows) w celu monitorowania stanu ochrony i tworzenia raportów dotyczących ochrony punktu końcowego.

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)
    
