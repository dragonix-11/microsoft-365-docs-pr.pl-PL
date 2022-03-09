---
title: centrum administracyjne platformy Microsoft 365 raportów o użyciu skrzynki pocztowej
ms.author: kwekua
author: kwekua
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
ms.assetid: beffbe01-ce2d-4614-9ae5-7898868e2729
description: Dowiedz się, jak uzyskać raport użycia skrzynki pocztowej o działaniach użytkowników ze skrzynką pocztową użytkownika.
ms.openlocfilehash: 6a28b6aed8721872a31af57d4c00cd82a89c06bc
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2022
ms.locfileid: "63400898"
---
# <a name="microsoft-365-reports-in-the-admin-center---mailbox-usage"></a>Microsoft 365 w centrum administracyjnym — Użycie skrzynki pocztowej

Raport **Użycie** skrzynki pocztowej zawiera informacje o użytkownikach ze skrzynką pocztową użytkownika oraz o poziomie aktywności każdego użytkownika na podstawie wiadomości e-mail przesyłanych, odczytywanych, tworzyć terminy, wysyłać, akceptować, odrzucać spotkania i anulować aktywność spotkania. Można w nim również znaleźć informacje o tym, ile miejsca do magazynowania zużywa każda skrzynka pocztowa użytkownika i ile z nich zbliża się do limitu przydziału magazynowania. 
 
## <a name="how-to-get-to-the-mailbox-usage-report"></a>Jak przejść do raportu o użyciu skrzynki pocztowej

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>.
2. Wybierz pozycję **Wyświetl więcej w** obszarze **Aktywność poczty e-mail**. 
3. Z listy **rozwijanej** Aktywność poczty e-mail **wybierz pozycję Exchange** \> **skrzynki pocztowej**.

## <a name="interpret-the-mailbox-usage-report"></a>Interpretowanie raportu o użyciu skrzynki pocztowej

Możesz zapoznać się z raportem **Użycie skrzynki pocztowej** w organizacji, oglądając wykresy **Skrzynka pocztowa**, **Magazyn** i **Przydział**.
  
:::image type="content" alt-text="Raport użycia skrzynki pocztowej." source="../../media/9f610e91-cbc1-4e59-b824-7b1ddd84b738.png" lightbox="../../media/9f610e91-cbc1-4e59-b824-7b1ddd84b738.png":::

|Element|Opis|
|:-----|:-----|
|1.  |W raporcie **Użycie skrzynki pocztowej** można przeglądać trendy z ostatnich 7, 30, 90 lub 180 dni. Jeśli jednak wybierzesz określony dzień w raporcie, tabela będzie zawierała dane dla do 28 dni od bieżącej daty (nie daty wygenerowania raportu). |
|2.  |Dane w poszczególnych raportach zazwyczaj obejmują od 24 do 48 godzin. |
|3.  |Wykres Skrzynka pocztowa przedstawia łączną liczbę skrzynek pocztowych użytkowników w organizacji oraz łączną liczbę skrzynek, które są aktywne danego dnia okresu raportowania. Skrzynka pocztowa użytkownika jest uznawana za aktywną, jeśli przy użyciu tej skrzynki nastąpiło wysłanie lub przeczytanie wiadomości e-mail, utworzenie terminu, wysłanie, zaakceptowanie lub odrzucenie zaproszenia na spotkanie albo odwołanie spotkania. |
|4.  |Wykres **Magazyn** przedstawia ilość miejsca do magazynowania używaną w organizacji. Storage Wykres nie zawiera archiwalnych skrzynek pocztowych. Aby uzyskać więcej informacji na temat automatycznego rozszerzania archiwizacji, zobacz Omówienie automatycznego rozwijania archiwizacji w [programie Microsoft 365](../../compliance/autoexpanding-archiving.md). |
|5.  | Wykres **Przydział** przedstawia liczbę skrzynek pocztowych użytkowników w poszczególnych kategoriach przydziału. Istnieją cztery kategorie przydziału:  <br/>  Dobry  liczba użytkowników, dla których ilość używanego miejsca do magazynowania jest poniżej przydziału powodującego wydanie ostrzeżenia.  <br/>  Ostrzeżenie  liczba użytkowników, dla których ilość używanego miejsca do magazynowania jest równa przydziałowi powodującemu wydanie ostrzeżenia lub przekracza go, ale jest poniżej przydziału powodującego zakazanie wysyłania.  <br/>  Nie można wysyłać  liczba użytkowników, dla których ilość używanego miejsca do magazynowania jest równa przydziałowi powodującemu zakazanie wysyłania lub przekracza go, ale jest poniżej przydziału powodującego zakazanie wysyłania/odbierania.  <br/>  Nie można wysyłać/odbierać  liczba użytkowników, dla których ilość używanego miejsca do magazynowania jest równa przydziałowi powodującemu zakazanie wysyłania/odbierania lub przewyższa go. |
|6.  | Na wykresie **Skrzynka pocztowa** oś Y przedstawia liczbę skrzynek pocztowych użytkowników.  <br/>  Na wykresie **Magazyn** oś Y przedstawia ilość miejsca do magazynowania zajętą przez skrzynki pocztowe użytkowników w organizacji.  <br/>  Na wykresie **Przydział** oś Y przedstawia liczbę skrzynek pocztowych użytkowników w poszczególnych przydziałach magazynowania.  <br/>  Oś X na wykresach Skrzynka pocztowa i Magazyn przedstawia wybrany w raporcie przedział czasu.  <br/>  Oś X na wykresie Przydział przedstawia kategorię przydziału. |
|7.  |Wykresy można filtrować, zaznaczając je w legendzie. |
|8.  | W tabeli przedstawiono zestawienie użycia skrzynki pocztowej na poziomie poszczególnych użytkowników. Możesz dodawać do tabeli dodatkowe kolumny.  <br/> **Nazwa użytkownika** to adres e-mail użytkownika.  <br/> **Nazwa wyświetlana** to pełna nazwa lub imię i nazwisko użytkownika.  <br/> Stan **Usunięte** oznacza skrzynkę pocztową, która obecnie jest już usunięta, ale była aktywna przez jakąś część okresu raportowania dla tego raportu.  <br/> **Data usunięcia** to data usunięcia skrzynki pocztowej.  <br/> **Data utworzenia** to data utworzenia skrzynki pocztowej.  <br/> **Data ostatniej aktywności** odwołuje się do daty, kiedy przy użyciu tej skrzynki nastąpiło wysłanie lub przeczytanie wiadomości e-mail.  <br/> **Liczba elementów** to całkowita liczba elementów w skrzynce pocztowej.  <br/> **Używana przestrzeń dyskowa (MB)** to całkowita ilość używanego miejsca do magazynowania.  <br/> **Liczba elementów usuniętych** oznacza łączną liczbę elementów usuniętych w skrzynce pocztowej. <br/> **Usunięte elementy o rozmiarze (MB)** to całkowity rozmiar wszystkich elementów usuniętych w skrzynce pocztowej. <br/> **Generuj ostrzeżenie  przydział (MB)** oznacza limit miejsca do magazynowania, po osiągnięciu którego właściciel skrzynki pocztowej otrzyma ostrzeżenie, że niedługo wykorzysta przydział magazynowania.  <br/> **Zabroń wysyłania  przydział (MB)** oznacza limit miejsca do magazynowania, po osiągnięciu którego ze skrzynki pocztowej nie można już wysyłać wiadomości e-mail.  <br/> **Limit przydziału dla blokady wysyłania/odbierania (MB)** oznacza limit miejsca do magazynowania, po osiągnięciu którego skrzynka pocztowa nie będzie już mogła wysyłać ani odbierać wiadomości e-mail.  <br/> **Przydział elementów odzyskiwalnych (MB)** to limit miejsca do magazynowania dla elementów odzyskiwalnych (usuniętych) w skrzynce pocztowej, gdy skrzynka pocztowa nie może już usuwać wiadomości e-mail.  <br/> **Pokazuje, czy** skrzynka pocztowa ma włączone archiwum online.  <br/>  Jeśli zasady organizacji nie pozwalają na wyświetlanie raportów zawierających identyfikowalne dane użytkowników, możesz zmienić ustawienie prywatności dla wszystkich tych raportów. Zobacz **sekcję Ukrywanie szczegółów użytkowników w raportach** w sekcji [Raporty aktywności w centrum administracyjne platformy Microsoft 365](activity-reports.md). |
|9.  |Wybierz **pozycję Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.  <br/> :::image type="content" alt-text="Raport użycia skrzynki pocztowej — wybieranie kolumn." source="../../media/ea3d0b18-6ac6-41b0-9bb9-4844f040ea75.png":::|
|10. |Dane raportu można również wyeksportować do pliku Excel .csv, wybierając link **Eksportuj**. |
|||
