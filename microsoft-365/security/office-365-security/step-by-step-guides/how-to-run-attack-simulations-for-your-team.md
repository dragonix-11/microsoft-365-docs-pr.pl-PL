---
title: Jak uruchamiać symulacje ataków dla zespołu
description: Kroki wysyłania ładunku symulacji ataku do użytkowników docelowych dla zespołu lub organizacji na potrzeby szkolenia. Symulowane ataki mogą pomóc w zidentyfikowaniu i znalezieniu narażonych użytkowników, zasad i praktyk, zanim rzeczywisty atak wpłynie na Organizację.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: article
ms.technology: mdo
ms.openlocfilehash: 96b1d512f89cafb782b348a0692fbf5c19902ebf
ms.sourcegitcommit: 7ab324551afac4fd82abc015247371ebfe6ccac2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65842516"
---
# <a name="how-to-run-attack-simulations-for-your-team"></a>Jak uruchamiać symulacje ataków dla zespołu

Trenowanie symulacji ataków umożliwia uruchamianie realistycznych, ale niegroźnych scenariuszy cyberataków w organizacji. Symulowane ataki mogą pomóc w identyfikowaniu i znajdowaniu narażonych użytkowników, zasad i praktyk, zanim rzeczywisty atak wpłynie na organizację, wykorzystując wbudowane lub niestandardowe szkolenia, aby zmniejszyć ryzyko i lepiej edukować użytkowników końcowych na temat zagrożeń.

## <a name="what-youll-need"></a>Co będzie potrzebne

- Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2 (uwzględniony w ramach E5)
- Wystarczające uprawnienia (rola administratora zabezpieczeń)
- 5–10 minut na wykonanie poniższych kroków.

## <a name="send-a-payload-to-target-users"></a>Wysyłanie ładunku do użytkowników docelowych

1. Przejdź do pozycji [Szkolenie symulacji ataków](https://security.microsoft.com/attacksimulator ) w subskrypcji.
1. Wybierz pozycję **Symulacje** na górnym pasku nawigacyjnym.
1. Wybierz **pozycję Uruchom symulację**.
1. Wybierz technikę, która ma być używana z wysuwanego menu, i naciśnij **przycisk Dalej**.
1. Nadaj symulacji nazwę odpowiednią/niezapomnianą i naciśnij **przycisk Dalej**.
1. Wybierz odpowiedni ładunek z kreatora, przejrzyj szczegóły i w razie potrzeby dostosuj je, gdy będziesz zadowolony z wyboru, naciśnij **przycisk Dalej**.
1. Wybierz lokalizację docelową ładunku. Jeśli wybierzesz całą organizację, zaznacz przycisk radiowy i naciśnij **przycisk Dalej**.
1. W przeciwnym razie wybierz pozycję **Dodaj użytkowników** , a następnie wyszukaj lub odfiltruj użytkowników za pomocą kreatora. Wybierz pozycję Dodaj użytkowników, a następnie **pozycję Dalej**.
1. W obszarze **Wybieranie preferencji zawartości szkoleniowej** pozostaw domyślne *środowisko szkoleniowe firmy Microsoft (zalecane)* lub wybierz pozycję *Przekieruj do niestandardowego adresu URL* , jeśli chcesz użyć niestandardowego adresu URL. Jeśli nie chcesz przypisywać żadnego szkolenia, wybierz pozycję *Nie trenowanie*.
    - Możesz zezwolić firmie Microsoft na przypisywanie kursów szkoleniowych, wybierając pozycję *Przypisz szkolenia dla mnie* lub możesz samodzielnie wybrać konkretne moduły z *opcją Wybieranie kursów szkoleniowych i modułów*
    - Wybierz datę ukończenia (30, 15 lub 7 dni) z menu rozwijanego.
    - Kliknij przycisk **Dalej**, aby kontynuować.
1. Dostosuj stronę docelową wyświetlaną, gdy użytkownik zostanie w razie potrzeby phished lub w inny sposób pozostawić wartość domyślną firmy Microsoft.
    1. W obszarze **Wskaźniki ładunku** zaznacz pole wyboru, aby dodać wskaźniki ładunku do wiadomości e-mail. Dodanie ładunków pomoże użytkownikom dowiedzieć się, jak zidentyfikować wiadomość e-mail dotyczącą wyłudzania informacji. Wybierz pozycję *Otwórz panel podglądu* , aby wyświetlić komunikat.
    1. Kliknij przycisk **Dalej**, aby kontynuować.
1. Wybierz, czy chcesz otrzymywać powiadomienia użytkowników końcowych, a jeśli tak, wybierz preferencje dostarczania i w razie potrzeby dostosuj je.
    1. Zwróć uwagę, że możesz również wybrać *język domyślny* dla powiadomienia w menu rozwijanym **Wybierz język domyślny** .
1. Wybierz, kiedy uruchomić symulację i jak długo powinna być prawidłowa. Możesz również włączyć *dostarczanie strefy czasowej obsługującej regiony*. Ta opcja będzie dostarczać pracownikom symulowane komunikaty o atakach w *godzinach pracy* na podstawie ich regionu. Wybierz pozycję **Dalej**.
1. Wyślij test, jeśli wszystko jest gotowe. Przejrzyj podsumowanie wyborów. Kliknij pozycję **Prześlij**.

### <a name="further-reading"></a>Linki zewnętrzne

Aby dowiedzieć się, jak działa symulacja ataków, zobacz [Symulowanie ataku wyłudzania informacji przy użyciu trenowania symulacji ataków — Office 365 | Microsoft Docs](../../office-365-security/attack-simulation-training.md)
