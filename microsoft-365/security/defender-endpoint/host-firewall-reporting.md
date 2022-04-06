---
title: Raportowanie zapory hosta w programie Ochrona punktu końcowego w usłudze Microsoft Defender
description: Hostuj i wyświetlaj raporty zapory w Microsoft 365 Defender sieci.
keywords: windows defender, zapora
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: dansimp
ms.author: dansimp
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: e5bbdd77226f8649f2a781866fef614706e8a789
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475284"
---
# <a name="host-firewall-reporting-in-microsoft-defender-for-endpoint"></a>Raportowanie zapory hosta w programie Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Jeśli jesteś administratorem, możesz teraz hostować raporty zapory w portalu Microsoft 365 Defender [sieci.](https://security.microsoft.com) Ta funkcja umożliwia wyświetlanie raportów Windows 10, Windows 11, Windows Server 2019 i Windows Server 2022 z scentralizowanej lokalizacji.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Musisz mieć uruchomiony program Windows 10, Windows 11 lub Windows Server 2019 albo Windows Server 2022.
- Aby na przykład do urządzenia Ochrona punktu końcowego w usłudze Microsoft Defender usługi, zobacz [tutaj](onboard-configure.md).
- Aby <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender rozpocząć</a> odbieranie danych, należy włączyć zdarzenia inspekcji dla zapory Windows Defender z  zabezpieczeniami zaawansowanymi:
  - [Upuszczenie pakietów platformy filtrowania inspekcji](/windows/security/threat-protection/auditing/audit-filtering-platform-packet-drop)
  - [Połączenie platformy filtrowania inspekcji](/windows/security/threat-protection/auditing/audit-filtering-platform-connection)
- Aby włączyć te zdarzenia, zasady grupy Edytora obiektów, lokalnych zasad zabezpieczeń auditpol.exe polecenia. Aby uzyskać więcej informacji, zobacz [tutaj](/windows/win32/fwp/auditing-and-logging).
  - Dwa polecenia programu PowerShell to:
    - **auditpol /set /subcategory:"Filtering Platform Packet Drop" /failure:enable**
    - **auditpol /set /podkategoria:"Połączenie platformy filtrowania" /błąd:włącz**

## <a name="the-process"></a>Proces

> [!NOTE]
> Należy się upewnić, że należy postępować zgodnie z instrukcjami podanymi w powyższej sekcji, i poprawnie skonfigurować swoje urządzenia pod celu wcześniejszego uczestnictwa w wersji Preview.

- Po włączeniu zdarzeń Microsoft 365 Defender rozpocznie się monitorowanie danych.
  - Zdalny adres IP, port zdalny, port lokalny, lokalny adres IP, nazwa komputera, przetwarzanie z połączeniami przychodzącymi i wychodzącymi.
- Administratorzy mogą teraz zobaczyć tutaj Windows aktywności [hosta zapory](https://security.microsoft.com/firewall).
  - Dodatkowe raportowanie można usprawnić, pobierając skrypt [raportowania](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall) niestandardowego w celu monitorowania działań Zapory Windows Defender za pomocą Power BI.
  - Zanim dane będą odzwierciedlane, może upłynie do 12 godzin.

## <a name="supported-scenarios"></a>Obsługiwane scenariusze

W trakcie testowania wersji Ring0 Preview są obsługiwane następujące scenariusze.

### <a name="firewall-reporting"></a>Raportowanie zapory

Oto kilka przykładów stron raportu zapory. Tutaj znajdziesz podsumowanie aktywności aplikacji i ruchu przychodzącego. Dostęp do tej strony możesz uzyskać bezpośrednio, przechodząc do strony <https://security.microsoft.com/firewall>.

> [!div class="mx-imgBorder"]
> :::image type="content" source="\images\host-firewall-reporting-page.png" alt-text="Strona raportowania Zapory hosta" lightbox="\images\host-firewall-reporting-page.png":::

Dostęp do tych raportów można również uzyskać, przechodząc do strony **ReportsSecurity** >  **ReportDevices** >  (sekcja) znajdującej się u dołu karty Połączenia przychodzące zablokowane przez **zaporę.**

### <a name="from-computers-with-a-blocked-connection-to-device"></a>Z "Komputery z zablokowanym połączeniem" do urządzenia

Karty obsługują obiekty interakcyjne. Możesz przejść do szczegółów aktywności na urządzeniu, klikając nazwę urządzenia, co spowoduje uruchomienie portalu Microsoft 365 Defender w nowej karcie i bezpośrednie przechodzenie do karty Oś **czasu urządzenia.**

> [!div class="mx-imgBorder"]
> :::image type="content" source="\images\firewall-reporting-blocked-connection.png" alt-text="Strona Komputery z zablokowanym połączeniem" lightbox="\images\firewall-reporting-blocked-connection.png":::

Teraz możesz wybrać **kartę Oś** czasu, która zawiera listę zdarzeń skojarzonych z tym urządzeniem.

Po kliknięciu **przycisku Filtry** w prawym górnym rogu okienka wyświetlania wybierz odpowiedni typ zdarzenia. W takim przypadku wybierz pozycję **Zdarzenia zapory** , a okienko zostanie odfiltrowane do zdarzeń zapory.

> [!div class="mx-imgBorder"]
> :::image type="content" source="\images\firewall-reporting-filters-button.png" alt-text="Przycisk Filtry" lightbox="\images\firewall-reporting-filters-button.png":::

### <a name="drill-into-advanced-hunting-preview-refresh"></a>Przechodzenie do szczegółów zaawansowanego wyszukiwania (odświeżanie podglądu)

Raporty zapory obsługują przechodzenie z karty bezpośrednio do pozycji **Szukanie zaawansowane** , klikając **przycisk Otwórz zaawansowane szukanie** . Zapytanie zostanie wstępnie wypełnione.

> [!div class="mx-imgBorder"]
> :::image type="content" source="\images\firewall-reporting-advanced-hunting.png" alt-text="Przycisk Wyszukiwania zaawansowanego" lightbox="\images\firewall-reporting-advanced-hunting.png":::

Kwerendę można teraz wykonać i można eksplorować wszystkie powiązane zdarzenia zapory z ostatnich 30 dni.

W celu uzyskania dodatkowych raportów lub zmian niestandardowych zapytanie można wyeksportować do Power BI do dalszej analizy. Raportowanie niestandardowe można usprawnić, pobierając skrypt [raportowania](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall) niestandardowego w celu monitorowania działań Zapory Windows Defender za pomocą Power BI.
