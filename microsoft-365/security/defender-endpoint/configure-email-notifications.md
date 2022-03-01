---
title: Konfigurowanie powiadomień alertów w programie Microsoft Defender dla punktu końcowego
description: Za pomocą programu Microsoft Defender for Endpoint możesz skonfigurować ustawienia powiadomień e-mail dla alertów zabezpieczeń na podstawie ważności i innych kryteriów.
keywords: powiadomienia e-mail, konfigurowanie powiadomień alertów, program Microsoft Defender dla punktu końcowego, powiadomienia programu Microsoft Defender dla punktu końcowego, alerty programu Microsoft Defender dla punktów końcowych, windows enterprise, windows education
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
ms.openlocfilehash: f2e4cc2db64a01605a0003561ceda27409b16cf5
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997856"
---
# <a name="configure-alert-notifications-in-microsoft-defender-for-endpoint"></a>Konfigurowanie powiadomień alertów w programie Microsoft Defender dla punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-emailconfig-abovefoldlink)

Możesz skonfigurować usługę Defender for Endpoint w celu wysyłania powiadomień e-mail do określonych adresatów o nowych alertach. Ta funkcja umożliwia zidentyfikowanie grupy osób, które zostaną natychmiast poinformowane i mogą działać na podstawie ich ważności.

> [!NOTE]
> Powiadomienia e-mail mogą konfigurować tylko użytkownicy z uprawnieniami do zarządzania ustawieniami zabezpieczeń. Jeśli wybrano podstawowe zarządzanie uprawnieniami, użytkownicy z rolami administratora zabezpieczeń lub administratora globalnego mogą konfigurować powiadomienia e-mail.

Możesz ustawić poziomy ważności alertów, które powodują powiadomienia. Możesz również dodać lub usunąć adresatów powiadomienia e-mail. Nowi adresaci otrzymują powiadomienia o alertach wyzwalanych po ich dodaniu. Aby uzyskać więcej informacji o alertach, zobacz [Wyświetlanie i organizowanie kolejki alertów](alerts-queue.md).

Jeśli korzystasz z kontroli dostępu opartej na rolach, adresaci będą otrzymywać powiadomienia tylko na podstawie grup urządzeń skonfigurowanych w  regułę powiadomień.
Użytkownicy z odpowiednimi uprawnieniami mogą tylko tworzyć, edytować i usuwać powiadomienia ograniczone do zakresu zarządzania grupą urządzeń.
Tylko użytkownicy przypisani do roli administratora globalnego mogą zarządzać regułami powiadomień skonfigurowanymi dla wszystkich grup urządzeń.

Powiadomienie e-mail zawiera podstawowe informacje o alercie i link do portalu, w którym można wykonać dalsze badanie.

## <a name="create-rules-for-alert-notifications"></a>Tworzenie reguł dla powiadomień alertów
Możesz utworzyć reguły, które określają urządzenia i ważność alertów, aby wysyłać powiadomienia e-mail dla adresatów i adresatów powiadomień.


1. W okienku nawigacji wybierz **pozycję Ustawienia** \> **Punkty końcowe Ogólne** \> **powiadomienia** **e-mail**\>.

2. Kliknij **pozycję Dodaj element**.

3. Określ informacje ogólne:
    - **Nazwa reguły** — określ nazwę reguły powiadomień.
    - **Uwzględnij nazwę organizacji** — określ nazwę klienta wyświetlaną w powiadomieniu e-mail.
    - **Dołącz link do portalu specyficznego** dla dzierżawy — umożliwia dodanie linku z identyfikatorem dzierżawy w celu umożliwienia dostępu do określonej dzierżawy.
    - **Uwzględnij informacje o urządzeniu** — zawiera nazwę urządzenia w treści alertu e-mail.

        > [!NOTE]
        > Te informacje mogą być przetwarzane przez serwery poczty adresatów, które nie są w lokalizacji geograficznej wybranej dla danych punktu końcowego usługi Defender.

    - **Urządzenia** — wybierz, czy chcesz powiadamiać adresatów o alertach na wszystkich urządzeniach (tylko w roli administratora globalnego), czy w wybranych grupach urządzeń. Aby uzyskać więcej informacji, zobacz [Tworzenie grup urządzeń i zarządzanie nimi](machine-groups.md).
    - **Ważność alertu** — wybierz poziom ważności alertu.

4. Kliknij **Dalej**.

5. Wprowadź adres e-mail adresata, a następnie kliknij **pozycję Dodaj adresata**. Możesz dodać wiele adresów e-mail.

6. Sprawdź, czy adresaci wiadomości e-mail mogą otrzymywać powiadomienia e-mail, wybierając pozycję **Wyślij testową wiadomość e-mail**.

7. Kliknij **pozycję Zapisz regułę powiadomień**.

## <a name="edit-a-notification-rule"></a>Edytowanie reguły powiadomień

1. Wybierz regułę powiadomień, które chcesz edytować.

2. Aktualizowanie informacji o kartach Ogólne i Adresaci.

3. Kliknij **pozycję Zapisz regułę powiadomień**.

## <a name="delete-notification-rule"></a>Usuwanie reguły powiadomień

1. Wybierz regułę powiadomień, które chcesz usunąć.

2. Kliknij przycisk **Usuń**.

## <a name="troubleshoot-email-notifications-for-alerts"></a>Rozwiązywanie problemów z powiadomieniami e-mail dla alertów

Ta sekcja zawiera listę różnych problemów, które mogą wystąpić podczas korzystania z powiadomień e-mail o alertach.

**Problem:** Zamierzony adresaci zgłaszają, że nie otrzymują powiadomień.

**Rozwiązanie:** Upewnij się, że powiadomienia nie są blokowane przez filtry wiadomości e-mail:

1. Sprawdź, czy powiadomienia e-mail dotyczące usługi Defender for Endpoint nie są wysyłane do folderu Wiadomości-śmieci. Oznaczaj je jako niebędące śmieciem.
2. Sprawdź, czy Twój produkt zabezpieczeń poczty e-mail nie blokuje powiadomień e-mail od usługi Defender for Endpoint.
3. Sprawdź reguły aplikacji poczty e-mail, które mogą być wychwytujące i przenoszące powiadomienia e-mail programu Defender dla punktu końcowego.

## <a name="related-topics"></a>Tematy pokrewne

- [Aktualizowanie ustawień przechowywania danych](data-retention-settings.md)
- [Konfigurowanie funkcji zaawansowanych](advanced-features.md)
- [Konfigurowanie powiadomień e-mail z luk w zabezpieczeniach w programie Microsoft Defender dla punktu końcowego](/microsoft-365/security/defender-endpoint/configure-vulnerability-email-notifications)
