---
title: Wdrażaj usługę ochrony punktu końcowego w usłudze Microsoft Defender w systemie Android za pomocą usługi Microsoft Intune
description: Opis sposobu wdrażania Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android przy użyciu Microsoft Intune
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mde, android, installation, deploy, uninstallation,
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: e5f38f701c865ad337bd04cb731ba40e00bf6118
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130460"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-android-with-microsoft-intune"></a>Wdrażaj usługę ochrony punktu końcowego w usłudze Microsoft Defender w systemie Android za pomocą usługi Microsoft Intune

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Dowiedz się, jak wdrożyć usługę Defender for Endpoint w systemie Android na Intune — Portal firmy zarejestrowanych urządzeniach. Aby uzyskać więcej informacji na temat rejestracji urządzeń Intune, zobacz [Rejestrowanie urządzenia](/mem/intune/user-help/enroll-device-android-company-portal).

> [!NOTE]
> **Usługa Defender for Endpoint w systemie Android jest teraz dostępna w [sklepie Google Play](https://play.google.com/store/apps/details?id=com.microsoft.scmx)**
>
> Możesz nawiązać połączenie z sklepem Google Play z Intune, aby wdrożyć aplikację Defender for Endpoint w trybach rejestracji administratora urządzenia i systemu Android Enterprise.
>
> Aktualizacje aplikacji są automatyczne za pośrednictwem sklepu Google Play.

## <a name="deploy-on-device-administrator-enrolled-devices"></a>Wdrażanie na urządzeniach zarejestrowanych przez administratora urządzeń

**Wdrażanie usługi Defender for Endpoint w systemie Android na Intune — Portal firmy — urządzenia zarejestrowane przez administratora urządzeń**

Dowiedz się, jak wdrożyć usługę Defender for Endpoint w systemie Android na urządzeniach Intune — Portal firmy — zarejestrowane przez administratora urządzeń.

### <a name="add-as-android-store-app"></a>Dodaj jako aplikację ze sklepu dla systemu Android

1. W [Microsoft Endpoint Manager centrum administracyjnym](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do pozycji **Aplikacje** \> **dla** \> systemu Android **Dodaj \> aplikację ze sklepu dla systemu Android** i wybierz **pozycję Wybierz**.

   :::image type="content" source="images/mda-addandroidstoreapp.png" alt-text="Okienko Dodawanie aplikacji ze sklepu dla systemu Android w portalu centrum administracyjnego Microsoft Endpoint Manager"  lightbox="images/mda-addandroidstoreapp.png":::

2. Na stronie **Dodawanie aplikacji** i w sekcji *Informacje o aplikacji* wprowadź:

   - **Nazwa**
   - **Opis**
   - **Publisher** jako firma Microsoft.
   - **Adres URL sklepu z aplikacjami** jako https://play.google.com/store/apps/details?id=com.microsoft.scmx (adres URL sklepu Google Play aplikacji Defender for Endpoint)

   Inne pola są opcjonalne. Wybierz pozycję **Dalej**.

   :::image type="content" source="images/mda-addappinfo.png" alt-text="Strona Dodawanie aplikacji z informacjami o wydawcy i adresie URL aplikacji w portalu centrum administracyjnego Microsoft Endpoint Manager" lightbox="images/mda-addappinfo.png":::

3. W sekcji *Przypisania* przejdź do sekcji **Wymagane** i wybierz pozycję **Dodaj grupę.** Następnie możesz wybrać grupy użytkowników, dla których chcesz kierować usługę Defender for Endpoint w aplikacji systemu Android. Wybierz **pozycję Wybierz** , a następnie **pozycję Dalej**.

    > [!NOTE]
    > Wybrana grupa użytkowników powinna składać się z Intune zarejestrowanych użytkowników.
    >
    > :::image type="content" source="images/363bf30f7d69a94db578e8af0ddd044b.png" alt-text="Okienko Dodawanie grupy na stronie Dodawanie aplikacji w portalu centrum administracyjnego Microsoft Endpoint Manager" lightbox="images/363bf30f7d69a94db578e8af0ddd044b.png":::

4. W sekcji **Przeglądanie i tworzenie** sprawdź, czy wszystkie wprowadzone informacje są poprawne, a następnie wybierz pozycję **Utwórz**.

    Za kilka chwil aplikacja Defender for Endpoint zostanie pomyślnie utworzona, a powiadomienie zostanie wyświetlone w prawym górnym rogu strony.

    :::image type="content" source="images/86cbe56f88bb6e93e9c63303397fc24f.png" alt-text="Okienko stanu aplikacji w portalu centrum administracyjnego Microsoft Endpoint Manager" lightbox="images/86cbe56f88bb6e93e9c63303397fc24f.png":::

5. Na wyświetlonej stronie informacji o aplikacji w sekcji **Monitorowanie** wybierz pozycję **Stan instalacji urządzenia** , aby sprawdzić, czy instalacja urządzenia zakończyła się pomyślnie.

    :::image type="content" source="images/513cf5d59eaaef5d2b5bc122715b5844.png" alt-text="Strona Stan instalacji urządzenia w portalu usługi Microsoft Defender 365" lightbox="images/513cf5d59eaaef5d2b5bc122715b5844.png":::

### <a name="complete-onboarding-and-check-status"></a>Zakończ dołączanie i sprawdź stan

1. Po zainstalowaniu usługi Defender for Endpoint w systemie Android na urządzeniu zostanie wyświetlona ikona aplikacji.

   :::image type="content" source="images/7cf9311ad676ec5142002a4d0c2323ca.jpg" alt-text="Ikona usługi Microsoft Defender ATP wymieniona w okienku Wyszukiwania" lightbox="images/7cf9311ad676ec5142002a4d0c2323ca.jpg":::

2. Naciśnij ikonę aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender i postępuj zgodnie z instrukcjami wyświetlanymi na ekranie, aby ukończyć dołączanie aplikacji. Szczegóły obejmują akceptację przez użytkownika końcowego uprawnień systemu Android wymaganych przez usługę Defender for Endpoint w systemie Android.

3. Po pomyślnym dołączeniu urządzenie zostanie wyświetlone na liście Urządzenia w portalu Microsoft 365 Defender.

    :::image type="content" source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" alt-text="Urządzenie w portalu Ochrona punktu końcowego w usłudze Microsoft Defender"  lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="deploy-on-android-enterprise-enrolled-devices"></a>Wdrażanie na urządzeniach z systemem Android Enterprise zarejestrowanych

Usługa Defender for Endpoint w systemie Android obsługuje urządzenia z systemem Android Enterprise zarejestrowane.

Aby uzyskać więcej informacji na temat opcji rejestracji obsługiwanych przez Intune, zobacz [Opcje rejestracji](/mem/intune/enrollment/android-enroll).

**Obecnie urządzenia należące do użytkownika z profilem służbowym i w pełni zarządzanymi rejestracjami urządzeń użytkowników należących do firmy są obsługiwane w przypadku wdrażania.**

## <a name="add-microsoft-defender-for-endpoint-on-android-as-a-managed-google-play-app"></a>Dodawanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android jako zarządzanej aplikacji Google Play

Wykonaj poniższe kroki, aby dodać aplikację Ochrona punktu końcowego w usłudze Microsoft Defender do zarządzanego sklepu Google Play.

1. W [Microsoft Endpoint Manager centrum administracyjnym](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do pozycji **Aplikacje** \> **dla** \> systemu Android **Dodaj** i wybierz pozycję **Zarządzana aplikacja Google Play**.

    :::image type="content" source="images/579ff59f31f599414cedf63051628b2e.png" alt-text="Okienko dodawania aplikacji w portalu centrum administracyjnego Microsoft Endpoint Manager" lightbox="images/579ff59f31f599414cedf63051628b2e.png":::

2. Na stronie zarządzanego sklepu Google Play, która zostanie załadowana później, przejdź do pola wyszukiwania i wprowadź wartość `Microsoft Defender`. Wyszukiwanie powinno wyświetlać aplikację Ochrona punktu końcowego w usłudze Microsoft Defender w zarządzanym sklepie Google Play. Kliknij aplikację Ochrona punktu końcowego w usłudze Microsoft Defender z wyniku wyszukiwania Aplikacje.

    :::image type="content" source="images/0f79cb37900b57c3e2bb0effad1c19cb.png" alt-text="Strona Zarządzanego sklepu Google Play w portalu centrum administracyjnego Microsoft Endpoint Manager" lightbox="images/0f79cb37900b57c3e2bb0effad1c19cb.png":::

3. Na stronie Opis aplikacji, która pojawi się w następnej kolejności, powinny być widoczne szczegóły aplikacji w usłudze Defender for Endpoint. Przejrzyj informacje na stronie, a następnie wybierz pozycję **Zatwierdź**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/07e6d4119f265037e3b80a20a73b856f.png" alt-text="Strona zarządzanego sklepu Google Play w portalu centrum administracyjnego Microsoft Endpoint Manager" lightbox="images/07e6d4119f265037e3b80a20a73b856f.png":::
      

4. Zostaną wyświetlone uprawnienia, które usługa Defender for Endpoint uzyskuje, aby działała. Przejrzyj je, a następnie wybierz pozycję **Zatwierdź**.

    :::image type="content" source="images/206b3d954f06cc58b3466fb7a0bd9f74.png" alt-text="Strona zatwierdzania uprawnień w portalu usługi Microsoft Defender 365" lightbox="images/206b3d954f06cc58b3466fb7a0bd9f74.png":::

5. Zostanie wyświetlona strona Ustawienia zatwierdzania. Strona potwierdza preferencję obsługi nowych uprawnień aplikacji, o które może poprosić usługa Defender for Endpoint w systemie Android. Przejrzyj wybrane opcje i wybierz preferowaną opcję. Wybierz pozycję **Gotowe**.

    Domyślnie zarządzany sklep Google Play wybiera pozycję **Zachowaj zatwierdzenie, gdy aplikacja żąda nowych uprawnień**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ffecfdda1c4df14148f1526c22cc0236.png" alt-text=" Strona uzupełniania konfiguracji ustawień zatwierdzania w portalu usługi Microsoft Defender 365" lightbox="images/ffecfdda1c4df14148f1526c22cc0236.png":::

6. Po dokonaniu wyboru obsługi uprawnień wybierz pozycję **Synchronizuj**, aby zsynchronizować Ochrona punktu końcowego w usłudze Microsoft Defender z listą aplikacji.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/34e6b9a0dae125d085c84593140180ed.png" alt-text="Okienko Synchronizacja w portalu usługi Microsoft Defender 365" lightbox="images/34e6b9a0dae125d085c84593140180ed.png":::

7. Synchronizacja zakończy się za kilka minut.

    :::image type="content" source="images/9fc07ffc150171f169dc6e57fe6f1c74.png" alt-text="Okienko stanu synchronizacji aplikacji na stronie aplikacji systemu Android w portalu usługi Microsoft Defender 365"  lightbox="images/9fc07ffc150171f169dc6e57fe6f1c74.png":::

8. Wybierz przycisk **Odśwież** na ekranie aplikacje systemu Android, a Ochrona punktu końcowego w usłudze Microsoft Defender powinny być widoczne na liście aplikacji.

    :::image type="content" source="images/fa4ac18a6333335db3775630b8e6b353.png" alt-text="Strona wyświetlająca zsynchronizowana aplikacja" lightbox="images/fa4ac18a6333335db3775630b8e6b353.png":::

9. Usługa Defender for Endpoint obsługuje zasady konfiguracji aplikacji dla urządzeń zarządzanych za pośrednictwem Intune. Tę możliwość można wykorzystać do wybierania różnych konfiguracji dla usługi Defender.

    1. Na stronie **Aplikacje** przejdź do pozycji **Zasady > Zasady konfiguracji aplikacji > Dodawanie urządzeń zarządzanych >**.

       :::image type="content" source="images/android-mem.png" alt-text="Okienko Zasady konfiguracji aplikacji w portalu centrum administracyjnego Microsoft Endpoint Manager" lightbox="images/android-mem.png":::

    1. Na stronie **Tworzenie zasad konfiguracji aplikacji** wprowadź następujące szczegóły:

        - Nazwa: Ochrona punktu końcowego w usłudze Microsoft Defender.
        - Wybierz **pozycję Android Enterprise** jako platformę.
        - Wybierz **pozycję Profil służbowy tylko** jako typ profilu.
        - Kliknij **pozycję Wybierz aplikację**, wybierz pozycję **Microsoft Defender ATP**, wybierz przycisk **OK** , a następnie pozycję **Dalej**.

        :::image type="content" source="images/android-create-app.png" alt-text=" Okienko Szczegóły skojarzonej aplikacji" lightbox="images/android-create-app.png":::

    1. Na stronie **Ustawienia** przejdź do sekcji **Ustawienia konfiguracji** i wybierz pozycję **"Użyj projektanta konfiguracji"** w formacie ustawień konfiguracji. 

       :::image type="content" alt-text="Obraz przedstawiający zasady konfiguracji aplikacji tworzenia aplikacji dla systemu Android." source="images/configurationformat.png" lightbox="images/configurationformat.png":::

    1. Kliknij pozycję **Dodaj** , aby wyświetlić listę obsługiwanych konfiguracji. Wybierz wymaganą konfigurację i kliknij przycisk **OK**.

       :::image type="content" alt-text="Obraz przedstawiający wybieranie zasad konfiguracji dla systemu Android." source="images/selectconfigurations.png" lightbox="images/selectconfigurations.png":::


    1. Powinny zostać wyświetlone wszystkie wybrane konfiguracje na liście. Możesz zmienić wartość konfiguracji zgodnie z potrzebami, a następnie wybrać przycisk **Dalej**.
        
        :::image type="content" alt-text="Obraz przedstawiający wybrane zasady konfiguracji." source="images/listedconfigurations.png" lightbox="images/listedconfigurations.png":::
       

    1. Na stronie **Przypisania** wybierz grupę użytkowników, do której zostaną przypisane te zasady konfiguracji aplikacji. Kliknij **pozycję Wybierz grupy do uwzględnienia** i wybierz odpowiednią grupę, a następnie wybierz pozycję **Dalej**. Wybrana w tym miejscu grupa jest zwykle tą samą grupą, do której należy przypisać Ochrona punktu końcowego w usłudze Microsoft Defender aplikacji systemu Android.

       :::image type="content" source="images/android-select-group.png" alt-text="Okienko Wybrane grupy" lightbox="images/android-select-group.png":::

    1. Na następnej stronie **Przeglądanie i tworzenie** przejrzyj wszystkie informacje, a następnie wybierz pozycję **Utwórz**.

        Zasady konfiguracji aplikacji dla usługi Defender for Endpoint, które automatycznie wyzwolą uprawnienie magazynu, są teraz przypisywane do wybranej grupy użytkowników.

        > [!div class="mx-imgBorder"]
        > :::image type="content" source="images/android-review-create.png" alt-text="Karta Przeglądanie i tworzenie na stronie Tworzenie zasad konfiguracji aplikacji" lightbox="images/android-review-create.png":::

10. Wybierz pozycję Aplikacja **usługi Microsoft Defender ATP** na liście \> **Właściwości** \> **Przypisania** **Edytuj**\>.

   :::image type="content" source="images/mda-properties.png" alt-text="Opcja Edytuj na stronie Właściwości" lightbox="images/mda-properties.png":::

11. Przypisz aplikację jako *wymaganą* aplikację do grupy użytkowników. Jest on automatycznie instalowany w *profilu służbowym* podczas następnej synchronizacji urządzenia za pośrednictwem aplikacji Portal firmy. To przypisanie można wykonać, przechodząc do sekcji \> *Wymagane* **Dodaj grupę,** wybierając grupę użytkowników i klikając pozycję **Wybierz**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ea06643280075f16265a596fb9a96042.png" alt-text="Strona Edytowanie aplikacji" lightbox="images/ea06643280075f16265a596fb9a96042.png":::

12. Na stronie **Edytowanie aplikacji** przejrzyj wszystkie informacje wprowadzone powyżej. Następnie wybierz pozycję **Przejrzyj i zapisz** , a następnie ponownie **zapisz** , aby rozpocząć przypisywanie.

### <a name="auto-setup-of-always-on-vpn"></a>Automatyczna instalacja zawsze włączonej sieci VPN

Usługa Defender for Endpoint obsługuje zasady konfiguracji urządzeń zarządzanych za pośrednictwem Intune. Tę możliwość można wykorzystać do **automatycznego konfigurowania zawsze włączonej sieci VPN** na urządzeniach z systemem Android Enterprise zarejestrowanych, więc użytkownik końcowy nie musi konfigurować usługi sieci VPN podczas dołączania.

1. Na **urządzeniach** wybierz pozycję **Profile konfiguracji** \> Utwórz **platformę** \> **profilu** \> dla **systemu Android Enterprise**

   Wybierz pozycję **Ograniczenia urządzenia** w ramach jednej z następujących opcji na podstawie typu rejestracji urządzenia:
   - **W pełni zarządzany, dedykowany i Corporate-Owned profil służbowy**
   - **Profil służbowy należący do użytkownika**

   Wybierz pozycję **Utwórz**.

   :::image type="content" source="images/1autosetupofvpn.png" alt-text="Element menu Profile konfiguracji w okienku Zasady" lightbox="images/1autosetupofvpn.png":::

2. **Konfiguracja Ustawienia** podaj **nazwę** i **opis**, aby jednoznacznie zidentyfikować profil konfiguracji.

   :::image type="content" source="images/2autosetupofvpn.png" alt-text="Pola Nazwa i opis profilu konfiguracji urządzeń w okienku Podstawy" lightbox="images/2autosetupofvpn.png":::

3. Wybierz pozycję **Łączność** i skonfiguruj sieć VPN:

   - Włączanie **zawsze włączonej sieci VPN**

     Skonfiguruj klienta sieci VPN w profilu służbowym, aby w miarę możliwości automatycznie łączyć się i ponownie łączyć z siecią VPN. Dla zawsze włączonej sieci VPN na danym urządzeniu można skonfigurować tylko jednego klienta sieci VPN, dlatego upewnij się, że na jednym urządzeniu wdrożono nie więcej niż jedną zawsze włączoną zasadę sieci VPN.

   - Wybierz pozycję **Niestandardowe** na liście rozwijanej klienta sieci VPN

     Niestandardowa sieć VPN w tym przypadku to usługa Defender for Endpoint VPN, która jest używana do udostępniania funkcji ochrony sieci Web.

     > [!NOTE]
     > Ochrona punktu końcowego w usłudze Microsoft Defender aplikacja musi być zainstalowana na urządzeniu użytkownika, aby działała automatyczna konfiguracja tej sieci VPN.

   - Wprowadź **identyfikator pakietu** aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender w sklepie Google Play. W przypadku adresu URL <https://play.google.com/store/apps/details?id=com.microsoft.scmx>aplikacji Defender identyfikator pakietu to **com.microsoft.scmx**

   - **Tryb blokady** Nie skonfigurowano (ustawienie domyślne)

     :::image type="content" source="images/3autosetupofvpn.png" alt-text="Okienko Łączność na karcie Ustawienia konfiguracji" lightbox="images/3autosetupofvpn.png":::

4. **Przypisania**

   Na stronie **Przypisania** wybierz grupę użytkowników, do której zostaną przypisane te zasady konfiguracji aplikacji. Wybierz **pozycję Wybierz grupy** do uwzględnienia i wybierając odpowiednią grupę, a następnie wybierz pozycję **Dalej**. Wybrana w tym miejscu grupa jest zwykle tą samą grupą, do której należy przypisać Ochrona punktu końcowego w usłudze Microsoft Defender aplikacji systemu Android.

   :::image type="content" source="images/4autosetupofvpn.png" alt-text="Okienko przypisania profilu konfiguracji urządzeń w ograniczeniach urządzenia" lightbox="images/4autosetupofvpn.png":::

5. Na następnej stronie **Przeglądanie i tworzenie** przejrzyj wszystkie informacje, a następnie wybierz pozycję **Utwórz**.
Profil konfiguracji urządzenia jest teraz przypisany do wybranej grupy użytkowników.

   :::image type="content" source="images/5autosetupofvpn.png" alt-text="Aprowizowanie profilu konfiguracji urządzeń na potrzeby przeglądania i tworzenia" lightbox="images/5autosetupofvpn.png":::

## <a name="check-status-and-complete-onboarding"></a>Sprawdzanie stanu i ukończenie dołączania

1. Potwierdź stan instalacji Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android, klikając pozycję **Stan instalacji urządzenia**. Sprawdź, czy urządzenie jest wyświetlane tutaj.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/900c0197aa59f9b7abd762ab2b32e80c.png" alt-text="Okienko stanu instalacji urządzenia" lightbox="images/900c0197aa59f9b7abd762ab2b32e80c.png":::

2. Na urządzeniu możesz zweryfikować stan dołączania, przechodząc do **profilu służbowego**. Upewnij się, że usługa Defender for Endpoint jest dostępna i że jesteś zarejestrowany na **urządzeniach należących do użytkownika z profilem służbowym**. Jeśli jesteś zarejestrowany na **firmowym, w pełni zarządzanym urządzeniu użytkownika**, na urządzeniu będziesz mieć jeden profil, w którym możesz potwierdzić, że usługa Defender for Endpoint jest dostępna.

    :::image type="content" source="images/c2e647fc8fa31c4f2349c76f2497bc0e.png" alt-text="Okienko wyświetlania aplikacji" lightbox="images/c2e647fc8fa31c4f2349c76f2497bc0e.png":::

3. Po zainstalowaniu aplikacji otwórz aplikację i zaakceptuj uprawnienia, a następnie dołączanie powinno zakończyć się pomyślnie.

    :::image type="content" source="images/MDE_new.png" alt-text="Wyświetlanie aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender na urządzeniu przenośnym" lightbox="images/MDE_new.png":::

4. Na tym etapie urządzenie zostało pomyślnie dołączone do usługi Defender for Endpoint w systemie Android. Możesz to sprawdzić w [portalu Microsoft 365 Defender](https://security.microsoft.com), przechodząc do strony **Spis urządzeń**.

    :::image type="content" source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" alt-text="Portal Ochrona punktu końcowego w usłudze Microsoft Defender" lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="set-up-microsoft-defender-in-personal-profile-on-android-enterprise-in-byod-mode"></a>Konfigurowanie usługi Microsoft Defender w profilu osobistym w systemie Android Enterprise w trybie BYOD

>[!NOTE]
>Obsługa usługi Microsoft Defender w profilu osobistym w systemie Android Enterprise (AE) w trybie "Przynieś własne urządzenie" (BYOD) jest teraz dostępna w publicznej wersji zapoznawczej. Poniższe informacje dotyczą wstępnie wydanego produktu, który może zostać znacząco zmodyfikowany przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

Dzięki obsłudze usługi Microsoft Defender w profilach osobistych systemu Android urządzenia użytkowników mogą być chronione przed atakami wyłudzania informacji i złośliwego oprogramowania w profilu osobistym, które mogą potencjalnie naruszyć bezpieczeństwo zasobów firmowych w profilu służbowym. 

**Konfigurowanie usługi Microsoft Defender w profilu osobistym**

Administratorzy mogą przejść do [centrum administracyjnego usługi Microsoft Endpoint Management](https://endpoint.microsoft.com) , aby skonfigurować i skonfigurować pomoc techniczną usługi Microsoft Defender w profilach osobistych, wykonując następujące kroki:
1. Przejdź do obszaru **Aplikacje> Zasady konfiguracji aplikacji** i kliknij pozycję **Dodaj**. Wybierz pozycję **Urządzenia zarządzane**.

    > [!div class="mx-imgBorder"]
    > ![Obraz przedstawiający dodawanie zasad konfiguracji aplikacji.](images/addpolicy.png)

1.  Wprowadź **nazwę** i **opis** , aby jednoznacznie zidentyfikować zasady konfiguracji. Wybierz platformę jako **"Android Enterprise",** typ profilu **jako "Tylko profil służbowy należący do użytkownika"** i Aplikacja docelowa jako **"Microsoft Defender"**.
 
    > [!div class="mx-imgBorder"]
    > ![Obraz przedstawiający zasady konfiguracji nazewnictwa.](images/selectapp.png)

1. Na stronie ustawień w **obszarze "Format ustawień konfiguracji"** wybierz pozycję **"Użyj projektanta konfiguracji",** a następnie kliknij pozycję **Dodaj**. Z wyświetlonej listy konfiguracji wybierz pozycję **"Microsoft Defender w profilu osobistym"**.

    > [!div class="mx-imgBorder"]
    > ![Obraz przedstawiający konfigurowanie profilu osobistego.](images/addconfiguration.png)

1. Zostanie wyświetlona wybrana konfiguracja. Zmień **wartość konfiguracji na 1** , aby włączyć obsługę profilów osobistych w usłudze Microsoft Defender. Zostanie wyświetlone powiadomienie informujące administratora o tym samym. Kliknij przycisk **Dalej**.

    > [!div class="mx-imgBorder"]
    > ![Obraz przedstawiający zmianę wartości konfiguracji.](images/changeconfigvalue.png)

1. **Przypisz** zasady konfiguracji do grupy użytkowników. **Przejrzyj i utwórz** zasady.

    > [!div class="mx-imgBorder"]
    > ![Obraz przedstawiający przeglądanie i tworzenie zasad.](images/savepolicy.png)

Administratorzy mogą również skonfigurować **mechanizmy kontroli prywatności** z centrum administracyjnego Microsoft Endpoint Manager, aby kontrolować, jakie dane mogą być wysyłane przez klienta mobilnego usługi Defender do portalu zabezpieczeń. Aby uzyskać więcej informacji, zobacz [konfigurowanie mechanizmów kontroli prywatności](android-configure.md).

Organizacje mogą komunikować się ze swoimi użytkownikami w celu ochrony profilu osobistego za pomocą usługi Microsoft Defender na zarejestrowanych urządzeniach BYOD.
- Wymagania wstępne: usługa Microsoft Defender musi być już zainstalowana i aktywna w profilu służbowym, aby włączyć usługę Microsoft Defender w profilach osobistych.

**Aby ukończyć dołączanie urządzenia**
1.  Zainstaluj aplikację Microsoft Defender w profilu osobistym przy użyciu osobistego konta sklepu Google Play.
2.  Zainstaluj aplikację Portal firmy w profilu osobistym. Logowanie nie jest wymagane.
3.  Po uruchomieniu aplikacji przez użytkownika zostanie wyświetlony ekran logowania. **Zaloguj się tylko przy użyciu konta firmowego**.
4.  Po pomyślnym zalogowaniu użytkownicy zobaczą następujące ekrany:

    a.  **Ekran umowy EULA**: prezentowany tylko wtedy, gdy użytkownik nie wyraził jeszcze zgody w profilu służbowym.

    b.  **Ekran powiadomienia**: użytkownicy muszą wyrazić zgodę na tym ekranie, aby kontynuować dołączanie aplikacji. Jest to wymagane tylko podczas pierwszego uruchomienia aplikacji.
5.  Podaj wymagane uprawnienia do ukończenia dołączania.

>[!NOTE]
>**Wymagania wstępne:**
 >1. Portal firmy musi być włączony w profilu osobistym.
 >2. Usługa Microsoft Defender musi być już zainstalowana i aktywna w profilu służbowym.


## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie usługi ochrony punktu końcowego w usłudze Microsoft Defender w systemie Android](microsoft-defender-endpoint-android.md)
- [Konfiguruj usługę ochrony punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
