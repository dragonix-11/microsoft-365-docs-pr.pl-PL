---
title: Microsoft 365 dla osób decyzyjnych w biznesie
description: Najbardziej typowe scenariusze zagrożeń i ataków napotykane obecnie przez organizacje w ich środowiskach Microsoft 365 oraz zalecane działania w celu ograniczania tego ryzyka.
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: johmar
audience: Admin
ms.topic: tutorial
ms.prod: m365-security
ms.technology: m365d
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
ms.openlocfilehash: 59b74fdc13cc21f0266e0f110935f76656827f65
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755176"
---
# <a name="microsoft-365-security-for-business-decision-makers-bdms"></a>Microsoft 365 dla osób decyzyjnych w biznesie

W tym artykule omówiono niektóre z najbardziej typowych scenariuszy zagrożeń i ataków napotykanych obecnie przez organizacje w ich środowiskach Microsoft 365, oraz omówiono zalecane działania w celu ograniczania tego ryzyka. Chociaż program Microsoft 365 oferuje szeroką gamę wstępnie skonfigurowanych funkcji zabezpieczeń, to także klient musi przejąć odpowiedzialność za zabezpieczanie tożsamości, danych i urządzeń używanych do uzyskiwania dostępu do usług w chmurze. Te wskazówki zostały opracowane przez Kozeta Beam (Microsoft Cloud Security Architect) i Thiagaraj Sundararajan (Starszy konsultant firmy Microsoft).

Ten artykuł jest uporządkowany według priorytetu pracy, począwszy od ochrony tych kont używanych do administrowania najważniejszymi usługami i zasobami, takimi jak dzierżawa, poczta e-mail i SharePoint. Stanowi ona metodyczną metodę na zbliżenie się do zabezpieczeń i współpracuje z następującym arkuszem kalkulacyjnym, dzięki czemu można śledzić postęp z uczestnikami projektu i zespołami w organizacji: Microsoft 365 dla arkusza kalkulacyjnego [BDMs](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Microsoft-365-BDM-security-recommendations-spreadsheet.xlsx).

:::image type="content" source="../downloads/microsoft-365-bdm-security-recommendations-spreadsheet-thumb.png" alt-text="Przykład arkusza informacyjnego Microsoft 365 zabezpieczeń BDM" lightbox="../downloads/microsoft-365-bdm-security-recommendations-spreadsheet-thumb.png":::

Firma Microsoft udostępnia w ramach twojej dzierżawy narzędzie Secure Score, które umożliwia automatyczne analizowanie stanu zabezpieczeń na podstawie zwykłych działań, przypisywanie wyników i przedstawianie zaleceń dotyczących poprawy zabezpieczeń. Przed podjęciem czynności zalecanych w tym artykule zanotuj swoje bieżące wyniki i zalecenia. Akcje zalecane w tym artykule zwiększą Twój wynik. Celem nie jest osiągnięcie maksymalnej liczby wyników, ale świadomość możliwości ochrony środowiska w sposób, który nie będzie miało negatywnego wpływu na wydajność pracy użytkowników. Zobacz [Microsoft Secure Score](defender/microsoft-secure-score.md).

:::image type="content" source="../media/security/security-for-bdms-overview.png" alt-text="Przykład narzędzia Secure Score, które zapewnia funkcje ochrony środowiska biznesowego w portalu Microsoft 365 Defender sieci Microsoft 365 Defender." lightbox="../media/security/security-for-bdms-overview.png":::

Jeszcze jedno przed rozpoczęciem . . . pamiętaj o [włączeniu dziennika inspekcji](../compliance/search-the-audit-log-in-security-and-compliance.md). Te dane będą potrzebne później na wypadek konieczności zbadania zdarzenia lub naruszenia.

## <a name="protect-privileged-accounts"></a>Ochrona kont z uprawnieniami

Pierwszym krokiem jest zapewnienie dodatkowej warstwy ochrony dla kluczowych kont w środowisku, ponieważ te konta mają dostęp i uprawnienia do zarządzania krytycznymi usługami i zasobami oraz zmieniania ich, co w przypadku naruszenia bezpieczeństwa może mieć negatywny wpływ na całą organizację. Ochrona kont uprzywilejowanych to jeden z najskuteczniejszych sposobów ochrony przed atakującym, który chce podnieść uprawnienia do naruszonego konta do konta administracyjnego.

|Zalecenie  |E3 |E5  |
|---------|---------|---------|
|Wymusz uwierzytelnianie wieloskładnikowe (MFA) dla wszystkich kont administracyjnych.|![zielony znacznik wyboru.](../media/green-check-mark.png)|![zielony znacznik wyboru.](../media/green-check-mark.png)|
|Zaimplikuj usługę Azure Active Directory (Azure AD) Privileged Identity Management (PIM), aby zastosować dostęp z uprawnieniami tylko na czas do zasobów usług Azure AD i Azure. Możesz również dowiedzieć się, kto ma dostęp do dostępu i kto ma uprawnienia do dostępu.|         | ![zielony znacznik wyboru.](../media/green-check-mark.png)|
|Implementowanie zarządzania dostępem z uprawnieniami w celu zarządzania szczegółową kontrolą dostępu nad zadaniami administratora z uprawnieniami w programie Office 365. |         | ![zielony znacznik wyboru.](../media/green-check-mark.png)|
|Konfigurowanie i używanie stacji roboczych programu Privileged Access (PAW) do administrowania usługami. Nie używaj tych samych stacji roboczych do przeglądania Internetu i sprawdzania wiadomości e-mail nie związanych z Twoim kontem administracyjnym.|  !![zielony znacznik wyboru.](../media/green-check-mark.png)|![zielony znacznik wyboru.](../media/green-check-mark.png)::: |

Na poniższym diagramie przedstawiono te możliwości.
:::image type="content" source="../media/m365-security-bdm-illustrations-privileged-accounts.png" alt-text="Przykład funkcji oferowanych przez narzędzia do ochrony kont z uprawnieniami" lightbox="../media/m365-security-bdm-illustrations-privileged-accounts.png":::

Dodatkowe zalecenia:

- Upewnij się, że konta synchronizowane lokalnie nie mają przypisanych ról administratora dla usług w chmurze. Pomaga to zapobiec stosowania kont lokalnych przez atakującego w celu uzyskania administracyjnego dostępu do usług w chmurze.
- Upewnij się, że do kont usługi nie przypisano ról administratora. Te konta często nie są monitorowane i ustawiane przy użyciu haseł, które nie wygasają. Zacznij od upewniania się, że konta usług AADConnect i ADFS nie są domyślnie administratorami globalnymi.
- Usuwanie licencji z kont administratora. O ile nie istnieje konkretny przypadek użycia w celu przypisania licencji do określonych kont administratora, usuń licencje z tych kont.

## <a name="reduce-the-surface-of-attack"></a>Zmniejszanie powierzchni ataków

Następny obszar fokusu zmniejsza obszar ataków. Można to osiągnąć przy minimalnym nakładzie pracy i wpływie na Twoich użytkowników i usługi. Przez zmniejszenie obszaru ataków atakujący mają mniej sposobów na rozpoczęcie ataków na Twoją organizację.

Oto kilka przykładów:

- Wyłącz protokoły POP3, IMAP i SMTP. Większość nowoczesnych organizacji nie używa już tych starszych protokołów. Możesz bezpiecznie wyłączyć te funkcje i zezwolić na wyjątki tylko w razie potrzeby.
- Ogranicz liczbę administratorów globalnych w dzierżawie do niezbędnego minimum. To bezpośrednio zmniejsza obszar ataków dla wszystkich aplikacji w chmurze.
- Wycofywanie serwerów i aplikacji, które nie są już używane w środowisku.
- Implementowanie procesu wyłączania i usuwania kont, które nie są już używane.

## <a name="protect-against-known-threats"></a>Ochrona przed znanymi zagrożeniami

Do znanych zagrożeń należą złośliwe oprogramowanie, naruszone konta i wyłudzanie informacji. Niektóre zabezpieczenia przed tymi zagrożeniami można szybko wdrożyć bez bezpośredniego wpływu na użytkowników, natomiast inne wymagają większej liczby szkoleń użytkowników i planowania.

|Zalecenie  |E3  |E5  |
|---------|---------|---------|
|**Skonfiguruj uwierzytelnianie wieloskładnikowe i użyj zalecanych zasad dostępu warunkowego, w tym zasad ryzyka logowania**. Firma Microsoft zaleca i przetestowała zestaw zasad, które współpracują ze sobą w celu ochrony wszystkich aplikacji w chmurze, w tym aplikacji Office 365 i Microsoft 365 internetowych. Zobacz [Konfiguracje tożsamości i dostępu do urządzeń](./office-365-security/microsoft-365-policies-configurations.md). | |![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Wymagaj uwierzytelniania wieloskładnikowego dla wszystkich użytkowników**. Jeśli nie masz licencji wymaganej do wdrożenia zalecanych zasad dostępu warunkowego, co najmniej wymaga uwierzytelniania wieloskładnikowego dla wszystkich użytkowników.|![zielony znacznik wyboru.](../media/green-check-mark.png)|![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Podnieś poziom ochrony przed złośliwym oprogramowaniem w wiadomościach e-mail**. Twoje Office 365 lub Microsoft 365 zawiera ochronę przed złośliwym oprogramowaniem, ale możesz zwiększyć tę ochronę, blokując załączniki za pomocą typów plików, które są często używane w celu ochrony przed złośliwym oprogramowaniem.|![zielony znacznik wyboru.](../media/green-check-mark.png)|![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Ochrona poczty e-mail przed atakami ukierunkowanych wyłudzania informacji**. Jeśli skonfigurowano co najmniej jedną domenę niestandardową dla środowiska Office 365 lub Microsoft 365, możesz skonfigurować ukierunkowaną ochronę przed wyłudzaniem informacji. Ochrona przed wyłudzaniem informacji, która jest częścią usługi Defender for Office 365, może pomóc chronić Twoją organizację przed atakami opartymi na złośliwych personifikacjach wyłudzających informacje i innymi atakami wyłudzania informacji. Jeśli nie skonfigurowano domeny niestandardowej, nie trzeba tego robić.| |![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Ochrona przed atakami oprogramowania wymuszającego okup w wiadomościach e-mail**. Oprogramowanie wymuszające okup zabiera dostęp do danych przez zaszyfrowanie plików lub zablokowanie ekranów komputera. Następnie próbuje wyłudzić pieniądze od osób, które szły na konto, prosząc o "ransom" zwykle w postaci banków, takich jak Waluty, w zamian za powrót dostępu do danych. Możesz pomóc chronić się przed oprogramowaniem wymuszającym okup, tworząc co najmniej jedną regułę przepływu poczty w celu blokowania rozszerzeń plików, które są często używane dla oprogramowania wymuszającego okup, lub ostrzeżenia dla użytkowników, którzy otrzymują te załączniki w wiadomościach e-mail.|![zielony znacznik wyboru.](../media/green-check-mark.png)|![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Blokuj połączenia z krajów, w których nie robisz interesów**. Utwórz zasady dostępu warunkowego usługi Azure AD w celu zablokowania połączeń pochodzących z tych krajów, co w praktyce utworzy zaporę geograficzną wokół Twojej dzierżawy.| |![zielony znacznik wyboru.](../media/green-check-mark.png)|

Na poniższym diagramie przedstawiono te możliwości.
:::image type="content" source="../media/m365-security-bdm-illustrations-known-threats.png" alt-text="Przykład różnych możliwości oferowanych przez narzędzia do ochrony przed zagrożeniami różnych typów" lightbox="../media/m365-security-bdm-illustrations-known-threats.png":::

## <a name="protect-against-unknown-threats"></a>Ochrona przed nieznanymi zagrożeniami

Po dodaniu dodatkowych zabezpieczeń do kont uprzywilejowanych i ochronie przed znanymi atakami możesz skupić się na ochronie przed nieznanymi zagrożeniami. Bardziej zdeterminowani i zaawansowani adwersiści korzystają z innowacyjnych i nowych, nieznanych metod ataków w organizacjach. Dzięki obszernej telemetrii danych zebranych przez ponad miliardy urządzeń, aplikacji i usług firmy Microsoft możemy wykonać usługę Defender dla systemu Office 365 w systemach Windows, Office 365 i Azure, aby zapobiegać atakom programu Zero-Day, korzystania ze środowisk skrzynki piasku oraz sprawdzać poprawność przed zezwoleniem na dostęp do zawartości.

|Zalecenie  |E3  |E5  |
|---------|---------|---------|
|**Skonfiguruj usługę Microsoft Defender dla Office 365**:<br>*Sejf załączników<br>* Sejf linków    <br>*Program Microsoft Defender for Endpoint for SharePoint, OneDrive, and Microsoft Teams<br>* Anti-phishing in Defender for Office 365 protection|         |![zielony znacznik wyboru.](../media/green-check-mark.png) |
|**Konfigurowanie programu Microsoft Defender na przykład w celu obsługi funkcji punktu końcowego**:<br>*<br>Program antywirusowy Windows Defender* exploit protection <br> *Zmniejszenie powierzchni ataków <br>*    Izolacji na podstawie sprzętu <br>* Kontrolowany dostęp do folderu     |         |![zielony znacznik wyboru.](../media/green-check-mark.png) |
|Odkryj aplikacje SaaS za pomocą programu **Microsoft Defender for Cloud Apps** i zacznij korzystać z analizy zachowania i wykrywania anomalii. |         |![zielony znacznik wyboru.](../media/green-check-mark.png) |

Na poniższym diagramie przedstawiono te możliwości.
:::image type="content" source="../media/m365-security-bdm-illustrations-unknown-threats.png" alt-text="Przykład funkcji oferowanych przez narzędzia do ochrony przed nieznanymi zagrożeniami" lightbox="../media/m365-security-bdm-illustrations-unknown-threats.png":::

Dodatkowe zalecenia:

- Zabezpieczanie komunikacji w kanałach partnerów, takich jak wiadomości e-mail, przy użyciu usługi TLS.
- Otwórz Teams tylko dla partnerów, z których się komunikujesz.
- Nie dodawaj domen nadawców, poszczególnych nadawców ani źródłowych adresów IP do listy adresów IP, ponieważ dzięki temu mogą one pomijać testy spamu i złośliwego oprogramowania — często klienci dodają własne zaakceptowane domeny lub wiele innych domen, w przypadku których problemy z przepływem poczty e-mail zostały zgłoszone do listy zezwalających. Nie dodawaj domen na liście Spam i Filtrowanie połączeń, ponieważ ta możliwość potencjalnie pomija wszystkie testy spamu.
- Włączanie powiadomień wychodzących o spamie — wewnętrzne włączanie powiadomień o spamie wychodzących do listy dystrybucyjnej do działu pomocy technicznej lub zespołu administracyjnego IT w celu zgłoszenia tego, czy któryś z użytkowników wewnętrznych wysyła wiadomości e-mail o spamie zewnętrznie. Może to oznaczać, że konto zostało naruszone.
- Wyłącz zdalny program PowerShell dla wszystkich użytkowników — zdalny program PowerShell jest używany głównie przez administratorów w celu uzyskiwania dostępu do usług administracyjnych lub programistycznych dostępów do interfejsu API. Zaleca się wyłączenie tej opcji użytkownikom niebędącym administratorem w celu uniknięcia ponownego rozesłania, o ile nie muszą oni mieć do niego dostępu.
- Zablokowanie dostępu do portalu Microsoft Azure zarządzaniem witrynami wszystkim administratorom, którzy nie są administratorami. Można to zrobić przez utworzenie reguły dostępu warunkowego w celu zablokowania wszystkich użytkowników (oprócz administratorów).

## <a name="assume-breach"></a>Założono naruszenie

Mimo że firma Microsoft podejmuje wszystkie możliwe środki w celu zapobiegania atakom i zagrożeniam, zalecamy, aby zawsze działać przy założeniu naruszenia zabezpieczeń. Nawet jeśli atakującemu udało się intruzować w środowisku, musimy upewnić się, że nie mogą oni eksfiltrować danych ani informacji o tożsamości ze środowiska. Z tego powodu zalecamy włączenie ochrony przed poufnymi wyciekami danych, takimi jak numery PESEL, numery kart kredytowych, inne informacje osobiste i inne informacje poufne na poziomie organizacji.


|Zalecenie |E3|E5 |
|---------|---------|---------|
|**Przeglądanie i optymalizowanie dostępu warunkowego oraz powiązanych zasad w celu zachowania kontroli nad bezbłędnym zaufaniem w sieci**. Ochrona przed znanymi zagrożeniami obejmuje implementowanie zestawu [zalecanych zasad](./office-365-security/microsoft-365-policies-configurations.md). Przejrzyj implementację tych zasad, aby upewnić się, że chronisz swoje aplikacje i dane przed hakerami, którzy uzyskali dostęp do Twojej sieci. Zalecane zasady ochrony aplikacji intune dla aplikacji Windows 10 umożliwiają Windows informacji (WIP). WIP chroni przed przypadkowymi wyciekami danych organizacji za pośrednictwem aplikacji i usług, takich jak poczta e-mail, media społecznościowe i publiczna chmura. |         |![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Wyłącz zewnętrzne przesyłanie dalej poczty e-mail**. Hakerzy, którzy uzyskają dostęp do skrzynki pocztowej użytkownika, mogą ukraść Twoją pocztę, ustawiając ją w celu automatycznego przesyłania dalej wiadomości e-mail. Może się to zdarzyć nawet bez wiedzy użytkownika. Możesz temu zapobiec, konfigurując regułę przepływu poczty.|![zielony znacznik wyboru.](../media/green-check-mark.png) |![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Wyłącz anonimowe udostępnianie kalendarza zewnętrznego**. Domyślnie jest dozwolone zewnętrzne anonimowe udostępnianie kalendarza. [Wyłącz udostępnianie kalendarza,](/exchange/sharing/sharing-policies/modify-a-sharing-policy) aby ograniczyć potencjalne wycieki poufnych informacji.|![zielony znacznik wyboru.](../media/green-check-mark.png) |![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Konfigurowanie zasad ochrony przed utratą danych w przypadku danych poufnych**. Utwórz zasady ochrony przed &amp; utratą danych w Centrum zgodności zabezpieczeń, aby odnajdować i chronić poufne dane, takie jak numery kart kredytowych, numery PESEL i numery kont bankowych. Microsoft 365 zawiera wiele wstępnie zdefiniowanych typów informacji poufnych, których można używać w zasadach ochrony przed utratą danych. Możesz również utworzyć własne typy informacji poufnych dla danych poufnych, które są niestandardowe w Twoim środowisku. |![zielony znacznik wyboru.](../media/green-check-mark.png)|![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Implementowanie zasad klasyfikacji danych i ochrony informacji**. Implementuj etykiety wrażliwości i używaj ich do klasyfikowania i stosowania ochrony do danych poufnych. Tych etykiet można również używać w zasadach ochrony przed utratą danych. Jeśli używasz etykiet usługi Azure Information Protection, zalecamy, aby nie tworzyć nowych etykiet w innych centrach aadministracyjnym.|         |![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Ochrona danych w aplikacjach i usługach innych firm za pomocą programu Defender dla aplikacji w chmurze**. Skonfiguruj zasady usługi Defender dla aplikacji w chmurze w celu ochrony poufnych informacji w aplikacjach chmurowych innych firm, takich jak Salesforce, Box Dropbox. Można używać typów informacji poufnych oraz etykiet wrażliwości utworzonych w programie Defender dla aplikacji w chmurze i stosować je we wszystkich aplikacjach SaaS. <br><br>Program Microsoft Defender dla aplikacji w chmurze umożliwia wymuszanie wielu zautomatyzowanych procesów. Zasady można skonfigurować tak, aby zapewniać ciągłe skanowanie zgodności, zadania zbierania elektronicznych materiałów dowodowych z przepisami, zasady DLP dotyczące poufnej zawartości udostępnianej publicznie i nie tylko. Usługa Defender for Cloud Apps może monitorować dowolny typ pliku w oparciu o ponad 20 filtrów metadanych (na przykład na poziomie dostępu, typ pliku). |         |![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Użyj [programu Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/information-protection-in-windows-overview), aby określić, czy użytkownicy przechowują poufne informacje na swoich Windows urządzeniach**. |         |![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Skaner [AIP umożliwia](/azure/information-protection/deploy-aip-scanner) identyfikowanie i klasyfikowanie informacji na serwerach i udziałach plików**. Użyj narzędzia do raportowania AIP, aby wyświetlić wyniki i podjąć odpowiednie działania.|         |![zielony znacznik wyboru.](../media/green-check-mark.png)|

Na poniższym diagramie przedstawiono te możliwości.
![Zalecane funkcje ochrony przed naruszeniem zabezpieczeń.](../media/m365-security-bdm-illustrations-assume-breach.png)
 :::image type="content" source="../media/m365-security-bdm-illustrations-assume-breach.png" alt-text="Przykład funkcji oferowanych przez narzędzie do ochrony przed naruszeniem" lightbox="../media/m365-security-bdm-illustrations-assume-breach.png":::

## <a name="continuous-monitoring-and-auditing"></a>Ciągłe monitorowanie i inspekcja

Wreszcie, ciągłe monitorowanie i inspekcja środowiska Microsoft 365 wraz ze środowiskiem Windows i urządzeniami ma kluczowe znaczenie dla szybkiego wykrywania i korygowania wszelkich łamania zabezpieczeń. Narzędzia, takie jak Secure Score, portal Microsoft 365 Defender i zaawansowana analiza zaawansowana usługi Microsoft Intelligent Graph, zapewniają nieocenione informacje w dzierżawie i łącz olbrzymie ilości danych analizy zagrożeń i zabezpieczeń w celu zapewnienia Ci wyjątkowej ochrony i wykrywania zagrożeń.

|Zalecenie |E3 |E5 |
|---------|---------|---------|
|Upewnij się **, że dziennik inspekcji** jest włączony.|![zielony znacznik wyboru.](../media/green-check-mark.png)|![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**Tygodniowy przegląd wyników** bezpiecznego — secure score to centralna lokalizacja do uzyskiwania dostępu do stanu zabezpieczeń firmy i podjęcia działań na podstawie rekomendacji dotyczących wyników bezpiecznego. Takie sprawdzanie zaleca się przeprowadzać co tydzień.|![zielony znacznik wyboru.](../media/green-check-mark.png)|![zielony znacznik wyboru.](../media/green-check-mark.png)|
|Użyj **programu Microsoft Defender, Office 365** narzędzi:<br>*Możliwości analizy zagrożeń i reakcji<br>*    Zautomatyzowane badanie i odpowiedź |         |![zielony znacznik wyboru.](../media/green-check-mark.png)|
|Użyj **programu Microsoft Defender dla punktu końcowego**:<br> *[Wykrywanie punktu końcowego i odpowiedź](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response) <br>*    Zautomatyzowany wynik bezpiecznego badania i rozwiązywania problemów <br>*    [Zaawansowane łowy](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview) <br>|         |![zielony znacznik wyboru.](../media/green-check-mark.png)|
|Za **pomocą usługi Microsoft Defender for Cloud Apps** wykrywaj nietypowe zachowanie w aplikacjach w chmurze w celu identyfikowania oprogramowania wymuszającego okup, naruszonych użytkowników lub aplikacji rogu, analizowania użycia wysokiego ryzyka i automatycznego rozwiązywania problemów w celu ograniczenia ryzyka dla Twojej organizacji.|         |:::image type="content" source="../media/green-check-mark.png" alt-text="Przykład zielonego, kolorowego znacznika wyboru" lightbox="../media/green-check-mark.png":::|
|Korzystaj **z programu Microsoft Sentinel** lub bieżącego narzędzia SIEM, aby monitorować zagrożenia w Twoim środowisku. |         |![zielony znacznik wyboru.](../media/green-check-mark.png)|
|**[Wdróż usługę Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp)** w celu monitorowania i ochrony przed zagrożeniami skierowanymi do lokalnego środowiska usługi Active Directory.   |         |![zielony znacznik wyboru.](../media/green-check-mark.png) |
|Usługa **Microsoft Defender dla chmury** monitoruje zagrożenia w obciążeniach hybrydowymi i chmurowych. Usługa Microsoft Defender dla chmury zawiera bezpłatną warstwę możliwości i standardową warstwę możliwości opłacaną w oparciu o godziny pracy zasobów lub transakcje.|         |         |

Na poniższym diagramie przedstawiono te możliwości.
:::image type="content" source="../media/m365-security-bdm-illustrations-monitoring-auditing.png" alt-text="Przykład funkcji oferowanych przez te narzędzia w celu umożliwienia ochrony i wykrywania zagrożeń" lightbox="../media/m365-security-bdm-illustrations-monitoring-auditing.png":::

Zalecane najważniejsze działania monitorujące:

- **Tygodniowy przegląd wyników** bezpiecznego firmy Microsoft — wynik bezpiecznego to centralna lokalizacja do uzyskiwania dostępu do stanu zabezpieczeń dzierżawy i do podjęcia działań na podstawie najlepszych zaleceń. Takie sprawdzanie zaleca się przeprowadzać co tydzień. Secure Score obejmuje zalecenia dotyczące usług Azure AD, Intune, Defender for Cloud Apps i Microsoft Defender for Endpoint, a także Office 365.
- **Przeglądanie ryzykownych logowań co tydzień** — korzystaj z centrum administracyjnego usługi Azure AD, aby co tydzień przeglądać ryzykowne logowania. Zalecane reguły dostępu do urządzenia i tożsamości obejmują zasady wymuszania zmiany hasła podczas ryzykownych logowania.  
-  Przejrzyj co tydzień najważniejsze złośliwe oprogramowanie i wyłudzeni użytkownicy — użyj programu Microsoft Office 365 Defender dla Eksploratora zagrożeń, aby przejrzeć użytkowników, którzy są docelowi za pomocą złośliwego oprogramowania i wyłudzeni informacji, oraz dowiedzieć się, jaka jest główna przyczyna tego wpływu na tych użytkowników.
