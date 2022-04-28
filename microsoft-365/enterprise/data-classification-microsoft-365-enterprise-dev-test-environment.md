---
title: Klasyfikacja danych dla Microsoft 365 dla środowiska testowego przedsiębiorstwa
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Skorzystaj z tego przewodnika po laboratorium testowym, aby tworzyć etykiety przechowywania dokumentów w Microsoft 365 dla środowiska testowego przedsiębiorstwa i używać ich.
ms.openlocfilehash: f5bcde88be148ed883b4ad10e3b8116ed21c9fa8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096815"
---
# <a name="data-classification-for-your-microsoft-365-for-enterprise-test-environment"></a>Klasyfikacja danych dla Microsoft 365 dla środowiska testowego przedsiębiorstwa

*Ten przewodnik po laboratorium testowym może służyć zarówno do Microsoft 365 dla środowisk testowych dla przedsiębiorstw, jak i Office 365 Enterprise.*

W tym artykule opisano sposób konfigurowania klasyfikacji danych przy użyciu etykiet przechowywania w Microsoft 365 dla środowiska testowego przedsiębiorstwa.

Klasyfikowanie danych w środowisku testowym obejmuje trzy fazy:
- [Faza 1. Tworzenie Microsoft 365 dla środowiska testowego przedsiębiorstwa](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Faza 2. Tworzenie etykiet przechowywania](#phase-2-create-retention-labels)
- [Faza 3. Stosowanie etykiet przechowywania do dokumentów](#phase-3-apply-retention-labels-to-documents)

![Przewodniki laboratorium testowego dla chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Aby uzyskać wizualną mapę na wszystkie artykuły w stosie przewodnika Microsoft 365 dla laboratorium testowego dla przedsiębiorstw, przejdź do [Microsoft 365 stosu przewodników laboratorium testowego dla przedsiębiorstw](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Faza 1. Tworzenie Microsoft 365 dla środowiska testowego przedsiębiorstwa

Jeśli chcesz skonfigurować etykiety przechowywania w sposób uproszczony z minimalnymi wymaganiami, postępuj zgodnie z instrukcjami w temacie [Uproszczona konfiguracja podstawowa](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Jeśli chcesz skonfigurować etykiety przechowywania w symulowanym przedsiębiorstwie, postępuj zgodnie z instrukcjami w temacie [Uwierzytelnianie przekazywane](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Testowanie etykiet przechowywania nie wymaga symulowanego środowiska testowego przedsiębiorstwa, które obejmuje symulowany intranet połączony z Internetem i synchronizację katalogów dla lasu Active Directory Domain Services (AD DS). Jest ona dostępna tutaj jako opcja, dzięki czemu można przetestować automatyczne licencjonowanie i członkostwo w grupie i eksperymentować z nim w środowisku reprezentującym typową organizację.

## <a name="phase-2-create-retention-labels"></a>Faza 2. Tworzenie etykiet przechowywania

W tej fazie utwórz etykiety przechowywania dla różnych poziomów przechowywania dla folderów dokumentów usługi SharePoint Online:

1. Zaloguj się do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a> przy użyciu konta administratora globalnego.
1. Na karcie **Narzędzia główne — Microsoft 365 zabezpieczeń** przeglądarki wybierz pozycję **Klasyfikacja** >  **Etykiety ponownej konfiguracji**.
1. Wybierz **pozycję Utwórz etykietę**.
1. W okienku **Name your label (Nazwa etykiety** ) wprowadź **ciąg Internal Public (Wewnętrzna publiczna** ) w polu **Name your label (Nazwa etykiety**), a następnie wybierz przycisk **Dalej**.
1. W okienku **Deskryptory planu plików** wybierz pozycję **Dalej**.
1. W okienku **Ustawienia etykiety** w razie potrzeby ustaw pozycję **Przechowywanie** **na Włączone**, a następnie wybierz pozycję **Dalej**.
1. W okienku **Przeglądanie ustawień** wybierz pozycję **Utwórz etykietę**.
1. Powtórz kroki 3–7 dla dodatkowych etykiet o następujących nazwach:
  - Prywatny
  - Wrażliwe
  - Wysoce poufne
1. W okienku **Etykiety przechowywania** wybierz pozycję **Publikuj etykiety**.
1. W okienku **Wybierz etykiety do opublikowania** wybierz pozycję **Wybierz etykiety do opublikowania**.
1. W okienku **Wybierz etykiety** wybierz pozycję **Dodaj** i wybierz wszystkie cztery etykiety.
1. Wybierz pozycję **Dodaj**, a następnie wybierz pozycję **Gotowe**.
1. W okienku **Wybierz etykiety do opublikowania** wybierz pozycję **Dalej**.
1. W okienku **Wybieranie lokalizacji** wybierz pozycję **Dalej**.
1. W okienku **Nazwa zasad** wprowadź **przykładową organizację** w polu **Nazwa**, a następnie wybierz pozycję **Dalej**.
1. W okienku **Przeglądanie ustawień** wybierz pozycję **Publikuj etykiety**.
 
Opublikowanie etykiet przechowywania może potrwać kilka minut.

## <a name="phase-3-apply-retention-labels-to-documents"></a>Faza 3. Stosowanie etykiet przechowywania do dokumentów

W tej fazie odnajdziesz domyślne zachowanie etykiety przechowywania plików w folderze Dokumenty witryny usługi SharePoint Online i ręcznie zmienisz etykietę przechowywania dokumentu.

Najpierw utwórz witrynę zespołu usługi SharePoint Online na poziomie poufnym:
  
1. Korzystając z prywatnego wystąpienia przeglądarki, zaloguj się do <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a> przy użyciu konta administratora globalnego.
1. Na liście kafelków wybierz pozycję **SharePoint**.
1. Na nowej **karcie SharePoint** w przeglądarce wybierz pozycję **Utwórz witrynę**.
1. Na stronie **Tworzenie witryny** wybierz pozycję **Witryna zespołu**.
1. W polu **Nazwa witryny zespołu** wprowadź **sensitiveFiles**.
1. W polu **Opis witryny zespołu** wprowadź **SharePoint witrynę dla poufnych plików**.
1. W **obszarze Ustawienia prywatności** wybierz pozycję **Prywatne — tylko członkowie mogą uzyskać dostęp do tej witryny**, a następnie wybierz pozycję **Dalej**.
1. W **okienku KtoTo czy chcesz dodać?** wybierz pozycję **Zakończ**.
    
Następnie skonfiguruj folder Documents witryny zespołu SensitiveFiles dla etykiety Przechowywania poufne.
  
1. Na karcie **SensitiveFiles** w przeglądarce wybierz pozycję **Dokumenty**.
1. Wybierz ikonę **Ustawienia**, a następnie wybierz pozycję **Ustawienia biblioteki**.
1. W obszarze **Uprawnienia i zarządzanie** wybierz pozycję **Zastosuj etykietę do elementów z tej listy lub biblioteki**. Jeśli ta opcja nie zostanie wyświetlona, etykiety przechowywania nie zostaną jeszcze opublikowane. Spróbuj wykonać ten krok później.
1. W **obszarze Ustawienia-Zastosuj etykietę** wybierz pozycję **Poufne** w polu listy rozwijanej, a następnie wybierz pozycję **Zapisz**.

Następnie utwórz nowy dokument w witrynie SensitiveFiles i zmień jego etykietę przechowywania.
    
1. W folderze documents wybierz pozycję **NewWord document (NowyWord).** > 
1. Wprowadź tekst w pustym dokumencie. Poczekaj na zapisanie tekstu.
1. Na pasku menu wybierz pozycję **Dokumenty udostępnione**.
1. Obok **nazwy plikuDocument.docx** wybierz pionowy wielokropek, a następnie wybierz pozycję **Szczegóły**.
1. W okienku po prawej stronie w sekcji **Właściwości** w obszarze **Zastosuj etykietę przechowywania** zwróć uwagę, że dokument automatycznie zastosował etykietę Przechowywania **poufnego** .
1. Kliknij **pozycję Edytuj wszystko**.
1. W okienku **Document.docx** w obszarze **Zastosuj etykietę przechowywania** wybierz etykietę **Wysoce poufne** , a następnie wybierz pozycję **Zapisz**.

## <a name="next-step"></a>Następny krok

Zapoznaj się z dodatkowymi funkcjami i możliwościami [ochrony informacji](m365-enterprise-test-lab-guides.md#information-protection) w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Microsoft 365 dla przewodników laboratorium testowego w przedsiębiorstwie](m365-enterprise-test-lab-guides.md)

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Dokumentacja dotycząca subskrypcji Microsoft 365 dla Przedsiębiorstw](/microsoft-365-enterprise/)
