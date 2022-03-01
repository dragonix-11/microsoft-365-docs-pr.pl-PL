---
title: Wdrażanie programu Microsoft Defender dla punktu końcowego w funkcjach systemu iOS
description: W tym artykule opisano, jak wdrożyć usługę Microsoft Defender for Endpoint na nie zarejestrowanych urządzeniach z systemem iOS.
keywords: microsoft, defender, Microsoft Defender for Endpoint, ios, configure, features, ios
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
ms.openlocfilehash: 082e03100c366294a193d5fc7eb3cf0dd868caa6
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63013891"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-unenrolled-ios-devices"></a>Wdrażanie programu Microsoft Defender dla punktu końcowego na niepodjętych urządzeniach z systemem iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Usługa Defender for Endpoint w systemie iOS używa połączenia VPN w celu zapewnienia funkcji ochrony sieci Web. Nie jest to zwykły sieci VPN i jest to lokalny/samopętny vpn, który nie przejmuje ruchu poza urządzenie.

## <a name="configure-microsoft-defender-for-endpoint-risk-signals-in-app-protection-policy-mam"></a>Konfigurowanie programu Microsoft Defender pod celu obsługi sygnałów ryzyka dla punktu końcowego w zasadach ochrony aplikacji (MAM)

Program Microsoft Defender for Endpoint w systemie iOS, który już chroni użytkowników przedsiębiorstwa w scenariuszach zarządzania urządzeniami przenośnymi (MDM), teraz obsługuje zarządzanie aplikacjami mobilnymi (MAM) dla urządzeń, które nie są zarejestrowane przy użyciu zarządzania urządzeniami przenośnymi Intune (MDM). Obejmuje to również klientów korzystających z innych rozwiązań do zarządzania mobilnością w przedsiębiorstwie, jednocześnie używających usługi Intune do zarządzania aplikacjami mobilnymi (MAM). Ta funkcja umożliwia zabezpieczanie danych organizacji i zarządzanie nimi w obrębie aplikacji.

Program Microsoft Defender for Endpoint dla informacji o zagrożeniach w systemie iOS korzysta z zasad usługi Intune App Protection w celu ochrony tych aplikacji. Zasady ochrony aplikacji (APP) to reguły, które zapewniają, że dane organizacji pozostają bezpieczne lub znajdują się w zarządzanej aplikacji. Aplikacja zarządzana ma zastosowane zasady ochrony aplikacji i może być zarządzana przez usługę Intune.  

Program Microsoft Defender for Endpoint w systemie iOS obsługuje obie konfiguracje mam
- **Intune MDM + MAM**: administratorzy IT mogą zarządzać aplikacjami tylko za pomocą zasad ochrony aplikacji na urządzeniach zarejestrowanych za pomocą zarządzania urządzeniami przenośnymi Intune (MDM).
- **MAM bez rejestracji urządzeń**: MAM bez rejestracji urządzenia lub MAM-WE, umożliwia administratorom informatycznym zarządzanie aplikacjami przy [](/mem/intune/app/app-protection-policy) użyciu zasad ochrony aplikacji na urządzeniach, które nie zostały zarejestrowane za pomocą usługi Intune MDM. Oznacza to, że aplikacjami można zarządzać w usłudze Intune na urządzeniach zarejestrowanych u dostawców usług EMM innych firm. Aby zarządzać aplikacjami przy użyciu w obu powyższych konfiguracjach, klienci powinni używać usługi Intune w centrum [Microsoft Endpoint Manager administracyjnego](https://go.microsoft.com/fwlink/?linkid=2109431)

Aby włączyć tę funkcję, administrator musi skonfigurować połączenie między usługą Microsoft Defender for Endpoint i Intune, utworzyć zasady ochrony aplikacji i zastosować je na urządzeniach i aplikacjach ukierunkowanych. 
 
Użytkownicy końcowi muszą również wykonać kroki instalacji programu Microsoft Defender dla punktu końcowego na swoim urządzeniu i aktywowania przepływu dołączania.

### <a name="pre-requisites"></a>Wymagania wstępne

1. **Sprawdź, czy jest włączony łącznik**. <br> Na [ujednoliconej konsoli zabezpieczeń](https://security.microsoft.com) przejdź do Ustawienia **EndpointsAdvanced** >  **Features** i upewnij się,  >  że **Microsoft Intune jest włączone** połączenie sieciowe.

  ![Obraz łącznika Defender for Endpoint -Intune](images/enable-intune-connection.png)
  
2. **Sprawdź, czy łącznik jest włączony w portalu Usługi Intune**. <br> W [centrum administracyjnym menedżera punktu końcowego firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do pozycji **Zabezpieczenia** >  punktu końcowegoMicrosoft **Defender for Endpoint** i upewnij się, że stan połączenia jest włączony.

  ![Ustawienia aplikacji](images/app-settings.png)

### <a name="create-an-app-protection-policy"></a>Tworzenie zasad ochrony aplikacji
 
Blokowanie dostępu lub czyszczenie danych aplikacji zarządzanej w oparciu o usługę Microsoft Defender dla punktów końcowych sygnalizuje przez utworzenie zasad ochrony aplikacji.
Program Microsoft Defender for Endpoint można skonfigurować do wysyłania sygnałów zagrożeń, które mają być używane w zasadach ochrony aplikacji (APP, znaną także jako MAM). Dzięki tej funkcji można chronić zarządzane aplikacje za pomocą programu Microsoft Defender for Endpoint.

1. Tworzenie zasad <br>
Zasady ochrony aplikacji (APP) to reguły, które zapewniają, że dane organizacji pozostają bezpieczne lub znajdują się w zarządzanej aplikacji. Zasady mogą być regułą wymuszaną podczas próby uzyskania dostępu do danych firmowych lub przenoszenia ich przez użytkownika albo zestawem działań zabronionych lub monitorowanych, gdy użytkownik znajduje się w aplikacji. 

![Obraz tworzenia zasad](images/create-policy.png)

2. Dodawanie aplikacji <br>
    a. Wybierz sposób stosowania tych zasad do aplikacji na różnych urządzeniach. Następnie dodaj co najmniej jedną aplikację. <br>
    Użyj tej opcji, aby określić, czy te zasady mają zastosowanie do urządzeń niezamanektowych. Możesz także kierować zasady do aplikacji na urządzeniach o dowolnym stanie zarządzania.
Ponieważ zarządzanie aplikacją mobilną nie wymaga zarządzania urządzeniami, możesz chronić dane firmowe zarówno na urządzeniach zarządzanych, jak i nieza zarządzania. Zarządzanie jest wyśrodkowane na tożsamości użytkownika, co usuwa wymaganie zarządzania urządzeniami. Firmy mogą jednocześnie korzystać z zasad ochrony aplikacji z usługą MDM lub bez nich. Rozważ na przykład pracownika, który używa zarówno telefonu wystawionego przez firmę, jak i własnego tabletu osobistego. Telefon firmowy jest zarejestrowany w usłudze MDM i chroniony za pomocą zasad ochrony aplikacji, natomiast urządzenie osobiste jest chronione tylko przez zasady ochrony aplikacji.

    b. Wybierz aplikacje<br>
    Aplikacja zarządzana to aplikacja, do która ma zastosowane zasady ochrony aplikacji i może być zarządzana przez usługę Intune. Każdą aplikację, która została zintegrowana z zestawem [SDK usługi Intune](/mem/intune/developer/app-sdk) lub zawijona przez zestaw [Intune App Wrapping Tool](/mem/intune/developer/apps-prepare-mobile-application-management) można zarządzać przy użyciu zasad ochrony aplikacji Intune. Zapoznaj się z oficjalna [listą Microsoft Intune aplikacji](/mem/intune/apps/apps-supported-intune-apps) chronionych, które zostały stworzone przy użyciu tych narzędzi i są dostępne do użytku publicznego.

    *Przykład: Outlook jako aplikacja zarządzana*

    ![Obraz Outlook jako aplikacja zarządzana](images/managed-app.png)

 3. Ustaw wymagania dotyczące zabezpieczeń logowania dla zasad ochrony. <br>
Wybierz **pozycję > maksymalny dozwolony poziom zagrożeń** urządzenia w warunkach **urządzenia i wprowadź** wartość. Następnie wybierz  **pozycję Akcja: "Blokuj dostęp"**. Program Microsoft Defender for Endpoint w systemie iOS udostępnia ten poziom zagrożeń urządzeń.

    ![Obraz uruchamiania warunkowego](images/conditional-launch.png)

4. Przypisz grupy użytkowników, do których mają zostać zastosowane zasady.<br>
  Wybierz **pozycję Uwzględnione grupy**. Następnie dodaj odpowiednie grupy. 


Aby uzyskać więcej informacji na temat zasad MAM lub ochrony aplikacji, zobacz [Ustawienia zasad ochrony aplikacji systemu iOS](/mem/intune/apps/app-protection-policy-settings-ios).

## <a name="deploy-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>Wdrażanie programu Microsoft Defender dla punktu końcowego dla mam lub na nie zarejestrowanych urządzeniach

Program Microsoft Defender for Endpoint w systemie iOS włącza scenariusz zasad ochrony aplikacji i jest dostępny w sklepie z aplikacjami firmy Apple.

Gdy zasady ochrony aplikacji są skonfigurowane dla aplikacji tak, aby zawierały sygnały ryzyka związane z urządzeniem z usługi Microsoft Defender for Endpoint, użytkownicy będą przekierowywani w celu zainstalowania programu Microsoft Defender for Endpoint podczas korzystania z takich aplikacji. Użytkownicy mogą również zainstalować najnowszą wersję aplikacji bezpośrednio ze sklepu App Store firmy Apple.
