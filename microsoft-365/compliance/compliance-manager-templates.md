---
title: Praca z szablonami oceniania w Menedżerze zgodności firmy Microsoft
f1.keywords:
- NOCSH
ms.author: v-jgriffee
author: jmgriffee
manager: laurawi
audience: Admin
ms.topic: article
ms.custom: admindeeplinkMAC
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Dowiedz się, jak używać szablonów do tworzenia ocen w Menedżerze zgodności firmy Microsoft i zarządzać nimi. Tworzenie i modyfikowanie szablonów przy użyciu Excel pliku.
ms.openlocfilehash: 99e243e86c66babd9a983ae6df891f4094cdbb83
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2021
ms.locfileid: "62989723"
---
# <a name="learn-about-assessment-templates-in-compliance-manager"></a>Informacje o szablonach oceniania w Menedżerze zgodności

**W tym artykule:** Dowiedz **się, jak działają szablony** i **jak nimi zarządzać** na stronie szablonów formularzy oceniania. Uzyskaj instrukcje **dotyczące tworzenia** nowych **szablonów, rozszerzania** i  modyfikowania istniejących szablonów, formatowania danych szablonu za pomocą **Excel** i eksportowania raportów **szablonów**.

> [!IMPORTANT]
> Szablony ocen dostępne dla Twojej organizacji zależą od umowy licencyjnej. [Przejrzyj szczegóły](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="templates-overview"></a>Omówienie szablonów

Szablon to struktury kontrolek do tworzenia oceny w Menedżerze zgodności. Nasz kompleksowy zestaw szablonów może pomóc Twojej organizacji w przestrzeganiu wymagań krajowych, regionalnych i branżowych dotyczących gromadzenia i używania danych.

Szablony są nazwane tak samo jak ich certyfikaty lub przepisy, na przykład szablon RODO UE i szablon ISO/IEC 27701:2019. Ponieważ za pomocą Mangera zgodności można oceniać różne typy produktów, każdy szablon jest dostarczany w dwóch wersjach: jednej, która dotyczy wstępnie zdefiniowanego produktu, takiego jak Microsoft 365, i uniwersalnej wersji, która może być dostosowana do wybranego produktu.

Należy zauważyć, że klienci Community administracji państwowej Stanów Zjednoczonych (GCC) Moderowany, GCC Wysoki i Dział obrony (DoD) nie mogą obecnie używać szablonów uniwersalnych.

## <a name="template-availability-and-licensing"></a>Dostępność i licencjonowanie szablonów

W Menedżerze zgodności są dwie kategorie szablonów: uwzględnione i Premium.

1. **Dołączone szablony** są udzielane w licencji Menedżera zgodności i obejmują najważniejsze przepisy i wymagania. Aby dowiedzieć się więcej o szablonach dostępnych w ramach umowy licencyjnej, zobacz [Szczegóły licencjonowania](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager).
2. **Premium szablonów, które** obejmują dodatkowe potrzeby i scenariusze, można uzyskać, kupując licencje szablonów.

Po rozpoczęciu tworzenia ocen Menedżer zgodności będzie śledzić, ile szablonów jest aktywnych, aby monitorować użycie. Aby dowiedzieć się więcej, zobacz [Szablony aktywne i nieaktywne](compliance-manager-templates.md#active-and-inactive-templates).

Wyświetl pełną [listę szablonów dostępnych](compliance-manager-templates-list.md) w Menedżerze zgodności.

### <a name="purchase-premium-template-licenses"></a>Kupowanie licencji szablonów premium

Licencje szablonów można uzyskać za pomocą jednej lub większej liczby tych metod, w zależności od umowy licencyjnej Menedżera zgodności. Po sfinalizowaniu zakupu szablony powinny zostać udostępnione w dzierżawie w ciągu 48 godzin.

**Komercyjna i GCC umiarkowana**

Komercyjne i GCC średnie konta mogą kupować licencje szablonów w centrum administracyjnym (dowiedz się więcej o subskrypcjach[, licencjach i rozliczeniach](/microsoft-365/commerce/)). Wybierz liczbę licencji, które chcesz kupić, i swój plan płatności.

Linki zakupów:

- [Komercyjna](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/46E9BF2A-3C8D-4A69-A7E7-3DA04687636D)
- [GCC umiarkowany](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/3129986d-5f4b-413b-a34b-b706db5a7669)

Możesz również uzyskać licencje w ramach uczestnictwa w programie Dostawca rozwiązań w chmurze [lub](https://partner.microsoft.com/membership/cloud-solution-provider) [licencjonowaniu zbiorowego](https://www.microsoft.com/licensing/licensing-programs/licensing-programs).

**GCC kont o wysokiej jakości i dod**

GCC DoD muszą kupować licencje szablonów w ramach [licencjonowania zbiorowego](https://www.microsoft.com/licensing/licensing-programs/licensing-programs).

### <a name="try-out-premium-templates"></a>Wypróbuj szablony klasy premium

Aby wypróbować szablony klasy premium przed zakupem, możesz również uzyskać wersje próbne licencji. Licencje wersji próbnej są dostępne dla maksymalnie 25 szablonów przez 90 dni. Po uzyskaniu licencji wersji próbnej szablony powinny zostać udostępnione w dzierżawie w ciągu 48 godzin.

Jeśli Twoja organizacja ma komercyjną licencję na Menedżera zgodności, możesz dowiedzieć się, jak rozpocząć wersję próbną na stronie Informacje o bezpłatnej wersji próbnej testów [premium usługi Microsoft Compliance Manager](compliance-easy-trials-compliance-manager-assessments.md).

Jeśli organizacja jest w ramach licencji GCC lub DOD, wybierz link dla odpowiedniej wersji próbnej dla organizacji:

- [GCC umiarkowany](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/87ed2908-0a8d-430a-9635-558ed42b581f)
- [GCC wysoki](https://portal.office365.us/SubscriptionDetails?OfferId=e14362d7-2c11-4a43-9c92-59f1b499b96a)
- [DOD](https://portal.apps.mil/Commerce/Trial.aspx?OfferId=17e28290-7de6-41a9-af30-f6497396ab2e)

#### <a name="active-and-inactive-templates"></a>Aktywne i nieaktywne szablony

W szablonach będzie wyświetlany stan aktywacji jako aktywny lub nieaktywny:

- Szablon jest uznawany za **aktywny** po utworzeniu oceny na podstawie tego szablonu.
- Szablon jest uznawany za **nieaktywny** , jeśli organizacja nie używa go do oceny.

Jeśli połączysz wszelkie testy z zakupionym szablonem premium, ten szablon będzie aktywny przez rok. Zakup zostanie automatycznie odnowiony, chyba że go anulujesz.

#### <a name="activated-templates-counter"></a>Licznik aktywowanych szablonów

Na górze strony szablonów formularzy oceniania **i szablonów** formularzy oceniania są aktywne szablony. Licznik zawiera liczbę szablonów w użyciu w  pominie liczbę, z których możesz korzystać zgodnie z umową licencyjną. Użycie szablonu jest liczone na poziomie certyfikacji.

Jeśli na przykład licznik zawiera dane 2/5, oznacza to, że organizacja aktywowała 2 szablony z 5 dostępnych do użycia.

Jeśli twoje dane licznika wskazują na wartość 2/5, oznacza to, że Twoja organizacja przekracza limity i musi kupić 3 szablony premium w użyciu.

Szablony dla wstępnie zdefiniowanego produktu, takiego Microsoft 365, mają wspólne licencjonowanie z wersjami uniwersalnymi tego samego szablonu. Umożliwia to stosowanie tego samego certyfikatu źródłowego dla więcej niż jednego produktu. Użycie jednej lub obu wersji tego samego szablonu spowoduje liczenie tylko jako jeden aktywowany szablon.

Aby uzyskać więcej szczegółowych informacji, zobacz [Wskazówki dotyczące licencjonowania Menedżera zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager).

## <a name="view-and-manage-templates"></a>Wyświetlanie szablonów i zarządzanie nimi

Na stronie szablonów oceniania w Menedżerze zgodności jest wyświetlana lista szablonów i kluczowych informacji na ich temat. Ta lista zawiera szablony udostępniane przez Menedżera zgodności, a także wszelkie szablony, które zostały zmodyfikowane lub utworzone przez organizację. Możesz zastosować filtry, aby znaleźć szablon na podstawie certyfikacji, zakresu produktu, kraju, branży, twórcy szablonu i tego, czy dla szablonu włączono tworzenie oceny.

Wybierz szablon z jego wiersza, aby wyprowadzić jego stronę szczegółów. Ta strona zawiera opis szablonu i dodatkowe informacje na temat certyfikacji, zakresu i kontrolek. Na tej stronie możesz wybrać odpowiednie przyciski, aby utworzyć ocenę, wyeksportować dane szablonu Excel lub zmodyfikować szablon.

## <a name="create-an-assessment-template"></a>Tworzenie szablonu oceny

Aby utworzyć własny nowy szablon na potrzeby niestandardowych ocen w Menedżerze zgodności, użyj specjalnie sformatowanych arkuszy Excel kalkulacyjnych do zbierania niezbędnych danych kontrolnych. Po zakończeniu pracy z arkuszem kalkulacyjnym zaimportujesz go do Menedżera zgodności. Aby dowiedzieć się więcej, [zobacz Tworzenie szablonu oceny](compliance-manager-templates-create.md).

## <a name="modify-an-assessment-template"></a>Modyfikowanie szablonu oceny

Podczas pracy z ocenami w Menedżerze zgodności możesz zmodyfikować utworzony szablon oceny. Proces tworzenia szablonu jest podobny do procesu tworzenia szablonu w ten sposób, że przekażesz sformatowany plik Excel z danymi szablonu. Aby dowiedzieć się więcej o tym, jak wprowadzić zmiany i jak zachować dane, które nadal chcesz zachować, zobacz [Modyfikowanie szablonu oceny](compliance-manager-templates-modify.md).

## <a name="extend-an-assessment-template"></a>Rozszerzanie szablonu oceny

Menedżer zgodności umożliwia dodanie własnych kontrolek i działań udoskonalania do istniejącego szablonu. Ten proces nosi nazwę rozszerzania szablonu. Aby rozszerzyć szablon, należy użyć specjalnych instrukcji dotyczących dodawania do danych szablonu w zależności od tego, czy rozszerzasz szablony oceniań firmy Microsoft, czy uniwersalne szablony oceniań. Aby dowiedzieć się więcej, zobacz [Rozszerzanie szablonu oceny](compliance-manager-templates-extend.md).

## <a name="format-assessment-template-data-in-excel"></a>Formatowanie danych szablonu oceny w programie Excel

Podczas tworzenia, modyfikowania lub rozszerzania szablonów ocen w Menedżerze zgodności będziesz pracować z Excel kalkulacyjnymi, które używają określonego formatu i schematu. Aby pliki zostały poprawnie zaimportowane, muszą być one poprawnie zaimportowane. Aby dowiedzieć się więcej, zobacz [Formatowanie danych szablonu oceny w programie Excel](compliance-manager-templates-format-excel.md).

## <a name="export-a-template"></a>Eksportowanie szablonu

Możesz wyeksportować Excel, który zawiera wszystkie dane szablonu. Aby go zmodyfikować, musisz wyeksportować szablon, ponieważ będzie to plik Excel edytowany i przesyłany w procesie [modyfikowania](compliance-manager-templates-modify.md). Możesz również wyeksportować szablon do użytku referencyjnego, jeśli chcesz użyć z niego danych podczas konstruowania nowego szablonu niestandardowego.

Aby wyeksportować szablon, przejdź do strony szczegółów szablonu i wybierz przycisk Eksportuj **Excel** szablonu.

Pamiętaj, że podczas eksportowania szablonu rozszerzonego z szablonu Menedżera zgodności wyeksportowany plik będzie zawierał tylko atrybuty dodane do szablonu. Wyeksportowany plik nie będzie zawierać oryginalnych danych szablonu dostarczonych przez firmę Microsoft. Aby uzyskać taki raport, zobacz instrukcje [eksportowania raportu z oceny](compliance-manager-assessments.md#export-an-assessment-report).