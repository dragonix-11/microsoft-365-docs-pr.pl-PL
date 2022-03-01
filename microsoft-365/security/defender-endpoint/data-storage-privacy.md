---
title: Usługa Microsoft Defender for Endpoint data storage and privacy
description: Dowiedz się, jak program Microsoft Defender for Endpoint obsługuje prywatność i zbierane przez nie dane.
keywords: Microsoft Defender for Endpoint, data storage and privacy, storage, privacy, licensing, geolocation, data retention, data
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 7e6e530406b4211c62d315f26b8f956cf6bf1bde
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997832"
---
# <a name="microsoft-defender-for-endpoint-data-storage-and-privacy"></a>Usługa Microsoft Defender for Endpoint data storage and privacy

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

W tej sekcji osącz niektóre z najczęściej zadawanych pytań dotyczących prywatności i obsługi danych w programie Defender for Endpoint.

> [!NOTE]
> W tym dokumencie wyjaśniono szczegóły dotyczące przechowywania danych i prywatności związane z usługą Defender for Endpoint. Aby uzyskać więcej informacji dotyczących programu Defender for Endpoint oraz innych produktów i usług, takich jak Program antywirusowy Microsoft Defender i Windows, zobacz [Oświadczenie o ochronie prywatności firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=827576). Aby uzyskać [więcej informacji, Windows często](https://go.microsoft.com/fwlink/?linkid=827577) zadawane pytania dotyczące prywatności.

## <a name="what-data-does-microsoft-defender-for-endpoint-collect"></a>Jakie dane zbiera usługa Microsoft Defender for Endpoint?

Program Microsoft Defender for Endpoint będzie zbierać i przechowywać informacje ze skonfigurowanych urządzeń w dedykowanej i podzielonej na klienta dzierżawie przeznaczonej do celów administracyjnych, śledzenia i raportowania.

Zbierane informacje obejmują dane plików (takie jak nazwy plików, rozmiary i skróty), dane procesu (uruchomione procesy, skróty), dane rejestru, dane połączenia sieciowego (adresy IP i porty hosta) oraz szczegóły urządzenia (takie jak identyfikatory urządzeń, nazwy i wersja systemu operacyjnego).

Firma Microsoft przechowuje te dane bezpiecznie Microsoft Azure i utrzymuje je zgodnie z zasadami zachowania poufności informacji firmy [Microsoft i Centrum zaufania firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=827578).

Te dane umożliwiają programowi Defender dla punktu końcowego:

- Aktywne identyfikowanie wskaźników ataków (IOA) w organizacji
- Generowanie alertów w przypadku wykrycia możliwych ataków
- Zapewnij swoim operacjeom zabezpieczeń dostęp do urządzeń, plików i adresów URL związanych z sygnałami zagrożeń z Twojej sieci, co pozwoli na badanie i eksplorowanie obecności zagrożeń bezpieczeństwa w sieci.

Firma Microsoft nie używa Twoich danych do reklam.

## <a name="data-protection-and-encryption"></a>Ochrona i szyfrowanie danych

Usługa Defender for Endpoint używa najnowych technologii ochrony danych opartych na Microsoft Azure danych.

Istnieją różne aspekty związane z ochroną danych, które zajmuje nasza usługa. Szyfrowanie jest jednym z najważniejszych i obejmuje szyfrowanie danych w czasie spoczynku, szyfrowanie w locie i zarządzanie kluczami za pomocą magazynu kluczy. Aby uzyskać więcej informacji na temat innych technologii używanych przez usługę Defender for Endpoint, zobacz Omówienie [szyfrowania platformy Azure](/azure/security/security-azure-encryption-overview).

We wszystkich scenariuszach dane są szyfrowane przy użyciu minimalnego szyfrowania 256-bitowego [AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard) .

## <a name="data-storage-location"></a>Lokalizacja przechowywania danych

Program Defender for Endpoint działa w Microsoft Azure danych w Unii Europejskiej, Zjednoczonym Królestwie lub Stanach Zjednoczonych. Dane klienta zebrane przez usługę mogą być przechowywane w: (a) lokalizacji geograficznej dzierżawy określonej podczas inicjowania obsługi lub (b) jeśli usługa Defender for Endpoint używa innej usługi online firmy Microsoft do przetwarzania tych danych, geolokalizacja określona przez reguły przechowywania danych tej innej usługi online.

Dane klienta w postaci pseudonimizowanej mogą być również przechowywane w centralnym magazynie i systemach przetwarzania w Stanach Zjednoczonych.

Po skonfigurowaniu tej konfiguracji nie można zmienić lokalizacji przechowywania danych. Jest to wygodny sposób na zminimalizowanie ryzyka związanego ze zgodnością przez aktywne wybieranie lokalizacji geograficznych, w których będą przechowywane Twoje dane.

## <a name="is-my-data-isolated-from-other-customer-data"></a>Czy moje dane są odizolowane od innych danych klientów?

Tak, dane są izolowane za pomocą uwierzytelniania dostępu i podziału logicznego na podstawie identyfikatora klienta. Każdy klient może uzyskać dostęp tylko do danych zebranych z własnej organizacji i danych ogólnych, które dostarcza firma Microsoft.

## <a name="how-does-microsoft-prevent-malicious-insider-activities-and-abuse-of-high-privilege-roles"></a>Jak firma Microsoft zapobiega złośliwym czynnościom niejawnego programu testów i nadużyciom ról o wysokich uprawnieniach?

Deweloperzy i administratorzy firmy Microsoft mają domyślnie uprawnienia wystarczające do wykonywania przypisanych im obowiązków w celu wykonania i rozwoju usługi. Firma Microsoft wdraża kombinacje działań naprawczych, kontrolnych i reaktywnych, w tym następujących mechanizmów zabezpieczania przed nieautoryzowanymi działaniami dewelopera i/lub administracyjnymi:

- Ścisła kontrola dostępu do danych poufnych
- Kombinacje kontrolek, które znacznie ulepszają niezależne wykrywanie złośliwej aktywności
- Wiele poziomów monitorowania, rejestrowania i raportowania

Ponadto firma Microsoft przeprowadza testy weryfikacji w tle określonych pracowników operacyjnych i ogranicza dostęp do aplikacji, systemów i infrastruktury sieciowej proporcjonalnie do poziomu weryfikacji w tle. Pracownicy operacyjni postępują zgodnie z formalnym procesem, gdy są wymagani do uzyskania dostępu do konta klienta lub powiązanych informacji podczas wykonywania obowiązków.

Dostęp do danych dotyczących usług wdrożonych w centrum danych instytucji rządowych Microsoft Azure jest udzielany tylko personelowi operacyjnemu, który został przesieniowany i zatwierdzony do obsługi danych, które podlegają pewnym przepisom i wymaganiami rządowym, takim jak FedRAMP, NIST 800.171 (DIB), ITAR, IRS 1075, DoD L4 i CJIS.

## <a name="is-data-shared-with-other-customers"></a>Czy dane są udostępniane innym klientom?

L.p. Dane klienta są izolowane od innych klientów i nie są udostępniane. Jednak szczegółowe informacje o danych wynikających z przetwarzania przez firmę Microsoft, które nie zawierają żadnych danych specyficznych dla klienta, mogą być udostępniane innym klientom. Każdy klient może uzyskać dostęp tylko do danych zebranych z własnej organizacji i danych ogólnych, które dostarcza firma Microsoft.

## <a name="how-long-will-microsoft-store-my-data-what-is-microsofts-data-retention-policy"></a>Jak długo firma Microsoft będzie przechowywać moje dane? Jakie są zasady przechowywania danych firmy Microsoft?

### <a name="at-service-onboarding"></a>Przy dołączaniu do usługi

Domyślnie dane są zachowywane przez 180 dni. Można jednak określić zasady przechowywania danych. Czas przechowywania danych zależy od czasu przechowywania danych przez program Window Defender for Endpoint. Istnieje możliwość elastycznego wybierania w zakresie od jednego miesiąca do sześciu miesięcy w celu zaspokojenia potrzeb firmy w zakresie zgodności z przepisami.

### <a name="at-contract-termination-or-expiration"></a>W momencie rozwiązania lub wygaśnięcia umowy

Twoje dane zostaną zachowane i będą dostępne, gdy licencja jest w okresie prolongaty lub w trybie zawieszonym. Po upływie tego okresu dane te zostaną usunięte z systemów firmy Microsoft w celu ich nieodwracalnego usunięcia nie później niż 180 dni od zakończenia lub wygaśnięcia umowy.

### <a name="advanced-hunting-data"></a>Zaawansowane dane chłoniania

Zaawansowane szukanie to oparte na zapytaniach narzędzie do wyszukiwania zagrożeń, które pozwala eksplorować nawet 30 dni nieprzetworzone dane.

## <a name="can-microsoft-help-us-maintain-regulatory-compliance"></a>Czy firma Microsoft może pomóc nam w utrzymywaniu zgodności z przepisami?

Firma Microsoft udostępnia klientom szczegółowe informacje na temat programów firmy Microsoft dotyczących zabezpieczeń i zgodności, w tym raportów inspekcji i pakietów zgodności, aby ułatwić klientom ocenę usługi Defender for Endpoint pod względem własnych wymogów prawnych i prawnych. Program Defender for Endpoint uzyskał wiele certyfikatów, takich jak ISO, SOC, FedRAMP High i PCI, i nadal realizuje dodatkowe certyfikaty krajowe, regionalne i branżowe.

Dostarczając klientom zgodne, niezależnie zweryfikowane usługi, firma Microsoft ułatwia klientom osiągnięcie zgodności z przepisami w zakresie infrastruktury i aplikacji, które uruchamiają.

Aby uzyskać więcej informacji na temat raportów certyfikacji programu Defender for Endpoint, zobacz [Centrum zaufania firmy Microsoft](https://servicetrust.microsoft.com/). 

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-datastorage-belowfoldlink)
