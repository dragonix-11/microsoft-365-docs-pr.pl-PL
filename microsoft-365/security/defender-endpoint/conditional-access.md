---
title: Włączanie dostępu warunkowego w celu lepszej ochrony użytkowników, urządzeń i danych
description: Włącz dostęp warunkowy, aby uniemożliwić uruchamianie aplikacji, jeśli urządzenie jest uznawane za ryzyko i aplikacja jest określona jako niezgodne.
keywords: dostęp warunkowy, blokowanie aplikacji, poziom zabezpieczeń, intune,
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 8ee1b1542eb2e737da509ce12ad9c2a605a4ffa5
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2021
ms.locfileid: "62996744"
---
# <a name="enable-conditional-access-to-better-protect-users-devices-and-data"></a>Włączanie dostępu warunkowego w celu lepszej ochrony użytkowników, urządzeń i danych

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-conditionalaccess-abovefoldlink)

Dostęp warunkowy to funkcja, która ułatwia lepszą ochronę informacji o użytkownikach i przedsiębiorstwie, upewniąc się, że tylko bezpieczne urządzenia mają dostęp do aplikacji.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4byD1]

Dzięki dostępowi warunkoweowi możesz sterować dostępem do informacji przedsiębiorstwa na podstawie poziomu ryzyka urządzenia. Pomaga to zachować zaufanych użytkowników na zaufanych urządzeniach przy użyciu zaufanych aplikacji.

Możesz zdefiniować warunki zabezpieczeń, w których urządzenia i aplikacje mogą uruchamiać informacje z Twojej sieci i uzyskać do nich dostęp, wymuszając zasady zatrzymania działania aplikacji do momentu, gdy urządzenie wróci do stanu zgodnego.

Implementacja dostępu warunkowego w usłudze Defender dla punktu końcowego jest oparta na zasadach zgodności urządzeń Microsoft Intune (Intune) i zasadach dostępu warunkowego usługi Azure Active Directory (Azure AD).

Zasady zgodności są używane z dostępem warunkowym w celu umożliwienia dostępu do aplikacji tylko tym urządzeniem, które spełniają co najmniej jedną regułę zasad zgodności urządzenia.

## <a name="understand-the-conditional-access-flow"></a>Opis przepływu dostępu warunkowego

Dostęp warunkowy jest zapewniany, dzięki czemu w przypadku zagrożenia na urządzeniu dostęp do poufnej zawartości jest blokowany do momentu jego rozwiązania.

Przepływ zaczyna się od tego, że urządzenia są postrzegane jako niskie, średnie lub wysokie ryzyko. Te określenia ryzyka są następnie wysyłane do usługi Intune.

W zależności od sposobu skonfigurowania zasad w usłudze Intune dostęp warunkowy można tak skonfigurować, aby po dochowyniu określonych warunków zasady zostały zastosowane.

Możesz na przykład skonfigurować usługę Intune w celu stosowania dostępu warunkowego na urządzeniach o wysokim poziomie ryzyka.

W usłudze Intune zasady zgodności urządzenia są używane w połączeniu z dostępem warunkowym usługi Azure AD w celu zablokowania dostępu do aplikacji. Równolegle jest uruchomiony zautomatyzowany proces badania i rozwiązywania problemów.

 Użytkownik może nadal korzystać z urządzenia w trakcie automatycznego badania i rozwiązywania problemów, ale dostęp do danych przedsiębiorstwa jest blokowany do momentu pełnego podjęcia działań naprawczych.

Aby rozwiązać problem z ryzykiem znalezionym na urządzeniu, musisz przywrócić zgodne urządzenie. Urządzenie powraca do stanu zgodnego, jeśli nie ma żadnego ryzyka związanego z tym urządzeniem.

Istnieją trzy sposoby rozwiązania tego ryzyka:

1. Użyj ręcznego lub automatycznego rozwiązywania problemów.
2. Usuwaj aktywne alerty na urządzeniu. Spowoduje to usunięcie ryzyka z urządzenia.
3. Możesz usunąć urządzenie z aktywnych zasad, a w konsekwencji dostęp warunkowy nie zostanie zastosowany na urządzeniu.

Ręczne działania naprawcze wymagają, aby administrator zabezpieczeń zbadał alert i rozwiązał ryzyko widoczne na urządzeniu. Automatyczne rozwiązywanie problemów jest konfigurowane za pomocą ustawień konfiguracji podanych w poniższej sekcji Konfigurowanie [dostępu warunkowego](configure-conditional-access.md).

Gdy to ryzyko zostanie usunięte za pośrednictwem ręcznego lub automatycznego rozwiązywania problemów, urządzenie wraca do zgodnego stanu i zostanie przyznany dostęp do aplikacji.

W poniższej przykładowej sekwencji zdarzeń wyjaśniono działanie dostępu warunkowego:

1. Użytkownik otworzy złośliwy plik, a program Defender for Endpoint oznaczy urządzenie jako najbardziej ryzykowne.
2. Ocena wysokiego ryzyka jest przekazywana do usługi Intune. Równolegle jest inicjowane zautomatyzowane badanie w celu rozwiązania zidentyfikowanego zagrożenia. Można też ręcznie wykonać działania naprawcze w celu rozwiązania zidentyfikowanego zagrożenia.
3. Na podstawie zasad utworzonych w usłudze Intune urządzenie jest oznaczone jako niezgodne. Ocena jest następnie przekazywane do usługi Azure AD za pomocą zasad dostępu warunkowego Intune. W usłudze Azure AD odpowiednie zasady są stosowane do blokowania dostępu do aplikacji.
4. Ręczne lub zautomatyzowane badania i działania naprawcze zostaną ukończone i zagrożenie zostanie usunięte. Usługa Defender for Endpoint widzi, że nie ma ryzyka związanego z urządzeniem, a usługa Intune ocenia urządzenie jako zgodne. Usługa Azure AD stosuje zasady, które umożliwiają dostęp do aplikacji.
5. Użytkownicy mogą teraz uzyskać dostęp do aplikacji.

## <a name="related-topic"></a>Temat pokrewny

- [Konfigurowanie dostępu warunkowego w programie Microsoft Defender dla punktu końcowego](configure-conditional-access.md)
