---
title: Dowiedz się więcej o szablonach oceny w programie Microsoft Purview Compliance Manager
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
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
description: Dowiedz się, jak używać szablonów do tworzenia ocen i zarządzać nimi w programie Microsoft Purview Compliance Manager. Tworzenie i modyfikowanie szablonów przy użyciu sformatowanego pliku programu Excel.
ms.openlocfilehash: ac4d3fb6f7a43aa642b9d8b343a68c9f38f29e25
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635650"
---
# <a name="learn-about-assessment-templates-in-compliance-manager"></a>Dowiedz się więcej o szablonach oceny w menedżerze zgodności

**W tym artykule:** Dowiedz **się, jak działają szablony** i **jak nimi zarządzać** na stronie szablonów oceny. Uzyskaj instrukcje dotyczące **tworzenia** nowych szablonów, **rozszerzania** i **modyfikowania** istniejących szablonów, **formatowania danych szablonu za pomocą programu Excel** i eksportowania **raportów szablonów**.

> [!IMPORTANT]
> Szablony oceny, które są dostępne dla Organizacji, zależą od umowy licencyjnej. [Przejrzyj szczegóły](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-compliance-manager).

## <a name="templates-overview"></a>Omówienie szablonów

Szablon to struktura mechanizmów kontroli do tworzenia oceny w menedżerze zgodności. Nasz kompleksowy zestaw szablonów może pomóc Twojej organizacji w spełnieniu krajowych, regionalnych i branżowych wymagań regulujących zbieranie i wykorzystywanie danych. Odnosimy się do szablonów o tej samej nazwie co ich podstawowa certyfikacja lub rozporządzenie, takie jak szablon RODO UE i szablon ISO/IEC 27701:2019.

## <a name="template-versions-microsoft-and-universal"></a>Wersje szablonów: Microsoft i uniwersalne

Menedżer zgodności może służyć do oceny różnych typów produktów. Wszystkie szablony, z wyjątkiem domyślnego szablonu [punktu odniesienia usługi Microsoft Data Protection](compliance-manager-assessments.md#data-protection-baseline-default-assessment) , są dostępne w dwóch wersjach:

1. Wersja, która ma zastosowanie do wstępnie zdefiniowanego produktu, takiego jak Microsoft 365, i
2. Uniwersalna wersja, która może być dostosowana do innych produktów.

Oceny z szablonów uniwersalnych są bardziej uogólnione, ale oferują rozszerzoną wszechstronność, ponieważ mogą ułatwić śledzenie zgodności organizacji w wielu produktach.

Należy pamiętać, że klienci us Government Community (GCC) Moderate, GCC High i Department of Defense (DoD) nie mogą obecnie używać szablonów uniwersalnych.

## <a name="template-availability-and-licensing"></a>Dostępność szablonu i licencjonowanie

W menedżerze zgodności istnieją dwie kategorie szablonów: dołączone i premium.

1. **Dołączone szablony są przyznawane** przez licencję programu Compliance Manager i obejmują kluczowe przepisy i wymagania. Aby dowiedzieć się więcej o tym, jakie szablony są dostępne w ramach umowy licencyjnej, zobacz [szczegóły licencjonowania](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager).
2. **Szablony Premium** na potrzeby dodatkowych potrzeb i scenariuszy można uzyskać, kupując licencje szablonów.

Po rozpoczęciu tworzenia ocen menedżer zgodności będzie śledzić liczbę aktywnych szablonów, aby można było monitorować użycie. Aby dowiedzieć się więcej, zobacz [Aktywne i nieaktywne szablony](compliance-manager-templates.md#active-and-inactive-templates).

Wyświetl [pełną listę szablonów](compliance-manager-templates-list.md) dostępnych w Menedżerze zgodności.

### <a name="purchase-premium-template-licenses"></a>Kupowanie licencji szablonów w warstwie Premium

Licencje szablonów można uzyskać za pomocą co najmniej jednej z tych metod, w zależności od umowy licencyjnej programu Compliance Manager. Po sfinalizowaniu zakupu szablony powinny zostać udostępnione w dzierżawie w ciągu 48 godzin.

**Komercyjne i GCC Moderate**

Konta komercyjne i konta GCC Moderate mogą kupować licencje szablonów w centrum administracyjnym ([dowiedz się więcej o subskrypcjach, licencjach i rozliczeniach](/microsoft-365/commerce/)). Wybierz liczbę licencji, które chcesz kupić, i plan płatności.

Linki do zakupów:

- [Handlowych](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/46E9BF2A-3C8D-4A69-A7E7-3DA04687636D)
- [GCC Moderate](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/3129986d-5f4b-413b-a34b-b706db5a7669)

Licencje można również uzyskać poprzez udział w [programie cloud solution provider](https://partner.microsoft.com/membership/cloud-solution-provider) lub [licencjonowaniu zbiorczym](https://www.microsoft.com/licensing/licensing-programs/licensing-programs).

**Konta GCC High i DOD**

Konta GCC High i DOD muszą kupować licencje szablonów w ramach [licencjonowania zbiorowego](https://www.microsoft.com/licensing/licensing-programs/licensing-programs).

### <a name="try-out-premium-templates"></a>Wypróbuj szablony w warstwie Premium

Aby wypróbować szablony premium przed dokonaniem zakupu, możesz również uzyskać wersje próbne licencji. Licencje próbne są dobre dla maksymalnie 25 szablonów przez 90 dni. Po uzyskaniu licencji próbnej szablony powinny zostać udostępnione w dzierżawie w ciągu 48 godzin.

Jeśli Twoja organizacja ma komercyjną licencję programu Compliance Manager, możesz dowiedzieć się, jak rozpocząć wersję próbną, korzystając z [bezpłatnej wersji próbnej ocen premium programu Microsoft Purview Compliance Manager](compliance-easy-trials-compliance-manager-assessments.md).

Jeśli Twoja organizacja korzysta z licencji GCC lub DOD, wybierz odpowiedni link do wersji próbnej dla twojej organizacji:

- [GCC Moderate](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/87ed2908-0a8d-430a-9635-558ed42b581f)
- [GCC High](https://portal.office365.us/SubscriptionDetails?OfferId=e14362d7-2c11-4a43-9c92-59f1b499b96a)
- [DOD](https://portal.apps.mil/Commerce/Trial.aspx?OfferId=17e28290-7de6-41a9-af30-f6497396ab2e)

#### <a name="active-and-inactive-templates"></a>Aktywne i nieaktywne szablony

Szablony będą wyświetlać stan aktywacji jako aktywny lub nieaktywny:

- Szablon jest uznawany za **aktywny** po utworzeniu oceny na podstawie tego szablonu.
- Szablon jest uznawany za **nieaktywny** , jeśli organizacja nie używa go do oceny.

Jeśli połączysz jakiekolwiek oceny z zakupionym szablonem premium, ten szablon będzie aktywny przez jeden rok. Zakup zostanie automatycznie odnowiony, chyba że anulujesz.

#### <a name="activated-templates-counter"></a>Licznik aktywowanych szablonów

Strona oceny i strona szablonów oceny mają **uaktywniony licznik szablonów** u góry. Licznik wyświetla liczbę używanych szablonów poza liczbą, której kwalifikujesz się do użycia zgodnie z umową licencyjną. Użycie szablonu jest liczone na poziomie certyfikacji.

Jeśli na przykład licznik ma wartość 2/5, oznacza to, że organizacja aktywowała 2 szablony z 5 dostępnych do użycia.

Jeśli licznik zawiera wartość 5/2, oznacza to, że twoja organizacja przekracza limity i musi kupić 3 używane szablony premium.

Szablony dla wstępnie zdefiniowanego produktu, takiego jak Microsoft 365, mają wspólne licencjonowanie z uniwersalnymi wersjami tego samego szablonu. Dzięki temu można używać tego samego certyfikatu bazowego dla więcej niż jednego produktu. Użycie jednej lub obu wersji tego samego szablonu będzie liczone tylko jako jeden aktywowany szablon.

Aby uzyskać więcej informacji, zobacz [Wskazówki dotyczące licencjonowania programu Compliance Manager](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager).

## <a name="view-and-manage-templates"></a>Wyświetlanie szablonów i zarządzanie nimi

Na stronie szablonów oceny w Menedżerze zgodności jest wyświetlana lista szablonów i najważniejszych informacji na ich temat. Lista zawiera szablony udostępniane przez menedżera zgodności, a także wszelkie szablony zmodyfikowane lub utworzone przez organizację. Filtry można zastosować, aby znaleźć szablon na podstawie certyfikacji, zakresu produktu, kraju, branży, kto go utworzył i czy szablon jest włączony do tworzenia oceny.

Wybierz szablon z wiersza, aby wyświetlić jego stronę szczegółów. Ta strona zawiera opis szablonu oraz dodatkowe informacje na temat certyfikacji, zakresu i szczegółów kontrolek. Na tej stronie możesz wybrać odpowiednie przyciski, aby utworzyć ocenę, wyeksportować dane szablonu do programu Excel lub zmodyfikować szablon.

## <a name="create-an-assessment-template"></a>Tworzenie szablonu oceny

Aby utworzyć własny nowy szablon dla ocen niestandardowych w Menedżerze zgodności, użyjesz specjalnie sformatowanego arkusza kalkulacyjnego programu Excel do zmontowania niezbędnych danych kontrolnych. Po ukończeniu arkusza kalkulacyjnego zaimportujesz go do Menedżera zgodności. Aby dowiedzieć się więcej, zobacz [Tworzenie szablonu oceny](compliance-manager-templates-create.md).

## <a name="modify-an-assessment-template"></a>Modyfikowanie szablonu oceny

Podczas pracy z ocenami w Menedżerze zgodności możesz zmodyfikować utworzony szablon oceny. Proces jest podobny do procesu tworzenia szablonu, ponieważ przekażesz sformatowany plik programu Excel z danymi szablonu. Aby dowiedzieć się więcej na temat sposobu wprowadzania zmian i zachowywania danych, które nadal chcesz zachować, zobacz [Modyfikowanie szablonu oceny](compliance-manager-templates-modify.md).

## <a name="extend-an-assessment-template"></a>Rozszerzanie szablonu oceny

Menedżer zgodności oferuje opcję dodawania własnych kontrolek i akcji ulepszania do istniejącego szablonu. Ten proces jest nazywany rozszerzaniem szablonu. Aby rozszerzyć szablon, należy użyć specjalnych instrukcji do dodawania danych szablonu w zależności od tego, czy rozszerzasz szablony oceny firmy Microsoft, czy szablony oceny uniwersalnej. Aby dowiedzieć się więcej, zobacz [Rozszerzanie szablonu oceny](compliance-manager-templates-extend.md).

## <a name="format-assessment-template-data-in-excel"></a>Formatowanie danych szablonu oceny w programie Excel

Podczas tworzenia, modyfikowania lub rozszerzania szablonów oceny w Menedżerze zgodności będziesz pracować z arkuszami kalkulacyjnymi programu Excel, które używają określonego formatu i schematu. Aby pliki zostały prawidłowo zaimportowane, należy przestrzegać tych specyfikacji. Aby dowiedzieć się więcej, zobacz [Formatowanie danych szablonu oceny w programie Excel](compliance-manager-templates-format-excel.md).

## <a name="export-a-template"></a>Eksportowanie szablonu

Możesz wyeksportować plik programu Excel zawierający wszystkie dane szablonu. Aby go zmodyfikować, musisz wyeksportować szablon, ponieważ będzie to plik programu Excel, który będzie edytowany i przekazywany w [procesie modyfikacji](compliance-manager-templates-modify.md). Możesz również wyeksportować szablon do odwołania, jeśli chcesz używać z niego danych podczas tworzenia nowego szablonu niestandardowego.

Aby wyeksportować szablon, przejdź do strony szczegółów szablonu i wybierz przycisk **Eksportuj do programu Excel** .

Należy pamiętać, że podczas eksportowania szablonu rozszerzonego z szablonu programu Compliance Manager wyeksportowany plik będzie zawierać tylko atrybuty dodane do szablonu. Wyeksportowany plik nie będzie zawierać oryginalnych danych szablonu dostarczonych przez firmę Microsoft. Aby uzyskać taki raport, zobacz instrukcje dotyczące [eksportowania raportu oceny](compliance-manager-assessments.md#export-an-assessment-report).
