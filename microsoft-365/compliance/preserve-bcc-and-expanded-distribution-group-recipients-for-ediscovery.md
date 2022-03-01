---
title: Zachowywanie adresatów z listy UDW i rozwiniętych grup dystrybucyjnych na rzecz zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/19/2017
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.assetid: eb8ddf15-0080-457e-9d83-e73e193da334
description: In-Place, Zawieszenie w związku z postępowaniem sądowym i zasady przechowywania Microsoft 365 umożliwiają zachowywanie zawartości skrzynek pocztowych w celu spełnienia wymagań dotyczących zgodności z przepisami i zbierania elektronicznych materiałów dowodowych.
ms.openlocfilehash: c157f2fb0b74e679bf1252b6f24208b77a657d8c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033744"
---
# <a name="preserve-bcc-and-expanded-distribution-group-recipients-for-ediscovery"></a>Zachowywanie adresatów z listy UDW i rozwiniętych grup dystrybucyjnych na rzecz zbierania elektronicznych materiałów dowodowych
  
Zasady przechowywania w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych Microsoft 365 zasad [przechowywania (](./retention.md)utworzonych na stronie Centrum zgodności platformy Microsoft 365) umożliwiają zachowywanie zawartości skrzynek pocztowych w celu spełnienia wymagań dotyczących zgodności z przepisami i zbierania elektronicznych materiałów dowodowych. Informacje o adresatach bezpośrednio zaadresowanych w polach Do i DW wiadomości są domyślnie uwzględniane we wszystkich wiadomościach. Twoja organizacja może jednak wymagać możliwości wyszukania i odtworzenia szczegółowych informacji o wszystkich adresatach wiadomości. Obejmuje to:
  
- **Adresaci zaadresowany za pomocą pola UDW wiadomości:** Adresaci z kolumny UDW są przechowywani w wiadomości w skrzynce pocztowej nadawcy, ale nie są uwzględniani w nagłówkach wiadomości, które są dostarczane do adresatów. 
    
- **Adresaci rozszerzonej grupy dystrybucyjnej:** Adresaci, którzy otrzymają wiadomość, ponieważ są członkami grupy dystrybucyjnej, do której zaadresowana jest wiadomość, w polach Do, DW lub UDW. 
    
Exchange Online i Exchange Server 2013 (aktualizacja skumulowana 7 i nowsze) zachowują informacje o adresacie UDW i rozwiniętych grupach dystrybucyjnych. Te informacje można wyszukiwać przy użyciu narzędzia zbierania elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365. 
  
## <a name="how-bcc-recipients-and-expanded-distribution-group-recipients-are-preserved"></a>Jak są zachowywani adresaci z listy UDW i adresaci rozszerzonej grupy dystrybucyjnej

Jak wspomniano wcześniej, informacje o adresatach z udw są przechowywane razem z wiadomością w skrzynce pocztowej nadawcy. Te informacje są indeksowane i dostępne dla wyszukiwań i zbierania elektronicznych materiałów dowodowych. 
  
Informacje o rozwiniętych adresatach grupy dystrybucyjnej są przechowywane razem z wiadomością po umieścić skrzynkę pocztową w In-Place lub w sączasie sądowym. Na Office 365 te informacje są również przechowywane, gdy Microsoft 365 przechowywania są stosowane do skrzynki pocztowej. Członkostwo w grupach dystrybucyjnych jest określane w momencie wysłania wiadomości. Zmiany członkostwa w grupie po wysłaniu wiadomości nie mają wpływu na rozwiniętą listę adresatów przechowywaną z wiadomością. 
  
| Informacje o... | Jest przechowywany w... | Czy jest domyślnie przechowywana? | Dostępność dla... |
|:-----|:-----|:-----|:-----|
|Adresaci w polu Do i DW  <br/> |Właściwości wiadomości w skrzynkach pocztowych nadawcy i adresata.  <br/> |Tak  <br/> |Nadawcy, adresaci i służby zgodności  <br/> |
|Adresaci z listy UDW  <br/> |Właściwość wiadomości w skrzynce pocztowej nadawcy.  <br/> |Tak  <br/> |Nadawcy i schłodni nadawcy  <br/> |
|Adresaci rozszerzonej grupy dystrybucyjnej  <br/> |Właściwości wiadomości w skrzynce pocztowej nadawcy.  <br/> |L.p. Rozszerzone informacje o adresatach grupy dystrybucyjnej są przechowywane po umieszczeniu skrzynki pocztowej w In-Place lub w związku z postępowaniem sądowym albo do zasad przechowywania Microsoft 365 grupy dystrybucyjnej.  <br/> |Schowek do przestrzegania zgodności  <br/> |
   
## <a name="searching-for-messages-sent-to-bcc-and-expanded-distribution-group-recipients"></a>Wyszukiwanie wiadomości wysłanych do udw i rozwiniętych adresatów grupy dystrybucyjnej

Podczas wyszukiwania wiadomości wysłanych do adresata wyniki wyszukiwania zbierania elektronicznych materiałów dowodowych obejmują teraz wiadomości wysłane do grupy dystrybucyjnej, do których ten adresat należy. W poniższej tabeli przedstawiono scenariusze, w których wiadomości wysyłane do pola UDW i rozwiniętych adresatów grupy dystrybucyjnej są zwracane w wyszukiwaniach zbierania elektronicznych materiałów dowodowych.
  
Scenariusz 1. Jan jest członkiem grupy US-Sales dystrybucyjnej. W poniższej tabeli przedstawiono wyniki wyszukiwania zbierania elektronicznych materiałów dowodowych, gdy Wojciech wysyła wiadomość do Jana bezpośrednio lub pośrednio za pośrednictwem grupy dystrybucyjnej.
  
| Gdy przeszukujesz skrzynkę pocztową Wojciecha w poszukiwaniu wysyłanych wiadomości... | A wiadomość jest wysyłana za pomocą... | Wyniki zawierają komunikat? |
|:-----|:-----|:-----|
|Do:Jan  <br/> |John on TO  <br/> |Tak  <br/> |
|Do:Jan  <br/> |US-Sales wł. DO  <br/> |Tak  <br/> |
|To:US-Sales  <br/> |US-Sales wł. DO  <br/> |Tak  <br/> |
|DW:Jan  <br/> |Jan na DW  <br/> |Tak  <br/> |
|DW:Jan  <br/> |US-Sales w polu DW  <br/> |Tak  <br/> |
|DW:US-Sales  <br/> |US-Sales w polu DW  <br/> |Tak  <br/> |
   
Scenariusz 2. Jacek wysyła wiadomość e-mail do Jana (Do/DW) i Jacka (UDW bezpośrednio lub pośrednio za pośrednictwem grupy dystrybucyjnej). W poniższej tabeli przedstawiono wyniki wyszukiwania zbierania elektronicznych materiałów dowodowych.
  
| Podczas wyszukiwania... | W przypadku wysłanych wiadomości... | Wyniki zawierają komunikat? | Uwagi |
|:-----|:-----|:-----|:-----|
|Skrzynka pocztowa Wojciecha  <br/> |Do/DW:Jan  <br/> |Tak  <br/> |Wskazuje, że Jack był udw.  <br/> |
|Skrzynka pocztowa Wojciecha  <br/> |UDW:Jack  <br/> |Tak  <br/> |Wskazuje, że Jack był udw.  <br/> |
|Skrzynka pocztowa Wojciecha  <br/> |UDW:Jack (za pośrednictwem grupy dystrybucyjnej)  <br/> |Tak  <br/> |Lista członków grupy dystrybucyjnej z pola UDW rozwinięta po wysłaniu wiadomości jest widoczna w podglądzie wyszukiwania zbierania elektronicznych materiałów dowodowych, eksportowaniu i dziennikach.  <br/> |
|Skrzynka pocztowa Jana  <br/> |Do/DW:Jan  <br/> |Tak  <br/> |Bez wskazania adresatów z udw.  <br/> |
|Skrzynka pocztowa Jana  <br/> |UDW:Jack (bezpośrednio lub za pośrednictwem grupy dystrybucyjnej)  <br/> |Nie  <br/> |Informacje z udw nie są przechowywane w wiadomości dostarczanej do adresatów. Należy przeszukać skrzynkę pocztową nadawcy.  <br/> |
|Skrzynka pocztowa Jacka  <br/> |Do/DW:Jan (bezpośrednio lub za pośrednictwem grupy dystrybucyjnej)  <br/> |Tak  <br/> |Informacje o polu Do/DW są zawarte w wiadomości dostarczanej do wszystkich adresatów.  <br/> |
|Skrzynka pocztowa Jacka  <br/> |UDW:Jack (bezpośrednio lub za pośrednictwem grupy dystrybucyjnej)  <br/> |Nie  <br/> |Informacje z udw nie są przechowywane w wiadomości dostarczanej do adresatów. Należy przeszukać skrzynkę pocztową nadawcy.  <br/> |
   
## <a name="frequently-asked-questions"></a>Często zadawane pytania

 **Q. Kiedy i gdzie są przechowywane informacje o adresatach z udw?**
  
Odp. Informacje o adresatach z udw są zachowywane domyślnie w oryginalnej wiadomości w skrzynce pocztowej nadawcy. Jeśli adresat UDW jest grupą dystrybucyjną, członkostwo w grupach dystrybucyjnych jest rozszerzane tylko wtedy, gdy skrzynka pocztowa nadawcy znajduje się w posiadaniu nadawcy lub jest przypisana do Microsoft 365 przechowywania.
  
 **Q. Kiedy i gdzie jest przechowywana lista adresatów rozszerzonej grupy dystrybucyjnej?**
  
Odp. Członkostwo w grupie jest rozszerzane w momencie wysłania wiadomości. Lista rozwiniętych członków grupy dystrybucyjnej jest przechowywana w oryginalnej wiadomości w skrzynce pocztowej nadawcy. Skrzynka pocztowa nadawcy musi znajdować się w In-Place, w związku z postępowaniem sądowym lub musi być przypisana do Microsoft 365 przechowywania.
  
 **Q. Czy adresaci z listy Do/DW mogą zobaczyć, którzy adresaci zostali za pomocą udw?**
  
Odp. L.p. Te informacje nie są zawarte w nagłówkach wiadomości i nie są widoczne dla adresatów Do/DW. Nadawca może zobaczyć pole UDW przechowywane w oryginalnej wiadomości przechowywanej w jego skrzynce pocztowej. Te informacje mogą być widziane przez służby zgodności podczas przeszukiwania skrzynki pocztowej nadawcy.
  
 **Q. Jak mogę się upewnić, że adresaci rozszerzonej grupy dystrybucyjnej są zawsze zachowywani?**
  
Odp. Aby mieć pewność, że rozwinięta grupa dystrybucyjna będzie zawsze zachowywana wraz z wiadomością[, umieść](/Exchange/policy-and-compliance/holds/place-all-mailboxes-on-hold) wszystkie skrzynki pocztowe w miejscu lub utwórz zasady przechowywania dla całej organizacji Microsoft 365 przechowywania. 
  
 **Q. Jakie typy grup są obsługiwane?**
  
Odp. Obsługiwane są grupy dystrybucyjne, grupy zabezpieczeń z obsługą poczty i dynamiczne grupy dystrybucyjne. 
  
 **Q. Czy istnieje limit liczby adresatów grupy dystrybucyjnej, którzy są rozszerzani i przechowywani w wiadomości?**
  
Odp. Maksymalnie 10 000 członków grupy dystrybucyjnej jest zachowywanych.
  
 **Q. Czy są obsługiwane zagnieżdżone grupy dystrybucyjne?**
  
Odp. Tak, rozwiniętych jest 25 poziomów zagnieżdżonych grup dystrybucyjnych.
  
 **Q. Gdzie są widoczne informacje o adresacie UDW i rozszerzonej grupy dystrybucyjnej?**
  
Odp. Informacje o adresatach z pola UDW i rozszerzonej grupy dystrybucyjnej są widoczne dla służb zgodności podczas wyszukiwania zbierania elektronicznych materiałów dowodowych. Adresaci z pola UDW i rozwinięta grupa dystrybucyjna są uwzględniani w wynikach wyszukiwania kopiowanych do skrzynki pocztowej odnajdowania lub eksportowanych do pliku PST i w dzienniku zbierania elektronicznych materiałów dowodowych uwzględnionym w wynikach wyszukiwania. Informacje o adresatach z pola UDW są również dostępne w podglądzie wyszukiwania.
  
 **Q. Co się stanie, jeśli członek grupy dystrybucyjnej jest ukryty na globalnej liście adresowej organizacji?**
  
Odp. Nie ma żadnego wpływu. Jeśli adresaci są ukryti na liście adresowej, nadal są oni uwzględniani na liście adresatów dla rozwiniętej grupy dystrybucyjnej.