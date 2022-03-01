---
title: Wykrywanie i blokowanie potencjalnie niechcianych aplikacji za pomocą programu Microsoft Defender for Endpoint w systemie Linux
description: Wykrywaj i blokuj potencjalnie niechciane aplikacje przy użyciu programu Microsoft Defender dla punktu końcowego w systemie Linux.
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, pua, pus
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
ms.openlocfilehash: 03c6f64e7272706262ef622a173e58260468e01b
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997308"
---
# <a name="detect-and-block-potentially-unwanted-applications-with-microsoft-defender-for-endpoint-on-linux"></a>Wykrywanie i blokowanie potencjalnie niechcianych aplikacji za pomocą programu Microsoft Defender for Endpoint w systemie Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Potencjalnie niechciana funkcja ochrony aplikacji (PUA) w programie Defender for Endpoint w systemie Linux może wykrywać i blokować pliki funkcji PUA w punktach końcowych w Twojej sieci.

Te aplikacje nie są traktowane jako wirusy, złośliwe oprogramowanie ani inne rodzaje zagrożeń, ale mogą wykonywać akcje dotyczące punktów końcowych, które negatywnie wpływają na ich wydajność lub sposób użycia. Może też odwoływać się do aplikacji, które są uznawane za o złej reputacji.

Te aplikacje mogą zwiększyć ryzyko zainfekowania sieci złośliwym oprogramowaniem, utrudnić identyfikację złośliwego oprogramowania i zmarnować zasoby it w oczyszczaniu aplikacji.

## <a name="how-it-works"></a>Jak to działa

Program Defender for Endpoint w systemie Linux może wykrywać i zgłaszać pliki pua. Po skonfigurowaniu w trybie blokowania pliki pua są przenoszone do kwarantanny.

Po wykryciu oprogramowania PUA w punkcie końcowym program Defender for Endpoint w systemie Linux przechowuje rejestr wirusa wirusa w historii zagrożeń. Historię można zwizualizować z Microsoft 365 Defender portalu lub za pomocą `mdatp` narzędzia wiersza polecenia. Nazwa zagrożenia będzie zawierać wyraz "Aplikacja".

## <a name="configure-pua-protection"></a>Konfigurowanie ochrony przed pua

Ochronę za pomocą zabezpieczeń PUA w programie Defender for Endpoint w systemie Linux można skonfigurować w jeden z następujących sposobów:

- **Wyłączone**: Ochrona pua jest wyłączona.
- **Inspekcja**: Pliki pua są zgłaszane w dziennikach produktów, ale nie są Microsoft 365 Defender. W historii zagrożeń nie jest przechowywana żadna historia zagrożeń, a produkt nie ma żadnych działań.
- **Blokuj**: Pliki PUA są zgłaszane w dziennikach produktów i w Microsoft 365 Defender. W historii zagrożeń jest przechowywana historia zagrożeń, a produkt także jest wyekspowywowany pod jego działaniem.

> [!WARNING]
> Domyślnie ochrona za pomocą zabezpieczeń po stronie użytkownika jest skonfigurowana w **trybie** inspekcji.

Obsługę plików PUA można skonfigurować z wiersza polecenia lub z konsoli zarządzania.

### <a name="use-the-command-line-tool-to-configure-pua-protection"></a>Za pomocą narzędzia wiersza polecenia skonfiguruj ochronę za pomocą funkcji pua:

W programie Terminal wykonaj następujące polecenie, aby skonfigurować ochronę przed pua:

```bash
mdatp threat policy set --type potentially_unwanted_application --action [off|audit|block]
```

### <a name="use-the-management-console-to-configure-pua-protection"></a>Skonfiguruj ochronę za pomocą konsoli zarządzania:

W przedsiębiorstwie można skonfigurować ochronę przed kodem puA z konsoli zarządzania, takiej jak Nasyć lub Ansible, podobnie jak w przypadku innych ustawień produktu. Aby uzyskać więcej informacji, zobacz [sekcję ustawień typu zagrożeń](linux-preferences.md#threat-type-settings) w artykule Ustawianie preferencji programu [Defender dla punktu końcowego w systemie Linux](linux-preferences.md) .

## <a name="related-articles"></a>Artykuły pokrewne

- [Ustawianie preferencji usługi Defender dla punktu końcowego w systemie Linux](linux-preferences.md)
