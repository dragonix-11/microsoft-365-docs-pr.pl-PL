---
title: Dołączanie urządzeń z systemem Windows w usłudze Azure Virtual Desktop
description: Dowiedz się, jak dołączać urządzenia z systemem Windows do usługi Defender for Endpoint w usłudze Azure Virtual Desktop
keywords: Azure Virtual Desktop, AVD, microsoft defender, endpoint, onboard
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: dansimp
ms.author: dansimp
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 91a9cc3e7a9fdc38a05deaf04f2124819f41d1ae
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607438"
---
# <a name="onboard-windows-devices-in-azure-virtual-desktop"></a>Dołączanie urządzeń z systemem Windows w usłudze Azure Virtual Desktop

6 minut do odczytu

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Wielosesyjna sesja systemu Windows uruchomiona w usłudze Azure Virtual Desktop (AVD)
- [Windows 10 Enterprise wielu sesjach](/microsoft-365/security/defender-endpoint/azure-server-integration)

Ochrona punktu końcowego w usłudze Microsoft Defender obsługuje monitorowanie sesji VDI i Azure Virtual Desktop. W zależności od potrzeb organizacji może być konieczne zaimplementowanie sesji VDI lub Azure Virtual Desktop, aby ułatwić pracownikom dostęp do firmowych danych i aplikacji z niezarządzanego urządzenia, lokalizacji zdalnej lub podobnego scenariusza. Za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender można monitorować te maszyny wirtualne pod kątem nietypowych działań.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Zapoznaj się z [zagadnieniami dotyczącymi nietrwałej interfejsu VDI](/microsoft-365/security/defender-endpoint/configure-endpoints-vdi#onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-1). Usługa [Azure Virtual Desktop](/azure/virtual-desktop/overview) nie zapewnia opcji braku trwałości, ale zapewnia sposoby używania złotego obrazu systemu Windows, który może służyć do aprowizacji nowych hostów i ponownego wdrażania maszyn. Zwiększa to zmienność w środowisku, a tym samym wpływa na to, jakie wpisy są tworzone i utrzymywane w portalu Ochrona punktu końcowego w usłudze Microsoft Defender, co może zmniejszyć widoczność analityków zabezpieczeń.

> [!NOTE]
> W zależności od wybranej metody dołączania urządzenia mogą być wyświetlane w portalu Ochrona punktu końcowego w usłudze Microsoft Defender jako:
>
> - Pojedynczy wpis dla każdego pulpitu wirtualnego
> - Wiele wpisów dla każdego pulpitu wirtualnego

Firma Microsoft zaleca dołączenie usługi Azure Virtual Desktop jako pojedynczego wpisu na pulpit wirtualny. Dzięki temu środowisko badania w portalu Ochrona punktu końcowego w usłudze Microsoft Defender znajduje się w kontekście jednego urządzenia na podstawie nazwy maszyny. Organizacje, które często usuwają i ponownie wdrażają hosty AVD, powinny zdecydowanie rozważyć użycie tej metody, ponieważ uniemożliwia ona tworzenie wielu obiektów dla tej samej maszyny w portalu Ochrona punktu końcowego w usłudze Microsoft Defender. Może to prowadzić do nieporozumień podczas badania zdarzeń. W przypadku środowisk testowych lub nietrwałych możesz zdecydować się na wybór w inny sposób.

Firma Microsoft zaleca dodanie skryptu dołączania Ochrona punktu końcowego w usłudze Microsoft Defender do złotego obrazu AVD. Dzięki temu możesz mieć pewność, że ten skrypt dołączania jest uruchamiany natychmiast przy pierwszym rozruchu. Jest on wykonywany jako skrypt uruchamiania przy pierwszym rozruchu na wszystkich maszynach AVD aprowizowanych na podstawie złotego obrazu AVD. Jeśli jednak używasz jednego z obrazów galerii bez modyfikacji, umieść skrypt w lokalizacji udostępnionej i wywołaj go z poziomu zasad grupy lokalnej lub domeny.

> [!NOTE]
> Umieszczenie i konfiguracja skryptu uruchamiania dołączania interfejsu VDI na złotym obrazie AVD konfiguruje go jako skrypt startowy uruchamiany po uruchomieniu avd. Nie **zaleca się** dołączania rzeczywistego złotego obrazu AVD. Inną kwestią jest metoda używana do uruchamiania skryptu. Powinien być uruchamiany tak wcześnie, jak to możliwe w procesie uruchamiania/aprowizacji, aby skrócić czas między maszyną dostępną do odbierania sesji a dołączaniem urządzenia do usługi. W poniższych scenariuszach 1 i 2 należy wziąć to pod uwagę.

### <a name="scenarios"></a>Scenariuszy

Istnieje kilka sposobów dołączania maszyny hosta AVD:

- Uruchom skrypt na złotym obrazie (lub z lokalizacji udostępnionej) podczas uruchamiania.
- Użyj narzędzia do zarządzania, aby uruchomić skrypt.
- [Integracja z usługą Microsoft Defender for Cloud](azure-server-integration.md)

#### <a name="scenario-1-using-local-group-policy"></a>*Scenariusz 1. Korzystanie z lokalnych zasad grupy*

Ten scenariusz wymaga umieszczenia skryptu w złotym obrazie i używa lokalnych zasad grupy do uruchomienia na wczesnym etapie procesu rozruchu.

Skorzystaj z instrukcji zawartych w temacie [Dołączanie nietrwałych urządzeń infrastruktury pulpitu wirtualnego (VDI](configure-endpoints-vdi.md)).

Postępuj zgodnie z instrukcjami dotyczącymi pojedynczego wpisu dla każdego urządzenia.

#### <a name="scenario-2-using-domain-group-policy"></a>*Scenariusz 2. Korzystanie z zasad grupy domen*

W tym scenariuszu używany jest skrypt centralnie zlokalizowany i uruchamiany przy użyciu zasad grupy opartej na domenie. Skrypt można również umieścić na złotym obrazie i uruchomić go w taki sam sposób.

##### <a name="download-the-windowsdefenderatponboardingpackagezip-file-from-the-windows-365-defender-portal"></a>Pobierz plik WindowsDefenderATPOnboardingPackage.zip z portalu usługi Windows 365 Defender

1. Otwórz plik .zip pakietu konfiguracji interfejsu VDI (WindowsDefenderATPOnboardingPackage.zip)

    1. W okienku nawigacji portalu Microsoft 365 Defender wybierz pozycję **Ustawienia** \> **Dołączanie punktów końcowych** \> (w obszarze **Zarządzanie urządzeniami**).
    1. Wybierz Windows 10 lub Windows 11 jako system operacyjny.
    1. W polu **Metoda wdrażania** wybierz pozycję VDI onboarding scripts for non-persistent endpoints (Skrypty dołączania interfejsu VDI dla nietrwałych punktów końcowych).
    1. Kliknij **pozycję Pobierz pakiet** i zapisz plik .zip.

2. Wyodrębnij zawartość pliku .zip do udostępnionej lokalizacji tylko do odczytu, do których może uzyskiwać dostęp urządzenie. Powinien istnieć folder o nazwie **OptionalParamsPolicy** i pliki **WindowsDefenderATPOnboardingScript.cmd** i **Onboard-NonPersistentMachine.ps1**.

##### <a name="use-group-policy-management-console-to-run-the-script-when-the-virtual-machine-starts"></a>Użyj konsoli zarządzania zasady grupy, aby uruchomić skrypt po uruchomieniu maszyny wirtualnej

1. Otwórz konsolę zarządzania zasady grupy (GPMC), kliknij prawym przyciskiem myszy obiekt zasady grupy , który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

2. W edytorze zarządzania zasady grupy przejdź do pozycji **Ustawienia panelu** sterowania **preferencji** \> **konfiguracji** \> komputera.

3. Kliknij prawym przyciskiem myszy **zaplanowane zadania**, kliknij pozycję **Nowe**, a następnie kliknij pozycję **Zadanie natychmiastowe** (co najmniej windows 7).

4. W wyświetlonym oknie Zadanie przejdź do karty **Ogólne** . W obszarze **Opcje zabezpieczeń** kliknij pozycję **Zmień użytkownika lub grupę** i wpisz SYSTEM. Kliknij **pozycję Sprawdź nazwy,** a następnie kliknij przycisk OK. NT AUTHORITY\SYSTEM jest wyświetlany jako konto użytkownika, które będzie uruchamiane jako zadanie.

5. Wybierz pozycję **Uruchom, czy użytkownik jest zalogowany, czy nie** , i zaznacz pole wyboru **Uruchom z najwyższymi uprawnieniami** .

6. Przejdź do karty **Akcje** i kliknij pozycję **Nowy**. Upewnij się, że w polu **Akcja wybrano opcję Uruchom program** . Wprowadź następujące informacje:

   `Action = "Start a program"`

   `Program/Script = C:\WINDOWS\system32\WindowsPowerShell\v1.0\powershell.exe`

   `Add Arguments (optional) = -ExecutionPolicy Bypass -command "& \\Path\To\Onboard-NonPersistentMachine.ps1"`

   Następnie wybierz przycisk **OK** i zamknij wszystkie otwarte okna kontrolera GPMC.

#### <a name="scenario-3-onboarding-using-management-tools"></a>*Scenariusz 3. Dołączanie przy użyciu narzędzi do zarządzania*

Jeśli planujesz zarządzanie maszynami przy użyciu narzędzia do zarządzania, możesz dołączyć urządzenia za pomocą programu Microsoft Endpoint Configuration Manager.

Aby uzyskać więcej informacji, zobacz [Dołączanie urządzeń z systemem Windows przy użyciu Configuration Manager](configure-endpoints-sccm.md).

> [!WARNING]
> Jeśli planujesz używać [odwołania do reguł zmniejszania obszaru ataków](attack-surface-reduction-rules-reference.md), pamiętaj, że reguła "[Blokuj tworzenie procesów pochodzących z poleceń PSExec i WMI](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands)" nie powinna być używana, ponieważ ta reguła jest niezgodna z zarządzaniem za pośrednictwem Configuration Manager punktu końcowego firmy Microsoft. Reguła blokuje polecenia usługi WMI używane przez klienta Configuration Manager do poprawnego działania.

> [!TIP]
> Po dołączeniu urządzenia można uruchomić test wykrywania, aby sprawdzić, czy urządzenie jest prawidłowo dołączone do usługi. Aby uzyskać więcej informacji, zobacz [Uruchamianie testu wykrywania na nowo dołączonym urządzeniu Ochrona punktu końcowego w usłudze Microsoft Defender](run-detection-test.md).

#### <a name="tagging-your-machines-when-building-your-golden-image"></a>Tagowanie maszyn podczas tworzenia złotego obrazu

W ramach dołączania warto rozważyć ustawienie tagu maszyny, aby łatwiej rozróżniać maszyny AVD w usłudze Microsoft Security Center. Aby uzyskać więcej informacji, zobacz [Dodawanie tagów urządzeń przez ustawienie wartości klucza rejestru](machine-tags.md#add-device-tags-by-setting-a-registry-key-value).

#### <a name="other-recommended-configuration-settings"></a>Inne zalecane ustawienia konfiguracji

Podczas tworzenia złotego obrazu możesz również skonfigurować początkowe ustawienia ochrony. Aby uzyskać więcej informacji, zobacz [Inne zalecane ustawienia konfiguracji](configure-endpoints-gp.md#other-recommended-configuration-settings).

Ponadto jeśli używasz profilów użytkowników FSlogix, zalecamy wykluczenie następujących plików z zawsze włączonej ochrony:

**Wyklucz pliki:**

`%ProgramFiles%\FSLogix\Apps\frxdrv.sys`

`%ProgramFiles%\FSLogix\Apps\frxdrvvt.sys`

`%ProgramFiles%\FSLogix\Apps\frxccd.sys`

`%TEMP%\*.VHD`

`%TEMP%\*.VHDX`

`%Windir%\TEMP\*.VHD`

`%Windir%\TEMP\*.VHDX`

`\\storageaccount.file.core.windows.net\share\*\*.VHD`

`\\storageaccount.file.core.windows.net\share\*\*.VHDX`

**Wyklucz procesy:**

`%ProgramFiles%\FSLogix\Apps\frxccd.exe`

`%ProgramFiles%\FSLogix\Apps\frxccds.exe`

`%ProgramFiles%\FSLogix\Apps\frxsvc.exe`

#### <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

Uwaga dotycząca licencjonowania: w przypadku korzystania z wielu sesji systemu Windows Enterprise, w zależności od wymagań, możesz wybrać licencję wszystkich użytkowników za pośrednictwem Ochrona punktu końcowego w usłudze Microsoft Defender (na użytkownika), Windows Enterprise E5, Microsoft 365 Security lub Microsoft 365 E5 lub mieć maszynę wirtualną licencjonowaną za pośrednictwem usługi Microsoft Defender dla Chmurze.
Wymagania licencyjne dotyczące Ochrona punktu końcowego w usłudze Microsoft Defender można znaleźć na stronie: [Wymagania dotyczące licencjonowania](minimum-requirements.md#licensing-requirements).

### <a name="known-issues-and-limitations"></a>Znane problemy i ograniczenia

Filtrowanie sieci Web w Windows 10 wielu sesjach jest obsługiwane tylko w przeglądarce Microsoft Edge.

#### <a name="related-links"></a>Linki pokrewne

[Dodawanie wykluczeń dla usługi Defender dla punktu końcowego za pośrednictwem programu PowerShell](/azure/architecture/example-scenario/wvd/windows-virtual-desktop-fslogix#add-exclusions-for-microsoft-defender-by-using-powershell)
