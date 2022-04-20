---
title: Zarządzanie konfiguracją istotności w usłudze eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ms.assetid: fd6be6d3-2e8d-449d-9851-03ab7546e6aa
ROBOTS: NOINDEX, NOFOLLOW
description: Zapoznaj się z zaleceniami dotyczącymi konfigurowania trenowania istotności w usłudze eDiscovery (Premium), aby oceniać pliki według ich istotności i generować wyniki analityczne.
ms.openlocfilehash: 66afbb3b8e7d8c2a4e266aa7fb63dc8434f9c8a6
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64946028"
---
# <a name="manage-relevance-setup-in-ediscovery-premium-classic"></a>Zarządzanie konfiguracją istotności w usłudze eDiscovery (Premium) (wersja klasyczna)

> [!NOTE]
> Usługa Microsoft Purview eDiscovery (Premium) wymaga Office 365 E3 z dodatkiem Zaawansowana zgodność lub subskrypcją E5 dla organizacji. Jeśli nie masz tego planu i chcesz spróbować zbierania elektronicznych materiałów dowodowych (Premium), możesz [utworzyć konto próbne Office 365 Enterprise E5](https://go.microsoft.com/fwlink/p/?LinkID=698279). 
  
 Technologia eDiscovery (Premium) Relevance wykorzystuje specjalistyczne oprogramowanie do oceniania plików według ich istotności. Istotność zbierania elektronicznych materiałów dowodowych (Premium) może być używana do wczesnej oceny przypadków (ECA), uboju i przeglądu przykładów plików. 
  
 Funkcja zbierania elektronicznych materiałów dowodowych (Premium) obejmuje składniki do trenowania istotności i tagowania plików istotnych dla danego przypadku. Funkcja eDiscovery (Premium) uczy się z wytrenowanych przykładów odpowiednich i nieistotnych plików w celu zapewnienia wyników istotności dla każdego pliku i generuje wyniki analityczne, które mogą być używane podczas procesu przeglądu plików i po nich. 
  
## <a name="guidelines-for-setting-up-relevance-training"></a>Wytyczne dotyczące konfigurowania trenowania istotności

 W obszarze Z wyprzedzeniem zbierania elektronicznych materiałów dowodowych w oknie **Sprawy** wybierz przypadek i kliknij pozycję **Przejdź do sprawy**. Kliknij **pozycję Konfiguracja istotności**\>. Postępuj zgodnie z tymi zalecanymi wytycznymi, aby skonfigurować istotność. 
  
- **Tagowanie**: skuteczność iteracyjnego procesu trenowania istotności zależy od możliwości otagowania przykładów plików przez eksperta z dokładnością i spójnością.

- **Problemy ze sprawami**:
  
  - W przypadku każdego problemu należy użyć tego samego eksperta w całym procesie trenowania istotności. Jednoczesne tagowanie tego samego problemu przez wielu ekspertów jest niedozwolone.
  
  - Określ, czy każda grupa plików jest istotna tylko dla określonego problemu.

  - Jeśli problem jest zdefiniowany zbyt ogólnie, zbierania elektronicznych materiałów dowodowych (Premium) może przynieść zbyt wiele plików, które nie są istotne. Jeśli problem jest zdefiniowany zbyt wąsko, proces trenowania istotności może zająć więcej czasu. 

  - Podczas każdego cyklu trenowania istotności funkcja eDiscovery (Premium) koncentruje się na pojedynczym aktywnym problemie, a wyniki przykładu pośredniego są odpowiednio wyświetlane.

  - W scenariuszu z wieloma problemami tryb próbkowania umożliwia uwzględnienie wyboru problemów w przetwarzaniu. Problemy zdefiniowane jako "wyłączone" nie są obsługiwane, dopóki ich tryb próbkowania nie zostanie zmieniony. Problem może być "bezczynny" lub "włączony" tylko dla jednego eksperta.

  - eDiscovery (Premium) może służyć do generowania plików uprawnień kandydata. Skonfiguruj osobny problem dla uprawnień. Jeśli to możliwe, najpierw wytrenuj i ubite, aby uzyskać istotność, a następnie wytrenuj tylko dla zestawu ubitego (przeładuj zestaw ubity jako osobny przypadek). 

  - Obliczenia usługi Batch można wykonać tylko wtedy, gdy nie ma otwartych przykładów (po kliknięciu pozycji Obliczenia usługi Batch zostanie wyświetlona lista użytkowników z otwartymi przykładami). Aby "zamknąć" przykłady innych użytkowników (powinno to być wykonywane tylko wtedy, gdy ci użytkownicy nie tagują tych przykładów), administrator może użyć narzędzia "Modyfikuj istotność" z opcją "Przykład wszyscy użytkownicy".

- **Metadane**: wykrywanie elektroniczne (Premium) koncentruje się na zawartości. Nie uwzględnia metadanych jako części kryteriów istotności.

- **Bogactwo**: jeśli wartość richness dla problemu jest mniejsza niż 3% po ocenie, rozważ rozstawienie szkolenia istotności ze znanymi odpowiednimi i nieistotnymi plikami.

- **Rozmiar pliku**: Duże pliki (ponad 5 242 880 znaków wyodrębnianego tekstu) są ignorowane w polu Istotność. Pliki nie uczestniczą w procesie trenowania istotności i nie otrzymują oceny istotności po obliczeniu usługi Batch. Pliki o rozmiarze powyżej 5 MB można uwzględnić w zestawie oceny.

## <a name="setting-up-case-issues"></a>Konfigurowanie problemów ze sprawami

Parametry opisane w tej sekcji są dostępne w **konfiguracji istotności** \> zbierania elektronicznych materiałów dowodowych (Premium).
  
- Problemy muszą być przypisane do użytkownika, który będzie szkolił pliki.

- Następnie zaimportowane pliki muszą zostać dodane do przetworzonego obciążenia.

- Dokładnie zdefiniuj i organizuj problemy, ponieważ może to mieć wpływ na wyniki trenowania istotności.

Po ustawieniu parametrów recenzent/ekspert może rozpocząć trenowanie plików na karcie **Istotność** .
