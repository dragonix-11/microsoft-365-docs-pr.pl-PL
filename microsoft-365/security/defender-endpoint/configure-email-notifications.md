---
title: Konfigurowanie powiadomień o alertach w Ochrona punktu końcowego w usłudze Microsoft Defender
description: Za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender można skonfigurować ustawienia powiadomień e-mail dla alertów zabezpieczeń na podstawie ważności i innych kryteriów.
keywords: powiadomienia e-mail, konfigurowanie powiadomień o alertach, Ochrona punktu końcowego w usłudze Microsoft Defender, Ochrona punktu końcowego w usłudze Microsoft Defender powiadomień, alerty Ochrona punktu końcowego w usłudze Microsoft Defender, windows enterprise, windows education
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: fde5ce238a44b6722770338378ae33c54a38a450
ms.sourcegitcommit: 60970cf8a2cb451011c423d797dfb77925394f89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2022
ms.locfileid: "65587495"
---
# <a name="configure-alert-notifications-in-microsoft-defender-for-endpoint"></a>Konfigurowanie powiadomień o alertach w Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft Defender dla Firm](../defender-business/mdb-overview.md)

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-emailconfig-abovefoldlink)

Usługę Defender for Endpoint można skonfigurować do wysyłania powiadomień e-mail do określonych adresatów dla nowych alertów. Ta funkcja umożliwia zidentyfikowanie grupy osób, które zostaną natychmiast poinformowane i będą mogły działać na podstawie ich ważności.

Jeśli używasz [usługi Defender dla Firm](../defender-business/mdb-overview.md), możesz skonfigurować powiadomienia e-mail dla określonych użytkowników (nie ról ani grup).

> [!NOTE]
> Tylko użytkownicy z uprawnieniami "Zarządzanie ustawieniami zabezpieczeń" mogą konfigurować powiadomienia e-mail. Jeśli wybrano użycie podstawowego zarządzania uprawnieniami, użytkownicy z rolami administratora zabezpieczeń lub administratora globalnego mogą konfigurować powiadomienia e-mail.

Możesz ustawić poziomy ważności alertów wyzwalające powiadomienia. Możesz również dodać lub usunąć adresatów powiadomienia e-mail. Nowi adresaci otrzymują powiadomienia o alertach wyzwalanych po ich dodaniu. Aby uzyskać więcej informacji na temat alertów, zobacz [Wyświetlanie i organizowanie kolejki alertów](alerts-queue.md).

Jeśli używasz kontroli dostępu opartej na rolach (RBAC), adresaci będą otrzymywać powiadomienia tylko na podstawie grup urządzeń skonfigurowanych w regule powiadomień. Użytkownicy z odpowiednimi uprawnieniami mogą tworzyć, edytować lub usuwać powiadomienia ograniczone do zakresu zarządzania grupami urządzeń. Tylko użytkownicy przypisani do roli administrator globalny mogą zarządzać regułami powiadomień skonfigurowanymi dla wszystkich grup urządzeń.

Powiadomienie e-mail zawiera podstawowe informacje o alercie i link do portalu, w którym można tworzyć dalsze badania.

## <a name="create-rules-for-alert-notifications"></a>Tworzenie reguł powiadomień o alertach
Można utworzyć reguły określające ważność urządzeń i alertów w celu wysyłania powiadomień e-mail dla adresatów powiadomień.

1. W okienku nawigacji wybierz pozycję **Ustawienia** \> Ogólne **powiadomienia e-mail** **dotyczące punktów końcowych** \>  \>.

2. Kliknij **pozycję Dodaj element**.

3. Określ informacje ogólne:
    - **Nazwa reguły** — określ nazwę reguły powiadomień.
    - **Dołącz nazwę organizacji** — określ nazwę klienta wyświetlaną w powiadomieniu e-mail.
    - **Dołącz link portalu specyficzny dla dzierżawy** — dodaje link z identyfikatorem dzierżawy, aby umożliwić dostęp do określonej dzierżawy.
    - **Uwzględnij informacje o urządzeniu** — zawiera nazwę urządzenia w treści alertu e-mail.

        > [!NOTE]
        > Te informacje mogą być przetwarzane przez serwery poczty adresatów, które nie znajdują się w lokalizacji geograficznej wybranej dla danych punktu końcowego usługi Defender.

    - **Urządzenia** — określ, czy powiadamiać adresatów o alertach na wszystkich urządzeniach (tylko administrator globalny roli), czy w wybranych grupach urządzeń. Aby uzyskać więcej informacji, zobacz [Tworzenie grup urządzeń i zarządzanie nimi](machine-groups.md). (Jeśli używasz [usługi Defender dla Firm](../defender-business/mdb-overview.md), grupy urządzeń nie mają zastosowania).
    - **Ważność alertu** — wybierz poziom ważności alertu.

4. Kliknij **Dalej**.

5. Wprowadź adres e-mail adresata, a następnie kliknij pozycję **Dodaj adresata**. Możesz dodać wiele adresów e-mail.

6. Sprawdź, czy adresaci wiadomości e-mail mogą odbierać powiadomienia e-mail, wybierając pozycję **Wyślij testowy adres e-mail**.

7. Kliknij **pozycję Zapisz regułę powiadomień**.

## <a name="edit-a-notification-rule"></a>Edytowanie reguły powiadomień

1. Wybierz regułę powiadomień, którą chcesz edytować.

2. Zaktualizuj informacje na karcie Ogólne i Adresat.

3. Kliknij **pozycję Zapisz regułę powiadomień**.

## <a name="delete-notification-rule"></a>Usuwanie reguły powiadomień

1. Wybierz regułę powiadomień, którą chcesz usunąć.

2. Kliknij przycisk **Usuń**.

## <a name="troubleshoot-email-notifications-for-alerts"></a>Rozwiązywanie problemów z powiadomieniami e-mail dla alertów

W tej sekcji wymieniono różne problemy, które mogą wystąpić podczas korzystania z powiadomień e-mail dotyczących alertów.

**Problem:** Zamierzoni adresaci zgłaszają, że nie otrzymują powiadomień.

**Rozwiązanie:** Upewnij się, że powiadomienia nie są blokowane przez filtry poczty e-mail:

1. Sprawdź, czy powiadomienia e-mail usługi Defender for Endpoint nie są wysyłane do folderu Wiadomości-śmieci. Oznacz je jako nie-śmieci.
2. Sprawdź, czy produkt zabezpieczeń poczty e-mail nie blokuje powiadomień e-mail z usługi Defender for Endpoint.
3. Sprawdź reguły aplikacji poczty e-mail, które mogą łapać i przenosić powiadomienia e-mail usługi Defender for Endpoint.

## <a name="related-topics"></a>Tematy pokrewne

- [Aktualizowanie ustawień przechowywania danych](data-retention-settings.md)
- [Konfiguruj funkcje zaawansowane](advanced-features.md)
- [Konfigurowanie powiadomień e-mail o lukach w zabezpieczeniach w Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/configure-vulnerability-email-notifications)
