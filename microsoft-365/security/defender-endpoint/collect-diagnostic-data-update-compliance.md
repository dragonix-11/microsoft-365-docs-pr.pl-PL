---
title: Zbieranie danych diagnostycznych w celu zachowania zgodności z przepisami i Program antywirusowy Microsoft Defender
description: Narzędzie umożliwia zbieranie danych w celu rozwiązywania problemów z aktualizowaniem zgodności podczas Program antywirusowy Microsoft Defender oceny.
keywords: rozwiązywanie problemów, błąd, poprawka, aktualizacja zgodności, oms, monitor, raport, Microsoft Defender AV
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 9e368f2cb3cecf9359c4aed5e727aef2ee21c02b
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2021
ms.locfileid: "62996767"
---
# <a name="collect-update-compliance-diagnostic-data-for-microsoft-defender-antivirus-assessment"></a>Zbieranie danych diagnostycznych aktualizacji zgodności na Program antywirusowy Microsoft Defender testów


**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

W tym artykule opisano, jak zbierać dane diagnostyczne, które mogą być używane przez zespoły pomocy technicznej i inżynierów firmy Microsoft w celu rozwiązywania problemów, które mogą wystąpić podczas korzystania z sekcji Program antywirusowy Microsoft Defender Assessment (Ocena Program antywirusowy Microsoft Defender) w dodatku Update Compliance.

Przed podjęciem próby tego procesu upewnij się, że wyczyszczysz temat Rozwiązywanie problemów Program antywirusowy Microsoft Defender [raportowania](troubleshoot-reporting.md), czy są spełnione wszystkie wymagania wstępne i czy zostały wykonane wszelkie inne sugerowane kroki rozwiązywania problemów.

Na co najmniej dwóch urządzeniach, które nie zgłaszają lub nie są wyświetlane w zgodności z aktualizacją, uzyskaj plik .cab diagnostycznego, wykonać następujące czynności:

1. Otwórz wersję wiersza polecenia na poziomie administratora w następujący sposób:

    a. Otwieranie menu **Start** .

    b. Wpisz **cmd**. Kliknij prawym przyciskiem myszy pozycję **Wiersz polecenia,** a następnie wybierz **pozycję Uruchom jako administrator**.

    c. Określ poświadczenia administratora lub zatwierdź monit.

2. Przejdź do Windows Defender adresowej. Domyślnie jest to `C:\Program Files\Windows Defender`.

3. Wpisz następujące polecenie, a następnie naciśnij klawisz **Enter**

    ```Dos
    mpcmdrun -getfiles
    ```

4. Zostanie .cab pliku zawierającego różne dzienniki diagnostyczne. Lokalizacja pliku zostanie określona w danych wyjściowych w wierszu polecenia. Domyślna lokalizacja to `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`.

5. Skopiuj te .cab do lokalizacji, do której dostęp ma pomoc techniczna firmy Microsoft. Przykładem może być chroniony hasłem folder OneDrive który możesz nam udostępnić.

6. Wyślij wiadomość e-mail przy użyciu <a href="mailto:ucsupport@microsoft.com?subject=MDAV assessment issue&body=I%20am%20encountering%20the%20following%20issue%20when%20using%20Windows%20Defender%20AV%20in%20Update%20Compliance%3a%20%0d%0aI%20have%20provided%20at%20least%202%20support%20.cab%20files%20at%20the%20following%20location%3a%20%3Caccessible%20share%2c%20including%20access%20details%20such%20as%20password%3E%0d%0aMy%20OMS%20workspace%20ID%20is%3a%20%0d%0aPlease%20contact%20me%20at%3a">szablonu</a> wiadomości e-mail pomocy technicznej dotyczącej aktualizacji i wypełnij szablon następującymi informacjami:

    ```text
    I am encountering the following issue when using Microsoft Defender Antivirus in Update Compliance:

    I have provided at least 2 support .cab files at the following location: <accessible share, including access details such as password>

    My OMS workspace ID is:

    Please contact me at:
    ```

## <a name="see-also"></a>Zobacz też

- [Rozwiązywanie problemów Program antywirusowy Microsoft Defender raportowania błędów](troubleshoot-reporting.md)
