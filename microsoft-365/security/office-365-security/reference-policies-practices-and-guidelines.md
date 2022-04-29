---
title: Zasady referencyjne, praktyki i wytyczne
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
description: Firma Microsoft opracowała różne zasady, procedury i przyjęła kilka najlepszych rozwiązań branżowych, aby chronić naszych użytkowników przed obraźliwymi, niepożądanymi lub złośliwymi wiadomościami e-mail.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 815fea8981fdab8825a109dae69abaf8232997f9
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130368"
---
# <a name="reference-policies-practices-and-guidelines"></a>Dokumentacja: zasady, praktyki i wytyczne

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Firma Microsoft jest przeznaczona do zapewniania najbardziej zaufanego środowiska użytkownika w Internecie. W związku z tym firma Microsoft opracowała różne zasady, procedury i przyjęła kilka najlepszych rozwiązań branżowych, aby chronić naszych użytkowników przed obraźliwymi, niepożądanymi lub złośliwymi wiadomościami e-mail. Nadawcy próbujący wysłać wiadomość e-mail do użytkowników powinni upewnić się, że w pełni rozumieją i postępują zgodnie ze wskazówkami w tym artykule, aby pomóc w tym wysiłku i uniknąć potencjalnych problemów z dostarczaniem.

Jeśli nie przestrzegasz tych zasad i wytycznych, nasz zespół pomocy technicznej może nie być w stanie Ci pomóc. Jeśli przestrzegasz wytycznych, praktyk i zasad przedstawionych w tym artykule i nadal występują problemy z dostarczaniem na podstawie twojego adresu IP wysyłania, wykonaj kroki, aby przesłać żądanie usunięcia z listy. Aby uzyskać instrukcje, zobacz [Usuwanie siebie z listy zablokowanych nadawców za pomocą portalu delist](use-the-delist-portal-to-remove-yourself-from-the-office-365-blocked-senders-lis.md).

## <a name="general-microsoft-policies"></a>Ogólne zasady firmy Microsoft

Wiadomość e-mail wysłana do użytkowników Microsoft 365 musi być zgodna ze wszystkimi zasadami firmy Microsoft dotyczącymi transmisji wiadomości e-mail i korzystania z Microsoft 365.

- Warunki świadczenia usług mające zastosowanie do Microsoft 365, w szczególności zakaz używania usługi do spamowania lub rozpowszechniania złośliwego oprogramowania.

- [Umowa o świadczenie usług firmy Microsoft](https://www.microsoft.com/servicesagreement/)

## <a name="governmental-regulations"></a>Regulacje rządowe

Wiadomość e-mail wysłana do użytkowników Microsoft 365 musi być zgodna ze wszystkimi obowiązującymi przepisami i przepisami dotyczącymi komunikacji e-mail w odpowiedniej jurysdykcji.

- [Can-SPAM Act: Przewodnik zgodności dla firm](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business)

- ["Usuń mnie" Odpowiedzi i obowiązki: Marketerzy poczty e-mail muszą honorować oświadczenia "Anuluj subskrypcję"](https://www.lawpublish.com/ftc-emai-marketers-unsubscribe-claims.html)

## <a name="technical-guidelines"></a>Wytyczne techniczne

Wiadomość e-mail wysłana do Microsoft 365 powinna być zgodna z odpowiednimi zaleceniami wymienionymi w poniższych dokumentach (niektóre linki są dostępne tylko w języku angielskim).

- [RFC 2505: Rekomendacje antyspamowe dla mtas SMTP](https://www.ietf.org/rfc/rfc2505.txt)

- [RFC 2920: Rozszerzenie usługi SMTP na potrzeby potokowania poleceń](https://www.ietf.org/rfc/rfc2920.txt)

Ponadto serwery poczty e-mail łączące się z Microsoft 365 muszą spełniać następujące wymagania:

- Nadawca ma spełniać wszystkie standardy techniczne dotyczące transmisji internetowej poczty e-mail, opublikowane przez Internet Society's Internet Engineering Task Force (IETF), w tym RFC 5321, RFC 5322 i inne.

- Po podaniu numerycznego kodu odpowiedzi na błąd SMTP z zakresu od 500 do 599 (znanego również jako odpowiedź bez dostarczenia lub NDR) nadawca nie może próbować ponownie przetransmitować tej wiadomości do tego adresata.

- Po wielu odpowiedziach niezwiązanych z dostarczaniem nadawca musi zaprzestać dalszych prób wysłania wiadomości e-mail do tego adresata.

- Komunikaty nie mogą być przesyłane za pośrednictwem niezabezpieczonej poczty e-mail lub serwerów proxy.

- Mechanizm anulowania subskrypcji z poszczególnych list lub wszystkich list hostowanych przez nadawcę musi być wyraźnie udokumentowany i łatwy do znalezienia i użycia przez adresatów.

- Połączenia z dynamicznej przestrzeni IP mogą nie być akceptowane.

- Serwery poczty e-mail muszą mieć prawidłowe odwrotne rekordy DNS.

## <a name="reputation-management"></a>Zarządzanie reputacją

Nadawcy, dostawcy usług i inni dostawcy usług powinni aktywnie zarządzać reputacją wychodzących adresów IP.

## <a name="microsoft-365-limits"></a>limity Microsoft 365

Nadawcy muszą przestrzegać limitów Microsoft 365 wymienionych w [Exchange Online Protection Limity](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-limits).

## <a name="email-delivery-resources-and-organizations"></a>Zasoby i organizacje dostarczania wiadomości e-mail

Firma Microsoft aktywnie współpracuje z organizacjami branżowymi i dostawcami usług w celu poprawy ekosystemu internetu i poczty e-mail. Te organizacje opublikowały dokumenty najlepszych rozwiązań, które obsługujemy i zalecamy, aby nadawcy się przestrzegali. Zwiększa to możliwość dostarczania wiadomości e-mail między kilkoma dostawcami usług poczty e-mail na całym świecie.

- [Grupa robocza ochrony przed nadużyciami w usłudze Messaging Malware Mobile](https://www.m3aawg.org/)

- [Sojusz zaufania online](https://www.internetsociety.org/ota/)

- [Koalicja dostawcy & nadawcy wiadomości e-mail](https://www.espcoalition.org/)

## <a name="abuse-and-spam-reporting"></a>Zgłaszanie nadużyć i spamu

Aby zgłosić niezgodną z prawem, obraźliwą, niepożądaną lub złośliwą wiadomość e-mail, zobacz [Zgłaszanie wiadomości i plików do firmy Microsoft](report-junk-email-messages-to-microsoft.md). Wysyłanie tego typu komunikacji jest naruszeniem zasad firmy Microsoft, a w przypadku potwierdzonych raportów zostaną podjęte odpowiednie działania.

## <a name="law-enforcement"></a>Ścigania

Jeśli jesteś członkiem organów ścigania i chcesz udostępnić firmie Microsoft Corporation dokumentację prawną dotyczącą Office 365 lub jeśli masz pytania dotyczące dokumentacji prawnej przesłanej firmie Microsoft, zadzwoń pod numer (1) (425) 722-1299.
