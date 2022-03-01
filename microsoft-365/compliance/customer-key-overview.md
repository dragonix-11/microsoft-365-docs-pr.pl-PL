---
title: Szyfrowanie usługi przy użyciu klucza klienta
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
description: Z tego artykułu dowiesz się, jak działa szyfrowanie usługi z kluczem klienta w Microsoft 365.
ms.openlocfilehash: 14760bfcb26fa1bf45c54661cbb6fc189bad7d93
ms.sourcegitcommit: f563b4229760fa099703296d1ad2c1f0264f1647
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2022
ms.locfileid: "63015755"
---
# <a name="service-encryption-with-customer-key"></a>Szyfrowanie usługi przy użyciu klucza klienta

Usługa Microsoft 365 udostępnia szyfrowanie bazowe na poziomie głośności za pośrednictwem funkcji BitLocker i Menedżera kluczy rozłożonych (DKM). Microsoft 365 udostępnia dodatkową warstwę szyfrowania dla zawartości. Ta zawartość obejmuje dane z usług Exchange Online, Skype dla firm, SharePoint Online, OneDrive dla Firm i Microsoft Teams.

## <a name="how-service-encryption-bitlocker-and-customer-key-work-together"></a>Jak współpracują ze sobą szyfrowanie usług, funkcję BitLocker i klucz klienta

Twoje dane są zawsze szyfrowane w miejscu w Microsoft 365 za pomocą funkcji BitLocker i DKM. Aby uzyskać więcej informacji, zobacz [Jak Exchange Online zabezpiecza sekrety poczty e-mail](exchange-online-secures-email-secrets.md). Klucz klienta zapewnia dodatkową ochronę przed wyświetlaniem danych przez nieautoryzowane systemy lub pracowników oraz uzupełnia szyfrowanie dysków funkcją BitLocker w centrach danych firmy Microsoft. Szyfrowanie usługi nie ma na celu uniemożliwiania pracownikom firmy Microsoft uzyskiwania dostępu do Twoich danych. Zamiast tego klucz klienta ułatwia spełnienie zobowiązań prawnych lub dotyczących zgodności z przepisami w celu kontrolowania kluczy głównych. Jawnie autoryzujesz usługi Microsoft 365 do używania Twoich kluczy szyfrowania w celu zapewnienia usług w chmurze o dodatkowych wartościach, takich jak zbierania elektronicznych materiałów dowodowych, ochrony przed złośliwym oprogramowaniem, ochrona przed spamem, indeksowanie wyszukiwania itp.

Klucz klienta jest zbudowany na podstawie szyfrowania usługi i umożliwia dostarczenie oraz kontrolowanie kluczy szyfrowania. Microsoft 365 następnie używa tych kluczy do szyfrowania danych w spoczynku zgodnie z opisem w Warunkach usług [online (OST).](https://www.microsoft.com/licensing/product-licensing/products.aspx) Klucz klienta ułatwia spełnianie wymagań dotyczących zgodności, ponieważ kontrolujesz klucze szyfrowania używane Microsoft 365 do szyfrowania i odszyfrowywania danych.
  
Klucz klienta zwiększa możliwość spełniania przez Twoją organizację wymagań dotyczących zgodności, które określają kluczowe układy dotyczące kluczowych rozwiązań usługodawca. Dzięki kluczowi klienta dostarczasz i kontrolujesz główne klucze szyfrowania dla Microsoft 365 danych w spoczynku na poziomie aplikacji. W wyniku tego będziesz sprawować kontrolę nad kluczami swojej organizacji.

## <a name="customer-key-with-hybrid-deployments"></a>Klucz klienta z wdrożeniami hybrydowymi

Klucz klienta szyfruje dane tylko w chmurze. Klucz klienta nie działa w celu ochrony lokalnych skrzynek pocztowych i plików. Dane lokalne możesz zaszyfrować przy użyciu innej metody, takiej jak bitLocker.

## <a name="about-data-encryption-policies"></a>Informacje o zasadach szyfrowania danych

Zasady szyfrowania danych (DEP) określają hierarchię szyfrowania. Ta hierarchia jest używana przez usługę do szyfrowania danych przy użyciu każdego z kluczy, które zarządzasz, oraz klucza dostępności chronionego przez firmę Microsoft. Za pomocą poleceń cmdlet programu PowerShell można tworzyć skrypty DEPs, a następnie przypisywać je do szyfrowania danych aplikacji. Istnieją trzy typy źródeł danych obsługiwanych przez Microsoft 365 Klienta. Poszczególne typy zasad mają różne polecenia cmdlet i zapewniają zasięg dla innego typu danych. Można zdefiniować następujące zasady dezp:

**Funkcja DEP w przypadku Microsoft 365 obciążeniami pracą** Te dezpki szyfrują dane w wielu obciążeniach pracą usługi M365 dla wszystkich użytkowników w dzierżawie. Są to następujące obciążenia pracą:

- Teams wiadomości czatu (czaty 1:1, czaty grupowe, czaty spotkań i konwersacje na kanale)
- Teams wiadomości multimedialne (obrazy, fragmenty kodu, wiadomości wideo, wiadomości audio, obrazy typu wiki)
- Teams połączeń i spotkań przechowywane w Teams magazynu
- Teams powiadomienia czatu
- Teams sugestii czatu za pomocą Cortana
- Teams o stanie
- Informacje o użytkownikach i sygnałach dla Exchange Online
- Exchange Online skrzynek pocztowych, które nie są jeszcze zaszyfrowane przez dezp skrzynek pocztowych
- Microsoft Information Protection:

  - Dokładne dane zgodne z danymi (EDM), w tym schematy plików danych, pakiety reguł i sosy użyte do skrótów danych poufnych. W przypadku usługi EDM i Microsoft Teams funkcja dep wielu obciążeń szyfruje nowe dane od czasu przypisania funkcji DEP do dzierżawy. Na Exchange Online klucz klienta szyfruje wszystkie istniejące i nowe dane.

  - Konfiguracja etykiet dla etykiet wrażliwości

Obsługa wielu obciążeń pracą nie szyfruje następujących typów danych. Zamiast Microsoft 365 tych danych są używane inne typy szyfrowania.

- SharePoint i OneDrive dla Firm danych.
- Microsoft Teams, a niektóre Teams połączeń i spotkań zapisane w usługach OneDrive dla Firm i SharePoint Online są szyfrowane przy użyciu funkcji dep SharePoint Online.
- Inne Microsoft 365, takie jak Yammer i Planner, które nie są obecnie obsługiwane przez klucz klienta.
- Teams danych zdarzenia na żywo.

Możesz utworzyć wiele deps na dzierżawę, ale przypisywać tylko jeden dep jednocześnie. Po przypisaniu funkcji DEP szyfrowanie rozpoczyna się automatycznie, ale w zależności od rozmiaru dzierżawy zajmuje trochę czasu.

**Deps for Exchange Online mailbox** dePs provide more precise control over individual mailboxes within Exchange Online. Za pomocą dezaktywowanych skrzynek pocztowych możesz szyfrować dane przechowywane w skrzynkach pocztowych EXO różnych typów, takich jak UserMailbox, MailUser, Group, PublicFolder i Shared mailboxes. Możesz mieć maksymalnie 50 aktywnych dezpów na dzierżawcę i przypisać je do poszczególnych skrzynek pocztowych. Możesz przypisać jedną dep do wielu skrzynek pocztowych.

Domyślnie skrzynki pocztowe są szyfrowane przy użyciu kluczy zarządzanych przez firmę Microsoft. Po przypisaniu funkcji DEP klucza klienta do skrzynki pocztowej:

- Jeśli skrzynka pocztowa jest szyfrowana przy użyciu funkcji DEP o wielu obciążeniach, usługa ponownie dezbuje skrzynkę pocztową przy użyciu nowej funkcji DEP, o ile użytkownik lub operacja systemowa uzyskuje dostęp do danych skrzynki pocztowej.

- Jeśli skrzynka pocztowa jest już zaszyfrowana przy użyciu kluczy zarządzanych przez firmę Microsoft, usługa ponownie wywrze do skrzynki pocztowej nową skrzynkę za pomocą funkcji DEP, o ile użytkownik lub operacja systemowa uzyskuje dostęp do danych skrzynki pocztowej.

- Jeśli skrzynka pocztowa nie jest jeszcze zaszyfrowana przy użyciu domyślnego szyfrowania, usługa oznacza skrzynkę pocztową za przeniesienie. Szyfrowanie ma miejsce po zakończeniu przenoszenia. Przeniesienie skrzynki pocztowej jest zarządzane zgodnie z priorytetami ustawionymi dla wszystkich Microsoft 365. Aby uzyskać więcej informacji, zobacz Żądania [przeniesienia w Microsoft 365 usługi.](/exchange/mailbox-migration/office-365-migration-best-practices#move-requests-in-the-microsoft-365-or-office-365-service) Jeśli skrzynki pocztowe nie są szyfrowane w określonym czasie, skontaktuj się z firmą Microsoft.

Później możesz odświeżyć element DEP lub przypisać do skrzynki pocztowej inny element DEP zgodnie z opisem w tece Zarządzanie [kluczem](customer-key-manage.md) klienta dla Office 365. Do każdej skrzynki pocztowej muszą być przypisane odpowiednie licencje. Aby uzyskać więcej informacji na temat licencjonowania, zobacz [Przed skonfigurowaniem klucza klienta](customer-key-set-up.md#before-you-set-up-customer-key).

Dezp można przypisywać do udostępnionej skrzynki pocztowej, skrzynki pocztowej folderu publicznego i skrzynki pocztowej grupy Microsoft 365 dzierżaw, które spełniają wymagania licencyjne dotyczące skrzynek pocztowych użytkowników. Do przypisania funkcji DEP klucza klienta nie są potrzebne osobne licencje dla skrzynek pocztowych innych niż określone przez użytkownika.

W przypadku dezb. klientów przypisanych do poszczególnych skrzynek pocztowych możesz zażądać od firmy Microsoft oczyszczania określonych działów obsługi klienta podczas opuszczania usługi. Aby uzyskać informacje na temat procesu przeczyszczania danych i odwołań klawiszy, zobacz Odwoływanie kluczy i rozpoczynanie [procesu ścieżki przeczyszczania danych](customer-key-manage.md#revoke-your-keys-and-start-the-data-purge-path-process).

Odwołanie dostępu do kluczy w ramach opuszczenia usługi spowoduje usunięcie klucza dostępności, co spowoduje kryptograficzne usunięcie danych. Usuwanie kryptograficzne ogranicza ryzyko ponownego zarządzania danymi, które jest ważne zarówno w przypadku wymogów bezpieczeństwa, jak i zgodności.

**Funkcja DEP dla usługi SharePoint Online** i OneDrive dla Firm Ten funkcja dep jest używany do szyfrowania zawartości przechowywanej w u usługi SPO i usługach OneDrive dla Firm, w tym także plików Microsoft Teams przechowywanych w u usługi SPO. Jeśli korzystasz z funkcji wielolokalizacji, możesz utworzyć jedną funkcję DEP dla każdego geolokalizacji dla organizacji. Jeśli nie korzystasz z funkcji wielolokalizacji, możesz utworzyć tylko jedną funkcję dep na dzierżawę. Zapoznaj się ze szczegółami w [tece Konfigurowanie klucza klienta](customer-key-set-up.md).

### <a name="encryption-ciphers-used-by-customer-key"></a>Szyfrowania używane przez klucz klienta

Klucz klienta szyfruje klucze przy pomocą różnych szyfrowania, jak pokazano na poniższych ilustracjach.

Hierarchia kluczy używana dla dezpów szyfrowanych danych dla wielu Microsoft 365 jest podobna do hierarchii stosowanej w przypadku dezp w przypadku poszczególnych skrzynek Exchange Online pocztowych. Jedyna różnica polega na tym, że klucz skrzynki pocztowej zostanie zastąpiony odpowiadającym mu kluczem Microsoft 365 obciążeniem.

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>Szyfruj szyfrowania używane do szyfrowania kluczy do Exchange Online i Skype dla firm

![Encryption ciphers for Exchange Online customer key.](../media/customerkeyencryptionhierarchiesexchangeskype.png)

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Szyfruj szyfrowania używane do szyfrowania kluczy do SharePoint Online, OneDrive dla Firm i Teams plików

![Encryption ciphers for SharePoint Customer Key.](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>Artykuły pokrewne

- [Konfigurowanie klucza klienta](customer-key-set-up.md)

- [Zarządzanie kluczem klienta](customer-key-manage.md)

- [Obracanie lub obracanie klucza klienta lub klucza dostępności](customer-key-availability-key-roll.md)

- [Informacje o kluczu dostępności](customer-key-availability-key-understand.md)

- [Skrytka klienta](customer-lockbox-requests.md)

- [Szyfrowanie usługi](office-365-service-encryption.md)
