---
title: Skonfiguruj i zweryfikuj połączenia sieciowe programu antywirusowego Microsoft Defender
description: Skonfiguruj i przetestuj połączenie z usługą Program antywirusowy Microsoft Defender cloud protection.
keywords: antivirus, Program antywirusowy Microsoft Defender, antimalware, security, defender, cloud, aggressiveness, protection level
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
ms.openlocfilehash: 8da099332ffbe2cc3d860faef504e4c5d9663614
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418637"
---
# <a name="configure-and-validate-microsoft-defender-antivirus-network-connections"></a>Skonfiguruj i zweryfikuj połączenia sieciowe programu antywirusowego Microsoft Defender

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Aby upewnić się, Program antywirusowy Microsoft Defender ochrona dostarczana przez chmurę działa prawidłowo, zespół ds. zabezpieczeń musi skonfigurować sieć tak, aby zezwalała na połączenia między punktami końcowymi a niektórymi serwerami firmy Microsoft. Ten artykuł zawiera listę połączeń, które muszą być dozwolone do korzystania z reguł zapory. Zawiera również instrukcje dotyczące weryfikowania połączenia. Prawidłowe skonfigurowanie ochrony gwarantuje, że otrzymasz najlepszą wartość z usług ochrony dostarczanych przez chmurę.

> [!IMPORTANT]
> Ten artykuł zawiera informacje dotyczące konfigurowania połączeń sieciowych tylko dla Program antywirusowy Microsoft Defender. Jeśli używasz Ochrona punktu końcowego w usłudze Microsoft Defender (w tym Program antywirusowy Microsoft Defender), zobacz [Konfigurowanie ustawień serwera proxy urządzenia i łączności internetowej dla usługi Defender for Endpoint](configure-proxy-internet.md).


> [!NOTE]
> Witryna demonstracyjna usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

## <a name="allow-connections-to-the-microsoft-defender-antivirus-cloud-service"></a>Zezwalaj na połączenia z usługą w chmurze Program antywirusowy Microsoft Defender

Usługa Program antywirusowy Microsoft Defender w chmurze zapewnia szybką i silną ochronę punktów końcowych. Włączenie usługi ochrony dostarczanej w chmurze jest opcjonalne. Program antywirusowy Microsoft Defender usługa w chmurze jest zalecana, ponieważ zapewnia ważną ochronę przed złośliwym oprogramowaniem w punktach końcowych i sieci. Aby uzyskać więcej informacji, zobacz [Enable cloud-delivered protection](enable-cloud-protection-microsoft-defender-antivirus.md) for enableing service with Intune, Microsoft Endpoint Configuration Manager, zasady grupy, PowerShell cmdlets, or individual clients in the Zabezpieczenia Windows app (Włączanie ochrony dostarczanej w chmurze na potrzeby włączania usługi za pomocą Intune, Microsoft Endpoint Configuration Manager, zasady grupy, poleceń cmdlet programu PowerShell lub klientów indywidualnych w aplikacji Zabezpieczenia Windows.

Po włączeniu usługi należy skonfigurować sieć lub zaporę, aby zezwalać na połączenia między siecią a punktami końcowymi. Ponieważ ochrona jest usługą w chmurze, komputery muszą mieć dostęp do Internetu i uzyskiwać dostęp do usług firmy Microsoft w chmurze. Nie wykluczaj adresu URL `*.blob.core.windows.net` z jakiejkolwiek inspekcji sieci.

> [!NOTE]
> Usługa Program antywirusowy Microsoft Defender w chmurze zapewnia zaktualizowaną ochronę sieci i punktów końcowych. Usługa w chmurze nie powinna być traktowana jako ochrona tylko plików przechowywanych w chmurze. Zamiast tego usługa w chmurze korzysta z zasobów rozproszonych i uczenia maszynowego, aby zapewnić ochronę punktów końcowych szybciej niż tradycyjne aktualizacje analizy zabezpieczeń.

## <a name="services-and-urls"></a>Usługi i adresy URL

W tabeli w tej sekcji wymieniono usługi i skojarzone z nimi adresy witryny sieci Web (adresy URL).

Upewnij się, że nie ma reguł filtrowania zapory ani sieci, które odmawiają dostępu do tych adresów URL. W przeciwnym razie należy utworzyć regułę zezwalania specjalnie dla tych adresów URL (z wyłączeniem adresu URL `*.blob.core.windows.net`). Adresy URL w poniższej tabeli używają portu 443 do komunikacji.

<br/><br/>

|Usługa i opis|ADRES URL|
|---|---|
|Program antywirusowy Microsoft Defender usługa ochrony dostarczana w chmurze jest określana jako usługa Microsoft Active Protection (MAPS).<p> Program antywirusowy Microsoft Defender korzysta z usługi MAPS w celu zapewnienia ochrony dostarczanej w chmurze.|`*.wdcp.microsoft.com` <p> `*.wdcpalt.microsoft.com` <p> `*.wd.microsoft.com`|
|Microsoft Update Service (MU) i Windows Update Service (WU) <p>Te usługi umożliwią analizę zabezpieczeń i aktualizacje produktów.|`*.update.microsoft.com` <p> `*.delivery.mp.microsoft.com`<p> `*.windowsupdate.com` <p> Aby uzyskać więcej informacji, zobacz [Punkty końcowe połączenia dla Windows Update](/windows/privacy/manage-windows-1709-endpoints#windows-update)|
|Aktualizacje analizy zabezpieczeń Alternatywna lokalizacja pobierania (ADL)<p>Jest to alternatywna lokalizacja dla aktualizacji analizy zabezpieczeń Program antywirusowy Microsoft Defender, jeśli zainstalowana analiza zabezpieczeń jest nieaktualna (co najmniej siedem dni).|`*.download.microsoft.com` <p> `*.download.windowsupdate.com`<p>  `go.microsoft.com`<p> `https://fe3cr.delivery.mp.microsoft.com/ClientWebService/client.asmx`|
|Magazyn przesyłania złośliwego oprogramowania <p>Jest to lokalizacja przekazywania plików przesłanych do firmy Microsoft za pośrednictwem formularza przesyłania lub automatycznego przesyłania przykładów.|`ussus1eastprod.blob.core.windows.net` <p> `ussus2eastprod.blob.core.windows.net` <p> `ussus3eastprod.blob.core.windows.net` <p> `ussus4eastprod.blob.core.windows.net` <p> `wsus1eastprod.blob.core.windows.net` <p> `wsus2eastprod.blob.core.windows.net` <p> `ussus1westprod.blob.core.windows.net` <p> `ussus2westprod.blob.core.windows.net` <p> `ussus3westprod.blob.core.windows.net` <p> `ussus4westprod.blob.core.windows.net` <p> `wsus1westprod.blob.core.windows.net` <p> `wsus2westprod.blob.core.windows.net` <p> `usseu1northprod.blob.core.windows.net` <p> `wseu1northprod.blob.core.windows.net` <p> `usseu1westprod.blob.core.windows.net` <p> `wseu1westprod.blob.core.windows.net` <p> `ussuk1southprod.blob.core.windows.net` <p> `wsuk1southprod.blob.core.windows.net` <p> `ussuk1westprod.blob.core.windows.net` <p> `wsuk1westprod.blob.core.windows.net`|
|Lista odwołania certyfikatów (CRL) <p> Windows używać tej listy podczas tworzenia połączenia SSL z usługą MAPS w celu zaktualizowania listy CRL.|`http://www.microsoft.com/pkiops/crl/` <p> `http://www.microsoft.com/pkiops/certs` <p> `http://crl.microsoft.com/pki/crl/products` <p> `http://www.microsoft.com/pki/certs`|
|Magazyn symboli <p>Program antywirusowy Microsoft Defender użyć magazynu symboli do przywrócenia niektórych plików krytycznych podczas przepływów korygowania.|`https://msdl.microsoft.com/download/symbols`|
|Uniwersalny klient RODO <p> Windows tego klienta do wysyłania danych diagnostycznych klienta. <p> Program antywirusowy Microsoft Defender używa ogólnego rozporządzenia o ochronie danych do celów związanych z jakością produktów i monitorowaniem.|Aktualizacja używa protokołu SSL (port TCP 443) do pobierania manifestów i przekazywania danych diagnostycznych do firmy Microsoft używających następujących punktów końcowych DNS: <p> `vortex-win.data.microsoft.com` <p> `settings-win.data.microsoft.com`|


## <a name="validate-connections-between-your-network-and-the-cloud"></a>Weryfikowanie połączeń między siecią a chmurą

Po dopuszczeniu wymienionych adresów URL sprawdź, czy masz połączenie z usługą w chmurze Program antywirusowy Microsoft Defender. Sprawdź, czy adresy URL prawidłowo zgłaszają i odbierają informacje, aby upewnić się, że jesteś w pełni chroniony.

### <a name="use-the-cmdline-tool-to-validate-cloud-delivered-protection"></a>Weryfikowanie ochrony dostarczanej w chmurze przy użyciu narzędzia cmdline

Użyj następującego argumentu z narzędziem wiersza polecenia Program antywirusowy Microsoft Defender (`mpcmdrun.exe`), aby sprawdzić, czy sieć może komunikować się z usługą w chmurze Program antywirusowy Microsoft Defender:

```console
"%ProgramFiles%\Windows Defender\MpCmdRun.exe" -ValidateMapsConnection
```

> [!NOTE]
> Otwórz wiersz polecenia jako administrator. Kliknij prawym przyciskiem myszy element w menu **Start** , kliknij przycisk **Uruchom jako administrator** i kliknij przycisk **Tak** w wierszu polecenia uprawnień. To polecenie będzie działać tylko w Windows 10, wersji 1703 lub nowszej lub Windows 11.

Aby uzyskać więcej informacji, zobacz [Zarządzanie Program antywirusowy Microsoft Defender za pomocą narzędzia wiersza polecenia mpcmdrun.exe](command-line-arguments-microsoft-defender-antivirus.md).

### <a name="attempt-to-download-a-fake-malware-file-from-microsoft"></a>Próba pobrania fałszywego pliku złośliwego oprogramowania od firmy Microsoft

Możesz pobrać przykładowy plik, który Program antywirusowy Microsoft Defender wykryje i zablokuje połączenie z chmurą. Odwiedź stronę [https://aka.ms/ioavtest](https://aka.ms/ioavtest) , aby pobrać plik.

> [!NOTE]
> Pobrany plik nie jest dokładnie złośliwym oprogramowaniem. Jest to fałszywy plik przeznaczony do testowania, czy masz prawidłowe połączenie z chmurą.

Jeśli masz prawidłowe połączenie, zostanie wyświetlone ostrzeżenie Program antywirusowy Microsoft Defender powiadomienia.

Jeśli używasz Microsoft Edge, zostanie również wyświetlony komunikat z powiadomieniem:

:::image type="content" source="../../media/wdav-bafs-edge.png" alt-text="Powiadomienie o znalezieniu złośliwego oprogramowania w przeglądarce Edge" lightbox="../../media/wdav-bafs-edge.png":::

Podobny komunikat występuje, jeśli używasz programu Internet Explorer:

:::image type="content" source="../../media/wdav-bafs-ie.png" alt-text="Powiadomienie usługi Microsoft Defender AV o znalezieniu złośliwego oprogramowania" lightbox="../../media/wdav-bafs-ie.png":::

#### <a name="view-the-fake-malware-detection-in-your-windows-security-app"></a>Wyświetlanie wykrywania fałszywego złośliwego oprogramowania w aplikacji Zabezpieczenia Windows

1. Na pasku zadań wybierz ikonę Tarcza, otwórz aplikację **Zabezpieczenia Windows**. Możesz też wyszukać pozycję **Rozpocznij** pod kątem *zabezpieczeń*.

2. Wybierz pozycję **Ochrona przed zagrożeniami & wirusami**, a następnie wybierz pozycję **Historia ochrony**.

3. W sekcji **Zagrożenia poddane kwarantannie** wybierz pozycję **Zobacz pełną historię** , aby zobaczyć wykryte fałszywe złośliwe oprogramowanie.

   > [!NOTE]
   > Wersje Windows 10 przed wersją 1703 mają inny interfejs użytkownika. Zobacz [Program antywirusowy Microsoft Defender w aplikacji Zabezpieczenia Windows](microsoft-defender-security-center-antivirus.md).

   W dzienniku zdarzeń Windows zostanie również wyświetlony [identyfikator zdarzenia klienta Windows Defender 1116](troubleshoot-microsoft-defender-antivirus.md).

    > [!TIP]
    > Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
    > - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
    > - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
    > - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
    > - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
    > - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
    > - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
    > - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)


## <a name="see-also"></a>Zobacz też

- [Konfigurowanie ustawień serwera proxy urządzenia i łączności z Internetem dla Ochrona punktu końcowego w usłudze Microsoft Defender](configure-proxy-internet.md)
- [Konfigurowanie Program antywirusowy Microsoft Defender i zarządzanie nimi przy użyciu ustawień zasady grupy](use-group-policy-microsoft-defender-antivirus.md)
- [Ważne zmiany w punkcie końcowym usług Microsoft Active Protection Services](https://techcommunity.microsoft.com/t5/Configuration-Manager-Archive/Important-changes-to-Microsoft-Active-Protection-Service-MAPS/ba-p/274006) 