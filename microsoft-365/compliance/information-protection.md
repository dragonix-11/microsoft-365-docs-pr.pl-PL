---
title: Microsoft Purview Information Protection
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ms.collection:
- m365solution-mip
- m365initiative-compliance
recommendations: false
description: Zaimplementuj funkcje usługi Microsoft Purview Information Protection, aby ułatwić ochronę poufnych informacji wszędzie tam, gdzie się znajdują lub podróżują.
ms.openlocfilehash: ac6627d620169aca962f85f30c98d830b4a34a9f
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64999877"
---
# <a name="protect-your-sensitive-data-with-microsoft-purview"></a>Ochrona poufnych danych za pomocą usługi Microsoft Purview

> [!TIP]
> *Czy wiesz, że możesz bezpłatnie wypróbować wersje premium wszystkich dziewięciu rozwiązań Usługi Microsoft Purview?* Skorzystaj z 90-dniowej wersji próbnej rozwiązań Purview, aby dowiedzieć się, jak niezawodne możliwości usługi Purview mogą pomóc organizacji spełnić jej potrzeby w zakresie zgodności. Microsoft 365 E3 i Office 365 E3 klienci mogą rozpocząć pracę w [centrum wersji próbnych portalu zgodności usługi Microsoft Purview](https://compliance.microsoft.com/trialHorizontalHub?sku=ComplianceE5&ref=DocsRef). Dowiedz się więcej o [tym, kto może zarejestrować się i zapoznać się z postanowieniami dotyczącymi wersji próbnej](compliance-easy-trials.md).

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

>*[Licencjonowanie na potrzeby zgodności & zabezpieczeń Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Zaimplementuj możliwości usługi **Microsoft Purview Information Protection** (dawniej Microsoft Information Protection), aby ułatwić odnajdywanie, klasyfikowanie i ochronę poufnych informacji wszędzie tam, gdzie się znajdują lub podróżują.

Te funkcje ochrony informacji zapewniają narzędzia do [poznania danych](#know-your-data), [ochrony danych](#protect-your-data) i [zapobiegania utracie danych](#prevent-data-loss).

![Obraz przedstawiający sposób, w jaki usługa Microsoft Purview Information Protection pomaga odnajdywać, klasyfikować i chronić poufne dane.](../media/powered-by-intelligent-platform.png)

Aby uzyskać opisowe wskazówki dotyczące wdrażania rozwiązania Information Protection usługi Microsoft Purview dla organizacji, zobacz [Wdrażanie rozwiązania do ochrony informacji w usłudze Microsoft Purview](information-protection-solution.md).

Aby uzyskać informacje na temat zarządzania danymi, zobacz [Zarządzanie danymi za pomocą usługi Microsoft Purview](manage-Information-governance.md).

## <a name="know-your-data"></a>Poznaj swoje dane

Aby zrozumieć poziome dane i zidentyfikować poufne dane w środowisku hybrydowym, skorzystaj z następujących możliwości:

|Możliwości|Jakie problemy rozwiązuje?|Wprowadzenie|
|:------|:------------|:--------------------|
|[Typy informacji poufnych](sensitive-information-type-learn-about.md)| Identyfikuje poufne dane przy użyciu wbudowanych lub niestandardowych wyrażeń regularnych lub funkcji. Dowody potwierdzające obejmują słowa kluczowe, poziomy ufności i bliskość.| [Dostosuj wbudowany typ informacji poufnych](customize-a-built-in-sensitive-information-type.md)|
|[Klasyfikatory z możliwością szkolenia](classifier-learn-about.md)| Identyfikuje dane poufne przy użyciu przykładów danych, które Cię interesują, zamiast identyfikować elementy w elemencie (dopasowywanie wzorców). Możesz użyć wbudowanych klasyfikatorów lub wytrenować klasyfikator z własną zawartością.| [Wprowadzenie do klasyfikatorów z możliwością szkolenia](classifier-get-started-with.md) |
|[Klasyfikacja danych](data-classification-overview.md) | Graficzna identyfikacja elementów w organizacji, które mają etykietę poufności, etykietę przechowywania lub zostały sklasyfikowane. Możesz również użyć tych informacji, aby uzyskać wgląd w akcje, które użytkownicy podejmują w tych elementach. | [Wprowadzenie do eksploratora zawartości](data-classification-content-explorer.md) <p> [Wprowadzenie do eksploratora aktywności](data-classification-activity-explorer.md) |

## <a name="protect-your-data"></a>Chroń swoje dane

Aby zastosować elastyczne akcje ochrony, które obejmują szyfrowanie, ograniczenia dostępu i oznaczenia wizualne, skorzystaj z następujących możliwości:

|Możliwości|Jakie problemy rozwiązuje?|Wprowadzenie|
|:------|:------------|---------------------|
|[Etykiety wrażliwości](sensitivity-labels.md)| Pojedyncze rozwiązanie dla aplikacji, usług i urządzeń umożliwiające etykietowanie i ochronę danych w miarę ich przenoszenia do organizacji i poza nią. <br /><br /> Przykładowe scenariusze: <br />- [Zarządzanie etykietami poufności dla aplikacji Office](sensitivity-labels-office-apps.md) <br />- [Szyfrowanie dokumentów i wiadomości e-mail](encryption-sensitivity-labels.md) <br />-  [Stosowanie i wyświetlanie etykiet w Power BI](/power-bi/admin/service-security-apply-data-sensitivity-labels) <br /><br /> Pełną listę scenariuszy dotyczących etykiet poufności można znaleźć w dokumentacji Wprowadzenie.|[Wprowadzenie do etykiet poufności](get-started-with-sensitivity-labels.md) |
|[Klient ujednoliconego etykietowania platformy Azure Information Protection](/azure/information-protection/rms-client/aip-clientv2)| W przypadku komputerów Windows rozszerzenie etykietowania do Eksplorator plików i programu PowerShell z dodatkowymi funkcjami dla aplikacji Office w razie potrzeby| [Przewodnik administratora klienta ujednoliconego etykietowania usługi Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide)|
|[Podwójne szyfrowanie kluczy](double-key-encryption.md)| W każdych okolicznościach tylko twoja organizacja może kiedykolwiek odszyfrować chronioną zawartość lub zgodnie z wymaganiami prawnymi, klucze szyfrowania muszą być przechowywane w granicach geograficznych. | [Wdrażanie szyfrowania podwójnego klucza](double-key-encryption.md#deploy-dke)|
|[Szyfrowanie wiadomości usługi Office 365 (OME)](ome.md)| Szyfruje wiadomości e-mail i dołączone dokumenty wysyłane do dowolnego użytkownika na dowolnym urządzeniu, dzięki czemu tylko autoryzowani adresaci mogą odczytywać informacje wysyłane pocztą e-mail. <br /><br />  Przykładowy scenariusz: [odwoływanie wiadomości e-mail zaszyfrowanych za pomocą zaawansowanego szyfrowania komunikatów](revoke-ome-encrypted-mail.md) | [Konfigurowanie nowych funkcji szyfrowania komunikatów](set-up-new-message-encryption-capabilities.md)|
|[Szyfrowanie usługi przy użyciu klucza klienta](customer-key-overview.md) | Chroni przed wyświetlaniem danych przez nieautoryzowane systemy lub personel i uzupełnia szyfrowanie dysków funkcji BitLocker w centrach danych firmy Microsoft. | [Konfigurowanie klucza klienta dla Office 365](customer-key-set-up.md)|
|[SharePoint Zarządzanie prawami do informacji (IRM)](set-up-irm-in-sp-admin-center.md#irm-enable-sharepoint-document-libraries-and-lists)|Chroni SharePoint list i bibliotek, dzięki czemu gdy użytkownik wyewidencjonuje dokument, pobrany plik jest chroniony, dzięki czemu tylko autoryzowane osoby mogą wyświetlać plik i używać go zgodnie z określonymi zasadami. | [Set up Information Rights Management (IRM) in SharePoint admin center](set-up-irm-in-sp-admin-center.md)|
[Łącznik usługi Rights Management](/azure/information-protection/deploy-rms-connector) |Ochrona tylko dla istniejących wdrożeń lokalnych korzystających z Exchange lub serwera SharePoint lub serwerów plików z systemem Windows Server and File Classification Infrastructure (FCI). | [Kroki wdrażania łącznika usługi RMS](/azure/information-protection/deploy-rms-connector#steps-to-deploy-the-rms-connector)
|[Skaner ujednoliconego etykietowania platformy Azure Information Protection](/azure/information-protection/deploy-aip-scanner)| Odnajduje, etykietuje i chroni poufne informacje znajdujące się w lokalnych magazynach danych. | [Konfigurowanie i instalowanie skanera ujednoliconego etykietowania usługi Azure Information Protection](/azure/information-protection/deploy-aip-scanner-configure-install)|
|[Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)| Odnajduje, etykietuje i chroni poufne informacje znajdujące się w magazynach danych znajdujących się w chmurze. | [Odnajdywanie, klasyfikowanie, etykietowanie i ochrona danych regulowanych i poufnych przechowywanych w chmurze](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|[Mapa danych usługi Microsoft Purview](/azure/purview/overview) |Identyfikuje dane poufne i stosuje automatyczne etykietowanie do zawartości w zasobach usługi Microsoft Purview Data Map. Obejmują one pliki w magazynie, takie jak usługa Azure Data Lake i Azure Files, oraz dane schematyzowane, takie jak kolumny w Azure SQL DB i Cosmos DB. |[Etykietowanie w usłudze Microsoft Purview Data Map](/azure/purview/create-sensitivity-label) |
|[zestaw SDK Microsoft Information Protection](/information-protection/develop/overview#microsoft-information-protection-sdk)|Rozszerza etykiety poufności na aplikacje i usługi innych firm. <br /><br />  Przykładowy scenariusz: [ustawianie i pobieranie etykiety poufności (C++)](/information-protection/develop/quick-file-set-get-label-cpp) |[Konfigurowanie zestawu SDK Microsoft Information Protection (MIP)](/information-protection/develop/setup-configure-mip)|


## <a name="prevent-data-loss"></a>Zapobieganie utracie danych

Aby zapobiec przypadkowemu nadmiernemu udostępnianiu poufnych informacji, skorzystaj z następujących możliwości:


|Możliwości|Jakie problemy rozwiązuje?|Wprowadzenie|
|:------|:------------|:---------------------|
|[Zapobieganie utracie danych w usłudze Microsoft Purview](dlp-learn-about-dlp.md)| Zapobiega przypadkowej wymianie poufnych elementów. | [Wprowadzenie do domyślnych zasad DLP](get-started-with-the-default-dlp-policy.md)|
|[Zapobieganie utracie danych punktu końcowego](endpoint-dlp-learn-about.md)| Rozszerza możliwości DLP na elementy, które są używane i udostępniane na komputerach Windows 10. | [Wprowadzenie do ochrony przed utratą danych punktu końcowego](endpoint-dlp-getting-started.md)|
|[Rozszerzenie zgodności firmy Microsoft](dlp-chrome-learn-about.md) | Rozszerza możliwości DLP na przeglądarkę Chrome | [Wprowadzenie do rozszerzenia zgodności firmy Microsoft](dlp-chrome-get-started.md)|
|[Lokalny skaner ochrony przed utratą danych w usłudze Microsoft Purview (wersja zapoznawcza)](dlp-on-premises-scanner-learn.md)|Rozszerza monitorowanie DLP działań plików i akcji ochronnych dla tych plików do lokalnych udziałów plików i SharePoint folderów i bibliotek dokumentów.|[Wprowadzenie przy użyciu lokalnego skanera ochrony przed utratą danych w usłudze Microsoft Purview (wersja zapoznawcza)](dlp-on-premises-scanner-get-started.md)|
|[Ochrona poufnych informacji w Microsoft Teams wiadomościach czatu i kanału](dlp-microsoft-teams.md) | Rozszerza niektóre funkcje DLP na Teams wiadomości czatu i kanału | [Dowiedz się więcej o domyślnych zasadach ochrony przed utratą danych w usłudze Microsoft Teams (wersja zapoznawcza)](dlp-teams-default-policy.md)|

## <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

Wymagania licencyjne dotyczące usługi Microsoft Purview Information Protection zależą od używanych scenariuszy i funkcji, zamiast określać wymagania licencyjne dla każdej funkcji wymienionej na tej stronie. Aby zrozumieć wymagania licencyjne i opcje dotyczące usługi Microsoft Purview Information Protection, zobacz sekcje **Information Protection** z [Microsoft 365 wskazówek dotyczących zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance) i powiązanego [pobierania plików PDF](https://go.microsoft.com/fwlink/?linkid=2139145) dotyczących wymagań dotyczących licencjonowania na poziomie funkcji.
