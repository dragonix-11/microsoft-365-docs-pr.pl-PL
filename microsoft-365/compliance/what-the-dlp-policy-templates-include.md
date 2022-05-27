---
title: Jakie szablony zasad DLP zawierają
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: reference
f1_keywords:
- ms.o365.cc.DLPNewPolicyFromTemplate
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
recommendations: false
description: Dowiedz się, jakie szablony zasad ochrony przed utratą danych (DLP) znajdują się w portal zgodności Microsoft Purview.
ms.openlocfilehash: 145f5b2a180023811afa8b5795bfa8b9d24f82f5
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753508"
---
# <a name="what-the-dlp-policy-templates-include"></a>Co obejmują szablony zasad DLP

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Ochrona przed utratą danych w Microsoft Purview (DLP) w portal zgodności Microsoft Purview zawiera gotowe do użycia szablony zasad, które spełniają typowe wymagania dotyczące zgodności, takie jak pomoc w ochronie poufnych informacji podlegających amerykańskiej ustawie o ubezpieczeniach zdrowotnych (HIPAA), USA. Gramm-Leach-Bliley Act (GLBA) lub U.S. Patriot Act. W tym artykule wymieniono wszystkie szablony zasad, typy informacji poufnych, których szukają, oraz domyślne warunki i akcje. Ten artykuł nie zawiera wszystkich szczegółów dotyczących sposobu konfigurowania poszczególnych szablonów zasad. Zamiast tego w artykule przedstawiono wystarczająco dużo informacji, które pomogą Ci zdecydować, który szablon jest najlepszym punktem wyjścia dla danego scenariusza. Pamiętaj, że możesz dostosować te szablony zasad, aby spełniać określone wymagania.
  
## <a name="australia-financial-data"></a>Dane finansowe Australii

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Australia Financial: Skanowanie zawartości udostępnionej na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Kod SWIFT — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer pliku podatkowego Australii — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer konta bankowego w Australii — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer karty kredytowej — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Australia Financial: Skanowanie zawartości udostępnionej na zewnątrz — duża liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Kod SWIFT — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer pliku podatkowego Australii — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer konta bankowego w Australii — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer karty kredytowej — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="australia-health-records-act-hrip-act"></a>Australia Health Records Act (HRIP Act)

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Australia HRIP: Skanowanie zawartości udostępnionej na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer pliku podatkowego Australii — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer konta medycznego w Australii — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Australia HRIP: Skanowanie zawartości udostępnionej na zewnątrz — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer pliku podatkowego Australii — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer konta medycznego w Australii — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="australia-personally-identifiable-information-pii-data"></a>Dane osobowe (PII) w Australii

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Australia PII: Skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer pliku podatkowego Australii — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer australijskiego prawa jazdy — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Australia PII: Skanuj zawartość udostępnioną na zewnątrz — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer pliku podatkowego Australii — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer australijskiego prawa jazdy — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="australia-privacy-act"></a>Australia Privacy Act

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Prywatność w Australii: Skanowanie zawartości udostępnionej na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer australijskiego prawa jazdy — minimalna liczba 1, maksymalna liczba 9  <br/>  Australia Passport Number — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Prywatność w Australii: Skanuj zawartość udostępnioną na zewnątrz — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer australijskiego prawa jazdy — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer paszportu Australii — minimalna liczba 10, maksymalna liczba 500 <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="canada-financial-data"></a>Dane finansowe Kanady

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Canada Financial Data: Skanowanie zawartości udostępnionej na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer konta bankowego w Kanadzie — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Canada Financial Data: Skanowanie zawartości udostępnionej na zewnątrz — duża liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer konta bankowego w Kanadzie — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="canada-health-information-act-hia"></a>Canada Health Information Act (HIA)

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Kanada HIA: Skanowanie zawartości udostępnionej na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Kanada Numer paszportu — minimalna liczba 1, maksymalna liczba 9  <br/>  Kanada Numer ubezpieczenia społecznego - Minimalna liczba 1, Maksymalna liczba 9  <br/>  Kanada Usługa kondycji Liczba — minimalna liczba 1, maksymalna liczba 9  <br/>  Canada Personal Health Identification Number (PHIN) — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Kanada HIA: Skanowanie zawartości udostępnionej na zewnątrz — duża liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Canada Passport Number — minimalna liczba 10, maksymalna liczba 500  <br/>  Kanada Numer ubezpieczenia społecznego - Minimalna liczba 10, Maksymalna liczba 500  <br/>  Kanada Usługa kondycji Liczba — minimalna liczba 10, maksymalna liczba 500  <br/>  Canada Personal Health Identification Number (PHIN) — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="canada-personal-health-act-phipa---ontario"></a>Canada Personal Health Act (PHIPA) - Ontario

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Kanada PHIPA: Skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Kanada Numer paszportu — minimalna liczba 1, maksymalna liczba 9  <br/>  Kanada Numer ubezpieczenia społecznego - Minimalna liczba 1, Maksymalna liczba 9  <br/>  Kanada Usługa kondycji Liczba — minimalna liczba 1, maksymalna liczba 9  <br/>  Canada Personal Health Identification Number (PHIN) — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Kanada PHIPA: Skanowanie zawartości udostępnionej na zewnątrz — duża liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Canada Passport Number — minimalna liczba 10, maksymalna liczba 500  <br/>  Kanada Numer ubezpieczenia społecznego - Minimalna liczba 10, Maksymalna liczba 500  <br/>  Kanada Usługa kondycji Liczba — minimalna liczba 10, maksymalna liczba 500  <br/>  Canada Personal Health Identification Number (PHIN) — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="canada-personal-health-information-act-phia---manitoba"></a>Canada Personal Health Information Act (PHIA) - Manitoba

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Kanada PHIA: Skanowanie zawartości udostępnionej na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Kanada Numer ubezpieczenia społecznego - Minimalna liczba 1, Maksymalna liczba 9  <br/>  Kanada Usługa kondycji Liczba — minimalna liczba 1, maksymalna liczba 9  <br/>  Canada Personal Health Identification Number (PHIN) — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Kanada PHIA: Skanowanie zawartości udostępnionej na zewnątrz — duża liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Kanada Numer ubezpieczenia społecznego - Minimalna liczba 10, Maksymalna liczba 500  <br/>  Kanada Usługa kondycji Liczba — minimalna liczba 10, maksymalna liczba 500 <br/>  Canada Personal Health Identification Number (PHIN) — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="canada-personal-information-protection-act-pipa"></a>Canada Personal Information Protection Act (PIPA)

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Kanada PIPA: Skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Kanada Numer paszportu — minimalna liczba 1, maksymalna liczba 9  <br/>  Kanada Numer ubezpieczenia społecznego - Minimalna liczba 1, Maksymalna liczba 9  <br/>  Kanada Usługa kondycji Liczba — minimalna liczba 1, maksymalna liczba 9  <br/>  Canada Personal Health Identification Number (PHIN) — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Kanada PIPA: Skanuj zawartość udostępnioną na zewnątrz — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Canada Passport Number — minimalna liczba 10, maksymalna liczba 500  <br/>  Kanada Numer ubezpieczenia społecznego - Minimalna liczba 10, Maksymalna liczba 500  <br/>  Kanada Usługa kondycji Liczba — minimalna liczba 10, maksymalna liczba 500  <br/>  Canada Personal Health Identification Number (PHIN) — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="canada-personal-information-protection-act-pipeda"></a>Canada Personal Information Protection Act (PIPEDA)

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Kanada PIPEDA: Skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Kanada Numer prawa jazdy — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer konta bankowego w Kanadzie — minimalna liczba 1, maksymalna liczba 9  <br/>  Kanada Numer paszportu — minimalna liczba 1, maksymalna liczba 9  <br/>  Kanada Numer ubezpieczenia społecznego - Minimalna liczba 1, Maksymalna liczba 9  <br/>  Kanada Usługa kondycji Liczba — minimalna liczba 1, maksymalna liczba 9  <br/>  Canada Personal Health Identification Number (PHIN) — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Kanada PIPEDA: Skanuj zawartość udostępnioną na zewnątrz — duża liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Kanada Numer prawa jazdy — minimalna liczba 10, maksymalna liczba 500 <br/>  Numer konta bankowego w Kanadzie — minimalna liczba 10, maksymalna liczba 500 <br/>  Canada Passport Number — minimalna liczba 10, maksymalna liczba 500  <br/>  Kanada Numer ubezpieczenia społecznego - Minimalna liczba 10, Maksymalna liczba 500  <br/>  Kanada Usługa kondycji Liczba — minimalna liczba 10, maksymalna liczba 500  <br/>  Canada Personal Health Identification Number (PHIN) — minimalna liczba 10, maksymalna liczba 500 <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="canada-personally-identifiable-information-pii-data"></a>Dane osobowe (PII) w Kanadzie

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Canada PII: Skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Kanada Numer prawa jazdy — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer konta bankowego w Kanadzie — minimalna liczba 1, maksymalna liczba 9  <br/>  Kanada Numer paszportu — minimalna liczba 1, maksymalna liczba 9  <br/>  Kanada Numer ubezpieczenia społecznego - Minimalna liczba 1, Maksymalna liczba 9  <br/>  Kanada Usługa kondycji Liczba — minimalna liczba 1, maksymalna liczba 9  <br/>  Canada Personal Health Identification Number (PHIN) — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Canada PII: Skanuj zawartość udostępnioną na zewnątrz — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Kanada Numer prawa jazdy — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer konta bankowego w Kanadzie — minimalna liczba 10, maksymalna liczba 500  <br/>  Canada Passport Number — minimalna liczba 10, maksymalna liczba 500  <br/>  Kanada Numer ubezpieczenia społecznego - Minimalna liczba 10, Maksymalna liczba 500  <br/>  Kanada Usługa kondycji Liczba — minimalna liczba 10, maksymalna liczba 500  <br/>  Canada Personal Health Identification Number (PHIN) — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="france-data-protection-act"></a>Francuska ustawa o ochronie danych

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Francja DPA: Skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Francuska krajowa karta tożsamości (CNI) — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer ubezpieczenia społecznego We Francji (INSEE) — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Francja DPA: Skanuj zawartość udostępnioną na zewnątrz — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  France National ID Card (CNI) — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer ubezpieczenia społecznego We Francji (INSEE) — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="france-financial-data"></a>Dane finansowe Francji

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|France Financial: Skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer karty debetowej UE — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|France Financial: Skanuj zawartość udostępnioną na zewnątrz — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer karty debetowej UE — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="france-personally-identifiable-information-pii-data"></a>Dane osobowe (PII) we Francji

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|France PII: Skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer ubezpieczenia społecznego We Francji (INSEE) — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer prawa jazdy We Francji — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer paszportu Francji — minimalna liczba 1, maksymalna liczba 9  <br/>  Francuska krajowa karta tożsamości (CNI) — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|France PII: Skanuj zawartość udostępnioną na zewnątrz — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer ubezpieczenia społecznego We Francji (INSEE) — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer prawa jazdy We Francji — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer paszportu Francji — minimalna liczba 10, maksymalna liczba 500  <br/>  France National ID Card (CNI) — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="general-data-protection-regulation-gdpr"></a>Ogólne rozporządzenie o ochronie danych (RODO)

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Znaleziono zawartość wrażliwą UE o małej liczbie woluminów  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty debetowej UE — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer prawa jazdy UE — minimalna liczba 1, maksymalna liczba 9  <br/>  Krajowy numer identyfikacyjny UE — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer paszportu UE — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer ubezpieczenia społecznego UE (SSN) lub równoważny identyfikator — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer identyfikacji podatkowej UE (TIN) — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie raportów o zdarzeniach do administratora  <br/> |
|Znaleziono dużą ilość poufnych treści UE  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty debetowej UE — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer prawa jazdy UE — minimalna liczba 10, maksymalna liczba 500  <br/>  Krajowy numer identyfikacyjny UE — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer paszportu UE — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer ubezpieczenia społecznego UE (SSN) lub równoważny identyfikator — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer IDENTYFIKACJI PODATKOWEJ UE (TIN) — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Ograniczanie dostępu do zawartości dla użytkowników zewnętrznych  <br/>  Powiadamianie użytkowników za pomocą wiadomości e-mail i wskazówek dotyczących zasad  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportów o zdarzeniach do administratora  <br/> |
   
## <a name="germany-financial-data"></a>Dane finansowe Niemiec

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Dane finansowe Niemiec: Skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer karty debetowej UE — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Dane finansowe Niemiec: Skanuj zawartość udostępnioną na zewnątrz — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer karty debetowej UE — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="germany-personally-identifiable-information-pii-data"></a>Dane osobowe (PII) w Niemczech

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Niemieckie dane osobowe: Skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer niemieckiego prawa jazdy — minimalna liczba 1, maksymalna liczba 9  <br/>  Niemiecki numer paszportu — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Niemieckie dane osobowe: Skanuj zawartość udostępnioną na zewnątrz — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Niemiecki numer prawa jazdy — minimalna liczba 10, maksymalna liczba 500  <br/>  Niemiecki numer paszportu — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="israel-financial-data"></a>Dane finansowe Izraela

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Dane finansowe Izraela: Skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer konta bankowego Izraela — minimalna liczba 1, maksymalna liczba 9  <br/>  Kod SWIFT — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer karty kredytowej — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Dane finansowe Izraela: Skanuj zawartość udostępnioną na zewnątrz — duża liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer konta bankowego Izraela — minimalna liczba 10, maksymalna liczba 500  <br/>  Kod SWIFT — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer karty kredytowej — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="israel-personally-identifiable-information-pii-data"></a>Dane osobowe (PII) w Izraelu

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Israel PII: Skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Identyfikator narodowy Izraela — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Israel PII: Skanuj zawartość udostępnioną na zewnątrz — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Identyfikator narodowy Izraela — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="israel-protection-of-privacy"></a>Ochrona prywatności w Izraelu

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Prywatność Izraela: Skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Identyfikator narodowy Izraela — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer konta bankowego Izraela — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Prywatność Izraela: Skanowanie zawartości udostępnionej na zewnątrz — duża liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Identyfikator narodowy Izraela — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer konta bankowego Izraela — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="japan-financial-data"></a>Dane finansowe Japonii

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Japan Financial: Skanowanie zawartości udostępnionej na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer konta bankowego w Japonii — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer karty kredytowej — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Japan Financial: Skanowanie zawartości udostępnionej na zewnątrz — duża liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer konta bankowego w Japonii — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer karty kredytowej — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="japan-personally-identifiable-information-pii-data"></a>Dane osobowe (PII) w Japonii

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Dane osobowe Japonii: skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer rejestracji rezydenta Japonii — minimalna liczba 1, maksymalna liczba 9  <br/>  Japoński numer ubezpieczenia społecznego (SIN) — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Dane osobowe Japonii: skanowanie zawartości udostępnionej na zewnątrz — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer rejestracji rezydenta Japonii — minimalna liczba 10, maksymalna liczba 500  <br/>  Japoński numer ubezpieczenia społecznego (SIN) — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="japan-protection-of-personal-information"></a>Japonia Ochrona danych osobowych

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Japonia PPI: Skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer rejestracji rezydenta Japonii — minimalna liczba 1, maksymalna liczba 9  <br/>  Japoński numer ubezpieczenia społecznego (SIN) — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Japonia PPI: Skanuj zawartość udostępnioną na zewnątrz — duża liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer rejestracji rezydenta Japonii — minimalna liczba 10, maksymalna liczba 500  <br/>  Japoński numer ubezpieczenia społecznego (SIN) — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="pci-data-security-standard-pci-dss"></a>PCI Data Security Standard (PCI DSS)

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|PCI DSS: Skanowanie zawartości udostępnionej na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|PCI DSS: Skanowanie zawartości udostępnionej na zewnątrz — duża liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="saudi-arabia---anti-cyber-crime-law"></a>Arabia Saudyjska - Ustawa o przeciwdziałaniu cyberprzestępczości

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Arabia Saudyjska ACC: Skanowanie zawartości udostępnionej na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Kod SWIFT — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer międzynarodowego konta bankowego (IBAN) — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Arabia Saudyjska ACC: Skanowanie zawartości udostępnionej na zewnątrz — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Kod SWIFT — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer międzynarodowego konta bankowego (IBAN) — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="saudi-arabia-financial-data"></a>Dane finansowe Arabii Saudyjskiej

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Saudi Arabia Financial: Skanowanie zawartości udostępnionej na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 1, maksymalna liczba 9  <br/>  Kod SWIFT — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer międzynarodowego konta bankowego (IBAN) — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Saudi Arabia Financial: Skanuj zawartość udostępnioną na zewnątrz — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 10, maksymalna liczba 500  <br/>  Kod SWIFT — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer międzynarodowego konta bankowego (IBAN) — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="saudi-arabia-personally-identifiable-information-pii-data"></a>Dane osobowe (PII) w Arabii Saudyjskiej

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Dane osobowe Arabii Saudyjskiej: Skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Identyfikator narodowy Arabii Saudyjskiej — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Dane osobowe Arabii Saudyjskiej: Skanuj zawartość udostępnioną na zewnątrz — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Identyfikator narodowy Arabii Saudyjskiej — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="uk-access-to-medical-reports-act"></a>WIELKIEJ BRYTANII. Ustawa o dostępie do raportów medycznych

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|WIELKIEJ BRYTANII. AMRA: Skanowanie zawartości udostępnionej na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  WIELKIEJ BRYTANII. Krajowa liczba Usługa kondycji — minimalna liczba 1, maksymalna liczba 9  <br/>  WIELKIEJ BRYTANII. Numer ubezpieczenia narodowego (NINO) — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|WIELKIEJ BRYTANII. AMRA: Skanowanie zawartości udostępnionej na zewnątrz — duża liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  WIELKIEJ BRYTANII. Krajowa liczba Usługa kondycji — minimalna liczba 10, maksymalna liczba 500  <br/>  WIELKIEJ BRYTANII. Numer ubezpieczenia narodowego (NINO) — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="uk-data-protection-act"></a>WIELKIEJ BRYTANII. Ustawa o ochronie danych

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|WIELKIEJ BRYTANII. DPA: Skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  WIELKIEJ BRYTANII. Numer ubezpieczenia narodowego (NINO) — minimalna liczba 1, maksymalna liczba 9  <br/>  Stany Zjednoczone /Zjednoczone Zjednoczone Numer paszportu — minimalna liczba 1, maksymalna liczba 9  <br/>  Kod SWIFT — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|WIELKIEJ BRYTANII. DPA: Skanuj zawartość udostępnioną na zewnątrz — duża liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  WIELKIEJ BRYTANII. Numer ubezpieczenia narodowego (NINO) — minimalna liczba 10, maksymalna liczba 500  <br/>  Stany Zjednoczone /Zjednoczone Zjednoczone Numer paszportu — minimalna liczba 10, maksymalna liczba 500  <br/>  Kod SWIFT — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="uk-financial-data"></a>WIELKIEJ BRYTANII. Dane finansowe

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|WIELKIEJ BRYTANII. Finansowe: Skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer karty debetowej UE — minimalna liczba 1, maksymalna liczba 9  <br/>  Kod SWIFT — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|WIELKIEJ BRYTANII. Finansowe: Skanowanie zawartości udostępnionej na zewnątrz — duża liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer karty debetowej UE — minimalna liczba 10, maksymalna liczba 500  <br/>  Kod SWIFT — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="uk-personal-information-online-code-of-practice-piocp"></a>WIELKIEJ BRYTANII. Personal Information Online Code of Practice (PIOCP)

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|WIELKIEJ BRYTANII. PIOCP: Skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  WIELKIEJ BRYTANII. Numer ubezpieczenia narodowego (NINO) — minimalna liczba 1, maksymalna liczba 9  <br/>  WIELKIEJ BRYTANII. Krajowa liczba Usługa kondycji — minimalna liczba 1, maksymalna liczba 9  <br/>  Kod SWIFT — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|WIELKIEJ BRYTANII. PIOCP: Skanowanie zawartości udostępnionej na zewnątrz — duża liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  WIELKIEJ BRYTANII. Numer ubezpieczenia narodowego (NINO) — minimalna liczba 10, maksymalna liczba 500  <br/>  WIELKIEJ BRYTANII. Krajowa liczba Usługa kondycji — minimalna liczba 10, maksymalna liczba 500  <br/>  Kod SWIFT — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="uk-personally-identifiable-information-pii-data"></a>WIELKIEJ BRYTANII. Dane osobowe

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|WIELKIEJ BRYTANII. PiI: Skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  WIELKIEJ BRYTANII. Numer ubezpieczenia narodowego (NINO) — minimalna liczba 1, maksymalna liczba 9  <br/>  Stany Zjednoczone /Zjednoczone Zjednoczone Numer paszportu — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|WIELKIEJ BRYTANII. PiI: Skanuj zawartość udostępnioną na zewnątrz — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  WIELKIEJ BRYTANII. Numer ubezpieczenia narodowego (NINO) — minimalna liczba 10, maksymalna liczba 500  <br/>  Stany Zjednoczone /Zjednoczone Zjednoczone Numer paszportu — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="uk-privacy-and-electronic-communications-regulations"></a>WIELKIEJ BRYTANII. Przepisy dotyczące prywatności i komunikacji elektronicznej

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|WIELKIEJ BRYTANII. PECR: Skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Kod SWIFT — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|WIELKIEJ BRYTANII. PECR: Skanuj zawartość udostępnioną na zewnątrz — duża liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Kod SWIFT — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="us-federal-trade-commission-ftc-consumer-rules"></a>U.S. Federal Trade Commission (FTC) Consumer Rules

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Reguły FTC w Stanach Zjednoczonych: Skanowanie zawartości udostępnionej na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer konta bankowego w Stanach Zjednoczonych — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer routingu ABA — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Reguły FTC w Stanach Zjednoczonych: Skanowanie zawartości udostępnionej na zewnątrz — duża liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer konta bankowego w Stanach Zjednoczonych — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer routingu ABA — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="us-financial-data"></a>Dane finansowe w Stanach Zjednoczonych

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|U.S. Financial: Skanowanie zawartości udostępnionej na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer konta bankowego w Stanach Zjednoczonych — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer routingu ABA — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|U.S. Financial: Skanowanie zawartości udostępnionej na zewnątrz — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer konta bankowego w Stanach Zjednoczonych — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer routingu ABA — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="us-gramm-leach-bliley-act-glba"></a>U.S. Gramm-Leach-Bliley Act (GLBA)

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|U.S. GLBA: Skanowanie zawartości udostępnionej na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer konta bankowego w Stanach Zjednoczonych — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer identyfikacyjny indywidualnego podatnika (ITIN) w Stanach Zjednoczonych — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer ubezpieczenia społecznego (SSN) w Stanach Zjednoczonych — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|U.S. GLBA: Skanuj zawartość udostępnioną na zewnątrz — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer konta bankowego w Stanach Zjednoczonych — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer identyfikacyjny indywidualnego podatnika (ITIN) w Stanach Zjednoczonych — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer ubezpieczenia społecznego USA (SSN) — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="us-health-insurance-act-hipaa"></a>U.S. Health Insurance Act (HIPAA)

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Zawartość pasuje do amerykańskiego hipaa  <br/> | Zawiera dowolne z następujących informacji poufnych:  <br/>  Numer ubezpieczenia społecznego (SSN) w Stanach Zjednoczonych — minimalna liczba 1, maksymalna liczba  <br/>  Drug Enforcement Agency (DEA) Number - Min count 1, Max count any  <br/> **I** <br/>  Zawartość zawiera dowolne z następujących terminów:  <br/>  Międzynarodowa klasyfikacja chorób (ICD-9-CM) — minimalna liczba 1, maksymalna liczba  <br/>  Międzynarodowa klasyfikacja chorób (ICD-10-CM) — minimalna liczba 1, maksymalna liczba  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
   
## <a name="us-patriot-act"></a>U.S. Patriot Act

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|U.S. Patriot Act: Skanowanie zawartości udostępnionej na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer konta bankowego w Stanach Zjednoczonych — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer identyfikacyjny indywidualnego podatnika (ITIN) w Stanach Zjednoczonych — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer ubezpieczenia społecznego (SSN) w Stanach Zjednoczonych — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|U.S. Patriot Act: Skanowanie zawartości udostępnionej na zewnątrz — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer konta bankowego w Stanach Zjednoczonych — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer identyfikacyjny indywidualnego podatnika (ITIN) w Stanach Zjednoczonych — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer ubezpieczenia społecznego USA (SSN) — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="us-personally-identifiable-information-pii-data"></a>Dane osobowe (PII) w Stanach Zjednoczonych

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Identyfikator PII w Stanach Zjednoczonych: Skanuj zawartość udostępnioną na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer identyfikacyjny indywidualnego podatnika (ITIN) w Stanach Zjednoczonych — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer ubezpieczenia społecznego (SSN) w Stanach Zjednoczonych — minimalna liczba 1, maksymalna liczba 9  <br/>  Stany Zjednoczone /Zjednoczone Zjednoczone Numer paszportu — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Identyfikator PII w Stanach Zjednoczonych: skanowanie zawartości udostępnionej na zewnątrz — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer identyfikacyjny indywidualnego podatnika (ITIN) w Stanach Zjednoczonych — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer ubezpieczenia społecznego USA (SSN) — minimalna liczba 10, maksymalna liczba 500  <br/>  Stany Zjednoczone /Zjednoczone Zjednoczone Numer paszportu — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="us-state-breach-notification-laws"></a>U.S. State Breach Notification Laws

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|Naruszenie stanu USA: Skanowanie zawartości udostępnionej na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer konta bankowego w Stanach Zjednoczonych — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer prawa jazdy w Stanach Zjednoczonych — minimalna liczba 1, maksymalna liczba 9  <br/>  Numer ubezpieczenia społecznego (SSN) w Stanach Zjednoczonych — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Naruszenie stanu USA: Skanowanie zawartości udostępnionej na zewnątrz — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer konta bankowego w Stanach Zjednoczonych — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer licencji kierowcy w Stanach Zjednoczonych — minimalna liczba 10, maksymalna liczba 500  <br/>  Numer ubezpieczenia społecznego USA (SSN) — minimalna liczba 10, maksymalna liczba 500 <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="us-state-social-security-number-confidentiality-laws"></a>U.S. State Social Security Number Confidentiality Laws

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Działania**|
|:-----|:-----|:-----|
|U.S. SSN Laws: Skanowanie zawartości udostępnionej na zewnątrz — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer ubezpieczenia społecznego (SSN) w Stanach Zjednoczonych — minimalna liczba 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|U.S. SSN Laws: Skanowanie zawartości udostępnionej na zewnątrz — duża liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer ubezpieczenia społecznego USA (SSN) — minimalna liczba 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymagaj uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   

