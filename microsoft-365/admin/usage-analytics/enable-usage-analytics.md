---
title: Włączanie analizy użycia platformy Microsoft 365
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9db96e9f-a622-4d5d-b134-09dcace55b6a
description: Dowiedz się, jak rozpocząć zbieranie danych dla dzierżawy przy użyciu aplikacji szablonu Microsoft 365 Usage Analytics w Power BI.
ms.openlocfilehash: cc2b74696dbdab416493be1909f1781b31f201a6
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64946951"
---
# <a name="enable-microsoft-365-usage-analytics"></a>Włączanie analizy użycia platformy Microsoft 365

Aby włączyć analizę użycia Microsoft 365 w dzierżawie Microsoft 365 us Government Community Cloud (GCC), zobacz [Połączenie, aby Microsoft 365 Government Community Cloud (GCC) danych za pomocą analizy użycia](connect-to-gcc-data-with-usage-analytics.md).

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby rozpocząć pracę z Microsoft 365 analizy użycia, musisz najpierw udostępnić dane w <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a>, a następnie zainicjować aplikację szablonu w Power BI.

## <a name="get-power-bi"></a>Uzyskiwanie usługi Power BI

Jeśli nie masz jeszcze Power BI, możesz [zarejestrować się w celu Power BI Pro](https://go.microsoft.com/fwlink/p/?linkid=845347). Wybierz pozycję **Wypróbuj bezpłatnie**, aby utworzyć konto próbne, lub **Kup teraz**, aby uzyskać Power BI Pro.


Możesz też rozwinąć sekcję **Produkty**, aby kupić inną wersję usługi Power BI.

> [!NOTE]
> Potrzebujesz licencji Power BI Pro, aby zainstalować, dostosować i rozpowszechnić aplikację szablonu. Aby uzyskać więcej informacji, zobacz [Wymagania wstępne](/power-bi/service-template-apps-install-distribute?source=docs#prerequisites).

Aby udostępnić dane, zarówno Ty, jak i osoby, które udostępniasz dane, potrzebujesz licencji Power BI Pro lub zawartość musi znajdować się w obszarze roboczym w [usłudze Power BI Premium](/power-bi/service-premium-what-is).

## <a name="enable-the-template-app"></a>Włączanie aplikacji szablonu

Aby włączyć aplikację szablonu, musisz być **administrator globalny**.

Aby uzyskać więcej informacji, zobacz [informacje o rolach administratora](../add-users/about-admin-roles.md) .

1. W centrum administracyjnym przejdź do karty **Usługi** **ustawień** \> **organizacji** \> Ustawienia.

2. Na karcie **Usługi** wybierz pozycję  **Raporty**.

3. Na panelu Raporty, który zostanie otwarty, ustaw pozycję **Udostępnij dane raportu, aby Microsoft 365 analizę użycia dla Power BI** **na wartość Przy zapisywaniu**\>.

Proces zbierania danych zakończy się w ciągu dwóch do 48 godzin w zależności od rozmiaru dzierżawy. Przycisk **Przejdź do usługi Power BI** zostanie włączony (nie będzie już szary) po zakończeniu gromadzenia danych. Po zakończeniu aplikacja udostępnia historyczne dane użycia na poziomie organizacji. 

> [!NOTE]
> Dane na karcie **"Aktywność użytkownika"** są odświeżane dopiero po piętnastym dniu bieżącego miesiąca i pierwszym dniu następnego miesiąca, więc początkowo pozostaną puste do momentu ukończenia pierwszego odświeżania.

## <a name="start-the-template-app"></a>Uruchamianie aplikacji szablonu

Aby uruchomić aplikację szablonu, musisz być **administratorem globalnym**, **czytelnikiem raportów**, **administratorem Exchange**, **administratorem Skype dla firm** lub **administratorem SharePoint**.

1. Skopiuj identyfikator dzierżawy i wybierz pozycję **Przejdź do Power BI**.

2. Po przejściu do usługi Power BI zaloguj się. Następnie **wybierz pozycję** **AplikacjePobierz**-> aplikacje z menu nawigacji.

3. Na karcie **Aplikacje** w polu wyszukiwania wpisz „Microsoft 365" i wybierz pozycję **analiza użycia platformy Microsoft 365** \> **Pobierz teraz**.

    [![Wybierz pozycję Pobierz teraz.](../../media/78102250-9874-4a32-8365-436f13560b52.png)](https://app.powerbi.com/groups/me/getapps/services/cia_microsoft365.microsoft-365-usage-analytics)

4. Po zainstalowaniu aplikacji. Wybierz kafelek, aby go otworzyć.

5. Wybierz pozycję **Eksploruj aplikację** , aby wyświetlić aplikację z przykładowymi danymi. Wybierz **Połączenie**, aby połączyć aplikację z danymi organizacji.

6. Wybierz **pozycję Połączenie** na **ekranie Połączenie, aby Microsoft 365 analizy użycia**, a następnie wpisz identyfikator dzierżawy (bez kresek) skopiowany w kroku (1), a następnie wybierz pozycję **Dalej**.

7. Na następnym ekranie wybierz pozycję **OAuth2** jako **metodę** \> uwierzytelniania **Zaloguj**. Jeśli wybierzesz inną metodę uwierzytelniania, połączenie z aplikacją szablonu zakończy się niepowodzeniem.

    ![Wybierz konto Microsoft jako metodę uwierzytelniania.](../../media/ab6f0463-c3f7-4088-a605-67c699fa86adnew.png)

8. Po utworzeniu wystąpienia aplikacji szablonu pulpit nawigacyjny analizy użycia Microsoft 365 będzie dostępny w Power BI w Internecie. Pierwsze ładowanie pulpitu nawigacyjnego może potrwać od 2 do 30 minut.

Agregacje na poziomie dzierżawy będą dostępne we wszystkich raportach po zalogowaniu się. **Szczegóły na poziomie użytkownika będą dostępne dopiero po 5. dniu następnego miesiąca kalendarzowego po wybraniu** opcji. Będzie to miało wpływ na wszystkie raporty w obszarze Aktywność użytkownika (zobacz [Nawigacja i używanie raportów w Microsoft 365 analizy użycia](navigate-and-utilize-reports.md), aby uzyskać wskazówki dotyczące wyświetlania tych raportów i korzystania z nich.

## <a name="make-the-collected-data-anonymous"></a>Ustawianie zbieranych danych jako anonimowych

Raporty zawierają informacje o danych użycia organizacji. Domyślnie raporty wyświetlają informacje o identyfikowalnych nazwach użytkowników, grup i witryn. Od 1 września 2021 r. domyślnie ukrywamy informacje o użytkownikach dla wszystkich raportów w ramach naszego stałego zobowiązania, aby pomóc firmom w obsłudze lokalnych przepisów dotyczących prywatności.
  
Administratorzy globalni mogą cofnąć tę zmianę dla swojej dzierżawy i wyświetlać identyfikowalne informacje o użytkownikach, jeśli zezwalają na to ich praktyki ochrony prywatności w organizacji. Można to osiągnąć w centrum administracyjnym platformy Microsoft 365, wykonując następujące kroki:
  
1. W centrum administracyjnym przejdź do strony **Ustawienia** \> **Ustawienia organizacji** \> **Usługi**.

2. Wybierz pozycję **Raporty**. 
  
3. Usuń zaznaczenie instrukcji **We wszystkich raportach wyświetl zdeidentyfikowane nazwy użytkowników, grup i witryn,** a następnie zapisz zmiany.  
  
Wprowadzenie tych zmian zajmie kilka minut. Wyświetlanie identyfikowalnych informacji o użytkowniku jest zarejestrowanym zdarzeniem w dzienniku inspekcji portalu zgodności usługi Microsoft Purview.   

## <a name="related-content"></a>Zawartość pokrewna

[Informacje o analizie użycia](usage-analytics.md) (artykuł)\
[Pobierz najnowszą wersję analizy użycia](get-the-latest-version-of-usage-analytics.md) (artykuł)\
[Nawigowanie po raportach i korzystanie z nich w Microsoft 365 analizy użycia](navigate-and-utilize-reports.md) (artykuł)
