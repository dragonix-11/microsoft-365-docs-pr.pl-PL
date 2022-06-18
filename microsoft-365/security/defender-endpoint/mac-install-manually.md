---
title: Ręczne wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender na macOS
description: Zainstaluj Ochrona punktu końcowego w usłudze Microsoft Defender na macOS ręcznie z poziomu wiersza polecenia.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mac, installation, deploy, uninstallation, intune, jamf, macos, catalina, mojave, high sierra
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 68f91e4b8f789087aacea14b6b2a8a8b67262fd0
ms.sourcegitcommit: b0b1be67de8f40b199bb9b51eb3568e59377e93a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2022
ms.locfileid: "66159624"
---
# <a name="manual-deployment-for-microsoft-defender-for-endpoint-on-macos"></a>Ręczne wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender na macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink).

W tym temacie opisano sposób ręcznego wdrażania Ochrona punktu końcowego w usłudze Microsoft Defender na macOS. Pomyślne wdrożenie wymaga wykonania wszystkich następujących kroków:

- [Pobieranie pakietów instalacyjnych i dołączanych](#download-installation-and-onboarding-packages)
- [Instalacja aplikacji (macOS 10.15)](#application-installation-macos-1015)
- [Instalacja aplikacji (macOS 11 i nowszych wersji)](#application-installation-macos-11-and-newer-versions)
- [Konfiguracja klienta](#client-configuration)

## <a name="prerequisites-and-system-requirements"></a>Wymagania wstępne i wymagania systemowe

Przed rozpoczęciem zapoznaj się z [głównym Ochrona punktu końcowego w usłudze Microsoft Defender na stronie macOS](microsoft-defender-endpoint-mac.md), aby zapoznać się z opisem wymagań wstępnych i wymagań systemowych dotyczących bieżącej wersji oprogramowania.

## <a name="download-installation-and-onboarding-packages"></a>Pobieranie pakietów instalacyjnych i dołączanych

Pobierz pakiety instalacyjne i dołączające z portalu Microsoft 365 Defender:

1. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a> przejdź do **obszaru Ustawienia > Endpoints > Device management > Onboarding (Punkty końcowe > Dołączanie do zarządzania urządzeniami**).
2. W sekcji 1 strony ustaw system operacyjny na **macOS**, a metodę wdrożenia na **skrypt lokalny**.
3. W sekcji 2 strony wybierz pozycję **Pobierz pakiet instalacyjny**. Zapisz go jako plik wdav.pkg w katalogu lokalnym.
4. W sekcji 2 strony wybierz pozycję **Pobierz pakiet dołączania**. Zapisz go jako WindowsDefenderATPOnboardingPackage.zip w tym samym katalogu.

   :::image type="content" source="images/portal-onboarding-macos.png" alt-text="Opcje pobierania pakietów instalacyjnych i dołączania" lightbox="images/portal-onboarding-macos.png":::

5. W wierszu polecenia sprawdź, czy masz dwa pliki.

## <a name="application-installation-macos-1015"></a>Instalacja aplikacji (macOS 10.15)

Aby ukończyć ten proces, musisz mieć uprawnienia administratora na urządzeniu.

1. Przejdź do pobranego pliku wdav.pkg w aplikacji Finder i otwórz go.

   :::image type="content" source="images/mdatp-28-appinstall.png" alt-text="Instalacja aplikacji" lightbox="images/mdatp-28-appinstall.png":::

2. Wybierz pozycję **Kontynuuj**, zaakceptuj postanowienia licencyjne i wprowadź hasło po wyświetleniu monitu.

   :::image type="content" source="images/mdatp-29-appinstalllogin.png" alt-text="Instalacja aplikacji" lightbox="images/mdatp-29-appinstalllogin.png":::

   > [!IMPORTANT]
   > Zostanie wyświetlony monit o zezwolenie na zainstalowanie sterownika firmy Microsoft ("Zablokowane rozszerzenie systemu" lub "Instalacja jest wstrzymana" lub oba te elementy. Należy zezwolić na instalację sterownika.

     :::image type="content" source="images/mdatp-30-systemextension.png" alt-text="Instalacja aplikacji" lightbox="images/mdatp-30-systemextension.png":::

3. Wybierz pozycję **Otwórz preferencje zabezpieczeń** lub **Otwórz preferencje systemowe > zabezpieczenia & prywatności**. Wybierz pozycję **Zezwalaj**:

   :::image type="content" source="images/mdatp-31-securityprivacysettings.png" alt-text="Okno Zabezpieczenia i prywatność" lightbox="images/mdatp-31-securityprivacysettings.png":::

   Instalacja jest kontynuowana.

   > [!CAUTION]
   > Jeśli nie wybierzesz opcji **Zezwalaj**, instalacja będzie kontynuowana po 5 minutach. Ochrona punktu końcowego w usłudze Microsoft Defender zostaną załadowane, ale niektóre funkcje, takie jak ochrona w czasie rzeczywistym, zostaną wyłączone. Aby uzyskać informacje na temat sposobu rozwiązania tego problemu, zobacz [Rozwiązywanie problemów z rozszerzeniem jądra](mac-support-kext.md) .

> [!NOTE]
> macOS może zażądać ponownego uruchomienia urządzenia podczas pierwszej instalacji Ochrona punktu końcowego w usłudze Microsoft Defender. Ochrona w czasie rzeczywistym nie będzie dostępna do momentu ponownego uruchomienia urządzenia.

## <a name="application-installation-macos-11-and-newer-versions"></a>Instalacja aplikacji (macOS 11 i nowszych wersji)

Aby ukończyć ten proces, musisz mieć uprawnienia administratora na urządzeniu.

1. Przejdź do pobranego pliku wdav.pkg w aplikacji Finder i otwórz go.

   :::image type="content" source="images/monterey-install-1.png" alt-text="Proces instalacji aplikacji" lightbox="images/monterey-install-1.png":::

2. Wybierz pozycję **Kontynuuj**, zaakceptuj postanowienia licencyjne i wprowadź hasło po wyświetleniu monitu.

3. Po zakończeniu procesu instalacji zostaniesz promowany w celu zatwierdzenia rozszerzeń systemowych używanych przez produkt. Wybierz pozycję **Otwórz preferencje zabezpieczeń**.

   :::image type="content" source="images/monterey-install-2.png" alt-text="Zatwierdzenie rozszerzenia systemu" lightbox="images/monterey-install-2.png":::

4. W oknie **Zabezpieczenia & prywatność** wybierz pozycję **Zezwalaj**.

   :::image type="content" source="images/monterey-install-3.png" alt-text="Preferencje zabezpieczeń rozszerzenia systemu1" lightbox="images/monterey-install-3.png":::

5. Powtórz kroki 3 & 4 dla wszystkich rozszerzeń systemowych dystrybuowanych za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac.

6. W ramach funkcji wykrywania punktów końcowych i reagowania Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac sprawdza ruch gniazd i zgłasza te informacje do portalu Microsoft 365 Defender. Po wyświetleniu monitu o przyznanie Ochrona punktu końcowego w usłudze Microsoft Defender uprawnień do filtrowania ruchu sieciego wybierz pozycję **Zezwalaj**.

   :::image type="content" source="images/monterey-install-4.png" alt-text="Preferencje zabezpieczeń rozszerzenia systemu2" lightbox="images/monterey-install-4.png":::

7. Otwórz **pozycję Zabezpieczenia preferencji systemowych** \> **& prywatność** i przejdź do karty **Prywatność** . Przyznaj uprawnienie **do pełnego dostępu do dysku** w usłudze **Microsoft Defender** i **rozszerzeniu zabezpieczeń punktu końcowego usługi Microsoft Defenders**.

   :::image type="content" source="images/monterey-install-5.png" alt-text="Pełny dostęp do dysku" lightbox="images/monterey-install-5.png":::

## <a name="client-configuration"></a>Konfiguracja klienta

1. Skopiuj pliki wdav.pkg i MicrosoftDefenderATPOnboardingMacOs.sh na urządzenie, na którym wdrażasz Ochrona punktu końcowego w usłudze Microsoft Defender na macOS.

    Urządzenie klienckie nie jest skojarzone z org_id. Należy pamiętać, że atrybut *org_id* jest pusty.

    ```bash
    mdatp health --field org_id
    ```

2. Uruchom skrypt powłoki Bash, aby zainstalować plik konfiguracji:

    ```bash
    Sudo bash -x MicrosoftDefenderATPOnboardingMacOs.sh
    ```

3. Sprawdź, czy urządzenie jest teraz skojarzone z Twoją organizacją i zgłosi prawidłowy identyfikator organizacji:

    ```bash
    mdatp health --field org_id
    ```

    Po zakończeniu instalacji ikona usługi Microsoft Defender zostanie wyświetlona na pasku stanu macOS w prawym górnym rogu.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-icon-bar.png" alt-text="Ikona usługi Microsoft Defender na pasku stanu" lightbox="images/mdatp-icon-bar.png":::

## <a name="how-to-allow-full-disk-access"></a>Jak zezwolić na pełny dostęp do dysku

> [!CAUTION]
> macOS 10.15 (Catalina) zawiera nowe ulepszenia zabezpieczeń i prywatności. Począwszy od tej wersji, domyślnie aplikacje nie mogą uzyskać dostępu do niektórych lokalizacji na dysku (takich jak Dokumenty, Pliki do pobrania, Pulpit itp.) bez wyraźnej zgody. W przypadku braku tej zgody Ochrona punktu końcowego w usłudze Microsoft Defender nie jest w stanie w pełni chronić urządzenia.

1. Aby udzielić zgody, otwórz **pozycję Preferencje systemowe** \> **Zabezpieczenia & Prywatność Prywatność** \>  \> **— pełny dostęp do dysku**. Kliknij ikonę blokady, aby wprowadzić zmiany (u dołu okna dialogowego). Wybierz pozycję Ochrona punktu końcowego w usłudze Microsoft Defender.

2. Uruchom test wykrywania av, aby sprawdzić, czy urządzenie jest prawidłowo dołączone i raportuje do usługi. Wykonaj następujące kroki na nowo dołączonym urządzeniu:

    1. Upewnij się, że ochrona w czasie rzeczywistym jest włączona (co oznacza wynik 1 z uruchamiania następującego polecenia):

        ```bash
        mdatp health --field real_time_protection_enabled
        ```

    1. Otwórz okno terminalu. Skopiuj i wykonaj następujące polecenie:

        ```bash
        curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt
        ```

    1. Plik powinien zostać poddany kwarantannie przez usługę Defender for Endpoint na komputerze Mac. Użyj następującego polecenia, aby wyświetlić listę wszystkich wykrytych zagrożeń:

        ```bash
        mdatp threat list
        ```

3. Uruchom test wykrywania EDR, aby sprawdzić, czy urządzenie jest prawidłowo dołączone i raportuje do usługi. Wykonaj następujące kroki na nowo dołączonym urządzeniu:

   1. W przeglądarce, takiej jak Microsoft Edge dla komputerów Mac lub Safari.

   1. Pobierz DIY.zip MDATP dla systemu MacOS z https://aka.ms/mdatpmacosdiy i wyodrębnij.

      Może zostać wyświetlony monit:

      > Czy chcesz zezwolić na pobieranie na "mdatpclientanalyzer.blob.core.windows.net"?<br/>
      > Możesz zmienić witryny internetowe, które mogą pobierać pliki w preferencjach witryn internetowych.

4. Kliknij pozycję **Zezwalaj**.

5. Otwórz **pliki do pobrania**.

6. Powinna zostać wyświetlona funkcja **MDATP dla systemu MacOS DIY**.

   > [!TIP]
   > Po dwukrotnym kliknięciu zostanie wyświetlony następujący komunikat:
   >
   > > **Nie można otworzyć "MDATP MacOS DIY", ponieważ deweloper nie może być weryfikatorem.**<br/>
   > > macOS nie może sprawdzić, czy ta aplikacja jest wolna od złośliwego oprogramowania.<br/>
   > > **\[Przenieś do kosza\]** **\[anuluj\]**

7. Kliknij przycisk **Anuluj**.

8. Kliknij prawym przyciskiem myszy **pozycję MDATP Dla systemu MacOS DIY**, a następnie kliknij przycisk **Otwórz**.

    System powinien wyświetlić następujący komunikat:

    > **macOS nie może zweryfikować dewelopera MDATP MacOS DIY. Czy na pewno chcesz go otworzyć?**<br/>
    > Otwarcie tej aplikacji spowoduje zastąpienie zabezpieczeń systemu, które może uwidoczniać komputer i dane osobowe złośliwemu oprogramowaniu, które może zaszkodzić twojemu komputerowi Mac lub naruszyć twoją prywatność.

9. Kliknij przycisk **Otwórz**.

    System powinien wyświetlić następujący komunikat:

    > Ochrona punktu końcowego w usłudze Microsoft Defender — plik testowy macOS EDR DIY<br/>
    > Odpowiedni alert będzie dostępny w portalu MDATP.

10. Kliknij przycisk **Otwórz**.

    W ciągu kilku minut powinien zostać zgłoszony alert o nazwie "macOS EDR Test Alert".

11. Przejdź do portalu Microsoft 365 Defender (https://security.microsoft.com/).

12. Przejdź do kolejki alertów.

    :::image type="content" source="images/b8db76c2-c368-49ad-970f-dcb87534d9be.png" alt-text="Alert testowy macOS EDR pokazujący ważność, kategorię, źródło wykrywania i zwinięte menu akcji" lightbox="images/b8db76c2-c368-49ad-970f-dcb87534d9be.png":::

    Przyjrzyj się szczegółom alertu i osi czasu urządzenia i wykonaj regularne kroki badania.

## <a name="logging-installation-issues"></a>Problemy z instalacją rejestrowania

Zobacz [Rejestrowanie problemów z instalacją](mac-resources.md#logging-installation-issues) , aby uzyskać więcej informacji na temat znajdowania automatycznie wygenerowanego dziennika utworzonego przez instalatora w przypadku wystąpienia błędu.

## <a name="uninstallation"></a>Dezinstalacji

Aby uzyskać szczegółowe informacje na temat usuwania Ochrona punktu końcowego w usłudze Microsoft Defender na macOS z urządzeń klienckich, zobacz [Odinstalowywanie](mac-resources.md#uninstalling).
