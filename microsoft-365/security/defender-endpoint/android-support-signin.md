---
title: Rozwiązywanie problemów z Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android
description: Rozwiązywanie problemów z Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mde, android, cloud, connectivity, communication
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
ms.openlocfilehash: 0a6f53b0723d7f3e9b4761aa83238e618d947e55
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783430"
---
# <a name="troubleshooting-issues-on-microsoft-defender-for-endpoint-on-android"></a>Rozwiązywanie problemów z Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Podczas dołączania urządzenia mogą wystąpić problemy z logowaniem po zainstalowaniu aplikacji.

Podczas dołączania mogą wystąpić problemy z logowaniem po zainstalowaniu aplikacji na urządzeniu.

Ten artykuł zawiera rozwiązania ułatwiające rozwiązywanie problemów z logowaniem.

## <a name="sign-in-failed---unexpected-error"></a>Logowanie nie powiodło się — nieoczekiwany błąd

**Logowanie nie powiodło się:** *nieoczekiwany błąd, spróbuj później*

:::image type="content" source="images/f9c3bad127d636c1f150d79814f35d4c.png" alt-text="Błąd niepowodzenia logowania Nieoczekiwany błąd na stronie logowania w portalu usługi Microsoft Defender 365." lightbox="images/f9c3bad127d636c1f150d79814f35d4c.png":::

**Komunikat:**

Nieoczekiwany błąd, spróbuj później

**Przyczyna:**

Na urządzeniu jest zainstalowana starsza wersja aplikacji "Microsoft Authenticator".

**Rozwiązanie:**

Zainstaluj najnowszą wersję i [Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator) ze Sklepu Google Play i spróbuj ponownie.

## <a name="sign-in-failed---invalid-license"></a>Logowanie nie powiodło się — nieprawidłowa licencja

**Logowanie nie powiodło się:** *Nieprawidłowa licencja, skontaktuj się z administratorem*

:::image type="content" source="images/920e433f440fa1d3d298e6a2a43d4811.png" alt-text="Dane kontaktowe dyrektywy na stronie logowania w portalu usługi Microsoft Defender 365" lightbox="images/920e433f440fa1d3d298e6a2a43d4811.png":::

**Komunikat:** *Nieprawidłowa licencja, skontaktuj się z administratorem*

**Przyczyna:**

Nie masz przypisanej licencji Microsoft 365 lub twoja organizacja nie ma licencji na subskrypcję Microsoft 365 Enterprise.

**Rozwiązanie:**

Skontaktuj się z administratorem, aby uzyskać pomoc.

## <a name="report-unsafe-site"></a>Zgłaszanie niebezpiecznej witryny

Witryny wyłudzające informacje podszywają się pod zaufane strony internetowe w celu uzyskania informacji osobistych lub finansowych. Odwiedź stronę [Przekaż opinię na temat ochrony sieci](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) , jeśli chcesz zgłosić witrynę internetową, która może być witryną wyłudzającą informacje.

## <a name="phishing-pages-arent-blocked-on-some-oem-devices"></a>Strony wyłudzające informacje nie są blokowane na niektórych urządzeniach OEM

**Dotyczy:** Tylko określone maszyny OEM

- **Xiaomi**

Wyłudzanie informacji i szkodliwe zagrożenia internetowe wykryte przez usługę Defender for Endpoint dla systemu Android nie są blokowane na niektórych urządzeniach Xiaomi. Poniższa funkcja nie działa na tych urządzeniach.

:::image type="content" source="images/0c04975c74746a5cdb085e1d9386e713.png" alt-text="Komunikat z powiadomieniem o niebezpiecznej witrynie" lightbox="images/0c04975c74746a5cdb085e1d9386e713.png":::

**Przyczyna:**

Urządzenia Xiaomi zawierają nowy model uprawnień. Zapobiega to wyświetlaniu wyskakujących okienek w usłudze Defender for Endpoint for Android w tle.

Uprawnienie urządzeń Xiaomi: "Wyświetlaj wyskakujące okna podczas pracy w tle".

:::image type="content" source="images/6e48e7b29daf50afddcc6c8c7d59fd64.png" alt-text="Okienko ustawień wyskakujące w portalu usługi Microsoft Defender 365" lightbox="images/6e48e7b29daf50afddcc6c8c7d59fd64.png":::

**Rozwiązanie:**

Włącz wymagane uprawnienie na urządzeniach Xiaomi.

- Wyświetl wyskakujące okna podczas działania w tle.

## <a name="unable-to-allow-permission-for-permanent-protection-during-onboarding-on-some-oem-devices"></a>Nie można zezwolić na uprawnienia do "trwałej ochrony" podczas dołączania na niektórych urządzeniach OEM

**Dotyczy:** Tylko określone urządzenia OEM.

- **Xiaomi z systemem Android 11**

Aplikacja Defender prosi o uprawnienie Optymalizacja baterii/Stała ochrona na urządzeniach w ramach dołączania aplikacji, a **wybranie pozycji Zezwalaj** zwraca błąd, którego nie można ustawić. Ma to wpływ tylko na ostatnie uprawnienie o nazwie "Permanent Protection". 

**Przyczyna:**

Xiaomi zmienił uprawnienia optymalizacji baterii w systemie Android 11. Usługa Defender dla punktu końcowego nie może skonfigurować tego ustawienia w celu ignorowania optymalizacji baterii.

**Rozwiązanie:**

Współpracujemy z programem OEM, aby znaleźć rozwiązanie umożliwiające włączenie tego uprawnienia z poziomu ekranu dołączania aplikacji. Po rozwiązaniu problemu zaktualizujemy dokumentację.
Użytkownicy mogą wykonać następujące kroki, aby włączyć te same uprawnienia z poziomu ustawień urządzenia: 

1. Przejdź do **Ustawienia** na urządzeniu.

2. Wyszukaj i wybierz pozycję **Optymalizacja baterii**.

   :::image type="content" source="images/search-battery-optimisation.png" alt-text="Strona, na której można wyszukiwać i wybierać pozycję Optymalizacja baterii" lightbox="images/search-battery-optimisation.png":::

3. W **obszarze Dostęp do aplikacji specjalnej** wybierz pozycję **Optymalizacja baterii**.

   :::image type="content" source="images/special-app-access.png" alt-text="Okienko Dostęp do aplikacji specjalnej, z którego można wybrać opcję Optymalizacja baterii" lightbox="images/special-app-access.png":::

4. Zmień listę rozwijaną, aby wyświetlić **pozycję Wszystkie aplikacje**.

   :::image type="content" source="images/show-all-apps-2.png" alt-text="Lista rozwijana, z której można zmienić wartość na Wszystkie aplikacje w okienku Optymalizacja baterii" lightbox="images/show-all-apps-2.png":::

   :::image type="content" source="images/show-all-apps-1.png" alt-text="Lista rozwijana zawierająca opcję Wszystkie aplikacje w okienku Optymalizacja baterii" lightbox="images/show-all-apps-1.png":::

5. Znajdź pozycję "Ochrona punktu końcowego w usłudze Microsoft Defender" i wybierz pozycję **Nie optymalizuj**.

   :::image type="content" source="images/select-dont-optimise.png" alt-text="Strona, która umożliwia lokalizację opcji Ochrona punktu końcowego w usłudze Microsoft Defender i wybór opcji Nie optymalizuj" lightbox="images/select-dont-optimise.png":::

Wróć do ekranu dołączania Ochrona punktu końcowego w usłudze Microsoft Defender, wybierz pozycję **Zezwalaj**, a nastąpi przekierowanie do ekranu pulpitu nawigacyjnego.

## <a name="send-in-app-feedback"></a>Wysyłanie opinii w aplikacji

Jeśli użytkownik napotka problem, który nie został jeszcze rozwiązany w powyższych sekcjach lub nie może rozwiązać problemu przy użyciu wymienionych kroków, użytkownik może przekazać **opinię w aplikacji** wraz z **danymi diagnostycznymi**. Nasz zespół może następnie zbadać dzienniki, aby zapewnić odpowiednie rozwiązanie. Użytkownicy mogą wykonać następujące kroki, aby zrobić to samo:

1. Otwórz **aplikację MDE** na urządzeniu i kliknij **ikonę profilu** w lewym górnym rogu.

    :::image type="content" source="images/select-profile-icon-1.jpg" alt-text="Ikona profilu w portalu Ochrona punktu końcowego w usłudze Microsoft Defender" lightbox="images/select-profile-icon-1.jpg":::

2. Wybierz pozycję "Pomoc & opinii".

    :::image type="content" source="images/selecthelpandfeedback2.png" alt-text="Opcja Pomoc & opinie, którą można wybrać w portalu Ochrona punktu końcowego w usłudze Microsoft Defender" lightbox="images/selecthelpandfeedback2.png":::

3. Wybierz pozycję "Wyślij opinię do firmy Microsoft".

    :::image type="content" alt-text="Wybierz pozycję Wyślij opinię do firmy Microsoft" source="images/send-feedback-to-microsoft-3.jpg":::

4. Wybierz jedną z podanych opcji. Aby zgłosić problem, wybierz pozycję "Chcę zgłosić problem".

    :::image type="content" source="images/report-issue-4.jpg" alt-text="Opcja Chcę zgłosić problem" lightbox="images/report-issue-4.jpg":::

5. Podaj szczegóły występującego problemu i sprawdź opcję "Wyślij dane diagnostyczne". Zalecamy sprawdzenie opcji "Dołącz twój adres e-mail", aby zespół mógł skontaktować się z Tobą za pomocą rozwiązania lub dalszych czynności.

    :::image type="content" source="images/finalsubmit5.png" alt-text="Okienko, w którym można dodawać szczegóły i dołączać dane diagnostyczne" lightbox="images/finalsubmit5.png":::

6. Kliknij pozycję "Prześlij", aby pomyślnie wysłać opinię.

