---
title: Zawartość przechowywana w Exchange Online pocztowych
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
description: Zawartość skojarzona z aplikacjami opartymi na chmurze Microsoft 365 jest przechowywana lub skojarzona ze skrzynką pocztową Exchange Online użytkownika. Tę zawartość można przeszukiwać przy użyciu narzędzi zbierania elektronicznych materiałów dowodowych firmy Microsoft.
ms.openlocfilehash: f7db327d21928df925bfd6451226ab96782d715b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986422"
---
# <a name="content-stored-in-exchange-online-mailboxes-for-ediscovery"></a>Zawartość przechowywana w Exchange Online eDiscovery

Skrzynka pocztowa w Exchange Online jest używana głównie do przechowywania elementów związanych z pocztą e-mail, takich jak wiadomości, elementy kalendarza, zadania i notatki. Jednak zmienia się to, ponieważ aplikacje oparte na chmurze przechowują również ich dane w skrzynce pocztowej użytkownika. Jedną z zalet przechowywania danych w skrzynce pocztowej jest możliwość korzystania z narzędzi wyszukiwania w przeszukiwaniu zawartości, podstawowym zbierania elektronicznych materiałów dowodowych i programie Advanced eDiscovery w celu znalezienia, wyświetlenia i wyeksportowania danych z tych aplikacji opartych na chmurze. Dane z niektórych z tych aplikacji są przechowywane w folderach ukrytych znajdujących się w drzewie podrzędnym wiadomości nieperpersonalnych (innych niż IPM) w skrzynce pocztowej. Dane z innych aplikacji opartych na chmurze mogą nie być  przechowywane w skrzynce pocztowej, ale są  skojarzone ze skrzynką pocztową i są zwracane w wyszukiwaniach (jeśli te dane są takie, jak zapytanie wyszukiwania). Niezależnie od tego, czy dane przechowywane w chmurze są przechowywane w skrzynce pocztowej użytkownika, czy skojarzone z nią, te dane zwykle nie są widoczne w kliencie poczty e-mail, gdy użytkownik otwiera skrzynkę pocztową.

W poniższej tabeli wymieniono aplikacje, które przechowywują lub kojarzą dane ze skrzynką pocztową w chmurze. W tabeli opisano również typ zawartości poszczególnych aplikacji.

<br>

****

|Microsoft 365 aplikacji|Opis|
|---|---|
|Formularze<sup>*</sup>|Formularze i odpowiedzi na formularz są przechowywane w plikach dołączonych do wiadomości e-mail i przechowywane w ukrytym folderze w skrzynce pocztowej użytkownika, który utworzył formularz. Formularze utworzone przed kwietniem 2020 r. są przechowywane jako plik PDF. Formularze utworzone po 2020 roku są przechowywane jako plik JSON. Odpowiedzi na formularz są przechowywane w pliku CSV. Podczas eksportowania zawartości z formularzy w pliku PST te dane znajdują się w folderze **ApplicationDataRoot** w podfolderze o nazwie o nazwie identyfikatorem GUID: **c9a559d2-7aab-4f13-a6ed-e7e9c52aec87**.|
|Microsoft 365 grupy|Wiadomości e-mail, elementy kalendarza, kontakty (Kontakty), notatki i zadania są przechowywane w skrzynce pocztowej skojarzonej z Microsoft 365 grupy.|
|Outlook/Exchange Online|Wiadomości e-mail, elementy kalendarza, kontakty (Kontakty), notatki i zadania są przechowywane w skrzynce pocztowej użytkownika.|
|Osoby|Kontakty w aplikacji Kontakty (które są tym samym kontaktem co kontakty dostępne w Outlook) są przechowywane w skrzynce pocztowej użytkownika.|
|Plan zajęć|Plany utworzone w planie zajęć są przechowywane w skrzynce pocztowej odpowiedniej grupy Microsoft 365, która jest zapewniana podczas tworzenia nowego planu. Alias skrzynki pocztowej grupy to nazwa planu.|
|Skype dla firm|Konwersacje Skype dla firm są przechowywane w folderze Historia konwersacji w skrzynce pocztowej użytkownika. Jeśli skrzynka pocztowa uczestnika spotkania programu Skype została umieszczona w związku z postępowaniem sądowym lub przypisana do zasad przechowywania, pliki dołączone do spotkania są zachowywane w skrzynce pocztowej uczestników.|
|Sway<sup>*</sup>|Swaye są przechowywane jako plik HTML dołączony do wiadomości e-mail i przechowywane w ukrytym folderze w skrzynce pocztowej użytkownika, który utworzył sway. Podczas eksportowania zawartości z aplikacji Sway w pliku PST te dane znajdują się w folderze **ApplicationDataRoot** w podfolderze o nazwie o następującym identyfikatorze GUID: **905fcf26-4eb7-48a0-9ff0-8dcc7194b5ba**.|
|Zadania|Zadania w aplikacji Zadania (które są zadaniami dostępnymi w programie Outlook) są przechowywane w skrzynce pocztowej użytkownika.|
|Teams|Konwersacje w ramach kanału Teams są skojarzone ze skrzynką Teams pocztowej. Konwersacje, które są częścią listy czatów w Teams (nazywanych również czatami *1 x N*) są skojarzone ze skrzynką pocztową użytkowników, którzy uczestniczą w czacie. Ponadto informacje podsumowujące dotyczące spotkań i połączeń w kanale Teams są skojarzone ze skrzynkami pocztowymi użytkowników, którzy nacięli się do spotkania lub połączenia telefonicznego. Zatem podczas wyszukiwania Teams zawartości w skrzynce pocztowej usługi Teams w celu wyszukiwania zawartości w konwersacjach na kanale i wyszukiwania zawartości w czatach 1 x N w skrzynkach pocztowych użytkowników.|
|To-Do|Zadania ( *nazywane zadaniami do wykonania*, które są zapisywane na listach zadań do wykonania) w aplikacji To-Do są przechowywane w skrzynce pocztowej użytkownika.|
|Yammer|Konwersacje i komentarze w społeczności programu Yammer są skojarzone ze skrzynką pocztową grupy Microsoft 365, a także skrzynką pocztową użytkownika autora i wszystkich nazwanych adresatów (@wzmiankowanych lub użytkowników z dw)." Prywatne wiadomości wysyłane poza społecznością Yammer są przechowywane w skrzynce pocztowej użytkowników, którzy uczestniczą w tej wiadomości prywatnej.|
|

> [!NOTE]
> <sup>*</sup>Obecnie, jeśli do skrzynki pocztowej zostanie umieszczone blokady (przy użyciu blokady w podstawowych przypadkach zbierania elektronicznych materiałów dowodowych lub Advanced eDiscovery), zawartość z tej aplikacji nie będzie zachowywana przez zastosowanie blokady.
