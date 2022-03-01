---
title: Przeglądanie działań naprawczych po zautomatyzowanych badaniach
description: Przegląd i zatwierdzanie (lub odrzucanie) działań naprawczych prowadzonych w wyniku zautomatyzowanego badania.
keywords: autoir, automated, investigation, detection, remediation, action, pending, approved
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: JoeDavies-MSFT
ms.author: josephd
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: how-to
ms.date: 01/29/2021
ms.technology: mde
ms.openlocfilehash: f6886cd109e8727dd05c7de0b4055f839b847de2
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997829"
---
# <a name="review-remediation-actions-following-an-automated-investigation"></a>Przeglądanie działań naprawczych w przypadku zautomatyzowanego badania

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="remediation-actions"></a>Działania naprawcze

Po [uruchamiam zautomatyzowanego](automated-investigations.md) badania jest generowany werdykt dla każdego zbadanych dowodów. Werdykty mogą być *złośliwe*, *podejrzane* lub *Nie można odnaleźć zagrożeń*.

W zależności od

- rodzaj zagrożenia,
- wynikowy werdykt i
- sposób konfigurowania [grup](/microsoft-365/security/defender-endpoint/machine-groups) urządzeń w organizacji,

działania naprawcze mogą być wykonywane automatycznie lub tylko po zatwierdzeniu ich przez zespół operacyjny ds. zabezpieczeń Twojej organizacji.

Oto kilka przykładów:

- **Przykład 1**. Grupy urządzeń firmy Fabrikam są ustawione na pełne **—** automatyczne korygowanie zagrożeń (zalecane ustawienie). W takim przypadku działania naprawcze są podejmowane automatycznie dla artefaktów uznanych za złośliwe w przypadku zautomatyzowanego badania (zobacz [Przeglądanie zakończonych akcji](#review-completed-actions)).

- **Przykład 2**. Urządzenia firmy Contoso są uwzględniane w grupie urządzeń ustawionej na wartość Pół - wymagaj zatwierdzenia wszelkich **działań naprawczych**. W takim przypadku zespół operacyjny zabezpieczeń firmy Contoso musi przejrzeć i zatwierdzić wszystkie działania naprawcze po automatycznym śledztwie (zobacz [Przeglądanie oczekujących akcji](#review-pending-actions)).

- **Przykład 3**. W grupach urządzeń w grupie Tailspin Toys jest ustawiona wartość **Brak automatycznej odpowiedzi** (zalecana). W tym przypadku nie są prowadzone zautomatyzowane badania. Nie są podejmowane ani oczekujące działania naprawcze i w Centrum akcji dla ich urządzeń nie są [](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center) rejestrowane żadne akcje (zobacz [Zarządzanie grupami urządzeń](/microsoft-365/security/defender-endpoint/machine-groups#manage-device-groups)).

Niezależnie od tego, czy zostanie wykonane automatycznie, czy po zatwierdzeniu, zautomatyzowane badanie może spowodować co najmniej jedno z działań naprawczych:

- Poddaj plikowi kwarantannę
- Usuwanie klucza rejestru
- Zaśmieć proces
- Zatrzymywanie usługi
- Wyłączanie sterownika
- Usuwanie zaplanowanego zadania

## <a name="review-pending-actions"></a>Przeglądanie oczekujących akcji

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender i</a> zaloguj się.
2. W okienku nawigacji wybierz pozycję **Centrum akcji**.
3. Przejrzyj elementy na karcie **Oczekujące** .
4. Wybierz akcję, aby otworzyć jej okienko wysuwu.
5. W wysuwanych okienkach przejrzyj informacje, a następnie zrób tak:
   - Wybierz **pozycję Otwórz stronę badania,** aby wyświetlić więcej szczegółów dotyczących badania.
   - Wybierz **pozycję Zatwierdź** , aby zainicjować oczekującą akcję.
   - Wybierz **pozycję Odrzuć** , aby zapobiec podejmowanej akcji oczekującej.
   - Wybierz **pozycję Przejdź wyszukiwania,** aby przejść do wyszukiwania [zaawansowanego](advanced-hunting-overview.md).

## <a name="review-completed-actions"></a>Przejrzyj wykonane akcje

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender i</a> zaloguj się.
2. W okienku nawigacji wybierz pozycję **Centrum akcji**.
3. Przejrzyj elementy na **karcie** Historia.
4. Wybierz element, aby wyświetlić więcej szczegółów dotyczących tej akcji zaradczej.

## <a name="undo-completed-actions"></a>Cofanie ukończonych akcji

Jeśli ustalisz, że urządzenie lub plik nie stanowią zagrożenia, możesz cofnąć wykonane akcje naprawcze, niezależnie od tego, czy zostały one wykonane automatycznie, czy ręcznie. W Centrum akcji **na karcie Historia** możesz cofnąć dowolną z następujących akcji:

<br>

****

|Źródło akcji|Obsługiwane akcje|
|---|---|
|<ul><li>Zautomatyzowane badanie</li><li>Program antywirusowy Microsoft Defender</li><li>Ręczne akcje odpowiedzi</li></ul>|<ul><li>Wyizoluj urządzenie</li><li>Ograniczanie wykonywania kodu</li><li>Poddaj plikowi kwarantannę</li><li>Usuwanie klucza rejestru</li><li>Zatrzymywanie usługi</li><li>Wyłączanie sterownika</li><li>Usuwanie zaplanowanego zadania</li></ul>|
|

### <a name="to-undo-multiple-actions-at-one-time"></a>Aby cofnąć wiele akcji jednocześnie

1. Przejdź do Centrum akcji ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) i zaloguj się.
2. Na **karcie Historia** wybierz akcje, które chcesz cofnąć. Pamiętaj, aby zaznaczyć elementy, które mają ten sam typ akcji. Zostanie otwarte okienko wysuwu.
3. W wysuwanych okienkach wybierz pozycję **Cofnij**.

### <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>Aby usunąć plik z kwarantanny na wielu urządzeniach

1. Przejdź do Centrum akcji ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) i zaloguj się.
2. Na karcie **Historia** wybierz element, który ma plik kwarantanny typu **Akcja**.
3. W wysuwanych okienkach wybierz **pozycję Zastosuj do X** większej liczby wystąpień tego pliku, a następnie wybierz pozycję Cofnij.

## <a name="automation-levels-automated-investigation-results-and-resulting-actions"></a>Poziomy automatyzacji, zautomatyzowane wyniki analizy i akcje wynikowe

Poziomy automatyzacji mają wpływ na to, czy niektóre działania naprawcze są podejmowane automatycznie, czy tylko po zatwierdzeniu. Czasami zespół operacyjny ds. zabezpieczeń musi wykonać więcej czynności, w zależności od wyników automatycznego badania. W poniższej tabeli podsumowano poziomy automatyzacji, wyniki zautomatyzowanych badań oraz czynności, które należy wykonać w każdym przypadku.

<br>

****

|Ustawienie grupy urządzeń|Zautomatyzowane wyniki badania|Co należy zrobić|
|---|---|---|
|**Pełne — automatyczne korygowanie zagrożeń** (zalecane ustawienie)|W przypadku jednego z *dowodów* osiągnięto werdykt złośliwego oprogramowania. <p> Odpowiednie działania naprawcze są podejmowane automatycznie.|[Przejrzyj wykonane akcje](#review-completed-actions)|
|**Pełne — automatyczne korygowanie zagrożeń**|Osiągnięto *werdykt* podejrzanych dowodów. <p> Działania naprawcze oczekują na zatwierdzenie kontynuowania.|[Zatwierdzanie (lub odrzucanie) oczekujących akcji](#review-pending-actions)|
|**Pół - wymagaj zatwierdzenia wszelkich działań naprawczych**|W celu zrzutu *tych* dowodów osiągnięto werdykt złośliwego lub podejrzanego. <p> Działania naprawcze oczekują na zatwierdzenie kontynuowania.|[Zatwierdzanie (lub odrzucanie) oczekujących akcji](#review-pending-actions)|
|**Pół - wymaganie zatwierdzenia rozwiązywania problemów z folderami podstawowymi**|W przypadku jednego z *dowodów* osiągnięto werdykt złośliwego oprogramowania. <p> Jeśli artefakt jest plikiem lub plikiem wykonywalnym i znajduje się w katalogu systemu operacyjnego, takim jak folder Windows lub folder Pliki programu, działania naprawcze oczekują na zatwierdzenie. <p> Jeśli artefakt nie *znajduje się w* katalogu systemu operacyjnego, akcje naprawcze są podejmowane automatycznie.|<ol><li>[Zatwierdzanie (lub odrzucanie) oczekujących akcji](#review-pending-actions)</li><li>[Przejrzyj wykonane akcje](#review-completed-actions)</li></ol>|
|**Pół - wymaganie zatwierdzenia rozwiązywania problemów z folderami podstawowymi**|Osiągnięto *werdykt* podejrzanych dowodów. <p> Działania naprawcze oczekują na zatwierdzenie.|[Zatwierdzanie (lub odrzucanie) oczekujących akcji](#review-pending-actions).|
|**Pół - wymaganie zatwierdzenia działań naprawczych folderów nie temp**|W przypadku jednego z *dowodów* osiągnięto werdykt złośliwego oprogramowania. <p> Jeśli artefakt jest plikiem lub plikiem wykonywalnym, który nie znajduje się w folderze tymczasowym, takim jak folder pobierania użytkownika lub folder tymczasowy, działania naprawcze oczekują na zatwierdzenie. <p> Jeśli artefakt jest plikiem lub plikiem *wykonywalnym,* który znajduje się w folderze tymczasowym, akcje naprawcze są podejmowane automatycznie.|<ol><li>[Zatwierdzanie (lub odrzucanie) oczekujących akcji](#review-pending-actions)</li><li>[Przejrzyj wykonane akcje](#review-completed-actions)</li></ol>|
|**Pół - wymaganie zatwierdzenia działań naprawczych folderów nie temp**|Osiągnięto *werdykt* podejrzanych dowodów. <p> Działania naprawcze oczekują na zatwierdzenie.|[Zatwierdzanie (lub odrzucanie) oczekujących akcji](#review-pending-actions)|
|Dowolny z poziomów **automatyzacji pełnej** **lub** półprzecjowej|W celu *zsyłki* dowodów osiągnięto werdykt "Nie znaleziono zagrożeń". <p> Nie są podejmowane żadne działania naprawcze i nie są podejmowane żadne działania oczekujące na zatwierdzenie.|[Wyświetlanie szczegółów i wyników zautomatyzowanych badań](/microsoft-365/security/defender-endpoint/auto-investigation-action-center)|
|**Brak automatycznej odpowiedzi** (nie jest zalecana)|Nie są uruchamiane żadne zautomatyzowane badania, więc nie są dostępne żadne werdykty i nie są podejmowane żadne działania naprawcze ani nie oczekują na zatwierdzenie.|[Rozważ skonfigurowanie lub zmianę grup urządzeń w celu **używania automatyzacji pełnej** **lub półprzezroczyskowej** .](/microsoft-365/security/defender-endpoint/machine-groups)|
|

W programie Microsoft Defender for Endpoint wszystkie werdykty są śledzone w [Centrum akcji](auto-investigation-action-center.md#new-a-unified-action-center).

## <a name="next-steps"></a>Następne kroki

- [Dowiedz się więcej o możliwościach reakcji na żywo](live-response.md)
- [Aktywne wyszukiwanie zagrożeń za pomocą zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Adres dodatnich/ujemnych wyników fałszywie dodatnich w programie Microsoft Defender dla punktu końcowego](defender-endpoint-false-positives-negatives.md)

## <a name="see-also"></a>Zobacz też

- [Omówienie zautomatyzowanych badań](automated-investigations.md)
