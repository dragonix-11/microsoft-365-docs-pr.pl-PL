---
title: Usuń siebie z listy zablokowanych nadawców i rozwiąż problem z błędami „5.7.511 Odmowa dostępu”
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
description: W tym artykule dowiesz się, jak usunąć siebie z listy zablokowanych nadawców platformy Microsoft 365 za pomocą portalu usuwania listy. Jest to najlepsza odpowiedź na rozwiązanie problemu z błędami „5.7.511 Odmowa dostępu”.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 83822faaf1c667524dd88fc1bba400c10fa30ac3
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647738"
---
# <a name="use-the-delist-portal-to-remove-yourself-from-the-blocked-senders-list-and-address-57511-access-denied-errors"></a>Użyj portalu usuwania z listy, aby usunąć siebie z listy zablokowanych nadawców i rozwiąż problem z błędami „5.7.511 Odmowa dostępu”

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Czy podczas próby wysłania wiadomości e-mail do adresata, którego adres e-mail znajduje się na platformie Microsoft 365, otrzymujesz komunikat o błędzie (na przykład „5.7.511 Odmowa dostępu”)? Jeśli uważasz, że nie powinien zostać wyświetlony komunikat o błędzie, możesz usunąć się z listy zablokowanych nadawców za pomocą portalu usuwania z listy zablokowanych nadawców.

## <a name="what-is-the-blocked-senders-list"></a>Co to jest lista zablokowanych nadawców?

Firma Microsoft korzysta z listy zablokowanych nadawców, aby chronić swoich klientów przed spamem, fałszowaniem i wyłudzaniem informacji. Adres IP serwera poczty, czyli adres używany przez serwer poczty do identyfikowania się w Internecie, został oznaczony jako potencjalne zagrożenie dla platformy Microsoft 365 z różnych powodów. Gdy platforma Microsoft 365 dodaje adres IP do listy, uniemożliwia to dalszą komunikację między adresem IP a dowolnym z naszych klientów za pomocą naszych centrów danych.

Będziesz wiedział, że zostałeś dodany do listy po otrzymaniu odpowiedzi na wiadomość e-mail zawierającą błąd, który wygląda mniej więcej tak:

> 550 5.7.606-649 Odmowa dostępu, zablokowano wysyłanie adresu IP [_adres IP_] (np. 5.7.511 Odmowa dostępu): Aby zażądać usunięcia z tej listy, odwiedź stronę <https://sender.office.com/> i postępuj zgodnie z instrukcjami. Aby uzyskać więcej informacji, zobacz [Raporty o niedostarczeniu wiadomości e-mail w usłudze Exchange Online](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online).

gdzie  _adres IP_ jest adresem IP komputera, na którym działa serwer poczty.

## <a name="verify-senders-before-removing-them-from-the-blocked-senders-list"></a>Zweryfikuj nadawców przed usunięciem ich z listy zablokowanych nadawców

Istnieją uzasadnione powody, dla których nadawcy trafiają na listę zablokowanych nadawców, ale mogą się zdarzyć błędy. Przyjrzyj się temu klipowi wideo, aby zapoznać się ze zrównoważonym wyjaśnieniem dotyczącym zablokowanych nadawców i usuwaniem ich z listy.
<p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMhvD]

## <a name="to-use-delist-portal-to-remove-yourself-from-the-blocked-senders-list-after-errors-like-57511-access-denied"></a>Aby usunąć siebie z listy zablokowanych nadawców za pomocą portalu usuwania z listy (po błędach takich jak „5.7.511 Odmowa dostępu”)

1. W przeglądarce internetowej przejdź do <https://sender.office.com>.

2. Postępuj zgodnie z instrukcjami na stronie. Upewnij się, że używasz adresu e-mail, na który został wysłany komunikat o błędzie, oraz adresu IP określonego w komunikacie o błędzie. Możesz wprowadzić tylko jeden adres e-mail i jeden adres IP na wizytę.

3. Kliknij pozycję **Prześlij**.

    Portal wysyła wiadomość e-mail na podany adres e-mail. Wiadomość e-mail będzie wyglądać mniej więcej tak:

    :::image type="content" source="../../media/bf13e4f7-f68c-4e46-baa7-b6ab4cfc13f3.png" alt-text="Wiadomość e-mail otrzymana podczas przesyłania żądania za pomocą portalu usuwania z listy" lightbox="../../media/bf13e4f7-f68c-4e46-baa7-b6ab4cfc13f3.png":::

4. Kliknij link potwierdzenia w wiadomości e-mail wysłanej przez portal do usuwania z listy.

    Spowoduje to powrót do portalu usuwania z listy.

5. W portalu usuwania z listy kliknij pozycję **Usuń z listy adres IP**.

    Po usunięciu adresu IP z listy zablokowanych nadawców wiadomości e-mail z tego adresu IP będą dostarczane do adresatów korzystających z platformy Microsoft 365. Upewnij się więc, że wiadomość e-mail wysłana z tego adresu IP nie będzie obraźliwa ani złośliwa; w przeciwnym razie adres IP może zostać ponownie zablokowany.

    > [!NOTE]
    > Zanim ograniczenia zostaną zniesione, może upłynąć do 24 godzin, a wyniki mogą się znacznie różnić.

Zobacz [Tworzenie bezpiecznych list nadawców w usłudze EOP](create-safe-sender-lists-in-office-365.md) i [Ochrona przed spamem wychodzącym w usłudze EOP](outbound-spam-controls.md), aby zapobiec blokowaniu adresu IP.

### <a name="how-do-fix-error-code-57511"></a>Jak naprawić kod błędu 5.7.511

W razie problemu z dostarczeniem wysłanej wiadomości e-mail platforma Microsoft 365 lub usługa Office 365 wysyła do nadawcy wiadomość e-mail z informacją o tym. Wiadomość e-mail, którą otrzymujesz, jest powiadomieniem o stanie dostarczenia(DSN), nazywanym również wiadomością zwróconą. Standardowe powiadomienie tego typu jest nazywane raportem o niedostarczeniu, który informuje, że wiadomość nie została dostarczona. W pewnych sytuacjach firma Microsoft musi przeprowadzić dodatkowe badania dotyczące ruchu z Twojego adresu IP, a jeśli otrzymujesz kod NDR 5.7.511, **nie będziesz** mieć możliwości korzystania z portalu usuwania z listy.

> 550 5.7.511 Odmowa dostępu, zablokowany nadawca[xxx.xxx.xxx.xxx]. Aby zażądać usunięcia z tej listy, prześlij dalej tę wiadomość do delist@messaging.microsoft.com. Aby uzyskać więcej informacji, przejdź do <https://go.microsoft.com/fwlink/?LinkId=526653>.

W wiadomości e-mail, aby zażądać usunięcia z tej listy, podaj pełny kod NDR i adres IP. Firma Microsoft skontaktuje się z Tobą w ciągu 48 godzin z informacją o kolejnych krokach.

## <a name="more-information"></a>Więcej informacji

Formularz usuwania z listy dla usługi **Outlook.com, obsługa konsumenta** można znaleźć [tutaj](https://support.microsoft.com/supportrequestform/8ad563e3-288e-2a61-8122-3ba03d6b8d75). Pamiętaj, aby najpierw przeczytać [często zadawane pytania](https://sendersupport.olc.protection.outlook.com/pm/troubleshooting.aspx), aby uzyskać instrukcję dotyczącą _przesyłania_.
