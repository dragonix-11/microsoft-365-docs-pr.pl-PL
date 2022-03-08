---
title: Usuwanie siebie z listy zablokowanych nadawców i adresu 5.7.511 Błędy odrzuconych dostępu
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 04/18/2016
audience: ITPro
ms.topic: troubleshooting
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 0bcecdd4-3343-4cc0-9e58-e19d4de515e8
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: W tym artykule dowiesz się, jak za pomocą portalu delist usunąć siebie z listy zablokowanych Microsoft 365 nadawców. Jest to najlepsza odpowiedź na błędy odrzucone przez program Access 5.7.511.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 36187288b2a7acf1a852e6c203cbb84035ba5d7a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320245"
---
# <a name="use-the-delist-portal-to-remove-yourself-from-the-blocked-senders-list-and-address-57511-access-denied-errors"></a>Korzystanie z portalu delist w celu usunięcia siebie z listy zablokowanych nadawców i adresu 5.7.511 Błędy odrzuconych dostępu

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Czy otrzymujesz komunikat o błędzie podczas próby wysłania wiadomości e-mail do adresata, którego adres e-mail znajduje się w programie Microsoft 365 (na przykład i adres 5.7.511 Odmowa dostępu)? Jeśli uważasz, że nie powinien być wyświetlany komunikat o błędzie, możesz użyć portalu delist, aby usunąć siebie z listy zablokowanych nadawców.

## <a name="what-is-the-blocked-senders-list"></a>Co to jest lista zablokowanych nadawców?

Firma Microsoft używa listy zablokowanych nadawców w celu ochrony swoich klientów przed spamem, fałszowaniem i wyłudzaniem informacji. Adres IP serwera poczty, który jest używany przez serwer poczty do identyfikowania się w Internecie, został otagowany jako potencjalne zagrożenie dla serwera Microsoft 365 z różnych powodów. Dodanie Microsoft 365 IP do listy uniemożliwia dalszą komunikację między tym adresem IP a dowolnym z naszych klientów za pośrednictwem naszych centrów danych.

Będziesz wiedzieć, że dodano Cię do listy po otrzymaniu odpowiedzi na wiadomość e-mail z komunikatem o błędzie, który wygląda podobnie do tego:

> 550 5.7.606-649 Odmowa dostępu, zablokowanie wysyłania adresu IP [_adres IP_] (np. 5.7.511 Odmowa dostępu: Aby zażądać usunięcia z tej listy, <https://sender.office.com/> odwiedź i postępuj zgodnie z instrukcjami. Aby uzyskać więcej informacji, [zobacz Raporty o niedo dostarczenia wiadomości e-mail w Exchange Online](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online).

Gdzie  _adres IP_ to adres IP komputera, na którym działa serwer poczty.

## <a name="verify-senders-before-removing-them-from-the-blocked-senders-list"></a>Weryfikowanie nadawców przed usunięciem ich z listy zablokowanych nadawców

Istnieją dobre powody, dla których nadawcy mogą się pojawiać na liście zablokowanych nadawców, ale mogą się zdarzyć błędy. W tym klipie wideo popatrz na zrównoważone objaśnienie zablokowanych nadawców i delistowania.
<p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMhvD]


## <a name="to-use-delist-portal-to-remove-yourself-from-the-blocked-senders-list-after-errors-like-57511-access-denied"></a>Aby użyć portalu delist w celu usunięcia siebie z listy zablokowanych nadawców (po błędach, takich jak 5.7.511 Odmowa dostępu)

1. W przeglądarce internetowej przejdź do .<https://sender.office.com>

2. Postępuj zgodnie z instrukcjami wyświetlanymi na stronie. Upewnij się, że używasz adresu e-mail, na który wysłano komunikat o błędzie, oraz adresu IP określonego w komunikacie o błędzie. Możesz wprowadzić tylko jeden adres e-mail i jeden adres IP podczas odwiedzin.

3. Kliknij **przycisk Prześlij**.

    Portal wysyła wiadomość e-mail na podany przez Ciebie adres e-mail. Wiadomość e-mail będzie wyglądać podobnie do następującego:

    ![Zrzut ekranu przedstawiający wiadomość e-mail otrzymaną po przesłaniu żądania za pośrednictwem portalu delist.](../../media/bf13e4f7-f68c-4e46-baa7-b6ab4cfc13f3.png)

4. Kliknij link potwierdzenia w wiadomości e-mail wysłanej do Ciebie przez portal delistowania.

    Powrócisz do portalu delist.

5. W portalu delist kliknij pozycję **Delist IP (Delist IP**).

    Po usunięciu adresu IP z listy zablokowanych nadawców wiadomości e-mail z tego adresu IP będą dostarczane do adresatów, którzy używają tego Microsoft 365. Dlatego upewnij się, że wiadomości e-mail wysyłane z tego adresu IP nie będą obraźliwe ani złośliwe. w przeciwnym razie adres IP może zostać ponownie zablokowany.

    > [!NOTE]
    > Usunięcie ograniczeń może potrwać do 24 godzin lub mogą być bardzo różne wyniki.

Aby [zapobiec blokowaniu](create-safe-sender-lists-in-office-365.md) adresów IP, zobacz Tworzenie list bezpiecznych nadawców w u usługi EOP i Ochrona [przed spamem](outbound-spam-controls.md) ruchu wychodzącego w u usługi EOP.

### <a name="how-do-fix-error-code-57511"></a>Jak naprawić kod błędu 5.7.511
 
W przypadku problemu z dostarczaniem wysłanej wiadomości e-mail usługa Microsoft 365 lub Office 365 e-mail z powiadomieniem. Odbierana wiadomość e-mail to powiadomienie o stanie dostarczenia, nazywane także wiadomością dsn lub wiadomością podskokową. Standardowe powiadomienie tego typu jest nazywane raportem o niedostarczeniu, który informuje, że wiadomość nie została dostarczona. W niektórych sytuacjach firma Microsoft musi przeprowadzić dodatkowe badania nad ruchem z Twojego adresu IP, a jeśli otrzymujesz kod błędu NDR 5.7.511, nie będzie można korzystać z portalu delist.
 
>   550 5.7.511 Odmowa dostępu, zablokowany nadawca[xxx.xxx.xxx.xxx]. Aby zażądać usunięcia z tej listy, przekaż tę wiadomość do delist@messaging.microsoft.com. Aby uzyskać więcej informacji, przejdź do https://go.microsoft.com/fwlink/?LinkId=526653. 
 
W wiadomości e-mail, aby zażądać usunięcia z tej listy, podaj pełny kod IDR i adres IP. Firma Microsoft skontaktuje się z Tobą w ciągu 48 godzin, przy użyciu następnych kroków. 

## <a name="more-information"></a>Więcej informacji
  
Tutaj można znaleźć formularz delistowania dla **Outlook.com, z** usługi dla klientów [konsumenckich](https://support.microsoft.com/supportrequestform/8ad563e3-288e-2a61-8122-3ba03d6b8d75). W pierwszej kolejności zapoznaj się z często [zadawanymi](https://sendersupport.olc.protection.outlook.com/pm/troubleshooting.aspx) pytaniami, aby *zapoznać się z kierunkiem* przesyłania.
