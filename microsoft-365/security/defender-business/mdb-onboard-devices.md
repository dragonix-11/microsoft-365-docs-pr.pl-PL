---
title: Urządzenia podłączone do Microsoft Defender dla Firm
description: Informacje o opcjach dołączania urządzeń do aplikacji Microsoft Defender dla Firm
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
ms.openlocfilehash: 78a8eaa5a9472a32c9615dfb7c7f5b08afe548ff
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634740"
---
# <a name="onboard-devices-to-microsoft-defender-for-business"></a>Urządzenia podłączone do Microsoft Defender dla Firm

> [!IMPORTANT]
> Microsoft Defender dla Firm jest wprowadzana u [klientów Microsoft 365 Business Premium](../../business-premium/index.md) począwszy od 1 marca 2022 r. Autonomiczna subskrypcja usługi Defender dla firm jest w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, [](https://aka.ms/mdb-preview) którzy zarejestrują się tutaj, aby poprosić o to. Wersja Preview zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać funkcje.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

Dzięki Microsoft Defender dla Firm masz do wyboru kilka opcji dołączania urządzeń firmy. W tym artykule opisano dostępne opcje i opisano sposób działania dołączania.

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">ankietę na temat Microsoft Defender dla Firm</a>. Chcemy ją usłyszeć!
>

## <a name="what-to-do"></a>Co należy zrobić

1. [Zapoznaj się z dostępnymi opcjami dla urządzeń](#device-onboarding-methods) dołączających i wybierz metodę. 

   - [Użyj automatycznego dołączania do Windows urządzeń już zarejestrowanych w Microsoft Endpoint Manager](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager)
   - [Używanie skryptu lokalnego na urządzeniach Windows lub macOS](#local-script-in-defender-for-business)
   - [Korzystanie Microsoft Endpoint Manager, aby korzystać z Windows, macOS lub urządzeń przenośnych](#microsoft-endpoint-manager)

2. [Uruchom test wykrywania](#run-a-detection-test) na nowo Windows urządzeniach.

3. [Zobacz następne kroki](#next-steps). 

Ten artykuł zawiera również informacje na [temat wywłasniania urządzenia](#offboarding-a-device).

## <a name="device-onboarding-methods"></a>Metody dołączania urządzenia

Usługę Defender dla firm udostępnia kilka różnych metod dołączania urządzeń: niezależnie od tego, czy korzystasz już z programu Microsoft Endpoint Manager, czy po prostu chcesz mieć uproszczone środowisko dołączania. Najczęściej używane metody dołączania urządzeń do usługi Defender dla firm to:

- **Automatyczne dołączanie dla** Windows, które są już zarejestrowane w programie Microsoft Endpoint Manager. Automatyczne wniesienie konfiguruje połączenie między usługą Defender dla firm i usługami Microsoft Endpoint Manager, a następnie na urządzeniach Windows z usługą Defender dla firm. Aby użyć tej opcji, urządzenia muszą już być zarejestrowane w Endpoint Manager. Aby dowiedzieć się więcej, [zobacz Automatyczne dołączanie](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager).

- **Skrypt lokalny** do ręcznego dołączania Windows i macOS do programu Defender dla firm. Korzystając ze skryptu lokalnego, można w tym czasie dodać maksymalnie 10 urządzeń. Aby dowiedzieć się więcej, zobacz [Skrypt lokalny w programie Defender dla firm](#local-script-in-defender-for-business).

- **Microsoft Intune** lub **Microsoft Endpoint Manager** na urządzenia Windows, macOS i urządzenia przenośne. Możesz zarejestrować urządzenia w programie Endpoint Manager, a następnie dodać je do usługi Defender dla firm. [Microsoft 365 Business Premium](../../business-premium/index.md) klienci mają [już Microsoft Intune](/mem/intune/fundamentals/what-is-intune) usługę Microsoft Intune i Zarządzanie urządzeniami [i Mobile Zarządzanie urządzeniami](/mem/intune/enrollment/device-enrollment) są teraz częścią Endpoint Manager. Aby użyć tej metody, zobacz [Microsoft Endpoint Manager](#microsoft-endpoint-manager).

> [!IMPORTANT]
> Jeśli coś poszło nie tak i proces dołączania zakończy się niepowodzeniem, [zobacz rozwiązywanie Microsoft Defender dla Firm problemów](mdb-troubleshooting.yml).

## <a name="automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager"></a>Automatyczne dołączanie dla Windows zarejestrowanych w usłudze Microsoft Endpoint Manager

Opcja automatycznego dołączania dotyczy tylko Windows urządzeniach. Automatyczne dołączanie jest dostępne, jeśli są spełnione następujące warunki:

- Przed użyciem usługi Defender dla firm Microsoft Endpoint Manager, Microsoft Intune lub usługi Mobile Zarządzanie urządzeniami (MDM) w firmie Microsoft Intune już używano usługi Microsoft Intune

- Masz już Windows urządzenia zarejestrowane w usłudze Endpoint Manager

Jeśli Windows urządzenia są już zarejestrowane w usłudze Endpoint Manager, program Defender dla firm wykryje je podczas konfigurowania i konfigurowania usługi Defender dla firm. Zostaniesz poproszony(-a) o zastosowanie automatycznego dołączania do wszystkich lub niektórych Windows urządzeniach. Możesz wychować wszystkie Windows urządzenia jednocześnie lub wybrać określone urządzenia, od których chcesz zacząć, a następnie dodać więcej urządzeń później.

> [!TIP]
> Zalecamy wybranie opcji "wszystkie zarejestrowane urządzenia". Dzięki temu po Windows urządzenia w usłudze Endpoint Manager będą automatycznie dołączane do usługi Defender dla firm. Ponadto, jeśli zarządzasz zasadami i ustawieniami zabezpieczeń w aplikacji Endpoint Manager, zalecamy przełączenie się do portalu Microsoft 365 Defender w celu zarządzania urządzeniami, zasadami i ustawieniami. Aby dowiedzieć się więcej, [zobacz Wybieranie miejsca zarządzania zasadami zabezpieczeń i urządzeniami](mdb-configure-security-settings.md#choose-where-to-manage-security-policies-and-devices).

Aby dowiedzieć się więcej o automatycznym dołączaniu, zobacz krok 2 w tece Konfigurowanie konfiguracji przy użyciu [Microsoft Defender dla Firm](mdb-use-wizard.md).

## <a name="local-script-in-defender-for-business"></a>Skrypt lokalny w programie Defender dla firm

Aby w urządzeniach Windows Mac, możesz użyć skryptu lokalnego. Po uruchomieniu skryptu dołączania na urządzeniu tworzy on zaufanie dla programu Azure Active Directory (jeśli jeszcze nie istnieje), rejestruje urządzenie w usłudze Microsoft Endpoint Manager (jeśli nie zostało jeszcze zarejestrowane), a następnie dodaje urządzenie do usługi Defender dla firm. Ta metoda jest przydatna w przypadku urządzeń dołączających do programu Defender dla firm. Możesz wychować do 10 urządzeń jednocześnie.

1. Przejdź do Microsoft 365 Defender portalu internetowego ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Ustawienia** >  **Endpoints**, a następnie w obszarze **Zarządzanie** urządzeniami wybierz **pozycję Dołączanie**.

3. Wybierz system operacyjny, na przykład Windows 10 **i 11** lub **macOS**, a następnie w sekcji **Metoda wdrażania** wybierz pozycję **Skrypt lokalny**. 

4. Wybierz **pozycję Pobierz pakiet dołączający**. Zalecamy zapisanie pakietu dołączania na dysku wymiennym. (Jeśli wybrano **system macOS**, wybierz też pozycję **Pobierz pakiet instalacyjny** i zapisz go na urządzeniu wymiennym).

5. Postępuj zgodnie z wskazówkami w poniższej tabeli:

   | System operacyjny | Procedura |
   |---|---|
   | System Windows | 1. Na Windows wyodrębnij zawartość pakietu konfiguracyjne do lokalizacji, takiej jak folder Pulpit. Plik powinien mieć nazwę `WindowsDefenderATPLocalOnboardingScript.cmd`. <br/><br/>2. Otwórz wiersz polecenia jako administrator.<br/><br/>3. Wpisz lokalizację pliku skryptu. Jeśli na przykład plik został skopiowany do folderu Pulpit, należy wpisać : `%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd`, a następnie nacisnąć klawisz Enter (lub wybrać przycisk **OK**).<br/><br/>4. Po uruchomieniu skryptu przejdź do [tematu Uruchamianie testu wykrywania](#run-a-detection-test). |
   | macOS | 1. Na komputerze Mac zapisz pakiet instalacyjny jako `wdav.pkg` katalog lokalny. <br/><br/>2. Zapisz pakiet dołączający jako `WindowsDefenderATPOnboardingPackage.zip` w tym samym katalogu, który został użyty w pakiecie instalacyjnym. <br/><br/>3. Za pomocą aplikacji Finder przejdź do zapisanego `wdav.pkg` pliku, a następnie otwórz go.<br/><br/>4. Wybierz **pozycję Kontynuuj**, zgadzam się z postanowieniami licencyjnym, a następnie po wyświetleniu monitu wprowadź hasło.<br/><br/>5. Zostanie wyświetlony monit o umożliwienie zainstalowania sterownika firmy Microsoft (zablokowane rozszerzenie systemu lub "Instalacja znajduje się w miejscu" lub obie te metody. Może być zainstalowany sterownik. Aby zezwolić na instalację, wybierz pozycję **Otwórz preferencje zabezpieczeń** lub **Otwórz preferencje** >  **systemoweBłędy & prywatności**, a następnie wybierz pozycję **Zezwalaj**.<br/><br/>6. Użyj następującego polecenia w języku Python w powłoce Bash, aby uruchomić pakiet dołączania: `/usr/bin/python MicrosoftDefenderATPOnboardingMacOs.py`. <br/><br/>7. Aby potwierdzić, że urządzenie jest skojarzone z Twoją firmą, użyj następującego polecenia w języku Python w powłoce Bash: `mdatp health --field org_id`.<br/><br/>8. Jeśli używasz systemu macOS w wersji 10.15 (Catalina) lub nowszej, ujmij program Defender dla firm w zgodę na ochronę Twojego urządzenia. Przejdź do **preferencji** **systemowychBłędzie** >  & **PrivacyPrivacyFull** >  >  **Disk Access**.  Wybierz ikonę kłódki, aby wprowadzić zmiany (w dolnej części okna dialogowego), a następnie wybierz pozycję Microsoft Defender dla Firm (lub Defender for Endpoint, jeśli tak jest). <br/><br/>9. Aby sprawdzić, czy urządzenie jest włozone, użyj następującego polecenia w powłoce Bash: `mdatp health --field real_time_protection_enabled`.    |

## <a name="microsoft-endpoint-manager"></a>Microsoft Endpoint Manager

Jeśli korzystano już z usługi Endpoint Manager (która obejmuje usługi Microsoft Intune i Mobile Zarządzanie urządzeniami), przed zakupem usługi Defender dla firm możesz nadal korzystać z usługi Endpoint Manager, aby korzystać z urządzeń firmowych. Dzięki Endpoint Manager możesz korzystać z komputerów, tabletów i telefonów, w tym urządzeń z systemami iOS i Android.

Zobacz [Rejestracja urządzenia w aplikacji Microsoft Intune](/mem/intune/enrollment/device-enrollment).

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

Urządzenia firmy można wdać w fazy. *To stopniowe dołączanie urządzeń jest nazywane "stopniowe dołączanie"*. 

1. Zidentyfikuj zestaw urządzeń do do urządzenia.

2. Przejdź do Microsoft 365 Defender portalu internetowego ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

3. W okienku nawigacji wybierz pozycję **Ustawienia** >  **Endpoints**, a następnie w obszarze **Zarządzanie** urządzeniami wybierz **pozycję Dołączanie**.

4. Wybierz system operacyjny (na przykład Windows 10 **i 11),** a następnie wybierz metodę dołączania (na przykład **skrypt lokalny**). Postępuj zgodnie z dostarczonymi wskazówkami dla wybranej metody.

5. Powtórz tę procedurę dla każdego zestawu urządzeń, które chcesz dodać. 

> [!TIP]
> Nie musisz używać tego samego pakietu dołączania za każdym razem, gdy dodajesz urządzenia. Na przykład możesz użyć skryptu lokalnego, aby dodać niektóre urządzenia, a później możesz wybrać inną metodę, aby dodać więcej urządzeń.

## <a name="offboarding-a-device"></a>Wyniesanie urządzenia

Jeśli chcesz odechować urządzenie, skorzystaj z jednej z następujących procedur:

| System operacyjny | Procedura |
|---|---|
| System Windows | 1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.<br/><br/>2. W okienku nawigacji **wybierz pozycję Ustawienia**, a następnie wybierz **pozycję Punkty końcowe**.<br/><br/>3. W **obszarze Zarządzanie urządzeniami** wybierz pozycję **Wyniesienie**.<br/><br/>4. Wybierz system operacyjny, na przykład Windows 10 i **11**, **a** następnie w obszarze Odsuń urządzenie w sekcji Metoda wdrażania wybierz pozycję **Skrypt lokalny**. <br/><br/>5. Na ekranie potwierdzenia przejrzyj informacje, a następnie wybierz pozycję **Pobierz** , aby kontynuować.<br/><br/>6. Wybierz **pozycję Pobierz pakiet wywęszania**. Zalecamy zapisanie pakietu wywrzenia na dysku wymiennym.<br/><br/>7. Uruchom skrypt na każdym urządzeniu, które chcesz wystartować.| 
| macOS | 1. Przejdź do **FinderApplications** > . <br/><br/>2. Kliknij prawym przyciskiem myszy ikonę Microsoft Defender dla Firm, a następnie wybierz pozycję **Przenieś do Kosza**. <br/><br/>--- lub --- <br/><br/> Użyj następującego polecenia: `sudo '/Library/Application Support/Microsoft/Defender/uninstall/uninstall'`.|

> [!IMPORTANT]
> Wyniesienie urządzenia powoduje zatrzymanie wysyłania danych do usługi Defender dla firm. Jednak dane otrzymane przed wynodaniem są zachowywane przez maksymalnie sześć (6) miesięcy.

## <a name="next-steps"></a>Następne kroki

Przejdź do:

- [Krok 5. Konfigurowanie ustawień i zasad zabezpieczeń w programie Microsoft Defender dla Firm](mdb-configure-security-settings.md)

- [Wprowadzenie z Microsoft Defender dla Firm](mdb-get-started.md) 
