---
title: Szyfrowanie usługi przy użyciu klucza klienta usługi Microsoft Purview
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: seo-marvel-apr2020
description: W tym artykule dowiesz się, jak szyfrowanie usługi działa z Microsoft Purview Klucz klienta.
ms.openlocfilehash: 3a0533b94cb70c9fc46d6246e99d3f9fdb5eb6e6
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415090"
---
# <a name="service-encryption-with-microsoft-purview-customer-key"></a>Szyfrowanie usługi przy użyciu klucza klienta usługi Microsoft Purview

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft 365 zapewnia podstawowe szyfrowanie na poziomie woluminu włączone za pośrednictwem BitLocker i rozproszonego menedżera kluczy (DKM). Microsoft 365 oferuje dodatkową warstwę szyfrowania zawartości. Ta zawartość obejmuje dane z Exchange Online, Skype dla firm, SharePoint Online, OneDrive dla Firm i Microsoft Teams.

## <a name="how-service-encryption-bitlocker-and-customer-key-work-together"></a>Jak szyfrowanie usługi, BitLocker i klucz klienta współpracują ze sobą

Dane są zawsze szyfrowane w usłudze Microsoft 365 za pomocą BitLocker i DKM. Aby uzyskać więcej informacji, zobacz [Jak Exchange Online zabezpiecza wpisy tajne poczty e-mail](exchange-online-secures-email-secrets.md). Klucz klienta zapewnia dodatkową ochronę przed wyświetlaniem danych przez nieautoryzowane systemy lub personel oraz uzupełnia szyfrowanie dysków BitLocker w centrach danych firmy Microsoft. Szyfrowanie usługi nie ma na celu uniemożliwienia pracownikom firmy Microsoft uzyskiwania dostępu do danych. Zamiast tego klucz klienta pomaga spełnić wymagania prawne lub zgodności dotyczące kontrolowania kluczy głównych. Jawnie autoryzujesz usługi Microsoft 365 do używania kluczy szyfrowania w celu dostarczania usług w chmurze o wartości dodanej, takich jak elektroniczne wykrywanie, ochrona przed złośliwym oprogramowaniem, ochrona przed spamem, indeksowanie wyszukiwania itd.

Klucz klienta jest oparty na szyfrowaniu usługi i umożliwia udostępnianie i kontrolowanie kluczy szyfrowania. Microsoft 365 następnie używa tych kluczy do szyfrowania danych magazynowanych zgodnie z opisem w [Warunkach usług online (OST).](https://www.microsoft.com/licensing/product-licensing/products.aspx) Klucz klienta pomaga spełnić wymagania dotyczące zgodności, ponieważ kontrolujesz klucze szyfrowania, które Microsoft 365 używane do szyfrowania i odszyfrowywania danych.
  
Klucz klienta zwiększa zdolność organizacji do spełnienia wymagań dotyczących zgodności, które określają kluczowe rozwiązania z dostawcą usług w chmurze. Klucz klienta umożliwia udostępnianie i kontrolowanie głównych kluczy szyfrowania dla Microsoft 365 danych magazynowanych na poziomie aplikacji. W związku z tym sprawujesz kontrolę nad kluczami organizacji.

## <a name="customer-key-with-hybrid-deployments"></a>Klucz klienta z wdrożeniami hybrydowymi

Klucz klienta szyfruje tylko dane magazynowane w chmurze. Klucz klienta nie działa w celu ochrony lokalnych skrzynek pocztowych i plików. Dane lokalne można zaszyfrować przy użyciu innej metody, takiej jak BitLocker.

## <a name="about-data-encryption-policies"></a>Informacje o zasadach szyfrowania danych

Zasady szyfrowania danych (DEP) definiują hierarchię szyfrowania. Ta hierarchia jest używana przez usługę do szyfrowania danych przy użyciu każdego zarządzanego klucza i klucza dostępności chronionego przez firmę Microsoft. Możesz tworzyć adresy DEPs przy użyciu poleceń cmdlet programu PowerShell, a następnie przypisywać te adresy DEPs do szyfrowania danych aplikacji. Istnieją trzy typy deps obsługiwane przez klucz klienta, każdy typ zasad używa różnych poleceń cmdlet i zapewnia pokrycie dla innego typu danych. Adresy IP, które można zdefiniować, obejmują:

**Program DEP dla wielu obciążeń Microsoft 365** Te dostawcy USŁUG szyfrują dane w wielu obciążeniach M365 dla wszystkich użytkowników w ramach dzierżawy. Te obciążenia obejmują:

- Teams wiadomości czatu (czaty 1:1, czaty grupowe, czaty na spotkania i rozmowy kanałowe)
- Teams wiadomości multimedialnych (obrazy, fragmenty kodu, wiadomości wideo, wiadomości audio, obrazy typu wiki)
- Teams nagrań rozmów i spotkań przechowywanych w magazynie Teams
- Teams powiadomień czatu
- Teams sugestie czatu Cortana
- Teams komunikaty o stanie
- Informacje o użytkowniku i sygnale dla Exchange Online
- Exchange Online skrzynki pocztowe, które nie są jeszcze szyfrowane przez adresy DEPs skrzynki pocztowej
- Ujednolicony magazyn dzienników inspekcji
- Microsoft Purview Information Protection:

  - Dokładne dane są zgodne z danymi (EDM), w tym schematy plików danych, pakiety reguł i sole używane do wyznaczania wartości skrótu danych poufnych. W przypadku programu EDM i Microsoft Teams program DEP z wieloma obciążeniami szyfruje nowe dane od momentu przypisania programu DEP do dzierżawy. W przypadku Exchange Online klucz klienta szyfruje wszystkie istniejące i nowe dane.

  - Konfiguracja etykiet dla etykiet poufności

Adresy IP z wieloma obciążeniami nie szyfruje następujących typów danych. Zamiast tego Microsoft 365 używa innych typów szyfrowania do ochrony tych danych.

- SharePoint i OneDrive dla Firm danych.
- Microsoft Teams pliki i niektóre Teams nagrania połączeń i spotkań zapisane w usłudze OneDrive dla Firm i SharePoint Online są szyfrowane przy użyciu programu DEP usługi SharePoint Online.
- Inne obciążenia Microsoft 365, takie jak Yammer i Planista, które nie są obecnie obsługiwane przez klucz klienta.
- Teams danych zdarzeń na żywo.

Możesz utworzyć wiele adresów DEPs na dzierżawę, ale jednocześnie przypisać tylko jeden program DEP. Po przypisaniu programu DEP szyfrowanie rozpoczyna się automatycznie, ale ukończenie szyfrowania zajmuje trochę czasu w zależności od rozmiaru dzierżawy.

**Adresy DEPS dla Exchange Online skrzynek pocztowych Adresy DEPs skrzynki pocztowej** zapewniają precyzyjniejszą kontrolę nad poszczególnymi skrzynkami pocztowymi w ramach Exchange Online. Adresy DEPs skrzynki pocztowej umożliwiają szyfrowanie danych przechowywanych w skrzynkach pocztowych EXO różnych typów, takich jak UserMailbox, MailUser, Group, PublicFolder i Udostępnione skrzynki pocztowe. Możesz mieć do 50 aktywnych adresów IP na dzierżawę i przypisać te adresy IP do poszczególnych skrzynek pocztowych. Jeden program DEP można przypisać do wielu skrzynek pocztowych.

Domyślnie skrzynki pocztowe są szyfrowane przy użyciu kluczy zarządzanych przez firmę Microsoft. Po przypisaniu programu DEP klucza klienta do skrzynki pocztowej:

- Jeśli skrzynka pocztowa jest szyfrowana przy użyciu wielozadaniowego programu DEP, usługa ponownie rozpakowuje skrzynkę pocztową przy użyciu nowej skrzynki pocztowej DEP, o ile użytkownik lub operacja systemowa uzyskuje dostęp do danych skrzynki pocztowej.

- Jeśli skrzynka pocztowa jest już zaszyfrowana przy użyciu kluczy zarządzanych przez firmę Microsoft, usługa ponownie rozpakowuje skrzynkę pocztową przy użyciu nowej skrzynki pocztowej DEP, o ile użytkownik lub operacja systemowa uzyskuje dostęp do danych skrzynki pocztowej.

- Jeśli skrzynka pocztowa nie jest jeszcze zaszyfrowana przy użyciu szyfrowania domyślnego, usługa oznacza skrzynkę pocztową do przeniesienia. Szyfrowanie odbywa się po zakończeniu przenoszenia. Przenoszenie skrzynek pocztowych zależy od priorytetów ustawionych dla wszystkich Microsoft 365. Aby uzyskać więcej informacji, zobacz [Przenoszenie żądań w usłudze Microsoft 365](/exchange/mailbox-migration/office-365-migration-best-practices#move-requests-in-the-microsoft-365-or-office-365-service). Jeśli skrzynki pocztowe nie są szyfrowane w określonym czasie, skontaktuj się z firmą Microsoft.

Później można odświeżyć program DEP lub przypisać inny program DEP do skrzynki pocztowej zgodnie z opisem w [temacie Zarządzanie kluczem klienta dla Office 365](customer-key-manage.md). Każda skrzynka pocztowa musi mieć odpowiednie licencje, do których ma zostać przypisany program DEP. Aby uzyskać więcej informacji na temat licencjonowania, zobacz [Przed skonfigurowanie klucza klienta](customer-key-set-up.md#before-you-set-up-customer-key).

Adresy IP można przypisać do udostępnionej skrzynki pocztowej, skrzynki pocztowej folderu publicznego i skrzynki pocztowej grupy Microsoft 365 dla dzierżaw, które spełniają wymagania licencyjne dla skrzynek pocztowych użytkowników. Nie potrzebujesz oddzielnych licencji dla skrzynek pocztowych innych niż specyficzne dla użytkownika, aby przypisać program DEP klucza klienta.

W przypadku adresów DEPs klucza klienta, które są przypisywane do poszczególnych skrzynek pocztowych, możesz zażądać od firmy Microsoft przeczyszczania określonych adresów IP po opuszczeniu usługi. Aby uzyskać informacje o procesie przeczyszczania danych i odwoływaniu [kluczy, zobacz Odwoływanie kluczy i uruchamianie procesu ścieżki przeczyszczania danych](customer-key-manage.md#revoke-your-keys-and-start-the-data-purge-path-process).

Po odwołaniu dostępu do kluczy w ramach opuszczania usługi klucz dostępności zostanie usunięty, co spowoduje usunięcie danych kryptograficznych. Usunięcie kryptograficzne zmniejsza ryzyko ponownego zarządzania danymi, co jest ważne w przypadku spełnienia zarówno obowiązków w zakresie zabezpieczeń, jak i zgodności.

**Program DEP dla SharePoint Online i OneDrive dla Firm** Ten program DEP służy do szyfrowania zawartości przechowywanej w sieci SPO i OneDrive dla Firm, w tym Microsoft Teams plików przechowywanych w spo. Jeśli używasz funkcji wielu obszarów geograficznych, możesz utworzyć jeden program DEP na obszar geograficzny dla swojej organizacji. Jeśli nie używasz funkcji wielu obszarów geograficznych, możesz utworzyć tylko jeden program DEP na dzierżawę. Zapoznaj się ze szczegółami w [temacie Konfigurowanie klucza klienta](customer-key-set-up.md).

### <a name="encryption-ciphers-used-by-customer-key"></a>Szyfry szyfrowania używane przez klucz klienta

Klucz klienta używa różnych szyfrów szyfrowania do szyfrowania kluczy, jak pokazano na poniższych rysunkach.

Hierarchia kluczy używana w celu szyfrowania danych dla wielu Microsoft 365 obciążeń jest podobna do hierarchii używanej dla adresów DEPs dla poszczególnych Exchange Online skrzynek pocztowych. Jedyną różnicą jest to, że klucz skrzynki pocztowej jest zastępowany odpowiednim kluczem obciążenia Microsoft 365.

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>Szyfry szyfrowania używane do szyfrowania kluczy dla Exchange Online i Skype dla firm

![Szyfry szyfrowania dla Exchange Online klucza klienta.](../media/customerkeyencryptionhierarchiesexchangeskype.png)

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Szyfry szyfrowania używane do szyfrowania kluczy dla plików SharePoint Online, OneDrive dla Firm i Teams

![Szyfry szyfrowania dla SharePoint klucza klienta online.](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>Artykuły pokrewne

- [Konfigurowanie klucza klienta](customer-key-set-up.md)

- [Zarządzanie kluczem klienta](customer-key-manage.md)

- [Tocz lub obracaj klucz klienta lub klucz dostępności](customer-key-availability-key-roll.md)

- [Dowiedz się więcej o kluczu dostępności](customer-key-availability-key-understand.md)

- [Skrytka klienta](customer-lockbox-requests.md)

- [Szyfrowanie usługi](office-365-service-encryption.md)
