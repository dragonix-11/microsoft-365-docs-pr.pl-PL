---
title: Korzystanie z protokołu DLP punktu końcowego
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
description: Dowiedz się, jak skonfigurować zasady ochrony przed utratą danych (DLP) w celu używania lokalizacji zapobiegania utracie danych punktu końcowego.
ms.openlocfilehash: 9107759e137d7b8dd86253f9c6567b76686d2518
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632382"
---
# <a name="using-endpoint-data-loss-prevention"></a>Korzystanie z ochrony przed utratą danych punktu końcowego

Aby ułatwić zapoznanie się z funkcjami DLP punktu końcowego i sposobem ich wyświetlania w zasadach DLP, przygotowaliśmy kilka scenariuszy do wykonania.

> [!IMPORTANT]
> Te scenariusze DLP punktu końcowego nie są oficjalnymi procedurami tworzenia i dostrajania zasad DLP. Zapoznaj się z poniższymi tematami, gdy musisz pracować z zasadami DLP w ogólnych sytuacjach:
>
>- [Dowiedz się więcej o Ochrona przed utratą danych w Microsoft Purview](dlp-learn-about-dlp.md)
>- [Wprowadzenie do domyślnych zasad DLP](get-started-with-the-default-dlp-policy.md)
>- [Twórz zasady DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md)
>- [Twórz, testuj i dostrajaj zasady DLP](create-test-tune-dlp-policy.md)

## <a name="scenario-1-create-a-policy-from-a-template-audit-only"></a>Scenariusz 1. Tworzenie zasad na podstawie szablonu, tylko inspekcja

Te scenariusze wymagają, aby urządzenia były już dołączone i raportowane w Eksploratorze działań. Jeśli urządzenia nie zostały jeszcze dołączone, zobacz [Wprowadzenie do zapobiegania utracie danych punktu końcowego](endpoint-dlp-getting-started.md).

1. Otwórz [stronę Zapobieganie utracie danych](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Wybierz **pozycję Utwórz zasady**.

3. W tym scenariuszu wybierz pozycję **Prywatność**, a następnie **dane osobowe (PII) w Stanach Zjednoczonych** i wybierz pozycję **Dalej**.

4. Przełącz pole **Stan** na wyłączone dla wszystkich lokalizacji z wyjątkiem **urządzeń**. Wybierz przycisk **Dalej**.

5. Zaakceptuj domyślne **ustawienie Przejrzyj i dostosuj ustawienia z wyboru szablonu** , a następnie wybierz pozycję **Dalej**.

6. Zaakceptuj domyślne wartości **akcji ochrony** i wybierz pozycję **Dalej**.

7. Wybierz pozycję **Inspekcja lub ograniczanie działań na urządzeniach z systemem Windows** i pozostaw akcje ustawione **tylko na Wartość Inspekcja**. Wybierz przycisk **Dalej**.

8. Zaakceptuj wartość domyślną **Chcę przetestować ją jako pierwszą** wartość i wybrać pozycję **Pokaż wskazówki dotyczące zasad w trybie testowym**. Wybierz przycisk **Dalej**.

9. Przejrzyj ustawienia i wybierz pozycję **Prześlij**.

10. Nowe zasady DLP pojawią się na liście zasad.

11. Sprawdź Eksploratora działań pod kątem danych z monitorowanych punktów końcowych. Ustaw filtr lokalizacji dla urządzeń i dodaj zasady, a następnie filtruj według nazwy zasad, aby zobaczyć wpływ tych zasad; Zobacz [Wprowadzenie do eksploratora działań](data-classification-activity-explorer.md), jeśli to konieczne.

12. Spróbuj udostępnić element testowy zawierający zawartość, która spowoduje wyzwolenie warunku danych osobowych (PII) w Stanach Zjednoczonych osobie spoza organizacji. Powinno to wyzwolić zasady.

13. Sprawdź Eksploratora działań pod kątem zdarzenia.

## <a name="scenario-2-modify-the-existing-policy-set-an-alert"></a>Scenariusz 2. Modyfikowanie istniejących zasad, ustawianie alertu

1. Otwórz [stronę Zapobieganie utracie danych](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Wybierz zasady **danych osobowych (PII)** utworzone w scenariuszu 1.

3. Wybierz **pozycję Edytuj zasady**.

4. Przejdź do strony **Zaawansowane reguły DLP** i edytuj plik **Inf o niskiej liczbie wykrytej zawartości w Stanach Zjednoczonych**.

5. Przewiń w dół do sekcji **Raporty o zdarzeniach** i ustaw **pozycję Wyślij alert do administratorów, gdy wystąpi dopasowanie reguły** do pozycji **Włączone**. Alerty e-mail będą automatycznie wysyłane do administratora i wszystkich innych osób dodanych do listy adresatów. 

![włączanie raportów o zdarzeniach.](../media/endpoint-dlp-2-using-dlp-incident-reports.png)
   
6. Na potrzeby tego scenariusza wybierz pozycję **Wyślij alert za każdym razem, gdy działanie jest zgodne z regułą**.

7. Wybierz pozycję **Zapisz**.

8. Zachowaj wszystkie poprzednie ustawienia, wybierając pozycję **Dalej** , a następnie **prześlij** zmiany zasad.

9. Spróbuj udostępnić element testowy zawierający zawartość, która spowoduje wyzwolenie warunku danych osobowych (PII) w Stanach Zjednoczonych osobie spoza organizacji. Powinno to wyzwolić zasady.

10. Sprawdź Eksploratora działań pod kątem zdarzenia.

## <a name="scenario-3-modify-the-existing-policy-block-the-action-with-allow-override"></a>Scenariusz 3. Modyfikowanie istniejących zasad, blokowanie akcji za pomocą przesłonięcia zezwalania

1. Otwórz [stronę Zapobieganie utracie danych](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Wybierz zasady **danych osobowych (PII)** utworzone w scenariuszu 1.

3. Wybierz **pozycję Edytuj zasady**.

4. Przejdź do strony **Zaawansowane reguły DLP** i edytuj plik **Inf o niskiej liczbie wykrytej zawartości w Stanach Zjednoczonych**.

5. Przewiń w dół do sekcji **Inspekcja lub ograniczanie działań na urządzeniu z systemem Windows** i dla każdego działania ustaw odpowiednią akcję na  **Wartość Blokuj z przesłonięciem**.

   > [!div class="mx-imgBorder"]
   > ![ustaw blok z akcją zastąpienia.](../media/endpoint-dlp-6-using-dlp-set-blocked-with-override.png)
   
6. Wybierz pozycję **Zapisz**.

7. Powtórz kroki 4–7 dla **dużej ilości wykrytej zawartości W Stanach Zjednoczonych— inf z możliwością identyfikacji osobistej**.

8. Zachowaj wszystkie poprzednie ustawienia, wybierając pozycję **Dalej** , a następnie **prześlij** zmiany zasad.

9. Spróbuj udostępnić element testowy zawierający zawartość, która spowoduje wyzwolenie warunku danych osobowych (PII) w Stanach Zjednoczonych osobie spoza organizacji. Powinno to wyzwolić zasady.

   Na urządzeniu klienckim zostanie wyświetlone takie okno podręczne:

   > [!div class="mx-imgBorder"]
   > ![powiadomienie o przesłonięciach zablokowane przez klienta programu endpoint dlp.](../media/endpoint-dlp-3-using-dlp-client-blocked-override-notification.png)

10. Sprawdź Eksploratora działań pod kątem zdarzenia.

## <a name="scenario-4-avoid-looping-dlp-notifications-from-cloud-synchronization-apps-with-auto-quarantine-preview"></a>Scenariusz 4. Unikanie zapętlania powiadomień DLP z aplikacji synchronizacji w chmurze za pomocą automatycznej kwarantanny (wersja zapoznawcza)

### <a name="before-you-begin"></a>Przed rozpoczęciem

W tym scenariuszu synchronizacja plików z etykietą **poufności o wysokim poziomie poufności** z usługą OneDrive jest zablokowana. Jest to złożony scenariusz z wieloma składnikami i procedurami. Potrzebne będą następujące elementy:

- Konto użytkownika usługi AAD do docelowego i dołączony komputer Windows 10, który już synchronizuje lokalny folder usługi OneDrive z magazynem w chmurze usługi OneDrive.
- Program Microsoft Word zainstalowany na docelowym komputerze Windows 10
- Etykiety poufności skonfigurowane i opublikowane — zobacz [Wprowadzenie do etykiet poufności](get-started-with-sensitivity-labels.md#get-started-with-sensitivity-labels) oraz [Tworzenie i konfigurowanie etykiet poufności i ich zasad](create-sensitivity-labels.md#create-and-configure-sensitivity-labels-and-their-policies).

Istnieją trzy procedury.

1. Skonfiguruj ustawienia automatycznego kwarantanny DLP punktu końcowego.
2. Utwórz zasady, które blokują poufne elementy, które mają etykietę **poufności o wysokim poziomie poufności** .
3. Utwórz dokument programu Word na urządzeniu Windows 10, do których są przeznaczone zasady, zastosuj etykietę i skopiuj go do lokalnego folderu usługi OneDrive, który jest synchronizowany na kontach użytkowników.  

### <a name="configure-endpoint-dlp-unallowed-app-and-auto-quarantine-settings"></a>Konfigurowanie nieobsługiwanej aplikacji punktu końcowego DLP i ustawień automatycznej kwarantanny

1. [Otwieranie ustawień DLP punktu końcowego](https://compliance.microsoft.com/datalossprevention?viewid=globalsettings)

2. Rozwiń węzeł **Aplikacje niezaurzane**.

3. Wybierz pozycję **Dodaj lub edytuj niedozwolone aplikacje** i dodaj usługę *OneDrive* jako nazwę wyświetlaną i nazwę wykonywalną *onedrive.exe*  , aby uniemożliwić onedrive.exe uzyskiwanie dostępu do elementów **etykiety Wysoce poufne** .

4. Wybierz pozycję **Automatyczna kwarantanna** i **Zapisz**.

5. W obszarze **Ustawienia automatycznego kwarantanny** wybierz pozycję **Edytuj ustawienia automatycznego kwarantanny**.

6. Włącz **automatyczną kwarantannę dla niedozwolonych aplikacji**.

7. Wprowadź ścieżkę do folderu na maszynach lokalnych, do którego mają zostać przeniesione oryginalne pliki poufne. Przykład:
   
    **"%homedrive%%homepath%\Microsoft DLP\Quarantine"** dla nazwy użytkownika *Isaiah langer* umieści przeniesione elementy w folderze o nazwie:  

    *C:\Users\IsaiahLanger\Microsoft DLP\Quarantine\OneDrive*

    i dołącz datę i sygnaturę czasową do oryginalnej nazwy pliku.
    
    > [!NOTE]
    > Automatyczna kwarantanna DLP spowoduje utworzenie podfolderów dla plików dla każdej niedozwolonej aplikacji. Jeśli więc na liście nieobjętych aplikacji znajdują się zarówno *Notatnik* , jak i *OneDrive* , dla **\OneDrive zostanie utworzony podfolder \OneDrive** i inny **podfolder \Notatnik**.

8. Wybierz **pozycję Zastąp pliki pliki .txt zawierającym następujący tekst** i wprowadź tekst, który chcesz w pliku zastępczym. Na przykład dla pliku o nazwie *auto quar 1.docx*:
    
    > %%Nazwa_pliku%% zawiera poufne informacje, które twoja organizacja chroni przy użyciu zasad ochrony przed utratą danych (DLP) %%PolicyName%% i została przeniesiona do folderu kwarantanny: %%QuarantinePath%%
    
    Spowoduje to pozostawienie pliku tekstowego zawierającego następujący komunikat:
    
    > auto quar 1.docx zawiera poufne informacje, które organizacja chroni za pomocą zasad ochrony przed utratą danych (DLP) i została przeniesiona do folderu kwarantanny: C:\Users\IsaiahLanger\Microsoft DLP\Quarantine\OneDrive\auto quar 1_20210728_151541.docx.

9. Wybierz **pozycję Zapisz**

### <a name="configure-a-policy-to-block-onedrive-synchronization-of-files-with-the-sensitivity-label-highly-confidential"></a>Konfigurowanie zasad w celu blokowania synchronizacji plików w usłudze OneDrive z etykietą poufności Wysoce poufne

1. Otwórz [stronę Zapobieganie utracie danych](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Wybierz **pozycję Utwórz zasady**.

3. W tym scenariuszu wybierz pozycję **Niestandardowe**, a następnie **zasady niestandardowe** i wybierz pozycję **Dalej**.

4. Wypełnij pola **Nazwa** i **Opis** , a następnie wybierz pozycję **Dalej**.

5. Przełącz pole **Stan** na wyłączone dla wszystkich lokalizacji z wyjątkiem **urządzeń**. Jeśli masz określone konto użytkownika końcowego, z których chcesz to przetestować, wybierz je w zakresie. Wybierz przycisk **Dalej**.

6. Zaakceptuj domyślny wybór **opcji Utwórz lub dostosuj zaawansowane reguły DLP** , a następnie wybierz pozycję **Dalej**.

7. Utwórz regułę z następującymi wartościami:
    1. **Nazwa** >  *Scenariusz 4 Automatyczna kwarantanna*.
    1. **Warunki** >  **Zawartość zawiera** >  **Etykiety** >  poufności **Wysoce poufne**.
    1.  **Działania** >  **Inspekcja lub ograniczanie działań na urządzeniach z systemem** >  Windows **Dostęp przez niedozwolone aplikacje** >  **Blokuj**. Na potrzeby tego scenariusza wyczyść wszystkie inne działania.
    1. **Powiadomienia użytkowników** >  **Włączone**.
    1. **Urządzenia punktu końcowego** > wybierz **pozycję Pokaż użytkownikom powiadomienie o poradach dotyczących zasad, jeśli działanie** nie zostało jeszcze włączone.
    
8. Wybierz **pozycję Zapisz** i **dalej**.

9. Wybierz pozycję **Włącz od razu**. Wybierz przycisk **Dalej**.

10. Przejrzyj ustawienia i wybierz pozycję **Prześlij**.

    > [!NOTE]
    > Zezwalaj co najmniej godzinę na replikowanie nowych zasad i stosowanie ich do docelowego komputera Windows 10.

11. Nowe zasady DLP pojawią się na liście zasad.

### <a name="test-auto-quarantine-on-the-windows-10-device"></a>Testowanie automatycznej kwarantanny na urządzeniu Windows 10

1. Zaloguj się na komputerze Windows 10 przy użyciu konta użytkownika określonego w artykule [Konfigurowanie zasad w celu blokowania synchronizacji plików w usłudze OneDrive przy użyciu etykiety poufności Wysoce poufne](#configure-a-policy-to-block-onedrive-synchronization-of-files-with-the-sensitivity-label-highly-confidential) krok 5.

2. Utwórz folder, którego zawartość nie będzie synchronizowana z usługą OneDrive. Przykład:

    *Folder źródłowy C:\automatycznej kwarantanny*

3. Otwórz program Microsoft Word i utwórz plik w folderze źródłowym automatycznej kwarantanny. Zastosuj etykietę **Wysoce poufne** poufności; Zobacz [Stosowanie etykiet poufności do plików i wiadomości e-mail w pakiecie Office](https://support.microsoft.com/topic/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).

4. Skopiuj utworzony plik do folderu synchronizacji usługi OneDrive. Powinno zostać wyświetlone wyskakujące powiadomienie użytkownika informujące o tym, że akcja jest niedozwolona i że plik zostanie poddany kwarantannie. Na przykład dla nazwy użytkownika *Isaiah Langer* i dokumentu zatytułowanego *dokument automatycznej kwarantanny 1.docx* zobaczysz następujący komunikat:

    ![Wyskakujące powiadomienie użytkownika dotyczące zapobiegania utracie danych z informacją, że akcja synchronizacji usługi OneDrive nie jest dozwolona dla określonego pliku i że plik zostanie poddany kwarantannie.](../media/auto-quarantine-user-notification-toast.png)
    
    Komunikat brzmi:
    
    > Otwieranie dokumentu autokwarantyny 1.docx z tą aplikacją jest niedozwolone. Plik zostanie poddany kwarantannie do folderu "C:\Users\IsaiahLanger\Microsoft DLP\OneDrive"

5. Wybierz pozycję **Odrzuć**.

6. Otwórz plik tekstowy uchwytu miejsca. Zostanie on nazwany **1.docx_ dokumentu automatycznej kwarantanny *date_time*.txt**. 

7. Otwórz folder kwarantanny i upewnij się, że oryginalny plik istnieje.
 
8. Sprawdź Eksploratora działań pod kątem danych z monitorowanych punktów końcowych. Ustaw filtr lokalizacji dla urządzeń i dodaj zasady, a następnie filtruj według nazwy zasad, aby zobaczyć wpływ tych zasad; Zobacz [Wprowadzenie do eksploratora działań](data-classification-activity-explorer.md), jeśli to konieczne.

9. Sprawdź Eksploratora działań pod kątem zdarzenia.

## <a name="scenario-5-restrict-unintentional-sharing-to-unallowed-cloud-apps-and-services"></a>Scenariusz 5. Ograniczanie przypadkowego udostępniania do niedozwolonych aplikacji i usług w chmurze

Za pomocą programu Endpoint DLP i przeglądarki sieci Web edge można ograniczyć przypadkowe udostępnianie poufnych elementów do niedozwolonych aplikacji i usług w chmurze. Przeglądarka Edge rozumie, kiedy element jest ograniczony przez zasady DLP punktu końcowego i wymusza ograniczenia dostępu.

Po wybraniu **pozycji Urządzenia** jako lokalizacji w prawidłowo skonfigurowanych zasadach DLP i użyciu przeglądarki Microsoft Edge niedozwolone przeglądarki zdefiniowane w tych ustawieniach nie będą mogły uzyskiwać dostępu do elementów poufnych zgodnych z kontrolkami zasad DLP. Zamiast tego użytkownicy zostaną przekierowani do korzystania z przeglądarki Microsoft Edge, która dzięki zrozumieniu ograniczeń nałożonych przez DLP może blokować lub ograniczać działania po spełnieniu warunków w zasadach DLP.

Aby użyć tego ograniczenia, należy skonfigurować trzy ważne elementy:

1. Określ miejsca — usługi, domeny, adresy IP — do których chcesz zapobiec udostępnianiu poufnych elementów.

2. Dodaj przeglądarki, które nie mogą uzyskiwać dostępu do niektórych poufnych elementów w przypadku dopasowania zasad DLP.

3. Skonfiguruj zasady DLP, aby zdefiniować rodzaje elementów poufnych, dla których przekazywanie powinno być ograniczone do tych miejsc, włączając opcję **Przekaż do usług w chmurze** i **dostęp z niedozwolonej przeglądarki**.

Możesz nadal dodawać nowe usługi, aplikacje i zasady, aby rozszerzać i rozszerzać ograniczenia w celu spełnienia potrzeb biznesowych i ochrony poufnych danych. 

Ta konfiguracja pomoże zapewnić bezpieczeństwo danych, jednocześnie unikając niepotrzebnych ograniczeń, które uniemożliwiają użytkownikom uzyskiwanie dostępu do elementów niepoufnych lub ich udostępnianie.
## <a name="see-also"></a>Zobacz też

- [Dowiedz się więcej o ochronie przed utratą danych punktu końcowego](endpoint-dlp-learn-about.md)
- [Wprowadzenie do ochrony przed utratą danych punktu końcowego](endpoint-dlp-getting-started.md)
- [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md)
- [Twórz, testuj i dostrajaj zasady DLP](create-test-tune-dlp-policy.md)
- [Wprowadzenie do Eksploratora działań](data-classification-activity-explorer.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/)
- [Dołączanie urządzeń Windows 10 i Windows 11 do usługi Microsoft Purview — omówienie](/microsoft-365/compliance/device-onboarding-overview)
- [Subskrypcja platformy Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Przyłączone do usługi Azure Active Directory (AAD)](/azure/active-directory/devices/concept-azure-ad-join)
- [Pobierz nową przeglądarkę Microsoft Edge na podstawie Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
- [Wprowadzenie do domyślnych zasad DLP](get-started-with-the-default-dlp-policy.md)
- [Twórz zasady DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md)
