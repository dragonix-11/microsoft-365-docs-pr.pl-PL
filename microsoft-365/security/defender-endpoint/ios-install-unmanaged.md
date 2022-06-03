---
title: Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w funkcjach iOS
description: Opis sposobu wdrażania Ochrona punktu końcowego w usłudze Microsoft Defender na niezarejestrowanych urządzeniach iOS.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, ios, configure, features, ios
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: sunasing
author: sunasing
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 1d05f515ef1f2badcb6ba0bde69daa3fa2677434
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873517"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-unenrolled-ios-devices"></a>Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender na niezarejestrowanych urządzeniach iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Usługa Defender for Endpoint w iOS używa sieci VPN w celu zapewnienia funkcji ochrony sieci Web. Nie jest to zwykła sieć VPN i jest lokalną/samopętlaną siecią VPN, która nie przyjmuje ruchu poza urządzeniem.

## <a name="configure-microsoft-defender-for-endpoint-risk-signals-in-app-protection-policy-mam"></a>Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender sygnałów ryzyka w zasadach ochrony aplikacji (MAM)

Ochrona punktu końcowego w usłudze Microsoft Defender na iOS, która już chroni użytkowników przedsiębiorstwa w scenariuszach usługi Mobile Zarządzanie urządzeniami (MDM), teraz rozszerza obsługę zarządzania aplikacjami mobilnymi (MAM) dla urządzeń, które nie są zarejestrowane przy użyciu Intune urządzenia przenośnego zarządzania urządzeniami przenośnymi (MDM). Rozszerza ona również tę pomoc techniczną na klientów, którzy korzystają z innych rozwiązań do zarządzania mobilnością w przedsiębiorstwie, a jednocześnie używają Intune do zarządzania aplikacjami mobilnymi (MAM). Ta funkcja umożliwia zarządzanie danymi organizacji i ochronę ich w aplikacji.

Ochrona punktu końcowego w usłudze Microsoft Defender informacji o zagrożeniach iOS są używane przez zasady ochrony aplikacji Intune w celu ochrony tych aplikacji. zasady Ochrona aplikacji (APP) to reguły, które zapewniają, że dane organizacji pozostają bezpieczne lub zawarte w zarządzanej aplikacji. Aplikacja zarządzana ma zastosowane zasady ochrony aplikacji i może być zarządzana przez Intune.  

Ochrona punktu końcowego w usłudze Microsoft Defender na iOS obsługuje obie konfiguracje funkcji MAM
- **Intune MDM + MAM**: administratorzy IT mogą zarządzać aplikacjami tylko przy użyciu zasad ochrony aplikacji na urządzeniach zarejestrowanych w Intune zarządzania urządzeniami przenośnymi (MDM).
- **Zarządzanie aplikacjami mobilnymi bez rejestracji urządzeń**: zarządzanie aplikacjami mobilnymi bez rejestracji urządzeń lub MAM-WE umożliwia administratorom IT zarządzanie aplikacjami przy użyciu [zasad ochrony aplikacji](/mem/intune/apps/app-protection-policy) na urządzeniach niezarejestrowanych w Intune mdm. Oznacza to, że aplikacjami można zarządzać za pomocą Intune na urządzeniach zarejestrowanych u innych dostawców EMM. Aby zarządzać aplikacjami przy użyciu obu powyższych konfiguracji, klienci powinni używać Intune w [centrum administracyjnym Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)

Aby włączyć tę funkcję, administrator musi skonfigurować połączenie między Ochrona punktu końcowego w usłudze Microsoft Defender i Intune, utworzyć zasady ochrony aplikacji i zastosować zasady na docelowych urządzeniach i aplikacjach. 
 
Użytkownicy końcowi muszą również wykonać kroki, aby zainstalować Ochrona punktu końcowego w usłudze Microsoft Defender na urządzeniu i aktywować przepływ dołączania.

### <a name="pre-requisites"></a>Wymagania wstępne

1. **Sprawdź, czy łącznik jest włączony**. <br> W [ujednoliconej konsoli zabezpieczeń](https://security.microsoft.com) przejdź do **Ustawienia** >  **Punkty** > **zaawansowane i** upewnij się, że **Microsoft Intune połączenie** jest włączone.

  :::image type="content" source="images/enable-intune-connection.png" alt-text="Łącznik Defender for Endpoint — Intune" lightbox="images/enable-intune-connection.png":::

  
2. **Sprawdź, czy łącznik jest włączony w portalu Intune**. <br> W [centrum administracyjnym programu Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do **pozycji Zabezpieczenia** >  punktu końcowego **Ochrona punktu końcowego w usłudze Microsoft Defender** i upewnij się, że stan połączenia jest włączony.

  :::image type="content" source="images/app-settings.png" alt-text="Ustawienia aplikacji" lightbox="images/app-settings.png":::

### <a name="create-an-app-protection-policy"></a>Tworzenie zasad ochrony aplikacji
 
Zablokuj dostęp lub wyczyść dane zarządzanej aplikacji na podstawie Ochrona punktu końcowego w usłudze Microsoft Defender sygnałów ryzyka, tworząc zasady ochrony aplikacji.
Ochrona punktu końcowego w usłudze Microsoft Defender można skonfigurować do wysyłania sygnałów zagrożeń do użycia w zasadach ochrony aplikacji (APP, znanej również jako MAM). Dzięki tej możliwości można używać Ochrona punktu końcowego w usłudze Microsoft Defender do ochrony zarządzanych aplikacji.

1. Tworzenie zasad <br>
zasady Ochrona aplikacji (APP) to reguły, które zapewniają, że dane organizacji pozostają bezpieczne lub zawarte w zarządzanej aplikacji. Zasady mogą być regułą wymuszaną, gdy użytkownik próbuje uzyskać dostęp do danych firmowych lub przenieść je, lub zestawem akcji, które są zabronione lub monitorowane, gdy użytkownik znajduje się w aplikacji. 

:::image type="content" source="images/create-policy.png" alt-text="Karta Tworzenie zasad w elemencie menu zasad Ochrona aplikacji" lightbox="images/create-policy.png":::

2. Dodawanie aplikacji <br>
    a. Wybierz sposób stosowania tych zasad do aplikacji na różnych urządzeniach. Następnie dodaj co najmniej jedną aplikację. <br>
    Użyj tej opcji, aby określić, czy te zasady mają zastosowanie do urządzeń niezarządzanych. Możesz również wybrać kierowanie zasad do aplikacji na urządzeniach o dowolnym stanie zarządzania.
Ponieważ zarządzanie aplikacjami mobilnymi nie wymaga zarządzania urządzeniami, można chronić dane firmowe na urządzeniach zarządzanych i niezarządzanych. Zarządzanie jest skoncentrowane na tożsamości użytkownika, co eliminuje wymaganie dotyczące zarządzania urządzeniami. Firmy mogą używać zasad ochrony aplikacji z rozwiązaniem MDM lub bez niego w tym samym czasie. Rozważmy na przykład pracownika korzystającego zarówno z telefonu wystawionego przez firmę, jak i własnego tabletu osobistego. Telefon firmy jest zarejestrowany w rozwiązaniu MDM i chroniony przez zasady ochrony aplikacji, podczas gdy urządzenie osobiste jest chronione tylko przez zasady ochrony aplikacji.

    b. Wybierz pozycję Aplikacje<br>
    Aplikacja zarządzana to aplikacja, która ma zastosowane zasady ochrony aplikacji i może być zarządzana przez Intune. Każdą aplikacją zintegrowaną z [zestawem Intune SDK](/mem/intune/developer/app-sdk) lub opakowaną przez [Intune App Wrapping Tool](/mem/intune/developer/apps-prepare-mobile-application-management) można zarządzać przy użyciu zasad ochrony aplikacji Intune. Zobacz oficjalną listę [Microsoft Intune chronionych aplikacji](/mem/intune/apps/apps-supported-intune-apps), które zostały utworzone przy użyciu tych narzędzi i są dostępne do użytku publicznego.

    *Przykład: Outlook jako aplikacja zarządzana*

     :::image type="content" source="images/managed-app.png" alt-text="Element menu microsoft Outlook w okienku nawigacji po lewej stronie" lightbox="images/managed-app.png":::
  

 3. Ustaw wymagania dotyczące zabezpieczeń logowania dla zasad ochrony. <br>
Wybierz pozycję **Ustawienie > maksymalny dozwolony poziom zagrożenia urządzenia** w **obszarze Warunki urządzenia** i wprowadź wartość. Następnie wybierz pozycję  **Akcja: "Blokuj dostęp"**. Ochrona punktu końcowego w usłudze Microsoft Defender na iOS udostępnia ten poziom zagrożenia urządzenia.

    
   :::image type="content" source="images/conditional-launch.png" alt-text="Okienko Warunki urządzenia" lightbox="images/conditional-launch.png":::

4. Przypisz grupy użytkowników, dla których należy zastosować zasady.<br>
  Wybierz pozycję **Dołączone grupy**. Następnie dodaj odpowiednie grupy. 


Aby uzyskać więcej informacji na temat zasad zarządzania aplikacjami mobilnymi lub ochrony aplikacji, zobacz [iOS ustawienia zasad ochrony aplikacji](/mem/intune/apps/app-protection-policy-settings-ios).

## <a name="deploy-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender na potrzeby zarządzania aplikacjami mobilnymi lub na niezarejestrowanych urządzeniach

Ochrona punktu końcowego w usłudze Microsoft Defender na iOS włącza scenariusz zasad ochrony aplikacji i jest dostępny w sklepie apple app store.

Gdy zasady ochrony aplikacji są skonfigurowane pod kątem dołączania przez aplikacje sygnałów ryzyka urządzenia z Ochrona punktu końcowego w usłudze Microsoft Defender, użytkownicy będą przekierowywani w celu zainstalowania Ochrona punktu końcowego w usłudze Microsoft Defender podczas korzystania z takich aplikacji. Alternatywnie użytkownicy mogą również zainstalować najnowszą wersję aplikacji bezpośrednio ze sklepu Apple App Store.
