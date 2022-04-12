---
title: Konfigurowanie wdrożenia Ochrona punktu końcowego w usłudze Microsoft Defender
description: Dowiedz się, jak skonfigurować wdrożenie dla Ochrona punktu końcowego w usłudze Microsoft Defender
keywords: wdrażanie, konfigurowanie, walidacja licencjonowania, konfiguracja dzierżawy, konfiguracja sieci
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-scenario
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: bae66223494d8de98737516cef1a2c407d7d1a6a
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783540"
---
# <a name="set-up-microsoft-defender-for-endpoint-deployment"></a>Konfigurowanie wdrożenia Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Wdrażanie usługi Defender dla punktu końcowego jest procesem trójfazowym:

|[![faza wdrażania — przygotowanie.](images/phase-diagrams/prepare.png#lightbox)](prepare-deployment.md)<br>[Faza 1. Przygotowanie](prepare-deployment.md) | ![faza wdrażania — konfiguracja](images/phase-diagrams/setup.png#lightbox)<br>Faza 2. Konfiguracja | [![faza wdrażania — dołączanie](images/phase-diagrams/onboard.png#lightbox)](onboarding.md)<br>[Faza 3. Dołączenie](onboarding.md)|
|---|---|---|
||*Jesteś tutaj!*||

Obecnie jesteś w fazie konfiguracji.

W tym scenariuszu wdrażania przeprowadzisz się przez następujące czynności:

- Walidacja licencjonowania
- Konfiguracja dzierżawy
- Konfiguracja sieci

> [!NOTE]
> W celu prowadzenia cię przez typowe wdrożenie ten scenariusz obejmuje tylko użycie Microsoft Endpoint Configuration Manager. Usługa Defender for Endpoint obsługuje korzystanie z innych narzędzi dołączania, ale nie obejmuje tych scenariuszy w przewodniku wdrażania. Aby uzyskać więcej informacji, zobacz [Dołączanie urządzeń do Ochrona punktu końcowego w usłudze Microsoft Defender](onboard-configure.md).

## <a name="check-license-state"></a>Sprawdzanie stanu licencji

Sprawdzanie stanu licencji i poprawnego aprowizowania można wykonać za pośrednictwem centrum administracyjnego lub portalu **Microsoft Azure**.

1. Aby wyświetlić licencje, przejdź do **portalu Microsoft Azure** i przejdź do [sekcji licencji portalu Microsoft Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products).

   :::image type="content" source="images/atp-licensing-azure-portal.png" alt-text="Strona Licencjonowanie platformy Azure" lightbox="images/atp-licensing-azure-portal.png":::

1. Alternatywnie w centrum administracyjnym przejdź do pozycji **Subskrypcje rozliczeniowe**\>.

    Na ekranie zostaną wyświetlone wszystkie aprowizowane licencje i ich bieżący **stan**.

    :::image type="content" source="images/atp-billing-subscriptions.png" alt-text="Strona licencji rozliczeniowych" lightbox="images/atp-billing-subscriptions.png":::

## <a name="cloud-service-provider-validation"></a>Weryfikacja dostawcy usług w chmurze

Aby uzyskać dostęp do licencji aprowizowanych w firmie i sprawdzić stan licencji, przejdź do centrum administracyjnego.

1. W **portalu partnerskim** wybierz pozycję **Administrowanie usługami > Office 365**.

2. Kliknięcie **linku portalu partnerskiego** spowoduje otwarcie opcji **Administrator w imieniu** i udzielenie dostępu do centrum administracyjnego klienta.

   :::image type="content" source="images/atp-O365-admin-portal-customer.png" alt-text="Portal administracyjny Office 365" lightbox="images/atp-O365-admin-portal-customer.png":::

## <a name="tenant-configuration"></a>Konfiguracja dzierżawy

Dołączanie do Ochrona punktu końcowego w usłudze Microsoft Defender jest łatwe. W menu nawigacji wybierz dowolny element w sekcji Punkty końcowe lub dowolną funkcję Microsoft 365 Defender, taką jak Zdarzenia, Wyszukiwanie zagrożeń, Centrum akcji lub Analiza zagrożeń, aby zainicjować proces dołączania.

W przeglądarce internetowej przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>.

## <a name="data-center-location"></a>Lokalizacja centrum danych
Ochrona punktu końcowego w usłudze Microsoft Defender będzie przechowywać i przetwarzać dane w [tej samej lokalizacji, co dane używane przez Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable). Jeśli Microsoft 365 Defender nie została jeszcze włączona, dołączanie do Ochrona punktu końcowego w usłudze Microsoft Defender również zostanie włączone Microsoft 365 Defender, a nowa lokalizacja centrum danych zostanie automatycznie wybrana na podstawie lokalizacji aktywnej Microsoft 365 usług zabezpieczeń. Wybrana lokalizacja centrum danych jest wyświetlana na ekranie.

## <a name="network-configuration"></a>Konfiguracja sieci

Jeśli organizacja nie wymaga, aby punkty końcowe korzystały z serwera proxy w celu uzyskania dostępu do Internetu, pomiń tę sekcję.

Czujnik Ochrona punktu końcowego w usłudze Microsoft Defender wymaga protokołu HTTP firmy Microsoft Windows (WinHTTP) do raportowania danych czujnika i komunikowania się z usługą Ochrona punktu końcowego w usłudze Microsoft Defender. Osadzony czujnik Ochrona punktu końcowego w usłudze Microsoft Defender działa w kontekście systemu przy użyciu konta LocalSystem. Czujnik korzysta z usług HTTP (WinHTTP) firmy Microsoft Windows, aby umożliwić komunikację z usługą w chmurze Ochrona punktu końcowego w usłudze Microsoft Defender. Ustawienie konfiguracji WinHTTP jest niezależne od ustawień serwera proxy przeglądania internetu Windows Internet (WinINet) i może odnajdywać serwer proxy tylko przy użyciu następujących metod odnajdywania:

- **Metody wykrywania automatycznego**:
  - Przezroczysty serwer proxy
  - Protokół WPAD (Web Proxy Autodiscovery Protocol)

  Jeśli w topologii sieci zaimplementowano przezroczysty serwer proxy lub WPAD, nie ma potrzeby stosowania specjalnych ustawień konfiguracji. Aby uzyskać więcej informacji na temat wykluczeń adresów URL Ochrona punktu końcowego w usłudze Microsoft Defender na serwerze proxy, zobacz sekcję [Adresy URL usługi serwera proxy](production-deployment.md#proxy-service-urls) w tym dokumencie, aby zapoznać się z listą dozwolonych adresów URL lub [w temacie Konfigurowanie ustawień serwera proxy urządzenia i łączności z Internetem](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

- **Ręczna konfiguracja statycznego serwera proxy**:
  - Konfiguracja oparta na rejestrze
  - Narzędzie WinHTTP skonfigurowane przy użyciu polecenia netsh

    Nadaje się tylko dla komputerów stacjonarnych w stabilnej topologii (na przykład: pulpit w sieci firmowej za tym samym serwerem proxy).

### <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>Ręczne konfigurowanie serwera proxy przy użyciu statycznego serwera proxy opartego na rejestrze

Skonfiguruj statyczny serwer proxy oparty na rejestrze, aby umożliwić tylko czujnikowi Ochrona punktu końcowego w usłudze Microsoft Defender zgłaszanie danych diagnostycznych i komunikowanie się z usługami Ochrona punktu końcowego w usłudze Microsoft Defender, jeśli komputer nie może nawiązać połączenia z serwerem Internet. Statyczny serwer proxy można skonfigurować za pośrednictwem zasady grupy (GP). Zasady grupy można znaleźć w następujących obszarach:

- Szablony \> administracyjne Windows składniki \> Zbieranie danych i kompilacje \> w wersji zapoznawczej Konfiguruj uwierzytelnione użycie serwera proxy dla połączonego środowiska użytkownika i usługi telemetrii
- Ustaw ją na **wartość Włączone** i wybierz pozycję **Wyłącz użycie uwierzytelnionego serwera proxy**

1. Otwórz Konsolę zarządzania zasadami grupy.
2. Utwórz zasady lub edytuj istniejące zasady na podstawie praktyk organizacyjnych.
3. Edytuj zasady grupy i przejdź do pozycji **Szablony \> administracyjne Windows Składniki \> Zbieranie danych i kompilacje \> w wersji zapoznawczej Konfigurowanie uwierzytelnionego użycia serwera proxy dla połączonego środowiska użytkownika i usługi telemetrii**.

   :::image type="content" source="images/atp-gpo-proxy1.png" alt-text="Opcje związane z konfiguracją zasad użycia" lightbox="images/atp-gpo-proxy1.png":::

4. Wybierz pozycję **Włączone**.
5. Wybierz pozycję **Wyłącz użycie uwierzytelnionego serwera proxy**.
6. Przejdź do **obszaru Szablony \> administracyjne Windows Components \> Data Collection and Preview Builds \> Configure connected user experiences and telemetry (Konfigurowanie środowisk połączonych użytkowników i telemetrii**).

   :::image type="content" source="images/atp-gpo-proxy2.png" alt-text="Opcje związane z konfiguracją połączonego środowiska użytkownika i telemetrią" lightbox="images/atp-gpo-proxy2.png":::

7. Wybierz pozycję **Włączone**.
8. Wprowadź **nazwę serwera proxy**.

Zasady ustawiają dwie wartości `TelemetryProxyServer` rejestru jako REG_SZ i `DisableEnterpriseAuthProxy` jako REG_DWORD w kluczu rejestru `HKLM\Software\Policies\Microsoft\Windows\DataCollection`.

Wartość `TelemetryProxyServer` rejestru przyjmuje następujący format ciągu:

```text
<server name or ip>:<port>
```

Na przykład: 10.0.0.6:8080

Wartość `DisableEnterpriseAuthProxy` rejestru powinna być ustawiona na 1.

### <a name="configure-the-proxy-server-manually-using-netsh-command"></a>Ręczne konfigurowanie serwera proxy przy użyciu polecenia netsh

Za pomocą programu netsh skonfiguruj statyczny serwer proxy w całym systemie.

> [!NOTE]
>
> - Będzie to miało wpływ na wszystkie aplikacje, w tym usługi Windows korzystające z usługi WinHTTP z domyślnym serwerem proxy.
> - Laptopy, które zmieniają topologię (na przykład: z biura do domu) będą działać nieprawidłowo z netsh. Użyj konfiguracji statycznego serwera proxy opartego na rejestrze.

1. Otwórz wiersz polecenia z podwyższonym poziomem poziomu:
    1. Przejdź do **pozycji Start** i wpisz **cmd**.
    1. Kliknij prawym **przyciskiem myszy wiersz polecenia** i wybierz pozycję **Uruchom jako administrator**.

2. Wprowadź następujące polecenie i naciśnij **klawisz Enter**:

   ```PowerShell
   netsh winhttp set proxy <proxy>:<port>
   ```

   Na przykład: netsh winhttp set proxy 10.0.0.6:8080

### <a name="proxy-configuration-for-down-level-devices"></a>Konfiguracja serwera proxy dla urządzeń niższego poziomu

Down-Level urządzenia obejmują stacje robocze Windows 7 z dodatkiem SP1 i Windows 8.1, a także Windows Server 2008 R2 oraz inne systemy operacyjne serwera, które zostały dołączone wcześniej przy użyciu Microsoft Monitoring Agent. Te systemy operacyjne będą miały serwer proxy skonfigurowany jako część agenta zarządzania firmy Microsoft do obsługi komunikacji z punktu końcowego do platformy Azure. Aby uzyskać informacje na temat konfigurowania serwera proxy na tych urządzeniach, zapoznaj się z przewodnikiem szybkiego wdrażania agenta zarządzania firmy Microsoft.

### <a name="proxy-service-urls"></a>Adresy URL usługi serwera proxy

Adresy URL, które zawierają w nich wersję 20, są potrzebne tylko wtedy, gdy masz urządzenia Windows 10 w wersji 1803 lub Windows 11. Na przykład jest potrzebne tylko wtedy, `us-v20.events.data.microsoft.com` gdy urządzenie jest w Windows 10, wersji 1803 lub Windows 11.

Jeśli serwer proxy lub zapora blokuje ruch anonimowy, ponieważ Ochrona punktu końcowego w usłudze Microsoft Defender czujnik łączy się z kontekstu systemu, upewnij się, że ruch anonimowy jest dozwolony w wymienionych adresach URL.

Poniższy arkusz kalkulacyjny do pobrania zawiera listę usług i skojarzonych z nimi adresów URL, z którymi sieć musi mieć możliwość nawiązania połączenia. Upewnij się, że nie ma reguł filtrowania zapory ani sieci, które odmawiałyby dostępu do tych adresów URL, lub może być konieczne utworzenie dla nich *reguły zezwalania* .

<br>

****


|Arkusz kalkulacyjny listy domen| Opis|
|---|---|
|lista adresów URL Ochrona punktu końcowego w usłudze Microsoft Defender dla klientów komercyjnych| Arkusz kalkulacyjny z określonymi rekordami DNS dla lokalizacji usług, lokalizacji geograficznych i systemu operacyjnego dla klientów komercyjnych. <p> [Pobierz arkusz kalkulacyjny tutaj.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| lista adresów URL Ochrona punktu końcowego w usłudze Microsoft Defender gov/GCC/doD | Arkusz kalkulacyjny z określonymi rekordami DNS dla lokalizacji usług, lokalizacji geograficznych i systemu operacyjnego dla klientów Gov/GCC/DoD. <p> [Pobierz arkusz kalkulacyjny tutaj.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

## <a name="next-step"></a>Następny krok

[![**Faza 3: dołączanie**.](images/onboard.png#lightbox)] <br> [Faza 3. Dołączanie](onboarding.md): dołączanie urządzeń do usługi, aby usługa Ochrona punktu końcowego w usłudze Microsoft Defender mogła pobierać z nich dane z czujników.
