---
title: Klasyfikacja danych Microsoft 365 w środowisku testowania przedsiębiorstwa
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-security-compliance
ms.custom:
- Ent_TLGs
- admindeeplinkMAC
- admindeeplinkDEFENDER
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Skorzystaj z tego przewodnika laboratorium testowego, aby tworzyć etykiety przechowywania i używać ich w dokumentach Microsoft 365 w środowisku testowania przedsiębiorstwa.
ms.openlocfilehash: 3cb3a07b4f636fcf8770432a825356269ff6d94c
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006175"
---
# <a name="data-classification-for-your-microsoft-365-for-enterprise-test-environment"></a>Klasyfikacja danych Microsoft 365 w środowisku testowania przedsiębiorstwa

*Ten przewodnik laboratorium testowego może być używany zarówno w przypadku Microsoft 365 przedsiębiorstwa, Office 365 Enterprise testowych.*

W tym artykule opisano, jak skonfigurować klasyfikację danych przy użyciu etykiet przechowywania Microsoft 365 w środowisku testowania przedsiębiorstwa.

Klasyfikowanie danych w środowisku testowym obejmuje trzy fazy:
- [Etap 1. Tworzenie środowiska testowego Microsoft 365 przedsiębiorstwa](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Etap 2. Tworzenie etykiet przechowywania](#phase-2-create-retention-labels)
- [Etap 3. Stosowanie etykiet przechowywania do dokumentów](#phase-3-apply-retention-labels-to-documents)

![Przewodniki laboratorium testowego dotyczące chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Aby uzyskać wizualną mapę do wszystkich artykułów w stosie przewodników laboratorium testowego Microsoft 365 dla przedsiębiorstw, przejdź do tematu Microsoft 365 — przewodnik laboratorium testowego w [przedsiębiorstwie](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Etap 1. Tworzenie środowiska testowego Microsoft 365 przedsiębiorstwa

Jeśli chcesz tylko skonfigurować etykiety przechowywania w sposób minimalny, postępuj zgodnie z instrukcjami w tece Konfiguracja bazy [podstawowej](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Jeśli chcesz skonfigurować etykiety przechowywania w symulowanym przedsiębiorstwie, postępuj zgodnie z instrukcjami w tece uwierzytelnianie [pass-through](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Testowanie etykiet przechowywania nie wymaga symulowanego środowiska testowania przedsiębiorstwa, które obejmuje symulowany intranet połączony z Internetem i synchronizację katalogów dla lasu Usługi domenowe w usłudze Active Directory (AD DS). Ta opcja jest dostępna jako opcja, która umożliwia testowanie automatycznego licencjonowania i członkostwa w grupach oraz eksperymentowanie z nim w środowisku reprezentującym typową organizację.

## <a name="phase-2-create-retention-labels"></a>Etap 2. Tworzenie etykiet przechowywania

W tej fazie utwórz etykiety przechowywania dla różnych poziomów przechowywania dla SharePoint Dokumenty online:

1. Zaloguj się do portalu <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-mail</a> przy użyciu konta administratora globalnego.
1. Na karcie **Narzędzia główne — Microsoft 365** zabezpieczeń przeglądarki wybierz pozycję **Etykiety** **ClassificationRetention** > .
1. Wybierz **pozycję Utwórz etykietę**.
1. W **okienku Nadaj nazwę etykiecie** wprowadź **wartość Publiczna wewnętrzna** w pole **Nazwij etykietę**, a następnie wybierz przycisk **Dalej**.
1. W **okienku Deskryptory planu** plików wybierz pozycję **Dalej**.
1. W **okienku Ustawienia** etykiet w razie potrzeby ustaw dla opcji **Przechowywanie wartość** **Wł**., a następnie wybierz przycisk **Dalej**.
1. W **okienku Przeglądanie ustawień** wybierz pozycję **Utwórz etykietę**.
1. Powtórz kroki od 3 do 7 w przypadku dodatkowych etykiet o tych nazwach:
  - Prywatna
  - Pochylić
  - Wysoce poufne
1. W **okienku Etykiety** przechowywania wybierz pozycję **Publikuj etykiety**.
1. W **okienku Wybierz etykiety do opublikowania** wybierz pozycję **Wybierz etykiety do opublikowania**.
1. W **okienku Wybieranie etykiet** wybierz pozycję **Dodaj** i zaznacz wszystkie cztery etykiety.
1. Wybierz **pozycję Dodaj**, a następnie wybierz pozycję **Gotowe**.
1. W **okienku Wybierz etykiety do opublikowania** wybierz pozycję **Dalej**.
1. W **okienku Wybierz lokalizacje** wybierz pozycję **Dalej**.
1. W **okienku Nadaj nazwę zasad** wprowadź **przykładową organizację** w **nazwach**, a następnie wybierz przycisk **Dalej**.
1. W **okienku Przeglądanie ustawień** wybierz pozycję **Publikuj etykiety**.
 
Opublikowanie etykiet przechowywania może potrwać kilka minut.

## <a name="phase-3-apply-retention-labels-to-documents"></a>Etap 3. Stosowanie etykiet przechowywania do dokumentów

W tej fazie poznasz domyślne zachowanie etykiet przechowywania dla plików w folderze Dokumenty w witrynie usługi SharePoint Online i ręcznie zmienisz etykietę przechowywania dokumentu.

Najpierw utwórz witrynę zespołu na poziomie poufnym SharePoint online:
  
1. Używając prywatnego wystąpienia przeglądarki, zaloguj się do centrum administracyjnego <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365</a> przy użyciu konta administratora globalnego.
1. Na liście kafelków **wybierz pozycję SharePoint**.
1. Na nowej karcie **SharePoint** w przeglądarce wybierz pozycję **Utwórz witrynę**.
1. Na **stronie Tworzenie witryny** wybierz pozycję **Witryna zespołu**.
1. W **polu Nazwa witryny zespołu** wprowadź **tekst SensitiveFiles**.
1. W **polu Opis witryny zespołu** wprowadź SharePoint **w przypadku poufnych plików**.
1. W **ustawieniach prywatności** wybierz **pozycję Prywatne — tylko członkowie mogą uzyskać dostęp do tej** witryny, a następnie wybierz pozycję **Dalej**.
1. W **okienku KtoTo chcesz dodać?** wybierz pozycję **Zakończ**.
    
Następnie skonfiguruj folder Dokumenty w witrynie zespołu SensitiveFiles pod etykietą przechowywania Poufne.
  
1. Na karcie **SensitiveFiles** w przeglądarce wybierz pozycję **Dokumenty**.
1. Wybierz **ikonę Ustawienia**, a następnie wybierz pozycję **Ustawienia biblioteki**.
1. W **obszarze Uprawnienia i zarządzanie** wybierz **pozycję Zastosuj etykietę do elementów na tej liście lub w tej bibliotece**. Jeśli ta opcja nie jest wyświetlana, etykiety przechowywania nie są jeszcze opublikowane. Spróbuj wykonać ten krok później.
1. W **Ustawienia Zastosuj etykietę** **wybierz z listy** rozwijanej pozycję Poufne, a następnie wybierz pozycję **Zapisz**.

Następnie utwórz nowy dokument w witrynie SensitiveFiles i zmień jego etykietę przechowywania.
    
1. W folderze dokumentów wybierz pozycję **Dokument NewWord** > .
1. Wprowadź tekst w pustym dokumencie. Poczekaj na zapisanie tekstu.
1. Na pasku menu wybierz pozycję **Dokumenty udostępnione**.
1. Obok nazwy **Document.docx** pliku wybierz pionowy wielokropek, a następnie wybierz pozycję **Szczegóły**.
1. W prawym okienku w sekcji **Właściwości** w obszarze Stosowanie etykiety **przechowywania** zwróć uwagę, że w dokumencie została automatycznie zastosowana etykieta przechowywania Poufne.
1. Kliknij **pozycję Edytuj wszystko**.
1. W **okienkuDocument.docx** w obszarze **Stosowanie etykiety przechowywania** wybierz etykietę Wysoce **poufne** , a następnie wybierz pozycję **Zapisz**.

## <a name="next-step"></a>Następny krok

Poznaj dodatkowe [funkcje i możliwości](m365-enterprise-test-lab-guides.md#information-protection) ochrony informacji w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Microsoft 365 laboratorium testowego dla przedsiębiorstw](m365-enterprise-test-lab-guides.md)

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Microsoft 365 dla przedsiębiorstw](/microsoft-365-enterprise/)
