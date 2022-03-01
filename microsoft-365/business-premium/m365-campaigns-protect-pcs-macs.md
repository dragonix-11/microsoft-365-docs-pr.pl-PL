---
title: Ochrona niezamanektowych Windows 10 PC i Mac
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
description: Chroń niezakierowane lub przynieś własne urządzenia (BYOD) za pomocą Microsoft 365.
ms.openlocfilehash: 0f14112356313dcbad56f5a78bd2c837987d234f
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011427"
---
# <a name="protect-unmanaged-windows-10-pcs-and-macs"></a>Ochrona niezamanektowych Windows 10 PC i Mac

Możesz zarządzać komputerami Windows 10 i Mac, rejestrując je w programie Microsoft Intune, co pozwoli zapewnić ich kondycję i bezpieczeństwo przed uzyskaniem dostępu do danych w Twoim środowisku. Jednak wiele kampanii i małych firm obejmuje pracowników, którzy wprowadzają własne urządzenia (BYOD), które nie będą zarządzane przez organizację. W przypadku tych niezawiąanych komputerów PC i Mac skorzystaj z tego artykułu, aby upewnić się, że skonfigurowano minimalne funkcje zabezpieczeń.

<!--A Windows 10 PC is considered managed after you have completed the following two steps:

1. You (or the admin) set up device and data protection policies in the [setup  wizard](../business/set-up.md).

2. You have [connected your computer to Azure Active Directory](../business/set-up-windows-devices.md) and use your Microsoft 365 username and password to sign in.
3. --> 

## <a name="protect-a-computer-running-windows-10-or-a-mac"></a>Ochrona komputera z systemem Windows 10 komputera Mac

<!--If you have a PC that is running Windows 10 that is not connected to Microsoft 365, or a Mac, the Microsoft 365 protections do not apply to it, but here are some things you can do to keep your data secure on these devices as well:
-->
Jeśli Twoja Windows 10 PC lub Mac nie jest zarządzana przez Twoją organizację, skonfiguruj te funkcje zabezpieczeń.

## <a name="windows-10"></a>[Windows 10](#tab/Windows10)

**Włączanie szyfrowania urządzeń**<p>

Szyfrowanie urządzeń jest dostępne na wielu urządzeniach z Windows i pomaga chronić dane przez ich szyfrowanie. Jeśli włączysz szyfrowanie urządzeń, tylko uprawnione osoby będą mogły uzyskać dostęp do Twojego urządzenia i danych. Aby [uzyskać instrukcje, zobacz Włączanie szyfrowania](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) urządzeń.

 Jeśli na Twoim urządzeniu nie jest dostępne szyfrowanie urządzeń, możesz włączyć standardowe szyfrowanie [BitLocker](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) . (Funkcją BitLocker nie jest dostępna w Windows 10 Home wersji). 

**Ochrona urządzenia za pomocą Zabezpieczenia Windows**<p>
Jeśli masz Windows 10, będziesz mieć dostęp do najnowszej ochrony antywirusowej dzięki programowi Zabezpieczenia Windows. Po uruchomieniu programu Windows 10 po raz pierwszy program Zabezpieczenia Windows jest wł. i aktywnie chroni komputer, skanując w poszukiwaniu złośliwego oprogramowania, wirusów i zagrożeń dla bezpieczeństwa. Zabezpieczenia Windows wszystko, co pobierasz lub uruchamiasz na komputerze, jest skanowane za pomocą ochrony w czasie rzeczywistym.

Windows Update automatycznie pobiera aktualizacje dla Zabezpieczenia Windows, aby zapewnić bezpieczeństwo komputera i chronić go przed zagrożeniami.

Jeśli masz wcześniejszą wersję programu Windows i używasz programu Microsoft Security Essentials, warto przejść do programu Zabezpieczenia Windows. Aby uzyskać więcej informacji, [zobacz Zapewnianie ochrony urządzenia za pomocą Zabezpieczenia Windows](https://support.microsoft.com/help/17464/windows-10-help-protect-my-device-with-windows-security).

**Włączanie zapory Windows sieciowej**<p>
Nawet jeśli włączona jest inna zapora, Windows zawsze powinna być włączona. Wyłączenie zapory Windows może spowodować, że urządzenie (i sieć, jeśli jest już na nich działa), będzie bardziej narażone na nieautoryzowany dostęp. Aby [uzyskać instrukcje Windows włączyć lub wyłączyć Zaporę](https://support.microsoft.com/help/4028544/windows-10-turn-windows-defender-firewall-on-or-off) sieciową.

## <a name="mac"></a>[Mac](#tab/Mac)

**Szyfrowanie dysku komputera Mac przy użyciu funkcji FileVault**<p>
Szyfrowanie dysku chroni dane w przypadku zgubienia lub kradzieży urządzenia. Pełne szyfrowanie dysku FileVault uniemożliwia nieautoryzowany dostęp do informacji na dysku startowym. Aby [uzyskać instrukcje, zobacz Szyfrowanie dysku startowego](https://support.apple.com/HT204837) na komputerze Mac za pomocą funkcji FileVault.

**Ochrona komputera Mac przed złośliwym oprogramowaniem**<p>
Firma Microsoft zaleca zainstalowanie na komputerze Mac i używanie niezawodnego oprogramowania antywirusowego. Zapoznaj się z następującym artykułem, aby uzyskać listę opcji: [Najlepsze oprogramowanie antywirusowe dla komputerów Mac 2019](https://www.macworld.co.uk/feature/mac-software/mac-antivirus-3672182/).

Ryzyko związane ze złośliwym oprogramowaniem można też zmniejszyć, używając tylko oprogramowania z wiarygodnych źródeł. Ustawienia w preferencjach & zabezpieczeń i prywatności umożliwiają określenie źródeł oprogramowania zainstalowanych na komputerze Mac. Aby uzyskać więcej informacji, zobacz [Ochrona komputera Mac przed złośliwym oprogramowaniem](https://support.apple.com/kb/PH25087).

**Włączanie ochrony zapór**<p>
Użyj ustawień zapory, aby chronić komputer Mac przed niechcianymi połączeniami inicjowanymi przez inne komputery, gdy masz połączenie z Internetem lub siecią. Bez tej ochrony komputer Mac może być bardziej narażony na nieautoryzowany dostęp. [Instrukcje zawiera zapora](https://support.apple.com/HT201642) aplikacji.
