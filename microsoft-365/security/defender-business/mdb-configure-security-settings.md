---
title: Wyświetlanie i edytowanie ustawień zabezpieczeń w programie Microsoft Defender dla firm
description: Konfigurowanie zasad zabezpieczeń w programie Microsoft Defender dla firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 4fbc4dc4b5b8628b075d5e6d5a91f760e322a6cf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329813"
---
# <a name="view-and-edit-your-security-policies-and-settings-in-microsoft-defender-for-business"></a>Wyświetlanie i edytowanie zasad zabezpieczeń oraz ustawień w programie Microsoft Defender dla firm

> [!IMPORTANT]
> Program Microsoft Defender dla firm jest wprowadzany dla Microsoft 365 Business Premium klientów od 1 marca 2022 r. Autonomiczna subskrypcja usługi Defender dla firm jest w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, [](https://aka.ms/mdb-preview) którzy zarejestrują się tutaj, aby poprosić o to. Wersja Preview zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać funkcje.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

## <a name="overview"></a>Omówienie

Po dojecheniu urządzeń organizacji do usługi Microsoft Defender dla Firm następnym krokiem jest wyświetlenie i w razie potrzeby edytowanie zasad zabezpieczeń oraz ustawień. Zasady zabezpieczeń to między innymi:

- **[Zasady ochrony następnej generacji](#view-or-edit-your-next-generation-protection-policies)**, które określają ochronę przed oprogramowaniem antywirusowym i złośliwym oprogramowaniem dla urządzeń organizacji
- **[Ochrona zapory i reguły](#view-or-edit-your-firewall-policies-and-custom-rules)**, które określają, jaki ruch sieciowy może przepływać do lub z urządzeń organizacji
- **[Filtrowanie zawartości sieci](#set-up-web-content-filtering)** Web, które uniemożliwia użytkownikom odwiedzanie określonych witryn internetowych (adresów URL) w zależności od kategorii, takich jak zawartość dla dorosłych lub odpowiedzialność odpowiedzialność za nie.

W programie Defender dla firm zasady zabezpieczeń są stosowane do urządzeń za [pośrednictwem grup urządzeń](mdb-create-edit-device-groups.md#what-is-a-device-group). 

Oprócz zasad zabezpieczeń można wyświetlać i edytować [ustawienia, na](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal) przykład strefę czasową używaną w portalu programu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) oraz określać, czy funkcje wersji Preview mają być udostępniane.

Ten artykuł jest przewodnikiem po zarządzaniu zasadami i ustawieniami zabezpieczeń.

## <a name="what-to-do"></a>Co należy zrobić

1. [Wybierz miejsce zarządzania zasadami zabezpieczeń i urządzeniami](#choose-where-to-manage-security-policies-and-devices).

2. [Wyświetlanie lub edytowanie zasad ochrony następnej generacji](#view-or-edit-your-next-generation-protection-policies).

3. [Wyświetlanie i edytowanie zasad zapory i reguł niestandardowych](#view-or-edit-your-firewall-policies-and-custom-rules).

4. [Konfigurowanie filtrowania zawartości sieci Web](#set-up-web-content-filtering).

5. [Wyświetlaj i edytuj inne ustawienia w portalu Microsoft 365 Defender sieci.](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal) 

6. [Przejdź do następnych kroków](#next-steps).

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

## <a name="choose-where-to-manage-security-policies-and-devices"></a>Wybieranie miejsca zarządzania zasadami zabezpieczeń i urządzeniami

Program Defender dla firm oferuje [uproszczony proces konfiguracji,](mdb-simplified-configuration.md) który ułatwia usprawnianie procesu konfiguracji i konfiguracji. Jeśli wybierzesz uproszczony proces konfiguracji, możesz wyświetlać zasady zabezpieczeń i zarządzać nimi w portalu Microsoft 365 Defender sieci ([https://security.microsoft.com/](https://security.microsoft.com/)). Nie ograniczamy się jednak do tej opcji. Jeśli korzystasz z programu Microsoft Endpoint Manager (w tym Microsoft Intune), możesz nadal korzystać z Endpoint Manager.

W poniższej tabeli przedstawiono sposób zarządzania zasadami i urządzeniami zabezpieczeń. <br/><br/>

| Opcja | Opis |
|:---|:---|
| **Korzystanie z Microsoft 365 Defender (***zalecane*) | Portal Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)) może być twoją jedną usługą do zarządzania urządzeniami, zasadami zabezpieczeń i ustawieniami zabezpieczeń organizacji. Możesz uzyskać dostęp do zasad i ustawień zabezpieczeń, korzystać z [](mdb-view-tvm-dashboard.md)pulpitu nawigacyjnego zarządzania & zagrożeniami i lukami w zabezpieczeniach oraz wyświetlać wszystkie zdarzenia i zarządzać nimi w jednym miejscu.[](mdb-view-manage-incidents.md)  |
| **Używanie Microsoft Endpoint Manager** | Jeśli Twoja organizacja używa już programu Endpoint Manager (który obejmuje program Microsoft Intune) do zarządzania zasadami zabezpieczeń, możesz nadal używać programu Endpoint Manager do zarządzania urządzeniami i zasadami zabezpieczeń. Aby dowiedzieć się więcej, zobacz [Zarządzanie zabezpieczeniami urządzeń za pomocą zasad zabezpieczeń punktów końcowych w programie Microsoft Intune](/mem/intune/protect/endpoint-security-policy). <br/><br/>Jeśli zdecydujesz się na przełączenie do uproszczonego procesu konfiguracji w uchcie programu [Defender](mdb-simplified-configuration.md) dla firm i zamiast tego będziesz korzystać z portalu programu Microsoft 365 Defender, zostanie wyświetlony monit o usunięcie wszystkich istniejących zasad zabezpieczeń w programie Endpoint Manager w celu uniknięcia konfliktów [zasad w późniejszym](mdb-troubleshooting.yml) czasie. |

> [!NOTE]
> Jeśli zarządzasz naszymi zasadami zabezpieczeń w portalu Microsoft 365 Defender, możesz je wyświetlać w  programie Endpoint Manager, wyszczególnionych jako zasady oprogramowania antywirusowego lub zapory. Podczas wyświetlania zasad zapory w Endpoint Manager na liście są wymienione dwie zasady: jedna zasady ochrony zapory, a druga dla reguł niestandardowych.

## <a name="view-or-edit-your-next-generation-protection-policies"></a>Wyświetlanie lub edytowanie zasad ochrony następnej generacji

W zależności od tego, czy do zarządzania zasadami ochrony następnej generacji Microsoft 365 Defender Microsoft Endpoint Manager, czy do zarządzania zasadami ochrony następnej generacji, użyj jednej z procedur z poniższej tabeli: <br/><br/>

| Portal | Procedura |
|:---|:---|
| Microsoft 365 Defender portalu ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się. <br/><br/>2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są uporządkowane według systemu operacyjnego i typu zasad.<br/><br/>3. Wybierz kartę systemu operacyjnego (na przykład Windows **klientów**).<br/><br/>4. **Rozwiń ochronę następnej generacji** , aby wyświetlić listę zasad.<br/><br/>5. Wybierz zasady, aby wyświetlić więcej szczegółów dotyczących zasad. Aby wprowadzić zmiany lub dowiedzieć się więcej o ustawieniach zasad, zobacz następujące artykuły: <br/>- [Wyświetlanie lub edytowanie zasad urządzenia](mdb-view-edit-policies.md)<br/>- [Opis ustawień konfiguracji następnej generacji](mdb-next-gen-configuration-settings.md)  |
| Microsoft Endpoint Manager administracyjne ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Przejdź do i [https://endpoint.microsoft.com](https://endpoint.microsoft.com) zaloguj się. Jesteś teraz w centrum Microsoft Endpoint Manager administracyjnego.<br/><br/>2. Wybierz **zabezpieczenia punktu końcowego**.<br/><br/>3. Wybierz pozycję **Oprogramowanie antywirusowe** , aby wyświetlić zasady w tej kategorii. <br/><br/>Aby uzyskać pomoc na temat zarządzania ustawieniami zabezpieczeń w aplikacji Microsoft Endpoint Manager, zacznij od [tematu Zarządzanie zabezpieczeniami punktów końcowych w Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="view-or-edit-your-firewall-policies-and-custom-rules"></a>Wyświetlanie i edytowanie zasad zapory i reguł niestandardowych

W zależności od tego, czy do zarządzania ochroną zapory używasz portalu Microsoft 365 Defender czy serwera Microsoft Endpoint Manager, użyj jednej z procedur z poniższej tabeli: <br/><br/>

| Portal | Procedura |
|:---|:---|
| Microsoft 365 Defender portalu ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się. <br/><br/>2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są uporządkowane według systemu operacyjnego i typu zasad.<br/><br/>3. Wybierz kartę systemu operacyjnego (na przykład Windows **klientów**).<br/><br/>4. **Rozwiń zaporę** , aby wyświetlić listę zasad.<br/><br/>5. Wybierz zasady, aby wyświetlić więcej szczegółów dotyczących zasad. Aby wprowadzić zmiany lub dowiedzieć się więcej o ustawieniach zasad, zobacz następujące artykuły: <br/>- [Wyświetlanie lub edytowanie zasad urządzenia](mdb-view-edit-policies.md)<br/>- [Ustawienia zapory](mdb-firewall.md)<br/>- [Zarządzanie regułami niestandardowymi dla zasad zapory](mdb-custom-rules-firewall.md)  |
| Microsoft Endpoint Manager administracyjne ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Przejdź do i [https://endpoint.microsoft.com](https://endpoint.microsoft.com) zaloguj się. Jesteś teraz w centrum Microsoft Endpoint Manager administracyjnego.<br/><br/>2. Wybierz **zabezpieczenia punktu końcowego**.<br/><br/>3. Wybierz pozycję **Zapora** , aby wyświetlić zasady w tej kategorii. Reguły niestandardowe zdefiniowane dla ochrony zapory są wymienione jako oddzielne zasady.<br/><br/>Aby uzyskać pomoc na temat zarządzania ustawieniami zabezpieczeń w aplikacji Microsoft Endpoint Manager, zacznij od [tematu Zarządzanie zabezpieczeniami punktów końcowych w Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="set-up-web-content-filtering"></a>Konfigurowanie filtrowania zawartości sieci Web

Filtrowanie zawartości sieci Web umożliwia Twojemu zespołowi zabezpieczeń śledzenie i regulowanie dostępu do witryn internetowych na podstawie ich kategorii zawartości, takich jak:

- Treści dla dorosłych: Witryny związane z natłokami, nagością, pornografią, erotycyjnymi materiałami lub przemocą
- Wysoka przepustowość: Pobieranie witryn, witryn udostępniania obrazów lub hostów równorzędnych
- Odpowiedzialność prawnie: Witryny, które zawierają obrazy dotyczące nadużyć wśród dzieci, promują działania niezgodne z prawem, promują oszustów lub szkoły oszukiwanie oraz promują szkodliwe działania
- Rozrywka: witryny, które zapewniają internetowe pokoje rozmów, gry online, pocztę e-mail opartą na sieci Web lub sieci społecznościowe
- Niekategoryzowane: witryny, które nie mają zawartości lub są nowo zarejestrowane

Nie wszystkie witryny internetowe w tych kategoriach są złośliwe, ale mogą być problematyczne dla Twojej organizacji ze względu na przepisy dotyczące zgodności, użycie przepustowości lub inne problemy. Ponadto można tworzyć zasady tylko do inspekcji, aby lepiej zrozumieć, czy zespół zabezpieczeń ma blokować kategorie witryn internetowych.

Filtrowanie zawartości sieci Web jest dostępne w głównych przeglądarkach internetowych, a bloki są wykonywane przez filtr Windows Defender SmartScreen (Microsoft Edge) i network Protection (Chrome, Firefox, Firefox, Firefox i Opera). Aby uzyskać więcej informacji, [zobacz Wymagania wstępne filtrowania zawartości sieci Web](../defender-endpoint/web-content-filtering.md#prerequisites).

### <a name="to-set-up-web-content-filtering"></a>Aby skonfigurować filtrowanie zawartości sieci Web

1. W portalu Microsoft 365 Defender sieci Web ([https://security.microsoft.com](https://security.microsoft.com)) wybierz pozycję **Ustawienia** >  **Filtrowanie zawartości sieci** >  Web **+ Dodaj zasady**.

2. Określ nazwę i opis zasad.

3. Wybierz kategorie, które chcesz zablokować. Za pomocą ikony rozwijania możesz w pełni rozwinąć każdą kategorię nadrzędną i wybrać określone kategorie zawartości sieci Web.

   Aby skonfigurować zasady tylko do inspekcji, które nie blokują żadnych witryn sieci Web, nie wybieraj żadnych kategorii.

   Nie zaznaczaj **opcji Bez kategorii**.

4. Określ zakres zasad, wybierając grupy urządzeń do zastosowania zasad. Dostęp do witryn internetowych w wybranych kategoriach nie będzie miał tylko urządzeń w wybranych grupach urządzeń.

5. Przejrzyj podsumowanie i zapisz zasady. Odświeżanie zasad może potrwać do 2 godzin, aby zastosować je do wybranych urządzeń.

> [!TIP]
> Aby dowiedzieć się więcej o filtrowaniu zawartości sieci Web, zobacz [Filtrowanie zawartości sieci Web](../defender-endpoint/web-content-filtering.md).

## <a name="view-and-edit-other-settings-in-the-microsoft-365-defender-portal"></a>Wyświetlanie i edytowanie innych ustawień w Microsoft 365 Defender sieci Microsoft 365 Defender sieci

Oprócz zasad zabezpieczeń, które są stosowane do urządzeń, istnieją inne ustawienia, które można wyświetlać i edytować w programie Defender dla firm. Możesz na przykład określić strefę czasową, która ma być używania, i możesz korzystać z urządzeń wyniesinych (lub wyłączonych). 

> [!NOTE]
> W dzierżawie może być więcej ustawień niż wymieniono w tym artykule. W tym artykule wyróżniliśmy najważniejsze ustawienia, które należy przejrzeć w programie Defender dla firm.

### <a name="settings-to-review-for-defender-for-business"></a>Ustawienia do przejrzenia dla usługi Defender dla firm

W poniższej tabeli opisano ustawienia wyświetlania (i w razie potrzeby edytowania) programu Defender dla firm.

<br/><br/>

| Kategoria | Ustawienie | Opis |
|:---|:---|:---|
| **Centrum zabezpieczeń** | **Strefa czasowa** | Wybierz strefę czasową, która ma być używana dla dat i godzin wyświetlanych w przypadku zdarzeń, wykrytych zagrożeń oraz automatycznego badania & rozwiązywania problemów. Możesz użyć czasu UTC lub lokalnej strefy czasowej (*zalecane*).  |
| **Microsoft 365 Defender** | **Konto** | Wyświetl szczegóły, takie jak miejsce przechowywania danych, identyfikator dzierżawy i identyfikator organizacji (organizacji). |
| **Microsoft 365 Defender**  | **Funkcje wersji Preview**  | Włącz funkcje wersji Preview, aby wypróbować nadchodzące funkcje i nowe funkcje. Możesz zostać jednym z pierwszych użytkowników, który będzie korzystać z wersji zapoznawczej nowych funkcji i przekazać opinię. |
| **Punkty końcowe**  | **Powiadomienia e-mail** | Skonfiguruj lub edytuj reguły powiadomień e-mail. W przypadku wykrycia luk lub utworzenia alertu adresaci wskazany w twoich zasadach powiadomień e-mail otrzymają wiadomość e-mail. [Dowiedz się więcej o powiadomieniach e-mail](mdb-email-notifications.md). |
| **Punkty końcowe**   | **Zarządzanie urządzeniami** >  **Wniesienie** | Urządzenia w programie Defender dla firm można dołączać za pomocą skryptu do pobrania. Aby dowiedzieć się więcej, zobacz [Urządzenia dołączane do programu Microsoft Defender dla firm](mdb-onboard-devices.md).   |  
| **Punkty końcowe**  |  **Zarządzanie urządzeniami** >  **Wyniesienie** | Urządzenia wye-tych (usuń) z usługi Defender dla firm. Po wyzłoceniu urządzenia nie będzie ono już wysyłać danych do usługi Defender dla firm, ale dane otrzymane przed wynodaniem urządzenia zostaną zachowane. Aby dowiedzieć się więcej, [zobacz Wyniesanie urządzenia](mdb-onboard-devices.md#offboarding-a-device).  |

### <a name="access-your-settings-in-the-microsoft-365-defender-portal"></a>Uzyskiwanie dostępu do ustawień w Microsoft 365 Defender sieci Microsoft 365 Defender

1. Przejdź do Microsoft 365 Defender portalu internetowego ([https://security.microsoft.com/](https://security.microsoft.com/)) i zaloguj się.

2. Wybierz **Ustawienia**, a następnie wybierz kategorię (na przykład Centrum **zabezpieczeń, Microsoft 365 Defender** **lub** **Punkty końcowe**).

3. Na liście ustawień wybierz element do wyświetlenia lub edytowania.


## <a name="next-steps"></a>Następne kroki

Przejdź do co najmniej jednego z następujących zadań:

- [Wprowadzenie do korzystania z usługi Microsoft Defender dla firm](mdb-get-started.md)

- [Zarządzanie urządzeniami w programie Microsoft Defender dla firm](mdb-manage-devices.md)

- [Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm](mdb-view-manage-incidents.md)

- [Wyświetlanie i edytowanie zasad w programie Microsoft Defender dla firm](mdb-view-edit-policies.md)
