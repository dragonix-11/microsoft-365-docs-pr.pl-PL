---
title: Ochrona niezarządzanych komputerów z systemem Windows i komputerów Mac w Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
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
description: Ochrona urządzeń niezarządzanych lub przynieś własne urządzenia (BYOD) przed cyberatakami za pomocą Microsoft 365 Business Premium. Jak skonfigurować cyberbezpieczeństwo dla komputerów z systemem Windows i komputerów Mac.
ms.openlocfilehash: 5a1239f84e801c6327eb18c1049e410cc0859bdb
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66631777"
---
# <a name="protect-unmanaged-windows-pcs-and-macs-in-microsoft-365-business-premium"></a>Ochrona niezarządzanych komputerów z systemem Windows i komputerów Mac w Microsoft 365 Business Premium

Ten cel koncentruje się na tworzeniu ochrony dla wszelkich niezarządzanych komputerów Windows 10 i komputerów Mac, które nie są zarejestrowane w Microsoft Intune. Jest bardzo prawdopodobne, że twoja mała firma lub kampania może mieć pracowników, którzy przynoszą własne urządzenia (BYOD), a te urządzenia nie są zarządzane. Usługa BYOD obejmuje telefony, tablety i komputery należące do użytkownika.

>[!NOTE]
>Użytkownicy usługi BYOD muszą zainstalować i uruchomić aplikację Portal firmy, aby zarejestrować te urządzenia i uzyskać dostęp do zasobów firmy.

Niezwykle ważne jest, aby zapewnić, aby użytkownicy pierwszej linii postępowali zgodnie z tymi wytycznymi, aby minimalne możliwości zabezpieczeń były konfigurowane na wszystkich urządzeniach BYOD.

## <a name="windows-10-or-11"></a>[Windows 10 lub 11](#tab/Windows10-11)

## <a name="windows-10-or-11"></a>Windows 10 lub 11

### <a name="turn-on-device-encryption"></a>Włączanie szyfrowania urządzenia

Szyfrowanie urządzenia jest dostępne na wielu urządzeniach z systemem Windows i pomaga chronić dane przez ich szyfrowanie. Jeśli włączysz szyfrowanie urządzenia, tylko autoryzowane osoby będą mogły uzyskać dostęp do urządzenia i danych. Aby uzyskać instrukcje [, zobacz Włączanie szyfrowania urządzeń](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) .

 Jeśli szyfrowanie urządzenia nie jest dostępne na urządzeniu, możesz włączyć standardowe [szyfrowanie BitLocker](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption). (BitLocker nie jest dostępna w wersji Windows 10 Home). 

### <a name="protect-your-device-with-windows-security"></a>Ochrona urządzenia za pomocą Zabezpieczenia Windows

Jeśli masz Windows 10 lub 11, otrzymasz najnowszą ochronę antywirusową z Zabezpieczenia Windows. Po pierwszym uruchomieniu Windows 10 Zabezpieczenia Windows jest włączony i aktywnie pomaga chronić komputer, skanując pod kątem złośliwego oprogramowania (złośliwego oprogramowania), wirusów i zagrożeń bezpieczeństwa. Zabezpieczenia Windows używa ochrony w czasie rzeczywistym do skanowania wszystkiego, co pobierasz lub uruchamiasz na komputerze.

Windows Update pobiera aktualizacje dla Zabezpieczenia Windows automatycznie, aby zapewnić bezpieczeństwo komputera i chronić go przed zagrożeniami.

Jeśli masz starszą wersję systemu Windows i używasz programu Microsoft Security Essentials, dobrym pomysłem jest przejście do Zabezpieczenia Windows. Aby uzyskać więcej informacji, zobacz [pomoc w ochronie urządzenia za pomocą Zabezpieczenia Windows](https://support.microsoft.com/help/17464/windows-10-help-protect-my-device-with-windows-security).

### <a name="turn-on-windows-defender-firewall"></a>Włącz Zapora Windows Defender

Zawsze należy uruchamiać Zapora Windows Defender, nawet jeśli włączono inną zaporę. Wyłączenie Zapora Windows Defender może sprawić, że urządzenie (i sieć, jeśli je masz) będą bardziej narażone na nieautoryzowany dostęp. Aby uzyskać instrukcje [, zobacz Włączanie lub wyłączanie zapory systemu Windows](https://support.microsoft.com/help/4028544/windows-10-turn-windows-defender-firewall-on-or-off) .

## <a name="next-mission"></a>Następna misja

Dobra, misja zakończona! Teraz pracujemy nad [zabezpieczeniem systemu poczty e-mail](m365bp-protect-email-overview.md) przed wyłudzaniem informacji i innymi atakami.

## <a name="macos"></a>[macOS](#tab/macOS)

## <a name="macos"></a>macOS

### <a name="use-filevault-to-encrypt-your-mac-disk"></a>Szyfrowanie dysku mac przy użyciu programu FileVault

Szyfrowanie dysków chroni dane w przypadku utraty lub kradzieży urządzeń. Szyfrowanie pełnego dysku w usłudze FileVault pomaga zapobiegać nieautoryzowanemu dostępowi do informacji na dysku startowym. Aby uzyskać instrukcje [, zobacz używanie programu FileVault do szyfrowania dysku startowego na komputerze Mac](https://support.apple.com/HT204837) .

### <a name="protect-your-mac-from-malware"></a>Ochrona komputera Mac przed złośliwym oprogramowaniem

Firma Microsoft zaleca zainstalowanie i użycie niezawodnego oprogramowania antywirusowego na komputerze Mac. Zobacz następujący artykuł, aby uzyskać listę opcji: [Najlepszy program antywirusowy dla komputerów Mac 2019](https://www.macworld.co.uk/feature/mac-software/mac-antivirus-3672182/).

Możesz również zmniejszyć ryzyko złośliwego oprogramowania przy użyciu oprogramowania tylko z wiarygodnych źródeł. Ustawienia w obszarze Preferencje ochrony prywatności & zabezpieczeń umożliwiają określenie źródeł oprogramowania zainstalowanego na komputerze Mac. Aby uzyskać więcej informacji, zobacz [ochrona komputera Mac przed złośliwym oprogramowaniem](https://support.apple.com/kb/PH25087).

### <a name="turn-on-firewall-protection"></a>Włączanie ochrony zapory

Użyj ustawień zapory, aby chronić komputer Mac przed niepożądanym kontaktem zainicjowanym przez inne komputery po nawiązaniu połączenia z Internetem lub siecią. Bez tej ochrony komputer Mac może być bardziej narażony na nieautoryzowany dostęp. Aby uzyskać instrukcje [, zobacz temat zapory aplikacji](https://support.apple.com/HT201642) .

## <a name="next-mission"></a>Następna misja

Dobra, misja zakończona! Teraz pracujemy nad [zabezpieczeniem systemu poczty e-mail](m365bp-protect-email-overview.md) przed wyłudzaniem informacji i innymi atakami.