---
title: Wprowadzenie do etykiet poufności
f1.keywords:
- CSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Chcesz wdrożyć etykiety poufności, aby chronić dane organizacji, ale nie wiesz, od czego zacząć? Zapoznaj się z praktycznymi wskazówkami, które pomogą Ci w procesie etykietowania.
ms.openlocfilehash: f27f1a475f5880058db40894015dabdec9038be1
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2022
ms.locfileid: "65286039"
---
# <a name="get-started-with-sensitivity-labels"></a>Wprowadzenie do etykiet poufności

>*[Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Aby uzyskać informacje o tym, czym są etykiety poufności i jak mogą pomóc w ochronie danych organizacji, zobacz [Dowiedz się więcej o etykietach poufności](sensitivity-labels.md).

Jeśli masz usługę [Azure Information Protection](/azure/information-protection/what-is-information-protection) i nadal używasz etykiet usługi Azure Information Protection zarządzanych z Azure Portal, musisz zmigrować te etykiety do [ujednoliconej platformy etykietowania](/azure/information-protection/faqs#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform). W przypadku komputerów Windows można [wybrać klienta etykietowania do użycia](/azure/information-protection/rms-client/use-client#choose-which-labeling-client-to-use-for-windows-computers) dla opublikowanych etykiet poufności.

Gdy wszystko będzie gotowe do rozpoczęcia ochrony danych organizacji przy użyciu etykiet poufności:

1. **Utwórz etykiety.** Utwórz etykiety poufności i nadaj im nazwę zgodnie z taksonomią klasyfikacji organizacji dla różnych poziomów poufności zawartości. Używaj nazw pospolitych lub terminów, które mają sens dla użytkowników. Jeśli nie masz jeszcze ustalonej taksonomii, rozważ rozpoczęcie od nazw etykiet, takich jak Osobiste, Publiczne, Ogólne, Poufne i Wysoce poufne. Następnie można użyć etykiet podrzędnych do grupowania podobnych etykiet według kategorii. Podczas tworzenia etykiety użyj tekstu etykietki narzędzia, aby ułatwić użytkownikom wybranie odpowiedniej etykiety.
    
    Aby uzyskać bardziej szczegółowe wskazówki dotyczące definiowania taksonomii klasyfikacji, pobierz oficjalny dokument "Klasyfikacja danych & taksonomia etykiet poufności" z [portalu zaufania usługi](https://aka.ms/DataClassificationWhitepaper).

2. **Zdefiniuj, co może zrobić każda etykieta.** Skonfiguruj ustawienia ochrony, które mają być skojarzone z każdą etykietą. Na przykład możesz chcieć, aby zawartość o niższej poufności (na przykład etykieta "Ogólne" miała zastosowany tylko nagłówek lub stopkę, podczas gdy zawartość o większej poufności (na przykład etykieta "Poufne") powinna mieć znak wodny i szyfrowanie.

3. **Opublikuj etykiety.** Po skonfigurowaniu etykiet poufności opublikuj je przy użyciu zasad etykiety. Zdecyduj, którzy użytkownicy i grupy mają mieć etykiety i jakie ustawienia zasad mają być używane. Pojedyncza etykieta jest wielokrotnego użytku — można ją zdefiniować raz, a następnie dołączyć ją do kilku zasad etykiet przypisanych do różnych użytkowników. Na przykład można pilotować etykiety poufności, przypisując zasady etykiet tylko do kilku użytkowników. Następnie, gdy wszystko będzie gotowe do wdrożenia etykiet w całej organizacji, możesz utworzyć nowe zasady etykiet dla etykiet i tym razem określić wszystkich użytkowników.


> Możesz kwalifikować się do automatycznego tworzenia etykiet domyślnych i domyślnych zasad etykiet, które zajmują się krokami 1–3. Aby uzyskać więcej informacji, zobacz [Domyślne etykiety i zasady dla usługi Microsoft Purview Information Protection](mip-easy-trials.md).

Podstawowy przepływ wdrażania i stosowania etykiet poufności:

![Diagram przedstawiający przepływ pracy dla etykiet poufności.](../media/Sensitivity-label-flow.png)

## <a name="subscription-and-licensing-requirements-for-sensitivity-labels"></a>Wymagania dotyczące subskrypcji i licencjonowania etykiet poufności

Wiele różnych subskrypcji obsługuje etykiety poufności, a wymagania licencyjne dla użytkowników zależą od używanych funkcji.

Aby wyświetlić opcje licencjonowania użytkowników w celu skorzystania z funkcji usługi Microsoft Purview, zobacz [wskazówki dotyczące licencjonowania Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). Aby uzyskać etykiety poufności, zobacz sekcję [Microsoft Purview Information Protection: etykietowanie poufności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-information-protection-sensitivity-labeling) i powiązane [pobieranie plików PDF](https://go.microsoft.com/fwlink/?linkid=2139145) w celu uzyskania wymagań dotyczących licencjonowania na poziomie funkcji.

## <a name="permissions-required-to-create-and-manage-sensitivity-labels"></a>Uprawnienia wymagane do tworzenia etykiet poufności i zarządzania nimi

Członkowie zespołu ds. zgodności, którzy będą tworzyć etykiety poufności, potrzebują uprawnień do portalu zgodności usługi Microsoft Purview.

Domyślnie administratorzy globalni dzierżawy mają dostęp do tego centrum administracyjnego i mogą udzielić urzędnikom zgodności i innym osobom dostępu bez udzielania im wszystkich uprawnień administratora dzierżawy. W przypadku tego ograniczonego dostępu administratora delegowanego dodaj użytkowników do grupy ról **Administrator danych zgodności**, **Administrator zgodności** lub **Administrator zabezpieczeń** . 

Alternatywnie w przypadku korzystania z ról domyślnych można utworzyć nową grupę ról i dodać do tej grupy role **Administrator etykiet poufności** lub **Konfiguracja organizacji** . W przypadku roli tylko do odczytu użyj **czytnika etykiet poufności**. 

> [!NOTE]
> Teraz w wersji zapoznawczej możesz użyć następujących grup ról:
> - **Information Protection**
> - **administratorzy Information Protection**
> - **analitycy Information Protection**
> - **Information Protection śledczy**
> - **czytniki Information Protection**
>
> Aby uzyskać wyjaśnienie każdej z nich i nowych ról, które zawierają, wybierz grupę ról w portalu  > <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">zgodności usługi Microsoft PurviewPermissions</a> **& roleW** >  **centrum** >  **zgodnościRole**, a następnie przejrzyj opis w okienku wysuwanym. Możesz też zobaczyć [grupy ról w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center).

Aby uzyskać instrukcje dodawania użytkowników do domyślnej grupy ról, ról lub tworzenia własnych grup ról, zobacz [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md).

Te uprawnienia są wymagane tylko do tworzenia i konfigurowania etykiet poufności i ich zasad etykiet. Nie są one wymagane do stosowania etykiet w aplikacjach lub usługach. Jeśli wymagane są dodatkowe uprawnienia dla określonych konfiguracji związanych z etykietami poufności, te uprawnienia zostaną wymienione w odpowiednich instrukcjach dokumentacji.

## <a name="deployment-strategy-for-sensitivity-labels"></a>Strategia wdrażania etykiet poufności
Skuteczną strategią wdrażania etykiet poufności dla organizacji jest utworzenie działającego zespołu wirtualnego, który identyfikuje wymagania biznesowe i techniczne oraz zarządza nimi, sprawdza testy koncepcji, wewnętrzne punkty kontrolne i zatwierdzenia oraz ostateczne wdrożenie środowiska produkcyjnego.

Korzystając z tabeli w następnej sekcji, zalecamy zidentyfikowanie pierwszego lub dwóch scenariuszy, które są mapowane na najbardziej wpływowe wymagania biznesowe. Po wdrożeniu tych scenariuszy wróć do listy, aby zidentyfikować następny lub dwa priorytety wdrożenia.

## <a name="common-scenarios-for-sensitivity-labels"></a>Typowe scenariusze dotyczące etykiet poufności

Wszystkie scenariusze wymagają [utworzenia i skonfigurowania etykiet poufności i ich zasad](create-sensitivity-labels.md).

|Chcę...|Dokumentacji|
|----------------|---------------|
|Zarządzanie etykietami poufności dla aplikacji Office, tak aby zawartość była oznaczona etykietą utworzoną — obejmuje obsługę ręcznego etykietowania na wszystkich platformach |[Zarządzanie etykietami poufności w aplikacjach Office](sensitivity-labels-office-apps.md)|
|Rozszerzanie etykietowania na Eksplorator plików i program PowerShell z dodatkowymi funkcjami Office aplikacji na Windows (w razie potrzeby)|[Klient ujednoliconego etykietowania platformy Azure Information Protection dla Windows](/azure/information-protection/rms-client/aip-clientv2)|
|Szyfruj dokumenty i wiadomości e-mail przy użyciu etykiet poufności i ogranicz, kto może uzyskiwać dostęp do tej zawartości i jak można jej używać |[Ogranicz dostęp do zawartości przy użyciu etykiet poufności w celu zastosowania szyfrowania](encryption-sensitivity-labels.md)|
|Włączanie etykiet poufności dla Office w sieci Web z obsługą współtworzenia, zbierania elektronicznych materiałów dowodowych, zapobiegania utracie danych, wyszukiwania — nawet wtedy, gdy dokumenty są szyfrowane | [Włącz etykiety poufności dla plików pakietu Office w programie SharePoint i usłudze OneDrive](sensitivity-labels-sharepoint-onedrive-files.md)
|Używanie współtworzenia i automatycznego zapisywania w aplikacjach klasycznych Office, gdy dokumenty są szyfrowane | [Włączanie współtworzyła pliki zaszyfrowane przy użyciu etykiet poufności](sensitivity-labels-coauthoring.md)
|Automatyczne stosowanie etykiet poufności do dokumentów i wiadomości e-mail | [Automatyczne stosowanie etykiety poufności do zawartości](apply-sensitivity-label-automatically.md)|
|Ochrona zawartości w Teams i SharePoint przy użyciu etykiet poufności |[Używanie etykiet poufności z Microsoft Teams, grupami Microsoft 365 i witrynami SharePoint](sensitivity-labels-teams-groups-sites.md)|
|Użyj etykiet poufności, aby skonfigurować domyślny typ łącza udostępniania dla witryn i poszczególnych dokumentów w SharePoint i OneDrive |[Użyj etykiet poufności, aby ustawić domyślny link do udostępniania witryn i dokumentów w SharePoint i OneDrive](sensitivity-labels-default-sharing-link.md)|
|Stosowanie etykiety poufności do modelu zrozumienia dokumentu, dzięki czemu identyfikowane dokumenty w bibliotece SharePoint są automatycznie klasyfikowane i chronione |[Stosowanie etykiety poufności do modelu w usłudze Microsoft SharePoint Syntex](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model)|
|Zapobieganie lub ostrzeganie użytkowników o udostępnianiu plików lub wiadomości e-mail z określoną etykietą poufności |[Używanie etykiet poufności jako warunków w zasadach DLP](dlp-sensitivity-label-as-condition.md) |
|Zastosuj etykietę poufności do pliku, gdy otrzymuję alert, że zawartość zawierająca dane osobowe jest udostępniana i wymaga ochrony| [Badanie i korygowanie alertów w usłudze Privacy Risk Management](/privacy/priva/risk-management-alerts)|
|Stosowanie etykiety przechowywania w celu przechowywania lub usuwania plików lub wiadomości e-mail z określoną etykietą poufności|[Automatyczne stosowanie etykiety przechowywania w celu zachowania lub usunięcia zawartości](apply-retention-labels-automatically.md) |
|Odnajdywanie, etykietowanie i ochrona plików przechowywanych w lokalnych magazynach danych |[Wdrażanie skanera usługi Azure Information Protection w celu automatycznego klasyfikowania i ochrony plików](/azure/information-protection/deploy-aip-scanner)|
|Odnajdywanie, etykietowanie i ochrona plików przechowywanych w magazynach danych znajdujących się w chmurze|[Odnajdywanie, klasyfikowanie, etykietowanie i ochrona danych regulowanych i poufnych przechowywanych w chmurze](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|Etykieta SQL kolumn bazy danych przy użyciu tych samych etykiet poufności, które są używane w przypadku plików i wiadomości e-mail, dzięki czemu organizacja ma ujednolicone rozwiązanie do etykietowania, które może nadal chronić te dane ustrukturyzowane podczas eksportowania |[Klasyfikacja & odnajdywania danych dla Azure SQL Database, Azure SQL Managed Instance i Azure Synapse Analytics](/azure/azure-sql/database/data-discovery-and-classification-overview) <br /><br /> [SQL odnajdywanie i klasyfikacja danych dla SQL Server lokalnie](/sql/relational-databases/security/sql-data-discovery-and-classification)|
|Stosowanie i wyświetlanie etykiet w Power BI oraz ochrona danych, gdy są one zapisywane poza usługą|[Etykiety poufności w Power BI](/power-bi/admin/service-security-sensitivity-label-overview)|
|Monitorowanie i zrozumienie sposobu użycia etykiet poufności w mojej organizacji|[Dowiedz się więcej o klasyfikacji danych](data-classification-overview.md)|
|Rozszerzanie etykiet poufności na aplikacje i usługi innych firm|[zestaw SDK Microsoft Information Protection](/information-protection/develop/overview#microsoft-information-protection-sdk)|
|Rozszerzanie etykiet poufności na zawartość w zasobach usługi Microsoft Purview Data Map, takich jak Azure Blob Storage, Azure Files, Azure Data Lake Storage i źródła danych w wielu chmurach|[Etykietowanie w usłudze Microsoft Purview Data Map](/azure/purview/create-sensitivity-label) |

## <a name="end-user-documentation-for-sensitivity-labels"></a>Dokumentacja użytkownika końcowego dotycząca etykiet poufności

Najbardziej efektywną dokumentacją użytkownika końcowego będą dostosowane wskazówki i instrukcje podane dla wybranych nazw etykiet i konfiguracji. Możesz użyć ustawienia zasad **etykietY Podaj użytkownikom link do niestandardowej strony pomocy** , aby określić link wewnętrzny dla tej dokumentacji. Użytkownicy mogą łatwo uzyskać do niego dostęp za pomocą przycisku **Czułość** :

- W przypadku wbudowanego etykietowania: opcja menu **Dowiedz się więcej** .
- W przypadku opcji menu Klient ujednoliconego etykietowania platformy Azure Information Protection: **Pomoc i opinie** > link **Powiedz mi więcej** w oknie dialogowym Microsoft Azure Information Protection.

Aby ułatwić dostarczenie dostosowanej dokumentacji, zobacz następującą stronę i pliki do pobrania, których możesz użyć, aby pomóc w szkoleniu użytkowników: [Szkolenie użytkowników końcowych dla etykiet poufności](https://microsoft.github.io/ComplianceCxE/enduser/sensitivity/). 

Aby uzyskać podstawowe instrukcje, możesz również użyć następujących zasobów:

- [Stosowanie etykiet wrażliwości do plików i wiadomości e-mail w pakiecie Office](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
    - [Znane problemy z etykietami poufności w Office](https://support.microsoft.com/en-us/office/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)

- [Automatyczne stosowanie lub rekomendowanie etykiet poufności do plików i wiadomości e-mail w Office](https://support.office.com/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)
    - [Znane problemy z automatycznym stosowaniem lub zalecaniem etykiet poufności](https://support.office.com/article/known-issues-with-automatically-applying-or-recommending-sensitivity-labels-451698ae-311b-4d28-83aa-a839a66f6efc)

- [Przewodnik użytkownika dotyczący ujednoliconego etykietowania na platformie Azure Information Protection](/azure/information-protection/rms-client/clientv2-user-guide)

Jeśli etykiety poufności stosują szyfrowanie dokumentów PDF, te dokumenty można otwierać za pomocą Microsoft Edge na Windows lub Mac. Aby uzyskać więcej informacji i alternatywnych czytelników, zobacz [Które czytniki PDF są obsługiwane dla chronionych plików PDF?](/azure/information-protection/rms-client/protected-pdf-readers#viewing-protected-pdfs-in-microsoft-edge-on-windows-or-mac)
