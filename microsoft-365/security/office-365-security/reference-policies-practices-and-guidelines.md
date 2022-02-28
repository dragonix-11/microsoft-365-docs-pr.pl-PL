---
title: Zasady, wskazówki i wskazówki odniesienie informacji
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ff3f140b-b005-445f-bfe0-7bc3f328aaf0
ms.collection:
- M365-security-compliance
description: Firma Microsoft opracowała różne zasady, procedury i przyjęły szereg najlepszych rozwiązań branżowych, aby chronić naszych użytkowników przed obraźliwymi, niechcianymi i złośliwymi wiadomościami e-mail.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 21b1918155755d7786f7b797ae7c705ca8c0ec39
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988435"
---
# <a name="reference-policies-practices-and-guidelines"></a>Informacje: Zasady, wskazówki i wskazówki

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Firma Microsoft ma na celu pomoc w zapewnianiu najbardziej zaufanego interfejsu użytkownika w sieci Web. Dlatego firma Microsoft opracowała różne zasady, procedury i przyjęły szereg najlepszych rozwiązań branżowych, aby chronić naszych użytkowników przed obraźliwymi, niechcianymi i złośliwymi wiadomościami e-mail. Nadawcy próbujący wysłać wiadomość e-mail do użytkowników powinni upewnić się, że w pełni rozumieją wskazówki w tym artykule i ich nasuną zgodnie z wytycznymi w tym artykule, aby pomóc w uniknięciu potencjalnych problemów z dostarczaniem.

Jeśli użytkownik nie jest zgodny z tymi zasadami i wytycznymi, nasz zespół pomocy technicznej może nie być w stanie ci pomóc. Jeśli przestrzegasz wytycznych, wskazówek i zasad przedstawionych w tym artykule i nadal występują problemy z dostarczaniem na podstawie adresu IP wysyłania, postępuj zgodnie z instrukcjami, aby przesłać żądanie wyeksportowania listy. Aby uzyskać instrukcje, [zobacz Usuwanie](use-the-delist-portal-to-remove-yourself-from-the-office-365-blocked-senders-lis.md) siebie z listy zablokowanych nadawców za pomocą portalu delist.

## <a name="general-microsoft-policies"></a>Ogólne zasady firmy Microsoft

Wiadomości e-mail Microsoft 365 do użytkowników muszą być zgodne ze wszystkimi zasadami firmy Microsoft dotyczącymi przesyłania wiadomości e-mail i korzystania z Microsoft 365.

- Warunki świadczenia usług mające zastosowanie do Microsoft 365, w szczególności zakaz używania tych usług do spamu i rozpowszechniania złośliwego oprogramowania.

- [Umowa o świadczenie usług firmy Microsoft](https://www.microsoft.com/servicesagreement/)

## <a name="governmental-regulations"></a>Przepisy rządowe

Wiadomości e-mail wysyłane do Microsoft 365 muszą być zgodne ze wszystkimi obowiązującymi przepisami prawnymi i przepisami dotyczącymi komunikacji za pośrednictwem poczty e-mail w jurysdykcji właściwej.

- [CAN-SPAM Act: A Compliance Guide for Business](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business)

- [Odpowiedzi i obowiązki "Usuń mnie": Marketerzy poczty e-mail muszą chcieć, aby oświadczenia "Anuluj subskrypcję"](https://www.lawpublish.com/ftc-emai-marketers-unsubscribe-claims.html)

## <a name="technical-guidelines"></a>Wskazówki techniczne

Wiadomości e-mail wysyłane na Microsoft 365 powinny być zgodne z obowiązującymi zaleceniami wymienionymi w poniższych dokumentach (niektóre linki są dostępne tylko w języku angielskim).

- [RFC 2505: Ochrona przed spamem Rekomendacje dla serwerów MTA SMTP](https://www.ietf.org/rfc/rfc2505.txt)

- [RFC 2920: Rozszerzenie usługi SMTP dla przekazywania poleceń](https://www.ietf.org/rfc/rfc2920.txt)

Ponadto serwery poczty e-mail łączące się Microsoft 365 muszą spełniać następujące wymagania:

- Nadawca powinien przestrzegać wszystkich standardów technicznych dotyczących przekazywania internetowej poczty e-mail, opublikowanych przez internetową siły zadań inżynierskich (IETF), w tym RFC 5321, RFC 5322 i inne.

- Po podawać numeryczny kod odpowiedzi SERWERA SMTP od 500 do 599 (nazywany również trwałą odpowiedzią o niedostarczeniu lub raportem o niedostarczeniu), nadawca nie może podjąć próby ponownego przesłania tej wiadomości do tego adresata.

- Po wielu odpowiedziach o niedo dostarczenia nadawca musi przerwać dalsze próby wysłania wiadomości e-mail do tego adresata.

- Wiadomości nie mogą być przesyłane przez niezabezpieczone serwery proxy lub przekazywania poczty e-mail.

- Mechanizm niewysubskrybowania, zarówno z pojedynczych list, jak i wszystkich list hostowanych przez nadawcę, musi być wyraźnie udokumentowany i łatwy w znajdowaniu i używaniu przez adresatów.

- Połączenia z dynamicznej przestrzeni IP mogą nie być akceptowane.

- Serwery poczty e-mail muszą mieć prawidłowe odwrotne rekordy DNS.

## <a name="reputation-management"></a>Zarządzanie reputacją

Nadawcy, usługodawcy internetowego i inni dostawcy usług powinni aktywnie zarządzać reputacją adresów IP połączeń wychodzących.

## <a name="microsoft-365-limits"></a>Microsoft 365 limitów

Nadawcy muszą przestrzegać Microsoft 365 podanych w [Exchange Online Protection wiadomości.](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-limits)

## <a name="email-delivery-resources-and-organizations"></a>Zasoby i organizacje dotyczące dostarczania poczty e-mail

Firma Microsoft aktywnie współpracuje z podmiotami branżowymi i dostawcami usług w celu ulepszania internetu i poczty e-mail. Te organizacje opublikowały dokumenty najlepszych rozwiązań, które obsługujemy i zaleca się, aby ich nadawcy przestrzegali. To zwiększa możliwość dostarczania poczty e-mail wśród kilku dostawców usług poczty e-mail na całym świecie.

- [Grupa robocza ds. ochrony przed nadużyciami w aplikacji Malware Mobile do obsługi wiadomości](https://www.m3aawg.org/)

- [Online Trust Alliance](https://www.internetsociety.org/ota/)

- [Nadawca wiadomości e&- dostawca](https://www.espcoalition.org/)

## <a name="abuse-and-spam-reporting"></a>Zgłaszanie nadużyć i spamu

Aby zgłosić nielegalne, obraźliwe, niechciane lub złośliwe wiadomości e-mail, zobacz [Zgłaszanie wiadomości i plików do firmy Microsoft](report-junk-email-messages-to-microsoft.md). Wysłanie tych typów komunikacji jest naruszeniem zasad firmy Microsoft i zostanie wykonane odpowiednie działanie w przypadku potwierdzono raportów.

## <a name="law-enforcement"></a>Działania porządkowe

Jeśli jesteś członkiem organu prawnego i chcesz obsługiwać firmę Microsoft Corporation w dokumentacji prawnej dotyczącej programu Office 365 lub jeśli masz pytania dotyczące dokumentacji prawnej przesłanej do firmy Microsoft, zadzwoń pod numer (1) (425) 722-1299.