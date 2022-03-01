---
title: Konfigurowanie i sprawdzanie poprawności Program antywirusowy Microsoft Defender połączeń sieciowych
description: Skonfiguruj i przetestuj połączenie z Program antywirusowy Microsoft Defender w chmurze.
keywords: oprogramowanie antywirusowe, Program antywirusowy Microsoft Defender, ochrona przed złośliwym kodem, zabezpieczenia, defender, chmura, agresywność, poziom ochrony
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 02/03/2022
ms.reviewer: mkaminska; pahuijbr
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: f29cf5f77acd52a4ff3ccc8384f3c64861e48b64
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019272"
---
# <a name="configure-and-validate-microsoft-defender-antivirus-network-connections"></a>Konfigurowanie i sprawdzanie poprawności Program antywirusowy Microsoft Defender połączeń sieciowych

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Aby zapewnić Program antywirusowy Microsoft Defender zapewnianą przez usługę w chmurze, zespół zabezpieczeń musi skonfigurować sieć tak, aby zezwalała na połączenia między punktami końcowymi a określonymi serwerami firmy Microsoft. W tym artykule wymieniono połączenia, z których można korzystać przy użyciu reguł zapory. Po tej stronie po przedstawiono również instrukcje sprawdzania poprawności połączenia. Poprawne skonfigurowanie ochrony zapewnia najlepszą wartość oferowanych usług ochrony w chmurze.

> [!IMPORTANT]
> Ten artykuł zawiera informacje dotyczące konfigurowania połączeń sieciowych tylko dla Program antywirusowy Microsoft Defender. Jeśli używasz programu Microsoft Defender for Endpoint (który zawiera program Program antywirusowy Microsoft Defender), zobacz Konfigurowanie ustawień serwera proxy urządzenia i łączności internetowej dla [programu Defender dla punktu końcowego](configure-proxy-internet.md).


> [!NOTE]
> Witryna pokazowa usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

## <a name="allow-connections-to-the-microsoft-defender-antivirus-cloud-service"></a>Zezwalaj na połączenia z usługą Program antywirusowy Microsoft Defender chmurze

Usługa Program antywirusowy Microsoft Defender w chmurze zapewnia szybką i silną ochronę dla punktów końcowych. Włączenie usługi ochrony w chmurze jest opcjonalne. Program antywirusowy Microsoft Defender usługi w chmurze, ponieważ zapewnia on ważną ochronę przed złośliwym oprogramowaniem w punktach końcowych i sieci. Aby uzyskać więcej informacji, [](enable-cloud-protection-microsoft-defender-antivirus.md) zobacz Włączanie ochrony w chmurze w celu włączenia usługi za pomocą usługi Intune, Microsoft Endpoint Configuration Manager, zasady grupy, poleceń cmdlet programu PowerShell lub poszczególnych klientów w Zabezpieczenia Windows aplikacji.

Po włączeniu usługi musisz skonfigurować sieć lub zaporę w celu zezwalania na połączenia między siecią a punktami końcowymi. Ponieważ ochrona to usługa w chmurze, komputery muszą mieć dostęp do Internetu i korzystać z usług firmy Microsoft w chmurze. Nie wyklucz adresu URL `*.blob.core.windows.net` podczas jakiejkolwiek inspekcji sieci.

> [!NOTE]
> Usługa Program antywirusowy Microsoft Defender zapewnia zaktualizowaną ochronę sieci i punktów końcowych. Usługa w chmurze nie powinna być uznawana za ochronę tylko dla plików przechowywanych w chmurze. Zamiast tego usługa w chmurze korzysta z zasobów rozłożonych i uczenia maszynowego w celu dostarczania ochrony punktów końcowych w szybszym tempie niż w przypadku tradycyjnych aktualizacji analizy zabezpieczeń.

## <a name="services-and-urls"></a>Usługi i adresy URL

W tabeli w tej sekcji wymieniono usługi i skojarzone z nimi adresy witryn sieci Web (adresy URL).

Upewnij się, że nie ma żadnych reguł zapory ani filtrowania sieci, które odmawiają dostępu do tych adresów URL. W przeciwnym razie należy utworzyć regułę zezwalania specjalnie dla tych adresów URL (z wyjątkiem adresu URL `*.blob.core.windows.net`). Adresy URL w poniższej tabeli używają portu 443 do komunikacji.

<br/><br/>

|Usługa i opis|ADRES URL|
|---|---|
|Program antywirusowy Microsoft Defender dostarczana w chmurze usługa ochrony jest nazywana usługa Microsoft Active Protection (MAPS).<p> Ta Program antywirusowy Microsoft Defender korzysta z usługi MAPY w celu zapewnienia ochrony w chmurze.|`*.wdcp.microsoft.com` <p> `*.wdcpalt.microsoft.com` <p> `*.wd.microsoft.com`|
|Usługa Microsoft Update (MU) i usługa Windows Update Service (WU) <p>Te usługi będą zezwalać na analizę zabezpieczeń i aktualizacje produktów.|`*.update.microsoft.com` <p> `*.delivery.mp.microsoft.com`<p> `*.windowsupdate.com` <p> Aby uzyskać więcej informacji, zobacz [Punkty końcowe połączenia dla usługi Windows.](/windows/privacy/manage-windows-1709-endpoints#windows-update)|
|Aktualizacje analizy zabezpieczeń : alternatywna lokalizacja pobierania (ADL, Security Intelligence)<p>Jest to alternatywna lokalizacja aktualizacji Program antywirusowy Microsoft Defender zabezpieczeń, jeśli zainstalowana inteligencja zabezpieczeń jest aktualny (co najmniej siedem dni wcześniej).|`*.download.microsoft.com` <p> `*.download.windowsupdate.com`<p>  `go.microsoft.com`<p> `https://fe3cr.delivery.mp.microsoft.com/ClientWebService/client.asmx`|
|Magazyn przesyłania złośliwego oprogramowania <p>Jest to lokalizacja przekazywania plików przesyłanych do firmy Microsoft za pośrednictwem formularza Przesyłanie lub automatycznego przesłania przykładu.|`ussus1eastprod.blob.core.windows.net` <p> `ussus2eastprod.blob.core.windows.net` <p> `ussus3eastprod.blob.core.windows.net` <p> `ussus4eastprod.blob.core.windows.net` <p> `wsus1eastprod.blob.core.windows.net` <p> `wsus2eastprod.blob.core.windows.net` <p> `ussus1westprod.blob.core.windows.net` <p> `ussus2westprod.blob.core.windows.net` <p> `ussus3westprod.blob.core.windows.net` <p> `ussus4westprod.blob.core.windows.net` <p> `wsus1westprod.blob.core.windows.net` <p> `wsus2westprod.blob.core.windows.net` <p> `usseu1northprod.blob.core.windows.net` <p> `wseu1northprod.blob.core.windows.net` <p> `usseu1westprod.blob.core.windows.net` <p> `wseu1westprod.blob.core.windows.net` <p> `ussuk1southprod.blob.core.windows.net` <p> `wsuk1southprod.blob.core.windows.net` <p> `ussuk1westprod.blob.core.windows.net` <p> `wsuk1westprod.blob.core.windows.net`|
|Lista odwołań certyfikatów (CRL) <p> Windows użyć tej listy podczas tworzenia połączenia SSL z usługą MAPY w celu zaktualizowania listy CRL.|`http://www.microsoft.com/pkiops/crl/` <p> `http://www.microsoft.com/pkiops/certs` <p> `http://crl.microsoft.com/pki/crl/products` <p> `http://www.microsoft.com/pki/certs`|
|Sklep z symbolami <p>Program antywirusowy Microsoft Defender magazyn symboli, aby przywrócić niektóre krytyczne pliki podczas przepływów rozwiązywania problemów.|`https://msdl.microsoft.com/download/symbols`|
|Klient uniwersalnego RODO <p> Windows tego klienta do wysyłania danych diagnostycznych klienta. <p> Program antywirusowy Microsoft Defender ogólne rozporządzenie o ochronie danych osobowych do celów jakości i monitorowania produktów.|Ta aktualizacja używa protokołu SSL (port TCP 443) do pobierania manifestów i przekazywania danych diagnostycznych do firmy Microsoft, która używa następujących punktów końcowych DNS: <p> `vortex-win.data.microsoft.com` <p> `settings-win.data.microsoft.com`|


## <a name="validate-connections-between-your-network-and-the-cloud"></a>Sprawdzanie poprawności połączeń między siecią a chmurą

Po umożliwieniu dostępu do wymienionych adresów URL sprawdź, czy masz połączenie z usługą Program antywirusowy Microsoft Defender w chmurze. Przetestuj, czy adresy URL są prawidłowo raportowane i odbierane informacje, aby upewnić się, że jesteś w pełni chroniony.

### <a name="use-the-cmdline-tool-to-validate-cloud-delivered-protection"></a>Używanie narzędzia cmdline do sprawdzania poprawności ochrony w chmurze

Użyj następującego argumentu z narzędziem Program antywirusowy Microsoft Defender wiersza polecenia (`mpcmdrun.exe`), aby sprawdzić, czy sieć może komunikować się z usługą Program antywirusowy Microsoft Defender chmurze:

```console
"%ProgramFiles%\Windows Defender\MpCmdRun.exe" -ValidateMapsConnection
```

> [!NOTE]
> Otwórz wiersz polecenia jako administrator. Kliknij prawym przyciskiem myszy element w menu **Start** , kliknij polecenie **Uruchom jako administrator** i kliknij pozycję **Tak w** wierszu uprawnień. To polecenie działa tylko w Windows 10, wersji 1703 lub wyższej albo Windows 11.

Aby uzyskać więcej informacji, zobacz [Zarządzanie Program antywirusowy Microsoft Defender za pomocą mpcmdrun.exe wiersza polecenia](command-line-arguments-microsoft-defender-antivirus.md).

### <a name="attempt-to-download-a-fake-malware-file-from-microsoft"></a>Próba pobrania fałszywego pliku złośliwego oprogramowania od firmy Microsoft

Możesz pobrać przykładowy plik, który Program antywirusowy Microsoft Defender wykryje i zablokuje, jeśli masz poprawne połączenie z chmurą. Odwiedź [https://aka.ms/ioavtest](https://aka.ms/ioavtest) stronę, aby pobrać plik.

> [!NOTE]
> Pobrany plik nie jest dokładnie złośliwym oprogramowaniem. Jest to fałszywy plik przeznaczony do testowania, jeśli masz poprawne połączenie z chmurą.

Jeśli połączenie jest poprawnie podłączone, zostanie wyświetlony komunikat ostrzegawczy z Program antywirusowy Microsoft Defender powiadomienia.

Jeśli korzystasz z Microsoft Edge, zobaczysz również komunikat z powiadomieniem:

:::image type="content" source="../../media/wdav-bafs-edge.png" alt-text="Zrzut ekranu przedstawiający powiadomienie o wykryciu złośliwego oprogramowania w programie Azure IoT Edge.":::

Podobny komunikat występuje w przypadku korzystania z programu Internet Explorer:

:::image type="content" source="../../media/wdav-bafs-ie.png" alt-text="Powiadomienie programu Microsoft Defender AV o wykryciu złośliwego oprogramowania.":::

#### <a name="view-the-fake-malware-detection-in-your-windows-security-app"></a>Wyświetlanie fałszywych wykrywanie złośliwego oprogramowania w Zabezpieczenia Windows aplikacji

1. Na pasku zadań wybierz ikonę Tarcza, **otwórz Zabezpieczenia Windows aplikacji**. Możesz też wyszukać w **polu Start** for *Security (Rozpocznij wyszukiwanie zabezpieczeń*).

2. Wybierz **pozycję Ochrona & zagrożeniami**, a następnie wybierz **pozycję Historia ochrony**.

3. W sekcji **Kwarantanna zagrożeń** wybierz pozycję **Zobacz pełną historię** , aby zobaczyć wykryte fałszywe złośliwe oprogramowanie.

   > [!NOTE]
   > Wersje pakietu Windows 10 wersji 1703 mają inny interfejs użytkownika. Zobacz [Program antywirusowy Microsoft Defender w Zabezpieczenia Windows aplikacji.](microsoft-defender-security-center-antivirus.md)

   W Windows zdarzeń będzie również Windows Defender [identyfikator zdarzenia klienta 1116](troubleshoot-microsoft-defender-antivirus.md).

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie ustawień serwera proxy urządzenia i łączności internetowej dla programu Microsoft Defender dla punktu końcowego](configure-proxy-internet.md)
- [Konfigurowanie zasady grupy zarządzanie plikami Program antywirusowy Microsoft Defender i zarządzanie nimi zasady grupy](use-group-policy-microsoft-defender-antivirus.md)
- [Ważne zmiany w punkcie końcowym usług Microsoft Active Protection Services](https://techcommunity.microsoft.com/t5/Configuration-Manager-Archive/Important-changes-to-Microsoft-Active-Protection-Service-MAPS/ba-p/274006) 