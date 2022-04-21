---
title: Zawartość przechowywana w Exchange Online skrzynkach pocztowych
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: ''
description: Zawartość generowana przez aplikacje oparte na chmurze w Microsoft 365 jest przechowywana lub skojarzona ze skrzynką pocztową Exchange Online użytkownika. Tę zawartość można przeszukiwać przy użyciu narzędzi microsoft eDiscovery.
ms.openlocfilehash: b5e8434f5345cda8ef4f637b3dff2d3cf704f748
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "65000801"
---
# <a name="content-stored-in-exchange-online-mailboxes-for-ediscovery"></a>Zawartość przechowywana w Exchange Online skrzynkach pocztowych na potrzeby zbierania elektronicznych materiałów dowodowych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Skrzynka pocztowa w Exchange Online jest używana głównie do przechowywania elementów związanych z pocztą e-mail, takich jak wiadomości, elementy kalendarza, zadania i notatki. Ale to się zmienia, ponieważ coraz więcej aplikacji opartych na chmurze przechowuje również swoje dane w skrzynce pocztowej użytkownika. Jedną z zalet przechowywania danych w skrzynce pocztowej jest to, że możesz użyć narzędzi wyszukiwania zawartości, eDiscovery microsoft Purview (Standard) i microsoft Purview eDiscovery (Premium), aby znaleźć, wyświetlić i wyeksportować dane z tych aplikacji opartych na chmurze. Dane z niektórych z tych aplikacji są przechowywane w ukrytych folderach znajdujących się w poddrzeniu wiadomości innych niż IPM w skrzynce pocztowej. Dane z innych aplikacji opartych na chmurze mogą nie być przechowywane _w_ skrzynce pocztowej, ale _są skojarzone ze_ skrzynką pocztową i są zwracane w wyszukiwaniach (jeśli te dane są zgodne z zapytaniem wyszukiwania). Niezależnie od tego, czy dane oparte na chmurze są przechowywane w skrzynce pocztowej użytkownika, czy skojarzone z nią, zwykle nie są widoczne w kliencie poczty e-mail, gdy użytkownik otwiera swoją skrzynkę pocztową.

W poniższej tabeli wymieniono aplikacje, które przechowują lub kojarzą dane ze skrzynką pocztową opartą na chmurze. W tabeli opisano również typ zawartości, którą tworzy każda aplikacja.

<br>

****

|aplikacja Microsoft 365|Opis|
|---|---|
|Formularzy<sup>*</sup>|Formularze i odpowiedzi na formularz są przechowywane w plikach dołączonych do wiadomości e-mail i przechowywanych w ukrytym folderze w skrzynce pocztowej użytkownika, który utworzył formularz. Formularze utworzone przed kwietniem 2020 r. są przechowywane jako plik PDF. Formularze utworzone po 2020 r. są przechowywane jako plik JSON. Odpowiedzi na formularz są przechowywane w pliku CSV. Podczas eksportowania zawartości z formularzy w pliku PST te dane znajdują się w folderze **ApplicationDataRoot** w podfolderze o nazwie z następującym unikatowym identyfikatorem globalnym (GUID): **c9a559d2-7aab-4f13-a6ed-e7e9c52aec87**.|
|Grupy Microsoft 365|Wiadomości e-mail, elementy kalendarza, kontakty (osoby), notatki i zadania są przechowywane w skrzynce pocztowej skojarzonej z grupą Microsoft 365.|
|Outlook/Exchange Online|Wiadomości e-mail, elementy kalendarza, kontakty (osoby), notatki i zadania są przechowywane w skrzynce pocztowej użytkownika.|
|Ludzi|Kontakty w aplikacji Osoby (które są tymi samymi kontaktami co kontakty dostępne w Outlook) są przechowywane w skrzynce pocztowej użytkownika.|
|Harmonogram zajęć|Plany utworzone w harmonogramie zajęć są przechowywane w skrzynce pocztowej odpowiedniej grupy Microsoft 365, która jest aprowizowana podczas tworzenia nowego planu. Alias skrzynki pocztowej grupy to nazwa planu.|
|Skype dla firm|Konwersacje w Skype dla firm są przechowywane w folderze Historia konwersacji w skrzynce pocztowej użytkownika. Jeśli skrzynka pocztowa uczestnika spotkania Skype zostanie wstrzymana lub przypisana do zasad przechowywania, pliki dołączone do spotkania zostaną zachowane w skrzynce pocztowej uczestników.|
|Sway<sup>*</sup>|Sways są przechowywane jako plik HTML, który jest dołączony do wiadomości e-mail i przechowywane w ukrytym folderze w skrzynce pocztowej użytkownika, który utworzył kołysanie. Podczas eksportowania zawartości z Sway w pliku PST te dane znajdują się w folderze **ApplicationDataRoot** w podfolderze o nazwie o następującym identyfikatorze GUID: **905fcf26-4eb7-48a0-9ff0-8dcc7194b5ba**.|
|Zadania|Zadania w aplikacji Zadania (które są tymi samymi zadaniami, które są dostępne w Outlook) są przechowywane w skrzynce pocztowej użytkownika.|
|Teams|Konwersacje będące częścią kanału Teams są skojarzone ze skrzynką pocztową Teams. Konwersacje, które są częścią listy czatów w Teams (nazywane również *1 x N czatów) są skojarzone* ze skrzynką pocztową użytkowników, którzy uczestniczą w czacie. Ponadto informacje podsumowujące dotyczące spotkań i połączeń w kanale Teams są skojarzone ze skrzynkami pocztowymi użytkowników, którzy wybrali się na spotkanie lub połączenie. Dlatego podczas wyszukiwania Teams zawartości należy wyszukać w Teams skrzynkę pocztową zawartość w konwersacjach kanału i wyszukać zawartość w 1 x N czatach.|
|To-Do|Zadania ( *nazywane zadaniami do wykonania*, które są zapisywane na listach zadań do wykonania) w aplikacji To-Do są przechowywane w skrzynce pocztowej użytkownika.|
|Yammer|Konwersacje i komentarze w społeczności Yammer są skojarzone ze skrzynką pocztową grupy Microsoft 365, a także skrzynką pocztową użytkownika autora i wszystkich nazwanych adresatów (@ wymienionych lub użytkowników DW'ed). Prywatne wiadomości wysyłane poza społeczność Yammer są przechowywane w skrzynce pocztowej użytkowników, którzy uczestniczą w wiadomości prywatnej.|
|

> [!NOTE]
> <sup>*</sup>W tej chwili, jeśli blokada zostanie umieszczona w skrzynce pocztowej (przy użyciu blokad w przypadkach zbierania elektronicznych materiałów dowodowych (w warstwie Standardowa) lub zbierania elektronicznych materiałów dowodowych (Premium), zawartość z tej aplikacji nie zostanie zachowana przez blokadę.
