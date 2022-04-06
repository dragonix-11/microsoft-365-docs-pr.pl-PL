---
title: Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w funkcjach systemu iOS
description: W tym artykule opisano, Ochrona punktu końcowego w usłudze Microsoft Defender na niepodjętych urządzeniach z systemem iOS.
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
ms.openlocfilehash: b1945059147f87499d131d241c74aaca749fb6e7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474118"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-unenrolled-ios-devices"></a>Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender na nieuznanych urządzeniach z systemem iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Usługa Defender for Endpoint w systemie iOS używa połączenia VPN w celu zapewnienia funkcji ochrony sieci Web. Nie jest to zwykły sieci VPN i jest to lokalny/samopętny vpn, który nie przejmuje ruchu poza urządzenie.

## <a name="configure-microsoft-defender-for-endpoint-risk-signals-in-app-protection-policy-mam"></a>Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender ryzyka w zasadach ochrony aplikacji (MAM)

Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS, który już chroni użytkowników przedsiębiorstwa w scenariuszach usługi Mobile Zarządzanie urządzeniami (MDM), teraz obsługuje zarządzanie aplikacjami mobilnymi (MAM Intune) dla urządzeń, które nie zostały zarejestrowane przy użyciu zarządzania urządzeniami przenośnymi (MDM, Mobile Device Management). Obejmuje to również klientów korzystających z innych rozwiązań do zarządzania mobilnością w przedsiębiorstwie, którzy nadal korzystają Intune do zarządzania aplikacjami mobilnymi (MAM). Ta funkcja umożliwia zabezpieczanie danych organizacji i zarządzanie nimi w obrębie aplikacji.

Ochrona punktu końcowego w usłudze Microsoft Defender o zagrożeniach w systemie iOS są Intune ochrony aplikacji w celu ochrony tych aplikacji. Ochrona aplikacji (APP) to reguły, które zapewniają, że dane organizacji pozostają bezpieczne lub znajdują się w zarządzanej aplikacji. Aplikacja zarządzana ma zastosowane zasady ochrony aplikacji i może być zarządzana przez Intune.  

Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS obsługuje obie konfiguracje mam
- **Intune MDM + MAM**: administratorzy IT mogą zarządzać aplikacjami tylko za pomocą zasad ochrony aplikacji na urządzeniach zarejestrowanych za pomocą usługi Intune zarządzanie urządzeniami przenośnymi.
- **MAM bez rejestracji urządzeń**: MAM bez rejestracji urządzenia lub MAM-WE, umożliwia administratorom informatycznym zarządzanie aplikacjami przy [](/mem/intune/app/app-protection-policy) użyciu zasad ochrony aplikacji na urządzeniach, które nie zostały zarejestrowane za pomocą Intune MDM. Oznacza to, że aplikacjami można zarządzać Intune na urządzeniach zarejestrowanych u innych dostawców usług EMM. Aby zarządzać aplikacjami przy użyciu w obu powyższych konfiguracjach, klienci powinni Intune w centrum [Microsoft Endpoint Manager administracyjnego](https://go.microsoft.com/fwlink/?linkid=2109431)

Aby włączyć tę funkcję, administrator musi skonfigurować połączenie między usługami Ochrona punktu końcowego w usłudze Microsoft Defender i Intune, utworzyć zasady ochrony aplikacji i zastosować je do urządzeń i aplikacji docelowych. 
 
Użytkownicy końcowi muszą również wykonać kroki instalowania aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender urządzenia i aktywowania przepływu dołączania.

### <a name="pre-requisites"></a>Wymagania wstępne

1. **Sprawdź, czy jest włączony łącznik**. <br> Na [ujednoliconej konsoli zabezpieczeń](https://security.microsoft.com) przejdź do Ustawienia **EndpointsAdvanced** >  **Features** i upewnij się,  >  że **Microsoft Intune jest włączone** połączenie sieciowe.

  :::image type="content" source="images/enable-intune-connection.png" alt-text="Defender for Endpoint - Intune connector" lightbox="images/enable-intune-connection.png":::

  
2. **Sprawdź, czy łącznik jest włączony w portalu Intune sieci.** <br> W [centrum administracyjnym menedżera punktu końcowego](https://go.microsoft.com/fwlink/?linkid=2109431) >  firmy Microsoft przejdź do pozycji Zabezpieczenia **Ochrona punktu końcowego w usłudze Microsoft Defender** i upewnij się, że jest włączony stan połączenia.

  :::image type="content" source="images/app-settings.png" alt-text="Ustawienia aplikacji" lightbox="images/app-settings.png":::

### <a name="create-an-app-protection-policy"></a>Tworzenie zasad ochrony aplikacji
 
Zablokuj dostęp lub wyczyść dane aplikacji zarządzanej na podstawie Ochrona punktu końcowego w usłudze Microsoft Defender sygnalizowania ryzyka przez utworzenie zasad ochrony aplikacji.
Ochrona punktu końcowego w usłudze Microsoft Defender skonfigurować do wysyłania sygnałów zagrożeń, które mają być używane w zasadach ochrony aplikacji (APP, znaną także jako MAM). Dzięki tej funkcji możesz chronić aplikacje zarządzane Ochrona punktu końcowego w usłudze Microsoft Defender za pomocą funkcji zarządzania.

1. Tworzenie zasad <br>
Ochrona aplikacji (APP) to reguły, które zapewniają, że dane organizacji pozostają bezpieczne lub znajdują się w zarządzanej aplikacji. Zasady mogą być regułą wymuszaną podczas próby uzyskania dostępu do danych firmowych lub przenoszenia ich przez użytkownika albo zestawem działań zabronionych lub monitorowanych, gdy użytkownik znajduje się w aplikacji. 

:::image type="content" source="images/create-policy.png" alt-text="Karta Tworzenie zasad w Ochrona aplikacji zasad grupy" lightbox="images/create-policy.png":::

2. Dodawanie aplikacji <br>
    a. Wybierz sposób stosowania tych zasad do aplikacji na różnych urządzeniach. Następnie dodaj co najmniej jedną aplikację. <br>
    Użyj tej opcji, aby określić, czy te zasady mają zastosowanie do urządzeń niezamanektowych. Możesz także kierować zasady do aplikacji na urządzeniach o dowolnym stanie zarządzania.
Ponieważ zarządzanie aplikacją mobilną nie wymaga zarządzania urządzeniami, możesz chronić dane firmowe zarówno na urządzeniach zarządzanych, jak i nieza zarządzania. Zarządzanie jest wyśrodkowane na tożsamości użytkownika, co usuwa wymaganie zarządzania urządzeniami. Firmy mogą jednocześnie korzystać z zasad ochrony aplikacji z usługą MDM lub bez nich. Rozważ na przykład pracownika, który używa zarówno telefonu wystawionego przez firmę, jak i własnego tabletu osobistego. Telefon firmowy jest zarejestrowany w usłudze MDM i chroniony za pomocą zasad ochrony aplikacji, natomiast urządzenie osobiste jest chronione tylko przez zasady ochrony aplikacji.

    b. Wybierz aplikacje<br>
    Aplikacja zarządzana to aplikacja, do która ma zastosowane zasady ochrony aplikacji i może być zarządzana przez Intune. Każdą aplikację, która została zintegrowana z zestawem [SDK pakietu Intune](/mem/intune/developer/app-sdk) lub zawijona przez [](/mem/intune/developer/apps-prepare-mobile-application-management) Intune App Wrapping Tool, można zarządzać przy użyciu Intune zasad ochrony aplikacji. Zapoznaj się z oficjalna [listą Microsoft Intune aplikacji](/mem/intune/apps/apps-supported-intune-apps) chronionych, które zostały stworzone przy użyciu tych narzędzi i są dostępne do użytku publicznego.

    *Przykład: Outlook jako aplikacja zarządzana*

     :::image type="content" source="images/managed-app.png" alt-text="Element menu Outlook Microsoft w lewym okienku nawigacji" lightbox="images/managed-app.png":::
  

 3. Ustaw wymagania dotyczące zabezpieczeń logowania dla zasad ochrony. <br>
Wybierz **pozycję > maksymalny dozwolony poziom zagrożeń** urządzenia w warunkach **urządzenia i wprowadź** wartość. Następnie wybierz  **pozycję Akcja: "Blokuj dostęp"**. Ochrona punktu końcowego w usłudze Microsoft Defender urządzeniach z systemem iOS jest udostępniany ten poziom zagrożeń dla urządzenia.

    
   :::image type="content" source="images/conditional-launch.png" alt-text="Okienko warunków urządzenia" lightbox="images/conditional-launch.png":::

4. Przypisz grupy użytkowników, do których mają zostać zastosowane zasady.<br>
  Wybierz **pozycję Uwzględnione grupy**. Następnie dodaj odpowiednie grupy. 


Aby uzyskać więcej informacji na temat zasad MAM lub ochrony aplikacji, zobacz [Ustawienia zasad ochrony aplikacji systemu iOS](/mem/intune/apps/app-protection-policy-settings-ios).

## <a name="deploy-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender dla mam lub na nie zarejestrowanych urządzeniach

Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS włącza scenariusz zasad ochrony aplikacji i jest dostępny w sklepie z aplikacjami firmy Apple.

Gdy zasady ochrony aplikacji są skonfigurowane dla aplikacji tak, aby zawierały sygnały ryzyka związane z urządzeniem Ochrona punktu końcowego w usłudze Microsoft Defender urządzenia, użytkownicy będą przekierowywani w celu zainstalowania Ochrona punktu końcowego w usłudze Microsoft Defender używania tych aplikacji. Użytkownicy mogą również zainstalować najnowszą wersję aplikacji bezpośrednio ze sklepu App Store firmy Apple.
