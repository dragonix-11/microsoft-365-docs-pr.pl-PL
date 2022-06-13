---
title: Jak skonfigurować zautomatyzowane ataki i szkolenia w ramach szkolenia z symulacji ataków
description: Kroki automatyzowania trenowania symulacji ataków i wysyłania ładunku do użytkowników docelowych. Korzystając z tego przewodnika, dowiesz się, jak tworzyć zautomatyzowane przepływy ataków z określonymi technikami i ładunkami.
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
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: ccf4222878777789fb7f89b6382c858eaad9f0c2
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2022
ms.locfileid: "66042144"
---
# <a name="how-to-setup-automated-attacks-and-training-within-attack-simulation-training"></a>Jak skonfigurować zautomatyzowane ataki i szkolenia w ramach szkolenia z symulacji ataków

Trenowanie symulacji ataków umożliwia uruchamianie niegroźnych symulacji ataków w organizacji w celu oceny ryzyka wyłudzania informacji i naucz użytkownikom, jak lepiej uniknąć ataków phish. Postępując zgodnie z tym przewodnikiem, skonfigurujesz zautomatyzowane przepływy z określonymi technikami i ładunkami uruchamianymi po spełnieniu określonych warunków, uruchamiając symulacje przeciwko twojej organizacji.

## <a name="what-youll-need"></a>Co będzie potrzebne

- Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2 (uwzględniony w ramach E5).
- Wystarczające uprawnienia (rola administratora zabezpieczeń).
- 5–10 minut na wykonanie poniższych kroków.

## <a name="send-a-payload-to-target-users"></a>Wysyłanie ładunku do użytkowników docelowych

1. Przejdź do [uczenia symulacji ataków](https://security.microsoft.com/attacksimulator).
1. Wybierz pozycję **Automatyzacje symulacji** na górnym pasku nawigacyjnym.
1. Naciśnij **pozycję Utwórz automatyzację**.
1. Nadaj automatyzacji symulacji nazwę odpowiednią i niezapomnianą. *Dalej*.
1. Wybierz techniki, których chcesz użyć z wysuwanego menu. *Dalej*.
1. Ręcznie wybierz maksymalnie 20 ładunków, których chcesz użyć na potrzeby tej automatyzacji, lub wybierz pozycję Randomize. *Dalej*.
1. Jeśli wybrano usługę OAuth jako ładunek, musisz wprowadzić nazwę, logo i zakres (uprawnienia), które chcesz, aby aplikacja była używana w symulacji. *Dalej*.
1. Wybierz lokalizację docelową ładunku, jeśli wybierzesz przycisk radiowy w całej organizacji. *Dalej*.
1. W przeciwnym razie wybierz pozycję **Dodaj użytkowników** , a następnie wyszukaj lub przefiltruj użytkowników za pomocą kreatora, naciśnij pozycję Dodaj użytkowników. *Dalej*.
1. W razie potrzeby dostosuj szkolenie, w przeciwnym razie pozostaw zaznaczone opcje Przypisz szkolenie dla mnie (zalecane). *Dalej*.
1. Dostosuj stronę docelową wyświetlaną, gdy użytkownik zostanie phished w razie potrzeby, w przeciwnym razie pozostaw jako domyślny microsoft. *Dalej*.
1. Wybierz, czy chcesz otrzymywać powiadomienia użytkowników końcowych, jeśli tak, wybierz preferencje dostarczania i w razie potrzeby dostosuj je. *Dalej*.
1. W przypadku harmonogramu symulacji możesz wybrać opcję **Randomized (Randomized** ) lub **Fixed (Naprawiono**), zalecaną opcją jest Randomized (Losowano), po wybraniu pozycji Dalej wybierz pozycję *Dalej*.
1. W zależności od wybranej opcji Randomized lub Fixed szczegóły harmonogramu mogą się różnić, ale wybierz preferencje wyboru, w tym daty rozpoczęcia i zakończenia automatyzacji. *Dalej*.
1. W obszarze **Szczegóły uruchamiania** wybierz wszystkie wybrane opcje końcowe, takie jak użycie unikatowych ładunków lub kierowanie ataków na recydywistów, a następnie wybierz pozycję *Dalej*.
1. **Prześlij** i zostanie skonfigurowana automatyzacja symulacji.

## <a name="learn-more"></a>Dodatkowe informacje

Pełne wskazówki można znaleźć na stronie [Automatyzacje symulacji na potrzeby trenowania symulacji ataków — Office 365 | Microsoft Docs](../../office-365-security/attack-simulation-training-simulation-automations.md).
