---
title: Przejdź do centrum akcji, aby wyświetlić i zatwierdzić zadania zautomatyzowanego badania i korygowania
description: Wyświetlanie szczegółów dotyczących zautomatyzowanego badania i zatwierdzanie oczekujących akcji za pomocą Centrum akcji
keywords: Centrum akcji, ochrona przed zagrożeniami, badanie, alert, oczekiwanie, zautomatyzowane, wykrywanie
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.openlocfilehash: 631849997fffc0e4f90a9aa9d1850646b764a52a
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493492"
---
# <a name="the-action-center"></a>Centrum akcji

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Centrum akcji udostępnia środowisko "pojedynczego okienka szkła" dla zadań zdarzeń i alertów, takich jak:

- Zatwierdzanie oczekujących akcji korygowania.
- Wyświetlanie dziennika inspekcji już zatwierdzonych akcji korygowania.
- Przejrzyj ukończone akcje korygowania.

Ponieważ centrum akcji zapewnia kompleksowy widok Microsoft 365 Defender w pracy, twój zespół ds. operacji zabezpieczeń może działać wydajniej i wydajniej.

## <a name="the-unified-action-center"></a>Ujednolicone Centrum akcji

Ujednolicone centrum akcji ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) wyświetla listę oczekujących i zakończonych akcji korygowania dla urządzeń, wiadomości e-mail & zawartości współpracy i tożsamości w jednej lokalizacji.

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="Ujednolicone centrum akcji w portalu Microsoft 365 Defender." lightbox="../../media/m3d-action-center-unified.png":::

Przykład: 

- Jeśli wcześniej korzystano z centrum Office 365 Security & Compliance Center ([https://protection.office.com](https://protection.office.com)), wypróbuj ujednolicone centrum akcji w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>.
- Jeśli używasz centrum akcji w Centrum zabezpieczeń usługi Microsoft Defender ([https://securitycenter.windows.com/action-center](https://securitycenter.windows.com/action-center)), wypróbuj ujednolicone centrum akcji w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>.
- Jeśli już korzystasz z <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>, zobaczysz kilka ulepszeń w centrum akcji ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)).

Ujednolicone centrum akcji łączy akcje korygowania w usłudze Defender for Endpoint i Ochrona usługi Office 365 w usłudze Defender. Definiuje język wspólny dla wszystkich akcji korygowania i zapewnia ujednolicone środowisko badania. Twój zespół ds. operacji zabezpieczeń ma "pojedyncze okienko szkła" do wyświetlania akcji korygowania i zarządzania nimi.  

Możesz użyć ujednoliconego Centrum akcji, jeśli masz odpowiednie uprawnienia i co najmniej jedną z następujących subskrypcji:

- [Ochrona punktu końcowego w usłudze Microsoft Defender](../defender-endpoint/microsoft-defender-endpoint.md)
- [Ochrona usługi Office 365 w usłudze Defender](/microsoft-365/security/office-365-security/defender-for-office-365)
- [Microsoft 365 Defender](microsoft-365-defender.md)

> [!TIP]
> Aby dowiedzieć się więcej, zobacz [Wymagania](./prerequisites.md).

## <a name="using-the-action-center"></a>Korzystanie z centrum akcji

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a> i zaloguj się. 
2. W okienku nawigacji wybierz pozycję **Centrum akcji**. 

Podczas wizyty w Centrum akcji zostaną wyświetlone dwie karty: **Oczekujące akcje** i **Historia**. Poniższa tabela zawiera podsumowanie tego, co zobaczysz na każdej karcie:

|Zakładka  |Opis  |
|---------|---------|
|**Oczekujące**     | Wyświetla listę akcji, które wymagają uwagi. Możesz zatwierdzać lub odrzucać akcje pojedynczo lub wybrać wiele akcji, jeśli mają one ten sam typ akcji (na przykład plik kwarantanny). <p>**PORADA**: Sprawdź i zatwierdź (lub odrzuć) oczekujące akcje tak szybko, jak to możliwe, aby zautomatyzowane badania mogły zakończyć się w odpowiednim czasie.       |
|**Historia**     | Służy jako dziennik inspekcji dla wykonanych akcji, takich jak: <br/>- Działania korygujące, które zostały podjęte w wyniku zautomatyzowanych dochodzeń <br/>- Akcje korygujące, które zostały podjęte w przypadku podejrzanych lub złośliwych wiadomości e-mail, plików lub adresów URL<br/>— Akcje korygowania zatwierdzone przez zespół ds. operacji zabezpieczeń <br/>— Polecenia, które zostały uruchomione i akcje korygowania, które zostały zastosowane podczas sesji odpowiedzi na żywo<br/>- Akcje korygujące, które zostały podjęte przez ochronę antywirusową <p>Umożliwia cofnięcie niektórych akcji (zobacz [Cofnij ukończone akcje](m365d-autoir-actions.md#undo-completed-actions)).        |

Dane można dostosowywać, sortować, filtrować i eksportować w centrum akcji.

:::image type="content" source="../../media/m3d-action-center-columnsfilters.png" alt-text="Funkcje sortowania, filtrowania i dostosowywania centrum akcji" lightbox="../../media/m3d-action-center-columnsfilters.png":::

- Wybierz nagłówek kolumny, aby sortować elementy w kolejności rosnącej lub malejącej.
- Użyj filtru okresu, aby wyświetlić dane z ostatniego dnia, tygodnia, 30 dni lub 6 miesięcy.
- Wybierz kolumny, które chcesz wyświetlić.
- Określ liczbę elementów do uwzględnienia na każdej stronie danych.
- Użyj filtrów, aby wyświetlić tylko elementy, które chcesz zobaczyć.
- Wybierz pozycję **Eksportuj** , aby wyeksportować wyniki do pliku .csv.

## <a name="actions-tracked-in-the-action-center"></a>Akcje śledzone w Centrum akcji

Wszystkie akcje, niezależnie od tego, czy oczekują na zatwierdzenie, czy zostały już podjęte, są śledzone w Centrum akcji. Dostępne akcje obejmują następujące elementy:

- Zbieraj pakiet badań 
- Izolowanie urządzenia (tę akcję można cofnąć) 
- Odłącz komputer 
- Wykonywanie kodu wydania 
- Zwolnienie z kwarantanny 
- Przykład żądania 
- Ograniczanie wykonywania kodu (tę akcję można cofnąć) 
- Uruchomiono skanowanie antywirusowe 
- Zatrzymywanie i kwarantanna 
- Zawiera urządzenia z sieci

Oprócz akcji korygowania, które są wykonywane automatycznie w wyniku [zautomatyzowanych badań](m365d-autoir.md), centrum akcji śledzi również akcje podjęte przez zespół ds. zabezpieczeń w celu rozwiązania wykrytych zagrożeń oraz działania, które zostały podjęte w wyniku funkcji ochrony przed zagrożeniami w Microsoft 365 Defender. Aby uzyskać więcej informacji na temat automatycznych i ręcznych akcji korygowania, zobacz [Akcje korygowania](m365d-remediation-actions.md).

## <a name="viewing-action-source-details"></a>Wyświetlanie szczegółów źródła akcji

(**NOWY!**) Ulepszone centrum akcji zawiera teraz kolumnę **źródła akcji** , która informuje, skąd pochodzi każda akcja. W poniższej tabeli opisano możliwe wartości **źródła akcji** :

| Wartość źródła akcji | Opis |
|:-----|:---|
| **Ręczna akcja urządzenia** | Ręczna akcja wykonywana na urządzeniu. Przykłady obejmują [izolację urządzenia](../defender-endpoint/respond-machine-alerts.md#isolate-devices-from-the-network) lub [kwarantannę plików](../defender-endpoint/respond-file-alerts.md#stop-and-quarantine-files). |
| **Ręczna akcja poczty e-mail** | Ręczna akcja wykonywana w wiadomości e-mail. Przykład obejmuje usuwanie nietrwałe wiadomości e-mail lub [korygowanie wiadomości e-mail](../office-365-security/remediate-malicious-email-delivered-office-365.md). |
| **Zautomatyzowana akcja urządzenia** | Zautomatyzowana akcja wykonywana na jednostce, taka jak plik lub proces. Przykłady zautomatyzowanych akcji obejmują wysyłanie pliku do kwarantanny, zatrzymywanie procesu i usuwanie klucza rejestru. (Zobacz [Akcje korygowania w Ochrona punktu końcowego w usłudze Microsoft Defender](../defender-endpoint/manage-auto-investigation.md#remediation-actions)). |
| **Zautomatyzowana akcja poczty e-mail** | Zautomatyzowana akcja wykonywana w przypadku zawartości wiadomości e-mail, na przykład wiadomości e-mail, załącznika lub adresu URL. Przykłady zautomatyzowanych akcji obejmują usuwanie nietrwałe wiadomości e-mail, blokowanie adresów URL i wyłączanie przekazywania wiadomości zewnętrznych. (Zobacz [Akcje korygowania w Ochrona usługi Office 365 w usłudze Microsoft Defender](../office-365-security/air-remediation-actions.md)). |
| **Zaawansowana akcja wyszukiwania zagrożeń** | Akcje podejmowane na urządzeniach lub w wiadomościach e-mail z [zaawansowanym wyszukiwaniem zagrożeń](./advanced-hunting-overview.md). |
| **Akcja Eksploratora** | Akcje podejmowane w przypadku zawartości wiadomości e-mail w [Eksploratorze](../office-365-security/threat-explorer.md). |
| **Ręczna akcja odpowiedzi na żywo** | Akcje wykonane na urządzeniu z [odpowiedzią na żywo](../defender-endpoint/live-response.md). Przykłady obejmują usunięcie pliku, zatrzymanie procesu i usunięcie zaplanowanego zadania. |
| **Akcja odpowiedzi na żywo** | Akcje podejmowane na urządzeniu za pomocą [interfejsów API Ochrona punktu końcowego w usłudze Microsoft Defender](../defender-endpoint/management-apis.md#microsoft-defender-for-endpoint-apis). Przykłady akcji obejmują izolowanie urządzenia, uruchamianie skanowania antywirusowego i uzyskiwanie informacji o pliku. |

## <a name="required-permissions-for-action-center-tasks"></a>Wymagane uprawnienia do zadań centrum akcji

Aby wykonywać zadania, takie jak zatwierdzanie lub odrzucanie oczekujących akcji w centrum akcji, musisz mieć przypisane uprawnienia wymienione w poniższej tabeli:

|Akcja korygowania |Wymagane role i uprawnienia |
|--|----|
|Ochrona punktu końcowego w usłudze Microsoft Defender korygowanie (urządzenia) |Rola **administratora zabezpieczeń** przypisana do usługi Azure Active Directory (Azure AD) ([https://portal.azure.com](https://portal.azure.com)) lub Centrum administracyjne platformy Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>--- lub ---<br/>**Rola aktywnych akcji korygowania** przypisana w Ochrona punktu końcowego w usłudze Microsoft Defender <br/> <br/> Aby dowiedzieć się więcej, zobacz następujące zasoby: <br/>- [Azure AD role wbudowane](/azure/active-directory/roles/permissions-reference)<br/>- [Tworzenie ról i zarządzanie nimi na potrzeby kontroli dostępu opartej na rolach (Ochrona punktu końcowego w usłudze Microsoft Defender)](../defender-endpoint/user-roles.md)  |
|Ochrona usługi Office 365 w usłudze Microsoft Defender korygowanie (zawartość pakietu Office i adres e-mail)  |Rola **administratora zabezpieczeń** przypisana w Azure AD ([https://portal.azure.com](https://portal.azure.com)) lub Centrum administracyjne platformy Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>--- i --- <br/>**Rola wyszukiwania i przeczyszczania** przypisana w Centrum zgodności & zabezpieczeń ([https://protection.office.com](https://protection.office.com)) <br/><br/>**WAŻNE**: Jeśli masz przypisaną rolę **administratora zabezpieczeń** tylko w centrum Office 365 Security & Compliance Center ([https://protection.office.com](https://protection.office.com)), nie będziesz mieć dostępu do centrum akcji ani Microsoft 365 Defender możliwości. Musisz mieć przypisaną rolę **administratora zabezpieczeń** w Azure AD lub Centrum administracyjne platformy Microsoft 365. <br/><br/>Aby dowiedzieć się więcej, zobacz następujące zasoby: <br/>- [Azure AD role wbudowane](/azure/active-directory/roles/permissions-reference)<br/>- [Uprawnienia w Centrum zgodności & zabezpieczeń](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) |

> [!TIP]
> Użytkownicy z przypisaną rolą **administratora globalnego** Azure AD mogą zatwierdzać lub odrzucać wszelkie oczekujące akcje w Centrum akcji. Jednak najlepszym rozwiązaniem jest ograniczenie liczby osób mających przypisaną rolę **administratora globalnego** w organizacji. Zalecamy używanie **administratora zabezpieczeń**, **aktywnych akcji korygowania** oraz ról **wyszukiwania i przeczyszczania** wymienionych w poprzedniej tabeli, aby uzyskać uprawnienia centrum akcji.

## <a name="next-step"></a>Następny krok 

- [Wyświetlanie działań naprawczych i zarządzanie nimi](m365d-autoir-actions.md)
