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
description: Dowiedz się, jak rozpocząć zbieranie danych dotyczących dzierżawy przy użyciu Microsoft 365 szablonu analizy użycia w programie Power BI.
ms.openlocfilehash: b547acc5adf312458e82108a36bbd9c0cbf60f10
ms.sourcegitcommit: 57211e8082a3429017ad33fe0e6bd9af203bb7ab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027088"
---
# <a name="enable-microsoft-365-usage-analytics"></a>Włączanie analizy użycia platformy Microsoft 365

Aby włączyć Microsoft 365 użycia w dzierżawie usługi Microsoft 365 Government Community Cloud (GCC) w Usa, zobacz Połączenie [do Microsoft 365 Government Community Cloud (GCC) za pomocą analizy użycia](connect-to-gcc-data-with-usage-analytics.md).

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby rozpocząć analizę Microsoft 365 użycia, najpierw udostępnij dane w <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365, a</a> następnie zainicjuj aplikację szablonu w Power BI.

## <a name="get-power-bi"></a>Uzyskiwanie usługi Power BI

Jeśli jeszcze tego nie masz, Power BI się w celu [Power BI Pro.](https://go.microsoft.com/fwlink/p/?linkid=845347) Wybierz **pozycję Wypróbuj bezpłatnie**, aby zapisać się na wersję próbną, lub Kup **teraz**, aby uzyskać Power BI Pro.


Możesz też rozwinąć sekcję **Produkty**, aby kupić inną wersję usługi Power BI.

> [!NOTE]
> Potrzebujesz licencji Power BI Pro, aby zainstalować, dostosować i rozpowszechnić aplikację szablonów. Aby uzyskać więcej informacji, zobacz [Wymagania wstępne](/power-bi/service-template-apps-install-distribute?source=docs#prerequisites).

Aby udostępnić dane, ty i osoby, którym udostępniasz dane, potrzebujecie licencji usługi Power BI Pro lub zawartości muszą się znaleźć w obszarze roboczym w usłudze [Power BI Premium](/power-bi/service-premium-what-is).

## <a name="enable-the-template-app"></a>Włączanie aplikacji szablonów

Aby włączyć aplikację szablonu, musisz być **administratorem globalnym**.

Aby [uzyskać więcej informacji, zobacz](../add-users/about-admin-roles.md) Role administratora.

1. W centrum administracyjnym przejdź do karty Ustawienia  \> **ustawienia organizacji** \> **.**

2. Na karcie **Usługi** wybierz pozycję  **Raporty**.

3. W panelu Raporty, który zostanie otwarty, ustaw opcję Udostępnij dane raportu w **celu Microsoft 365 analizy** użycia dla Power BI **na pozycję Przy** \> **zapisywach**.

Proces zbierania danych zostanie ukończony w dwie do 48 godzin w zależności od rozmiaru Dzierżawy. Przycisk **Przejdź do usługi Power BI** zostanie włączony (nie będzie już szary) po zakończeniu gromadzenia danych. Po zakończeniu aplikacja udostępnia historyczne dane użycia na poziomie organizacji. 

> [!NOTE]
> Dane dla karty **"Działania użytkowników"** są odświeżane dopiero po piętnastym dniu bieżącego miesiąca i pierwszego dnia następnego miesiąca, więc pozostaną początkowo puste do czasu ukończenia pierwszego odświeżania.

## <a name="start-the-template-app"></a>Uruchamianie aplikacji szablonów

Aby uruchomić aplikację szablonu, musisz być **administratorem** **globalnym,** czytelnikiem **raportów,** administratorem Exchange, administratorem Skype dla firm **administratorem** lub **SharePoint administratorem**.

1. Skopiuj identyfikator dzierżawy i wybierz **pozycję Przejdź do Power BI**.

2. Po przejściu do usługi Power BI zaloguj się. Następnie **wybierz pozycję** **AplikacjeUzyskaj**-> aplikacje z menu nawigacji.

3. Na karcie **Aplikacje** w polu wyszukiwania wpisz „Microsoft 365" i wybierz pozycję **analiza użycia platformy Microsoft 365** \> **Pobierz teraz**.

    [![Wybierz pozycję Pobierz teraz.](../../media/78102250-9874-4a32-8365-436f13560b52.png)](https://app.powerbi.com/groups/me/getapps/services/cia_microsoft365.microsoft-365-usage-analytics)

4. Po zainstalowaniu aplikacji. Wybierz kafelek, aby go otworzyć.

5. Wybierz **pozycję Eksploruj** aplikację, aby wyświetlić aplikację z przykładami danych. Wybierz **Połączenie**, aby połączyć aplikację z danymi Twojej organizacji.

6. Wybierz **Połączenie**, na ekranie Połączenie do analizy użycia Microsoft 365 następnie wpisz identyfikator dzierżawy (bez kresek) skopiowany w kroku (1), **a** następnie wybierz pozycję **Dalej**.

7. Na następnym ekranie wybierz pozycję **OAuth2** jako metodę **logowania** \> **uwierzytelniania**. W przypadku wybrania innej metody uwierzytelniania połączenie z aplikacją szablonu nie powiedzie się.

    ![Wybierz konto Microsoft jako metodę uwierzytelniania.](../../media/ab6f0463-c3f7-4088-a605-67c699fa86adnew.png)

8. Po wystąpienia aplikacji szablonu pulpit nawigacyjny analizy Microsoft 365 będzie dostępny w Power BI w sieci Web. Pierwsze ładowanie pulpitu nawigacyjnego może potrwać od 2 do 30 minut.

Wartości zagregowane na poziomie dzierżawy będą dostępne we wszystkich raportach po ich wybraniu. **Szczegóły na poziomie użytkownika będą dostępne tylko w ciągu 5. dnia następnego miesiąca kalendarzowego po ich wybraniu**. Ma to wpływ na wszystkie raporty w obszarze Aktywność użytkowników (zobacz Nawigowanie po raportach i korzystanie z nich w p Microsoft 365 [analizy](navigate-and-utilize-reports.md) użycia, aby uzyskać porady dotyczące wyświetlania i używania tych raportów).

## <a name="make-the-collected-data-anonymous"></a>Ustawianie zbieranych danych jako anonimowych

Raporty zawierają informacje na temat danych dotyczących użycia w organizacji. Domyślnie w raportach są wyświetlane informacje umożliwiające identyfikację nazw użytkowników, grup i witryn. Począwszy od 1 września 2021 r., wszystkie raporty domyślnie ukrywają informacje o użytkownikach w ramach naszego bieżącego zobowiązania do pomagania firmom w ochronie prywatności w ich lokalnych działaniach.
  
Administratorzy globalni mogą przywrócić tę zmianę w dzierżawie i pokazać identyfikowalne dane użytkowników, jeśli pozwalają na to zasady zachowania poufności informacji ich organizacji. Można to osiągnąć w centrum administracyjne platformy Microsoft 365, korzystając z następujących kroków:
  
1. W centrum administracyjnym przejdź do strony centrum **Ustawienia** \> **organizacji Ustawienia** \> **usługi.**

2. Wybierz pozycję **Raporty**. 
  
3. Usuń zaznaczenie instrukcji **We wszystkich raportach wyświetl odznaczone nazwy użytkowników, grup** i witryn, a następnie zapisz zmiany.  
  
Może potrwać kilka minut, aby te zmiany obowiązywały. Pokazywanie identyfikowalnych informacji użytkownika to zarejestrowane zdarzenie w Centrum zgodności platformy Microsoft 365 inspekcji.   

## <a name="related-content"></a>Zawartość pokrewna

[Analiza użycia (](usage-analytics.md) artykuł)\
[Uzyskiwanie najnowszej wersji analizy użycia](get-the-latest-version-of-usage-analytics.md) (artykuł)\
[Nawigowanie po raportach i korzystanie Microsoft 365 analizy](navigate-and-utilize-reports.md) użycia (artykuł)
