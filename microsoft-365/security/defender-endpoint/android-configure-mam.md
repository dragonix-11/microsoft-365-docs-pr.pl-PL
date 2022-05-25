---
title: Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender sygnałów ryzyka przy użyciu zasad ochrony aplikacji (MAM)
description: Opis sposobu konfigurowania sygnałów ryzyka Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu zasad usługi App Protection
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mde, android, configuration, MAM, App Protectection Policies, Managed app
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
ms.openlocfilehash: 48a128e32e949ecad6c34c4dfc96f6246780d0db
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2022
ms.locfileid: "65670185"
---
# <a name="configure-microsoft-defender-for-endpoint-risk-signals-using-app-protection-policies-mam"></a>Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender sygnałów ryzyka przy użyciu zasad ochrony aplikacji (MAM)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



Ochrona punktu końcowego w usłudze Microsoft Defender na Android, która już chroni użytkowników przedsiębiorstwa w scenariuszach usługi Mobile Zarządzanie urządzeniami (MDM), teraz rozszerza obsługę zarządzania aplikacjami mobilnymi (MAM) dla urządzeń, które nie są zarejestrowane przy użyciu Intune  zarządzanie urządzeniami przenośnymi (MDM). Rozszerza ona również tę pomoc techniczną na klientów, którzy korzystają z innych rozwiązań do zarządzania mobilnością w przedsiębiorstwie, a jednocześnie używają Intune do zarządzania aplikacjami mobilnymi (MAM). Ta funkcja umożliwia zarządzanie danymi organizacji i ochronę ich w aplikacji.

Ochrona punktu końcowego w usłudze Microsoft Defender informacji o zagrożeniach Android są stosowane przez zasady ochrony aplikacji Intune w celu ochrony tych aplikacji. zasady Ochrona aplikacji (APP) to reguły, które zapewniają, że dane organizacji pozostają bezpieczne lub zawarte w zarządzanej aplikacji. Aplikacja zarządzana ma zastosowane zasady ochrony aplikacji i może być zarządzana przez Intune.  

Ochrona punktu końcowego w usłudze Microsoft Defender na Android obsługuje obie konfiguracje funkcji MAM
- **Intune MDM + MAM**: administratorzy IT mogą zarządzać aplikacjami tylko przy użyciu zasad ochrony aplikacji na urządzeniach zarejestrowanych w Intune zarządzania urządzeniami przenośnymi (MDM).
- **Zarządzanie aplikacjami mobilnymi bez rejestracji urządzeń**: zarządzanie aplikacjami mobilnymi bez rejestracji urządzeń lub MAM-WE umożliwia administratorom IT zarządzanie aplikacjami przy użyciu [zasad ochrony aplikacji](/mem/intune/apps/app-protection-policy) na urządzeniach niezarejestrowanych w Intune mdm. Ten aprowizowanie oznacza, że aplikacjami można zarządzać za pomocą Intune na urządzeniach zarejestrowanych u innych dostawców EMM. Aby zarządzać aplikacjami w obu tych konfiguracjach, klienci powinni używać Intune w [centrum administracyjnym Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

Aby włączyć tę funkcję, administrator musi skonfigurować połączenie między Ochrona punktu końcowego w usłudze Microsoft Defender i Intune, utworzyć zasady ochrony aplikacji i zastosować zasady na docelowych urządzeniach i aplikacjach. 
 
Użytkownicy końcowi muszą również wykonać kroki, aby zainstalować Ochrona punktu końcowego w usłudze Microsoft Defender na urządzeniu i aktywować przepływ dołączania.


## <a name="admin-prerequisites"></a>Administracja wymagania wstępne

- **Sprawdzanie, czy łącznik usługi Microsoft Defender dla Endpoint-Intune jest włączony**

  a. Przejdź do security.microsoft.com. 

  b. Wybierz **pozycję Ustawienia > Punkty końcowe> funkcje zaawansowane > Microsoft Intune połączenie** jest włączone.

  c. Jeśli połączenie nie jest włączone, wybierz przełącznik, aby je włączyć, a następnie wybierz pozycję **Zapisz preferencje**.

  :::image type="content" source="images/enable-intune-connection.png" alt-text="Sekcja Funkcje zaawansowane w portalu Microsoft 365 Defender" lightbox="images/enable-intune-connection.png":::

  d. Przejdź do **Microsoft Endpoint Manager (Intune)** i sprawdź, czy łącznik usługi Microsoft Defender dla Endpoint-Intune jest włączony.

  :::image type="content" source="images/validate-intune-connector.png" alt-text="Okienko stanu łącznika usługi Intune w portalu Microsoft 365 Defender" lightbox="images/validate-intune-connector.png":::

- **Włączanie Ochrona punktu końcowego w usłudze Microsoft Defender w łączniku Android dla zasad ochrony aplikacji (APP)**
  
  Skonfiguruj łącznik w Intune Microsoft Endpoint Manager dla zasad Ochrona aplikacji:

  a. Przejdź do obszaru **Administracja dzierżawą > Łączniki i tokeny > Ochrona punktu końcowego w usłudze Microsoft Defender**.

  b. Włącz przełącznik dla zasad ochrony aplikacji dla Android (jak pokazano na poniższym zrzucie ekranu).

  c. Wybierz **Zapisz**.

  :::image type="content" source="images/app-settings.png" alt-text="Okienko ustawień aplikacji w portalu Microsoft 365 Defender" lightbox="images/app-settings.png":::

- **Tworzenie zasad ochrony aplikacji** 
 
Zablokuj dostęp lub wyczyść dane zarządzanej aplikacji na podstawie Ochrona punktu końcowego w usłudze Microsoft Defender sygnałów ryzyka, tworząc zasady ochrony aplikacji.
Ochrona punktu końcowego w usłudze Microsoft Defender można skonfigurować do wysyłania sygnałów zagrożeń do użycia w zasadach ochrony aplikacji (APP, znanej również jako MAM). Dzięki tej możliwości można używać Ochrona punktu końcowego w usłudze Microsoft Defender do ochrony zarządzanych aplikacji.

1. Tworzenie zasad <br>
zasady Ochrona aplikacji (APP) to reguły, które zapewniają, że dane organizacji pozostają bezpieczne lub zawarte w zarządzanej aplikacji. Zasady mogą być regułą wymuszaną, gdy użytkownik próbuje uzyskać dostęp do danych firmowych lub przenieść je, lub zestawem akcji, które są zabronione lub monitorowane, gdy użytkownik znajduje się w aplikacji. 

:::image type="content" source="images/create-policy.png" alt-text="Karta Tworzenie zasad na stronie zasad Ochrona aplikacji w portalu Microsoft 365 Defender" lightbox="images/create-policy.png":::

2. Dodawanie aplikacji <br>
    a. Wybierz sposób stosowania tych zasad do aplikacji na różnych urządzeniach. Następnie dodaj co najmniej jedną aplikację. <br>
    Użyj tej opcji, aby określić, czy te zasady mają zastosowanie do urządzeń niezarządzanych. W Android można określić zasady stosowane do urządzeń Android Enterprise, urządzenia Administracja lub niezarządzanych. Możesz również wybrać kierowanie zasad do aplikacji na urządzeniach o dowolnym stanie zarządzania.
Ponieważ zarządzanie aplikacjami mobilnymi nie wymaga zarządzania urządzeniami, można chronić dane firmowe na urządzeniach zarządzanych i niezarządzanych. Zarządzanie jest skoncentrowane na tożsamości użytkownika, co eliminuje wymaganie dotyczące zarządzania urządzeniami. Firmy mogą używać zasad ochrony aplikacji z rozwiązaniem MDM lub bez niego w tym samym czasie. Rozważmy na przykład pracownika korzystającego zarówno z telefonu wystawionego przez firmę, jak i własnego tabletu osobistego. Telefon firmy jest zarejestrowany w rozwiązaniu MDM i chroniony przez zasady ochrony aplikacji, podczas gdy urządzenie osobiste jest chronione tylko przez zasady ochrony aplikacji.

    b. Wybierz pozycję Aplikacje<br>
    Aplikacja zarządzana to aplikacja, która ma zastosowane zasady ochrony aplikacji i może być zarządzana przez Intune. Każdą aplikacją zintegrowaną z [zestawem Intune SDK](/mem/intune/developer/app-sdk) lub opakowaną przez [Intune App Wrapping Tool](/mem/intune/developer/apps-prepare-mobile-application-management) można zarządzać przy użyciu zasad ochrony aplikacji Intune. Zobacz oficjalną listę [Microsoft Intune chronionych aplikacji](/mem/intune/apps/apps-supported-intune-apps), które zostały utworzone przy użyciu tych narzędzi i są dostępne do użytku publicznego.

    *Przykład: Outlook jako aplikacja zarządzana*

  :::image type="content" source="images/managed-app.png" alt-text="Okienko Aplikacje publiczne w portalu Microsoft 365 Defender" lightbox="images/managed-app.png":::


 3. Ustaw wymagania dotyczące zabezpieczeń logowania dla zasad ochrony. <br>
Wybierz pozycję **Ustawienie > maksymalny dozwolony poziom zagrożenia urządzenia** w **obszarze Warunki urządzenia** i wprowadź wartość. Następnie wybierz pozycję  **Akcja: "Blokuj dostęp"**. Ochrona punktu końcowego w usłudze Microsoft Defender na Android udostępnia ten poziom zagrożenia urządzenia.

  :::image type="content" source="images/conditional-launch.png" alt-text="Okienko Warunki urządzenia w portalu Microsoft 365 Defender" lightbox="images/conditional-launch.png":::
  
- **Przypisz grupy użytkowników, dla których należy zastosować zasady.**<br>
  Wybierz pozycję **Dołączone grupy**. Następnie dodaj odpowiednie grupy. 

    :::image type="content" source="images/assignment.png" alt-text="Okienko Dołączone grupy w portalu Microsoft 365 Defender" lightbox="images/assignment.png":::


## <a name="end-user-prerequisites"></a>Wymagania wstępne użytkownika końcowego
- Aplikacja brokera musi być zainstalowana
    - Intune — Portal firmy
    
- Użytkownicy mają wymagane licencje dla aplikacji zarządzanej i mają zainstalowaną aplikację

### <a name="end-user-onboarding"></a>Dołączanie użytkowników końcowych 

1. Zaloguj się do aplikacji zarządzanej, na przykład Outlook. Urządzenie jest zarejestrowane, a zasady ochrony aplikacji są synchronizowane z urządzeniem. Zasady ochrony aplikacji rozpoznają stan kondycji urządzenia.  

2. Naciśnij przycisk **Kontynuuj**. Zostanie wyświetlony ekran, który zaleca pobieranie i konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender w aplikacji Android.

3. Wybierz pozycję **Pobierz**. Nastąpi przekierowanie do sklepu z aplikacjami (Google Play). 

4.  Zainstaluj aplikację Ochrona punktu końcowego w usłudze Microsoft Defender (Mobile) i uruchom z powrotem ekran dołączania aplikacji zarządzanej.

  :::image type="content" source="images/download-mde.png" alt-text="Strony ilustracyjne, które zawierają procedurę pobierania środowiska MDE i uruchamiania z powrotem ekranu dołączania aplikacji" lightbox="images/download-mde.png":::
  

5.  Kliknij przycisk **Kontynuuj > uruchamiania**. Zainicjowano przepływ dołączania/aktywacji aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender. Wykonaj kroki, aby zakończyć dołączanie. Nastąpi automatyczne przekierowanie z powrotem do ekranu dołączania aplikacji zarządzanej, który teraz wskazuje, że urządzenie jest w dobrej kondycji.

6. Wybierz pozycję **Kontynuuj** , aby zalogować się do aplikacji zarządzanej. 



## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie usługi ochrony punktu końcowego w usłudze Microsoft Defender w systemie Android](microsoft-defender-endpoint-android.md)
- [Wdrażaj usługę ochrony punktu końcowego w usłudze Microsoft Defender w systemie Android za pomocą usługi Microsoft Intune](android-intune.md)
