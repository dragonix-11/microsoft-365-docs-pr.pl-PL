---
title: Konfigurowanie programu Microsoft Defender dla funkcji punktu końcowego w systemie Android
description: W tym artykule opisano sposób konfigurowania programu Microsoft Defender dla punktu końcowego w systemie Android
keywords: microsoft, defender, Microsoft Defender for Endpoint, mde, android, configuration
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
ms.openlocfilehash: 22e0eed3becebdcb3dee4c31ddc7659651bac71f
ms.sourcegitcommit: e3bff611439354e6339bb666a88682078f32ec13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2022
ms.locfileid: "62974013"
---
# <a name="configure-defender-for-endpoint-on-android-features"></a>Konfigurowanie usługi Defender dla funkcji punktu końcowego w systemie Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="conditional-access-with-defender-for-endpoint-on-android"></a>Dostęp warunkowy z usługą Defender dla punktu końcowego w systemie Android

Program Microsoft Defender dla punktu końcowego w systemie Android wraz Microsoft Intune i Azure Active Directory umożliwia wymuszanie zgodności urządzeń i zasad dostępu warunkowego na podstawie poziomów ryzyka urządzeń. Defender for Endpoint is a Mobile Threat Defense (MTD) solution that you can deploy to leverage this capability through Intune.

Aby uzyskać więcej informacji na temat sposobu skonfigurowania programu Defender dla punktu końcowego w systemie Android i dostępu warunkowego, zobacz [Defender for Endpoint (Punkt końcowy) i Intune (Intune](/mem/intune/protect/advanced-threat-protection)).

## <a name="configure-custom-indicators"></a>Konfigurowanie wskaźników niestandardowych

> [!NOTE]
> Program Defender for Endpoint w systemie Android obsługuje tworzenie wskaźników niestandardowych tylko dla adresów IP i adresów URL/domen.

Program Defender for Endpoint w systemie Android umożliwia administratorom skonfigurowanie wskaźników niestandardowych do obsługi urządzeń z systemem Android. Aby uzyskać więcej informacji na temat konfigurowania wskaźników niestandardowych, zobacz [Zarządzanie wskaźnikami](manage-indicators.md).

## <a name="configure-web-protection"></a>Konfigurowanie ochrony sieci Web
Program Defender for Endpoint w systemie Android umożliwia administratorom systemów informatycznych konfigurowanie funkcji ochrony sieci Web. Ta funkcja jest dostępna w centrum Microsoft Endpoint Manager administracyjnego.

> [!NOTE]
> Usługa Defender for Endpoint w systemie Android korzystałaby z połączenia VPN w celu zapewnienia funkcji ochrony sieci Web. Nie jest to zwykły sieci VPN i jest to lokalny/samopętny vpn, który nie przejmuje ruchu poza urządzenie.
> Aby uzyskać więcej informacji, zobacz [Konfigurowanie ochrony sieci Web na urządzeniach z systemem Android](/mem/intune/protect/advanced-threat-protection-manage-android).

## <a name="privacy-controls"></a>Mechanizmy kontroli prywatności

> [!IMPORTANT]
> Mechanizmy kontroli prywatności dla programu Microsoft Defender for Endpoint w systemie Android są w wersji Preview. Poniższe informacje dotyczą wstępnie dzierżawionych produktów, które mogą ulec znacznej modyfikacji przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

Dostępne są następujące mechanizmy kontroli prywatności dotyczące konfigurowania danych wysyłanych przez usługę Defender for Endpoint z urządzeń z systemem Android:

|Raport zagrożeń     |Szczegóły      |
|--------------------|-------------|
|Raport złośliwego oprogramowania |Administratorzy mogą skonfigurować raport ochrony prywatności dla złośliwego oprogramowania — jeśli prywatność jest włączona, program Defender dla punktu końcowego nie będzie wysyłać nazwy aplikacji złośliwego oprogramowania ani innych szczegółów aplikacji w ramach raportu alertu o złośliwym oprogramowaniu |
|Raport phish |Administratorzy mogą skonfigurować kontrolę prywatności dla raportów wyłudzyowych — jeśli włączono ochronę prywatności, program Defender dla punktu końcowego nie wyśle nazwy domeny ani szczegółów niebezpiecznej witryny sieci Web w ramach raportu alertu o wiadomościach wyłudzywowych |
|Ocena luk w zabezpieczeniach aplikacji (tylko system Android) |Domyślnie w celu oceny luk w zabezpieczeniach są wysyłane tylko informacje o aplikacjach zainstalowanych w profilu służbowym. Administratorzy mogą wyłączyć prywatność, aby uwzględnić aplikacje osobiste|

## <a name="configure-vulnerability-assessment-of-apps-for-byod-devices"></a>Konfigurowanie oceny luk w zabezpieczeniach aplikacji dla urządzeń BYOD

W wersji 1.0.3425.0303 programu Microsoft Defender dla punktu końcowego dla systemu Android będzie można uruchamiać oceny luk w zabezpieczeniach systemu operacyjnego i aplikacji zainstalowanych na urządzeniach przenośnych.

> [!NOTE]
> Ocena luk w zabezpieczeniach jest częścią [zarządzania zagrożeniami i lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md) w programie Microsoft Defender for Endpoint. 

**Uwagi dotyczące prywatności związane z aplikacjami z urządzeń osobistych (BYOD):**

- W przypadku Enterprise z systemem Android z profilem służbowym będą obsługiwane tylko aplikacje zainstalowane w profilu służbowym.
- W przypadku innych trybów BYOD ocena luk w zabezpieczeniach aplikacji domyślnie nie **będzie** włączona. Gdy jednak urządzenie jest w trybie administratora, administratorzy mogą jawnie włączyć tę funkcję za pośrednictwem programu Microsoft Endpoint Manager, aby uzyskać listę aplikacji zainstalowanych na urządzeniu. Aby uzyskać więcej informacji, zobacz szczegóły poniżej.

### <a name="configure-privacy-for-device-administrator-mode"></a>Konfigurowanie prywatności dla trybu administratora urządzenia

Aby włączyć ocenę luk **w zabezpieczeniach** aplikacji na urządzeniach w trybie **administratora** urządzenia dla użytkowników docelowych, należy wykonać poniższe czynności. 

> [!NOTE]
> Ta opcja jest domyślnie wyłączona dla urządzeń zarejestrowanych w trybie administratora urządzeń.

1. W [Microsoft Endpoint Manager administracyjnego](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do **strony UrządzeniaKonfigurowanie** >  >  **profilówTworzenie profilu** i wprowadź następujące ustawienia:

   - **Platforma**: Wybierz pozycję Administrator urządzeń z systemem Android
   - **Profil**: Wybierz pozycję "Niestandardowe" i kliknij pozycję Utwórz

2. W **sekcji Podstawy** określ nazwę i opis profilu.

3. W **ustawieniach konfiguracji** wybierz pozycję Dodaj ustawienie **OMA-URI** :

   - **Nazwa**: Wprowadź unikatową nazwę i opis tego ustawienia usługi OMA-URI, aby można je było łatwo później znaleźć.
   - OMA-URI: **./Vendor/MSFT/DefenderATP/DefenderTVMPrivacyMode**
   - Typ danych: Z listy rozwijanej wybierz pozycję Integer (Liczba całkowita).
   - Wartość: Wprowadź wartość 0, aby wyłączyć ustawienie prywatności (domyślna wartość to 1)

4. Kliknij **przycisk Dalej** i przypisz ten profil do urządzeń/użytkowników docelowych.

### <a name="configure-privacy-for-android-enterprise-work-profile"></a>Konfigurowanie prywatności w profilu służbowym Enterprise w systemie Android

Program Defender for Endpoint obsługuje ocenę luk w zabezpieczeniach aplikacji w profilu służbowym. Jednak jeśli chcesz wyłączyć tę funkcję dla użytkowników docelowych, możesz wykonać następujące czynności:

1. W [Microsoft Endpoint Manager administracyjnego i](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do **pozycji Zasady** >  **konfiguracji aplikacjiAppAddZa** >  >  **zarządzania urządzeniami**.
2. Nadaj zasadom nazwę. **Platform > Android Enterprise**; wybierz typ profilu.
3. Wybierz **pozycję Microsoft Defender for Endpoint** jako aplikację docelową.
4. In Ustawienia page, select **Use configuration designer and** **add DefenderTVMPrivacyMode** as the key and value type as **Integer**
   - Aby wyłączyć luki w zabezpieczeniach aplikacji w profilu służbowym, wprowadź wartość tych zasad `1` i przypisz je użytkownikom. Domyślnie ta wartość jest ustawiona na `0`.
   - W przypadku użytkowników z kluczem ustawionym jako `0`, usługa Defender for Endpoint wyśle listę aplikacji z profilu służbowego do usługi zaplecza w celu oceny luk w zabezpieczeniach.
5. Kliknij **przycisk Dalej** i przypisz ten profil do urządzeń/użytkowników docelowych.

Włączenie lub wyłączenie powyższych kontrolek prywatności nie ma wpływu na sprawdzanie zgodności urządzenia ani dostęp warunkowy.

## <a name="configure-privacy-for-phishing-alert-report"></a>Konfigurowanie prywatności dla raportu alertu wyłudzania informacji

Za pomocą funkcji kontroli prywatności dla raportów o wyłudach można wyłączyć zbiór nazw domen lub informacji o witrynach internetowych w raporcie o zagrożeniach tego rodzaju. Zapewnia to organizacjom elastyczność w zakresie wyboru, czy chcą zbierać nazwę domeny w przypadku wykrycia i zablokowania złośliwej lub wyłudzonych informacji witryny internetowej przez usługę Defender for Endpoint.

### <a name="configure-privacy-for-phishing-alert-report-on-android-device-administrator-enrolled-devices"></a>Konfigurowanie prywatności dla raportu alertu wyłudzającego informacje na urządzeniach zarejestrowanych przez administratora urządzeń z systemem Android:

Aby włączyć ją dla użytkowników docelowych, należy wykonać następujące czynności:

1. W [Microsoft Endpoint Manager administracyjnego](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do **strony UrządzeniaKonfigurowanie** >  >  **profilówTworzenie profilu** i wprowadź następujące ustawienia:

   - **Platforma**: Wybierz pozycję Administrator urządzeń z systemem Android.
   - **Profil**: Wybierz pozycję "Niestandardowe" i kliknij pozycję **Utwórz**.

2. W **sekcji Podstawy** określ nazwę i opis profilu.

3. W **ustawieniach konfiguracji** wybierz pozycję Dodaj ustawienie **OMA-URI** :

   - **Nazwa**: Wprowadź unikatową nazwę i opis tego ustawienia usługi OMA-URI, aby można je było łatwo później znaleźć.
   - OMA-URI: **./Vendor/MSFT/DefenderATP/DefenderExcludeURLInReport**
   - Typ danych: Z listy rozwijanej wybierz pozycję Integer (Liczba całkowita).
   - Wartość: Wprowadź wartość 1, aby włączyć ustawienie prywatności. Wartość domyślna to 0.

4. Kliknij **przycisk Dalej** i przypisz ten profil do urządzeń/użytkowników docelowych.

Korzystanie z tej kontroli prywatności nie ma wpływu na sprawdzanie zgodności urządzenia ani dostęp warunkowy.

### <a name="configure-privacy-for-phishing-alert-report-on-android-enterprise-work-profile"></a>Konfigurowanie prywatności dla raportu alertu o wyłudzaniu informacji Enterprise w profilu służbowym systemu Android

Aby włączyć prywatność dla użytkowników docelowych w profilu służbowym, należy wykonać następujące czynności:

1. W [Microsoft Endpoint Manager administracyjnego i](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do **pozycji Zasady** >  **konfiguracji aplikacjiAppAddZa** >  >  **zarządzania urządzeniami**.
2. Nadaj zasadom nazwę, **platformę > dla Enterprise Android**, wybierz typ profilu.
3. Wybierz **pozycję Microsoft Defender for Endpoint** jako aplikację docelową.
4. Na Ustawienia wybierz pozycję Użyj projektanta **konfiguracji** i dodaj **wartość DefenderExcludeURLInReport** jako wartość typu **Integer.**
   - Wprowadź **wartość 1, aby włączyć prywatność**. Wartość domyślna to 0.
5. Kliknij **przycisk Dalej** i przypisz ten profil do urządzeń/użytkowników docelowych.

Włączenie lub wyłączenie powyższych kontrolek prywatności nie ma wpływu na sprawdzanie zgodności urządzenia ani dostęp warunkowy.

## <a name="configure-privacy-for-malware-threat-report"></a>Konfigurowanie prywatności pod kątem raportu o zagrożeniach w złośliwym oprogramowaniu

Za pomocą funkcji kontroli prywatności raport o zagrożeniach przed złośliwym oprogramowaniem można wyłączyć zbiór szczegółów aplikacji (informacje o nazwie i pakiecie) z raportu o zagrożeniach złośliwym oprogramowaniem. Zapewnia to organizacjom elastyczność w zakresie wyboru, czy chcą zbierać nazwę aplikacji po wykryciu złośliwej aplikacji.

### <a name="configure-privacy-for-malware-alert-report-on-android-device-administrator-enrolled-devices"></a>Konfigurowanie prywatności raportu alertów o złośliwym oprogramowaniu na urządzeniach zarejestrowanych przez administratora urządzeń z systemem Android:

Aby włączyć ją dla użytkowników docelowych, należy wykonać następujące czynności:

1. W [Microsoft Endpoint Manager administracyjnego](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do **strony UrządzeniaKonfigurowanie** >  >  **profilówTworzenie** profilu i wprowadź następujące ustawienia:

   - **Platforma**: Wybierz pozycję Administrator urządzeń z systemem Android.
   - **Profil**: Wybierz pozycję "Niestandardowe" i kliknij pozycję **Utwórz**.

2. W **sekcji Podstawy** określ nazwę i opis profilu.

3. W **ustawieniach konfiguracji** wybierz pozycję Dodaj ustawienie **OMA-URI** :

   - **Nazwa**: Wprowadź unikatową nazwę i opis tego ustawienia usługi OMA-URI, aby można je było łatwo później znaleźć.
   - OMA-URI: **./Vendor/MSFT/DefenderATP/DefenderExcludeAppInReport**
   - Typ danych: Z listy rozwijanej wybierz pozycję Integer (Liczba całkowita).
   - Wartość: Wprowadź wartość 1, aby włączyć ustawienie prywatności. Wartość domyślna to 0.

4. Kliknij **przycisk Dalej** i przypisz ten profil do urządzeń/użytkowników docelowych.

Korzystanie z tej kontroli prywatności nie ma wpływu na sprawdzanie zgodności urządzenia ani dostęp warunkowy. Na przykład urządzenia ze złośliwą aplikacją zawsze mają poziom ryzyka "Średni".

### <a name="configure-privacy-for-malware-alert-report-on-android-enterprise-work-profile"></a>Konfigurowanie prywatności w raporcie alertów o złośliwym Enterprise w profilu służbowym systemu Android

Aby włączyć prywatność dla użytkowników docelowych w profilu służbowym, należy wykonać następujące czynności:

1. W [Microsoft Endpoint Manager administracyjnego i](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do **pozycji Zasady** >  **konfiguracji aplikacjiAppAddZa** >  >  **zarządzania urządzeniami**.
2. Nadaj zasadom nazwę, **platformę > dla Enterprise Android**, wybierz typ profilu.
3. Wybierz **pozycję Microsoft Defender for Endpoint** jako aplikację docelową.
4. In Ustawienia page, select **Use configuration designer** and **add DefenderExcludeAppInReport** as the key and value type as **Integer**
   - Wprowadź **wartość 1, aby włączyć prywatność**. Wartość domyślna to 0.
5. Kliknij **przycisk Dalej** i przypisz ten profil do urządzeń/użytkowników docelowych.

Korzystanie z tej kontroli prywatności nie ma wpływu na sprawdzanie zgodności urządzenia ani dostęp warunkowy. Na przykład urządzenia ze złośliwą aplikacją zawsze mają poziom ryzyka "Średni".

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie programu Microsoft Defender dla punktu końcowego w systemie Android](microsoft-defender-endpoint-android.md)
- [Wdrażanie programu Microsoft Defender dla punktu końcowego w systemie Android za pomocą Microsoft Intune](android-intune.md)
