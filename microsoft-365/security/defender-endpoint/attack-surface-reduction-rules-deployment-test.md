---
title: Przetestuj reguły zmniejszania obszaru podatnego na ataki
description: Zawiera wskazówki dotyczące testowania wdrażania reguł zmniejszania obszaru ataków (ASR).
keywords: Wdrażanie reguł zmniejszania obszaru ataków, wdrażanie usługi ASR, włączanie reguł asr, konfigurowanie usługi ASR, system zapobiegania włamaniom do hostów, reguły ochrony, reguły ochrony przed lukami w zabezpieczeniach, reguły antyeksploatowania, reguły wykorzystujące luki w zabezpieczeniach, reguły zapobiegania zakażeniom, Ochrona punktu końcowego w usłudze Microsoft Defender, konfigurowanie reguł usługi ASR
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection:
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 8bfe3e0d36a02831b5673b92217152ce87804d0a
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66601295"
---
# <a name="test-attack-surface-reduction-asr-rules"></a>Przetestuj reguły zmniejszania obszaru podatnego na ataki

Testowanie reguł zmniejszania obszaru ataków (ASR) pomaga określić, czy reguły będą utrudniać operacje biznesowe przed włączeniem jakiejkolwiek reguły. Zaczynając od małej, kontrolowanej grupy, możesz ograniczyć potencjalne zakłócenia pracy podczas rozszerzania wdrożenia w całej organizacji.

Rozpocznij wdrażanie reguł zmniejszania obszaru ataków (ASR) za pomocą pierścienia 1.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-testing-steps.png" alt-text="Kroki testowania reguł usługi ASR" lightbox="images/asr-rules-testing-steps.png":::
  
## <a name="step-1-test-asr-rules-using-audit"></a>Krok 1. Testowanie reguł usługi ASR przy użyciu funkcji Inspekcja

Rozpocznij fazę testowania, włączając reguły usługi ASR z regułami ustawionymi na Wartość Inspekcja, zaczynając od użytkowników lub urządzeń w pierścieniu 1. Zazwyczaj zaleca się włączenie wszystkich reguł (w obszarze Inspekcja), aby można było określić, które reguły są wyzwalane w fazie testowania. Należy pamiętać, że reguły, które są ustawione na Inspekcja, zwykle nie wpływają na funkcjonalność jednostki lub jednostek, do których jest stosowana reguła, ale generują zarejestrowane zdarzenia dla oceny; nie ma wpływu na użytkowników końcowych.

### <a name="configure-asr-rules-using-mem"></a>Konfigurowanie reguł usługi ASR przy użyciu MEM

Do konfigurowania niestandardowych reguł usługi ASR można użyć usługi Microsoft Endpoint Manager (MEM) Endpoint Security.

1. Otwórz [centrum administracyjne Endpoint Manager firmy Microsoft](https://endpoint.microsoft.com/#home).
2. Przejdź do obszaru **Zmniejszanie obszaru ataków** zabezpieczeń  > **punktu końcowego**.
3. Wybierz pozycję **Utwórz zasady**.
4. W **obszarze Platforma** wybierz pozycję **Windows 10 i nowsze**, a następnie w obszarze **Profil** wybierz pozycję **Reguły zmniejszania obszaru ataków**.
  
    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/asr-mem-create-profile.png" alt-text="Strona tworzenia profilu dla reguł usługi ASR" lightbox="images/asr-mem-create-profile.png":::

5. Kliknij **pozycję Utwórz**.
6. Na karcie **Podstawy** okienka **Tworzenie profilu** w obszarze **Nazwa** dodaj nazwę zasad. W **obszarze Opis** dodaj opis zasad reguł usługi ASR.
7. Na karcie **Ustawienia konfiguracji** w obszarze **Reguły zmniejszania obszaru podatnego na ataki** ustaw wszystkie reguły na **tryb inspekcji**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/asr-mem-configuration-settings.png" alt-text="Konfiguracja reguł usługi ASR w trybie inspekcji" lightbox="images/asr-mem-configuration-settings.png":::

    >[!Note]
    >Istnieją różnice w niektórych listach trybu reguł usługi ASR; _Zablokowane_ i _włączone_ zapewniają te same funkcje.

8. [Opcjonalnie] W okienku **Tagi zakresu** możesz dodać informacje o tagach do określonych urządzeń. Możesz również użyć kontroli dostępu opartej na rolach i tagów zakresu, aby upewnić się, że odpowiedni administratorzy mają odpowiedni dostęp i wgląd w odpowiednie obiekty Intune. Dowiedz się więcej: [Użyj kontroli dostępu opartej na rolach (RBAC) i tagów zakresu dla rozproszonej infrastruktury IT w Intune](/mem/intune/fundamentals/scope-tags).
9. W okienku **Przypisania** można wdrożyć lub "przypisać" profil do grup użytkowników lub urządzeń. Dowiedz się więcej: [Przypisywanie profilów urządzeń w Microsoft Intune](/mem/intune/configuration/device-profile-assign#exclude-groups-from-a-profile-assignment)
10. Przejrzyj ustawienia w okienku **Przeglądanie i tworzenie** . Kliknij **pozycję Utwórz** , aby zastosować reguły.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/asr-mem-review-create.png" alt-text="Strona Tworzenie profilu" lightbox="images/asr-mem-review-create.png":::

Nowe zasady zmniejszania obszaru ataków dla reguł usługi ASR są wymienione w **| zabezpieczeń punktu końcowego Zmniejszanie obszaru podatnego na ataki**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/asr-mem-my-asr-rules.png" alt-text=" Strona zmniejszania obszaru ataków" lightbox="images/asr-mem-my-asr-rules.png":::

## <a name="step-2-understand-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal"></a>Krok 2. Omówienie strony raportowania reguł zmniejszania obszaru ataków w portalu Microsoft 365 Defender

Strona raportowania reguł usługi ASR znajduje się w **Microsoft 365 Defender portalu****Raporty Reguły** > **zmniejszania obszaru** >  podatnego na ataki. Ta strona ma trzy karty:

- Wykrywania
- Konfiguracja
- Dodawanie wykluczeń

### <a name="detections-tab"></a>Karta Wykrywanie

Zapewnia 30-dniową oś czasu wykrytego inspekcji i zablokowanych zdarzeń.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-01.png" alt-text="Karta Wykrywanie reguł zmniejszania obszaru ataków" lightbox="images/asr-defender365-01.png":::

Okienko Reguły zmniejszania obszaru podatnego na ataki zawiera omówienie wykrytych zdarzeń na podstawie reguły.

>[!Note]
>Istnieją pewne różnice w raportach reguł usługi ASR. Firma Microsoft jest w trakcie aktualizowania zachowania raportów reguł usługi ASR w celu zapewnienia spójnego środowiska.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-01b.png" alt-text="Strona Reguły zmniejszania obszaru ataków" lightbox="images/asr-defender365-01b.png"::: 

Kliknij **pozycję Wyświetl wykrywania** , aby otworzyć kartę **Wykrywanie** .

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-reports-detections.png" alt-text="Wykrywanie reguł zmniejszania obszaru ataków" lightbox="images/asr-defender365-reports-detections.png":::

Okienko GroupBy i Filter ( **Grupuj według** ) i **Filter (Filtr** ) udostępnia następujące opcje:

Funkcja **GroupBy** zwraca wyniki ustawione na następujące grupy:

- Brak grupowania
- Wykryty plik
- Inspekcja lub blokowanie
- Reguły
- Aplikacja źródłowa
- Urządzenie
- Użytkownik
- Publisher

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-reports-detections.png" alt-text="Filtr GroupBy wykrywania reguł zmniejszania obszaru ataków" lightbox="images/asr-defender365-reports-detections.png":::

**Filtr** otwiera stronę **Filtruj reguły** , która umożliwia określanie zakresu wyników tylko do wybranych reguł usługi ASR:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-filter.png" alt-text="Filtr wykrywania reguł zmniejszania obszaru ataków w regułach" lightbox="images/asr-defender365-filter.png":::

>[!Note]
>Jeśli masz licencję Microsoft Microsoft 365 Security E5 lub A5, Windows E5 lub A5, poniższy link otwiera kartę Raporty usługi Microsoft Defender 365 > [obszaru ataków](https://security.microsoft.com/asr?viewid=detections) > kartę Wykrywanie.

### <a name="configuration-tab"></a>Karta Konfiguracja

Wyświetla — na podstawie komputera — zagregowany stan reguł usługi ASR: Wyłączone, Inspekcja, Blokuj.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-configurations.png" alt-text="Karta Konfiguracja reguł zmniejszania obszaru ataków i wpis na jej stronie" lightbox="images/asr-defender365-configurations.png":::

Na karcie Konfiguracje możesz sprawdzić — na poszczególnych urządzeniach — które reguły usługi ASR są włączone i w jakim trybie, wybierając urządzenie, dla którego chcesz przejrzeć reguły usługi ASR.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-configurations.settings.png" alt-text="Włączone reguły zmniejszania obszaru ataków i tryb" lightbox="images/asr-defender365-configurations.settings.png":::

Link **Wprowadzenie** otwiera centrum administracyjne usługi Microsoft Endpoint Manager, w którym można utworzyć lub zmodyfikować zasady ochrony punktu końcowego dla usługi ASR:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-05b-mem1.png" alt-text="Element menu *Zabezpieczenia punktu końcowego na stronie Przegląd" lightbox="images/asr-defender365-05b-mem1.png":::

W | zabezpieczeń punktu końcowego Omówienie, wybierz pozycję **Zmniejszanie obszaru ataków**:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-05b-mem2.png" alt-text="Zmniejszanie obszaru ataków w MEM" lightbox="images/asr-defender365-05b-mem2.png":::

| zabezpieczeń punktu końcowego Zostanie otwarte okienko zmniejszania obszaru podatnego na ataki:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-05b-mem3.png" alt-text="Okienko zmniejszania obszaru ataków zabezpieczeń punktu końcowego" lightbox="images/asr-defender365-05b-mem3.png":::

>[!Note]
>Jeśli masz licencję usługi Microsoft Defender 365 E5 (lub Windows E5?), ten link spowoduje otwarcie karty Raporty usługi Microsoft Defender 365 > Atak > [konfiguracji](https://security.microsoft.com/asr?viewid=configuration) .

### <a name="add-exclusions"></a>Dodawanie wykluczeń

Ta karta zawiera metodę wybierania wykrytych jednostek (na przykład wyników fałszywie dodatnich) do wykluczenia. Po dodaniu wykluczeń raport zawiera podsumowanie oczekiwanego wpływu.

>[!Note]
> Wykluczenia av programu antywirusowego Microsoft Defender są przestrzegane przez reguły usługi ASR.  Zobacz [Konfigurowanie i weryfikowanie wykluczeń na podstawie rozszerzenia, nazwy lub lokalizacji](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

> [!div class="mx-imgBorder"]
> :::image type="content" source="Images/asr-defender365-06d.png" alt-text="Okienko wykluczania wykrytego pliku" lightbox="Images/asr-defender365-06d.png":::

> [!Note]
>Jeśli masz licencję microsoft defender 365 E5 (lub Windows E5?), ten link otworzy kartę Raporty usługi Microsoft Defender 365 > Obszar ataków > [wykluczenia](https://security.microsoft.com/asr?viewid=exclusions) .

### <a name="use-powershell-as-an-alternative-method-to-enable-asr-rules"></a>Używanie programu PowerShell jako alternatywnej metody w celu włączenia reguł usługi ASR

Możesz użyć programu PowerShell — jako alternatywy dla MEM — aby włączyć reguły usługi ASR w trybie inspekcji, aby wyświetlić rekord aplikacji, które zostałyby zablokowane, gdyby funkcja została w pełni włączona. Możesz również zorientować się, jak często reguły będą uruchamiane podczas normalnego użytkowania.

Aby włączyć regułę zmniejszania obszaru ataków w trybie inspekcji, użyj następującego polecenia cmdlet programu PowerShell:

```PowerShell
Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions AuditMode
```

Gdzie `<rule ID>` jest [wartością identyfikatora GUID reguły zmniejszania obszaru ataków](attack-surface-reduction-rules-reference.md).

Aby włączyć wszystkie dodane reguły zmniejszania obszaru ataków w trybie inspekcji, użyj następującego polecenia cmdlet programu PowerShell:

```PowerShell
(Get-MpPreference).AttackSurfaceReductionRules_Ids | Foreach {Add-MpPreference -AttackSurfaceReductionRules_Ids $_ -AttackSurfaceReductionRules_Actions AuditMode}
```

> [!TIP]
> Jeśli chcesz w pełni przeprowadzić inspekcję sposobu działania reguł zmniejszania obszaru ataków w organizacji, musisz użyć narzędzia do zarządzania, aby wdrożyć to ustawienie na urządzeniach w sieciach.

Możesz również użyć dostawców usług konfiguracji zasady grupy, Intune lub zarządzania urządzeniami przenośnymi (MDM), aby skonfigurować i wdrożyć to ustawienie. Dowiedz się więcej w artykule Main [Attack surface reduction rules (Główne reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction.md) ).

## <a name="use-windows-event-viewer-review-as-an-alternative-to-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal"></a>Używanie funkcji Windows Podgląd zdarzeń Review jako alternatywy dla strony raportowania reguł zmniejszania obszaru ataków w portalu Microsoft 365 Defender

Aby przejrzeć aplikacje, które zostałyby zablokowane, otwórz Podgląd zdarzeń i odfiltruj identyfikator zdarzenia 1121 w dzienniku Microsoft-Windows-Windows Defender/Operational. W poniższej tabeli wymieniono wszystkie zdarzenia ochrony sieci.

Identyfikator zdarzenia | Opis
-|-
 5007 | Zdarzenie po zmianie ustawień
 1121 | Zdarzenie, gdy reguła zmniejszania obszaru ataków jest uruchamiana w trybie bloku
 1122 | Zdarzenie, gdy reguła zmniejszania obszaru ataków jest uruchamiana w trybie inspekcji

## <a name="additional-topics-in-this-deployment-collection"></a>Dodatkowe tematy w tej kolekcji wdrożeń

[Omówienie wdrażania reguł zmniejszania powierzchni podatnej na ataki (ASR)](attack-surface-reduction-rules-deployment.md)

[Zaplanuj wdrażanie reguł zmniejszania powierzchni podatnej na ataki (ASR)](attack-surface-reduction-rules-deployment-plan.md)

[Włącz reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction-rules-deployment-implement.md)

[Operacjonalizuj reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction-rules-deployment-operationalize.md)

[Odwołuj reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction-rules-reference.md)
