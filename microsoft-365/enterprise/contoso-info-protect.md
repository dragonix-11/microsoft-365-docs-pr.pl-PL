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
description: Dowiedz się, jak firma Contoso używa funkcji ochrony informacji w Microsoft 365 dla przedsiębiorstw w celu zabezpieczenia zasobów cyfrowych w chmurze.
ms.openlocfilehash: 70d5a0a6fba7204177771256d9a508c76a010d6d
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64931588"
---
# <a name="information-protection-for-the-contoso-corporation"></a>Ochrona informacji dla firmy Contoso Corporation

Firma Contoso poważnie traktuje swoje bezpieczeństwo informacji. Wyciek lub zniszczenie własności intelektualnej opisujące ich projekty produktów i zastrzeżone techniki produkcji postawiłyby je w niekorzystnej sytuacji konkurencyjnej.

Przed przeniesieniem poufnych zasobów cyfrowych do chmury firma Contoso upewniła się, że wymagania dotyczące klasyfikacji i ochrony informacji lokalnych są obsługiwane przez oparte na chmurze usługi Microsoft 365 dla przedsiębiorstw.

## <a name="contoso-data-security-classification"></a>Klasyfikacja zabezpieczeń danych firmy Contoso

Firma Contoso wykonała analizę swoich danych i określiła następujące poziomy klasyfikacji.

| Poziom 1: Punkt odniesienia | Poziom 2: poufny | Poziom 3: Wysoce regulowane |
|:-------|:-----|:-----|
| Dane są szyfrowane i dostępne tylko dla uwierzytelnionych użytkowników.<BR> <BR> Zapewniane dla wszystkich danych przechowywanych lokalnie oraz w magazynie i obciążeniach opartych na chmurze. Dane są szyfrowane, gdy znajdują się w usłudze i są przesyłane między usługą a urządzeniami klienckimi. <BR><BR>Przykłady danych poziomu 1 to normalna komunikacja biznesowa (poczta e-mail) i pliki dla pracowników administracyjnych, sprzedaży i pomocy technicznej. | Poziom 1 oraz silne uwierzytelnianie i ochrona przed utratą danych.<BR> <BR> Silne uwierzytelnianie obejmuje uwierzytelnianie wieloskładnikowe usługi Azure AD (MFA) z weryfikacją wiadomości SMS. Ochrona przed utratą danych w usłudze Microsoft Purview zapewnia, że poufne lub krytyczne informacje nie przemieszczają się poza chmurę firmy Microsoft.<BR><BR>Przykładami danych poziomu 2 są informacje finansowe i prawne oraz dane badawcze i rozwojowe dotyczące nowych produktów. | Poziom 2 oraz najwyższy poziom szyfrowania, uwierzytelniania i inspekcji.<BR><BR>Najwyższy poziom szyfrowania danych magazynowanych i w chmurze, zgodny z przepisami regionalnymi w połączeniu z uwierzytelnianiem wieloskładnikowym z kartami inteligentnymi oraz szczegółową inspekcją i alertami.<BR> <BR>Przykłady danych poziomu 3 to dane osobowe klientów i partnerów, specyfikacje inżynierii produktu i zastrzeżone techniki produkcyjne.  |
||||

## <a name="contoso-information-policies"></a>Zasady informacji firmy Contoso
W poniższej tabeli wymieniono zasady informacji firmy Contoso.


| Value | Access | Przechowywanie danych | Ochrona informacji |
|:-------|:-----|:-----|:-----|
| Niska wartość biznesowa (poziom 1: punkt odniesienia) | Zezwalaj na dostęp do wszystkich.  | 6 miesięcy | Użyj szyfrowania. |
| Średnia wartość biznesowa (poziom 2: poufny) | Zezwalaj na dostęp do pracowników, podwykonawców i partnerów firmy Contoso. <BR><BR> Użyj uwierzytelniania wieloskładnikowego, zabezpieczeń warstwy transportu (TLS) i zarządzania aplikacjami mobilnymi (MAM). | 2 lata  | Użyj wartości skrótu, aby uzyskać integralność danych.  |
| Wysoka wartość biznesowa (poziom 3: wysoce regulowane) | Zezwalaj na dostęp do kadry kierowniczej i potencjalnych klientów w dziedzinie inżynierii i produkcji. <BR> <BR> System zarządzania prawami (RMS) tylko z zarządzanymi urządzeniami sieciowymi.  | 7 lat  | Użyj podpisów cyfrowych w przypadku braku odrzucenia.  |
|||||

## <a name="the-contoso-path-to-information-protection-with-microsoft-365-for-enterprise"></a>Ścieżka firmy Contoso do ochrony informacji za pomocą Microsoft 365 dla przedsiębiorstw

Firma Contoso wykonaj następujące kroki, aby przygotować Microsoft 365 dla przedsiębiorstw do spełnienia wymagań dotyczących ochrony informacji:

1. Identyfikowanie informacji, które mają być chronione

   Firma Contoso dokonała obszernego przeglądu istniejących zasobów cyfrowych znajdujących się w lokalnych SharePoint witrynach i udziałach plików oraz sklasyfikowała każdy zasób.

2. Określanie zasad dostępu, przechowywania i ochrony informacji dla poziomów danych

   Na podstawie poziomów danych firma Contoso określiła szczegółowe wymagania dotyczące zasad, które były używane do ochrony istniejących zasobów cyfrowych w miarę ich przenoszenia do chmury.

3. Tworzenie etykiet poufności i ich ustawień dla różnych poziomów informacji

   Firma Contoso utworzyła etykiety poufności dla swoich poziomów danych za pomocą wysoce regulowanej etykiety, która obejmuje szyfrowanie, uprawnienia i znaki wodne.

4. Przenoszenie danych z lokalnych witryn SharePoint i udziałów plików do nowych witryn SharePoint

    Pliki zmigrowane do nowych witryn SharePoint dziedziczyły domyślne etykiety przechowywania przypisane do witryny.

5. Szkolenie pracowników, jak używać etykiet poufności dla nowych dokumentów, jak korzystać z działu IT firmy Contoso podczas tworzenia nowych witryn SharePoint i zawsze przechowywać zasoby cyfrowe w SharePoint lokacjach

    Zmiana złych nawyków przechowywania informacji pracowników jest często uważana za najtrudniejszą część przejścia na ochronę informacji w chmurze. Contoso IT and management needed to get employees to always label and store their digital assets in the cloud, refrain from using on-premises file shares, and not use third-party cloud storage services or USB drive.

## <a name="conditional-access-policies-for-information-protection"></a>Zasady dostępu warunkowego na potrzeby ochrony informacji

W ramach wdrażania Exchange Online i SharePoint firma Contoso skonfigurowała następujący zestaw zasad dostępu warunkowego i zastosowała je do odpowiednich grup:

- [Dostęp do aplikacji zarządzanych i niezarządzanych na zasadach urządzeń](../security/office-365-security/identity-access-policies.md)
- [zasady dostępu Exchange Online](../security/office-365-security/secure-email-recommended-policies.md)
- [zasady dostępu SharePoint](../security/office-365-security/sharepoint-file-access-policies.md)

Oto zestaw zasad firmy Contoso na potrzeby ochrony informacji.

:::image type="content" alt-text="Zasady dostępu warunkowego urządzenia, Exchange Online i SharePoint." source="../media/contoso-info-protect/contoso-info-protect-fig1.png" lightbox="../media/contoso-info-protect/contoso-info-protect-fig1.png":::

>[!Note]
>Firma Contoso skonfigurowała również dodatkowe zasady dostępu warunkowego dla tożsamości i logowania. Zobacz [Identity for the Contoso Corporation (Tożsamość dla firmy Contoso Corporation](contoso-identity.md#conditional-access-policies-for-zero-trust-identity-and-device-access)).
>

Te zasady zapewniają, że:

- Aplikacje, które są dozwolone, oraz akcje, które mogą wykonywać z danymi organizacji, są definiowane przez zasady ochrony aplikacji.
- Komputery i urządzenia przenośne muszą być zgodne.
- Exchange Online używa szyfrowania komunikatów Office 365 (OME) dla Exchange Online.
- SharePoint używa ograniczeń wymuszanych przez aplikację.
- SharePoint używa zasad kontroli dostępu tylko do przeglądarki i do blokowania dostępu dla urządzeń niezarządzanych.

## <a name="mapping-microsoft-365-for-enterprise-features-to-contoso-data-levels"></a>Mapowanie Microsoft 365 funkcji przedsiębiorstwa na poziomy danych firmy Contoso

Poniższa tabela mapuje poziomy danych firmy Contoso na funkcje ochrony informacji w Microsoft 365 dla przedsiębiorstw.

| Poziom | usługi w chmurze Microsoft 365 | Windows 10 i Aplikacje Microsoft 365 dla przedsiębiorstw | Zabezpieczenia i zgodność |
|:-------|:-----|:-----|:-----|
| Poziom 1: Punkt odniesienia  | zasady dostępu warunkowego SharePoint i Exchange Online <BR> Uprawnienia w witrynach SharePoint | Etykiety wrażliwości <BR> Funkcją bitlocker <BR> Windows Information Protection | Zasady dostępu warunkowego urządzenia i zasady zarządzania aplikacjami mobilnymi |
| Poziom 2: poufny | Poziom 1 plus: <BR> <BR> Etykiety wrażliwości <BR> Microsoft 365 etykiet przechowywania w witrynach SharePoint <BR> Ochrona przed utratą danych dla SharePoint i Exchange Online <BR> Izolowane witryny SharePoint  | Poziom 1 plus: <BR> <BR> Etykiety poufności zasobów cyfrowych  | Poziom 1 |
| Poziom 3: Wysoce regulowane | Poziom 2 plus: <BR><BR> Szyfrowanie i ochrona własnego klucza (BYOK) na potrzeby informacji o wpisach tajnych handlowych <BR> Azure Key Vault dla aplikacji biznesowych, które wchodzą w interakcje z usługami Microsoft 365 | Poziom 2 | Poziom 1 |
|||||

Oto wynikowa konfiguracja ochrony informacji firmy Contoso.

:::image type="content" alt-text="Wynikowe konfiguracje ochrony informacji firmy Contoso." source="../media/contoso-info-protect/contoso-info-protect-fig2.png":::

## <a name="next-step"></a>Następny krok

Dowiedz się, jak firma Contoso korzysta z [funkcji zabezpieczeń w Microsoft 365 dla przedsiębiorstw](contoso-security-summary.md) na potrzeby zarządzania tożsamościami i dostępem, ochrony przed zagrożeniami, ochrony informacji i zarządzania zabezpieczeniami.

## <a name="see-also"></a>Zobacz też

[Plan zabezpieczeń](../security/office-365-security/security-roadmap.md)

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Przewodniki laboratorium testowego](m365-enterprise-test-lab-guides.md)