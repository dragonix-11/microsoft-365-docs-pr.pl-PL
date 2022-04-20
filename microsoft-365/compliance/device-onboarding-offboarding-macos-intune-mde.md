---
title: Dołączanie i dołączanie urządzeń z systemem macOS do rozwiązań zgodności przy użyciu Microsoft Intune dla klientów Ochrona punktu końcowego w usłudze Microsoft Defender
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Dowiedz się, jak dołączać i dołączać urządzenia z systemem macOS do rozwiązań usługi Microsoft Purview przy użyciu Microsoft Intune dla klientów mde
ms.openlocfilehash: c6b374ad3c35ba3441e82412d9897132006d0559
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64952847"
---
# <a name="onboard-and-offboard-macos-devices-into-compliance-solutions-using-intune-for-microsoft-defender-for-endpoint-customers"></a>Dołączanie i dołączanie urządzeń z systemem macOS do rozwiązań zgodności przy użyciu Intune dla klientów Ochrona punktu końcowego w usłudze Microsoft Defender

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!IMPORTANT]
> Użyj tej procedury ***, jeśli wdrożono*** Ochrona punktu końcowego w usłudze Microsoft Defender (MDE) na urządzeniach z systemem macOS

**Dotyczy:**

- Klienci, którzy wdrożyli rozwiązanie MDE na swoich urządzeniach z systemem macOS.
- [Ochrona przed utratą danych punktu końcowego (DLP)](./endpoint-dlp-learn-about.md)
- [Zarządzanie ryzykiem wewnętrznym](insider-risk-management.md)


## <a name="before-you-begin"></a>Przed rozpoczęciem

- Upewnij się, że [urządzenia z systemem macOS zostały dołączone do Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) i zarejestrowane w [aplikacji Portal firmy](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- Upewnij się, że masz dostęp do [centrum Microsoft Endpoint Manager](https://endpoint.microsoft.com/#home)
- Obsługuje to system macOS w wersji Catalina 10.15 lub nowszej
- Instalowanie przeglądarki v95+ Edge na urządzeniach z systemem macOS 

## <a name="onboard-macos-devices-into-microsoft-purview-solutions-using-microsoft-intune"></a>Dołączanie urządzeń z systemem macOS do rozwiązań usługi Microsoft Purview przy użyciu Microsoft Intune

Wykonaj te kroki, aby dołączyć urządzenie z systemem macOS do rozwiązań zgodności, jeśli zostało już wdrożone w nim rozwiązanie MDE.

1. Te pliki będą potrzebne do tej procedury.

|plik wymagany do |Źródła |
|---------|---------|
|Dostępności |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
pełny dostęp do dysku     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|

> [!TIP]
> Pliki *mobileconfig* można pobrać pojedynczo lub w [jednym połączonym pliku](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) , który zawiera:
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> 
>
>Jeśli którykolwiek z tych pojedynczych plików zostanie zaktualizowany, konieczne będzie ponowne pobranie połączonego pliku lub pojedynczego zaktualizowanego pliku indywidualnie.

### <a name="create-system-configuration-profiles"></a>Tworzenie profilów konfiguracji systemu

1. Otwórz **Microsoft Endpoint Manager** **centerDevicesProfile** >  >  **konfiguracji**.

1. Wybierz: **Utwórz profil**. 

1. Wybierz:
    1. **Platforma = macOS**
    1. **Typ profilu = Szablony**
    1. **Nazwa szablonu = Niestandardowa**

1. Wybierz **pozycję Utwórz**

1. W tym przykładzie wybierz nazwę profilu, na przykład *AccessibilityformacOS* . Wybierz przycisk **Dalej**.

1. Wybierz plik **accessibility.mobileconfig** pobrany w kroku 1 jako plik profilu konfiguracji.

1. Wybierz **pozycję Dalej**

1. Na **karcie Przypisania** dodaj grupę, do którą chcesz wdrożyć te konfiguracje, i wybierz pozycję **Dalej**.

1. Przejrzyj ustawienia i wybierz pozycję **Utwórz** , aby wdrożyć konfigurację.

1. Otwórz **pozycję** **UrządzeniaProfile** >  konfiguracji. Powinny zostać tam wyświetlone utworzone profile.

1. Na stronie **Profile konfiguracji wybierz właśnie** utworzony profil, w tym *przykładzie AccessibilityformacOS* i wybierz pozycję **Stan urządzenia** , aby wyświetlić listę urządzeń i stan wdrożenia profilu konfiguracji.

### <a name="update-configuration-profiles"></a>Aktualizowanie profilów konfiguracji

1. Zaktualizuj istniejący profil pełnego dostępu do dysku przy użyciu pliku **fulldisk.mobileconfig** .

1. Zaktualizuj profil preferencji mde exisiting przy użyciu tych wartości
   
```xml
<key>features</key>
<dict>
    <key>systemExtensions</key>
    <string>enabled</string>
    <key>dataLossPrevention</key>
    <string>enabled</string>
</dict>
```

## <a name="offboard-macos-devices-using-intune"></a>Odłączanie urządzeń z systemem macOS przy użyciu Intune

> [!IMPORTANT]
> Odłączanie powoduje, że urządzenie przestaje wysyłać dane czujnika do portalu, ale dane z urządzenia, w tym odwołanie do wszelkich alertów, które miał, zostaną zachowane przez maksymalnie 6 miesięcy.

1. W **centrum Microsoft Endpoint Manager** otwórz pozycję **UrządzeniaProfile** >  konfiguracji, w tym miejscu powinny zostać wyświetlone utworzone profile.

2. Na stronie **Profile konfiguracji** wybierz profil preferencji MDE.

1. Usuń następujące ustawienia:
   
```xml
<key>features</key>
<dict>
    <key>systemExtensions</key>
    <string>enabled</string>
    <key>dataLossPrevention</key>
    <string>enabled</string>
</dict>
```
3. **Zapisz**.
