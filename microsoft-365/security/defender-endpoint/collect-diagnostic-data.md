---
title: Zbieranie danych diagnostycznych Program antywirusowy Microsoft Defender
description: Używanie narzędzia do zbierania danych w celu rozwiązywania problemów z Program antywirusowy Microsoft Defender
keywords: rozwiązywanie problemów, błąd, poprawka, aktualizacja zgodności, oms, monitor, raport, Microsoft Defender av, obiekt zasad grupy, ustawienie, dane diagnostyczne
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 06/29/2020
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 73f07a7346edbaebe7e53cd4e17e29a5e6764073
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2021
ms.locfileid: "62996746"
---
# <a name="collect-microsoft-defender-antivirus-diagnostic-data"></a>Zbieranie Program antywirusowy Microsoft Defender diagnostycznych

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

W tym artykule opisano sposób zbierania danych diagnostycznych, które mogą być używane przez zespoły pomocy technicznej i inżynierów firmy Microsoft w celu rozwiązywania problemów, które mogą wystąpić podczas korzystania z Program antywirusowy Microsoft Defender.

> [!NOTE]
> W ramach procesu badania lub odpowiedzi możesz zebrać pakiet badania z urządzenia. Poniżej opisano, jak to zrobić: [Zbierz pakiet badania z urządzeń](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts#collect-investigation-package-from-devices).

Na co najmniej dwóch urządzeniach, na których występuje ten sam problem, uzyskaj plik .cab diagnostycznego, wykonać następujące czynności:

1. Otwórz wersję wiersza polecenia na poziomie administratora w następujący sposób:

    a. Otwieranie menu **Start** .

    b. Wpisz **cmd**. Kliknij prawym przyciskiem myszy pozycję **Wiersz polecenia,** a następnie wybierz **pozycję Uruchom jako administrator**.

    c. Określ poświadczenia administratora lub zatwierdź monit.

2. Przejdź do katalogu plików Program antywirusowy Microsoft Defender. Domyślnie jest to `C:\Program Files\Windows Defender`.

   > [!NOTE]
   > Jeśli używasz zaktualizowanej wersji platformy [programu Microsoft Defender ochrony przed złośliwym](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform) kodem, uruchom program `MpCmdRun` z następującej lokalizacji: `C:\ProgramData\Microsoft\Windows Defender\Platform\<version>`.

3. Wpisz następujące polecenie, a następnie naciśnij klawisz **Enter**

    ```Dos
    mpcmdrun.exe -GetFiles
    ```

4. Zostanie .cab pliku zawierającego różne dzienniki diagnostyczne. Lokalizacja pliku zostanie określona w danych wyjściowych w wierszu polecenia. Domyślna lokalizacja to `C:\ProgramData\Microsoft\Microsoft Defender\Support\MpSupportFiles.cab`.

   > [!NOTE]
   > Aby przekierować plik cab do innej ścieżki lub udziału UNC, użyj następującego polecenia:
   >
   > `mpcmdrun.exe -GetFiles -SupportLogLocation <path>`
   >
   > Aby uzyskać więcej informacji, zobacz [Przekierowywanie danych diagnostycznych do udziału UNC](#redirect-diagnostic-data-to-a-unc-share).

5. Skopiuj te .cab do lokalizacji, do której dostęp ma pomoc techniczna firmy Microsoft. Przykładem może być chroniony hasłem folder OneDrive który możesz nam udostępnić.

> [!NOTE]
> Jeśli masz problem z aktualizowaniem zgodności, wyślij wiadomość e-mail przy użyciu szablonu wiadomości e-mail pomocy technicznej dotyczącej aktualizacji <a href="mailto:ucsupport@microsoft.com?subject=WDAV assessment issue&body=I%20am%20encountering%20the%20following%20issue%20when%20using%20Windows%20Defender%20AV%20in%20Update%20Compliance%3a%20%0d%0aI%20have%20provided%20at%20least%202%20support%20.cab%20files%20at%20the%20following%20location%3a%20%3Caccessible%20share%2c%20including%20access%20details%20such%20as%20password%3E%0d%0aMy%20OMS%20workspace%20ID%20is%3a%20%0d%0aPlease%20contact%20me%20at%3a">zgodności i wypełnij</a> szablon następującymi informacjami:
>
> Podczas korzystania z funkcji zgodności z Program antywirusowy Microsoft Defender występuje następujący problem:
>
> Mam co najmniej 2 pliki .cab w następującej lokalizacji:
>
> \<accessible share, including access details such as password\>
>
> Identyfikator mojego obszaru roboczego programu OMS to:
>
> Skontaktuj się ze mną pod adres:

## <a name="redirect-diagnostic-data-to-a-unc-share"></a>Przekierowywanie danych diagnostycznych do udziału UNC

Aby zebrać dane diagnostyczne w repozytorium centralnym, możesz określić parametr SupportLogLocation.

```Dos
mpcmdrun.exe -GetFiles -SupportLogLocation <path>
```

Kopiuje dane diagnostyczne do określonej ścieżki. Jeśli ścieżka nie zostanie określona, dane diagnostyczne zostaną skopiowane do lokalizacji określonej w konfiguracji lokalizacji dziennika pomocy technicznej.

W przypadku parametru SupportLogLocation w ścieżce docelowej zostanie utworzona następująca struktura folderów:

```Dos
<path>\<MMDD>\MpSupport-<hostname>-<HHMM>.cab
```

<br>

****

|pole|Opis|
|---|---|
|ścieżka|Ścieżka określona w wierszu polecenia lub pobrana z konfiguracji|
|MMDD|Miesiąc i dzień, w którym zbierano dane diagnostyczne (na przykład 0530)|
|nazwa hosta|Nazwa hosta urządzenia, na którym zostały zebrane dane diagnostyczne|
|HHMM|Godziny i minuty, w których zbierano dane diagnostyczne (na przykład 1422)|
|

> [!NOTE]
> Podczas korzystania z udziału plików upewnij się, że konto użyte do zbierania pakietu diagnostycznego ma dostęp do zapisu tego udziału.

## <a name="specify-location-where-diagnostic-data-is-created"></a>Określanie lokalizacji, w której są tworzone dane diagnostyczne

Możesz także określić miejsce, w którym plik .cab ma zostać utworzony przy użyciu obiektu zasady grupy danych (GPO).

1. Otwórz Edytor zasady grupy sieci lokalnej i znajdź dla tego edytora GPO SupportLogLocation w lokalizacji: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\SupportLogLocation`.

2. Wybierz **pozycję Definiuj ścieżkę katalogu, aby skopiować pliki dziennika pomocy technicznej**.

   ![Zrzut ekranu przedstawiający edytor lokalnych zasad grupy](images/GPO1-SupportLogLocationDefender.png)

   ![Zrzut ekranu przedstawiający ustawienie Definiowanie ścieżki dla plików dziennika](images/GPO2-SupportLogLocationGPPage.png)

    ![Zrzut ekranu przedstawiający edytor lokalnych zasad grupy.](images/GPO1-SupportLogLocationDefender.png)  
        
     ![Zrzut ekranu przedstawiający ustawienie definiowania ścieżki dla plików dziennika.](images/GPO2-SupportLogLocationGPPage.png)  
3. W Edytorze zasad wybierz pozycję **Włączone**.

4. Określ ścieżkę katalogu, do której chcesz skopiować pliki dziennika pomocy technicznej, w **polu** Opcje.
     ![Zrzut ekranu przedstawiający ustawienie niestandardowe Włączone ścieżki katalogu.](images/GPO3-SupportLogLocationGPPageEnabledExample.png) 
5. Wybierz **przycisk OK** lub **Zastosuj**.

## <a name="see-also"></a>Zobacz też

- [Rozwiązywanie problemów Program antywirusowy Microsoft Defender raportowania błędów](troubleshoot-reporting.md)
