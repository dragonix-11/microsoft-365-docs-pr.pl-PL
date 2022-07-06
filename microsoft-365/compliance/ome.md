---
title: szyfrowanie komunikatów Office 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 02/07/2020
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.assetid: f87cb016-7876-4317-ae3c-9169b311ff8a
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się, jak wysyłać i odbierać zaszyfrowane wiadomości e-mail między osobami w organizacji i poza nią.
ms.openlocfilehash: 746a1cbb1d4fa5e98fb3fc3cbba529232178987c
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66640571"
---
# <a name="message-encryption"></a>Szyfrowanie komunikatów

Osoby często używają poczty e-mail do wymiany poufnych informacji, takich jak dane finansowe, umowy prawne, poufne informacje o produkcie, raporty sprzedaży i prognozy, informacje o kondycji pacjenta lub informacje o klientach i pracownikach. W związku z tym skrzynki pocztowe mogą stać się repozytoriami dla dużych ilości potencjalnie poufnych informacji, a wyciek informacji może stać się poważnym zagrożeniem dla organizacji.

Dzięki Office 365 szyfrowaniu wiadomości organizacja może wysyłać i odbierać zaszyfrowane wiadomości e-mail między osobami w organizacji i poza nią. Office 365 szyfrowanie wiadomości współpracuje z usługami Outlook.com, Yahoo!, Gmail i innymi usługami poczty e-mail. Szyfrowanie wiadomości e-mail pomaga zapewnić, że tylko zamierzoni adresaci mogą wyświetlać zawartość wiadomości.

## <a name="how-message-encryption-works"></a>Jak działa szyfrowanie komunikatów

Pozostała część tego artykułu dotyczy Szyfrowanie wiadomości w Microsoft Purview.

Szyfrowanie wiadomości w Microsoft Purview to usługa online oparta na usłudze Microsoft Azure Rights Management (Azure RMS), która jest częścią usługi Azure Information Protection. Ta usługa obejmuje zasady szyfrowania, tożsamości i autoryzacji, które ułatwiają zabezpieczanie poczty e-mail. Komunikaty można szyfrować przy użyciu szablonów zarządzania prawami, [opcji Nie przesyłaj dalej](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails) i [opcji tylko do szyfrowania](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

Użytkownicy mogą następnie szyfrować wiadomości e-mail i różne załączniki przy użyciu tych opcji. Aby uzyskać pełną listę obsługiwanych typów załączników, zobacz ["Typy plików objęte zasadami IRM, gdy są dołączane do komunikatów" w temacie Wprowadzenie do usługi IRM dla wiadomości e-mail](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM).

Jako administrator możesz również zdefiniować reguły przepływu poczty, aby zastosować tę ochronę. Można na przykład utworzyć regułę, która wymaga szyfrowania wszystkich komunikatów skierowanych do określonego adresata lub zawierających określone słowa w wierszu tematu, a także określić, że adresaci nie mogą kopiować ani drukować zawartości wiadomości.

W przeciwieństwie do poprzedniej wersji OME nowe możliwości zapewniają ujednolicone środowisko nadawcy, niezależnie od tego, czy wysyłasz pocztę w organizacji, czy do adresatów spoza platformy Microsoft 365. Ponadto adresaci, którzy otrzymują chronioną wiadomość e-mail wysłaną na konto usługi Microsoft 365 w Outlook 2016 lub Outlook w sieci Web, nie muszą podejmować żadnych innych działań w celu wyświetlenia wiadomości. Działa bezproblemowo. Adresaci korzystający z innych klientów poczty e-mail i dostawców usług poczty e-mail również mają ulepszone środowisko. Aby uzyskać informacje, zobacz [Informacje o chronionych komunikatach w Office 365](https://support.office.com/article/Learn-about-protected-messages-in-Office-365-2baf3ac7-12db-40a4-8af7-1852204b4b67) i [Jak mogę otwierania chronionej wiadomości](https://support.office.com/article/How-do-I-open-a-protected-message-1157a286-8ecc-4b1e-ac43-2a608fbf3098).

Aby uzyskać szczegółową listę różnic między poprzednią wersją protokołu OME i Szyfrowanie wiadomości w Microsoft Purview, zobacz [Porównanie wersji szyfrowania komunikatów](ome-version-comparison.md).

Gdy ktoś wyśle wiadomość e-mail zgodną z regułą przepływu poczty szyfrowania, wiadomość zostanie zaszyfrowana przed jej wysłaniem. Wszyscy użytkownicy końcowi platformy Microsoft 365, którzy używają klientów programu Outlook do odczytywania poczty, otrzymują natywne, najwyższej klasy środowiska do odczytu zaszyfrowanej i chronionej prawami poczty, nawet jeśli nie znajdują się w tej samej organizacji co nadawca. Do obsługiwanych klientów programu Outlook należą programy Outlook Desktop, Outlook Mac, Outlook mobile w systemach iOS i Android oraz Outlook w sieci Web (wcześniej znane jako Outlook Web App).

Adresaci zaszyfrowanych wiadomości, którzy odbierają zaszyfrowaną lub chronioną prawami pocztę wysłaną na swoje konta Outlook.com, Gmail i Yahoo, otrzymują wiadomość e-mail z otoką, która kieruje je do portalu OME, gdzie mogą łatwo uwierzytelniać się przy użyciu konta Microsoft, gmaila lub poświadczeń Yahoo.

Użytkownicy końcowi, którzy odczytują zaszyfrowaną lub chronioną prawami pocztę na klientach innych niż Outlook, używają również portalu OME do wyświetlania wiadomości zaszyfrowanych i chronionych prawami, które otrzymują.

Jeśli nadawca chronionej poczty znajduje się w GCC High, a adresat znajduje się poza GCC High, w tym użytkowników komercyjnych, użytkowników Outlook.com i użytkowników innych dostawców poczty e-mail, takich jak Gmail, adresat otrzymuje wiadomość e-mail otoki. Wiadomość e-mail otoki kieruje adresata do portalu OME, gdzie adresat może odczytać wiadomość i odpowiedzieć na nią. W przeciwnym razie, jeśli nadawca i adresat znajdują się w środowisku GCC High, nawet jeśli nie należą do tej samej organizacji, adresaci, którzy używają klientów programu Outlook do odczytywania poczty, otrzymują natywne, najwyższej klasy środowiska odczytu dla zaszyfrowanej i chronionej prawami poczty. Aby uzyskać więcej informacji na temat różnych środowisk w GCC High, zobacz [Porównanie wersji OME](ome-version-comparison.md).

Aby uzyskać więcej informacji na temat limitów rozmiaru komunikatów i załączników, które można szyfrować przy użyciu protokołu OME, zobacz [Exchange Online Limity](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits).

## <a name="how-microsoft-purview-advanced-message-encryption-works-on-top-of-microsoft-purview-message-encryption"></a>Jak działa zaawansowane szyfrowanie komunikatów w usłudze Microsoft Purview na Szyfrowanie wiadomości w Microsoft Purview

Zaawansowane szyfrowanie komunikatów usługi Microsoft Purview umożliwia tworzenie wielu szablonów znakowania, dzięki czemu można dostosować kontrolę nad pocztą adresatów i utworzyć niestandardowe środowiska znakowania w celu obsługi zróżnicowanej struktury organizacyjnej.

Zaawansowane szyfrowanie komunikatów w usłudze Microsoft 365 pomaga spełnić wymagania dotyczące zgodności, które wymagają bardziej elastycznej kontroli nad dostępem adresata zewnętrznego do zaszyfrowanych wiadomości e-mail. Dzięki zaawansowanemu szyfrowaniu komunikatów jako administrator możesz kontrolować poufne wiadomości e-mail udostępniane poza organizacją za pomocą automatycznych zasad wykrywania poufnych typów informacji (na przykład identyfikatorów pii, finansowych lub zdrowotnych) lub słów kluczowych w celu zwiększenia ochrony poprzez wygaśnięcie dostępu za pośrednictwem bezpiecznego portalu internetowego do zaszyfrowanych wiadomości e-mail. Jako administrator możesz dodatkowo kontrolować zaszyfrowane wiadomości e-mail dostępne za pośrednictwem portalu internetowego, cofając dostęp do wiadomości e-mail w dowolnym momencie.

Odwoływanie i wygasanie wiadomości działa tylko w przypadku wiadomości e-mail wysyłanych przez użytkowników do adresatów spoza organizacji. Ponadto adresaci muszą uzyskać dostęp do wiadomości e-mail za pośrednictwem portalu internetowego. Aby upewnić się, że adresat korzysta z portalu do odbierania wiadomości e-mail, należy skonfigurować niestandardowy szablon znakowania, który stosuje otokę. Następnie zastosujesz szablon znakowania w regule przepływu poczty. Aby uzyskać więcej informacji na temat zaawansowanego szyfrowania komunikatów, zobacz [Zaawansowane szyfrowanie komunikatów](ome-advanced-message-encryption.md).

## <a name="defining-rules-for-microsoft-purview-message-encryption"></a>Definiowanie reguł dla Szyfrowanie wiadomości w Microsoft Purview

Jednym ze sposobów włączenia Szyfrowanie wiadomości w Microsoft Purview jest zdefiniowanie reguł przepływu poczty przez administratorów Exchange Online i Exchange Online Protection. Te reguły określają, w jakich warunkach wiadomości e-mail powinny być szyfrowane. Po ustawieniu akcji szyfrowania dla reguły wszystkie komunikaty zgodne z warunkami reguły są szyfrowane przed ich wysłaniem.

Reguły przepływu poczty są elastyczne, co umożliwia łączenie warunków, dzięki czemu można spełnić określone wymagania dotyczące zabezpieczeń w jednej regule. Można na przykład utworzyć regułę szyfrowania wszystkich komunikatów zawierających określone słowa kluczowe i adresowanych do adresatów zewnętrznych. Szyfrowanie wiadomości w Microsoft Purview również szyfrować odpowiedzi od adresatów zaszyfrowanej wiadomości e-mail.

Aby uzyskać więcej informacji na temat sposobu tworzenia reguł przepływu poczty w celu skorzystania z Szyfrowanie wiadomości w Microsoft Purview, zobacz [Definiowanie reguł przepływu poczty w celu szyfrowania wiadomości e-mail](define-mail-flow-rules-to-encrypt-email.md).

## <a name="get-started-with-the-microsoft-purview-message-encryption"></a>Wprowadzenie do Szyfrowanie wiadomości w Microsoft Purview

Jeśli wszystko jest gotowe do rozpoczęcia korzystania z Szyfrowanie wiadomości w Microsoft Purview w organizacji, zobacz [Konfigurowanie Szyfrowanie wiadomości w Microsoft Purview](set-up-new-message-encryption-capabilities.md).

## <a name="sending-viewing-and-replying-to-encrypted-email-messages"></a>Wysyłanie, wyświetlanie i odpowiadanie na zaszyfrowane wiadomości e-mail

Dzięki Szyfrowanie wiadomości w Microsoft Purview użytkownicy mogą wysyłać zaszyfrowane wiadomości e-mail z programu Outlook i Outlook w sieci Web. Ponadto administratorzy mogą skonfigurować reguły przepływu poczty w usłudze Microsoft 365 w celu automatycznego szyfrowania wiadomości e-mail na podstawie dopasowania słów kluczowych lub innych warunków.

Adresaci zaszyfrowanych wiadomości należących do organizacji będą mogli bezproblemowo odczytywać te komunikaty w dowolnej wersji programu Outlook, w tym w programie Outlook dla komputerów PC, Outlook dla komputerów Mac, Outlook w sieci Web, Outlook dla systemu iOS i Outlook dla systemu Android. Użytkownicy odbierający zaszyfrowane wiadomości na innych klientach poczty e-mail mogą wyświetlać wiadomości w portalu OME.

Aby uzyskać szczegółowe wskazówki dotyczące wysyłania i wyświetlania zaszyfrowanych komunikatów, zapoznaj się z tymi artykułami.

|Przeczytaj ten artykuł...|Jeśli jesteś...|
|:-----|:-----|
|[Dowiedz się więcej o chronionych komunikatach w Office 365](https://support.office.com/article/2baf3ac7-12db-40a4-8af7-1852204b4b67.aspx)|Użytkownik końcowy, który chce dowiedzieć się więcej o tym, jak działają zaszyfrowane komunikaty i jakie opcje są dostępne dla Ciebie.|
|[Jak mogę otworzyć chroniony komunikat?](https://support.office.com/article/1157a286-8ecc-4b1e-ac43-2a608fbf3098.aspx)|Użytkownik końcowy, który chce odczytać wiadomość chronioną, która została do Ciebie wysłana. Ten artykuł zawiera informacje o odczytywaniu wiadomości w kilku wersjach programu Outlook i z różnych kont e-mail, w tym tych kont spoza platformy Microsoft 365, takich jak gmail i Yahoo! Konta.|
|[Wysyłanie, wyświetlanie i odpowiadanie na zaszyfrowane wiadomości w programie Outlook](https://support.microsoft.com/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980)|Użytkownik końcowy, który chce wysyłać, wyświetlać lub odpowiadać na zaszyfrowaną wiadomość z programu Outlook. Nawet jeśli nie jesteś członkiem organizacji, nadal otrzymujesz powiadomienie o zaszyfrowanych wiadomościach wysłanych do Ciebie w programie Outlook. Skorzystaj z tego artykułu, aby uzyskać instrukcje dotyczące wyświetlania zaszyfrowanych wiadomości wysyłanych z Office 365 i odpowiadania na nie.|
|[Wysyłanie wiadomości podpisanej cyfrowo lub zaszyfrowanej](https://support.microsoft.com/office/send-a-digitally-signed-or-encrypted-message-a18ecf7f-a7ac-4edd-b02e-687b05eff547)|Użytkownik końcowy, który chce wysyłać, wyświetlać lub odpowiadać na zaszyfrowane wiadomości przy użyciu Outlook dla komputerów Mac. W tym artykule opisano również używanie metod szyfrowania innych niż OME, takich jak S/MIME.|
|[Wyświetlanie zaszyfrowanych komunikatów na urządzeniu z systemem Android](https://support.office.com/article/83d60f17-2305-407a-a762-7d518401fdeb)|Użytkownik końcowy, który otrzymał wiadomość zaszyfrowaną za pomocą Office 365 szyfrowania komunikatów na urządzeniu z systemem Android, możesz użyć bezpłatnej aplikacji OME Viewer, aby wyświetlić komunikat i wysłać zaszyfrowaną odpowiedź. W tym artykule wyjaśniono, jak to zrobić.|
|[Wyświetlanie zaszyfrowanych wiadomości na telefonie iPhone lub urządzeniu iPad](https://support.microsoft.com/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf)|Użytkownik końcowy, który otrzymał wiadomość zaszyfrowaną za pomocą Office 365 szyfrowania komunikatów na telefonie iPhone lub iPadzie, możesz użyć bezpłatnej aplikacji OME Viewer, aby wyświetlić komunikat i wysłać zaszyfrowaną odpowiedź. W tym artykule wyjaśniono, jak to zrobić.|
||
