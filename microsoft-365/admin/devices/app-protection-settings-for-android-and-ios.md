---
title: Konfigurowanie ustawień ochrony aplikacji dla urządzeń z systemem Android lub iOS
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: 6f2b80b4-81c3-4714-a7bc-ae69313e8a33
description: Dowiedz się, jak tworzyć, edytować lub usuwać zasady zarządzania aplikacją oraz jak chronić pliki służbowe na urządzeniach z systemem Android lub iOS.
ms.openlocfilehash: 6849b24f691f7b567cc55dce2dda21f2a7e93f22
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313989"
---
# <a name="set-app-protection-settings-for-android-or-ios-devices"></a>Konfigurowanie ustawień ochrony aplikacji dla urządzeń z systemem Android lub iOS

Ten artykuł dotyczy wszystkich Microsoft 365 Business Premium.

> [!NOTE]
> Program Microsoft Defender dla firm jest wprowadzany dla Microsoft 365 Business Premium klientów od 1 marca 2022 r. Ta oferta oferuje dodatkowe funkcje zabezpieczeń dla urządzeń. [Dowiedz się więcej o uchcie programu Defender dla firm](../../security/defender-business/mdb-overview.md).

## <a name="watch-secure-office-apps-on-ios"></a>Obejrzyj: Zabezpieczanie Office w systemie iOS

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FLvZ?autoplay=false]

Możesz skonfigurować zasady dostępu użytkowników, które wymagają, aby użytkownicy mobilni wprowadzali numer PIN lub odcisk palca w celu zalogowania się, a także szyfrować pliki służbowe przechowywane na ich urządzeniach.

1. Zaloguj się do <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjnego usługi Microsoft 365</a>.
1. W **obszarze Zasady** wybierz **pozycję Dodaj zasady**.
1. W **okienku Dodaj** zasady wprowadź nazwę w obszarze Nazwa **zasad i wybierz** odpowiedni typ zasad w obszarze **Typ zasad**.
1. Włącz zarządzanie **dostępem użytkowników do Office na** urządzeniach przenośnych, a następnie upewnij się, że są włączone następujące trzy ustawienia:
    - **Wymagaj numeru PIN lub odcisku palca w celu uzyskania dostępu do aplikacji pakietu Office**
    - **Chroń pliki służbowe w przypadku zgubienia lub kradzieży urządzenia**
    - **Szyfruj pliki służbowe**

1. W **obszarze Pliki w tych aplikacjach będą chronione** wybierz Office, które chcesz chronić na urządzeniach przenośnych.
1. W **KtoTo ustawienia?**, wszyscy użytkownicy są wybrani domyślnie, ale możesz wybrać pozycję Zmień, aby wybrać utworzone przez  Ciebie grupy zabezpieczeń.
1. Aby zakończyć tworzenie zasad, wybierz pozycję **Dodaj**.
1. Na stronie **Dodawanie zasad** wybierz pozycję **Zamknij**.
1. Na stronie głównej centrum administracyjnego potwierdź dodanie nowych zasad, wybierając pozycję Zasady  i przeglądając **zasady na stronie** Zasady.

## <a name="create-an-app-management-policy"></a>Tworzenie zasad zarządzania aplikacjami

1. Przejdź do centrum administracyjnego w stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>. 
    
2. W lewym okienku narracji wybierz pozycję **Urządzenia Zasady** \> **Dodaj**\>.
  
3. W okienku **Dodawanie zasad** wprowadź unikatową nazwę dla zasad. 
    
4. W **obszarze Typ zasad** wybierz **pozycję Zarządzanie aplikacją dla systemu Android** lub Zarządzanie aplikacją dla systemu **iOS** w zależności od tego, jaki zestaw zasad chcesz utworzyć. 
    
5. **Rozwiń temat Chroń pliki służbowe w** przypadku zgubienia lub kradzieży urządzenia i Zarządzaj **dostępem użytkowników do Office na urządzeniach przenośnych**. Skonfiguruj ustawienia w taki sposób, jak chcesz. **Opcja Zarządzaj dostępem użytkowników Office** na urządzeniach przenośnych jest domyślnie  wyłączona, ale zalecamy jej włączenie i zachowanie wartości domyślnych. Aby uzyskać więcej informacji, zobacz [Dostępne ustawienia](#available-settings). 
    
    Aby zresetować ustawienia do wartości domyślnych, w dowolnej chwili możesz użyć linku **Resetuj ustawienia domyślne**. 
    
    ![Zrzut ekranu przedstawiający tworzenie zasad z wybraną elekcją Zarządzanie aplikacją dla systemu Android.](../../media/eabbe06d-ac0a-4f3a-8630-68c808b1e662.png)
  
6. Next decide **Who will get these settings?** Jeśli nie chcesz używać domyślnej grupy zabezpieczeń **Wszyscy** użytkownicy, wybierz pozycję **Zmień**, wybierz grupy zabezpieczeń, które uzyskają te **ustawienia Wybierz**\>.
    
7. Na koniec wybierz przycisk **Gotowe**, aby zapisać zasady i zastosować je na urządzeniach. 
    
## <a name="edit-an-app-management-policy"></a>Edytowanie zasad zarządzania aplikacjami

1. Na karcie **Zasady** wybierz pozycję **Edytuj zasady**.
    
2. W okienku **Edytowanie zasad** wybierz zasadę, którą chcesz zmienić. 
    
3. Wybierz opcję **Edytuj** obok poszczególnych ustawień, aby zmienić wartości zasad. Zmiana wartości spowoduje automatyczne zapisanie jej w zasadach.
    
4. Po zakończeniu zamknij okienko **Edytowanie zasad** . 
    
## <a name="delete-an-app-management-policy"></a>Usuwanie zasad zarządzania aplikacjami

1. Na stronie **Zasady** wybierz zasady, a następnie wybierz pozycję **Usuń**.
    
2. W **okienku Usuwanie zasad** wybierz pozycję **Potwierdź** , aby usunąć wybrane zasady. 
    
## <a name="available-settings"></a>Dostępne ustawienia

W poniższych tabelach szczegółowo opisano ustawienia dostępne w celu ochrony plików służbowych na urządzeniach oraz ustawienia, które sterują dostępem użytkowników do plików Office z urządzeń przenośnych.
  
 Aby uzyskać więcej informacji, zobacz [Jak działa funkcja ochrony w Microsoft 365 Business Premium mapowanie do ustawień usługi Intune](map-protection-features-to-intune-settings.md). 
  
### <a name="settings-that-protect-work-files"></a>Ustawienia chroniące pliki służbowe

W przypadku zgubienia lub kradzieży urządzenia użytkownika dostępne są następujące ustawienia chroniące pliki służbowe:


|Ustawienie  <br/> |Opis  <br/> |
|:-----|:-----|
|Usuń pliki służbowe z nieaktywnego urządzenia po określonej liczbie dni  <br/> |Jeśli urządzenie nie jest używane przez tę liczbę dni, która jest tutaj podana, wszelkie pliki służbowe przechowywane na urządzeniu zostaną automatycznie usunięte.  <br/> |
|Wymuszaj na użytkownikach zapisywanie wszystkich plików służbowych w usłudze OneDrive dla Firm  <br/> |Jeśli to ustawienie jest **Wł.**, jedyną dostępną lokalizacją zapisu plików służbowych jest OneDrive dla Firm.  <br/> |
|Szyfruj pliki służbowe  <br/> |Zachowaj to ustawienie **Włączone**, aby chronić pliki służbowe przy użyciu szyfrowania. Nawet jeśli urządzenie zostanie zgubione lub skradzione, nikt nie będzie miał możliwości odczytania danych firmowych.  <br/> |
   
### <a name="settings-that-control-how-users-access-office-files-on-mobile-devices"></a>Ustawienia, które sterują dostępem użytkowników do plików pakietu Office na urządzeniach przenośnych

Na potrzeby zarządzania dostępem użytkowników do plików służbowych w pakiecie Office dostępne są następujące ustawienia:


|Ustawienie  <br/> |Opis  <br/> |
|:-----|:-----|
|Wymagaj numeru PIN lub odcisku palca w celu uzyskania dostępu do aplikacji pakietu Office  <br/> |Jeśli to ustawienie jest  Wł., użytkownicy muszą podać inną formę uwierzytelniania, oprócz nazwy użytkownika i hasła, aby użytkownicy Office aplikacji na swoich urządzeniach przenośnych.<br/> |
|Resetuj numer PIN w przypadku wielokrotnego niepowodzenia logowania  <br/> |Aby uniemożliwić nieautoryzowanym użytkownikom odgadywanie kodu PIN, ten kod jest resetowany po określonej liczbie nieudanych prób jego podania.  <br/> |
|Wymagaj ponownego logowania użytkowników po czasie bezczynności aplikacji pakietu Office  <br/> |To ustawienie określa, jak długo użytkownik może nie być bezczynny, zanim zostanie wyświetlony monit o ponowne zalogowanie się.  <br/> |
|Odmów dostępu do plików służbowych na urządzeniach z usuniętymi natywnymi ograniczeniami producenta  <br/> |Sprytni użytkownicy mogą mieć urządzenie z usuniętymi natywnymi ograniczeniami producenta. Umożliwia to użytkownikowi modyfikowanie systemu operacyjnego, co może uczynić urządzenie bardziej podatnym na złośliwe oprogramowanie. Te urządzenia zostaną zablokowane, jeśli to ustawienie będzie **Włączone**.  <br/> |
|Nie zezwalaj użytkownikom na kopiowanie zawartości z aplikacji Office do aplikacji osobistych  <br/> |Domyślnie jest to dozwolone, ale gdy to ustawienie jest **włączone**, użytkownik może kopiować informacje z pliku służbowego do osobistego. Jeśli to ustawienie jest **wyłączone**, użytkownik nie będzie mógł kopiować informacji z konta służbowego do aplikacji osobistej ani na konto osobiste.  <br/> |

## <a name="see-also"></a>Zobacz też

[10 najlepszych sposobów zabezpieczania planów Microsoft 365 dla firm](../security-and-compliance/secure-your-business-data.md)