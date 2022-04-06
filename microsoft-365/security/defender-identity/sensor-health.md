---
title: Microsoft Defender for Identity kondycji i ustawień czujnika w Microsoft 365 Defender
description: Dowiedz się, jak skonfigurować Microsoft Defender for Identity i monitorować ich stan zdrowia w Microsoft 365 Defender
ms.date: 06/07/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: 246fd5ca880ca2d7e187283d06f19d071f5d7e0e
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468528"
---
# <a name="microsoft-defender-for-identity-sensor-health-and-settings-in-microsoft-365-defender"></a>Microsoft Defender for Identity kondycji i ustawień czujnika w Microsoft 365 Defender

**Dotyczy:**

- Microsoft 365 Defender
- Defender for Identity

W tym artykule wyjaśniono, jak konfigurować i [monitorować Microsoft Defender for Identity](/defender-for-identity) [czujniki Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>W ramach schłodowania w Microsoft 365 Defender tożsamości niektóre opcje i szczegóły zmieniły się od ich lokalizacji w portalu usługi Defender dla tożsamości. Zapoznaj się ze szczegółami poniżej, aby dowiedzieć się, gdzie znaleźć zarówno znane, jak i nowe funkcje.

## <a name="view-defender-for-identity-sensor-settings-and-status"></a>Wyświetl ustawienia i stan czujnika tożsamości usługi Defender

1. Na <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> **przejdź do Ustawienia** i **Tożsamości**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Opcja Tożsamości na stronie Ustawienia sieci Web" lightbox="../../media/defender-identity/settings-identities.png":::

1. Wybierz stronę **Czujniki** , na której są wyświetlane wszystkie czujniki usługi Defender for Identity. Dla każdego czujnika zobaczysz jego nazwę, członkostwo w domenie, numer wersji, jeśli aktualizacje powinny być opóźnione, stan usługi, stan aktualizacji, stan kondycji, liczbę problemów dotyczących kondycji oraz czas utworzenia czujnika.

    [![Strona czujnika.](../../media/defender-identity/sensor-page.png)](../../media/defender-identity/sensor-page.png#lightbox)

    >[!NOTE]
    >W portalu usługi Defender for Identity ustawienia czujnika i informacje o kondycji były w osobnych lokalizacjach. Pamiętaj, Microsoft 365 Defender że teraz są na tej samej stronie.

1. Jeśli wybierzesz **pozycję** Filtry, możesz wybrać filtry, które będą dostępne. Następnie w przypadku każdego filtru możesz wybrać czujniki do wyświetlenia.

    [![Filtry czujnika.](../../media/defender-identity/sensor-filters.png)](../../media/defender-identity/sensor-filters.png#lightbox)

    :::image type="content" source="../../media/defender-identity/filtered-sensor.png" alt-text="Czujnik filtrowany" lightbox="../../media/defender-identity/filtered-sensor.png":::

1. Jeśli wybierzesz jeden z czujnika, zostanie otwarte okienko z informacjami o czujniku i jego stanie kondycji.

    [![Szczegóły czujnika.](../../media/defender-identity/sensor-details.png)](../../media/defender-identity/sensor-details.png#lightbox)

1. Jeśli wybierzesz dowolny z problemów z kondycją, zostanie otwarte okienko ze szczegółami na ich temat. Jeśli wybierzesz problem zamknięty, możesz otworzyć go ponownie w tym miejscu.

   :::image type="content" source="../../media/defender-identity/issue-details.png" alt-text="Szczegóły problemu" lightbox="../../media/defender-identity/issue-details.png":::
    

1. Jeśli wybierzesz **pozycję Zarządzaj czujnikiem**, zostanie otwarte okienko, w którym możesz skonfigurować szczegóły czujnika.

   :::image type="content" source="../../media/defender-identity/manage-sensor.png" alt-text="Opcja Zarządzaj czujnikiem" lightbox="../../media/defender-identity/manage-sensor.png":::

   :::image type="content" source="../../media/defender-identity/configure-sensor-details.png" alt-text="Strona, na której konfiguruje się ustawienia czujnika" lightbox="../../media/defender-identity/configure-sensor-details.png":::

1. Na stronie **Czujniki** możesz wyeksportować listę czujniki do pliku .csv, wybierając pozycję **Eksportuj**.

   :::image type="content" source="../../media/defender-identity/export-sensors.png" alt-text="Lista czujników eksportu" lightbox="../../media/defender-identity/export-sensors.png":::

## <a name="add-a-sensor"></a>Dodaj czujnik

Na stronie **Czujniki** możesz dodać nowy czujnik.

1. Wybierz **pozycję Dodaj czujnik**.

   :::image type="content" source="../../media/defender-identity/add-sensor.png" alt-text="Opcja Dodaj czujnik" lightbox="../../media/defender-identity/add-sensor.png":::

1. Zostanie otwarte okienko z przyciskiem pobierania instalatora czujnika i wygenerowanym kluczem dostępu.

   :::image type="content" source="../../media/defender-identity/installer-access-key.png" alt-text="Opcje pobierania instalatora i ponownego generowania klucza" lightbox="../../media/defender-identity/installer-access-key.png":::

1. Wybierz **pozycję Pobierz instalatora** , aby zapisać pakiet lokalnie. Plik zip zawiera następujące pliki:

    - Instalator czujnika usługi Defender for Identity

    - Plik ustawień konfiguracji z informacjami wymaganymi do nawiązania połączenia z usługą w chmurze Defender for Identity

1. Skopiuj klawisz **programu Access**. Do połączenia się z wystąpieniem usługi Defender for Identity jest wymagany klucz dostępu czujnika tożsamości usługi Defender. Klucz dostępu to hasło logowania się do wdrożenia czujnika, po którym cała komunikacja jest wykonywana przy użyciu certyfikatów na celu uwierzytelniania i szyfrowania TLS. Użyj **przycisku Generuj** ponownie, jeśli kiedykolwiek zajdą konieczność ponownego wygenerowania nowego klucza dostępu. Nie wpływa on na żadne wcześniej wdrożone czujniki, ponieważ jest używany tylko do wstępnej rejestracji czujnika.

1. Skopiuj pakiet na dedykowany serwer lub kontroler domeny, na który instalujesz czujnik usługi Defender for Identity.

## <a name="see-also"></a>Zobacz też

- [Zarządzanie alertami zabezpieczeń usługi Defender for Identity](manage-security-alerts.md)
