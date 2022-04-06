---
title: Wdrażanie oparte na aplikacji dla aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender systemie iOS
ms.reviewer: ''
description: W tym artykule opisano Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS przy użyciu aplikacji
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, ios, aplikacja, instalacja, wdrożenie, dezinstalacja, intune
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 239d16bdbdb3fd7770061a91d77a3f190cfb8f4a
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476186"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-ios"></a>Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

W tym temacie opisano wdrażanie usługi Defender for Endpoint w systemie iOS Intune — Portal firmy urządzeniach zarejestrowanych. Aby uzyskać więcej informacji na Intune rejestracji urządzeń, zobacz Rejestrowanie urządzeń [z systemem iOS/iPadOS w aplikacji Intune](/mem/intune/enrollment/ios-enroll).

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Upewnij się, że masz dostęp do [centrum administracyjnego programu Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

- Upewnij się, że rejestracja w systemie iOS jest wykonywana dla użytkowników. Użytkownicy muszą mieć przypisaną licencję usługi Defender for Endpoint, aby korzystać z usługi Defender for Endpoint w systemie iOS. Aby uzyskać [instrukcje dotyczące przypisywania licencji,](/azure/active-directory/users-groups-roles/licensing-groups-assign) zobacz Przypisywanie licencji użytkownikom.

> [!NOTE]
> Ochrona punktu końcowego w usłudze Microsoft Defender iOS jest dostępna w sklepie [Apple App Store](https://aka.ms/mdatpiosappstore).

## <a name="deployment-steps"></a>Kroki wdrażania

Wdeksuj usługę Defender dla punktu końcowego w systemie iOS za pośrednictwem Intune — Portal firmy.

### <a name="add-ios-store-app"></a>Dodaj aplikację ze sklepu iOS

1. W [centrum administracyjnym menedżera punktu końcowego firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do aplikacji sklepu **AppsiOS** -> **/iPadOSAddiOS** ->  ->  i kliknij pozycję **Wybierz**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-1.png" alt-text="Karta Dodawanie aplikacji w centrum administracyjnym Microsoft Endpoint Manager administracyjnego" lightbox="images/ios-deploy-1.png":::

1. Na stronie **Dodawanie aplikacji** kliknij pozycję Wyszukaj w **App Store** i **wpisz Ochrona punktu końcowego w usłudze Microsoft Defender** na pasku wyszukiwania. W sekcji wyników wyszukiwania kliknij pozycję *Ochrona punktu końcowego w usłudze Microsoft Defender i kliknij* pozycję **Wybierz**.

1. Wybierz **system operacyjny iOS 11.0** . Przejrzyj pozostałe informacje o aplikacji i kliknij przycisk **Dalej**.

1. W **sekcji Zadania przejdź** do sekcji **Wymagane i wybierz** pozycję **Dodaj grupę**. Następnie możesz wybrać grupy użytkowników, do których chcesz kierować program Defender na punkt końcowy w aplikacji systemu iOS. Kliknij **pozycję Wybierz** , a następnie **przycisk Dalej**.

    > [!NOTE]
    > Wybrana grupa użytkowników powinna składać się z Intune zarejestrowanych użytkowników.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-2.png" alt-text="Karta Dodawanie grupy w centrum Microsoft Endpoint Manager administracyjnego" lightbox="images/ios-deploy-2.png":::

1. W sekcji *Recenzja + Utwórz* sprawdź, czy wszystkie wprowadzone informacje są poprawne, a następnie wybierz pozycję **Utwórz**. W chwili obecnej aplikacja Defender for Endpoint powinna zostać pomyślnie utworzona, a w prawym górnym rogu strony powinno zostać wyświetlane powiadomienie.

1. Na wyświetlonej stronie z informacjami o aplikacji w sekcji **Monitor** wybierz pozycję Stan  instalacji urządzenia, aby sprawdzić, czy instalacja urządzenia została ukończona pomyślnie.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-3.png" alt-text="Strona stanu instalacji urządzenia" lightbox="images/ios-deploy-3.png":::

## <a name="complete-deployment-for-supervised-devices"></a>Pełne wdrożenie urządzeń nadzorowanych

Aplikacja Ochrona punktu końcowego w usłudze Microsoft Defender na urządzeniach z systemem iOS ma wyspecjalizowaną możliwość pracy na urządzeniach z systemem iOS/iPadOS nadzorowanych ze względu na zwiększone możliwości zarządzania zapewniane przez platformę na tych typach urządzeń. Może również zapewniać ochronę sieci Web **bez konfigurowania lokalnego połączenia VPN na urządzeniu**. Zapewnia to użytkownikom konieczną ochronę przed wyłudzaniem informacji i innymi atakami internetowymi.

### <a name="configure-supervised-mode-via-intune"></a>Konfigurowanie trybu nadzórowanego za pośrednictwem Intune

Następnie skonfiguruj tryb nadzorowany dla aplikacji Defender for Endpoint za pośrednictwem App Configuration końcowych.

   > [!NOTE]
   > Te zasady konfiguracji aplikacji dla urządzeń nadzorowanych mają zastosowanie tylko do urządzeń zarządzanych i powinny być kierowane do WSZYSTKICH zarządzanych urządzeń z systemem iOS jako najlepszego rozwiązania.

1. Zaloguj się do centrum [Microsoft Endpoint Manager administracyjnego aplikacji](https://go.microsoft.com/fwlink/?linkid=2109431) i przejdź do **pozycji Zasady** \> **konfiguracji aplikacji Dodaj** \> **.** Wybierz **pozycję Urządzenia zarządzane**.

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager administracyjnego4.](images/ios-deploy-4.png)

1. Na *stronie Tworzenie zasad konfiguracji aplikacji* podaj następujące informacje:
    - Nazwa zasad
    - Platforma: wybierz pozycję iOS/iPadOS
    - Aplikacja docelowa: wybierz **Ochrona punktu końcowego w usłudze Microsoft Defender** z listy

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager administracyjnego5.](images/ios-deploy-5.png)

1. Na następnym ekranie wybierz **pozycję Użyj projektanta konfiguracji** jako formatu. Określ następującą właściwość:
    - Klucz konfiguracji: issupervised
    - Typ wartości: Ciąg
    - Wartość konfiguracji: {{issupervised}}

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager administracyjnego6.](images/ios-deploy-6.png)

1. Wybierz **pozycję** Dalej, aby otworzyć **stronę Tagi zakresu** . Tagi zakresu są opcjonalne. Wybierz przycisk **Dalej**, aby kontynuować.

1. Na **stronie Zadania** wybierz grupy, które otrzymają ten profil. W tym scenariuszu najlepszym rozwiązaniem jest kierowanie wszystkich **urządzeń**. Aby uzyskać więcej informacji na temat przypisywania profilów, zobacz [Przypisywanie profilów użytkowników i urządzeń](/mem/intune/configuration/device-profile-assign).

   Podczas wdrażania w grupach użytkowników użytkownik musi zalogować się na urządzeniu, zanim zasady będą stosowane.

   Kliknij **Dalej**.

1. Na stronie **Przeglądanie + tworzenie** po zakończeniu wybierz pozycję **Utwórz**. Nowy profil zostanie wyświetlony na liście profilów konfiguracji.

1. Następnie należy wdrożyć profil niestandardowy na urządzeniach z systemem iOS nadzorowanych. Jest to ulepszone funkcje ochrony przed wyłudzaniem informacji. Wykonaj poniższe czynności:

    - Pobierz profil konfiguracji z [https://aka.ms/mdeiosprofilesupervised](https://aka.ms/mdeiosprofilesupervised)
    - Przejdź do **strony DevicesiOS** -> **/iPadOSKonfiguracja** ->  **profilesTworzenie profilu** -> 

    > [!div class="mx-imgBorder"]
    > ![Obraz Microsoft Endpoint Manager administracyjnego7.](images/ios-deploy-7.png)
    
    - Podaj nazwę profilu. Po wyświetleniu monitu o zaimportowanie pliku profilu konfiguracji wybierz plik pobrany z poprzedniego kroku.
    - W sekcji **Zadanie** wybierz grupę urządzeń, do której chcesz zastosować ten profil. Najlepszym rozwiązaniem jest zastosowanie tej zasady do wszystkich zarządzanych urządzeń z systemem iOS. Wybierz pozycję **Dalej**.
    - Na stronie **Przeglądanie + tworzenie** po zakończeniu wybierz pozycję **Utwórz**. Nowy profil zostanie wyświetlony na liście profilów konfiguracji.


## <a name="auto-onboarding-of-vpn-profile-simplified-onboarding"></a>Automatyczne dołączanie profilu VPN (uproszczone dołączanie)

W przypadku urządzeń niewidomych sieć VPN jest używana w celu zapewnienia funkcji ochrony sieci Web. Nie jest to zwykły sieci VPN i jest to lokalny/samopętny vpn, który nie przejmuje ruchu poza urządzenie.

>[!NOTE]
>W przypadku urządzeń nadzorowanych sieć VPN nie jest potrzebna na potrzeby funkcji ochrony sieci Web i wymaga od administratorów konfigurowania profilu konfiguracji na urządzeniach nadzorowanych. Aby skonfigurować urządzenia nadzorowane, postępuj zgodnie z instrukcjami w sekcji Pełne [wdrożenie urządzeń](#complete-deployment-for-supervised-devices) nadzorowanych.

Administratorzy mogą skonfigurować automatyczną konfigurację profilu VPN. Spowoduje to automatyczną konfigurację profilu VPN programu Defender dla punktu końcowego bez konieczności korzystania z tej usługi podczas dołączania. 

Ten krok upraszcza proces dołączania przez skonfigurowanie profilu VPN. Aby uzyskać środowisko w trybie zerowego dotyku lub dyskretnego dołączania, zobacz następną sekcję: [Tablica](#zero-touch-onboarding-of-microsoft-defender-for-endpoint-preview) bez dotyku.

1. W [centrum administracyjnym menedżera punktu końcowego firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do **strony** **DevicesConfiguration** ->  **ProfilesTworzenie** ->  profilu.
1. Wybierz **platformę w** systemie **iOS/iPadOS** i **wybierz typ profilu jako** **VPN**. Kliknij **przycisk Utwórz**.
1. Wpisz nazwę profilu i kliknij przycisk **Dalej**.
1. Wybierz **pozycję Niestandardowy vpn** dla typu połączenia i w sekcji **Base VPN** (Bazowy interfejs VPN) wprowadź następujące informacje:
    - Nazwa połączenia = Ochrona punktu końcowego w usłudze Microsoft Defender
    - Adres serwera VPN = 127.0.0.1
    - Metoda uwierzytelniania = "Nazwa użytkownika i hasło"
    - Rozdzielanie rozdzielane = Wyłącz
    - Identyfikator VPN = com.microsoft.scmx
    - W parach klucz-wartość wprowadź klucz **Autoonboard** i ustaw wartość **Prawda**.
    - Typ automatycznego połączenia VPN = VPN na żądanie
    - Kliknij **pozycję Dodaj** **reguły na żądanie** i wybierz pozycję Chcę wykonać następujące **czynności = Ustanawianie sieci VPN**, chcę **ograniczyć do = Wszystkie domeny**.

    :::image type="content" source="images/ios-deploy-8.png" alt-text="Karta Ustawienia konfiguracji profilu SIECI VPN" lightbox="images/ios-deploy-8.png":::

1. Kliknij przycisk Dalej i przypisz profil do użytkowników docelowych.
1. W sekcji *Recenzja + Utwórz* sprawdź, czy wszystkie wprowadzone informacje są poprawne, a następnie wybierz pozycję **Utwórz**.

## <a name="zero-touch-onboarding-of-microsoft-defender-for-endpoint-preview"></a>Dołączanie do programu w trybie Ochrona punktu końcowego w usłudze Microsoft Defender (wersja Preview)

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wypuszczonych produktów, które mogą zostać znacząco zmodyfikowane przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

> [!NOTE]
> Na urządzeniach z systemem iOS, które zostały zarejestrowane bez chętnych użytkowników (urządzeń o mniejszej obsługi lub urządzeń współużytkonych), nie można skonfigurować obsługi zerowej obsługi dotykowej.

Administratorzy mogą skonfigurować Ochrona punktu końcowego w usłudze Microsoft Defender w celu dyskretnego wdrażania i aktywowania. W tym przepływie administrator tworzy profil wdrożenia, a użytkownik jest po prostu powiadamiany o instalacji. Program Defender for Endpoint jest instalowany automatycznie bez konieczności otwierania aplikacji przez użytkownika. Wykonaj poniższe czynności, aby skonfigurować zerowe dotykowe lub dyskretne wdrażanie usługi Defender dla punktu końcowego na zarejestrowanych urządzeniach z systemem iOS:

1. W [centrum administracyjnym menedżera punktu końcowego firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do **strony** **DevicesConfiguration** >  **ProfilesTworzenie** >  profilu.
1. Wybierz **platformę w** systemie **iOS/iPadOS** i **wybierz typ profilu jako** **VPN**. Wybierz pozycję **Utwórz**.
1. Wpisz nazwę profilu i wybierz pozycję **Dalej**.
1. Wybierz **pozycję Niestandardowy vpn** dla typu połączenia i w sekcji **Base VPN** (Bazowy interfejs VPN) wprowadź następujące informacje:
    - Nazwa połączenia = Ochrona punktu końcowego w usłudze Microsoft Defender
    - Adres serwera VPN = 127.0.0.1
    - Metoda uwierzytelniania = "Nazwa użytkownika i hasło"
    - Rozdzielanie rozdzielane = Wyłącz
    - Identyfikator VPN = com.microsoft.scmx
    - W parach klucz-wartość wprowadź klucz **SilentOnboard** i ustaw wartość **Prawda**.
    - Typ automatycznego połączenia VPN = VPN na żądanie
    - Wybierz **pozycję Dodaj** reguły **na żądanie** i wybierz pozycję Chcę wykonać następujące **czynności = Ustanawianie połączenia VPN**, chcę **ograniczyć do = Wszystkie domeny**.

    :::image type="content" source="images/ios-deploy-9.png" alt-text="Strona Konfiguracja profilu SIECI VPN" lightbox="images/ios-deploy-9.png":::

1. Wybierz **pozycję Dalej** i przypisz profil do użytkowników docelowych.
1. W sekcji *Recenzja + Utwórz* sprawdź, czy wszystkie wprowadzone informacje są poprawne, a następnie wybierz pozycję **Utwórz**.

Po zakończeniu powyższej konfiguracji i zsynchronizowaniu jej z urządzeniem na docelowych urządzeniach z systemem iOS są wykonywane następujące akcje:
    - Ochrona punktu końcowego w usłudze Microsoft Defender zostaną wdrożone i w trybie dyskretnym, a urządzenie będzie widoczne w portalu usługi Defender for Endpoint.
    - Do urządzenia użytkownika zostanie wysłane powiadomienie z powiadomieniem.
    - Zostanie aktywowana ochrona sieci Web i inne funkcje.

   > [!NOTE]
   > W przypadku urządzeń nadzorowanych, chociaż profil VPN nie jest wymagany, administratorzy nadal mogą skonfigurować dołączanie zerowym dotknięciem, konfigurując profil VPN programu Defender for Endpoint za pośrednictwem Intune. Profil VPN zostanie wdrożony na urządzeniu, ale będzie prezentowany tylko na urządzeniu jako profil przechodnia i można go usunąć po początkowym dodaniu.

## <a name="complete-onboarding-and-check-status"></a>Zakończenie dołączania i sprawdzanie stanu

1. Gdy program Defender for Endpoint w systemie iOS zostanie zainstalowany na urządzeniu, zobaczysz ikonę aplikacji.

    :::image type="content" source="images/41627a709700c324849bf7e13510c516.png" alt-text="Automatycznie wygenerowany opis smartfonu" lightbox="images/41627a709700c324849bf7e13510c516.png":::

2. Naciśnij ikonę aplikacji Defender for Endpoint (MSDefender) i postępuj zgodnie z wyświetlanymi na ekranie instrukcjami, aby ukończyć procedurę dołączania. Szczegóły obejmują akceptowanie przez użytkownika końcowego uprawnień systemu iOS wymaganych przez program Defender dla punktu końcowego w systemie iOS.

3. Po pomyślnym rozpoczęciu dołączania urządzenie zacznie być wyświetlane na liście Urządzenia w Microsoft 365 Defender sieci.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/device-inventory-screen.png" alt-text="Strona spisu urządzeń" lightbox="images/device-inventory-screen.png":::

## <a name="configure-microsoft-defender-for-endpoint-for-supervised-mode"></a>Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender dla trybu nadzorowanego

Aplikacja Ochrona punktu końcowego w usłudze Microsoft Defender na urządzeniach z systemem iOS ma wyspecjalizowaną możliwość pracy na urządzeniach z systemem iOS/iPadOS nadzorowanych ze względu na zwiększone możliwości zarządzania zapewniane przez platformę na tych typach urządzeń. Aby można było korzystać z tych funkcji, aplikacja Defender for Endpoint musi wiedzieć, czy urządzenie jest w trybie nadzórnym.

### <a name="configure-supervised-mode-via-intune"></a>Konfigurowanie trybu nadzórowanego za pośrednictwem Intune

Intune umożliwia skonfigurowanie usługi Defender dla aplikacji dla systemu iOS za pośrednictwem App Configuration danych.

   > [!NOTE]
   > Te zasady konfiguracji aplikacji dla urządzeń nadzorowanych mają zastosowanie tylko do urządzeń zarządzanych i powinny być kierowane do wszystkich zarządzanych urządzeń z systemem iOS jako najlepszego rozwiązania.

1. Zaloguj się do centrum [Microsoft Endpoint Manager administracyjnego aplikacji](https://go.microsoft.com/fwlink/?linkid=2109431) i przejdź do **pozycji Zasady** \> **konfiguracji aplikacji Dodaj** \> **.** Kliknij pozycję **Urządzenia zarządzane**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-4.png" alt-text="Opcja Urządzenia zarządzane" lightbox="images/ios-deploy-4.png":::

1. Na *stronie Tworzenie zasad konfiguracji aplikacji* podaj następujące informacje:
    - Nazwa zasad
    - Platforma: wybierz pozycję iOS/iPadOS
    - Aplikacja docelowa: wybierz **Ochrona punktu końcowego w usłudze Microsoft Defender** z listy

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-5.png" alt-text="Podstawowe pola zasad konfiguracji aplikacji" lightbox="images/ios-deploy-5.png":::

1. Na następnym ekranie wybierz **pozycję Użyj projektanta konfiguracji** jako formatu. Określ następującą właściwość:
    - Klucz konfiguracji: issupervised
    - Typ wartości: Ciąg
    - Wartość konfiguracji: {{issupervised}}

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-6.png" alt-text="Strona, z której należy wybrać format ustawień konfiguracji zasad" lightbox="images/ios-deploy-6.png":::

1. Kliknij **przycisk** Dalej, aby otworzyć **stronę Tagi zakresu** . Tagi zakresu są opcjonalne. Kliknij przycisk **Dalej**, aby kontynuować.

1. Na **stronie Zadania** wybierz grupy, które otrzymają ten profil. W tym scenariuszu najlepszym rozwiązaniem jest kierowanie wszystkich **urządzeń**. Aby uzyskać więcej informacji na temat przypisywania profilów, zobacz [Przypisywanie profilów użytkowników i urządzeń](/mem/intune/configuration/device-profile-assign).

   Podczas wdrażania w grupach użytkowników użytkownik musi zalogować się na urządzeniu, zanim zasady będą stosowane.

   Kliknij **Dalej**.

1. Na stronie **Przeglądanie + tworzenie** po zakończeniu wybierz pozycję **Utwórz**. Nowy profil zostanie wyświetlony na liście profilów konfiguracji.

## <a name="next-steps"></a>Następne kroki

- [Konfigurowanie zasad ochrony aplikacji tak, aby uwzględniały usługę Defender dla sygnałów ryzyka punktu końcowego (MAM)](ios-install-unmanaged.md)
- [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu iOS](ios-configure-features.md)
