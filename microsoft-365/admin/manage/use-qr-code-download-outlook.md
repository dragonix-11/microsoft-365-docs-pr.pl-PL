---
title: Używanie kodu QR do logowania się do aplikacji Outlook urządzenia przenośnego
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
description: Dowiedz się, jak używać kodu QR do uwierzytelniania i pobierania Outlook urządzenia przenośnego.
ms.openlocfilehash: 736628fb97cf2a6f4f6c6d175384a30c41bf642d
ms.sourcegitcommit: 7f0c5b55e2966c0c1ce6a153a4e6a7ec035bd818
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2021
ms.locfileid: "63007487"
---
# <a name="use-a-qr-code-to-sign-in-to-the-outlook-mobile-apps"></a>Używanie kodu QR do logowania się do aplikacji Outlook urządzenia przenośnego

Jako administrator Microsoft 365, możesz umożliwić użytkownikom logowanie się do aplikacji Outlook dla systemu Android lub iOS na urządzeniach przenośnych bez konieczności wprowadzania nazwy użytkownika i hasła. Skanując kod QR, użytkownicy mogą bezpiecznie uwierzytelnić się i zalogować do Outlook urządzenia przenośnego.

W Outlook w sieci Web aplikacji klasycznej Outlook lub innych aplikacjach klasycznych użytkownicy mogą zobaczyć powiadomienia z powiadomieniem o tym, że mogą używać aplikacji Outlook na swoim urządzeniu przenośnym. Tymi powiadomieniami może zarządzać administrator, używając programu Exchange PowerShell. Jeśli użytkownicy wybiorą opcję wysłania do siebie wiadomości SMS w celu pobrania aplikacji na swoje urządzenie przenośne, na ich komputerze pojawi się kod QR. Będzie on mógł zeskanować kod QR, aby zalogować Outlook na telefonie lub tablecie. Ten kod QR to krótki token, który można zrealizować tylko raz.

Powiadomienie jest generowane tylko wtedy, gdy są spełnione następujące warunki:

1. Środowisko kodu QR jest włączone dla dzierżawy (to środowisko jest domyślnie włączone).

2. Użytkownik nie używa jeszcze aplikacji Outlook dla systemów iOS i Android.

3. Użytkownik ma pusty stan w okienku odczytu (nie zaznacza opcji automatycznego otwierania pierwszej wiadomości e-mail).

4. Użytkownik nie odrzucił powiadomienia.

> [!NOTE]
> W niektórych przypadkach użytkownicy muszą ponownie uwierzytelnić się na swoim komputerze, aby wygenerować kod QR.

## <a name="use-exchange-powershell"></a>Używanie Exchange PowerShell

Ta funkcja jest domyślnie włączona. Aby wyłączyć tę funkcję, wykonaj poniższe czynności.

1. [Połączenie do Exchange PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
2. Za pomocą programu PowerShell możesz wyłączyć powiadomienia informujące użytkowników o Outlook dla urządzeń przenośnych. Uniemożliwia to również pokazywanie przepływu logowania przy użyciu kodu QR.

```powershell
Set-OrganizationConfig -MobileAppEducationEnabled <Boolean>
```

> [!NOTE]
> W przypadku używania Exchange PowerShell propagowanie zmian może potrwać do 8 godzin.

## <a name="related-content"></a>Zawartość pokrewna

[Konfigurowanie opcji wydania standardowego lub kierowanego](release-options-in-office-365.md) (artykuł)\
[Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) (artykuł)
