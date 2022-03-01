---
title: Szablony informacji o zarządzaniu ryzykiem w niejawnym programie testów
description: Informacje o szablonach informacji o zarządzaniu ryzykiem w programie Microsoft 365
keywords: Microsoft 365, zarządzanie ryzykiem w niejawnym programie testów, zarządzanie ryzykiem, zgodność
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: cfa9628861e592b1e8cf235fe5c68e538be354ba
ms.sourcegitcommit: efb333ce0772265da91632110acba39acfbe0bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2021
ms.locfileid: "62996843"
---
# <a name="insider-risk-management-notice-templates"></a>Szablony informacji o zarządzaniu ryzykiem w niejawnym programie testów

Szablony powiadomiń o zarządzaniu ryzykiem w ramach niejawnego programu testów umożliwiają automatyczne wysyłanie wiadomości e-mail do użytkowników po utworzeniu sprawy dotyczącej działań, które wygenerowały dopasowanie zasad i potwierdzone alerty. W przypadku większości alertów generującej przypadki akcje użytkownika są wynikiem błędów lub niezamierzonych działań bez określonych intencji. Powiadomienia mogą służyć jako proste przypomnienia dla użytkowników, aby zachować większą ostrożność, zawierać linki do informacji na temat odświeżanego szkolenia lub do zasobów zasad firmy. Powiadomienia mogą być ważną częścią wewnętrznego programu szkoleniowego ds. zgodności i ułatwiają tworzenie udokumentowanych dzienników inspekcji dla użytkowników z działaniami cyklicznego ryzyka.

Utwórz szablony powiadomienia, jeśli chcesz wysłać do użytkowników wiadomość e-mail z powiadomieniem o przypomnieniu o dopasowaniach zasad w ramach procesu rozwiązywania problemów. Powiadomienia można wysyłać tylko na adres e-mail użytkownika skojarzonego z przeglądaną konkretną sprawą. Wybierając szablon powiadomienia do zastosowania do dopasowania zasad, możesz zaakceptować wartości pól zdefiniowane w tym szablonie lub zastąpić pola w razie potrzeby

## <a name="notice-templates-dashboard"></a>Pulpit nawigacyjny szablonów z powiadomieniami

Na **pulpicie nawigacyjnym** Szablony powiadomienia jest wyświetlana lista skonfigurowanych szablonów zawiadomień oraz możliwość tworzenia nowych szablonów z powiadomieniami. Szablony z powiadomieniami są wyświetlane w kolejności odwrotnej do daty z pierwszym szablonem powiadomienia o najnowszej dacie.

![Pulpit nawigacyjny szablonów szablonów informacji o zarządzaniu ryzykiem w niejawnym programie testów.](../media/insider-risk-notices-dashboard.png)

## <a name="html-for-notices"></a>Html na uwagi

Jeśli chcesz utworzyć więcej niż zwykłą wiadomość e-mail opartą na tekście na powiadomieniach, możesz utworzyć bardziej szczegółową wiadomość, używając kodu HTML w polu treści wiadomości szablonu powiadomienia. W poniższym przykładzie przedstawiono format treści wiadomości dla podstawowego szablonu wiadomości e-mail opartego na języku HTML:

```HTML
<!DOCTYPE html>
<html>
<body>
<h2>Action Required: Contoso User Code of Conduct Policy Training</h2>
<p>A recent activity you've performed has generated a risk alert prohibited by the Contoso User <a href='https://www.contoso.com'>Code of Conduct Policy</a>.</p>
<p>You are required to attend the Contoso User Code of Conduct <a href='https://www.contoso.com'>training</a> within the next 14 days. Please contact <a href='mailto:hr@contoso.com'>Human Resources</a> with any questions about this training request.</p>
<p>Thank you,</p>
<p><em>Human Resources</em></p>
</body>
</html>
```

> [!NOTE]
> Implementacja atrybutu href HTML w szablonach informacji o zarządzaniu ryzykiem w niejawnym programie testów obsługuje obecnie tylko pojedynczy cudzysłów zamiast podwójnego cudzysłowu na odwołania do adresów URL.

## <a name="create-a-new-notice-template"></a>Tworzenie nowego szablonu powiadomienia

Aby utworzyć nowy szablon powiadomienia o zarządzaniu ryzykiem w niejawnym programie testów, skorzystaj z narzędzia  do tworzenia informacji w rozwiązaniu do zarządzania ryzykiem w niejawnym programie testów w Centrum zgodności platformy Microsoft 365.

Wykonaj poniższe czynności, aby utworzyć nowy szablon powiadomienia o zarządzaniu ryzykiem w niejawnym programie testów:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do strony Zarządzanie **ryzykiem w niejawnym programie testów** i wybierz **kartę Powiadomienia o szablonach**.
2. Wybierz **pozycję Utwórz szablon powiadomienia** , aby otworzyć narzędzie do tworzenia zawiadomienia.
3. Na stronie **Tworzenie nowego szablonu powiadomienia** wypełnij następujące pola:
    - **Nazwa szablonu**: Wprowadź przyjazną nazwę powiadomienia. Ta nazwa jest wyświetlana na liście powiadomień na pulpicie nawigacyjnym powiadomień i na liście powiadomień podczas wysyłania powiadomień o przypadku.
    - **Wyślij od**: Wprowadź adres e-mail nadawcy powiadomienia. Ten adres zostanie wyświetlony w **polu Od:** we wszystkich powiadomieniach wysyłanych do użytkowników, chyba że zmieni się podczas wysyłania powiadomienia o przypadku.
    - **Pola DW i UDW** : Opcjonalni użytkownicy lub grupy, którzy mają zostać powiadomieni o dopasowanych zasadach, wybranych z usługi Active Directory dla Twojej subskrypcji.
    - **Temat**: Informacje wyświetlane w wierszu tematu wiadomości, obsługują znaki tekstowe.
    - **Treść wiadomości**: Informacje wyświetlane w treści wiadomości, obsługujące tekst lub wartości HTML.
4. Wybierz **pozycję Utwórz** , aby utworzyć i zapisać szablon powiadomienia, lub pozycję **Anuluj** , aby zamknąć bez zapisywania szablonu powiadomienia.

## <a name="update-a-notice-template"></a>Aktualizowanie szablonu powiadomienia

Aby zaktualizować istniejący szablon powiadomienia o zarządzaniu ryzykiem niejawnego programu testów, wykonaj następujące czynności:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do strony Zarządzanie **ryzykiem w niejawnym programie testów** i wybierz **kartę Powiadomienia o szablonach**.
2. Na pulpicie nawigacyjnym z powiadomieniami wybierz szablon powiadomienia, którym chcesz zarządzać.
3. Na stronie szczegółów powiadomienia wybierz pozycję **Edytuj**
4. Na **stronie Edycja** możesz edytować następujące pola:
    - **Nazwa szablonu**: Wprowadź nową przyjazną nazwę powiadomienia. Ta nazwa jest wyświetlana na liście powiadomień na pulpicie nawigacyjnym powiadomień i na liście powiadomień podczas wysyłania powiadomień o przypadku.
    - **Wyślij od**: Zaktualizuj adres e-mail nadawcy powiadomienia. Ten adres zostanie wyświetlony w **polu Od:** we wszystkich powiadomieniach wysyłanych do użytkowników, chyba że zmieni się podczas wysyłania powiadomienia o przypadku.
    - **Pola DW i UDW** : Zaktualizuj opcjonalnych użytkowników lub grupy, aby były o nich powiadamiane o dopasowaniu zasad wybranym z usługi Active Directory dla Twojej subskrypcji.
    - **Temat**. Zaktualizuj informacje wyświetlane w wierszu tematu wiadomości, obsługujące znaki tekstowe.
    - **Treść wiadomości**: Zaktualizuj informacje wyświetlane w treści wiadomości, obsługują wartości tekstowe lub HTML.
5. Wybierz **pozycję Zapisz** , aby zaktualizować i zapisać powiadomienie, lub pozycję **Anuluj** , aby zamknąć bez zapisywania szablonu powiadomienia.

## <a name="delete-a-notice-template"></a>Usuwanie szablonu powiadomienia

Aby usunąć istniejący szablon powiadomienia o zarządzaniu ryzykiem w ramach niejawnego programu testów, wykonaj następujące czynności:

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com) do strony Zarządzanie **ryzykiem w niejawnym programie testów** i wybierz **kartę Powiadomienia o szablonach**.
2. Na pulpicie nawigacyjnym z powiadomieniami wybierz szablon powiadomienia, który chcesz usunąć.
3. Wybierz **ikonę Usuń** na pasku narzędzi.
4. Aby usunąć szablon powiadomienia, w oknie **dialogowym** usuwania wybierz pozycję Tak. Aby anulować usuwanie, wybierz pozycję **Anuluj**.
