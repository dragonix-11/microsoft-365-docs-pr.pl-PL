---
title: Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI)
description: Wdróż pakiet konfiguracji na urządzeniu infrastruktury pulpitu wirtualnego (VDI), aby był dołączany do usługi Ochrona punktu końcowego w usłudze Microsoft Defender.
keywords: konfigurowanie urządzenia infrastruktury pulpitu wirtualnego (VDI), vdi, zarządzania urządzeniami, konfigurowania Ochrona punktu końcowego w usłudze Microsoft Defender, punktów końcowych
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.date: 04/15/2022
ms.technology: mde
ms.openlocfilehash: 78d22772ccc9713b968347de5dee4c3a9699fe26
ms.sourcegitcommit: dba1a846ae78ea14240d28efa8d4934fe303f308
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2022
ms.locfileid: "64891871"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-in-microsoft-365-defender"></a>Dołączanie nietrwałych urządzeń infrastruktury pulpitu wirtualnego w Microsoft 365 Defender

Infrastruktura pulpitu wirtualnego (VDI) to koncepcja infrastruktury IT, która umożliwia użytkownikom końcowym dostęp do wystąpień pulpitów wirtualnych przedsiębiorstwa z niemal każdego urządzenia (takiego jak komputer osobisty, smartfon lub tablet), eliminując konieczność zapewnienia użytkownikom maszyn fizycznych przez organizację. Korzystanie z urządzeń VDI zmniejsza koszty, ponieważ działy IT nie są już odpowiedzialne za zarządzanie, naprawianie i zastępowanie fizycznych punktów końcowych. Autoryzowani użytkownicy mogą uzyskiwać dostęp do tych samych firmowych serwerów, plików, aplikacji i usług z dowolnego zatwierdzonego urządzenia za pośrednictwem bezpiecznego klienta lub przeglądarki klasycznej.

Podobnie jak w przypadku każdego innego systemu w środowisku IT, te również powinny mieć rozwiązanie do wykrywania i reagowania na punkty końcowe (EDR) i oprogramowanie antywirusowe w celu ochrony przed zaawansowanymi zagrożeniami i atakami.


[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Urządzenia infrastruktury pulpitu wirtualnego (VDI)
- Windows 10, Windows 11, Windows Server 2019, Windows Server 2022, Windows Server 2008R2/2012R2/2016

> Chcesz poznać usługę Defender for Endpoint? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configvdi-abovefoldlink)

 > [!NOTE]
  > **Trwałe interfejsy** -  VDI [Dołączanie trwałej maszyny VDI](configure-endpoints.md) do Ochrona punktu końcowego w usłudze Microsoft Defender jest obsługiwane w taki sam sposób, jak w przypadku dołączania maszyny fizycznej, takiej jak komputer stacjonarny lub laptop. Zasady grupy, Microsoft Endpoint Manager i inne metody mogą służyć do dołączania maszyny trwałej. W portalu Microsoft 365 Defender (https://security.microsoft.com) w obszarze dołączania wybierz preferowaną metodę dołączania i postępuj zgodnie z instrukcjami dla tego typu. 

## <a name="onboarding-non-persistent-virtual-desktop-infrastructure-vdi-devices"></a>Dołączanie nietrwałych urządzeń infrastruktury pulpitu wirtualnego (VDI)

Usługa Defender for Endpoint obsługuje dołączanie nietrwałej sesji VDI.

Podczas dołączania wystąpień VDI mogą wystąpić problemy. Poniżej przedstawiono typowe wyzwania dla tego scenariusza:

- Natychmiastowe wczesne dołączanie krótkotrwałej sesji, która musi zostać dołączona do usługi Defender for Endpoint przed rzeczywistą aprowizowaniem.
- Nazwa urządzenia jest zwykle ponownie używana dla nowych sesji.

W środowisku VDI wystąpienia VDI mogą mieć krótki okres życia. Urządzenia VDI mogą być wyświetlane w portalu usługi Defender for Endpoint jako jedno z następujących:


- Wpis pojedynczego portalu dla każdego wystąpienia VDI. Jeśli wystąpienie VDI zostało już dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender i w pewnym momencie usunięte, a następnie ponownie utworzone z tą samą nazwą hosta, nowy obiekt reprezentujący to wystąpienie VDI NIE zostanie utworzony w portalu. 


  > [!NOTE]
  > W takim przypadku podczas tworzenia sesji należy skonfigurować *tę samą* nazwę urządzenia, na przykład przy użyciu nienadzorowanego pliku odpowiedzi.

- Wiele wpisów dla każdego urządzenia — po jednym dla każdego wystąpienia VDI.

Poniższe kroki przeprowadzą Cię przez dołączanie urządzeń VDI i wyróżnią kroki dla pojedynczych i wielu wpisów.

> [!WARNING]
> W środowiskach, w których konfiguracje zasobów są niskie, procedura rozruchu interfejsu VDI może spowolnić dołączanie czujnika usługi Defender for Endpoint.

### <a name="for-windows-10-or-windows-11-or-windows-server-2012-r2-and-later"></a>W przypadku Windows 10 lub Windows 11 lub Windows Server 2012 R2 i nowszych

> [!NOTE]
> Windows Server 2016 i Windows Server 2012 R2 należy przygotować, stosując najpierw pakiet instalacyjny, korzystając z instrukcji zawartych w temacie [Dołączanie serwerów Windows](/microsoft-365/security/defender-endpoint/configure-server-endpoints#windows-server-2012-r2-and-windows-server-2016), aby ta funkcja działała.

1.  Otwórz pakiet konfiguracji interfejsu VDI .zip plik (*WindowsDefenderATPOnboardingPackage.zip*), który został pobrany z kreatora dołączania usługi. Pakiet można również pobrać z <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>:

    1. W okienku nawigacji wybierz pozycję **Ustawienia** >  **EndpointsDevice** >  **managementOnboarding** > .

    1. Wybierz system operacyjny.

    1.  W polu **Metoda wdrażania** wybierz pozycję **VDI onboarding scripts for non-persistent endpoints (Skrypty dołączania interfejsu VDI dla nietrwałych punktów końcowych**).

    1. Kliknij **pozycję Pobierz pakiet** i zapisz plik .zip.

2. Skopiuj pliki z folderu WindowsDefenderATPOnboardingPackage wyodrębnionego z pliku .zip do obrazu golden/master w ścieżce `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup`.
    1. Jeśli implementujesz wiele wpisów dla każdego urządzenia — po jednym dla każdej sesji, skopiuj plik WindowsDefenderATPOnboardingScript.cmd.
    2. Jeśli implementujesz pojedynczy wpis dla każdego urządzenia, skopiuj pliki Onboard-NonPersistentMachine.ps1 i WindowsDefenderATPOnboardingScript.cmd.

    > [!NOTE]
    > Jeśli nie widzisz folderu `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` , może on być ukryty. Musisz wybrać opcję **Pokaż ukryte pliki i foldery** z Eksplorator plików.

3. Otwórz okno Edytor lokalnych zasady grupy i przejdź do pozycji **Konfiguracja** \> komputera **Windows Ustawienia** \> **Uruchamianie skryptów**\>.

   > [!NOTE]
   > Zasady grupy domeny mogą być również używane do dołączania nietrwałych urządzeń VDI.

4. W zależności od metody, którą chcesz zaimplementować, wykonaj odpowiednie kroki:
    - Dla pojedynczego wpisu dla każdego urządzenia:

         Wybierz kartę **Skrypty programu PowerShell**, a następnie kliknij pozycję **Dodaj** (Windows Eksplorator otworzy się bezpośrednio w ścieżce, w której wcześniej skopiowano skrypt dołączania). Przejdź do dołączania skryptu `Onboard-NonPersistentMachine.ps1`programu PowerShell. Nie trzeba określać innego pliku, ponieważ zostanie on wyzwolony automatycznie.

    - W przypadku wielu wpisów dla każdego urządzenia:

         Wybierz kartę **Skrypty**, a następnie kliknij pozycję **Dodaj** (Windows Eksplorator otworzy się bezpośrednio w ścieżce, w której wcześniej skopiowano skrypt dołączania). Przejdź do skryptu `WindowsDefenderATPOnboardingScript.cmd`powłoki bash dołączania.

5. Przetestuj rozwiązanie:
   1. Utwórz pulę przy użyciu jednego urządzenia.
   2. Zaloguj się na urządzeniu.
   3. Wyloguj się z urządzenia.
   4. Zaloguj się na urządzeniu przy użyciu innego użytkownika.
   5. W zależności od metody, którą chcesz zaimplementować, wykonaj odpowiednie kroki:
      - Dla pojedynczego wpisu dla każdego urządzenia: sprawdź tylko jeden wpis w portalu Microsoft 365 Defender.
      - Dla wielu wpisów dla każdego urządzenia: sprawdź wiele wpisów w portalu Microsoft 365 Defender.

6. Kliknij **listę Urządzenia** w okienku Nawigacji.

7. Użyj funkcji wyszukiwania, wprowadzając nazwę urządzenia i wybierając pozycję **Urządzenie** jako typ wyszukiwania.

## <a name="for-downlevel-skus-windows-server-2008-r2"></a>W przypadku jednostek SKU niskiego poziomu (Windows Server 2008 R2)

> [!NOTE]
> Te instrukcje dotyczące innych wersji serwera Windows mają zastosowanie również w przypadku uruchamiania poprzednich Ochrona punktu końcowego w usłudze Microsoft Defender dla Windows Server 2016 i Windows Server 2012 R2, które wymagają mma. Instrukcje migracji do nowego ujednoliconego rozwiązania znajdują się [w scenariuszach migracji serwera w Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/server-migration).

> [!NOTE]
> Poniższy rejestr ma zastosowanie tylko wtedy, gdy celem jest osiągnięcie "pojedynczego wpisu dla każdego urządzenia".

1. Ustaw wartość rejestru na:

    ```console
   [HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection\DeviceTagging]
    "VDI"="NonPersistent"
    ```

    lub przy użyciu wiersza polecenia:

    ```console
    reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection\DeviceTagging" /v VDI /t REG_SZ /d "NonPersistent" /f
    ```

2. Postępuj zgodnie z [procesem dołączania serwera](configure-server-endpoints.md). 

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>Aktualizowanie nietrwałych obrazów infrastruktury pulpitu wirtualnego (VDI)

Dzięki możliwości łatwego wdrażania aktualizacji na maszynach wirtualnych działających w interfejsach VDI skróciliśmy ten przewodnik, aby skupić się na tym, jak można szybko i łatwo uzyskiwać aktualizacje na maszynach. Nie trzeba już okresowo tworzyć i uszczelniać złotych obrazów, ponieważ aktualizacje są rozszerzane na ich bity składników na serwerze hosta, a następnie pobierane bezpośrednio na maszynę wirtualną po jej włączeniu.

Aby uzyskać więcej informacji, postępuj zgodnie ze wskazówkami w [przewodniku wdrażania dotyczącym Program antywirusowy Microsoft Defender w środowisku infrastruktury pulpitu wirtualnego (VDI).](/microsoft-365/security/defender-endpoint/deployment-vdi-microsoft-defender-antivirus)


## <a name="related-topics"></a>Tematy pokrewne
- [Dołącz urządzenia z systemem Windows przy użyciu zasad grupy](configure-endpoints-gp.md)
- [Dołącz urządzenia z systemem Windows przy użyciu menedżera konfiguracji punktu końcowego Microsoft](configure-endpoints-sccm.md)
- [Dołącz urządzenia z systemem Windows przy użyciu narzędzi do zarządzania urządzeniami przenośnymi](configure-endpoints-mdm.md)
- [Dołącz urządzenia z systemem Windows przy użyciu skryptu lokalnego](configure-endpoints-script.md)
- [Rozwiązywanie problemów z dołączaniem Ochrona punktu końcowego w usłudze Microsoft Defender](troubleshoot-onboarding.md)
