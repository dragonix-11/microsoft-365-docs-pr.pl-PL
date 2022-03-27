---
title: Wykrywanie zagrożeń w Eksploratorze zagrożeń i w czasie rzeczywistym w programie Microsoft Defender dla Office 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: MSFTTracyp
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 05/05/2021
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Efektywne badanie zagrożeń i reagowanie na nie za pomocą wykrywania w Eksploratorze lub czasie rzeczywistym.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3b889649de7b56d6a1b5300ff323850a4e555b57
ms.sourcegitcommit: 9c8eca862a2f0fdca7a66c641e382e37fcaefa10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2022
ms.locfileid: "63775373"
---
# <a name="explorer-and-real-time-detections"></a>Wykrywanie Eksploratora i w czasie rzeczywistym

**Dotyczy**
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W tym artykule:

- [Różnice między wykrywaniem w Czasie rzeczywistym a Eksploratorem](#differences-between-explorer-and-real-time-detections)
- [Zaktualizowano środowisko wykrywania w Eksploratorze i w czasie rzeczywistym](#updated-experience-for-explorer-and-real-time-detections)
- [Wymagane licencje i uprawnienia](#required-licenses-and-permissions)

> [!NOTE]
> Jest to część 3-articleowej serii w Eksploratorze **(** znanej również jako Eksplorator zagrożeń), zabezpieczeń poczty **e-mail** oraz eksploratora i wykrywania w czasie rzeczywistym (takich jak różnice między narzędziami i uprawnienia potrzebne do ich obsługi). Pozostałe dwa artykuły z tej serii to Wyszukiwania zagrożeń w [Eksploratorze i](threat-hunting-in-threat-explorer.md) Zabezpieczenia [poczty e-mail w Eksploratorze](email-security-in-microsoft-defender.md).

W tym artykule wyjaśniono różnice między raportowaniem Eksploratora a wykrywaniem w czasie rzeczywistym, zaktualizowanym doświadczeniem w Eksploratorze i wykrywaniami w czasie rzeczywistym, gdzie można przełączać się między starym i nowym środowiskom oraz wymaganymi licencjami i uprawnieniami.

Jeśli organizacja ma program [Microsoft Defender for Office 365](defender-for-office-365.md) i masz odpowiednie [uprawnienia, możesz](#required-licenses-and-permissions) wykrywać i reagotować zagrożenia za pomocą Eksploratora **(znanego** również jako Eksplorator **zagrożeń) lub** wykrywania w czasie rzeczywistym.

W portalu Microsoft 365 Defender przejdź <https://security.microsoft.com>do opcji Współpraca za pomocą poczty **e-mail &**, a następnie wybierz pozycję **Eksplorator**  lub **Wykrywanie w czasie rzeczywistym**. Aby przejść bezpośrednio do strony, użyj lub <https://security.microsoft.com/threatexplorer> <https://security.microsoft.com/realtimereports>.

Za pomocą tych narzędzi możesz:

- Zobacz złośliwe oprogramowanie wykryte przez Microsoft 365 zabezpieczeń.
- Wyświetl adres URL wyłudzania informacji i kliknij pozycję werdykt danych.
- Uruchom zautomatyzowany proces badania i odpowiedzi z widoku w Eksploratorze.
- Badanie złośliwych wiadomości e-mail i nie tylko.

Aby uzyskać więcej informacji, zobacz [Zabezpieczenia poczty e-mail w Eksploratorze](email-security-in-microsoft-defender.md).

## <a name="differences-between-explorer-and-real-time-detections"></a>Różnice między wykrywaniem w Czasie rzeczywistym a Eksploratorem

- *Wykrywanie w czasie rzeczywistym to* narzędzie do raportowania dostępne w programie Defender dla Office 365 Plan 1. *Eksplorator zagrożeń to* narzędzie do wyszukiwania i rozwiązywania problemów ze zagrożeniami dostępne w programie Defender dla Office 365 Plan 2.
- Raport Wykrywanie w czasie rzeczywistym umożliwia wyświetlanie wykrywania w czasie rzeczywistym. Narzędzie Eksplorator zagrożeń również to robi, ale udostępnia dodatkowe szczegóły dotyczące danego ataku, takie jak wyróżnianie kampanii ataków, oraz udostępnia zespołom operacji zabezpieczeń możliwość korygowania zagrożeń (w tym wyzwalania automatycznego badania i analizy [odpowiedzi).](automated-investigation-response-office.md)
- Widok *Cała poczta e-mail* jest dostępny w Eksploratorze zagrożeń, ale nie jest uwzględniony w raporcie Wykrywanie w czasie rzeczywistym.
- W Eksploratorze zagrożeń są dostępne rozbudowane funkcje filtrowania i akcje naprawcze. Aby uzyskać więcej informacji, zobacz [Microsoft Defender for Office 365 Service Description: Feature availability across Defender for Office 365 plans](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

## <a name="updated-experience-for-explorer-and-real-time-detections"></a>Zaktualizowano środowisko wykrywania w Eksploratorze i w czasie rzeczywistym

Środowisko wykrywania zagrożeń w Eksploratorze i czasie rzeczywistym jest aktualizowane w celu dostosowania do nowoczesnych standardów ułatwień dostępu i zoptymalizowania przepływu pracy. Przez krótki czas będzie można przełączać się między starym i nowym.  

> [!NOTE]
> Przełączanie ma wpływ tylko na Twoje konto i nie ma wpływu na inne osoby w Twojej dzierżawie. 

Wykrywanie zagrożeń w Eksploratorze i w czasie rzeczywistym jest podzielone na następujące widoki:

- *Wszystkie wiadomości e-mail*: Wyświetla wszystkie wiadomości e-mail analizowane przez usługę Defender dla usługi Office 365 oraz zawierające zarówno dobre, jak i złośliwe wiadomości e-mail. Ta funkcja jest dostępna tylko w Eksploratorze zagrożeń i nie jest dostępna dla wykrywania w czasie rzeczywistym. Domyślnie jest tak ustawione wyświetlanie danych dla dwóch dni, które można rozszerzyć do 30 dni. Jest to również widok domyślny Eksploratora zagrożeń.  

- *Widok złośliwego oprogramowania*: wyświetla wiadomości e-mail, w których zidentyfikowano zagrożenie złośliwym oprogramowaniem. Jest to widok domyślny dla wykrywania w czasie rzeczywistym i wyświetla dane dla dwóch dni (można je rozszerzyć do 30 dni).  

- *Widok wyłudzy*: wyświetla wiadomości e-mail, w których zidentyfikowano zagrożenie.

- *Widok złośliwego oprogramowania*: pokazuje złośliwe wykrywanie plików zidentyfikowanych w OneDrive, SharePoint lub innych Teams. 

Oto typowe składniki w tych środowiskoch:

- Filtry

    - Za pomocą różnych filtrów możesz wyświetlać dane na podstawie atrybutów plików lub wiadomości e-mail.  

    - Domyślnie filtr czasu jest stosowany do rekordów i jest stosowany przez dwa dni.  

    - Jeśli stosujesz wiele filtrów, są one stosowane w trybie "ORAZ" i możesz użyć filtru zaawansowanego, aby zmienić go na tryb "LUB".  

    - Możesz użyć przecinków, aby dodać wiele wartości dla tego samego filtru.  

    > [!div class="mx-imgBorder"]
    > ![Filtry w Eksploratorze](../../media/explorer-new-experience-filters.png)

- Wykresy

    - Wykresy zapewniają wizualny, zagregowany widok danych oparty na filtrach. Dane można wyświetlać według różnych wymiarów za pomocą różnych filtrów.  

    > [!NOTE]
    > W widoku wykresu możesz nie wyświetlać żadnych wyników, nawet jeśli widzisz pozycję w widoku listy. Dzieje się tak, jeśli filtr nie powoduje uzyskania żadnych danych. Jeśli na przykład zastosowano filtr rodziny złośliwego oprogramowania, ale dane źródłowe nie mają żadnych złośliwych wiadomości e-mail, w tym scenariuszu może być wyświetlany komunikat, w którym nie ma dostępnych danych.  

    > [!div class="mx-imgBorder"]
    > ![Widok wykresu w Eksploratorze](../../media/explorer-new-experience-export-chart-data.png)

- Siatka wyników  

    - Siatka wyników pokazuje wyniki wiadomości e-mail na podstawie zastosowanych filtrów.  

    - Na podstawie zestawu konfiguracji dzierżawcy dane będą wyświetlane w czasie UTC lub lokalnej strefy czasowej, a informacje o strefie czasowej będą dostępne w pierwszej kolumnie.  

    - Możesz przejść do strony jednostki poczty e-mail z widoku listy, klikając **ikonę Otwórz w nowym oknie** . 

    - Możesz również dostosować kolumny, aby dodać lub usunąć kolumny w celu zoptymalizowania widoku.

    > [!Note]
    > Możesz przełączać się między widokiem *wykresu* *i widokiem listy* , aby zmaksymalizować zestaw wyników.  

    > [!div class="mx-imgBorder"]
    > ![Widok siatki Eksploratora](../../media/explorer-new-experience-list-chart-view.png)

- Szczegółowe wysuwu  

    - Możesz kliknąć hiperlinki, aby przejść do panelu podsumowania wiadomości e-mail (wpisów w kolumnie Temat), adresata lub wysuwu adresu IP.  

    - Panel podsumowania wiadomości e-mail zastępuje starsze wysuwne wiadomości e-mail oraz udostępnia ścieżkę dostępu do panelu encji wiadomości e-mail.  

    - Poszczególne encji wysuwu, takie jak IP, recipient i URL, odzwierciedlałyby te same informacje, ale przedstawiane w jednym widoku opartym na kartach, z możliwością rozwijania i zwijania poszczególnych sekcji w zależności od wymagań.  

    - W przypadku wysuwu, takiego jak adresy URL, możesz kliknąć pozycję  Wyświetl wszystkie wiadomości e-mail lub Wyświetl wszystkie kliknięcia, aby wyświetlić pełny zestaw wiadomości e-mail/kliknięć zawierających ten adres URL, a także wyeksportować zestaw wyników.  

- Akcje

    - W Eksploratorze zagrożeń możesz wyzwalać akcje naprawcze, takie jak *Usuwanie wiadomości e-mail*. Aby uzyskać więcej informacji na temat rozwiązywania problemów, limitów rozwiązywania problemów i śledzenia środków zaradczych, zobacz [Rozwiązywanie problemów ze złośliwymi wiadomościami e-mail](remediate-malicious-email-delivered-office-365.md).  

- Eksportowanie

    - Możesz kliknąć pozycję **Eksportuj dane wykresu** , aby wyeksportować szczegóły wykresu. Podobnie kliknij pozycję **Eksportuj listę wiadomości e-mail,** aby wyeksportować szczegóły wiadomości e-mail.

    - Możesz wyeksportować do 200 000 rekordów dla listy wiadomości e-mail. Jednak w celu lepszej wydajności systemu i skrócenia czasu pobierania należy używać różnych filtrów wiadomości e-mail.

    > [!div class="mx-imgBorder"]
    > ![Eksportowanie danych wykresu](../../media/explorer-new-experience-export-chart-data.png)

Oprócz tych funkcji otrzymasz również zaktualizowane środowisko, takie jak na początku adresów *URL**, na* początku *kliknięć,* Najgorętsi użytkownicy docelowi i Pochodzenie wiadomości *e-mail*. *Top URL*, *Top clicks*, and *Top targeted users* can be further filtered based on the filter that you apply within Explorer. 

## <a name="required-licenses-and-permissions"></a>Wymagane licencje i uprawnienia

Program [Microsoft Defender for Office 365](defender-for-office-365.md) może korzystać z wykrywania w Czasie rzeczywistym lub Eksploratora:

- Eksplorator jest dołączony tylko do usługi Defender dla Office 365 Plan 2.
- Raport wykrywanie w czasie rzeczywistym jest zawarty w programie Defender for Office 365 Plan 1.

Zespoły ds. operacji zabezpieczeń muszą przypisywać licencje wszystkim użytkownikom, którzy powinni być chronieni przez program Defender for Office 365, i mieć świadomość, że wykrywanie Eksploratora i czasu rzeczywistego pokazuje dane wykrywania dla licencjonowanych użytkowników.

Do wyświetlania i używania *wykrywania* w Eksploratorze lub w czasie rzeczywistym potrzebne są następujące uprawnienia:

- W programie Defender dla Office 365:
  - Zarządzanie organizacją
  - Administrator zabezpieczeń (tę pozycję można przypisać w centrum administracyjnym Azure Active Directory (<https://aad.portal.azure.com>)
  - Czytnik zabezpieczeń
- W Exchange Online:
  - Zarządzanie organizacją
  - View-Only zarządzanie organizacją
  - View-Only adresaci
  - Zarządzanie zgodnością

Aby dowiedzieć się więcej o rolach i uprawnieniach, zobacz następujące artykuły:

- [Uprawnienia w Microsoft 365 Defender portalu](permissions-microsoft-365-security-center.md)
- [Uprawnienia w aplikacji Exchange Online](/e/exchange/permissions-exo/permissions-exo)

## <a name="more-information"></a>Więcej informacji

- [Eksplorator zagrożeń zbiera szczegóły wiadomości e-mail na stronie jednostki wiadomości e-mail](mdo-email-entity-page.md)
- [Znajdowanie i badanie dostarczonych złośliwych wiadomości e-mail](investigate-malicious-email-that-was-delivered.md)
- [Wyświetlaj złośliwe pliki wykryte w usługach SharePoint Online, OneDrive i Microsoft Teams](mdo-for-spo-odb-and-teams.md)
- [Raport o stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report)
- [Automatyczne badanie i reagowanie w zakresie ochrony przed zagrożeniami firmy Microsoft](automated-investigation-response-office.md)
