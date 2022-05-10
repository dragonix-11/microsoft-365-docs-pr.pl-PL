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
ms.openlocfilehash: a3d7548dc71c3a9d588d2a77fae5c4ed71f139f4
ms.sourcegitcommit: 4cd8be7c22d29100478dce225dce3bcdce52644d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2022
ms.locfileid: "65302322"
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
> Integracja jest dostępna w oprogramowaniu Corelight Sensor w wersji 24 lub nowszej.
> 
> Aby rozwiązanie działało, potrzebna będzie łączność z Internetem, aby czujnik dotarł zarówno do usług w chmurze Defender, jak i Corelight.

#### <a name="enable-the-integration-in-the-corelight-web-interface"></a>Włączanie integracji w interfejsie internetowym Corelight

1. W interfejsie internetowym Corelight przejdź do pozycji **Eksportowanie czujników**\>.

   :::image type="content" source="images/exporttodefender.png" alt-text="Eksportowanie platformy Kafka" lightbox="images/exporttodefender.png":::

2. Włącz **opcję Eksportuj do usługi Microsoft Defender**.
3. Wprowadź identyfikator dzierżawy usługi Microsoft 356 Defender.
4. Opcjonalnie możesz:
    - ustaw opcję **Dzienniki zeek na Wyklucz**. Minimalny zestaw dzienników, które należy uwzględnić, to: dns, conn, files, http, ssl, ssh, x509, snmp, smtp, ftp, sip, dhcp i notice.
    - wybierz opcję utworzenia **filtru dziennika usługi Microsoft Defender**.
5. Wybierz pozycję **Zastosuj zmiany**.

#### <a name="enable-the-integration-in-the-corelight-client"></a>Włączanie integracji w kliencie corelight-client

1. Włącz **opcję Eksportuj do usługi Microsoft Defender** przy użyciu następującego polecenia w kliencie corelight-client:

    ``` command
    corelight-client configuration update \
    --bro.export.defender.enable True
    ```

2. Ustawianie identyfikatora dzierżawy

3. Opcjonalnie możesz użyć następującego polecenia, aby wykluczyć niektóre dzienniki lub utworzyć filtr dziennika usługi Microsoft Defender. Minimalny zestaw dzienników, które należy uwzględnić, to: dns, conn, files, http, ssl, ssh, x509, snmp, smtp, ftp, sip, dhcp i notice.

   ``` command
     corelight-client configuration update \
    --bro.export.defender.exclude=<logs_to_exclude> \
    --bro.export.defender.filter=<logs_to_filter>
   ```

## <a name="see-also"></a>Zobacz też

- [Wykrywanie urządzeń — często zadawane pytania](device-discovery-faq.md)