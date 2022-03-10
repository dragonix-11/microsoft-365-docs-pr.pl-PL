---
title: Urządzenia w programie Microsoft Defender dla firm
description: Dowiedz się więcej o opcjach dołączania urządzeń do usługi Microsoft Defender dla firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/09/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: a078b2a88fdde3af840cff64414fec0a712ae92e
ms.sourcegitcommit: 40f89c46032ea33de25417106f39cbeebef5a049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/10/2022
ms.locfileid: "63419308"
---
# <a name="onboard-devices-to-microsoft-defender-for-business"></a>Urządzenia w programie Microsoft Defender dla firm

> [!IMPORTANT]
> Program Microsoft Defender dla firm jest wprowadzany dla Microsoft 365 Business Premium klientów od 1 marca 2022 r. Autonomiczna subskrypcja usługi Defender dla firm jest w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, [](https://aka.ms/mdb-preview) którzy zarejestrują się tutaj, aby poprosić o to. Wersja Preview zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać funkcje.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

Środowisko dołączania urządzeń w programie Defender dla firm zostało stworzone na podstawie procesów podobnych do tego, co używamy w programie Microsoft Defender for Endpoint. Obejrzyj poniższy klip wideo, aby zobaczyć, jak to działa:<br/><br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

Usługa Microsoft Defender dla firm pozwala wybrać jedną z opcji dołączania urządzeń organizacji. W tym artykule opisano dostępne opcje i opisano sposób działania dołączania.

> [!TIP]
> Aby wyświetlić bardziej szczegółowe informacje na temat dołączania urządzeń w programie Defender dla punktu końcowego, zobacz Urządzenia na urządzeniach na urządzeniach mobilnych [i skonfiguruj program Microsoft Defender na temat możliwości punktu końcowego](../defender-endpoint/onboard-configure.md).

## <a name="what-to-do"></a>Co należy zrobić

1. Zapoznaj się z opcjami [urządzeń dołączających](#device-onboarding-methods) do pracy i wybierz jedną z następujących metod: 

   - [Automatyczne dołączanie dla Windows zarejestrowanych w usłudze Microsoft Endpoint Manager](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager)
   - [Skrypt lokalny dla Windows komputerów Mac i komputerów Mac](#local-script-in-defender-for-business)
   - [Microsoft Endpoint Manager (Microsoft Intune)](#microsoft-endpoint-manager)
   - [Konfiguracja zabezpieczeń programu Microsoft Defender dla firm](#microsoft-defender-for-business-security-configuration)

2. [Uruchom test wykrywania](#run-a-detection-test) dla nowo Windows urządzeniach.

3. [Zobacz następne kroki](#next-steps). 

Ten artykuł zawiera również informacje na temat uruchamiania testu wykrywania [dla Windows urządzeń](#run-a-detection-test) i [Wyzysowania urządzenia](#offboarding-a-device).

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

## <a name="device-onboarding-methods"></a>Metody dołączania urządzenia

W poniższej tabeli opisano najczęściej używane metody dołączania urządzeń do usługi Defender dla firm. 

| Metoda dołączania  | Opis  | System operacyjny |
|---------|---------|---------|
| **Automatyczne dołączanie**<br/>(*dostępne dla klientów, którzy już Microsoft Endpoint Manager*) | *Microsoft 365 Business Premium klienci mają już Microsoft Intune klientów i mogą skorzystać z tej opcji*. Automatyczne wniesienie konfiguruje połączenie między usługą Defender dla firm i usługami Microsoft Endpoint Manager, a następnie na urządzeniach Windows z usługą Defender dla firm. Aby użyć tej opcji, urządzenia muszą już być zarejestrowane w Endpoint Manager.<br/><br/>Aby dowiedzieć się więcej, [zobacz Automatyczne dołączanie](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager). | System Windows |
| **Skrypt lokalny** <br/> | Ta opcja umożliwia ręczne dołączanie poszczególnych urządzeń do programu Defender dla firm. Korzystając ze skryptu lokalnego, można w tym czasie dodać maksymalnie 10 urządzeń.<br/><br/>Aby dowiedzieć się więcej, zobacz [Skrypt lokalny w programie Defender dla firm](#local-script-in-defender-for-business). | System Windows <br/>macOS |
| **Microsoft Intune** lub **Microsoft Endpoint Manager**<br/>(*dostępne dla klientów, którzy Microsoft Intune lub Endpoint Manager*) | [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) zarządzanie [urządzeniami przenośnymi](/mem/intune/enrollment/device-enrollment) są częścią Endpoint Manager. Microsoft 365 Business Premium klienci mają już Microsoft Intune klientów i mogą skorzystać z tej opcji.<br/><br/>Jeśli korzystasz już z usługi Endpoint Manager usługi Defender dla firm, możesz kontynuować korzystanie z usługi Endpoint Manager do korzystania z urządzeń i zarządzania nimi<br/><br/>Aby użyć tej metody, zobacz [Microsoft Endpoint Manager](#microsoft-endpoint-manager). | System Windows <br/>macOS<br/>iOS<br/>System operacyjny Android | 
| **Konfiguracja zabezpieczeń programu Microsoft Defender dla firm** <br/>(*używa portalu Microsoft 365 Defender)* | Aby użyć tej opcji, skonfiguruj pewne ustawienia w celu ułatwienia komunikacji między usługą Defender dla Firm a programem Endpoint Manager. Następnie możesz wnosić urządzenia do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) przy użyciu pakietu, który można pobrać i uruchomić na każdym urządzeniu. Między urządzeniami a usługą Azure AD jest ustanowione zaufanie i zasady zabezpieczeń usługi Defender Azure Active Directory usługi Defender dla firm są wypychane na urządzenia.<br/><br/>Aby dowiedzieć się więcej, zobacz [Konfiguracja zabezpieczeń programu Microsoft Defender dla firm](#microsoft-defender-for-business-security-configuration). | System Windows <br/>macOS |

> [!IMPORTANT]
> Jeśli coś poszło nie tak, a proces dołączania zakończy się niepowodzeniem, zobacz Rozwiązywanie problemów z usługą [Microsoft Defender dla firm](mdb-troubleshooting.yml).

## <a name="automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager"></a>Automatyczne dołączanie dla Windows zarejestrowanych w usłudze Microsoft Endpoint Manager

Opcja automatycznego dołączania dotyczy tylko Windows urządzeniach. Automatyczne dołączanie jest dostępne, jeśli Twoja organizacja używa już usługi Microsoft Endpoint Manager, Microsoft Intune lub Zarządzania urządzeniami przenośnymi (MDM) w usłudze Microsoft Intune przed użyciem programu Defender dla firm i masz już zarejestrowane Windows urządzenia Endpoint Manager. 

Jeśli Windows urządzenia są już zarejestrowane w usłudze Endpoint Manager, program Defender dla firm wykryje je podczas konfigurowania i konfigurowania usługi Defender dla firm. Zostaniesz poproszony(-a) o zastosowanie automatycznego dołączania do wszystkich lub niektórych Windows urządzeniach. Możesz wychować wszystkie Windows urządzenia jednocześnie lub wybrać określone urządzenia, od których chcesz zacząć, a następnie dodać więcej urządzeń później.

Aby dowiedzieć się więcej o automatycznym dołączaniu, zobacz krok 2 w tece [Konfigurowanie usługi Microsoft Defender dla firm](mdb-use-wizard.md) za pomocą kreatora.

## <a name="local-script-in-defender-for-business"></a>Skrypt lokalny w programie Defender dla firm

Aby w urządzeniach Windows Mac, możesz użyć skryptu lokalnego. Po uruchomieniu skryptu dołączania na urządzeniu tworzy on zaufanie dla programu Azure Active Directory (jeśli jeszcze nie istnieje), rejestruje urządzenie w usłudze Microsoft Endpoint Manager (jeśli nie zostało jeszcze zarejestrowane), a następnie dodaje urządzenie do usługi Defender dla firm. Ta metoda jest przydatna w przypadku urządzeń dołączających do programu Defender dla firm. Możesz wychować do 10 urządzeń jednocześnie.

1. Przejdź do Microsoft 365 Defender portalu internetowego ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Ustawienia** >  **Endpoints**, a następnie w obszarze **Zarządzanie** urządzeniami wybierz **pozycję Dołączanie**.

3. Wybierz system operacyjny, na przykład Windows 10 i **11**, **a** następnie w obszarze Na wsadu urządzenia w sekcji Metoda wdrażania  wybierz pozycję **Skrypt lokalny**. 

4. Wybierz **pozycję Pobierz pakiet dołączający**. Zalecamy zapisanie pakietu dołączania na dysku wymiennym.

5. Postępuj zgodnie z wskazówkami w następujących artykułach:

   - Windows urządzenia: Na [urządzeniach Windows korzystające ze skryptu lokalnego](../defender-endpoint/configure-endpoints-script.md#onboard-devices)
   - Urządzenia z systemem macOS: [Ręczne wdrażanie programu Microsoft Defender dla punktu końcowego w systemie macOS](../defender-endpoint/mac-install-manually.md#client-configuration)

## <a name="microsoft-endpoint-manager"></a>Microsoft Endpoint Manager

Jeśli korzystano już z programu Endpoint Manager (który obejmuje usługi Microsoft Intune i zarządzanie urządzeniami przenośnymi), przed zakupem usługi Defender dla firm możesz nadal używać programu Endpoint Manager do wnosnia urządzeń w organizacji. Dzięki Endpoint Manager możesz korzystać z komputerów, tabletów i telefonów, w tym urządzeń z systemami iOS i Android.

Zobacz [Rejestracja urządzenia w aplikacji Microsoft Intune](/mem/intune/enrollment/device-enrollment).

## <a name="microsoft-defender-for-business-security-configuration"></a>Konfiguracja zabezpieczeń programu Microsoft Defender dla firm

> [!NOTE]
> Jeśli już używasz programu Endpoint Manager do zarządzania urządzeniami i zasadami zabezpieczeń, pomiń tę metodę i zobacz, [Microsoft Endpoint Manager](#microsoft-endpoint-manager) inne.

Konfiguracja zabezpieczeń programu Microsoft Defender dla firm została zbudowana z funkcji nazywanej zarządzaniem zabezpieczeniami dla programu [Microsoft Defender for Endpoint (wersja Preview)](/mem/intune/protect/mde-security-integration). Pozwala on na dołączanie urządzeń do usługi Defender dla firm w portalu usługi Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) bez konieczności wcześniejszego wcześniejszego zarejestrowania tych urządzeń w usłudze Microsoft Endpoint Manager usług. 

Ta metoda umożliwia dołączanie urządzeń oraz zarządzanie zasadami oprogramowania antywirusowego i zapory w portalu Microsoft 365 Defender sieci ([https://security.microsoft.com](https://security.microsoft.com)). Oto jak to działa:

1. Pobierasz pakiet dołączający z portalu Microsoft 365 Defender, a następnie uruchamiasz go na swoich urządzeniach, aby na tych urządzeniach do usługi Defender for Business.

2. Uruchomienie pakietu ustanawia zaufanie między każdym urządzeniem (jeśli zaufanie jeszcze nie istnieje) a usługą Azure Active Directory (Azure AD). 

3. Urządzenia komunikują się Endpoint Manager za pomocą usługi Azure AD Identity, a zasady zabezpieczeń w usłudze Defender dla firm są wypychane na urządzenia.

4. Urządzenia i zasady można wyświetlać zarówno w portalu usługi Microsoft 365 Defender, jak i w centrum Endpoint Manager administracyjnego ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)).

Aby użyć tej opcji, należy wcześniej skonfigurować pewne ustawienia. Aby dowiedzieć się więcej, w tym o wymaganiach wstępnych i obsługiwanych systemach operacyjnych, zobacz Zarządzanie programem [Microsoft Defender dla punktu końcowego na urządzeniach z systemem Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration).

## <a name="run-a-detection-test"></a>Uruchamianie testu wykrywania

Po włoceniu innych urządzeń Windows do usługi Defender dla firm możesz uruchomić test wykrywania na urządzeniu z systemem Windows, aby upewnić się, że wszystko działa poprawnie.

1. Na Windows utwórz folder: `C:\test-MDATP-test`.

2. Otwórz wiersz polecenia jako administrator.

3. W oknie Wiersz polecenia uruchom następujące polecenie programu PowerShell:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Po uruchomieniu polecenia okno Wiersz polecenia zostanie zamknięte automatycznie. Jeśli wykrywanie zakończy się pomyślnie, test wykrywania zostanie oznaczony jako ukończony, a w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) dla nowo dodanego urządzenia w ciągu około 10 minut zostanie wyświetlony nowy alert.

## <a name="gradual-device-onboarding"></a>Stopniowe dołączanie urządzeń

Urządzenia organizacji można dołączać w fazach. *To stopniowe dołączanie urządzeń jest nazywane "stopniowe dołączanie"*. 

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

7. Uruchom skrypt na każdym urządzeniu, które chcesz wyłączyć. Potrzebujesz pomocy w tym zadaniu? Zobacz następujące zasoby:   

   - Windows urządzenia: [Urządzenia Windows urządzeniach przy użyciu skryptu lokalnego](../defender-endpoint/configure-endpoints-script.md#offboard-devices-using-a-local-script)
   - Urządzenia z systemem macOS: [Odinstalowywanie w systemie macOS](../defender-endpoint/mac-resources.md#uninstalling)

> [!IMPORTANT]
> Wyniesienie urządzenia powoduje zatrzymanie wysyłania danych do usługi Defender dla firm. Jednak dane otrzymane przed wynodaniem są zachowywane przez maksymalnie sześć (6) miesięcy.

## <a name="next-steps"></a>Następne kroki

Przejdź do:

- [Krok 5. Konfigurowanie ustawień i zasad zabezpieczeń w programie Microsoft Defender dla firm](mdb-configure-security-settings.md)

- [Wprowadzenie do korzystania z usługi Microsoft Defender dla firm](mdb-get-started.md) 
