---
title: Szyfrowanie poczty e-mail w usłudze Microsoft 365
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
description: Porównaj opcje szyfrowania platformy Microsoft 365, w tym Szyfrowanie wiadomości w Microsoft Purview, S/MIME, Zarządzanie prawami do informacji (IRM) i dowiedz się więcej o zabezpieczeniach warstwy transportu (TLS).
ms.openlocfilehash: a5541c9a1478d1eb1add40a5aecb7439d1442e1b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624250"
---
# <a name="email-encryption"></a>Szyfrowanie wiadomości e-mail

W tym artykule porównaliśmy opcje szyfrowania na platformie Microsoft 365, w tym Szyfrowanie wiadomości w Microsoft Purview, S/MIME, Zarządzanie prawami do informacji (IRM) i wprowadzono zabezpieczenia warstwy transportu (TLS).
  
Platforma Microsoft 365 oferuje wiele opcji szyfrowania, które ułatwiają spełnienie potrzeb biznesowych dotyczących zabezpieczeń poczty e-mail. W tym artykule przedstawiono trzy sposoby szyfrowania wiadomości e-mail w Office 365. Jeśli chcesz dowiedzieć się więcej o wszystkich funkcjach zabezpieczeń w Office 365, odwiedź [centrum zaufania Office 365](https://go.microsoft.com/fwlink/p/?LinkID=282470). W tym artykule przedstawiono trzy typy szyfrowania dostępne dla administratorów platformy Microsoft 365, które ułatwiają zabezpieczanie poczty e-mail w Office 365:
  
- Szyfrowanie wiadomości w Microsoft Purview.

- Bezpieczne/uniwersalne rozszerzenia poczty internetowej (S/MIME).

- Zarządzanie prawami do informacji (IRM).

## <a name="how-microsoft-365-uses-email-encryption"></a>Jak platforma Microsoft 365 używa szyfrowania poczty e-mail

Szyfrowanie to proces kodowania informacji, dzięki czemu tylko autoryzowany adresat może dekodować informacje i korzystać z nich. Platforma Microsoft 365 używa szyfrowania na dwa sposoby: w usłudze i jako kontrola klienta. W usłudze szyfrowanie jest domyślnie używane na platformie Microsoft 365; Nie musisz niczego konfigurować. Na przykład platforma Microsoft 365 używa protokołu Transport Layer Security (TLS) do szyfrowania połączenia lub sesji między dwoma serwerami. 
  
Oto jak zwykle działa szyfrowanie poczty e-mail:
  
- Komunikat jest szyfrowany lub przekształcany z zwykłego tekstu w nieczytelny szyfrowanie na maszynie nadawcy lub przez serwer centralny, gdy komunikat jest przesyłany.

- Komunikat pozostaje w szyfrowanym tekstie, gdy jest przesyłany, aby chronić go przed odczytem w przypadku przechwycenia komunikatu.

- Po odebraniu wiadomości przez adresata wiadomość zostanie przekształcona z powrotem w czytelny zwykły tekst na jeden z dwóch sposobów:

  - Maszyna odbiorcy używa klucza do odszyfrowania wiadomości lub

  - Centralny serwer odszyfrowuje komunikat w imieniu adresata po zweryfikowaniu tożsamości adresata.

Aby uzyskać więcej informacji o tym, jak platforma Microsoft 365 zabezpiecza komunikację między serwerami, takimi jak między organizacjami w ramach platformy Microsoft 365 lub między platformą Microsoft 365 a zaufanym partnerem biznesowym spoza platformy Microsoft 365, zobacz [Jak Exchange Online używa protokołu TLS do zabezpieczania połączeń poczty e-mail w Office 365](exchange-online-uses-tls-to-secure-email-connections.md).
    
## <a name="comparing-email-encryption-options-available-in-office-365"></a>Porównanie opcji szyfrowania poczty e-mail dostępnych w Office 365

|Technologia szyfrowania poczty e-mail|![Grafika koncepcyjna opisująca OME.](../media/2bf27b5e-bbb3-46d1-95bf-884dc27a746c.png)|![Grafika koncepcyjna opisująca usługę IRM](../media/9c0cc444-9448-40c6-b244-8fcc593a64e0.png)|![Grafika koncepcyjna opisująca protokół SMIME](../media/ae4613a8-c17e-47e1-8e13-12e891e43744.png)|
|:-----|:-----|:-----|:-----|
|Co to?|Szyfrowanie wiadomości to usługa oparta na usłudze Azure Rights Management (Azure RMS), która umożliwia wysyłanie zaszyfrowanych wiadomości e-mail do osób w organizacji lub poza nią, niezależnie od docelowego adresu e-mail (Gmail, Yahoo! Poczta, Outlook.com itp.). <br/> Jako administrator możesz skonfigurować reguły transportu definiujące warunki szyfrowania. Gdy użytkownik wysyła komunikat zgodny z regułą, szyfrowanie jest stosowane automatycznie. <br/> Aby wyświetlić zaszyfrowane wiadomości, adresaci mogą uzyskać jednorazowy kod dostępu, zalogować się przy użyciu konta Microsoft lub zalogować się przy użyciu konta służbowego skojarzonego z Office 365. Adresaci mogą również wysyłać zaszyfrowane odpowiedzi. Nie potrzebują subskrypcji platformy Microsoft 365 do wyświetlania zaszyfrowanych wiadomości ani wysyłania zaszyfrowanych odpowiedzi.|IRM to rozwiązanie szyfrowania, które stosuje również ograniczenia użycia do wiadomości e-mail. Zapobiega to drukowaniu, przekazywaniu lub kopiowaniu poufnych informacji przez nieautoryzowane osoby. <br/> Funkcje IRM w usłudze Microsoft 365 korzystają z usługi Azure Rights Management (Azure RMS).|S/MIME to oparte na certyfikatach rozwiązanie do szyfrowania, które umożliwia szyfrowanie i cyfrowe podpisywanie komunikatu. Szyfrowanie komunikatów pomaga zagwarantować, że tylko zamierzony adresat może otworzyć i odczytać komunikat. Podpis cyfrowy pomaga adresatowi zweryfikować tożsamość nadawcy. <br/> Zarówno podpisy cyfrowe, jak i szyfrowanie komunikatów są możliwe dzięki użyciu unikatowych certyfikatów cyfrowych, które zawierają klucze do weryfikowania podpisów cyfrowych oraz szyfrowania lub odszyfrowywania komunikatów. <br/> Aby użyć protokołu S/MIME, musisz mieć klucze publiczne w pliku dla każdego adresata. Adresaci muszą utrzymywać własne klucze prywatne, które muszą pozostać bezpieczne. Jeśli klucze prywatne adresata zostaną naruszone, odbiorca musi uzyskać nowy klucz prywatny i ponownie rozesłać klucze publiczne do wszystkich potencjalnych nadawców.|
|Co to robi?|OME: <br/> Szyfruje wiadomości wysyłane do adresatów wewnętrznych lub zewnętrznych. <br/>  Umożliwia użytkownikom wysyłanie zaszyfrowanych wiadomości na dowolny adres e-mail, w tym Outlook.com, Yahoo! Poczta i Gmail. <br/>  Umożliwia, jako administrator, dostosowanie portalu wyświetlania wiadomości e-mail w celu odzwierciedlenia marki organizacji. <br/> Firma Microsoft bezpiecznie zarządza kluczami i przechowuje je, więc nie musisz tego robić. <br/> Nie jest wymagane żadne specjalne oprogramowanie po stronie klienta, o ile w przeglądarce można otworzyć zaszyfrowaną wiadomość (wysłaną jako załącznik HTML).|IRM: <br/> Używa ograniczeń szyfrowania i użycia, aby zapewnić ochronę wiadomości e-mail i załączników w trybie online i offline. <br/> Umożliwia administratorowi skonfigurowanie reguł transportu lub reguł ochrony programu Outlook w celu automatycznego stosowania usługi IRM do wybierania komunikatów. <br/> Umożliwia użytkownikom ręczne stosowanie szablonów w programie Outlook lub Outlook w sieci Web (dawniej nazywanym Outlook Web App).|Protokół S/MIME adresuje uwierzytelnianie nadawcy za pomocą podpisów cyfrowych i poufność komunikatów za pomocą szyfrowania.|
|Czego nie robi?|Protokół OME nie umożliwia stosowania ograniczeń użycia do komunikatów. Na przykład nie można jej użyć, aby uniemożliwić adresatowi przekazywanie lub drukowanie zaszyfrowanej wiadomości.|Niektóre aplikacje mogą nie obsługiwać wiadomości e-mail IRM na wszystkich urządzeniach. Aby uzyskać więcej informacji na temat tych i innych produktów, które obsługują pocztę e-mail usługi IRM, zobacz [Możliwości urządzeń klienckich](/azure/information-protection/requirements#BKMK_ClientCapabilities).|Protokół S/MIME nie zezwala na skanowanie zaszyfrowanych wiadomości pod kątem złośliwego oprogramowania, spamu ani zasad.|
|Zalecenia i przykładowe scenariusze|Zalecamy używanie protokołu OME, jeśli chcesz wysyłać poufne informacje biznesowe do osób spoza organizacji, niezależnie od tego, czy są to konsumenci, czy inne firmy. Przykład:  <br/>  Pracownik banku wysyłający wyciągi z kart kredytowych do klientów  <br/>  Biuro lekarskie wysyłające dokumentację medyczną do pacjenta  <br/>  Adwokat wysyłający poufne informacje prawne do innego adwokata|Zalecamy używanie usługi IRM, jeśli chcesz zastosować ograniczenia użycia, a także szyfrowanie. Przykład:  <br/>  Menedżer wysyłający do swojego zespołu poufne szczegóły dotyczące nowego produktu stosuje opcję "Nie przesyłaj dalej".  <br/>  Dyrektor musi podzielić się propozycją oferty z inną firmą, która zawiera załącznik od partnera, który korzysta z Office 365, i wymaga, aby zarówno wiadomość e-mail, jak i załącznik były chronione.|Zalecamy używanie protokołu S/MIME, gdy organizacja lub organizacja odbiorcy wymaga prawdziwego szyfrowania równorzędnego.  <br/>  Protokół S/MIME jest najczęściej używany w następujących scenariuszach:  <br/>  Agencje rządowe komunikujące się z innymi agencjami rządowymi  <br/>  Firma komunikująca się z agencją rządową|
||

## <a name="what-encryption-options-are-available-for-my-microsoft-365-subscription"></a>Jakie opcje szyfrowania są dostępne dla mojej subskrypcji platformy Microsoft 365?

Aby uzyskać informacje o opcjach szyfrowania poczty e-mail dla subskrypcji platformy Microsoft 365, zobacz [opis usługi Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description). Tutaj możesz znaleźć informacje o następujących funkcjach szyfrowania:
  
- Usługa Azure RMS, w tym zarówno możliwości IRM, jak i Szyfrowanie wiadomości w Microsoft Purview

- S/MIME

- TLS

- Szyfrowanie danych magazynowanych (za pośrednictwem BitLocker)

Możesz również użyć narzędzi szyfrowania innych firm w usłudze Microsoft 365, na przykład PGP (całkiem dobra prywatność). Platforma Microsoft 365 nie obsługuje protokołu PGP/MIME i możesz wysyłać i odbierać wiadomości e-mail zaszyfrowane za pomocą protokołu PGP/Inline.

## <a name="what-about-encryption-for-data-at-rest"></a>A co z szyfrowaniem danych magazynowanych?

"Dane magazynowane" odnoszą się do danych, które nie są aktywnie przesyłane. W usłudze Microsoft 365 dane poczty e-mail magazynowane są szyfrowane przy użyciu szyfrowania dysków BitLocker. BitLocker szyfruje dyski twarde w centrach danych firmy Microsoft, aby zapewnić lepszą ochronę przed nieautoryzowanym dostępem. Aby dowiedzieć się więcej, zobacz [omówienie BitLocker](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831713(v=ws.11)).
  
## <a name="more-information-about-email-encryption-options"></a>Więcej informacji o opcjach szyfrowania poczty e-mail

Aby uzyskać więcej informacji na temat opcji szyfrowania wiadomości e-mail w tym artykule, a także protokołu TLS, zobacz następujące artykuły:
  
**Szyfrowanie wiadomości w Microsoft Purview**
  
[Szyfrowanie wiadomości ](ome.md)
  
**IRM**
  
[Zarządzanie prawami do informacji w Exchange Online](./information-rights-management-in-exchange-online.md)
  
[Co to jest usługa Azure Rights Management?](/azure/information-protection/what-is-azure-rms)
  
**S/MIME**
  
[Protokół S/MIME na potrzeby podpisywania i szyfrowania komunikatów](/Exchange/policy-and-compliance/smime/smime)
  
[Opis protokołu S/MIME](/previous-versions/tn-archive/aa995740(v=exchg.65))
  
[Opis kryptografii klucza publicznego](/previous-versions/tn-archive/aa998077(v=exchg.65))
  
**TLS**
  
[Konfigurowanie niestandardowego przepływu poczty przy użyciu łączników](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)
