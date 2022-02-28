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
description: Dowiedz się, jak za pomocą raportu uściślić domyślne zasady ochrony przed utratą danych (DLP) organizacji.
ms.openlocfilehash: 0e63648f78fd5adf2b0a354fa1a26abae4561ba8
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987777"
---
# <a name="get-started-with-the-default-dlp-policy"></a>Wprowadzenie do domyślnych zasad DLP

Zanim utworzysz już pierwszą politykę ochrony przed utratą danych (DLP, Data Loss Prevention), ochrona przed utratą danych pomaga chronić Poufne informacje przy użyciu zasad domyślnych. Te zasady domyślne i ich zalecenia (przedstawione poniżej) ułatwiają zabezpieczanie poufnej zawartości, informując Cię o tym, gdy wiadomości e-mail lub dokumenty zawierające numer karty kredytowej zostały udostępnione osobie spoza Twojej organizacji. Na stronie głównej Centrum  &amp; zgodności zabezpieczeń zobaczysz to zalecenie. 
  
Za pomocą tego widżetu możesz szybko sprawdzić, kiedy i ile informacji poufnych zostało udostępnionych, a następnie uściślić domyślne zasady DLP za pomocą jednego lub dwóch kliknięcia. Domyślne zasady DLP można także edytować w dowolnym momencie, ponieważ można je w pełni dostosować. Zwróć uwagę, że jeśli na początku nie widzisz zalecenia, kliknij pozycję **+Więcej** u dołu sekcji **Polecane dla** Ciebie. 
  
![Widżet o nazwie Dalsza ochrona udostępnianej zawartości.](../media/2bae6dbc-cc92-4f35-b54c-c36e60226b5b.png)
  
## <a name="view-the-report-and-refine-the-default-dlp-policy"></a>Wyświetlanie raportu i uściślij domyślne zasady DLP

Gdy widżet pokazuje, że użytkownicy udostępniali poufne informacje osobom spoza organizacji, wybierz pozycję **Uściślij zasady DLP** u dołu. 
  
Raport szczegółowy zawiera informacje o tym, kiedy i ile zawartości zawierającej numery kart kredytowych udostępniono w ciągu ostatnich 30 dni. Pamiętaj, że wyświetlanie dopasowania reguł w widżecie może potrwać do 48 godzin.
  
Aby chronić informacje poufne, domyślne zasady DLP:
  
- Wykrywa, czy zawartość w Exchange, SharePoint i w OneDrive zawierająca co najmniej jeden numer karty kredytowej jest udostępniana osobom spoza organizacji.
    
- Wyświetla poradę o zasadach i wysyła do użytkowników wiadomość e-mail z powiadomieniem, gdy próbują udostępnić te informacje poufne osobom spoza organizacji. Aby uzyskać więcej informacji o tych opcjach, zobacz Wysyłanie [powiadomień e-mail i wyświetlanie porad dotyczących zasad DLP](use-notifications-and-policy-tips.md).
    
- Generuje szczegółowe raporty aktywności, aby śledzić na przykład osoby, które udostępniły zawartość osobom spoza organizacji, i kiedy to zrobiły. Aby wyświetlić te informacje, możesz użyć raportów [funkcji DLP](view-the-dlp-reports.md) i danych [dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md) (gdzie **activityDLP** = ).
    
Aby szybko uściślić domyślne zasady DLP, możesz wybrać jedną z tych opcji:
  
- Wyślij do Ciebie wiadomość e-mail z raportem o zdarzeniu, gdy użytkownicy będą udostępniać te poufne informacje osobom spoza organizacji.
    
- Dodaj innych użytkowników do raportu o zdarzeniu poczty e-mail.
    
- Zablokuj dostęp do zawartości zawierającej informacje poufne, ale zezwalaj użytkownikowi na zastępowanie i udostępnianie lub wysyłanie w razie potrzeby.
    
Aby uzyskać więcej informacji na temat raportów zdarzeń lub ograniczeń dostępu, zobacz Informacje [dotyczące ochrony przed utratą danych](data-loss-prevention-policies.md).
  
Jeśli chcesz później zmienić te opcje, możesz w dowolnym momencie edytować domyślne zasady DLP — zobacz następną sekcję.
  
![Ustawienia widżetu o nazwie Dalsza ochrona udostępnianej zawartości.](../media/dad30a84-2715-4c0a-a5c5-44d85492363e.png)
  
## <a name="edit-the-default-dlp-policy"></a>Edytowanie domyślnych zasad DLP

Te zasady mają nazwę **Domyślne zasady DLP i** są wyświetlane w obszarze Ochrona przed **utratą** **danych na stronie** Zasady w Centrum &amp; zgodności zabezpieczeń. 
  
Te zasady można w pełni dostosowywać, tak samo jak wszelkie zasady DLP, które tworzysz samodzielnie od podstaw. Możesz również wyłączyć lub usunąć zasady, aby twoi użytkownicy nie osyłali już porad dotyczących zasad ani powiadomień e-mail.
  
![Zasady DLP o nazwie Domyślne zasady DLP.](../media/260731e8-4d57-4c98-abec-07b052ec48d5.png)
  
## <a name="when-the-widget-does-and-does-not-appear"></a>Gdy widżet jest wyświetlany i nie jest wyświetlany

Widżet o nazwie **Dalsza ochrona udostępnianej** zawartości jest wyświetlany w **sekcji Polecane** dla **Ciebie na stronie** głównej Centrum &amp; zgodności zabezpieczeń. 
  
Ten widżet jest wyświetlany tylko w przypadku:
  
- Centrum zgodności zabezpieczeń &amp; ani centrum administracyjne firmy Exchange nie mają żadnych zasad ochrony przed utratą danych. Ten widżet ma ułatwić Ci rozpoczynanie pracy z zasadami DLP, dlatego nie jest wyświetlany, jeśli masz już zasady DLP.
    
- Zawartość zawierająca co najmniej jedną kartę kredytową została udostępniona osobie spoza Twojej organizacji w ciągu ostatnich 30 dni.
    
Pamiętaj, że dostęp do dopasowania reguł może potrwać do 48 godzin, więc po wykryciu poufnych informacji udostępnionych zewnętrznie może upłynie do dwóch dni, aż pojawi się zalecenie.
  
Na koniec, po użyciu widżetu do uściśnięcia domyślnych zasad DLP widżet zniknie ze strony **głównej** . 
  

