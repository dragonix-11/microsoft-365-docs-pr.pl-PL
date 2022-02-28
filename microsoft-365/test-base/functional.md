---
title: Testy funkcjonalności na podstawie testu
description: Szczegółowe informacje na temat testowania aplikacji przy użyciu istniejących zautomatyzowanych testów funkcjonalnych
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: f64480d66cd91dc4b08f9694331cfe0d9c130ee4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984954"
---
# <a name="functional-testing"></a>Testy funkcjonalności

Jako dostawca oprogramowania, możesz teraz przeprowadzać niestandardowe testy funkcjonalności przy użyciu wybranej struktury testowej — za pośrednictwem samoobsługowej bazy testowej dla portalu M365. 

Podczas początkowego uruchamiania usługi zaoferowali test "Od klienta", który jest wstępnie zdefiniowanym zestawem testów opartym na standardowym skryptach. Jednak to nie może zapewnić pełnego zakresu testów dla wielu niezależnych dostawców oprogramowania (ISV). 

Dlatego w odpowiedzi na opinie użytkowników udostępniamy naszym plikom isv możliwość przekazywania zautomatyzowanych testów funkcjonalnych.

Aby korzystać z tej funkcji, wykonaj następujące czynności:

1. Upload pliki (pliki binarne, zależności i skrypty) jako jeden .zip pliku.
2. Wybierz, czy chcesz ponownie uruchomić testowe maszyny wirtualne w różnych miejscach wykonywania.
3. Zarządzaj dostępnymi opcjami skryptów.
4. Wybierz, kiedy zastosować aktualizację Windows maszyny wirtualnej podczas wykonywania.

Poniżej wyróżnione są szczegółowe opisy powyższych kroków:

**Upload funkcjonalny pakiet testowy**

Aby rozpocząć, przejdź do strony Upload aplikacji, wybierz pozycję Upload nowej aplikacji w obszarze Wykaz aplikacji w menu nawigacji po lewej stronie w portalu Test base for M365 na platformie Azure. W tym miejscu:

Karta 1 — Wprowadzanie podstawowych informacji. Podaj nazwę i wersję aplikacji. W opcji Typ testu wybierz pozycję ```Functional tests```. 

*Pamiętaj, że domyślnie wymagana jest opcja "Out-of-Box" (OOB).*


![Wybierz kartę testowania funkcjonalności.](Media/functional_testing_tab1.png)

Karta 2 — Upload składników pakietu, przesyłając plik zip z całym testem (pliki binarne, zależności, skrypty itp.). 

Zobacz aka.ms/usl-package-outline, aby uzyskać szczegółowe informacje. (Uwaga: Zarówno skrypty testowe, jak i zawartość testu funkcjonalności powinny zostać umieszczone w tym samym pliku zip). Obecnie rozmiar pliku jest ograniczony do 2 GB.

Karta 3 — konfigurowanie zadań testowych od urządzenia do pracy i funkcji. W tym miejscu wybierz ścieżki do skryptów programu PowerShell, które będą instalować, uruchamiać, zamykać i odinstalowywać aplikacje (w przypadku środowiska Out-of-Box), a także ścieżki do wszystkich skryptów niestandardowych w celu przeprowadzenia testu działania. **(Uwaga: skrypt odinstalowywania aplikacji jest opcjonalny).**

Obecnie na testy funkcjonalne możesz przekazać od 1 do 8 skryptów. (Jeśli potrzebujesz większej liczby skryptów, opublikuj ten wpis).

![Upload maksymalnie 8 skryptów ze testami funkcjonalnymi.](Media/functional_testing_tab3.png)

(Opcjonalnie) Skonfiguruj ponowne uruchomienie po instalacji. Niektóre aplikacje wymagają ponownego uruchomienia po instalacji. 

Wybierz ```Reboot After Execution``` dla określonego skryptu na karcie Zadania, jeśli chcesz przeprowadzić ponowne uruchomienie po wykonaniu tego skryptu.

Karta 4 . Wybierz, kiedy ma zostać zainstalowana Windows: Aplikacja poprawki aktualizacji Windows jest wykonywana przed dowolnym skryptem. Zaleca się zainstalowanie po zainstalowaniu Windows aplikacji, aby dokładnie naśladować scenariusze używania aplikacji w świecie rzeczywistym.

![Aktualizację Windows można zainstalować po określonym skrypcie.](Media/functional_testing_tab4.png)

Karta 5 . Przejrzyj i utwórz pakiet. Po zakończeniu czynności wymienionych powyżej wybierz pozycję ```Create``` , aby zakończyć proces przekazywania.

Po utworzeniu pakietu możesz sprawdzić stan weryfikacji przesyłki.

Uruchamiamy test początkowy, aby zainstalować, uruchomić, zamknąć i odinstalować aplikację. Dzięki temu możemy sprawdzić, czy Twój pakiet można zainstalować na naszej usłudze bez błędów.

Proces weryfikacji może potrwać do 24 godzin. Po zakończeniu weryfikacji ```Manage packages``` w menu będzie wyświetlony stan, który może być jedną z dwóch pozycji:

1. Weryfikacja zakończy się powodzeniem: Pakiet zostanie automatycznie przetestowany pod kątem wersji wstępnej Windows aktualizacji wybranych kompilacji systemu operacyjnego.
lub
2. Weryfikacja kończy się niepowodzeniem: Konieczne będzie badanie przyczyn niepowodzenia, rozwiązanie problemu i ponowne przekazanie pakietu.

O jednym z wyników zostanie również powiadomiony za pośrednictwem ikony powiadomień w portalu Azure Portal.
