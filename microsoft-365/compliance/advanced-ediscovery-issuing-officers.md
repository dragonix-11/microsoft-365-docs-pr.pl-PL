---
title: Zarządzanie urzędnikami wystawiającym certyfikaty w usłudze eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: W usłudze eDiscovery (Premium) można dodać pracowników wystawiających certyfikaty w całej organizacji, aby w dowolnym przypadku w organizacji można było dodać ich do dowolnej komunikacji w zakresie opieki.
ms.openlocfilehash: 0a3383f9f725a7d5afacd1cab504eefc97b91fd3
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627696"
---
# <a name="manage-issuing-officers-in-ediscovery-premium"></a>Zarządzanie urzędnikami wystawiającym certyfikaty w usłudze eDiscovery (Premium)

Gdy ty lub inne osoby utworzysz powiadomienie o blokadzie lub inny typ komunikacji, który jest wysyłany do użytkownika, który jest opiekunem w przypadku, musisz określić urzędnika wystawiającego. Powiadomienie jest wysyłane do opiekuna w imieniu określonego urzędnika wystawiającego. Na przykład paralegal w organizacji może być odpowiedzialny za tworzenie i wysyłanie powiadomień blokady do opiekunów w przypadku. W tym scenariuszu paralegal może określić adwokata w organizacji jako wystawiającego. Kogo można określić jako urzędnika wystawiającego? Istnieją dwa typy użytkowników, którzy mogą zostać wybrani jako inspektor wystawiający do komunikacji z opiekunem:

- Każdy członek konkretnego przypadku, którego komunikat jest wysyłany w imieniu użytkownika.

- Każdy użytkownik dodany do listy urzędników wystawiających certyfikaty w całej organizacji. Użytkowników z tej listy można dodać do każdego przypadku w organizacji.

W tym artykule wyjaśniono, jak dodawać i usuwać użytkowników z listy urzędników wystawiających certyfikaty w całej organizacji.

## <a name="before-you-add-an-issuing-officer"></a>Przed dodaniem urzędnika wystawiającego

- Aby dodać lub usunąć urzędników wystawiających certyfikaty, musisz być administratorem zbierania elektronicznych materiałów dowodowych w organizacji. Aby uzyskać więcej informacji, zobacz [Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych w portal zgodności Microsoft Purview](assign-ediscovery-permissions.md)  

- Użytkownik dodany jako urzędnik wystawiający certyfikaty musi mieć aktywną skrzynkę pocztową w organizacji platformy Microsoft 365.

- Twoja organizacja może mieć maksymalnie 15 urzędników wystawiających certyfikaty. Członkowie sprawy, których można określić jako urzędnika wystawiającego certyfikaty, nie są wliczane do tego limitu. Ten limit dotyczy tylko liczby użytkowników, których można dodać do strony **Wystawiający oficerowie** w usłudze eDiscovery (Premium).

## <a name="add-an-issuing-officer"></a>Dodawanie urzędnika wystawiającego

1. W portalu zgodności przejdź do obszaru [eDiscovery (Premium),](https://go.microsoft.com/fwlink/p/?linkid=2173764) a następnie kliknij pozycję **Ustawienia zbierania elektronicznych materiałów dowodowych (Premium).**

   ![Wybierz ustawienia zbierania elektronicznych materiałów dowodowych (Premium)](..\media\HistoricalVersions1.png)

2. Na stronie **Ustawienia** wybierz kartę **Wystawiający oficerowie** , aby wyświetlić stronę **Zarządzanie urzędnikami wystawiającym certyfikaty** .

   ![Strona ustawień urzędników wystawiających.](..\media\AeDIssuingOfficers1.png)

3. Kliknij **przycisk Dodaj,** a następnie wyszukaj i dodaj co najmniej jednego użytkownika do listy wystawiających certyfikaty.

Po dodaniu użytkowników jako osoby wystawiające certyfikaty ty lub inni użytkownicy będziecie mogli określić tych użytkowników jako osoby wystawiające certyfikaty na potrzeby komunikacji z opiekunem w dowolnym przypadku w organizacji. Aby uzyskać więcej informacji na temat tworzenia komunikacji z opiekunem, zobacz [Tworzenie powiadomienia o wstrzymaniu ze względów prawnych](create-hold-notification.md).

## <a name="remove-an-issuing-officer"></a>Usuwanie urzędnika wystawiającego

1. W portalu zgodności przejdź do obszaru [eDiscovery (Premium),](https://go.microsoft.com/fwlink/p/?linkid=2173764) a następnie kliknij pozycję **Ustawienia zbierania elektronicznych materiałów dowodowych (Premium).**

2. Na stronie **Ustawienia** wybierz kartę **Wystawiający oficerowie** .

3. Wybierz co najmniej jednego użytkownika na liście urzędników wystawiających, a następnie kliknij przycisk **Usuń**.

Po usunięciu użytkowników z listy urzędników wystawiających certyfikaty nie można już określić tych użytkowników jako osoby wystawiające certyfikaty w nowej komunikacji opiekuna, chyba że użytkownik jest członkiem konkretnego przypadku, z którym jest wydawana komunikacja. Ponadto usunięcie urzędnika wystawiającego nie wpłynie na żadną komunikację, która została wysłana przed usunięciem użytkownika jako urzędnik wystawiający.
