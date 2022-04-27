---
title: Centrum administracyjne platformy Microsoft 365 raporty użycia przeglądarki
ms.author: waxiaoyu
author: sarahwxy
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
description: Dowiedz się, jak uzyskać raport użycia przeglądarki Firmy Microsoft przy użyciu pulpitu nawigacyjnego Microsoft 365 Reports w Centrum administracyjne platformy Microsoft 365.
ms.openlocfilehash: 5515c00b5c7fc64a6f0295bdce724e5b798fb018
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65078318"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-browser-usage"></a>Microsoft 365 Raporty w centrum administracyjnym — użycie przeglądarki Microsoft

Na pulpicie nawigacyjnym raportów Microsoft 365 przedstawiono omówienie działań w produktach w organizacji. Umożliwia przechodzenie do szczegółów poszczególnych raportów na poziomie produktu, aby uzyskać bardziej szczegółowy wgląd w działania w ramach każdego produktu. Zobacz [temat zawierający omówienie pulpitu nawigacyjnego Raporty](activity-reports.md). W raporcie użycia przeglądarki firmy Microsoft możesz uzyskać szczegółowe informacje na temat programu Internet Explorer, Starsza wersja Microsoft Edge i nowego użycia Microsoft Edge. Raportowanie użycia jest oparte na Microsoft 365 Usługi online, do których uzyskuje się dostęp za pomocą przeglądarki Microsoft na dowolnym urządzeniu korzystającym z konta Microsoft 365.

## <a name="how-to-get-to-the-microsoft-browser-usage-report"></a>Jak uzyskać dostęp do raportu użycia przeglądarki firmy Microsoft

1. W centrum administracyjnym przejdź do strony **Raporty** \> <b><a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">użycia</a></b> .

2. Na stronie głównej pulpitu nawigacyjnego kliknij przycisk **Wyświetl więcej** na karcie użycia przeglądarki firmy Microsoft.

## <a name="how-to-notify-users-to-upgrade-their-browser"></a>Jak powiadomić użytkowników o uaktualnieniu przeglądarki

:::image type="content" alt-text="Przepływ akcji raportu użycia przeglądarki Firmy Microsoft." source="../../media/1ef4eb08-18b8-4dda-aa15-1aad013ecd70.png" lightbox="../../media/1ef4eb08-18b8-4dda-aa15-1aad013ecd70.png":::

Administratorzy globalni mogą zdecydować się na wysyłanie komunikatów do użytkowników, którzy uzyskują dostęp do usług Microsoft 365 z programu Internet Explorer (przypominamy, że aplikacja klasyczna programu Internet Explorer zostanie wycofana 15 czerwca 2022 r.). Ten docelowy komunikat powiadamia użytkowników, że obsługa tych przeglądarek zakończy się wkrótce i linki do artykułu pomocy technicznej z informacjami na temat Microsoft Edge i prostych kroków do wykonania w celu przełączenia przeglądarek. 

Tę funkcję można znaleźć na stronie raportu użycia przeglądarki Firmy Microsoft, jeśli w raporcie jest wyświetlane użycie programu Internet Explorer (wymagane są uprawnienia administratora globalnego). Po utworzeniu komunikatu użytkownicy będą otrzymywać powiadomienia z częstotliwością określoną do 15 czerwca 2022 r. Tę funkcję można włączyć lub wyłączyć w dowolnym momencie.

Jest to funkcja ograniczona czasowo, która jest obecnie dostępna tylko dla administratorów globalnych w Stanach Zjednoczonych i umożliwia powiadomienia użytkowników w Excel online.

## <a name="interpret-the-microsoft-browser-usage-report"></a>Interpretowanie raportu użycia przeglądarki Firmy Microsoft

:::image type="content" alt-text="Raport użycia przeglądarki Firmy Microsoft." source="../../media/95557c88-24ee-417d-a828-96ba00b17aaf.png" lightbox="../../media/95557c88-24ee-417d-a828-96ba00b17aaf.png":::

|Element|Opis|
|:-----|:-----|
|1. |Raport **użycia przeglądarki firmy Microsoft** można wyświetlić dla trendów z ostatnich 7 dni, 30 dni, 90 dni lub 180 dni. |
|2. |Dane w każdym raporcie zwykle obejmują maksymalnie siedem ostatnich dni. |
|3. |Wykres **Dzienni aktywni użytkownicy** pokazuje dzienną liczbę użytkowników dla Microsoft Edge, Starsza wersja Microsoft Edge i Programu Internet Explorer, gdy są używane do uzyskiwania dostępu do usług Microsoft 365. |
|4. |Wykres **Aktywni użytkownicy** przedstawia łączną liczbę użytkowników korzystających z Microsoft Edge, Starsza wersja Microsoft Edge i programu Internet Explorer, gdy są używane do uzyskiwania dostępu do usług Microsoft 365 w wybranym okresie. |
|5. |W tabeli przedstawiono zestawienie danych na poziomie poszczególnych użytkowników. Możesz dodać lub usunąć kolumny z tabeli.  <br/><br/>**Nazwa użytkownika** to adres e-mail użytkownika, który łączył się z usługami Microsoft 365 przy użyciu przeglądarek firmy Microsoft.<br><br/>**Użyte Microsoft Edge** pokazuje znacznik wyboru, jeśli użytkownik użył Microsoft Edge do nawiązania połączenia z usługami Microsoft 365.<br/><br/>**Użyte Starsza wersja Microsoft Edge** pokazuje znacznik wyboru, jeśli użytkownik użył Starsza wersja Microsoft Edge do nawiązania połączenia z usługami Microsoft 365.<br/><br/>**Używany program Internet Explorer** pokazuje znacznik wyboru, jeśli użytkownik używał programu Internet Explorer do nawiązywania połączenia z usługami Microsoft 365. |
|6. |Wybierz ikonę **Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.|
|7. |Możesz również wyeksportować dane raportu do pliku Excel .csv, wybierając link **Eksportuj**. Umożliwia to eksportowanie danych dla wszystkich użytkowników i umożliwia wykonywanie prostej agregacji, sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 100 użytkowników, możesz sortować i filtrować w tabeli w samym raporcie. Jeśli masz więcej niż 100 użytkowników, aby filtrować i sortować, musisz wyeksportować dane.|
