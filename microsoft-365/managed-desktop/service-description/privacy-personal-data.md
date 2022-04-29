---
title: Prywatność i dane osobowe
description: Szczegóły zbieranych, przechowywanych i używanych przez usługę danych
keywords: RODO, przechowywanie, usuwanie, magazyn, przechowywanie, przetwarzanie, zabezpieczenia, inspekcja
ms.service: m365-md
ms.sitesec: library
author: tiaraquan
manager: dougeby
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.topic: article
audience: Admin, ITPro
ms.localizationpriority: medium
ms.openlocfilehash: e7c9912e3890d9b13003c7f3264490f67c4fc305
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128351"
---
# <a name="privacy"></a>Prywatność

Microsoft Managed Desktop jest usługą IT-as-a-Service (ITaaS) dla klientów w chmurze przedsiębiorstwa zaprojektowaną tak, aby urządzenia Windows pracowników były wdrażane i aktualizowane.

Zapewnia również zarządzanie usługami IT i operacje, monitoruje zabezpieczenia i reagowanie na zdarzenia oraz obsługę użytkowników. Ten artykuł zawiera więcej szczegółów na temat platformy danych i zgodności z prywatnością dla Microsoft Managed Desktop.

## <a name="microsoft-managed-desktop-data-sources-and-purpose"></a>Microsoft Managed Desktop źródła danych i przeznaczenie

Microsoft Managed Desktop udostępnia swoją usługę klientom korporacyjnym i prawidłowo zarządza zarejestrowanymi urządzeniami klientów przy użyciu danych z różnych źródeł.

Źródła te obejmują Azure Active Directory, Microsoft Intune, microsoft Windows 10 i Ochrona punktu końcowego w usłudze Microsoft Defender. Zapewniają one kompleksowy widok urządzeń, które Microsoft Managed Desktop zarządza. Usługa korzysta również z tych usługi firmy Microsoft, aby umożliwić Microsoft Managed Desktop zapewnianie możliwości ITaaS:

| Źródło danych | Celu |
| ------ | ------ |
| [Microsoft Windows 10 Enterprise](/windows/windows-10/) | Zarządzanie środowiskiem konfiguracji urządzeń, zarządzanie połączeniami z innymi usługami i obsługa operacyjna dla specjalistów IT. |
| [Windows Update dla firm](/windows/deployment/update/waas-manage-updates-wufb) | Używa Windows 10 Enterprise danych diagnostycznych, aby dostarczyć dodatkowych informacji na temat aktualizacji Windows 10. |
| [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) | Zarządzanie urządzeniami i zabezpieczanie danych. Następujące źródła danych należą do Microsoft Endpoint Manager:<br><ul><li>[Microsoft Azure Active Directory](/azure/active-directory/): uwierzytelnianie i identyfikacja wszystkich kont użytkowników.</li><li>[Microsoft Intune](/mem/intune/): Dystrybucja konfiguracji urządzeń, zarządzanie urządzeniami i zarządzanie aplikacjami.</li><li>[Analiza punktów końcowych](/mem/analytics/overview): szczegółowe informacje analityczne dotyczące użycia urządzeń i aplikacji.</li><li>[Windows Autopilot](/microsoft-365/windows/windows-autopilot): aprowizowanie i wdrażanie urządzeń.</li><li>[Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/): udostępnia usługi zabezpieczeń, takie jak monitorowanie zabezpieczeń urządzeń i dane analizy zabezpieczeń.</li></ul>
| [Microsoft Managed Desktop](https://endpoint.microsoft.com/#home) | Dane dostarczone przez klienta lub wygenerowane przez usługę podczas uruchamiania usługi. |
| [aplikacje Microsoft 365 dla przedsiębiorstw](https://www.microsoft.com/en-us/microsoft-365/enterprise/compare-office-365-plans?rtc=1)| Zarządzanie Aplikacje Microsoft 365.

## <a name="microsoft-managed-desktop-data-process-and-storage"></a>Microsoft Managed Desktop procesu i magazynu danych

Microsoft Managed Desktop korzysta z danych pochodzących z wielu produktów i usług firmy Microsoft w celu świadczenia usług klientom korporacyjnym.

Aby chronić i obsługiwać zarejestrowane urządzenia, przetwarzamy i kopiujemy dane z tych usług do Microsoft Managed Desktop. Podczas przetwarzania danych postępujemy zgodnie z podanymi przez Ciebie udokumentowanymi wskazówkami, o których mowa w [postanowieniach dotyczących usług online](https://www.microsoft.com/licensing/product-licensing/products) i [oświadczeniu o ochronie prywatności firmy Microsoft](https://privacy.microsoft.com/privacystatement).

obowiązki procesora Microsoft Managed Desktop obejmują zapewnienie odpowiedniej poufności, bezpieczeństwa i odporności. Microsoft Managed Desktop stosuje dodatkowe środki ochrony prywatności i bezpieczeństwa w celu zapewnienia właściwego postępowania z danymi osobowymi, które można zidentyfikować.

## <a name="microsoft-managed-desktop-data-storage-and-staff-location"></a>Microsoft Managed Desktop magazynu danych i lokalizacji personelu

Microsoft Managed Desktop przechowuje swoje dane w centrach danych platformy Azure w Stany Zjednoczone.

Dane osobowe uzyskane przez Microsoft Managed Desktop i inne usługi są wymagane do utrzymania działania usługi. Jeśli urządzenie zostanie usunięte z Microsoft Managed Desktop, przechowujemy dane osobowe przez maksymalnie 30 dni. Jednak dane alertów zbierane przez Ochrona punktu końcowego w usłudze Microsoft Defender są przechowywane przez 180 dni ze względów bezpieczeństwa. Aby uzyskać więcej informacji na temat przechowywania danych, zobacz [Przechowywanie, usuwanie i niszczenie danych w Microsoft 365](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview).

zespoły Microsoft Managed Desktop Engineering Operations and Security Operations znajdują się w Stany Zjednoczone, Indiach i Rumunii.

### <a name="microsoft-windows-10-diagnostic-data"></a>Dane diagnostyczne Windows 10 firmy Microsoft

Microsoft Managed Desktop używa [Windows 10 rozszerzonych danych diagnostycznych](/windows/privacy/windows-diagnostic-data), aby zapewnić Windows bezpieczeństwa, aktualności, rozwiązywania problemów i ulepszeń produktu.

Ulepszone ustawienie danych diagnostycznych zawiera bardziej szczegółowe informacje o urządzeniach zarejestrowanych w Microsoft Managed Desktop oraz ich ustawieniach, możliwościach i kondycji urządzeń. Po wybraniu rozszerzonych danych diagnostycznych zbierane są dane, w tym wymagane dane diagnostyczne. Aby uzyskać więcej informacji, zobacz [Zmiany w Windows zbieranie danych diagnostycznych](/windows/privacy/changes-to-windows-diagnostic-data-collection) dotyczących ustawienia danych diagnostycznych Windows 10 i zbierania danych.

Terminologia danych diagnostycznych zmieni się w przyszłych wersjach Windows. Microsoft Managed Desktop jest zobowiązana do przetwarzania tylko danych, których potrzebuje usługa. Chociaż będzie to oznaczać, że poziom diagnostyki zmieni się na **Opcjonalny**, Microsoft Managed Desktop zaimplementuje ograniczone zasady diagnostyczne, aby dostosować zbieranie danych diagnostycznych wymaganych dla usługi. Aby uzyskać więcej informacji, zobacz [Zmiany w Windows zbierania danych diagnostycznych](/windows/privacy/changes-to-windows-diagnostic-data-collection).

Microsoft Managed Desktop przetwarza i przechowuje tylko dane na poziomie systemu z Windows 10 opcjonalnych danych diagnostycznych pochodzących z zarejestrowanych urządzeń, takich jak niezawodność aplikacji i urządzeń oraz informacje o wydajności. Microsoft Managed Desktop nie przetwarza i nie przechowuje danych osobowych klientów, takich jak historia czatu i przeglądarki, głos, tekst lub dane mowy.

Aby uzyskać więcej informacji na temat zbierania danych diagnostycznych przez firmę Microsoft Windows 10, zobacz sekcję [Where we store and process personal data (Gdzie przechowujemy i przetwarzamy dane osobowe](https://privacy.microsoft.com/privacystatement#mainwherewestoreandprocessdatamodule)) w oświadczeniu o ochronie prywatności firmy Microsoft.

### <a name="microsoft-windows-update-for-business"></a>Microsoft Windows Update for Business

Usługa Microsoft Windows Update for Business używa danych z diagnostyki Windows do analizowania stanu aktualizacji i niepowodzeń. Microsoft Managed Desktop używa tych danych i używa ich do eliminowania i rozwiązywania problemów, aby upewnić się, że wszystkie zarejestrowane urządzenia są aktualne na podstawie wstępnie zdefiniowanego okresu aktualizacji.

### <a name="microsoft-azure-active-directory"></a>Microsoft Azure Active Directory

Identyfikowanie danych używanych przez Microsoft Managed Desktop jest przechowywane przez Azure Active Directory (Azure AD) w lokalizacji geograficznej. Lokalizacja geograficzna jest oparta na lokalizacji udostępnianej przez organizację po subskrybowaniu usługi Microsoft Usługi online, takiej jak Microsoft Apps dla Enterprise i platformy Azure. Aby uzyskać więcej informacji o tym, gdzie znajdują się dane Azure AD, zobacz [Azure Active Directory — gdzie znajdują się twoje dane?](https://msit.powerbi.com/view?r=eyJrIjoiODdjOWViZDctMWRhZS00ODUzLWI4MmQtNWM5NjBkZTBkNjFlIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9)

### <a name="microsoft-intune"></a>Microsoft Intune

Microsoft Intune zbiera, przetwarza i udostępnia dane, aby Microsoft Managed Desktop do obsługi operacji biznesowych i usług. Aby uzyskać więcej informacji na temat danych zebranych w Intune, zobacz [Zbieranie danych w Intune](/mem/intune/protect/privacy-data-collect)

Aby uzyskać więcej informacji na temat Microsoft Intune lokalizacji danych, zobacz [Where your Microsoft 365 customer data is stored (Gdzie są przechowywane dane klienta Microsoft 365](/microsoft-365/enterprise/o365-data-locations)). Intune uwzględnia wybór lokalizacji magazynu dokonany przez administratora dla danych klientów.

### <a name="microsoft-defender-for-endpoint"></a>Ochrona punktu końcowego w usłudze Microsoft Defender

Ochrona punktu końcowego w usłudze Microsoft Defender zbiera i przechowuje informacje dotyczące urządzeń zarejestrowanych w Microsoft Managed Desktop do celów administracyjnych, śledzenia i raportowania. Zebrane informacje obejmują:

- Dane pliku (takie jak nazwy plików, rozmiar i skróty)
- Przetwarzanie danych (uruchamianie procesów, skrótów)
- Dane rejestru
- Dane połączenia sieciowego
- Szczegóły urządzenia (takie jak identyfikatory urządzeń, nazwy urządzeń i wersja systemu operacyjnego)

Aby uzyskać więcej informacji na temat lokalizacji zbierania danych i magazynowania Ochrona punktu końcowego w usłudze Microsoft Defender, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender magazyn danych i prywatność](/microsoft-365/security/defender-endpoint/data-storage-privacy#what-data-does-microsoft-defender-atp-collect).

### <a name="microsoft-365-apps-for-enterprise"></a>Aplikacje Microsoft 365 dla Enterprise

Aplikacje Microsoft 365 dla Enterprise zbiera i udostępnia dane Microsoft Managed Desktop, aby upewnić się, że te aplikacje są aktualne w najnowszej wersji. Te aktualizacje są oparte na wstępnie zdefiniowanych kanałach aktualizacji zarządzanych przez Microsoft Managed Desktop. Aby uzyskać więcej informacji na temat lokalizacji zbierania danych i magazynowania Aplikacje Microsoft 365, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender magazyn danych i prywatność](/microsoft-365/security/defender-endpoint/data-storage-privacy#what-data-does-microsoft-defender-atp-collect).

## <a name="major-data-change-notification"></a>Powiadomienie o zmianie danych głównych

Microsoft Managed Desktop jest zgodny z procesem kontroli zmian opisanym w naszej strukturze komunikacji z usługami.

Powiadamiamy klientów za pośrednictwem centrum komunikatów Microsoft 365 i Microsoft Managed Desktop portalu administracyjnego o zdarzeniach zabezpieczeń i istotnych zmianach w usłudze.

Zmiany typów zbieranych danych i miejsca ich przechowywania są uważane za istotną zmianę. Przekażemy co najmniej 30 dni zaawansowanego powiadomienia o tej zmianie, zgodnie ze standardową praktyką dotyczącą produktów i usług Microsoft 365. Aby uzyskać więcej informacji, zobacz [Zmiany usługi i komunikacja](/microsoft-365/managed-desktop/service-description/servicechanges).

## <a name="compliance"></a>Zgodność

Microsoft Managed Desktop przeszła zewnętrzne audyty i uzyskała kompleksowy zestaw ofert zgodności. Więcej informacji można znaleźć w temacie [Zgodność](/microsoft-365/managed-desktop/intro/compliance). Raporty inspekcji są dostępne do pobrania w [portalu zaufania usługi](https://aka.ms/stp) firmy Microsoft, który służy jako centralne repozytorium usług Microsoft Enterprise Online Services. Microsoft Managed Desktop znajduje się w tych dokumentach w kategorii "Monitorowanie i zarządzanie".

### <a name="data-subject-requests"></a>Żądania podmiotów danych

Microsoft Managed Desktop są zgodne z przepisami RODO i CCPA dotyczącymi prywatności, które dają podmiotom danych określone prawa do ich danych osobowych.

Te prawa obejmują:

- Uzyskiwanie kopii danych osobowych
- Żądanie poprawek
- Ograniczanie przetwarzania
- Usuwanie go
- Odbieranie go w formacie elektronicznym, dzięki czemu można go przenieść do innego kontrolera.

Aby uzyskać bardziej ogólne informacje na temat żądań podmiotów danych , zobacz [Żądania podmiotów danych oraz RODO i CCPA](/compliance/regulatory/gdpr-data-subject-requests).

Aby wykonywać żądania podmiotów danych dotyczące danych zebranych przez system zarządzania sprawami Microsoft Managed Desktop, zobacz następujące żądania podmiotów danych:

| Żądania podmiotów danych | Opis |
| ------ | ------ |
| Dane z alertów Ochrona punktu końcowego w usłudze Microsoft Defender | Administrator zabezpieczeń może zażądać usunięcia lub wyodrębnienia danych osobowych związanych z alertami Ochrona punktu końcowego w usłudze Microsoft Defender, przesyłając żądanie raportu w [portalu administracyjnym](https://aka.ms/memadmin). <br><br> Podaj następujące informacje: <br><ul><li>Typ żądania: Żądanie zmiany</li><li>Kategoria: Zabezpieczenia</li><li>Podkategoria: Inne</li><li>Opis: podaj odpowiednie nazwy urządzeń.</li></ul> |
| Dane z Microsoft Managed Desktop żądań pomocy technicznej | Administrator IT może zażądać usunięcia lub wyodrębnienia żądań pomocy technicznej związanych z danymi osobowymi, przesyłając żądanie raportu w [portalu administracyjnym](https://aka.ms/memadmin). <br><br> Podaj następujące informacje: <ul><li>Typ żądania: Żądanie zmiany</li><li>Kategoria: Zabezpieczenia</li><li>Podkategoria: Inne</li><li>Opis: podaj odpowiednie nazwy urządzeń lub nazwy użytkowników.</li></ul>

W przypadku żądań DSR z innych produktów związanych z usługą zobacz następujące artykuły:

- Windows [danych diagnostycznych](/compliance/regulatory/gdpr-dsr-windows)
- [Dane Intune](/compliance/regulatory/gdpr-dsr-intune) firmy Microsoft
- Dane usługi Azure Active [Directory](/compliance/regulatory/gdpr-dsr-azure)

## <a name="legal"></a>Prawnych

**Powiadomienie firmy Microsoft o ochronie prywatności dla użytkowników końcowych produktów dostarczanych przez klientów organizacyjnych**:

Zasady [zachowania poufności informacji firmy Microsoft](https://privacy.microsoft.com/privacystatement) powiadamiają użytkowników końcowych, że podczas logowania się do produktów firmy Microsoft przy użyciu konta służbowego:

1. Ich organizacja może kontrolować swoje konto i administrować nimi (w tym kontrolować ustawienia związane z prywatnością) oraz uzyskiwać dostęp do danych i przetwarzać je.
1. Firma Microsoft może zbierać i przetwarzać dane w celu świadczenia usługi dla organizacji i użytkowników końcowych.
