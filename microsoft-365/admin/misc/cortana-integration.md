---
title: Cortana w Microsoft 365
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 7257cb50-0d5c-4f7a-ac2e-9fe5d13bb5cb
description: Użytkownicy z prawidłowymi kontami służbowymi mogą uzyskiwać Cortana w środowiskach Microsoft 365 spełniających Office 365 obietnic zabezpieczeń na poziomie przedsiębiorstwa.
ms.openlocfilehash: 2f9bf926c2d72115e4c4723940b6a182684b79fb
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782176"
---
# <a name="cortana-in-microsoft-365"></a>Cortana w Microsoft 365

Cortana, twój osobisty asystent produktywności, oferuje środowiska oparte na sztucznej inteligencji, aby zaoszczędzić czas i skupić uwagę na tym, co najważniejsze. Cortana jest przeznaczony do dostarczania funkcji, które bezpiecznie przetwarzają i rozumują Office 365 danych, takich jak wiadomości e-mail, pliki, czaty itp., aby zaoszczędzić czas, zwiększyć wydajność i zwiększyć produktywność użytkowników.

Po zalogowaniu się przy użyciu prawidłowych kont służbowych użytkownicy mogą uzyskiwać usługi pomocy opartej na chmurze z Cortana w środowiskach Microsoft 365 spełniających obietnice Office 365 dotyczące prywatności, zabezpieczeń i zgodności na poziomie przedsiębiorstwa ("**Cortana usługi dla przedsiębiorstw**").

- **Cortana usługi dla przedsiębiorstw obejmują** Cortana w Windows 10 (wersja 2004 lub nowsza), Outlook dla systemów iOS i Android, Microsoft Teams aplikacje mobilne dla systemów iOS i Android oraz [Microsoft Teams wyświetlane](/microsoftteams/devices/teams-displays).

- Te różne środowiska podlegają oddzielnym warunkom licencjonowania i mają oddzielne kroki rezygnacji opisane poniżej.

- Zgodnie z innymi usługami Office 365 usługi Cortana dla przedsiębiorstw spełniają te same obietnice dotyczące prywatności, zabezpieczeń i zgodności na poziomie przedsiębiorstwa, co zostało to odzwierciedlone w [warunkach usług online (OST).](https://www.microsoft.com/licensing/product-licensing/products)

- Nowe środowiska Microsoft 365, takie jak wiadomość e-mail z briefingiem i odtwarzanie moich wiadomości e-mail, zostaną włączone przy użyciu usług Cortana dla przedsiębiorstw i w pełni spełniają te obietnice. Te funkcje są obecnie dostępne na całym świecie (standardowa wielodostępna). Aby uzyskać więcej informacji na temat znajdowania lokalizacji użycia, odwiedź stronę [Wyświetlanie dodatkowych wartości właściwości dla kont](../../enterprise/view-user-accounts-with-microsoft-365-powershell.md#view-additional-property-values-for-accounts).

- Istniejące środowiska konsumentów, w tym Cortana w Windows 10 (wersja 1909 lub starsza), podlegają [umowie o świadczenie usług firmy Microsoft](https://www.microsoft.com/licensing/product-licensing/products) i [oświadczeniu o ochronie prywatności firmy Microsoft](https://privacy.microsoft.com/privacystatement) (zobacz sekcję "Istniejące usługi dla konsumentów" poniżej). Te warunki będą również regulować Cortana usług przedsiębiorstwa udostępnianych użytkownikowi po zalogowaniu się przy użyciu poświadczeń konsumenta.

## <a name="what-data-is-processed-by-cortana-enterprise-services"></a>Jakie dane są przetwarzane przez usługi Cortana przedsiębiorstwie?

Cortana usługi przedsiębiorstwa przetwarzają zapytania od użytkownika, Office dane potrzebne do spełnienia żądania użytkownika oraz inne dane telemetryczne generowane przez systemy firmy Microsoft w celu uruchomienia usługi. Dane zbierane przez usługi Cortana enterprise obejmują tekstową reprezentację zapytań mówionych użytkownika (tj. transkrypcje z rozpoznawania mowy). Te dane tekstowe są danymi klienta i są zarządzane zgodnie z  [Warunkami dotyczącymi usług online](https://www.microsoft.com/licensing/product-licensing/products). Służy tylko do opracowywania i ulepszania modeli uczenia maszynowego zgodnych z warunkami dotyczącymi usługi online.

## <a name="what-is-the-governance-model-for-customer-data-in-cortana-enterprise-services"></a>Jaki jest model ładu dla danych klienta w Cortana usługach dla przedsiębiorstw?

Zgodnie z innymi usługami Office 365 usługi Cortana dla przedsiębiorstw są zabezpieczone i podlegają [Warunkom dotyczącym usług online](https://www.microsoft.com/licensing/product-licensing/products). Obejmuje to zestaw obietnic dotyczących ochrony danych klienta przed przypadkową utratą, zmianą, nieautoryzowanym ujawnieniem lub dostępem lub bezprawnym zniszczeniem. Dane klienta podlegają również ścisłym ograniczeniom dostępu. Firma Microsoft używa danych klienta tylko do świadczenia usług uzgodnionych i do celów zgodnych z tymi usługami. Aby uzyskać szczegółowe informacje, zobacz poniższą tabelę.

## <a name="how-does-microsoft-store-retain-process-and-use-customer-data-in-cortana"></a>Jak firma Microsoft przechowuje, przechowuje, przetwarza i używa danych klienta w Cortana?

W poniższej tabeli opisano obsługę danych Cortana usług przedsiębiorstwa.

|Name (Nazwa)|Opis|
|---|---|
|**Magazynowanie**|Dane klienta są przechowywane na serwerach firmy Microsoft w chmurze Office 365. Dane są częścią dzierżawy. <br/><br/>Dźwięk mowy nie jest zachowywany.|
|**Pobyty w obszarze geograficznym**|Dane klienta są przechowywane na serwerach firmy Microsoft w chmurze Office 365 w obszarze Geograficznym. Dane są częścią dzierżawy.|
|**Przechowywania**|Dane klienta są usuwane po zamknięciu konta przez administratora dzierżawy lub w przypadku żądania usunięcia praw podmiotu danych RODO. <br/><br/>Dźwięk mowy nie jest zachowywany.|
|**Przetwarzanie i poufność**|Pracownicy zaangażowani w przetwarzanie danych klienta i danych osobowych (i) będą przetwarzać takie dane tylko na podstawie instrukcji od Klienta, a (ii) będą zobowiązani do zachowania poufności i bezpieczeństwa takich danych nawet po zakończeniu ich zaangażowania.|
|**Użycia**|Firma Microsoft używa danych klienta tylko do świadczenia usług uzgodnionych i do celów zgodnych z tymi usługami. Jednym z tych celów jest uczenie maszynowe do opracowywania i ulepszania modeli. Uczenie maszynowe odbywa się wewnątrz chmury Office 365 i nie ma możliwości przeglądania, przeglądania ani etykietowania danych klienta przez człowieka. <br/><br/>Twoje dane nie są używane do celów reklamowych.|

## <a name="cortana-enterprise-services-in-microsoft-365-experiences"></a>Cortana usługi dla przedsiębiorstw w środowiskach Microsoft 365

### <a name="cortana-in-windows-10-version-2004-and-later"></a>Cortana w Windows 10 (wersja 2004 i nowsze)

Aplikacja Cortana w Windows 10 pomaga użytkownikom szybko uzyskiwać informacje w Microsoft 365, używając zapytań wpisanych lub mówionych do nawiązywania połączenia z osobami, sprawdzania kalendarzy, ustawiania przypomnień i nie tylko.

Cortana w Windows mogą pomóc użytkownikom w lepszym zarządzaniu harmonogramem i zadaniami. Mogą oni dodawać do swoich list w Microsoft To Do, wyszukiwać informacje lokalne, uzyskiwać definicje i śledzić najnowsze wiadomości, informacje o pogodzie i finansach za pomocą wyszukiwania Bing.

Cortana w Windows 10, wersja 2004 lub nowsza, spełnia te same obietnice dotyczące prywatności, zabezpieczeń i zgodności na poziomie przedsiębiorstwa dla usług Cortana przedsiębiorstwie, co zostało odzwierciedlone w [warunkach dotyczących usług online (OST).](https://www.microsoft.com/licensing/product-licensing/products)

### <a name="how-to-opt-out-of-cortana-in-windows-10"></a>Jak zrezygnować z Cortana w Windows 10

Rezygnacja z Cortana w Windows 10 nie wyklucza innych środowisk, które są kontrolowane oddzielnie. Administratorzy mogą skonfigurować Cortana w Windows 10 dla swojej organizacji przy użyciu zasad MdM Experience\AllowCortana lub za pośrednictwem zasady grupy: Konfiguracja komputera\Szablony administracyjne\Windows Components\Search\Allow Cortana.

Począwszy od Windows 10, wersja 2004, Cortana to aplikacja platforma uniwersalna systemu Windows (UWP) wstępnie zainstalowana z Windows i jest regularnie aktualizowana za pośrednictwem Microsoft Store. Aby otrzymywać najnowsze aktualizacje Cortana, należy [włączyć aktualizacje za pośrednictwem Microsoft Store](/windows/configuration/stop-employees-from-using-microsoft-store).

[Dowiedz się więcej o Cortana w Windows 10](/windows/configuration/cortana-at-work/cortana-at-work-overview)

### <a name="cortana-voice-assistance-in-teams-mobile-and-teams-display"></a>Cortana pomoc głosowa w Teams wyświetlaczu mobilnym i Teams

> [!NOTE]
> Cortana pomoc głosowa jest obsługiwana w aplikacjach mobilnych Microsoft Teams dla systemów iOS i Android, a [Microsoft Teams jest wyświetlana](/microsoftteams/devices/teams-displays) w języku angielskim dla użytkowników w Stany Zjednoczone, Wielkiej Brytanii, Kanadzie, Indiach i Australii.  Microsoft Teams Rooms na Windows jest obsługiwana tylko dla użytkowników w Stany Zjednoczone. Cortana pomoc głosowa nie jest obecnie dostępna dla dzierżaw GCC, GCC-High, DoD i EDU. Rozszerzenie do dodatkowych języków i regionów nastąpi w ramach przyszłych wydań, a klienci administracyjni zostaną powiadomieni za pośrednictwem Centrum komunikatów i [planu Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=65346).

Cortana pomoc głosową w aplikacji mobilnej Teams i na Microsoft Teams urządzeniach wyświetlające umożliwia użytkownikom Microsoft 365 Enterprise usprawnienie komunikacji, współpracy i zadań związanych ze spotkaniami przy użyciu mówionego języka naturalnego. Użytkownicy mogą rozmawiać z Cortana, wybierając przycisk mikrofonu znajdujący się w prawym górnym rogu aplikacji mobilnej Teams lub mówiąc "Cortana" na ekranie Microsoft Teams. Aby szybko nawiązać połączenie z zespołem bez użycia rąk, a w podróży użytkownicy mogą wysyłać zapytania, takie jak "call Megan" lub "send a message to my next meeting". Użytkownicy mogą również dołączać do spotkań, mówiąc "dołącz do mojego następnego spotkania" i korzystając z pomocy głosowej, aby udostępniać pliki, sprawdzać swój kalendarz i nie tylko. Te środowiska pomocy głosowej są dostarczane przy użyciu Cortana usług klasy korporacyjnej, które są w pełni zgodne z obietnicami dotyczącymi prywatności, bezpieczeństwa i zgodności Office 365 zgodnie z [warunkami dotyczącymi usług online (OST).](https://www.microsoft.com/licensing/product-licensing/products)

#### <a name="admin-control"></a>Kontrola administratora

Cortana pomoc głosowa będzie domyślnie włączona dla dzierżawców. Administratorzy mogą kontrolować, kto w dzierżawie może korzystać z Cortana pomocy głosowej w Teams za pośrednictwem zasad (TeamsCortanaPolicy). Te zasady można ustawić na poziomie konta użytkownika lub dzierżawy. Administratorzy mogą również użyć pola CortanaVoiceInvocationMode w ramach tej kontrolki zasad, aby określić, czy Cortana jest wyłączona, włączona tylko z wywołaniem przycisku naciśnięcia, czy włączona z wywołaniem słowa wznawiania (dotyczy również urządzeń, które go obsługują, na przykład wyświetlania Microsoft Teams).

#### <a name="user-control"></a>Kontrola użytkownika

Poszczególni użytkownicy mogą wypróbować Cortana pomocy głosowej w aplikacji mobilnej Teams, klikając przycisk mikrofonu. Mogą wypróbować Cortana pomocy głosowej na urządzeniach Microsoft Teams wyświetlania, mówiąc po prostu "Cortana". Mogą również kontrolować, czy Cortana odpowiada na wywołanie słowa budzenia.

1. Otwórz Teams mobile
2. Przejdź do **Ustawienia**
3. Wybierz **Cortana**
4. Przełączanie przełącznika **aktywacji głosowej**

[Dowiedz się więcej o korzystaniu z pomocy głosowej w Teams](https://support.microsoft.com/office/274bb2f0-d962-4182-b45d-307435cea256)

### <a name="cortana-voice-assistance-in-teams-meeting-room"></a>Cortana pomoc głosowa w Teams Sala konferencyjna

Cortana pomoc głosowa w pokojach konferencyjnych Teams wykracza poza to, co można zrobić z Teams na urządzeniach osobistych, zapewniając unikatowe możliwości w pokoju, takie jak sprzężenie jednym dotknięciem, kamery zawartości do udostępniania tablic fizycznych na spotkaniu w inteligentny sposób i funkcje zbliżeniowe, takie jak bezproblemowe przenoszenie pokoju na spotkanie Teams z własnego urządzenia osobistego. Użytkownicy mogą używać wypychania do rozmowy (PTT), naciskając mikrofon, aby zainicjować Cortana a następnie mówiąc: "Rozpocznij spotkanie". Po włączeniu funkcji wykrywania słów kluczowych (KWS) Cortana zacznie nasłuchiwać, gdy użytkownicy powiedzą "Cortana".

#### <a name="admin-control"></a>Kontrola administratora

Cortana pomoc głosowa w Teams jest dostarczana przy użyciu usług, które są w pełni zgodne z Office 365 obietnic dotyczących prywatności, zabezpieczeń i zgodności na poziomie przedsiębiorstwa. Aby uzyskać więcej informacji na temat przetwarzania danych w usługach Cortana enterprise, zobacz Cortana w Microsoft 365. Cortana jest domyślnie włączona w Teams pokojach spotkań dla dzierżaw. Administratorzy IT mogą zrezygnować z pomocy głosowej dla Teams Sala konferencyjna w Centrum administracyjne platformy Microsoft 365.

Jak zrezygnować ze wszystkich funkcji Cortana w Teams salach konferencyjnych:

1. Zaloguj się do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com/adminportal/home?ref=Domains)
2. **Wybieranie urządzeń**
3. Wybierz **Teams Rooms**
4. Wybierz jedno lub wiele urządzeń, na które chcesz wprowadzić zmiany
5. Wybierz pozycję **Edytuj Ustawienia**
6. Przejdź do **Cortana** i wybierz pozycję Zamień istniejącą wartość na **Wył.**
7. Wybierz pozycję Zastosuj

Jak zrezygnować z aktywacji głosowej w Teams salach konferencyjnych:

1. Zaloguj się do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com/adminportal/home?ref=Domains)
2. **Wybieranie urządzeń**
3. Wybierz **Teams Rooms**
4. Wybierz jedno lub wiele urządzeń, na które chcesz wprowadzić zmiany
5. Wybierz pozycję **Edytuj Ustawienia**
6. Usuń zaznaczenie pola **wykrywania wyrazów wznawiania**
7. Wybierz pozycję **Zastosuj**

#### <a name="configure-cortana-remotely-using-an-xml-configuration-file"></a>Konfigurowanie Cortana zdalnie przy użyciu pliku konfiguracji XML

Aby uzyskać informacje na temat zdalnego zarządzania ustawieniami konsoli Microsoft Teams Rooms przy użyciu pliku konfiguracji XML, zobacz [Zdalne zarządzanie ustawieniami urządzenia Microsoft Teams Rooms](/microsoftteams/rooms/xml-config-file).

[Dowiedz się więcej o Cortana pomocy głosowej w Teams](/microsoftteams/cortana-in-teams)

### <a name="conversational-ai-in-outlook-for-ios-with-cortana"></a>Konwersacyjna sztuczna inteligencja w Outlook dla systemu iOS z Cortana

W Outlook dla systemu iOS oparte na głosie środowisko sztucznej inteligencji Cortana umożliwia użytkownikom proszenie asystenta produktywności o zaplanowanie spotkań, tworzenie wiadomości e-mail, zarządzanie kalendarzem i skrzynką odbiorczą oraz znajdowanie wszelkiego rodzaju informacji.

Korzystając z języka naturalnego, rozpoznawania mowy, uczenia maszynowego i językoznawstwa opartego na technologii sztucznej inteligencji firmy Microsoft, Cortana poznaje Twój kontekst, aby pomóc w utrzymaniu porządkowania, łączności z osobami i rzeczami, które są dla Ciebie ważne, oraz kontroli dnia.

Wystarczy użyć przycisku mikrofonu, aby poprosić Cortana o dodanie adresatów spotkania lub zmianę dat, godzin lub lokalizacji. Możesz również poprosić Cortana o znalezienie określonych zdarzeń. Na koniec możesz poprosić Cortana o utworzenie szybkich wiadomości e-mail, przesyłanie dalej wiadomości lub odpowiadanie na wątki. Cortana mikrofon może również pomóc w rozpoczęciu odtwarzania moich wiadomości e-mail w Outlook dla systemu iOS, dzięki czemu możesz słuchać swojej skrzynki odbiorczej bez użycia rąk.

Początkowo ta nowa funkcja konwersacyjnej sztucznej inteligencji z Cortana będzie dostępna w języku angielskim dla klientów w Stany Zjednoczone przy użyciu Outlook dla systemu iOS z kontem służbowym Microsoft 365. Aby dowiedzieć się więcej, przejdź do [tematu Rozpocznij rozmowę z osobistym asystentem produktywności w Outlook z Cortana](https://techcommunity.microsoft.com/t5/outlook-blog/start-a-conversation-with-your-personal-productivity-assistant/ba-p/2071416#:~:text=Conversational%20AI%20allows%20you%20to,time%2C%20all%20with%20your%20voice).

### <a name="conversational-ai-with-cortana-in-outlook-with-ios-is-an-opt-in-experience"></a>Konwersacyjna sztuczna inteligencja z Cortana w Outlook z systemem iOS to środowisko opt-in

Poszczególni użytkownicy zostaną poproszeni o wyrażenie zgody na konwersacyjne środowisko sztucznej inteligencji przy pierwszym wybraniu przycisku mikrofonu "Użyj głosu" w Outlook w systemie iOS.

### <a name="play-my-emails"></a>Odtwórz moje wiadomości e-mail

Odtwarzanie moich wiadomości e-mail (połączonych z usługą za pośrednictwem Outlook mobile) to sterowane głosem, praktyczne środowisko umożliwiające użytkownikom słuchanie nowych wiadomości w ich ukierunkowanej skrzynce odbiorczej i zmienianie ich dnia za pośrednictwem głośników w telefonie, słuchawkach lub połączonym urządzeniu audio. Użytkownicy mogą poprosić Cortana o przeczytanie ostatnich wiadomości e-mail na głos i poprosić Cortana o podjęcie akcji, takich jak flaga, archiwizowanie, usuwanie i pomijanie wiadomości. Ta funkcja jest szczególnie przydatna do nadrobienia zaległości w wiadomości e-mail podczas dojazdów, wielozadaniowości lub w podróży. Gdy użytkownik rozmawia z Cortana w obszarze Odtwarzanie moich wiadomości e-mail, żądanie audio mowy trafia bezpośrednio do Cortana usług przedsiębiorstwa. Odczyt wiadomości e-mail użytkownika z tekstem na mowę jest przetwarzany w chmurze Office 365. W trakcie tego procesu żadne dane Office 365 nie są przetwarzane na urządzeniu przenośnym użytkownika i nie są zapisywane żadne dane poczty e-mail. Transkrypcja poleceń mówionych (tj. "oznacz jako przeczytane", "dalej", "flaga" itp.) może zostać zachowana zgodnie z warunkami ochrony danych w [Warunkach usług online](https://www.microsoft.com/licensing/product-licensing/products) firmy Microsoft.

Cortana wywoła, gdy wiadomość e-mail jest chroniona i krótko wstrzymana przed przeczytaniem wiadomości, aby dać użytkownikom wystarczająco dużo czasu na wstrzymanie odtwarzania lub przejście do następnej wiadomości. Podobnie jak w przypadku prywatnej rozmowy telefonicznej, użytkownicy powinni zachować ostrożność podczas inicjowania odtwarzania w lokalizacjach, w których można potencjalnie podsłuchać poufne informacje. W takich przypadkach zaleca się, aby pracownicy organizacji nosili słuchawki w odpowiednich środowiskach podczas korzystania z funkcji Odtwarzanie moich wiadomości e-mail w Outlook mobile.

### <a name="how-to-opt-out-of-play-my-emails"></a>Jak zrezygnować z odtwarzania moich wiadomości e-mail

Osoby fizyczne mogą zrezygnować z odtwarzania moich wiadomości e-mail, wykonując następujące kroki.

1. Otwórz Outlook mobile.

2. Przejdź do **Ustawienia**.

3. Wybierz pozycję **Odtwórz moje wiadomości e-mail**.

4. Przenieś przełącznik na wyłączone na kontach, które chcesz wyłączyć.

[Dowiedz się więcej o odtwarzaniu moich wiadomości e-mail](https://support.microsoft.com/help/4558256)

### <a name="briefing-email"></a>Wiadomość e-mail z briefingu

Cortana wysyła spersonalizowaną wiadomość e-mail z zadaniami i zobowiązaniami wykonanymi w wygodny sposób, aby oznaczyć je jako **gotowe** lub zaplanować czas koncentracji uwagi, aby je wykonać. Zawiera również podsumowanie spotkań i odpowiednich dokumentów na twój dzień. Cortana wyodrębnia informacje z wiadomości e-mail użytkownika i przechowuje je w Exchange Online skrzynce pocztowej, dopóki nie zostać skonsolidowane w wiadomości e-mail z informacjami. W żadnym momencie dane osobowe nie są dostępne poza Exchange Online skrzynką pocztową. Użytkownicy uzyskują dostęp do wiadomości e-mail z informacją tylko wtedy, gdy mają licencje obejmujące plan usługi Exchange Online.

### <a name="how-to-opt-out-of-briefing-email"></a>Jak zrezygnować z otrzymywania wiadomości e-mail z briefingu

Administratorzy mogą skonfigurować briefing dla swojej organizacji przy użyciu programu [PowerShell](/briefing/be-admin) w Exchange Online. Osoby fizyczne mogą zrezygnować z wiadomości e-mail z briefingu Cortana, wybierając pozycję **Anuluj subskrypcję** w stopce wiadomości.

[Dowiedz się więcej o wiadomości e-mail z briefingiem](https://support.microsoft.com/help/4558259)

Będziemy nadal wprowadzać więcej środowisk, takich jak powyższe, aby zwiększyć produktywność organizacji.

[Dowiedz się więcej o ofertach zgodności firmy Microsoft](/compliance/regulatory/offering-home)

## <a name="how-is-the-delivery-of-cortana-enterprise-services-different-from-the-delivery-of-other-cortana-features-i-may-have-previously-experienced"></a>Czym różni się dostarczanie usług Cortana dla przedsiębiorstw od dostarczania innych funkcji Cortana, których wcześniej doświadczyłem?

Poniżej przedstawiono dwa sposoby myślenia o tym, jak działa Cortana w przedsiębiorstwie:

**Nowe środowiska dla organizacji z usługami Cortana enterprise**: Cortana usługi dla przedsiębiorstw zostały zaprojektowane tak, aby spełniać wymagania organizacji w zakresie zabezpieczeń i zgodności:

1. Jest to nowa usługa, która została omówiona w tym dokumencie.

2. W przypadku usług podlegających warunkom dotyczącym usług online firma Microsoft jest podmiotem przetwarzającym dane: firma Microsoft zbiera dane klienta i korzysta z nich tylko w celu zapewnienia Usługi online żądanych przez naszych klientów oraz do celów, które są instruowane przez naszych klientów. Zgodnie z ogólnym rozporządzeniem o ochronie danych (RODO) klient jest administratorem danych swoich danych. Zapoznaj się z [postanowieniami dotyczącymi usług online](https://www.microsoft.com/licensing/product-licensing/products) i [wprowadzeniem większej przejrzystości prywatności dla naszych klientów korzystających z chmury komercyjnej](https://blogs.microsoft.com/eupolicy/2019/11/18/introducing-privacy-transparency-commercial-cloud-customers/).

3. Na przykład Odtwórz moje wiadomości e-mail to usługa Cortana, z którą użytkownicy mogą łączyć się za pośrednictwem Outlook dla systemu iOS i korzysta z usług Cortana przedsiębiorstwa.

4. Administratorzy IT zawsze będą mieć kontrolki opcjonalnych połączonych środowisk dla Cortana, podobnie jak w przypadku opcjonalnych środowisk połączonych podczas korzystania z aplikacji Office ProPlus.

**Istniejące usługi dla konsumentów**: Cortana opcjonalne połączone usługi są przeznaczone przede wszystkim do obsługi użytkowników i są obecnie dostarczane w Windows 10 (wersja 1909 lub starsza) oraz w aplikacji Cortana w systemach iOS i Android.

1. Te środowiska umożliwiają korzystanie z funkcji, takich jak pogoda, wiadomości i ruch.

2. Administratorzy dzierżawy mogą kontrolować, czy Cortana w Windows 10 (wersja 1909 i starsza) oraz aplikacja Cortana w systemach iOS i Android mogą zezwalać Cortana na nawiązywanie połączenia z Office 365 danych dzierżawy.

Wyłączanie Cortana dostępu do hostowanych danych firmy Microsoft w organizacji

1. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a> wybierz pozycję **Ustawienia** >  **Org Ustawienia** i wybierz pozycję **Cortana**.

2. Usuń zaznaczenie pola wyboru **Zezwalaj Cortana w Windows 10 (wersja 1909 i starsza) oraz aplikacji Cortana w systemach iOS i Android na dostęp do danych hostowanych przez firmę Microsoft w imieniu osób w organizacji w** celu wyłączenia Cortana połączonych środowisk.

3. Wybierz pozycję **Zapisz zmiany**.

W przypadku usług podlegających [umowie o świadczenie usług firmy Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=2109174) i [oświadczeniu o ochronie prywatności firmy Microsoft](https://privacy.microsoft.com/privacystatement) firma Microsoft jest administratorem danych. Jako administrator danych firma Microsoft używa danych do ulepszania produktów i usług zgodnie z oświadczeniem [o ochronie prywatności firmy Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="related-content"></a>Zawartość pokrewna

[Cortana pomocy głosowej w Teams](/microsoftteams/cortana-in-teams) (artykuł)\
[Konfigurowanie Cortana w Windows 10](/windows/configuration/cortana-at-work/cortana-at-work-overview) (artykuł)\
[Co możesz zrobić z odtwarzaniem moich wiadomości e-mail z Cortana?](https://support.microsoft.com/help/4558256)
