---
title: Powiadomienia o incydentach za pośrednictwem poczty e-mail Microsoft 365 Defender
description: Dowiedz się, jak utworzyć reguły, aby otrzymywać powiadomienia e-mail o incydentach w aplikacji Microsoft 365 Defender
keywords: zdarzenie, wiadomość e-mail, powiadomienia o wiadomościach e-mail, konfigurowanie, użytkownicy, skrzynka pocztowa, wiadomość e-mail, zdarzenia, analiza, odpowiedź
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 600ff555762112222769fde0372716f4a89a12b9
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2021
ms.locfileid: "62989727"
---
# <a name="get-incident-notifications-by-email"></a>Powiadomienia o incydentach za pośrednictwem poczty e-mail

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Możesz skonfigurować powiadamianie Microsoft 365 Defender e-mail o nowych zdarzeniach lub aktualizacjach istniejących zdarzeń. Możesz otrzymywać powiadomienia na podstawie:

- Ważność zdarzenia.
- Grupa Urządzenia.
- Tylko w pierwszej aktualizacji na zdarzenie.

Powiadomienie e-mail zawiera między innymi ważne informacje o zdarzeniu, takie jak nazwa zdarzenia, ważność i kategorie. Możesz również przejść bezpośrednio do zdarzenia i od razu rozpocząć analizę. Aby uzyskać więcej informacji, zobacz [Badanie zdarzeń](investigate-incidents.md).

Możesz dodawać lub usuwać adresatów w powiadomieniach e-mail. Nowi adresaci są powiadamiani o incydentach po ich dodaniu. 

>[!NOTE]
>Do skonfigurowania ustawień powiadomień e-mail potrzebne są uprawnienia "Zarządzaj ustawieniami zabezpieczeń". Jeśli wybrano podstawowe zarządzanie uprawnieniami, użytkownicy z rolami administratora zabezpieczeń lub administratora globalnego mogą konfigurować powiadomienia e-mail. <br> <br>
Podobnie, jeśli organizacja używa kontroli dostępu opartej na rolach (RBAC, role based access control), możesz tylko tworzyć, edytować, usuwać i odbierać powiadomienia w oparciu o grupy urządzeń, które możesz zarządzać.

## <a name="create-a-rule-for-email-notifications"></a>Tworzenie reguły dotyczącej powiadomień e-mail

Wykonaj poniższe czynności, aby utworzyć nową regułę i dostosować ustawienia powiadomień e-mail.

1. W okienku nawigacji wybierz pozycję Ustawienia > Microsoft 365 Defender > **e-mail o zdarzeniu**.
2. Wybierz **pozycję Dodaj element**.
3. Na stronie **Podstawy** wpisz nazwę reguły i opis, a następnie wybierz pozycję **Dalej**.
4. Na stronie **Ustawienia powiadomień** skonfiguruj:
    - **Ważność alertu** — wybierz ważność alertu, które powodują uruchomienie powiadomienia o zdarzeniu. Jeśli na przykład chcesz zostać poinformowany tylko o zdarzeniach o wysokim poziomie ważności, wybierz pozycję **Wysoka**.
    - **Zakres grupy urządzeń** — możesz określić wszystkie grupy urządzeń lub wybrać je z listy grup urządzeń w dzierżawie.
    - **Powiadamianie tylko przy pierwszym wystąpieniu zdarzenia** — wybierz, czy chcesz, aby powiadomienie było tylko przy pierwszym alercie, który jest taki, jak w przypadku innych zaznaczeń. Późniejsze aktualizacje i alerty dotyczące zdarzenia nie będą wysyłać dodatkowych powiadomień.
    - **Uwzględnij nazwę organizacji w wiadomości** e-mail — wybierz, czy nazwa organizacji ma być wyświetlana w powiadomieniu e-mail.
    - **Dołącz link do portalu specyficznego** dla dzierżawy — wybierz, czy chcesz dodać link z identyfikatorem dzierżawy w powiadomieniu e-mail o uzyskiwaniu dostępu do określonej Microsoft 365 dzierżawy.

    :::image type="content" source="../../media/get-incident-notifications/incidents-ss-email-notification-settings.png" alt-text="Ustawienia powiadomień dotyczących powiadomień e-mail o incydentach.":::

5. Wybierz pozycję **Dalej**. Na stronie **Adresaci** dodaj adresy e-mail, na które będą wysyłane powiadomienia o incydentach. Wybierz **pozycję Dodaj** po wpisaniu każdego nowego adresu e-mail. Aby przetestować powiadomienia i upewnić się, że adresaci otrzymają je w skrzynkach odbiorczych, wybierz pozycję **Wyślij testową wiadomość e-mail**. 
6. Wybierz pozycję **Dalej**. Na **stronie Recenzja** reguły przejrzyj ustawienia reguły, a następnie wybierz pozycję **Utwórz regułę**. W zależności od ustawień adresaci zaczną otrzymywać powiadomienia o incydentach za pośrednictwem poczty e-mail.

Aby edytować istniejącą regułę, wybierz ją z listy reguł. W okienku z nazwą reguły wybierz pozycję Edytuj  regułę i zmień ustawienia na stronach **Podstawowe** informacje, Ustawienia **powiadomień** **i Adresaci**.

Aby usunąć regułę, wybierz ją z listy reguł. W okienku z nazwą reguły wybierz pozycję **Usuń**.

## <a name="see-also"></a>Zobacz też
- [Omówienie zdarzeń](incidents-overview.md)
- [Określanie priorytetów zdarzeń](incident-queue.md)
- [Badanie zdarzeń](investigate-incidents.md)
