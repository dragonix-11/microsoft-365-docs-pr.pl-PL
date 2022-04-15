---
title: Dołączanie urządzeń do Microsoft Defender dla Firm
description: Dowiedz się więcej o opcjach dołączania urządzeń w Microsoft Defender dla Firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/14/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: ba816430521db2848273a4f7c6ca7d1a61703690
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862289"
---
# <a name="onboard-devices-to-microsoft-defender-for-business"></a>Dołączanie urządzeń do Microsoft Defender dla Firm

> [!NOTE]
> Microsoft Defender dla Firm jest teraz uwzględniony w [Microsoft 365 Business Premium](../../business-premium/index.md). 

Dzięki Microsoft Defender dla Firm masz do wyboru kilka opcji dołączania urządzeń firmy. W tym artykule przedstawiono opcje i omówienie sposobu działania dołączania.

>
> **Masz minutę?**
> Weź udział w <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótkiej ankiecie dotyczącej bezpieczeństwa</a>. Chcielibyśmy usłyszeć od Ciebie!
>

## <a name="what-to-do"></a>Co robić

1. Wybierz kartę dla systemu operacyjnego: 

   - klienci Windows
   - serwer Windows (wersja zapoznawcza)
   - Komputery z systemem macOS
   - urządzenia przenośne

2. Wyświetl opcje dołączania i postępuj zgodnie ze wskazówkami na wybranej karcie.

3. Przejdź do kolejnych kroków.

## <a name="windows-clients"></a>[**klienci Windows**](#tab/WindowsClientDevices)

## <a name="windows-clients"></a>klienci Windows

Wybierz jedną z następujących opcji dołączania Windows urządzeń klienckich do usługi Defender dla Firm:

- [Skrypt lokalny](#local-script-for-windows-clients) (do ręcznego dołączania urządzeń w portalu Microsoft 365 Defender)
- [Microsoft Endpoint Manager](#endpoint-manager-for-windows-clients) (zawarte w [Microsoft 365 Business Premium](../../business-premium/index.md))


### <a name="local-script-for-windows-clients"></a>Skrypt lokalny dla klientów Windows

Do dołączania Windows urządzeń klienckich można użyć skryptu lokalnego. Po uruchomieniu skryptu dołączania na urządzeniu tworzy on relację zaufania z Azure Active Directory (jeśli to zaufanie jeszcze nie istnieje), rejestruje urządzenie w Microsoft Endpoint Manager (jeśli nie zostało jeszcze zarejestrowane), a następnie dołącza urządzenie do usługi Defender dla Firm. Lokalna metoda skryptu działa nawet wtedy, gdy obecnie nie masz Endpoint Manager (lub Microsoft Intune). Zalecamy dołączanie maksymalnie 10 urządzeń jednocześnie przy użyciu tej metody.

> [!TIP]
> Zalecamy dołączanie maksymalnie 10 urządzeń w czasie korzystania z lokalnej metody skryptu.

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Ustawienia** >  **Punkty końcowe**, a następnie w obszarze **Zarządzanie urządzeniami** wybierz pozycję **Dołączanie**.

3. Wybierz system operacyjny, taki jak **Windows 10 i 11**, a następnie w sekcji **Metoda wdrażania** wybierz pozycję **Skrypt lokalny**. 

4. Wybierz pozycję **Pobierz pakiet dołączania**. Zalecamy zapisanie pakietu dołączania na dysku wymiennym.

5. Na urządzeniu Windows wyodrębnij zawartość pakietu konfiguracji do lokalizacji, takiej jak folder Desktop. Powinien istnieć plik o nazwie `WindowsDefenderATPLocalOnboardingScript.cmd`. 

6. Otwórz wiersz polecenia jako administrator.

7. Wpisz lokalizację pliku skryptu. Jeśli na przykład plik został skopiowany do folderu Desktop, wpisz `%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd`polecenie , a następnie naciśnij klawisz Enter (lub wybierz przycisk **OK**).

8. Po uruchomieniu skryptu przejdź do [pozycji Uruchom test wykrywania](#running-a-detection-test-on-a-windows-client).

### <a name="endpoint-manager-for-windows-clients"></a>Endpoint Manager dla klientów Windows

Jeśli Twoja subskrypcja obejmuje [Microsoft Endpoint Manager](/mem/endpoint-manager-overview), możesz dołączyć Windows klientów i inne urządzenia w centrum administracyjnym Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). Jeśli na przykład masz [Microsoft 365 Business Premium](../../business/index.yml), masz Endpoint Manager w ramach subskrypcji. Endpoint Manager obejmuje funkcje [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) i [mobile Zarządzanie urządzeniami](/mem/intune/fundamentals/what-is-device-management). 

Istnieje kilka metod rejestrowania urządzeń w Intune. Zalecamy rozpoczęcie od jednej z następujących metod:

- [Włączanie Windows automatycznej rejestracji](/mem/intune/enrollment/windows-enroll) urządzeń należących do firmy lub zarządzanych przez firmę
- [Poproś użytkowników o zarejestrowanie własnych urządzeń Windows 10/11 w Intune](/mem/intune/user-help/enroll-windows-10-device)

#### <a name="to-enable-automatic-enrollment-for-windows-devices"></a>Aby włączyć automatyczną rejestrację dla urządzeń Windows

Podczas konfigurowania rejestracji automatycznej użytkownicy dodają swoje konto służbowe do urządzenia. W tle urządzenie rejestruje i dołącza Azure Active Directory (Azure AD) i jest rejestrowane w Intune.

1. Przejdź do Azure Portal ([https://portal.azure.com/](https://portal.azure.com/)) i zaloguj się. 

2. Wybierz **pozycję Azure Active Directory** >  **Mobilność (MDM i MAM)** > **Microsoft Intune**.

3. Skonfiguruj zakres użytkownika mdm i zakres użytkownika mam.

   :::image type="content" source="media/mem-mam-scope-azure-ad.png" alt-text="Zrzut ekranu przedstawiający ustawianie zakresu użytkownika mdm i zakresu użytkownika mam w Intune.":::

   - W przypadku zakresu użytkownika rozwiązania MDM zalecamy wybranie pozycji **Wszystkie**, aby wszyscy użytkownicy mogli automatycznie rejestrować swoje urządzenia Windows.
   - W sekcji Zakres użytkownika zarządzania aplikacjami mobilnymi zalecamy użycie następujących wartości domyślnych dla adresów URL:

       - **Adres URL Warunków użytkowania zarządzania urządzeniami mobilnymi**
       - **Adres URL odnajdywania zarządzania urządzeniami przenośnymi**
       - **Adres URL zgodności oprogramowania MDM**

4. Wybierz pozycję **Zapisz**.

5. Po zarejestrowaniu urządzenia w Intune możesz dodać je do grupy urządzeń. [Dowiedz się więcej o grupach urządzeń w Microsoft Defender dla Firm](mdb-create-edit-device-groups.md).


> [!TIP]
> Aby dowiedzieć się więcej na temat rejestracji automatycznej, zobacz [Włączanie rejestracji automatycznej Windows](/mem/intune/enrollment/windows-enroll).

#### <a name="to-have-users-enroll-their-own-windows-devices"></a>Aby użytkownicy rejestrowali własne urządzenia Windows

1. Obejrzyj poniższy film wideo, aby zobaczyć, jak działa rejestracja: <br/><br/>

   > [!VIDEO https://www.youtube.com/embed/TKQxEckBHiE?rel=0]  

2. Udostępnij ten artykuł użytkownikom w organizacji: [Rejestrowanie urządzeń Windows 10/11 w Intune](/mem/intune/user-help/enroll-windows-10-device).

3. Po zarejestrowaniu urządzenia w Intune możesz dodać je do grupy urządzeń. [Dowiedz się więcej o grupach urządzeń w Microsoft Defender dla Firm](mdb-create-edit-device-groups.md).

### <a name="running-a-detection-test-on-a-windows-client"></a>Uruchamianie testu wykrywania na kliencie Windows

Po dodaniu urządzeń Windows do usługi Defender dla Firm możesz uruchomić test wykrywania na urządzeniu Windows, aby upewnić się, że wszystko działa poprawnie.

1. Na urządzeniu Windows utwórz folder: `C:\test-MDATP-test`.

2. Otwórz wiersz polecenia jako administrator.

3. W oknie wiersza polecenia uruchom następujące polecenie programu PowerShell:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Po uruchomieniu polecenia okno wiersza polecenia zostanie zamknięte automatycznie. Jeśli test wykrywania zakończy się pomyślnie, zostanie on oznaczony jako ukończony, a nowy alert zostanie wyświetlony w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) dla nowo dołączonego urządzenia w ciągu około 10 minut.

## <a name="view-a-list-of-onboarded-devices"></a>Wyświetlanie listy dołączonych urządzeń

Aby wyświetlić listę urządzeń dołączonych do usługi Defender dla Firm, w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) w okienku nawigacji w obszarze **Punkty końcowe** wybierz pozycję **Invetory urządzenia**.

## <a name="next-steps"></a>Następne kroki

- Jeśli masz inne urządzenia do dołączenia, wybierz kartę odpowiadającą systemowi operacyjnemu na urządzeniach [(Windows klientów, Windows Server, macOS lub urządzenia przenośne](#what-to-do)) i postępuj zgodnie ze wskazówkami na tej karcie.
- Jeśli skończysz dołączać urządzenia, przejdź do [kroku 5. Konfigurowanie ustawień zabezpieczeń i zasad w Microsoft Defender dla Firm](mdb-configure-security-settings.md)
- Zobacz [Wprowadzenie przy użyciu Microsoft Defender dla Firm](mdb-get-started.md).

## <a name="windows-server"></a>[**Windows Server**](#tab/WindowsServerEndpoints)

## <a name="windows-server-preview"></a>serwer Windows (wersja zapoznawcza)

Urządzenie Windows Server można dołączyć przy użyciu skryptu lokalnego. 

> [!IMPORTANT]
> Możliwość dołączania punktów końcowych serwera Windows jest obecnie dostępna w wersji zapoznawczej.

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Ustawienia** >  **Punkty końcowe**, a następnie w obszarze **Zarządzanie urządzeniami** wybierz pozycję **Dołączanie**.

3. Wybierz system operacyjny, taki jak **Windows Server 1803, 2019 i 2022**, a następnie w sekcji **Metoda wdrażania** wybierz pozycję **Skrypt lokalny**. 

   Jeśli wybierzesz **Windows Server 2012 R2 i 2016**, będziesz mieć dwa pakiety do pobrania i uruchomienia: pakiet instalacyjny i pakiet dołączania. Pakiet instalacyjny zawiera plik MSI, który instaluje agenta Microsoft Defender dla Firm. Pakiet dołączania zawiera skrypt dołączania punktu końcowego Windows Server do usługi Defender for Business. 

4. Wybierz pozycję **Pobierz pakiet dołączania**. Zalecamy zapisanie pakietu dołączania na dysku wymiennym.

   Jeśli wybrano **opcje Windows Server 2012 R2 i 2016**, wybierz również pozycję **Pobierz pakiet instalacyjny** i zapisz go na dysku wymiennym

5. W punkcie końcowym serwera Windows wyodrębnij zawartość pakietów instalacyjnych/dołączających do lokalizacji, takiej jak folder Desktop. Powinien istnieć plik o nazwie `WindowsDefenderATPLocalOnboardingScript.cmd`. 

   Jeśli dołączasz Windows Server 2012 R2 lub Windows Server 2016, najpierw wyodrębnij pakiet instalacyjny.

6. Otwórz wiersz polecenia jako administrator.

7. Jeśli dołączasz Windows Server 2012R2 lub Windows Server 2016, uruchom następujące polecenie: `Msiexec /i md4ws.msi /quiet`. 

   Jeśli dołączasz Windows Server 1803, 2019 lub 2022, pomiń ten krok i przejdź do kroku 8.

8. Wpisz lokalizację pliku skryptu. Jeśli na przykład plik został skopiowany do folderu Desktop, wpisz `%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd`polecenie , a następnie naciśnij klawisz Enter (lub wybierz przycisk **OK**).

9. Kontynuuj [uruchamianie testu wykrywania na serwerze Windows](#running-a-detection-test-on-windows-server)

### <a name="running-a-detection-test-on-windows-server"></a>Uruchamianie testu wykrywania na serwerze Windows

Po dodaniu punktu końcowego serwera Windows do usługi Defender dla Firm możesz uruchomić test wykrywania, aby upewnić się, że wszystko działa prawidłowo.

1. Na urządzeniu Windows Server utwórz folder: `C:\test-MDATP-test`.

2. Otwórz wiersz polecenia jako administrator.

3. W oknie wiersza polecenia uruchom następujące polecenie programu PowerShell:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Po uruchomieniu polecenia okno wiersza polecenia zostanie zamknięte automatycznie. Jeśli test wykrywania zakończy się pomyślnie, zostanie on oznaczony jako ukończony, a nowy alert zostanie wyświetlony w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) dla nowo dołączonego urządzenia w ciągu około 10 minut.

## <a name="view-a-list-of-onboarded-devices"></a>Wyświetlanie listy dołączonych urządzeń

Aby wyświetlić listę urządzeń dołączonych do usługi Defender dla Firm, w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) w okienku nawigacji w obszarze **Punkty końcowe** wybierz pozycję **Invetory urządzenia**.

## <a name="next-steps"></a>Następne kroki

- Jeśli masz inne urządzenia do dołączenia, wybierz kartę odpowiadającą systemowi operacyjnemu na urządzeniach [(Windows klientów, Windows Server, macOS lub urządzenia przenośne](#what-to-do)) i postępuj zgodnie ze wskazówkami na tej karcie.
- Jeśli skończysz dołączać urządzenia, przejdź do [kroku 5. Konfigurowanie ustawień zabezpieczeń i zasad w Microsoft Defender dla Firm](mdb-configure-security-settings.md)
- Zobacz [Wprowadzenie przy użyciu Microsoft Defender dla Firm](mdb-get-started.md).

## <a name="macos"></a>[**macOS**](#tab/macOSdevices)

## <a name="macos-computers"></a>Komputery z systemem macOS

> [!NOTE]
> - Zalecamy używanie [skryptu lokalnego do dołączania urządzeń z systemem macOS](#local-script-for-macos). Chociaż [rejestrację dla urządzeń z systemem macOS można skonfigurować w Intune](/mem/intune/enrollment/macos-enroll), skrypt lokalny jest najprostszą metodą dołączania urządzeń z systemem macOS do usługi Defender for Business. 

Wybierz jedną z następujących opcji dołączania urządzeń z systemem macOS:

- [Skrypt lokalny dla systemu macOS](#local-script-for-macos) (*zalecane*)
- [Endpoint Manager dla systemu macOS](#endpoint-manager-for-macos)

### <a name="local-script-for-macos"></a>Skrypt lokalny dla systemu macOS

Po uruchomieniu skryptu lokalnego na urządzeniu z systemem macOS tworzy on relację zaufania z Azure Active Directory (jeśli to zaufanie jeszcze nie istnieje), rejestruje urządzenie w Microsoft Endpoint Manager (jeśli nie zostało jeszcze zarejestrowane), a następnie dołącza urządzenie do usługi Defender dla Firm. Lokalna metoda skryptu działa nawet wtedy, gdy obecnie nie masz Endpoint Manager (lub Microsoft Intune). Zalecamy dołączanie maksymalnie 10 urządzeń jednocześnie przy użyciu tej metody.

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Ustawienia** >  **Punkty końcowe**, a następnie w obszarze **Zarządzanie urządzeniami** wybierz pozycję **Dołączanie**.

3. Wybierz pozycję **macOS**, a następnie w sekcji **Metoda wdrażania** wybierz pozycję **Skrypt lokalny**. 

4. Wybierz pozycję **Pobierz pakiet dołączania** i zapisz go na dysku wymiennym. Wybierz również pozycję **Pobierz pakiet instalacyjny** i zapisz go na urządzeniu wymiennym.

5. Na urządzeniu z systemem macOS zapisz pakiet instalacyjny jako `wdav.pkg` w katalogu lokalnym.

6. Zapisz pakiet dołączania w `WindowsDefenderATPOnboardingPackage.zip` tym samym katalogu, który był używany dla pakietu instalacyjnego.

7. Użyj narzędzia Finder, aby przejść do `wdav.pkg` zapisanego obszaru, a następnie otworzyć go.

8. Wybierz pozycję **Kontynuuj**, zaakceptuj postanowienia licencyjne, a następnie wprowadź hasło po wyświetleniu monitu.

9. Zostanie wyświetlony monit o zezwolenie na zainstalowanie sterownika firmy Microsoft ("Zablokowane rozszerzenie systemu" lub "Instalacja jest wstrzymana" lub oba te elementy. Należy zezwolić na instalację sterownika. Aby zezwolić na instalację, wybierz pozycję **Otwórz preferencje zabezpieczeń** lub **Otwórz preferencje systemoweZabezpieczenia** >  **& prywatności**, a następnie wybierz pozycję **Zezwalaj**.

10. Użyj następującego polecenia języka Python w programie Bash, aby uruchomić pakiet dołączania: `/usr/bin/python MicrosoftDefenderATPOnboardingMacOs.py`

11. Po zarejestrowaniu urządzenia w Intune możesz dodać je do grupy urządzeń. [Dowiedz się więcej o grupach urządzeń w Microsoft Defender dla Firm](mdb-create-edit-device-groups.md).

### <a name="endpoint-manager-for-macos"></a>Endpoint Manager dla systemu macOS

Jeśli Twoja subskrypcja obejmuje [Microsoft Endpoint Manager](/mem/endpoint-manager-overview), możesz dołączyć urządzenia z systemem macOS w centrum administracyjnym Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). Jeśli na przykład masz [Microsoft 365 Business Premium](../../business/index.yml), masz Endpoint Manager w ramach subskrypcji. Endpoint Manager obejmuje funkcje [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) i [mobile Zarządzanie urządzeniami](/mem/intune/fundamentals/what-is-device-management). 

Istnieje kilka metod rejestrowania urządzeń w Intune. Zalecamy rozpoczęcie od jednej z następujących metod:

- [Wybierz opcję dla firmowych urządzeń z systemem macOS](#options-for-company-owned-macos-devices)
- [Poproś użytkowników o zarejestrowanie własnych urządzeń z systemem macOS w Intune](#ask-users-to-enroll-their-own-macos-devices-in-intune)

#### <a name="options-for-company-owned-macos-devices"></a>Opcje dla firmowych urządzeń z systemem macOS

Wybierz jedną z opcji w poniższej tabeli, aby zarejestrować urządzenia z systemem macOS zarządzane przez firmę w Intune:

| Opcja  | Opis  |
|---------|---------|
| Automatyczna rejestracja urządzeń firmy Apple |  Ta metoda służy do automatyzowania środowiska rejestracji na urządzeniach zakupionych za pośrednictwem programu Apple Business Manager lub Apple School Manager. Automatyczna rejestracja urządzeń wdraża profil rejestracji na antenie, dzięki czemu nie trzeba mieć fizycznego dostępu do urządzeń. <br/><br/>Zobacz [Automatyczne rejestrowanie urządzeń z systemem macOS przy użyciu programu Apple Business Manager lub Apple School Manager](/mem/intune/enrollment/device-enrollment-program-enroll-macos). |
| Menedżer rejestracji urządzeń (DEM)  |  Użyj tej metody w przypadku wdrożeń na dużą skalę i gdy w organizacji jest wiele osób, które mogą pomóc w konfiguracji rejestracji. Osoba z uprawnieniami menedżera rejestracji urządzeń (DEM) może zarejestrować maksymalnie 1000 urządzeń przy użyciu jednego konta Azure Active Directory. Ta metoda używa aplikacji Portal firmy lub aplikacji Microsoft Intune do rejestrowania urządzeń. Nie można użyć konta DEM do rejestrowania urządzeń za pośrednictwem zautomatyzowanej rejestracji urządzeń.<br/><br/> Zobacz [Rejestrowanie urządzeń w Intune przy użyciu konta menedżera rejestracji urządzeń](/mem/intune/enrollment/device-enrollment-manager-enroll).  |
| Rejestracja bezpośrednia  | Rejestracja bezpośrednia rejestruje urządzenia bez koligacji użytkownika, dlatego ta metoda jest najlepsza w przypadku urządzeń, które nie są skojarzone z jednym użytkownikiem. Ta metoda wymaga fizycznego dostępu do zarejestrowanych komputerów Mac. <br/><br/>Zobacz [Używanie rejestracji bezpośredniej dla urządzeń z systemem macOS](/mem/intune/enrollment/device-enrollment-direct-enroll-macos).      |

#### <a name="ask-users-to-enroll-their-own-macos-devices-in-intune"></a>Poproś użytkowników o zarejestrowanie własnych urządzeń z systemem macOS w Intune

Jeśli Twoja firma woli, aby osoby rejestrowały własne urządzenia w Intune, poproś użytkowników, aby postępowali zgodnie z następującymi krokami:

1. Przejdź do witryny internetowej Portal firmy ([https://portal.manage.microsoft.com/](https://portal.manage.microsoft.com/)) i zaloguj się.

2. Postępuj zgodnie z instrukcjami w witrynie internetowej Portal firmy, aby dodać swoje urządzenie.

3. Zainstaluj aplikację Portal firmy pod adresem [https://aka.ms/EnrollMyMac](https://aka.ms/EnrollMyMac)i postępuj zgodnie z instrukcjami w aplikacji.

### <a name="confirm-that-a-macos-device-is-onboarded"></a>Upewnij się, że urządzenie z systemem macOS jest dołączone

1. Aby potwierdzić, że urządzenie jest skojarzone z Firmą, użyj następującego polecenia języka Python w powłoki Bash: `mdatp health --field org_id`.

2. Jeśli używasz systemu macOS 10.15 (Catalina) lub nowszego, przyznaj usłudze Defender for Business zgodę na ochronę urządzenia. Przejdź do **obszaru Preferencje** **systemoweZabezpieczenia** >  & **prywatnośćPrivacyDywatny** >  >  **dostęp do dysku**. Wybierz ikonę blokady, aby wprowadzić zmiany (u dołu okna dialogowego), a następnie wybierz pozycję **Microsoft Defender dla Firm** (lub **Defender for Endpoint**, jeśli to właśnie widzisz).

3. Aby sprawdzić, czy urządzenie jest dołączone, użyj następującego polecenia w powłoki Bash: `mdatp health --field real_time_protection_enabled`

4. Po zarejestrowaniu urządzenia w Intune możesz dodać je do grupy urządzeń. [Dowiedz się więcej o grupach urządzeń w Microsoft Defender dla Firm](mdb-create-edit-device-groups.md).

## <a name="view-a-list-of-onboarded-devices"></a>Wyświetlanie listy dołączonych urządzeń

Aby wyświetlić listę urządzeń dołączonych do usługi Defender dla Firm, w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) w okienku nawigacji w obszarze **Punkty końcowe** wybierz pozycję **Spis urządzeń**.

## <a name="next-steps"></a>Następne kroki

- Jeśli masz inne urządzenia do dołączenia, wybierz kartę odpowiadającą systemowi operacyjnemu na urządzeniach ([Windows klientów, Windows Server, macOS lub urządzenia przenośne](#what-to-do)) i postępuj zgodnie ze wskazówkami na tej karcie.
- Jeśli skończysz dołączać urządzenia, przejdź do [kroku 5. Konfigurowanie ustawień zabezpieczeń i zasad w Microsoft Defender dla Firm](mdb-configure-security-settings.md)
- Zobacz [Wprowadzenie przy użyciu Microsoft Defender dla Firm](mdb-get-started.md).

## <a name="mobile-devices"></a>[**urządzenia przenośne**](#tab/mobiles)

## <a name="mobile-devices"></a>Urządzenia przenośne

Musisz Microsoft Intune do dołączania urządzeń przenośnych, takich jak urządzenia z systemem Android i iOS/iPadOS. Jeśli masz [Microsoft 365 Business Premium](../../business/index.yml), masz Endpoint Manager w ramach subskrypcji. Endpoint Manager obejmuje funkcje [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) i [mobile Zarządzanie urządzeniami](/mem/intune/fundamentals/what-is-device-management). 

Zobacz następujące zasoby, aby uzyskać pomoc dotyczącą rejestrowania tych urządzeń w Intune:

- [Rejestrowanie urządzeń z systemem Android](/mem/intune/enrollment/android-enroll)
- [Rejestrowanie urządzeń z systemem iOS lub iPadOS](/mem/intune/enrollment/ios-enroll)

Po zarejestrowaniu urządzenia w Intune możesz dodać je do grupy urządzeń. [Dowiedz się więcej o grupach urządzeń w Microsoft Defender dla Firm](mdb-create-edit-device-groups.md).

## <a name="next-steps"></a>Następne kroki

- Jeśli masz inne urządzenia do dołączenia, wybierz kartę odpowiadającą systemowi operacyjnemu na urządzeniach ([Windows klientów, Windows Server, macOS lub urządzenia przenośne](#what-to-do)) i postępuj zgodnie ze wskazówkami na tej karcie.
- Jeśli skończysz dołączać urządzenia, przejdź do [kroku 5. Konfigurowanie ustawień zabezpieczeń i zasad w Microsoft Defender dla Firm](mdb-configure-security-settings.md)
- Zobacz [Wprowadzenie przy użyciu Microsoft Defender dla Firm](mdb-get-started.md).
