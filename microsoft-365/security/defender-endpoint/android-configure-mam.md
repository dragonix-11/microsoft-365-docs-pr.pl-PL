---
title: Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender ryzyka przy użyciu zasad ochrony aplikacji (MAM)
description: W tym artykule opisano sposób konfigurowania Ochrona punktu końcowego w usłudze Microsoft Defender ryzyka przy użyciu zasad ochrony aplikacji
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mde, android, configuration, MAM, Zasady ochrony aplikacji, aplikacja zarządzana
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: shthota
author: shthota
manager: dansimp
ms.localizationpriority: medium
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 5d74fd2af61ee4047dd2728c28e6093efbc58ce9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471302"
---
# <a name="configure-microsoft-defender-for-endpoint-risk-signals-using-app-protection-policies-mam"></a>Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender ryzyka przy użyciu zasad ochrony aplikacji (MAM)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android, który już chroni użytkowników przedsiębiorstwa w scenariuszach usługi Mobile Zarządzanie urządzeniami (MDM), teraz obsługuje zarządzanie aplikacjami mobilnymi (MAM) dla urządzeń, które nie zostały zarejestrowane za pomocą zarządzania urządzeniami przenośnymi w usłudze Intune. Obejmuje to również klientów korzystających z innych rozwiązań do zarządzania mobilnością w przedsiębiorstwie, którzy nadal korzystają Intune do zarządzania aplikacjami mobilnymi (MAM). Ta funkcja umożliwia zabezpieczanie danych organizacji i zarządzanie nimi w obrębie aplikacji.

Ochrona punktu końcowego w usłudze Microsoft Defender o zagrożeniach w systemie Android są stosowane przez Intune ochrony aplikacji w celu ochrony tych aplikacji. Ochrona aplikacji (APP) to reguły, które zapewniają, że dane organizacji pozostają bezpieczne lub znajdują się w zarządzanej aplikacji. Aplikacja zarządzana ma zastosowane zasady ochrony aplikacji i może być zarządzana przez Intune.  

Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android obsługuje obie konfiguracje mam
- **Intune MDM + MAM**: administratorzy IT mogą zarządzać aplikacjami tylko za pomocą zasad ochrony aplikacji na urządzeniach zarejestrowanych za pomocą usługi Intune zarządzanie urządzeniami przenośnymi.
- **MAM bez rejestracji urządzeń**: MAM bez rejestracji urządzenia lub MAM-WE, umożliwia administratorom informatycznym zarządzanie aplikacjami przy [](/mem/intune/app/app-protection-policy) użyciu zasad ochrony aplikacji na urządzeniach, które nie zostały zarejestrowane za pomocą Intune MDM. To oznacza, że aplikacjami można zarządzać Intune na urządzeniach zarejestrowanych u innych dostawców usług EMM. Aby zarządzać aplikacjami przy użyciu w obu powyższych konfiguracjach, klienci powinni Intune w centrum [Microsoft Endpoint Manager administracyjnego](https://go.microsoft.com/fwlink/?linkid=2109431)

Aby włączyć tę funkcję, administrator musi skonfigurować połączenie między usługami Ochrona punktu końcowego w usłudze Microsoft Defender i Intune, utworzyć zasady ochrony aplikacji i zastosować je do urządzeń i aplikacji docelowych. 
 
Użytkownicy końcowi muszą również wykonać kroki instalowania aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender urządzenia i aktywowania przepływu dołączania.


## <a name="admin-prerequisites"></a>Wymagania wstępne administratorów

- **Sprawdzanie, czy jest włączony program Microsoft Defender Endpoint-Intune łącznika**

  a. Przejdź do security.microsoft.com. 

  b. Wybierz **Ustawienia > punkty końcowe> zaawansowane > Microsoft Intune włączona** połączenie.

  c. Jeśli połączenie nie jest włączone, wybierz przełącznik, aby go włączyć, a następnie wybierz pozycję **Zapisz preferencje**.

  :::image type="content" source="images/enable-intune-connection.png" alt-text="Sekcja Funkcje zaawansowane w portalu Microsoft 365 Defender zaawansowanej" lightbox="images/enable-intune-connection.png":::

  d. Przejdź do **Microsoft Endpoint Manager (Intune)** i Sprawdź, czy program Microsoft Defender dla Endpoint-Intune jest włączony.

  :::image type="content" source="images/validate-intune-connector.png" alt-text="Okienko stanu intune-connector w portalu Microsoft 365 Defender sieci Microsoft 365 Defender" lightbox="images/validate-intune-connector.png":::

- **Włączanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji Android Connector dla zasad ochrony aplikacji (APP)**
  
  Skonfiguruj łącznik na Intune Microsoft Endpoint Manager dla Ochrona aplikacji sieci:

  a. Przejdź do **strony Administracja dzierżawą> łączniki i tokeny > Ochrona punktu końcowego w usłudze Microsoft Defender**.

  b. Włącz przełącznik zasad ochrony aplikacji dla systemu Android (jak pokazano na poniższym zrzucie ekranu).

  c. Wybierz **Zapisz**.

  :::image type="content" source="images/app-settings.png" alt-text="Okienko ustawień aplikacji w portalu Microsoft 365 Defender aplikacji" lightbox="images/app-settings.png":::

- **Tworzenie zasad ochrony aplikacji** 
 
Zablokuj dostęp lub wyczyść dane aplikacji zarządzanej na podstawie Ochrona punktu końcowego w usłudze Microsoft Defender sygnalizowania ryzyka przez utworzenie zasad ochrony aplikacji.
Ochrona punktu końcowego w usłudze Microsoft Defender skonfigurować do wysyłania sygnałów zagrożeń, które mają być używane w zasadach ochrony aplikacji (APP, znaną także jako MAM). Dzięki tej funkcji możesz chronić aplikacje zarządzane Ochrona punktu końcowego w usłudze Microsoft Defender za pomocą funkcji zarządzania.

1. Tworzenie zasad <br>
Ochrona aplikacji (APP) to reguły, które zapewniają, że dane organizacji pozostają bezpieczne lub znajdują się w zarządzanej aplikacji. Zasady mogą być regułą wymuszaną podczas próby uzyskania dostępu do danych firmowych lub przenoszenia ich przez użytkownika albo zestawem działań zabronionych lub monitorowanych, gdy użytkownik znajduje się w aplikacji. 

:::image type="content" source="images/create-policy.png" alt-text="Karta Tworzenie zasad na stronie Ochrona aplikacji zasad w portalu Microsoft 365 Defender sieci Web" lightbox="images/create-policy.png":::

2. Dodawanie aplikacji <br>
    a. Wybierz sposób stosowania tych zasad do aplikacji na różnych urządzeniach. Następnie dodaj co najmniej jedną aplikację. <br>
    Użyj tej opcji, aby określić, czy te zasady mają zastosowanie do urządzeń niezamanektowych. W systemie Android możesz określić, które zasady mają zastosowanie do systemu Android Enterprise, Administrator urządzeń lub Urządzenia niezamanektowane. Możesz także kierować zasady do aplikacji na urządzeniach o dowolnym stanie zarządzania.
Ponieważ zarządzanie aplikacją mobilną nie wymaga zarządzania urządzeniami, możesz chronić dane firmowe zarówno na urządzeniach zarządzanych, jak i nieza zarządzania. Zarządzanie jest wyśrodkowane na tożsamości użytkownika, co usuwa wymaganie zarządzania urządzeniami. Firmy mogą jednocześnie korzystać z zasad ochrony aplikacji z usługą MDM lub bez nich. Rozważ na przykład pracownika, który używa zarówno telefonu wystawionego przez firmę, jak i własnego tabletu osobistego. Telefon firmowy jest zarejestrowany w usłudze MDM i chroniony za pomocą zasad ochrony aplikacji, natomiast urządzenie osobiste jest chronione tylko przez zasady ochrony aplikacji.

    b. Wybierz aplikacje<br>
    Aplikacja zarządzana to aplikacja, do która ma zastosowane zasady ochrony aplikacji i może być zarządzana przez Intune. Każdą aplikację, która została zintegrowana z zestawem [SDK pakietu Intune](/mem/intune/developer/app-sdk) lub zawijona przez [](/mem/intune/developer/apps-prepare-mobile-application-management) Intune App Wrapping Tool, można zarządzać przy użyciu Intune zasad ochrony aplikacji. Zapoznaj się z oficjalna [listą Microsoft Intune aplikacji](/mem/intune/apps/apps-supported-intune-apps) chronionych, które zostały stworzone przy użyciu tych narzędzi i są dostępne do użytku publicznego.

    *Przykład: Outlook jako aplikacja zarządzana*

  :::image type="content" source="images/managed-app.png" alt-text="Okienko Aplikacje publiczne w portalu Microsoft 365 Defender sieci Web" lightbox="images/managed-app.png":::


 3. Ustaw wymagania dotyczące zabezpieczeń logowania dla zasad ochrony. <br>
Wybierz **pozycję > maksymalny dozwolony poziom zagrożeń** urządzenia w warunkach **urządzenia i wprowadź** wartość. Następnie wybierz  **pozycję Akcja: "Blokuj dostęp"**. Ochrona punktu końcowego w usłudze Microsoft Defender Android udostępnia ten poziom zagrożeń dla urządzenia.

  :::image type="content" source="images/conditional-launch.png" alt-text="Okienko warunków urządzenia w portalu Microsoft 365 Defender urządzenia" lightbox="images/conditional-launch.png":::
  
- **Przypisz grupy użytkowników, do których mają zostać zastosowane zasady.**<br>
  Wybierz **pozycję Uwzględnione grupy**. Następnie dodaj odpowiednie grupy. 

    :::image type="content" source="images/assignment.png" alt-text="Okienko Grupy uwzględnione w portalu Microsoft 365 Defender grupy" lightbox="images/assignment.png":::


## <a name="end-user-prerequisites"></a>Wymagania wstępne użytkowników końcowych
- Aplikacja brokera musi być zainstalowana
    - Intune — Portal firmy
    
- Użytkownicy mają wymagane licencje dla aplikacji zarządzanej i mają zainstalowaną aplikację

### <a name="end-user-onboarding"></a>Dołączanie użytkowników końcowych 

1. Zaloguj się do aplikacji zarządzanej, na przykład do aplikacji Outlook. Urządzenie zostanie zarejestrowane, a zasady ochrony aplikacji zsynchronizowane z urządzeniem. Zasady ochrony aplikacji rozpoznają stan kondycji urządzenia.  

2. Wybierz **pozycję Kontynuuj**. Zostanie przedstawiony ekran, który zaleca pobieranie i konfigurowanie aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender dla systemu Android.

3. Wybierz **pozycję Pobierz**. Nastąpi przekierowanie do sklepu z aplikacjami (Google Play). 

4.  Zainstaluj aplikację Ochrona punktu końcowego w usłudze Microsoft Defender (mobile) i uruchom ponownie ekran dołączania aplikacji zarządzanej.

  :::image type="content" source="images/download-mde.png" alt-text="Strony z ilustracjami, które zawierają procedurę pobierania aplikacji MDE i uruchamiania z powrotem ekranu dołączania aplikacji" lightbox="images/download-mde.png":::
  

5.  Kliknij **przycisk Kontynuuj > Uruchom**. Proces Ochrona punktu końcowego w usłudze Microsoft Defender/aktywacji aplikacji jest inicjowany. Postępuj zgodnie z instrukcjami, aby ukończyć dołączanie. Nastąpi automatyczne przekierowanie z powrotem do ekranu wnoszeń aplikacji zarządzanych, który teraz wskazuje, że urządzenie jest w dobrej kondycji.

6. Wybierz **pozycję Kontynuuj** , aby zalogować się do aplikacji zarządzanej. 



## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android](microsoft-defender-endpoint-android.md)
- [Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android za pomocą aplikacji Microsoft Intune](android-intune.md)
