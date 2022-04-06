---
title: Zarządzanie szablonami komunikacji w bibliotece komunikacji w programie Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: W programie Advanced eDiscovery można dodać szablony komunikacji po stronie iniekcyjną (na przykład szablon powiadomienia o zawieszonej komunikacji), aby można było ich używać w każdym przypadku w organizacji.
ms.openlocfilehash: 1b5be4a4a923050b43943e81ac64265e16749899
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704860"
---
# <a name="manage-custodian-communications-templates-in-advanced-ediscovery"></a>Zarządzanie szablonami komunikacji w aplikacji Advanced eDiscovery

Podczas tworzenia przez Ciebie lub innych użytkowników powiadomień o wstrzymaniu lub innych rodzajów informacji, które chcesz przechowywać, musisz utworzyć dokument komunikacji od podstaw za pomocą edytora komunikacji  na karcie Komunikacja w Advanced eDiscovery przypadku. Teraz wydaliśmy nową funkcję, która umożliwia tworzenie szablonów komunikacji, za pomocą których można tworzyć korespondencję w dowolnym przypadku w organizacji. Po utworzeniu szablonów do komunikacji są one dostępne do użycia w przypadku. Oznacza to, że paralegaci lub inni użytkownicy tworzący komunikację z osobami, które się w tym zakresie komunikują, nie muszą zaczynać od podstaw, aby utworzyć powiadomienie. Zamiast tego mogą wybrać szablon, aby utworzyć powiadomienie wysyłane do opiekuna.

W tym artykule wyjaśniono, jak tworzyć szablony komunikacji dla całej organizacji i wybierać je podczas tworzenia nowego powiadomienia o niechcieniania dla określonej Advanced eDiscovery przypadku.

## <a name="before-you-create-templates-in-the-communications-library"></a>Przed utworzeniem szablonów w bibliotece komunikacji

- Aby dodawać lub usuwać szablony w bibliotece komunikacji w programie Advanced eDiscovery, musisz być administratorem zbierania elektronicznych materiałów dowodowych w Advanced eDiscovery. Aby uzyskać więcej informacji, [zobacz Przypisywanie uprawnień zbierania](assign-ediscovery-permissions.md) elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365  

- Twoja organizacja może mieć maksymalnie 50 szablonów w bibliotece Komunikacji.

## <a name="create-a-communications-template"></a>Tworzenie szablonu komunikacji

1. W Centrum zgodności platformy Microsoft 365 przejdź do strony [Advanced eDiscovery](https://go.microsoft.com/fwlink/p/?linkid=2173764), a następnie kliknij pozycję **Advanced eDiscovery ustawienia**.

   ![Wybierz Advanced eDiscovery ustawienia](..\media\HistoricalVersions1.png)

2. Na stronie **Ustawienia** wybierz **kartę Biblioteka komunikacji**.

3. Na stronie **Biblioteka komunikacji** kliknij pozycję **Utwórz**.

4. Postępuj zgodnie z procedurą tworzenia komunikacji przechoczej. Aby uzyskać instrukcje krok po kroku, zobacz [Tworzenie powiadomienia o wstrzymaniu ze wskazówkami prawnie](create-hold-notification.md).

   > [!NOTE]
   > Procedura tworzenia szablonu komunikacji jest taka sama jak procedura tworzenia powiadomienia w ramach sprawy. Jedyna różnica polega na tym, że podczas tworzenia szablonu nie określa się inspektora rozsyłającego i nie przypisuje się osób- opiekunów. W przypadku tworzenia za pomocą szablonu komunikacji powiadomienia o przechowyceniu dla sprawy robi się określenie inspektora insektjącego i przypisanie do nich osób-

5. Po utworzeniu szablonu jest on wyświetlany na stronie **Biblioteka komunikacji** .

   ![Szablony wyświetlane w bibliotece komunikacji](..\media\AeDCommunicationsLibrary1.png)

Ty i inni administratorzy zbierania elektronicznych materiałów dowodowych możecie edytować szablon komunikacji. Żadne zmiany wprowadzone w szablonie nie mają wpływu na żadne powiadomienia utworzone wcześniej przy użyciu tego szablonu ani nie modyfikują ich. Te zmiany zostaną wprowadzone tylko w przypadku nowych powiadomień utworzonych przy użyciu zaktualizowanego szablonu.

## <a name="use-a-communications-template-to-create-a-custodian-notification"></a>Tworzenie powiadomienia o treści dokumentu przy użyciu szablonu komunikacji

Po utworzeniu jednego lub większej liczby szablonów komunikacji w bibliotece komunikacji można wybrać takie szablony w celu utworzenia powiadomienia o przechowyceniu w przypadku.

Aby wybrać szablon:

1. W Centrum zgodności platformy Microsoft 365 przejdź do tematu **Zbierania elektronicznych** materiałów dowodowych > Zaawansowane, aby wyświetlić listę spraw w organizacji.

2. Wybierz sprawę, kliknij **kartę Komunikacja** , a następnie kliknij pozycję **Nowa komunikacja**.

3. Na stronie **Nazywanie komunikacji** użyj listy rozwijanej **Wybierz** szablon komunikacji, aby wybrać szablon komunikacji do utworzenia powiadomienia o treści dokumentu.

   Lista szablonów w bibliotece komunikacji organizacji jest wyświetlana na liście rozwijanej.

   ![Szablony z biblioteki komunikacji wyświetlane na liście rozwijanej.](..\media\AeDCommunicationsTemplates1.png)
