---
title: Urządzenia w programie Microsoft Defender dla firm (wersja Preview)
description: Dowiedz się więcej o opcjach dołączania urządzeń w programie Microsoft Defender dla firm (wersja Preview)
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/16/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 073478300e6b5a9d5a9fc10e634f6e3113897fb3
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2022
ms.locfileid: "63014833"
---
# <a name="onboard-devices-to-microsoft-defender-for-business-preview"></a>Urządzenia w programie Microsoft Defender dla firm (wersja Preview)

> [!IMPORTANT]
> Usługa Microsoft Defender dla firm jest teraz w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, którzy zarejestrują się tutaj [, aby](https://aka.ms/mdb-preview) poprosić o to. W najbliższych tygodniach nawiązemy wstępną ofertę klientów i partnerów oraz rozszerzymy jej wersja zapoznawczą, aby rozszerzyć jej dostępność do ogólnej dostępności. Pamiętaj, że wersja Preview zostanie uruchamiana z [początkowym zestawem scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a funkcje będą regularnie dodajemy.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

Środowisko dołączania urządzeń w programie Defender dla firm zostało zbudowane na tych samych procesach dołączania urządzeń, które są używane w programie Microsoft Defender for Endpoint. Obejrzyj poniższy klip wideo, aby zobaczyć, jak to działa:<br/><br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

Usługa Microsoft Defender dla firm (w wersji Preview) pozwala wybrać jedną z opcji dołączania do urządzeń organizacji. W tym artykule opisano dostępne opcje i opisano sposób działania dołączania.

> [!TIP]
> Aby wyświetlić bardziej szczegółowe informacje na temat dołączania urządzeń w programie Defender dla punktu końcowego, zobacz Urządzenia na urządzeniach na urządzeniach mobilnych [i skonfiguruj program Microsoft Defender na temat możliwości punktu końcowego](../defender-endpoint/onboard-configure.md).

## <a name="what-to-do"></a>Co należy zrobić

1. Zapoznaj się z dostępnymi opcjami [dla urządzeń dołączających](#device-onboarding-methods).

2. Na urządzeniu można wdychać je przy użyciu jednej z następujących metod:
    - [Automatyczne dołączanie dla Windows zarejestrowanych w usłudze Microsoft Endpoint Manager](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager)
    - [Lokalny skrypt dla Windows, macOS i Linux](#onboard-devices-using-a-local-script-in-defender-for-business)
    - [Microsoft Endpoint Manager komputerów, tabletów i telefonów](#onboard-devices-using-microsoft-endpoint-manager)
    - [zasady grupy dla Windows urządzeń](#onboard-windows-devices-using-group-policy)
    - [Inna metoda, która nie została tutaj wymieniona](#onboard-devices-using-a-method-not-listed-here)

3. [Uruchom test wykrywania](#run-a-detection-test) dla nowo Windows urządzeniach.

4. [Zobacz następne kroki](#next-steps). 

Ten artykuł zawiera również informacje na [temat wywłasniania urządzenia](#offboarding-a-device).

## <a name="device-onboarding-methods"></a>Metody dołączania urządzenia

W poniższej tabeli opisano najczęściej używane metody dołączania urządzeń do usługi Defender dla firm. 

| Metoda dołączania  | Opis  |
|---------|---------|
| **Automatyczne dołączanie**<br/>(*dostępne dla klientów, którzy już Microsoft Endpoint Manager*) | Automatyczne wniesienie konfiguruje połączenie między usługą Defender dla firm (wersja Preview) i Microsoft Endpoint Manager, a następnie na urządzeniach Windows Defender dla firm (wersja Preview). Urządzenia muszą już być zarejestrowane w programie Endpoint Manager.<br/><br/>Aby dowiedzieć się więcej, [zobacz Używanie automatycznego wnoszania na Windows urządzeniach zarejestrowanych w Microsoft Endpoint Manager](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager). |
| **Skrypt lokalny**<br/>(*zalecane podczas wyświetlania podglądu; przydatne do dołączania kilku urządzeń jednocześnie*)  | Komputery można uruchamiać w programie Defender dla firm (wersja Preview) za pomocą skryptu, który można pobrać i uruchomić na Windows, macOS lub Linux. Skrypt konfiguruje zaufanie dla Azure Active Directory i rejestruje urządzenie.<br/><br/>Aby użyć tej metody, zobacz [Używanie skryptu lokalnego na urządzeniach w programie Defender dla firm](#onboard-devices-using-a-local-script-in-defender-for-business). |
| **Microsoft Intune** lub **Microsoft Endpoint Manager**<br/>(*dostępne dla klientów, którzy już Microsoft Intune lub Endpoint Manager*) | [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) zarządzanie [urządzeniami przenośnymi](/mem/intune/enrollment/device-enrollment) są częścią Endpoint Manager. Jeśli używasz już programu Endpoint Manager przed użyciem programu Defender dla firm (wersja Preview), możesz nadal używać programu Endpoint Manager do korzystania z urządzeń i zarządzania nimi<br/><br/>Aby użyć tej metody, zobacz [Urządzenia w urządzeniach w urządzeniu Microsoft Endpoint Manager](#onboard-devices-using-microsoft-endpoint-manager). |
| **zasady grupy** | Jeśli Twoja organizacja już korzysta z usługi zasady grupy, możesz tworzyć grupy gpOs i stosować je do urządzeń organizacji w programie Defender dla firm (wersja Preview).<br/><br/>Aby dowiedzieć się więcej o tej metodzie, zobacz [Na urządzeniach Windows urządzeniach korzystających z zasady grupy](#onboard-windows-devices-using-group-policy). | 

> [!IMPORTANT]
> Jeśli coś poszło nie tak, a proces dołączania zakończy się niepowodzeniem, zobacz Rozwiązywanie problemów z usługą [Microsoft Defender dla firm](mdb-troubleshooting.yml).

## <a name="automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager"></a>Automatyczne dołączanie dla Windows zarejestrowanych w usłudze Microsoft Endpoint Manager

Opcja automatycznego dołączania dotyczy tylko Windows urządzeniach. Ta opcja jest dostępna, jeśli Twoja organizacja używa już usługi Microsoft Endpoint Manager, Microsoft Intune lub zarządzania urządzeniami przenośnymi (MDM) w usłudze Microsoft Intune przed użyciem programu Defender dla firm (wersja Preview), Windows masz już zarejestrowane urządzenia Endpoint Manager. 

Jeśli Windows urządzenia są już zarejestrowane w usłudze Endpoint Manager, program Defender dla firm wykryje je podczas konfigurowania i konfigurowania usługi Defender dla firm. Zostaniesz poproszony(-a) o zastosowanie automatycznego dołączania do wszystkich lub niektórych Windows urządzeniach. 

Proces automatycznego dołączania konfiguruje połączenie między programem Defender dla firm i programem Endpoint Manager, a następnie dołącza urządzenia do usługi Defender dla firm. Możesz zdecydować się na włogę wszystkich zarejestrowanych Windows urządzeniach jednocześnie lub wybrać zestaw urządzeń Windows do donia.

Aby dowiedzieć się więcej, zobacz krok 3 w [tece Konfigurowanie programu Microsoft Defender dla firm (wersja Preview](mdb-use-wizard.md)) za pomocą kreatora.

## <a name="onboard-devices-using-a-local-script-in-defender-for-business"></a>Urządzenia na urządzeniach w programie Defender dla firm korzystające ze skryptu lokalnego

Skrypt lokalny umożliwia dołączanie aplikacji do Windows, macOS i Linux do usługi Defender dla firm. Uruchomienie skryptu dołączania na urządzeniu powoduje utworzenie zaufania za pomocą programu Azure Active Directory, zarejestrowanie urządzenia w programie Microsoft Endpoint Manager i uruchomienie programu Defender dla firm. Ta metoda jest przydatna w przypadku urządzeń dołączających do programu Defender dla firm i dołączania kilku urządzeń jednocześnie.

1. Przejdź do Microsoft 365 Defender portalu internetowego ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Ustawienia** >  **Endpoints**, a następnie w obszarze **Zarządzanie** urządzeniami wybierz **pozycję Dołączanie**.

3. Wybierz system operacyjny, na przykład Windows 10 i **11**, **a** następnie w obszarze Na wsadu urządzenia w sekcji Metoda wdrażania  wybierz pozycję **Skrypt lokalny**. 

4. Wybierz **pozycję Pobierz pakiet dołączający**. Zalecamy zapisanie pakietu dołączania na dysku wymiennym.

5. Postępuj zgodnie z wskazówkami w następujących artykułach:

   - Windows urządzenia: Na [urządzeniach Windows korzystające ze skryptu lokalnego](../defender-endpoint/configure-endpoints-script.md#onboard-devices)
   - Urządzenia z systemem macOS: [Ręczne wdrażanie programu Microsoft Defender dla punktu końcowego w systemie macOS](../defender-endpoint/mac-install-manually.md#client-configuration)
   - Urządzenia z systemem Linux: [Ręczne wdrażanie programu Microsoft Defender dla punktu końcowego w systemie Linux](../defender-endpoint/linux-install-manually.md#client-configuration)

> [!IMPORTANT]
> Jeśli coś poszło nie tak i proces dołączania zakończy się niepowodzeniem, zobacz Rozwiązywanie problemów z usługą [Microsoft Defender dla firm (wersja Preview](mdb-troubleshooting.yml)).

## <a name="onboard-devices-using-microsoft-endpoint-manager"></a>Urządzenia w urządzeniach w urządzeniu Microsoft Endpoint Manager

Jeśli korzystano już z programu Microsoft Intune przed uzyskaniem programu Defender dla firm (wersja Preview), możesz nadal używać programu Microsoft Intune urządzeniach. Dzięki Endpoint Manager możesz korzystać z komputerów, tabletów i telefonów. 

Zobacz [Rejestracja urządzenia w aplikacji Microsoft Intune](/mem/intune/enrollment/device-enrollment).

## <a name="onboard-windows-devices-using-group-policy"></a>Na urządzeniach Windows przy użyciu aplikacji zasady grupy

[zasady grupy](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831791(v=ws.11)) infrastruktury, która umożliwia określenie konfiguracji zarządzanych dla użytkowników i komputerów za pomocą zasady grupy konfiguracji i preferencji zasady grupy użytkowników. Obiekt zasady grupy to obiekt logiczny składający się z zasady grupy projektu i zasady grupy szablonu. 

Jeśli Twoja organizacja już używa programu zasady grupy do zarządzania urządzeniami, możesz używać aplikacji zasady grupy urządzenia do usługi Defender dla firm. Jeśli nie masz jeszcze danych zasady grupy, zalecamy użycie innej metody, na przykład Endpoint Manager skryptu lokalnego. 

Zobacz [Urządzenia Windows urządzeniach przy użyciu zasady grupy](../defender-endpoint/configure-endpoints-gp.md).

## <a name="onboard-devices-using-a-method-not-listed-here"></a>Urządzenia w tablicach w przypadku użycia metody, która nie została wymieniona w tym miejscu

Jeśli chcesz używać innej metody, której nie wymieniono w tym artykule, do korzystania z urządzeń na urządzeniach, zobacz Opcje narzędzia do dołączania [i konfiguracji](../defender-endpoint/onboard-configure.md#onboarding-and-configuration-tool-options).

## <a name="run-a-detection-test"></a>Uruchamianie testu wykrywania

Po włoceniu urządzeń z systemem Windows do programu Defender dla firm (wersja Preview) możesz uruchomić test wykrywania na urządzeniu z systemem Windows, aby upewnić się, że wszystko działa poprawnie.

1. Na Windows utwórz folder: `C:\test-MDATP-test`.

2. Otwórz wiersz polecenia jako administrator.

3. W oknie Wiersz polecenia uruchom następujące polecenie programu PowerShell:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Po uruchomieniu polecenia okno Wiersz polecenia zostanie zamknięte automatycznie. Jeśli wykrywanie zakończy się pomyślnie, test wykrywania zostanie oznaczony jako ukończony, a w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) dla nowo dodanego urządzenia w ciągu około 10 minut zostanie wyświetlony nowy alert.

## <a name="gradual-device-onboarding"></a>Stopniowe dołączanie urządzeń

Jeśli chcesz dodać urządzenia organizacji w fazach, wykonaj następujące czynności:

1. Zidentyfikuj zestaw urządzeń do do urządzenia.

2. Przejdź do Microsoft 365 Defender portalu internetowego ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

3. W okienku nawigacji wybierz pozycję **Ustawienia** >  **Endpoints**, a następnie w obszarze **Zarządzanie** urządzeniami wybierz **pozycję Dołączanie**.

4. Wybierz system operacyjny (na przykład Windows 10 **i 11),** a następnie wybierz metodę dołączania (na przykład **skrypt lokalny**). Postępuj zgodnie z dostarczonymi wskazówkami dla wybranej metody.

5. Powtórz tę procedurę dla każdego zestawu urządzeń, które chcesz dodać. 

> [!TIP]
> Nie musisz używać tego samego pakietu dołączania za każdym razem, gdy dodajesz urządzenia. Na przykład możesz użyć skryptu lokalnego, aby dodać niektóre urządzenia, a później możesz wybrać inną metodę, aby dodać więcej urządzeń.

## <a name="offboarding-a-device"></a>Wyniesanie urządzenia

Jeśli chcesz wyłączyć urządzenie, wykonaj następujące czynności:

1. Przejdź do Microsoft 365 Defender konta ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Ustawienia**, a następnie wybierz **pozycję Punkty końcowe**.

3. W **obszarze Zarządzanie urządzeniami** wybierz pozycję **Wyniesienie**.

4. Wybierz system operacyjny, na przykład Windows 10 i **11**, a następnie w obszarze **Odsuń** urządzenie w sekcji Metoda wdrażania wybierz pozycję  **Skrypt lokalny**. 

5. Na ekranie potwierdzenia przejrzyj informacje, a następnie wybierz pozycję **Pobierz,** aby kontynuować.

6. Wybierz **pozycję Pobierz pakiet wywęszania**. Zalecamy zapisanie pakietu wywrzenia na dysku wymiennym.

7. Uruchom skrypt na każdym urządzeniu, które chcesz wyłączyć. 

   Potrzebujesz pomocy w tym zadaniu? Zobacz następujące zasoby:   

   - Windows urządzenia: [Urządzenia Windows urządzeniach przy użyciu skryptu lokalnego](../defender-endpoint/configure-endpoints-script.md#offboard-devices-using-a-local-script)
   - Urządzenia z systemem macOS: [Odinstalowywanie w systemie macOS](../defender-endpoint/mac-resources.md#uninstalling)
   - Urządzenia z systemem Linux: [Odinstalowywanie w systemie Linux](../defender-endpoint/linux-resources.md#uninstall)

> [!IMPORTANT]
> Wyniesienie urządzenia powoduje zatrzymanie wysyłania danych do usługi Defender dla firm (wersja Preview). Jednak dane otrzymane przed wynodaniem są zachowywane przez maksymalnie sześć (6) miesięcy.

## <a name="next-steps"></a>Następne kroki

Przejdź do:

- [Krok 5. Konfigurowanie ustawień zabezpieczeń i zasad w programie Microsoft Defender dla firm (wersja Preview)](mdb-configure-security-settings.md)

- [Wprowadzenie do korzystania z usługi Microsoft Defender dla firm (wersja Preview)](mdb-get-started.md) 