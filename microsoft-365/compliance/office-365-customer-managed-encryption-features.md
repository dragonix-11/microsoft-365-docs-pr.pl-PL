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
description: W tym artykule dowiesz się więcej o technologiach szyfrowania, które można zarządzać i konfigurować w Microsoft 365.
ms.openlocfilehash: 55bc743f83b79ac83c764af24ef4100e5f72369d
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622548"
---
# <a name="customer-managed-encryption-features"></a>Funkcje szyfrowania zarządzane przez klienta

- [Azure Rights Management](/azure/information-protection/what-is-azure-rms)

- [Szyfrowanie wiadomości w Microsoft Purview](https://products.office.com/en-us/exchange/office-365-message-encryption)

- [Bezpieczny przepływ poczty w organizacji partnerskiej](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)

Aby uzyskać więcej informacji na temat tych technologii, zobacz [opisy usługi Microsoft 365](/office365/servicedescriptions/office-365-service-descriptions-technet-library).

## <a name="azure-rights-management"></a>Azure Rights Management

[Azure Rights Management](/azure/information-protection/what-is-azure-rms) (Azure RMS) to technologia ochrony używana przez usługę [Azure Information Protection](/information-protection/understand-explore/what-is-information-protection). Używa ona zasad szyfrowania, tożsamości i autoryzacji w celu zabezpieczenia plików i poczty e-mail na wielu platformach i urządzeniach — telefonach, tabletach i komputerach. Informacje mogą być chronione zarówno w organizacji, jak i poza nią, ponieważ ochrona pozostaje z danymi. Usługa Azure RMS zapewnia trwałą ochronę wszystkich typów plików, chroni pliki w dowolnym miejscu, obsługuje współpracę między firmami oraz szeroką gamę urządzeń Windows i innych niż Windows. Usługa Azure RMS Protection może również rozszerzać [zasady ochrony przed utratą danych (DLP](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)). Aby uzyskać więcej informacji na temat aplikacji i usług, które mogą korzystać z usługi Azure Rights Management z usługi Azure Information Protection, zobacz [Jak aplikacje obsługują usługę Azure Rights Management](/information-protection/understand-explore/applications-support).

Usługa Azure RMS jest zintegrowana z Microsoft 365 i dostępna dla wszystkich klientów. Aby skonfigurować Microsoft 365 do korzystania z usługi Azure RMS, zobacz [Konfigurowanie usługi IRM do korzystania z usługi Azure Rights Management i Konfigurowanie usługi Information Rights Management (IRM) w centrum administracyjnym SharePoint](../enterprise/activate-rms-in-microsoft-365.md). Jeśli korzystasz z serwera usług RMS lokalna usługa Active Directory (AD), możesz również [skonfigurować usługę IRM do korzystania z lokalnego serwera usług AD RMS](/office365/SecurityCompliance/configure-irm-to-use-an-on-premises-ad-rms-server), ale zdecydowanie zalecamy [migrację do usługi Azure RMS](/azure/information-protection/migrate-from-ad-rms-to-azure-rms) w celu korzystania z nowych funkcji, takich jak bezpieczna współpraca z innymi organizacjami.

W przypadku ochrony danych klientów za pomocą usługi Azure RMS usługa Azure RMS używa 2048-bitowego klucza asymetrycznego RSA z algorytmem skrótu SHA-256 w celu zapewnienia integralności w celu szyfrowania danych. Klucz symetryczny dla dokumentów Office i poczty e-mail to 128-bitowy system AES. Dla każdego dokumentu lub wiadomości e-mail, który jest chroniony przez usługę Azure RMS, usługa Azure RMS tworzy jeden klucz AES ("klucz zawartości"), a ten klucz jest osadzony w dokumencie i jest utrwalany w wersjach dokumentu. Klucz zawartości jest chroniony za pomocą klucza RSA organizacji ("Klucz dzierżawy usługi Azure Information Protection") w ramach zasad w dokumencie, a zasady są również podpisywane przez autora dokumentu. Ten klucz dzierżawy jest wspólny dla wszystkich dokumentów i wiadomości e-mail chronionych przez usługę Azure RMS dla organizacji, a ten klucz może zostać zmieniony przez administratora usługi Azure Information Protection tylko wtedy, gdy organizacja używa klucza dzierżawy zarządzanego przez klienta. Aby uzyskać więcej informacji na temat kontrolek kryptograficznych używanych przez usługę Azure RMS, zobacz [Jak działa usługa Azure RMS? Pod maską](/information-protection/understand-explore/how-does-it-work).

W domyślnej implementacji usługi Azure RMS firma Microsoft generuje klucz główny unikatowy dla każdej dzierżawy i zarządza nimi. Klienci mogą zarządzać cyklem życia klucza głównego w usłudze Azure RMS za pomocą usługi Azure Key Vault Services przy użyciu metody zarządzania kluczami o nazwie [Bring Your Own Key (BYOK),](/azure/information-protection/plan-implement-tenant-key) która umożliwia generowanie klucza w lokalnych modułach HSM (sprzętowych modułach zabezpieczeń) i zachowanie kontroli nad tym kluczem po przeniesieniu do modułów HSM z weryfikacją fips 140-2 firmy Microsoft. Dostęp do klucza głównego nie jest udzielany żadnemu personelowi, ponieważ nie można eksportować ani wyodrębniać kluczy z modułów HSM, które je chronią. Ponadto możesz w dowolnym momencie uzyskać dostęp do dziennika niemal w czasie rzeczywistym pokazującego cały dostęp do klucza głównego. Aby uzyskać więcej informacji, zobacz [Rejestrowanie i analizowanie użycia Rights Management platformy Azure](/azure/information-protection/log-analyze-usage).

Usługa Azure Rights Management pomaga uniknąć zagrożeń, takich jak podsłuchiwanie, ataki typu man-in-the-middle, kradzież danych i niezamierzone naruszenia zasad udostępniania organizacji. Jednocześnie wszelkie nieuzasadnione dostępy do danych klientów przesyłanych lub magazynowanych przez nieautoryzowanego użytkownika, który nie ma odpowiednich uprawnień, są blokowane za pośrednictwem zasad, które stosują te dane, zmniejszając w ten sposób ryzyko, że dane wpadną w niepowołane ręce świadomie lub nieświadomie i udostępniają funkcje zapobiegania utracie danych. Jeśli usługa Azure RMS jest używana jako część usługi Azure Information Protection, zapewnia również funkcje klasyfikacji i etykietowania danych, oznaczania zawartości, śledzenia dostępu do dokumentów i odwoływania dostępu. Aby dowiedzieć się więcej na temat tych możliwości, zobacz [Co to jest usługa Azure Information Protection](/information-protection/understand-explore/what-is-information-protection), [plan wdrażania usługi Azure Information Protection](/information-protection/plan-design/deployment-roadmap) i [samouczek Szybki start dla usługi Azure Information Protection](/information-protection/get-started/infoprotect-quick-start-tutorial).

## <a name="secure-multipurpose-internet-mail-extension"></a>Bezpieczne rozszerzenie poczty internetowej z wieloma przeznaczeniami

Secure/Multipurpose Internet Mail Extensions (S/MIME) to standard szyfrowania klucza publicznego i podpisywania cyfrowego danych MIME. Protokół S/MIME jest definiowany w dokumentach RFC 3369, 3370, 3850, 3851 i innych. Umożliwia użytkownikowi szyfrowanie wiadomości e-mail i cyfrowe podpisywanie wiadomości e-mail. Wiadomość e-mail zaszyfrowana przy użyciu protokołu S/MIME może zostać odszyfrowana tylko przez adresata wiadomości e-mail przy użyciu klucza prywatnego, który jest dostępny tylko dla tego adresata. W związku z tym wiadomości e-mail nie mogą być odszyfrowywane przez nikogo innego niż adresat wiadomości e-mail.

[Firma Microsoft obsługuje protokół S/MIME](https://blogs.technet.com/b/exchange/archive/2014/12/15/how-to-configure-s-mime-in-office-365.aspx). Certyfikaty publiczne są dystrybuowane do lokalna usługa Active Directory klienta i przechowywane w atrybutach, które mogą być replikowane do dzierżawy Microsoft 365. Klucze prywatne, które odpowiadają kluczom publicznym, pozostają lokalne i nigdy nie są przesyłane do Office 365. Użytkownicy mogą tworzyć, szyfrować, odszyfrowywać, odczytywać i podpisywać cyfrowo wiadomości e-mail między dwoma użytkownikami w organizacji przy użyciu klientów Outlook, Outlook w sieci Web i Exchange ActiveSync. Aby uzyskać więcej informacji, zobacz [Szyfrowanie S/MIME teraz w Office 365](https://blogs.office.com/2014/02/26/smime-encryption-now-in-office-365/).

## <a name="office-365-message-encryption"></a>szyfrowanie komunikatów Office 365

[Office 365 szyfrowanie komunikatów](https://products.office.com/exchange/office-365-message-encryption) (OME) oparte na usłudze [Azure Information Protection](/information-protection/understand-explore/what-is-information-protection) (AIP) umożliwia wysyłanie wiadomości zaszyfrowanych i chronionych prawami do wszystkich osób. OME łagodzi zagrożenia, takie jak podsłuchiwanie i ataki typu man-in-the-middle, oraz inne zagrożenia, takie jak nieuzasadniony dostęp do danych przez nieautoryzowanego użytkownika, który nie ma odpowiednich uprawnień. Wprowadziliśmy inwestycje, które zapewniają prostsze, bardziej intuicyjne i bezpieczne środowisko poczty e-mail oparte na usłudze Azure Information Protection. Możesz chronić wiadomości wysyłane z Microsoft 365 do wszystkich osób w organizacji lub poza nią. Te wiadomości można wyświetlać w różnych grupach klientów poczty przy użyciu dowolnej tożsamości, w tym Azure Active Directory, konta Microsoft i identyfikatorów Google. Aby uzyskać więcej informacji na temat sposobu używania zaszyfrowanych komunikatów w organizacji, zobacz [Office 365 Szyfrowanie komunikatów](./ome.md).

## <a name="transport-layer-security"></a>Zabezpieczenia warstwy transportu

Jeśli chcesz zapewnić bezpieczną komunikację z partnerem, możesz użyć łączników przychodzących i wychodzących, aby zapewnić bezpieczeństwo i integralność komunikatów. Możesz skonfigurować wymuszony przychodzący i wychodzący protokół TLS dla każdego łącznika przy użyciu certyfikatu. Użycie zaszyfrowanego kanału SMTP może uniemożliwić kradzież danych za pośrednictwem ataku typu man-in-the-middle. Aby uzyskać więcej informacji, zobacz [Jak Exchange Online używa protokołu TLS do zabezpieczania połączeń poczty e-mail](./exchange-online-uses-tls-to-secure-email-connections.md).

## <a name="domain-keys-identified-mail"></a>Adres e-mail z zidentyfikowanymi kluczami domeny

Exchange Online Protection (EOP) i Exchange Online obsługują walidację przychodzącą wiadomości DKIM (Domain Keys Identified Mail). DKIM to metoda sprawdzania, czy komunikat został wysłany z domeny, z którego pochodzi i że nie został sfałszowany przez inną osobę. Wiąże ona wiadomość e-mail z organizacją odpowiedzialną za jej wysłanie i jest częścią większego paradygmatu szyfrowania wiadomości e-mail. Aby uzyskać więcej informacji na temat trzech części tego paradygmatu, zobacz:

- [Konfigurowanie platformy SPF w celu zapobiegania spoofingowi](/office365/SecurityCompliance/set-up-spf-in-office-365-to-help-prevent-spoofing)

- [Sprawdzanie poprawności wychodzących wiadomości e-mail wysyłanych z domeny niestandardowej za pomocą funkcji DKIM](/office365/SecurityCompliance/use-dkim-to-validate-outbound-email)

- [Sprawdzanie poprawności poczty e-mail przy użyciu usługi DMARC](/office365/SecurityCompliance/use-dmarc-to-validate-email)
