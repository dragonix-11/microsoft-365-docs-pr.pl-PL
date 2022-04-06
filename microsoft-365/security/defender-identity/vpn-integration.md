---
title: Microsoft Defender for Identity vpn w sieci Microsoft 365 Defender
description: Dowiedz się, jak zbierać informacje księgowe przez integrację sieci VPN dla sieci Microsoft Defender for Identity sieci Microsoft 365 Defender
ms.date: 06/07/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: a5c45ecda43b32e37f7309b9a2de33810d60bd15
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469168"
---
# <a name="defender-for-identity-vpn-integration-in-microsoft-365-defender"></a>Integracja sieci VPN z usługą Defender for Identity w Microsoft 365 Defender

**Dotyczy:**

- Microsoft 365 Defender
- Defender for Identity

W tym artykule wyjaśniono, jak zintegrować sieć VPN z [siecią Microsoft Defender for Identity](/defender-for-identity) sieci [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>W ramach schłodowania w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> tożsamości niektóre opcje i szczegóły zmieniły się od ich lokalizacji w portalu usługi Defender dla tożsamości. Zapoznaj się ze szczegółami poniżej, aby dowiedzieć się, gdzie znaleźć zarówno znane, jak i nowe funkcje.

[!INCLUDE [Product long](includes/product-long.md)] mogą zbierać informacje księgowe z rozwiązań VPN. Po skonfigurowaniu strona profilu użytkownika zawiera informacje z połączeń VPN, takie jak adresy IP i lokalizacje, w których pochodzą połączenia. Stanowi to uzupełnienie procesu badania, udostępniając dodatkowe informacje na temat aktywności użytkowników, a także nowe wykrywanie nieprawidłowych połączeń VPN. Połączenie w celu rozpoznania zewnętrznego adresu IP dla lokalizacji jest anonimowe. W ten sposób nie jest wysyłany żaden identyfikator osobisty.

[!INCLUDE [Product short](includes/product-short.md)] Integruje się z rozwiązaniem VPN, słuchając zdarzeń księgowych RADIUS w przód do czujnika [!INCLUDE [Product short](includes/product-short.md)] . Ten mechanizm jest oparty na standardowym programie RADIUS Accounting ([RFC 2866](https://tools.ietf.org/html/rfc2866)) i obsługiwane są następujące dostawcy sieci VPN:

- Microsoft
- F5
- Check Point
- Cisco ASA

## <a name="prerequisites"></a>Wymagania wstępne

Aby włączyć integrację z siecią VPN, ustaw następujące parametry:

- Otwórz port UDP 1813 na czujnikiach [!INCLUDE [Product short](includes/product-short.md)] i/lub autonomicznych [!INCLUDE [Product short](includes/product-short.md)] czujnikiach.

> [!NOTE]
>
> - Po włączeniu **programu Radius Accounting** czujnik włączy wstępnie Windows zasady zapory o nazwie Czujnik, aby umożliwić przychodzącej funkcji RADIUS Accounting [!INCLUDE [Product short](includes/product-short.md)] **[!INCLUDE [Product long](includes/product-long.md)]** w porcie UDP 1813.
> - Integracja sieci VPN nie jest obsługiwana w środowiskach, które przylegają do federalnych standardów przetwarzania informacji (FIPS, Federal Information Processing Standards)

W poniższym przykładzie użyto programu Microsoft Routing and Remote Access Server (RRAS) do opisania procesu konfiguracji sieci VPN.

Jeśli używasz rozwiązania VPN innej firmy, zapoznaj się z ich dokumentacją, aby uzyskać instrukcje dotyczące włączania programu RADIUS Accounting.

## <a name="configure-radius-accounting-on-the-vpn-system"></a>Konfigurowanie usługi RADIUS Accounting w systemie VPN

Wykonaj poniższe czynności na serwerze RRAS.

1. Otwórz **konsolę Routing i dostęp** zdalny.
1. Kliknij prawym przyciskiem myszy nazwę serwera i wybierz pozycję **Właściwości**.
1. Na karcie **Zabezpieczenia w** obszarze Dostawca **księgowości** wybierz pozycję **RADIUS Accounting** i wybierz pozycję **Konfiguruj**.

   :::image type="content" source="../../media/defender-identity/radius-setup.png" alt-text="Konfiguracja USŁUGI RADIUS" lightbox="../../media/defender-identity/radius-setup.png":::

1. W **oknie Add RADIUS Server (Dodaj serwer RADIUS** ) wpisz **nazwę serwera** [!INCLUDE [Product short](includes/product-short.md)] najbliższego czujnika (który ma łączność sieciową). Aby uzyskać wysoką dostępność, możesz dodać dodatkowe czujniki [!INCLUDE [Product short](includes/product-short.md)] jako serwery RADIUS. W **obszarze Port** upewnij się, że skonfigurowano domyślną wartość 1813. Wybierz **pozycję** Zmień i wpisz nowy udostępniony tajny ciąg znaków alfanumerycznych. Zanotuj nowy udostępniony ciąg tajny, ponieważ będzie konieczne jego późniejsze wypełnienie podczas konfiguracji [!INCLUDE [Product short](includes/product-short.md)] . Zaznacz pole **wyboru Wyślij konto Wł. i Księgowe** wyłączone dla konta i wybierz przycisk **OK** we wszystkich otwartych oknach dialogowych.

   :::image type="content" source="../../media/defender-identity/vpn-set-accounting.png" alt-text="Konfiguracja sieci VPN" lightbox="../../media/defender-identity/vpn-set-accounting.png":::

## <a name="configure-vpn-in-defender-for-identity"></a>Konfigurowanie sieci VPN w programie Defender dla tożsamości

[!INCLUDE [Product short](includes/product-short.md)] zbiera dane vpn, które pomagają profilować lokalizacje, z których komputery nawiązą połączenie z siecią, oraz wykrywać podejrzane połączenia VPN.

Aby skonfigurować dane vpn w sieci [!INCLUDE [Product short](includes/product-short.md)] Microsoft 365 Defender:

1. Na <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> **przejdź do Ustawienia** i **Tożsamości**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Opcja Tożsamości w obszarze pozycji menu Ustawienia" lightbox="../../media/defender-identity/settings-identities.png":::

1. Wybierz **pozycję VPN**.
1. Wybierz **pozycję Włącz księgowość promieniową** i wpisz **współużytkowana** tajemnica skonfigurowana wcześniej na serwerze VPN usługi RRAS. Następnie wybierz **pozycję Zapisz**.

   :::image type="content" source="../../media/defender-identity/vpn-integration.png" alt-text="Integracja z siecią VPN" lightbox="../../media/defender-identity/vpn-integration.png":::

Po włączeniu tej funkcji wszystkie czujniki usługi Defender dla tożsamości będą nasłuchiwać zdarzeń programu RADIUS na porcie 1813 i konfiguracja sieci VPN zostanie ukończona.

Gdy czujnik usługi Defender for Identity odbierze zdarzenia VPN i wyśle je do usługi w chmurze Defender for Identity w celu przetworzenia, profil jednostki będzie wskazywać odrębne dostępne lokalizacje VPN i działania w profilu będą wskazywać lokalizacje.

## <a name="see-also"></a>Zobacz też

- [Badanie alertów w programie Microsoft 365 Defender](../defender/investigate-alerts.md)
