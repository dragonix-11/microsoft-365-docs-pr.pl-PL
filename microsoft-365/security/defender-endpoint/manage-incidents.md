---
title: Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender zdarzeniami
description: Zarządzaj zdarzeniami, przypisując je, aktualizując jego stan lub ustawiając jego klasyfikację.
keywords: zdarzenia, zarządzanie, przypisywanie, stan, klasyfikacja, prawdziwy alert, alert fałsz
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
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: a84f7ba72acb4caf3e229f0bed4d997e123cc7ae
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466218"
---
# <a name="manage-microsoft-defender-for-endpoint-incidents"></a>Zarządzanie Ochrona punktu końcowego w usłudze Microsoft Defender zdarzeniami

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Zarządzanie zdarzeniami to istotny element każdej operacji jego obsługi. Możesz zarządzać zdarzeniami, wybierając je w kolejce **Zdarzenia** lub **w okienku zarządzania Zdarzeniami**. 


Wybranie zdarzenia w **kolejce Zdarzenia** otwiera okienko zarządzania zdarzeniami,  w którym można otworzyć stronę zdarzenia w celu jej szczegółowego otwarcia.

:::image type="content" source="images/atp-incidents-mgt-pane-updated.png" alt-text="Okienko zarządzania zdarzeniami" lightbox="images/atp-incidents-mgt-pane-updated.png":::

Możesz przypisać do siebie zdarzenia, zmienić stan i klasyfikację, zmienić nazwę lub dodać komentarz do nich, aby śledzić ich postęp.

> [!TIP]
> Aby uzyskać dodatkową widoczność informacji, nazwy zdarzeń są generowane automatycznie na podstawie atrybutów alertów, takich jak liczba punktów końcowych, których dotyczy problem, użytkownicy, źródła wykrywania lub kategorie. Umożliwia to szybkie zrozumienie zakresu zdarzenia.
>
> Przykład: *Wieloetapowe zdarzenie dotyczące wielu punktów końcowych zgłoszonych przez wiele źródeł.*
>
> Zdarzenia, które istniały przed rozpoczęciem automatycznego nazewnictwa zdarzeń, zachowają swoje nazwy.
>

:::image type="content" source="images/atp-incident-details-updated.png" alt-text="Strona ze szczegółami zdarzenia" lightbox="images/atp-incident-details-updated.png":::

## <a name="assign-incidents"></a>Przypisywanie zdarzeń
Jeśli zdarzenie nie zostało jeszcze przypisane, możesz wybrać pozycję **Przypisz** do mnie, aby przypisać zdarzenie do siebie. W ten sposób przyjmuje się, że właścicielem zdarzenia są nie tylko zdarzenia, ale także wszystkie skojarzone z nim alerty.

## <a name="set-status-and-classification"></a>Ustawianie stanu i klasyfikacji
### <a name="incident-status"></a>Stan zdarzenia
Zdarzenia można kategoryzować (jako **aktywne lub** rozwiązane), zmieniając ich status w trakcie postępowania w śledztwie. Ułatwia to organizowanie zdarzeń i zarządzanie tym, jak zespół może reagować na zdarzenia.

Na przykład analityk SoC może przejrzeć pilne **aktywne** zdarzenia w ciągu dnia i zdecydować o przydzieleniu ich do badania samodzielnie.

Alternatywnie analityk soc może ustawić zdarzenie jako **Rozwiązane** , jeśli zdarzenie zostało rozwiązane. 

### <a name="classification"></a>Klasyfikacja
Możesz nie ustawiać klasyfikacji lub zdecydować, czy zdarzenie ma być prawdziwe, czy fałszywe. Ułatwia to zespołowi zobaczenie wzorców i naukę na ich temat.

### <a name="add-comments"></a>Dodawanie komentarzy
Możesz dodawać komentarze i wyświetlać historyczne zdarzenia dotyczące zdarzenia, aby zobaczyć wprowadzone wcześniej zmiany.

Każda zmiana lub komentarz w alercie jest rejestrowany w sekcji Komentarze i historia.

Dodane komentarze natychmiast pojawiają się w okienku.



## <a name="related-topics"></a>Tematy pokrewne
- [Kolejka zdarzeń](/microsoft-365/security/defender-endpoint/view-incidents-queue)
- [Wyświetlanie i organizowanie kolejki Zdarzenia](view-incidents-queue.md)
- [Badanie zdarzeń](investigate-incidents.md)
