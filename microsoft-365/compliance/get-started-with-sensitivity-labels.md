---
title: Wprowadzenie do etykiet wrażliwości
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
description: Wszystko gotowe do wdrożenia etykiet wrażliwości w celu ochrony danych Twojej organizacji, ale nie wiesz, od czego zacząć? Przeczytaj kilka praktycznych wskazówek, które pomogą Ci rozpocząć podróż z etykietami.
ms.openlocfilehash: adc939d44715bcfaeb97cdbfa530f55a5aeecd4e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322089"
---
# <a name="get-started-with-sensitivity-labels"></a>Wprowadzenie do etykiet wrażliwości

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Aby uzyskać informacje na temat etykiet wrażliwości i sposobu ich ochrony danych organizacji, zobacz Informacje [o etykietach wrażliwości](sensitivity-labels.md).

Jeśli masz [usługę Azure Information Protection](/azure/information-protection/what-is-information-protection) i nadal używasz etykiet usługi Azure Information Protection, które były zarządzane z poziomu portalu Azure Portal, musisz przeprowadzić migrację tych etykiet do [ujednoliconej platformy etykiet](/azure/information-protection/faqs#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform). W Windows komputerach możesz następnie wybrać klienta etykiet, którego będzie [używać dla](/azure/information-protection/rms-client/use-client#choose-which-labeling-client-to-use-for-windows-computers) opublikowanych etykiet wrażliwości.

Gdy wszystko będzie gotowe do rozpoczęcia ochrony danych organizacji za pomocą etykiet wrażliwości:

1. **Utwórz etykiety.** Utwórz etykiety wrażliwości i nadaj ich nazwy zgodnie z taksonomią klasyfikacji organizacji dla różnych poziomów wrażliwości zawartości. Używaj popularnych nazw lub terminów, które mają sens dla użytkowników. Jeśli nie masz jeszcze taksonomii ustalonej, rozważ rozpoczęcie od nazw etykiet, takich jak Osobiste, Publiczne, Ogólne, Poufne i Wysoce poufne. Za pomocą etykiet podrzędnych można następnie grupować podobne etykiety według kategorii. Podczas tworzenia etykiety użyj tekstu etykiety narzędzia, aby ułatwić użytkownikom wybranie odpowiedniej etykiety.
    
    Aby uzyskać bardziej rozbudowane wskazówki dotyczące definiowania taksonomii klasyfikacji, pobierz oficjalny dokument "Klasyfikacja danych & taksonomii wrażliwości" z Portalu [zaufania usług](https://aka.ms/DataClassificationWhitepaper).

2. **Zdefiniuj zakres, jaki może mieć każda etykieta.** Skonfiguruj ustawienia ochrony, które chcesz skojarzyć z każdą etykietą. Na przykład możesz chcieć, aby zawartość wrażliwości (na przykład etykieta "Ogólne" zawierała tylko nagłówek lub stopkę), a wyższa zawartość wrażliwości (na przykład etykieta "Poufne") powinna zawierać znak wodny i szyfrowanie.

3. **Publikowanie etykiet.** Po skonfigurowaniu etykiet wrażliwości opublikuj je przy użyciu zasad etykiet. Zdecyduj, którzy użytkownicy i grupy powinni mieć etykiety i jakich ustawień zasad należy użyć. Pojedyncza etykieta jest nadaje się do ponownego użycia — definiujesz ją raz, a następnie możesz dołączyć do kilku zasad etykiet przypisanych do różnych użytkowników. Na przykład możesz pilotować etykiety wrażliwości, przypisując zasady dotyczące etykiet tylko kilku użytkownikom. Następnie, gdy wszystko będzie gotowe do rozdysłania etykiet w organizacji, możesz utworzyć nowe zasady etykiet dla etykiet i tym razem określić wszystkich użytkowników.


> Być może kwalifikujesz się do automatycznego tworzenia etykiet domyślnych i domyślnych zasad etykiet, które zajmą się krokami od 1 do 3. Aby uzyskać więcej informacji, zobacz [Domyślne etykiety i zasady dotyczące Microsoft Information Protection](mip-easy-trials.md).

Podstawowy przepływ wdrażania i stosowania etykiet wrażliwości:

![Diagram przedstawiający przepływ pracy dla etykiet wrażliwości.](../media/Sensitivity-label-flow.png)

## <a name="subscription-and-licensing-requirements-for-sensitivity-labels"></a>Wymagania dotyczące subskrypcji i licencjonowania etykiet wrażliwości

Wiele różnych subskrypcji obsługuje etykiety wrażliwości, a wymagania licencyjne użytkowników zależą od tego, z których funkcji korzystasz.

Aby wyświetlić opcje licencjonowania użytkowników w celu skorzystania z funkcji zgodności Microsoft 365, zobacz wskazówki Microsoft 365 dotyczące licencjonowania w zakresie zabezpieczeń [& zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). Aby uzyskać etykiety wrażliwości, zobacz sekcję [Ochrona informacji:](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-sensitivity-labeling) etykiety wrażliwości i powiązany z nią plik [PDF](https://go.microsoft.com/fwlink/?linkid=2139145) do pobrania, aby uzyskać informacje o wymaganiach licencyjnych na poziomie funkcji.

## <a name="permissions-required-to-create-and-manage-sensitivity-labels"></a>Uprawnienia wymagane do tworzenia etykiet poufności i zarządzania nimi

Członkowie Twojego zespołu zgodności, którzy będą tworzyć etykiety wrażliwości, muszą mieć uprawnienia do Centrum zgodności platformy Microsoft 365.

Domyślnie administratorzy globalni Twojej dzierżawy mają dostęp do tego centrum administracyjnego i mogą udzielać służbom zgodności z przepisami i innym osobom dostępu bez nadawania im wszystkich uprawnień administratora dzierżawy. W przypadku tego delegowanego ograniczonego dostępu administratora dodaj użytkowników do grupy ról **Administrator** danych zgodności, **Administrator zgodności** lub **Administrator** zabezpieczeń. 

Zamiast korzystania z ról domyślnych możesz utworzyć nową grupę ról i dodać do tej grupy role  administratora etykiet wrażliwości lub  konfigurację organizacji. W przypadku roli tylko do odczytu użyj **czytnika etykiet wrażliwości**. 

> [!NOTE]
> Teraz w wersji Preview możesz używać następujących grup ról:
> - **Ochrona informacji**
> - **Administratorzy ochrony informacji**
> - **Analitycy ochrony informacji**
> - **Schoweki ochrony informacji**
> - **Czytniki informacji**
>
> Aby zapoznać się z objaśnieniami każdej z nich i nowo zawartymi rolami, wybierz grupę ról w okienku <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a> >  Uprawności **&** >  >  RoleZaplanowania, a następnie przejrzyj opis w okienku wysuwanym. Lub zobacz [Grupy ról w Centrum & zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center).

Aby uzyskać instrukcje dotyczące dodawania użytkowników do domyślnej grupy ról, ról lub tworzenia własnych grup ról, zobacz Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md).

Te uprawnienia są wymagane tylko do tworzenia i konfigurowania etykiet wrażliwości oraz ich zasad etykiet. Nie są one wymagane do stosowania etykiet w aplikacjach i usługach. Jeśli w przypadku określonych konfiguracji związanych z etykietami wrażliwości potrzebne są dodatkowe uprawnienia, będą one wymienione w odpowiednich instrukcjach dokumentacji.

## <a name="deployment-strategy-for-sensitivity-labels"></a>Strategia wdrażania etykiet wrażliwości
Pomyślną strategią wdrażania etykiet wrażliwości w organizacji jest utworzenie roboczego zespołu wirtualnego, który identyfikuje wymagania biznesowe i techniczne oraz zarządza nimi, sprawdza test koncepcji, wewnętrzne punkty kontrolne i zatwierdzenia oraz wdraża końcowe wdrożenie w środowisku produkcyjnym.

Używając tabeli w następnej sekcji, zalecamy zidentyfikowanie jednego lub dwóch najlepszych scenariuszy zamapowania na najbardziej wywłaszne wymagania biznesowe. Po wdrożeniu tych scenariuszy wróć do listy, aby zidentyfikować następny jeden lub dwa priorytety wdrożenia.

Dodatkowe ogólne wskazówki dotyczące wdrażania i najlepsze rozwiązania znajdziesz w Przewodniku po przyspieszaniu wdrażania usługi [Microsoft Information Protection](https://microsoft.github.io/ComplianceCxE/dag/mip-dlp/) i Zapobieganie utracie danych, jednym z zasobów w witrynie Zespołu przyspieszania przez klienta [(CAT, Customer Acceleration Team](https://microsoft.github.io/ComplianceCxE/)).

## <a name="common-scenarios-for-sensitivity-labels"></a>Typowe scenariusze dotyczące etykiet wrażliwości

Wszystkie scenariusze wymagają utworzenia [i skonfigurowania etykiet wrażliwości oraz ich zasad](create-sensitivity-labels.md).

|Chcę...|Dokumentacja|
|----------------|---------------|
|Zarządzanie etykietami wrażliwości dla Office, tak aby zawartość była oznaczana podczas tworzenia — obejmuje obsługę ręcznego oznaczania etykiet na wszystkich platformach |[Zarządzanie etykietami poufności w aplikacjach Office](sensitivity-labels-office-apps.md)|
|Rozszerzanie etykiet do Eksploratora plików i programu PowerShell o dodatkowe funkcje dla aplikacji pakietu Office Windows (w razie potrzeby)|[Ujednolicony klient etykiet usługi Azure Information Protection dla komputerów Windows](/azure/information-protection/rms-client/aip-clientv2)|
|Szyfrowanie dokumentów i wiadomości e-mail za pomocą etykiet wrażliwości oraz ograniczanie dostępu do tej zawartości i sposobu jej stosowania |[Ograniczanie dostępu do zawartości przy użyciu etykiet wrażliwości w celu zastosowania szyfrowania](encryption-sensitivity-labels.md)|
|Włączanie etykiet wrażliwości dla Office w sieci Web z obsługą współtworzenie, zbierania elektronicznych materiałów dowodowych, ochrony przed utratą danych, wyszukiwania — nawet wtedy, gdy dokumenty są szyfrowane | [Włączanie etykiet wrażliwości dla Office w SharePoint i OneDrive](sensitivity-labels-sharepoint-onedrive-files.md)
|Używanie funkcji współtworzenia i Autozaza Office w aplikacjach klasycznych, gdy dokumenty są szyfrowane | [Włączanie współtworowania plików zaszyfrowanych przy użyciu etykiet wrażliwości](sensitivity-labels-coauthoring.md)
|Automatyczne stosowanie etykiet wrażliwości do dokumentów i wiadomości e-mail | [Automatyczne stosowanie etykiet wrażliwości do zawartości](apply-sensitivity-label-automatically.md)|
|Etykiety wrażliwości chronią zawartość w Teams i SharePoint |[Używanie etykiet wrażliwości z Microsoft Teams, Microsoft 365 grupami i SharePoint sieci Web](sensitivity-labels-teams-groups-sites.md)|
|Użyj etykiet wrażliwości, aby skonfigurować domyślny typ linku udostępniania dla witryn i poszczególnych dokumentów w SharePoint i OneDrive |[Użyj etykiet wrażliwości, aby ustawić domyślny link udostępniania dla witryn i dokumentów w SharePoint i OneDrive](sensitivity-labels-default-sharing-link.md)|
|Stosowanie etykiety wrażliwości do modelu zrozumienia dokumentu w celu automatycznego klasyfikowania i ochrony SharePoint dokumentów w bibliotece dokumentów |[Stosowanie etykiet wrażliwości do modelu w aplikacji Microsoft SharePoint Syntex](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model)|
|Uniemożliwianie lub ostrzeganie użytkowników o udostępnianiu plików lub wiadomości e-mail z określoną etykietą wrażliwości |[Używanie etykiet wrażliwości jako warunków zasad DLP](dlp-sensitivity-label-as-condition.md) |
|Stosowanie etykiety przechowywania w celu przechowywania lub usuwania plików lub wiadomości e-mail z określoną etykietą wrażliwości|[Automatyczne stosowanie etykiety przechowywania w celu zachowania lub usunięcia zawartości](apply-retention-labels-automatically.md) |
|Odnajdowanie, oznaczanie i chroninie plików przechowywanych w lokalnych magazynach danych |[Wdrażanie programu Azure Information Protection w celu automatycznego klasyfikowania i chronienia plików](/azure/information-protection/deploy-aip-scanner)|
|Odnajdowanie, oznaczanie i chroninie plików przechowywanych w magazynach danych przechowywanych w chmurze|[Odnajdowanie, klasyfikowanie, oznaczanie i ochrona danych chronionych zgodnie z regulacjami regulacyjną i poufnymi przechowywanymi w chmurze](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|Stosowanie i wyświetlanie etykiet Power BI danych oraz ochrona danych podczas ich zapisania poza usługą|[Etykiety wrażliwości w Power BI](/power-bi/admin/service-security-sensitivity-label-overview)|
|Monitorowanie i zrozumienie sposobu, w jaki etykiety wrażliwości są używane w mojej organizacji|[Informacje o klasyfikacji danych](data-classification-overview.md)|
|Rozszerzanie etykiet wrażliwości na usługi i aplikacje innych firm|[Microsoft Information Protection SDK](/information-protection/develop/overview#microsoft-information-protection-sdk)|
|Rozszerzanie etykiet wrażliwości na zawartość w obrębie zasobów usługi Azure Purview, takich jak usługa Azure Blob Storage, pliki platformy Azure, usługa Azure Data Lake Storage i wielochmurzeowe źródła danych|[Oznaczanie etykietami w usłudze Azure Purview](/azure/purview/create-sensitivity-label) |


## <a name="end-user-documentation-for-sensitivity-labels"></a>Dokumentacja użytkownika końcowego do etykiet wrażliwości

Najbardziej skuteczną dokumentacją dla użytkowników końcowych będą dostosowane wskazówki i instrukcje dotyczące nazw etykiet i konfiguracji, które wybierzesz. Możesz użyć ustawienia zasad etykiet Udostępnij użytkownikom link do niestandardowej strony pomocy **,** aby określić wewnętrzny link do tej dokumentacji. Użytkownicy mogą łatwo uzyskać do niego dostęp za pomocą **przycisku** Charakter:

- Wbudowane opcje menu Etykiety: **Dowiedz się więcej** .
- W przypadku klienta ujednoliconego etykiet usługi Azure Information **Protection: opcja** **menu Pomoc i** opinie > linku Powiedz mi więcej w oknie dialogowym Ochrona Microsoft Azure informacji.

Aby ułatwić dostarczenie dostosowanej dokumentacji, zobacz następującą stronę i materiały do pobrania, których można użyć w celu przeszkolenia użytkowników: Szkolenia użytkownika końcowego dotyczące [etykiet wrażliwości](https://microsoft.github.io/ComplianceCxE/enduser/sensitivity/). 

Podstawowe instrukcje można również znaleźć w następujących zasobach:

- [Stosowanie etykiet wrażliwości do plików i wiadomości e-mail w pakiecie Office](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
    - [Znane problemy z etykietami wrażliwości w Office](https://support.microsoft.com/en-us/office/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)

- [Automatyczne stosowanie etykiet wrażliwości do plików i wiadomości e-mail w wiadomościach e-mail w programie Office](https://support.office.com/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)
    - [Znane problemy dotyczące automatycznego stosowania lub polecania etykiet wrażliwości](https://support.office.com/article/known-issues-with-automatically-applying-or-recommending-sensitivity-labels-451698ae-311b-4d28-83aa-a839a66f6efc)

- [Ujednolicony przewodnik użytkownika usługi Azure Information Protection z etykietami](/azure/information-protection/rms-client/clientv2-user-guide)

Jeśli etykiety wrażliwości stosują szyfrowanie w przypadku dokumentów PDF, można je otwierać za pomocą Microsoft Edge na Windows komputerach Mac. Aby uzyskać więcej informacji i uzyskać informacje alternatywne, zobacz Które czytniki [plików PDF są obsługiwane w przypadku chronionych plików PDF?](/azure/information-protection/rms-client/protected-pdf-readers#viewing-protected-pdfs-in-microsoft-edge-on-windows-or-mac)
