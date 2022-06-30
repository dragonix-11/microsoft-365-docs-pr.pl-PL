---
title: Ochrona punktu końcowego w usłudze Microsoft Defender magazyn danych i prywatność
description: Dowiedz się, jak Ochrona punktu końcowego w usłudze Microsoft Defender obsługuje prywatność i zbierane dane.
keywords: Ochrona punktu końcowego w usłudze Microsoft Defender, magazyn danych i prywatność, magazyn, prywatność, licencjonowanie, geolokalizacja, przechowywanie danych, dane
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
ms.openlocfilehash: d1d8ad0a16129e909476891291c0b2c0f0d54956
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2022
ms.locfileid: "66554152"
---
# <a name="microsoft-defender-for-endpoint-data-storage-and-privacy"></a>Ochrona punktu końcowego w usłudze Microsoft Defender magazyn danych i prywatność

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

W tej sekcji opisano niektóre z najczęściej zadawanych pytań dotyczących prywatności i obsługi danych w usłudze Defender for Endpoint.

> [!NOTE]
> W tym dokumencie wyjaśniono szczegóły magazynu danych i prywatności związane z usługą Defender for Endpoint. Aby uzyskać więcej informacji dotyczących usługi Defender for Endpoint oraz innych produktów i usług, takich jak program antywirusowy Microsoft Defender i system Windows, zobacz [Zasady zachowania poufności informacji firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=827576). Aby uzyskać więcej informacji, zobacz również [Często zadawane pytania dotyczące prywatności systemu Windows](https://go.microsoft.com/fwlink/?linkid=827577) .

## <a name="what-data-does-microsoft-defender-for-endpoint-collect"></a>Jakie dane zbiera Ochrona punktu końcowego w usłudze Microsoft Defender?

Ochrona punktu końcowego w usłudze Microsoft Defender będzie zbierać i przechowywać informacje ze skonfigurowanych urządzeń w dedykowanej i oddzielonej dzierżawie klienta specyficznej dla usługi na potrzeby administrowania, śledzenia i raportowania.

Zbierane informacje obejmują dane plików (takie jak nazwy plików, rozmiary i skróty), dane procesu (uruchomione procesy, skróty), dane rejestru, dane połączenia sieciowego (adresy IP hosta i porty) oraz szczegóły urządzenia (takie jak identyfikatory urządzeń, nazwy i wersja systemu operacyjnego).

Firma Microsoft przechowuje te dane bezpiecznie na platformie Microsoft Azure i utrzymuje je zgodnie z zasadami ochrony prywatności firmy Microsoft i [Zasadami Centrum zaufania firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=827578).

Te dane umożliwiają usłudze Defender for Endpoint:

- Proaktywne identyfikowanie wskaźników ataków (IOA) w organizacji
- Generowanie alertów w przypadku wykrycia możliwego ataku
- Udostępnij operacje zabezpieczeń z widokiem na urządzenia, pliki i adresy URL związane z sygnałami zagrożeń z sieci, umożliwiając badanie i badanie obecności zagrożeń bezpieczeństwa w sieci.

Firma Microsoft nie używa Twoich danych do reklamowania.

## <a name="data-protection-and-encryption"></a>Ochrona i szyfrowanie danych

Usługa Defender for Endpoint wykorzystuje najnowocześniejsze technologie ochrony danych oparte na infrastrukturze platformy Microsoft Azure.

Istnieją różne aspekty związane z ochroną danych, o które dba nasza usługa. Szyfrowanie jest jednym z najważniejszych i obejmuje szyfrowanie danych magazynowanych, szyfrowanie w locie i zarządzanie kluczami za pomocą Key Vault. Aby uzyskać więcej informacji na temat innych technologii używanych przez usługę Defender for Endpoint, zobacz [Omówienie szyfrowania platformy Azure](/azure/security/security-azure-encryption-overview).

We wszystkich scenariuszach dane są szyfrowane przy użyciu 256-bitowego [szyfrowania AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard) co najmniej.

## <a name="data-storage-location"></a>Lokalizacja magazynu danych

Usługa Defender for Endpoint działa w centrach danych platformy Microsoft Azure w Unii Europejskiej, Wielkiej Brytanii lub w Stany Zjednoczone. Dane klienta zebrane przez usługę mogą być przechowywane w: (a) lokalizacji geograficznej dzierżawy, jak określono podczas aprowizacji, lub (b) jeśli usługa Defender for Endpoint używa innej usługi online firmy Microsoft do przetwarzania takich danych, geolokalizacji zdefiniowanej przez reguły przechowywania danych tej innej usługi online.

Dane klientów w postaci pseudonimizowanej mogą być również przechowywane w centralnych systemach magazynowania i przetwarzania w Stany Zjednoczone.

Po skonfigurowaniu nie można zmienić lokalizacji przechowywania danych. Zapewnia to wygodny sposób minimalizowania ryzyka zgodności przez aktywne wybieranie lokalizacji geograficznych, w których będą znajdować się dane.

## <a name="is-my-data-isolated-from-other-customer-data"></a>Czy moje dane są odizolowane od innych danych klientów?

Tak, dane są izolowane za pomocą uwierzytelniania dostępu i logicznego podziału na podstawie identyfikatora klienta. Każdy klient może uzyskiwać dostęp tylko do danych zebranych z własnej organizacji i ogólnych danych udostępnianych przez firmę Microsoft.

## <a name="how-does-microsoft-prevent-malicious-insider-activities-and-abuse-of-high-privilege-roles"></a>W jaki sposób firma Microsoft zapobiega złośliwym działaniom niejawnych testerów i nadużywaniu ról o wysokich uprawnieniach?

Deweloperzy i administratorzy firmy Microsoft mają zgodnie z projektem wystarczające uprawnienia do wykonywania przypisanych im obowiązków związanych z działaniem i rozwijaniem usługi. Firma Microsoft wdraża kombinacje mechanizmów zapobiegawczych, detektywistycznych i reaktywnych, w tym następujących mechanizmów ochrony przed nieautoryzowanym deweloperem i/lub działaniami administracyjnymi:

- Ścisła kontrola dostępu do danych poufnych
- Kombinacje kontrolek, które znacznie usprawniają niezależne wykrywanie złośliwych działań
- Wiele poziomów monitorowania, rejestrowania i raportowania

Ponadto firma Microsoft przeprowadza kontrole weryfikacji przeszłości niektórych pracowników operacyjnych i ogranicza dostęp do aplikacji, systemów i infrastruktury sieci proporcjonalnie do poziomu weryfikacji przeszłości. Pracownicy ds. operacji postępują zgodnie z formalnym procesem, gdy są oni zobowiązani do uzyskania dostępu do konta klienta lub powiązanych informacji w ramach wykonywania swoich obowiązków.

Dostęp do danych dla usług wdrożonych w centrach danych firmy Microsoft Azure Government jest udzielany tylko pracownikom operacyjnym, którzy zostali poddani kontroli i zatwierdzeniu do obsługi danych podlegających określonym przepisom i wymaganiom rządowym, takim jak FedRAMP, NIST 800.171 (DIB), ITAR, IRS 1075, DoD L4 i CJIS.

## <a name="is-data-shared-with-other-customers"></a>Czy dane są udostępniane innym klientom?

Nie. Dane klientów są odizolowane od innych klientów i nie są udostępniane. Jednak szczegółowe informacje na temat danych wynikających z przetwarzania przez firmę Microsoft, które nie zawierają żadnych danych specyficznych dla klienta, mogą być udostępniane innym klientom. Każdy klient może uzyskiwać dostęp tylko do danych zebranych z własnej organizacji i ogólnych danych udostępnianych przez firmę Microsoft.

## <a name="how-long-will-microsoft-store-my-data-what-is-microsofts-data-retention-policy"></a>Jak długo firma Microsoft będzie przechowywać moje dane? Jakie są zasady przechowywania danych firmy Microsoft?

### <a name="at-service-onboarding"></a>Dołączanie do usługi

Domyślnie dane są przechowywane przez 180 dni; Można jednak określić zasady przechowywania danych. Określa to, jak długo Ochrona punktu końcowego w usłudze Microsoft Defender będą przechowywać dane. Istnieje elastyczność wyboru w zakresie od jednego miesiąca do sześciu miesięcy w celu spełnienia wymagań firmy w zakresie zgodności z przepisami.

### <a name="at-contract-termination-or-expiration"></a>W momencie wypowiedzenia lub wygaśnięcia umowy

Twoje dane będą przechowywane i będą dostępne, gdy licencja jest w trybie prolongaty lub wstrzymania. Po upływie tego okresu te dane zostaną usunięte z systemów firmy Microsoft, aby były nieodwracalne, nie później niż 180 dni od zakończenia lub wygaśnięcia umowy.

### <a name="advanced-hunting-data"></a>Zaawansowane dane wyszukiwania zagrożeń

Zaawansowane wyszukiwanie zagrożeń to oparte na zapytaniach narzędzie do wyszukiwania zagrożeń, które umożliwia eksplorowanie nieprzetworzonych danych przez maksymalnie 30 dni.

## <a name="can-microsoft-help-us-maintain-regulatory-compliance"></a>Czy firma Microsoft może pomóc nam utrzymać zgodność z przepisami?

Firma Microsoft udostępnia klientom szczegółowe informacje na temat programów zabezpieczeń i zgodności firmy Microsoft, w tym raportów inspekcji i pakietów zgodności, aby pomóc klientom ocenić usługę Defender dla punktów końcowych w stosunku do własnych wymagań prawnych i regulacyjnych. Usługa Defender for Endpoint uzyskała szereg certyfikatów, w tym ISO, SOC, FedRAMP High i PCI, i nadal dąży do uzyskania dodatkowych certyfikatów krajowych, regionalnych i branżowych.

Udostępniając klientom zgodne, niezależnie zweryfikowane usługi, firma Microsoft ułatwia klientom osiągnięcie zgodności z infrastrukturą i aplikacjami, które uruchamiają.

Aby uzyskać więcej informacji na temat raportów certyfikacji usługi Defender for Endpoint, zobacz [Centrum zaufania firmy Microsoft](https://servicetrust.microsoft.com/). 

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-datastorage-belowfoldlink)
