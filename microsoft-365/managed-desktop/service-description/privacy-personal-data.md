---
title: Prywatność i dane osobowe
description: Szczegóły danych zbieranych, przechowywanych i używanych przez usługę
keywords: RODO, przechowywanie, usuwanie, przechowywanie, przechowywanie, przetwarzanie, zabezpieczenia, inspekcja
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
ms.openlocfilehash: a381bc70e73bf3bbb9f654f5d5dfffd2047f8ab5
ms.sourcegitcommit: 9f0e84835121ce6228fdc69182c24be7ad1cb20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63014877"
---
# <a name="privacy"></a>Prywatność

Microsoft Managed Desktop to usługa IT-as-a-Service (ITaaS) dla klientów chmury przedsiębiorstwa zaprojektowana tak, aby zapewnić wdrażanie i aktualizowanie Windows pracowników na urządzeniach.

Ponadto udostępnia on funkcje zarządzania usługami IT i operacji, monitoruje zabezpieczenia i reagowanie na incydenty oraz zapewnia pomoc techniczną dla użytkowników. Ten artykuł zawiera więcej szczegółowych informacji na temat platformy danych i zgodności z przepisami dotyczącymi prywatności Microsoft Managed Desktop.

## <a name="microsoft-managed-desktop-data-sources-and-purpose"></a>Microsoft Managed Desktop źródła danych i przeznaczenie

Microsoft Managed Desktop dostarcza swoje usługi klientom korporacyjnym i prawidłowo administruje zarejestrowanymi urządzeniami klientów, używając danych z różnych źródeł.

Do tych źródeł należą Azure Active Directory, Microsoft Intune, Microsoft Windows 10 i Microsoft Defender for Endpoint. Zapewniają one kompleksowy widok urządzeń, które są Microsoft Managed Desktop zarządzać. Ponadto usługa korzysta z tych usługi firmy Microsoft w celu umożliwienia Microsoft Managed Desktop iTaaS:

| Źródło danych | Cel |
| ------ | ------ |
| [Microsoft Windows 10 Enterprise](/windows/windows-10/) | Zarządzanie doświadczeniem konfiguracji urządzeń, zarządzanie połączeniami z innymi usługami i operacyjną pomocą techniczną dla informatyków. |
| [Windows dla firm](/windows/deployment/update/waas-manage-updates-wufb) | Używa Windows 10 Enterprise danych diagnostycznych w celu zapewnienia dodatkowych informacji Windows 10 aktualizacji. |
| [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) | Zarządzanie urządzeniami i zabezpieczanie danych. Następujące źródła danych są następujące Microsoft Endpoint Manager:<br><ul><li>[Microsoft Azure Active Directory](/azure/active-directory/): Uwierzytelnianie i identyfikacja wszystkich kont użytkowników.</li><li>[Microsoft Intune](/mem/intune/): rozpowszechnianie konfiguracji urządzeń, zarządzania urządzeniami i zarządzania aplikacją.</li><li>[Endpoint Analytics](/mem/analytics/overview): Analytical insights about device and app usage.</li><li>[Windows Autopilot](/microsoft-365/windows/windows-autopilot): Inicjowanie obsługi i wdrażanie urządzeń.</li><li>[Program Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/): Zapewnia usługi zabezpieczeń, takie jak dane monitorowania zabezpieczeń urządzeń i analizy zabezpieczeń.</li></ul>
| [Microsoft Managed Desktop](https://endpoint.microsoft.com/#home) | Dane dostarczone przez klienta lub wygenerowane przez usługę podczas uruchamiania usługi. |
| [Microsoft 365 dla przedsiębiorstw](https://www.microsoft.com/en-us/microsoft-365/enterprise/compare-office-365-plans?rtc=1)| Zarządzanie Aplikacje Microsoft 365.

## <a name="microsoft-managed-desktop-data-process-and-storage"></a>Microsoft Managed Desktop i przechowywanie danych

Microsoft Managed Desktop korzysta z danych z wielu produktów i usług firmy Microsoft w celu świadczenia swoich usług klientom korporacyjnym.

W celu ochrony i obsługi zarejestrowanych urządzeń przetwarzamy i kopiujemy dane z tych usług w celu ich Microsoft Managed Desktop. Podczas przetwarzania danych postępujemy zgodnie z instrukcjami w dokumentach, do których odwołujemy się w warunkach usług [online i](https://www.microsoft.com/licensing/product-licensing/products) oświadczeniu o ochronie prywatności [firmy Microsoft](https://privacy.microsoft.com/privacystatement).

Microsoft Managed Desktop podmiotu przetwarzającego obejmuje zapewnianie odpowiedniej poufności, zabezpieczeń i odporności. Microsoft Managed Desktop stosuje dodatkowe środki ochrony prywatności i zabezpieczeń, aby zapewnić odpowiednią obsługę danych osobowych umożliwiających identyfikację.

## <a name="microsoft-managed-desktop-data-storage-and-staff-location"></a>Microsoft Managed Desktop przechowywania danych i lokalizacji personelu

Microsoft Managed Desktop danych są przechowywane w centrach danych platformy Azure w Stanach Zjednoczonych.

Dane osobowe uzyskane przez firmę Microsoft Managed Desktop i inne usługi są wymagane do utrzymania działania usługi. Jeśli urządzenie zostanie usunięte z Microsoft Managed Desktop, dane osobowe są przez maksymalnie 30 dni. Jednak dane alertów zebrane przez program Microsoft Defender dla punktu końcowego są przechowywane przez 180 dni ze względów bezpieczeństwa. Aby uzyskać więcej informacji na temat przechowywania danych, zobacz [Przechowywanie, usuwanie](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview) i przechowywanie danych w Microsoft 365.

Microsoft Managed Desktop operacji inżynierskich i operacji zabezpieczeń znajdują się w Stanach Zjednoczonych i Indiach.

### <a name="microsoft-windows-10-diagnostic-data"></a>Microsoft Windows 10 dane diagnostyczne

Microsoft Managed Desktop korzysta [Windows 10 rozszerzonych](/windows/privacy/windows-diagnostic-data) danych diagnostycznych w Windows, aby zapewnić, że są Windows aktualne, rozwiązywać problemy i ulepszać produkty.

Ulepszone ustawienie danych diagnostycznych zawiera bardziej szczegółowe informacje o urządzeniach zarejestrowanych w programie Microsoft Managed Desktop oraz ich ustawieniach, możliwościach i kondycji urządzenia. Po wybraniu rozszerzonych danych diagnostycznych są zbierane dane, w tym wymagane dane diagnostyczne. Aby uzyskać więcej informacji, zobacz [Zmiany dotyczące Windows danych diagnostycznych](/windows/privacy/changes-to-windows-diagnostic-data-collection) dotyczących Windows 10 ustawień danych diagnostycznych i gromadzenia danych.

Terminologia dotycząca danych diagnostycznych zmieni się w przyszłych wersjach Windows. Microsoft Managed Desktop dane są zatwierdzone do przetwarzania tylko tych danych, których usługa potrzebuje. Oznacza to, że poziom diagnostyki zmieni się na Microsoft Managed Desktop, jednak w celu precyzyjnego dostosowania zbioru danych diagnostycznych wymaganych dla usługi zostaną zaimplementowane ograniczone zasady diagnostyczne. Aby uzyskać więcej informacji, [zobacz Zmiany w Windows danych diagnostycznych](/windows/privacy/changes-to-windows-diagnostic-data-collection).

Microsoft Managed Desktop przetwarza i przechowuje dane na poziomie systemu z Windows 10 opcjonalnych danych diagnostycznych pochodzących z zarejestrowanych urządzeń, takich jak niezawodność aplikacji i urządzeń oraz informacje o wydajności. Microsoft Managed Desktop nie przetwarzają i nie przechowują danych osobowych klientów, takich jak historia czatu i przeglądarki, głos, tekst czy dane mowy.

Aby uzyskać więcej informacji na temat zbierania danych diagnostycznych firmy Microsoft Windows 10, zobacz sekcję [](https://privacy.microsoft.com/privacystatement#mainwherewestoreandprocessdatamodule) Gdzie przechowujemy i przetwarzamy dane osobowe w zasadach zachowania poufności informacji firmy Microsoft.

### <a name="microsoft-windows-update-for-business"></a>Microsoft Windows Update dla firm

Usługa Microsoft Windows Update dla firm używa danych z diagnostyki Windows do analizowania stanu aktualizacji i niepowodzeń. Microsoft Managed Desktop te dane są używane do ich załagodniania oraz rozwiązywania problemów w celu zapewnienia, że wszystkie zarejestrowane urządzenia są aktualne na podstawie wstępnie zdefiniowanej aktualizacji.

### <a name="microsoft-azure-active-directory"></a>Microsoft Azure Active Directory

Dane identyfikujące używane przez Microsoft Managed Desktop są przechowywane przez usługę Azure Active Directory (Azure AD) w lokalizacji geograficznej. Lokalizacja geograficzna jest oparta na lokalizacji udostępnianej przez organizację w przypadku subskrybowania usług online firmy Microsoft, takich jak usługa Microsoft Apps dla Enterprise i azure. Aby uzyskać więcej informacji na temat tego, gdzie znajdują się dane usługi Azure AD, zobacz [Azure Active Directory — Gdzie znajdują się Twoje dane?](https://msit.powerbi.com/view?r=eyJrIjoiODdjOWViZDctMWRhZS00ODUzLWI4MmQtNWM5NjBkZTBkNjFlIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9)

### <a name="microsoft-intune"></a>Microsoft Intune

Microsoft Intune zbiera, przetwarza i udostępnia dane Microsoft Managed Desktop w celu obsługi operacji biznesowych i usług. Aby uzyskać więcej informacji o danych zbieranych w usłudze Intune, zobacz [Zbieranie danych w usłudze Intune.](/mem/intune/protect/privacy-data-collect) 

Aby uzyskać więcej informacji Microsoft Intune lokalizacji danych, zobacz Gdzie są [Microsoft 365 przechowywane dane klienta](/microsoft-365/enterprise/o365-data-locations). Usługa Intune szanuje opcje lokalizacji przechowywania danych klientów wybrane przez administratora.

### <a name="microsoft-defender-for-endpoint"></a>Ochrona punktu końcowego w usłudze Microsoft Defender

Program Microsoft Defender for Endpoint zbiera i przechowuje informacje dotyczące urządzeń zarejestrowanych w usłudze Microsoft Managed Desktop na potrzeby administracji, śledzenia i raportowania. Zbierane informacje obejmują:

- Dane pliku (takie jak nazwy plików, rozmiar i skróty)
- Przetwarzanie danych (uruchomione procesy, skróty)
- Dane rejestru
- Dane połączenia sieciowego
- Szczegóły urządzenia (takie jak identyfikatory urządzeń, nazwy urządzeń i wersja systemu operacyjnego)

Aby uzyskać więcej informacji na temat lokalizacji zbierania i przechowywania danych programu Microsoft Defender dla punktu końcowego, zobacz Program [Microsoft Defender](/microsoft-365/security/defender-endpoint/data-storage-privacy#what-data-does-microsoft-defender-atp-collect) do przechowywania danych i prywatności.

### <a name="microsoft-365-apps-for-enterprise"></a>Aplikacje Microsoft 365 dla Enterprise

Aplikacje Microsoft 365 for Enterprise for Enterprise data with Microsoft Managed Desktop to ensure those apps are date with the latest version. Te aktualizacje są oparte na wstępnie zdefiniowanych kanałach aktualizacji zarządzanych przez Microsoft Managed Desktop. Aby uzyskać więcej informacji Aplikacje Microsoft 365 lokalizacji zbierania i przechowywania danych, zobacz Program Microsoft Defender do przechowywania danych i [prywatności w programie Endpoint](/microsoft-365/security/defender-endpoint/data-storage-privacy#what-data-does-microsoft-defender-atp-collect).

## <a name="major-data-change-notification"></a>Powiadomienie o zmianie głównych danych

Microsoft Managed Desktop ramach procesu kontroli zmian opisanego w naszej platformie komunikacji usługi.

Klienci są powiadamiani za pośrednictwem centrum Microsoft 365 wiadomości i portalu administracyjnego usługi Microsoft Managed Desktop o incydentach zabezpieczających i istotnych zmianach w usłudze.

Zmiany typów zbieranych danych i miejsca ich przechowywania są traktowane jako zmiana materiałowa. Powiadomimy Cię o tej zmianie co najmniej 30 dni, co jest standardową praktyką w zakresie Microsoft 365 produktów i usług. Aby uzyskać więcej informacji, zobacz [Zmiany w usłudze i komunikacja](/microsoft-365/managed-desktop/service-description/servicechanges).

## <a name="compliance"></a>Zgodność

Microsoft Managed Desktop przeszła audyty zewnętrzne i uzyskała kompleksowy zestaw ofert zgodności. Więcej informacji znajdziesz w tece [Zgodność](/microsoft-365/managed-desktop/intro/compliance). Raporty inspekcji są dostępne do pobrania w [Portalu](https://aka.ms/stp) zaufania usług firmy Microsoft, który służy jako repozytorium centralna usługi Microsoft Enterprise Online Services. Microsoft Managed Desktop znajduje się w tych dokumentach w kategorii "Monitorowanie i zarządzanie".

### <a name="data-subject-requests"></a>Żądania osób, których dane dotyczą

Microsoft Managed Desktop przepisy RODO i USTAWY O OCHRONIE PRYWATNOŚCI, które dają określonym tematom danych prawa do ich danych osobowych.

Do tych praw należą:

- Uzyskiwanie kopii danych osobowych
- Żądanie korekty
- Ograniczanie przetwarzania
- Usuwanie
- Odbierana w formacie elektronicznym, więc można ją przenosić do innego kontrolera.

Aby uzyskać bardziej ogólne informacje o żądaniach osób, których dane dotyczą, zobacz Wnioski osób, których dane dotyczą[, oraz RODO i KPI.](/compliance/regulatory/gdpr-data-subject-requests)

W celu wytłaniania żądań osób, których dane dotyczą, dotyczących danych zbieranych przez system zarządzania Microsoft Managed Desktop przypadku, zobacz następujące wnioski osób, których dane dotyczą:

| Żądania osób, których dane dotyczą | Opis |
| ------ | ------ |
| Dane z alertów programu Microsoft Defender dla punktu końcowego | Administrator zabezpieczeń może zażądać usunięcia lub wyodrębnienia danych osobistych związanych z alertami programu Microsoft Defender for Endpoint, przesyłając żądanie raportu w portalu [administracyjnym](https://aka.ms/memadmin). <br><br> Podaj następujące informacje: <br><ul><li>Typ żądania: Zmień żądanie</li><li>Kategoria: Zabezpieczenia</li><li>Podkategoria: Inne</li><li>Opis. Podaj odpowiednie nazwy urządzeń.</li></ul> |
| Dane z Microsoft Managed Desktop pomocy technicznej | Administrator IT może zażądać usunięcia lub wyodrębnienia wniosków o pomoc techniczną związaną z danymi osobistymi, przesyłając żądanie raportu w [portalu administracyjnym](https://aka.ms/memadmin). <br><br> Podaj następujące informacje: <ul><li>Typ żądania: Zmień żądanie</li><li>Kategoria: Zabezpieczenia</li><li>Podkategoria: Inne</li><li>Opis. Podaj odpowiednie nazwy urządzeń lub nazwy użytkowników.</li></ul>

W przypadku informacji o stanie usług (DSR) od innych produktów związanych z usługą zobacz następujące artykuły:

- Windows [danych diagnostycznych](/compliance/regulatory/gdpr-dsr-windows)
- Dane [usługi Microsoft Intune](/compliance/regulatory/gdpr-dsr-intune)
- Dane usługi Azure Active [Directory](/compliance/regulatory/gdpr-dsr-azure)

## <a name="legal"></a>Legal

**Zasady zachowania poufności informacji firmy Microsoft dotyczące użytkowników końcowych produktów dostarczanych przez klientów w organizacji**:

Zasady [zachowania poufności informacji firmy Microsoft](https://privacy.microsoft.com/privacystatement) informują użytkowników końcowych, że po zalogowaniu się do produktów firmy Microsoft za pomocą konta służbowego:

1. Ich organizacja może kontrolować swoje konto i administrować nim (w tym kontrolować ustawienia związane z prywatnością), a także uzyskać dostęp do ich danych i je przetwarzać.
1. Firma Microsoft może zbierać i przetwarzać te dane w celu świadczenia usługi na poziomie organizacji i użytkowników końcowych.
