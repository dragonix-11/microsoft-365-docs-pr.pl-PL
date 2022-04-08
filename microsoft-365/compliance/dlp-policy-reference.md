---
title: Dokumentacja zasad ochrony przed utratą danych
f1.keywords: CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 03/02/2022
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- MET150
ms.assetid: 6501b5ef-6bf7-43df-b60d-f65781847d6c
ms.collection:
- M365-security-compliance
- SPO_Content
recommendations: false
description: Informacje o składniku zasad DLP i konfiguracji
ms.custom: seo-marvel-apr2021
ms.openlocfilehash: d6bc24f313d1998979a460bcd41e87ccbe8abc5c
ms.sourcegitcommit: 5c9137f98e688ab23c144e75687399e390bb2601
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2022
ms.locfileid: "64704928"
---
# <a name="data-loss-prevention-policy-reference"></a>Dokumentacja zasad ochrony przed utratą danych

Zasady ochrony przed utratą danych (DLP) mają wiele składników do skonfigurowania. Aby utworzyć skuteczne zasady, musisz zrozumieć, jaki jest cel poszczególnych składników i jak jego konfiguracja zmienia zachowanie zasad. Ten artykuł zawiera szczegółową anatomię zasad DLP.

## <a name="policy-templates"></a>Szablony zasad 

Szablony zasad DLP są wstępnie posortowane na cztery kategorie:

- Te, które mogą wykrywać i chronić typy informacji **finansowych** .
- Te, które mogą wykrywać i chronić typy informacji **medycznych i zdrowotnych** .
- Te, które mogą wykrywać i chronić typy informacji o **ochronie prywatności** .
- Szablon **niestandardowy** , którego można użyć do tworzenia własnych zasad, jeśli jedna z pozostałych nie spełnia twoich potrzeb organizacji.

Ta tabela zawiera listę wszystkich szablonów zasad i poufnych typów informacji (SIT), które obejmują. 

zaktualizowano: 23.06.2021 r.

|Kategoria| Szablon | SIEDZIEĆ |
|---------|---------|---------|
|Finansowych| Dane finansowe Australii| - [Kod SWIFT](sensitive-information-type-entity-definitions.md#swift-code) </br> - [Numer pliku podatkowego Australii](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [Numer konta bankowego w Australii](sensitive-information-type-entity-definitions.md#australia-bank-account-number) </br> - [Numer karty kredytowej](sensitive-information-type-entity-definitions.md#credit-card-number)|
|Finansowych| Kanada Dane finansowe |- [Numer karty kredytowej](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Numer konta bankowego w Kanadzie](sensitive-information-type-entity-definitions.md#canada-bank-account-number)|
|Finansowych| Francja — dane finansowe |- [Numer karty kredytowej](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Numer karty debetowej UE](sensitive-information-type-entity-definitions.md#eu-debit-card-number)|
|Finansowych| Dane finansowe Niemiec |- [Numer karty kredytowej](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Numer karty debetowej UE](sensitive-information-type-entity-definitions.md#eu-debit-card-number)|
|Finansowych| Dane finansowe Izraela |- [Numer konta bankowego Izraela](sensitive-information-type-entity-definitions.md#israel-bank-account-number) </br> - [Kod SWIFT](sensitive-information-type-entity-definitions.md#swift-code) </br> - [Numer karty kredytowej](sensitive-information-type-entity-definitions.md#credit-card-number)|
|Finansowych| Dane finansowe Japonii |- [Numer konta bankowego w Japonii](sensitive-information-type-entity-definitions.md#japan-bank-account-number) </br> - [Numer karty kredytowej](sensitive-information-type-entity-definitions.md#credit-card-number)|
|Finansowych| PCI Data Security Standard (PCI DSS)|- [Numer karty kredytowej](sensitive-information-type-entity-definitions.md#credit-card-number)|
|Finansowych| Arabia Saudyjska – ustawa o przeciwdziałaniu cyberprzestępczości|- [Kod SWIFT](sensitive-information-type-entity-definitions.md#swift-code) </br> - [Numer międzynarodowego konta bankowego (IBAN)](sensitive-information-type-entity-definitions.md#international-banking-account-number-iban) |
|Finansowych| Dane finansowe Arabii Saudyjskiej |- [Numer karty kredytowej](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Kod SWIFT](sensitive-information-type-entity-definitions.md#swift-code) </br> - [Numer międzynarodowego konta bankowego (IBAN)](sensitive-information-type-entity-definitions.md#international-banking-account-number-iban)|
|Finansowych| Dane finansowe Wielkiej Brytanii|- [Numer karty kredytowej](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Numer karty debetowej UE](sensitive-information-type-entity-definitions.md#eu-debit-card-number) </br> - [Kod SWIFT](sensitive-information-type-entity-definitions.md#swift-code)|
|Finansowych| Dane finansowe STANÓW Zjednoczonych|- [Numer karty kredytowej](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Numer konta bankowego w Stanach Zjednoczonych](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [Numer routingu ABA](sensitive-information-type-entity-definitions.md#aba-routing-number)|
|Finansowych| U.S. Federal Trade Commission (FTC) Consumer Rules|- [Numer karty kredytowej](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Numer konta bankowego w Stanach Zjednoczonych](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [Numer routingu ABA](sensitive-information-type-entity-definitions.md#aba-routing-number)|
|Finansowych| U.S. Gramm-Leach-Bliley Act (GLBA) Enhanced|- [Numer karty kredytowej](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Numer konta bankowego w Stanach Zjednoczonych](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [Numer identyfikacyjny indywidualnego podatnika w Stanach Zjednoczonych (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [Numer ubezpieczenia społecznego (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [Numer paszportu USA/Wielkiej Brytanii](sensitive-information-type-entity-definitions.md#usuk-passport-number) </br> -[Numer prawa jazdy w Stanach Zjednoczonych](sensitive-information-type-entity-definitions.md#us-drivers-license-number)</br> - [Wszystkie pełne nazwy](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [Adresy fizyczne w Stanach Zjednoczonych](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|Finansowych| U.S. Gramm-Leach-Bliley Act (GLBA)|- [Numer karty kredytowej](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Numer konta bankowego w Stanach Zjednoczonych](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [Numer identyfikacyjny indywidualnego podatnika w Stanach Zjednoczonych (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [Numer ubezpieczenia społecznego (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|
|Medycyna i zdrowie| Australia Health Records Act (HRIP Act) Enhanced |- [Numer pliku podatkowego Australii](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [Numer konta medycznego w Australii](sensitive-information-type-entity-definitions.md#australia-medical-account-number) </br> - [Wszystkie pełne nazwy](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [Wszystkie warunki i postanowienia medyczne](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions) </br> - [Adresy fizyczne w Australii](sensitive-information-type-entity-definitions.md#australia-physical-addresses)|
|Medycyna i zdrowie| Australia Health Records Act (HRIP Act)|- [Numer pliku podatkowego Australii](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [Numer konta medycznego w Australii](sensitive-information-type-entity-definitions.md#australia-medical-account-number)|
|Medycyna i zdrowie| Canada Health Information Act (HIA) |- [Numer paszportu Kanada](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Kanada numer ubezpieczenia społecznego](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Numer usługi kondycji Kanady](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Kanada Osobisty numer identyfikacyjny kondycji](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Medycyna i zdrowie| Kanada Personal Health Information Act (PHIA) Manitoba|- [Kanada numer ubezpieczenia społecznego](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Numer usługi kondycji Kanady](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Kanada Osobisty numer identyfikacyjny kondycji](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Medycyna i zdrowie| Kanada Personal Health Act (PHIPA) Ontario |- [Numer paszportu Kanada](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Kanada numer ubezpieczenia społecznego](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Numer usługi kondycji Kanady](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Kanada Osobisty numer identyfikacyjny kondycji](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Medycyna i zdrowie| WIELKIEJ BRYTANII. Ustawa o dostępie do raportów medycznych|- [Numer krajowej służby zdrowia w Zjednoczonym Zjednoczonym Kraju](sensitive-information-type-entity-definitions.md#uk-national-health-service-number) </br> - [Numer ubezpieczenia narodowego W. Brytanii (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino)|
|Medycyna i zdrowie| U.S. Health Insurance Act (HIPAA) Enhanced|</br> - [Międzynarodowa klasyfikacja chorób (ICD-9-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-9-cm) </br> - [Międzynarodowa klasyfikacja chorób (ICD-10-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-10-cm) </br> - [Wszystkie pełne nazwy](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [Wszystkie warunki i postanowienia medyczne](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions) </br> - [Adresy fizyczne w Stanach Zjednoczonych](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|Medycyna i zdrowie| U.S. Health Insurance Act (HIPAA)| - [Międzynarodowa klasyfikacja chorób (ICD-9-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-9-cm) </br> - [Międzynarodowa klasyfikacja chorób (ICD-10-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-10-cm)|
|Prywatność| Australia Privacy Act Enhanced|- [Numer prawa jazdy w Australii](sensitive-information-type-entity-definitions.md#australia-drivers-license-number) </br> - [Numer paszportu Australii](sensitive-information-type-entity-definitions.md#australia-passport-number) </br> - [Wszystkie pełne nazwy](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [Wszystkie warunki i postanowienia medyczne](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions) </br> - [Adresy fizyczne w Australii](sensitive-information-type-entity-definitions.md#australia-physical-addresses)|
|Prywatność| Australia Privacy Act|- [Numer prawa jazdy w Australii](sensitive-information-type-entity-definitions.md#australia-drivers-license-number) </br> - [Numer paszportu Australii](sensitive-information-type-entity-definitions.md#australia-passport-number)|
|Prywatność| Dane osobowe (PII) w Australii|- [Numer pliku podatkowego Australii](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [Numer prawa jazdy w Australii](sensitive-information-type-entity-definitions.md#australia-drivers-license-number)|
|Prywatność| Dane osobowe (PII) w Kanadzie|- [Numer prawa jazdy w Kanadzie](sensitive-information-type-entity-definitions.md#canada-drivers-license-number)</br> - [Numer konta bankowego w Kanadzie](sensitive-information-type-entity-definitions.md#canada-bank-account-number) </br> - [Numer paszportu Kanada](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Kanada numer ubezpieczenia społecznego](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Numer usługi kondycji Kanady](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Kanada Osobisty numer identyfikacyjny kondycji](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Prywatność| Canada Personal Information Protection Act (PIPA)|- [Numer paszportu Kanada](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Kanada numer ubezpieczenia społecznego](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Numer usługi kondycji Kanady](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Kanada Osobisty numer identyfikacyjny kondycji](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Prywatność| Canada Personal Information Protection Act (PIPEDA)|- [Numer prawa jazdy w Kanadzie](sensitive-information-type-entity-definitions.md#canada-drivers-license-number) </br> - [Numer konta bankowego w Kanadzie](sensitive-information-type-entity-definitions.md#canada-bank-account-number) </br> - [Numer paszportu Kanada](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Kanada numer ubezpieczenia społecznego](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Numer usługi kondycji Kanady](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Kanada Osobisty numer identyfikacyjny kondycji](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Prywatność| Francuska ustawa o ochronie danych|- [Francuski identyfikator krajowy (CNI)](sensitive-information-type-entity-definitions.md#france-national-id-card-cni) </br> - [Numer ubezpieczenia społecznego We Francji (INSEE)](sensitive-information-type-entity-definitions.md#france-social-security-number-insee)|
|Prywatność| Dane osobowe (PII) we Francji|- [Numer ubezpieczenia społecznego We Francji (INSEE)](sensitive-information-type-entity-definitions.md#france-social-security-number-insee) </br> - [Numer prawa jazdy we Francji](sensitive-information-type-entity-definitions.md#france-drivers-license-number) </br> - [Numer paszportu We Francji](sensitive-information-type-entity-definitions.md#france-passport-number) </br> - [Francuski identyfikator krajowy (CNI)](sensitive-information-type-entity-definitions.md#france-national-id-card-cni)|
|Prywatność| Rozszerzono ogólne rozporządzenie o ochronie danych (RODO)|- [Adresy fizyczne Austrii](sensitive-information-type-entity-definitions.md#austria-physical-addresses) </br> - [Adresy fizyczne Belgii](sensitive-information-type-entity-definitions.md#belgium-physical-addresses)</br> - [Adresy fizyczne Bułgarii](sensitive-information-type-entity-definitions.md#bulgaria-physical-addresses)</br> - [Adresy fizyczne Chorwacji](sensitive-information-type-entity-definitions.md#croatia-physical-addresses)</br> - [Adresy fizyczne cypryjskie](sensitive-information-type-entity-definitions.md#cyprus-physical-addresses)</br> - [Adresy fizyczne w Czechach](sensitive-information-type-entity-definitions.md#czech-republic-physical-addresses)</br> - [Duńskie adresy fizyczne](sensitive-information-type-entity-definitions.md#denmark-physical-addresses)</br> - [Adresy fizyczne Estonii](sensitive-information-type-entity-definitions.md#estonia-physical-addresses)</br> - [Adresy fizyczne Finlandii](sensitive-information-type-entity-definitions.md#finland-physical-addresses)</br> - [Adresy fizyczne We Francji](sensitive-information-type-entity-definitions.md#france-physical-addresses)</br> - [Adresy fizyczne w Niemczech](sensitive-information-type-entity-definitions.md#germany-physical-addresses)</br> - [Adresy fizyczne Grecji](sensitive-information-type-entity-definitions.md#greece-physical-addresses)</br> - [Węgierskie adresy fizyczne](sensitive-information-type-entity-definitions.md#hungary-physical-addresses)</br> - [Adresy fizyczne Irlandii](sensitive-information-type-entity-definitions.md#ireland-physical-addresses)</br> - [Włochy — adresy fizyczne](sensitive-information-type-entity-definitions.md#italy-physical-addresses)</br> - [Adresy fizyczne Łotwy](sensitive-information-type-entity-definitions.md#latvia-physical-addresses)</br> - [Adresy fizyczne Litwy](sensitive-information-type-entity-definitions.md#lithuania-physical-addresses)</br> - [Adresy fizyczne w Luksemburgu](sensitive-information-type-entity-definitions.md#luxemburg-physical-addresses)</br> - [Adresy fizyczne Malty](sensitive-information-type-entity-definitions.md#malta-physical-addresses)</br> - [Holenderskie adresy fizyczne](sensitive-information-type-entity-definitions.md#netherlands-physical-addresses)</br> - [Adresy fizyczne w Polsce](sensitive-information-type-entity-definitions.md#poland-physical-addresses)</br> - [Portugalskie adresy fizyczne](sensitive-information-type-entity-definitions.md#portugal-physical-addresses)</br> - [Adresy fizyczne Rumunii](sensitive-information-type-entity-definitions.md#romania-physical-addresses)</br> - [Adresy fizyczne Słowacji](sensitive-information-type-entity-definitions.md#slovakia-physical-addresses)</br> - [Adresy fizyczne Słowenii](sensitive-information-type-entity-definitions.md#slovenia-physical-addresses)</br> - [Adresy fizyczne Hiszpanii](sensitive-information-type-entity-definitions.md#spain-physical-addresses)</br> - [Adresy fizyczne Szwecji](sensitive-information-type-entity-definitions.md#sweden-physical-addresses)</br> - [Numer ubezpieczenia społecznego w Austrii](sensitive-information-type-entity-definitions.md#austria-social-security-number)</br> - [Francuski numer ubezpieczenia społecznego (INSEE)](sensitive-information-type-entity-definitions.md#france-social-security-number-insee)</br> - [Numer ubezpieczenia społecznego w Grecji (AMKA)](sensitive-information-type-entity-definitions.md#greece-social-security-number-amka)</br> - [Węgierski numer ubezpieczenia społecznego (TAJ)](sensitive-information-type-entity-definitions.md#hungary-social-security-number-taj)</br> - [Numer ubezpieczenia społecznego w Hiszpanii (SSN)](sensitive-information-type-entity-definitions.md#spain-social-security-number-ssn)</br> - [Austria Identity Card](sensitive-information-type-entity-definitions.md#austria-identity-card)</br> - [Cypr identity card](sensitive-information-type-entity-definitions.md#cyprus-identity-card)</br> - [Numer niemieckiego numeru karty tożsamości](sensitive-information-type-entity-definitions.md#germany-identity-card-number)</br> - [Numer karty tożsamości Malty](sensitive-information-type-entity-definitions.md#malta-identity-card-number)</br> - [Francuska krajowa karta tożsamości (CNI)](sensitive-information-type-entity-definitions.md#france-national-id-card-cni)</br> - [Grecja National ID Card](sensitive-information-type-entity-definitions.md#greece-national-id-card)</br> - [Identyfikator krajowy Finlandii](sensitive-information-type-entity-definitions.md#finland-national-id)</br> - [Polski identyfikator krajowy (PESEL)](sensitive-information-type-entity-definitions.md#poland-national-id-pesel)</br> - [Identyfikator krajowy Szwecji](sensitive-information-type-entity-definitions.md#sweden-national-id)</br> - [Numer identyfikacji osobistej Chorwacji (OIB)](sensitive-information-type-entity-definitions.md#croatia-personal-identification-oib-number)</br> - [Czeski numer tożsamości osobistej](sensitive-information-type-entity-definitions.md#czech-personal-identity-number)</br> - [Duński osobisty numer identyfikacyjny](sensitive-information-type-entity-definitions.md#denmark-personal-identification-number)</br> - [Estoński osobisty kod identyfikacyjny](sensitive-information-type-entity-definitions.md#estonia-personal-identification-code)</br> - [Węgierski osobisty numer identyfikacyjny](sensitive-information-type-entity-definitions.md#hungary-personal-identification-number)</br> - [Luksemburski krajowy numer identyfikacyjny (osoby fizyczne)](sensitive-information-type-entity-definitions.md#luxemburg-national-identification-number-natural-persons)</br> - [Luksemburski krajowy numer identyfikacyjny (osoby niebędące osobami fizycznymi)](sensitive-information-type-entity-definitions.md#luxemburg-national-identification-number-non-natural-persons)</br> - [Włoski kodeks obrachunkowy](sensitive-information-type-entity-definitions.md#italy-fiscal-code)</br> - [Kod osobisty Łotwy](sensitive-information-type-entity-definitions.md#latvia-personal-code)</br> - [Litewski kod osobisty](sensitive-information-type-entity-definitions.md#lithuania-personal-code)</br> - [Rumunia Osobisty kod numeryczny (CNP)](sensitive-information-type-entity-definitions.md#romania-personal-numeric-code-cnp)</br> - [Numer usługi obywatela Holandii (BSN)](sensitive-information-type-entity-definitions.md#netherlands-citizens-service-bsn-number)</br> - [Numer służby publicznej (PPS) w Irlandii](sensitive-information-type-entity-definitions.md#ireland-personal-public-service-pps-number)</br> - [Bułgaria — jednolity numer cywilny](sensitive-information-type-entity-definitions.md#bulgaria-uniform-civil-number)</br> - [Numer krajowy Belgii](sensitive-information-type-entity-definitions.md#belgium-national-number)</br> - [Hiszpania DNI](sensitive-information-type-entity-definitions.md#spain-dni)</br> - [Słoweński unikatowy główny numer obywatela](sensitive-information-type-entity-definitions.md#slovenia-unique-master-citizen-number)</br> - [Słowacja — numer osobisty](sensitive-information-type-entity-definitions.md#slovakia-personal-number)</br> - [Numer karty obywatela Portugalii](sensitive-information-type-entity-definitions.md#portugal-citizen-card-number)</br> - [Numer NIP Malty](sensitive-information-type-entity-definitions.md#malta-tax-identification-number)</br> - [Austriacki numer identyfikacji podatkowej](sensitive-information-type-entity-definitions.md#austria-tax-identification-number)</br> - [Numer identyfikacyjny podatku cypryjskiego](sensitive-information-type-entity-definitions.md#cyprus-tax-identification-number)</br> - [Francuski numer identyfikacji podatkowej (numéro SPI.)](sensitive-information-type-entity-definitions.md#france-tax-identification-number)</br> - [Numer NIP w Niemczech](sensitive-information-type-entity-definitions.md#germany-tax-identification-number)</br> - [Grecki numer identyfikacji podatkowej](sensitive-information-type-entity-definitions.md#greece-tax-identification-number)</br> - [Węgry Numer identyfikacji podatkowej](sensitive-information-type-entity-definitions.md#hungary-tax-identification-number)</br> - [Holenderski numer identyfikacji podatkowej](sensitive-information-type-entity-definitions.md#netherlands-tax-identification-number)</br> - [Numer NIP w Polsce](sensitive-information-type-entity-definitions.md#poland-tax-identification-number)</br> - [Numer identyfikacji podatkowej Portugalii](sensitive-information-type-entity-definitions.md#portugal-tax-identification-number)</br> - [Słoweński numer identyfikacji podatkowej](sensitive-information-type-entity-definitions.md#slovenia-tax-identification-number)</br> - [Numer identyfikacyjny podatku w Hiszpanii](sensitive-information-type-entity-definitions.md#spain-tax-identification-number)</br> - [Szwedzki numer identyfikacji podatkowej](sensitive-information-type-entity-definitions.md#sweden-tax-identification-number)</br> - [Austria Prawo jazdy](sensitive-information-type-entity-definitions.md#austria-drivers-license-number)</br> - [Belgijski numer prawa jazdy](sensitive-information-type-entity-definitions.md#belgium-drivers-license-number)</br> - [Bułgarski numer prawa jazdy](sensitive-information-type-entity-definitions.md#bulgaria-drivers-license-number)</br> - [Numer prawa jazdy Chorwacji](sensitive-information-type-entity-definitions.md#croatia-drivers-license-number)</br> - [Numer prawa jazdy cypryjskiego](sensitive-information-type-entity-definitions.md#cyprus-drivers-license-number)</br> - [Czeski numer prawa jazdy](sensitive-information-type-entity-definitions.md#czech-drivers-license-number)</br> - [Duński numer prawa jazdy](sensitive-information-type-entity-definitions.md#denmark-drivers-license-number)</br> - [Estoński numer prawa jazdy](sensitive-information-type-entity-definitions.md#estonia-drivers-license-number)</br> - [Numer prawa jazdy w Finlandii](sensitive-information-type-entity-definitions.md#finland-drivers-license-number)</br> - [Francuski numer prawa jazdy](sensitive-information-type-entity-definitions.md#france-drivers-license-number)</br> - [Niemiecki numer prawa jazdy](sensitive-information-type-entity-definitions.md#germany-drivers-license-number)</br> - [Grecja Numer prawa jazdy](sensitive-information-type-entity-definitions.md#greece-drivers-license-number)</br> - [Węgierski numer prawa jazdy](sensitive-information-type-entity-definitions.md#hungary-drivers-license-number)</br> - [Irlandzki numer prawa jazdy](sensitive-information-type-entity-definitions.md#ireland-drivers-license-number)</br> - [Włochy Numer prawa jazdy](sensitive-information-type-entity-definitions.md#italy-drivers-license-number)</br> - [Numer prawa jazdy Łotwy](sensitive-information-type-entity-definitions.md#latvia-drivers-license-number)</br> - [Litewski numer prawa jazdy](sensitive-information-type-entity-definitions.md#lithuania-drivers-license-number)</br> - [Luksemburski numer prawa jazdy](sensitive-information-type-entity-definitions.md#luxemburg-drivers-license-number)</br> - [Malta Numer prawa jazdy](sensitive-information-type-entity-definitions.md#malta-drivers-license-number)</br> - [Holenderski numer prawa jazdy](sensitive-information-type-entity-definitions.md#netherlands-drivers-license-number)</br> - [Numer polskiego prawa jazdy](sensitive-information-type-entity-definitions.md#poland-drivers-license-number)</br> - [Numer prawa jazdy Portugalia](sensitive-information-type-entity-definitions.md#portugal-drivers-license-number)</br> - [Rumunia Numer prawa jazdy](sensitive-information-type-entity-definitions.md#romania-drivers-license-number)</br> - [Słowacki numer prawa jazdy](sensitive-information-type-entity-definitions.md#slovakia-drivers-license-number)</br> - [Słoweński numer prawa jazdy](sensitive-information-type-entity-definitions.md#slovenia-drivers-license-number)</br> - [Numer hiszpańskiego prawa jazdy](sensitive-information-type-entity-definitions.md#spain-drivers-license-number)</br> - [Szwedzki numer prawa jazdy](sensitive-information-type-entity-definitions.md#sweden-drivers-license-number)</br> - [Numer paszportu Austrii](sensitive-information-type-entity-definitions.md#austria-passport-number)</br> - [Numer paszportu Belgia](sensitive-information-type-entity-definitions.md#belgium-passport-number)</br> - [Numer paszportu Bułgarii](sensitive-information-type-entity-definitions.md#bulgaria-passport-number)</br> - [Numer paszportu Chorwacji](sensitive-information-type-entity-definitions.md#croatia-passport-number)</br> - [Numer paszportu cypryjskiego](sensitive-information-type-entity-definitions.md#cyprus-passport-number)</br> - [Numer paszportu w Republice Czeskiej](sensitive-information-type-entity-definitions.md#czech-passport-number)</br> - [Duński numer paszportu](sensitive-information-type-entity-definitions.md#denmark-passport-number)</br> - [Numer paszportu Estonii](sensitive-information-type-entity-definitions.md#estonia-passport-number)</br> - [Numer paszportu Finlandii](sensitive-information-type-entity-definitions.md#finland-passport-number)</br> - [Numer paszportu Francji](sensitive-information-type-entity-definitions.md#france-passport-number)</br> - [Niemiecki numer paszportu](sensitive-information-type-entity-definitions.md#germany-passport-number)</br> - [Numer paszportu Grecji](sensitive-information-type-entity-definitions.md#greece-passport-number)</br> - [Węgierski numer paszportu](sensitive-information-type-entity-definitions.md#hungary-passport-number)</br> - [Numer paszportu Irlandii](sensitive-information-type-entity-definitions.md#ireland-passport-number)</br> - [Numer paszportu Włochy](sensitive-information-type-entity-definitions.md#italy-passport-number)</br> - [Numer paszportu łotwy](sensitive-information-type-entity-definitions.md#latvia-passport-number)</br> - [Litewski numer paszportu](sensitive-information-type-entity-definitions.md#lithuania-passport-number)</br> - [Numer paszportu luksemburski](sensitive-information-type-entity-definitions.md#luxemburg-passport-number)</br> - [Malta Passport Number](sensitive-information-type-entity-definitions.md#malta-passport-number)</br> - [Holenderski numer paszportu](sensitive-information-type-entity-definitions.md#netherlands-passport-number)</br> - [Polska Passport](sensitive-information-type-entity-definitions.md#poland-passport-number)</br> - [Numer paszportu Portugalii](sensitive-information-type-entity-definitions.md#portugal-passport-number)</br> - [Numer paszportu Rumunii](sensitive-information-type-entity-definitions.md#romania-passport-number)</br> - [Numer paszportu Słowacji](sensitive-information-type-entity-definitions.md#slovakia-passport-number)</br> - [Numer paszportu Słowenii](sensitive-information-type-entity-definitions.md#slovenia-passport-number)</br> - [Numer paszportu Hiszpanii](sensitive-information-type-entity-definitions.md#spain-passport-number)</br> - [Numer paszportu Szwecji](sensitive-information-type-entity-definitions.md#sweden-passport-number)</br> - [Numer karty debetowej UE](sensitive-information-type-entity-definitions.md#eu-debit-card-number)</br> - [Wszystkie pełne nazwy](sensitive-information-type-entity-definitions.md#all-full-names)|
|Prywatność| Ogólne rozporządzenie o ochronie danych (RODO)|- [Numer karty debetowej UE](sensitive-information-type-entity-definitions.md#eu-debit-card-number) </br> - [Numer prawa jazdy UE](sensitive-information-type-entity-definitions.md#eu-drivers-license-number) </br> - [Krajowy numer identyfikacyjny UE](sensitive-information-type-entity-definitions.md#eu-national-identification-number)</br> - [Numer paszportu UE](sensitive-information-type-entity-definitions.md#eu-passport-number) </br> - [Numer ubezpieczenia społecznego UE lub równoważna identyfikacja](sensitive-information-type-entity-definitions.md#eu-social-security-number-or-equivalent-identification)</br> - [Numer identyfikacji podatkowej UE](sensitive-information-type-entity-definitions.md#eu-tax-identification-number)|
|Prywatność| Dane osobowe (PII) w Niemczech|- [Numer niemieckiego prawa jazdy](sensitive-information-type-entity-definitions.md#germany-drivers-license-number) </br> - [Numer paszportu w Niemczech](sensitive-information-type-entity-definitions.md#germany-passport-number)| 
|Prywatność| Dane osobowe (PII) w Izraelu|- [Narodowy numer identyfikacyjny Izraela](sensitive-information-type-entity-definitions.md#israel-national-identification-number)| 
|Prywatność| Ochrona prywatności w Izraelu|- [Narodowy numer identyfikacyjny Izraela](sensitive-information-type-entity-definitions.md#israel-national-identification-number)</br> - [Numer konta bankowego Izraela](sensitive-information-type-entity-definitions.md#israel-bank-account-number)|
|Prywatność| Ulepszono dane danych osobowych (PII) w Japonii|- [Japoński numer ubezpieczenia społecznego (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin)</br> - [Japonia Mój numer - Osobisty](sensitive-information-type-entity-definitions.md#japan-my-number---personal)</br> - [Numer paszportu Japonii](sensitive-information-type-entity-definitions.md#japan-passport-number)</br> - [Numer japońskiego prawa jazdy](sensitive-information-type-entity-definitions.md#japan-drivers-license-number)</br> - [Wszystkie pełne nazwy](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [Japońskie adresy fizyczne](sensitive-information-type-entity-definitions.md#all-physical-addresses)|
|Prywatność| Dane osobowe (PII) w Japonii|- [Numer rejestracyjny rezydenta Japonii](sensitive-information-type-entity-definitions.md#japan-resident-registration-number) </br> - [Japoński numer ubezpieczenia społecznego (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin)|
|Prywatność| Zwiększono ochronę danych osobowych w Japonii|- [Japoński numer ubezpieczenia społecznego (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin) </br> - [Japonia Mój numer - Osobisty](sensitive-information-type-entity-definitions.md#japan-my-number---personal)</br> - [Numer paszportu Japonii](sensitive-information-type-entity-definitions.md#japan-passport-number) </br> - [Numer japońskiego prawa jazdy](sensitive-information-type-entity-definitions.md#japan-drivers-license-number)</br> - [Wszystkie pełne nazwy](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [Japońskie adresy fizyczne](sensitive-information-type-entity-definitions.md#all-physical-addresses)|
|Prywatność| Japonia Ochrona danych osobowych|- [Numer rejestracyjny rezydenta Japonii](sensitive-information-type-entity-definitions.md#japan-resident-registration-number)</br> - [Japoński numer ubezpieczenia społecznego (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin)|
|Prywatność| Dane osobowe (PII) w Arabii Saudyjskiej|- [Identyfikator narodowy Arabii Saudyjskiej](sensitive-information-type-entity-definitions.md#saudi-arabia-national-id)|
|Prywatność| WIELKIEJ BRYTANII. Ustawa o ochronie danych|- [Numer ubezpieczenia narodowego W. Brytanii (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino) </br> - [Numer paszportu USA/Wielkiej Brytanii](sensitive-information-type-entity-definitions.md#usuk-passport-number) </br> - [Kod SWIFT](sensitive-information-type-entity-definitions.md#swift-code)|
|Prywatność| WIELKIEJ BRYTANII. Przepisy dotyczące prywatności i komunikacji elektronicznej|- [Kod SWIFT](sensitive-information-type-entity-definitions.md#swift-code)|
|Prywatność| WIELKIEJ BRYTANII. Dane osobowe|- [Numer ubezpieczenia narodowego W. Brytanii (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino) </br> - [Numer paszportu USA/Wielkiej Brytanii](sensitive-information-type-entity-definitions.md#usuk-passport-number)|
|Prywatność| WIELKIEJ BRYTANII. Personal Information Online Code of Practice (PIOCP)|- [Numer ubezpieczenia narodowego W. Brytanii (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino) </br> - [Numer krajowej służby zdrowia w Zjednoczonym Zjednoczonym Kraju](sensitive-information-type-entity-definitions.md#uk-national-health-service-number) </br> - [Kod SWIFT](sensitive-information-type-entity-definitions.md#swift-code)|
|Prywatność| U.S Patriot Act Enhanced|- [Numer karty kredytowej](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Numer konta bankowego w Stanach Zjednoczonych](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [Numer identyfikacyjny indywidualnego podatnika w Stanach Zjednoczonych (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [Numer ubezpieczenia społecznego (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [Wszystkie pełne nazwy](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [Adresy fizyczne w Stanach Zjednoczonych](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|Prywatność| U.S. Patriot Act|- [Numer karty kredytowej](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Numer konta bankowego w Stanach Zjednoczonych](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [Numer identyfikacyjny indywidualnego podatnika w Stanach Zjednoczonych (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [Numer ubezpieczenia społecznego (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|
|Prywatność| Ulepszono dane osobowe (PII) w Stanach Zjednoczonych|- [Numer identyfikacyjny indywidualnego podatnika w Stanach Zjednoczonych (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [Numer ubezpieczenia społecznego (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [Numer paszportu USA/Wielkiej Brytanii](sensitive-information-type-entity-definitions.md#usuk-passport-number)</br> - [Wszystkie pełne nazwy](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [Adresy fizyczne w Stanach Zjednoczonych](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|Prywatność| Dane osobowe (PII) w Stanach Zjednoczonych|- [Numer identyfikacyjny indywidualnego podatnika w Stanach Zjednoczonych (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [Numer ubezpieczenia społecznego (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [Numer paszportu USA/Wielkiej Brytanii](sensitive-information-type-entity-definitions.md#usuk-passport-number)|
|Prywatność| Rozszerzono przepisy dotyczące powiadamiania o naruszeniach zabezpieczeń stanu USA|- [Numer karty kredytowej](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Numer konta bankowego w Stanach Zjednoczonych](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> -[Numer prawa jazdy w Stanach Zjednoczonych](sensitive-information-type-entity-definitions.md#us-drivers-license-number) </br> - [Numer ubezpieczenia społecznego (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [Wszystkie pełne nazwy](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [Numer paszportu USA/Wielkiej Brytanii](sensitive-information-type-entity-definitions.md#usuk-passport-number)</br> - [Wszystkie warunki i postanowienia medyczne](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions)|
|Prywatność| U.S. State Breach Notification Laws|- [Numer karty kredytowej](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Numer konta bankowego w Stanach Zjednoczonych](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> -[Numer prawa jazdy w Stanach Zjednoczonych](sensitive-information-type-entity-definitions.md#us-drivers-license-number) </br> - [Numer ubezpieczenia społecznego (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|
|Prywatność| U.S. State Social Security Number Confidentiality Laws|- [Numer ubezpieczenia społecznego (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|

## <a name="locations"></a>Lokalizacje

Zasady DLP mogą znajdować i chronić elementy zawierające poufne informacje w wielu lokalizacjach.

|Lokalizacja  |Uwzględnij/wyklucz zakres  |Stan danych  |Dodatkowe wymagania wstępne |
|---------|---------|---------|---------|
|Exchange wiadomości e-mail online |grupa dystrybucyjna | dane w ruchu| Nie |
|SharePoint witryn online   |Witryn       | dane magazynowane </br> dane w użyciu | Nie|
|konta OneDrive dla Firm| konto lub grupa dystrybucyjna |dane magazynowane </br> dane w użyciu|Nie|
|Teams wiadomości czatu i kanału     | konto lub grupa dystrybucyjna |dane w ruchu </br> dane w użyciu |  Nie       |
|Microsoft Defender for Cloud Apps   | wystąpienie aplikacji w chmurze       |dane magazynowane         | - [Używanie zasad ochrony przed utratą danych dla aplikacji w chmurze innych niż Microsoft](dlp-use-policies-non-microsoft-cloud-apps.md#use-data-loss-prevention-policies-for-non-microsoft-cloud-apps)        |
|Urządzeń  |użytkownik lub grupa         |dane magazynowane </br>  dane w użyciu </br>  dane w ruchu         |- [Dowiedz się więcej o zapobieganiu utracie danych punktu końcowego Microsoft 365](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention) </br>- [Wprowadzenie z zapobieganiem utracie danych punktu końcowego](endpoint-dlp-getting-started.md#get-started-with-endpoint-data-loss-prevention) </br>- [Konfigurowanie ustawień serwera proxy urządzenia i połączenia internetowego dla Information Protection](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection) |
|Repozytoria lokalne (udziały plików i SharePoint)    |Repozytorium         | dane magazynowane         | - [Dowiedz się więcej na temat lokalnego skanera Microsoft 365 zapobiegania utracie danych](dlp-on-premises-scanner-learn.md#learn-about-the-microsoft-365-data-loss-prevention-on-premises-scanner) </br> - [Wprowadzenie z lokalnym skanerem zapobiegania utracie danych](dlp-on-premises-scanner-get-started.md#get-started-with-the-data-loss-prevention-on-premises-scanner)         |
|PowerBI| Obszarów roboczych | dane w użyciu | Nie|

Jeśli zdecydujesz się uwzględnić określone grupy dystrybucyjne w Exchange, zasady DLP będą ograniczone tylko do członków tej grupy. Podobnie wykluczenie grupy dystrybucyjnej spowoduje wykluczenie wszystkich członków tej grupy dystrybucyjnej z oceny zasad. Możesz wybrać zakres zasad do elementów członkowskich list dystrybucyjnych, dynamicznych grup dystrybucyjnych i grup zabezpieczeń. Zasady DLP mogą zawierać nie więcej niż 50 takich wkluczeń i wykluczeń.

Jeśli zdecydujesz się dołączyć lub wykluczyć określone witryny SharePoint lub konta OneDrive, zasady DLP mogą zawierać nie więcej niż 100 takich dołączań i wykluczeń. Chociaż ten limit istnieje, możesz przekroczyć ten limit, stosując zasady dla całej organizacji lub zasady, które mają zastosowanie do całych lokalizacji.

Jeśli zdecydujesz się dołączyć lub wykluczyć określone OneDrive kont lub grup, zasady DLP mogą zawierać nie więcej niż 100 kont użytkowników lub 50 grup jako dołączenie lub wykluczenie.

### <a name="location-support-for-how-content-can-be-defined"></a>Obsługa lokalizacji dla sposobu definiowania zawartości

Zasady DLP wykrywają poufne elementy, dopasowując je do typu informacji poufnych (SIT), etykiety poufności lub etykiety przechowywania. Każda lokalizacja obsługuje różne metody definiowania poufnej zawartości. Po połączeniu lokalizacji w zasadach sposób definiowania zawartości może zmienić się od sposobu jej definiowania przez pojedynczą lokalizację. 

> [!IMPORTANT]
> Po wybraniu wielu lokalizacji dla zasad wartość "nie" dla kategorii definicji zawartości ma pierwszeństwo przed wartością "tak". Na przykład po wybraniu tylko SharePoint witryn zasady będą obsługiwać wykrywanie poufnych elementów przez co najmniej jeden element SIT, etykietę poufności lub etykietę przechowywania. Jednak po wybraniu SharePoint witryn ***i*** Teams lokalizacji komunikatów czatu i kanału zasady będą obsługiwać tylko wykrywanie poufnych elementów przez usługę SIT.

|Lokalizacja| Zawartość może być definiowana przez usługę SIT| Zawartość może być zdefiniowana etykietą poufności| Zawartość można zdefiniować za pomocą etykiety przechowywania|
|---------|---------|---------|---------|
|Exchange wiadomości e-mail online|Tak| Tak| Nie|
|SharePoint witryn online| Tak| Tak| Tak|
|konta OneDrive dla Firm| Tak| Tak| Tak|
|Teams wiadomości czatu i kanału | Tak| Nie| Nie|
|Urządzeń |Tak | Tak|  Nie|
|Microsoft Defender for Cloud Apps | Tak| Tak| Tak|
|Repozytoria lokalne| Tak| Tak| Nie|
|PowerBI|Tak | Tak| Nie|

> [!NOTE]
> DLP obsługuje wykrywanie etykiet poufności w wiadomościach e-mail i załącznikach Zobacz, [Używanie etykiet poufności jako warunków w zasadach DLP](dlp-sensitivity-label-as-condition.md#use-sensitivity-labels-as-conditions-in-dlp-policies).

## <a name="rules"></a>Reguły

<!--This section introduces the classifications of content that, when detected, can be protected. Link out to [Learn about sensitive information types]() and [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) as well as labels (cross referenced by supporting workload). It will touch on the purpose of multiple conditions, confidence levels (link out to [more on confidence levels](sensitive-information-type-learn-about.md#more-on-confidence-levels)) and confidence levels video. How to use the confidence level to change the behavior of a policy in conjunction with the instance count.  eg. if you want your policy to trigger when it encounters situation DEF, set your conditions like HIJ.-->
<!--
- What is a rule in the context of a Policy?
- when and why should I have more than one rule?
- The purpose of rule groups
- How do I tune the behavior of a Policy through the tuning of rules
- what's in a rule-->

Reguły to logika biznesowa zasad DLP. Składają się one z następujących elementów:

- [**Warunki**](#conditions) , które są dopasowane, wyzwalają zasady
- [**Wyjątki od**](#exceptions) warunków
- [**Akcje**](#actions) do wykonania po wyzwoleniu zasad
- [**Powiadomienia użytkowników**](#user-notifications-and-policy-tips) informujące użytkowników o wykonywaniu czynności wyzwalających zasady i ułatwiające informowanie ich o tym, jak organizacja chce traktować poufne informacje
- [**Przesłonięcia użytkownika**](#user-overrides) skonfigurowane przez administratora umożliwiają użytkownikom selektywne zastępowanie akcji blokującej
- [**Raporty o zdarzeniach**](#incident-reports) , które powiadamiają administratorów i innych kluczowych uczestników projektu w przypadku dopasowania reguły
- [**Dodatkowe opcje**](#additional-options) definiujące priorytet oceny reguł i mogą zatrzymać dalsze przetwarzanie reguł i zasad.

 Zasady zawierają co najmniej jedną regułę. Reguły są wykonywane sekwencyjnie, począwszy od reguły o najwyższym priorytecie w poszczególnych zasadach.

### <a name="the-priority-by-which-rules-are-processed"></a>Priorytet przetwarzania reguł

#### <a name="hosted-service-workloads"></a>Obciążenia usługi hostowanej

W przypadku obciążeń usługi hostowanej, takich jak Exchange Online, SharePoint Online i OneDrive dla Firm, każda reguła ma przypisany priorytet w kolejności, w jakiej została utworzona. Oznacza to, że utworzona reguła ma pierwszy priorytet, druga reguła ma drugi priorytet itd. 
  
![Reguły w kolejności priorytetów](../media/dlp-rules-in-priority-order.png)

Gdy zawartość jest oceniana względem reguł, reguły są przetwarzane w kolejności priorytetowej. Jeśli zawartość jest zgodna z wieloma regułami, zostanie wymuszona pierwsza reguła, która ma *najbardziej* restrykcyjną akcję. Jeśli na przykład zawartość jest zgodna ze wszystkimi następującymi regułami, *reguła 3* jest wymuszana, ponieważ jest to reguła o najwyższym priorytecie, najbardziej restrykcyjna:
  
- Reguła 1: powiadamia tylko użytkowników
- Reguła 2: powiadamia użytkowników, ogranicza dostęp i zezwala na przesłonięcia użytkowników
- *Reguła 3: powiadamia użytkowników, ogranicza dostęp i nie zezwala na przesłonięcia użytkowników*
- Reguła 4. Ogranicza dostęp

Reguły 1, 2 i 4 zostaną ocenione, ale nie zostaną zastosowane. W tym przykładzie dopasowania dla wszystkich reguł są rejestrowane w dziennikach inspekcji i wyświetlane w raportach DLP, mimo że zastosowano tylko najbardziej restrykcyjną regułę.

Reguła umożliwia spełnienie określonego wymagania dotyczącego ochrony, a następnie użycie zasad DLP w celu zgrupowania wspólnych wymagań dotyczących ochrony, takich jak wszystkie reguły wymagane do zapewnienia zgodności z określonym rozporządzeniem.
  
Na przykład mogą istnieć zasady DLP, które ułatwiają wykrywanie obecności informacji podlegających ustawie HIPAA (Health Insurance Portability and Accountability Act). Te zasady DLP mogą pomóc w ochronie danych HIPAA (co) we wszystkich witrynach SharePoint Online i wszystkich witrynach OneDrive dla Firm (gdzie), znajdując dowolny dokument zawierający te poufne informacje udostępniane osobom spoza organizacji (warunki), a następnie blokując dostęp do dokumentu i wysyłając powiadomienie (akcje). Te wymagania są przechowywane jako pojedyncze reguły i grupowane razem jako zasady DLP, aby uprościć zarządzanie i raportowanie.
  
![Diagram pokazuje, że zasady DLP zawierają lokalizacje i reguły](../media/c006860c-2d00-42cb-aaa4-5b5638d139f7.png)

#### <a name="for-endpoints"></a>W przypadku punktów końcowych

Priorytet dla reguł w punktach końcowych jest również przypisywany zgodnie z kolejnością jego utworzenia. Oznacza to, że utworzona reguła ma pierwszy priorytet, druga reguła ma drugi priorytet itd. 

Gdy plik w punkcie końcowym jest zgodny z wieloma zasadami DLP, pierwszą regułą, która jest włączona z najbardziej restrykcyjnym wymuszanie [działań punktu końcowego](endpoint-dlp-learn-about.md#endpoint-activities-you-can-monitor-and-take-action-on) , jest ta, która jest wymuszana na zawartości. Jeśli na przykład zawartość jest zgodna ze wszystkimi następującymi regułami, reguła 2 ma pierwszeństwo przed innymi regułami, ponieważ jest najbardziej restrykcyjna.

- Reguła 1. Tylko inspekcja wszystkich działań 
- *Reguła 2: blokuje wszystkie działania*
- Reguła 3: blokuje wszystkie działania z opcją zastąpienia przez użytkownika końcowego

W poniższym przykładzie reguła 1 ma pierwszeństwo przed innymi zgodnymi regułami, ponieważ jest najbardziej restrykcyjna.

- *Reguła 1: blokuje działanie i nie zezwala na zastępowanie przez użytkownika*
- Reguła 2: blokuje działanie i zezwala na przesłonięcia użytkowników
- Reguła 3. Tylko inspekcja wszystkich działań
- Reguła 4. Brak wymuszania

Wszystkie inne reguły są oceniane, ale ich akcje nie są wymuszane. Dzienniki inspekcji będą pokazywać najbardziej restrykcyjną regułę stosowaną w pliku. Jeśli istnieje więcej niż jedna reguła, która jest zgodna i są one równie restrykcyjne, zasady i priorytet reguły określają, która reguła będzie stosowana do pliku.

W przypadku punktów końcowych można skonfigurować akcje wykonywane przez DLP dla wszystkich obsługiwanych działań w jednej regule dla określonego zestawu warunków dołączania.

### <a name="conditions"></a>Warunki

Warunki są inkluzywne i są miejscem definiowania, czego chcesz szukać reguły i kontekstu, w którym te elementy są używane. Informują regułę &#8212;, gdy znajdziesz element, który wygląda *następująco* i jest używany w *ten* sposób, &#8212; jest to dopasowanie, a pozostałe akcje w zasadach powinny zostać wykonane. Warunki umożliwiają przypisanie różnych akcji do różnych poziomów ryzyka. Na przykład zawartość poufna udostępniana wewnętrznie może być mniejsza i wymagać mniejszej liczby akcji niż zawartość poufna udostępniana osobom spoza organizacji.

> [!NOTE]
> Użytkownicy, którzy mają konta niebędące gośćmi w usłudze Active Directory lub dzierżawie Azure Active Directory organizacji hosta, są uważane za osoby w organizacji. 

#### <a name="content-contains"></a>Zawartość zawiera

 Wszystkie lokalizacje obsługują warunek **Zawartość zawiera** . Możesz wybrać wiele wystąpień każdego typu zawartości i dodatkowo uściślić warunki przy użyciu **operatorów Dowolny z tych** (logicznych OR) lub **Wszystkie z tych** (logicznych AND):

- [typy informacji poufnych](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [etykiety poufności](sensitivity-labels.md)
- [etykiety przechowywania](retention.md#using-a-retention-label-as-a-condition-in-a-dlp-policy)

w zależności od [lokalizacji](#location-support-for-how-content-can-be-defined) , do których chcesz zastosować zasady. 

Reguła będzie szukać tylko obecności wybranych **etykiet poufności** i **etykiet przechowywania** . 

SIC mają wstępnie zdefiniowany [**poziom ufności**](https://www.microsoft.com/videoplayer/embed/RE4Hx60) , który można zmienić w razie potrzeby. Aby uzyskać więcej informacji, zobacz [Więcej informacji na temat poziomów ufności](sensitive-information-type-learn-about.md#more-on-confidence-levels). 

> [!IMPORTANT]
> Interfejsy SIC mają dwa różne sposoby definiowania maksymalnej liczby unikatowych parametrów liczby wystąpień. Aby dowiedzieć się więcej, zobacz [Liczba obsługiwanych wartości wystąpień dla usługi SIT](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit).

#### <a name="condition-context"></a>Kontekst warunku

Dostępne opcje kontekstu zmieniają się w zależności od wybranej lokalizacji. Jeśli wybierzesz wiele lokalizacji, dostępne są tylko wspólne warunki, które mają wspólne lokalizacje.

##### <a name="conditions-exchange-supports"></a>Obsługa warunków Exchange

- Zawartość zawiera
- Zawartość jest udostępniana z Microsoft 365
- Zawartość jest odbierana z
- Adres IP nadawcy jest
- Czy nadawca przesłaniał poradę dotyczącą zasad
- Nadawca jest
- Domena nadawcy jest
- Adres nadawcy zawiera wyrazy
- Adres nadawcy zawiera wzorce
- Atrybut usługi AD nadawcy zawiera wyrazy lub frazy
- Atrybut usługi AD nadawcy pasuje do wzorców
- Nadawca jest członkiem
- Nie można skanować zawartości załącznika wiadomości e-mail
- Zawartość załącznika wiadomości e-mail nie została ukończona podczas skanowania
- Załącznik jest chroniony hasłem
- Rozszerzenie pliku jest
- Adresat jest członkiem
- Domena adresata jest
- Adresat jest
- Adres odbiorcy zawiera wyrazy
- Adres odbiorcy pasuje do wzorców
- Atrybut usługi AD adresata zawiera wyrazy lub frazy
- Atrybut usługi AD odbiorcy pasuje do wzorców
- Nazwa dokumentu zawiera wyrazy lub frazy
- Nazwa dokumentu jest zgodna z wzorcami
- Właściwość dokumentu jest
- Rozmiar dokumentu jest równy lub większy niż
- Zawartość dokumentu zawiera słowa lub frazy
- Zawartość dokumentu pasuje do wzorców
- Temat zawiera wyrazy lub frazy
- Temat pasuje do wzorców
- Temat lub treść zawiera wyrazy lub frazy
- Obiekt lub treść pasują do wzorców
- Zestaw znaków zawartości zawiera wyrazy
- Nagłówek zawiera wyrazy lub frazy
- Nagłówek pasuje do wzorców
- Rozmiar komunikatu jest równy lub jest większy niż
- Typ komunikatu to
- Ważność komunikatu jest

##### <a name="conditions-sharepoint-supports"></a>Warunki, SharePoint obsługuje
 
- Zawartość zawiera
- Zawartość jest udostępniana z Microsoft 365
- Dokument utworzony przez
- Dokument utworzony przez członka
- Nazwa dokumentu zawiera wyrazy lub frazy
- Nazwa dokumentu jest zgodna z wzorcami
- Rozmiar dokumentu powyżej
- Właściwość dokumentu jest
- Rozszerzenie pliku jest

##### <a name="conditions-onedrive-accounts-supports"></a>Warunki, OneDrive konta obsługują

- Zawartość zawiera
- Zawartość jest udostępniana z Microsoft 365
- Dokument utworzony przez
- Dokument utworzony przez członka
- Nazwa dokumentu zawiera wyrazy lub frazy
- Nazwa dokumentu jest zgodna z wzorcami
- Rozmiar dokumentu powyżej
- Właściwość dokumentu jest
- Rozszerzenie pliku jest

##### <a name="conditions-teams-chat-and-channel-messages-supports"></a>Warunki Teams wiadomości czatu i kanału obsługują

- Zawartość zawiera
- Zawartość jest udostępniana z Microsoft 365
- Nadawca jest 
- Domena nadawcy jest 
- Domena adresata jest 
- Adresat jest 

##### <a name="conditions-devices-supports"></a>Warunki, które urządzenia obsługują

- Zawartość zawiera
- Zobacz [Działania punktu końcowego, które można monitorować i podejmować](endpoint-dlp-learn-about.md#endpoint-activities-you-can-monitor-and-take-action-on)

##### <a name="conditions-microsoft-defender-for-cloud-apps-supports"></a>Obsługa warunków Microsoft Defender for Cloud Apps

- Zawartość zawiera
- Zawartość jest udostępniana z Microsoft 365

##### <a name="conditions-on-premises-repositories-supports"></a>Repozytoria warunków lokalnych obsługują

- Zawartość zawiera
- Rozszerzenie pliku jest
- Właściwość dokumentu jest

##### <a name="conditions-powerbi-supports"></a>Warunki obsługiwane przez usługę PowerBI

- Zawartość zawiera

#### <a name="condition-groups"></a>Grupy warunków

Czasami potrzebujesz reguły, aby zidentyfikować tylko jedną rzecz, taką jak cała zawartość zawierająca numer ubezpieczenia społecznego w USA, który jest definiowany przez pojedyncze sit. Jednak w wielu scenariuszach, w których typy elementów, które próbujesz zidentyfikować, są bardziej złożone i dlatego trudniej je zdefiniować, wymagana jest większa elastyczność definiowania warunków.

Aby na przykład zidentyfikować zawartość objętą amerykańską ustawą o ubezpieczeniach zdrowotnych (HIPAA), należy poszukać następujących elementów:
  
- Zawartość, która zawiera określone typy informacji poufnych, takich jak numer ubezpieczenia społecznego USA lub numer Agencji Egzekwowania Narkotyków (DEA).
    
    I
    
- Zawartość, która jest trudniejsza do zidentyfikowania, taka jak komunikacja o opiece nad pacjentem lub opisy świadczonych usług medycznych. Zidentyfikowanie tej zawartości wymaga pasujących słów kluczowych z dużych list słów kluczowych, takich jak Międzynarodowa Klasyfikacja Chorób (ICD-9-CM lub ICD-10-CM).
    
Tego typu dane można zidentyfikować, grupując warunki i używając operatorów logicznych (AND, OR) między grupami.
    
W przypadku **amerykańskiej ustawy o ubezpieczeniach zdrowotnych (HIPPA)** warunki są pogrupowane w następujący sposób:

![Warunki zasad HIPPA](../media/dlp-rules-condition-groups-booleans.png)

Pierwsza grupa zawiera SIC identyfikujące i indywidualne, a druga zawiera SIC identyfikujące diagnostykę medyczną.

### <a name="exceptions"></a>Wyjątki

W regułach wyjątki definiują warunki, które są używane do wykluczania elementu z zasad. Logicznie wyłączne warunki, które są oceniane po warunkach inkluzywnych i kontekście. Mówią, że reguła &#8212;, gdy znajdziesz element, który wygląda *następująco* i jest używany w taki sposób *, że* jest zgodny, a pozostałe akcje w zasadach powinny zostać wykonane ***, chyba*** że... &#8212; 

Na przykład zgodnie z zasadami HIPPA możemy zmodyfikować regułę, aby wykluczyć dowolny element zawierający belgijski numer prawa jazdy, w następujący sposób:

![Zasady HIPPA z wykluczeniami](../media/dlp-rule-exceptions.png)

Warunki wyjątków obsługiwane przez lokalizację są identyczne ze wszystkimi warunkami dołączania, a jedyną różnicą jest wstępnie oczekujące wartości "Z wyjątkiem, jeśli" dla każdego obsługiwanego warunku. Jeśli reguła zawiera tylko wyjątki, będzie miała zastosowanie do wszystkich wiadomości e-mail lub plików, które nie spełniają kryteriów wykluczenia.

Tak jak wszystkie lokalizacje obsługują warunek inkluzywny:

- Zawartość zawiera

wyjątek:

- **Z wyjątkiem sytuacji, gdy** zawartość zawiera 

### <a name="actions"></a>Działania 

Każdy element, który przechodzi przez filtry uwzględniające ***warunki** _ i _*_wyjątki wyłączne_*_ , będzie miał wszystkie _*_akcje_*_ zdefiniowane w regule. Musisz skonfigurować wymagane opcje, aby obsługiwać akcję. Jeśli na przykład wybierzesz opcję Exchange z akcją _ *Ogranicz dostęp lub zaszyfruj zawartość w Microsoft 365 lokalizacjach**, musisz wybrać jedną z następujących opcji:

- Blokowanie użytkownikom dostępu do zawartości udostępnionych SharePoint, OneDrive i Teams
    - Blokuj wszystkich. Tylko właściciel zawartości, ostatni modyfikator i administrator witryny będą nadal mieć dostęp
    - Blokuj tylko osoby spoza organizacji. Użytkownicy w organizacji będą nadal mieć dostęp.
- Szyfrowanie wiadomości e-mail (dotyczy tylko zawartości w Exchange)

Akcje dostępne w regule zależą od wybranych lokalizacji. Jeśli wybierzesz tylko jedną lokalizację dla zasad, do których mają zostać zastosowane, dostępne akcje zostaną wymienione poniżej.

> [!IMPORTANT]
> W przypadku SharePoint Online i OneDrive dla Firm lokalizacji dokumenty będą aktywnie blokowane bezpośrednio po wykryciu informacji poufnych, niezależnie od tego, czy dokument jest udostępniony, czy nie, dla wszystkich użytkowników zewnętrznych, podczas gdy użytkownicy wewnętrzni będą nadal mieli dostęp do dokumentu.

#### <a name="exchange-location-actions"></a>akcje lokalizacji Exchange

- Ograniczanie dostępu lub szyfrowanie zawartości w Microsoft 365 lokalizacjach
- Ustawianie nagłówków
- Usuń nagłówek
- Przekierowywanie komunikatu do określonych użytkowników
- Przekazywanie komunikatu do zatwierdzenia do menedżera nadawcy
- Przekazywanie komunikatu do zatwierdzenia do określonych osób zatwierdzających
- Dodaj adresata do pola Do
- Dodawanie adresata do pola DW
- Dodawanie adresata do pola Bcc
- Dodawanie menedżera nadawcy jako adresata
- Usunięto szyfrowanie komunikatów O365 i ochronę praw
- Temat przedpłaty wiadomości e-mail
- Modyfikowanie tematu wiadomości e-mail
- Dodawanie zastrzeżenia HTML

#### <a name="sharepoint-sites-location-actions"></a>akcje lokalizacji lokacji SharePoint

- Ograniczanie dostępu lub szyfrowanie zawartości w Microsoft 365 lokalizacjach

#### <a name="onedrive-account-location-actions"></a>akcje lokalizacji konta OneDrive

- Ograniczanie dostępu lub szyfrowanie zawartości w Microsoft 365 lokalizacjach

#### <a name="teams-chat-and-channel-messages-actions"></a>Teams akcji wiadomości czatu i kanału

- Ograniczanie dostępu lub szyfrowanie zawartości w Microsoft 365 lokalizacjach

#### <a name="devices-actions"></a>Akcje urządzeń

- Inspekcja lub ograniczanie działań na urządzeniach Windows

Aby użyć tych ustawień, należy skonfigurować opcje w **ustawieniach DLP** i zasadach, w których mają być używane. Aby uzyskać więcej informacji, zobacz [Ograniczone aplikacje i grupy aplikacji](dlp-configure-endpoint-settings.md#restricted-apps-and-app-groups) .

Lokalizacja urządzeń udostępnia wiele działań podrzędnych (warunków) i akcji. Aby dowiedzieć się więcej, zobacz [Działania punktu końcowego, które można monitorować i podejmować działania](endpoint-dlp-learn-about.md#endpoint-activities-you-can-monitor-and-take-action-on).

Po wybraniu opcji **Inspekcja lub ograniczanie działań na urządzeniach Windows** można ograniczyć działania użytkownika według domeny usługi lub przeglądarki oraz określić zakres akcji wykonywanych przez program DLP:

- Wszystkie aplikacje
- Przez listę aplikacji z ograniczeniami, które definiujesz
- Zdefiniowana grupa aplikacji z ograniczeniami (wersja zapoznawcza).

##### <a name="service-domain-and-browser-activities"></a>Działania dotyczące domeny usługi i przeglądarki

Po skonfigurowaniu **listy Zezwalaj/Blokuj domeny usług w chmurze** i **Niezauzwalanych przeglądarek** (zobacz [Ograniczenia przeglądarki i domeny dla danych poufnych](dlp-configure-endpoint-settings.md#browser-and-domain-restrictions-to-sensitive-data)) użytkownik próbuje przekazać plik chroniony do domeny usługi w chmurze lub uzyskać do niego dostęp z niedozwolonej przeglądarki, można skonfigurować akcję zasad na `Audit only`wartość , `Block with override`lub `Block` działanie.

##### <a name="file-activities-for-all-apps"></a>Działania dotyczące plików dla wszystkich aplikacji

W przypadku opcji **Działania plików dla wszystkich aplikacji** wybierz opcję **Nie ograniczaj działań dotyczących plików** lub **Zastosuj ograniczenia do określonych działań**. Po wybraniu opcji stosowania ograniczeń do określonych działań akcje wybrane w tym miejscu są stosowane, gdy użytkownik uzyskuje dostęp do chronionego elementu DLP. W przypadku tych działań użytkownika można przekazać polecenie DLP do `Audit only`, `Block with override``Block` (akcje):

- **Kopiuj do schowka**
- **Kopiowanie na dysk wymienny USB** 
- **Kopiowanie do udziału sieciowego**
- **Drukowania**
- **Kopiowanie lub przenoszenie przy użyciu niedozwolonej aplikacji Bluetooth**
- **Usługi pulpitu zdalnego**


##### <a name="restricted-app-activities"></a>Działania aplikacji z ograniczeniami  

Wcześniej nazywane aplikacjami nieobsługiwanymi definiujesz listę aplikacji w ustawieniach DLP punktu końcowego, na których chcesz umieścić ograniczenia. Gdy użytkownik próbuje uzyskać dostęp do pliku chronionego przez protokół DLP przy użyciu aplikacji, która znajduje się na liście, możesz wykonać `Audit only``Block with override`działanie , lub `Block` . Akcje DLP zdefiniowane w **działaniach aplikacji z ograniczeniami** są zastępowane, jeśli aplikacja jest członkiem grupy aplikacji z ograniczeniami. Następnie zostaną zastosowane akcje zdefiniowane w grupie aplikacji z ograniczeniami.

##### <a name="file-activities-for-apps-in-restricted-app-groups-preview"></a>Działania dotyczące plików dla aplikacji w grupach aplikacji z ograniczeniami (wersja zapoznawcza)

Grupy aplikacji z ograniczeniami można zdefiniować w ustawieniach DLP punktu końcowego i dodać do zasad grupy aplikacji z ograniczeniami. Po dodaniu grupy aplikacji z ograniczeniami do zasad należy wybrać jedną z następujących opcji:

- Nie ograniczaj działania pliku
- Stosowanie ograniczeń do wszystkich działań
- Stosowanie ograniczeń do określonego działania

Po wybraniu jednej z opcji *Zastosuj ograniczenia* użytkownik próbuje uzyskać dostęp do pliku chronionego przez protokół DLP przy użyciu aplikacji należącej do grupy aplikacji z ograniczeniami, możesz wykonać `Audit only``Block with override`działanie , lub `Block` według działania. Akcje DLP zdefiniowane w tym miejscu przesłaniają akcje zdefiniowane w **działaniach aplikacji z ograniczeniami** i **działaniach plików dla wszystkich aplikacji** dla aplikacji.

Aby uzyskać więcej informacji, zobacz [Ograniczone aplikacje i grupy aplikacji](dlp-configure-endpoint-settings.md#restricted-apps-and-app-groups) . 

#### <a name="microsoft-defender-for-cloud-apps-actions"></a>akcje Microsoft Defender for Cloud Apps

- Ograniczanie dostępu lub szyfrowanie zawartości w Microsoft 365 lokalizacjach
- Ograniczanie aplikacji innych firm

#### <a name="on-premises-repositories-actions"></a>Akcje repozytoriów lokalnych

- Ograniczanie dostępu lub usuwanie plików lokalnych

#### <a name="powerbi-actions"></a>Akcje usługi PowerBI

- Powiadamianie użytkowników za pomocą wiadomości e-mail i wskazówek dotyczących zasad
- Wysyłanie alertów do administratora

#### <a name="actions-available-when-you-combine-locations"></a>Akcje dostępne podczas łączenia lokalizacji

Jeśli wybierzesz Exchange i dowolną inną pojedynczą lokalizację, do których mają zostać zastosowane zasady,

- Ograniczanie dostępu lub szyfrowanie zawartości w Microsoft 365 lokalizacjach

i

- wszystkie akcje dla lokalizacji innej niż Exchange

akcje będą dostępne.

Jeśli wybierzesz co najmniej dwie lokalizacje inne niż Exchange, do których mają zostać zastosowane zasady,

- Ograniczanie dostępu lub szyfrowanie zawartości w Microsoft 365 lokalizacjach

I

- wszystkie akcje dla lokalizacji innych niż Exchange 

akcje będą dostępne.

Jeśli na przykład wybierzesz opcję Exchange i Urządzenia jako lokalizacje, te akcje będą dostępne:

- Ograniczanie dostępu lub szyfrowanie zawartości w Microsoft 365 lokalizacjach
- Inspekcja lub ograniczanie działań na urządzeniach Windows

Jeśli wybierzesz pozycję Urządzenia i Microsoft Defender for Cloud Apps, te akcje będą dostępne:

- Ograniczanie dostępu lub szyfrowanie zawartości w Microsoft 365 lokalizacjach
- Inspekcja lub ograniczanie działań na urządzeniach Windows
- Ograniczanie aplikacji innych firm

To, czy akcja wchodzi w życie, czy nie, zależy od sposobu konfigurowania trybu zasad. Możesz uruchomić zasady w trybie testowym z lub bez wyświetlania wskazówek dotyczących zasad, wybierając **opcję Przetestuj je jako pierwszą** . Zasady należy uruchomić już po godzinie od jej utworzenia, wybierając opcję **Włącz od razu** lub możesz po prostu je zapisać i wrócić do niej później, wybierając opcję **Nie wyłączaj** . 


<!-- This section needs to explain that the actions available depend on the locations selected AND that the observed behavior of a policy is produced through an interaction of the configured actions AND the configured status (off, test, apply) of a policy. It will detail the purpose of each of the available actions and the location/desired outcome interaction and provide examples eg. how to use the Restrict Third Party apps in the context of a policy that is applied to endpoints so that users can't use a upload content to a third party site or the interaction of on-premises scanner with restrict access or remove on-premises files.  Also what happens when I select multiple locations? provide abundant examples for most common scenarios-->


### <a name="user-notifications-and-policy-tips"></a>Powiadomienia użytkowników i porady dotyczące zasad

<!--This section introduces the business need for user notifications, what they are, their benefit, how to use them, how to customize them, and links out to 

- https://docs.microsoft.com/en-us/microsoft-365/compliance/use-notifications-and-policy-tips?view=o365-worldwide
- https://docs.microsoft.com/en-us/microsoft-365/compliance/dlp-policy-tips-reference?view=o365-worldwide

for where they are used/expected behavior-->

<!--You can use notifications and overrides to educate your users about DLP policies and help them remain compliant without blocking their work. For example, if a user tries to share a document containing sensitive information, a DLP policy can both send them an email notification and show them a policy tip in the context of the document library that allows them to override the policy if they have a business justification.-->

Gdy użytkownik podejmie próbę wykonania akcji na poufnym elemencie w kontekście spełniającym warunki i wyjątki reguły, możesz poinformować go o tym za pośrednictwem wiadomości e-mail z powiadomieniami użytkownika i w wyskakującym okienku porad dotyczących zasad kontekstowych. Te powiadomienia są przydatne, ponieważ zwiększają świadomość i ułatwiają informowanie użytkowników o zasadach DLP organizacji.

Na przykład zawartość, taka jak skoroszyt Excel w witrynie OneDrive dla Firm, która zawiera dane osobowe i jest udostępniana gościowi.

![Pasek komunikatów zawiera poradę dotyczącą zasad w Excel 2016](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)

> [!NOTE]
> Wiadomości e-mail z powiadomieniami są wysyłane bez ochrony.

Możesz również dać użytkownikom możliwość [zastąpienia zasad](#user-overrides), aby nie były blokowane, jeśli mają prawidłową potrzebę biznesową lub jeśli zasady wykrywają wynik fałszywie dodatni.

Opcje konfiguracji powiadomień użytkownika i porad dotyczących zasad różnią się w zależności od wybranych lokalizacji monitorowania. Jeśli wybrano opcję:

- Exchange
- SharePoint
- OneDrive
- czat Teams i kanał
- Defender for Cloud Apps


Możesz włączyć/wyłączyć powiadomienia użytkowników dla różnych aplikacji firmy Microsoft. Zobacz [Informacje na temat porad dotyczących zasad ochrony przed utratą danych](dlp-policy-tips-reference.md#data-loss-prevention-policy-tips-reference)

- Możesz włączyć/wyłączyć **powiadamianie użytkowników w usłudze Office 365** za pomocą porady dotyczącej zasad.
    - powiadomienia e-mail do użytkownika, który wysłał, udostępnił lub ostatnio zmodyfikował zawartość LUB
    - powiadamianie określonych osób

i dostosuj tekst wiadomości e-mail, temat i tekst porad zasad.

![Opcje konfiguracji porad dotyczących powiadomień użytkowników i zasad, które są dostępne dla Exchange, SharePoint, OneDrive, czatu Teams i kanału oraz aplikacji Defender dla Chmury](../media/dlp-user-notification-non-devices.png)

Jeśli wybrano tylko pozycję Urządzenia, zostaną wyświetlone wszystkie te same opcje, które są dostępne dla Exchange, SharePoint, OneDrive, Teams czatu i kanału i aplikacji Defender dla Chmury, a także opcję dostosowania tytułu powiadomień i zawartości wyświetlanej na Windows 10 Urządzenia.

![Opcje konfiguracji powiadomień użytkownika i porad dotyczących zasad, które są dostępne dla urządzeń](../media/dlp-user-notification-devices.png)  

Tytuł i treść tekstu można dostosować przy użyciu tych parametrów. Tekst treści obsługuje następujące elementy:

|Nazwa pospolita  |Parametr  |Przykład
|---------|---------|---------|
|nazwa pliku     |%%Nazwa pliku%% | Contoso doc 1 |
|nazwa procesu     |%%ProcessName%% | Word |
|nazwa zasad     |%%PolicyName%%| Firma Contoso jest wysoce poufna |
|Działania | %%AppliedActions%% | wklejanie zawartości dokumentu ze schowka do innej aplikacji |

**%%AppliedActions%%** zastępuje te wartości treścią komunikatu:


|nazwa pospolita akcji |wartość zastąpiona parametrem %%AppliedActions%% |
|---------|---------|
|kopiowanie do magazynu z możliwością usunięcia    |*zapisywanie w magazynie wymiennym*         |
|kopiowanie do udziału sieciowego     |*zapisywanie w udziale sieciowym*         |
|Drukowania     |*Drukowanie*         |
|wklejanie ze schowka  |*wklejanie ze schowka*         |
|kopiowanie za pośrednictwem połączenia Bluetooth   |*przenoszenie za pośrednictwem Bluetooth*         |
|otwieranie za pomocą aplikacji, która nie jest dozwolona     |*otwieranie przy użyciu tej aplikacji*         |
|kopiowanie do pulpitu zdalnego (RDP)     |*przenoszenie do pulpitu zdalnego*         |
|przekazywanie do niedozwolonej witryny internetowej     |*przekazywanie do tej witryny*         |
|uzyskiwanie dostępu do elementu za pośrednictwem przeglądarki bez uprawnień     |*otwieranie za pomocą tej przeglądarki*         |

Korzystanie z tego dostosowanego tekstu

*%%AppliedActions%% Nazwa pliku %%FileName%% za pośrednictwem %%ProcessName%% nie jest dozwolona przez organizację. Kliknij pozycję Zezwalaj, jeśli chcesz pominąć zasady %%PolicyName%%* 

Tworzy ten tekst w dostosowanym powiadomieniu:

*wklejanie ze schowka Nazwa pliku: Contoso doc 1 za pośrednictwem WINWORD.EXE jest niedozwolone przez organizację. Kliknij przycisk "Zezwalaj", jeśli chcesz pominąć zasady, które firma Contoso jest wysoce poufna*
 

> [!NOTE]
> Powiadomienia użytkowników i wskazówki dotyczące zasad nie są dostępne dla lokalizacji lokalnej

> [!NOTE]
> Zostanie wyświetlona tylko porada dotycząca zasad o najwyższym priorytecie, najbardziej restrykcyjna reguła. Na przykład porada dotycząca zasad z reguły, która blokuje dostęp do zawartości, będzie wyświetlana za pośrednictwem wskazówki dotyczącej zasad z reguły, która po prostu wysyła powiadomienie. Uniemożliwia to użytkownikom wyświetlanie kaskady porad dotyczących zasad.

Aby dowiedzieć się więcej na temat konfiguracji i użycia porad dotyczących powiadomień użytkownika i zasad, w tym sposobu dostosowywania powiadomienia i tekstu porad, zobacz 
- [Wysyłanie powiadomień e-mail i wyświetlanie wskazówek dotyczących zasad dotyczących zasad DLP](use-notifications-and-policy-tips.md#send-email-notifications-and-show-policy-tips-for-dlp-policies).
  
<!--The email can notify the person who sent, shared, or last modified the content and, for site content, the primary site collection administrator and document owner. In addition, you can add or remove whomever you choose from the email notification.
  
In addition to sending an email notification, a user notification displays a policy tip:
  
- In Outlook and Outlook on the web.
    
- For the document on a SharePoint Online or OneDrive for Business site.
    
- In Excel, PowerPoint, and Word, when the document is stored on a site included in a DLP policy.
    
The email notification and policy tip explain why content conflicts with a DLP policy. If you choose, the email notification and policy tip can allow users to override a rule by reporting a false positive or providing a business justification. This can help you educate users about your DLP policies and enforce them without preventing people from doing their work. Information about overrides and false positives is also logged for reporting (see below about the DLP reports) and included in the incident reports (next section), so that the compliance officer can regularly review this information.
  
Here's what a policy tip looks like in a OneDrive for Business account.
  
![Policy tip for a document in a OneDrive account](../media/f9834d35-94f0-4511-8555-0fe69855ce6d.png)

 To learn more about user notifications and policy tips in DLP policies, see [Use notifications and policy tips](use-notifications-and-policy-tips.md).

> [!NOTE]
> The default behavior of a DLP policy, when there is no alert configured, is not to alert or trigger. This applies only to default information types. For custom information types, the system will alert even if there is no action defined in the policy.
-->

### <a name="user-overrides"></a>Przesłonięcia użytkownika

Celem **zastąpienia użytkownika** jest zapewnienie użytkownikom sposobu obejścia, z uzasadnieniem, blokowania akcji zasad DLP dla poufnych elementów w Exchange, SharePoint, OneDrive lub Teams, aby mogli kontynuować swoją pracę. Przesłonięcia użytkowników są włączane tylko wtedy, gdy włączono **powiadamianie użytkowników w usługach Office 365 z poradą dotyczącą zasad**, dlatego przesłonięcia użytkownika idą w parze z poradami dotyczącymi powiadomień i zasad. 

![Opcje zastępowania przez użytkownika zasad DLP](../media/dlp-user-overrides.png)

> [!NOTE]
> Przesłonięcia użytkownika nie są dostępne dla lokalizacji repozytoriów lokalnych.

Zazwyczaj przesłonięcia użytkowników są przydatne, gdy organizacja wprowadza zasady po raz pierwszy. Opinie otrzymane z wszelkich uzasadnień zastąpienia i identyfikowania wyników fałszywie dodatnich ułatwiają dostrajanie zasad. 

<!-- This section covers what they are and how to best use them in conjunction with Test/Turn it on right away and link out to where to find the business justification for the override (DLP reports?  https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide)  https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide#view-the-justification-submitted-by-a-user-for-an-override-->

- Jeśli wskazówki dotyczące zasad w najbardziej restrykcyjnej regule zezwalają użytkownikom na zastąpienie reguły, zastąpienie tej reguły zastępuje również wszelkie inne reguły dopasowane do zawartości.
 
<!--![User notifications and user overrides sections of DLP rule editor](../media/37b560d4-6e4e-489e-9134-d4b9daf60296.png)-->
 
Aby dowiedzieć się więcej na temat przesłonięcia użytkowników, zobacz:

- [Wyświetlanie uzasadnienia przesłanego przez użytkownika w celu zastąpienia](view-the-dlp-reports.md#view-the-justification-submitted-by-a-user-for-an-override)

### <a name="incident-reports"></a>Raporty o zdarzeniach

<!--DLP interacts with other M365 information protection services, like IR. Link this to a process outline for triaging/managing/resolving DLP incidents


https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide
https://docs.microsoft.com/en-us/microsoft-365/compliance/dlp-configure-view-alerts-policies?view=o365-worldwide-->

Po dopasowaniu reguły możesz wysłać raport o zdarzeniu do oficera zgodności (lub dowolnych wybranych osób) ze szczegółami zdarzenia. Raport zawiera informacje o dopasowanym elemencie, rzeczywistej zawartości zgodnej z regułą oraz o nazwie osoby, która ostatnio zmodyfikowała zawartość. W przypadku wiadomości e-mail raport zawiera również jako załącznik oryginalną wiadomość zgodną z zasadami DLP.

DLP przesyła informacje o zdarzeniach do innych Microsoft 365 usług ochrony informacji, takich jak [zarządzanie ryzykiem wewnętrznym w Microsoft 365](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365). Aby uzyskać informacje o zdarzeniach do zarządzania ryzykiem wewnętrznym, należy ustawić poziom ważności **raportów o zdarzeniach** na **wysoki**.

<!--![Page for configuring incident reports](../media/31c6da0e-981c-415e-91bf-d94ca391a893.png)-->

Alerty mogą być wysyłane za każdym razem, gdy działanie jest zgodne z regułą, która może być hałaśliwa lub może być agregowana na mniejszą liczbę alertów na podstawie liczby dopasowań lub liczby elementów w określonym okresie.

![wysyłanie alertu za każdym razem, gdy reguła dopasowuje lub agreguje w czasie mniejszą liczbę raportów](../media/dlp-incident-reports-aggregation.png)

DLP skanuje pocztę e-mail inaczej niż SharePoint online lub OneDrive dla Firm elementów. W usłudze SharePoint Online i OneDrive dla Firm usługa DLP skanuje istniejące elementy, a także nowe i generuje raport o zdarzeniu za każdym razem, gdy zostanie znalezione dopasowanie. W Exchange Online usługa DLP skanuje nowe wiadomości e-mail i generuje raport tylko wtedy, gdy istnieje dopasowanie zasad. DLP ***nie*** skanuje ani nie pasuje do wcześniej istniejących elementów poczty e-mail przechowywanych w skrzynce pocztowej lub archiwum.

### <a name="additional-options"></a>Opcje dodatkowe

Jeśli w zasadach znajduje się wiele reguł, możesz użyć **opcji Dodatkowe** , aby kontrolować dalsze przetwarzanie reguł, jeśli istnieje dopasowanie do edytowanej reguły, a także ustawić priorytet oceny reguły.

## <a name="see-also"></a>Zobacz też

- [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Planowanie zapobiegania utracie danych (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [Twórz zasady DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md#create-a-dlp-policy-from-a-template)
- [Twórz, testuj i dostrajaj zasady DLP](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)
