---
title: Wprowadzenie do domyślnych zasad DLP
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: e0ada764-6422-4b44-9472-513bed04837b
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się, jak za pomocą raportu uściślić domyślne zasady ochrony przed utratą danych (DLP) w organizacji.
ms.openlocfilehash: 893aae6dfbc4e5c9fcf48a8eec53694352ead4f2
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753457"
---
# <a name="get-started-with-the-default-dlp-policy"></a>Wprowadzenie do domyślnych zasad DLP

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Przed utworzeniem pierwszych zasad Ochrona przed utratą danych w Microsoft Purview (DLP) DLP pomaga chronić poufne informacje przy użyciu zasad domyślnych. Te domyślne zasady i zalecenia (pokazane poniżej) pomagają chronić poufną zawartość, powiadamiając Cię o udostępnieniu wiadomości e-mail lub dokumentów zawierających numer karty kredytowej osobie spoza organizacji. To zalecenie zostanie wyświetlone na stronie **głównej** portal zgodności Microsoft Purview. 
  
Ten widżet umożliwia szybkie wyświetlanie, kiedy i ile informacji poufnych zostało udostępnionych, a następnie uściślić domyślne zasady DLP za pomocą kliknięcia lub dwóch. Domyślne zasady DLP można również edytować w dowolnym momencie, ponieważ są w pełni dostosowywalne. Pamiętaj, że jeśli na początku nie widzisz zalecenia, spróbuj kliknąć pozycję **+Więcej** w dolnej części sekcji **Zalecane.** 
  
![Widżet o nazwie Dalej chroń udostępnioną zawartość.](../media/2bae6dbc-cc92-4f35-b54c-c36e60226b5b.png)
  
## <a name="view-the-report-and-refine-the-default-dlp-policy"></a>Wyświetlanie raportu i uściślanie domyślnych zasad DLP

Gdy widżet pokazuje, że użytkownicy udostępniali poufne informacje osobom spoza organizacji, wybierz pozycję **Uściślij zasady DLP** u dołu. 
  
Szczegółowy raport pokazuje, kiedy i ile zawartości zawierającej numery kart kredytowych zostało udostępnione w ciągu ostatnich 30 dni. Pamiętaj, że wyświetlanie dopasowań reguł w widżecie może potrwać do 48 godzin.
  
Aby chronić poufne informacje, domyślne zasady DLP:
  
- Wykrywa, kiedy zawartość Exchange, SharePoint i OneDrive zawierająca co najmniej jeden numer karty kredytowej jest udostępniana osobom spoza organizacji.
    
- Przedstawia poradę dotyczącą zasad i wysyła powiadomienie e-mail do użytkowników podczas próby udostępnienia tych poufnych informacji osobom spoza organizacji. Aby uzyskać więcej informacji na temat tych opcji, zobacz [Wysyłanie powiadomień e-mail i pokaż wskazówki dotyczące zasad dotyczących zasad DLP](use-notifications-and-policy-tips.md).
    
- Generuje szczegółowe raporty aktywności, dzięki czemu można śledzić takie elementy, jak osoby spoza organizacji, które udostępniły zawartość i kiedy ją zrobiły. Aby wyświetlić te informacje, możesz użyć [raportów DLP](view-the-dlp-reports.md) i [danych dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md) (gdzie **DLP działania** = ).
    
Aby szybko uściślić domyślne zasady DLP, możesz je wybrać:
  
- Wyślij wiadomość e-mail z raportem o zdarzeniu, gdy użytkownicy udostępniają te poufne informacje osobom spoza organizacji.
    
- Dodaj innych użytkowników do raportu o zdarzeniu e-mail.
    
- Zablokuj dostęp do zawartości zawierającej informacje poufne, ale w razie potrzeby zezwalaj użytkownikowi na zastępowanie i udostępnianie lub wysyłanie.
    
Aby uzyskać więcej informacji na temat raportów o zdarzeniach lub ograniczania dostępu, zobacz [Dokumentacja dotycząca zapobiegania utracie danych](data-loss-prevention-policies.md).
  
Jeśli chcesz zmienić te opcje później, możesz w dowolnym momencie edytować domyślne zasady DLP — zobacz następną sekcję.
  
![Ustawienia dla widżetu o nazwie Dalej chroń udostępnioną zawartość.](../media/dad30a84-2715-4c0a-a5c5-44d85492363e.png)
  
## <a name="edit-the-default-dlp-policy"></a>Edytowanie domyślnych zasad DLP

Te zasady mają nazwę **Domyślne zasady DLP** i są wyświetlane w obszarze **Zapobieganie utracie danych** na stronie **Zasady** portal zgodności Microsoft Purview. 
  
Te zasady można w pełni dostosowywać, tak samo jak wszystkie zasady DLP tworzone samodzielnie od podstaw. Możesz również wyłączyć lub usunąć zasady, aby użytkownicy nie otrzymywali już wskazówek dotyczących zasad ani powiadomień e-mail.
  
![Zasady DLP o nazwie Domyślne zasady DLP.](../media/260731e8-4d57-4c98-abec-07b052ec48d5.png)
  
## <a name="when-the-widget-does-and-does-not-appear"></a>Gdy widżet jest wyświetlany i nie jest wyświetlany

Widżet o nazwie **Dalej chroń udostępnioną zawartość** zostanie wyświetlony w sekcji **Zalecane dla Ciebie** na stronie **głównej** portal zgodności Microsoft Purview. 
  
Ten widżet jest wyświetlany tylko wtedy, gdy:
  
- Brak zasad ochrony przed utratą danych w centrum administracyjnym portal zgodności Microsoft Purview lub Exchange. Ten widżet ma ułatwić rozpoczęcie pracy z DLP, więc nie jest wyświetlany, jeśli masz już zasady DLP.
    
- Zawartość zawierająca co najmniej jedną kartę kredytową została udostępniona osobie spoza organizacji w ciągu ostatnich 30 dni.
    
Pamiętaj, że dostępność dopasowań reguł może potrwać do 48 godzin, więc po wykryciu poufnych informacji udostępnionych zewnętrznie wyświetlenie zalecenia może potrwać do dwóch dni.
  
Na koniec, gdy użyjesz widżetu do uściślenia domyślnych zasad DLP, widżet zniknie ze strony **głównej** . 
  

