---
title: Konfigurowanie bezpiecznego udostępniania plików i dokumentów oraz współpracy z Teams w Microsoft 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-securecollab
- m365solution-overview
ms.custom:
- M365solutions
- seo-marvel-jun2020
f1.keywords: NOCSH
recommendations: false
description: Poznaj najlepsze rozwiązania dotyczące konfigurowania bezpiecznej współpracy i udostępniania plików w Teams w celu ochrony danych na podstawie ich poufności.
ms.openlocfilehash: aadc2bf092713ffde68cd8fb9824d837c2f14acf
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64935418"
---
# <a name="set-up-secure-file-sharing-and-collaboration-with-microsoft-teams"></a>Konfigurowanie bezpiecznego udostępniania plików i współpracy z Microsoft Teams

Możliwość łatwego udostępniania plików i dokumentów odpowiednim osobom przy jednoczesnym zapobieganiu nadmiernemu udostępnianiu jest kluczem do sukcesu organizacji. Obejmuje to możliwość bezpiecznego udostępniania poufnych lub innych poufnych danych tylko tym, którzy powinni mieć do nich dostęp. W zależności od projektu może to obejmować udostępnianie poufnych danych osobom spoza organizacji.

Te wskazówki dotyczące rozwiązania do współpracy obejmują dwa składniki ułatwiające:

- Wdrażanie Teams z odpowiednim poziomem ochrony dla każdego projektu
- Konfigurowanie udostępniania zewnętrznego przy użyciu odpowiednich ustawień zabezpieczeń dla każdego projektu

![Wdróż Teams z odpowiednią ochroną i skonfiguruj udostępnianie zewnętrzne przy użyciu odpowiednich ustawień zabezpieczeń.](..\media\solutions-architecture-center\secure-collaboration-overview.png)

Jeśli wszechstronne i łatwe w użyciu narzędzia do współpracy plików nie są dostępne, użytkownicy często będą współpracować, wysyłając dokumenty pocztą e-mail. Jest to żmudna i podatna na błędy metoda współpracy i może zwiększyć ryzyko niewłaściwego udostępniania informacji. Jeśli użytkownicy uważają, że udostępnianie plików jest zbyt trudne, mogą powrócić do używania produktów konsumenckich, które nie są zarządzane przez it. Może to stanowić jeszcze większe ryzyko.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxMmL?autoplay=false]

Dzięki Microsoft 365 można wdrożyć Teams z różnymi konfiguracjami, które ułatwiają:

- Ochrona własności intelektualnej
- Umożliwianie łatwej współpracy z dokumentami i innymi plikami
- Tworzenie równowagi między zabezpieczeniami a użytecznością, która zwiększa zadowolenie użytkowników i zmniejsza ryzyko wystąpienia w tle it

Większość organizacji ma różne informacje o różnym stopniu poufności i różnym stopniu wpływu na działalność, jeśli informacje są niewłaściwie udostępniane. W zależności od poufności danej informacji możesz zezwolić na udostępnianie za pomocą następujących elementów:

- Każdy (nieuwierzytelniony)
- Osoby w organizacji
- Określone osoby w organizacji
- Określone osoby w organizacji i poza nią

Informacje, takie jak broszury marketingowe, są przeznaczone do udostępniania szeroko poza organizacją. Informacje, takie jak menu kafeterii, nie są przeznaczone do udostępniania zewnętrznego, ale nie miałyby wpływu na działalność biznesową, gdyby były udostępniane zewnętrznie. Tego typu informacje wymagają niewielkiej ochrony lub nie wymagają żadnej ochrony.

Te same broszury marketingowe, będąc w trakcie opracowywania, mogą być udostępniane tylko w organizacji. W takim przypadku domyślne ustawienia udostępniania w Teams mogą być wystarczające.

Informacje o nowym produkcie, który jest w trakcie opracowywania, mogą być uważane za wrażliwe, nawet w organizacji. W tym przypadku może być odpowiedni większy stopień ochrony. Możesz na przykład ograniczyć dostęp do tych informacji do członków określonego zespołu. W zależności od projektu może być konieczna współpraca z osobami spoza organizacji, takimi jak dostawca lub organizacja partnerska.

Informacje, które mają kluczowe znaczenie dla powodzenia organizacji lub mają rygorystyczne wymagania dotyczące zabezpieczeń lub zgodności, mogą wymagać jeszcze większego poziomu ochrony.

![Skala ryzyka od niskiego (wydana broszura) do wysokiego (poufne dane biznesowe).](../media/solutions-architecture-center/SecureCollaboration-SensitivityAndBusinessImpactofSharing-fromVisio.png)

We wszystkich powyższych scenariuszach można używać zespołów w Microsoft Teams do przechowywania, udostępniania i współpracy nad informacjami.

Aby skonfigurować bezpieczną współpracę, należy użyć tych Microsoft 365 możliwości i funkcji.

|Produkt lub składnik|Możliwość lub funkcja|Licencjonowanie|
|---|---|---|
|Ochrona usługi Office 365 w usłudze Microsoft Defender|Sejf załączników dla spo, OneDrive i Teams; Sejf dokumenty; linki Sejf dla Teams|Microsoft 365 E1, E3 i E5|
|SharePoint|Zasady udostępniania witryn i plików, uprawnienia do udostępniania witryn, linki do udostępniania, żądania dostępu, ustawienia udostępniania gościa witryny|Microsoft 365 E1, E3 i E5|
|Microsoft Teams|Dostęp gościa, zespoły prywatne, kanały prywatne, kanały udostępnione|Microsoft 365 E1, E3 i E5|
|Microsoft Purview|Etykiety wrażliwości|Microsoft 365 E3 i E5|

## <a name="collaboration-governance-framework-for-teams-and-microsoft-365"></a>Struktura ładu współpracy dla Teams i Microsoft 365

Microsoft 365 oferuje wiele opcji zarządzania rozwiązaniem do współpracy. Zalecamy użycie tej zawartości wdrożenia wraz z [zawartością ładu współpracy](collaboration-governance-overview.md) w celu utworzenia najlepszego rozwiązania do współpracy dla organizacji.

### <a name="securing-teams-for-sensitive-and-highly-sensitive-data"></a>Zabezpieczanie Teams danych poufnych i wysoce poufnych

Aby zarządzać dostępem do informacji o różnych czułościach, opracowaliśmy [trzy różne warstwy ochrony dla Teams](configure-teams-three-tiers-protection.md). Możesz dostosować dowolną z tych warstw, aby lepiej zaspokoić potrzeby lub firmę.

![Grafika przedstawiająca trzy poziomy ochrony Teams.](../media/solutions-architecture-center/Teams-tiers-of-protection-1.png)

Te warstwy — *punkt odniesienia*, *wrażliwe* i *wysoce wrażliwe* — stopniowo zwiększają ochronę, która pomaga zapobiegać nadmiernemu udostępnianiu i potencjalnym wyciekom informacji, jak pokazano w poniższej tabeli.

|-|Warstwa odniesienia|Warstwa wrażliwa|Warstwa wysoce wrażliwa|
|---|---|---|---|
|Zespół publiczny lub prywatny|Dowolna z tych opcji|Prywatny|Prywatny|
|Udostępnianie bez uwierzytelniania|Zablokowany|Zablokowany|Zablokowany|
|Udostępnianie plików|Dozwolone|Dozwolone|Tylko właściciele zespołu mogą udostępniać.|
|Członkostwo w zespole|Każdy może dołączyć do zespołów publicznych.<br>Zatwierdzenie właściciela zespołu wymagane do dołączenia do zespołów prywatnych.|Zatwierdzenie właściciela zespołu wymagane do dołączenia.|Zatwierdzenie właściciela zespołu wymagane do dołączenia.|
|Szyfrowanie dokumentów|||Dostępne z etykietą poufności|
|Udostępnianie gościa|Dozwolone|Może być dozwolone lub zablokowane|Może być dozwolone lub zablokowane|
|Urządzenia niezarządzane|Brak ograniczeń|Dostęp tylko do sieci Web|Zablokowany|

Konfigurowanie tych warstw obejmuje:

- Konfigurowanie ustawień w Teams dostępu gościa i kanałów prywatnych
- Konfigurowanie ustawień w skojarzonej witrynie SharePoint zespołu na potrzeby udostępniania wewnętrznego i gościa, żądań dostępu i łączy udostępniania
- W przypadku warstw *poufnych* i *wysoce poufnych* konfigurowanie etykiet poufności w celu klasyfikowania zespołów oraz kontrolowanie udostępniania gości i dostępu z urządzeń niezarządzanych
- W przypadku warstwy *wysoce wrażliwej* konfigurowanie etykiety poufności w celu szyfrowania dokumentów, do których jest stosowana

Zacznij od warstwy odniesienia, a następnie dodaj zespoły, które używają *warstw poufnych* i *wysoce poufnych* , zgodnie z potrzebami, aby chronić informacje w organizacji. Aby rozpocząć pracę, zobacz następujące zasoby:

- [Konfigurowanie zespołów z ochroną punktu odniesienia](configure-teams-baseline-protection.md)
- [Konfigurowanie zespołów z ochroną danych poufnych](configure-teams-sensitive-protection.md)
- [Konfigurowanie zespołów z ochroną danych wysoce poufnych](configure-teams-highly-sensitive-protection.md)

Jeśli masz wysoce poufny projekt, który wymaga dodatkowej ochrony przed udostępnianiem nawet w organizacji, możesz skonfigurować zespół, który używa własnej etykiety poufności do szyfrowania plików, aby tylko członkowie zespołu mogli je odczytać. Aby uzyskać szczegółowe informacje [, zobacz Konfigurowanie zespołu z izolacją zabezpieczeń](secure-teams-security-isolation.md) .

### <a name="sharing-with-people-outside-your-organization"></a>Udostępnianie osobom spoza organizacji

Może być konieczne [udostępnienie informacji o dowolnej poufności osobom spoza organizacji](collaborate-with-people-outside-your-organization.md). Może to się wahać od udostępniania pojedynczego dokumentu pojedynczej osobie do współpracy nad dużym projektem z dużą organizacją partnerską lub niezależnymi osobami z całego świata. W Microsoft 365 ten zakres udostępniania zewnętrznego można łatwo i z odpowiednimi zabezpieczeniami, aby chronić poufne informacje.

Te zasoby pomogą Ci rozpocząć konfigurowanie środowiska do współpracy z osobami spoza organizacji:

- [Współpracuj nad dokumentami w](collaborate-on-documents.md) celu udostępniania pojedynczych plików folderów.
- [Współpracuj w witrynie](collaborate-in-site.md), aby współpracować z gośćmi w witrynie SharePoint.
- [Współpracuj jako zespół](collaborate-as-team.md) , aby współpracować z gośćmi w zespole.
- [Współpracuj z uczestnikami zewnętrznymi w kanale](/microsoft-365/solutions/collaborate-teams-direct-connect) , aby współpracować z osobami spoza organizacji w kanale udostępnionym.

W zależności od poufności udostępnianych informacji można dodać zabezpieczenia, aby zapobiec nadmiernemu udostępnianiu. Te zasoby pomogą Ci skonfigurować ochronę potrzebną organizacji:

- [Najlepsze rozwiązania dotyczące udostępniania plików i folderów nieuwierzytelnionym użytkownikom](best-practices-anonymous-sharing.md)
- [Ograniczanie przypadkowego narażenia na pliki podczas udostępniania osobom spoza organizacji](share-limit-accidental-exposure.md)
- [Tworzenie bezpiecznego środowiska udostępniania gościa](create-secure-guest-sharing-environment.md)

Jeśli masz duży projekt w organizacji partnerskiej, możesz użyć [kanałów udostępnionych](/microsoft-365/solutions/collaborate-teams-direct-connect) lub [usługi Azure Entitlement Management](b2b-extranet.md) , aby zarządzać osobami spoza organizacji, z którymi musisz współpracować.

## <a name="training-for-administrators"></a>Szkolenie dla administratorów

Te moduły szkoleniowe z usługi Microsoft Learn mogą pomóc w poznaniu funkcji współpracy, ładu i tożsamości w Teams i SharePoint.

### <a name="teams"></a>Teams

|Szkolenia:|Zarządzanie współpracą zespołu za pomocą Microsoft Teams|
|---|---|
|![Teams ikona trenowania współpracy.](../media/manage-team-collaboration-with-microsoft-teams.svg)|Zarządzanie współpracą zespołu za pomocą Microsoft Teams wprowadza funkcje i możliwości Microsoft Teams, centralnego centrum współpracy zespołowej w Microsoft 365. Dowiesz się, jak za pomocą Teams ułatwiać pracę zespołową i komunikację w organizacji, zarówno lokalnie, jak i poza nimi, na wielu urządzeniach — od komputerów stacjonarnych po tablety i telefony — przy jednoczesnym wykorzystaniu wszystkich zaawansowanych funkcji aplikacji Office 365. Zrozumiasz, w jaki sposób Teams zapewnia kompleksowe i elastyczne środowisko do współpracy między aplikacjami i urządzeniami. Ta ścieżka szkoleniowa może pomóc w przygotowaniu się do certyfikacji Microsoft 365 Certified: Teams Administrator Associate.<p>2 godz. 17 min — ścieżka Edukacja — 5 modułów|

> [!div class="nextstepaction"]
> [Rozpocznij >](/learn/modules/m365-teams-collab-prepare-deployment/introduction/)

### <a name="sharepoint"></a>SharePoint

|Szkolenia:|Współpraca z SharePoint w Microsoft 365|
|---|---|
|![SharePoint ikona trenowania.](../media/collaborate-with-sharepoint-in-microsoft-365.svg)|Zarządzanie zawartością udostępnioną firmie Microsoft SharePoint wprowadza funkcje i możliwości SharePoint oraz sposób jej działania z Microsoft 365. Poznasz różne typy witryn SharePoint, w tym lokacje centrum, a także ochronę informacji, raportowanie i monitorowanie. Dowiesz się również, jak za pomocą udostępniania plików i folderów SharePoint zoptymalizować współpracę, jak udostępniać pliki na zewnątrz oraz jak zarządzać witrynami SharePoint w centrum administracyjnym SharePoint. Ta ścieżka szkoleniowa może pomóc w przygotowaniu się do certyfikatu Microsoft 365 Certified: Teamwork Administrator Associate.<p>1 godz. 14 min — ścieżka Edukacja — 4 moduły|

> [!div class="nextstepaction"]
> [Rozpocznij >](/learn/modules/m365-teams-sharepoint-plan-sharepoint/introduction/)

### <a name="information-protection"></a>Ochrona informacji

|Szkolenia:|Ochrona informacji o przedsiębiorstwie za pomocą Microsoft 365|
|---|---|
|![Teams ikona trenowania ochrony informacji.](../media/protect-enterprise-information-microsoft-365.svg)|Ochrona i zabezpieczanie informacji organizacji jest trudniejsze niż kiedykolwiek wcześniej. W ścieżce szkoleniowej Ochrona informacji o przedsiębiorstwie za pomocą Microsoft 365 omówiono sposób ochrony poufnych informacji przed przypadkowym nadmiernym udostępnianiem lub niewłaściwym użyciem, sposobu odnajdywania i klasyfikowania danych, sposobu ich ochrony za pomocą etykiet poufności oraz sposobu monitorowania i analizowania poufnych informacji w celu ochrony przed ich utratą. Ta ścieżka szkoleniowa może pomóc w przygotowaniu się do certyfikacji Microsoft 365 Certified: Security Administrator Associate i Microsoft 365 Certified: Enterprise Administration Expert.<p>1 godz. ścieżka Edukacja — 5 modułów|

> [!div class="nextstepaction"]
> [Rozpocznij >](/learn/modules/m365-security-info-overview/introduction/)

### <a name="identity-and-access"></a>Tożsamość i dostęp

|Szkolenia:|Ochrona tożsamości i dostępu za pomocą Azure Active Directory|
|---|---|
|![Ikona trenowania tożsamości i dostępu.](../media/protect-identity-and-access-with-microsoft-365.svg)|Ścieżka szkoleniowa Dotycząca tożsamości i dostępu obejmuje najnowsze technologie tożsamości i dostępu, narzędzia do wzmacniania uwierzytelniania oraz wskazówki dotyczące ochrony tożsamości w organizacji. Technologie dostępu i tożsamości firmy Microsoft umożliwiają zabezpieczanie tożsamości organizacji, niezależnie od tego, czy jest ona lokalna, czy w chmurze, oraz umożliwianie użytkownikom bezpiecznej pracy z dowolnej lokalizacji. Ta ścieżka szkoleniowa może pomóc w przygotowaniu się do certyfikacji Microsoft 365 Certified: Security Administrator Associate i Microsoft 365 Certified: Enterprise Administration Expert.<p>2 godz. 52 min — ścieżka Edukacja — 6 modułów|

> [!div class="nextstepaction"]
> [Rozpocznij >](/learn/modules/m365-identity-overview/introduction/)

## <a name="training-for-end-users"></a>Szkolenie dla użytkowników końcowych

Te moduły szkoleniowe mogą ułatwić użytkownikom korzystanie z Teams, grup i SharePoint do współpracy w Microsoft 365.

|Teams|SharePoint|
|---|---|
|![Skonfiguruj i dostosuj ikonę trenowania zespołu.](../media/set-up-customize-team-training.png)<br>**[Konfigurowanie i dostosowywanie zespołu](https://support.microsoft.com/office/702a2977-e662-4038-bef5-bdf8ee47b17b)**|![SharePoint ikona trenowania udostępniania i synchronizacji](../media/sharepoint-share-sync-training.png)<br>**[Udostępnianie i synchronizowanie](https://support.microsoft.com/office/98cb2ff2-c27e-42ea-b055-c2d895f8a5de)**|
|![Teams ikonę trenowania przekazywania i znajdowania plików.](../media/smc-teams-upload-find-files-training.png)<br>**[Upload i znajdź pliki](https://support.microsoft.com/office/57b669db-678e-424e-b0a0-15d19215cb12)**||
|![Ikona Współpraca w zespołach i kanałach.](../media/teams-collaborate-channels-training.png)<br>**[Współpraca w zespołach i kanałach](https://support.microsoft.com/office/c3d63c10-77d5-4204-a566-53ddcf723b46)**||

## <a name="illustrations"></a>Ilustracje

Te ilustracje pomogą Ci zrozumieć, w jaki sposób grupy i zespoły współdziałają z innymi usługami w Microsoft 365 oraz jakie funkcje zapewniania ładu i zgodności ułatwiają zarządzanie tymi usługami w organizacji.

### <a name="groups-in-microsoft-365-for-it-architects"></a>Grupy w Microsoft 365 dla architektów IT

Co architekci IT muszą wiedzieć o grupach w Microsoft 365

|**Element**|**Opis**|
|---|---|
|[![Obraz kciuka dla infografiki grup.](../downloads/msft-m365-groups-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-groups.vsdx) <br> Zaktualizowano czerwiec 2019 r.|Na tych ilustracjach przedstawiono różne typy grup, sposób ich tworzenia i zarządzania oraz kilka zaleceń dotyczących ładu.|

### <a name="microsoft-teams-and-related-productivity-services-in-microsoft-365-for-it-architects"></a>Microsoft Teams i powiązanych usług produktywności w Microsoft 365 dla architektów IT

Architektura logiczna usług produktywności w Microsoft 365, wiodąca z Microsoft Teams.

|**Element**|**Opis**|
|---|---|
|[![Obraz kciuka dla Teams plakatu architektury logicznej.](../downloads/msft-teams-logical-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-teams-logical-architecture.vsdx)  <br>Zaktualizowano kwiecień 2019 r.|Firma Microsoft oferuje zestaw usług zwiększających produktywność, które współpracują ze sobą w celu zapewnienia współpracy z funkcjami zapewniania ładu, zabezpieczeń i zgodności danych. <p>Ta seria ilustracji przedstawia logiczną architekturę usług produktywności dla architektów przedsiębiorstw, prowadzących z Microsoft Teams.|

## <a name="deploy-the-secure-collaboration-solution"></a>Wdrażanie rozwiązania do bezpiecznej współpracy

Gdy wszystko będzie gotowe do wdrożenia tego rozwiązania, wykonaj następujące kroki:

1. Skonfiguruj [trzy różne warstwy ochrony dla Teams](configure-teams-three-tiers-protection.md).
2. Skonfiguruj ustawienia [udostępniania informacji o dowolnej poufności osobom spoza organizacji](collaborate-with-people-outside-your-organization.md).

## <a name="see-also"></a>Zobacz też

[Dokumentacja zabezpieczeń platformy Microsoft 365](../security/index.yml)

[Dokumentacja usługi Microsoft Purview](../compliance/index.yml)

[Witamy w Microsoft Teams](/MicrosoftTeams/Teams-overview)
