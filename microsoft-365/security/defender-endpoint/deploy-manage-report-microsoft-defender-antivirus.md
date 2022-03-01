---
title: Wdrażanie i zgłaszanie w Program antywirusowy Microsoft Defender
description: Możesz wdrażać aplikacje i zarządzać nimi za Program antywirusowy Microsoft Defender Intune, Microsoft Endpoint Configuration Manager, zasady grupy, PowerShell lub WMI
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
ms.openlocfilehash: 1ce212bf01b8c464760192a4bbd6355498d19c3c
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997795"
---
# <a name="deploy-manage-and-report-on-microsoft-defender-antivirus"></a>Wdrażanie i zgłaszanie w Program antywirusowy Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Wdrożenie aplikacji, zarządzanie nimi i zgłaszanie Program antywirusowy Microsoft Defender na wiele sposobów.

Ponieważ Program antywirusowy Microsoft Defender klienta jest instalowany jako podstawowa część programu Windows 10 i Windows 11, tradycyjne wdrażanie klienta do Twoich punktów końcowych nie ma zastosowania.

Jednak w większości przypadków konieczne będzie włączenie usługi ochrony na swoich punktach końcowych za pomocą programu Microsoft Intune, Microsoft Endpoint Configuration Manager, Microsoft Defender dla chmury lub obiektów zasady grupy, co opisano w poniższej tabeli.

Zobaczysz też dodatkowe linki dla:

- Zarządzanie Program antywirusowy Microsoft Defender siecią, w tym zarządzanie aktualizacjami produktów i ochrony
- Raportowanie dotyczące Program antywirusowy Microsoft Defender danych

> [!IMPORTANT]
> W większości przypadków oprogramowanie Windows 10 lub Windows 11 wyłączy program Program antywirusowy Microsoft Defender, jeśli znajdzie inny uruchomiony i aktualny produkt antywirusowy. Aby programy antywirusowe innych firm działały, musisz Program antywirusowy Microsoft Defender je wyłączyć. Jeśli ponownie włączysz lub zainstalujesz produkty antywirusowe innych firm, oprogramowanie Windows 10 lub Windows 11 automatycznie Program antywirusowy Microsoft Defender.

Narzędzie|Opcje wdrażania (<a href="#fn2" id="ref2">2</a>)|Opcje zarządzania (konfiguracja sieciowa i zasady lub wdrożenie bazowe) ([3](#fn3))|Opcje raportowania
---|---|---|---
Microsoft Intune|[Dodawanie ustawień ochrony punktu końcowego w usłudze Intune](/intune/endpoint-protection-configure)|[Konfigurowanie ustawień ograniczeń urządzeń w usłudze Intune](/intune/device-restrictions-configure)| [Zarządzanie urządzeniami przy użyciu konsoli Intune](/intune/device-management)
Microsoft Endpoint Manager ([1](#fn1))|Użyj [rola systemu Endpoint Protection punktowego] i [włącz Endpoint Protection klienta z niestandardowymi ustawieniami klienta][]|Z [domyślnymi i dostosowanymi zasadami ochrony przed złośliwym oprogramowaniem] i [zarządzaniem klientami][]|Z domyślnym obszarem roboczym monitorowania Menedżer konfiguracji[] i [alerty e-mail][]
zasady grupy Usługi Active Directory (przyłączone do domeny)|Użyj obiektu zasady grupy, aby wdrożyć zmiany konfiguracji i upewnić Program antywirusowy Microsoft Defender włączony.|Obiekty zasady grupy (GPOS) to [Konfigurowanie opcji aktualizacji dla programu Program antywirusowy Microsoft Defender][] i [Konfigurowanie Windows Defender funkcji][]|Raportowanie punktu końcowego nie jest dostępne w zasady grupy. Możesz wygenerować listę [Zasady grupy, aby określić, czy jakieś ustawienia lub zasady nie są stosowane][]
PowerShell|Wdrożenie za zasady grupy, Microsoft Endpoint Configuration Manager lub ręcznie w poszczególnych punktach końcowych.|Użyj cmdlet [Set-MpPreference] i [Update-MpSignature] dostępnych w module Defender.|Użyj odpowiednich [Get- cmdlet dostępnych w module Defender][]
Windows instrumentacja zarządzania|Wdrożenie za zasady grupy, Microsoft Endpoint Configuration Manager lub ręcznie w poszczególnych punktach końcowych.|Użyj metody [Ustaw klasę MSFT_MpPreference]] i [Metoda aktualizacji MSFT_MpSignature klasa]]|Użyj klasy [MSFT_MpComputerStatus][] i uzyskaj metodę skojarzoną z klasami w dostawcy [Windows Defender WMIv2][]
Microsoft Azure|Wd Microsoft Antimalware azure w portalu [Azure Portal, za pomocą](/azure/security/azure-security-antimalware#antimalware-deployment-scenarios) Visual Studio konfiguracji maszyny wirtualnej lub przy użyciu Azure PowerShell cmdlet. Możesz również zainstalować [ochronę punktu końcowego w programie Microsoft Defender dla chmury*](/azure/security-center/security-center-install-endpoint-protection)|Konfigurowanie Microsoft Antimalware maszyn wirtualnych i usług w chmurze [za Azure PowerShell cmdlet](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) lub [używanie przykładów kodów](https://gallery.technet.microsoft.com/Antimalware-For-Azure-5ce70efe)|Użyj Microsoft Antimalware maszyn wirtualnych i usług w chmurze z [Azure PowerShell cmdlet](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets), aby włączyć monitorowanie. Możesz również przeglądać raporty użycia w programie Azure Active Directory, aby ustalić podejrzaną aktywność, w tym raport [Być może zainfekowane urządzenia][] i skonfigurować narzędzie SIEM do zgłaszania zdarzeń [Program antywirusowy Microsoft Defender][] i dodawania tego narzędzia jako aplikacji w programie AAD.

1. <span id="fn1" />Dostępność niektórych funkcji, zwłaszcza związanych z ochroną dostarczaną w chmurze, różni się w Microsoft Endpoint Manager (Bieżąca gałąź) i System Center 2012 Menedżer konfiguracji. W tej bibliotece skupiliśmy się na Windows 10, Windows 11, Windows Server 2016 i Microsoft Endpoint Manager (Bieżąca gałąź). Aby [uzyskać informacje o głównych różnicach, Program antywirusowy Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md) artykule Używanie ochrony chmurowej firmy Microsoft w programie Program antywirusowy Microsoft Defender. [(Powrót do tabeli)](#ref2)

2. <span id="fn2" />W Windows 10 i Windows 11 Program antywirusowy Microsoft Defender to składnik dostępny bez instalowania lub wdrażania dodatkowego klienta lub usługi. Zostanie on automatycznie włączony, gdy produkty antywirusowe innych firm zostaną odinstalowane lub będą aktualne (z wyjątkiem Windows Server 2016). Tradycyjne wdrażanie nie jest więc wymagane. To wdrożenie ma na celu zapewnienie Program antywirusowy Microsoft Defender jest dostępny i włączony w punktach końcowych lub serwerach. [(Powrót do tabeli)](#ref2)

3. <span id="fn3" />Konfigurowanie funkcji i ochrony, w tym konfigurowanie aktualizacji produktu i ochrony, opisano szczegółowo w sekcji [Program antywirusowy Microsoft Defender funkcji w](configure-notifications-microsoft-defender-antivirus.md) tej bibliotece. [(Powrót do tabeli)](#ref2)

## <a name="in-this-section"></a>W tej sekcji

Temat | Opis
---|---
[Wdrażanie i włączanie Program antywirusowy Microsoft Defender zabezpieczeń](deploy-microsoft-defender-antivirus.md) | Gdy klient jest instalowany jako podstawowa część programu Windows 10 lub Windows 11 i tradycyjne wdrażanie nie ma zastosowania, nadal musisz włączyć klienta w punktach końcowych przy użyciu obiektów Microsoft Endpoint Configuration Manager, Microsoft Intune lub zasady grupy.
[Zarządzanie Program antywirusowy Microsoft Defender i stosowanie planu bazowego](manage-updates-baselines-microsoft-defender-antivirus.md) | Istnieją dwie części aktualizacji Program antywirusowy Microsoft Defender: aktualizowanie klienta na punktach końcowych (aktualizacjach produktów) i aktualizowanie analizy zabezpieczeń (aktualizacji ochrony). Funkcje analizy zabezpieczeń można aktualizować na wiele sposobów, korzystając z Microsoft Endpoint Configuration Manager, zasady grupy, PowerShell i WMI.
[Monitorowanie ochrony sieci i zgłaszanie Program antywirusowy Microsoft Defender informacji](report-monitor-microsoft-defender-antivirus.md) | Za pomocą programu Microsoft Intune, Microsoft Endpoint Configuration Manager, dodatku Update Compliance dla pakietu Microsoft Operations Management Suite lub produktu SIEM innej firmy (korzystając z dzienników zdarzeń programu Windows) możesz monitorować stan ochrony i tworzyć raporty na temat ochrony punktu końcowego.
