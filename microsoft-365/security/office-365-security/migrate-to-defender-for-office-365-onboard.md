---
title: 'Migrowanie do fazy 3 Ochrona usługi Office 365 w usłudze Microsoft Defender: dołączanie'
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
description: Wykonaj kroki migracji z usługi ochrony innej firmy lub urządzenia w celu Ochrona usługi Office 365 w usłudze Microsoft Defender ochrony.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b2358103b3ab6bfee34e88d23f4b3de0d774e34e
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66492131"
---
# <a name="migrate-to-microsoft-defender-for-office-365---phase-3-onboard"></a>Migrowanie do Ochrona usługi Office 365 w usłudze Microsoft Defender — faza 3: dołączanie

**Dotyczy**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)

<br>

|[![Faza 1. Przygotowanie.](../../media/phase-diagrams/prepare.png#lightbox)](migrate-to-defender-for-office-365-prepare.md) <br> [Faza 1. Przygotowanie](migrate-to-defender-for-office-365-prepare.md)|[![Faza 2. Konfigurowanie.](../../media/phase-diagrams/setup.png#lightbox)](migrate-to-defender-for-office-365-setup.md) <br> [Faza 2. Konfiguracja](migrate-to-defender-for-office-365-setup.md)|![Faza 3. Dołączanie.](../../media/phase-diagrams/onboard.png) <br> Faza 3. Dołączenie|
|---|---|---|
|||*Jesteś tutaj!*|

Witamy w **fazie 3: dołączanie** **[migracji do Ochrona usługi Office 365 w usłudze Microsoft Defender](migrate-to-defender-for-office-365.md#the-migration-process)**! Ta faza migracji obejmuje następujące kroki:

1. [Rozpoczynanie dołączania zespołów zabezpieczeń](#step-1-begin-onboarding-security-teams)
2. [(Opcjonalnie) Wykluczenie użytkowników pilotażowych z filtrowania według istniejącej usługi ochrony](#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service)
3. [Dostrajanie inteligencji fałszowania](#step-3-tune-spoof-intelligence)
4. [Dostrajanie ochrony przed personifikacją i analizy skrzynek pocztowych](#step-4-tune-impersonation-protection-and-mailbox-intelligence)
5. [Mierzenie i dostosowywanie danych przesyłanych przez użytkowników przy użyciu danych przesyłanych przez użytkownika](#step-5-use-data-from-user-submissions-to-measure-and-adjust)
6. [(Opcjonalnie) Dodawanie większej liczby użytkowników do pilotażu i iterowanie](#step-6-optional-add-more-users-to-your-pilot-and-iterate)
7. [Rozszerzanie ochrony platformy Microsoft 365 na wszystkich użytkowników i wyłączanie reguły przepływu poczty SCL=-1](#step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule)
8. [Przełączanie rekordów MX](#step-8-switch-your-mx-records)

## <a name="step-1-begin-onboarding-security-teams"></a>Krok 1. Rozpoczynanie dołączania zespołów zabezpieczeń

Jeśli Twoja organizacja ma zespół reagowania na zabezpieczenia, nadszedł czas, aby rozpocząć integrację Ochrona usługi Office 365 w usłudze Microsoft Defender z procesami reagowania, w tym systemami biletów. Jest to cały temat sam w sobie, ale czasami jest pomijany. Wczesne zaangażowanie zespołu ds. reagowania na zabezpieczenia zapewni, że organizacja będzie gotowa do radzenia sobie z zagrożeniami podczas przełączania rekordów MX. Reagowanie na zdarzenia musi być dobrze przygotowane do obsługi następujących zadań:

- Poznaj nowe narzędzia i zintegruj je z istniejącymi przepływami. Przykład:
  - Administracja zarządzanie komunikatami poddanymi kwarantannie jest ważne. Aby uzyskać instrukcje, zobacz [Zarządzanie komunikatami i plikami poddanymi kwarantannie jako administrator](manage-quarantined-messages-and-files.md).
  - Śledzenie komunikatów pozwala zobaczyć, co się stało z komunikatami podczas ich wprowadzania lub opuszczania platformy Microsoft 365. Aby uzyskać więcej informacji, zobacz [Śledzenie komunikatów w nowoczesnym centrum administracyjnym programu Exchange w Exchange Online](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac).
- Identyfikowanie zagrożeń, które mogły zostać wprowadzone do organizacji.
- Dostrajanie i dostosowywanie [alertów](../../compliance/alert-policies.md) dla procesów organizacyjnych.
- Zarządzanie kolejką zdarzeń i korygowanie potencjalnych zagrożeń.

Jeśli Organizacja zakupiła Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2, powinna rozpocząć zapoznanie się z funkcjami, takimi jak Eksplorator zagrożeń, zaawansowane wyszukiwanie zagrożeń i zdarzenia. Aby uzyskać odpowiednie szkolenia, zobacz <https://aka.ms/mdoninja>.

Jeśli zespół reagowania na zabezpieczenia zbiera i analizuje niefiltrowane wiadomości, możesz skonfigurować skrzynkę pocztową SecOps w celu odbierania tych niefiltrowanych wiadomości. Aby uzyskać instrukcje, zobacz [Konfigurowanie skrzynek pocztowych SecOps w zaawansowanych zasadach dostarczania](configure-advanced-delivery.md#use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy).

### <a name="siemsoar"></a>SIEM/SOAR

Aby uzyskać więcej informacji na temat integracji z rozwiązaniem SIEM/SOAR, zobacz następujące artykuły:

- [Omówienie interfejsów API usługi Microsoft 365 Defender](/microsoft-365/security/defender/api-overview)
- [Interfejs API przesyłania strumieniowego](/microsoft-365/security/defender/streaming-api)
- [Interfejs API zaawansowanego wyszukiwania zagrożeń](/microsoft-365/security/defender/api-advanced-hunting)
- [Interfejsy API zdarzeń](/microsoft-365/security/defender/api-incident)

Jeśli Twoja organizacja nie ma zespołu reagowania na zabezpieczenia ani istniejących przepływów procesów, możesz użyć tego czasu, aby zapoznać się z podstawowymi funkcjami wyszukiwania zagrożeń i reagowania w Ochrona usługi Office 365 w usłudze Defender. Aby uzyskać więcej informacji, zobacz [Badanie zagrożeń i reagowanie](office-365-ti.md).

### <a name="rbac-roles"></a>Role RBAC

Uprawnienia w Ochrona usługi Office 365 w usłudze Defender są oparte na kontroli dostępu opartej na rolach (RBAC) i opisano je w temacie Uprawnienia w [portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md). Należy pamiętać o następujących ważnych kwestiach:

- Azure AD role dają uprawnienia do **wszystkich** obciążeń w usłudze Microsoft 365. Jeśli na przykład dodasz użytkownika do administratora zabezpieczeń w Azure Portal, wszędzie ma uprawnienia administratora zabezpieczeń.
- Role współpracy & poczty e-mail w portalu Microsoft 365 Defender udzielają uprawnień portalowi Microsoft 365 Defender, portal zgodności Microsoft Purview i starszemu Centrum zgodności & zabezpieczeń. Jeśli na przykład dodasz użytkownika do administratora zabezpieczeń w portalu Microsoft 365 Defender, ma on dostęp administratora zabezpieczeń **tylko** w portalu Microsoft 365 Defender, portal zgodności Microsoft Purview i Centrum zgodności & zabezpieczeń.
- Wiele funkcji w portalu Microsoft 365 Defender jest opartych na poleceniach cmdlet programu PowerShell Exchange Online i dlatego wymaga członkostwa w grupach ról w odpowiednich rolach (technicznie grupach ról) w Exchange Online (w szczególności w celu uzyskania dostępu do odpowiednich Exchange Online  Polecenia cmdlet programu PowerShell).
- W portalu Microsoft 365 Defender istnieją role współpracy & poczty e-mail, które nie mają odpowiedników ról Azure AD i są ważne w przypadku operacji zabezpieczeń (na przykład roli podglądu oraz roli Wyszukiwanie i przeczyszczanie).

Zazwyczaj tylko podzbiór pracowników ochrony będzie potrzebował dodatkowych praw do pobierania wiadomości bezpośrednio ze skrzynek pocztowych użytkowników. Wymaga to dodatkowego uprawnienia, które domyślnie nie ma czytnika zabezpieczeń.

## <a name="step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service"></a>Krok 2. (Opcjonalnie) Wykluczenie użytkowników pilotażowych z filtrowania według istniejącej usługi ochrony

Chociaż ten krok nie jest wymagany, należy rozważyć skonfigurowanie użytkowników pilotażowych w celu obejścia filtrowania według istniejącej usługi ochrony. Ta akcja umożliwia Ochrona usługi Office 365 w usłudze Defender obsługę **wszystkich** obowiązków związanych z filtrowaniem i ochroną użytkowników pilotażowych. Jeśli nie zwolnisz użytkowników pilotażowych z istniejącej usługi ochrony, Ochrona usługi Office 365 w usłudze Defender efektywnie działa tylko w przypadku chybień z innej usługi (filtrowanie komunikatów, które zostały już odfiltrowane).

> [!NOTE]
> Ten krok jest jawnie wymagany, jeśli bieżąca usługa ochrony udostępnia zawijanie linków, ale chcesz pilotować funkcje bezpiecznych łączy. Podwójne zawijanie łączy nie jest obsługiwane.

## <a name="step-3-tune-spoof-intelligence"></a>Krok 3. Dostrajanie analizy fałszowania

Sprawdź szczegółowe informacje o analizie [fałszowania](learn-about-spoof-intelligence.md) , aby zobaczyć, co jest dozwolone lub zablokowane jako fałszowanie, oraz ustalić, czy musisz zastąpić werdykt systemu w celu fałszowania. Niektóre źródła wiadomości e-mail o znaczeniu krytycznym dla działania firmy mogły niepoprawnie skonfigurować rekordy uwierzytelniania poczty e-mail w systemach DNS (SPF, DKIM i DMARC) i być może używasz przesłoń w istniejącej usłudze ochrony do maskowania problemów z domeną.

Analiza fałszowania może uratować pocztę e-mail z domen bez odpowiednich rekordów uwierzytelniania poczty e-mail w systemie DNS, ale funkcja czasami wymaga pomocy w odróżnieniu dobrego fałszowania od nieprawidłowego fałszowania. Skoncentruj się na następujących typach źródeł komunikatów:

- Źródła komunikatów, które znajdują się poza zakresami adresów IP zdefiniowanymi w [rozszerzonym filtrowaniu dla łączników](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).
- Źródła komunikatów, które mają największą liczbę komunikatów.
- Źródła komunikatów, które mają największy wpływ na organizację.

Analiza fałszowania ostatecznie dostroi się po skonfigurowaniu przesyłania użytkowników, więc nie ma potrzeby perfekcji.

## <a name="step-4-tune-impersonation-protection-and-mailbox-intelligence"></a>Krok 4. Dostrajanie ochrony przed personifikacją i analizy skrzynki pocztowej

Gdy masz wystarczająco dużo czasu, aby obserwować wyniki ochrony przed personifikacją w trybie **Nie stosuj żadnej akcji** , możesz indywidualnie włączyć każdą akcję ochrony przed personifikacją w zasadach ochrony przed wyłudzaniem informacji:

- Ochrona przed personifikacją użytkowników: **kwarantanna komunikatu zarówno dla standardowego** , jak i ścisłego.
- Ochrona przed personifikacją domeny: **poddaj kwarantannie komunikat dla zarówno standardowego** , jak i ścisłego.
- Ochrona przed analizą skrzynki pocztowej: **przenieś wiadomość do folderów wiadomości-śmieci adresatów w warstwie** Standardowa; **Kwarantanna komunikatu** dla ścisłe.

Dłużej monitorujesz wyniki ochrony przed personifikacją bez działania na komunikatach, tym więcej danych będziesz potrzebować do zidentyfikowania zezwalania lub bloków, które mogą być wymagane. Rozważ użycie opóźnienia między włączeniem każdej ochrony, która jest wystarczająco znacząca, aby umożliwić obserwację i dostosowanie.

> [!NOTE]
> Częste i ciągłe monitorowanie i dostrajanie tych zabezpieczeń jest ważne. Jeśli podejrzewasz wynik fałszywie dodatni, zbadaj przyczynę i użyj przesłoń tylko w razie potrzeby i tylko w przypadku funkcji wykrywania, która tego wymaga.

### <a name="tune-mailbox-intelligence"></a>Dostrajanie analizy skrzynki pocztowej

Mimo że analiza skrzynek pocztowych została skonfigurowana tak, aby nie podejmowała żadnych działań w przypadku wiadomości, które zostały [uznane za próby personifikacji](impersonation-insight.md), była włączona i uczyła się wzorców wysyłania i odbierania wiadomości e-mail użytkowników pilotażowych. Jeśli użytkownik zewnętrzny ma kontakt z jednym z użytkowników pilotażowych, wiadomości od tego użytkownika zewnętrznego nie będą identyfikowane jako próby personifikacji przez analizę skrzynki pocztowej (co zmniejsza liczbę wyników fałszywie dodatnich).

Gdy wszystko będzie gotowe, wykonaj następujące kroki, aby umożliwić analizie skrzynek pocztowych działanie na komunikatach wykrytych jako próby personifikacji:

- W zasadach ochrony przed wyłudzaniem informacji z ustawieniami ochrony standardowej zmień wartość **Jeśli analiza skrzynki pocztowej wykryje personifikowanego użytkownika** , aby **przenieść wiadomość do folderów wiadomości-śmieci adresatów**.

- W zasadach ochrony przed wyłudzaniem informacji przy użyciu ustawień ścisłej ochrony zmień wartość **wartości Jeśli analiza skrzynki pocztowej wykryje i personifikuje użytkownika** z pozycji **Kwarantanna wiadomości**.

Aby zmodyfikować zasady, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender](configure-mdo-anti-phishing-policies.md).

Po zaobserwowaniu wyników i wprowadzeniu jakichkolwiek korekt przejdź do następnej sekcji, aby przejść do komunikatów kwarantanny wykrytych przez personifikację użytkownika.

### <a name="tune-user-impersonation-protection"></a>Dostrajanie ochrony przed personifikacją użytkowników

W obu zasadach ochrony przed wyłudzaniem informacji na podstawie ustawień standardowych i ścisłych zmień wartość **jeśli komunikat zostanie wykryty jako personifikowany użytkownik** , aby **poddać komunikat kwarantannie**.

Sprawdź [szczegółowe informacje o personifikacji](impersonation-insight.md) , aby zobaczyć, co jest blokowane podczas prób personifikacji użytkowników.

Aby zmodyfikować zasady, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender](configure-mdo-anti-phishing-policies.md).

Po zaobserwowaniu wyników i wprowadzeniu jakichkolwiek korekt przejdź do następnej sekcji, aby przejść do komunikatów kwarantanny wykrytych przez personifikację domeny.

### <a name="tune-domain-impersonation-protection"></a>Dostrajanie ochrony przed personifikacją domeny

W obu zasadach ochrony przed wyłudzaniem informacji na podstawie ustawień standardowych i ścisłych zmień wartość **jeśli komunikat zostanie wykryty jako domena personifikowana** , aby **poddać komunikat kwarantannie**.

Sprawdź [szczegółowe informacje o personifikacji](impersonation-insight.md) , aby zobaczyć, co jest blokowane podczas prób personifikacji domeny.

Aby zmodyfikować zasady, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender](configure-mdo-anti-phishing-policies.md).

Obserwuj wyniki i w razie potrzeby wprowadź wszelkie zmiany.

## <a name="step-5-use-data-from-user-submissions-to-measure-and-adjust"></a>Krok 5. Używanie danych przesyłanych przez użytkowników do mierzenia i dostosowywania

Gdy użytkownicy pilotażowi zgłaszają wyniki fałszywie dodatnie i fałszywie ujemne, komunikaty będą wyświetlane na [stronie Przesłane w portalu Microsoft 365 Defender](admin-submission.md). Możesz zgłosić błędnie zidentyfikowane komunikaty do firmy Microsoft w celu analizy i użyć tych informacji, aby dostosować ustawienia i wyjątki w policji pilotażowej w razie potrzeby.

Użyj następujących funkcji, aby monitorować i iterować ustawienia ochrony w Ochrona usługi Office 365 w usłudze Defender:

- [Kwarantanna](manage-quarantined-messages-and-files.md)
- [Eksplorator zagrożeń](email-security-in-microsoft-defender.md)
- [Raporty zabezpieczeń poczty e-mail](view-email-security-reports.md)
- [raporty Ochrona usługi Office 365 w usłudze Defender](view-reports-for-mdo.md)
- [Szczegółowe informacje o przepływie poczty](/exchange/monitoring/mail-flow-insights/mail-flow-insights)
- [Raporty przepływu poczty](/exchange/monitoring/mail-flow-reports/mail-flow-reports)

Jeśli Twoja organizacja używa usługi innej firmy do raportów użytkowników, możesz zintegrować te dane z pętlą opinii.

## <a name="step-6-optional-add-more-users-to-your-pilot-and-iterate"></a>Krok 6. (Opcjonalnie) Dodawanie większej liczby użytkowników do pilotażu i iterowanie

Gdy znajdziesz i rozwiążesz problemy, możesz dodać więcej użytkowników do grup pilotażowych (i odpowiednio zwolnić tych nowych użytkowników pilotażowych ze skanowania przez istniejącą usługę ochrony odpowiednio). Więcej testów, które teraz wykonujesz, tym mniej problemów z użytkownikami będzie trzeba rozwiązać później. Takie podejście "kaskadowe" umożliwia dostrajanie większej części organizacji i daje zespołom ds. zabezpieczeń czas na dostosowanie się do nowych narzędzi i procesów.

- Platforma Microsoft 365 generuje alerty, gdy zasady organizacji zezwalają na wyłudzanie informacji o wysokim poziomie zaufania. Aby zidentyfikować te komunikaty, dostępne są następujące opcje:
  - Przesłonięcia w [raporcie o stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report).
  - Filtruj w Eksploratorze zagrożeń, aby zidentyfikować komunikaty.
  - Filtruj w obszarze Zaawansowane wyszukiwanie zagrożeń, aby zidentyfikować komunikaty.

  Zgłoś firmę Microsoft wyniki fałszywie dodatnie tak wcześnie, jak to możliwe za pośrednictwem przesyłania przez administratora, użyj funkcji [Zezwalaj na dzierżawę/Lista zablokowanych](tenant-allow-block-list.md) , aby skonfigurować bezpieczne przesłonięcia dla tych wyników fałszywie dodatnich.

- Dobrym pomysłem jest również zbadanie niepotrzebnych przesłonięcia. Innymi słowy, przyjrzyj się werdyktom dostarczonym przez platformę Microsoft 365 w wiadomościach. Jeśli platforma Microsoft365 wyrenderuje prawidłowy werdykt, konieczność zastąpienia jest znacznie zmniejszona lub wyeliminowana.

## <a name="step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule"></a>Krok 7. Rozszerzanie ochrony platformy Microsoft 365 na wszystkich użytkowników i wyłączanie reguły przepływu poczty SCL=-1

Wykonaj kroki opisane w tej sekcji, gdy wszystko będzie gotowe do przełączenia rekordów MX na platformę Microsoft 365.

1. Rozszerzanie zasad pilotażowych na całą organizację. Zasadniczo istnieją różne sposoby, aby to zrobić:
   - Użyj [wstępnie ustawionych zasad zabezpieczeń](preset-security-policies.md) i podziel użytkowników między profil ochrony standardowej i profil ścisłej ochrony (upewnij się, że wszyscy są objęci ochroną). Wstępnie ustawione zasady zabezpieczeń są stosowane przed utworzonymi przez Ciebie zasadami niestandardowymi lub wszelkimi domyślnymi zasadami. Możesz wyłączyć indywidualne zasady pilotażowe bez ich usuwania.

     Wadą wstępnie ustawionych zasad zabezpieczeń jest to, że nie można zmienić wielu ważnych ustawień po ich utworzeniu.

   - Zmień zakres zasad utworzonych i dostosowanych podczas pilotażu, aby uwzględnić wszystkich użytkowników (na przykład wszystkich adresatów we wszystkich domenach). Pamiętaj, że jeśli wiele zasad tego samego typu (na przykład zasad ochrony przed wyłudzaniem informacji) ma zastosowanie do tego samego użytkownika (indywidualnie, według członkostwa w grupie lub domeny poczty e-mail), stosowane są tylko ustawienia zasad o najwyższym priorytecie (numer o najniższym priorytecie) i zatrzymania przetwarzania dla tego typu zasad.

2. Wyłącz regułę przepływu poczty SCL=-1 (możesz ją wyłączyć bez usuwania).

3. Sprawdź, czy poprzednie zmiany weszły w życie i czy Ochrona usługi Office 365 w usłudze Defender jest teraz prawidłowo włączona dla wszystkich użytkowników. W tym momencie wszystkie funkcje ochrony Ochrona usługi Office 365 w usłudze Defender mogą teraz działać w wiadomościach e-mail dla wszystkich adresatów, ale ta poczta została już zeskanowana przez istniejącą usługę ochrony.

Na tym etapie można wstrzymać rejestrowanie i dostrajanie danych na większą skalę.

## <a name="step-8-switch-your-mx-records"></a>Krok 8. Przełączanie rekordów MX

> [!NOTE]
>
> - Po przełączeniu rekordu MX dla domeny propagacja zmian w Internecie może potrwać do 48 godzin.
> - Zalecamy obniżenie wartości czasu wygaśnięcia rekordów DNS, aby umożliwić szybszą reakcję i możliwe wycofanie (w razie potrzeby). Możesz przywrócić oryginalną wartość czasu wygaśnięcia po zakończeniu przełączania i zweryfikowaniu.
> - Należy rozważyć rozpoczęcie od zmiany domen, które są używane rzadziej. Możesz wstrzymać i monitorować przed przejściem do większych domen. Jednak nawet jeśli to zrobisz, nadal upewnij się, że wszyscy użytkownicy i domeny są objęci zasadami, ponieważ pomocnicze domeny SMTP są rozpoznane w domenach podstawowych przed aplikacją zasad.
> - Z technicznego punktu widzenia działa wiele rekordów MX dla jednej domeny, co pozwala na dzielenie routingu, pod warunkiem że wykonano wszystkie wskazówki przedstawione w tym artykule. W szczególności należy upewnić się, że zasady są stosowane do wszystkich użytkowników, że reguła przepływu poczty SCL=-1 jest stosowana tylko do poczty, która przechodzi przez istniejącą usługę ochrony zgodnie z opisem w [kroku 3 konfiguracji: Obsługa lub tworzenie reguły przepływu poczty SCL=-1](migrate-to-defender-for-office-365-setup.md#step-3-maintain-or-create-the-scl-1-mail-flow-rule). Jednak ta konfiguracja wprowadza zachowanie, które znacznie utrudnia rozwiązywanie problemów i dlatego zwykle nie zalecamy tego, szczególnie przez dłuższy czas.
> - Przed przełączeniem rekordów MX sprawdź, czy następujące ustawienia nie są włączone w łączniku przychodzącym z usługi ochrony na platformę Microsoft 365. Zazwyczaj łącznik będzie miał skonfigurowane co najmniej jedno z następujących ustawień:
>   - **i wymagać, aby nazwa podmiotu certyfikatu używana przez partnera do uwierzytelniania przy użyciu Office 365 odpowiadała tej nazwie domeny** (*RestrictDomainsToCertificate*)
>   - **Odrzuć wiadomości e-mail, jeśli nie są one wysyłane z tego zakresu adresów IP** (*RestrictDomainsToIPAddresses*) Jeśli typ łącznika to **Partner** i któreś z tych ustawień jest włączone, dostarczanie poczty do domen zakończy się niepowodzeniem po przełączeniu rekordów MX. Przed kontynuowaniem należy wyłączyć te ustawienia. Jeśli łącznik jest łącznikiem lokalnym używanym do użycia hybrydowego, nie musisz modyfikować łącznika lokalnego. Jednak nadal możesz sprawdzić obecność łącznika **partnerów** .
> - Jeśli bieżąca brama poczty również zapewnia weryfikację adresata, możesz sprawdzić, czy domena jest skonfigurowana jako [autorytatywna](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) w usłudze Microsoft 365. Może to zapobiec niepotrzebnym komunikatom odbijania.

Gdy wszystko będzie gotowe, przełącz rekord MX dla swoich domen. Wszystkie domeny można migrować jednocześnie. Możesz też najpierw przeprowadzić migrację rzadziej używanych domen, a następnie przeprowadzić migrację pozostałych domen później.

Możesz wstrzymać się i ocenić tutaj w dowolnym momencie. Pamiętaj jednak, że po wyłączeniu reguły przepływu poczty SCL=-1 użytkownicy mogą mieć dwa różne środowiska sprawdzania wyników fałszywie dodatnich. Im szybciej zapewnisz pojedyncze, spójne środowisko, tym szczęśliwsi użytkownicy i zespoły pomocy technicznej będą musieli rozwiązać problem z brakującą wiadomością.

## <a name="next-steps"></a>Następne kroki

Gratulacje! Migracja [do Ochrona usługi Office 365 w usłudze Microsoft Defender została ukończona](migrate-to-defender-for-office-365.md#the-migration-process)! Ponieważ wykonano kroki opisane w tym przewodniku migracji, pierwsze dni, w których poczta jest dostarczana bezpośrednio do platformy Microsoft 365, powinny być znacznie płynniejsze.

Teraz rozpoczniesz normalną operację i konserwację Ochrona usługi Office 365 w usłudze Defender. Monitoruj i obserwuj problemy podobne do tych, które wystąpiły podczas pilotażu, ale na większą skalę. Najbardziej przydatne będą [szczegółowe informacje dotyczące analizy podróbek](learn-about-spoof-intelligence.md) i [szczegółowe informacje o personifikacji](impersonation-insight.md) , ale rozważ regularne wykonywanie następujących działań:

- Przeglądanie przesłanych przez użytkowników, zwłaszcza [wiadomości wyłudzających informacje zgłaszane przez użytkowników](automated-investigation-response-office.md)
- Przejrzyj przesłonięcia w [raporcie o stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report).
- Użyj [zapytań zaawansowanego wyszukiwania zagrożeń](/microsoft-365/security/defender/advanced-hunting-example) , aby wyszukać możliwości dostrajania i ryzykowne komunikaty.
