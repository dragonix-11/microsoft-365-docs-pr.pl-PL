---
title: Program antywirusowy Microsoft Defender na Windows Server
description: Dowiedz się, jak włączyć i skonfigurować Program antywirusowy Microsoft Defender w Windows Server 2016, Windows Server 2019 i Windows Server 2022.
keywords: windows defender, server, scep, ochrona punktu końcowego centrum systemu, serwer 2016, bieżąca gałąź, serwer 2012
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.reviewer: pahuijbr
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 04/01/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 412033e274cce22b9350292c612b91ef6e34e209
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634850"
---
# <a name="microsoft-defender-antivirus-on-windows-server"></a>Program antywirusowy Microsoft Defender na Windows Server

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

Program antywirusowy Microsoft Defender jest dostępna w następujących wersjach/wersjach programu Windows Server:

- Windows Server 2022
- Windows Server 2019
- Windows Server w wersji 1803 lub nowszej
- System Windows Server 2016
- Windows Server 2012 R2 (wymaga Ochrona punktu końcowego w usłudze Microsoft Defender)

## <a name="setting-up-microsoft-defender-antivirus-on-windows-server"></a>Konfigurowanie Program antywirusowy Microsoft Defender na Windows Server

Proces konfigurowania i uruchamiania programu Program antywirusowy Microsoft Defender w Windows Server obejmuje następujące czynności:

1. [Włącz interfejs](#enable-the-user-interface-on-windows-server).
2. [Instalowanie Program antywirusowy Microsoft Defender](#install-microsoft-defender-antivirus-on-windows-server).
3. [Sprawdź Program antywirusowy Microsoft Defender czy jest uruchomiony](#verify-microsoft-defender-antivirus-is-running).
4. [Zaktualizuj zabezpieczenia przed złośliwym kodem](#update-antimalware-security-intelligence).
5. (W razie potrzeby) [Prześlij próbki](#submit-samples).
6. (W razie potrzeby) [Konfigurowanie wykluczeń automatycznych](#configure-automatic-exclusions).
7. (Tylko w razie potrzeby) Ustaw [Windows serwer na tryb pasywny](#passive-mode-and-windows-server).

## <a name="enable-the-user-interface-on-windows-server"></a>Włączanie interfejsu użytkownika na Windows Server

> [!IMPORTANT]
> Jeśli korzystasz z pakietu Windows Server 2012 R2, zobacz [Opcje instalowania Ochrona punktu końcowego w usłudze Microsoft Defender](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

Domyślnie na Program antywirusowy Microsoft Defender i działa on na Windows Server. Czasami interfejs użytkownika jest domyślnie instalowany. Interfejs użytkownika nie jest wymagany. do zarządzania plikami możesz używać programu PowerShell, zasady grupy lub innych Program antywirusowy Microsoft Defender. Jednak wiele organizacji woli używać graficznego interfejsu użytkownika na Program antywirusowy Microsoft Defender. Aby zainstalować interfejs użytkownika przy użyciu jednej z procedur z poniższej tabeli:

| Procedura | Co należy zrobić |
|:---|:---|
| Włączanie graficznego interfejsu użytkownika przy użyciu Kreatora dodawania ról i funkcji | 1. Zobacz Instalowanie [ról, usług ról](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) i funkcji przy użyciu Kreatora dodawania ról i funkcji, a następnie korzystanie z Kreatora dodawania **ról i funkcji**. <br/><br/>2. Po otworzyeniu kroku **Funkcje** kreatora w obszarze Funkcje Windows Defender wybierz graficznego interfejsu **użytkownika, aby** **Windows Defender** graficzne. |
| Włączanie graficznego interfejsu użytkownika przy użyciu programu PowerShell | 1. Na Windows otwórz program Windows PowerShell jako administrator. <br/><br/>2. Uruchom następujące polecenie cmdlet programu PowerShell: `Install-WindowsFeature -Name Windows-Defender-GUI` |

## <a name="install-microsoft-defender-antivirus-on-windows-server"></a>Instalowanie Program antywirusowy Microsoft Defender na Windows Server

Jeśli chcesz zainstalować lub ponownie zainstalować pakiet Program antywirusowy Microsoft Defender na Windows Server, użyj jednej z procedur z poniższej tabeli:

| Procedura | Co należy zrobić |
|:---|:---|
| Instalowanie nowych użytkowników za pomocą Kreatora dodawania ról i funkcji Program antywirusowy Microsoft Defender | 1. Zobacz Instalowanie [lub odinstalowywanie ról, usług ról](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) lub funkcji i korzystanie z Kreatora dodawania **ról i funkcji**. <br/><br/>2. Po dojechu do kroku **Funkcje** kreatora wybierz Program antywirusowy Microsoft Defender kreatora. Wybierz też opcję **graficznego interfejsu użytkownika Windows Defender** interfejsu użytkownika. |
| Instalowanie programu PowerShell Program antywirusowy Microsoft Defender | 1. Na Windows otwórz program Windows PowerShell jako administrator. <br/><br/>2. Uruchom następujące polecenie cmdlet programu PowerShell: `Install-WindowsFeature -Name Windows-Defender` |

> [!NOTE]
> Komunikaty o zdarzeniach aparatu ochrony przed złośliwym oprogramowaniem dołączonego Program antywirusowy Microsoft Defender można znaleźć w Program antywirusowy Microsoft Defender [Zdarzenia](troubleshoot-microsoft-defender-antivirus.md).

## <a name="verify-microsoft-defender-antivirus-is-running"></a>Sprawdzanie Program antywirusowy Microsoft Defender czy jest uruchomiony

Po zainstalowaniu (lub ponownym zainstalowaniu) programu Program antywirusowy Microsoft Defender następnym krokiem jest sprawdzenie, czy program jest uruchomiony. Użyj poleceń cmdlet programu PowerShell z poniższej tabeli:

| Procedura | Polecenie cmdlet programu PowerShell |
|:---|:---|
| Sprawdzanie, czy Program antywirusowy Microsoft Defender działa | `Get-Service -Name windefend` |
| Sprawdzanie, czy jest włączona ochrona zapór | `Get-Service -Name mpssvc` |

Jako alternatywy dla programu PowerShell możesz użyć wiersza polecenia, aby sprawdzić, Program antywirusowy Microsoft Defender działa. W tym celu uruchom następujące polecenie z wiersza polecenia:

```cmd
sc query Windefend
```

Polecenie `sc query` zwraca informacje o Program antywirusowy Microsoft Defender sieci. Gdy Program antywirusowy Microsoft Defender uruchomiony, jest wyświetlana `STATE` wartość `RUNNING`.

Aby wyświetlić wszystkie usługi, które nie są uruchomione, uruchom następujące polecenie cmdlet programu PowerShell:

```cmd
sc query state= all
```

## <a name="update-antimalware-security-intelligence"></a>Aktualizacja analizy zabezpieczeń przed złośliwym kodem

Aby uzyskać regularne aktualizacje analizy zabezpieczeń, usługa Windows Update musi być uruchomiona. Jeśli korzystasz z usługi zarządzania aktualizacjami, na przykład programu Windows Server Update Services (WSUS), upewnij się, że aktualizacje dla programu Program antywirusowy Microsoft Defender Funkcje analizy zabezpieczeń są zatwierdzone dla komputerów, których zarządzasz.

Domyślnie aktualizacje Windows Update są automatycznie pobieranie i instalowanie na Windows Server 2019 lub Windows Server 2022 lub Windows Server 2016. Tę konfigurację można zmienić przy użyciu jednej z następujących metod:

| Metoda | Opis |
|---|---|
| **Windows Update** w programie Panel sterowania | **Zainstalowanie aktualizacji powoduje automatyczne** zainstalowanie wszystkich aktualizacji, w tym aktualizacji analizy Windows Defender zabezpieczeń. <br/><br/> **Pobieraj aktualizacje, ale zdecyduję**, czy je zainstalować, Windows Defender automatyczne pobieranie i instalowanie aktualizacji analizy zabezpieczeń, ale inne aktualizacje nie są instalowane automatycznie. |
| **Zasady grupy** | Konfigurację usługi Windows Update i zarządzanie nimi można uzyskać, używając ustawień dostępnych w programie zasady grupy w następującej ścieżce: Szablony administracyjne **\Windows Składniki\Windows Update\Konfigurowanie** aktualizacji automatycznych |
| Klucz rejestru **AUOptions** | Dwie poniższe wartości umożliwiają automatyczne Windows Update pobierania i instalowania aktualizacji analizy zabezpieczeń: <br/><br/> **4** -  **Automatyczne instalowanie aktualizacji**. Ta wartość powoduje, że wszystkie aktualizacje są instalowane automatycznie, w tym aktualizacje Windows Defender aktualizacje analizy zabezpieczeń. <br/><br/> **3** -  **Pobieraj aktualizacje, ale pozwól mi wybrać, czy chcesz je zainstalować**. Ta wartość umożliwia Windows Defender automatyczne pobieranie i instalowanie aktualizacji analizy zabezpieczeń, ale inne aktualizacje nie są instalowane automatycznie. |

Aby zapewnić ochronę przed złośliwym oprogramowaniem, włącz następujące usługi:

- Raportowanie błędów systemu Windows usługi
- Windows Update usługi

W poniższej tabeli wymieniono usługi dla Program antywirusowy Microsoft Defender i usługi zależne.

| Nazwa usługi | Lokalizacja pliku | Opis |
|---|---|---|
| Windows Defender (WinDefend) | `C:\Program Files\Windows Defender\MsMpEng.exe` | Jest to główna Program antywirusowy Microsoft Defender, która musi być zawsze uruchomiona.|
| Raportowanie błędów systemu Windows (Wersvc) | `C:\WINDOWS\System32\svchost.exe -k WerSvcGroup` | Ta usługa wysyła raporty o błędach z powrotem do firmy Microsoft. |
| Windows Defender MpsSvc | `C:\WINDOWS\system32\svchost.exe -k LocalServiceNoNetwork` | Zalecamy, aby włączyć Windows Defender Zapory sieciowej. |
| Windows Update (Wuauserv) | `C:\WINDOWS\system32\svchost.exe -k netsvcs`| Windows Update jest niezbędne do uzyskania aktualizacji analizy zabezpieczeń i aktualizacji aparatu ochrony przed złośliwym kodem |

## <a name="submit-samples"></a>Prześlij próbki

Przykładowe przesyłanie umożliwia firmie Microsoft zbieranie próbek potencjalnie złośliwego oprogramowania. Aby zapewnić trwałą i na bieżąco ochronę, firma Microsoft używa tych próbek do analizowania podejrzanych działań i tworzenia zaktualizowanych analizy zabezpieczeń przed złośliwym kodem. Gromadzimy pliki wykonywalne programu, takie jak pliki .exe i .dll pliki. Nie gromadzimy plików zawierających dane osobowe, takich jak pliki Microsoft Word pdf.

### <a name="submit-a-file"></a>Przesyłanie pliku

1. Przejrzyj przewodnik [przesyłania](/windows/security/threat-protection/intelligence/submission-guide).

2. Odwiedź [przykładowy portal przesyłania](https://www.microsoft.com/wdsi/filesubmission) i prześlij plik.

### <a name="enable-automatic-sample-submission"></a>Włączanie automatycznego przesyłania próbek

Aby włączyć automatyczne przesyłanie próbek, uruchom konsolę Windows PowerShell jako administrator i ustaw dane wartości **SubmitSamplesConsent** zgodnie z jednym z następujących ustawień:

|Ustawienie|Opis|
|---|---|
| **0** -  **Zawsze monituj** | Usługa Program antywirusowy Microsoft Defender wyświetli monit o potwierdzenie przesłania wszystkich wymaganych plików. Jest to domyślne ustawienie dla programu Program antywirusowy Microsoft Defender, ale nie jest zalecane w przypadku instalacji w programie Windows Server 2016, 2019 lub Windows Server 2022 bez graficznego interfejsu użytkownika. |
| **1**  -  **Automatyczne wysyłanie bezpiecznych próbek** | Usługa Program antywirusowy Microsoft Defender wysyła wszystkie pliki oznaczone jako "bezpieczne" i wyświetla monit o pozostałe pliki. |
| **2** -  **Nigdy nie wysyłaj** | Usługa Program antywirusowy Microsoft Defender nie wyświetla monitu i nie wysyła żadnych plików. |
| **3** -  **Automatyczne wysyłanie wszystkich próbek** | Usługa Program antywirusowy Microsoft Defender wysyła wszystkie pliki bez monitu o potwierdzenie. |

> [!NOTE]
> Ta opcja nie jest dostępna w przypadku Windows Server 2012 R2. 

## <a name="configure-automatic-exclusions"></a>Konfigurowanie wykluczeń automatycznych

W celu zapewnienia bezpieczeństwa i wydajności niektóre wykluczenia są dodawane automatycznie na podstawie ról i funkcji instalowanych podczas korzystania z programu Program antywirusowy Microsoft Defender w systemie Windows Server 2016 lub 2019 albo Windows Server 2022.

Zobacz [Konfigurowanie wykluczeń w Program antywirusowy Microsoft Defender na Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md).

## <a name="passive-mode-and-windows-server"></a>Tryb pasywny i Windows serwera

Jeśli używasz produktu antywirusowego innego niż firmy Microsoft jako podstawowego rozwiązania antywirusowego w programie Windows Server, musisz ustawić tryb Program antywirusowy Microsoft Defender pasywny lub wyłączony. Jeśli punkt Windows serwera jest dołączany do Ochrona punktu końcowego w usłudze Microsoft Defender, możesz Program antywirusowy Microsoft Defender tryb pasywny. Jeśli nie korzystasz z programu Ochrona punktu końcowego w usłudze Microsoft Defender, ustaw dla Program antywirusowy Microsoft Defender tryb wyłączony. 

> [!TIP]
> Zobacz [Program antywirusowy Microsoft Defender z innymi produktami zabezpieczającymi](microsoft-defender-antivirus-compatibility.md).

W poniższej tabeli opisano metody ustawienia trybu Program antywirusowy Microsoft Defender na pasywny, wyłączenia Program antywirusowy Microsoft Defender i odinstalowywania Program antywirusowy Microsoft Defender:

| Procedura | Opis |
|---|---|
| Ustawianie Program antywirusowy Microsoft Defender na tryb pasywny przy użyciu klucza rejestru | Ustaw klucz rejestru ForceDefenderPassiveMode w następujący sposób: <br/>— Ścieżka: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection` <br/>- Nazwa: `ForceDefenderPassiveMode` <br/>- Wpisz: `REG_DWORD` <br/>- Wartość: `1` |
| Wyłączanie interfejsu Program antywirusowy Microsoft Defender przy użyciu programu PowerShell | Otwórz Windows PowerShell jako administrator i uruchom następujące polecenie cmdlet programu PowerShell:`Uninstall-WindowsFeature -Name Windows-Defender-GUI`
| Wyłączanie Program antywirusowy Microsoft Defender przy użyciu programu PowerShell | Użyj następującego polecenia cmdlet programu PowerShell: `Set-MpPreference -DisableRealtimeMonitoring $true` |
| Wyłączanie Program antywirusowy Microsoft Defender przy użyciu kreatora Usuwanie ról i funkcji | Zobacz [Instalowanie lub odinstalowywanie ról, usług ról lub funkcji](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#remove-roles-role-services-and-features-by-using-the-remove-roles-and-features-wizard) i korzystanie z Kreatora **usuwania ról i funkcji**. <br/><br/>Po **dojechu** do kroku Funkcje kreatora wyczyść opcję Windows Defender **Funkcje**. <br/><br/> Jeśli wyczyścisz **Windows Defender** w sekcji Funkcje Windows Defender, zostanie wyświetlony  monit o usunięcie graficznego interfejsu użytkownika dla **Windows Defender**.<br/><br/>Program antywirusowy Microsoft Defender działać normalnie bez interfejsu użytkownika, ale nie można włączyć interfejsu użytkownika, jeśli wyłączysz podstawową **Windows Defender** interfejsu. |
| Odinstalowywanie Program antywirusowy Microsoft Defender przy użyciu programu PowerShell | Użyj następującego polecenia cmdlet programu PowerShell: `Uninstall-WindowsFeature -Name Windows-Defender` |
| Wyłączanie Program antywirusowy Microsoft Defender przy użyciu zasady grupy | W Edytorze zasady grupy kliknij  >  pozycję Szablon administracyjny **Windows Składnik** >  **Endpoint Protection** >  **Wyzysłane Endpoint Protection**, a następnie wybierz **pozycję EnabledOK** > . |

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>Używasz programu Windows Server 2012 R2 lub Windows Server 2016?

Jeśli komputer Windows jest Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze, możesz teraz uruchamiać Program antywirusowy Microsoft Defender trybie pasywnym na Windows Server 2012 R2 i Windows Server 2016. Zobacz następujące artykuły:

- [Opcje instalowania Ochrona punktu końcowego w usłudze Microsoft Defender](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages)

- [Program antywirusowy Microsoft Defender zgodności z innymi produktami zabezpieczającymi](microsoft-defender-antivirus-compatibility.md)

## <a name="see-also"></a>Zobacz też

- [Program antywirusowy Microsoft Defender w systemie Windows](microsoft-defender-antivirus-windows.md)

