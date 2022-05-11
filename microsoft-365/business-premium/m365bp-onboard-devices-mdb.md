---
title: Dołączanie urządzeń organizacji do Microsoft Defender dla Firm
description: Dołączanie urządzeń organizacji do Microsoft Defender dla Firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/01/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: a03d79da004dab7a68e691c6c2a8ac21ac2b7501
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2022
ms.locfileid: "65318187"
---
# <a name="onboard-enrolled-devices-to-microsoft-defender-for-business"></a>Dołączanie zarejestrowanych urządzeń do Microsoft Defender dla Firm

Po zarejestrowaniu urządzeń należy je dołączyć do Microsoft Defender dla Firm w celu zaimplementowania ochrony nowej generacji (ochrony antywirusowej, ochrony przed złośliwym kodem i ochrony dostarczanej w chmurze), ochrony zapory, filtrowania zawartości internetowej i nie tylko. 

Aby dołączyć urządzenia, możesz wybrać jedną z kilku opcji:

- [Używanie automatycznego dołączania dla urządzeń Windows, które są już zarejestrowane w Microsoft Endpoint Manager](#use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-microsoft-endpoint-manager)

- [Dołączanie urządzeń Windows i macOS przy użyciu skryptu lokalnego](#use-a-local-script-to-onboard-windows-and-macos-devices)

- [Rejestrowanie urządzeń](#use-microsoft-endpoint-manager-to-enroll-devices) (Windows, macOS, iOS i Android przy użyciu Endpoint Manager), a następnie stosowanie zasad usługi Defender for Business na tych urządzeniach

Ten artykuł zawiera również następujące elementy:

- [Jak uruchomić test wykrywania na urządzeniu Windows](#run-a-detection-test-on-a-windows-device)

- [Jak stopniowo dołączać urządzenia](#onboard-devices-gradually)

- [Jak odłączyć urządzenie](#offboard-a-device) , jeśli urządzenie zostanie zastąpione lub ktoś opuści organizację

> [!IMPORTANT]
> Jeśli coś pójdzie nie tak i proces dołączania zakończy się niepowodzeniem, zobacz [Microsoft Defender dla Firm rozwiązywanie problemów](../security/defender-business/mdb-troubleshooting.yml).

## <a name="use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-microsoft-endpoint-manager"></a>Używanie automatycznego dołączania dla urządzeń Windows, które są już zarejestrowane w Microsoft Endpoint Manager

Opcja automatycznego dołączania dotyczy tylko urządzeń Windows. Automatyczne dołączanie jest dostępne, jeśli spełnione są następujące warunki:

- Twoja organizacja używała już Microsoft Endpoint Manager, Microsoft Intune lub mobile Zarządzanie urządzeniami (MDM) w Microsoft Intune, zanim otrzymasz usługę Defender for Business ( Microsoft 365 Business Premium klienci mają już Microsoft Intune).

- Masz już Windows urządzenia zarejestrowane w Endpoint Manager.

Jeśli Windows urządzenia są już zarejestrowane w usłudze Endpoint Manager, usługa Defender dla Firm wykryje te urządzenia podczas konfigurowania i konfigurowania usługi Defender dla firm. Zostanie wyświetlone pytanie, czy chcesz używać automatycznego dołączania dla wszystkich lub niektórych urządzeń Windows. Możesz dołączyć wszystkie urządzenia Windows jednocześnie lub wybrać określone urządzenia do rozpoczęcia, a następnie dodać więcej urządzeń później.

> [!TIP]
> Zalecamy wybranie opcji "wszystkie zarejestrowane urządzenia". Dzięki temu, gdy Windows urządzenia zostaną zarejestrowane w Endpoint Manager później, zostaną automatycznie dołączone do usługi Defender for Business.
Aby dowiedzieć się więcej na temat automatycznego dołączania, zobacz Krok 2 w temacie [Używanie kreatora do konfigurowania Microsoft Defender dla Firm](../security/defender-business/mdb-use-wizard.md).

## <a name="use-a-local-script-to-onboard-windows-and-macos-devices"></a>Dołączanie urządzeń Windows i macOS przy użyciu skryptu lokalnego

Do dołączania Windows i komputerów Mac można użyć skryptu lokalnego. Po uruchomieniu skryptu dołączania na urządzeniu tworzy on relację zaufania z Azure Active Directory (jeśli to zaufanie jeszcze nie istnieje), rejestruje urządzenie w Microsoft Endpoint Manager (jeśli nie zostało jeszcze zarejestrowane), a następnie dołącza urządzenie do usługi Defender dla Firm. Ta metoda jest przydatna do dołączania urządzeń w usłudze Defender dla Firm. Jednocześnie można dołączyć maksymalnie 10 urządzeń.

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Ustawienia** >  **Punkty końcowe**, a następnie w obszarze **Zarządzanie urządzeniami** wybierz pozycję **Dołączanie**.

3. Wybierz system operacyjny, taki jak **Windows 10 i 11** lub **macOS**, a następnie w sekcji **Metoda wdrażania** wybierz pozycję **Skrypt lokalny**. 

4. Wybierz pozycję **Pobierz pakiet dołączania**. Zalecamy zapisanie pakietu dołączania na dysku wymiennym. (Jeśli **wybrano macOS**, wybierz również pozycję **Pobierz pakiet instalacyjny** i zapisz go na urządzeniu wymiennym).

5. Skorzystaj z następujących wskazówek:

   - urządzenia Windows: [dołączanie urządzeń Windows przy użyciu skryptu lokalnego](../security/defender-endpoint/configure-endpoints-script.md#onboard-windows-devices-using-a-local-script)

   - urządzenia macOS: [ręczne wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender na macOS](../security/defender-endpoint/mac-install-manually.md#download-installation-and-onboarding-packages)

## <a name="use-microsoft-endpoint-manager-to-enroll-devices"></a>Rejestrowanie urządzeń przy użyciu Microsoft Endpoint Manager

Aby zarejestrować urządzenie, zarejestruj je samodzielnie lub poproś użytkowników o zalogowanie się do portalu firmy i zarejestrowanie i zainstalowanie wszystkich potrzebnych aplikacji. 

Jeśli używasz już Endpoint Manager (w tym Microsoft Intune i mobile Zarządzanie urządzeniami), zanim otrzymasz usługę Defender dla Firm, możesz nadal używać Endpoint Manager do dołączania urządzeń organizacji. Dzięki Endpoint Manager można dołączyć komputery, tablety i telefony, w tym urządzenia iOS i Android.

Zobacz [Rejestrowanie urządzeń w Microsoft Intune](/mem/intune/enrollment/device-enrollment). 

## <a name="run-a-detection-test-on-a-windows-device"></a>Uruchamianie testu wykrywania na urządzeniu Windows

Po dodaniu urządzeń Windows do usługi Defender dla Firm możesz uruchomić test wykrywania na urządzeniu Windows, aby upewnić się, że wszystko działa poprawnie.

1. Na urządzeniu Windows utwórz folder: `C:\test-MDATP-test`.

2. Otwórz wiersz polecenia jako administrator.

3. W oknie wiersza polecenia uruchom następujące polecenie programu PowerShell:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Po uruchomieniu polecenia okno wiersza polecenia zostanie zamknięte automatycznie. Jeśli test wykrywania zakończy się pomyślnie, w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) dla nowo dołączonego urządzenia zostanie wyświetlony nowy alert w ciągu około dziesięciu minut.

## <a name="onboard-devices-gradually"></a>Stopniowo dołączanie urządzeń

Jeśli wolisz dołączać urządzenia w fazach, które nazywamy *stopniowym dołączaniem urządzeń*, wykonaj następujące kroki: 

1. Zidentyfikuj zestaw urządzeń do dołączenia.

2. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

3. W okienku nawigacji wybierz pozycję **Ustawienia** >  **Punkty końcowe**, a następnie w obszarze **Zarządzanie urządzeniami** wybierz pozycję **Dołączanie**.

4. Wybierz system operacyjny (na przykład **Windows 10 i 11),** a następnie wybierz metodę dołączania (na przykład **skrypt lokalny**). Postępuj zgodnie ze wskazówkami podanymi dla wybranej metody.

5. Powtórz ten proces dla każdego zestawu urządzeń, które chcesz dołączyć. 

> [!TIP]
> Nie trzeba używać tego samego pakietu dołączania za każdym razem, gdy dołączasz urządzenia. Na przykład możesz użyć skryptu lokalnego do dołączania niektórych urządzeń, a później możesz wybrać inną metodę dołączania większej liczby urządzeń.

## <a name="offboard-a-device"></a>Odłączanie urządzenia

Jeśli chcesz odłączyć urządzenie, użyj jednej z następujących procedur:

1. W okienku nawigacji wybierz **pozycję Ustawienia**, a następnie wybierz pozycję **Punkty końcowe**.

1. W obszarze **Zarządzanie urządzeniami** wybierz pozycję **Odłączanie**.

1. Wybierz system operacyjny, taki jak **Windows 10 i 11**, a następnie w obszarze **Odłącz urządzenie** w sekcji **Metoda wdrażania** wybierz pozycję **Skrypt lokalny**. 

1. Na ekranie potwierdzenia przejrzyj informacje, a następnie wybierz pozycję **Pobierz** , aby kontynuować.

1. Wybierz pozycję **Pobierz pakiet odłączania**. Zalecamy zapisanie pakietu odłączania na dysku wymiennym.

1. Uruchom skrypt na każdym urządzeniu, które chcesz odłączyć. Potrzebujesz pomocy dotyczącej tego zadania? Zobacz następujące zasoby:   

   - urządzenia Windows: [odłączanie urządzeń Windows przy użyciu skryptu lokalnego](../security/defender-endpoint/configure-endpoints-script.md#offboard-devices-using-a-local-script)
   
   - urządzenia macOS: [odinstalowywanie na macOS](../security/defender-endpoint/mac-resources.md#uninstalling)

> [!IMPORTANT]
> Odłączenie urządzenia powoduje, że urządzenia przestają wysyłać dane do usługi Defender dla Firm. Jednak dane odebrane przed odłożeniem są przechowywane przez maksymalnie sześć (6) miesięcy.

## <a name="next-objective"></a>Następny cel

[Skonfiguruj ochronę urządzeń Windows](m365bp-protection-settings-for-windows-10-devices.md).
