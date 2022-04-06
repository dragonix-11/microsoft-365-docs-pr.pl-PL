---
title: Wdowaj urządzenia organizacji, aby Microsoft Defender dla Firm
description: Wdowaj urządzenia organizacji, aby Microsoft Defender dla Firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/01/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: e9810b453136025e094ef8a0e88bff526f2c5a51
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634784"
---
# <a name="onboard-managed-devices-to-microsoft-defender-for-business"></a>Dołączanie urządzeń zarządzanych do Microsoft Defender dla Firm

Urządzenia w nim Microsoft Defender dla Firm w celu ich ochrony za pomocą ochrony nowej generacji (ochrony antywirusowej, ochrony przed złośliwym oprogramowaniem i dostarczana w chmurze), ochrony zapory, filtrowania zawartości sieci Web i innych. 

Aby wychować urządzenia, możesz wybrać jedną z kilku opcji:

- [Użyj automatycznego dołączania dla Windows, które są już zarejestrowane w programie Microsoft Endpoint Manager](#use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-microsoft-endpoint-manager)

- [Używanie skryptu lokalnego na urządzeniach Windows i macOS](#use-a-local-script-to-onboard-windows-and-macos-devices)

- [Zarejestruj Endpoint Manager](#use-microsoft-endpoint-manager-to-enroll-devices) urządzenia (w systemie Windows, macOS, iOS i Android), a następnie zastosuj zasady usługi Defender dla firm do tych urządzeń

Ten artykuł zawiera również:

- [Jak uruchomić test wykrywania na Windows urządzenia](#run-a-detection-test-on-a-windows-device)

- [Jak stopniowo dołączać urządzenia](#onboard-devices-gradually)

- [Jak wyeżdżać urządzenie](#offboard-a-device) w przypadku jego wymiany lub gdy ktoś odejdzie z organizacji

> [!IMPORTANT]
> Jeśli coś poszło nie tak i proces dołączania zakończy się niepowodzeniem, [zobacz rozwiązywanie Microsoft Defender dla Firm problemów](../security/defender-business/mdb-troubleshooting.yml).

## <a name="use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-microsoft-endpoint-manager"></a>Użyj automatycznego dołączania dla Windows, które są już zarejestrowane w programie Microsoft Endpoint Manager

Opcja automatycznego dołączania dotyczy tylko Windows urządzeniach. Automatyczne dołączanie jest dostępne, jeśli Twoja organizacja używa już usługi Microsoft Endpoint Manager, Microsoft Intune lub Mobile Zarządzanie urządzeniami (MDM) w układzie Microsoft Intune przed użyciem programu Defender dla firm i masz już usługę Windows urządzenia zarejestrowane w programie Endpoint Manager. 

Jeśli Windows urządzenia są już zarejestrowane w usłudze Endpoint Manager, program Defender dla firm wykryje je podczas konfigurowania i konfigurowania usługi Defender dla firm. Zostaniesz poproszony(-a) o zastosowanie automatycznego dołączania do wszystkich lub niektórych Windows urządzeniach. Możesz wychować wszystkie Windows urządzenia jednocześnie lub wybrać określone urządzenia, od których chcesz zacząć, a następnie dodać więcej urządzeń później.

Aby dowiedzieć się więcej o automatycznym dołączaniu, zobacz Krok 2 w tece Konfigurowanie konfiguracji przy użyciu [Microsoft Defender dla Firm](../security/defender-business/mdb-use-wizard.md).

## <a name="use-a-local-script-to-onboard-windows-and-macos-devices"></a>Używanie skryptu lokalnego na urządzeniach Windows i macOS

Aby w urządzeniach Windows i macOS, możesz użyć skryptu lokalnego. Po uruchomieniu skryptu dołączania na urządzeniu tworzy on zaufanie dla programu Azure Active Directory (jeśli to zaufanie jeszcze nie istnieje), rejestruje urządzenie w usłudze Microsoft Endpoint Manager (jeśli nie zostało jeszcze zarejestrowane), a następnie uruchamia urządzenie do usługi Defender dla firm. 

Za pomocą tej metody można wychować do 10 urządzeń jednocześnie.

1. Przejdź do Microsoft 365 Defender portalu internetowego ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Ustawienia** >  **Endpoints**, a następnie w obszarze **Zarządzanie** urządzeniami wybierz **pozycję Dołączanie**.

3. Wybierz system operacyjny, na przykład Windows 10 i **11**, **a** następnie w obszarze Na wsadu urządzenia w sekcji Metoda wdrażania  wybierz pozycję **Skrypt lokalny**. 

4. Wybierz **pozycję Pobierz pakiet dołączający**. Zalecamy zapisanie pakietu dołączania na dysku wymiennym.

5. Postępuj zgodnie z wskazówkami w następujących artykułach:

   - Windows urządzenia: Na [urządzeniach Windows korzystające ze skryptu lokalnego](../security/defender-endpoint/configure-endpoints-script.md#onboard-windows-devices-using-a-local-script)

   - Urządzenia z systemem macOS: [Ręczne wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](../security/defender-endpoint/mac-install-manually.md#download-installation-and-onboarding-packages)

## <a name="use-microsoft-endpoint-manager-to-enroll-devices"></a>Zarejestruj Microsoft Endpoint Manager za pomocą urządzenia

Jeśli korzystano już z usługi Endpoint Manager (która obejmuje aplikacje Microsoft Intune i Mobile Zarządzanie urządzeniami), przed zakupem usługi Defender dla firm możesz nadal korzystać z programu Endpoint Manager do wnosnia urządzeń organizacji. Dzięki Endpoint Manager możesz korzystać z komputerów, tabletów i telefonów, w tym urządzeń z systemami iOS i Android.

Jeśli Twoja organizacja używa urządzeń z systemem Android, użyj tej metody.

Zobacz [Rejestracja urządzenia w aplikacji Microsoft Intune](/mem/intune/enrollment/device-enrollment).


## <a name="run-a-detection-test-on-a-windows-device"></a>Uruchamianie testu wykrywania na Windows urządzenia

Po włoceniu innych urządzeń Windows do usługi Defender dla firm możesz uruchomić test wykrywania na urządzeniu z systemem Windows, aby upewnić się, że wszystko działa poprawnie.

1. Na Windows utwórz folder: `C:\test-MDATP-test`.

2. Otwórz wiersz polecenia jako administrator.

3. W oknie Wiersz polecenia uruchom następujące polecenie programu PowerShell:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Po uruchomieniu polecenia okno Wiersz polecenia zostanie zamknięte automatycznie. Jeśli wykrywanie zakończy się pomyślnie, test wykrywania zostanie oznaczony jako ukończony, a w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) dla nowo dodanego urządzenia w ciągu około 10 minut zostanie wyświetlony nowy alert.

## <a name="onboard-devices-gradually"></a>Urządzenia na wsadu stopniowo

Jeśli wolisz używać urządzeń w fazach, czyli stopniowo dołączanie *urządzeń, wykonaj* następujące czynności: 

1. Zidentyfikuj zestaw urządzeń do do urządzenia.

2. Przejdź do Microsoft 365 Defender portalu internetowego ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

3. W okienku nawigacji wybierz pozycję **Ustawienia** >  **Endpoints**, a następnie w obszarze **Zarządzanie** urządzeniami wybierz **pozycję Dołączanie**.

4. Wybierz system operacyjny (na przykład Windows 10 **i 11),** a następnie wybierz metodę dołączania (na przykład **skrypt lokalny**). Postępuj zgodnie z dostarczonymi wskazówkami dla wybranej metody.

5. Powtórz tę procedurę dla każdego zestawu urządzeń, które chcesz dodać. 

> [!TIP]
> Nie musisz używać tego samego pakietu dołączania za każdym razem, gdy dodajesz urządzenia. Na przykład możesz użyć skryptu lokalnego, aby dodać niektóre urządzenia, a później możesz wybrać inną metodę, aby dodać więcej urządzeń.

## <a name="offboard-a-device"></a>Odłożanie urządzenia

Jeśli chcesz wyłączyć urządzenie, wykonaj następujące czynności:

1. Przejdź do Microsoft 365 Defender konta ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Ustawienia**, a następnie wybierz **pozycję Punkty końcowe**.

3. W **obszarze Zarządzanie urządzeniami** wybierz pozycję **Wyniesienie**.

4. Wybierz system operacyjny, na przykład Windows 10 i **11**, a następnie w obszarze **Odsuń** urządzenie w sekcji Metoda wdrażania wybierz pozycję  **Skrypt lokalny**. 

5. Na ekranie potwierdzenia przejrzyj informacje, a następnie wybierz pozycję **Pobierz,** aby kontynuować.

6. Wybierz **pozycję Pobierz pakiet wywęszania**. Zalecamy zapisanie pakietu wywrzenia na dysku wymiennym.

7. Uruchom skrypt na każdym urządzeniu, które chcesz wyłączyć. Potrzebujesz pomocy w tym zadaniu? Zobacz następujące zasoby:   

   - Windows urządzenia: [Urządzenia Windows urządzeniach przy użyciu skryptu lokalnego](../security/defender-endpoint/configure-endpoints-script.md#offboard-devices-using-a-local-script)
   
   - Urządzenia z systemem macOS: [Odinstalowywanie w systemie macOS](../security/defender-endpoint/mac-resources.md#uninstalling)

> [!IMPORTANT]
> Wyniesienie urządzenia powoduje zatrzymanie wysyłania danych do usługi Defender dla firm. Jednak dane otrzymane przed wynodaniem są zachowywane przez maksymalnie sześć (6) miesięcy.

## <a name="next-steps"></a>Następne kroki

[Przejrzyj działania naprawcze w programie Microsoft 365 Business Premium](m365bp-review-remediation-actions-devices.md)