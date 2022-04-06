---
title: Program antywirusowy Microsoft Defender na serwerze Windows
description: Dowiedz się, jak włączyć i skonfigurować Program antywirusowy Microsoft Defender na Windows Server 2016, Windows Server 2019 i Windows Server 2022.
keywords: windows defender, server, scep, system center endpoint protection, server 2016, current branch, server 2012
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
ms.openlocfilehash: b93595375982e3ed61d1ac94ae410575b0d72307
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666993"
---
# <a name="microsoft-defender-antivirus-on-windows-server"></a>Program antywirusowy Microsoft Defender na serwerze Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

Program antywirusowy Microsoft Defender jest dostępna w następujących wersjach/wersjach serwera Windows:

- Windows Server 2022
- Windows Server 2019
- Windows Server, wersja 1803 lub nowsza
- System Windows Server 2016
- Windows Server 2012 R2 (wymaga Ochrona punktu końcowego w usłudze Microsoft Defender)

## <a name="setting-up-microsoft-defender-antivirus-on-windows-server"></a>Konfigurowanie Program antywirusowy Microsoft Defender na serwerze Windows

Proces konfigurowania i uruchamiania Program antywirusowy Microsoft Defender na serwerze Windows Server obejmuje następujące kroki:

1. [Włącz interfejs](#enable-the-user-interface-on-windows-server).
2. [Zainstaluj Program antywirusowy Microsoft Defender](#install-microsoft-defender-antivirus-on-windows-server).
3. [Sprawdź, Program antywirusowy Microsoft Defender jest uruchomiona](#verify-microsoft-defender-antivirus-is-running).
4. [Zaktualizuj analizę zabezpieczeń ochrony przed złośliwym kodem](#update-antimalware-security-intelligence).
5. (W razie potrzeby) [Prześlij przykłady](#submit-samples).
6. (W razie potrzeby) [Konfigurowanie automatycznych wykluczeń](#configure-automatic-exclusions).
7. (Tylko w razie potrzeby) Ustaw [Windows Server na tryb pasywny](#passive-mode-and-windows-server).

## <a name="enable-the-user-interface-on-windows-server"></a>Włączanie interfejsu użytkownika na serwerze Windows

> [!IMPORTANT]
> Jeśli używasz Windows Server 2012 R2, zobacz [Opcje instalowania Ochrona punktu końcowego w usłudze Microsoft Defender](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

Domyślnie Program antywirusowy Microsoft Defender jest zainstalowany i działa na serwerze Windows. Czasami interfejs użytkownika (GUI) jest instalowany domyślnie. Graficzny interfejs użytkownika nie jest wymagany; Do zarządzania Program antywirusowy Microsoft Defender można użyć programu PowerShell, zasady grupy lub innych metod. Jednak wiele organizacji woli używać graficznego interfejsu użytkownika dla Program antywirusowy Microsoft Defender. Aby zainstalować graficzny interfejs użytkownika, użyj jednej z procedur w poniższej tabeli:

| Procedura | Co robić |
|:---|:---|
| Włączanie interfejsu użytkownika przy użyciu Kreatora dodawania ról i funkcji | 1. Zobacz [Instalowanie ról, usług ról i funkcji przy użyciu Kreatora dodawania ról i funkcji](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) oraz **kreatora dodawania ról i funkcji**. <br/><br/>2. Po przejściu do kroku **Funkcje** kreatora w obszarze **funkcje Windows Defender** wybierz graficzny **interfejs użytkownika, aby Windows Defender** opcję. |
| Włączanie interfejsu użytkownika przy użyciu programu PowerShell | 1. Na serwerze Windows otwórz Windows PowerShell jako administrator. <br/><br/>2. Uruchom następujące polecenie cmdlet programu PowerShell: `Install-WindowsFeature -Name Windows-Defender-GUI` |

## <a name="install-microsoft-defender-antivirus-on-windows-server"></a>Instalowanie Program antywirusowy Microsoft Defender na serwerze Windows

Jeśli musisz zainstalować lub ponownie zainstalować Program antywirusowy Microsoft Defender na serwerze Windows Server, użyj jednej z procedur w poniższej tabeli:

| Procedura | Co robić |
|:---|:---|
| Użyj Kreatora dodawania ról i funkcji, aby zainstalować Program antywirusowy Microsoft Defender | 1. Zobacz [Instalowanie lub odinstalowywanie ról, usług ról lub funkcji](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) oraz korzystanie z **Kreatora dodawania ról i funkcji**. <br/><br/>2. Po przejściu do kroku **Funkcje** kreatora wybierz opcję Program antywirusowy Microsoft Defender. Wybierz również graficzny **interfejs użytkownika dla opcji Windows Defender**. |
| Instalowanie Program antywirusowy Microsoft Defender przy użyciu programu PowerShell | 1. Na serwerze Windows otwórz Windows PowerShell jako administrator. <br/><br/>2. Uruchom następujące polecenie cmdlet programu PowerShell: `Install-WindowsFeature -Name Windows-Defender` |

> [!NOTE]
> Komunikaty o zdarzeniach dla aparatu ochrony przed złośliwym kodem dołączone do Program antywirusowy Microsoft Defender można znaleźć w [Program antywirusowy Microsoft Defender Zdarzenia](troubleshoot-microsoft-defender-antivirus.md).

## <a name="verify-microsoft-defender-antivirus-is-running"></a>Sprawdź, czy Program antywirusowy Microsoft Defender jest uruchomiona

Po zainstalowaniu (lub ponownym zainstalowaniu) Program antywirusowy Microsoft Defender następnym krokiem jest sprawdzenie, czy jest on uruchomiony. Użyj poleceń cmdlet programu PowerShell w poniższej tabeli:

| Procedura | Polecenie cmdlet programu PowerShell |
|:---|:---|
| Sprawdź, czy Program antywirusowy Microsoft Defender jest uruchomiona | `Get-Service -Name windefend` |
| Sprawdź, czy ochrona zapory jest włączona | `Get-Service -Name mpssvc` |

Alternatywnie do programu PowerShell możesz użyć wiersza polecenia, aby sprawdzić, czy Program antywirusowy Microsoft Defender jest uruchomiona. W tym celu uruchom następujące polecenie w wierszu polecenia:

```cmd
sc query Windefend
```

Polecenie `sc query` zwraca informacje o usłudze Program antywirusowy Microsoft Defender. Gdy Program antywirusowy Microsoft Defender jest uruchomiona, wartość jest wyświetlana `STATE` `RUNNING`.

Aby wyświetlić wszystkie usługi, które nie są uruchomione, uruchom następujące polecenie cmdlet programu PowerShell:

```cmd
sc query state= all
```

## <a name="update-antimalware-security-intelligence"></a>Aktualizowanie analizy zabezpieczeń ochrony przed złośliwym kodem

Aby uzyskać regularne aktualizacje analizy zabezpieczeń, musi być uruchomiona usługa Windows Update. Jeśli używasz usługi zarządzania aktualizacjami, takiej jak Windows Server Update Services (WSUS), upewnij się, że aktualizacje Program antywirusowy Microsoft Defender Analiza zabezpieczeń są zatwierdzane dla zarządzanych komputerów.

Domyślnie Windows Update nie pobiera ani nie instaluje aktualizacji automatycznie na serwerze Windows Server 2019 lub Windows Server 2022 lub Windows Server 2016. Tę konfigurację można zmienić przy użyciu jednej z następujących metod:

| Metoda | Opis |
|---|---|
| **Windows Update** w Panel sterowania | **Automatyczne instalowanie aktualizacji** powoduje automatyczne instalowanie wszystkich aktualizacji, w tym Windows Defender aktualizacji analizy zabezpieczeń. <br/><br/> **Pobierz aktualizacje, ale pozwól mi wybrać, czy je zainstalować**, umożliwia Windows Defender automatyczne pobieranie i instalowanie aktualizacji analizy zabezpieczeń, ale inne aktualizacje nie są instalowane automatycznie. |
| **Zasady grupy** | Windows Update można skonfigurować i zarządzać nimi przy użyciu ustawień dostępnych w zasady grupy, w następującej ścieżce: **Szablony administracyjne\Windows Components\Windows Update\Configure Automatic Updates** |
| Klucz rejestru **AUOptions** | Następujące dwie wartości umożliwiają Windows Update automatyczne pobieranie i instalowanie aktualizacji analizy zabezpieczeń: <br/><br/> **4.** -  **Zainstaluj aktualizacje automatycznie**. Ta wartość powoduje automatyczne instalowanie wszystkich aktualizacji, w tym Windows Defender aktualizacji analizy zabezpieczeń. <br/><br/> **3.** -  **Pobierz aktualizacje, ale pozwól mi wybrać, czy je zainstalować**. Ta wartość umożliwia Windows Defender automatyczne pobieranie i instalowanie aktualizacji analizy zabezpieczeń, ale inne aktualizacje nie są instalowane automatycznie. |

Aby zapewnić ochronę przed złośliwym oprogramowaniem, włącz następujące usługi:

- usługa Raportowanie błędów systemu Windows
- usługa Windows Update

W poniższej tabeli wymieniono usługi dla usług Program antywirusowy Microsoft Defender i usług zależnych.

| Nazwa usługi | Lokalizacja pliku | Opis |
|---|---|---|
| usługa Windows Defender (WinDefend) | `C:\Program Files\Windows Defender\MsMpEng.exe` | Jest to główna usługa Program antywirusowy Microsoft Defender, która musi być zawsze uruchomiona.|
| usługa Raportowanie błędów systemu Windows (Wersvc) | `C:\WINDOWS\System32\svchost.exe -k WerSvcGroup` | Ta usługa wysyła raporty o błędach z powrotem do firmy Microsoft. |
| zapora Windows Defender (MpsSvc) | `C:\WINDOWS\system32\svchost.exe -k LocalServiceNoNetwork` | Zalecamy włączenie usługi zapory Windows Defender. |
| Windows Update (Wuauserv) | `C:\WINDOWS\system32\svchost.exe -k netsvcs`| Windows Update jest potrzebny do pobierania aktualizacji analizy zabezpieczeń i aktualizacji aparatu ochrony przed złośliwym kodem |

## <a name="submit-samples"></a>Przesyłanie przykładów

Przykładowe przesyłanie umożliwia firmie Microsoft zbieranie przykładów potencjalnie złośliwego oprogramowania. Aby zapewnić ciągłą i aktualną ochronę, badacze firmy Microsoft używają tych przykładów do analizowania podejrzanych działań i tworzenia zaktualizowanych analiz zabezpieczeń chroniących przed złośliwym kodem. Zbieramy pliki wykonywalne programu, takie jak pliki .exe i pliki .dll. Nie zbieramy plików zawierających dane osobowe, takich jak dokumenty Microsoft Word i pliki PDF.

### <a name="submit-a-file"></a>Przesyłanie pliku

1. Zapoznaj się z [przewodnikiem przesyłania](/windows/security/threat-protection/intelligence/submission-guide).

2. Odwiedź [przykładowy portal przesyłania](https://www.microsoft.com/wdsi/filesubmission) i prześlij plik.

### <a name="enable-automatic-sample-submission"></a>Włączanie automatycznego przesyłania przykładów

Aby włączyć automatyczne przesyłanie przykładów, uruchom konsolę Windows PowerShell jako administrator i ustaw dane wartości **SubmitSamplesConsent** zgodnie z jednym z następujących ustawień:

|Ustawienie|Opis|
|---|---|
| **0** -  **Zawsze monituj** | Usługa Program antywirusowy Microsoft Defender monituje o potwierdzenie przesłania wszystkich wymaganych plików. Jest to ustawienie domyślne dla Program antywirusowy Microsoft Defender, ale nie jest zalecane w przypadku instalacji na Windows Server 2016, 2019 lub Windows Server 2022 bez graficznego interfejsu użytkownika. |
| **1**  -  **Automatyczne wysyłanie bezpiecznych próbek** | Usługa Program antywirusowy Microsoft Defender wysyła wszystkie pliki oznaczone jako "bezpieczne" i monituje o resztę plików. |
| **2.** -  **Nigdy nie wysyłaj** | Usługa Program antywirusowy Microsoft Defender nie wyświetla monitów i nie wysyła żadnych plików. |
| **3.** -  **Automatycznie wysyłaj wszystkie przykłady** | Usługa Program antywirusowy Microsoft Defender wysyła wszystkie pliki bez monitu o potwierdzenie. |

> [!NOTE]
> Ta opcja nie jest dostępna dla Windows Server 2012 R2. 

## <a name="configure-automatic-exclusions"></a>Konfigurowanie automatycznych wykluczeń

Aby zapewnić bezpieczeństwo i wydajność, niektóre wykluczenia są automatycznie dodawane na podstawie ról i funkcji instalowanych podczas korzystania z Program antywirusowy Microsoft Defender na Windows Server 2016 lub 2019 lub Windows Server 2022.

Zobacz [Konfigurowanie wykluczeń w Program antywirusowy Microsoft Defender na serwerze Windows](configure-server-exclusions-microsoft-defender-antivirus.md).

## <a name="passive-mode-and-windows-server"></a>Tryb pasywny i serwer Windows

Jeśli używasz produktu antywirusowego innego niż Microsoft jako podstawowego rozwiązania antywirusowego na serwerze Windows Server, musisz ustawić Program antywirusowy Microsoft Defender na tryb pasywny lub wyłączony. Jeśli punkt końcowy serwera Windows jest dołączony do Ochrona punktu końcowego w usłudze Microsoft Defender, możesz ustawić Program antywirusowy Microsoft Defender na tryb pasywny. Jeśli nie używasz Ochrona punktu końcowego w usłudze Microsoft Defender, ustaw Program antywirusowy Microsoft Defender na tryb wyłączony. 

> [!TIP]
> Zobacz [Program antywirusowy Microsoft Defender zgodności z innymi produktami zabezpieczającymi](microsoft-defender-antivirus-compatibility.md).

W poniższej tabeli opisano metody ustawiania Program antywirusowy Microsoft Defender na tryb pasywny, wyłączania Program antywirusowy Microsoft Defender i odinstalowywania Program antywirusowy Microsoft Defender:

| Procedura | Opis |
|---|---|
| Ustawianie Program antywirusowy Microsoft Defender na tryb pasywny przy użyciu klucza rejestru | Ustaw klucz rejestru ForceDefenderPassiveMode w następujący sposób: <br/>- Ścieżka: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection` <br/>- Nazwa: `ForceDefenderPassiveMode` <br/>- Typ: `REG_DWORD` <br/>- Wartość: `1` |
| Wyłączanie interfejsu użytkownika Program antywirusowy Microsoft Defender przy użyciu programu PowerShell | Otwórz Windows PowerShell jako administrator i uruchom następujące polecenie cmdlet programu PowerShell:`Uninstall-WindowsFeature -Name Windows-Defender-GUI`
| Wyłączanie Program antywirusowy Microsoft Defender przy użyciu programu PowerShell | Użyj następującego polecenia cmdlet programu PowerShell: `Set-MpPreference -DisableRealtimeMonitoring $true` |
| Wyłączanie Program antywirusowy Microsoft Defender przy użyciu kreatora usuwania ról i funkcji | Zobacz [Instalowanie lub odinstalowywanie ról, usług ról lub funkcji](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#remove-roles-role-services-and-features-by-using-the-remove-roles-and-features-wizard) oraz korzystanie z **Kreatora usuwania ról i funkcji**. <br/><br/>Po przejściu do kroku **Funkcje** kreatora wyczyść opcję **Windows Defender Funkcje**. <br/><br/> Jeśli wyczyścisz **Windows Defender** samodzielnie w sekcji **funkcje Windows Defender**, zostanie wyświetlony monit o usunięcie **graficznego interfejsu użytkownika opcji interfejsu dla Windows Defender**.<br/><br/>Program antywirusowy Microsoft Defender nadal będą działać normalnie bez interfejsu użytkownika, ale nie można włączyć interfejsu użytkownika, jeśli wyłączysz podstawową funkcję **Windows Defender**. |
| Odinstalowywanie Program antywirusowy Microsoft Defender przy użyciu programu PowerShell | Użyj następującego polecenia cmdlet programu PowerShell: `Uninstall-WindowsFeature -Name Windows-Defender` |
| Wyłączanie Program antywirusowy Microsoft Defender przy użyciu zasady grupy | W lokalnym edytorze zasady grupy przejdź do pozycji **Szablon** >  administracyjny **Windows Składnik** >  **Endpoint Protection** >  **Disable Endpoint Protection**, a następnie wybierz pozycję **EnabledOK** > . |

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>Czy używasz Windows Server 2012 R2, czy Windows Server 2016?

Jeśli serwer Windows jest dołączony do Ochrona punktu końcowego w usłudze Microsoft Defender, możesz teraz uruchomić Program antywirusowy Microsoft Defender w trybie pasywnym w Windows Server 2012 R2 i Windows Server 2016. Zobacz następujące artykuły:

- [Opcje instalacji Ochrona punktu końcowego w usłudze Microsoft Defender](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages)

- [Program antywirusowy Microsoft Defender zgodności z innymi produktami zabezpieczającymi](microsoft-defender-antivirus-compatibility.md)

## <a name="see-also"></a>Zobacz też

- [Program antywirusowy Microsoft Defender w systemie Windows](microsoft-defender-antivirus-windows.md)

