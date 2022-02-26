---
title: Szyfrowanie wiadomości e-mail w Microsoft 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 8/28/2019
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ms.assetid: c0d87cbe-6d65-4c03-88ad-5216ea5564e8
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
description: Porównaj Microsoft 365 szyfrowaniem, w tym Szyfrowanie wiadomości usługi Office 365 (OME), S/MIME, Zarządzanie prawami do informacji (IRM, Information Rights Management) i dowiedz się więcej o zabezpieczeniach Transport Layer Security (TLS).
ms.openlocfilehash: 1d6ad4f595652b39ff6e984afe096272a7920c4d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973674"
---
# <a name="email-encryption"></a>Szyfrowanie wiadomości e-mail

W tym artykule porównano opcje szyfrowania w programach Microsoft 365, w tym Szyfrowanie wiadomości usługi Office 365 (OME), S/MIME, Information Rights Management (IRM) i wprowadzono szyfrowanie TLS (Transport Layer Security).
  
Microsoft 365 udostępnia wiele opcji szyfrowania, które pomogą Ci sprostać potrzebom biznesowym w zakresie zabezpieczeń poczty e-mail. Ten artykuł zawiera trzy sposoby szyfrowania wiadomości e-mail w Office 365. Aby dowiedzieć się więcej o wszystkich funkcjach zabezpieczeń w programie Office 365, odwiedź centrum Office 365 [zaufania](https://go.microsoft.com/fwlink/p/?LinkID=282470). W tym artykule oprowadzono trzy typy szyfrowania dostępne dla administratorów Microsoft 365, które ułatwiają zabezpieczanie poczty e-mail w Office 365:
  
- Office szyfrowania wiadomości (OME).

- Rozszerzenia S/MIME (Secure/Multipurpose Internet Mail Extensions).

- Zarządzanie prawami do informacji (IRM).

## <a name="how-microsoft-365-uses-email-encryption"></a>Jak Microsoft 365 korzysta z szyfrowania poczty e-mail

Szyfrowanie to proces, w którym informacje są kodowane, dzięki czemu tylko autoryzowany adresat może je dekodować i z nich korzystać. Microsoft 365 stosuje szyfrowanie na dwa sposoby: w usłudze i jako kontrolę klienta. W usłudze szyfrowanie jest domyślnie używane Microsoft 365, nie trzeba nic konfigurować. Za Microsoft 365 TLS (Transport Layer Security) można na przykład zaszyfrować połączenie (czyli sesję) między dwoma serwerami. 
  
Oto jak zwykle działa szyfrowanie wiadomości e-mail:
  
- Wiadomość jest zaszyfrowana lub przekształcana ze zwykłego tekstu w nieprzeczytany tekst, który można odczytać na komputerze nadawcy lub przez serwer centralny w trakcie przesyłania wiadomości.

- Wiadomość pozostaje w tekstu szyfrowania podczas jej przesyłania, aby chronić ją przed odczytaniem w przypadku przecięcia wiadomości.

- Gdy wiadomość zostanie odebrana przez adresata, zostanie ona przekształcona z powrotem w czytelny zwykły tekst na jeden z dwóch sposobów:

  - Komputer adresata odszyfrowuje wiadomość za pomocą klucza, lub

  - Serwer centralny odszyfrowuje wiadomość w imieniu adresata, po weryfikacji tożsamości adresata.

Aby uzyskać więcej informacji na temat zabezpieczania Microsoft 365 między serwerami, na przykład między organizacjami w ramach usługi Microsoft 365 lub między firmą Microsoft 365 a zaufanym partnerem biznesowym spoza firmy Microsoft 365, zobacz Jak Exchange Online [  Korzysta z usługi TLS do zabezpieczania połączeń e-mail w Office 365](exchange-online-uses-tls-to-secure-email-connections.md).
    
## <a name="comparing-email-encryption-options-available-in-office-365"></a>Porównanie opcji szyfrowania poczty e-mail dostępnych w Office 365

|Technologia szyfrowania poczty e-mail|![Grafika koncepcyjna opisującą OME.](../media/2bf27b5e-bbb3-46d1-95bf-884dc27a746c.png)|![Grafika koncepcyjna opisującą usługi IRM](../media/9c0cc444-9448-40c6-b244-8fcc593a64e0.png)|![Grafika koncepcyjna opisującą SMIME](../media/ae4613a8-c17e-47e1-8e13-12e891e43744.png)|
|:-----|:-----|:-----|:-----|
|Co to?|Szyfrowanie wiadomości usługi Office 365 (OME) to usługa wbudowana w usługę Azure Rights Management (Azure RMS), która umożliwia wysyłanie zaszyfrowanych wiadomości e-mail do osób w organizacji i poza nią, niezależnie od docelowego adresu e-mail (Gmail, Yahoo! Mail, Outlook.com itp.). <br/> Jako administrator możesz skonfigurować reguły transportu definiujące warunki szyfrowania. Gdy użytkownik wyśle wiadomość z regułą, szyfrowanie jest stosowane automatycznie. <br/> Aby wyświetlić zaszyfrowane wiadomości, adresaci mogą uzyskać kod dostępu w postaci kodu dostępu w postaci kodu dostępu, zalogować się za pomocą konta Microsoft lub zalogować się przy użyciu konta służbowego skojarzonego z programem Office 365. Adresaci mogą również wysyłać zaszyfrowane odpowiedzi. Do wyświetlania zaszyfrowanych Microsoft 365 i wysyłania zaszyfrowanych odpowiedzi nie jest potrzebna subskrypcja usługi.|IRM to rozwiązanie do szyfrowania, które stosuje również ograniczenia dotyczące użycia wiadomości e-mail. Pozwala zapobiec drukowaniu, przesyłaniu dalej i kopiowaniu poufnych informacji przez osoby nieautoryzowane. <br/> Funkcje usługi IRM w Microsoft 365 Azure Rights Management (Azure RMS).|S/MIME to rozwiązanie do szyfrowania oparte na certyfikatach, które umożliwia zarówno szyfrowanie, jak i cyfrowe podpisywanie wiadomości. Szyfrowanie wiadomości pozwala zagwarantować, że tylko zamierzony adresat będzie miał możliwość otwarcia i odczytania wiadomości. Podpis cyfrowy ułatwia adresatowi zweryfikowanie tożsamości nadawcy. <br/> Zarówno podpisy cyfrowe, jak i szyfrowanie wiadomości, są możliwe dzięki użyciu unikatowych certyfikatów cyfrowych, które zawierają klucze do weryfikowania podpisów cyfrowych oraz do szyfrowania lub odszyfrowywania wiadomości. <br/> Aby użyć funkcji S/MIME, należy mieć w pliku klucze publiczne dla każdego adresata. Adresaci muszą utrzymywać własne klucze prywatne, które muszą pozostać bezpieczne. Jeśli klucze prywatne adresata zostaną naruszone, adresat musi uzyskać nowy klucz prywatny i ponownie rozesłać klucze publiczne do wszystkich potencjalnych nadawców.|
|Do czego to działa?|OME: <br/> Szyfruje wiadomości wysyłane do adresatów wewnętrznych lub zewnętrznych. <br/>  Umożliwia użytkownikom wysyłanie zaszyfrowanych wiadomości na dowolny adres e-mail, w tym na Outlook.com, Yahoo! Poczta i Gmail. <br/>  Umożliwia administratorowi dostosowanie portalu wyświetlania poczty e-mail w celu odzwierciedlenia marki organizacji. <br/> Firma Microsoft bezpiecznie zarządza kluczami i przechowuje je, więc nie musisz tego zrobić. <br/> Nie jest wymagane specjalne oprogramowanie po stronie klienta, o ile zaszyfrowane wiadomości (wysłane jako załącznik HTML) można otworzyć w przeglądarce.|IRM: <br/> Używa ograniczeń szyfrowania i użytkowania w celu zapewnienia ochrony online i offline dla wiadomości e-mail i załączników. <br/> Umożliwia administratorowi skonfigurowanie reguł transportu lub reguł ochrony przed Outlook automatyczne stosowanie usługi IRM do wybierania wiadomości. <br/> Umożliwia użytkownikom ręczne stosowanie szablonów w Outlook lub Outlook w sieci Web (dawniej znany jako Outlook Web App).|S/MIME uwzględnia uwierzytelnianie nadawców za pomocą podpisów cyfrowych oraz poufność wiadomości przy użyciu szyfrowania.|
|Czego to nie robi?|OME nie umożliwia stosowania ograniczeń dotyczących użycia do wiadomości. Nie można jej na przykład użyć w celu zatrzymania przesyłania dalej lub drukowania zaszyfrowanej wiadomości przez adresata.|Niektóre aplikacje mogą nie obsługiwać wiadomości e-mail usługi IRM na wszystkich urządzeniach. Aby uzyskać więcej informacji na temat tych i innych produktów, które obsługują pocztę e-mail usługi IRM, zobacz [Funkcje urządzeń klienckich](/azure/information-protection/requirements#BKMK_ClientCapabilities).|S/MIME nie umożliwia skanowania zaszyfrowanych wiadomości w poszukiwaniu złośliwego oprogramowania, spamu ani zasad.|
|Rekomendacje i przykładowe scenariusze|Zalecamy używanie narzędzia OME, jeśli chcesz wysyłać poufne informacje służbowe do osób spoza organizacji, niezależnie od tego, czy są one odbiorcami, czy też innymi firmami. Przykład:  <br/>  Pracownik bankowy wysyłający wyciągi z kart kredytowych klientom  <br/>  Dokumentacja medyczna wysyłana do pacjenta w biurze lekarskim  <br/>  Prawni prawnicy wysyłają poufne informacje prawne do innego pełnomocnika|Zalecamy korzystanie z usługi IRM, gdy chcesz zastosować ograniczenia dotyczące użycia, a także szyfrowanie. Przykład:  <br/>  Kierownik wysyłający do swojego zespołu poufne informacje dotyczące nowego produktu stosuje opcję "Nie przesyłaj dalej".  <br/>  Kierownik musi udostępnić ofertę oferty innej firmie, która zawiera załącznik od partnera, który używa programu Office 365, i wymagać ochrony zarówno wiadomości e-mail, jak i załącznika.|Zalecamy korzystanie z funkcji S/MIME, gdy Organizacja albo organizacja adresata wymaga prawdziwego szyfrowania równorzędnego.  <br/>  Kod S/MIME jest najczęściej używany w następujących scenariuszach:  <br/>  Instytucje rządowe komunikują się z innymi agencjami rządowymi  <br/>  Firma komunikuje się z agencją rządową|
||

## <a name="what-encryption-options-are-available-for-my-microsoft-365-subscription"></a>Jakie opcje szyfrowania są dostępne dla mojej Microsoft 365 subskrypcji?

Aby uzyskać informacje na temat opcji szyfrowania poczty e-mail dla Microsoft 365 subskrypcji, zobacz [Exchange Online opisu usługi](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description). Tutaj można znaleźć informacje o następujących funkcjach szyfrowania:
  
- Usługa Azure RMS z możliwościami usługi IRM i OME

- S/MIME

- TLS

- Szyfrowanie danych w spoczynku (przy użyciu funkcji BitLocker)

Możesz również używać narzędzi do szyfrowania innych firm z Microsoft 365, na przykład PGP (Pretty Good Privacy). Microsoft 365 nie obsługuje PGP/MIME, a do wysyłania i odbierania wiadomości e-mail zaszyfrowanych PGP można używać tylko protokołu PGP/inline.

## <a name="what-about-encryption-for-data-at-rest"></a>A co z szyfrowaniem danych w spoczynku?

"Dane w spoczynku" odnoszą się do danych, które nie są aktywnie wykorzystywane do przesyłania. W Microsoft 365 danych poczty e-mail w miejscu są szyfrowane przy użyciu szyfrowania dysków funkcją BitLocker. Funkcje BitLocker szyfrują dyski twarde w centrach danych firmy Microsoft, aby zapewnić lepszą ochronę przed nieautoryzowanym dostępem. Aby dowiedzieć się więcej, zobacz [Omówienie funkcji BitLocker](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831713(v=ws.11)).
  
## <a name="more-information-about-email-encryption-options"></a>Więcej informacji na temat opcji szyfrowania poczty e-mail

Aby uzyskać więcej informacji o opcjach szyfrowania wiadomości e-mail w tym artykule oraz o adresie TLS, zobacz następujące artykuły:
  
**OME**
  
[Szyfrowanie wiadomości usługi Office 365 (OME)](ome.md)
  
**IRM**
  
[Zarządzanie prawami do informacji w Exchange Online](./information-rights-management-in-exchange-online.md)
  
[Co to jest usługa Azure Rights Management?](/azure/information-protection/what-is-azure-rms)
  
**S/MIME**
  
[S/MIME do podpisywania i szyfrowania wiadomości](/Exchange/policy-and-compliance/smime/smime)
  
[Opis S/MIME](/previous-versions/tn-archive/aa995740(v=exchg.65))
  
[Opis kryptografii klucza publicznego](/previous-versions/tn-archive/aa998077(v=exchg.65))
  
**TLS**
  
[Konfigurowanie niestandardowego przepływu poczty e-mail za pomocą łączników](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)
