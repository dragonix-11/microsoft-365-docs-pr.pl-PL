---
title: Przygotowywanie programu Microsoft Defender do wdrożenia punktu końcowego
description: Przygotowanie zatwierdzenia interesariuszy, osi czasu, kwestii środowiska i kolejności przyjęcia w celu wdrożenia programu Microsoft Defender dla punktu końcowego
keywords: wdrażanie, przygotowywanie, uczestników projektu, oś czasu, środowisko, punkt końcowy, serwer, zarządzanie, wdrażanie
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-scenario
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 29f9aabf2c0345e46123ba76869718c15d8d1885
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019344"
---
# <a name="prepare-microsoft-defender-for-endpoint-deployment"></a>Przygotowywanie programu Microsoft Defender do wdrożenia punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Wdrażanie usługi Defender dla punktu końcowego jest procesem trzyfazowym:

|![faza wdrażania — przygotowywanie.](images/phase-diagrams/prepare.png)<br>Etap 1. Przygotowywanie|[![Faza wdrażania — konfiguracja](images/phase-diagrams/setup.png)](production-deployment.md)<br>[Etap 2. Konfigurowanie](production-deployment.md)|[![Faza wdrażania — wdrożenie](images/phase-diagrams/onboard.png)](onboarding.md)<br>[Etap 3. Wniesienie](onboarding.md)|
|---|---|---|
|*Jesteś tutaj!*|||

Jesteś obecnie w fazie przygotowawowej.

Przygotowanie jest kluczem do każdego pomyślnego wdrożenia. W tym artykule otrzymasz  przewodniki na temat punktów, które należy wziąć pod uwagę podczas przygotowywania się do wdrożenia usługi Defender dla punktu końcowego.

## <a name="stakeholders-and-approval"></a>Uczestnicy projektu i zatwierdzenia

W poniższej sekcji powiadom wszystkich uczestników projektu, którzy są zaangażowani w projekt, i którzy muszą je zatwierdzić, przejrzeć lub na bieżąco chcieć.

Dodaj uczestników projektu do poniższej tabeli odpowiednio do potrzeb organizacji.

- SO = Zatwierdź projekt
- R = Przejrzyj ten projekt i wprowadź dane wejściowe
- I = Poinformowanie o tym projekcie

<br>

****

|Name (Nazwa)|Rola|Akcja|
|---|---|---|
|Wprowadź nazwę i adres e-mail|**Dyrektor ds. zabezpieczeń informacji (CISO)** Jest to przedstawiciel kadry kierowniczej, który pełni *rolę sponsora wdrożenia nowej technologii w organizacji.*|SO|
|Wprowadź nazwę i adres e-mail|**Kierownik Centrum ochrony przed cyberzagrożeniami (CDOC) Przedstawiciel zespołu CDOC** odpowiedzialny za określenie, jak ta zmiana jest dopasowana do procesów w zespole operacji *zabezpieczeń klientów.*|SO|
|Wprowadź nazwę i adres e-mail|**Security Architect** Przedstawiciel zespołu zabezpieczeń odpowiedzialny za określenie, jak ta zmiana będzie dostosowana do podstawowej architektury zabezpieczeń *w organizacji.*|R|
|Wprowadź nazwę i adres e-mail|**Workplace Architect** *Przedstawiciel zespołu IT* odpowiedzialny za określenie sposobu dostosowania tej zmiany do architektury podstawowego miejsca pracy w organizacji.|R|
|Wprowadź nazwę i adres e-mail|**Analityk zabezpieczeń** *Przedstawiciel zespołu CDOC*, który może zapewnić wkład w funkcje wykrywania, środowisko użytkownika i ogólną użyteczność tej zmiany z perspektywy operacji zabezpieczeń.|I|
||||

## <a name="environment"></a>Środowisko

Ta sekcja ma na celu zapewnienie, że twoje środowisko jest dobrze zrozumiane przez uczestników projektu, co pomaga w zidentyfikowaniu potencjalnych zależności i/lub zmian wymaganych w technologiach lub procesach.

<br>

****

|Co|Opis|
|---|---|
|Liczba punktów końcowych|Łączna liczba punktów końcowych według systemu operacyjnego.|
|Liczba serwerów|Łączna liczba serwerów według wersji systemu operacyjnego.|
|Aparat zarządzania|Nazwa i wersja aparatu zarządzania (na przykład System Center Configuration Manager wersja Bieżąca gałąź 1803).|
|Rozpowszechnianie CDOC|Struktura dokumentu CDOC wysokiego poziomu (na przykład warstwa 1 z usługą Contoso, poziom 2 i poziom 3 w firmie są dystrybuowane na terenie Europy i Azji).|
|Informacje o zabezpieczeniach i wydarzenia (SIEM)|Technologia SIEM w użyciu.|
|||

## <a name="role-based-access-control"></a>Kontrola dostępu oparta na rolach

Firma Microsoft zaleca korzystanie z pojęcia "jak najmniejszych uprawnień". Program Defender for Endpoint korzysta z wbudowanych ról w Azure Active Directory. Firma Microsoft zaleca [, aby zapoznać się z różnymi](/azure/active-directory/roles/permissions-reference) dostępnymi rolami i wybrać odpowiednią, która rozwiąże potrzeby każdej osoby w danej aplikacji. Niektóre role mogą wymagać tymczasowego zastosowania i usunięcia po ukończeniu wdrażania.

<br>

****

|Personas|Role|Rola usługi Azure AD (jeśli to konieczne)|Przypisz do|
|---|---|---|---|
|Administrator zabezpieczeń||||
|Analityk zabezpieczeń||||
|Administrator punktu końcowego||||
|Administrator infrastruktury||||
|Właściciel/uczestnik projektu firmy||||
|

Firma Microsoft zaleca, aby [Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure) rolami w celu zapewnienia użytkownikom z uprawnieniami do katalogu dodatkowej inspekcji, kontroli i przeglądu dostępu.

Program Defender for Endpoint obsługuje dwa sposoby zarządzania uprawnieniami:

- **Podstawowe zarządzanie uprawnieniami**: Ustaw uprawnienia na pełny dostęp lub tylko do odczytu. Użytkownicy z rolami administratora globalnego lub administratora zabezpieczeń Azure Active Directory mają pełny dostęp. Rola czytnika zabezpieczeń ma dostęp tylko do odczytu i nie udziela dostępu do wyświetlania komputerów/spisu urządzeń.

- **Kontrola dostępu oparta na rolach( RBAC**, Role based access control): Ustaw szczegółowe uprawnienia, definiując role, przypisując grupy użytkowników usługi Azure AD do ról i udzielając grupom użytkowników dostępu do grup urządzeń. Aby uzyskać więcej informacji. zobacz [Zarządzanie dostępem do portalu za pomocą kontroli dostępu opartej na rolach](rbac.md).

Firma Microsoft zaleca stosowanie zasad RBAC w celu zapewnienia, że tylko użytkownicy, którzy mają uzasadnienie biznesowe, mogą uzyskać dostęp do usługi Defender for Endpoint.

Szczegółowe informacje na temat wskazówek dotyczących uprawnień można znaleźć tutaj: [Tworzenie ról i przypisywanie](/microsoft-365/security/defender-endpoint/user-roles#create-roles-and-assign-the-role-to-an-azure-active-directory-group) roli do grupy Azure Active Directory grupy.

W poniższej przykładowej tabeli przedstawiono strukturę Centrum ochrony przed cyberzagrożeniami w środowisku, która pomoże w określeniu struktury RBAC wymaganej dla środowiska.

<br>

****

|Warstwa|Opis|Uprawnienie Wymagane|
|---|---|---|
|Poziom 1|**Lokalny zespół operacyjny ds. zabezpieczeń / zespół IT** <p> Ten zespół zazwyczaj sprawdza i bada alerty zawarte w ich lokalizacji geograficznej i eskalacji do warstwy 2 w przypadkach, gdy wymagane jest aktywne działania naprawcze.||
|Warstwa 2|**Regionalny zespół operacyjny ds. zabezpieczeń** <p> Ten zespół może wyświetlić wszystkie urządzenia dla swojego regionu i wykonywać działania naprawcze.|Wyświetlanie danych|
|Warstwa 3|**Globalny zespół operacyjny ds. zabezpieczeń** <p> Ten zespół składa się z ekspertów ds. zabezpieczeń i ma autoryzowany dostęp do wszystkich działań z portalu.|Wyświetlanie danych <p> Badanie alertów Aktywne działania naprawcze <p> Badanie alertów Aktywne działania naprawcze <p> Zarządzanie ustawieniami systemowym portalu <p> Zarządzanie ustawieniami zabezpieczeń|
||||

## <a name="adoption-order"></a>Porządek przyjęcia

W wielu przypadkach organizacje będą mieć istniejące produkty zabezpieczeń punktów końcowych. Minimalne wymagania każdej organizacji powinny być rozwiązaniem antywirusowym. Jednak w niektórych przypadkach organizacja mogła już wcześniej EDR rozwiązanie.

Ze względów historycznych zastąpienie wszystkich rozwiązań zabezpieczeń, które kiedyś było pracochłonne i trudne do osiągnięcia ze względu na ścisłe zależności między warstwą aplikacji i infrastrukturą. Jednak ponieważ program Defender for Endpoint jest wbudowany w system operacyjny, zastąpienie rozwiązań innych firm jest teraz łatwe do osiągnięcia.

Wybierz składnik usługi Defender for Endpoint do zastosowania i usuń te, które nie mają zastosowania. W poniższej tabeli przedstawiono kolejność, w jaką firma Microsoft zaleca, aby określić, w jaki sposób należy włączyć pakiet zabezpieczeń punktu końcowego.

<br>

****

|Składnik|Opis|Pozycja zamówienia przyjęcia|
|---|---|---|
|Wykrywanie punktu & odpowiedzi (EDR)|Program Defender for Endpoint wykrywanie i reagowanie w punktach końcowych funkcje zaawansowane wykrywania ataków, które są blisko czasu rzeczywistego i które oferują akcję. Analitycy zabezpieczeń mogą efektywnie określać priorytety alertów, zyskać wgląd w pełny zakres naruszenia zabezpieczeń oraz podjąć działania w celu reagowania na zagrożenia. <p> [Dowiedz się więcej.](/windows/security/threat-protection/windows-defender-atp/overview-endpoint-detection-response)|1|
|Zarządzanie & zagrożeniami i zagrożeniami|Zarządzanie & zagrożeniami i lukami w zabezpieczeniach to składnik programu Microsoft Defender for Endpoint, który zapewnia unikatowych wartości zarówno administratorom zabezpieczeń, jak i zespołom operacji zabezpieczeń, w tym: <ul><li>Analizy w czasie rzeczywistym wykrywanie i reagowanie w punktach końcowych (EDR) skorelowane z lukami w punktach końcowych</li><li>Nieocenieniowy kontekst luki w zabezpieczeniach urządzenia podczas badania zdarzeń</li><li>Wbudowane procesy rozwiązywania problemów za pośrednictwem usług Microsoft Intune i Microsoft System Center Configuration Manager</li></ul> <p> [Dowiedz się więcej](https://techcommunity.microsoft.com/t5/Windows-Defender-ATP/Introducing-a-risk-based-approach-to-threat-and-vulnerability/ba-p/377845).|2|
|Ochrona następnej generacji (NGP)|Program antywirusowy Microsoft Defender to wbudowane rozwiązanie ochrony przed złośliwym oprogramowaniem, które zapewnia ochronę komputerów stacjonarnych, przenośnych i serwerów następnej generacji. Program antywirusowy Microsoft Defender zawiera: <ul><li>Zapewnianie ochrony w chmurze w celu natychmiastowego wykrywania i blokowania nowych i pojawiających się zagrożeń. Oprócz uczenia maszynowego i inteligentnego Graph ochrona w chmurze jest częścią technologii nowej generacji, które są zaawansowane dla Program antywirusowy Microsoft Defender.</li><li>Skanowanie zawsze przy użyciu zaawansowanego monitorowania zachowania plików i procesów oraz innych funkcji heuristics (nazywanych też "ochroną w czasie rzeczywistym").</li><li>Dedykowane aktualizacje ochrony oparte na uczeniem maszynowym, analizie danych big-data przez ludzi oraz szczegółowe badania odporność na zagrożenia.</li></ul> <p> [Dowiedz się więcej](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10).|3|
|Zmniejszenie powierzchni ataków (ASR)|Funkcje ograniczania powierzchni ataków w programie Microsoft Defender dla punktu końcowego pomagają chronić urządzenia i aplikacje w organizacji przed nowymi i pojawiającymi się zagrożeniami. <br> [Dowiedz się więcej.](/windows/security/threat-protection/windows-defender-atp/overview-attack-surface-reduction)|4|
|Działania naprawcze & autowywiadu (AIR)|Program Microsoft Defender for Endpoint używa zautomatyzowanych analiz w celu znacznego zmniejszenia liczby alertów, które trzeba zbadać indywidualnie. Funkcja automatycznego badania korzysta z różnych algorytmów inspekcji i procesów używanych przez analityków (takich jak podręczniki) do badania alertów i podejmowania natychmiastowych działań naprawczych w celu rozwiązania naruszeń. Znacząco zmniejsza to liczbę alertów, umożliwiając ekspertom z operacji zabezpieczeń skoncentrowanie się na bardziej zaawansowanych zagrożeniach i innych inicjatywach o wysokich wartościach. <p> [Dowiedz się więcej.](/windows/security/threat-protection/windows-defender-atp/automated-investigations-windows-defender-advanced-threat-protection)|Nie dotyczy|
|Microsoft Threat Experts (MTE)|Microsoft Threat Experts to zarządzana służba chłoń, która zapewnia centrach operacji zabezpieczeń (SOC, Security Operation Center) z specjalistycznej kontroli i analizy, aby zapewnić, że nie przegapisz krytycznych zagrożeń w ich unikatowych środowiskach. <p> [Dowiedz się więcej.](/windows/security/threat-protection/windows-defender-atp/microsoft-threat-experts)|Nie dotyczy|

## <a name="next-step"></a>Następny krok

![Etap 2. Konfigurowanie.](images/setup.png) <br> [Etap 2. Konfigurowanie](production-deployment.md)

Konfigurowanie programu Microsoft Defender do wdrażania punktu końcowego.
