---
title: Tworzenie, testowanie i dostosowywanie zasad DLP
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.NewPolicyFromTemplate
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
ms.custom:
- seo-marvel-mar2020
ms.assetid: 59414438-99f5-488b-975c-5023f2254369
description: W tym artykule dowiesz się, jak tworzyć, testować i dostrajać zasady DLP zgodnie z potrzebami Twojej organizacji.
ms.openlocfilehash: cc31d067eaf2684c17a09d7b2731a5cc3500af76
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2022
ms.locfileid: "63009700"
---
# <a name="create-test-and-tune-a-dlp-policy"></a>Tworzenie, testowanie i dostosowywanie zasad DLP

Ochrona przed utratą danych (DLP, Data loss prevention) pomaga zapobiec niezamierzonemu lub przypadkowemu udostępnieniu poufnych informacji.

W przypadku usługi DLP wiadomości e-mail i pliki są sprawdzane pod adresem poufnych informacji, takich jak numer karty kredytowej. Przy użyciu funkcji DLP można wykrywać informacje poufne i podjąć takie działania, jak:

- Rejestrowanie zdarzenia na potrzeby inspekcji
- Wyświetlanie ostrzeżenia dla użytkownika końcowego, który wysyła wiadomość e-mail lub udostępnia plik
- Aktywnie blokuj wysyłanie wiadomości e-mail lub udostępnianie plików

## <a name="permissions"></a>Uprawnienia

Członkowie Twojego zespołu zgodności, którzy będą tworzyć zasady DLP, muszą mieć uprawnienia do Centrum zgodności. Domyślnie administrator dzierżawy będzie miał dostęp do danych służb zgodności i innych osób. Wykonaj następujące czynności:
  
1. Utwórz grupę w u Microsoft 365 i dodaj do niego pracowników do tego zespołu pracowników do zgodności.
    
2. Utwórz grupę ról na **stronie Uprawnienia** w Centrum zgodności &amp; zabezpieczeń. 

3. Podczas tworzenia grupy ról użyj sekcji **Wybieranie ról** , aby dodać do grupy ról następującą rolę: Zarządzanie **zgodnością DLP**.
    
4. Za pomocą **sekcji Wybieranie** członków dodaj do Microsoft 365 ról utworzoną wcześniej grupę ról.

Rola Zarządzanie **zgodnością DLP** tylko w widoku umożliwia tworzenie grupy ról z uprawnieniami tylko do wyświetlania zasad DLP i raportów funkcji DLP.

Aby uzyskać więcej informacji, zobacz [Zapewnianie użytkownikom dostępu do centrum Office 365 zgodności](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).
  
Te uprawnienia są wymagane do utworzenia i zastosowania zasad DLP, aby nie wymuszać zasad.

### <a name="roles-and-role-groups-in-preview"></a>Role i grupy ról w wersji Preview

W wersji Preview są dostępne role i grupy ról, które możesz przetestować, aby precyzyjnie dostosować kontrolki dostępu.

Oto lista dostępnych w wersji Microsoft Information Protection (MIP), które są dostępne w wersji zapoznawczej. Aby dowiedzieć się więcej na ich temat, zobacz [Role w Centrum & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Administrator ochrony informacji
- Analityk ochrony informacji
- Ochrona informacji
- Czytnik ochrony informacji

Poniżej znajdziesz listę grup ról miP, które są dostępne w wersji Preview. Aby dowiedzieć się więcej, [zobacz Grupy ról w Centrum & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Ochrona informacji
- Administratorzy ochrony informacji
- Analitycy ochrony informacji
- Schoweki ochrony informacji
- Czytniki informacji

## <a name="how-sensitive-information-is-detected-by-dlp"></a>Jak poufne informacje są wykrywane przez DLP

Dzięki zasadom DLP informacje poufne są wyszukiwane przez dopasowanie wzorca wyrażeń regularnych (RegEx) w połączeniu z innymi wskaźnikami, takimi jak odległość określonych słów kluczowych od zgodnych wzorców. Na przykład numer karty kredytowej VISA ma 16 cyfr. Jednak te cyfry można zapisywać na różne sposoby, na przykład 1111-1111-1111-1111, 1111 1111 1111 1111 lub 1111111111111111.

Dowolny ciąg 16-cyfrowy nie musi być numerem karty kredytowej, może to być numer biletu z systemu pomocy technicznej lub numer seryjny sprzętu. Aby odróżnić numer karty kredytowej od niegroźnych 16-cyfrowych ciągów, wykonywane jest obliczenie (sumy kontrolne), aby potwierdzić, że liczby są zgodne ze wzorcem różnych marek kart kredytowych.

Jeśli ochrona przed odmową (DLP) znajdzie słowa kluczowe, takie jak "VISA" lub "AMEX", wartości najbliższych dat mogące być datą wygaśnięcia karty kredytowej, na ich pomocą ochrona przed kartą kredytową również korzysta z tych danych w celu podjęcia decyzji, czy ciąg jest numerem karty kredytowej, czy nie.

Innymi słowy funkcja DLP jest wystarczająco inteligentna, aby rozpoznawać różnicę między tymi dwoma ciągami tekstu w wiadomości e-mail:

- "Czy możesz zamówić mi nowy laptop. Użyj numeru VISA 1111-1111-1111-1111, wygasa 22-11-22 i wyślij mi szacowaną datę dostawy, gdy ją masz".
- "Mój numer seryjny laptopa to 2222-2222-2222-2222, który został kupiony 11/2010. Przy okazji, czy moja wiza jest jeszcze zatwierdzoną?".

Zobacz [Definicje encji typów informacji poufnych](sensitive-information-type-entity-definitions.md) , w których wyjaśniono, jak są wykrywane poszczególne typy informacji.

## <a name="where-to-start-with-data-loss-prevention"></a>Od czego zacząć od ochrony przed utratą danych

Jeśli ryzyko związane z wyciekiem danych nie jest całkowicie oczywiste, trudno jest dokładnie zacząć od wdrożenia ochrony przed zagrożeniami. Na szczęście zasady DLP można uruchamiać w "trybie testowania", dzięki czemu można ocenić ich skuteczność i dokładność przed ich włączeniem.

Zasadami DLP dla Exchange Online zarządzać za pośrednictwem Exchange administracyjnego. Zasady DLP można jednak skonfigurować dla wszystkich obciążeń za pośrednictwem Centrum zabezpieczeń i zgodności usługi &, aby użyć ich w pokazach w tym artykule. W Centrum & zgodności znajdziesz zasady ochrony przed utratą danych w obszarze **Zasady ochrony przed utratą** >  **danych**. Wybierz **pozycję Utwórz zasady,** aby rozpocząć.

Microsoft 365 udostępnia szereg szablonów zasad [DLP,](what-the-dlp-policy-templates-include.md) których możesz użyć do tworzenia zasad. Załóżmy, że jesteś australijskim firmą. Możesz filtrować szablony w Australii, a następnie wybierać opcje Finansowe, Medyczne i Medyczne oraz Prywatność.

![Opcja wyboru kraju lub regionu.](../media/DLP-create-test-tune-choose-country.png)

W tym pokazie wybiorę opcję Dane umożliwiające identyfikację użytkownika (Australian Personally Identifiable Information, PII), która zawiera typy informacji o numerze pliku australijskiego podatku (TFN) i numer prawa jazdy.

![Opcja wyboru szablonu zasad.](../media/DLP-create-test-tune-choose-policy-template.png)

Nadaj nazwę nowym zasadom DLP. Domyślna nazwa będzie odpowiadać szablonowi zasad DLP, ale należy wybrać bardziej opisową nazwę własną, ponieważ na podstawie tego samego szablonu można utworzyć wiele zasad.

![Opcja na nazwania zasad.](../media/DLP-create-test-tune-name-policy.png)

Wybierz lokalizacje, do których będą stosowane zasady. Zasady DLP mogą mieć zastosowanie do Exchange Online, SharePoint Online i OneDrive dla Firm. Zamierzam pozostawić te zasady skonfigurowane do stosowania do wszystkich lokalizacji.

![Opcja wyboru wszystkich lokalizacji.](../media/DLP-create-test-tune-choose-locations.png)

W pierwszym kroku **Ustawienia** zasad zaakceptuj na razie ustawienia domyślne. Możesz dostosować zasady DLP, ale na początek możesz zacząć od wartości domyślnych.

![Opcje dostosowywania typu zawartości do ochrony.](../media/DLP-create-test-tune-default-customization-settings.png)

Po kliknięciu przycisku Dalej** zostanie przedstawiona strona więcej zasad **Ustawienia** z większej liczby opcji dostosowywania. W przypadku testowych zasad możesz wprowadzić pewne zmiany w tym miejscu.

- Na razie wyłączyłam porady dotyczące zasad, co jest rozsądne, jeśli testujemy wszystko i nie chcesz jeszcze wyświetlać żadnych danych użytkownikom. Porady dotyczące zasad wyświetlają ostrzeżenia użytkownikom, że chcą naruszać zasady DLP. Na przykład użytkownik usługi Outlook zobaczy ostrzeżenie, że dołączony plik zawiera numery kart kredytowych i spowoduje odrzucenie wiadomości e-mail. Porady dotyczące zasad mają na celu zatrzymanie, zanim będzie to zgodne zachowanie.
- Zmniejszyłam także liczbę wystąpień z 10 do 1, tak aby te zasady wykryły wszelkie udostępnianie australijskich danych PII, a nie tylko zbiorcze udostępnianie danych.
- Do wiadomości e-mail raportu o zdarzeniu dodano także innego adresata.

![Dodatkowe ustawienia zasad.](../media/DLP-create-test-tune-more-policy-settings.png)

Na koniec skonfigurowaliśmy te zasady do początkowego uruchamiania w trybie testowania. Zwróć uwagę, że jest też dostępna opcja wyłączenia porad dotyczących zasad w trybie testowania. Zapewnia to elastyczność w zakresie włączonych w zasadach porad dotyczących zasad, a następnie decydowanie, czy mają być wyświetlane, czy pomijane podczas testowania.

![Opcja przetestowania zasad w pierwszej kolejności.](../media/DLP-create-test-tune-test-mode.png)

Na ekranie przeglądu końcowego kliknij przycisk **Utwórz** , aby zakończyć tworzenie zasad.

## <a name="test-a-dlp-policy"></a>Testowanie zasad DLP

Możesz poczekać, aż zasady zostaną wyzwolone przez normalne działanie użytkownika, lub możesz spróbować wyzwolić je samodzielnie. Wcześniej, który został przeze mnie połączony z definicjami jednostki [typu](sensitive-information-type-entity-definitions.md) informacji poufnych, który zawiera informacje na temat wyzwalania dopasowania funkcji DLP.

Na przykład zasady DLP utworzone dla tego artykułu wykryją australijskie numery plików podatkowych (TFN). Zgodnie z dokumentacją dopasowanie jest oparte na następujących kryteriach.

![Dokumentacja dotycząca numeru pliku podatkowego w Australii.](../media/DLP-create-test-tune-Australia-Tax-File-Number-doc.png)
 
Aby w dość błędny sposób pokazać wykrywanie sieci TFN, w wiadomości e-mail z wyrazami "Numer pliku podatkowego" i 9-cyfrowym ciągiem w zbliżeniu wypłynie bez żadnych problemów. Zasady DLP nie powodują wyzwolenia tego, że 9-cyfrowy ciąg musi przejść przez ciąg sprawdzany, który wskazuje, że jest prawidłową kartą TFN, a nie tylko nieszkodliwym ciągiem liczb.

![Numer pliku podatkowego Australia, który nie przejdzie sumy kontrolnej.](../media/DLP-create-test-tune-email-test1.png)

Dla porównania: wiadomość e-mail z wyrazami "Numer pliku podatkowego" i prawidłową politykę tfn, która przejdzie sprawdzanie, spowoduje wyzwolenie zasad. W przypadku rekordu w tym miejscu z witryny sieci Web, która generuje prawidłowe, ale nie oryginalnymi, sieci TFN, została generowana witryna internetowa. Takie witryny są przydatne, ponieważ jeden z najbardziej typowych błędów podczas testowania zasad DLP powoduje użycie fałszywej liczby, która jest nieprawdzia i nie przejdzie przez testy (dlatego nie wyzwoli tych zasad).

![Numer pliku podatkowego Australia przechodzący przez podsumowy.](../media/DLP-create-test-tune-email-test2.png)

Wiadomość e-mail raportu o zdarzeniu zawiera typ wykrytych informacji poufnych, informacje o tym, ile wystąpień zostało wykrytych i jaki jest poziom ufności wykrywania.

![Raport z incydentów pokazujący wykryty numer pliku podatkowego.](../media/DLP-create-test-tune-email-incident-report.png)

Jeśli pozostawisz zasady DLP w trybie testowania i przeanalizujesz wiadomości e-mail z raportu o zdarzeniu, możesz zacząć się chcieć sprawdzić dokładność zasad DLP i ich skuteczność po ich wymuszeniu. Oprócz raportów o incydentach można używać raportów funkcji [DLP](view-the-dlp-reports.md) w celu wyświetlania zagregowanego widoku dopasowania zasad w całej dzierżawie.

## <a name="tune-a-dlp-policy"></a>Dostosowywanie zasad DLP

Podczas analizowania trafień do zasad może być konieczne dostosowanie sposobu działania zasad. Jako prosty przykład można stwierdzić, że jedna grupa TFN w wiadomości e-mail nie stanowi problemu (wydaje mi się, że tak, ale przyjrzyjmy się jej w sposób pokazowy), ale co najmniej dwa wystąpienia mogą stanowić problem. Wiele wystąpień może stanowić ryzykowny scenariusz, na przykład sytuacja pracownika, który wysyła eksport pliku CSV z bazy danych kadr do strony zewnętrznej, na przykład zewnętrzną usługę księgowej. Zdecydowanie jest to preferowane do wykrycia i zablokowania.

W Centrum zgodności możesz edytować istniejące zasady, aby dostosować zachowanie.

![Opcja edycji zasad.](../media/DLP-create-test-tune-edit-policy.png)
 
Ustawienia lokalizacji można dostosować tak, aby zasady dotyczyły tylko określonych obciążeń albo określonych witryn i kont.

![Opcje wyboru konkretnych lokalizacji.](../media/DLP-create-test-tune-edit-locations.png)

Możesz także dostosować ustawienia zasad i edytować reguły, aby lepiej odpowiadały Twoim potrzebom.

![Opcja edycji reguły.](../media/DLP-create-test-tune-edit-rule.png)

Podczas edytowania reguły w ramach zasad DLP możesz zmienić:

- Warunki, w tym typ i liczba wystąpień poufnych danych, które będą wyzwalać regułę.
- Są to na przykład akcje ograniczające dostęp do zawartości.
- Powiadomienia użytkowników, czyli porady dotyczące zasad wyświetlane użytkownikowi w jego kliencie poczty e-mail lub przeglądarce internetowej.
- Użytkownik może zastąpić konto e-mail lub udostępnić plik, niezależnie od tego, czy może kontynuować udostępnianie poczty e-mail.
- Raporty o incydentach w celu powiadamiania administratorów.

![Opcje edycji części reguły.](../media/DLP-create-test-tune-editing-options.png)

W tym pokazie dodano do zasad powiadomienia użytkowników (należy uważać, aby nie zostały przemyślanie tego bez odpowiedniego szkolenia dla użytkowników) i zezwolić użytkownikom na zastąpienie tych zasad na uzasadnienie biznesowe lub oznaczanie ich jako fałszywie dodatnich. Możesz także dostosować tekst wiadomości e-mail i porad dotyczących zasad, jeśli chcesz dodać dodatkowe informacje na temat zasad organizacji, lub poprosić użytkowników o skontaktowanie się z pomocą techniczną, jeśli mają pytania.

![Opcje powiadomień i zastępować użytkowników.](../media/DLP-create-test-tune-user-notifications.png)

Te zasady zawierają dwie reguły obsługi dużej i niskiej głośności, dlatego należy edytować je zarówno z zastosowaniem akcji, jak i tych, które chcesz. Jest to możliwość traktowania spraw inaczej w zależności od ich cech. Na przykład możesz zezwolić na zastępowanie w przypadku naruszeń niskiego poziomu głośności, ale nie zezwolić na zastępowanie w przypadku naruszeń dużej ilości głośności.

![Jedna reguła dla dużej głośności i jedna reguła dla niskiej głośności.](../media/DLP-create-test-tune-two-rules.png)

Ponadto, jeśli chcesz faktycznie zablokować lub ograniczyć dostęp do zawartości, która jest narusza zasady, musisz skonfigurować w tym celu akcję na tej  regułie.

![Opcja ograniczenia dostępu do zawartości.](../media/DLP-create-test-tune-restrict-access-action.png)

Po zapisaniu tych zmian w ustawieniach zasad muszę także wrócić na stronę główną ustawień zasad i włączyć opcję pokazywania porad dotyczących zasad użytkownikom, gdy zasady są w trybie testowania. Jest to skuteczny sposób wprowadzania zasad ochrony przed zasadami ochrony przed zagrożeniami dla użytkowników końcowych i szkolenia dla użytkowników w zakresie zwiększania ich wiedzy bez ryzyka wystąpienia zbyt wielu wyników fałszywie dodatnich, które wpłyną na ich produktywność.

![Opcja pokazywania porad dotyczących zasad w trybie testowania.](../media/DLP-create-test-tune-show-policy-tips.png)

Zmiana po stronie serwera (lub po stronie chmury, jeśli wolisz) może nie zostać w związku z różnymi interwałami przetwarzania w poszczególnych interwałach przetwarzania. Jeśli wprowadzasz zmianę zasad DLP, która spowoduje wyświetlenie użytkownikowi nowych porad dotyczących zasad, zmiany te mogą nie zostać natychmiast wprowadzone w kliencie usługi Outlook, który sprawdza zmiany zasad co 24 godziny. Jeśli chcesz przyspieszyć testowanie, możesz użyć tej poprawki rejestru w celu wyczyszczenia ostatniej sygnatury czasowej pobierania z klucza [PolicyN różnych ustawień](https://support.microsoft.com/en-au/help/2823261/changes-to-a-data-loss-prevention-policy-don-t-take-effect-in-outlook?__hstc=18650278.46377037dc0a82baa8a30f0ef07a7b2f.1538687978676.1538693509953.1540315763430.3&__hssc=18650278.1.1540315763430&__hsfp=3446956451). Outlook zostaną pobrać najnowsze informacje o zasadach przy następnym jej ponownym uruchomieniu i rozpoczęciu pracy nad wiadomością e-mail.

Jeśli masz włączone porady dotyczące zasad, użytkownik zacznie widzieć porady w aplikacji Outlook i będzie miał możliwość zgłaszania wyników fałszywie dodatnich, gdy wystąpią.

![Porada co do zasad z opcją zgłaszania wyników fałszywie dodatnich.](../media/DLP-create-test-tune-policy-tip-in-outlook.png)

## <a name="investigate-false-positives"></a>Badanie wyników fałszywie dodatnich

Szablony zasad DLP nie są idealne od razu dostępne. Prawdopodobnie w Twoim środowisku zajdą wyniki fałszywie dodatnie, dlatego tak ważne jest, aby ułatwić sobie sposób wdrażania ochrony przed błędami DLP, co zabiera czas na odpowiednie testowanie i dostosowywanie zasad.

Oto przykład wyników fałszywie dodatnich. Ta wiadomość e-mail jest dość nieszkodliwa. Użytkownik udostępnia kimś swój numer telefonu komórkowego wraz z podpisem e-mail.

![Wiadomość e-mail z informacją fałszywie dodatnią.](../media/DLP-create-test-tune-false-positive-email.png)
 
Jednak użytkownik widzi poradę o zasadach z ostrzeżeniem, że wiadomość e-mail zawiera informacje poufne, w szczególności numer prawa jazdy w Australii.

![Opcja zgłaszania wyników fałszywie dodatnich w poradach co do zasad.](../media/DLP-create-test-tune-policy-tip-closeup.png)

Użytkownik może zgłosić wynik fałszywie dodatni, a administrator może sprawdzić, dlaczego tak się stało. W wiadomości e-mail raportu o zdarzeniu wiadomość e-mail jest oflagowana jako fałszywie dodatnia.

![Raport zdarzeń z wynikami fałszywie dodatnimi.](../media/DLP-create-test-tune-false-positive-incident-report.png)

Dobrym przykładem jest przypadek prawa jazdy. Przyczyną tego dodatniego błędu jest to, że typ "Australijskie prawo jazdy" zostanie wyzwolony przez dowolny 9-cyfrowy ciąg (nawet ten, który jest częścią ciągu 10-cyfrowego) w odległości 300 znaków od słów kluczowych "Sydney nsw" (bez rozróżnianie wielkości liter). Powoduje to wyzwolenie numeru telefonu i podpisu e-mail tylko dlatego, że użytkownik jest użytkownikiem z Sydney.


Jedną z opcji jest usunięcie z zasad typu danych australijskiego prawa jazdy. Znajduje się on w tym szablonie, ponieważ jest częścią szablonu zasad DLP, ale nie trzeba z niego korzystać. Jeśli interesuje Cię tylko numery plików podatkowych, a nie prawa jazdy, możesz je po prostu usunąć. Można na przykład usunąć ją z reguły niskiego woluminu w zasadach, ale pozostawić ją w trybie wysokiego głośności, dzięki czemu listy licencji z wieloma sterownikami będą nadal wykrywane.
 
Innym rozwiązaniem jest zwiększenie liczby wystąpień, tak aby niewielka liczba licencji sterownika była wykrywana tylko w przypadku wielu wystąpień.

![Opcja edycji liczby wystąpień.](../media/DLP-create-test-tune-edit-instance-count.png)

Oprócz zmiany liczby wystąpień można także dostosować dokładność dopasowania (czyli poziom ufności). Jeśli typ informacji poufnych ma wiele wzorców, możesz dopasować dokładność dopasowywania w regule tak, aby reguła była dopasowana tylko do określonych wzorców. Aby na przykład zmniejszyć liczbę wyników fałszywie dodatnich, można ustawić dokładność dopasowania reguły tak, aby była ona dopasowana tylko do wzorca o najwyższym poziomie ufności. Aby uzyskać więcej informacji na temat poziomów ufności, zobacz [Jak dostosować reguły przy użyciu poziomu ufności](data-loss-prevention-policies.md#match-accuracy).

Jeśli natomiast chcesz uzyskać jeszcze bardziej zaawansowane funkcje, możesz dostosować każdy typ informacji poufnych, na przykład usunąć nazwę "Sydney NSW" z listy słów kluczowych numeru prawa jazdy w Australii [, aby](sensitive-information-type-entity-definitions.md#australia-drivers-license-number) wyeliminować wynik fałszywie dodatni. Aby dowiedzieć się, jak to zrobić przy użyciu języka XML i programu PowerShell, zobacz Dostosowywanie wbudowanego typu informacji [poufnych](customize-a-built-in-sensitive-information-type.md).

## <a name="turn-on-a-dlp-policy"></a>Włączanie zasad DLP

Jeśli Twoje zasady DLP dokładnie i skutecznie wykrywają typy informacji poufnych oraz że twoi użytkownicy końcowi są gotowi do czynienia z obecnie działaniami zasad, możesz je włączyć.

![Opcja umożliwia włączenie zasad.](../media/DLP-create-test-tune-turn-on-policy.png)
 
Jeśli czekasz na ich stosowanie, zaczekaj na ich stosowanie, przekieruj Połączenie do programu [PowerShell](/powershell/exchange/connect-to-scc-powershell) centrum zabezpieczeń & i uruchom [polecenie cmdlet Get-DlpCompliancePolicy](/powershell/module/exchange/get-dlpcompliancepolicy), aby wyświetlić statystykę dystrybucji.

 ```powershell
 Get-DlpCompliancePolicy "Testing -Australia PII" -DistributionDetail | Select distributionstatus
 ```
Po włączeniu zasad DLP należy wykonać własne testy końcowe, aby upewnić się, że oczekiwane akcje zasad występują. Jeśli próbujesz przetestować takie dane jak dane kart kredytowych, w trybie online znajdują się witryny internetowe z informacjami na temat sposobu generowania przykładowej karty kredytowej lub innych informacji osobistych, które będą przechodzić przez sumy kontrolne i wyzwalać zasady.

Zasady umożliwiające zastępowanie użytkowników będą przedstawiać tę opcję użytkownikowi w ramach porady dotyczącej zasad.

![Porada o zasadach umożliwiająca użytkownikom zastępowanie.](../media/DLP-create-test-tune-override-option.png)

Zasady ograniczające zawartość będą przedstawiały ostrzeżenie użytkownikowi w ramach porady dotyczącej zasad i nie mogą wysyłać wiadomości e-mail.

![Porada zasad oznacza, że zawartość jest ograniczona.](../media/DLP-create-test-tune-restrict-warning.png)

## <a name="summary"></a>Podsumowanie

Zasady ochrony przed utratą danych są przydatne w organizacjach wszystkich typów. Testowanie niektórych zasad DLP jest ćwiczeniami o niskim ryzyku ze względu na posiadaną kontrolę nad sprawami, np. poradami dotyczącymi zasad, zastępowaniem użytkowników końcowych i raportami o incydentach. Możesz w ciszy przetestować niektóre zasady ochrony przed naruszeniem, aby sprawdzić, jakiego typu naruszenia już występują w Twojej organizacji, a następnie tworzyć zasady o niskich stawkach fałszywie dodatnich, kształć użytkowników w zakresie dozwolonych, a nie dozwolonych, a następnie wytworzyć zasady ochrony przed naruszeniem wartości w organizacji.
