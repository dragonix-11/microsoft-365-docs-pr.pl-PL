---
title: Szablony powiadomień dotyczących zarządzania ryzykiem wewnętrznym
description: Dowiedz się więcej o szablonach powiadomień dotyczących zarządzania ryzykiem wewnętrznym w usłudze Microsoft Purview
keywords: Microsoft 365, Microsoft Purview, ryzyko wewnętrzne, zarządzanie ryzykiem, zgodność
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
ms.openlocfilehash: 7af1152d1393aaaf9eeb242c78b280cf0e9d80e6
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66639803"
---
# <a name="insider-risk-management-notice-templates"></a>Szablony powiadomień dotyczących zarządzania ryzykiem wewnętrznym

Szablony powiadomień dotyczących zarządzania ryzykiem wewnętrznym umożliwiają automatyczne wysyłanie wiadomości e-mail do użytkowników w przypadku utworzenia przypadku dla działań, które wygenerowały dopasowanie zasad i potwierdzony alert. W przypadku większości alertów, które generują przypadki, akcje użytkownika są wynikiem błędów lub nieumyślnych działań bez złej intencji. Powiadomienia służą użytkownikom jako proste przypomnienia, aby zachować większą ostrożność, udostępniać linki do informacji na potrzeby szkolenia odświeżania lub do zasobów zasad firmowych. Powiadomienia mogą być ważną częścią wewnętrznego programu szkoleń dotyczących zgodności i mogą pomóc w utworzeniu udokumentowanego szlaku inspekcji dla użytkowników z cyklicznymi działaniami ryzyka.

Utwórz szablony powiadomień, jeśli chcesz wysłać użytkownikom powiadomienie o przypomnieniu e-mail dotyczące dopasowań zasad w ramach procesu rozwiązywania przypadków. Powiadomienia mogą być wysyłane tylko na adres e-mail użytkownika skojarzony z rozpatrywanym konkretnym przypadkiem. Podczas wybierania szablonu powiadomienia, który ma zostać zastosowany do dopasowania zasad, można zaakceptować wartości pól zdefiniowane w szablonie lub zastąpić pola zgodnie z potrzebami

## <a name="notice-templates-dashboard"></a>Pulpit nawigacyjny szablonów powiadomień

Pulpit **nawigacyjny szablonów powiadomień** wyświetla listę skonfigurowanych szablonów powiadomień i umożliwia tworzenie nowych szablonów powiadomień. Szablony powiadomień są wymienione w kolejności odwrotnej daty z najnowszym szablonem powiadomienia wymienionym jako pierwszy.

![Pulpit nawigacyjny szablonu powiadomienia dotyczącego zarządzania ryzykiem wewnętrznym.](../media/insider-risk-notices-dashboard.png)

## <a name="html-for-notices"></a>KOD HTML dla powiadomień

Jeśli chcesz utworzyć więcej niż prostą tekstową wiadomość e-mail dla powiadomień, możesz utworzyć bardziej szczegółową wiadomość przy użyciu kodu HTML w polu treść wiadomości szablonu powiadomienia. Poniższy przykład zawiera format treści wiadomości dla podstawowego szablonu powiadomień e-mail opartego na języku HTML:

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
> Implementacja atrybutu href HTML w szablonach powiadomień dotyczących zarządzania ryzykiem wewnętrznym obsługuje obecnie tylko pojedyncze cudzysłowy zamiast podwójnego cudzysłowu dla odwołań do adresów URL.

## <a name="create-a-new-notice-template"></a>Tworzenie nowego szablonu powiadomienia

Aby utworzyć nowy szablon powiadomienia dotyczącego zarządzania ryzykiem wewnętrznym, użyjesz narzędzia do tworzenia powiadomień w rozwiązaniu **do zarządzania ryzykiem wewnętrznym** w portal zgodności Microsoft Purview.

Wykonaj następujące kroki, aby utworzyć nowy szablon powiadomienia dotyczącego zarządzania ryzykiem wewnętrznym:

1. W [portal zgodności Microsoft Purview](https://compliance.microsoft.com) przejdź do obszaru **Zarządzanie ryzykiem wewnętrznym** i wybierz kartę **Szablony powiadomień**.
2. Wybierz pozycję **Utwórz szablon powiadomienia** , aby otworzyć narzędzie do tworzenia powiadomień.
3. Na stronie **Tworzenie nowego szablonu powiadomienia** wypełnij następujące pola:
    - **Nazwa szablonu**: wprowadź przyjazną nazwę powiadomienia. Ta nazwa jest wyświetlana na liście powiadomień na pulpicie nawigacyjnym powiadomień i na liście wyboru powiadomień podczas wysyłania powiadomień ze sprawy.
    - **Wyślij od**: wprowadź adres e-mail nadawcy dla powiadomienia. Ten adres będzie wyświetlany w polu **Od:** we wszystkich powiadomieniach wysyłanych do użytkowników, chyba że zostanie on zmieniony podczas wysyłania powiadomienia ze sprawy.
    - **Pola DW i BCC** : opcjonalni użytkownicy lub grupy, którzy mają być powiadamiani o dopasowaniu zasad, wybrani z usługi Active Directory dla subskrypcji.
    - **Temat**: Informacje wyświetlane w wierszu tematu wiadomości obsługują znaki tekstowe.
    - **Treść komunikatu**: informacje wyświetlane w treści wiadomości obsługują wartości tekstowe lub HTML.
4. Wybierz pozycję **Utwórz** , aby utworzyć i zapisać szablon powiadomienia, lub wybierz pozycję **Anuluj** , aby zamknąć bez zapisywania szablonu powiadomienia.

## <a name="update-a-notice-template"></a>Aktualizowanie szablonu powiadomienia

Aby zaktualizować istniejący szablon powiadomienia o zarządzaniu ryzykiem wewnętrznym, wykonaj następujące kroki:

1. W [portal zgodności Microsoft Purview](https://compliance.microsoft.com) przejdź do obszaru **Zarządzanie ryzykiem wewnętrznym** i wybierz kartę **Szablony powiadomień**.
2. Na pulpicie nawigacyjnym powiadomień wybierz szablon powiadomienia, który chcesz zarządzać.
3. Na stronie szczegółów powiadomienia wybierz pozycję **Edytuj**
4. Na stronie **Edytuj** można edytować następujące pola:
    - **Nazwa szablonu**: wprowadź nową przyjazną nazwę powiadomienia. Ta nazwa jest wyświetlana na liście powiadomień na pulpicie nawigacyjnym powiadomień i na liście wyboru powiadomień podczas wysyłania powiadomień ze sprawy.
    - **Wyślij od**: zaktualizuj adres e-mail nadawcy dla powiadomienia. Ten adres będzie wyświetlany w polu **Od:** we wszystkich powiadomieniach wysyłanych do użytkowników, chyba że zostanie on zmieniony podczas wysyłania powiadomienia ze sprawy.
    - Pola **DW i BCC**: zaktualizuj opcjonalnych użytkowników lub grupy, aby były powiadamiane o dopasowaniu zasad wybranych w usłudze Active Directory dla subskrypcji.
    - **Temat**: Zaktualizuj informacje wyświetlane w wierszu tematu wiadomości, obsługuje znaki tekstowe.
    - **Treść komunikatu**: zaktualizuj informacje wyświetlane w treści wiadomości, obsługuje wartości tekstowe lub HTML.
5. Wybierz pozycję **Zapisz** , aby zaktualizować i zapisać powiadomienie, lub wybierz pozycję **Anuluj** , aby zamknąć bez zapisywania szablonu powiadomienia.

## <a name="delete-a-notice-template"></a>Usuwanie szablonu powiadomienia

Aby usunąć istniejący szablon powiadomienia o zarządzaniu ryzykiem wewnętrznym, wykonaj następujące kroki:

1. W [portal zgodności Microsoft Purview](https://compliance.microsoft.com) przejdź do obszaru **Zarządzanie ryzykiem wewnętrznym** i wybierz kartę **Szablony powiadomień**.
2. Na pulpicie nawigacyjnym powiadomień wybierz szablon powiadomienia, który chcesz usunąć.
3. Wybierz ikonę **Usuń** na pasku narzędzi.
4. Aby usunąć szablon powiadomienia, wybierz pozycję **Tak** w oknie dialogowym usuwania. Aby anulować usunięcie, wybierz pozycję **Anuluj**.
