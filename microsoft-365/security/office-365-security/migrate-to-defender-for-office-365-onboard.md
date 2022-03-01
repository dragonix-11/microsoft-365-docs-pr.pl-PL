---
title: 'Migrowanie do programu Microsoft Defender Office 365 etap 3. etap: wsad'
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: migrationguides
description: Wykonaj kroki migracji z usługi lub urządzenia innej firmy do programu Microsoft Defender w celu Office 365 ochrony.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3798bdb28bb44b5148574b4c09a372ff564e47e5
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/02/2022
ms.locfileid: "63009827"
---
# <a name="migrate-to-microsoft-defender-for-office-365---phase-3-onboard"></a>Migrowanie do usługi Microsoft Defender dla Office 365 — Etap 3. Etap: wsuń

**Dotyczy**
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)

<br>

|[![Etap 1. Przygotowanie.](../../media/phase-diagrams/prepare.png)](migrate-to-defender-for-office-365-prepare.md) <br> [Etap 1. Przygotowywanie](migrate-to-defender-for-office-365-prepare.md)|[![Etap 2. Konfigurowanie.](../../media/phase-diagrams/setup.png)](migrate-to-defender-for-office-365-setup.md) <br> [Etap 2. Konfigurowanie](migrate-to-defender-for-office-365-setup.md)|![Etap 3. Wsad.](../../media/phase-diagrams/onboard.png) <br> Etap 3. Wniesienie|
|---|---|---|
|||*Jesteś tutaj!*|

Etap **3 : Etap 3: Etap** migracji do programu **[Microsoft Defender dla](migrate-to-defender-for-office-365.md#the-migration-process)** Office 365! Ten etap migracji obejmuje następujące kroki:

1. [Rozpoczynanie dołączania do Teams](#step-1-begin-onboarding-security-teams)
2. [(Opcjonalnie) Wykluczanie użytkowników pilotażowych z filtrowania według istniejącej usługi ochrony](#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service)
3. [Dostosowywanie spoof intelligence](#step-3-tune-spoof-intelligence)
4. [Dostosowywanie ochrony personifikacji i analizy skrzynki pocztowej](#step-4-tune-impersonation-protection-and-mailbox-intelligence)
5. [Używanie danych  przysyłanych przez użytkowników do mierzenia i dostosowania](#step-5-use-data-from-user-submissions-to-measure-and-adjust)
6. [(Opcjonalnie) Dodawanie kolejnych użytkowników do pilotażu i iteratu](#step-6-optional-add-more-users-to-your-pilot-and-iterate)
7. [Rozszerzanie Microsoft 365 na wszystkich użytkowników i wyłączanie reguły przepływu poczty SCL=-1](#step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule)
8. [Przełączanie rekordów MX](#step-8-switch-your-mx-records)

## <a name="step-1-begin-onboarding-security-teams"></a>Krok 1. Rozpoczęcie dołączania do Teams

Jeśli Twoja organizacja ma zespół odpowiedzi zabezpieczeń, na tym czas zacząć integrację usługi Microsoft Defender for Office 365 z procesami reakcji, w tym z systemami biletowymi. To cały temat, ale czasami jest przeoczył. Wczesne przygotowanie zespołu reagowania na zabezpieczenia zapewni gotowość Twojej organizacji do reagowania na zagrożenia podczas przełączania rekordów MX. Aby reagowanie na incydenty było potrzebne do obsługi następujących zadań:

- Poznaj nowe narzędzia i zintegruj je z istniejącymi przepływami. Przykład:
  - Ważne jest zarządzanie kwarantanną wiadomości przez administratora. Aby uzyskać instrukcje, zobacz [Zarządzanie wiadomościami i plikami poddanymi kwarantannie jako administrator](manage-quarantined-messages-and-files.md).
  - Śledzenie wiadomości pozwala zobaczyć, co się stało z wiadomościami podczas ich wprowadzania lub Microsoft 365. Aby uzyskać więcej informacji, zobacz [Śledzenie wiadomości w nowoczesnym centrum administracyjnym usługi Exchange w programie Exchange Online](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac).
- Identyfikuj czynniki ryzyka, które zostały wpusz ich do organizacji.
- Dostosowywanie alertów [dla](../../compliance/alert-policies.md) procesów organizacyjnych.
- Zarządzanie kolejką zdarzeń i rozwiązywanie potencjalnych zagrożeń.

Jeśli Twoja organizacja zakupiła usługę Microsoft Defender dla systemu Office 365 Plan 2, powinna zacząć zaznajomić się z funkcjami, takimi jak Eksplorator zagrożeń, łowiectwo zaawansowane i zdarzenia. Aby uzyskać odpowiednie szkolenia, zobacz <https://aka.ms/mdoninja>.

Jeśli zespół odpowiedzi zabezpieczeń zbiera i analizuje niefiltrowane wiadomości, możesz skonfigurować skrzynkę pocztową usługi SecOps w celu odbierania tych niefiltrowanych wiadomości. Aby uzyskać instrukcje, [zobacz Konfigurowanie skrzynek pocztowych usługi SecOps w zaawansowanych zasadach dostarczania](configure-advanced-delivery.md#use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy).

### <a name="siemsoar"></a>SIEM/SOAR

Aby uzyskać więcej informacji na temat integracji ze swoim SIEM/SOAR, zobacz następujące artykuły:

- [Omówienie Microsoft 365 Defender API](/microsoft-365/security/defender/api-overview)
- [Interfejs API przesyłania strumieniowego](/microsoft-365/security/defender/streaming-api)
- [Zaawansowany interfejs API łowiectwo](/microsoft-365/security/defender/api-advanced-hunting)
- [Interfejsy API zdarzeń](/microsoft-365/security/defender/api-incident)

Jeśli Twoja organizacja nie ma zespołu reagowania na zabezpieczenia ani nie ma istniejących przepływów procesu, możesz użyć tego czasu, aby zapoznać się z podstawowymi funkcjami łowy i odpowiedzi w programie Defender for Office 365. Aby uzyskać więcej informacji, zobacz [Badanie zagrożeń i odpowiedź na nie](office-365-ti.md).

### <a name="rbac-roles"></a>Role RBAC

Uprawnienia usługi Defender dla Office 365 są oparte na kontroli dostępu opartej na rolach (RBAC, role based access control) i wyjaśniono je w tece Uprawnienia Microsoft 365 Defender [portalu](permissions-microsoft-365-security-center.md). Oto ważne kwestie, o których należy pamiętać:

- Role usługi Azure AD nadawaj uprawnienia **wszystkim obciążeniam** pracą w Microsoft 365. Jeśli na przykład dodasz użytkownika do administratora zabezpieczeń w portalu Azure Portal, będzie miał uprawnienia Administratora zabezpieczeń wszędzie.
- Poczta & e-mail w portalu Microsoft 365 Defender nadać uprawnienia do portalu Microsoft 365 Defender, centrum Centrum zgodności platformy Microsoft 365 i starszego Centrum zgodności & zabezpieczeń. Jeśli na przykład dodasz użytkownika do administratora zabezpieczeń w portalu Microsoft 365 Defender, będzie miał dostęp administrator zabezpieczeń tylko w portalu Microsoft 365 Defender, portalu  usługi Centrum zgodności platformy Microsoft 365 oraz centrum zabezpieczeń i zgodności &. Wyśrodkuj.
- Wiele funkcji w portalu Microsoft 365 Defender jest opartych na poleceniach cmdlet programu Exchange Online PowerShell i dlatego wymaga członkostwa w grupach ról w odpowiadających im rolach (technicznie, grupach ról) w programie Exchange Online (w szczególności w celu uzyskania dostępu do odpowiednich Exchange Online  Polecenia cmdlet programu PowerShell).
- W portalu Microsoft 365 Defender w usłudze & są dostępne role współpracy z innymi użytkownikami poczty e-mail, które nie są równoważne z rolami usługi Azure AD i są ważne w przypadku operacji zabezpieczeń (na przykład rola Podgląd oraz rola Wyszukiwanie i przeczyszczanie).

Zazwyczaj tylko podzbiór pracowników ochrony będzie potrzebować dodatkowych praw do pobierania wiadomości bezpośrednio ze skrzynek pocztowych użytkowników. Wymaga to dodatkowych uprawnień, które domyślnie nie są dostępne w czytniku zabezpieczeń.

## <a name="step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service"></a>Krok 2. (Opcjonalnie) Wykluczanie użytkowników pilotażowych z filtrowania według istniejącej usługi ochrony

Mimo że ten krok nie jest wymagany, rozważ skonfigurowanie użytkowników pilotażowych tak, aby pomijali filtrowanie według istniejącej usługi ochrony. Ta akcja umożliwia ułaścicieli Office 365 obsługę wszystkich  obowiązków w zakresie filtrowania i ochrony w przypadku użytkowników pilotażowych. Jeśli nie wykluczono użytkowników pilotażowych z istniejącej usługi ochrony, usługa Defender for Office 365 efektywnie działa tylko w przypadku nieodebranych informacji z innej usługi (filtrowanie wiadomości, które już zostały odfiltrowane).

> [!NOTE]
> Ten krok jest jawnie wymagany, jeśli bieżąca usługa ochrony udostępnia zawijanie linków, ale chcesz pilotażować Sejf linki. Podwójne zawijanie linków nie jest obsługiwane.

## <a name="step-3-tune-spoof-intelligence"></a>Krok 3. Dostosowywanie spoof intelligence

Sprawdź szczegółowe [informacje dotyczące](learn-about-spoof-intelligence.md) fałszowania, aby zobaczyć, co jest dozwolone lub blokowane jako fałszowanie, oraz określić, czy musisz zastąpić werdykt systemu w celu fałszowania. Niektóre źródła krytycznej dla firmy poczty e-mail mogły niepoprawnie skonfigurować rekordy uwierzytelniania poczty e-mail w systemie DNS (SPF, DKIM i DMARC) i być może używasz zastępować w istniejącej usłudze ochrony do maskowania problemów z domenami.

Fałszywa inteligencja może pomóc w rozróżnianiu poczty e-mail z domen bez odpowiednich rekordów uwierzytelniania wiadomości e-mail w systemie DNS, ale ta funkcja czasami wymaga pomocy w odróżnianiu prawidłowego spoofingu od podszywania się pod niego. Koncentruj się na następujących typach źródeł wiadomości:

- Źródła wiadomości spoza zakresów adresów IP zdefiniowanych w [rozszerzonym filtrowaniu łączników](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).
- Źródła wiadomości, które mają największą liczbę wiadomości.
- Źródła wiadomości, które mają największy wpływ na organizację.

Po skonfigurowaniu przesyłania użytkowników zostanie w końcu dostrajanie samej analizy podszywające się pod siebie, więc nie trzeba chcieć się chcieć.

## <a name="step-4-tune-impersonation-protection-and-mailbox-intelligence"></a>Krok 4. Dostosowywanie ochrony personifikacji i analizy skrzynki pocztowej

Po wystarczająco dużo czasu na obserwowanie wyników ochrony przed personifikacji w trybie Nie zastosuj żadnego trybu akcji, możesz włączyć osobno każdą akcję ochrony przed personifikacji w zasadach ochrony przed wyłudzaniem informacji:

- Ochrona personifikacji użytkownika: **poddaj wiadomość kwarantannie** zarówno dla ustawienia Standardowa, jak i Ściśle.
- Ochrona personifikacji domeny: **poddaj wiadomość** kwarantannie zarówno dla standardowego, jak i ścisłego.
- Ochrona skrzynki pocztowej: Przenieś wiadomości do folderów wiadomości-śmieci adresatów **w standardzie** ; **Poddaj wiadomość kwarantannie** na ścisłe.

Im dłużej jest monitorowana ochrona przed personifikacjami, tym więcej danych będzie wymagało zidentyfikowania wymaganych zezwalań lub bloków. Rozważ zastosowanie opóźnienia między włączeniem każdej ochrony, która jest wystarczająco istotna, aby umożliwić obserwowanie i dopasowanie.

> [!NOTE]
> Częste i ciągłe monitorowanie i dostosowywanie tych zabezpieczeń jest ważne. Jeśli podejrzewasz wynik fałszywie dodatni, zbadaj przyczynę i użyj funkcji zastępowania tylko w razie potrzeby i tylko dla funkcji wykrywania, która tego wymaga.

### <a name="tune-mailbox-intelligence"></a>Dostosowywanie analizy skrzynek pocztowych

Mimo że w analizie skrzynek pocztowych skonfigurowano, aby nie podejmować żadnych działań w związku z wiadomościami, które zostały określone jako próby personifikacji [, została](impersonation-insight.md) ona w nim wniesiona i poznała wzorce wysyłania i odbierania wiadomości e-mail użytkowników pilotażowych. Jeśli użytkownik zewnętrzny ma kontakt z jednym z użytkowników pilotażowych, wiadomości od tego użytkownika zewnętrznego nie zostaną zidentyfikowane jako próby personifikacji przez analizę skrzynki pocztowej (co zmniejsza wartość wyników fałszywie dodatnich).

Gdy wszystko będzie gotowe, wykonaj następujące czynności, aby umożliwić działanie analizy skrzynki pocztowej na wiadomości wykryte jako próby personifikacji:

- W zasadach ochrony przed wyłudzaniem informacji przy użyciu ustawień Standardowa ochrona zmień  wartość Jeśli inteligencja skrzynek pocztowych wykryje spersonifikowanego użytkownika, a następnie przenieś wiadomość do folderów wiadomości-śmieci **adresatów**.

- W zasadach ochrony przed wyłudzaniem informacji z ustawieniami ścisłej ochrony zmień  wartość w te sposób: Jeśli inteligencja skrzynek pocztowych wykryje i podszyje się pod użytkownika, z poddaj wiadomość **kwarantannie**.

Aby zmodyfikować zasady, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w programie Defender dla Office 365](configure-mdo-anti-phishing-policies.md).

Po obserwowaniu wyników i wróceniu jakichkolwiek zmian przejdź do następnej sekcji w celu kwarantanny wiadomości wykrytych przez personifikację użytkownika.

### <a name="tune-user-impersonation-protection"></a>Dostosowywanie ochrony personifikacji użytkownika

W obu zasadach ochrony przed wyłudzaniem informacji na podstawie ustawień standardowych i ścisłych zmień wartość  ustawienia Jeśli wiadomość zostanie wykryta jako personifikowany użytkownik, w celu poddaj wiadomości **kwarantannie**.

Sprawdź szczegółowe [informacje o personifikacji](impersonation-insight.md) , aby zobaczyć, co jest blokowane w przypadku prób personifikacji użytkownika.

Aby zmodyfikować zasady, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w programie Defender dla Office 365](configure-mdo-anti-phishing-policies.md).

Po obserwowaniu wyników i wreguleniu przejdź do następnej sekcji w celu kwarantanny wiadomości wykrytych przez personifikację domeny.

### <a name="tune-domain-impersonation-protection"></a>Dostosowywanie ochrony personifikacji domeny

W obu zasadach ochrony przed wyłudzaniem informacji opartych na ustawieniach standardowych i ścisłych  zmień wartość ustawienia Jeśli wiadomość zostanie wykryta jako spersonifikowana domena, w celu poddaj wiadomość **kwarantannie**.

Sprawdź szczegółowe [informacje o personifikacji](impersonation-insight.md) , aby zobaczyć, co jest blokowane w przypadku prób personifikacji domeny.

Aby zmodyfikować zasady, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w programie Defender dla Office 365](configure-mdo-anti-phishing-policies.md).

Sprawdź wyniki i w razie potrzeby wprowadzić odpowiednie zmiany.

## <a name="step-5-use-data-from-user-submissions-to-measure-and-adjust"></a>Krok 5. Używanie danych z przesyłania użytkowników do mierzenia i dostosowania

Gdy użytkownicy pilotażowi zgłaszają wyniki fałszywie dodatnie i fałszywie ujemne, wiadomości będą wyświetlane na stronie Przesyłanie w Microsoft 365 Defender [sieci Web](admin-submission.md). Błędniezidentyfikowane wiadomości można zgłosić do firmy Microsoft w celu analizy, a następnie, w razie potrzeby, za pomocą tych informacji, dostosować ustawienia i wyjątki w ramach zasad pilotażowych.

Aby monitorować ustawienia ochrony i iterować ustawienia ochrony w programie Defender for Office 365, użyj następujących Office 365:

- [Kwarantanna](manage-quarantined-messages-and-files.md)
- [Eksplorator zagrożeń](email-security-in-microsoft-defender.md)
- [Raporty zabezpieczeń poczty e-mail](view-email-security-reports.md)
- [Defender for Office 365 reports](view-reports-for-mdo.md)
- [Szczegółowe informacje dotyczące przepływu poczty e-mail](/exchange/monitoring/mail-flow-insights/mail-flow-insights)
- [Raporty przepływu poczty e-mail](/exchange/monitoring/mail-flow-reports/mail-flow-reports)

Jeśli w raportach użytkowników organizacja korzysta z usługi innej firmy, możesz zintegrować te dane z pętlą opinii.

## <a name="step-6-optional-add-more-users-to-your-pilot-and-iterate"></a>Krok 6. (Opcjonalnie) Dodawanie kolejnych użytkowników do pilotażu i iteratu

Po odnalezieniu i naprawieniu problemów możesz dodać kolejnych użytkowników do grup pilotażowych (a następnie wykluczć tych nowych użytkowników pilotażowych z możliwości skanowania za pomocą istniejącej usługi ochrony, jeśli to konieczne). Im więcej testów przejmiesz teraz, tym mniej problemów użytkowników, których trzeba będzie zająć się później. Ta "kaskadowa" metoda dostosowywania jest dostosowana do większych części organizacji i zapewnia zespołom zabezpieczeń czas na dostosowanie się do nowych procesów i narzędzi.

- Microsoft 365 generuje alerty, gdy wiadomości służące do wyłudzania informacji w dużej pewności są dozwolone przez zasady organizacji. Aby zidentyfikować te wiadomości, dostępne są następujące opcje:
  - Zastępuje raport o [stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report).
  - Filtruj w Eksploratorze zagrożeń, aby zidentyfikować wiadomości.
  - Filtruj w zaawansowanym chłonie w celu zidentyfikowania wiadomości.

  Zgłaszanie wyników fałszywie dodatnich firmie Microsoft tak wcześnie, jak to możliwe za pośrednictwem przesyłania przez administratora, użyj funkcji Listy zezwalania [/](tenant-allow-block-list.md) blokowania dzierżawy, aby skonfigurować bezpieczne zastępowanie wyników fałszywie dodatnich.

- Warto również zbadać niepotrzebne zastępowanie. Innymi słowy przyjrzyj się werdyktom, które Microsoft 365 zostałyby podane w wiadomościach. Jeśli usługa Microsoft365 renderowała poprawny werdykt, konieczność zastępowania znacznie się zmniejsza lub jest usuwana.

## <a name="step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule"></a>Krok 7. Rozszerzanie Microsoft 365 o wszystkich użytkowników i wyłączanie reguły przepływu poczty SCL=-1

Wykonaj czynności opisane w tej sekcji, gdy wszystko będzie gotowe do przełączenia rekordów MX w celu Microsoft 365.

1. Rozszerz zasady pilotażowe na całą organizację. Istnieją różne sposoby na to:
   - Użyj [wstępnie ustawionych zasad](preset-security-policies.md) zabezpieczeń i podziel użytkowników między profil Ochrony standardowej i Profil ścisłej ochrony (upewnij się, że ochrona obejmuje wszystkie osoby). Wstępnie ustawione zasady zabezpieczeń są stosowane przed dowolnymi utworzonymi przez Ciebie zasadami niestandardowymi lub domyślnymi. Możesz wyłączyć poszczególne zasady pilotażowe bez ich usuwania.

     Wadą wstępnie ustawionych zasad zabezpieczeń jest to, że po ich utworzeniu nie można zmienić wielu ważnych ustawień.

   - Zmień zakres zasad utworzonych i dostosowanych podczas pilotażu, tak aby uwzględnić wszystkich użytkowników (na przykład wszystkich adresatów we wszystkich domenach). Pamiętaj, że jeśli do tego samego użytkownika ma zastosowanie wiele zasad tego samego typu (na przykład zasady ochrony przed wyłudzaniem informacji) (indywidualnie, według członkostwa w grupie lub domeny poczty e-mail), zostaną zastosowane tylko ustawienia zasad o najwyższym priorytecie (numer o najniższym priorytecie) i zatrzymanie przetwarzania dla tego typu zasad.

2. Wyłącz regułę przepływu poczty SCL=-1 (możesz ją wyłączyć bez jej usuwania).

3. Sprawdź, czy poprzednie zmiany zostały wprowadzone i czy program Defender dla systemu Office 365 jest teraz poprawnie włączony dla wszystkich użytkowników. Obecnie wszystkie funkcje ochrony usługi Defender dla systemu Office 365 mogą działać na pocztę dla wszystkich adresatów, ale ta poczta została już przeskanowana przez istniejącą usługę ochrony.

Na tym etapie możesz wstrzymać rejestrowanie i dostosowywanie danych na dużą skalę.

## <a name="step-8-switch-your-mx-records"></a>Krok 8. Przełączanie rekordów MX

> [!NOTE]
>
> - Gdy przełączasz rekord MX dla swojej domeny, propagacja zmian w Internecie może potrwać do 48 godzin.
>
> - Zalecamy obniżenie wartości TTL rekordów DNS, aby umożliwić szybszą odpowiedź i możliwe wycofywanie (jeśli jest to wymagane). Po zakończeniu i zweryfikowaniu przełączenia możesz przywrócić pierwotną wartość TTL.
>
> - Należy rozważyć rozpoczęcie od zmiany rzadziej używanych domen. Możesz wstrzymywać i monitorować przed przejściem do większych domen. Jednak nawet wtedy należy się upewnić, że wszyscy użytkownicy i domeny są objęci zasadami, ponieważ pomocnicze domeny SMTP są rozpoznawane jako domeny podstawowe przed aplikacją zasad.
>   
> - Wiele rekordów MX dla jednej domeny będzie działać technicznie, co pozwala na rozsyłanie dzielone, o ile zostały one dostarczone zgodnie ze wszystkimi wskazówkami w tym artykule. W szczególności należy upewnić się, że zasady są stosowane do wszystkich użytkowników, że reguła przepływu poczty SCL=-1 jest stosowana tylko do poczty przechodzącej przez istniejącą usługę ochrony zgodnie z opisem w Kroku konfiguracji 3. Obsługa lub tworzenie reguły przepływu poczty [SCL=-1](migrate-to-defender-for-office-365-setup.md#step-3-maintain-or-create-the-scl-1-mail-flow-rule). Taka konfiguracja wprowadza jednak zachowanie, które znacznie utrudnia rozwiązywanie problemów, dlatego zwykle nie jest to zalecane, szczególnie przez dłuższy czas.
>
> - Przed przełączeniem rekordów MX upewnij się, że na łączniku ruchu przychodzącego nie włączono następujących ustawień z usługi ochrony do Microsoft 365. Zazwyczaj łącznik ma skonfigurowane co najmniej jedno z następujących ustawień:
>
>   - **i wymagać, aby nazwa** podmiotu w certyfikacie używanym przez partnera do uwierzytelniania w umacie Office 365 była taka sama jak nazwa domeny (*RestrictDomainsToCertificate*)
>   - **Odrzucanie wiadomości e-mail, jeśli nie są wysyłane z tego zakresu adresów IP** (*RestrictDomainsToIPAddresses*)
>
>   Jeśli typ łącznika to **Partner** i oba te ustawienia są włączone, po przełączeniu rekordów MX dostarczenie poczty do Twoich domen nie powiedzie się. Przed kontynuowaniem musisz wyłączyć te ustawienia. Jeśli łącznik jest łącznikiem lokalnym używanym na potrzeby środowiska hybrydowego, nie musisz modyfikować łącznika lokalnego. Możesz jednak sprawdzić obecność łącznika **partnera** .
>   
> - Jeśli bieżąca brama poczty również zapewnia sprawdzanie poprawności adresatów, warto sprawdzić, czy domena jest skonfigurowana jako [autorytatywna](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) w programie Microsoft 365. Może to zapobiegać niepotrzebnym wiadomościom odsyłki.

Gdy wszystko będzie gotowe, przełącz rekord MX dla swoich domen. Możesz przeprowadzić migrację wszystkich domen jednocześnie. Możesz też najpierw przeprowadzić migrację rzadziej używanych domen, a następnie zmigrować pozostałe.

Zachęcamy do wstrzymywania i oceniania w dowolnym momencie. Ale pamiętaj: po wyłączenie reguły przepływu poczty SCL=-1 użytkownicy mogą mieć dwa różne sposoby sprawdzania wyników fałszywie dodatnich. Im szybciej zapewnisz pojedyncze, spójne środowisko, tym szczęśliwsi użytkownicy i zespoły pomocy technicznej będą w stanie rozwiązać problem z brakującą wiadomością.

## <a name="next-steps"></a>Następne kroki

Gratulacje! Ukończono migrację do [usługi Microsoft Defender dla systemu Office 365](migrate-to-defender-for-office-365.md#the-migration-process)! Ponieważ zostały one opisane w tym przewodniku migracji, pierwsze kilka dni, w których poczta jest dostarczana bezpośrednio Microsoft 365 powinna być znacznie płynniejsze.

Teraz rozpoczynasz normalną operację i konserwację usługi Defender dla systemu Office 365. Monitoruj i obserwuj, czy problemy są podobne do tych, które wystąpiły podczas pilotażu, ale na większą skalę. Analiza [fałszerska](learn-about-spoof-intelligence.md) i analiza [personifikacji](impersonation-insight.md) będą najbardziej pomocne, ale rozważ regularne wykonywanie następujących działań:

- Przeglądanie przesyłania użytkowników, zwłaszcza wiadomości [wyłudzających informacje zgłoszonych przez użytkowników](https://docs.microsoft.com/microsoft-365/security/office-365-security/automated-investigation-response-office)
- Przesłonięcia recenzji w [raporcie o stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report).
- Użyj [zapytania wyszukiwania zaawansowanego](/microsoft-365/security/defender/advanced-hunting-example) , aby szukać możliwości i ryzykownych wiadomości.
