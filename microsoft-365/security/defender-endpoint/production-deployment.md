---
title: Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender sieci
description: Dowiedz się, jak skonfigurować wdrożenie pakietu Ochrona punktu końcowego w usłudze Microsoft Defender
keywords: wdrażanie, konfiguracja, sprawdzanie poprawności licencjonowania, konfiguracja dzierżawy, konfiguracja sieci
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
ms.openlocfilehash: e1fbfdaa71cc57a7797a2b95c96a56abba4fcc40
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2022
ms.locfileid: "64506994"
---
# <a name="set-up-microsoft-defender-for-endpoint-deployment"></a>Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender sieci

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Wdrażanie usługi Defender dla punktu końcowego jest procesem trzyfazowym:

|[![faza wdrażania — przygotowywanie.](images/phase-diagrams/prepare.png#lightbox)](prepare-deployment.md)<br>[Etap 1. Przygotowywanie](prepare-deployment.md) | ![Faza wdrażania — konfiguracja](images/phase-diagrams/setup.png#lightbox)<br>Etap 2. Konfigurowanie | [![Faza wdrażania — wdrożenie](images/phase-diagrams/onboard.png#lightbox)](onboarding.md)<br>[Etap 3. Wniesienie](onboarding.md)|
|---|---|---|
||*Jesteś tutaj!*||

Jesteś obecnie w fazie projektowania.

W tym scenariuszu wdrażania zostaną Ci opisane następujące kroki:

- Sprawdzanie poprawności licencji
- Konfiguracja dzierżawy
- Konfiguracja sieci

> [!NOTE]
> W celu prowadzenia Cię przez typowe wdrożenie ten scenariusz obejmie tylko wykorzystanie Microsoft Endpoint Configuration Manager. Program Defender for Endpoint obsługuje korzystanie z innych narzędzi wdrażania, ale nie obejmuje tych scenariuszy w przewodniku wdrażania. Aby uzyskać więcej informacji, zobacz [Na urządzeniach](onboard-configure.md) Ochrona punktu końcowego w usłudze Microsoft Defender.

## <a name="check-license-state"></a>Sprawdź stan licencji

Sprawdzanie stanu licencji i jego poprawnej obsługi administracyjnej jest możliwe za pośrednictwem centrum administracyjnego lub portalu **Microsoft Azure administracyjnego**.

1. Aby wyświetlić licencje, przejdź do portalu **Microsoft Azure i** przejdź do sekcji Microsoft Azure [licencji portalu](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products) internetowego.

   :::image type="content" source="images/atp-licensing-azure-portal.png" alt-text="Strona Licencjonowanie platformy Azure" lightbox="images/atp-licensing-azure-portal.png":::

1. Ewentualnie w centrum administracyjnym przejdź do pozycji **Subskrypcje** **rozliczeniowe**\>.

    Na ekranie zobaczysz wszystkie licencje z inicjowaniem obsługi administracyjnej i ich bieżący **stan**.

    :::image type="content" source="images/atp-billing-subscriptions.png" alt-text="Strona licencji rozliczeniowych" lightbox="images/atp-billing-subscriptions.png":::

## <a name="cloud-service-provider-validation"></a>Sprawdzanie poprawności dostawcy usług w chmurze

Aby uzyskać dostęp do licencji, dla których jest zapewniana inicjowanie obsługi administracyjnej Twojej firmy, oraz sprawdzić stan licencji, przejdź do centrum administracyjnego.

1. W portalu **partnerów** wybierz pozycję **Administruj usługami > Office 365**.

2. Kliknięcie linku **Portalu partnerskiego** spowoduje otwarcie opcji **Administrator w** imieniu użytkownika i zapewni Ci dostęp do centrum administracyjnego klientów.

   :::image type="content" source="images/atp-O365-admin-portal-customer.png" alt-text="Portalu Office 365 administracyjnego" lightbox="images/atp-O365-admin-portal-customer.png":::

## <a name="tenant-configuration"></a>Konfiguracja dzierżawy

Dołączanie do Ochrona punktu końcowego w usłudze Microsoft Defender jest łatwe. Z menu nawigacji wybierz dowolny element w sekcji Punkty końcowe lub dowolną Microsoft 365 Defender, taką jak Zdarzenia, Myśli, Centrum akcji lub Analiza zagrożeń, aby zainicjować proces dołączania.

Z przeglądarki internetowej przejdź do portalu <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender sieci Web</a>.

## <a name="data-center-location"></a>Lokalizacja centrum danych
Ochrona punktu końcowego w usłudze Microsoft Defender będą przechowywane i przetwarzane w tej [samej lokalizacji co używane przez firmę Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable). Jeśli Microsoft 365 Defender nie zostało jeszcze włączone, włączenie dołączania do usługi Ochrona punktu końcowego w usłudze Microsoft Defender spowoduje również włączenie Microsoft 365 Defender i automatyczne wybrana nowa lokalizacja centrum danych na podstawie lokalizacji aktywnego użytkownika Microsoft 365 zabezpieczeń. Wybrana lokalizacja centrum danych zostanie pokazana na ekranie.

## <a name="network-configuration"></a>Konfiguracja sieci

Jeśli organizacja nie wymaga, aby punkty końcowe korzystały z serwera proxy w celu uzyskania dostępu do Internetu, pomiń tę sekcję.

Czujnik Ochrona punktu końcowego w usłudze Microsoft Defender wymaga od firmy Microsoft Windows HTTP (WinHTTP) zgłaszania danych czujnika i komunikowania się z Ochrona punktu końcowego w usłudze Microsoft Defender serwisem. Osadzony Ochrona punktu końcowego w usłudze Microsoft Defender działa w kontekście systemowym przy użyciu konta LocalSystem. Czujnik używa usług Microsoft Windows HTTP (WinHTTP) w celu umożliwienia komunikacji z usługą Ochrona punktu końcowego w usłudze Microsoft Defender w chmurze. Ustawienie konfiguracji WinHTTP jest niezależne od ustawień serwera Windows proxy przeglądania Internetu (WinINet) i może wykrywać tylko serwer proxy przy użyciu następujących metod odnajdowania:

- **Metody wykrywania automatycznego**:
  - Przezroczysty serwer proxy
  - Protokół automatycznego wykrywania proxy sieci Web (WPAD)

  Jeśli w topologii sieci wdrożono przezroczysty serwer proxy lub tablet WPAD, nie ma potrzeby żadnych specjalnych ustawień konfiguracji. Aby uzyskać więcej informacji na temat Ochrona punktu końcowego w usłudze Microsoft Defender URL wykluczeń adresów URL w serwerze [](production-deployment.md#proxy-service-urls) proxy, zobacz sekcję Adresy URL usługi proxy w tym dokumencie, aby uzyskać listę adresów URL ze zezwalaniami lub na temat Konfigurowania ustawień serwera proxy i łączności [internetowej urządzenia](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

- **Ręczna statyczna konfiguracja serwera proxy**:
  - Konfiguracja oparta na rejestrze
  - WinHTTP configured using netsh command

    Ta możliwość jest przeznaczona tylko dla komputerów stacjonarnych w stabilnej topologii (na przykład: komputer stacjonarny w sieci firmowej za tym samym serwerem proxy).

### <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>Ręczne konfigurowanie serwera proxy przy użyciu statycznego serwera proxy opartego na rejestrze

Skonfiguruj statyczny serwer proxy oparty na rejestrze, aby umożliwić tylko czujnikowi Ochrona punktu końcowego w usłudze Microsoft Defender zgłaszanie danych diagnostycznych i komunikowanie się z usługami firmy Ochrona punktu końcowego w usłudze Microsoft Defender, jeśli komputer nie jest dozwolony do łączenia się z Internet. Statyczny serwer proxy można skonfigurować za pośrednictwem zasady grupy (GP). Zasady grupy można znaleźć w obszarze:

- Szablony administracyjne Windows \> kompilacji zbierania \> \> i podglądu danych składników Konfiguruj uwierzytelniony serwer proxy dla usługi połączonego interfejsu użytkownika i telemetrii
- Ustaw dla ustawienia **Włączone i** wybierz **pozycję Wyłącz uwierzytelniony serwer proxy**

1. Otwórz Konsolę zarządzania zasadami grupy.
2. Utwórz zasady lub edytuj istniejące zasady zgodnie z praktykami organizacyjnymi.
3. Edytuj zasady grupy i przejdź do szablonu administracyjnego **Windows kompilacji \> \> zbierania danych składników i podglądu Konfiguruj uwierzytelnione użycie serwera proxy dla usługi połączonego użytkownika i telemetrii.\>**

   :::image type="content" source="images/atp-gpo-proxy1.png" alt-text="Opcje związane z konfiguracją zasad użytkowania" lightbox="images/atp-gpo-proxy1.png":::

4. Wybierz **pozycję Włączone**.
5. Wybierz **pozycję Wyłącz uwierzytelniony serwer proxy**.
6. Przejdź do **szablonu administracyjnego Windows \> kompilacji zbierania \> \> i podglądu składników Konfiguruj połączone środowisko użytkownika i telemetrię**.

   :::image type="content" source="images/atp-gpo-proxy2.png" alt-text="Opcje związane z konfiguracją połączonego interfejsu użytkownika i telemetrii" lightbox="images/atp-gpo-proxy2.png":::

7. Wybierz **pozycję Włączone**.
8. Wprowadź nazwę **serwera proxy**.

Zasady ustawiają dwie wartości `TelemetryProxyServer` rejestru jako REG_SZ i jako `DisableEnterpriseAuthProxy` REG_DWORD w ramach klucza rejestru `HKLM\Software\Policies\Microsoft\Windows\DataCollection`.

Wartość rejestru przyjmuje `TelemetryProxyServer` następujący format ciągu:

```text
<server name or ip>:<port>
```

Na przykład: 10.0.0.6:8080

Wartość rejestru powinna `DisableEnterpriseAuthProxy` być ustawiona na 1.

### <a name="configure-the-proxy-server-manually-using-netsh-command"></a>Ręczne konfigurowanie serwera proxy przy użyciu polecenia netsh

Za pomocą metody netsh skonfiguruj statyczny serwer proxy dla całego systemu.

> [!NOTE]
>
> - Dotyczy to wszystkich aplikacji, w tym usług Windows, które korzystają z winHTTP z domyślnym serwerem proxy.
> - Komputery przenośne, które zmieniają topologię (na przykład z biura do domu) zostaną niepoprawnie niepoprawne przy użyciu oprogramowania Netsh. Użyj statycznej konfiguracji serwera proxy opartej na rejestrze.

1. Otwieranie wiersza polecenia z podwyższonym poziomem uprawnień:
    1. Przejdź do **przycisku Start** i wpisz **cmd**.
    1. Kliknij prawym przyciskiem myszy **pozycję Wiersz polecenia i** wybierz **pozycję Uruchom jako administrator**.

2. Wprowadź następujące polecenie i naciśnij klawisz **Enter**:

   ```PowerShell
   netsh winhttp set proxy <proxy>:<port>
   ```

   Na przykład: netsh winhttp set proxy 10.0.0.6:8080

### <a name="proxy-configuration-for-down-level-devices"></a>Konfiguracja serwera proxy dla urządzeń  down-level

Down-Level to stacje robocze Windows 7 z dodatkiem SP1 i Windows 8.1, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 oraz wersje Windows Server 2016 wcześniejszych niż Windows  Server CB 1803. W tych systemach operacyjnych serwer proxy zostanie skonfigurowany jako część agenta zarządzania firmy Microsoft do obsługi komunikacji z punktu końcowego do platformy Azure. Aby uzyskać informacje na temat konfiguracji serwera proxy na tych urządzeniach, zobacz Przewodnik po szybkim wdrażaniu agenta zarządzania firmy Microsoft.

### <a name="proxy-service-urls"></a>Adresy URL usługi serwera proxy

Adresy URL, które zawierają wersję 20, są potrzebne tylko w przypadku, Windows 10, wersji 1803 lub Windows 11 urządzeniach. Jest ona potrzebna tylko wtedy, `us-v20.events.data.microsoft.com` gdy urządzenie jest Windows 10 wersji 1803 lub Windows 11.

Jeśli serwer proxy lub zapora blokuje ruch anonimowy, ponieważ czujnik Ochrona punktu końcowego w usłudze Microsoft Defender łączy się z kontekstu systemowego, upewnij się, że ruch anonimowy jest dozwolony w podanych adresach URL.

Poniższy arkusz kalkulacyjny zawiera listę usług i skojarzonych z nimi adresów URL, z których sieć musi nawiązać połączenie. Upewnij się, że nie ma żadnych reguł zapory lub filtrowania sieci, które odmówią dostępu do tych adresów URL, lub może być konieczne utworzenie reguły zezwalania *przeznaczonej* specjalnie dla tych adresów URL.

<br>

****


|Arkusz kalkulacyjny listy domen| Opis|
|---|---|
|Ochrona punktu końcowego w usłudze Microsoft Defender adresu URL dla klientów komercyjnych| Arkusz kalkulacyjny z określonymi rekordami DNS dla lokalizacji usług, lokalizacji geograficznych i systemu operacyjnego dla klientów komercyjnych. <p> [Pobierz arkusz kalkulacyjny tutaj.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Ochrona punktu końcowego w usłudze Microsoft Defender url list for Gov/GCC/DoD | Arkusz kalkulacyjny z określonymi rekordami DNS dla lokalizacji usług, lokalizacji geograficznych i systemu operacyjnego dla klientów GCC/DoD. <p> [Pobierz arkusz kalkulacyjny tutaj.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

## <a name="next-step"></a>Następny krok

[![**Etap 3. Wsuń**.](images/onboard.png#lightbox)] <br> [Etap 3. Wsuń](onboarding.md) urządzenia do usługi, aby usługa Ochrona punktu końcowego w usłudze Microsoft Defender uzyskać od nich dane czujnika.
