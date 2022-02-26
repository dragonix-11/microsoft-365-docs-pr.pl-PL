---
title: Potwierdzanie powiadomienia o wstrzymaniu
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
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się, jak za Advanced eDiscovery wysyłać powiadomienia o zobowiązaniach prawnych i postępować w ich związku pocztą e-mail, a także monitorować stan zobowiązań.
ms.openlocfilehash: 57cda6e88968fc90845965a8554f55d80bd3ded0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973789"
---
# <a name="acknowledge-a-hold-notification"></a>Potwierdzanie powiadomienia o wstrzymaniu

W odpowiedzi na żądanie lub badanie prawne może być wymagane poinformowanie osób składowych o zobowiązaniach do zachowania informacji przechowywanych elektronicznie (ESI) oraz o wszelkich materiałach, które mogą być istotne dla aktywnego lub bliskich kwestii prawnych. Po wysłaniu zespoły prawne muszą wiedzieć, że każdy odbierany, odczytywany, zrozumiały i wyrażany zgodę na postępuj zgodnie z podanymi instrukcjami.

Aby skrócić czas, koszt i nakład pracy w związku z rzeczami przechowywania, funkcja Advanced eDiscovery umożliwia wysyłanie pocztą e-mail powiadomień o wstrzymaniu się z prawem i obserwowanie tych powiadomień. Oprócz powiadomień e-mail każdy opiekun będzie miał dostęp do indywidualnego Portalu zgodności, dzięki czemu osoby przechowane będą informowane o zmianach stanu ich zobowiązania.

## <a name="email-notifications"></a>Powiadomienia e-mail

Po otrzymaniu powiadomienia o wstrzymaniu obsługi prawnej każdy opiekun otrzyma unikatową i spersonalizowaną wiadomość e-mail zawierającą powiadomienie o wstrzymaniu jej użytkowania i dodane instrukcje. 

> [!TIP]
> Zobacz, jak można używać wbudowanego Edytora [](using-communications-editor.md) komunikacji, aby umożliwić twoim opiekunom potwierdzenie ich powiadomienia lub uzyskanie dostępu do Portalu zgodności bezpośrednio z ich wiadomości e-mail.

Na podstawie konfiguracji powiadomienia o wstrzymaniu ze względu na to, że osoby przechwytują dane osobowe, mogą otrzymać następujące powiadomienia: 

- **Powiadomienie o wydaniu:** Pierwsze powiadomienie wysłane do użytkownika, który się odzywuje. To powiadomienie będzie zawierać instrukcje dotyczące wydawania informacji oraz powiadomienie o wstrzymaniu, dołączone na końcu wiadomości.

- **Przypomnienie:** Jeśli funkcja jest włączona, do osób, które włączyły funkcję, zostanie wysłane powiadomienie z przypomnieniem na podstawie określonej częstotliwości i interwału. Przypomnienia będą nadal wysyłane do momentu potwierdzenia przez opiekuna powiadomienia lub do czasu wyczerpania liczby przypomnień.

- **Powiadomienie o eskalacji:** Jeśli ta funkcja jest włączona, po wyczerpaniu przypomnień do użytkownika i jego kierownika zostanie wysłane powiadomienie o eskalacji. System będzie automatycznie wysyłał powiadomienia o eskalacji do momentu ukończenia określonej liczby eskalacji lub do czasu potwierdzenia przez użytkownika powiadomień o wstrzymaniu.

- **Powiadomienie o ponownej rezygnacji:** W trakcie badania, jeśli zawartość powiadomienia o wstrzymaniu zostanie zaktualizowana, powiadomienie zostanie automatycznie wysłane do osoby dojechaczej.

- **Informacje o wersji:** Po wydaniu przez opiekuna informacji z tej sprawy zostanie do nich wysłane powiadomienie o wersji. 

## <a name="compliance-portal"></a>Portal zgodności

Oprócz powiadomień e-mail każdy opiekun będzie miał dostęp do unikatowego Portalu zgodności. Za pośrednictwem portalu każdy wołomiański może wyświetlać i potwierdzać aktywne powiadomienia o swoich wstrzymywaniach, a także dostęp do nich.

![Portal zgodności dla opiekuna.](../media/CustodianPortal.jpg)
