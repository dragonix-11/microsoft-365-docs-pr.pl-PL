---
title: Podstawowe informacje o Eksploratorze zagrożeń i wykrywaniu w czasie rzeczywistym w Ochrona usługi Office 365 w usłudze Microsoft Defender
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
description: Użyj Eksploratora lub wykrywania w czasie rzeczywistym, aby efektywnie badać zagrożenia i reagować na nie.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e7f3109048f3a4931d25029df3db9a3c217d6354
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647430"
---
# <a name="explorer-and-real-time-detections"></a>Wykrywanie eksploratora i czasu rzeczywistego

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W tym artykule:

- [Różnice między wykrywaniem Eksploratora a wykrywaniem w czasie rzeczywistym](#differences-between-explorer-and-real-time-detections)
- [Zaktualizowano środowisko wykrywania Eksploratora i w czasie rzeczywistym](#updated-experience-for-explorer-and-real-time-detections)
- [Wymagane licencje i uprawnienia](#required-licenses-and-permissions)

> [!NOTE]
> Jest to część **serii 3 artykułów** na temat **Eksploratora (znanego również jako Eksplorator zagrożeń),** **zabezpieczeń poczty e-mail** oraz **podstaw wykrywania Eksploratora i czasu rzeczywistego** (takich jak różnice między narzędziami i uprawnienia wymagane do ich obsługi). Pozostałe dwa artykuły z tej serii to [Wyszukiwanie zagrożeń w Eksploratorze](threat-hunting-in-threat-explorer.md) i [Zabezpieczenia poczty e-mail w Eksploratorze](email-security-in-microsoft-defender.md).

W tym artykule wyjaśniono różnicę między raportowaniem wykrywania Eksploratora a wykrywaniem w czasie rzeczywistym, zaktualizowanym środowiskiem Eksploratora i wykrywaniem w czasie rzeczywistym, w którym można przełączać się między starymi i nowymi środowiskami oraz wymaganymi licencjami i uprawnieniami.

Jeśli Twoja organizacja ma [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md) i masz [uprawnienia](#required-licenses-and-permissions), możesz użyć **Eksploratora** (znanego również jako **Eksplorator zagrożeń**) lub **wykrywania w czasie rzeczywistym do wykrywania** i korygowania zagrożeń.

W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do obszaru **Współpraca & poczty e-mail**, a następnie wybierz pozycję **Eksplorator** _lub_ **Wykrywanie w czasie rzeczywistym**. Aby przejść bezpośrednio do strony, użyj polecenia <https://security.microsoft.com/threatexplorer> lub <https://security.microsoft.com/realtimereports>.

Za pomocą tych narzędzi możesz:

- Zobacz złośliwe oprogramowanie wykryte przez funkcje zabezpieczeń Microsoft 365.
- Wyświetl adres URL wyłudzania informacji i kliknij pozycję Dane werdyktu.
- Rozpocznij zautomatyzowane badanie i proces odpowiedzi z widoku w Eksploratorze.
- Zbadaj złośliwą wiadomość e-mail i nie tylko.

Aby uzyskać więcej informacji, zobacz [Zabezpieczenia poczty e-mail w Eksploratorze](email-security-in-microsoft-defender.md).

## <a name="differences-between-explorer-and-real-time-detections"></a>Różnice między wykrywaniem Eksploratora a wykrywaniem w czasie rzeczywistym

- *Wykrywanie w czasie rzeczywistym* to narzędzie do raportowania dostępne w Ochrona usługi Office 365 w usłudze Defender planie 1. *Eksplorator zagrożeń* to narzędzie do wyszukiwania zagrożeń i korygowania dostępne w planie Ochrona usługi Office 365 w usłudze Defender 2.
- Raport wykrywania w czasie rzeczywistym umożliwia wyświetlanie wykrywania w czasie rzeczywistym. Eksplorator zagrożeń również to robi, ale udostępnia dodatkowe szczegóły danego ataku, takie jak wyróżnianie kampanii ataków, i zapewnia zespołom operacji zabezpieczeń możliwość korygowania zagrożeń (w tym wyzwalania [zautomatyzowanego badania i badania odpowiedzi](automated-investigation-response-office.md).
- Widok *Wszystkie wiadomości e-mail* jest dostępny w Eksploratorze zagrożeń, ale nie jest uwzględniony w raporcie wykrywania w czasie rzeczywistym.
- Zaawansowane możliwości filtrowania i akcje korygowania są dostępne w Eksploratorze zagrożeń. Aby uzyskać więcej informacji, zobacz [Ochrona usługi Office 365 w usłudze Microsoft Defender Service Description: Feature availability across Ochrona usługi Office 365 w usłudze Defender plans (Opis usługi Ochrona usługi Office 365 w usłudze Microsoft Defender: dostępność funkcji w planach Ochrona usługi Office 365 w usłudze Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans)).

## <a name="updated-experience-for-explorer-and-real-time-detections"></a>Zaktualizowano środowisko wykrywania Eksploratora i w czasie rzeczywistym

Środowisko wykrywania zagrożeń i wykrywania w czasie rzeczywistym jest aktualizowane tak, aby było zgodne z nowoczesnymi standardami ułatwień dostępu i optymalizując przepływ pracy. Przez krótki czas będzie można przełączać się między starym doświadczeniem a nowym.  

> [!NOTE]
> Przełączanie ma wpływ tylko na Twoje konto i nie ma wpływu na inną osobę w dzierżawie. 

Wykrywanie zagrożeń i wykrywania w czasie rzeczywistym jest podzielone na następujące widoki:

- *Wszystkie wiadomości e-mail*: wyświetla wszystkie wiadomości e-mail analizowane przez usługę Defender dla usługi Office 365 i zawierają zarówno dobre, jak i złośliwe wiadomości e-mail. Ta funkcja jest obecna tylko w Eksploratorze zagrożeń i nie jest dostępna w przypadku wykrywania w czasie rzeczywistym. Domyślnie jest ona ustawiona na wyświetlanie danych przez dwa dni, które można rozszerzyć do 30 dni. Jest to również widok domyślny dla Eksploratora zagrożeń.  

- *Widok złośliwego oprogramowania*: pokazuje wiadomości e-mail, na których zidentyfikowano zagrożenie złośliwym oprogramowaniem. Jest to domyślny widok wykrywania w czasie rzeczywistym i pokazuje dane z dwóch dni (można je rozszerzyć do 30 dni).  

- *Widok phish*: pokazuje wiadomości e-mail, na których zidentyfikowano zagrożenie phish.

- *Widok złośliwego oprogramowania* zawartości: pokazuje złośliwe wykrycia zidentyfikowane w plikach udostępnionych za pośrednictwem OneDrive, SharePoint lub Teams. 

Oto typowe składniki w tych środowiskach:

- Filtry

    - Możesz użyć różnych filtrów, aby wyświetlić dane na podstawie atrybutów poczty e-mail lub pliku.  

    - Domyślnie filtr czasu jest stosowany do rekordów i jest stosowany przez dwa dni.  

    - Jeśli stosujesz wiele filtrów, są one stosowane w trybie "AND" i można użyć filtru zaawansowanego, aby zmienić go na tryb "OR".  

    - Przecinki umożliwiają dodanie wielu wartości dla tego samego filtru.  

    > [!div class="mx-imgBorder"]
    > ![Filtry Eksploratora](../../media/explorer-new-experience-filters.png)

- Wykresy

    - Wykresy zapewniają wizualny, agregujący widok danych na podstawie filtrów. Możesz użyć różnych filtrów, aby wyświetlić dane według różnych wymiarów.  

    > [!NOTE]
    > Wyniki w widoku wykresu mogą nie być widoczne, nawet jeśli widzisz wpis w widoku listy. Dzieje się tak, jeśli filtr nie generuje żadnych danych. Jeśli na przykład zastosowano rodzinę złośliwego oprogramowania filtru, ale dane bazowe nie zawierają żadnych złośliwych wiadomości e-mail, w tym scenariuszu mogą pojawić się żadne dane.  

    > [!div class="mx-imgBorder"]
    > ![Widok wykresu Eksploratora](../../media/explorer-new-experience-export-chart-data.png)

- Siatka wyników  

    - Siatka wyników pokazuje wyniki wiadomości e-mail na podstawie zastosowanych filtrów.  

    - Na podstawie konfiguracji ustawionej w dzierżawie dane będą wyświetlane w formacie UTC lub lokalnej strefie czasowej, a informacje o strefie czasowej będą dostępne w pierwszej kolumnie.  

    - Możesz przejść do indywidualnej strony jednostki poczty e-mail z widoku listy, klikając ikonę **Otwórz w nowym oknie** . 

    - Możesz również dostosować kolumny, aby dodawać lub usuwać kolumny, aby zoptymalizować widok.

    > [!Note]
    > Aby zmaksymalizować zestaw wyników, możesz przełączać się między *widokiem wykresu* a *widokiem listy* .  

    > [!div class="mx-imgBorder"]
    > ![Widok siatki Eksploratora](../../media/explorer-new-experience-list-chart-view.png)

- Szczegółowy wysuwany  

    - Możesz kliknąć hiperlinki, aby przejść do panelu podsumowania wiadomości e-mail (wpisy w kolumnie Temat), adresata lub wysuwanego adresu IP.  

    - Panel podsumowania wiadomości e-mail zastępuje starsze wysuwane wiadomości e-mail, a także udostępnia ścieżkę dostępu do panelu jednostki poczty e-mail.  

    - Poszczególne wysuwane jednostki, takie jak adres IP, adresat i adres URL, odzwierciedlają te same informacje, ale są prezentowane w widoku opartym na jednej karcie, z możliwością rozwijania i zwijania różnych sekcji na podstawie wymagań.  

    - W przypadku wysuwanych elementów, takich jak adresy URL, możesz kliknąć pozycję **Wyświetl wszystkie wiadomości e-mail** lub **Wyświetl wszystkie kliknięcia** , aby wyświetlić pełny zestaw wiadomości e-mail/kliknięć zawierających ten adres URL, a także wyeksportować zestaw wyników.  

- Działania

    - W Eksploratorze zagrożeń można wyzwalać akcje korygowania, takie jak *Usuwanie wiadomości e-mail*. Aby uzyskać więcej informacji na temat korygowania, limitów korygowania i śledzenia korygowania, zobacz [Korygowanie złośliwych wiadomości e-mail](remediate-malicious-email-delivered-office-365.md).  

- Eksportowanie

    - Aby wyeksportować szczegóły wykresu, możesz kliknąć pozycję **Eksportuj dane wykresu** . Podobnie kliknij pozycję **Eksportuj listę wiadomości e-mail** , aby wyeksportować szczegóły wiadomości e-mail.

    - Możesz wyeksportować do 200 000 rekordów dla listy wiadomości e-mail. Jednak w celu zwiększenia wydajności systemu i skrócenia czasu pobierania należy użyć różnych filtrów poczty e-mail.

    > [!div class="mx-imgBorder"]
    > ![Eksportowanie danych wykresu](../../media/explorer-new-experience-export-chart-data.png)

Oprócz tych funkcji uzyskasz również zaktualizowane środowiska, takie jak *najważniejsze adresy URL*, *najważniejsze kliknięcia*, *użytkownicy docelowi i* *źródło wiadomości e-mail*. *Najważniejsze adresy URL*, *kliknięcia górne* i *użytkownicy docelowi* mogą być dalej filtrowane na podstawie filtru zastosowanego w Eksploratorze. 

## <a name="required-licenses-and-permissions"></a>Wymagane licencje i uprawnienia

Musisz mieć [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md), aby używać Eksploratora lub wykrywania w czasie rzeczywistym:

- Eksplorator jest uwzględniony tylko w planie Ochrona usługi Office 365 w usłudze Defender 2.
- Raport wykrywania w czasie rzeczywistym jest uwzględniony w planie Ochrona usługi Office 365 w usłudze Defender 1.

Zespoły ds. operacji zabezpieczeń muszą przypisywać licencje dla wszystkich użytkowników, którzy powinni być chronieni przez Ochrona usługi Office 365 w usłudze Defender i mieć świadomość, że w Eksploratorze i wykrywaniu w czasie rzeczywistym są wyświetlane dane wykrywania dla licencjonowanych użytkowników.

Do wyświetlania i używania Eksploratora *lub* wykrywania w czasie rzeczywistym potrzebne są następujące uprawnienia:

- W Ochrona usługi Office 365 w usłudze Defender:
  - Zarządzanie organizacją
  - Administrator zabezpieczeń (można to przypisać w centrum administracyjnym Azure Active Directory (<https://aad.portal.azure.com>)
  - Czytelnik zabezpieczeń
- W Exchange Online:
  - Zarządzanie organizacją
  - zarządzanie organizacją View-Only
  - adresaci View-Only
  - Zarządzanie zgodnością

Aby dowiedzieć się więcej na temat ról i uprawnień, zobacz następujące artykuły:

- [Uprawnienia w portalu usługi Microsoft 365 Defender](permissions-microsoft-365-security-center.md)
- [Uprawnienia w Exchange Online](/e/exchange/permissions-exo/permissions-exo)

## <a name="more-information"></a>Więcej informacji

- [Eksplorator zagrożeń zbiera szczegóły wiadomości e-mail na stronie jednostki poczty e-mail](mdo-email-entity-page.md)
- [Znajdowanie i badanie dostarczonej złośliwej wiadomości e-mail](investigate-malicious-email-that-was-delivered.md)
- [Wyświetlanie złośliwych plików wykrytych w usłudze SharePoint Online, OneDrive i Microsoft Teams](mdo-for-spo-odb-and-teams.md)
- [Raport o stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report)
- [Zautomatyzowane badanie i reagowanie w usłudze Microsoft Threat Protection](automated-investigation-response-office.md)
