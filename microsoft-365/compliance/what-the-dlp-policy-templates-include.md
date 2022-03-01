---
title: Szablony zasad DLP
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
description: Dowiedz się, jakie szablony zasad ochrony przed utratą danych (DLP) są dostępne w Centrum Office 365 zabezpieczeń & zgodności.
ms.openlocfilehash: cad7270fd60b0bce9febe90f25156bd27bdcee32
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2021
ms.locfileid: "63004958"
---
# <a name="what-the-dlp-policy-templates-include"></a>Szablony zasad DLP

Ochrona przed utratą danych (DLP, Data loss prevention) &amp; w Centrum zgodności zabezpieczeń zawiera gotowe do użycia szablony zasad, które spełniają typowe wymagania dotyczące zgodności, takie jak pomoc w ochronie poufnych informacji podlegających amerykańskiej ustawie HIPAA, U.S. Gramm-Leach-Bliley Act (GLBA) lub amerykańskiej ustawy Health Insurance Act. Ten temat zawiera listę wszystkich szablonów zasad, typów informacji poufnych, których szukają, oraz domyślnych warunków i akcji. W tym temacie nie opisano wszystkich szczegółów konfiguracji poszczególnych szablonów zasad. Zamiast tego temat zawiera wystarczająco dużo informacji, aby ułatwić ci podjęcie decyzji, który szablon będzie najlepszym punktem wyjścia dla scenariusza. Pamiętaj, że możesz dostosować te szablony zasad do określonych wymagań.
  
## <a name="australia-financial-data"></a>Australia Dane finansowe

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Australia — finansowe: Skanowanie zawartości udostępnianej poza — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Kod SWIFT — minimum 1, maksimum 9  <br/>  Numer pliku podatkowego Australii — minimum 1, liczba maksymalna 9  <br/>  Australia Numer konta bankowego — liczba min 1, maksimum 9  <br/>  Numer karty kredytowej — liczba min 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Australia Finansowa: Skanowanie zawartości udostępnionej poza obszarem — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Kod SWIFT — minimum 10, maksimum 500  <br/>  Numer pliku podatkowego w Australii — minimum 10, maksimum 500  <br/>  Australia Numer konta bankowego — minimum 10, maksimum 500  <br/>  Numer karty kredytowej — minimum 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="australia-health-records-act-hrip-act"></a>Australia Health Records Act (HRIP Act)

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Australia H ZJEDN. Skanuj zawartość udostępnioną poza obszarem — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer pliku podatkowego Australii — minimum 1, liczba maksymalna 9  <br/>  Australia Numer konta medycznego — minimum 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Australia H ZJEDN. Skanuj zawartość udostępnioną poza — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer pliku podatkowego w Australii — minimum 10, maksimum 500  <br/>  Australia Numer konta medycznego — minimum 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="australia-personally-identifiable-information-pii-data"></a>Dane umożliwiające identyfikację użytkownika (PII) w Australii

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Australia PII: Skanowanie zawartości udostępnianej poza siecią — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer pliku podatkowego Australii — minimum 1, liczba maksymalna 9  <br/>  Numer prawa jazdy w Australii — minimum 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Australia PII: Skanowanie zawartości udostępnianej poza siecią — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer pliku podatkowego w Australii — minimum 10, maksimum 500  <br/>  Numer prawa jazdy w Australii — minimum 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="australia-privacy-act"></a>Australia Privacy Act

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Prywatność w Australii: Skanowanie zawartości udostępnianej poza siecią — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer prawa jazdy w Australii — minimum 1, maksimum 9  <br/>  Numer paszportu Australii — liczba minimalna 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Prywatność w Australii: Skanowanie zawartości udostępnianej poza siecią — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer prawa jazdy w Australii — minimum 10, maksimum 500  <br/>  Numer paszportu Australii — liczba minimalna 10, Maksimum 500 <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="canada-financial-data"></a>Kanada Dane finansowe

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Kanada — dane finansowe: skanowanie zawartości udostępnianej poza obszarem o niskiej wartości  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — liczba min 1, maksimum 9  <br/>  Canada Bank Account Number — Min count 1, Max count 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Kanada — dane finansowe: Skanowanie zawartości udostępnionej poza obszarem — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimum 10, maksimum 500  <br/>  Canada Bank Account Number — Min count 10, Max count 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="canada-health-information-act-hia"></a>Canada Health Information Act (HIA)

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Kanada HIA: Skanowanie zawartości udostępnianej poza obszarem — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer paszportu Kanady — liczba minimalna 1, maksimum 9  <br/>  Canada Social Insurance Number — Min count 1, Max count 9  <br/>  Kanada Usługa kondycji — liczba minimalna 1, maksimum 9  <br/>  Kanada — numer identyfikacyjny zdrowia osobistego (PHIN) — liczba minimalna 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Kanada HIA: Skanowanie zawartości udostępnionej poza obszarem — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer paszportu Kanady — liczba minimalna 10, maksimum 500  <br/>  Canada Social Insurance Number — Min count 10, Max count 500  <br/>  Kanada Usługa kondycji liczba — minimum 10, maksimum 500  <br/>  Kanada — osobisty numer identyfikacyjny kondycji (PHIN) — liczba minimalna 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="canada-personal-health-act-phipa---ontario"></a>Canada Personal Health Act (PHIPA) — Ontario

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|PhiPA w Kanadzie: Skanowanie zawartości udostępnionej poza siecią — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer paszportu Kanady — liczba minimalna 1, maksimum 9  <br/>  Canada Social Insurance Number — Min count 1, Max count 9  <br/>  Kanada Usługa kondycji — liczba minimalna 1, maksimum 9  <br/>  Kanada — numer identyfikacyjny zdrowia osobistego (PHIN) — liczba minimalna 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|PhiPA (Kanada): skanowanie zawartości udostępnionej poza siecią — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer paszportu Kanady — liczba minimalna 10, maksimum 500  <br/>  Canada Social Insurance Number — Min count 10, Max count 500  <br/>  Kanada Usługa kondycji liczba — minimum 10, maksimum 500  <br/>  Kanada — osobisty numer identyfikacyjny kondycji (PHIN) — liczba minimalna 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="canada-personal-health-information-act-phia---manitoba"></a>Canada Personal Health Information Act (PHIA) — Manitoba

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|PHIA w Kanadzie: Skanowanie zawartości udostępnianej poza siecią — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Canada Social Insurance Number — Min count 1, Max count 9  <br/>  Kanada Usługa kondycji — liczba minimalna 1, maksimum 9  <br/>  Kanada — numer identyfikacyjny zdrowia osobistego (PHIN) — liczba minimalna 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|PHIA w Kanadzie: Skanowanie zawartości udostępnionej poza siecią — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Canada Social Insurance Number — Min count 10, Max count 500  <br/>  Kanada Usługa kondycji liczba — minimum 10, maksimum 500 <br/>  Kanada — osobisty numer identyfikacyjny kondycji (PHIN) — liczba minimalna 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="canada-personal-information-protection-act-pipa"></a>Canada Personal Information Protection Act (PIPA)

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Canada PIPA: Skanowanie zawartości udostępnionej poza siecią — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer paszportu Kanady — liczba minimalna 1, maksimum 9  <br/>  Canada Social Insurance Number — Min count 1, Max count 9  <br/>  Kanada Usługa kondycji — liczba minimalna 1, maksimum 9  <br/>  Kanada — numer identyfikacyjny zdrowia osobistego (PHIN) — liczba minimalna 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Canada PIPA: Skanowanie zawartości udostępnionej poza siecią — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer paszportu Kanady — liczba minimalna 10, maksimum 500  <br/>  Canada Social Insurance Number — Min count 10, Max count 500  <br/>  Kanada Usługa kondycji liczba — minimum 10, maksimum 500  <br/>  Kanada — osobisty numer identyfikacyjny kondycji (PHIN) — liczba minimalna 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="canada-personal-information-protection-act-pipeda"></a>Canada Personal Information Protection Act (PIPEDA)

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Kanada PIPEDA: skanowanie zawartości udostępnianej poza siecią — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer prawa jazdy w Kanadzie — minimum 1, maksimum 9  <br/>  Canada Bank Account Number — Min count 1, Max count 9  <br/>  Numer paszportu Kanady — liczba minimalna 1, maksimum 9  <br/>  Canada Social Insurance Number — Min count 1, Max count 9  <br/>  Kanada Usługa kondycji — liczba minimalna 1, maksimum 9  <br/>  Kanada — numer identyfikacyjny zdrowia osobistego (PHIN) — liczba minimalna 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Canada PIPEDA: Skanowanie zawartości udostępnionej poza siecią — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer prawa jazdy w Kanadzie — minimum 10, maksimum 500 <br/>  Canada Bank Account Number — Min count 10, Max count 500 <br/>  Numer paszportu Kanady — liczba minimalna 10, maksimum 500  <br/>  Canada Social Insurance Number — Min count 10, Max count 500  <br/>  Kanada Usługa kondycji liczba — minimum 10, maksimum 500  <br/>  Kanada — osobisty numer identyfikacyjny kondycji (PHIN) — liczba minimalna 10, maksimum 500 <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="canada-personally-identifiable-information-pii-data"></a>Dane umożliwiające identyfikację użytkownika (PII) w Kanadzie

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|PiI w Kanadzie: Skanowanie zawartości udostępnionej poza siecią — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer prawa jazdy w Kanadzie — minimum 1, maksimum 9  <br/>  Canada Bank Account Number — Min count 1, Max count 9  <br/>  Numer paszportu Kanady — liczba minimalna 1, maksimum 9  <br/>  Canada Social Insurance Number — Min count 1, Max count 9  <br/>  Kanada Usługa kondycji — liczba minimalna 1, maksimum 9  <br/>  Kanada — numer identyfikacyjny zdrowia osobistego (PHIN) — liczba minimalna 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|PiI w Kanadzie: Skanowanie zawartości udostępnionej poza siecią — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer prawa jazdy w Kanadzie — minimum 10, maksimum 500  <br/>  Canada Bank Account Number — Min count 10, Max count 500  <br/>  Numer paszportu Kanady — liczba minimalna 10, maksimum 500  <br/>  Canada Social Insurance Number — Min count 10, Max count 500  <br/>  Kanada Usługa kondycji liczba — minimum 10, maksimum 500  <br/>  Kanada — osobisty numer identyfikacyjny kondycji (PHIN) — liczba minimalna 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="france-data-protection-act"></a>France Data Protection Act

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|France DPA: Skanowanie zawartości udostępnianej poza obszarem — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  France National ID Card (CNI) — Min count 1, Max count 9  <br/>  France Social Security Number (INSEE) — Min count 1, Max count 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|France DPA: Skanowanie zawartości udostępnianej poza obszarem — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  France National ID Card (CNI) — Min count 10, Max count 500  <br/>  France Social Security Number (INSEE) — Min count 10, Max count 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="france-financial-data"></a>Dane finansowe Dotyczące Francji

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Francja — finansowe: Skanowanie zawartości udostępnianej poza obszarem — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — liczba min 1, maksimum 9  <br/>  Numer karty debetowej UE — liczba minimalna 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|France Financial: Scan content shared outside - high count  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimum 10, maksimum 500  <br/>  Numer karty debetowej UE — minimum 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="france-personally-identifiable-information-pii-data"></a>Dane umożliwiające identyfikację użytkownika (PII) we Francji

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|France PII: Skanowanie zawartości udostępnianej poza siecią — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  France Social Security Number (INSEE) — Min count 1, Max count 9  <br/>  Numer prawa jazdy we Francji — minimum 1, maksimum 9  <br/>  Numer paszportu Francji — liczba minimalna 1, maksimum 9  <br/>  France National ID Card (CNI) — Min count 1, Max count 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|France PII: Skanowanie zawartości udostępnianej poza siecią — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  France Social Security Number (INSEE) — Min count 10, Max count 500  <br/>  Numer prawa jazdy we Francji — minimum 10, maksimum 500  <br/>  Numer paszportu Francji — liczba minimalna 10, maksimum 500  <br/>  France National ID Card (CNI) — Min count 10, Max count 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="general-data-protection-regulation-gdpr"></a>Ogólne Rozporządzenie o Ochronie Danych (RODO)

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Znaleziona zawartość z danymi wrażliwymi w UE o małej pojemności  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty debetowej UE — liczba minimalna 1, maksymalna liczba 9  <br/>  Numer prawa jazdy w UE — minimum 1, maksimum 9  <br/>  Narodowy numer identyfikacyjny UE — liczba minimalna 1, maksimum 9  <br/>  Numer paszportu UE — liczba minimalna 1, maksimum 9  <br/>  Numer PE PE PEŁSZ lub identyfikator równoważne — minimum 1, maksimum liczba 9  <br/>  Numer identyfikacyjny podatku UE (TIN) — liczba min 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie raportów o incydentach do administratora  <br/> |
|Duża ilość odnalezionej zawartości poufnej w UE  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty debetowej UE — minimum 10, maksymalna liczba 500  <br/>  Numer prawa jazdy w UE — minimum 10, maksimum 500  <br/>  Narodowy numer identyfikacyjny UE — liczba minimalna 10, maksimum 500  <br/>  Numer paszportu UE — minimum 10, maksimum 500  <br/>  Numer PE PEZ lub identyfikator odpowiednika — minimum 10, maksimum 500  <br/>  Numer identyfikacyjny podatku UE (TIN) — liczba minimalna 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Ograniczanie dostępu do zawartości użytkownikom zewnętrznym  <br/>  Powiadamianie użytkowników za pomocą poczty e-mail i porad dotyczących zasad  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportów o incydentach do administratora  <br/> |
   
## <a name="germany-financial-data"></a>Dane finansowe w Niemczech

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Germany Financial Data: Scan content shared outside - low count  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — liczba min 1, maksimum 9  <br/>  Numer karty debetowej UE — liczba minimalna 1, maksymalna liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Germany Financial Data: Scan content shared outside - high count  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimum 10, maksimum 500  <br/>  Numer karty debetowej UE — minimum 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="germany-personally-identifiable-information-pii-data"></a>Dane umożliwiające identyfikację użytkownika (PII) w Niemczech

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Germany PII: Skanowanie zawartości udostępnianej poza — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Niemiecki numer prawa jazdy — minimum 1, maksimum 9  <br/>  Numer paszportu niemieckiego — liczba minimalna 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Germany PII: Skanowanie zawartości udostępnianej poza siecią — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Niemiecki numer prawa jazdy — minimum 10, maksimum 500  <br/>  Numer paszportu niemieckiego — liczba minimalna 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="israel-financial-data"></a>Dane finansowe Izraela

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Izrael — dane finansowe: skanowanie zawartości udostępnianej poza obszarem o niskiej wartości  <br/> | Zawartość zawiera informacje poufne:  <br/>  Izrael Numer konta bankowego — liczba minimalna 1, maksimum 9  <br/>  Kod SWIFT — minimum 1, maksimum 9  <br/>  Numer karty kredytowej — liczba min 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Izrael — dane finansowe: skanowanie zawartości udostępnianej poza obszarem — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Izrael Numer konta bankowego — liczba minimalna 10, maksimum 500  <br/>  Kod SWIFT — minimum 10, maksimum 500  <br/>  Numer karty kredytowej — minimum 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="israel-personally-identifiable-information-pii-data"></a>Dane umożliwiające identyfikację użytkownika (PII) w Izraelu

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|PiI Izrael: Skanowanie zawartości udostępnianej poza siecią — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Identyfikator narodowy Izrael — liczba minimalna 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|PiI Izrael: Skanowanie zawartości udostępnianej poza siecią — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Identyfikator narodowy Izrael — liczba minimalna 10, maksymalna liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="israel-protection-of-privacy"></a>Izrael : ochrona prywatności

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Ochrona prywatności w Izraelie: Skanowanie zawartości udostępnianej poza siecią — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Identyfikator narodowy Izrael — liczba minimalna 1, maksimum 9  <br/>  Izrael Numer konta bankowego — liczba minimalna 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Prywatność w Izraelie: Skanowanie zawartości udostępnianej poza siecią — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Identyfikator narodowy Izrael — liczba minimalna 10, maksymalna liczba 500  <br/>  Izrael Numer konta bankowego — liczba minimalna 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="japan-financial-data"></a>Japonia - dane finansowe

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Japonia — finansowe: Skanowanie zawartości udostępnianej poza — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Japan Bank Account Number — Min count 1, Max count 9  <br/>  Numer karty kredytowej — liczba min 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Japonia — finansowe: Skanowanie zawartości udostępnianej poza — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Japan Bank Account Number — Minimum 10, Maksimum 500  <br/>  Numer karty kredytowej — minimum 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="japan-personally-identifiable-information-pii-data"></a>Dane umożliwiające identyfikację użytkownika (PII) w Japonii

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Japoński kod PII: Skanowanie zawartości udostępnianej poza siecią — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Japoński numer rejestru rezydentny — liczba minimalna 1, maksimum 9  <br/>  Japoński numer ubezpieczenia społecznego (SIN) — liczba minimalna 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Japoński kod PII: Skanowanie zawartości udostępnianej poza siecią — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Japoński numer rejestracyjny — minimum 10, maksimum 500  <br/>  Japoński numer ubezpieczenia społecznego (SIN) — minimum 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="japan-protection-of-personal-information"></a>Japonia ochrona informacji osobistych

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Japonia — ppi: skanowanie zawartości udostępnianej poza siecią — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Japoński numer rejestru rezydentny — liczba minimalna 1, maksimum 9  <br/>  Japoński numer ubezpieczenia społecznego (SIN) — liczba minimalna 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Japonia PPI: Skanowanie zawartości udostępnianej poza siecią — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Japoński numer rejestracyjny — minimum 10, maksimum 500  <br/>  Japoński numer ubezpieczenia społecznego (SIN) — minimum 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="pci-data-security-standard-pci-dss"></a>PCI Data Security Standard (PCI DSS)

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|PCI DSS: Skanowanie zawartości udostępnianej poza siecią — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — liczba min 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|PCI DSS: Skanowanie zawartości udostępnionej poza siecią — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimum 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="saudi-arabia---anti-cyber-crime-law"></a>Arabia Saudyjska — prawo do ochrony przed cyberatak

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Arabia Saudyjska: Skanowanie zawartości udostępnianej poza — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Kod SWIFT — minimum 1, maksimum 9  <br/>  Numer konta bankowego międzynarodowego (IBAN) — minimum 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Arabia Saudyjska: Skanowanie zawartości udostępnionej poza — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Kod SWIFT — minimum 10, maksimum 500  <br/>  Numer konta bankowego międzynarodowego (IBAN) — minimum 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="saudi-arabia-financial-data"></a>Dane finansowe z Arabia Saudyjska

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Arabia Saudyjska — finansowe: skanowanie zawartości udostępnionej poza obszarem — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — liczba min 1, maksimum 9  <br/>  Kod SWIFT — minimum 1, maksimum 9  <br/>  Numer konta bankowego międzynarodowego (IBAN) — minimum 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Arabia Saudyjska — finansowe: skanowanie zawartości udostępnionej poza obszarem — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimum 10, maksimum 500  <br/>  Kod SWIFT — minimum 10, maksimum 500  <br/>  Numer konta bankowego międzynarodowego (IBAN) — minimum 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="saudi-arabia-personally-identifiable-information-pii-data"></a>Dane umożliwiające identyfikację użytkownika (PII) w Arabia Saudyjska

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Arabia Saudyjska: Skanowanie zawartości udostępnionej poza siecią — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Identyfikator narodowy Arabia Saudyjska — liczba minimalna 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Arabia Saudyjska. Skanowanie zawartości udostępnionej poza siecią — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Identyfikator narodowy Arabia Saudyjska — minimum 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="uk-access-to-medical-reports-act"></a>Zjednoczone Emiraty Zjednoczone Access to Medical Reports Act

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Zjednoczone Emiraty Zjednoczone AMRA: Skanowanie zawartości udostępnianej poza obszarem — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Zjednoczone Emiraty Zjednoczone National Usługa kondycji Number — Min count 1, Max count 9  <br/>  Zjednoczone Emiraty Zjednoczone National Insurance Number (NINO) — Min count 1, Max count 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Zjednoczone Emiraty Zjednoczone AMRA: Skanowanie zawartości udostępnianej poza obszarem — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Zjednoczone Emiraty Zjednoczone Numer Usługa kondycji państwowej — minimum 10, maksimum 500  <br/>  Zjednoczone Emiraty Zjednoczone National Insurance Number (NINO) — Min count 10, Max count 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="uk-data-protection-act"></a>Zjednoczone Emiraty Zjednoczone Data Protection Act

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Zjednoczone Emiraty Zjednoczone DPA: Skanowanie zawartości udostępnianej poza obszarem — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Zjednoczone Emiraty Zjednoczone National Insurance Number (NINO) — Min count 1, Max count 9  <br/>  Stany Zjednoczone Numer paszportu — liczba minimalna 1, maksimum 9  <br/>  Kod SWIFT — minimum 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Zjednoczone Emiraty Zjednoczone DPA: Skanowanie zawartości udostępnianej poza obszarem — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Zjednoczone Emiraty Zjednoczone National Insurance Number (NINO) — Min count 10, Max count 500  <br/>  Stany Zjednoczone Numer paszportu — minimum 10, maksimum 500  <br/>  Kod SWIFT — minimum 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="uk-financial-data"></a>Zjednoczone Emiraty Zjednoczone Dane finansowe

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Zjednoczone Emiraty Zjednoczone Finansowe: Skanowanie zawartości udostępnianej poza obszarem — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — liczba min 1, maksimum 9  <br/>  Numer karty debetowej UE — liczba minimalna 1, maksymalna liczba 9  <br/>  Kod SWIFT — minimum 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Zjednoczone Emiraty Zjednoczone Finansowe: Skanowanie zawartości udostępnianej poza obszarem — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimum 10, maksimum 500  <br/>  Numer karty debetowej UE — minimum 10, maksymalna liczba 500  <br/>  Kod SWIFT — minimum 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="uk-personal-information-online-code-of-practice-piocp"></a>Zjednoczone Emiraty Zjednoczone Praktyki dotyczące informacji osobistych w trybie online (PIOCP)

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Zjednoczone Emiraty Zjednoczone PIOCP: Skanowanie zawartości udostępnianej poza — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Zjednoczone Emiraty Zjednoczone National Insurance Number (NINO) — Min count 1, Max count 9  <br/>  Zjednoczone Emiraty Zjednoczone National Usługa kondycji Number — Min count 1, Max count 9  <br/>  Kod SWIFT — minimum 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Zjednoczone Emiraty Zjednoczone PIOCP: Skanowanie zawartości udostępnianej poza — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Zjednoczone Emiraty Zjednoczone National Insurance Number (NINO) — Min count 10, Max count 500  <br/>  Zjednoczone Emiraty Zjednoczone Numer Usługa kondycji państwowej — minimum 10, maksimum 500  <br/>  Kod SWIFT — minimum 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="uk-personally-identifiable-information-pii-data"></a>Zjednoczone Emiraty Zjednoczone Dane umożliwiające identyfikację użytkownika

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Zjednoczone Emiraty Zjednoczone PiI: Skanowanie zawartości udostępnianej poza siecią — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Zjednoczone Emiraty Zjednoczone National Insurance Number (NINO) — Min count 1, Max count 9  <br/>  Stany Zjednoczone Numer paszportu — liczba minimalna 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Zjednoczone Emiraty Zjednoczone PII: Skanowanie zawartości udostępnianej poza siecią — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Zjednoczone Emiraty Zjednoczone National Insurance Number (NINO) — Min count 10, Max count 500  <br/>  Stany Zjednoczone Numer paszportu — minimum 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="uk-privacy-and-electronic-communications-regulations"></a>Zjednoczone Emiraty Zjednoczone Zasady ochrony prywatności i komunikacji elektronicznej

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Zjednoczone Emiraty Zjednoczone PECR: Skanowanie zawartości udostępnianej poza obszarem — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Kod SWIFT — minimum 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Zjednoczone Emiraty Zjednoczone PECR: Skanowanie zawartości udostępnianej poza obszarem — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Kod SWIFT — minimum 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="us-federal-trade-commission-ftc-consumer-rules"></a>Reguły amerykańskiej Federal Trade Commission (FTC)

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Reguły ftc Stanów Zjednoczonych: skanowanie zawartości udostępnianej poza siecią — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — liczba min 1, maksimum 9  <br/>  Numer konta bankowego w Stanach Zjednoczonych — minimum 1, maksimum 9  <br/>  Numer routingu ABA — liczba minimalna 1, liczba maksymalna 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Reguły ftc Stanów Zjednoczonych: skanowanie zawartości udostępnianej poza siecią — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimum 10, maksimum 500  <br/>  Numer konta bankowego w Stanach Zjednoczonych — minimum 10, maksimum 500  <br/>  Numer routingu ABA — liczba minimalna 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="us-financial-data"></a>Dane finansowe Stanów Zjednoczonych

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Stany Zjednoczone — finanse: skanowanie zawartości udostępnianej poza — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — liczba min 1, maksimum 9  <br/>  Numer konta bankowego w Stanach Zjednoczonych — minimum 1, maksimum 9  <br/>  Numer routingu ABA — liczba minimalna 1, liczba maksymalna 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Stany Zjednoczone — finanse: skanowanie zawartości udostępnionej poza obszarem — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimum 10, maksimum 500  <br/>  Numer konta bankowego w Stanach Zjednoczonych — minimum 10, maksimum 500  <br/>  Numer routingu ABA — liczba minimalna 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="us-gramm-leach-bliley-act-glba"></a>U.S. Gramm-Leach-Bliley Act (GLBA)

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|GLBA w Stanach Zjednoczonych: Skanowanie zawartości udostępnianej poza — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — liczba min 1, maksimum 9  <br/>  Numer konta bankowego w Stanach Zjednoczonych — minimum 1, maksimum 9  <br/>  Numer identyfikacyjny identyfikacji indywidualnej (ITIN) Stanów Zjednoczonych — liczba min 1, maksimum 9  <br/>  U.S. Social Security Number (SSN) — minimum 1, Maksimum, liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|GLBA w Stanach Zjednoczonych: Skanowanie zawartości udostępnianej poza — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimum 10, maksimum 500  <br/>  Numer konta bankowego w Stanach Zjednoczonych — minimum 10, maksimum 500  <br/>  Amerykański numer identyfikacji indywidualnej identyfikacji podatkowej (ITIN) — minimum 10, maksimum 500  <br/>  U.S. Social Security Number (SSN) — Minimum 10, Maksimum liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="us-health-insurance-act-hipaa"></a>Amerykańska ustawa HIPAA (Health Insurance Act)

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Zawartość jest dopiska amerykańskiej USTAWY HIPAA  <br/> | Zawiera dowolne z następujących informacji poufnych:  <br/>  U.S. Social Security Number (SSN) — minimum 1, maksimum  <br/>  Liczba agencji wymuszania odpowiedzialności za stosowanie środków odurzanych (DEA) — minimum 1, maksymalna liczba  <br/> **AND** <br/>  Zawartość zawiera dowolny z tych warunków:  <br/>  Międzynarodowa Klasyfikacja Kwalifikacji (ICD-9-CM) — minimum 1, maksimum — dowolna  <br/>  Klasyfikacja międzynarodowa najbłędszej (ICD-10-CM) — minimum 1, maksymalna liczba  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
   
## <a name="us-patriot-act"></a>Stany Zjednoczone

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Amerykańska act: skanowanie zawartości udostępnianej poza obszarem o małej wartości  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — liczba min 1, maksimum 9  <br/>  Numer konta bankowego w Stanach Zjednoczonych — minimum 1, maksimum 9  <br/>  Numer identyfikacyjny identyfikacji indywidualnej (ITIN) Stanów Zjednoczonych — liczba min 1, maksimum 9  <br/>  U.S. Social Security Number (SSN) — minimum 1, Maksimum, liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Stany Zjednoczone — act: Skanowanie zawartości udostępnianej poza — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimum 10, maksimum 500  <br/>  Numer konta bankowego w Stanach Zjednoczonych — minimum 10, maksimum 500  <br/>  Amerykański numer identyfikacji indywidualnej identyfikacji podatkowej (ITIN) — minimum 10, maksimum 500  <br/>  U.S. Social Security Number (SSN) — Minimum 10, Maksimum liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="us-personally-identifiable-information-pii-data"></a>Dane umożliwiające identyfikację użytkownika (PII)

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|U.S. PII: Skanowanie zawartości udostępnianej poza siecią — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer identyfikacyjny identyfikacji indywidualnej (ITIN) Stanów Zjednoczonych — liczba min 1, maksimum 9  <br/>  U.S. Social Security Number (SSN) — minimum 1, Maksimum, liczba 9  <br/>  Stany Zjednoczone Numer paszportu — liczba minimalna 1, maksimum 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|U.S. PII: Skanowanie zawartości udostępnianej poza — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Amerykański numer identyfikacji indywidualnej identyfikacji podatkowej (ITIN) — minimum 10, maksimum 500  <br/>  U.S. Social Security Number (SSN) — Minimum 10, Maksimum liczba 500  <br/>  Stany Zjednoczone Numer paszportu — minimum 10, maksimum 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="us-state-breach-notification-laws"></a>Przepisy dotyczące powiadomień o naruszeniu zabezpieczeń (UA)

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Naruszenie bezpieczeństwa w Stanach Zjednoczonych: skanowanie zawartości udostępnianej poza — niska liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — liczba min 1, maksimum 9  <br/>  Numer konta bankowego w Stanach Zjednoczonych — minimum 1, maksimum 9  <br/>  Numer prawa jazdy w Stanach Zjednoczonych — minimum 1, maksimum 9  <br/>  U.S. Social Security Number (SSN) — minimum 1, Maksimum, liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Naruszenie bezpieczeństwa stanów Zjednoczonych: skanuj zawartość udostępnianą poza — wysoka liczba  <br/> | Zawartość zawiera informacje poufne:  <br/>  Numer karty kredytowej — minimum 10, maksimum 500  <br/>  Numer konta bankowego w Stanach Zjednoczonych — minimum 10, maksimum 500  <br/>  Numer prawa jazdy w Stanach Zjednoczonych — minimum 10, maksimum 500  <br/>  U.S. Social Security Number (SSN) — Minimum 10, Maksimum liczba 500 <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   
## <a name="us-state-social-security-number-confidentiality-laws"></a>Przepisy dotyczące poufności informacji dotyczące numeru PE PEŁ STANÓW ZJEDNOCZONYCH

|**Nazwa reguły**|**Warunki  <br/> (w tym typy informacji poufnych)**|**Akcje**|
|:-----|:-----|:-----|
|Przepisy amerykańskiego departamentu stanów zjednoczonych: skanowanie zawartości udostępnianej poza obszarem o małej wartości  <br/> | Zawartość zawiera informacje poufne:  <br/>  U.S. Social Security Number (SSN) — minimum 1, Maksimum, liczba 9  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> |Wysyłanie powiadomienia  <br/> |
|Przepisy amerykańskiego departamentu danych (SSN): skanowanie zawartości udostępnianej poza dużą liczbę  <br/> | Zawartość zawiera informacje poufne:  <br/>  U.S. Social Security Number (SSN) — Minimum 10, Maksimum liczba 500  <br/>  Zawartość jest udostępniana:  <br/>  Osoby spoza mojej organizacji  <br/> | Blokowanie dostępu do zawartości  <br/>  Wysyłanie powiadomienia  <br/>  Zezwalaj na zastępowanie  <br/>  Wymaganie uzasadnienia biznesowego  <br/>  Wysyłanie raportu o zdarzeniu  <br/> |
   

