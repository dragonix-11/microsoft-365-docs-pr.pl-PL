---
title: Filtrowanie zawartości sieci Web
description: Filtrowanie zawartości sieci Web w programie Ochrona punktu końcowego w usłudze Microsoft Defender umożliwia śledzenie i regulowanie dostępu do witryn internetowych na podstawie ich kategorii zawartości.
keywords: ochrona sieci Web, ochrona przed zagrożeniami internetowymi, przeglądanie Internetu, monitorowanie, raporty, karty, lista domen, zabezpieczenia, wyłudzanie informacji, złośliwe oprogramowanie, exploit, witryny internetowe, ochrona sieci, Edge, Internet Explorer, Chrome, Firefox, przeglądarka internetowa
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 2535845c52285b1ce28fbe142709089778503c09
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469586"
---
# <a name="web-content-filtering"></a>Filtrowanie zawartości sieci Web

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

Filtrowanie zawartości sieci Web jest częścią funkcji ochrony sieci [Web](web-protection-overview.md) w programie Ochrona punktu końcowego w usłudze Microsoft Defender. Pozwala organizacji śledzić dostęp do witryn internetowych i regulować go na podstawie ich kategorii zawartości. Wiele z tych witryn sieci Web, chociaż nie jest złośliwych, może być problematycznych ze względu na zgodność z przepisami, użycie przepustowości lub inne problemy.

Skonfiguruj zasady dla różnych grup urządzeń, aby blokować określone kategorie. Zablokowanie kategorii uniemożliwia użytkownikom w określonych grupach urządzeń uzyskiwanie dostępu do adresów URL skojarzonych z tą kategorią. W przypadku kategorii, która nie jest blokowana, adresy URL są automatycznie insektowane. Użytkownicy mogą bez zakłóceń uzyskać dostęp do adresów URL, a Ty zbierasz statystyki dostępu, aby ułatwić tworzenie bardziej niestandardowych decyzji dotyczących zasad. Użytkownicy zobaczą powiadomienie o zablokowaniu, jeśli element na wyświetlanej stronie będzie dzwonić do zablokowanego zasobu.

Filtrowanie zawartości sieci Web jest dostępne w głównych przeglądarkach internetowych, a bloki są wykonywane przez filtr Windows Defender SmartScreen (Microsoft Edge) i network Protection (Chrome, Firefox, Firefox, Firefox i Opera). Aby uzyskać więcej informacji na temat obsługi przeglądarek, zobacz sekcję wymagań wstępnych.

## <a name="benefits-of-web-content-filtering"></a>Zalety filtrowania zawartości sieci Web

- Użytkownicy nie mogą uzyskać dostępu do witryn internetowych w kategoriach zablokowanych, niezależnie od tego, czy przeglądają witryny lokalne, czy z dala od sieci.

- Zespół zabezpieczeń może wygodnie wdrażać zasady w grupach użytkowników za pomocą grup urządzeń zdefiniowanych w Ochrona punktu końcowego w usłudze Microsoft Defender [kontroli dostępu opartej na rolach](/microsoft-365/security/defender-endpoint/rbac).

- Twój zespół zabezpieczeń może uzyskać dostęp do raportów sieci Web w tej samej lokalizacji centralnej z widocznością na rzeczywistych blokach i użyciu sieci Web.

## <a name="prerequisites"></a>Wymagania wstępne

Przed wypróbowaniem tej funkcji upewnij się, że są spełnione następujące wymagania:

- Subskrypcja obejmuje jedną z następujących usług: Windows 10 Enterprise E5, Microsoft 365 E5, Zabezpieczenia platformy Microsoft 365 E5, Microsoft 365 E3 + Zabezpieczenia platformy Microsoft 365 E5 dodatku lub licencji Ochrona punktu końcowego w usłudze Microsoft Defender autonomicznej. 

- Masz dostęp do portalu <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender sieci.</a>

- Na urządzeniach organizacji jest Windows 10 rocznicowa aktualizacja (wersja 1607) lub nowsza albo Windows 11 z najnowszymi aktualizacjami oprogramowania antywirusowego/ochrony przed [złośliwym oprogramowaniem](manage-updates-baselines-microsoft-defender-antivirus.md).

- Windows Defender i Ochrona sieci są włączone na urządzeniach organizacji.

## <a name="data-handling"></a>Obsługa danych

Dane są przechowywane w regionie wybranym w ramach ustawień obsługi Ochrona punktu końcowego w usłudze Microsoft Defender [danych](data-storage-privacy.md). Twoje dane nie opuszczą centrum danych w tym regionie. Ponadto Twoje dane nie będą udostępniane innym podmiotom, w tym naszym dostawcom danych.

## <a name="turn-on-web-content-filtering"></a>Włączanie filtrowania zawartości sieci Web

W lewym okienku nawigacji w witrynie <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender wybierz</a> **pozycję** \> Ustawienia **punkty końcowe Ogólne** \> **funkcje** \> **zaawansowane**. Przewijaj w dół, aż zobaczysz wpis **Filtrowanie zawartości sieci Web**. Przestaw przełącznik na pozycję Włącz **i** **Zapisz preferencje**.

### <a name="configure-web-content-filtering-policies"></a>Konfigurowanie zasad filtrowania zawartości sieci Web

Zasady filtrowania zawartości sieci Web określają, które kategorie witryn są blokowane dla poszczególnych grup urządzeń. Aby zarządzać zasadami, przejdź do **Ustawienia** \> **filtrowania** \> zawartości sieci **Web punktów końcowych** (w obszarze **Reguły**).

Zasady można wdrożyć w celu zablokowania dowolnej z następujących kategorii nadrzędnych lub podrzędnych:

<details>
<summary>Zawartość dla dorosłych</summary>

**Karty**: Witryny związane z grupami lub ruchami, których członkowie mają pasję w systemie przeświadczenia, który różni się od tych, które są akceptowane społecznościowo. 

**Więcej**: witryny internetowe i takie, które sprzyjają rozwoju umiejętności i ćwiczeń.

**Nagość**: Witryny, które zawierają obrazy lub klipy wideo w pełnej formie półnagiej i półnagie, zazwyczaj w formie artystycznej, które mogą umożliwiać pobieranie lub sprzedaż takich materiałów.

**Pornografia / erocycyjni**: witryny zawierające eroerograficznych treści w formie tekstowej lub obrazów. W tym miejscu są również wymienione wszelkie formy materiałów o treści eroce.

Edukacja płciowa **: witryny**, które dyskutują o płci i erotyce w czytelny i nieoputyczny sposób, w tym witryny edukacyjne dotyczące odtwarzania przez człowieka i odtwarzania, witryny, które oferują porady dotyczące zapobiegania dostępowi do choroby erotycznej, oraz witryny, które oferują porady dotyczące zdrowia osób erotycznych.

**Niesmakowe**: witryny ukierunkowane na zawartość nieuprawnianą do wyświetlania przez dzieci w szkołach lub że pracodawca miałby kłopoty z dostępem ich personelu, ale nie musi to być pornografia czy pornografia.

**Przemoc**: witryny, które wyświetlają lub promują zawartość związaną z przemocą wobec osób lub zwierząt.

</details>

<details>
<summary>Wysoka przepustowość</summary>

**Pobieranie witryn**: witryny, których podstawową funkcją jest zezwalanie użytkownikom na pobieranie zawartości multimedialnej lub programów, takich jak programy komputerowe.

**Udostępnianie obrazów**: Witryny używane głównie do wyszukiwania lub udostępniania zdjęć, w tym witryn o aspektach społecznościowych.

**Komunikacja równorzędna**: Witryny hostuje oprogramowanie P2P lub ułatwiają udostępnianie plików przy użyciu oprogramowania P2P.

**Przesyłanie strumieniowe multimediów &** pobierania: Witryny, których podstawową funkcją jest rozpowszechnianie multimediów strumieniowych, lub witryn, które umożliwiają użytkownikom wyszukiwanie, oglądanie lub odsłuchiwać strumieniowanie multimediów.
  
</details>

<details>
<summary>Odpowiedzialność prawnie</summary>

**Obrazy wykorzystywania przez dzieci**: Witryny, które zawierają obrazy lub pornografię z nadużyciami dziecka. 

**Działania przestępcze**: Witryny, które instrukcje, porady dotyczące działań niezgodnych z prawem lub promocji.

**Hacking**: Witryny, które dostarczają zasoby na użytek niezgodnego z prawem lub mogącego stanowić wątpliwości użycia oprogramowania komputerowego lub sprzętu, w tym witryn rozpowszechniających materiały chronione prawem autorskim, które zostały pęknięte.

**Nienawiść &** wychwytywanie: Witryny promujące agresywne, poniżające lub obraźliwe opinie na temat dowolnej sekcji populacji, która może być identyfikowana przez rasę, religię, płeć, wiek, nacjonalność, niepełnosprawność fizyczną, sytuację ekonomiczne, preferencje dotyczące orientacji ciała lub inny wybór stylu życia.

**Niezgodne z prawem:** witryny, które sprzedają niedozwolone/kontrolowane witryny, promują nadużycie w wiadce lub sprzedaży powiązanych paraphernalia.

**Niezgodne z** prawem oprogramowanie: Witryny zawierające złośliwe oprogramowanie, programy szpiegujące, botnety, wyłudzanie informacji i kradzieże praw autorskich &.

**Ściągawki szkolne**: Witryny związane z oszustami i oszustwami szkolnmi. 

**Samoobsługa**: witryny, które promują działania autoszkodne, w tym witryny cyberprzemocne, które zawierają obraźliwe i/lub obraźliwe wiadomości wobec użytkowników.

**Wschowa**: każda witryna, która sprzedaje schowek lub popiera użycie chłoniaka, w tym między innymi schłoń i wigorę.

</details>

<details>
<summary>Rozrywka</summary>

**Czat**: Witryny, które są przede wszystkim internetowymi pokojami rozmów.

**Gry**: Witryny związane z grami wideo lub komputerowymi, w tym witryny promujące gry poprzez Usługi online lub informacje związane z grami.

**Wiadomości błyskawiczne**: Witryny, których można używać do pobierania oprogramowania do wiadomości błyskawicznych lub wiadomości błyskawicznych klienta.

**Professional sieci:** Witryny, które zapewniają profesjonalne usługi sieciowe.

**Sieci społecznościowe**: witryny, które zapewniają usługi sieci społecznościowych.

**Internetowa poczta e-mail**: Witryny oferujące usługi poczty internetowej.
  
</details>

<details>
<summary>Bez kategorii</summary>

**Nowo zarejestrowane domeny**: Witryny, które zostały nowo zarejestrowane w ciągu ostatnich 30 dni i nie zostały jeszcze przeniesione do innej kategorii.

**Zaparkowane domeny**: Witryny, które nie mają zawartości lub są zaparkowane do późniejszego użytku.
  
**UWAGA**: Niekategorizowane zawiera tylko nowo zarejestrowane domeny i zaparkowane domeny, a nie obejmuje wszystkich innych witryn spoza tych kategorii.
  
</details>

### <a name="create-a-policy"></a>Tworzenie zasad

Aby dodać nowe zasady, wykonaj następujące czynności:

1. W portalu <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender wybierz</a> pozycję filtrowanie **zawartości** >  Ustawienia **Web** > **+ Dodaj zasady**.

2. Określ nazwę.

3. Wybierz kategorie, które chcesz zablokować. Za pomocą ikony rozwijania możesz w pełni rozwinąć każdą kategorię nadrzędną i wybrać określone kategorie zawartości sieci Web.

4. Określanie zakresu zasad. Wybierz grupy urządzeń, aby określić, gdzie mają być stosowane zasady. Dostęp do witryn internetowych w wybranych kategoriach nie będzie miał tylko urządzeń w wybranych grupach urządzeń.

5. Przejrzyj podsumowanie i zapisz zasady. Odświeżanie zasad może potrwać do 2 godzin, aby zastosować je do wybranych urządzeń.

> [!NOTE]
>
> - Zasady można wdrożyć bez wybierania żadnej kategorii w grupie urządzeń. Ta akcja spowoduje utworzenie zasad inspekcji tylko w celu zrozumienia zachowania użytkownika przed utworzeniem zasad blokowania.
> - Jeśli usuwasz zasady lub zmieniasz grupy urządzeń w tym samym czasie, może to powodować opóźnienie we wdrożeniu zasad.
> - Zablokowanie kategorii "Niekategoryzowane" może prowadzić do nieoczekiwanych i nieoczekiwanych wyników.

## <a name="end-user-experience"></a>Środowisko użytkownika końcowego

Środowisko blokowania przeglądarek obsługiwanych przez inne firmy jest udostępniane przez usługę Network Protection, która dostarcza użytkownikowi komunikatu na poziomie systemu z powiadomieniem o zablokowanym połączeniu. Aby uzyskać bardziej przyjazne środowisko użytkownika w przeglądarce, rozważ korzystanie z programu Microsoft Edge.

### <a name="allow-specific-websites"></a>Zezwalaj na określone witryny internetowe

Można zastąpić zablokowaną kategorię w filtrowaniu zawartości sieci Web, aby zezwolić na dostęp do pojedynczej witryny przez utworzenie niestandardowych zasad wskaźników. Zasady wskaźnika niestandardowego sprządną, że zasady filtrowania zawartości sieci Web zostaną wtedy zastosowane do danych grup urządzeń.

Aby zdefiniować wskaźnik niestandardowy, wykonaj następujące czynności:

1. W portalu <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender przejdź</a> do pozycji Adres **URL Ustawienia** \>  \> punktów **końcowych** \> **/Dodaj** \> **element domeny**.

2. Wprowadź domenę witryny.

3. Ustaw akcję zasad na **Zezwalaj**.

### <a name="dispute-categories"></a>Kategorie sporów

Jeśli napotkasz niepoprawnie skategoryzowaną domenę, możesz sporyć o kategorię bezpośrednio z portalu.

Aby sporyć o kategorię domeny, przejdź do strony **Raporty** \> szczegółów filtrowania zawartości sieci **Web** \> **ochrony** \> sieci **Web**. Na karcie domen raportów filtrowania zawartości sieci Web obok każdej z tych domen będzie wyświetlony wielokropek. Umieść wskaźnik myszy na tym wielokropek i wybierz **pozycję Kategoria sporu**.

Zostanie otwarty panel, w którym można wybrać priorytet, i dodać więcej szczegółów, na przykład sugerowaną kategorię do ponownej kategorii. Po zakończeniu formularzy wybierz pozycję **Prześlij**. Nasz zespół będzie przeglądać żądanie w ciągu jednego dnia biznesowego. Aby natychmiast odblokować, utwórz [niestandardowy wskaźnik zezwalania](indicator-ip-domain.md).

### <a name="url-category-lookup"></a>Odnośnik kategorii adresu URL

Aby ustalić kategorię witryny internetowej, możesz użyć funkcji wyszukiwania adresów URL dostępnej w portalu Microsoft 365 Defender sieci Web (<https://security.microsoft.com>) w obszarze **Wyszukiwanie punktów końcowych**\>. W wynikach wyszukiwania adresu URL kategoria filtrowania zawartości sieci Web jest wyświetlana w obszarze **Szczegóły adresu URL/domeny**. Administratorzy mogą także sporyć o kategorię domeny bezpośrednio z tej strony, jak pokazano na poniższej ilustracji. Jeśli wynik kategorii nie jest wyświetlany, adres URL nie jest obecnie przypisany do istniejącej kategorii filtrowania zawartości sieci Web.

:::image type="content" source="../../media/web-content-filtering-category-lookup.png" alt-text="Wyniki wyszukiwania kategorii filtrowania zawartości sieci Web" lightbox="../../media/web-content-filtering-category-lookup.png":::

## <a name="web-content-filtering-cards-and-details"></a>Karty i szczegóły filtrowania zawartości sieci Web

Wybierz **pozycję Raporty** \> **ochrona sieci Web** , aby wyświetlić karty z informacjami na temat filtrowania zawartości sieci Web i ochrony przed zagrożeniami internetowymi. Poniższe karty zawierają podsumowanie informacji na temat filtrowania zawartości sieci Web.

### <a name="web-activity-by-category"></a>Aktywność w sieci Web według kategorii

Ta karta zawiera listę nadrzędnych kategorii zawartości sieci Web z największym zwiększeniem lub zmniejszeniem liczby prób dostępu. Zrozumienie zmian znacząco zmianami wzorców aktywności w Internecie w organizacji z ostatnich 30, 3 miesięcy lub 6 miesięcy. Wybierz nazwę kategorii, aby wyświetlić więcej informacji.

W ciągu pierwszych 30 dni korzystania z tej funkcji twoja organizacja może nie mieć wystarczającej ilości danych, aby wyświetlić te informacje.

:::image type="content" source="images/web-activity-by-category600.png" alt-text="Aktywność w Internecie według karty kategorii" lightbox="images/web-activity-by-category600.png":::

### <a name="web-content-filtering--summary-card"></a>Karta podsumowania filtrowania zawartości sieci Web

Na tej karcie jest wyświetlany rozkład prób zablokowania dostępu w poszczególnych nadrzędnych kategoriach zawartości sieci Web. Wybierz jeden z kolorowych pasków, aby wyświetlić więcej informacji na temat określonej nadrzędnej kategorii sieci Web.

:::image type="content" source="images/web-content-filtering-summary.png" alt-text="Karta podsumowania filtrowania zawartości sieci Web" lightbox="images/web-content-filtering-summary.png":::

### <a name="web-activity-summary-card"></a>Karta podsumowania aktywności w sieci Web

Ta karta zawiera łączną liczbę żądań zawartości sieci Web we wszystkich adresach URL.

:::image type="content" source="images/web-activity-summary.png" alt-text="Karta podsumowania aktywności w sieci Web" lightbox="images/web-activity-summary.png":::

### <a name="view-card-details"></a>Wyświetl szczegóły karty

Aby uzyskać dostęp do szczegółów **raportu dla** każdej karty, wybierz wiersz tabeli lub kolorowy pasek na karcie. Strona szczegółów raportu dla każdej karty zawiera rozbudowane dane statystyczne dotyczące kategorii zawartości sieci Web, domen witryn sieci Web i grup urządzeń.

:::image type="content" source="images/web-protection-report-details.png" alt-text="Szczegóły raportu ochrony sieci Web" lightbox="images/web-protection-report-details.png":::

- **Kategorie sieci Web**: Zawiera listę kategorii zawartości sieci Web, do których dostęp miały próby uzyskania dostępu w organizacji. Wybierz konkretną kategorię, aby otworzyć wysuwne podsumowanie.

- **Domeny**: zawiera listę domen sieci Web, do których dostęp uzyskano lub zablokowano w organizacji. Wybierz konkretną domenę, aby wyświetlić szczegółowe informacje o tej domenie.

- **Grupy urządzeń**. Wyświetla listę wszystkich grup urządzeń, które wygenerowała aktywność w sieci Web w organizacji.

Użyj filtru zakresu czasu w lewym górnym rogu strony, aby wybrać przedział czasu. Możesz też filtrować informacje lub dostosowywać kolumny. Zaznacz wiersz, aby otworzyć okienko wysuwu z jeszcze większej liczby informacji na temat zaznaczonego elementu.

### <a name="known-issues-and-limitations"></a>Znane problemy i ograniczenia

Obsługiwane Microsoft Edge tylko wtedy, gdy konfiguracją systemu operacyjnego Twojego urządzenia jest serwer (**cmd** \> **Systeminfo** \> **OS Configuration**). Ochrona sieci jest obsługiwana tylko w trybie inspekcji na urządzeniach z systemem Server, który jest odpowiedzialny za zabezpieczanie ruchu we wszystkich obsługiwanych przeglądarkach innych firm.

Obsługiwane Microsoft Edge i ochrona sieci nie jest obsługiwana na Windows 10 hostach wielosektapowych pulpitu wirtualnego Azure.

Ochrona sieci obecnie nie obsługuje inspekcji SSL, co może powodować, że niektóre witryny będą dozwolone przez filtrowanie zawartości sieci Web, które zwykle byłoby zablokowane. Witryny mogą być dozwolone ze względu na brak widoczności w zaszyfrowanym ruchu po zakończeniu uściślenia TLS i braku możliwości analizowania niektórych przekierowywania.  Dotyczy to przekierowywania z niektórych internetowych stron logowania poczty do strony skrzynki pocztowej. Jako zaakceptowane obejście możesz utworzyć niestandardowy wskaźnik blokowania dla strony logowania, aby upewnić się, że żaden użytkownik nie będzie mógł uzyskać dostępu do witryny. Pamiętaj, że może to zablokować im dostęp do innych usług skojarzonych z tą samą witryną internetową. 

## <a name="see-also"></a>Zobacz też

- [Omówienie ochrony sieci Web](web-protection-overview.md)
- [Ochrona przed zagrożeniami internetowymi](web-threat-protection.md)
- [Monitorowanie zabezpieczeń sieci Web](web-protection-monitoring.md)
- [Reagowanie na zagrożenia w sieci Web](web-protection-response.md)
- [Wymagania dotyczące ochrony sieci](web-content-filtering.md)
