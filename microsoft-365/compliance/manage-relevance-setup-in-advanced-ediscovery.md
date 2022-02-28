---
title: Zarządzanie konfiguracją istotności w programie Advanced eDiscovery
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
description: Zapoznaj się z zaleceniami w zakresie konfigurowania szkolenia z tematu istotności Advanced eDiscovery oceny plików na podstawie ich istotności i wygenerowania wyników analitycznych.
ms.openlocfilehash: bed912c0631511e9d3d4839e5d6925de79554163
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987765"
---
# <a name="manage-relevance-setup-in-advanced-ediscovery-classic"></a>Zarządzanie konfiguracją istotności w Advanced eDiscovery (klasyczne)

> [!NOTE]
> Advanced eDiscovery organizacji wymaga Office 365 E3 z dodatku Advanced Compliance lub subskrypcji E5. Jeśli nie masz tego planu i chcesz wypróbować go Advanced eDiscovery, możesz utworzyć konta w celu wypróbowania Office 365 Enterprise [E5](https://go.microsoft.com/fwlink/p/?LinkID=698279). 
  
 Advanced eDiscovery technologii Istotność wykorzystuje oprogramowanie do oceny z przewodnikiem ekspertów do oceniania wyników na jego istotność. Advanced eDiscovery oceny istotności można użyć do oceny wczesnego przypadku, cullinga i przeglądu próbki plików. 
  
 Advanced eDiscovery do szkolenia na temat istotności oraz do znakowania plików poszczególnych przypadków. Advanced eDiscovery się z przeszkolonych próbek odpowiednich i nieuczonych plików w celu zapewnienia wyników istotności dla każdego pliku i generuje wyniki analityczne, których można użyć w trakcie procesu przeglądu pliku i po jego zakończeniu. 
  
## <a name="guidelines-for-setting-up-relevance-training"></a>Wskazówki dotyczące konfigurowania szkolenia na temat istotności

 W oknie Sprawy zbierania elektronicznych materiałów dowodowych  z wyprzedzeniem zaznacz sprawę i kliknij pozycję **Przejdź do sprawy**. Kliknij **pozycję Konfiguracja** \> **istotności.** Postępuj zgodnie z tymi zalecanymi wskazówkami, aby skonfigurować istotność. 
  
- **Otagowanie**: Skuteczność procesu szkolenia dotyczącej iteracyjnych istotności zależy od możliwości eksperta w zakresie precyzyjnego i spójnego otagowania próbek plików.

- **Problemy dotyczące sprawy**:
  
  - W przypadku każdego problemu należy korzystać z tego samego eksperta w całym procesie szkolenia dotyczącej istotności. Jednoczesne znakowanie tego samego problemu przez wielu ekspertów nie jest dozwolone.
  
  - Ustal, czy każda grupa plików dotyczy tylko konkretnego problemu.

  - Jeśli problem jest zbyt ogólnie zdefiniowany, może Advanced eDiscovery zbyt wiele plików, które nie są istotne. Jeśli problem zostanie zdefiniowany zbyt wąsko, proces szkolenia z tematem Istotność może potrwać dłużej. 

  - W trakcie każdego cyklu szkoleń dotyczące istotności program Advanced eDiscovery się na jednym aktywnym problemie, a następnie odpowiednio wyświetlane są pośrednie wyniki próbki.

  - W scenariuszu wielu problemów tryb próbkowania umożliwia uwzględnianie wyboru problemów w przetwarzaniu. Problemy zdefiniowane jako "wyłączone" nie są obsługiwane, dopóki tryb próbkowania nie zostanie zmieniony. Problem może być "bezczynny" lub "wł" tylko dla jednego eksperta.

  - Advanced eDiscovery można użyć do wygenerowania plików uprawnień kandydata. Skonfiguruj osobny problem z uprawnieniami. Jeśli to możliwe, najpierw przeszkolij i zwądek w celu oceny jego istotności, a następnie przeszkolij jedynie w celu przeszkolić w celu przeszkolinia wyłącznie na tym zestawie (ponowne załadowanie zestawu jako oddzielnej sprawy). 

  - Obliczenia wsadowe można wykonywać tylko wtedy, gdy nie ma otwartych próbek (po kliknięciu pozycji Obliczenie wsadu zostanie wyświetlona lista użytkowników z otwartymi próbkami). Aby "zamknąć" próbki innych użytkowników (należy to zrobić tylko wtedy, gdy ci użytkownicy nie otagują tych przykładów), administrator może użyć narzędzia "Modyfikowanie istotności" z opcją "Wszyscy użytkownicy, przykład".

- **Metadane**: Advanced eDiscovery się na zawartości. W ramach kryteriów istotności nie są rozważane metadane.

- **Bogatyość**: Jeśli po zakończeniu oceny richness danego problemu wynosi mniej niż 3%, rozważ iniekowanie szkolenia dotyczące istotności przy użyciu znanych i nie istotnych plików.

- **Rozmiar pliku**: Duże pliki (ponad 5 242 880 znaków wyodrębninego tekstu) są ignorowane w istotności. Pliki nie uczestniczą w procesie szkoleniowym nad istotnością i po obliczeniu partii nie otrzymuje się wyników oceny istotności. Do zestawu oceniania można dodać pliki o rozmiarze ponad 5 MB.

## <a name="setting-up-case-issues"></a>Konfigurowanie problemów ze sprawami

Parametry opisane w tej sekcji są dostępne w sekcji Advanced eDiscovery **Istotność** \> **.**
  
- Problemy trzeba przypisać do użytkownika, który przeszkoli pliki.

- Zaimportowane pliki należy następnie dodać do przetwarzanego ładowania.

- Starannie zdefiniuj i organizuj problemy, ponieważ może to mieć wpływ na wyniki szkolenia dotyczące istotności.

Po skonfigurowaniu parametrów recenzent/ekspert może rozpocząć szkolenie plików na **karcie Istotność** .
