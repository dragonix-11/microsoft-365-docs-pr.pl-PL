---
title: Zachowywanie adresatów Bcc i rozszerzonych grup dystrybucyjnych na potrzeby zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 6/19/2017
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.assetid: eb8ddf15-0080-457e-9d83-e73e193da334
description: zasady przechowywania In-Place Hold, Litigation Hold i Microsoft 365 umożliwiają zachowanie zawartości skrzynki pocztowej w celu spełnienia wymagań dotyczących zgodności z przepisami i zbierania elektronicznych materiałów dowodowych.
ms.openlocfilehash: de1a04c223856e1257e03e5dd47ae6d5e88033eb
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637092"
---
# <a name="preserve-bcc-and-expanded-distribution-group-recipients-for-ediscovery"></a>Zachowywanie adresatów Bcc i rozszerzonych grup dystrybucyjnych na potrzeby zbierania elektronicznych materiałów dowodowych
  
Spory sądowe, blokady zbierania elektronicznych materiałów dowodowych i [zasady przechowywania platformy Microsoft 365](./retention.md) (utworzone w portal zgodności Microsoft Purview) umożliwiają zachowanie zawartości skrzynki pocztowej w celu spełnienia wymagań dotyczących zgodności z przepisami i zbierania elektronicznych materiałów dowodowych. Informacje o adresatach bezpośrednio adresowanych w polach Do i DW wiadomości są domyślnie uwzględniane we wszystkich komunikatach. Organizacja może jednak wymagać możliwości wyszukiwania i odtwarzania szczegółów dotyczących wszystkich adresatów wiadomości. Obejmuje to:
  
- **Adresaci adresaci adresaci za pomocą pola Bcc wiadomości:** Adresaci usługi Bcc są przechowywane w wiadomości w skrzynce pocztowej nadawcy, ale nie są uwzględniane w nagłówkach wiadomości dostarczonej do adresatów. 
    
- **Rozszerzoni adresaci grupy dystrybucyjnej:** Adresaci, którzy otrzymają wiadomość, ponieważ są członkami grupy dystrybucyjnej, do której adresowano wiadomość, w polach Do, DW lub BCC. 
    
Exchange Online i Exchange Server 2013 r. (aktualizacja zbiorcza 7 i nowsze wersje) przechowują informacje o adresatach Bcc i rozszerzonych grup dystrybucyjnych. Te informacje można wyszukać za pomocą narzędzia zbierania elektronicznych materiałów dowodowych w portalu zgodności.
  
## <a name="how-bcc-recipients-and-expanded-distribution-group-recipients-are-preserved"></a>Jak są zachowywane adresaci usługi Bcc i adresaci rozszerzonej grupy dystrybucyjnej

Jak wspomniano wcześniej, informacje o adresatach Bcc'ed są przechowywane z wiadomością w skrzynce pocztowej nadawcy. Te informacje są indeksowane i dostępne dla wyszukiwań i blokad zbierania elektronicznych materiałów dowodowych.

Informacje o rozszerzonych adresatach grup dystrybucyjnych są przechowywane w wiadomości po umieszczeniu skrzynki pocztowej w In-Place Blokada lub Blokada postępowania sądowego. W Office 365 te informacje są również przechowywane, gdy zasady przechowywania platformy Microsoft 365 są stosowane do skrzynki pocztowej. Członkostwo w grupie dystrybucyjnej jest określane w momencie wysłania komunikatu. Po wysłaniu wiadomości zmiany w członkostwie w grupie nie mają wpływu na rozszerzoną listę adresatów przechowywaną w wiadomości.

|Informacje o...|Jest przechowywany w...|Czy jest domyślnie przechowywany?|Jest dostępny dla...|
|---|---|---|---|
|Adresaci do i adresatów DW|Właściwości wiadomości w skrzynkach pocztowych nadawcy i adresatów.|Tak|Nadawca, adresaci i funkcjonariusze ds. zgodności|
|Adresaci programu Bcc|Właściwość message w skrzynce pocztowej nadawcy.|Tak|Nadawca i funkcjonariusze ds. zgodności|
|Rozszerzoni adresaci grupy dystrybucyjnej|Właściwości wiadomości w skrzynce pocztowej nadawcy.|L.p. Informacje o adresacie rozszerzonej grupy dystrybucyjnej są przechowywane po umieszczeniu skrzynki pocztowej w In-Place blokadzie lub blokadzie postępowania sądowego albo przypisaniu do zasad przechowywania platformy Microsoft 365.|Funkcjonariusze ds. zgodności|

## <a name="searching-for-messages-sent-to-bcc-and-expanded-distribution-group-recipients"></a>Wyszukiwanie komunikatów wysyłanych do usługi Bcc i rozszerzonych adresatów grupy dystrybucyjnej

Podczas wyszukiwania wiadomości wysłanych do adresata wyniki wyszukiwania zbierania elektronicznych materiałów dowodowych zawierają teraz komunikaty wysyłane do grupy dystrybucyjnej, do których należy adresat. W poniższej tabeli przedstawiono scenariusze, w których komunikaty wysyłane do Bcc i rozszerzonych adresatów grup dystrybucyjnych są zwracane w wyszukiwaniach zbierania elektronicznych materiałów dowodowych.

Scenariusz 1. Jan jest członkiem US-Sales grupy dystrybucyjnej. W tej tabeli przedstawiono wyniki wyszukiwania zbierania elektronicznych materiałów dowodowych, gdy Bob wysyła komunikat do Jana bezpośrednio lub pośrednio za pośrednictwem grupy dystrybucyjnej.

|Podczas wyszukiwania w skrzynce pocztowej Boba wiadomości wysłane...|A wiadomość jest wysyłana z...|Wyniki zawierają komunikat?|
|---|---|---|
|Do:Jan|John na TO|Tak|
|Do:Jan|US-Sales w usłudze TO|Tak|
|To:US-Sales|US-Sales w usłudze TO|Tak|
|DW:Jan|Jan w programie CC|Tak|
|DW:Jan|US-Sales w programie CC|Tak|
|Cc:US-Sales|US-Sales w programie CC|Tak|

Scenariusz 2. Bob wysyła wiadomość e-mail do Jana (To/Cc) i Jacka (Bcc bezpośrednio lub pośrednio za pośrednictwem grupy dystrybucyjnej). W poniższej tabeli przedstawiono wyniki wyszukiwania zbierania elektronicznych materiałów dowodowych.

|Podczas wyszukiwania...|W przypadku wysłanych wiadomości...|Wyniki zawierają komunikat?|Uwagi|
|---|---|---|---|
|Skrzynka pocztowa Boba|Do/Cc:John|Tak|Wskazuje, że Jack był Bcc'ed.|
|Skrzynka pocztowa Boba|Bcc:Jack|Tak|Wskazuje, że Jack był Bcc'ed.|
|Skrzynka pocztowa Boba|Bcc:Jack (za pośrednictwem grupy dystrybucyjnej)|Tak|Lista członków grupy dystrybucyjnej Bcc'ed, rozwinięta po wysłaniu komunikatu, jest widoczna w podglądzie wyszukiwania elektronicznego, wyeksportowaniu i dziennikach.|
|Skrzynka pocztowa Jana|Do/Cc:John|Tak|Brak wskazania adresatów BCC.|
|Skrzynka pocztowa Jana|Bcc:Jack (bezpośrednio lub za pośrednictwem grupy dystrybucyjnej)|Nie|Informacje Bcc nie są przechowywane w wiadomości dostarczonej do adresatów. Musisz przeszukać skrzynkę pocztową nadawcy.|
|Skrzynka pocztowa Jacka|To/Cc:John (bezpośrednio lub za pośrednictwem grupy dystrybucyjnej)|Tak|Informacje o to/DW są zawarte w wiadomości dostarczanej do wszystkich adresatów.|
|Skrzynka pocztowa Jacka|Bcc:Jack (bezpośrednio lub za pośrednictwem grupy dystrybucyjnej)|Nie|Informacje Bcc nie są przechowywane w wiadomości dostarczonej do adresatów. Musisz przeszukać skrzynkę pocztową nadawcy.|

## <a name="frequently-asked-questions"></a>Często zadawane pytania

 **P. Kiedy i gdzie są przechowywane informacje o adresacie Bcc?**

Odp. Informacje o adresacie BCC są domyślnie zachowywane w oryginalnej wiadomości w skrzynce pocztowej nadawcy. Jeśli adresat Bcc jest grupą dystrybucyjną, członkostwo w grupie dystrybucyjnej jest rozszerzane tylko wtedy, gdy skrzynka pocztowa nadawcy jest wstrzymana lub przypisana do zasad przechowywania platformy Microsoft 365.

 **P. Kiedy i gdzie jest przechowywana lista rozszerzonych adresatów grup dystrybucyjnych?**

Odp. Członkostwo w grupie jest rozszerzane w momencie wysłania komunikatu. Lista rozwiniętych członków grupy dystrybucyjnej jest przechowywana w oryginalnej wiadomości w skrzynce pocztowej nadawcy. Skrzynka pocztowa nadawcy musi znajdować się w In-Place Blokada, Blokada postępowania sądowego lub przypisana do zasad przechowywania usługi Microsoft 365.

 **P. Czy adresaci To/Cc mogą zobaczyć, którzy adresaci byli Bcc'ed?**

Odp. L.p. Te informacje nie są zawarte w nagłówkach komunikatów i nie są widoczne dla adresatów Do/DW. Nadawca może zobaczyć pole Bcc przechowywane w oryginalnej wiadomości przechowywanej w skrzynce pocztowej. Funkcjonariusze ds. zgodności mogą wyświetlać te informacje podczas przeszukiwania skrzynki pocztowej nadawcy.

 **P. Jak zapewnić, że adresaci rozszerzonej grupy dystrybucyjnej są zawsze zachowywane?**

Odp. Aby upewnić się, że rozwinięte elementy członkowskie grupy dystrybucyjnej są zawsze zachowywane za pomocą wiadomości, [umieść wszystkie skrzynki pocztowe w stanie wstrzymania](/Exchange/policy-and-compliance/holds/place-all-mailboxes-on-hold) lub utwórz zasady przechowywania platformy Microsoft 365 dla całej organizacji.

 **P. Które typy grup są obsługiwane?**

Odp. Obsługiwane są grupy dystrybucyjne, grupy zabezpieczeń z obsługą poczty i dynamiczne grupy dystrybucyjne.

 **P. Czy istnieje limit liczby adresatów grup dystrybucyjnych, które są rozwinięte i przechowywane w wiadomości?**

Odp. Do 10 000 członków grupy dystrybucyjnej jest zachowywanych.

 **P. Czy obsługiwane są zagnieżdżone grupy dystrybucyjne?**

Odp. Tak, rozszerzono 25 poziomów zagnieżdżonych grup dystrybucji.

 **P. Gdzie są widoczne informacje o adresacie Bcc i rozszerzonej grupie dystrybucyjnej?**

Odp. Informacje o adresatach rozszerzonej grupy dystrybucyjnej i BCC są widoczne dla funkcjonariuszy ds. zgodności podczas wykonywania wyszukiwania zbierania elektronicznych materiałów dowodowych. Adresaci Bcc i rozszerzonej grupy dystrybucyjnej są uwzględniane w wynikach wyszukiwania skopiowanych do skrzynki pocztowej odnajdywania lub wyeksportowanych do pliku PST i w dzienniku zbierania elektronicznych materiałów dowodowych zawartych w wynikach wyszukiwania. Informacje o adresacie BCC są również dostępne w wersji zapoznawczej wyszukiwania.

 **P. Co się stanie, jeśli członek grupy dystrybucyjnej zostanie ukryty przed globalną listą adresową organizacji?**

Odp. Nie ma to wpływu. Jeśli adresaci są ukryte przed gal, są one nadal zawarte na liście adresatów dla rozszerzonej grupy dystrybucyjnej.
