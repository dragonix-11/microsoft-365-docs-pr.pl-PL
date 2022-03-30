---
title: Korzystanie z ochrony przed utratą danych w punkcie końcowym
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
description: Dowiedz się, jak skonfigurować zasady ochrony przed utratą danych (DLP) w celu używania Microsoft 365 lokalizacji ochrony przed utratą danych (EPDLP, Endpoint Data Loss Prevention).
ms.openlocfilehash: aeb85b883738e94f2d7161cb2bc3434edbb16428
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680033"
---
# <a name="using-endpoint-data-loss-prevention"></a>Korzystanie z ochrony przed utratą danych w punkcie końcowym

Aby ułatwić Ci zapoznanie się z funkcjami DLP w punktach końcowych i ich działaniami w zasadach ochrony przed zasadami DLP, znajdziesz w nim kilka scenariuszy do obserwowania.

> [!IMPORTANT]
> Te scenariusze ochrony przed dlp punktu końcowego nie są oficjalnymi procedurami tworzenia i dostosowywania zasad DLP. Aby pracować z zasadami ochrony przed zasadami DLP w sytuacjach ogólnych, zapoznaj się z poniższymi tematami:
>
>- [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md)
>- [Wprowadzenie do domyślnych zasad DLP](get-started-with-the-default-dlp-policy.md)
>- [Tworzenie zasad DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md)
>- [Tworzenie, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md)

## <a name="scenario-1-create-a-policy-from-a-template-audit-only"></a>Scenariusz 1. Tworzenie zasad na podstawie szablonu, tylko inspekcja

Te scenariusze wymagają, aby urządzenia były już podłączone i raportowane w Eksploratorze aktywności. Jeśli urządzenia nie zostały jeszcze na nim podłączone, zobacz Wprowadzenie do ochrony przed utratą danych [w punkcie końcowym](endpoint-dlp-getting-started.md).

1. Otwórz stronę [Ochrona przed utratą danych](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Wybierz **pozycję Utwórz zasady**.

3. W tym scenariuszu wybierz pozycję **Prywatność**, a następnie Dane umożliwiające identyfikację użytkownika **(PII)** w Stanach Zjednoczonych, a następnie wybierz pozycję **Dalej**.

4. Wyłącz pole **Stan dla** wszystkich lokalizacji z wyjątkiem **urządzeń**. Wybierz przycisk **Dalej**.

5. Zaakceptuj ustawienia domyślne **Przejrzyj i dostosuj ustawienia z wyboru szablonu** , a następnie wybierz przycisk **Dalej**.

6. Zaakceptuj domyślne wartości **akcji ochrony i** wybierz przycisk **Dalej**.

7. Wybierz **pozycję Inspekcja lub ograniczanie działań na Windows urządzeniach** i pozostaw akcje ustawione na Tylko **inspekcja**. Wybierz przycisk **Dalej**.

8. Zaakceptuj ustawienie domyślne **, które chcę przetestować** jako pierwszą wartość, a następnie wybierz pozycję **Pokaż porady dotyczące zasad w trybie testowania**. Wybierz przycisk **Dalej**.

9. Przejrzyj ustawienia i wybierz pozycję **Prześlij**.

10. Nowe zasady DLP zostaną wyświetlone na liście zasad.

11. Sprawdź, czy w Eksploratorze aktywności nie ma danych z monitorowanych punktów końcowych. Ustaw filtr lokalizacji dla urządzeń i dodaj zasady, a następnie filtruj według nazw zasad, aby zobaczyć wpływ tych zasad. zobacz [Wprowadzenie do Eksploratora aktywności](data-classification-activity-explorer.md), jeśli to konieczne.

12. Spróbuj udostępnić element testowy zawierający zawartość, która wyzwoli warunek danych umożliwiających identyfikację użytkownika (PII) w Stanach Zjednoczonych osobie spoza organizacji. Powinno to wyzwolić zasady.

13. Sprawdź w Eksploratorze aktywności zdarzenie.

## <a name="scenario-2-modify-the-existing-policy-set-an-alert"></a>Scenariusz 2. Modyfikowanie istniejących zasad i ustawianie alertu

1. Otwórz stronę [Ochrona przed utratą danych](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Wybierz zasady **danych umożliwiających identyfikację użytkownika (PII)** utworzone w scenariuszu 1.

3. Wybierz **pozycję Edytuj zasady**.

4. Przejdź do strony **Advanced DLP rules** (Zaawansowane reguły DLP) i edytuj stan **inf** (Niska ilość zawartości wykrytej jako identyfikowalna danych osobowych Stanów Zjednoczonych).

5. Przewiń w dół do sekcji **Raporty o incydentach** i ustaw dla administratorów ustawienie **Wysyłaj alert** , gdy wystąpi dopasowanie reguły do **pozycji Wł**. Alerty e-mail będą automatycznie wysyłane do administratora i wszystkich innych osób, które dodasz do listy adresatów. 

![włączanie raportów o zdarzeniu.](../media/endpoint-dlp-2-using-dlp-incident-reports.png)
   
6. Na potrzeby tego scenariusza wybierz pozycję Wyślij alert za każdym razem, **gdy działanie będzie odpowiadać reguły**.

7. Wybierz pozycję **Zapisz**.

8. Zachowaj wszystkie poprzednie ustawienia, wybierając przycisk **Dalej** , a **następnie pozycję Prześlij** zmiany zasad.

9. Spróbuj udostępnić element testowy zawierający zawartość, która wyzwoli warunek danych umożliwiających identyfikację użytkownika (PII) w Stanach Zjednoczonych osobie spoza organizacji. Powinno to wyzwolić zasady.

10. Sprawdź w Eksploratorze aktywności zdarzenie.

## <a name="scenario-3-modify-the-existing-policy-block-the-action-with-allow-override"></a>Scenariusz 3. Modyfikowanie istniejących zasad, blokowanie akcji za pomocą zastępowania zezwalania

1. Otwórz stronę [Ochrona przed utratą danych](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Wybierz zasady **danych umożliwiających identyfikację użytkownika (PII)** utworzone w scenariuszu 1.

3. Wybierz **pozycję Edytuj zasady**.

4. Przejdź do strony **Advanced DLP rules** (Zaawansowane reguły DLP) i edytuj stan **inf** (Niska ilość zawartości wykrytej jako identyfikowalna danych osobowych Stanów Zjednoczonych).

5. Przewiń w dół do sekcji **Inspekcja lub ograniczanie działań na Windows** urządzeniach i dla każdego działania ustaw odpowiednią akcję **Zablokuj z zastępowaniem**.

   > [!div class="mx-imgBorder"]
   > ![ustaw blok z akcją zastępowania.](../media/endpoint-dlp-6-using-dlp-set-blocked-with-override.png)
   
6. Wybierz pozycję **Zapisz**.

7. Powtórz kroki od 4 do 7 w przypadku dużej ilości zawartości wykrytej w **U.S. Personally Identifiable Inf**.

8. Zachowaj wszystkie poprzednie ustawienia, wybierając przycisk **Dalej** , a **następnie pozycję Prześlij** zmiany zasad.

9. Spróbuj udostępnić element testowy zawierający zawartość, która wyzwoli warunek danych umożliwiających identyfikację użytkownika (PII) w Stanach Zjednoczonych osobie spoza organizacji. Powinno to wyzwolić zasady.

   Na urządzeniu klienckim pojawi się takie wyskakujące okienko:

   > [!div class="mx-imgBorder"]
   > ![Powiadomienie o zablokowanym kliencie dlp punktu końcowego.](../media/endpoint-dlp-3-using-dlp-client-blocked-override-notification.png)

10. Sprawdź w Eksploratorze aktywności zdarzenie.

## <a name="scenario-4-avoid-looping-dlp-notifications-from-cloud-synchronization-apps-with-auto-quarantine-preview"></a>Scenariusz 4. Unikanie w pętli powiadomień DLP z aplikacji do synchronizacji chmury z automatycznym kwarantanną (wersja zapoznawcza)

### <a name="before-you-begin"></a>Przed rozpoczęciem

W tym scenariuszu synchronizowanie plików z etykietą poufności **Wysoce** poufne OneDrive jest blokowane. Jest to złożony scenariusz z wieloma składnikami i procedurami. Potrzebne są:

- Konto AAD docelowe i komputer Windows 10, który już synchronizuje lokalny folder poczty OneDrive z magazynem OneDrive w chmurze.
- Microsoft Word na komputerze docelowym Windows 10 komputera
- Skonfigurowane i opublikowane etykiety wrażliwości — zobacz [Wprowadzenie do](get-started-with-sensitivity-labels.md#get-started-with-sensitivity-labels) etykiet wrażliwości oraz [Tworzenie i konfigurowanie etykiet wrażliwości oraz ich zasad](create-sensitivity-labels.md#create-and-configure-sensitivity-labels-and-their-policies).

Istnieją trzy procedury.

1. Skonfiguruj ustawienia punktu końcowego DLP do automatycznej kwarantanny.
2. Tworzenie zasad blokowania elementów poufnych, które mają **etykietę Poufność** wysoce poufna.
3. Utwórz dokument programu Word na urządzeniu Windows 10, na które są kierowane zasady, zastosuj etykietę i skopiuj ją do lokalnego folderu poczty OneDrive użytkowników, który jest synchronizowany.  

### <a name="configure-endpoint-dlp-unallowed-app-and-auto-quarantine-settings"></a>Konfigurowanie aplikacji usługi DLP dla punktu końcowego i ustawień automatycznej kwarantanny

1. Otwórz [ustawienia ochrony przed DLP punktu końcowego](https://compliance.microsoft.com/datalossprevention?viewid=globalsettings)

2. **Rozwiń niezaszepowane aplikacje**.

3. Wybierz **pozycję Dodaj lub** edytuj aplikacje niedozwolone *i* dodaj program OneDrive jako nazwę wyświetlaną oraz plik wykonywalny *onedrive.exe*, aby nie zezwalać onedrive.exe na dostęp do elementów etykiety **Wysoce poufne.**

4. Wybierz **pozycję Automatycznie poddaj kwarantannie i** **zapisz**.

5. W **obszarze Ustawienia auto kwarantanny wybierz** **pozycję Edytuj ustawienia auto kwarantanny**.

6. Włącz **automatyczne kwarantannę dla aplikacji niezaszepłanych**.

7. Wprowadź ścieżkę do folderu na komputerach lokalnych, do którego chcesz przenieść oryginalne poufne pliki. Przykład:
   
    **Element "%homedrive%%homepath%\Microsoft DLP\Quarantine"** dla użytkownika *Isaiah langer* będzie umieszczał przeniesione elementy w folderze o nazwie:  

    *C:\Użytkownicy\IsaiahLanger\Microsoft DLP\Quarantine\OneDrive*

    i dołącz sygnaturę daty i czasu do oryginalnej nazwy pliku.
    
    > [!NOTE]
    > Funkcja automatycznego kwarantanny DLP utworzy podfoldery dla plików dla każdej aplikacji, która nie została odblokowana. Jeśli na liście *nie Notatnik* aplikacji znajduje się zarówno folder *Notatnik*, jak i folder OneDrive, zostanie utworzony podfolder dla folderu **\OneDrive, a** inny podfolder dla folderu **\Notatnik**.

8. Wybierz **pozycję Zamień pliki na plik .txt zawierający** następujący tekst, a następnie wprowadź odpowiedni tekst w pliku zastępczym. Na przykład w przypadku pliku o *nazwie Autokwartyl 1.docx*:
    
    > Plik %%FileName%% zawiera informacje poufne, które twoja organizacja chroni za pomocą zasad ochrony przed utratą danych (DLP) %%PolicyName%% i została przeniesiona do folderu kwarantanny: %%QuarantinePath%%
    
    pozostawi plik tekstowy zawierający ten komunikat:
    
    > Autokwartyl 1.docx zawiera informacje poufne, które twoja organizacja chroni za pomocą zasad ochrony przed utratą danych (DLP), i została przeniesiona do folderu kwarantanny: C:\Użytkownicy\IsaiahLanger\Microsoft DLP\Quarantine\OneDrive\autokwartyl 1_20210728_151541.docx.

9. Wybierz **pozycję Save (Zapisz).**

### <a name="configure-a-policy-to-block-onedrive-synchronization-of-files-with-the-sensitivity-label-highly-confidential"></a>Konfigurowanie zasad w celu blokowania synchronizacji OneDrive plików z etykietą poufności Wysoce poufne

1. Otwórz stronę [Ochrona przed utratą danych](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Wybierz **pozycję Utwórz zasady**.

3. W tym scenariuszu wybierz pozycję **Zasady** niestandardowe, a następnie **pozycję Zasady niestandardowe** i pozycję **Dalej**.

4. Wypełnij pola **Nazwa i** **Opis** i wybierz przycisk **Dalej**.

5. Wyłącz pole **Stan dla** wszystkich lokalizacji z wyjątkiem **urządzeń**. Jeśli masz określone konto użytkownika końcowego, z którego chcesz to sprawdzić, wybierz je w zakresie. Wybierz przycisk **Dalej**.

6. Zaakceptuj domyślną opcję **Utwórz lub dostosuj zaawansowane reguły DLP** i wybierz przycisk **Dalej**.

7. Utwórz regułę z tymi wartościami:
    1. **Nazwa** >  *Scenariusz 4. Automatyczne poddaj kwarantannie*.
    1. **Warunki** >  **Zawartość zawiera** >  **Etykiety wrażliwości** >  **Wysoce poufne**.
    1.  **Akcje** >  **Inspekcja lub ograniczanie działań na Windows Dostęp** >  **przez aplikacje** **niedozwoloneBlok.** >  Na potrzeby tego scenariusza wyczyść wszystkie pozostałe działania.
    1. **Powiadomienia użytkownika** >  **Wł**.
    1. **Urządzenia punktu końcowego** > Wybierz pozycję Pokaż użytkownikom powiadomienie z poradą o **zasadach, jeśli działanie nie** zostało jeszcze włączone.
    
8. Wybierz **pozycję Zapisz i** **dalej**.

9. Wybierz **pozycję Włącz od razu**. Wybierz przycisk **Dalej**.

10. Przejrzyj ustawienia i wybierz pozycję **Prześlij**.

    > [!NOTE]
    > Zezwalaj na replikowanie nowych zasad i ich zastosowanie do komputera docelowego Windows 10 godzinę.

11. Nowe zasady DLP zostaną wyświetlone na liście zasad.

### <a name="test-auto-quarantine-on-the-windows-10-device"></a>Testowanie automatycznego kwarantanny na Windows 10 urządzenia

1. Zaloguj się do komputera Windows 10 przy użyciu konta użytkownika określonego w kroku 5 konfigurowania zasad w celu blokowania OneDrive synchronizacji plików z etykietą poufności [Wysoce poufne.](#configure-a-policy-to-block-onedrive-synchronization-of-files-with-the-sensitivity-label-highly-confidential)

2. Utwórz folder, którego zawartość nie będzie synchronizowana z folderem OneDrive. Przykład:

    *C:\folder źródłowy autodeks kwarantanny*

3. Otwórz Microsoft Word i utwórz plik w folderze źródłowym autodeks kwarantanny. Stosowanie **etykiety Wysoce poufne** poufność. zobacz [Stosowanie etykiet wrażliwości do plików i wiadomości e-mail w Office](https://support.microsoft.com/topic/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).

4. Skopiuj właśnie utworzony plik do folderu OneDrive synchronizacji. Powinien zostać wyświetlony wyskakujące powiadomienie użytkownika z informacją, że akcja nie jest dozwolona i że plik zostanie poddany kwarantannie. Na przykład w przypadku nazwy użytkownika *Izaiah Langer* i dokumentu zatytułowanego autodadeksuj dokument 1.docxzostanie wyświetlony ten komunikat:**

    ![Okienko podręczne z powiadomieniem użytkownika ochrony przed utratą danych z informacją OneDrive że akcja synchronizacji danych nie jest dozwolona dla określonego pliku i że plik zostanie poddany kwarantannie.](../media/auto-quarantine-user-notification-toast.png)
    
    Zostanie wyświetlony komunikat:
    
    > Otwieranie autokwadranowego 1.docx za pomocą tej aplikacji nie jest dozwolone. Plik zostanie poddany kwarantannie w folderze "C:\Użytkownicy\IsaiahLanger\Microsoft DLP\OneDrive"

5. Wybierz **pozycję Odrzuć**.

6. Otwórz plik tekstowy uchwytu miejsca. Będzie on nosił nazwę **autodadeksu do kwarantanny 1.docx_ *date_time*.txt**. 

7. Otwórz folder kwarantanny i upewnij się, że znajduje się tam oryginalny plik.
 
8. Sprawdź, czy w Eksploratorze aktywności nie ma danych z monitorowanych punktów końcowych. Ustaw filtr lokalizacji dla urządzeń i dodaj zasady, a następnie filtruj według nazw zasad, aby zobaczyć wpływ tych zasad. zobacz [Wprowadzenie do Eksploratora aktywności](data-classification-activity-explorer.md), jeśli to konieczne.

9. Sprawdź w Eksploratorze aktywności zdarzenie.

## <a name="scenario-5-restrict-unintentional-sharing-to-unallowed-cloud-apps-and-services"></a>Scenariusz 5. Ograniczanie niezamierzonego udostępniania do aplikacji i usług w chmurze, które nie są niedozwolone

Dzięki zasadom DLP w punkcie końcowym i przeglądarce internetowej Microsoft Edge możesz ograniczyć niezamierzone udostępnianie elementów poufnych do aplikacji i usług w chmurze, które nie są niedozwolone. Program Edge rozumie, kiedy element jest ograniczony przez zasady DLP punktu końcowego i wymusza ograniczenia dostępu.

Po wybraniu pozycji  Urządzenia jako lokalizacji w prawidłowo skonfigurowanych zasadach DLP i użyciu przeglądarki Microsoft Edge niedozwolone przeglądarki zdefiniowane w tych ustawieniach nie będą mieć dostępu do poufnych elementów, które są zgodne z kontrolkami zasad DLP. Zamiast tego użytkownicy będą przekierowywani do używania aplikacji Microsoft Edge które, wraz ze zrozumieniem nałożonych ograniczeń ochrony przed zasadami DLP, mogą blokować lub ograniczać działania, gdy zostaną spełnione warunki zasad DLP.

Aby użyć tego ograniczenia, musisz skonfigurować trzy ważne elementy:

1. Określ miejsca — usługi, domeny, adresy IP — w przypadku których chcesz zapobiec udostępnianiu poufnych elementów.

2. Dodaj przeglądarki, które nie mają dostępu do określonych elementów poufnych w przypadku wystąpienia dopasowania zasad DLP.

3. Skonfiguruj zasady DLP w celu zdefiniowania rodzajów elementów poufnych, dla których przekazywanie powinno być ograniczone do tych miejsc, włączając usługę **Upload** do usług w chmurze i dostęp z wszelkiej **przeglądarki**.

Możesz nadal dodawać nowe usługi, aplikacje i zasady, aby rozszerzać i rozszerzać ograniczenia w celu zaspokojenia potrzeb biznesowych i ochrony poufnych danych. 

Dzięki tej konfiguracji dane pozostają bezpieczne, a jednocześnie nie trzeba ograniczać niepotrzebnych ograniczeń uniemożliwiających użytkownikom uzyskiwanie dostępu do elementów nie poufnych i udostępnianie ich.
## <a name="see-also"></a>Zobacz też

- [Informacje na temat ochrony przed utratą danych w punkcie końcowym](endpoint-dlp-learn-about.md)
- [Wprowadzenie do ochrony przed utratą danych w punkcie końcowym](endpoint-dlp-getting-started.md)
- [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md)
- [Tworzenie, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md)
- [Wprowadzenie do Eksploratora aktywności](data-classification-activity-explorer.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/)
- [Omówienie dołączania Windows 10 i Windows 11 Microsoft 365 urządzeniach](/microsoft-365/compliance/device-onboarding-overview)
- [Microsoft 365 subskrypcji](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure Active Directory (AAD)](/azure/active-directory/devices/concept-azure-ad-join)
- [Pobierz nowy Microsoft Edge na podstawie Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
- [Wprowadzenie do domyślnych zasad DLP](get-started-with-the-default-dlp-policy.md)
- [Tworzenie zasad DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md)
