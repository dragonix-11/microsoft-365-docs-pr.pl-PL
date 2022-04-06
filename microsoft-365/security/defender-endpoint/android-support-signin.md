---
title: Rozwiązywanie problemów z systemem Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android
description: Rozwiązywanie problemów z systemem Ochrona punktu końcowego w usłudze Microsoft Defender Android
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mde, android, chmura, łączność, komunikacja
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
ms.openlocfilehash: 574e02c837ce1f2e3639ed562ed52bacc0e67629
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472226"
---
# <a name="troubleshooting-issues-on-microsoft-defender-for-endpoint-on-android"></a>Rozwiązywanie problemów z systemem Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Podczas dołączania do urządzenia po zainstalowaniu aplikacji mogą pojawić się problemy z logowaniem.

Podczas dołączania po zainstalowaniu aplikacji na urządzeniu mogą wystąpić problemy z logowaniem.

W tym artykule przedstawiono rozwiązania problemów z logowaniem.

## <a name="sign-in-failed---unexpected-error"></a>Logowanie nie powiodło się — nieoczekiwany błąd

**Logowanie nie powiodło się: Nieoczekiwany** *błąd, spróbuj później*

:::image type="content" source="images/f9c3bad127d636c1f150d79814f35d4c.png" alt-text="Błąd logowania nie powiodło się Nieoczekiwany błąd na stronie logowania w portalu usługi Microsoft Defender 365." lightbox="images/f9c3bad127d636c1f150d79814f35d4c.png":::

**Komunikat:**

Nieoczekiwany błąd, spróbuj później

**Przyczyna:**

Na urządzeniu jest zainstalowana starsza wersja aplikacji "Microsoft Authenticator".

**Rozwiązanie:**

Zainstaluj najnowszą wersję i [najnowszą Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator) ze sklepu Google Play i spróbuj ponownie.

## <a name="sign-in-failed---invalid-license"></a>Logowanie nie powiodło się — nieprawidłowa licencja

**Logowanie nie powiodło się:** *Nieprawidłowa licencja, skontaktuj się z administratorem*

:::image type="content" source="images/920e433f440fa1d3d298e6a2a43d4811.png" alt-text="Dane kontaktowe w witrynie internetowej edytowania na stronie logowania w portalu usługi Microsoft Defender 365" lightbox="images/920e433f440fa1d3d298e6a2a43d4811.png":::

**Komunikat: Nieprawidłowa** *licencja, skontaktuj się z administratorem*

**Przyczyna:**

Nie masz przypisanej Microsoft 365 lub Twoja organizacja nie ma licencji na Microsoft 365 Enterprise subskrypcji.

**Rozwiązanie:**

Aby uzyskać pomoc, skontaktuj się z administratorem.

## <a name="report-unsafe-site"></a>Zgłoś niebezpieczną witrynę

Witryny wyłudzujące informacje spersonifikują zaufane witryny internetowe w celu uzyskania informacji osobistych lub finansowych. Odwiedź stronę [Opinie na temat ochrony sieci](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) , jeśli chcesz zgłosić witrynę internetową, która może być witryną wyłudzającą informacje.

## <a name="phishing-pages-arent-blocked-on-some-oem-devices"></a>Strony wyłudzania informacji nie są blokowane na niektórych urządzeniach OEM

**Dotyczy:** Tylko konkretne OEM

- **Xiaomi**

Wyłudzanie informacji i niebezpieczne zagrożenia w sieci Web wykrywane przez usługę Defender dla punktu końcowego systemu Android nie są blokowane na niektórych urządzeniach Xiaomi. Poniższe funkcje nie działają na tych urządzeniach.

:::image type="content" source="images/0c04975c74746a5cdb085e1d9386e713.png" alt-text="Niebezpieczny komunikat z powiadomieniem" lightbox="images/0c04975c74746a5cdb085e1d9386e713.png":::

**Przyczyna:**

Urządzenia Xiaomi zawierają nowy model uprawnień. Zapobiega to wyświetlaniu wyskakujących okien programu Defender dla punktu końcowego systemu Android, gdy działa w tle.

Uprawnienia urządzeń Xiaomi: "Wyświetlanie okien podręcznych podczas pracy w tle".

:::image type="content" source="images/6e48e7b29daf50afddcc6c8c7d59fd64.png" alt-text="Okienko ustawień podręcznych w portalu usługi Microsoft Defender 365" lightbox="images/6e48e7b29daf50afddcc6c8c7d59fd64.png":::

**Rozwiązanie:**

Włącz wymagane uprawnienia na urządzeniach Xiaomi.

- Wyświetlanie wyskakujących okien podczas pracy w tle.

## <a name="unable-to-allow-permission-for-permanent-protection-during-onboarding-on-some-oem-devices"></a>Nie można zezwolić na uprawnienie do "Trwałej ochrony" podczas dołączania na niektórych urządzeniach OEM

**Dotyczy:** Tylko określone urządzenia OEM.

- **Xiaomi z systemem Android 11**

Aplikacja Defender pyta o uprawnienia optymalizacji baterii/trwałej ochrony na urządzeniach w ramach dołączania aplikacji, a  wybranie opcji Zezwalaj zwraca błąd, że nie można ustawić uprawnienia. Dotyczy ona tylko ostatniego uprawnienia o nazwie "Trwała ochrona". 

**Przyczyna:**

Firma Xiaomi zmieniła uprawnienia do optymalizacji baterii w systemie Android 11. Program Defender for Endpoint nie może skonfigurować tego ustawienia w celu ignorowania optymalizacji baterii.

**Rozwiązanie:**

Współpracujemy z producentem OEM nad znalezieniem rozwiązania umożliwiającego włączenie tego uprawnienia z poziomu ekranu dołączania aplikacji. Zaktualizujemy dokumentację, gdy problem zostanie rozwiązany.
Użytkownicy mogą wykonać następujące czynności, aby włączyć te same uprawnienia z poziomu ustawień urządzenia: 

1. Przejdź do **Ustawienia** na urządzeniu.

2. Wyszukaj i wybierz pozycję **Optymalizacja baterii**.

   :::image type="content" source="images/search-battery-optimisation.png" alt-text="Strona, na której można wyszukiwać i wybrać pozycję Bateria" lightbox="images/search-battery-optimisation.png":::

3. W **special app access (Specjalny dostęp do** aplikacji) wybierz **pozycję Battery Optimization (Optymalizacja baterii**).

   :::image type="content" source="images/special-app-access.png" alt-text="Okienko dostępu do aplikacji Specjalne, z poziomu którego możesz wybrać pozycję Chowaj baterię" lightbox="images/special-app-access.png":::

4. Zmień menu rozwijane, aby wyświetlić **wszystkie aplikacje**.

   :::image type="content" source="images/show-all-apps-2.png" alt-text="Lista rozwijana, z której można zmienić wartość na Wszystkie aplikacje w okienku Konwersja baterii" lightbox="images/show-all-apps-2.png":::

   :::image type="content" source="images/show-all-apps-1.png" alt-text="Lista rozwijana z opcją Wszystkie aplikacje w okienku Konwersja baterii" lightbox="images/show-all-apps-1.png":::

5. Znajdź pozycję "Ochrona punktu końcowego w usłudze Microsoft Defender" i wybierz **pozycję Nie optymalizuj**.

   :::image type="content" source="images/select-dont-optimise.png" alt-text="Strona umożliwiająca lokalizację opcji i Ochrona punktu końcowego w usłudze Microsoft Defender opcji Nie optymalizuj" lightbox="images/select-dont-optimise.png":::

Wróć do ekranu Ochrona punktu końcowego w usłudze Microsoft Defender, wybierz pozycję Zezwalaj **, a** nastąpi przekierowanie do ekranu pulpitu nawigacyjnego.

## <a name="send-in-app-feedback"></a>Wysyłanie opinii w aplikacji

Jeśli użytkownik napotyka problem, który nie został jeszcze rozwiązany w powyższych sekcjach lub nie może rozwiązać problemu przy użyciu wymienionych czynności, może przekazać opinię w aplikacji wraz z danymi **diagnostycznmi**. Nasz zespół może następnie zbadać dzienniki w celu podania odpowiedniego rozwiązania. Użytkownicy mogą wykonać te same czynności:

1.  Otwórz aplikację **MDE na** urządzeniu i kliknij **ikonę** profilu w lewym górnym rogu.

    :::image type="content" source="images/select-profile-icon-1.jpg" alt-text="Ikona profilu w portalu Ochrona punktu końcowego w usłudze Microsoft Defender sieci" lightbox="images/select-profile-icon-1.jpg":::

2.  Wybierz pozycję "Pomoc &".

    :::image type="content" source="images/selecthelpandfeedback2.png" alt-text="Opcja pomoc & opinie, która może być wybrana w Ochrona punktu końcowego w usłudze Microsoft Defender portalu" lightbox="images/selecthelpandfeedback2.png":::

3.  Wybierz pozycję "Wyślij opinię do firmy Microsoft".

    :::image type="content" alt-text="Wybierz pozycję Wyślij opinię do firmy Microsoft" source="images/send-feedback-to-microsoft-3.jpg":::

4.  Wybierz jedną z dostępnych opcji. Aby zgłosić problem, wybierz pozycję "Chcę zgłosić problem".

    :::image type="content" source="images/report-issue-4.jpg" alt-text="Opcja Chcę zgłosić problem" lightbox="images/report-issue-4.jpg":::

5.  Podaj szczegóły problemu, z którym masz do czynienia, i zaznacz pole wyboru "Wyślij dane diagnostyczne". Zalecamy skorzystanie z ustawienia "Uwzględnij swój adres e-mail", aby zespół może się z Toem wrócić do Ciebie w celu rozwiązania lub rozwiązania problemu.

    :::image type="content" source="images/finalsubmit5.png" alt-text="Okienko, w którym można dodawać szczegóły i dołączać dane diagnostyczne" lightbox="images/finalsubmit5.png":::

6.  Kliknij pozycję "Prześlij", aby pomyślnie wysłać opinię.
