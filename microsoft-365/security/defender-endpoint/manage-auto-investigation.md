---
title: Przejrzyj akcje korygowania po zautomatyzowanych badaniach
description: Przejrzyj i zatwierdź (lub odrzuć) akcje korygowania po zautomatyzowanym badaniu.
keywords: autoir, automated, investigation, detection, remediation, action, pending, approved
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: how-to
ms.technology: mde
ms.openlocfilehash: 06e2c6c5269b32b29be87f44635d65b9c610c344
ms.sourcegitcommit: e624221597480295b799d56568c4f6f56d40b41d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2022
ms.locfileid: "65535873"
---
# <a name="review-remediation-actions-following-an-automated-investigation"></a>Przejrzyj akcje korygowania po zautomatyzowanym badaniu

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft Defender dla Firm](../defender-business/mdb-overview.md)

## <a name="remediation-actions"></a>Działania naprawcze

Po uruchomieniu [zautomatyzowanego dochodzenia](automated-investigations.md) dla każdego badanego dowodu generowany jest werdykt. Werdykty mogą być *złośliwe*, *podejrzane* lub *nie znaleziono zagrożeń*.

W zależności od

- typ zagrożenia,
- wynikowy werdykt, oraz
- sposób konfigurowania [grup urządzeń](/microsoft-365/security/defender-endpoint/machine-groups) w organizacji,

Akcje korygowania mogą być wykonywane automatycznie lub tylko po zatwierdzeniu przez zespół ds. operacji zabezpieczeń w organizacji.

Oto kilka przykładów:

- **Przykład 1**: Grupy urządzeń firmy Fabrikam są ustawione na **Wartość Pełna — automatycznie koryguj zagrożenia** (zalecane ustawienie). W takim przypadku akcje korygowania są wykonywane automatycznie dla artefaktów, które są uważane za złośliwe po zautomatyzowanym badaniu (zobacz [Przeglądanie zakończonych akcji](#review-completed-actions)).

- **Przykład 2**: Urządzenia firmy Contoso znajdują się w grupie urządzeń ustawionej dla aplikacji **Semi — wymagają zatwierdzenia dla każdego korygowania**. W takim przypadku zespół ds. operacji zabezpieczeń firmy Contoso musi przejrzeć i zatwierdzić wszystkie akcje korygowania po zautomatyzowanym badaniu (zobacz [Przeglądanie oczekujących akcji](#review-pending-actions)).

- **Przykład 3**: W przypadku aplikacji Tailspin Toys grupy urządzeń mają ustawioną wartość **Brak automatycznej odpowiedzi** (niezalecane). W takim przypadku zautomatyzowane badania nie są wykonywane. Żadne akcje korygowania nie są podejmowane ani oczekujące, a żadne akcje nie są rejestrowane w [Centrum akcji](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center) dla swoich urządzeń (zobacz [Zarządzanie grupami urządzeń](/microsoft-365/security/defender-endpoint/machine-groups#manage-device-groups)).

Niezależnie od tego, czy jest wykonywane automatycznie, czy po zatwierdzeniu, zautomatyzowane badanie może spowodować co najmniej jedną akcję korygowania:

- Kwarantanna pliku
- Usuwanie klucza rejestru
- Zabij proces
- Zatrzymywanie usługi
- Wyłączanie sterownika
- Usuwanie zaplanowanego zadania

## <a name="review-pending-actions"></a>Przeglądanie oczekujących akcji

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a> i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Centrum akcji**.

3. Przejrzyj elementy na karcie **Oczekujące** .

4. Wybierz akcję, aby otworzyć okienko wysuwane.

5. W okienku wysuwanym przejrzyj informacje, a następnie wykonaj jedną z następujących czynności:

   - Wybierz **pozycję Otwórz stronę badania** , aby wyświetlić więcej szczegółów na temat badania.
   - Wybierz pozycję **Zatwierdź** , aby zainicjować oczekującą akcję.
   - Wybierz pozycję **Odrzuć** , aby zapobiec podjęciu oczekującej akcji.
   - Wybierz pozycję **Go hunt** ,aby przejść do [pozycji Zaawansowane wyszukiwanie zagrożeń](advanced-hunting-overview.md).

## <a name="review-completed-actions"></a>Przejrzyj ukończone akcje

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a> i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Centrum akcji**.

3. Przejrzyj elementy na karcie **Historia** .

4. Wybierz element, aby wyświetlić więcej szczegółów dotyczących tej akcji korygowania.

## <a name="undo-completed-actions"></a>Cofnij ukończone akcje

Jeśli ustalisz, że urządzenie lub plik nie stanowi zagrożenia, możesz cofnąć podjęte akcje korygowania, niezależnie od tego, czy te akcje zostały wykonane automatycznie, czy ręcznie. W centrum akcji na karcie **Historia** możesz cofnąć dowolną z następujących akcji:

|Źródło akcji|Obsługiwane akcje|
|---|---|
|<ul><li>Zautomatyzowane badanie</li><li>Ręczne akcje reagowania (zobacz poniższą notatkę)</li><li>Program antywirusowy Microsoft Defender</li></ul>|<ul><li>Wyłączanie sterownika</li><li>Izolowanie urządzenia</li><li>Kwarantanna pliku</li><li>Usuwanie klucza rejestru</li><li>Usuwanie zaplanowanego zadania</li><li>Ograniczanie wykonywania kodu</li><li>Zatrzymywanie usługi</li></ul>|

> [!NOTE]
> [Usługa Defender for Endpoint Plan 1](defender-endpoint-plan-1.md) i [Microsoft Defender dla Firm](../defender-business/mdb-overview.md) obejmują tylko następujące ręczne akcje odpowiedzi:
>
> - Uruchomiono skanowanie antywirusowe
> - Izolowanie urządzenia
> - Zatrzymywanie i kwarantanna pliku
> - Dodawanie wskaźnika w celu zablokowania lub zezwolenia na plik
>
> Aby dowiedzieć się więcej, zobacz [Porównanie planów Ochrona punktu końcowego w usłudze Microsoft Defender](defender-endpoint-plan-1-2.md) i [Porównanie funkcji zabezpieczeń w planach Microsoft 365 dla małych i średnich firm](../defender-business/compare-mdb-m365-plans.md).

### <a name="to-undo-multiple-actions-at-one-time"></a>Aby cofnąć wiele akcji jednocześnie

1. Przejdź do centrum akcji ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) i zaloguj się.

2. Na karcie **Historia** wybierz akcje, które chcesz cofnąć. Pamiętaj, aby wybrać elementy o tym samym typie akcji. Zostanie otwarte okienko wysuwane.

3. W okienku wysuwanym wybierz pozycję **Cofnij**.

### <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>Aby usunąć plik z kwarantanny na wielu urządzeniach

1. Przejdź do centrum akcji ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) i zaloguj się.

2. Na karcie **Historia** wybierz element z **plikiem Kwarantanna typu Akcja**.

3. W okienku wysuwanym wybierz pozycję **Zastosuj do X więcej wystąpień tego pliku**, a następnie wybierz pozycję **Cofnij**.

## <a name="automation-levels-automated-investigation-results-and-resulting-actions"></a>Poziomy automatyzacji, zautomatyzowane wyniki badania i wynikowe akcje

Poziomy automatyzacji mają wpływ na to, czy niektóre akcje korygowania są wykonywane automatycznie, czy tylko po zatwierdzeniu. Czasami zespół ds. operacji zabezpieczeń ma więcej kroków do wykonania w zależności od wyników zautomatyzowanego badania. Poniższa tabela zawiera podsumowanie poziomów automatyzacji, wyników zautomatyzowanych badań i czynności, które należy wykonać w każdym przypadku.

|Ustawienie grupy urządzeń|Wyniki zautomatyzowanego badania|Co robić|
|---|---|---|
|**Pełne — automatyczne korygowanie zagrożeń**<br/>(zalecane)|Werdykt *Złośliwy* jest osiągany w celu uzyskania dowodu. <p> Odpowiednie akcje korygowania są wykonywane automatycznie.|[Przejrzyj ukończone akcje](#review-completed-actions)|
|**Pełne — automatyczne korygowanie zagrożeń**|Werdykt *Podejrzanego* jest osiągnięty w celu uzyskania dowodu. <p> Akcje korygowania oczekują na zatwierdzenie.|[Zatwierdzanie (lub odrzucanie) oczekujących akcji](#review-pending-actions)|
|**Semi — wymaga zatwierdzenia dla wszelkich działań korygowania**|Werdykt *złośliwego* lub *podejrzanego* jest osiągany w celu uzyskania dowodu. <p> Akcje korygowania oczekują na zatwierdzenie.|[Zatwierdzanie (lub odrzucanie) oczekujących akcji](#review-pending-actions)|
|**Semi — wymaga zatwierdzenia korygowania folderów podstawowych**|Werdykt *Złośliwy* jest osiągany w celu uzyskania dowodu. <p> Jeśli artefakt jest plikiem lub plikiem wykonywalnym i znajduje się w katalogu systemu operacyjnego, takim jak folder Windows lub folder Pliki programu, akcje korygowania oczekują na zatwierdzenie. <p> Jeśli artefakt *nie* znajduje się w katalogu systemu operacyjnego, akcje korygowania są wykonywane automatycznie.|<ol><li>[Zatwierdzanie (lub odrzucanie) oczekujących akcji](#review-pending-actions)</li><li>[Przejrzyj ukończone akcje](#review-completed-actions)</li></ol>|
|**Semi — wymaga zatwierdzenia korygowania folderów podstawowych**|Werdykt *Podejrzanego* jest osiągnięty w celu uzyskania dowodu. <p> Akcje korygowania oczekują na zatwierdzenie.|[Zatwierdź (lub odrzuć) oczekujące akcje](#review-pending-actions).|
|**Semi — wymaga zatwierdzenia korygowania folderów innych niż temp**|Werdykt *Złośliwy* jest osiągany w celu uzyskania dowodu. <p> Jeśli artefakt jest plikiem lub plikiem wykonywalnym, który nie znajduje się w folderze tymczasowym, takim jak folder pobierania użytkownika lub folder tymczasowy, akcje korygowania oczekują na zatwierdzenie. <p> Jeśli artefakt jest plikiem *lub plikiem* wykonywalnym znajdującym się w folderze tymczasowym, akcje korygowania są wykonywane automatycznie.|<ol><li>[Zatwierdzanie (lub odrzucanie) oczekujących akcji](#review-pending-actions)</li><li>[Przejrzyj ukończone akcje](#review-completed-actions)</li></ol>|
|**Semi — wymaga zatwierdzenia korygowania folderów innych niż temp**|Werdykt *Podejrzanego* jest osiągnięty w celu uzyskania dowodu. <p> Akcje korygowania oczekują na zatwierdzenie.|[Zatwierdzanie (lub odrzucanie) oczekujących akcji](#review-pending-actions)|
|Dowolny z poziomów automatyzacji **pełnej** lub **średniej**|Werdykt *Nie znaleziono zagrożeń jest osiągnięty* na dowód. <p> Nie są podejmowane żadne akcje korygowania i żadne akcje nie oczekują na zatwierdzenie.|[Wyświetl szczegóły i wyniki zautomatyzowanych badań](/microsoft-365/security/defender-endpoint/auto-investigation-action-center)|
|**Brak automatycznej odpowiedzi** (niezalecane)|Nie są uruchamiane żadne zautomatyzowane dochodzenia, więc nie są podejmowane żadne werdykty i nie są podejmowane żadne działania korygujące ani oczekujące na zatwierdzenie.|[Rozważ skonfigurowanie lub zmianę grup urządzeń w celu korzystania z automatyzacji **pełnej** lub **średniej**](/microsoft-365/security/defender-endpoint/machine-groups)|

Wszystkie werdykty są śledzone w [centrum akcji](auto-investigation-action-center.md#the-unified-action-center).

> [!NOTE]
> W [usłudze Defender dla firm](../defender-business/mdb-overview.md) możliwości zautomatyzowanego badania i korygowania są wstępnie ustawione do **używania funkcji Pełne — automatycznie koryguj zagrożenia**. Te możliwości są domyślnie stosowane do wszystkich urządzeń.

## <a name="next-steps"></a>Następne kroki

- [Dowiedz się więcej o możliwościach odpowiedzi na żywo](live-response.md)
- [Proaktywne wyszukiwanie zagrożeń przy użyciu zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
- [Rozwiązywanie problemów z wynikami fałszywie pozytywnymi/negatywnymi w ochronie punktu końcowego w usłudze Microsoft Defender](defender-endpoint-false-positives-negatives.md)

## <a name="see-also"></a>Zobacz też

- [Omówienie zautomatyzowanych badań](automated-investigations.md)
