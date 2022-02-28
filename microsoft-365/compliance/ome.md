---
title: Szyfrowanie wiadomości
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
ms.openlocfilehash: 04c2ddd3bfb77199f924a10e29f23dc3d27cc38b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986424"
---
# <a name="message-encryption"></a>Szyfrowanie wiadomości

Za pomocą poczty e-mail często wymienia się informacjami poufnymi, takimi jak dane finansowe, umowy prawne, poufne informacje o produktach, raporty sprzedaży i projekcje, informacje o stanie zdrowia pacjentów lub informacje o klientach i pracownikach. W wyniku tego skrzynki pocztowe mogą stać się repozytoriami dużych ilości potencjalnie poufnych informacji i wycieków informacji, które mogą stanowić poważne zagrożenie dla organizacji.

Dzięki Szyfrowanie wiadomości usługi Office 365 Twoja organizacja może wysyłać i odbierać zaszyfrowane wiadomości e-mail między osobami w organizacji i poza nią. Szyfrowanie wiadomości usługi Office 365 z usługami Outlook.com, Yahoo!, Gmail i innymi usługami poczty e-mail. Szyfrowanie wiadomości e-mail pozwala zagwarantować, że tylko zamierzony adresaci mogą wyświetlać zawartość wiadomości.

## <a name="how-office-365-message-encryption-works"></a>Jak Szyfrowanie wiadomości usługi Office 365 działa

Pozostała część tego artykułu dotyczy nowych funkcji OME.

Szyfrowanie wiadomości usługi Office 365 to usługa online wbudowana w usługę Microsoft Azure rights Management (Azure RMS), która jest częścią usługi Azure Information Protection. Ta usługa obejmuje zasady szyfrowania, tożsamości i autoryzacji, które ułatwiają zabezpieczanie poczty e-mail. Wiadomości można szyfrować przy użyciu szablonów zarządzania prawami dostępu, opcji [Nie](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails) przesyłaj dalej i opcji [tylko do szyfrowania](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

Za pomocą tych opcji użytkownicy mogą szyfrować wiadomości e-mail i różne załączniki. Aby uzyskać pełną listę obsługiwanych typów załączników, zobacz "Typy plików objęte zasadami usługi IRM w przypadku ich dołączenia do wiadomości" w tece Wprowadzenie do usługi [IRM dla wiadomości e-mail](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM).

Jako administrator możesz również zdefiniować reguły przepływu poczty e-mail, aby zastosować tę ochronę. Można na przykład utworzyć regułę wymaganą szyfrowania wszystkich wiadomości zaadresowanych do określonego adresata lub zawierającej określone wyrazy w wierszu tematu, a także określić, że adresaci nie mogą kopiować ani drukować zawartości wiadomości.

W przeciwieństwie do poprzedniej wersji OME nowe funkcje zapewniają ujednolicone środowisko nadawców, niezależnie od tego, czy wysyłasz pocztę wewnątrz organizacji, czy do adresatów spoza Microsoft 365. Ponadto adresaci, którzy otrzymają chronioną wiadomość e-mail wysłaną na konto Microsoft 365 w programie Outlook 2016 lub Outlook w sieci Web, nie muszą nic więcej zrobić, aby wyświetlić wiadomość. Działa to bezproblemowo. Adresaci korzystający z innych klientów poczty e-mail i dostawców usług poczty e-mail mają również ulepszone środowisko. Aby uzyskać informacje, zobacz [Informacje o chronionych](https://support.office.com/article/Learn-about-protected-messages-in-Office-365-2baf3ac7-12db-40a4-8af7-1852204b4b67) Office 365 [wiadomościach i Jak otworzyć chronioną wiadomość](https://support.office.com/article/How-do-I-open-a-protected-message-1157a286-8ecc-4b1e-ac43-2a608fbf3098).

Aby uzyskać szczegółową listę różnic między poprzednią wersją OME a nowymi możliwościami OME, zobacz [Porównanie wersji OME](ome-version-comparison.md).

Gdy ktoś wyśle wiadomość e-mail, która jest inna niż reguła przepływu poczty szyfrowania, wiadomość jest szyfrowana przed jej wysłaniem. Wszyscy Microsoft 365 korzystający z klientów Outlook do czytania poczty otrzymują natywne środowisko odczytu pierwszej klasy dla zaszyfrowanej i chronionej prawami poczty, nawet jeśli nie należy do tej samej organizacji, co nadawca. Obsługiwane Outlook to komputer Outlook, Outlook Mac, Outlook dla urządzeń przenośnych z systemami iOS i Android oraz Outlook w sieci Web (wcześniej znany jako Outlook Web App).

Adresaci zaszyfrowanych wiadomości, które odbierają zaszyfrowaną lub chronioną prawami pocztę wysłaną na ich konta w usługach Outlook.com, Gmail i Yahoo, otrzymują wiadomość zawijaną, która przekieruje ich do portalu OME, w którym mogą łatwo uwierzytelniać się za pomocą poświadczeń konta Microsoft, Gmail lub Yahoo.

Użytkownicy końcowi, którzy odczytują zaszyfrowaną lub chronioną prawami pocztę w klientach innych niż Outlook używają również portalu OME do wyświetlania obierania zaszyfrowanych i chronionych prawami wiadomości.

Jeśli nadawca chronionej poczty znajduje się w usłudze GCC Wysoka, a adresat znajduje się poza obszarem GCC Wysoka, w tym także użytkownicy komercyjni, użytkownicy usługi Outlook.com i użytkownicy innych dostawców poczty e-mail, takich jak Gmail, adresat otrzymuje wiadomość zawijaną. Wiadomość zawijacza przekierowywuje adresata do portalu OME, w którym adresat może odczytać wiadomość i odpowiedzieć na nie. W przeciwnym razie, jeśli nadawca i adresat znajdują się w środowisku wysokiego poziomu GCC, nawet jeśli znajdują się w tej samej organizacji, adresaci, którzy używają klientów programu Outlook do czytania poczty, otrzymują natywne środowiska odczytu pierwszej klasy dla zaszyfrowanej i chronionej prawami poczty. Aby uzyskać więcej informacji na temat różnych wersji programu GCC, zobacz [Porównanie wersji aplikacji OME](ome-version-comparison.md).

Aby uzyskać więcej informacji o limitach rozmiaru wiadomości i załączników, które można szyfrować przy użyciu OME, zobacz Limity Exchange Online [wiadomości](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits).

## <a name="how-office-365-advanced-message-encryption-works-on-top-of-ome"></a>Jak Zaawansowane szyfrowanie wiadomości usługi Office 365 działa nad OME

Zaawansowane szyfrowanie wiadomości usługi Office 365 umożliwia tworzenie wielu szablonów marki w celu dostosowywania kontroli nad pocztą adresatów oraz tworzenia niestandardowych środowisk  marki w celu obsługi różnych struktur organizacyjnych.

Zaawansowane szyfrowanie wiadomości w Microsoft 365 ułatwia spełnienie wymagań dotyczących zgodności, które wymagają bardziej elastycznej kontroli nad dostępem adresatów zewnętrznych do zaszyfrowanych wiadomości e-mail. Dzięki funkcji zaawansowanego szyfrowania wiadomości w użytce Office 365 jako administrator możesz sterować poufnymi wiadomościami e-mail udostępnianymi poza organizacją przy użyciu automatycznych zasad wykrywających poufne typy informacji (na przykład identyfikatory PII, identyfikatory finansowe lub identyfikatory kondycji) lub słowa kluczowe w celu zwiększenia ochrony, wygasając dostęp za pośrednictwem bezpiecznego portalu sieci Web do zaszyfrowanych wiadomości e-mail. Jako administrator możesz dodatkowo kontrolować zaszyfrowane wiadomości e-mail uzyskiwane za pośrednictwem Microsoft 365 sieci Web przez odwołanie dostępu do wiadomości e-mail w dowolnym momencie.

Odwołania i wygasanie wiadomości działają tylko w przypadku wiadomości e-mail wysyłanych przez użytkowników do adresatów spoza organizacji. Ponadto adresaci muszą uzyskać dostęp do wiadomości e-mail za pośrednictwem portalu sieci Web. Aby upewnić się, że adresat odbierze wiadomość e-mail za pomocą portalu, należy skonfigurować niestandardowy szablon  marki, który stosuje zawijanie. Następnie zastosuj szablon  marki w  regułę przepływu poczty e-mail. Aby uzyskać więcej informacji na temat zaawansowanego szyfrowania wiadomości, [zobacz Zaawansowane szyfrowanie wiadomości usługi Office 365](ome-advanced-message-encryption.md).

## <a name="defining-rules-for-office-365-message-encryption"></a>Definiowanie reguł dla Szyfrowanie wiadomości usługi Office 365

Jednym ze sposobów na włączenie nowych możliwości obsługi poczty e-Szyfrowanie wiadomości usługi Office 365 administratorom poczty Exchange Online i administratorom Exchange Online Protection definiowanie reguł przepływu poczty e-mail. Te reguły określają, na jakich warunkach wiadomości e-mail powinny być szyfrowane. Gdy dla reguły jest ustawiona akcja szyfrowania, wszystkie wiadomości zgodne z warunkami reguły są szyfrowane przed ich wysłaniem.

Elastyczne reguły przepływu poczty e-mail pozwalającą łączyć warunki, dzięki czemu można spełnić określone wymagania dotyczące zabezpieczeń w ramach jednej reguły. Można na przykład utworzyć regułę szyfrowania wszystkich wiadomości zawierających określone słowa kluczowe i zaadresowanych do adresatów zewnętrznych. Nowe funkcje do Szyfrowanie wiadomości usługi Office 365 także szyfrować odpowiedzi od adresatów zaszyfrowanych wiadomości e-mail.

Aby uzyskać więcej informacji na temat tworzenia reguł przepływu poczty e-mail w celu skorzystania z nowych funkcji OME, zobacz Definiowanie [reguł dla Szyfrowanie wiadomości usługi Office 365](define-mail-flow-rules-to-encrypt-email.md).

## <a name="get-started-with-the-new-ome-capabilities"></a>Wprowadzenie do nowych funkcji OME

Jeśli chcesz rozpocząć korzystanie z nowych funkcji usługi OME w organizacji, zobacz Konfigurowanie nowych funkcji Szyfrowanie wiadomości usługi Office 365 [danych](set-up-new-message-encryption-capabilities.md).

## <a name="sending-viewing-and-replying-to-encrypted-email-messages"></a>Wysyłanie, wyświetlanie i odpowiadanie na zaszyfrowane wiadomości e-mail

Dzięki Szyfrowanie wiadomości usługi Office 365 użytkownicy mogą wysyłać zaszyfrowane wiadomości e-mail Outlook i Outlook w sieci Web. Ponadto administratorzy mogą skonfigurować reguły przepływu poczty e-mail Microsoft 365 automatyczne szyfrowanie wiadomości e-mail na podstawie dopasowania słów kluczowych lub innych warunków.

Adresaci zaszyfrowanych wiadomości w organizacjach będą mogli bezproblemowo odczytać te wiadomości w dowolnej wersji pakietu Outlook, w tym w Outlook dla komputerów PC, Outlook dla komputerów Mac, Outlook w sieci Web, Outlook dla systemu iOS i Outlook dla systemu Android. Użytkownicy, którzy otrzymują zaszyfrowane wiadomości w innych klientach poczty e-mail, mogą wyświetlać te wiadomości w portalu OME.

Aby uzyskać szczegółowe informacje na temat wysyłania i wyświetlania zaszyfrowanych wiadomości, skorzystaj z tych artykułów.

|Przeczytaj ten artykuł...|Jeśli...|
|:-----|:-----|
|[Informacje o chronionych wiadomościach w programie Office 365](https://support.office.com/article/2baf3ac7-12db-40a4-8af7-1852204b4b67.aspx)|Użytkownik końcowy, który chce dowiedzieć się więcej na temat działania zaszyfrowanych wiadomości i dostępnych opcji.|
|[Jak otworzyć chronioną wiadomość?](https://support.office.com/article/1157a286-8ecc-4b1e-ac43-2a608fbf3098.aspx)|Użytkownik końcowy, który chce przeczytać chronioną wiadomość, która została do Ciebie wysłana. Ten artykuł zawiera informacje na temat czytania wiadomości w kilku wersjach programu Outlook i z różnych kont e-mail, w tym z kont spoza firmy Microsoft 365 na przykład Gmail i Yahoo! .|
|[Wysyłanie i wyświetlanie zaszyfrowanych wiadomości oraz odpowiadanie na nie w aplikacji Outlook](https://support.microsoft.com/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980)|Użytkownik końcowy, który chce wysyłać, wyświetlać i odpowiadać na zaszyfrowaną wiadomość z Outlook. Nawet jeśli nie jesteś członkiem organizacji, nadal otrzymujesz powiadomienia o zaszyfrowanych wiadomościach wysyłanych do Ciebie w aplikacji Outlook. Ten artykuł zawiera instrukcje dotyczące wyświetlania zaszyfrowanych wiadomości wysłanych z aplikacji i odpowiadania na nie Office 365.|
|[Wysyłanie wiadomości podpisanej cyfrowo lub zaszyfrowanej](https://support.microsoft.com/office/send-a-digitally-signed-or-encrypted-message-a18ecf7f-a7ac-4edd-b02e-687b05eff547)|Użytkownik końcowy, który chce wysyłać, wyświetlać i odpowiadać na zaszyfrowane wiadomości przy użyciu Outlook dla komputerów Mac. W tym artykule o mowa również, jak używać metod szyfrowania innych niż OME, takich jak S/MIME.|
|[Wyświetlanie zaszyfrowanych wiadomości na urządzeniu z systemem Android](https://support.office.com/article/83d60f17-2305-407a-a762-7d518401fdeb)|Użytkownik końcowy, który otrzymał wiadomość zaszyfrowaną za pomocą Szyfrowanie wiadomości usługi Office 365 na urządzeniu z systemem Android, może użyć bezpłatnej aplikacji Przeglądarka OME do wyświetlenia wiadomości i wysłania zaszyfrowanej odpowiedzi. W tym artykule wyjaśniono, jak to zrobić.|
|[Wyświetlanie zaszyfrowanych wiadomości na iPhone lub iPad](https://support.microsoft.com/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf)|Użytkownik końcowy, który otrzymał wiadomość zaszyfrowaną za pomocą programu Szyfrowanie wiadomości usługi Office 365 na Twoim komputerze iPhone lub iPad, może wyświetlić wiadomość i wysłać zaszyfrowaną odpowiedź za pomocą bezpłatnej aplikacji Przeglądarka OME. W tym artykule wyjaśniono, jak to zrobić.|
||