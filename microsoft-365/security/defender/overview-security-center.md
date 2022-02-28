---
title: Microsoft 365 Defender, łączenie MDO, MDE, MDI i MCAS
description: 'Zalety programu Microsoft 365 Defender: połączenie usług Microsoft Defender for Office 365 (MDO) i Microsoft Defender for Endpoint (MDE) z usługami Microsoft Defender for Identity (MDI) i Microsoft Cloud App Security (MCAS). W tym artykule przedstawiono Microsoft 365 Defender dla administratorów.'
keywords: zabezpieczenia, złośliwe oprogramowanie, Microsoft 365, M365, centrum zabezpieczeń, monitorowanie, raport, tożsamości, dane, urządzenia, aplikacje
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.date: 04/21/2021
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid: met150
ms.custom: seo-marvel-jun2020
ms.technology: m365d
ms.openlocfilehash: a0dce3a61847924043a10df4c13c963f279ea011
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2021
ms.locfileid: "62989739"
---
# <a name="microsoft-365-defender-overview"></a>Microsoft 365 Defender omówienie

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Usługa Microsoft Defender dla Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)

> Chcesz doświadczyć Microsoft 365 Defender? Można go [ocenić w środowisku laboratoryjnym](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) lub [uruchomić projekt pilotażowy w środowisku produkcyjnym](m365d-pilot.md?ocid=cx-evalpilot).

**Microsoft 365 Defender** ([https://security.microsoft.com](https://security.microsoft.com)) w centralnym portalu łączy funkcje ochrony, wykrywania, badania i reakcji na wiadomości e-mail *, współpracę**, tożsamość* i zagrożenia dla urządzeń.

Microsoft 365 Defender funkcje z istniejących portali zabezpieczeń firmy Microsoft, takich jak Centrum zabezpieczeń usługi Microsoft Defender i Centrum Office 365 zabezpieczeń & zgodności. Centrum zabezpieczeń uwydatnia szybki dostęp do informacji, prostsze układy i połączenie powiązanych informacji w celu łatwiejszego korzystania z nich. W tym centrum są:

- **[Program Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)** Microsoft Defender for Office 365 ułatwia organizacjom zabezpieczanie przedsiębiorstwa za pomocą zestawu funkcji zapobiegania, wykrywania, badań i łowiectw w celu ochrony poczty e-mail Office 365 zasobów.
- **[Program Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/microsoft-defender-advanced-threat-protection)** zapewnia ochronę zapobiegawną, wykrywanie po naruszeniu zabezpieczeń, zautomatyzowane badanie i reagowanie na urządzenia w Twojej organizacji.
- **[Microsoft 365 Defender](microsoft-365-defender.md)** jest częścią rozwiązania firmy Microsoft w zakresie rozszerzonego wykrywania i odpowiedzi (XDR, *Extended Detection and Response*), które wykorzystuje portfel zabezpieczeń usługi Microsoft 365 do automatycznego analizowania danych zagrożeń w różnych domenach oraz tworzenia obrazu ataków na jednym pulpicie nawigacyjnym.

Jeśli potrzebujesz informacji o tym, co się zmieniło w Centrum zgodności Office 365 Zabezpieczeń & lub Centrum zgodności, Centrum zabezpieczeń usługi Microsoft Defender zobacz:

- [Defender for Office 365 in Microsoft 365 Defender](microsoft-365-security-center-mdo.md)
- [Defender for Endpoint in Microsoft 365 Defender](microsoft-365-security-center-mde.md)

> [!NOTE]
> Portal Microsoft 365 zabezpieczeń używa i wymusza dostęp oparty na istniejących rolach, a także przenosi każdy model zabezpieczeń do ujednoliconego portalu. Każde obciążenie pracą zbiega się z własnym dostępem opartym na rolach. Role dostępne już w tych produktach zostaną automatycznie zbiegły się w Microsoft 365 zabezpieczeń. Jednak role i uprawnienia dla usługi MCAS nadal będą obsługiwane w u usługi MCAS.

## <a name="what-to-expect"></a>Czego można się spodziewać

Całą zawartość zabezpieczeń używaną w Centrum zabezpieczeń i zgodności usługi Office 365 (protection.office.com) i Centrum zabezpieczeń programu Microsoft Defender (securitycenter.microsoft.com) można teraz znaleźć w *Microsoft 365 Defender*.

Microsoft 365 Defender pomaga zespołom zabezpieczeń badać ataki i reagować na nie, łącząc sygnały z różnych obciążeń do zestawu ujednoliconych funkcji dla:

- Alerty o & zdarzeniach
- Goniące
- Centrum akcji
- Analiza zagrożeń

Microsoft 365 Defender *celu większej* przejrzystości i wspólnych celów, ponieważ łączy program Microsoft Defender for Office 365 usługę Microsoft Defender for Endpoint. Ta korespondencja seryjna została oparta na priorytetach wymienionych poniżej i została wykonana bez poświęcania możliwości, które każdy pakiet zabezpieczeń połączył w kombinacji:

- Typowe bloki konstrukcyjne
- Wspólna terminologia
- Wspólne jednostki
- Parowalność funkcji z innymi obciążeniami pracą

> [!NOTE]
> Microsoft 365 Defender będą dostępne bez konieczności kroków migracji ani zakupu nowej licencji przez klientów. Na przykład ten nowy portal będzie dostępny dla administratorów z subskrypcją E3, podobnie jak dla użytkowników korzystających z programu Microsoft Defender dla usług Office 365 Plan 1 i Plan 2. Jednak klienci korzystający z usług Exchange Online Protection i Defender dla planu Office 365 Plan 1 będą widzieć tylko funkcje zabezpieczeń, które obsługuje licencja subskrypcji. Celem nowego centrum jest scentralizowanie zabezpieczeń.

## <a name="unified-investigations"></a>Ujednolicone badania

Zbieżne centra zabezpieczeń tworzą jedno miejsce do badania zdarzeń zabezpieczających w różnych Microsoft 365. Podstawowym przykładem są **zdarzenia w** obszarze **zdarzenia & alerty** dotyczące szybkiego uruchamiania aplikacji Microsoft 365 Defender.

:::image type="content" source="../../media/converged-incidents-2.png.png" alt-text="Strona Zdarzenia w programie Microsoft 365 Defender.":::

Wybranie nazwy zdarzenia powoduje wyświetlenie strony, która pokazuje wartość zbiegających się centrów zabezpieczeń.

:::image type="content" source="../../media/converged-incident-info-3.png" alt-text="Przykład strony Podsumowanie zdarzenia w programie Microsoft 365 Defender":::

<!--
![Example of the Summary page for an incident in Microsoft 365 Defender.](../../media/converged-incident-info-3.png)
--> 

U góry strony zdarzenia zobaczysz karty **Podsumowanie,** Alerty **, Urządzenia****, Użytkownicy****,** Skrzynki **pocztowe,** **Badania** i **Dowód**. Wybierz te karty, aby uzyskać bardziej szczegółowe informacje. Na przykład na karcie  Użytkownicy są wyświetlane informacje dotyczące użytkowników z zbieżnych obciążeń (Microsoft Defender for Endpoint, Microsoft Defender for Identity i Microsoft Cloud App Security) oraz zakres źródeł, takich jak lokalne źródła usług Usługi domenowe w usłudze Active Directory (AD DS), Azure Active Directory (Azure AD) i dostawców tożsamości innych firm. Aby uzyskać więcej informacji, zobacz [Badanie użytkowników](investigate-users.md).

Poeksymaj czas, aby przejrzeć zdarzenia w środowisku, przejść do szczegółów tych kart i przećwiczyć budowanie zrozumienia sposobu uzyskiwania dostępu do informacji dotyczących zdarzeń związanych z różnymi rodzajami zagrożeń.

Aby uzyskać więcej informacji, [zobacz Zdarzenia w Microsoft 365 Defender](incidents-overview.md).

## <a name="improved-processes"></a>Ulepszone procesy

Typowe kontrolki i zawartość występują w tym samym miejscu lub są zagęszczane w jednym kanale danych, co ułatwia ich znajdowanie. Na przykład ujednolicone ustawienia.

### <a name="unified-settings"></a>Ujednolicone ustawienia

![Po kliknięciu przycisku "Role" i otwarciu strony Ustawienia z ustawieniami ogólnymi, uprawnieniami, interfejsami API i regułami. Otwórz pozycję Uprawnienia, a następnie pozycję Role. Pokazuje wszystkie role.](../../media/converged-add-role-9.png)

### <a name="permissions--roles"></a>Uprawnienia & ról

![Uprawnienia & Role z rolami punktów końcowych &, Role i Grupy urządzeń.](../../media/converged-roles-5.png)

 Dostęp do Microsoft 365 Defender jest skonfigurowany za pomocą Azure Active Directory ról globalnych lub przy użyciu ról niestandardowych. Aby uzyskać informacje na temat programu Defender dla [punktu końcowego, zobacz Przypisywanie dostępu użytkownika do Centrum zabezpieczeń usługi Microsoft Defender](/microsoft-365/security/defender-endpoint/assign-portal-access). W przypadku usługi Defender Office 365 zobacz Uprawnienia w [Centrum zgodności platformy Microsoft 365 i Microsoft 365 Defender](../office-365-security/permissions-microsoft-365-compliance-security.md).

- Dowiedz się więcej o tym[, jak zarządzać dostępem do Microsoft 365 Defender](m365d-permissions.md)
- Dowiedz się więcej na temat [tworzenia niestandardowych ról w programie](custom-roles.md) Microsoft 365 Defender

> [!NOTE]
> Program Microsoft Defender for Endpoint w usłudze Microsoft 365 Defender obsługuje udzielanie dostępu do zarządzanych dostawców usług zabezpieczeń [(MSSP)](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) w ten sam sposób, w jaki dostęp jest udzielany w centrum zabezpieczeń [programu Microsoft Defender](./mssp-access.md).

### <a name="integrated-reports"></a>Zintegrowane raporty

Raporty są również ujednolicone w Microsoft 365 Defender. Administratorzy mogą zacząć od ogólnego raportu zabezpieczeń, a następnie rozgałęzieć do konkretnych raportów dotyczących punktów końcowych, poczty e-mail & współpracy. Linki w tym miejscu są generowane dynamicznie na podstawie konfiguracji obciążenia pracą.

### <a name="quickly-view-your-microsoft-365-environment"></a>Szybkie wyświetlanie środowiska Microsoft 365 sieci

Strona **główna** zawiera wiele typowych kart potrzebnych zespołom zabezpieczeń. Układ kart i danych zależy od roli użytkownika. Ponieważ Microsoft 365 Defender korzysta z kontroli dostępu opartej na rolach, różne role widzą karty, które są bardziej znaczące w poszczególnych zadaniach.  

Te szybko dostępne informacje pomagają być na bieżąco z najnowszymi działaniami w organizacji. Microsoft 365 Defender łączy sygnały z różnych źródeł w celu zaprezentowania widoku Microsoft 365 danych.

Karty można podzielone na następujące kategorie:

- **Tożsamości —** monitoruj tożsamości w organizacji i śledź podejrzane lub ryzykowne zachowania. [Dowiedz się więcej o ochronie tożsamości](/azure/active-directory/identity-protection/overview-identity-protection).
- **Dane** — ułatwiają śledzenie działań użytkowników, które mogą prowadzić do nieautoryzowanego ujawnienia danych.
- **Urządzenia** — uzyskaj aktualne informacje na temat alertów, działań związanych z naruszeniem zabezpieczeń i innych zagrożeń na Twoich urządzeniach.
- **Aplikacje** — uzyskaj szczegółowe informacje na temat sposobu, w jaki aplikacje w chmurze są używane w Twojej organizacji. [Dowiedz się więcej o Cloud App Security wykrytych aplikacji](/cloud-app-security/discovered-apps).

## <a name="threat-analytics-with-better-data-coverage"></a>Analiza zagrożeń i lepsza ochrona danych
Śledź wyłaniające się zagrożenia i odpowiadaj na nie, Microsoft 365 Defender środowisko zintegrowane analizy zagrożeń:

- Lepsza ochrona danych między programem Microsoft Defender for Endpoint i programem Microsoft Defender for Office 365, co umożliwia połączone zarządzanie zdarzeniami, automatyczne badanie, rozwiązywanie problemów oraz aktywne lub reakcyjne pochylenie przed zagrożeniami w całej domenie. 
- Wykrywanie i środki zaradcze związane z pocztą e-mail z programu Microsoft Defender Office 365 dla programu Office 365, oprócz danych punktu końcowego dostępnych już w programie Microsoft Defender dla punktu końcowego.
- Widok zdarzeń związanych z zagrożeniami, które agregują alerty w całej historii ataków dotyczących usługi Microsoft Defender dla punktu końcowego i usługi Microsoft Defender dla programu Office 365 w celu zmniejszenia kolejki pracy, a także uproszczenia i przyspieszenia badania.
- Próby ataków wykrytych i zablokowanych przez Microsoft 365 Defender rozwiązania. Dostępne są również dane, które mogą być wykorzystywane do kierowania działań działań zapobiegawczych, które zawęgną ryzyko dalszego ekspozycji i zwiększają odporność. 
- Ulepszony projekt, który umieszcza w centrum uwagi informacje z możliwością działania, które ułatwiają szybkie identyfikowanie danych w celu pilnego skupienia się na tych danych, zbadania ich i wykorzystania w raportach.

## <a name="a-centralized-learning-hub"></a>Scentralizowane centrum Edukacja

Microsoft 365 Defender zawiera centrum szkoleniowe, które zawiera oficjalne wskazówki z zasobów, takich jak blog poświęcony zabezpieczeniach firmy Microsoft, społeczność zabezpieczeń Firmy Microsoft w serwisie YouTube i oficjalna dokumentacja w docs.microsoft.com.

W centrum nauki wskazówki dotyczące współpracy za pomocą poczty e-mail & (Microsoft Defender dla systemu Office 365) są obok siebie z punktem końcowym (Program Microsoft Defender dla punktu końcowego) i Microsoft 365 Defender zasobów edukacyjnych.

Zostanie otwarte centrum szkoleniowe z Edukacja tematami, takimi jak "Jak badać przy użyciu programu Microsoft 365 Defender?". oraz "Microsoft Defender for Office 365 Best Practices". Ta sekcja jest obecnie projektowana przez grupę produktów zabezpieczeń firmy Microsoft. Każda Edukacja ścieżka odzwierciedla prognozowany czas, który zajmuje na koncepcjach. Na przykład "Kroki do podjęcia, gdy usługa Microsoft Defender dla systemu Office 365 zostanie naruszona", jest przewidujena na 8 minut i jest cennym procesem uczenia się w czasie pracy.

Po kliknięciu zawartości może być przydatne zakładkowanie tej witryny i organizowanie zakładek w folderze "Zabezpieczenia" lub "Krytyczne". Aby wyświetlić wszystkie Edukacja, kliknij link Pokaż wszystko w panelu głównym.

> [!NOTE]
> W **górnej części** centrum szkoleniowego programu Microsoft 365 Defender znajdują się pomocne filtry, które umożliwiają wybór produktów (obecnie jest Microsoft 365 Defender, Program Microsoft Defender dla punktów końcowych i program Microsoft Defender dla systemu Office 365). Zwróć uwagę, że na liście znajduje się liczba zasobów szkoleniowych dla każdej sekcji, co może ułatwić uczących się śledzenie liczby dostępnych zasobów do szkoleń i nauki.
>
> Oprócz filtru Produktu są wymienione bieżące tematy, typy zasobów (od klipów wideo do seminariów internetowych), poziomy znajomości obszarów zabezpieczeń, ról zabezpieczeń i funkcji produktu.

> [!TIP]
> W witrynie [Microsoft Learn](/learn/) istnieje wiele innych możliwości nauki. Znajdziesz tam szkolenie certyfikacji, takie jak [Kurs MS-500T02-A: Implementowanie](/learn/certifications/courses/ms-500t02) ochrony przed Microsoft 365 zagrożeniami.

## <a name="send-us-your-feedback"></a>Prześlij nam swoją opinię

Potrzebujemy Twojej opinii. Cały czas chcemy ulepszać funkcje, więc jeśli chcesz coś zobaczyć, prześlij nam swoją Microsoft 365 Defender [opinię](https://www.microsoft.com/videoplayer/embed/RE4K5Ci).

Możesz również pozostawić opinię na ten temat. W sekcji "Opinia" na końcu sekcji "Prześlij i wyświetl opinię dla" dostępne są opcje *Ten produkt* lub *Ta strona*.

Użyj **przycisku Ten produkt** , aby *uzyskać opinię o* produkcie:

1. Wybierz *pozycję Ten* produkt u dołu artykułu.
    1. Kliknij prawym przyciskiem myszy ten przycisk i polecenie "Otwórz w nowej karcie", jeśli chcesz kontynuować czytanie tych wskazówek.
2. Spowoduje to przejście do **forum UserVoice**.
3. Dostępne są 2 opcje:
    1. Przewiń w dół do pola tekstowego Jak *możemy poprawić* zgodność lub lepiej chronić użytkowników w Office 365? i wklej je *Microsoft 365 Defender*. Możesz wyszukać na wynikach pomysł, taki jak Twój, i zagłosować na niego lub użyć przycisku **Opublikuj nowy pomysł**.
    1. Jeśli masz pewność, że ten problem jest już zgłoszony i chcesz podnieść jego profil, głosem (lub głosami), użyj  pola Opinie po prawej stronie okna UserVoice. Wyszukaj *Microsoft 365 Defender,* **znajdź problem i podnieś** jego status za pomocą przycisku głosu.

Użyj *tej strony,* aby uzyskać opinię na temat samego artykułu. Dziękujemy za opinię. Twój głos pomaga nam ulepszać produkty.

### <a name="explore-what-the-security-center-has-to-offer"></a>Sprawdź, co ma do zaoferowania centrum zabezpieczeń

Poznaj funkcje i możliwości w programie Microsoft 365 Defender:

- [Zarządzanie zdarzeniami i alertami](manage-incidents.md)
- [Śledzenie wyłaniających się zagrożeń i reagowanie na nie za pomocą analizy zagrożeń](threat-analytics.md)
- [Centrum akcji](m365d-action-center.md)
- [Poszukiwania zagrożeń na różnych urządzeniach, w wiadomościach e-mail, aplikacjach i tożsamościach](./advanced-hunting-query-emails-devices.md)
- [Niestandardowe reguły wykrywania](./custom-detection-rules.md)
- [Alerty dotyczące & poczty e-mail](../../compliance/alert-policies.md#default-alert-policies)
- [Tworzenie symulacyjnej próby wyłudzania](../office-365-security/attack-simulation-training.md) informacji [i tworzenie ładu na szkolenia dla zespołów](/microsoft-365/security/office-365-security/attack-simulation-training-payloads)
 
### <a name="related-information"></a>Informacje pokrewne
- [Usługa Microsoft Defender dla Office 365 w programie Microsoft 365 Defender](microsoft-365-security-center-mdo.md)
- [Program Microsoft Defender dla punktu końcowego w programie Microsoft 365 Defender](microsoft-365-security-center-mde.md)
- [Przekierowywanie kont z usługi Microsoft Defender for Endpoint do usługi Microsoft 365 Defender](microsoft-365-security-mde-redirection.md)