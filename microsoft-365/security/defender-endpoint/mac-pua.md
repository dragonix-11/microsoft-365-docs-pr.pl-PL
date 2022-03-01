---
title: Wykrywanie i blokowanie potencjalnie niechcianych aplikacji za pomocą programu Microsoft Defender for Endpoint na komputerze Mac
description: Wykrywaj i blokuj potencjalnie niechciane aplikacje przy użyciu programu Microsoft Defender for Endpoint w systemie macOS.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, pua, pus
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: a0fb8e19dd573da67936892c81cd515b463a7cba
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011345"
---
# <a name="detect-and-block-potentially-unwanted-applications-with-microsoft-defender-for-endpoint-on-macos"></a>Wykrywanie i blokowanie potencjalnie niechcianych aplikacji za pomocą programu Microsoft Defender for Endpoint w systemie macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Potencjalnie niechciana funkcja ochrony aplikacji (PUA) w programie Microsoft Defender for Endpoint w systemie macOS może wykrywać i blokować pliki funkcji PUA w punktach końcowych w Twojej sieci.

Te aplikacje nie są traktowane jako wirusy, złośliwe oprogramowanie ani inne rodzaje zagrożeń, ale mogą wykonywać akcje dotyczące punktów końcowych, które negatywnie wpływają na ich wydajność lub sposób użycia. Może też odwoływać się do aplikacji, które są uznawane za o złej reputacji.

Te aplikacje mogą zwiększyć ryzyko zainfekowania sieci złośliwym oprogramowaniem, utrudnić identyfikację złośliwego oprogramowania i zmarnować zasoby it w oczyszczaniu aplikacji.

## <a name="how-it-works"></a>Jak to działa

Program Microsoft Defender for Endpoint w systemie macOS może wykrywać i zgłaszać pliki PUA. Po skonfigurowaniu w trybie blokowania pliki pua są przenoszone do kwarantanny.

Po wykryciu aktualizacji PUA w punkcie końcowym program Microsoft Defender for Endpoint w systemie macOS powiadomi użytkownika, chyba że wyłączono powiadomienia. Nazwa zagrożenia będzie zawierać wyraz "Aplikacja".

## <a name="configure-pua-protection"></a>Konfigurowanie ochrony przed pua

Ochronę za pomocą oprogramowania PUA w programie Microsoft Defender for Endpoint w systemie macOS można skonfigurować w jeden z następujących sposobów:

- **Wyłączone**: Ochrona pua jest wyłączona.
- **Inspekcja**: Pliki PUA są raporty w dziennikach produktów, ale nie są Microsoft 365 Defender portalu. Użytkownikowi nie zostanie żadne powiadomienie, a produkt nie zostanie wykonane żadne działanie.
- **Blokuj**: Pliki PUA są zgłaszane w dziennikach produktów i w Microsoft 365 Defender produktu. Użytkownik otrzyma powiadomienie i zostanie wykonane działanie przez produkt.

> [!WARNING]
> Domyślnie ochrona za pomocą zabezpieczeń po stronie użytkownika jest skonfigurowana w **trybie** inspekcji.

Obsługę plików PUA można skonfigurować z wiersza polecenia lub z konsoli zarządzania.

### <a name="use-the-command-line-tool-to-configure-pua-protection"></a>Za pomocą narzędzia wiersza polecenia skonfiguruj ochronę za pomocą funkcji pua:

W programie Terminal wykonaj następujące polecenie, aby skonfigurować ochronę przed pua:

```bash
mdatp threat policy set --type potentially_unwanted_application --action [off|audit|block]
```

### <a name="use-the-management-console-to-configure-pua-protection"></a>Skonfiguruj ochronę za pomocą konsoli zarządzania:

W przedsiębiorstwie możesz skonfigurować ochronę przed kodem PUA z konsoli zarządzania, takiej jak usługa JAMF lub Intune, podobnie jak w przypadku innych ustawień produktu. Aby uzyskać więcej informacji, zobacz [sekcję Ustawienia typu zagrożeń](mac-preferences.md#threat-type-settings) w temacie Ustawianie preferencji programu [Microsoft Defender dla punktu końcowego w systemie macOS](mac-preferences.md) .

## <a name="related-topics"></a>Tematy pokrewne

- [Ustawianie preferencji programu Microsoft Defender dla punktu końcowego w systemie macOS](mac-preferences.md)
