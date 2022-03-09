---
title: centrum administracyjne platformy Microsoft 365 raportów dotyczących użycia przeglądarki
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
description: Dowiedz się, jak uzyskać raport użycia przeglądarki firmy Microsoft przy użyciu pulpitu nawigacyjnego Raporty Microsoft 365 na stronie centrum administracyjne platformy Microsoft 365.
ms.openlocfilehash: cfeed7f311816e72d06f63e36aabe9f6ffad718f
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2022
ms.locfileid: "63400968"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-browser-usage"></a>Microsoft 365 raporty w centrum administracyjnym — Użycie przeglądarki firmy Microsoft

Pulpit Microsoft 365 raporty umożliwia przegląd aktywności w produktach w organizacji. Przechodzenie do poziomu raportów dotyczących poszczególnych produktów umożliwia uzyskanie bardziej szczegółowych informacji o aktywności w poszczególnych produktach. Zobacz [temat zawierający omówienie pulpitu nawigacyjnego Raporty](activity-reports.md). Raport użycia przeglądarki firmy Microsoft pozwala uzyskać szczegółowe informacje na temat przeglądarek Internet Explorer, aplikacji Starsza wersja Microsoft Edge oraz nowych funkcji Microsoft Edge przeglądarce. Raportowanie użycia jest oparte na Microsoft 365 online, do których można uzyskiwać dostęp przy użyciu przeglądarki firmy Microsoft.

## <a name="how-to-get-to-the-microsoft-browser-usage-report"></a>Jak uzyskać dostęp do raportu użycia przeglądarki firmy Microsoft

1. W centrum administracyjnym przejdź do strony **Raporty** \> <b><a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">użycia</a></b> .

2. Na stronie głównej pulpitu nawigacyjnego kliknij przycisk **Wyświetl więcej** na karcie Użycie przeglądarki firmy Microsoft.

## <a name="how-to-notify-users-to-upgrade-their-browser"></a>Jak powiadomić użytkowników o uaktualnieniu przeglądarki

:::image type="content" alt-text="Przepływ akcji raportu użycia przeglądarki firmy Microsoft." source="../../media/1ef4eb08-18b8-4dda-aa15-1aad013ecd70.png" lightbox="../../media/1ef4eb08-18b8-4dda-aa15-1aad013ecd70.png":::

Administratorzy globalni mogą wyrazić zgodę na wysyłanie wiadomości do użytkowników, którzy mają dostęp do usług Microsoft 365 z programu Internet Explorer (przypomnienie: aplikacja komputerowa Internet Explorer zostanie wycofana 15 czerwca 2022 r.). W tej wiadomości docelowej jest wyświetlany komunikat z powiadomieniem dla użytkowników, że obsługa tych przeglądarek zostanie wkrótce przesłana wraz z linkiem do artykułu pomocy technicznej z informacjami na temat Microsoft Edge i czynnościami, które należy wykonać w celu przełączenia przeglądarek. 

Tę funkcję można znaleźć na stronie Raport użycia przeglądarki firmy Microsoft, jeśli w raporcie jest wyświetlone użycie programu Internet Explorer (wymagane są uprawnienia administratora globalnego). Po utworzeniu wiadomości użytkownicy będą o tym powiadamiani z częstotliwością określoną do 15 czerwca 2022 r. Tę funkcję można włączyć lub wyłączyć w dowolnym momencie.

Jest to funkcja ograniczona czas, która jest obecnie dostępna tylko dla administratorów globalnych w USA i umożliwia powiadomienia użytkowników w Excel online.

## <a name="interpret-the-microsoft-browser-usage-report"></a>Interpretowanie raportu użycia przeglądarki firmy Microsoft

:::image type="content" alt-text="Raport użycia przeglądarki firmy Microsoft." source="../../media/95557c88-24ee-417d-a828-96ba00b17aaf.png" lightbox="../../media/95557c88-24ee-417d-a828-96ba00b17aaf.png":::

|Element|Opis|
|:-----|:-----|
|1. |W **raporcie Użycie przeglądarki firmy Microsoft** można przeglądać trendy z ostatnich 7, 30, 90 lub 180 dni. |
|2. |Dane w poszczególnych raportach zazwyczaj obejmują maksymalnie siedem ostatnich dni. |
|3. |Wykres **Dzienna liczba** aktywnych użytkowników przedstawia dzienną liczbę użytkowników w usługach Microsoft Edge, Starsza wersja Microsoft Edge i Internet Explorer, gdy są używane do uzyskiwania dostępu do Microsoft 365 usług. |
|4. |Wykres **Aktywni** użytkownicy przedstawia łączną liczbę użytkowników korzystających z programów Microsoft Edge, Starsza wersja Microsoft Edge i Internet Explorer, którzy korzystali z usług Microsoft 365 w wybranym okresie. |
|5. |W tabeli przedstawiono zestawienie danych na poziomie poszczególnych użytkowników. Możesz dodać lub usunąć kolumny z tabeli.  <br/><br/>**Nazwa** użytkownika to adres e-mail użytkownika, który łączył się z Microsoft 365 usług przy użyciu przeglądarek firmy Microsoft.<br><br/>**Użyty Microsoft Edge** wyświetla znacznik osi, jeśli użytkownik Microsoft Edge do łączenia się z Microsoft 365 usługami.<br/><br/>**Pole Starsza wersja Microsoft Edge** wyświetla znacznik osi, jeśli użytkownik Starsza wersja Microsoft Edge się z Microsoft 365 usługami.<br/><br/>**Używany program Internet Explorer** wyświetla znacznik wyboru, jeśli użytkownik łączył się z Microsoft 365 Internet Explorer. |
|6. |Wybierz **ikonę Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.|
|7. |Dane raportu można również wyeksportować do pliku Excel .csv, wybierając link **Eksportuj**. Umożliwia to wyeksportowanie danych wszystkich użytkowników oraz umożliwia proste agregacje, sortowanie i filtrowanie w celu dalszej analizy. Jeśli masz mniej niż 100 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 100 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane.|
