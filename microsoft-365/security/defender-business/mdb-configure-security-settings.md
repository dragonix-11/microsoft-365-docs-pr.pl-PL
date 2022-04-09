---
title: Wyświetlanie i edytowanie ustawień zabezpieczeń w Microsoft Defender dla Firm
description: Konfigurowanie zasad zabezpieczeń w Microsoft Defender dla Firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 3d6ef3a7bc3ae9b7556041cedc88df354421f885
ms.sourcegitcommit: dd5fc139affb4cba4089cbdb2c478968b680699a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2022
ms.locfileid: "64746497"
---
# <a name="view-and-edit-your-security-policies-and-settings-in-microsoft-defender-for-business"></a>Wyświetlanie i edytowanie zasad zabezpieczeń i ustawień w Microsoft Defender dla Firm

> [!IMPORTANT]
> Microsoft Defender dla Firm jest wdrażana dla [klientów Microsoft 365 Business Premium](../../business-premium/index.md) od 1 marca 2022 r. Usługa Defender dla Firm jako subskrypcja autonomiczna jest dostępna w wersji zapoznawczej i będzie stopniowo wdrażana dla klientów i partnerów IT, którzy [zarejestrują się tutaj](https://aka.ms/mdb-preview) , aby zażądać tej subskrypcji. Wersja zapoznawcza zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać możliwości.
> 
> Niektóre informacje zawarte w tym artykule odnoszą się do wstępnie wydanych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjnym wydaniem. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, dotyczących informacji podanych tutaj. 

## <a name="overview"></a>Omówienie

Po dołączeniu urządzeń firmy do Microsoft Defender dla Firm następnym krokiem jest wyświetlenie i w razie potrzeby edytowanie zasad i ustawień zabezpieczeń. Zasady zabezpieczeń do skonfigurowania obejmują:

- **[Zasady ochrony nowej generacji](#view-or-edit-your-next-generation-protection-policies)**, które określają ochronę antywirusową i ochronę przed złośliwym kodem dla urządzeń firmy
- **[Ochrona zapory i reguły](#view-or-edit-your-firewall-policies-and-custom-rules)**, które określają, jaki ruch sieciowy może przepływać do lub z urządzeń firmy
- **[Filtrowanie zawartości internetowej](#set-up-web-content-filtering)**, które uniemożliwia użytkownikom odwiedzanie niektórych witryn internetowych (adresów URL) na podstawie kategorii, takich jak treści dla dorosłych lub odpowiedzialność prawna.

W usłudze Defender dla firm zasady zabezpieczeń są stosowane do urządzeń za pośrednictwem [grup urządzeń](mdb-create-edit-device-groups.md#what-is-a-device-group). 

Oprócz zasad zabezpieczeń można [wyświetlać i edytować ustawienia](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal), takie jak strefa czasowa do użycia w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) oraz to, czy mają być odbierane funkcje w wersji zapoznawczej w miarę ich udostępniania.

Skorzystaj z tego artykułu jako przewodnika po zarządzaniu zasadami i ustawieniami zabezpieczeń.

## <a name="what-to-do"></a>Co robić

1. [Wybierz miejsce zarządzania zasadami zabezpieczeń i urządzeniami](#choose-where-to-manage-security-policies-and-devices).

2. [Wyświetlanie lub edytowanie zasad ochrony nowej generacji](#view-or-edit-your-next-generation-protection-policies).

3. [Wyświetlanie lub edytowanie zasad zapory i reguł niestandardowych](#view-or-edit-your-firewall-policies-and-custom-rules).

4. [Skonfiguruj filtrowanie zawartości internetowej](#set-up-web-content-filtering).

5. [Wyświetl i edytuj inne ustawienia w portalu Microsoft 365 Defender](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal). 

6. [Przejdź do kolejnych kroków](#next-steps).

>
> **Masz minutę?**
> Weźmy <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę dotyczącą Microsoft Defender dla Firm</a>. Chcielibyśmy usłyszeć od Ciebie!
>

## <a name="choose-where-to-manage-security-policies-and-devices"></a>Wybieranie miejsca zarządzania zasadami zabezpieczeń i urządzeniami

Usługa Defender dla firm oferuje [uproszczony proces konfiguracji](mdb-simplified-configuration.md) , który pomaga usprawnić proces konfiguracji i konfiguracji. Jeśli wybierzesz uproszczony proces konfiguracji, możesz wyświetlić zasady zabezpieczeń i zarządzać nimi w portalu Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)). Nie ograniczasz się jednak do tej opcji. Jeśli używasz Microsoft Endpoint Manager (w tym Microsoft Intune), możesz nadal korzystać z Endpoint Manager.

Poniższa tabela może pomóc w wyborze miejsca zarządzania zasadami zabezpieczeń i urządzeniami. <br/><br/>

| Opcja | Opis |
|:---|:---|
| **Korzystanie z portalu Microsoft 365 Defender** (*zalecane*) | Portal Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)) może być punktem obsługi do zarządzania urządzeniami firmy, zasadami zabezpieczeń i ustawieniami zabezpieczeń. Możesz uzyskiwać dostęp do zasad i ustawień zabezpieczeń, korzystać z [pulpitu nawigacyjnego zarządzania lukami w zabezpieczeniach & zagrożeniami](mdb-view-tvm-dashboard.md) oraz [wyświetlać zdarzenia i zarządzać nimi](mdb-view-manage-incidents.md) w jednym miejscu. <br/><br/>Jeśli używasz Microsoft Endpoint Manager, urządzenia dołączone do usługi Defender dla Firm i zasady zabezpieczeń są widoczne w Endpoint Manager. Aby dowiedzieć się więcej, zobacz następujące artykuły:<br/><br/>- [Ustawienia domyślne usługi Defender dla firm i Microsoft Endpoint Manager](mdb-next-gen-configuration-settings.md#defender-for-business-default-settings-and-microsoft-endpoint-manager)<br/><br/>- [Zapora w Microsoft Defender dla Firm](mdb-firewall.md)   |
| **Korzystanie z Microsoft Endpoint Manager** | Jeśli twoja firma już używa Endpoint Manager (w tym Microsoft Intune) do zarządzania zasadami zabezpieczeń, możesz nadal używać Endpoint Manager do zarządzania urządzeniami i zasadami zabezpieczeń. Aby dowiedzieć się więcej, zobacz [Zarządzanie zabezpieczeniami urządzeń przy użyciu zasad zabezpieczeń punktu końcowego w Microsoft Intune](/mem/intune/protect/endpoint-security-policy). <br/><br/>Jeśli zdecydujesz się na przejście do [uproszczonego procesu konfiguracji w usłudze Defender dla firm](mdb-simplified-configuration.md), zostanie wyświetlony monit o usunięcie wszelkich istniejących zasad zabezpieczeń w Endpoint Manager, aby uniknąć [konfliktów zasad](mdb-troubleshooting.yml) później. |

> [!IMPORTANT]
> Jeśli zarządzasz zasadami zabezpieczeń w portalu Microsoft 365 Defender, możesz *wyświetlić* te zasady w Endpoint Manager, wymienione jako zasady ochrony antywirusowej lub zapory. Podczas wyświetlania zasad zapory w Endpoint Manager zostaną wyświetlone dwie zasady: jedna dla ochrony zapory, a druga dla reguł niestandardowych.

## <a name="view-or-edit-your-next-generation-protection-policies"></a>Wyświetlanie lub edytowanie zasad ochrony nowej generacji

W zależności od tego, czy używasz portalu Microsoft 365 Defender, czy Microsoft Endpoint Manager do zarządzania zasadami ochrony nowej generacji, użyj jednej z procedur w poniższej tabeli: <br/><br/>

| Portal | Procedura |
|:---|:---|
| portal Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się. <br/><br/>2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są zorganizowane według systemu operacyjnego i typu zasad.<br/><br/>3. Wybierz kartę systemu operacyjnego (na przykład **Windows klientów**).<br/><br/>4. Rozwiń **kolejną generację ochrony** , aby wyświetlić listę zasad.<br/><br/>5. Wybierz zasady, aby wyświetlić więcej szczegółów dotyczących zasad. Aby wprowadzić zmiany lub dowiedzieć się więcej o ustawieniach zasad, zobacz następujące artykuły: <br/>- [Wyświetlanie lub edytowanie zasad urządzeń](mdb-view-edit-policies.md)<br/>- [Omówienie ustawień konfiguracji następnej generacji](mdb-next-gen-configuration-settings.md)  |
| centrum administracyjne Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Przejdź do [https://endpoint.microsoft.com](https://endpoint.microsoft.com) obszaru i zaloguj się. Jesteś teraz w centrum administracyjnym Microsoft Endpoint Manager.<br/><br/>2. Wybierz pozycję **Zabezpieczenia punktu końcowego**.<br/><br/>3. Wybierz pozycję **Program antywirusowy** , aby wyświetlić zasady w tej kategorii. <br/><br/>Aby uzyskać pomoc dotyczącą zarządzania ustawieniami zabezpieczeń w Microsoft Endpoint Manager, zacznij od [pozycji Zarządzanie zabezpieczeniami punktów końcowych w Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="view-or-edit-your-firewall-policies-and-custom-rules"></a>Wyświetlanie lub edytowanie zasad zapory i reguł niestandardowych

W zależności od tego, czy używasz portalu Microsoft 365 Defender, czy Microsoft Endpoint Manager do zarządzania ochroną zapory, użyj jednej z procedur w poniższej tabeli: <br/><br/>

| Portal | Procedura |
|:---|:---|
| portal Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się. <br/><br/>2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**. Zasady są zorganizowane według systemu operacyjnego i typu zasad.<br/><br/>3. Wybierz kartę systemu operacyjnego (na przykład **Windows klientów**).<br/><br/>4. Rozwiń węzeł **Zapora** , aby wyświetlić listę zasad.<br/><br/>5. Wybierz zasady, aby wyświetlić więcej szczegółów dotyczących zasad. Aby wprowadzić zmiany lub dowiedzieć się więcej o ustawieniach zasad, zobacz następujące artykuły: <br/>- [Wyświetlanie lub edytowanie zasad urządzeń](mdb-view-edit-policies.md)<br/>- [Ustawienia zapory](mdb-firewall.md)<br/>- [Zarządzanie niestandardowymi regułami zasad zapory](mdb-custom-rules-firewall.md)  |
| centrum administracyjne Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Przejdź do [https://endpoint.microsoft.com](https://endpoint.microsoft.com) obszaru i zaloguj się. Jesteś teraz w centrum administracyjnym Microsoft Endpoint Manager.<br/><br/>2. Wybierz pozycję **Zabezpieczenia punktu końcowego**.<br/><br/>3. Wybierz pozycję **Zapora** , aby wyświetlić zasady w tej kategorii. Reguły niestandardowe zdefiniowane na potrzeby ochrony zapory są wyświetlane jako oddzielne zasady.<br/><br/>Aby uzyskać pomoc dotyczącą zarządzania ustawieniami zabezpieczeń w Microsoft Endpoint Manager, zacznij od [pozycji Zarządzanie zabezpieczeniami punktów końcowych w Microsoft Intune](/mem/intune/protect/endpoint-security). |

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

3. Wybierz kategorie do zablokowania. Użyj ikony rozwijania, aby w pełni rozwinąć każdą kategorię nadrzędną i wybrać określone kategorie zawartości internetowej.

   Aby skonfigurować zasady tylko do inspekcji, które nie blokują żadnych witryn internetowych, nie wybieraj żadnych kategorii.

   Nie wybieraj pozycji **Bez kategorii**.

4. Określ zakres zasad, wybierając grupy urządzeń do zastosowania zasad. Tylko urządzenia w wybranych grupach urządzeń nie będą mogły uzyskiwać dostępu do witryn internetowych w wybranych kategoriach.

5. Przejrzyj podsumowanie i zapisz zasady. Odświeżanie zasad może potrwać do 2 godzin w przypadku wybranych urządzeń.

> [!TIP]
> Aby dowiedzieć się więcej na temat filtrowania zawartości internetowej, zobacz [Filtrowanie zawartości sieci Web](../defender-endpoint/web-content-filtering.md).

## <a name="view-and-edit-other-settings-in-the-microsoft-365-defender-portal"></a>Wyświetlanie i edytowanie innych ustawień w portalu Microsoft 365 Defender

Oprócz zasad zabezpieczeń stosowanych do urządzeń istnieją inne ustawienia, które można wyświetlać i edytować w usłudze Defender dla firm. Na przykład należy określić strefę czasową do użycia i można dołączyć (lub odłączyć) urządzenia. 

> [!NOTE]
> W dzierżawie może być wyświetlanych więcej ustawień niż w tym artykule. W tym artykule wyróżniono najważniejsze ustawienia, które należy przejrzeć w usłudze Defender dla Firm.

### <a name="settings-to-review-for-defender-for-business"></a>Ustawienia do przeglądu dla usługi Defender dla Firm

W poniższej tabeli opisano ustawienia do wyświetlania (i w razie potrzeby edytowania) w usłudze Defender dla firm.

<br/><br/>

| Kategoria | Ustawienie | Opis |
|:---|:---|:---|
| **Centrum zabezpieczeń** | **Strefa czasowa** | Wybierz strefę czasowej, która ma być używana dla dat i godzin wyświetlanych w zdarzeniach, wykrytych zagrożeniach i zautomatyzowanego badania & korygowania. Możesz użyć czasu UTC lub lokalnej strefy czasowej (*zalecane*).  |
| **Microsoft 365 Defender** | **Konta** | Wyświetl szczegóły, takie jak miejsce przechowywania danych, identyfikator dzierżawy i identyfikator organizacji (organizacji). |
| **Microsoft 365 Defender**  | **Funkcje wersji zapoznawczej**  | Włącz funkcje w wersji zapoznawczej, aby wypróbować nadchodzące funkcje i nowe możliwości. Możesz być jednym z pierwszych, którzy chcą zapoznać się z nowymi funkcjami i przekazać opinię. |
| **Punkty końcowe**  | **Powiadomienia e-mail** | Skonfiguruj lub edytuj reguły powiadomień e-mail. Po wykryciu luk w zabezpieczeniach lub utworzeniu alertu adresaci określoni w regułach powiadomień e-mail otrzymają wiadomość e-mail. [Dowiedz się więcej o powiadomieniach e-mail](mdb-email-notifications.md). |
| **Punkty końcowe**   | **Zarządzanie urządzeniami** >  **Dołączania** | Dołączanie urządzeń do usługi Defender dla Firm przy użyciu skryptu do pobrania. Aby dowiedzieć się więcej, zobacz [Dołączanie urządzeń do Microsoft Defender dla Firm](mdb-onboard-devices.md).   |  
| **Punkty końcowe**  |  **Zarządzanie urządzeniami** >  **Odłączanie** | Odłączanie (usuwanie) urządzeń z usługi Defender dla Firm. Po odłączeniu urządzenia nie wysyła ono już danych do usługi Defender dla Firm, ale dane odebrane przed odłączeniem są zachowywane. Aby dowiedzieć się więcej, zobacz [Odłączanie urządzenia](mdb-onboard-devices.md#offboarding-a-device).  |

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
