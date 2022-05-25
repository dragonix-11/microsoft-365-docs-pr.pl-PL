---
title: Wykrywanie i blokowanie potencjalnie niechcianych aplikacji za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux
description: Wykrywanie i blokowanie potencjalnie niechcianych aplikacji (PUA) przy użyciu Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, linux, pua, pus
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
ms.openlocfilehash: 004a9d7af09e8a2abb656c29db558d797173edcd
ms.sourcegitcommit: 612ce4d15d8a2fdbf7795393b50af477d81b6139
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65663607"
---
# <a name="detect-and-block-potentially-unwanted-applications-with-microsoft-defender-for-endpoint-on-linux"></a>Wykrywanie i blokowanie potencjalnie niechcianych aplikacji za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Funkcja ochrony potencjalnie niechcianej aplikacji (PUA) w usłudze Defender for Endpoint w systemie Linux może wykrywać i blokować pliki PUA w punktach końcowych w sieci.

Te aplikacje nie są uważane za wirusy, złośliwe oprogramowanie ani inne typy zagrożeń, ale mogą wykonywać akcje w punktach końcowych, które niekorzystnie wpływają na ich wydajność lub użycie. Usługa PUA może również odwoływać się do aplikacji, które są uważane za mające słabą reputację.

Te aplikacje mogą zwiększyć ryzyko zainfekowania sieci złośliwym oprogramowaniem, spowodować, że infekcje złośliwego oprogramowania będą trudniejsze do zidentyfikowania i mogą marnować zasoby IT podczas czyszczenia aplikacji.

## <a name="how-it-works"></a>Jak to działa

Usługa Defender for Endpoint w systemie Linux może wykrywać i zgłaszać pliki PUA. Po skonfigurowaniu w trybie blokowania pliki PUA są przenoszone do kwarantanny.

Po wykryciu pua w punkcie końcowym, defender dla punktu końcowego w systemie Linux przechowuje zapis infekcji w historii zagrożeń. Historię można zwizualizować z portalu Microsoft 365 Defender lub za pomocą narzędzia wiersza `mdatp` polecenia. Nazwa zagrożenia będzie zawierać słowo "Aplikacja".

## <a name="configure-pua-protection"></a>Konfigurowanie ochrony pua

Ochronę pua w usłudze Defender for Endpoint w systemie Linux można skonfigurować na jeden z następujących sposobów:

- **Wyłączone**: ochrona pua jest wyłączona.
- **Inspekcja**: pliki PUA są zgłaszane w dziennikach produktów, ale nie w Microsoft 365 Defender. Żaden zapis zakażenia nie jest przechowywany w historii zagrożeń i produkt nie podejmuje żadnych działań.
- **Blokuj**: pliki PUA są zgłaszane w dziennikach produktów i w Microsoft 365 Defender. Zapis zakażenia jest przechowywany w historii zagrożeń, a produkt podejmuje działania.

> [!WARNING]
> Domyślnie ochrona pua jest skonfigurowana w trybie **inspekcji** .

Sposób obsługi plików PUA można skonfigurować z poziomu wiersza polecenia lub konsoli zarządzania.

### <a name="use-the-command-line-tool-to-configure-pua-protection"></a>Użyj narzędzia wiersza polecenia, aby skonfigurować ochronę pua:

W terminalu wykonaj następujące polecenie, aby skonfigurować ochronę pua:

```bash
mdatp threat policy set --type potentially_unwanted_application --action [off|audit|block]
```

### <a name="use-the-management-console-to-configure-pua-protection"></a>Użyj konsoli zarządzania, aby skonfigurować ochronę pua:

W przedsiębiorstwie można skonfigurować ochronę pua z poziomu konsoli zarządzania, takiej jak Puppet lub Ansible, podobnie jak w przypadku innych ustawień produktu. Aby uzyskać więcej informacji, zobacz sekcję [Ustawienia typu zagrożenia](linux-preferences.md#threat-type-settings) w artykule [Ustawianie preferencji dla usługi Defender dla punktu końcowego w systemie Linux](linux-preferences.md) .

## <a name="related-articles"></a>Powiązane artykuły:

- [Ustawianie preferencji dla usługi Defender dla punktu końcowego w systemie Linux](linux-preferences.md)
