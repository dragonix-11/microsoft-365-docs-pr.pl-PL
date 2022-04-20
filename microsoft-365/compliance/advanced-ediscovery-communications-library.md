---
title: Zarządzanie szablonami komunikacji opiekuna w bibliotece communications w usłudze eDiscovery (Premium)
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
description: Szablony komunikacji opiekuna (takie jak szablon powiadomienia o blokadzie) można dodawać w obszarze zbierania elektronicznych materiałów dowodowych (Premium), aby można było ich używać w dowolnym przypadku w organizacji.
ms.openlocfilehash: be8311a9687eb4edb9cc44e15264808a2a05a69a
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945158"
---
# <a name="manage-custodian-communications-templates-in-ediscovery-premium"></a>Zarządzanie szablonami komunikacji opiekuna w usłudze eDiscovery (Premium)

Gdy ty lub inni użytkownicy tworzycie powiadomienie o blokadzie lub inne rodzaje komunikacji z opiekunami, trzeba było utworzyć dokument komunikacji od podstaw przy użyciu edytora komunikacji na karcie **Komunikacja** w przypadku zbierania elektronicznych materiałów dowodowych (Premium). Teraz opublikowaliśmy nową funkcję, która umożliwia tworzenie szablonów komunikacji, których można użyć do tworzenia komunikacji w dowolnym przypadku w organizacji. Po utworzeniu szablonów komunikacji są one dostępne do użycia w przypadku. Oznacza to, że paralegals lub innych użytkowników, którzy tworzą komunikację opiekuna nie muszą zaczynać od podstaw, aby utworzyć powiadomienie. Zamiast tego mogą wybrać szablon, aby utworzyć powiadomienie wysyłane do opiekuna.

W tym artykule wyjaśniono, jak tworzyć szablony komunikacji dla całej organizacji i wybierać je podczas tworzenia nowego powiadomienia opiekuna dla konkretnego przypadku zbierania elektronicznych materiałów dowodowych (Premium).

## <a name="before-you-create-templates-in-the-communications-library"></a>Przed utworzeniem szablonów w bibliotece communications

- Musisz być administratorem zbierania elektronicznych materiałów dowodowych w organizacji, aby dodawać lub usuwać szablony w bibliotece usługi Communications w usłudze eDiscovery (Premium). Aby uzyskać więcej informacji, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych w portalu zgodności usługi Microsoft Purview](assign-ediscovery-permissions.md)  

- Twoja organizacja może mieć maksymalnie 50 szablonów w bibliotece usługi Communications.

## <a name="create-a-communications-template"></a>Tworzenie szablonu komunikacji

1. W portalu zgodności przejdź do obszaru [eDiscovery (Premium),](https://go.microsoft.com/fwlink/p/?linkid=2173764) a następnie kliknij pozycję **Ustawienia zbierania elektronicznych materiałów dowodowych (Premium**).

   ![Wybierz ustawienia zbierania elektronicznych materiałów dowodowych (Premium)](..\media\HistoricalVersions1.png)

2. Na stronie **Ustawienia** wybierz kartę **Biblioteka komunikacji**.

3. Na stronie **Biblioteka komunikacji** kliknij pozycję **Utwórz**.

4. Postępuj zgodnie z procedurą, aby utworzyć komunikat opiekuna. Aby uzyskać instrukcje krok po kroku, zobacz [Tworzenie powiadomienia o blokadzie prawnej](create-hold-notification.md).

   > [!NOTE]
   > Kroki tworzenia szablonu komunikacji są takie same jak w przypadku tworzenia powiadomienia w ramach przepływu pracy. Jedyną różnicą jest to, że podczas tworzenia szablonu nie określasz urzędnika wystawiającego i nie przypisujesz opiekunów. Określanie urzędnika wystawiającego i przypisywanie opiekunów odbywa się w przypadku użycia szablonu komunikacji w celu utworzenia powiadomienia opiekuna dla sprawy.

5. Po utworzeniu szablonu zostanie on **wyświetlony na stronie Biblioteka komunikacji** .

   ![Szablony wyświetlane w bibliotece komunikacji](..\media\AeDCommunicationsLibrary1.png)

Ty lub inni administratorzy zbierania elektronicznych materiałów dowodowych mogą edytować szablon komunikacji. Wszelkie zmiany wprowadzone w szablonie nie wpływają ani nie modyfikują żadnych powiadomień utworzonych wcześniej przy użyciu tego szablonu. Te zmiany będą dotyczyć tylko nowych powiadomień utworzonych przy użyciu zaktualizowanego szablonu.

## <a name="use-a-communications-template-to-create-a-custodian-notification"></a>Tworzenie powiadomienia opiekuna za pomocą szablonu komunikacji

Po utworzeniu co najmniej jednego szablonu komunikacji w bibliotece communications można wybrać te szablony, aby utworzyć powiadomienie opiekuna w takim przypadku.

Aby wybrać szablon:

1. W portalu zgodności przejdź do obszaru **eDiscovery > Advanced** , aby wyświetlić listę przypadków w organizacji.

2. Wybierz przypadek, kliknij kartę **Komunikacja** , a następnie kliknij pozycję **Nowa komunikacja**.

3. Na stronie **Komunikacja nazw** użyj listy rozwijanej **Wybierz szablon komunikacji** , aby wybrać szablon komunikacji do użycia w celu utworzenia powiadomienia opiekuna.

   Lista szablonów w bibliotece komunikacji organizacji jest wyświetlana na liście rozwijanej.

   ![Szablony z biblioteki communications wyświetlane na liście rozwijanej.](..\media\AeDCommunicationsTemplates1.png)
