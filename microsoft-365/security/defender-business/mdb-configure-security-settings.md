---
title: Wyświetlanie i edytowanie ustawień zabezpieczeń w Microsoft Defender dla Firm
description: Wyświetlanie i edytowanie zasad i ustawień zabezpieczeń w usłudze Defender dla firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 9d401c5be4fc0454ce1d895fe5ea49267e5c5f70
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2022
ms.locfileid: "65469178"
---
# <a name="view-and-edit-your-security-policies-and-settings-in-microsoft-defender-for-business"></a>Wyświetlanie i edytowanie zasad zabezpieczeń i ustawień w Microsoft Defender dla Firm

Po dołączeniu urządzeń firmy do Microsoft Defender dla Firm następnym krokiem jest zapoznanie się z zasadami zabezpieczeń. W razie potrzeby można edytować zasady i ustawienia zabezpieczeń. 

> [!TIP]
> Usługa Defender dla firm zawiera wstępnie skonfigurowane zasady zabezpieczeń, które używają zalecanych ustawień. Można jednak edytować ustawienia zgodnie z potrzebami biznesowymi.

Zasady zabezpieczeń do przeglądania i konfigurowania obejmują:

- **[Zasady ochrony nowej generacji](#view-or-edit-your-next-generation-protection-policies)**, które określają ochronę antywirusową i ochronę przed złośliwym kodem dla urządzeń firmy
- **[Ochrona zapory i reguły](#view-or-edit-your-firewall-policies-and-custom-rules)**, które określają, jaki ruch sieciowy może przepływać do lub z urządzeń firmy
- **[Filtrowanie zawartości internetowej](#set-up-web-content-filtering)**, które uniemożliwia użytkownikom odwiedzanie niektórych witryn internetowych (adresów URL) na podstawie kategorii, takich jak treści dla dorosłych lub odpowiedzialność prawna.
- **[Zaawansowane funkcje](#review-settings-for-advanced-features)**, takie jak zautomatyzowane badanie i reagowanie oraz wykrywanie i reagowanie w punktach końcowych (EDR) w trybie bloku.

W usłudze Defender dla firm zasady zabezpieczeń są stosowane do urządzeń za pośrednictwem [grup urządzeń](mdb-create-edit-device-groups.md#what-is-a-device-group). 

Oprócz zasad zabezpieczeń można [wyświetlać i edytować ustawienia](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal), takie jak strefa czasowa do użycia w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) oraz to, czy mają być odbierane funkcje w wersji zapoznawczej w miarę ich udostępniania.

Skorzystaj z tego artykułu jako przewodnika po zarządzaniu zasadami i ustawieniami zabezpieczeń.

## <a name="what-to-do"></a>Co robić

1. [Wybierz miejsce zarządzania zasadami zabezpieczeń i urządzeniami](#choose-where-to-manage-security-policies-and-devices).
2. [Przejrzyj zasady ochrony nowej generacji](#view-or-edit-your-next-generation-protection-policies).
3. [Przejrzyj zasady zapory i reguły niestandardowe](#view-or-edit-your-firewall-policies-and-custom-rules).
4. [Skonfiguruj filtrowanie zawartości internetowej](#set-up-web-content-filtering).
5. [Przejrzyj ustawienia funkcji zaawansowanych](#review-settings-for-advanced-features).
6. [Wyświetl inne ustawienia w portalu Microsoft 365 Defender](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal). 
7. [Przejdź do kolejnych kroków](#next-steps).

>
> **Masz minutę?**
> Weź udział w <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótkiej ankiecie dotyczącej bezpieczeństwa</a>. Chcielibyśmy usłyszeć od Ciebie!
>

## <a name="choose-where-to-manage-security-policies-and-devices"></a>Wybieranie miejsca zarządzania zasadami zabezpieczeń i urządzeniami

Usługa Defender dla firm oferuje [uproszczony proces konfiguracji](mdb-simplified-configuration.md) , który pomaga usprawnić proces konfiguracji i konfiguracji. Jeśli wybierzesz uproszczony proces konfiguracji, możesz wyświetlić zasady zabezpieczeń i zarządzać nimi w portalu Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)). Nie ograniczasz się jednak do tej opcji. Jeśli używasz Microsoft Intune, możesz nadal korzystać z centrum administracyjnego Microsoft Endpoint Manager.

Poniższa tabela może pomóc w wyborze miejsca zarządzania zasadami zabezpieczeń i urządzeniami. <br/><br/>

| Opcja | Opis |
|:---|:---|
| **Korzystanie z portalu Microsoft 365 Defender** (*zalecane*) | Portal Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)) może być punktem obsługi do zarządzania urządzeniami firmy, zasadami zabezpieczeń i ustawieniami zabezpieczeń. Możesz uzyskiwać dostęp do zasad i ustawień zabezpieczeń, korzystać z [pulpitu nawigacyjnego zarządzania lukami w zabezpieczeniach & zagrożeniami](mdb-view-tvm-dashboard.md) oraz [wyświetlać zdarzenia i zarządzać nimi](mdb-view-manage-incidents.md) w jednym miejscu. <br/><br/>Jeśli używasz Intune, urządzenia dołączone do usługi Defender dla Firm i zasady zabezpieczeń są widoczne w centrum administracyjnym Endpoint Manager. Aby dowiedzieć się więcej, zobacz następujące artykuły:<br/>- [Ustawienia domyślne usługi Defender dla firm i Microsoft Intune](mdb-next-gen-configuration-settings.md#defender-for-business-default-settings-and-microsoft-intune) <br/>- [Zapora w Microsoft Defender dla Firm](mdb-firewall.md)   |
| **Korzystanie z centrum administracyjnego Microsoft Endpoint Manager** | Jeśli twoja firma już używa Intune do zarządzania zasadami zabezpieczeń, możesz nadal używać centrum administracyjnego Endpoint Manager do zarządzania urządzeniami i zasadami zabezpieczeń. Aby dowiedzieć się więcej, zobacz [Zarządzanie zabezpieczeniami urządzeń przy użyciu zasad zabezpieczeń punktu końcowego w Microsoft Intune](/mem/intune/protect/endpoint-security-policy). <br/><br/>Jeśli zdecydujesz się na przejście do [uproszczonego procesu konfiguracji w usłudze Defender dla firm](mdb-simplified-configuration.md), zostanie wyświetlony monit o usunięcie wszelkich istniejących zasad zabezpieczeń w Intune, aby uniknąć [konfliktów zasad](mdb-troubleshooting.yml) później. |

> [!IMPORTANT]
> Jeśli zarządzasz zasadami zabezpieczeń w portalu Microsoft 365 Defender, możesz *wyświetlić* te zasady w centrum administracyjnym Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), wymienionym jako **zasady ochrony antywirusowej** lub **zapory**. Podczas wyświetlania zasad zapory w centrum administracyjnym Endpoint Manager zostaną wyświetlone dwie zasady: jedna zasada ochrony zapory, a druga dla reguł niestandardowych.

## <a name="view-or-edit-your-next-generation-protection-policies"></a>Wyświetlanie lub edytowanie zasad ochrony nowej generacji

W zależności od tego, czy używasz portalu Microsoft 365 Defender, czy centrum administracyjnego Microsoft Endpoint Manager do zarządzania zasadami ochrony nowej generacji, użyj jednej z procedur w poniższej tabeli:

| Portal | Procedura |
|:---|:---|
| portal Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się. <br/><br/>2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są zorganizowane według systemu operacyjnego i typu zasad.<br/><br/>3. Wybierz kartę systemu operacyjnego (na przykład **Windows klientów**).<br/><br/>4. Rozwiń **kolejną generację ochrony** , aby wyświetlić listę zasad.<br/><br/>5. Wybierz zasady, aby wyświetlić więcej szczegółów dotyczących zasad. Aby wprowadzić zmiany lub dowiedzieć się więcej o ustawieniach zasad, zobacz następujące artykuły: <br/>- [Wyświetlanie lub edytowanie zasad urządzeń](mdb-view-edit-policies.md)<br/>- [Omówienie ustawień konfiguracji następnej generacji](mdb-next-gen-configuration-settings.md)  |
| centrum administracyjne Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Przejdź do [https://endpoint.microsoft.com](https://endpoint.microsoft.com) obszaru i zaloguj się. Jesteś teraz w centrum administracyjnym Endpoint Manager.<br/><br/>2. Wybierz pozycję **Zabezpieczenia punktu końcowego**.<br/><br/>3. Wybierz pozycję **Program antywirusowy** , aby wyświetlić zasady w tej kategorii. <br/><br/>Aby uzyskać pomoc w zarządzaniu ustawieniami zabezpieczeń w Intune, zacznij od [pozycji Zarządzanie zabezpieczeniami punktów końcowych w Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="view-or-edit-your-firewall-policies-and-custom-rules"></a>Wyświetlanie lub edytowanie zasad zapory i reguł niestandardowych

W zależności od tego, czy używasz portalu Microsoft 365 Defender, czy centrum administracyjnego Microsoft Endpoint Manager do zarządzania ochroną zapory, użyj jednej z procedur w poniższej tabeli:

| Portal | Procedura |
|:---|:---|
| portal Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się. <br/><br/>2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są zorganizowane według systemu operacyjnego i typu zasad.<br/><br/>3. Wybierz kartę systemu operacyjnego (na przykład **Windows klientów**).<br/><br/>4. Rozwiń węzeł **Zapora** , aby wyświetlić listę zasad.<br/><br/>5. Wybierz zasady, aby wyświetlić więcej szczegółów dotyczących zasad. Aby wprowadzić zmiany lub dowiedzieć się więcej o ustawieniach zasad, zobacz następujące artykuły: <br/>- [Wyświetlanie lub edytowanie zasad urządzeń](mdb-view-edit-policies.md)<br/>- [Ustawienia zapory](mdb-firewall.md)<br/>- [Zarządzanie niestandardowymi regułami zasad zapory](mdb-custom-rules-firewall.md)  |
| centrum administracyjne Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Przejdź do [https://endpoint.microsoft.com](https://endpoint.microsoft.com) obszaru i zaloguj się. Jesteś teraz w centrum administracyjnym Endpoint Manager.<br/><br/>2. Wybierz pozycję **Zabezpieczenia punktu końcowego**.<br/><br/>3. Wybierz pozycję **Zapora** , aby wyświetlić zasady w tej kategorii. Reguły niestandardowe zdefiniowane na potrzeby ochrony zapory są wyświetlane jako oddzielne zasady.<br/><br/>Aby uzyskać pomoc w zarządzaniu ustawieniami zabezpieczeń w Intune, zacznij od [pozycji Zarządzanie zabezpieczeniami punktów końcowych w Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="set-up-web-content-filtering"></a>Konfigurowanie filtrowania zawartości internetowej

Filtrowanie zawartości internetowej umożliwia zespołowi ds. zabezpieczeń śledzenie i regulowanie dostępu do witryn internetowych na podstawie kategorii zawartości, takich jak:

- Treści dla dorosłych: Witryny związane z kultami, hazardem, nagością, pornografią, materiałami o charakterze jednoznacznie seksualnym lub przemocą
- Wysoka przepustowość: pobieranie witryn, witryn udostępniania obrazów lub hostów równorzędnych
- Odpowiedzialność prawna: Witryny, które obejmują obrazy wykorzystywania dzieci, promują nielegalne działania, sprzyjają plagiatowi lub oszustwom szkolnym lub promują szkodliwe działania
- Wypoczynek: witryny, które zapewniają czaty internetowe, gry online, internetową pocztę e-mail lub sieci społecznościowe
- Bez kategorii: witryny, które nie mają zawartości lub które są nowo zarejestrowane

Nie wszystkie witryny internetowe w tych kategoriach są złośliwe, ale mogą być problematyczne dla Twojej firmy z powodu przepisów dotyczących zgodności, użycia przepustowości lub innych problemów. Ponadto można utworzyć zasady tylko do inspekcji, aby lepiej zrozumieć, czy zespół ds. zabezpieczeń powinien blokować dowolne kategorie witryn internetowych.

Filtrowanie zawartości internetowej jest dostępne w głównych przeglądarkach internetowych z blokami wykonywanymi przez Windows Defender SmartScreen (Microsoft Edge) i Network Protection (Chrome, Firefox, Brave i Opera). Aby uzyskać więcej informacji, zobacz [Wymagania wstępne dotyczące filtrowania zawartości internetowej](../defender-endpoint/web-content-filtering.md#prerequisites).

### <a name="to-set-up-web-content-filtering"></a>Aby skonfigurować filtrowanie zawartości internetowej

1. W portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) wybierz pozycję **Ustawienia** >  Filtrowanie  > **zawartości sieci Web****+ Dodaj zasady**.

2. Określ nazwę i opis zasad.

3. Wybierz kategorie do zablokowania. Użyj ikony rozwijania, aby w pełni rozwinąć każdą kategorię nadrzędną i wybrać określone kategorie zawartości internetowej. Aby skonfigurować zasady tylko do inspekcji, które nie blokują żadnych witryn internetowych, nie wybieraj żadnych kategorii.

   Nie wybieraj pozycji **Bez kategorii**.

4. Określ zakres zasad, wybierając grupy urządzeń do zastosowania zasad. Tylko urządzenia w wybranych grupach urządzeń nie będą mogły uzyskiwać dostępu do witryn internetowych w wybranych kategoriach.

5. Przejrzyj podsumowanie i zapisz zasady. Odświeżanie zasad może potrwać do 2 godzin w przypadku wybranych urządzeń.

> [!TIP]
> Aby dowiedzieć się więcej na temat filtrowania zawartości internetowej, zobacz [Filtrowanie zawartości sieci Web](../defender-endpoint/web-content-filtering.md).

## <a name="review-settings-for-advanced-features"></a>Przeglądanie ustawień funkcji zaawansowanych

Oprócz zasad ochrony nowej generacji, zapory i filtrowania zawartości internetowej usługa Defender dla firm obejmuje zaawansowane funkcje zabezpieczeń. Te funkcje są wstępnie skonfigurowane przy użyciu zalecanych ustawień; Można je jednak przejrzeć i w razie potrzeby edytować ustawienia zgodnie z potrzebami biznesowymi.

Aby uzyskać dostęp do ustawień zaawansowanych funkcji, w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) przejdź do **obszaru Ustawienia** EndpointsGeneralAdvanced features(Ustawienia  >  EndpointsGeneralAdvanced >  >  **features**).

W poniższej tabeli opisano ustawienia funkcji zaawansowanych:

| Ustawienie | Opis |
|:---|:---|
| **Badanie zautomatyzowane** <br/>(domyślnie włączone) | W miarę generowania alertów mogą być wykonywane zautomatyzowane badania. Każde zautomatyzowane badanie określa, czy wykryte zagrożenie wymaga działania, a następnie podejmuje (lub zaleca) akcje korygujące (takie jak wysyłanie pliku do kwarantanny, zatrzymywanie procesu, izolowanie urządzenia lub blokowanie adresu URL). Gdy badanie jest uruchomione, wszelkie inne powiązane alerty, które pojawiają się, są dodawane do badania do czasu jego zakończenia. Jeśli jednostka, których dotyczy problem, jest widoczna gdzie indziej, zautomatyzowane badanie rozszerza swój zakres, aby uwzględnić tę jednostkę, a proces badania powtarza się.<br/><br/>Możesz wyświetlić badania na stronie **Zdarzenia** . Wybierz zdarzenie, a następnie wybierz kartę **Badania** .<br/><br/>Domyślnie funkcje automatycznego badania i reagowania są włączone w całej dzierżawie. **Zalecamy włączenie automatycznego badania**. Jeśli ją wyłączysz, ochrona w czasie rzeczywistym w Program antywirusowy Microsoft Defender zostanie naruszona, a ogólny poziom ochrony zostanie zmniejszony. <br/><br/>[Dowiedz się więcej o zautomatyzowanych badaniach](../defender-endpoint/automated-investigations.md).   |
| **Odpowiedź na żywo**  | Usługa Defender dla firm obejmuje następujące typy akcji ręcznego reagowania: <br/>— Uruchamianie skanowania antywirusowego<br/>- Izolowanie urządzenia<br/>— Zatrzymywanie i kwarantanna pliku<br/>- Dodaj wskaźnik, aby zablokować lub zezwolić na plik <br/><br/>[Dowiedz się więcej o akcjach reagowania](../defender-endpoint/respond-machine-alerts.md). |
| **Odpowiedź na żywo dla serwerów** | (To ustawienie nie jest obecnie dostępne w usłudze Defender dla Firm)   |
| **Wykonywanie skryptu bez znaku odpowiedzi na żywo** | (To ustawienie nie jest obecnie dostępne w usłudze Defender dla Firm)  | 
| **Włączanie EDR w trybie bloku**<br/>(domyślnie włączone) | Zapewnia dodatkową ochronę przed złośliwymi artefaktami, gdy Program antywirusowy Microsoft Defender nie jest podstawowym produktem antywirusowym i działa w trybie pasywnym na urządzeniu. Wykrywanie i reagowanie na punkty końcowe (EDR) w trybie bloku działa w tle w celu skorygowania złośliwych artefaktów wykrytych przez funkcje EDR. Takie artefakty mogły zostać pominięte przez podstawowy produkt antywirusowy spoza firmy Microsoft.<br/><br/>[Dowiedz się więcej o EDR w trybie bloku](../defender-endpoint/edr-in-block-mode.md). |
| **Zezwalanie na plik lub blokowanie go** <br/>(domyślnie włączone) | Umożliwia zezwalanie na plik lub blokowanie go przy użyciu [wskaźników](../defender-endpoint/indicator-file.md). Ta funkcja wymaga włączenia Program antywirusowy Microsoft Defender w trybie aktywnym i [ochrony w chmurze](../defender-endpoint/cloud-protection-microsoft-defender-antivirus.md).<br/><br/>Zablokowanie pliku uniemożliwi jego odczyt, zapisanie lub wykonanie na urządzeniach w organizacji. <br/><br/>[Dowiedz się więcej o wskaźnikach dla plików](../defender-endpoint/indicator-file.md).  |
| **Niestandardowe wskaźniki sieci**<br/>(domyślnie włączone) | Umożliwia zezwalanie na adres IP, adres URL lub domenę lub blokowanie go przy użyciu [wskaźników sieciowych](../defender-endpoint/indicator-ip-domain.md). Ta funkcja wymaga włączenia Program antywirusowy Microsoft Defender w trybie aktywnym i [ochrony sieci](../defender-endpoint/enable-network-protection.md).<br/><br/>Możesz zezwalać na adresy IP, adresy URL lub domeny albo blokować je na podstawie własnej analizy zagrożeń. Możesz również ostrzec użytkowników za pomocą monitu, jeśli otworzą ryzykowną aplikację. Monit nie uniemożliwi im korzystania z aplikacji, ale możesz podać ostrzeżenie dla użytkowników.<br/><br/>[Dowiedz się więcej o ochronie sieci](../defender-endpoint/network-protection.md). |
| **Ochrona przed naruszeniami**<br/>(Zalecamy włączenie tego ustawienia) | Ochrona przed naruszeniami uniemożliwia złośliwym aplikacjom podejmowanie akcji, takich jak:<br/>- Wyłączanie ochrony przed wirusami i zagrożeniami<br/>— Wyłączanie ochrony w czasie rzeczywistym<br/>- Wyłączanie monitorowania zachowania<br/>— Wyłączanie ochrony w chmurze<br/>— Usuwanie aktualizacji analizy zabezpieczeń<br/>— Wyłączanie automatycznych akcji w wykrytych zagrożeniach<br/><br/>Ochrona przed naruszeniami zasadniczo blokuje Program antywirusowy Microsoft Defender do jej bezpiecznych, domyślnych wartości i uniemożliwia zmianę ustawień zabezpieczeń przez aplikacje i nieautoryzowane metody. <br/><br/>[Dowiedz się więcej o ochronie przed naruszeniami](../defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection.md).  |
| **Pokaż szczegóły użytkownika**<br/>(domyślnie włączone) | Umożliwia osobom w organizacji wyświetlanie szczegółów, takich jak obraz, nazwa, tytuł i dział pracowników. Te szczegóły są przechowywane w Azure Active Directory (Azure AD).<br/><br/>[Dowiedz się więcej o profilach użytkowników w Azure AD](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).  |
| **integracja Skype dla firm**<br/>(domyślnie włączone) | Skype dla firm został wycofany w lipcu 2021 roku. Jeśli jeszcze nie przeniesiono cię do Microsoft Teams, zobacz [Konfigurowanie Microsoft Teams w małej firmie](/microsoftteams/deploy-small-business). <br/><br/>Integracja z Microsoft Teams (lub byłym Skype dla firm) umożliwia komunikację jednym kliknięciem między osobami w Firmie.   |
| **Filtrowanie zawartości sieci Web**<br/>(domyślnie włączone) | Blokuj dostęp do witryn internetowych zawierających niepożądaną zawartość i śledź aktywność internetową we wszystkich domenach. Zobacz [Konfigurowanie filtrowania zawartości internetowej](#set-up-web-content-filtering). |
| **połączenie Microsoft Intune**<br/>(Zalecamy włączenie tego ustawienia, jeśli masz Intune) | Jeśli subskrypcja organizacji obejmuje Microsoft Intune (uwzględnioną w [Microsoft 365 Business Premium](../../business/index.yml)), to ustawienie umożliwia usłudze Defender dla firm udostępnianie informacji o urządzeniach Intune.  |
| **Wykrywanie urządzeń**<br/>(domyślnie włączone) | Umożliwia zespołowi ds. zabezpieczeń znajdowanie niezarządzanych urządzeń połączonych z siecią firmy. Nieznane i niezarządzane urządzenia wiążą się ze znacznymi zagrożeniami dla sieci — niezależnie od tego, czy jest to drukarka nienadzorowana, urządzenia sieciowe ze słabymi konfiguracjami zabezpieczeń, czy serwer bez mechanizmów kontroli zabezpieczeń. <br/><br/>Odnajdywanie urządzeń używa urządzeń dołączonych do odnajdywania urządzeń niezarządzanych, dzięki czemu zespół ds. zabezpieczeń może dołączyć niezarządzane urządzenia i zmniejszyć lukę w zabezpieczeniach. <br/><br/>[Dowiedz się więcej o odnajdywaniem urządzeń](../defender-endpoint/device-discovery.md).    |
| **Funkcje wersji zapoznawczej** | Firma Microsoft stale aktualizuje usługi, takie jak Defender dla Firm, w celu uwzględnienia nowych ulepszeń i możliwości funkcji. Jeśli zdecydujesz się na otrzymywanie funkcji w wersji zapoznawczej, będziesz jednym z pierwszych, którzy spróbują wypróbować nadchodzące funkcje w wersji zapoznawczej. <br/><br/>[Dowiedz się więcej o funkcjach w wersji zapoznawczej](../defender-endpoint/preview.md).  |

## <a name="view-and-edit-other-settings-in-the-microsoft-365-defender-portal"></a>Wyświetlanie i edytowanie innych ustawień w portalu Microsoft 365 Defender

Oprócz zasad zabezpieczeń stosowanych do urządzeń istnieją inne ustawienia, które można wyświetlać i edytować w usłudze Defender dla firm. Na przykład należy określić strefę czasową do użycia i można dołączyć (lub odłączyć) urządzenia. 

> [!NOTE]
> W dzierżawie może być wyświetlanych więcej ustawień niż w tym artykule. W tym artykule wyróżniono najważniejsze ustawienia, które należy przejrzeć w usłudze Defender dla Firm.

### <a name="settings-to-review-for-defender-for-business"></a>Ustawienia do przeglądu dla usługi Defender dla Firm

W poniższej tabeli opisano ustawienia do wyświetlania (i w razie potrzeby edytowania) w usłudze Defender dla firm:

| Kategoria | Ustawienie | Opis |
|:---|:---|:---|
| **Centrum zabezpieczeń** | **Strefa czasowa** | Wybierz strefę czasowej, która ma być używana dla dat i godzin wyświetlanych w zdarzeniach, wykrytych zagrożeniach i zautomatyzowanego badania & korygowania. Możesz użyć czasu UTC lub lokalnej strefy czasowej (*zalecane*).  |
| **Microsoft 365 Defender** | **Konta** | Wyświetl szczegóły, takie jak miejsce przechowywania danych, identyfikator dzierżawy i identyfikator organizacji (organizacji). |
| **Microsoft 365 Defender**  | **Funkcje wersji zapoznawczej**  | Włącz funkcje w wersji zapoznawczej, aby wypróbować nadchodzące funkcje i nowe możliwości. Możesz być jednym z pierwszych, którzy chcą zapoznać się z nowymi funkcjami i przekazać opinię. |
| **Punkty końcowe**  | **Powiadomienia e-mail** | Skonfiguruj lub edytuj reguły powiadomień e-mail. Po wykryciu luk w zabezpieczeniach lub utworzeniu alertu adresaci określoni w regułach powiadomień e-mail otrzymają wiadomość e-mail. [Dowiedz się więcej o powiadomieniach e-mail](mdb-email-notifications.md). |
| **Punkty końcowe**   | **Zarządzanie urządzeniami** >  **Dołączania** | Dołączanie urządzeń do usługi Defender dla Firm przy użyciu skryptu do pobrania. Aby dowiedzieć się więcej, zobacz [Dołączanie urządzeń do Microsoft Defender dla Firm](mdb-onboard-devices.md).   |  
| **Punkty końcowe**  |  **Zarządzanie urządzeniami** >  **Odłączanie** | Odłączanie (usuwanie) urządzeń z usługi Defender dla Firm. Po odłączeniu urządzenia nie wysyła ono już danych do usługi Defender dla Firm, ale dane odebrane przed odłączeniem są zachowywane. Aby dowiedzieć się więcej, zobacz [Odłączanie urządzenia](mdb-offboard-devices.md).  |

### <a name="access-your-settings-in-the-microsoft-365-defender-portal"></a>Uzyskiwanie dostępu do ustawień w portalu Microsoft 365 Defender

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)) i zaloguj się.

2. Wybierz **pozycję Ustawienia**, a następnie wybierz kategorię (na przykład **Security Center**, **Microsoft 365 Defender** lub **Endpoints**).

3. Na liście ustawień wybierz element do wyświetlenia lub edycji.

## <a name="next-steps"></a>Następne kroki

Przejdź do co najmniej jednego z następujących zadań:

- [Wprowadzenie przy użyciu Microsoft Defender dla Firm](mdb-get-started.md)
- [Zarządzanie urządzeniami w Microsoft Defender dla Firm](mdb-manage-devices.md)
- [Wyświetlanie zdarzeń i zarządzanie nimi w Microsoft Defender dla Firm](mdb-view-manage-incidents.md)
- [Wyświetlanie lub edytowanie zasad w Microsoft Defender dla Firm](mdb-view-edit-policies.md)
