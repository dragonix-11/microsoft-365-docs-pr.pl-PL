---
title: Przejdź do Centrum akcji, aby wyświetlić i zatwierdzić zadania automatycznego badania i rozwiązywania problemów
description: Wyświetlanie szczegółów automatycznego badania i zatwierdzanie oczekujących akcji za pomocą Centrum akcji
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
ms.openlocfilehash: e4ac7636b019b0e8c1d00487e95335ede4600d85
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2022
ms.locfileid: "64570046"
---
# <a name="the-action-center"></a>Centrum akcji

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Centrum akcji udostępnia "pojedyncze okienko szyby" dla zadań związanych z incydentami i alertami, takich jak:

- Zatwierdzanie oczekujących działań naprawczych.
- Wyświetlanie dziennika inspekcji już zatwierdzonych działań naprawczych.
- Przeglądanie ukończonych działań naprawczych.

Ponieważ Centrum akcji udostępnia obszerny Microsoft 365 Defender w pracy, Twój zespół operacyjny bezpieczeństwa może działać wydajniej i skuteczniej.

## <a name="the-unified-action-center"></a>Ujednolicone Centrum akcji

Ujednolicone Centrum akcji zawiera[https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) listę oczekujących i ukończonych akcji naprawczych dla Twoich urządzeń, wiadomości e& zawartości współpracy i tożsamości w jednym miejscu.

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="Ujednolicone Centrum akcji w portalu Microsoft 365 Defender akcji." lightbox="../../media/m3d-action-center-unified.png":::

Przykład: 

- Jeśli wcześniej korzystano z Centrum Office 365 zabezpieczeń & ([https://protection.office.com](https://protection.office.com)), wypróbuj ujednolicone Centrum akcji w portalu Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">zabezpieczeń</a>.
- Jeśli korzystano z Centrum akcji w centrum Centrum zabezpieczeń usługi Microsoft Defender ([https://securitycenter.windows.com/action-center](https://securitycenter.windows.com/action-center)), wypróbuj ujednolicone Centrum akcji w portalu Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">akcji</a>.
- Jeśli korzystasz już z portalu <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, zobaczysz kilka ulepszeń w Centrum akcji ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)).

Ujednolicone Centrum akcji łączy działania naprawcze w usługach Defender for Endpoint i Ochrona usługi Office 365 w usłudze Defender. Definiuje on język wspólny dla wszystkich działań naprawczych i zapewnia ujednolicone środowisko badania. Zespół operacyjny ds. zabezpieczeń ma "pojedyncze okienko szyb" do wyświetlania działań naprawczych i zarządzania nimi.  

Ujednoliconego Centrum akcji możesz używać, jeśli masz odpowiednie uprawnienia i co najmniej jedną z następujących subskrypcji:

- [Ochrona punktu końcowego w usłudze Microsoft Defender](../defender-endpoint/microsoft-defender-endpoint.md)
- [Ochrona usługi Office 365 w usłudze Defender](/microsoft-365/security/office-365-security/defender-for-office-365)
- [Microsoft 365 Defender](microsoft-365-defender.md)

> [!TIP]
> Aby dowiedzieć się więcej, zobacz [Wymagania](./prerequisites.md).

## <a name="using-the-action-center"></a>Korzystanie z Centrum akcji

1. Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender i</a> zaloguj się. 
2. W okienku nawigacji wybierz pozycję **Centrum akcji**. 

Po odwiedzenia Centrum akcji są dostępne dwie karty: **Oczekujące akcje** i **Historia**. W poniższej tabeli podsumowano elementy, które będą zawierały poszczególne karty:

|Tab  |Opis  |
|---------|---------|
|**Oczekiwanie**     | Wyświetla listę akcji wymagających uwagi. Możesz zatwierdzać lub odrzucać akcje na raz albo wybierać wiele akcji, jeśli mają one taki sam typ akcji (na przykład plik kwarantanny). <p>**PORADA**: Należy jak najszybciej przejrzeć i zatwierdzić (lub odrzucić) oczekujące akcje, aby można było wykonać zautomatyzowane badania w terminie.       |
|**Historia**     | Pełni rolę dziennika inspekcji dla działań, które zostały wykonane, takich jak: <br/>— Działania naprawcze podejmowane w wyniku zautomatyzowanych badań <br/>— Działania naprawcze podejmowane w przypadku podejrzanych lub złośliwych wiadomości e-mail, plików lub adresów URL<br/>— Działania naprawcze, które zostały zatwierdzone przez Twój zespół operacyjny ds. zabezpieczeń <br/>— Polecenia uruchomione i akcje naprawcze, które były stosowane podczas sesji odpowiedzi na żywo<br/>— Działania naprawcze wykonane przez ochronę antywirusową <p>Umożliwia cofnięcie pewnych akcji (zobacz [Cofanie ukończonych akcji](m365d-autoir-actions.md#undo-completed-actions)).        |

W Centrum akcji możesz dostosowywać, sortować, filtrować i eksportować dane.

:::image type="content" source="../../media/m3d-action-center-columnsfilters.png" alt-text="Funkcje sortowania, filtrowania i dostosowywania w Centrum akcji" lightbox="../../media/m3d-action-center-columnsfilters.png":::

- Zaznacz nagłówek kolumny, aby posortować elementy w kolejności rosnącej lub malejącej.
- Użyj filtru okresu, aby wyświetlić dane za przeszły dzień, tydzień, 30 dni lub 6 miesięcy.
- Wybierz kolumny, które chcesz wyświetlić.
- Określ liczbę elementów, które mają być dołączane na każdej stronie danych.
- Użyj filtrów, aby wyświetlić tylko te elementy, które chcesz wyświetlić.
- Wybierz **pozycję Eksportuj** , aby wyeksportować wyniki do .csv pliku.

## <a name="actions-tracked-in-the-action-center"></a>Akcje śledzone w Centrum akcji

Wszystkie akcje, niezależnie od tego, czy oczekują na zatwierdzenie, czy zostały już wykonane, są śledzone w Centrum akcji. Dostępne są następujące akcje:

- Zbieraj pakiet badań 
- Wyizoluj urządzenie (tę akcję można cofnąć) 
- Odłącz komputer 
- Wykonywanie kodu wydania 
- Zwolnienie z kwarantanny 
- Przykład żądania 
- Ograniczanie wykonywania kodu (tę akcję można cofnąć) 
- Uruchomiono skanowanie antywirusowe 
- Zatrzymywanie i kwarantanna 

Oprócz działań naprawczych, które są podejmowane automatycznie w wyniku zautomatyzowanych [badań, Centrum](m365d-autoir.md) akcji śledzi również akcje wykonane przez Twój zespół zabezpieczeń w celu rozwiązania wykrytych zagrożeń oraz akcje wykonane w wyniku funkcji ochrony przed zagrożeniami w programie Microsoft 365 Defender. Aby uzyskać więcej informacji na temat automatycznych i ręcznych działań naprawczych, zobacz [Akcje naprawcze](m365d-remediation-actions.md).

## <a name="viewing-action-source-details"></a>Wyświetlanie szczegółów źródła akcji

(**NOWOŚĆ!**) Ulepszone Centrum akcji zawiera teraz **kolumnę Źródło** akcji, która informuje o tym, skąd pochodzą poszczególne akcje. W poniższej tabeli opisano możliwe **wartości źródła** akcji:

| Wartość źródła akcji | Opis |
|:-----|:---|
| **Ręczna akcja urządzenia** | Czynność podejmowane ręcznie na urządzeniu. Przykłady obejmują [izolacji urządzenia](../defender-endpoint/respond-machine-alerts.md#isolate-devices-from-the-network) lub [kwarantannę pliku](../defender-endpoint/respond-file-alerts.md#stop-and-quarantine-files). |
| **Ręczna akcja wiadomości e-mail** | Czynność podejmowane ręcznie na wiadomości e-mail. Przykład obejmuje "miękkie usunięcie" wiadomości e-mail lub [rozwiązywanie problemów z wiadomością](../office-365-security/remediate-malicious-email-delivered-office-365.md). |
| **Automatyczna akcja urządzenia** | Zautomatyzowane działanie podejmowane w encji, takiej jak plik lub proces. Przykłady zautomatyzowanych akcji to wysłanie pliku do kwarantanny, zatrzymanie procesu i usunięcie klucza rejestru. (Zobacz [Działania naprawcze w programie Ochrona punktu końcowego w usłudze Microsoft Defender](../defender-endpoint/manage-auto-investigation.md#remediation-actions)). |
| **Automatyczna akcja wiadomości e-mail** | Zautomatyzowane działanie podejmowane w związku z zawartością wiadomości e-mail, taką jak wiadomość e-mail, załącznik lub adres URL. Przykładami zautomatyzowanych akcji są miękkie usuwanie wiadomości e-mail, blokowanie adresów URL i wyłączanie zewnętrznego przesyłania dalej poczty. (Zobacz [Działania naprawcze w programie Ochrona usługi Office 365 w usłudze Microsoft Defender](../office-365-security/air-remediation-actions.md)). |
| **Zaawansowana akcja łętwna** | Akcje wykonane na urządzeniach lub w wiadomości e-mail z [zaawansowanymi wyszukiwaniami](./advanced-hunting-overview.md). |
| **Akcja Eksploratora** | Akcje podejmowane w przypadku zawartości wiadomości e-mail za pomocą [Eksploratora](../office-365-security/threat-explorer.md). |
| **Ręczne działanie odpowiedzi na żywo** | Akcje wykonane na urządzeniu z [odpowiedzią na żywo](../defender-endpoint/live-response.md). Przykłady: usunięcie pliku, zatrzymanie procesu i usunięcie zaplanowanego zadania. |
| **Akcja odpowiedzi na żywo** | Akcje wykonane na urządzeniu z Ochrona punktu końcowego w usłudze Microsoft Defender [API](../defender-endpoint/management-apis.md#microsoft-defender-for-endpoint-apis). Przykłady akcji to odizolowanie urządzenia, uruchamianie skanowania antywirusowego i uzyskiwanie informacji o pliku. |

## <a name="required-permissions-for-action-center-tasks"></a>Wymagane uprawnienia dla zadań Centrum akcji

Aby wykonywać zadania, takie jak zatwierdzanie lub odrzucanie akcji oczekujących w Centrum akcji, musisz mieć przypisane uprawnienia wymienione w poniższej tabeli:

|Działania naprawcze |Wymagane role i uprawnienia |
|--|----|
|Ochrona punktu końcowego w usłudze Microsoft Defender działania naprawcze (urządzenia) |**Rola administratora** zabezpieczeń przypisana w usłudze Azure Active Directory (Azure AD) ([https://portal.azure.com](https://portal.azure.com)) lub usłudze Centrum administracyjne platformy Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>--- lub ---<br/>**Rola aktywnej akcji naprawczych** przypisana w programie Ochrona punktu końcowego w usłudze Microsoft Defender <br/> <br/> Aby dowiedzieć się więcej, zobacz następujące zasoby: <br/>- [Wbudowane role w usłudze Azure AD](/azure/active-directory/roles/permissions-reference)<br/>- [Tworzenie ról w kontrolach dostępu opartych na rolach i zarządzanie nimi (Ochrona punktu końcowego w usłudze Microsoft Defender)](../defender-endpoint/user-roles.md)  |
|Ochrona usługi Office 365 w usłudze Microsoft Defender dotyczące rozwiązywania problemów (Office zawartości i wiadomości e-mail)  |**Rola administratora** zabezpieczeń przypisana w usłudze Azure AD ([https://portal.azure.com](https://portal.azure.com)) lub w usłudze Centrum administracyjne platformy Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>--- i --- <br/>**Rola wyszukiwania i przeczyszczania** przypisana w Centrum zgodności & zabezpieczeń ([https://protection.office.com](https://protection.office.com)) <br/><br/>**WAŻNE**: Jeśli masz przypisaną rolę **Administratora** zabezpieczeń tylko w Centrum zgodności usługi Office 365 Security & ([https://protection.office.com](https://protection.office.com)), nie będziesz mieć dostępu do Centrum akcji ani funkcji Microsoft 365 Defender zabezpieczeń. Musisz mieć przypisaną **rolę Administratora** zabezpieczeń w usłudze Azure AD lub Centrum administracyjne platformy Microsoft 365. <br/><br/>Aby dowiedzieć się więcej, zobacz następujące zasoby: <br/>- [Wbudowane role w usłudze Azure AD](/azure/active-directory/roles/permissions-reference)<br/>- [Uprawnienia w Centrum & zgodności](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) |

> [!TIP]
> Użytkownicy z przypisaną **rolą administratora globalnego** w usłudze Azure AD mogą zatwierdzić lub odrzucić wszystkie oczekujące akcje w Centrum akcji. Najlepszym rozwiązaniem jest jednak ograniczenie liczby osób z przypisaną rolą **administratora** globalnego. Zalecamy używanie ról **Administrator** **zabezpieczeń, Aktywne** działania naprawcze oraz Ról wyszukiwania i  przeczyszczania wymienionych w poprzedniej tabeli dla uprawnień Centrum akcji.

## <a name="next-step"></a>Następny krok 

- [Wyświetlanie działań naprawczych i zarządzanie nimi](m365d-autoir-actions.md)
