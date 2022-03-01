---
title: Ochrona informacji dla firmy Contoso Corporation
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
ms.date: 10/02/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
ms.custom: ''
description: Zrozumienie, jak firma Contoso korzysta z funkcji ochrony informacji Microsoft 365 firmy Microsoft 365 przedsiębiorstwa w celu zabezpieczenia swoich cyfrowych zasobów w chmurze.
ms.openlocfilehash: 1dff2cadd5afa66b3b469a2debedddbb347db0e5
ms.sourcegitcommit: 07405a81513d1c63071a128b9d5070d3a3bfe1cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "63007041"
---
# <a name="information-protection-for-the-contoso-corporation"></a>Ochrona informacji dla firmy Contoso Corporation

Firma Contoso poważnie podejmuje swoje bezpieczeństwo informacji. Wyciek lub ochrona własności intelektualnej, która opisuje projekty ich produktów i własne techniki produkcyjne, mogą stanowić ich wadę konkurencyjności.

Przed przeniesieniem poufnych zasobów cyfrowych do chmury firma Contoso upewniała się, że ich lokalne wymagania dotyczące klasyfikacji i ochrony informacji były obsługiwane przez usługi chmurowe usługi Microsoft 365 dla przedsiębiorstw.

## <a name="contoso-data-security-classification"></a>Klasyfikacja zabezpieczeń danych contoso

Firma Contoso wykonała analizę danych i ustaliła następujące poziomy klasyfikacji.

| Poziom 1: Plan bazowy | Poziom 2. Poufne | Poziom 3. Wysoce uregulowane |
|:-------|:-----|:-----|
| Dane są szyfrowane i dostępne tylko dla uwierzytelnionych użytkowników.<BR> <BR> Są one udostępniane dla wszystkich danych przechowywanych lokalnie oraz w opartym na chmurze magazynie i obciążeniach pracą. Dane są szyfrowane, gdy znajdują się w usłudze i w trakcie przesyłania między usługą a urządzeniami klienckimi. <BR><BR>Przykładami danych poziomu 1 są normalna komunikacja biznesowa (poczta e-mail) i pliki dla pracowników administracyjnych, sprzedaży i pomocy technicznej. | Poziom 1 oraz silne uwierzytelnianie i ochrona przed utratą danych.<BR> <BR> Silne uwierzytelnianie obejmuje uwierzytelnianie wieloskładnikowe (MFA) usługi Azure AD ze sprawdzaniem poprawności wiadomości SMS. Ochrona przed utratą danych gwarantuje, że informacje poufne lub krytyczne nie trafią poza chmurę firmy Microsoft.<BR><BR>Przykładami danych poziomu 2 są informacje finansowe i prawne oraz dane dotyczące badań i rozwoju nowych produktów. | Poziom 2 oraz najwyższe poziomy szyfrowania, uwierzytelniania i inspekcji.<BR><BR>Najwyższe poziomy szyfrowania danych w spoczynku i w chmurze, zgodne z przepisami regionalnymi, w połączeniu z uwierzytelniania wieloskładnikowego z kartami inteligentnymi oraz szczegółową inspekcją i alertami.<BR> <BR>Przykładami danych poziomu 3 są dane osobowe klientów i partnerów, specyfikacje techniczne produktów i własne techniki produkcyjne.  |
||||

## <a name="contoso-information-policies"></a>Zasady dotyczące informacji o firmie Contoso
W poniższej tabeli wymieniono zasady dotyczące informacji Contoso.


| Value | Access | Przechowywanie danych | Ochrona informacji |
|:-------|:-----|:-----|:-----|
| Niska wartość biznesowa (poziom 1: plan bazowy) | Zezwalaj na dostęp do wszystkich.  | 6 miesięcy | Użyj szyfrowania. |
| Średnia wartość biznesowa (poziom 2: poufne) | Zezwalaj na dostęp pracownikom firmy Contoso, podwykonawcom i partnerom. <BR><BR> Korzystanie z uwierzytelniania wieloskładnikowego, zabezpieczeń transport layer (TLS) i zarządzania aplikacjami mobilnymi (MAM). | 2 lata  | Aby zapewnić integralność danych, użyj wartości skrótów.  |
| Wysoka wartość biznesowa (poziom 3: ściśle uregulowane) | Umożliwianie dostępu kadry kierowniczej i potencjalnych klientów w zakresie inżynierii i produkcji. <BR> <BR> System zarządzania prawami (RMS) tylko z zarządzanymi urządzeniami sieciowymi.  | 7 lat  | Nie można ponownie użyć podpisów cyfrowych.  |
|||||

## <a name="the-contoso-path-to-information-protection-with-microsoft-365-for-enterprise"></a>Ścieżka firmy Contoso do ochrony informacji w aplikacji Microsoft 365 przedsiębiorstwa

Firma Contoso wykonać poniższe kroki w celu przygotowania Microsoft 365 dla przedsiębiorstwa na potrzeby ochrony informacji:

1. Określanie informacji, które mają być chronine

   Firma Contoso przeglądała swoje istniejące zasoby cyfrowe znajdujące się w lokalnych witrynach SharePoint udziałach plików i klasyfikowała poszczególne zasoby.

2. Określanie zasad dostępu, przechowywania i ochrony informacji dla poziomów danych

   Na podstawie poziomów danych firma Contoso ustaliła szczegółowe wymagania dotyczące zasad, które zostały użyte do ochrony istniejących zasobów cyfrowych po ich przeniesionej do chmury.

3. Tworzenie etykiet wrażliwości i ich ustawień dla różnych poziomów informacji

   Etykiety wrażliwości firmy Contoso na ich poziomy danych są oznaczone etykietami o wysokim poziomie regulacji, które obejmują szyfrowanie, uprawnienia i znaki wodne.

4. Przenoszenie danych z lokalnych witryn SharePoint i udziałów plików do nowych SharePoint witryn

    Pliki migrowane do nowych witryn SharePoint dziedziczyły domyślne etykiety przechowywania przypisane do witryny.

5. Szkolenie pracowników w jaki sposób używać etykiet wrażliwości w nowych dokumentach, jak korzystać z działu IT firmy Contoso podczas tworzenia nowych witryn SharePoint sieci Web oraz jak zawsze przechowywać zasoby cyfrowe w witrynach SharePoint internetowych

    Zmiana nawyków dotyczących przechowywania informacji złych pracowników jest często uważana za najbardziej trudny element przejścia do ochrony informacji w chmurze. Pracownicy it i kierownictwo firmy Contoso musieli zawsze oznaczać i przechowywać swoje zasoby cyfrowe w chmurze bez używania lokalnych udziałów plików i nie korzystaj z usług magazynu w chmurze innych firm ani dysków USB.

## <a name="conditional-access-policies-for-information-protection"></a>Zasady dostępu warunkowego w celu ochrony informacji

W ramach tego programu firma Contoso Exchange Online i SharePoint, skonfigurowała następujący zestaw zasad dostępu warunkowego i stosować je do odpowiednich grup:

- [Zasady zarządzania dostępem do aplikacji na urządzeniach i zarządzanie nimi](../security/office-365-security/identity-access-policies.md)
- [Exchange Online dostępu](../security/office-365-security/secure-email-recommended-policies.md)
- [SharePoint dostępu](../security/office-365-security/sharepoint-file-access-policies.md)

Oto wynikowy zestaw zasad firmy Contoso dotyczących ochrony informacji.

:::image type="content" alt-text="Urządzenia, Exchange Online i SharePoint dostęp warunkowy." source="../media/contoso-info-protect/contoso-info-protect-fig1.png" lightbox="../media/contoso-info-protect/contoso-info-protect-fig1.png":::

>[!Note]
>Firma Contoso skonfigurowała również dodatkowe zasady dostępu warunkowego dla tożsamości i logowania. Zobacz [Tożsamość firmy Contoso Corporation](contoso-identity.md#conditional-access-policies-for-zero-trust-identity-and-device-access).
>

Te zasady zapewniają:

- Dozwolone aplikacje i akcje, które mogą być podejmowane wraz z danymi organizacji, są definiowane przez zasady ochrony aplikacji.
- Komputery i urządzenia przenośne muszą być zgodne.
- Exchange Online wiadomości Office 365 szyfrowanie wiadomości (OME, Message Encryption) do Exchange Online.
- SharePoint są używane ograniczenia wymuszane przez aplikacje.
- SharePoint kontroli dostępu na urządzeniach niezawiązywanych korzysta z zasad kontroli dostępu, które są dostępne tylko w przeglądarce.

## <a name="mapping-microsoft-365-for-enterprise-features-to-contoso-data-levels"></a>Mapowanie Microsoft 365 funkcji przedsiębiorstwa na poziomy danych Contoso

W poniższej tabeli poziomy danych firmy Contoso są mapowe na funkcje ochrony informacji Microsoft 365 przedsiębiorstwa.

| Poziom | Microsoft 365 usług w chmurze | Windows 10 i Aplikacje Microsoft 365 dla przedsiębiorstw | Zabezpieczenia i zgodność |
|:-------|:-----|:-----|:-----|
| Poziom 1: Plan bazowy  | SharePoint i Exchange Online dostępu warunkowego <BR> Uprawnienia dotyczące SharePoint witryn | Etykiety wrażliwości <BR> BitLocker <BR> Windows informacji | Zasady dostępu warunkowego urządzenia i zasady zarządzania aplikacją mobilną |
| Poziom 2. Poufne | Poziom 1 oraz: <BR> <BR> Etykiety wrażliwości <BR> Microsoft 365 przechowywania w witrynach SharePoint sieci Web <BR> Ochrona przed utratą danych w SharePoint i Exchange Online <BR> Odizolowane SharePoint witryn  | Poziom 1 oraz: <BR> <BR> Etykiety wrażliwości na zasoby cyfrowe  | Poziom 1 |
| Poziom 3. Wysoce uregulowane | Poziom 2 oraz: <BR><BR> Przyniesij własne szyfrowanie i ochronę klucza (BYOK) dla informacji tajemnic handlowych <BR> Magazyn kluczy platformy Azure dla aplikacji biznesowych, które współdziałają z Microsoft 365 biznesowymi | Poziom 2 | Poziom 1 |
|||||

Oto wynikowa konfiguracja ochrony informacji firmy Contoso.

:::image type="content" alt-text="Wynikowa konfiguracja ochrony informacji firmy Contoso." source="../media/contoso-info-protect/contoso-info-protect-fig2.png":::

## <a name="next-step"></a>Następny krok

Dowiedz się, jak firma Contoso używa [funkcji zabezpieczeń w całej firmie Microsoft 365 przedsiębiorstwa](contoso-security-summary.md) w zakresie zarządzania tożsamościami i dostępem, ochrony przed zagrożeniami, ochrony informacji i zarządzania zabezpieczeniami.

## <a name="see-also"></a>Zobacz też

[Plan zabezpieczeń](../security/office-365-security/security-roadmap.md)

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Przewodniki laboratorium testowego](m365-enterprise-test-lab-guides.md)