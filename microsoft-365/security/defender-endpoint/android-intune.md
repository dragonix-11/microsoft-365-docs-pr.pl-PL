---
title: Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android za pomocą aplikacji Microsoft Intune
description: W tym artykule opisano, Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android za pomocą aplikacji Microsoft Intune
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mde, android, instalacja, wdrażanie, dezinstalacja,
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
ms.openlocfilehash: aab50764a13a671cdeb10902744456dcbc1cb48f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471412"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-android-with-microsoft-intune"></a>Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android za pomocą aplikacji Microsoft Intune

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Dowiedz się, jak wdrożyć usługę Defender for Endpoint w systemie Android Intune — Portal firmy zarejestrowanych urządzeniach. Aby uzyskać więcej informacji na Intune rejestracji urządzenia, zobacz [Rejestrowanie urządzenia](/mem/intune/user-help/enroll-device-android-company-portal).

> [!NOTE]
> **Usługa Defender for Endpoint w systemie Android jest teraz dostępna w [sklepie Google Play](https://play.google.com/store/apps/details?id=com.microsoft.scmx)**
>
> Możesz połączyć się ze sklepem Google Play z aplikacji Intune, aby wdrożyć aplikację Defender for Endpoint w administratorze urządzenia i systemie Android Enterprise trybach rejestracji.
>
> Aktualizacje aplikacji są automatyczne dostępne za pośrednictwem sklepu Google Play.

## <a name="deploy-on-device-administrator-enrolled-devices"></a>Wdrażanie na urządzeniach zarejestrowanych przez administratora urządzeń

**Wdrażanie usługi Defender dla punktu końcowego w systemie Android Intune — Portal firmy — zarejestrowane urządzenia przez administratora urządzeń**

Dowiedz się, jak wdrożyć usługę Defender for Endpoint w systemie Android Intune — Portal firmy — zarejestrowane urządzenia przez administratora urządzeń.

### <a name="add-as-android-store-app"></a>Dodaj jako aplikację ze Sklepu Android

1. W [Microsoft Endpoint Manager administracyjnym](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do  \> pozycji Aplikacje **Android Aplikacje** \> Dodaj **aplikację \> ze sklepu Android i** wybierz pozycję **Wybierz**.

   :::image type="content" source="images/mda-addandroidstoreapp.png" alt-text="Dodawanie sklepu z systemem Android okienko aplikacji w Microsoft Endpoint Manager centrum administracyjnym systemu Android"  lightbox="images/mda-addandroidstoreapp.png":::

2. Na stronie **Dodawanie aplikacji** i w sekcji *Informacje o aplikacji* wprowadź:

   - **Nazwa**
   - **Opis**
   - **Publisher** jako firma Microsoft.
   - **Adres URL sklepu App Store** jako https://play.google.com/store/apps/details?id=com.microsoft.scmx (Defender dla aplikacji końcowej Google Play Adres URL sklepu Google Play)

   Inne pola są opcjonalne. Wybierz pozycję **Dalej**.

   :::image type="content" source="images/mda-addappinfo.png" alt-text="Strona Dodawanie aplikacji z informacjami o wydawcy i adresie URL aplikacji w portalu Centrum Microsoft Endpoint Manager administracyjnego w programie" lightbox="images/mda-addappinfo.png":::

3. W *sekcji Zadania przejdź* do sekcji **Wymagane i wybierz** pozycję **Dodaj grupę.** Następnie możesz wybrać grupy użytkowników, do których chcesz kierować element Defender dla punktu końcowego w aplikacji dla systemu Android. Wybierz **pozycję Wybierz** , a następnie **przycisk Dalej**.

    > [!NOTE]
    > Wybrana grupa użytkowników powinna składać się z Intune zarejestrowanych użytkowników.
    >
    > :::image type="content" source="images/363bf30f7d69a94db578e8af0ddd044b.png" alt-text="Okienko Dodawanie grupy na stronie Dodawanie aplikacji w portalu Centrum Microsoft Endpoint Manager administracyjnego" lightbox="images/363bf30f7d69a94db578e8af0ddd044b.png":::

4. W sekcji **Recenzja+Tworzenie** sprawdź, czy wszystkie wprowadzone informacje są poprawne, a następnie wybierz pozycję **Utwórz**.

    W chwilę pomyślnie utworzono aplikację Defender for Endpoint i w prawym górnym rogu strony było wyświetlane powiadomienie.

    :::image type="content" source="images/86cbe56f88bb6e93e9c63303397fc24f.png" alt-text="Okienko stanu aplikacji w portalu Centrum Microsoft Endpoint Manager administracyjnego" lightbox="images/86cbe56f88bb6e93e9c63303397fc24f.png":::

5. Na wyświetlonej stronie z informacjami o aplikacji w sekcji **Monitor** wybierz pozycję Stan  instalacji urządzenia, aby sprawdzić, czy instalacja urządzenia została ukończona pomyślnie.

    :::image type="content" source="images/513cf5d59eaaef5d2b5bc122715b5844.png" alt-text="Strona stanu instalacji urządzenia w portalu usługi Microsoft Defender 365" lightbox="images/513cf5d59eaaef5d2b5bc122715b5844.png":::

### <a name="complete-onboarding-and-check-status"></a>Zakończenie dołączania i sprawdzanie stanu

1. Po zainstalowaniu na urządzeniu programu Defender dla punktu końcowego systemu Android zobaczysz ikonę aplikacji.

   :::image type="content" source="images/7cf9311ad676ec5142002a4d0c2323ca.jpg" alt-text="The Microsoft Defender ATP icon listed in the Search pane" lightbox="images/7cf9311ad676ec5142002a4d0c2323ca.jpg":::

2. Naciśnij ikonę Ochrona punktu końcowego w usłudze Microsoft Defender aplikacji i postępuj zgodnie z instrukcjami wyświetlanymi na ekranie, aby ukończyć dołączanie aplikacji. Szczegóły obejmują akceptowanie przez użytkownika końcowego uprawnień systemu Android wymaganych przez program Defender dla punktu końcowego w systemie Android.

3. Po pomyślnym rozpoczęciu dołączania urządzenie zacznie być wyświetlane na liście Urządzenia w Microsoft 365 Defender sieci.

    :::image type="content" source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" alt-text="Urządzenie w portalu Ochrona punktu końcowego w usłudze Microsoft Defender użytkowników"  lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="deploy-on-android-enterprise-enrolled-devices"></a>Wdrażanie na zarejestrowanych Enterprise Android

Program Defender dla punktu końcowego w systemie Android obsługuje Enterprise Urządzenia z systemem Android.

Aby uzyskać więcej informacji na temat opcji rejestracji obsługiwanych przez Intune, zobacz [Opcje rejestracji](/mem/intune/enrollment/android-enroll).

**Obecnie urządzenia będące własnością użytkownika z profilem służbowym i w pełni zarządzanymi rejestracjami urządzeń użytkowników są obsługiwane w celu wdrożenia.**

## <a name="add-microsoft-defender-for-endpoint-on-android-as-a-managed-google-play-app"></a>Dodawanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android jako aplikacji zarządzanej Google Play

Wykonaj poniższe czynności, aby dodać aplikację Ochrona punktu końcowego w usłudze Microsoft Defender do zarządzanej usługi Google Play.

1. W [Microsoft Endpoint Manager administracyjnym](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do **pozycji Aplikacje** \> **Systemu Android Aplikacje** \> **Dodaj** i wybierz pozycję **Aplikacja zarządzana Google Play**.

    :::image type="content" source="images/579ff59f31f599414cedf63051628b2e.png" alt-text="Okienko dodawania aplikacji w portalu centrum Microsoft Endpoint Manager administracyjnego" lightbox="images/579ff59f31f599414cedf63051628b2e.png":::

2. Na zarządzanej stronie Google Play, która zostanie ładowana później, przejdź do pola wyszukiwania i wpisz .`Microsoft Defender` W wynikach wyszukiwania powinna być wyświetlana Ochrona punktu końcowego w usłudze Microsoft Defender w zarządzanej usłudze Google Play. Kliknij ikonę Ochrona punktu końcowego w usłudze Microsoft Defender w wynikach wyszukiwania Aplikacji.

    :::image type="content" source="images/0f79cb37900b57c3e2bb0effad1c19cb.png" alt-text="Strona Zarządzane usługi Google Play w portalu centrum Microsoft Endpoint Manager administracyjnego" lightbox="images/0f79cb37900b57c3e2bb0effad1c19cb.png":::

3. Na stronie Opis aplikacji, która zostanie wyświetlony następny, powinny być możliwe wyświetlanie szczegółów aplikacji w programie Defender for Endpoint. Przejrzyj informacje na stronie, a następnie wybierz pozycję **Zatwierdź**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/07e6d4119f265037e3b80a20a73b856f.png" alt-text="Strona zarządzanej usługi Google Play w portalu centrum Microsoft Endpoint Manager administracyjnego" lightbox="images/07e6d4119f265037e3b80a20a73b856f.png":::
      

4. Otrzymasz uprawnienia, które do działania tej usługi uzyskuje program Defender for Endpoint. Przejrzyj je, a następnie wybierz pozycję **Zatwierdź**.

    :::image type="content" source="images/206b3d954f06cc58b3466fb7a0bd9f74.png" alt-text="Strona zatwierdzania uprawnień w portalu usługi Microsoft Defender 365" lightbox="images/206b3d954f06cc58b3466fb7a0bd9f74.png":::

5. Zostanie przedstawiona strona Ustawienia zatwierdzania. Strona potwierdza preferencje obsługi nowych uprawnień aplikacji, o które może prosić program Defender dla punktu końcowego systemu Android. Przejrzyj wybrane opcje i wybierz preferowaną opcję. Wybierz pozycję **Gotowe**.

    Domyślnie zarządzane usługi Google Play wybiera opcję Zachowaj **zatwierdzone, gdy aplikacja zażąda nowych uprawnień**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ffecfdda1c4df14148f1526c22cc0236.png" alt-text=" Strona ukończenia konfigurowania ustawień zatwierdzania w portalu usługi Microsoft Defender 365" lightbox="images/ffecfdda1c4df14148f1526c22cc0236.png":::

6. Po wybraniu opcji obsługi uprawnień wybierz pozycję Synchronizuj, Ochrona punktu końcowego w usłudze Microsoft Defender z listą aplikacji.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/34e6b9a0dae125d085c84593140180ed.png" alt-text="Okienko synchronizacji w portalu usługi Microsoft Defender 365" lightbox="images/34e6b9a0dae125d085c84593140180ed.png":::

7. Synchronizacja zostanie ukończona za kilka minut.

    :::image type="content" source="images/9fc07ffc150171f169dc6e57fe6f1c74.png" alt-text="Okienko stanu synchronizacji aplikacji na stronie aplikacji systemu Android w portalu usługi Microsoft Defender 365"  lightbox="images/9fc07ffc150171f169dc6e57fe6f1c74.png":::

8. Wybierz przycisk **Odśwież** na ekranie aplikacji systemu Android, Ochrona punktu końcowego w usłudze Microsoft Defender powinien być widoczny na liście aplikacji.

    :::image type="content" source="images/fa4ac18a6333335db3775630b8e6b353.png" alt-text="Strona z wyświetloną zsynchronizowaną aplikacją" lightbox="images/fa4ac18a6333335db3775630b8e6b353.png":::

9. Program Defender for Endpoint obsługuje zasady konfiguracji aplikacji dla urządzeń zarządzanych za pośrednictwem Intune. Funkcji tej można używać do automatycznego wykonywania uprawnień systemu Android, więc użytkownik nie musi akceptować tych uprawnień.

    1. Na stronie **Aplikacje** przejdź do strony **Zasady > zasady konfiguracji aplikacji i > Dodaj > urządzeniach zarządzanych**.

       :::image type="content" source="images/android-mem.png" alt-text="Okienko Zasady konfiguracji aplikacji w portalu centrum Microsoft Endpoint Manager administracyjnego" lightbox="images/android-mem.png":::

    1. Na stronie **Tworzenie zasad konfiguracji aplikacji** wprowadź następujące szczegóły:

        - Nazwa: Ochrona punktu końcowego w usłudze Microsoft Defender.
        - Wybierz **pozycję Enterprise Android** jako platformę.
        - Wybierz **pozycję Profil służbowy tylko** jako Typ profilu.
        - Kliknij **pozycję Wybierz aplikację**, wybierz pozycję **Microsoft Defender ATP**, wybierz przycisk **OK** , a następnie przycisk **Dalej**.

        :::image type="content" source="images/android-create-app.png" alt-text=" Okienko szczegółów skojarzonej aplikacji" lightbox="images/android-create-app.png":::

    1. Na **Ustawienia przejdź** do sekcji Uprawnienia, kliknij pozycję Dodaj, aby wyświetlić listę obsługiwanych uprawnień. W sekcji Dodawanie uprawnień wybierz następujące uprawnienia:

       - Pamięć zewnętrzna (odczyt)
       - Pamięć zewnętrzna (zapis)

       Następnie wybierz przycisk **OK**.

       :::image type="content" source="images/android-create-app-config.png" alt-text="Okienko Dodawanie uprawnień" lightbox="images/android-create-app-config.png":::

    1. Teraz na liście powinny być wyświetlane zarówno uprawnienia, jak i autograntowanie. W tym celu wybierz pozycję Autogrant z listy rozwijanej Stan uprawnień, a następnie wybierz pozycję **Dalej**.

       :::image type="content" source="images/android-auto-grant.png" alt-text="Okienko Stan uprawnień" lightbox="images/android-auto-grant.png":::

    1. Na **stronie Zadania** wybierz grupę użytkowników, do której zostaną przypisane te zasady konfiguracji aplikacji. Kliknij **pozycję Wybierz grupy, aby dołączyć** i wybrać odpowiednie grupy, a następnie wybierz pozycję **Dalej**. Grupa zaznaczona w tym miejscu jest zwykle taką samą grupą, do której można przypisać Ochrona punktu końcowego w usłudze Microsoft Defender dla systemu Android.

       :::image type="content" source="images/android-select-group.png" alt-text="Okienko Zaznaczone grupy" lightbox="images/android-select-group.png":::

    1. Na **następnej stronie Recenzja +** Utwórz przejrzyj wszystkie informacje, a następnie wybierz pozycję **Utwórz**.

        Zasady konfiguracji aplikacji dla usługi Defender dla punktu końcowego automatycznego przesyłania uprawnień magazynu są teraz przypisywane do wybranej grupy użytkowników.

        > [!div class="mx-imgBorder"]
        > :::image type="content" source="images/android-review-create.png" alt-text="Karta Recenzja + tworzenie na stronie Tworzenie zasad konfiguracji aplikacji" lightbox="images/android-review-create.png":::

10. Na liście Właściwości Zadań  \>  \> \> Edytuj wybierz aplikację **Microsoft Defender ATP****.**

   :::image type="content" source="images/mda-properties.png" alt-text="Opcja Edytuj na stronie Właściwości" lightbox="images/mda-properties.png":::

11. Przypisz aplikację jako *wymaganą* do grupy użytkowników. Jest on automatycznie instalowany w *profilu służbowym* podczas następnej synchronizacji urządzenia za pośrednictwem Portal firmy sieci. To zadanie można wykonać, przechodząc do sekcji *Wymagane,* \> **dodaj grupę,** wybierając grupę użytkowników i klikając pozycję **Wybierz**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ea06643280075f16265a596fb9a96042.png" alt-text="Strona Edytowanie aplikacji" lightbox="images/ea06643280075f16265a596fb9a96042.png":::

12. Na stronie **Edytowanie aplikacji** przejrzyj wszystkie informacje wprowadzone powyżej. Następnie wybierz pozycję **Recenzja + Zapisz, a** następnie **ponownie zapisz,** aby rozpocząć zadanie.

### <a name="auto-setup-of-always-on-vpn"></a>Automatyczna konfiguracja always-on VPN

Program Defender for Endpoint obsługuje zasady konfiguracji urządzeń dla urządzeń zarządzanych za pośrednictwem Intune. Tę funkcję można wykorzystać do automatycznej konfiguracji zawsze włączonych sieci **VPN** na zarejestrowanych urządzeniach z systemem Android Enterprise, więc użytkownik końcowy nie musi skonfigurować usługi VPN podczas dołączania.

1. Na **urządzeniach** wybierz **pozycję Profile konfiguracji Utwórz** \> **platformę** \> **profilu dla** \> **systemu Android Enterprise**

   W **zależności od** typu rejestracji urządzenia wybierz ograniczenia dotyczące urządzeń w jednym z następujących obszarze:
   - **W pełni zarządzany, dedykowany i Corporate-Owned służbowy**
   - **Profil służbowy użytkownika**

   Wybierz pozycję **Utwórz**.

   :::image type="content" source="images/1autosetupofvpn.png" alt-text="Element menu Profile konfiguracji w okienku Zasad" lightbox="images/1autosetupofvpn.png":::

2. **Konfiguracja Ustawienia** Podaj **nazwę i** **opis,** aby jednoznacznie zidentyfikować profil konfiguracji.

   :::image type="content" source="images/2autosetupofvpn.png" alt-text="Pola Nazwa i Opis profilu konfiguracji urządzeń w okienku Podstawowe informacje" lightbox="images/2autosetupofvpn.png":::

3. Wybierz **pozycję Łączność** i skonfiguruj sieć VPN:

   - Włącz **opcję Zawsze w sieci VPN**

     Skonfiguruj klienta VPN w profilu służbowym, aby automatycznie łączyć się z siecią VPN, gdy to możliwe. Na danym urządzeniu można skonfigurować tylko jednego klienta VPN dla zawsze na danym urządzeniu, dlatego upewnij się, że na jednym urządzeniu nie wdrożono więcej niż jednej zawsze wdrażanych zasad VPN.

   - Wybierz **pozycję Niestandardowe** na liście rozwijanej klienta sieci VPN

     W tym przypadku niestandardowa sieć VPN to usługa Defender for Endpoint VPN, która jest używana do zapewnienia funkcji ochrony sieci Web.

     > [!NOTE]
     > Ochrona punktu końcowego w usłudze Microsoft Defender musi być zainstalowana na urządzeniu użytkownika, aby umożliwić automatyczne konfigurowanie tej sieci VPN.

   - Wprowadź **identyfikator przesyłki** ze sklepu Ochrona punktu końcowego w usłudze Microsoft Defender Google Play. W przypadku adresu URL <https://play.google.com/store/apps/details?id=com.microsoft.scmx>aplikacji Defender identyfikator pakietu to **com.microsoft.scmx**

   - **Tryb blokowania** Nieskonfigurowane (domyślne)

     :::image type="content" source="images/3autosetupofvpn.png" alt-text="Okienko Łączność na karcie Ustawienia konfiguracji" lightbox="images/3autosetupofvpn.png":::

4. **Zadanie**

   Na **stronie Zadania** wybierz grupę użytkowników, do której zostaną przypisane te zasady konfiguracji aplikacji. Wybierz **pozycję Wybierz grupy** do dołączyć i wybrać odpowiednie grupy, a następnie wybierz przycisk **Dalej**. Grupa zaznaczona w tym miejscu jest zwykle taką samą grupą, do której można przypisać Ochrona punktu końcowego w usłudze Microsoft Defender dla systemu Android.

   :::image type="content" source="images/4autosetupofvpn.png" alt-text="Okienko zadań profilu konfiguracji urządzeń w ograniczeniach dotyczących urządzeń" lightbox="images/4autosetupofvpn.png":::

5. Na **następnej stronie Recenzja +** Utwórz przejrzyj wszystkie informacje, a następnie wybierz pozycję **Utwórz**.
Profil konfiguracji urządzenia zostanie przypisany do wybranej grupy użytkowników.

   :::image type="content" source="images/5autosetupofvpn.png" alt-text="A devices configuration profile's provision for Review + create" lightbox="images/5autosetupofvpn.png":::

## <a name="check-status-and-complete-onboarding"></a>Sprawdzanie stanu i pełne dołączanie

1. Potwierdź stan instalacji pakietu Ochrona punktu końcowego w usłudze Microsoft Defender Android, klikając pozycję **Stan instalacji urządzenia**. Sprawdź, czy urządzenie jest wyświetlane w tym miejscu.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/900c0197aa59f9b7abd762ab2b32e80c.png" alt-text="Okienko stanu instalacji urządzenia" lightbox="images/900c0197aa59f9b7abd762ab2b32e80c.png":::

2. Na urządzeniu możesz sprawdzić stan dołączania, przechodząc do **profilu służbowego**. Upewnij się, że program Defender for Endpoint jest dostępny i że jesteś zarejestrowany na urządzeniach należących **do Ciebie z profilem służbowym**. Jeśli korzystasz z w pełni zarządzanego urządzenia użytkownika należącego do firmy, będziesz mieć pojedynczy profil na urządzeniu **,** na którym możesz potwierdzić, że program Defender for Endpoint jest dostępny.

    :::image type="content" source="images/c2e647fc8fa31c4f2349c76f2497bc0e.png" alt-text="Okienko wyświetlania aplikacji" lightbox="images/c2e647fc8fa31c4f2349c76f2497bc0e.png":::

3. Po zainstalowaniu aplikacji otwórz ją i zaakceptuj odpowiednie uprawnienia, a wówczas dołączanie powinno się powiodło.

    :::image type="content" source="images/MDE_new.png" alt-text="Th display of a Ochrona punktu końcowego w usłudze Microsoft Defender application on a mobile device" lightbox="images/MDE_new.png":::

4. Na tym etapie urządzenie jest pomyślnie dołączane do programu Defender dla punktu końcowego w systemie Android. Możesz to sprawdzić w portalu [Microsoft 365 Defender,](https://security.microsoft.com) przechodząc do strony **Spis** urządzeń.

    :::image type="content" source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" alt-text="Portal Ochrona punktu końcowego w usłudze Microsoft Defender użytkowników" lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android](microsoft-defender-endpoint-android.md)
- [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android](android-configure.md)
