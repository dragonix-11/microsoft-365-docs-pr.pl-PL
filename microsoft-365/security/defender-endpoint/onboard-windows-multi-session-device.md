---
title: Dołączanie Windows wielosektapowych w usłudze Azure Virtual Desktop
description: Dowiedz się więcej w tym artykule o dołączaniu do Windows wielosetapowych w usłudze Azure Virtual Desktop
keywords: Azure Virtual Desktop, WVD, microsoft defender, endpoint, onboard
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
ms.openlocfilehash: d97326987af49b9bac44b3578884c72d756d5595
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324063"
---
# <a name="onboard-windows-multi-session-devices-in-azure-virtual-desktop"></a>Dołączanie Windows wielosektapowych w usłudze Azure Virtual Desktop

6 minut na przeczytanie

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Windows z wieloma sesjami w środowisku Azure Virtual Desktop (AVD)

Program Microsoft Defender for Endpoint obsługuje monitorowanie zarówno sesji VDI, jak i sesji pulpitu wirtualnego Azure. W zależności od potrzeb organizacji może być konieczne zaimplementowanie sesji pulpitu wirtualnego VDI lub Azure Virtual Desktop, aby ułatwić pracownikom dostęp do firmowych danych i aplikacji z nieza zarządzaniem urządzeniem, lokalizacją zdalną lub podobnym scenariuszem. Za pomocą programu Microsoft Defender for Endpoint możesz monitorować te maszyny wirtualne pod celu monitorowania ich działań.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Zapoznaj się z zagadnieniami [nietrwałych VDI](/microsoft-365/security/defender-endpoint/configure-endpoints-vdi#onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-1). Chociaż [pulpit wirtualny Azure](/azure/virtual-desktop/overview) nie oferuje opcji nietrwale, zapewnia on sposoby używania złotego Windows, który może być używany do inicjowania obsługi nowych hostów i ponownego używania komputerów. To zwiększa się w środowisku, a tym samym wpływa na to, jakie wpisy są tworzone i utrzymywane w portalu programu Microsoft Defender for Endpoint, co potencjalnie ogranicza widoczność dla analityków zabezpieczeń.

> [!NOTE]
> W zależności od wybranej metody dołączania urządzenia mogą być wyświetlane w portalu programu Microsoft Defender for Endpoint w następujący sposób:
>
> - Jedna pozycja dla każdego pulpitu wirtualnego
> - Wiele wpisów dla każdego pulpitu wirtualnego

Firma Microsoft zaleca dołączanie programu Azure Virtual Desktop jako jednej pozycji na pulpit wirtualny. Dzięki temu środowisko badania w portalu programu Microsoft Defender dla punktu końcowego znajduje się w kontekście jednego urządzenia na podstawie nazwy komputera. Organizacje, które często usuwają i ponownie rozsyłają hosty WVD, zdecydowanie powinny rozważyć zastosowanie tej metody, ponieważ uniemożliwia ona tworzenia wielu obiektów na tym samym komputerze w portalu programu Microsoft Defender for Endpoint. Może to prowadzić do nieporozumień w śledztwie zdarzeń. W przypadku środowisk testowych i nietrwałych możesz wybrać inny wybór.

Firma Microsoft zaleca dodanie skryptu dołączania programu Microsoft Defender for Endpoint do złotego obrazu WVD. Dzięki temu można mieć pewność, że skrypt dołączania zostanie uruchomiony natychmiast przy pierwszym uruchomieniu komputera. Jest on wykonywany jako skrypt uruchamiania przy pierwszym uruchomieniu na wszystkich komputerach WVD, których obsługi administracyjne zostały zasypowane na podstawie złotego obrazu WVD. Jeśli jednak używasz jednego z obrazów galerii bez modyfikacji, umieść skrypt w lokalizacji udostępnionej i wywołaj go przy użyciu zasad grupy lokalnej lub domeny.

> [!NOTE]
> Położenie i konfiguracja skryptu uruchamiania dołączania VDI na złotym obrazie WVD konfiguruje go jako skrypt uruchamiania uruchamiany po uruchomieniu WVD. Nie zaleca **się stosowania** rzeczywistego złotego obrazu WVD. Inną kwestią jest metoda uruchamiania skryptu. Powinna ona być uruchamiana tak wcześnie w procesie uruchamiania/inicjowania obsługi, jak to tylko możliwe, aby skrócić czas między dostępnym na komputerze czasem na odbieranie sesji i dołączanie urządzenia do usługi. Poniżej przedstawiono scenariusze 1 i 2, które należy wziąć pod uwagę.

### <a name="scenarios"></a>Scenariusze

Istnieje kilka sposobów na włodowanie komputera hosta WVD:

- Uruchom skrypt w złotym obrazie (lub z udostępnionej lokalizacji) podczas uruchamiania.
- Użyj narzędzia do zarządzania, aby uruchomić skrypt.
- Dzięki [integracji z programem Microsoft Defender dla chmury](azure-server-integration.md)

#### <a name="scenario-1-using-local-group-policy"></a>*Scenariusz 1. Korzystanie z lokalnych zasad grupy*

Ten scenariusz wymaga umieszczenia skryptu w złotym obrazie i używa lokalnych zasad grupy do wcześniejszego uruchomienia procesu rozruchu.

Skorzystaj z instrukcji podanych w tezie: Wnosz korzystanie z nietrwałych urządzeń infrastruktury pulpitów wirtualnych [(VDI, Non-persistent Virtual Desktop Infrastructure](configure-endpoints-vdi.md)).

Postępuj zgodnie z instrukcjami dotyczącymi pojedynczej pozycji dla każdego urządzenia.

#### <a name="scenario-2-using-domain-group-policy"></a>*Scenariusz 2. Korzystanie z zasad grupy domeny*

W tym scenariuszu jest używany centralnie zlokalizowany skrypt i jest uruchamiany przy użyciu zasad grupy opartych na domenie. Możesz również umieścić skrypt w złotym obrazie i uruchomić go w taki sam sposób.

##### <a name="download-the-windowsdefenderatponboardingpackagezip-file-from-the-windows-365-defender-portal"></a>Pobierz plik WindowsDefenderATPOnboardingPackage.zip z portalu usługi Windows 365 Defender

1. Otwieranie pliku konfiguracji VDI .zip (WindowsDefenderATPOnboardingPackage.zip)

    1. W okienku Microsoft 365 Defender nawigacji portalu wybierz pozycję **Dołączanie Ustawienia** \> **punktów** \> **końcowych** (w obszarze **Zarządzanie urządzeniami**).
    1. Wybierz Windows 10 lub Windows 11 jako system operacyjny.
    1. W polu **Metoda wdrażania** wybierz pozycję Skrypty wdrażania VDI dla nietrwałych punktów końcowych.
    1. Kliknij **pozycję Pobierz pakiet** i zapisz .zip pliku.

2. Wyodrębnianie zawartości pliku .zip do udostępnionej lokalizacji tylko do odczytu, do której dostęp jest możliwy na urządzeniu. Powinien mieć folder o nazwie **OptionalParamsPolicy** i pliki **WindowsDefenderATPOnboardingScript.cmd** **iOnboard-NonPersistentMachine.ps1**.

##### <a name="use-group-policy-management-console-to-run-the-script-when-the-virtual-machine-starts"></a>Użyj zasady grupy zarządzania, aby uruchomić skrypt podczas uruchamiania maszyny wirtualnej

1. Otwórz konsolę zasady grupy zarządzania (GPMC), kliknij prawym przyciskiem myszy obiekt zasady grupy (GPO), który chcesz skonfigurować, a następnie kliknij polecenie **Edytuj**.

2. W oknie zasady grupy zarządzaniem przejdź do  \> konfiguracja komputera **Preferencje** \> **Ustawienia panelu sterowania**.

3. Kliknij prawym przyciskiem myszy **pozycję Zaplanowane zadania**, kliknij pozycję **Nowe**, a następnie **kliknij pozycję Zadanie** natychmiastowe (co najmniej Windows 7).

4. W oknie Zadanie, które zostanie otwarte, przejdź do **karty** Ogólne. W **obszarze Opcje zabezpieczeń** kliknij **pozycję Zmień użytkownika lub grupę i** wpisz SYSTEM. Kliknij **pozycję Sprawdź nazwy** , a następnie kliknij przycisk OK. Nt AUTHORITY\SYSTEM pojawi się jako konto użytkownika, jako które będzie działać zadanie.

5. Zaznacz **pole wyboru Uruchom** niezależnie od tego, czy użytkownik jest zalogowany, i zaznacz **pole wyboru Uruchom z najwyższymi uprawnieniami** .

6. Przejdź do karty **Akcje** i kliknij pozycję **Nowy**. Upewnij się **, że w** polu Akcja jest wybrana opcja Uruchom program. Wprowadź następujące informacje:

   `Action = "Start a program"`

   `Program/Script = C:\WINDOWS\system32\WindowsPowerShell\v1.0\powershell.exe`

   `Add Arguments (optional) = -ExecutionPolicy Bypass -command "& \\Path\To\Onboard-NonPersistentMachine.ps1"`

   Następnie wybierz **przycisk OK** i zamknij wszystkie otwarte okna GPMC.

#### <a name="scenario-3-onboarding-using-management-tools"></a>*Scenariusz 3. Dołączanie przy użyciu narzędzi do zarządzania*

Jeśli planujesz zarządzać swoimi komputerami za pomocą narzędzia do zarządzania, możesz używać urządzeń Microsoft Endpoint Configuration Manager.

Aby uzyskać więcej informacji, [zobacz Windows urządzeniach przy użyciu Menedżer konfiguracji](configure-endpoints-sccm.md).

> [!WARNING]
> Jeśli planujesz stosowanie odwoływać się do reguł zmniejszania powierzchni [ataków, zwróć](attack-surface-reduction-rules-reference.md) uwagę, że nie należy używać reguły "Blokuj tworzenie procesów pochodzących z poleceń [PSExec i WMI](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands)", ponieważ ta reguła jest niezgodna z zarządzaniem za pośrednictwem programu Microsoft Endpoint Configuration Manager. Reguła blokuje polecenia WMI, które Menedżer konfiguracji do poprawnego działania klienta.

> [!TIP]
> Po włoceniu urządzenia możesz uruchomić test wykrywania w celu sprawdzenia, czy urządzenie jest prawidłowo podłączone do usługi. Aby uzyskać więcej informacji, zobacz Uruchamianie testu wykrywania na nowo włodarzony [program Microsoft Defender dla urządzenia końcowego](run-detection-test.md).

#### <a name="tagging-your-machines-when-building-your-golden-image"></a>Otagowanie komputerów podczas tworzenia złotego obrazu

W ramach dołączania warto rozważyć ustawienie tagu maszynowego w celu najrównszego odróżniania komputerów WVD w Centrum zabezpieczeń Microsoft. Aby uzyskać więcej informacji, [zobacz Dodawanie tagów urządzeń przez ustawienie wartości klucza rejestru](machine-tags.md#add-device-tags-by-setting-a-registry-key-value).

#### <a name="other-recommended-configuration-settings"></a>Inne zalecane ustawienia konfiguracji

Podczas tworzenia złotego obrazu możesz chcieć także skonfigurować początkowe ustawienia ochrony. Aby uzyskać więcej informacji, zobacz [Inne zalecane ustawienia konfiguracji](configure-endpoints-gp.md#other-recommended-configuration-settings).

Ponadto, jeśli korzystasz z profilów użytkowników usługi FSlogix, zalecamy wykluczenie z zawsze najbłędszej ochrony następujących plików:

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

**Wykluczanie procesów:**

`%ProgramFiles%\FSLogix\Apps\frxccd.exe`

`%ProgramFiles%\FSLogix\Apps\frxccds.exe`

`%ProgramFiles%\FSLogix\Apps\frxsvc.exe`

#### <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

Uwaga: Podczas korzystania z wielu sesji programu Windows Enterprise, w zależności od Twoich wymagań, możesz wybrać, czy wszyscy użytkownicy mają licencję programu Microsoft Defender dla punktu końcowego (na użytkownika), Windows Enterprise E5, Microsoft 365 Security lub Microsoft 365 E5 albo licencję maszyny wirtualnej za pośrednictwem programu Microsoft Defender for Cloud.
Wymagania licencyjne dotyczące programu Microsoft Defender dla punktu końcowego można znaleźć w te sposób: [Wymagania dotyczące licencjonowania](minimum-requirements.md#licensing-requirements).

### <a name="known-issues-and-limitations"></a>Znane problemy i ograniczenia

Filtrowanie Microsoft Edge jest obsługiwane tylko w przypadku Windows 10 w wielu sesjach.

#### <a name="related-links"></a>Linki pokrewne

[Dodawanie wykluczeń dla usługi Defender dla punktu końcowego za pośrednictwem programu PowerShell](/azure/architecture/example-scenario/wvd/windows-virtual-desktop-fslogix#add-exclusions-for-microsoft-defender-by-using-powershell)
