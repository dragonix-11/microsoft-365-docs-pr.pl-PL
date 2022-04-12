---
title: Centrum administracyjne platformy Microsoft 365 Teams raporty aktywności użycia
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Dowiedz się, jak uzyskać raport aktywności użycia Microsoft Teams i uzyskać wgląd w działania Teams w organizacji.
ms.openlocfilehash: 93bcb5d1e6c8d0e3bbb96671333bff1c6b7b429f
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781695"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-usage-activity"></a>Microsoft 365 Raporty w centrum administracyjnym — działanie użycia Microsoft Teams

Na pulpicie nawigacyjnym raportów Microsoft 365 przedstawiono omówienie działań w produktach w organizacji. Przechodząc do poziomu raportów dotyczących poszczególnych produktów, możesz uzyskać bardziej szczegółowe informacje o aktywności w poszczególnych produktach. Zobacz [temat zawierający omówienie pulpitu nawigacyjnego Raporty](activity-reports.md).

Zupełnie nowy **raport użycia Teams** zawiera omówienie aktywności użycia w Teams, w tym liczbę aktywnych użytkowników, kanałów i komunikatów, dzięki czemu można szybko zobaczyć, ilu użytkowników w organizacji używa Teams do komunikowania się i współpracy.  Obejmuje ona również inne Teams konkretne działania, takie jak liczba aktywnych gości, spotkania i wiadomości.

![raporty Microsoft 365 — raport aktywności Microsoft Teams.](../../media/teams-usage.png)

## <a name="how-to-get-to-the-microsoft-teams-usage-activity-report"></a>Jak uzyskać dostęp do raportu aktywności użycia Microsoft Teams

1. W centrum administracyjnym przejdź do strony **Raporty** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Użycie</a>.
2. Na stronie głównej pulpitu nawigacyjnego kliknij przycisk **Wyświetl więcej** na karcie **aktywności Microsoft Teams**.

   ![Microsoft 365 raporty — karta aktywności Microsoft Teams.](../../media/teams-usage-card.png)<br/>

3. Na stronie **raportów Microsoft Teams** wybierz kartę **Teams Użycie**.

## <a name="interpret-the-microsoft-teams-usage-activity-report"></a>Interpretowanie raportu aktywności użycia Microsoft Teams

Możesz wyświetlić działanie użytkownika w raporcie Teams, wybierając kartę **Teams Użycie**. Spowoduje to wyświetlenie następujących wykresów:

- **Użycie kanału**: śledzi liczbę zastosowań kanału według typu działania w czasie.

  ![Teams raport aktywności użycia — użycie kanału.](../../media/teams-usage-channel.png)

- **Użycie zespołu**: śledzi liczbę zespołów według typu i aktywności w czasie.

  ![Teams raport aktywności użycia — użycie zespołu.](../../media/teams-usage-usage.png)

Ponadto wykres zawiera szczegóły użycia poszczególnych zespołów, takie jak data ostatniego działania, aktywni użytkownicy, aktywne kanały i inne dane.

![Microsoft 365 raporty — tabela działań użycia Microsoft Teams.](../../media/teams-usage-table.png)

W tabeli wybierz pozycję **Wybierz kolumny** , aby dodać lub usunąć kolumny z raportu.

![Teams raport aktywności użycia — wybierz kolumny.](../../media/teams-usage-columns.png)

Możesz również wyeksportować dane raportu do pliku Excel .csv, wybierając link **Eksportuj**. Powoduje to wyeksportowanie danych wszystkich użytkowników oraz umożliwia wykonywanie prostego sortowania i filtrowania w celu dalszej analizy. Jeśli masz mniej niż 2000 użytkowników, możesz sortować i filtrować dane wewnątrz tabeli raportu. Jeśli masz więcej niż 2000 użytkowników, w celu filtrowania i sortowania należy wyeksportować dane. Wyeksportowany format **czasu audio**, **czasu wideo** i **czasu udostępniania ekranu** jest zgodny z formatem czasu trwania ISO8601.

Raport **aktywności użycia Microsoft Teams** można wyświetlić dla trendów z ostatnich 7 dni, 30 dni, 90 dni lub 180 dni. Jeśli jednak wybierzesz konkretny dzień w raporcie, w tabeli będą wyświetlane dane przez maksymalnie 28 dni od bieżącej daty (a nie daty wygenerowania raportu).

Aby zapewnić jakość danych, przeprowadzamy codzienne sprawdzanie poprawności danych w ciągu ostatnich trzech dni i będziemy wypełniać wszelkie wykryte luki. Podczas tego procesu można zauważyć różnice w danych historycznych.

> [!Important]
> Dane dla danego dnia zostaną wyświetlone w ciągu 48 godzin. Na przykład dane z 10 stycznia powinny zostać wyświetlone w raporcie do 12 stycznia.

### <a name="channel-usage-metrics"></a>Metryki użycia kanału

Na wykresie użycia kanału są wyświetlane dane dotyczące następujących metryk.

|Element|Opis|
|:-----|:-----|
|**Metrycznych**|**Definicja**|
|Aktywni użytkownicy kanału|Jest to suma aktywnych użytkowników wewnętrznych, aktywnych gości i aktywnych użytkowników zewnętrznych.  <br/><br/> **Aktywni użytkownicy wewnętrzni** — użytkownicy, którzy mają co najmniej jedną akcję panelu w określonym przedziale czasu. Nie obejmuje to gości.   <br/> **Aktywni goście** — goście, którzy mają co najmniej jedną akcję panelu w określonym przedziale czasu. Gość to osoba spoza organizacji, która uzyskuje dostęp do udostępnionych zasobów, logując się do konta gościa w moim katalogu.  <br/> **Aktywny użytkownik zewnętrzny** — uczestnicy zewnętrzni, którzy mają co najmniej jedną akcję panelu w określonym okresie. Uczestnik zewnętrzny to osoba spoza organizacji, która uczestniczy w zasobie , takim jak kanał udostępniony, przy użyciu własnej tożsamości, a nie konta gościa w katalogu.|
|Aktywne kanały|Prawidłowe kanały w aktywnych zespołach, które mają co najmniej jednego aktywnego użytkownika w określonym okresie. Obejmuje to kanały publiczne, prywatne lub udostępnione.|
|Komunikaty kanału|Liczba unikatowych komunikatów, które użytkownik zamieścił na prywatnej czacie w określonym okresie.|

### <a name="team-usage-metrics"></a>Metryki użycia zespołu

Wykres użycia Teams przedstawia dane dotyczące następujących metryk.

|Element|Opis|
|:-----|:-----|
|**Metrycznych**|**Definicja**|
|Zespoły prywatne|Prywatny zespół, który jest aktywny lub nieaktywny.|
|Zespoły publiczne|Zespół publiczny, który jest aktywny lub nieaktywny.|
|Aktywne zespoły prywatne|Zespół, który jest prywatny i aktywny.|
|Aktywne zespoły publiczne|Zespół, który jest publiczny i aktywny.|

### <a name="teams-details"></a>szczegóły Teams

Dane dla następujących metryk są dostępne dla poszczególnych zespołów.

|Element|Opis|
|:-----|:-----|
|**Metrycznych**|**Definicja**|
|Identyfikator zespołu|Identyfikator zespołu|
|Aktywni użytkownicy wewnętrzni|Użytkownicy, którzy mają co najmniej jedną akcję panelu w określonym okresie, w tym gości. <br/> <br/> Użytkownicy wewnętrzni i goście, którzy znajdują się w tej samej dzierżawie. Użytkownicy wewnętrzni wykluczają gości.|
|Aktywni goście|Goście, którzy mają co najmniej jedną akcję panelu w określonym okresie. <br/> <br/> Gość jest definiowany jako osoby spoza organizacji, które uzyskują dostęp do udostępnionych zasobów, logując się do konta gościa w moim katalogu.|
|Aktywni użytkownicy zewnętrzni|Uczestnicy zewnętrzni, którzy mają co najmniej jedną akcję panelu w określonym okresie.<br/><br/> Uczestnik zewnętrzny jest definiowany jako osoba spoza organizacji, która uczestniczy w zasobie , takim jak kanał udostępniony, przy użyciu własnej tożsamości, a nie konta gościa w katalogu.|
|Aktywne kanały|Prawidłowe kanały w aktywnych zespołach, które mają co najmniej jednego aktywnego użytkownika w określonym okresie. Obejmuje to kanały publiczne, prywatne lub udostępnione.|
|Aktywne kanały udostępnione|Prawidłowe kanały udostępnione w aktywnych zespołach, które mają co najmniej jednego aktywnego użytkownika w określonym czasie. <br/> <br/>Kanał udostępniony jest definiowany jako kanał Teams, który można udostępniać osobom spoza zespołu. Te osoby mogą znajdować się w Organizacji lub innych organizacjach usługi Azure AD.|
|Łączna liczba zorganizowanych spotkań|Suma jednorazowych zaplanowanych, cyklicznych, ad hoc i niesklasyfikowanych spotkań zorganizowanych przez użytkownika w określonym okresie.|
|Posty|Liczba wszystkich komunikatów postów w kanałach w określonym okresie.|
|Odpowiedzi|Liczba wszystkich wiadomości odpowiedzi w kanałach w określonym okresie.|
|Wspomina|Liczba wszystkich wzmianek dokonanych w określonym okresie.|
|Reakcje|Liczba reakcji aktywnego użytkownika wykonanych w określonym okresie.|
|Pilne komunikaty|Liczba pilnych komunikatów w określonym okresie.|
|Komunikaty kanału|Liczba unikatowych komunikatów, które użytkownik zamieścił na czacie zespołowym w określonym okresie.|
|Data ostatniego działania|Ostatnia data zatwierdzenia akcji przez dowolnego członka zespołu.|

## <a name="make-the-user-specific-data-anonymous"></a>Anonimowość danych specyficznych dla użytkownika

Aby dane w Teams raport aktywności użytkownika były anonimowe, musisz być administratorem globalnym. Spowoduje to ukrycie możliwych do zidentyfikowania informacji (przy użyciu skrótów MD5), takich jak nazwa wyświetlana, adres e-mail i identyfikator obiektu Azure Active Directory w raporcie i ich eksport.

1. W Centrum administracyjne platformy Microsoft 365 przejdź do **Ustawienia Ustawienia** >  **Org**, a następnie w obszarze **Usługi** wybierz pozycję **Raporty**.

2. Wybierz pozycję **Raporty**, a następnie wybierz pozycję **Wyświetl identyfikatory anonimowe**. To ustawienie jest stosowane zarówno do raportów użycia w Centrum administracyjne platformy Microsoft 365, jak i w centrum administracyjnym Teams.

3. Wybierz pozycję **Zapisz zmiany**.

## <a name="see-also"></a>Zobacz też

[Microsoft Teams raport użycia urządzenia](../activity-reports/microsoft-teams-device-usage-preview.md)

[Microsoft Teams raport aktywności użytkownika](../activity-reports/microsoft-teams-user-activity-preview.md)
