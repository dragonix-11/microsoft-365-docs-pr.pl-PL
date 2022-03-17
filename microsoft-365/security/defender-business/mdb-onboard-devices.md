---
title: Urządzenia w programie Microsoft Defender dla firm
description: Dowiedz się więcej o opcjach dołączania urządzeń do usługi Microsoft Defender dla firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 590810e7e8a5486816310da35968d6d9b3659330
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63525335"
---
# <a name="onboard-devices-to-microsoft-defender-for-business"></a>Urządzenia w programie Microsoft Defender dla firm

> [!IMPORTANT]
> Program Microsoft Defender dla firm jest wprowadzany [dla Microsoft 365 Business Premium](../../business-premium/index.md) klientów od 1 marca 2022 r. Autonomiczna subskrypcja usługi Defender dla firm jest w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, [](https://aka.ms/mdb-preview) którzy zarejestrują się tutaj, aby poprosić o to. Wersja Preview zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać funkcje.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

Usługa Microsoft Defender dla firm oferuje kilka opcji dołączania urządzeń firmy do wyboru. W tym artykule opisano dostępne opcje i opisano sposób działania dołączania.

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

## <a name="get-the-device-onboarding-guide"></a>Pobierz przewodnik po dołączaniu do urządzenia

Skorzystaj z poniższego przewodnika i informacji, aby wybrać najlepszą opcję dla swojej firmy.

[:::image type="content" source="media/mdb-device-onboarding.png" alt-text="Zrzut ekranu przedstawiający diagram dołączania urządzenia":::](https://download.microsoft.com/download/4/d/2/4d2d8a86-2130-45b4-ba42-2997c854383a/MDB-DeviceOnboardingFlow-March2022.pdf) <br/>
[PDF](https://download.microsoft.com/download/4/d/2/4d2d8a86-2130-45b4-ba42-2997c854383a/MDB-DeviceOnboardingFlow-March2022.pdf) | [Visio](https://download.microsoft.com/download/4/d/2/4d2d8a86-2130-45b4-ba42-2997c854383a/MDB-DeviceOnboardingFlow-March2022.vsdx)

## <a name="what-to-do"></a>Co należy zrobić

1. [Zapoznaj się z dostępnymi opcjami dla urządzeń](#device-onboarding-methods) dołączających i wybierz metodę. 

   - [Użyj automatycznego dołączania do Windows urządzeń już zarejestrowanych w Microsoft Endpoint Manager](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager)
   - [Używanie skryptu lokalnego na urządzeniach Windows lub macOS](#local-script-in-defender-for-business)
   - [Korzystanie Microsoft Endpoint Manager, aby korzystać z Windows, macOS lub urządzeń przenośnych](#microsoft-endpoint-manager)
   - [Dowiedz się więcej o dołączaniu urządzeń za pomocą konfiguracji zabezpieczeń programu Microsoft Defender dla firm](#microsoft-defender-for-business-security-configuration)

2. [Uruchom test wykrywania](#run-a-detection-test) na nowo Windows urządzeniach.

3. [Zobacz następne kroki](#next-steps). 

Ten artykuł zawiera również informacje na [temat wywłasniania urządzenia](#offboarding-a-device).

## <a name="device-onboarding-methods"></a>Metody dołączania urządzenia

Usługę Defender dla firm udostępnia kilka różnych metod dołączania urządzeń: niezależnie od tego, czy korzystasz już z programu Microsoft Endpoint Manager, czy po prostu chcesz mieć uproszczone środowisko dołączania. Najczęściej używane metody dołączania urządzeń do usługi Defender dla firm to:

- **Automatyczne dołączanie dla** Windows, które są już zarejestrowane w programie Microsoft Endpoint Manager. Automatyczne wniesienie konfiguruje połączenie między usługą Defender dla firm i usługami Microsoft Endpoint Manager, a następnie na urządzeniach Windows z usługą Defender dla firm. Aby użyć tej opcji, urządzenia muszą już być zarejestrowane w Endpoint Manager. Aby dowiedzieć się więcej, [zobacz Automatyczne dołączanie](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager).

- **Skrypt lokalny** do ręcznego dołączania Windows i macOS do programu Defender dla firm. Korzystając ze skryptu lokalnego, można w tym czasie dodać maksymalnie 10 urządzeń. Aby dowiedzieć się więcej, zobacz [Skrypt lokalny w programie Defender dla firm](#local-script-in-defender-for-business).

- **Microsoft Intune** lub **Microsoft Endpoint Manager** na urządzenia Windows, macOS i urządzenia przenośne. Możesz zarejestrować urządzenia w programie Endpoint Manager, a następnie dodać je do usługi Defender dla firm. [Microsoft 365 Business Premium](../../business-premium/index.md) klienci mają [już Microsoft Intune usługi](/mem/intune/fundamentals/what-is-intune) i Microsoft Intune zarządzanie urządzeniami przenośnymi są teraz częścią Endpoint Manager.[](/mem/intune/enrollment/device-enrollment) Aby użyć tej metody, zobacz [Microsoft Endpoint Manager](#microsoft-endpoint-manager).

- **Konfiguracja zabezpieczeń programu Microsoft Defender dla firm na** urządzeniach wnoszeniowych bezpośrednio w portalu Microsoft 365 Defender sieci ([https://security.microsoft.com](https://security.microsoft.com)). Aby użyć tej opcji, skonfiguruj pewne ustawienia w celu ułatwienia komunikacji między usługą Defender dla Firm a programem Endpoint Manager. Następnie możesz wnosić urządzenia do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) przy użyciu pakietu, który wybierasz, pobierasz i uruchamiasz na każdym urządzeniu. Między urządzeniami a usługą Azure AD jest ustanowione zaufanie i zasady zabezpieczeń usługi Defender Azure Active Directory usługi Defender dla firm są wypychane na urządzenia. Aby dowiedzieć się więcej, zobacz [Konfiguracja zabezpieczeń programu Microsoft Defender dla firm](#microsoft-defender-for-business-security-configuration). 

> [!IMPORTANT]
> Jeśli coś poszło nie tak, a proces dołączania zakończy się niepowodzeniem, zobacz Rozwiązywanie problemów z usługą [Microsoft Defender dla firm](mdb-troubleshooting.yml).

## <a name="automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager"></a>Automatyczne dołączanie dla Windows zarejestrowanych w usłudze Microsoft Endpoint Manager

Opcja automatycznego dołączania dotyczy tylko Windows urządzeniach. Automatyczne dołączanie jest dostępne, jeśli są spełnione następujące warunki:

- Twoja firma używa już usługi Microsoft Endpoint Manager, Microsoft Intune lub zarządzania urządzeniami przenośnymi (MDM) w programie Microsoft Intune przed zakupem usługi Defender dla firm

- Masz już Windows urządzenia zarejestrowane w usłudze Endpoint Manager

Jeśli Windows urządzenia są już zarejestrowane w usłudze Endpoint Manager, program Defender dla firm wykryje je podczas konfigurowania i konfigurowania usługi Defender dla firm. Zostaniesz poproszony(-a) o zastosowanie automatycznego dołączania do wszystkich lub niektórych Windows urządzeniach. Możesz wychować wszystkie Windows urządzenia jednocześnie lub wybrać określone urządzenia, od których chcesz zacząć, a następnie dodać więcej urządzeń później.

> [!TIP]
> Zalecamy wybranie opcji "wszystkie zarejestrowane urządzenia". Dzięki temu po Windows urządzenia w usłudze Endpoint Manager będą automatycznie dołączane do usługi Defender dla firm. Ponadto, jeśli zarządzasz zasadami i ustawieniami zabezpieczeń w aplikacji Endpoint Manager, zalecamy przełączenie się do portalu Microsoft 365 Defender w celu zarządzania urządzeniami, zasadami i ustawieniami. Aby dowiedzieć się więcej, [zobacz Wybieranie miejsca zarządzania zasadami zabezpieczeń i urządzeniami](mdb-configure-security-settings.md#choose-where-to-manage-security-policies-and-devices).

Aby dowiedzieć się więcej o automatycznym dołączaniu, zobacz krok 2 w tece [Konfigurowanie usługi Microsoft Defender dla firm](mdb-use-wizard.md) za pomocą kreatora.

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
   | macOS | 1. Na komputerze Mac zapisz pakiet instalacyjny jako `wdav.pkg` katalog lokalny. <br/><br/>2. Zapisz pakiet dołączający jako `WindowsDefenderATPOnboardingPackage.zip` w tym samym katalogu, który został użyty w pakiecie instalacyjnym. <br/><br/>3. Za pomocą aplikacji Finder przejdź do zapisanego `wdav.pkg` pliku, a następnie otwórz go.<br/><br/>4. Wybierz **pozycję Kontynuuj**, zgadzam się z postanowieniami licencyjnym, a następnie po wyświetleniu monitu wprowadź hasło.<br/><br/>5. Zostanie wyświetlony monit o umożliwienie zainstalowania sterownika firmy Microsoft (zablokowane rozszerzenie systemu lub "Instalacja znajduje się w miejscu" lub obie te metody. Może być zainstalowany sterownik. Aby zezwolić na instalację, wybierz pozycję **Otwórz preferencje zabezpieczeń** lub **Otwórz preferencje** >  **systemoweBłędy & prywatności**, a następnie wybierz pozycję **Zezwalaj**.<br/><br/>6. Użyj następującego polecenia w języku Python w powłoce Bash, aby uruchomić pakiet dołączania: `/usr/bin/python MicrosoftDefenderATPOnboardingMacOs.py`. <br/><br/>7. Aby potwierdzić, że urządzenie jest skojarzone z Twoją firmą, użyj następującego polecenia w języku Python w powłoce Bash: `mdatp health --field org_id`.<br/><br/>8. Jeśli używasz systemu macOS w wersji 10.15 (Catalina) lub nowszej, ujmij program Defender dla firm w zgodę na ochronę Twojego urządzenia. Przejdź do **preferencji** **systemowychBłędzie** >  & **PrivacyPrivacyFull** >  >  **Disk Access**.  Wybierz ikonę kłódki, aby wprowadzić zmiany (w dolnej części okna dialogowego), a następnie wybierz pozycję Microsoft Defender for Business (lub Defender for Endpoint, jeśli tak jest). <br/><br/>9. Aby sprawdzić, czy urządzenie jest włozone, użyj następującego polecenia w powłoce Bash: `mdatp health --field real_time_protection_enabled`.    |

## <a name="microsoft-endpoint-manager"></a>Microsoft Endpoint Manager

Jeśli korzystano już z programu Endpoint Manager (który obejmuje usługi Microsoft Intune i zarządzanie urządzeniami przenośnymi), przed zakupem usługi Defender dla firm możesz nadal używać programu Endpoint Manager do wnosnia urządzeń firmy. Dzięki Endpoint Manager możesz korzystać z komputerów, tabletów i telefonów, w tym urządzeń z systemami iOS i Android.

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
| macOS | 1. Przejdź do **FinderApplications** > . <br/><br/>2. Kliknij prawym przyciskiem myszy usługę Microsoft Defender for Business, a następnie wybierz **pozycję Przenieś do Kosza**. <br/><br/>--- lub --- <br/><br/> Użyj następującego polecenia: `sudo '/Library/Application Support/Microsoft/Defender/uninstall/uninstall'`.|

> [!IMPORTANT]
> Wyniesienie urządzenia powoduje zatrzymanie wysyłania danych do usługi Defender dla firm. Jednak dane otrzymane przed wynodaniem są zachowywane przez maksymalnie sześć (6) miesięcy.

## <a name="next-steps"></a>Następne kroki

Przejdź do:

- [Krok 5. Konfigurowanie ustawień i zasad zabezpieczeń w programie Microsoft Defender dla firm](mdb-configure-security-settings.md)

- [Wprowadzenie do korzystania z usługi Microsoft Defender dla firm](mdb-get-started.md) 
