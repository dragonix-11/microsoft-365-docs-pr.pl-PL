---
title: Włączanie integracji z programem Corelight w Ochrona punktu końcowego w usłudze Microsoft Defender
description: Włącz integrację z programem Corelight, aby uzyskać widoczność informacji skupioną na urządzeniach IoT/OT w obszarach sieci, w których nie wdrożono funkcji MDE
keywords: Enable siem connector, siem, connector, security information and events
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
ms.openlocfilehash: 3a7a4b7ab842baaadb276e60037451e8eb919bf9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465492"
---
# <a name="enable-corelight-data-integration"></a>Włączanie integracji danych z programem Corelight

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Firma Microsoft współpracuje z firmą [Corelight](https://corelight.com/integrations/iot-security), dostawcą wiodącej w branży platformy do wykrywania i reagowania (NDR, Open Network Detection and Response), aby ułatwić odnajdowanie urządzeń IoT/OT w organizacji. Korzystanie z danych wysyłanych z urządzeń sieciowych Corelight zwiększa Microsoft 365 Defender wgląd w działania sieciowe urządzeń niezamanektowych, w tym komunikację z innymi urządzeniami niezakierowymi lub sieciami zewnętrznymi.

Gdy to źródło danych jest włączone, wszystkie zdarzenia z urządzeń sieciowych Corelight są wysyłane do Microsoft 365 Defender. Te działania możesz wyświetlić na osi czasu dla urządzeń nieza zarządzaniem, dostępnej w spisie Ochrona punktu końcowego w usłudze Microsoft Defender urządzeniach. Aby uzyskać więcej informacji, zobacz [Odnajdowanie urządzeń](device-discovery.md).

## <a name="enabling-the-corelight-integration"></a>Włączanie integracji z programem Corelight

Aby włączyć integrację z programem Corelight, musisz wykonać następujące czynności:

[Krok 1. Włączanie doświetlania Corelight jako źródła danych](#step-1-turn-on-corelight-as-a-data-source)<br>
[Krok 2. Nadaj corelight uprawnienia do wysyłania zdarzeń do Microsoft 365 Defender](#step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender)<br>
[Krok 3. Konfigurowanie urządzenia Corelight w celu wysyłania danych do Microsoft 365 Defender](#step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender)

### <a name="step-1-turn-on-corelight-as-a-data-source"></a>Krok 1. Włączanie doświetlania Corelight jako źródła danych

1. W okienku nawigacji w portalu wybierz [https://security.microsoft.com](https://security.microsoft.com/) pozycję Ustawienia  \> **Źródeł danych odnajdowania** \> **urządzeń**.

   :::image type="content" source="images/enable-corelight.png" alt-text="Strona źródeł danych w portalu Microsoft 365 Defender sieci Web" lightbox="images/enable-corelight.png":::

2. Wybierz **pozycję Wyślij dane corelight do M365D** i wybierz pozycję **Zapisz**.

### <a name="step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender"></a>Krok 2. Nadaj corelight uprawnienia do wysyłania zdarzeń do Microsoft 365 Defender

> [!NOTE]
> Musisz być administratorem globalnym, aby udzielić corelight uprawnienia dostępu do zasobów w Twojej organizacji.

1. Aby udzielić uprawnień, jako administrator globalny dzierżawy, przejdź [do tego linku](<https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=d8be544e-9d1a-4825-a5cb-fb447457f692&response_type=code&sso_reload=true>) .
2. Przejdź do [https://security.microsoft.com](https://security.microsoft.com/) portalu, wybierz **Ustawienia** \> **Microsoft 365 Defender** i zanotuj identyfikator **dzierżawy**. Te informacje są potrzebne podczas konfigurowania urządzenia Corelight.

### <a name="step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender"></a>Krok 3. Konfigurowanie urządzenia Corelight w celu wysyłania danych do Microsoft 365 Defender

> [!NOTE]
>  Integracja będzie publiczna w oprogramowaniu Corelight Sensor 24 i nowszych wersjach. 

Aby wyświetlić podgląd w wersji 23 lub 22.1, `corelight-client configuration update --enable.adfiot 1` należy wykonać w celu włączenia sekcji konfiguracji przy identyfikatorze GUID.

Poza tym sprawdzanie poprawności graficznego interfejsu użytkownika wymaga skonfigurowania brokera w sekcji konfiguracji we wszystkich wersjach 23.  Zapewniany przez Ciebie pośrednictwo jest wymagany, ale w rzeczywistości nie będzie używany. Wprowadź `127.0.0.1:1234` dane w _polu kafka brokera_, aby zapewnić pomyślną weryfikację przed rozpoczęciem poniższych czynności, aby umożliwić wysyłanie danych do Microsoft 365 Defender.

> [!NOTE]
> Aby rozwiązanie działało, potrzebujesz łączności z Internetem, aby uzyskać dostęp zarówno do usług Defender, jak i Corelight w chmurze.

#### <a name="enabling-in-the-corelight-sensor-gui"></a>Włączanie w interfejsie UŻYTKOWNIKA czujnika Corelight

1. W sekcji konfiguracji graficznego interfejsu użytkownika czujnika Corelight wybierz pozycję **Eksport czujnika** \> **.**
2. Z listy przejdź do export **to KAFKA** i wybierz przełącznik, aby go włączyć.

   :::image type="content" source="images/exporttokafka.png" alt-text="Kafka export" lightbox="images/exporttokafka.png":::

3. Następnie włącz eksport do usługi **AZURE DEFENDER FOR IOT** i wprowadź identyfikator dzierżawy w kroku 1 w polu Identyfikator DZIERŻAWY.

   :::image type="content" source="images/exporttodiot.png" alt-text="Eksport iot" lightbox="images/exporttodiot.png":::

4. Wybierz **pozycję Apply Changes (Zastosuj zmiany**).

   :::image type="content" source="images/corelightapply.png" alt-text="Ikona Zastosuj zmiany" lightbox="images/corelightapply.png":::

> [!NOTE]
> Opcje konfiguracji w programie Kafka (z wyjątkiem wykluczeń dziennika i filtrów) nie powinny być zmieniane. Wszelkie wprowadzone zmiany zostaną zignorowane.

#### <a name="enabling-in-the-corelight-client"></a>Włączanie w kliencie corelight-client

Możesz włączyć eksportowanie **do witryny KAFKA** i wyeksportować do usługi **AZURE DEFENDER FOR IOT** przy użyciu następującego polecenia w kliencie programu Corelight:

`corelight-client configuration update --bro.export.kafka.defender.enable true --bro.export.kafka.defender.tenant\_id <your tenant>`.

> [!IMPORTANT]
> Jeśli korzystasz już z eksportu programu Kafka, skontaktuj się z pomocą techniczną Corelight, aby uzyskać alternatywną konfigurację.

Aby skonfigurować wysyłanie tylko minimalnej ilości dzienników:

1. W interfejsie GUID czujnika Corelight przejdź do sekcji Kafka
2. Przejdź do **dzienników Zeek, aby wykluczyć**
3. Zaznacz **wszystko**
4. Następnie wybierz **pozycję x** obok następujących dzienników, aby upewnić się, że nadal będą one przepływać do firmy Microsoft:  
    `dns  conn  files  http  ssl  ssh  x509  snmp  smtp  ftp  sip  dhcp  notice`
5. Wybierz **pozycję Apply Changes (Zastosuj zmiany)**

Lista dzienników przepływanych do firmy Microsoft może być z czasem rozszerzana.

## <a name="see-also"></a>Zobacz też

- [Odnajdowanie urządzeń — często zadawane pytania](device-discovery-faq.md)
