---
title: Dołączanie i wydojadowanie urządzeń macOS do rozwiązań zgodności przy Microsoft Intune microsoft Defender dla klientów korzystających z punktu końcowego (wersja Preview)
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
description: Dowiedz się, jak dołączać i wydojać urządzenia z systemem macOS Microsoft 365 rozwiązania zgodności przy Microsoft Intune dla klientów MDE (wersja zapoznawcza)
ms.openlocfilehash: 6cc4362e924f291c6a8396bff342c6f628e33be3
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526558"
---
# <a name="onboard-and-offboard-macos-devices-into-compliance-solutions-using-intune-for-microsoft-defender-for-endpoint-customers-preview"></a>Dołączanie i wydojażanie urządzeń macOS w rozwiązaniach zgodności przy użyciu usługi Intune dla klientów programu Microsoft Defender for Endpoint (wersja preview)

> [!IMPORTANT]
> Skorzystaj z tej ***procedury, jeśli program*** Microsoft Defender for Endpoint (MDE) został wdrożony na urządzeniach z systemem macOS

**Dotyczy:**

- Klienci, którzy wdrożyli aplikację MDE na swoich urządzeniach z systemem macOS.
- [Microsoft 365 punktu końcowego ochrony przed utratą danych (DLP)](./endpoint-dlp-learn-about.md)
- [Zarządzanie ryzykiem w niejawnym programie testów](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)


## <a name="before-you-begin"></a>Przed rozpoczęciem

- Upewnij się, [że urządzenia z systemem macOS są podłączone do usługi Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) i zarejestrowane w Portal firmy [aplikacji](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- Upewnij się, że masz dostęp do centrum [Microsoft Endpoint Manager konta](https://endpoint.microsoft.com/#home)
- Obsługuje to system macOS w wersji Catalina w wersji 10.15 i w wersji wyższej
- Instalowanie przeglądarki Edge w wersji 95+ na urządzeniach z systemem macOS 

## <a name="onboard-macos-devices-into-microsoft-365-compliance-solutions-using-microsoft-intune"></a>Na urządzeniach z systemem macOS można Microsoft 365 rozwiązania do zgodności przy użyciu Microsoft Intune

Skorzystaj z tej procedury, aby wdrożyć urządzenie z systemem macOS w rozwiązaniach zgodności, jeśli już w nim wdrożono funkcję MDE.

1. Te pliki będą potrzebne do tej procedury.

|wymagany dla |źródło |
|---------|---------|
|ułatwienia dostępu |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
pełny dostęp do dysku     |[fullconfig.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|

> [!TIP]
> Możesz pobrać pliki *.mobileconfig* pojedynczo lub w [jednym połączonym pliku](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) , który zawiera:
> - accessibility.mobileconfig
> - fullconfig.mobileconfig
> 
>
>Jeśli którykolwiek z tych pojedynczych plików zostanie zaktualizowany, konieczne będzie pobranie ponownie połączonego pliku lub pojedynczego aktualizowanego pliku.

### <a name="create-system-configuration-profiles"></a>Tworzenie profilów konfiguracji systemu

1. Otwórz centrum **Microsoft Endpoint Manager** >  **UrządnianiaKonfiguracja** >  **profilów**.

1. Wybierz pozycję: **Utwórz profil**. 

1. Wybierz pozycję:
    1. **Platforma = macOS**
    1. **Typ profilu = Szablony**
    1. **Nazwa szablonu = Niestandardowe**

1. Wybierz pozycję **Create (Utwórz)**

1. W tym przykładzie wybierz nazwę profilu, na przykład *AccessibilityformacOS* . Wybierz przycisk **Dalej**.

1. Wybierz plik **accessibility.mobileconfig** pobrany w kroku 1 jako plik profilu konfiguracji.

1. Wybierz przycisk **Dalej**

1. Na **karcie Zadania dodaj** grupę, w której chcesz wdrożyć te konfiguracje, i wybierz pozycję **Dalej**.

1. Przejrzyj ustawienia i wybierz pozycję **Utwórz,** aby wdrożyć konfigurację.

1. Otwórz **profile** **DevicesConfiguration** > , powinny być tam dostępne utworzone profile.

1. Na **stronie Profile konfiguracji** wybierz utworzony profil, w tym przykładzie *AccessibilityformacOS* i wybierz pozycję Stan urządzenia, aby  wyświetlić listę urządzeń i stan wdrożenia profilu konfiguracji.

### <a name="update-configuration-profiles"></a>Aktualizowanie profilów konfiguracji

1. Zaktualizuj istniejący pełny profil dostępu do dysku przy użyciu **pliku fullconfig.mobileconfig** .

1. Aktualizowanie exisiting MDE preferences profile with these values
   
```xml
<key>features</key>
<dict>
    <key>systemExtensions</key>
    <string>enabled</string>
    <key>dataLossPrevention</key>
    <string>enabled</string>
</dict>
```

## <a name="offboard-macos-devices-using-intune"></a>Urządzenia z systemem macOS w usłudze Intune

> [!IMPORTANT]
> Wynoszenie powoduje, że urządzenie przestaje wysyłać dane czujnika do portalu, ale dane z urządzenia, w tym odwołania do wszelkich posiadanych alertów, będą przechowywane przez maksymalnie 6 miesięcy.

1. W **Microsoft Endpoint Manager Otwórz** **urządzeniaKonfiguracja** >  profile powinny być tam dostępne utworzone profile.

2. Na stronie **Profile konfiguracji** wybierz profil preferencji MDE.

1. Usuń te ustawienia:
   
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