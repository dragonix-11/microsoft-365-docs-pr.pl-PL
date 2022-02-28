---
title: Funkcje szyfrowania zarządzane przez klienta
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
ms.custom:
- seo-marvel-mar2020
description: Z tego artykułu dowiesz się więcej o technologiach szyfrowania, które można zarządzać technologiami szyfrowania i je konfigurować w Microsoft 365.
ms.openlocfilehash: 80a0726e112324a673fc964a9fabdbc3ba0ac42e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987996"
---
# <a name="customer-managed-encryption-features"></a>Funkcje szyfrowania zarządzane przez klienta

Oprócz technologii szyfrowania w usługach Microsoft 365 zarządzanych przez firmę Microsoft firma Microsoft 365 także z dodatkowymi technologiami szyfrowania, które można zarządzać i konfigurować, takimi jak:

- [Azure Rights Management](/azure/information-protection/what-is-azure-rms)

- [Rozszerzenie Secure Multipurpose Internet Mail](https://blogs.technet.com/b/exchange/archive/2014/12/15/how-to-configure-s-mime-in-office-365.aspx)

- [Szyfrowanie wiadomości usługi Office 365](https://products.office.com/en-us/exchange/office-365-message-encryption)

- [Zabezpieczanie przepływu poczty e-mail przy użyciu organizacji partnerskiej](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)

Dodatkowe informacje na temat tych technologii można znaleźć w [Microsoft 365 opisach usług](/office365/servicedescriptions/office-365-service-descriptions-technet-library).

## <a name="azure-rights-management"></a>Azure Rights Management

[Azure Rights Management](/azure/information-protection/what-is-azure-rms) (Azure RMS) to technologia ochrony używana przez [usługę Azure Information Protection](/information-protection/understand-explore/what-is-information-protection). Stosuje on zasady szyfrowania, tożsamości i autoryzacji, aby chronić pliki i pocztę e-mail na wielu platformach i urządzeniach — telefonach, tabletach i komputerach. Informacje mogą być chronione zarówno w obrębie organizacji, jak i poza nią, ponieważ ochrona pozostaje z danymi. Usługa Azure RMS zapewnia trwałą ochronę wszystkich typów plików, chroni pliki w dowolnym miejscu, obsługuje współpracę między firmami oraz szeroką gamę urządzeń typu Windows i innych niż Windows biznesowe. Usługa Azure RMS Protection może również [rozszerzyć zasady ochrony przed utratą danych (DLP](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)). Aby uzyskać więcej informacji o tym, które aplikacje i usługi mogą korzystać z usługi Azure Rights Management z usługi Azure Information Protection, zobacz Jak aplikacje [obsługują usługę Azure Rights Management](/information-protection/understand-explore/applications-support).

Usługa Azure RMS jest zintegrowana z usługą Microsoft 365 i dostępna dla wszystkich klientów. Aby skonfigurować usługę Microsoft 365 usługi Azure RMS, zobacz Konfigurowanie usługi IRM do korzystania z usługi Azure Rights Management i Konfigurowanie usługi Zarządzanie prawami do informacji [(IRM)](../enterprise/activate-rms-in-microsoft-365.md) w SharePoint administracyjnym. Jeśli korzystasz z lokalnego serwera RMS usługi Active Directory (AD), możesz również skonfigurować usługę IRM tak, aby korzystać z lokalnego serwera [USŁUG AD RMS](/office365/SecurityCompliance/configure-irm-to-use-an-on-premises-ad-rms-server), ale zdecydowanie zalecamy migrowanie do usługi [Azure RMS](/azure/information-protection/migrate-from-ad-rms-to-azure-rms) w celu używania nowych funkcji, takich jak bezpieczna współpraca z innymi organizacjami.

Gdy chronisz dane klienta za pomocą usługi Azure RMS, usługa Azure RMS używa 2048-bitowego klucza asymetrycznego RSA z algorytmem skrótów SHA-256 do szyfrowania danych. Symetrycznym kluczem do Office e-mail i dokumentów jest 128-bitowy AES. W przypadku każdego dokumentu lub wiadomości e-mail chronionego za pomocą usługi Azure RMS usługa Azure RMS tworzy jeden klucz AES ("klucz zawartości"), który jest osadzony w dokumencie i jest utrwalony w wersjach dokumentu. Klucz zawartości jest chroniony kluczem RSA organizacji ("klucz dzierżawy usługi Azure Information Protection") w ramach zasad w dokumencie, a zasady są również podpisane przez autora dokumentu. Ten klucz dzierżawy jest wspólny dla wszystkich dokumentów i wiadomości e-mail chronionych przez usługę Azure RMS dla organizacji. Ten klucz może zmienić tylko administrator usługi Azure Information Protection, jeśli organizacja korzysta z klucza dzierżawy zarządzanego przez klienta. Aby uzyskać więcej informacji na temat kontrolek kryptograficznych używanych przez usługę Azure RMS, zobacz [Jak działa usługa Azure RMS? W zacieniu](/information-protection/understand-explore/how-does-it-work).

W domyślnej implementacji usługi Azure RMS firma Microsoft generuje klucz główny, który jest unikatowy dla każdej dzierżawy, i zarządza nimi. Klienci mogą zarządzać cyklem życia klucza głównego w usłudze Azure RMS za pomocą usług magazynu kluczy platformy Azure przy użyciu metody zarządzania kluczami o nazwie [Bring Your Own Key (BYOK),](/azure/information-protection/plan-implement-tenant-key) która pozwala na generowanie klucza w lokalnych modułach zabezpieczeń sprzętu, a także pozostawać pod kontrolą tego klucza po przeniesieniu do modułów HSM poziomu 2 weryfikowanych przez firmę Microsoft. Dostęp do klucza głównego nie jest podawany żadnym personelom, ponieważ nie można eksportować ani wyodrębniać kluczy z zabezpieczeń HSM. Ponadto w dowolnym momencie możesz uzyskać dostęp do niemal dziennika w czasie rzeczywistym, w którym jest pokazywany cały dostęp do klucza głównego. Aby uzyskać więcej informacji, zobacz [Rejestrowanie i analizowanie użycia usługi Azure Rights Management](/azure/information-protection/log-analyze-usage).

Usługa Azure Rights Management pomaga zminimalizować zagrożenia, takie jak natłaczanie przewodowe, ataki typu "man-in-the-middle" (man-in-the-middle attacks), kradzież danych i niezamierzone naruszenia zasad udostępniania danych organizacji. W tym samym czasie nieuprawniony dostęp do danych klienta podczas przesyłania lub w czasie spoczynku przez nieautoryzowanego użytkownika, który nie miał odpowiednich uprawnień, jest blokowany przez zasady korzystające z tych danych, zmniejszając ryzyko, że dane dopadną w niepowołanych ręcech, bez znajomości lub nieuprawnionym dostępem do funkcji ochrony przed utratą danych. Jeśli usługa Azure Information Protection jest używana w ramach usługi Azure Information Protection, usługa Azure RMS zapewnia również możliwości klasyfikacji i etykiet, oznaczania zawartości, śledzenia dostępu do dokumentów i możliwości odwołania dostępu. Aby dowiedzieć się więcej o tych możliwościach, zobacz Co to jest usługa [Azure Information Protection](/information-protection/understand-explore/what-is-information-protection), Przewodnik po wdrażaniu usługi [Azure Information Protection](/information-protection/plan-design/deployment-roadmap) i [Samouczek Szybki start dla usługi Azure Information Protection](/information-protection/get-started/infoprotect-quick-start-tutorial).

## <a name="secure-multipurpose-internet-mail-extension"></a>Rozszerzenie Secure Multipurpose Internet Mail

Rozszerzenie S/MIME (Secure/Multipurpose Internet Mail Extensions) to standard szyfrowania klucza publicznego i cyfrowego podpisywania danych MIME. Kod S/MIME jest zdefiniowany w kodach OFERTOWYCH 3369, 3370, 3850, 3851 i innych. Pozwala on użytkownikowi zaszyfrować wiadomość e-mail i cyfrowo podpisać wiadomość e-mail. Wiadomość e-mail zaszyfrowana przy użyciu protokołu S/MIME może zostać odszyfrowana tylko przez adresata, używając jego klucza prywatnego, który jest dostępny tylko dla tego adresata. Z tego względu nikt inny niż odbiorca nie może odszyfrowywać wiadomości e-mail.

[Firma Microsoft obsługuje funkcję S/MIME](https://blogs.technet.com/b/exchange/archive/2014/12/15/how-to-configure-s-mime-in-office-365.aspx). Certyfikaty publiczne są rozpowszechniane z lokalną usługą Active Directory klienta i przechowywane w atrybutach, które można replikować do Microsoft 365 dzierżawy. Klucze prywatne odpowiadające kluczom publicznym pozostają lokalne i nigdy nie są przesyłane Office 365. Użytkownicy mogą redagować, szyfrować, odszyfrowywać, odczytywać i cyfrowo podpisywać wiadomości e-mail między dwoma użytkownikami w organizacji przy użyciu Outlook, Outlook w sieci Web i Exchange ActiveSync klientów. Aby uzyskać więcej informacji, zobacz Szyfrowanie [S/MIME teraz w programie Office 365](https://blogs.office.com/2014/02/26/smime-encryption-now-in-office-365/).

## <a name="office-365-message-encryption"></a>Szyfrowanie wiadomości usługi Office 365

[Szyfrowanie wiadomości usługi Office 365](https://products.office.com/exchange/office-365-message-encryption) (OME) wbudowana w usługę Azure Information Protection (AIP, [Azure Information Protection](/information-protection/understand-explore/what-is-information-protection)) umożliwia wysyłanie zaszyfrowanych i chronionych prawami wiadomości do wszystkich osób. OME ogranicza zagrożenia, takie jak ataki typu "wire-in-the-middle" i "man-in-the-middle" oraz inne zagrożenia, takie jak nieuprawniony dostęp do danych przez nieautoryzowanego użytkownika, który nie ma odpowiednich uprawnień. Wprowadzone inwestycje zapewniają prostsze, bardziej intuicyjne i bezpieczne środowisko poczty e-mail dzięki usłudze Azure Information Protection. Możesz chronić wiadomości wysłane z Microsoft 365 do wszystkich osób w organizacji i poza nią. Te wiadomości mogą być wyświetlane w różnych zestawach klientów poczty przy użyciu dowolnej tożsamości, w tym identyfikatorów Azure Active Directory, konta Microsoft i identyfikatorów Google. Aby uzyskać więcej informacji na temat używania zaszyfrowanych wiadomości w organizacji[, zobacz Szyfrowanie wiadomości usługi Office 365](./ome.md).

## <a name="transport-layer-security"></a>Transport Layer Security

Jeśli chcesz zapewnić bezpieczną komunikację z partnerem, możesz za pomocą łączników ruchu przychodzącego i wychodzącego zapewnić bezpieczeństwo i integralność wiadomości. Przy użyciu certyfikatu można skonfigurować wymuszaną dla każdego łącznika usługę TLS dla ruchu przychodzącego i wychodzącego. Użycie zaszyfrowanego kanału SMTP może zapobiec kradzieży danych w trakcie ataku typu man-in-the-middle. Aby uzyskać więcej informacji, zobacz [Jak Exchange Online połączeń poczty e-mail przy Exchange Online TLS](./exchange-online-uses-tls-to-secure-email-connections.md).

## <a name="domain-keys-identified-mail"></a>Identyfikowana poczta w kluczach domen

Exchange Online Protection (EOP) i Exchange Online weryfikację ruchu przychodzącego wiadomości DKIM (Domain Keys Identified Mail). DKIM to metoda sprawdzania, czy wiadomość została wysłana z domeny, z której pochodziła, i że nie została sfałszowana przez inną osobę. Jest ona owijania wiadomości e-mail do organizacji odpowiedzialnej za jej wysłanie i jest częścią większego paradego szyfrowania poczty e-mail. Aby uzyskać więcej informacji na temat trzech części tego pardigm, zobacz:

- [Konfigurowanie spf w celu zapobiegania fałszerszem](/office365/SecurityCompliance/set-up-spf-in-office-365-to-help-prevent-spoofing)

- [Używanie funkcji DKIM do sprawdzania poprawności wychodzących wiadomości e-mail wysłanych z domeny niestandardowej](/office365/SecurityCompliance/use-dkim-to-validate-outbound-email)

- [Używanie funkcji DMARC do sprawdzania poprawności wiadomości e-mail](/office365/SecurityCompliance/use-dmarc-to-validate-email)