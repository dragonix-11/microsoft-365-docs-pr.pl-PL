---
title: Włączanie integracji rozwiązania Corelight w Ochrona punktu końcowego w usłudze Microsoft Defender
description: Włącz integrację z rozwiązaniem Corelight, aby uzyskać widoczność skoncentrowaną na urządzeniach IoT/OT w obszarach sieci, w których nie wdrożono rozwiązania MDE
keywords: włączanie łącznika siem, siem, łącznika, informacji o zabezpieczeniach i zdarzeń
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: bf3095b9178b4ff2e71d4ee5f652d9316f233746
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664595"
---
# <a name="enable-corelight-data-integration"></a>Włącz integrację danych Corelight

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Firma Microsoft nawiązała współpracę z [firmą Corelight](https://corelight.com/integrations/iot-security), dostawcą wiodącej w branży platformy do wykrywania i reagowania na otwarte sieci (NDR), aby ułatwić odnajdywanie urządzeń IoT/OT w całej organizacji. Korzystając z danych wysyłanych z urządzeń sieciowych Corelight, Microsoft 365 Defender zyskuje zwiększony wgląd w działania sieciowe urządzeń niezarządzanych, w tym komunikację z innymi urządzeniami niezarządzanymi lub sieciami zewnętrznymi.

Po włączeniu tego źródła danych wszystkie zdarzenia z urządzeń sieciowych Corelight są wysyłane do Microsoft 365 Defender. Te działania można wyświetlić na osi czasu urządzeń niezarządzanych, dostępnej w spisie urządzeń Ochrona punktu końcowego w usłudze Microsoft Defender. Aby uzyskać więcej informacji, zobacz [Odnajdywanie urządzeń](device-discovery.md).

## <a name="enabling-the-corelight-integration"></a>Włączanie integracji z rozwiązaniem Corelight

Aby włączyć integrację z rozwiązaniem Corelight, należy wykonać następujące kroki:

[Krok 1. Włączanie funkcji Corelight jako źródła danych](#step-1-turn-on-corelight-as-a-data-source)<br>
[Krok 2. Nadaj corelight uprawnienia do wysyłania zdarzeń do Microsoft 365 Defender](#step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender)<br>
[Krok 3. Konfigurowanie urządzenia Corelight w celu wysyłania danych do Microsoft 365 Defender](#step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender)

### <a name="step-1-turn-on-corelight-as-a-data-source"></a>Krok 1. Włączanie funkcji Corelight jako źródła danych

1. W okienku nawigacji portalu [https://security.microsoft.com](https://security.microsoft.com/) wybierz pozycję **Ustawienia** \> **Źródła danych** **odnajdywania** \> urządzeń.

   :::image type="content" source="images/enable-corelight.png" alt-text="Strona źródeł danych w portalu Microsoft 365 Defender" lightbox="images/enable-corelight.png":::

2. Wybierz pozycję **Wyślij dane Corelight do M365D** i wybierz pozycję **Zapisz**.

### <a name="step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender"></a>Krok 2. Nadaj corelight uprawnienia do wysyłania zdarzeń do Microsoft 365 Defender

> [!NOTE]
> Aby udzielić corelight uprawnień dostępu do zasobów w organizacji, musisz być administratorem globalnym.

1. Jako administrator globalny dzierżawy przejdź do tego [linku](<https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=d8be544e-9d1a-4825-a5cb-fb447457f692&response_type=code&sso_reload=true>) , aby udzielić uprawnień.
2. Przejdź do [https://security.microsoft.com](https://security.microsoft.com/) portalu, wybierz **pozycję Ustawienia** \> **Microsoft 365 Defender** i zanotuj **identyfikator dzierżawy**. Te informacje będą potrzebne podczas konfigurowania urządzenia Corelight.

### <a name="step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender"></a>Krok 3. Konfigurowanie urządzenia Corelight w celu wysyłania danych do Microsoft 365 Defender

> [!NOTE]
>  Integracja będzie publiczna w oprogramowaniu Corelight Sensor w wersji 24 lub nowszej. 

Aby wyświetlić podgląd w wersji 23 lub 22.1, należy wykonać polecenie `corelight-client configuration update --enable.adfiot 1` , aby włączyć sekcję konfiguracji w graficznym interfejsie użytkownika.

Oprócz tego weryfikacja graficznego interfejsu użytkownika wymaga skonfigurowania brokera w sekcji konfiguracji we wszystkich wersjach 23.  Podany broker jest wymagany, ale w rzeczywistości nie będzie używany. Wprowadź `127.0.0.1:1234` wartość w polu _broker kafka_, aby zapewnić pomyślne sprawdzenie poprawności przed wykonaniem poniższych kroków, aby włączyć wysyłanie danych do Microsoft 365 Defender.

> [!NOTE]
> Aby rozwiązanie działało, potrzebna będzie łączność z Internetem, aby czujnik dotarł zarówno do usług w chmurze Defender, jak i Corelight.

#### <a name="enabling-in-the-corelight-sensor-gui"></a>Włączanie w graficznym interfejsie użytkownika czujnika Corelight

1. W sekcji Konfiguracja interfejsu UŻYTKOWNIKA czujnika Corelight wybierz pozycję **Eksportowanie czujników**\>.
2. Z listy przejdź do pozycji **EKSPORTUJ DO PLATFORMY KAFKA** i wybierz przełącznik, aby go włączyć.

   :::image type="content" source="images/exporttokafka.png" alt-text="Eksportowanie platformy Kafka" lightbox="images/exporttokafka.png":::

3. Następnie włącz pozycję **EKSPORTUJ DO USŁUGI AZURE DEFENDER FOR IOT** i wprowadź identyfikator dzierżawy zanotowany w kroku 1 w polu Identyfikator dzierżawy.

   :::image type="content" source="images/exporttodiot.png" alt-text="Eksportowanie iot" lightbox="images/exporttodiot.png":::

4. Wybierz pozycję **Zastosuj zmiany**.

   :::image type="content" source="images/corelightapply.png" alt-text="Ikona Zastosuj zmiany" lightbox="images/corelightapply.png":::

> [!NOTE]
> Nie należy zmieniać opcji konfiguracji na platformie Kafka (z wyłączeniem wykluczeń dziennika i filtrów). Wszelkie wprowadzone zmiany zostaną zignorowane.

#### <a name="enabling-in-the-corelight-client"></a>Włączanie w kliencie corelight-client

**Eksportowanie do platformy KAFKA** i **eksportowanie do usługi AZURE DEFENDER FOR IOT** można włączyć przy użyciu następującego polecenia w kliencie corelight-client:

`corelight-client configuration update --bro.export.kafka.defender.enable true --bro.export.kafka.defender.tenant\_id <your tenant>`.

> [!IMPORTANT]
> Jeśli już używasz eksportu platformy Kafka, skontaktuj się z pomocą techniczną corelight w celu uzyskania alternatywnej konfiguracji.

Aby skonfigurować wysyłanie tylko minimalnego zestawu dzienników:

1. W graficznym interfejsie użytkownika czujnika Corelight przejdź do sekcji Kafka
2. Przejdź do **dzienników Zeek, aby wykluczyć**
3. Wybierz **pozycję Wszystkie**
4. Następnie wybierz pozycję **x** obok następujących dzienników, aby upewnić się, że nadal będą one przepływać do firmy Microsoft:  
    `dns  conn  files  http  ssl  ssh  x509  snmp  smtp  ftp  sip  dhcp  notice`
5. Wybierz pozycję **Zastosuj zmiany**

Lista dzienników, które przepływa do firmy Microsoft, może się rozwijać z upływem czasu.

## <a name="see-also"></a>Zobacz też

- [Wykrywanie urządzeń — często zadawane pytania](device-discovery-faq.md)
