---
title: Microsoft Managed Desktop i Windows 11
description: Jak i kiedy Windows 11 w usłudze
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: b7a4366281172254a893c20dfd7519e2e8ef36d1
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63013371"
---
# <a name="microsoft-managed-desktop-and-windows-11"></a>Microsoft Managed Desktop i Windows 11

Po ogłoszeniu Windows 11 być może rozpoczęto planowanie migracji z Windows 11 w ramach starań o to, aby urządzenia z systemem Windows 10 były aktualne. W tym artykule przedstawiono ważne zagadnienia i o tym, Microsoft Managed Desktop będzie obsługiwać płynne przejścia w Twoich środowiskach. Aby uzyskać informacje Windows 11, zobacz omówienie [Windows 11](/windows/whats-new/windows-11).

Aby uzyskać szczegółowe instrukcje dotyczące instalacji Windows 11 na Twoich Microsoft Managed Desktop komputerach, zobacz Podgląd i testowanie wersji [Windows 11](../working-with-managed-desktop/test-win11-mmd.md) z Microsoft Managed Desktop.

## <a name="timeline-for-windows-10-and-windows-11"></a>Oś czasu dla Windows 10 i Windows 11

Windows 11 został ogólnie dostępny 4 października 2021 r. Jest ona gotowa do wdrożenia dla klientów konsumenckich i przedsiębiorstw i jest w pełni obsługiwana platformą. Począwszy od stycznia 2023 r., rozpoczniemy planowanie wdrożeń dla wszystkich Microsoft Managed Desktop, ale zapewnimy pełną pomoc techniczną dla tych, którzy chcą wdrożyć usługę Windows 11 szybciej. Skonsultujemy się i poradzymy administratorom, aby opracowywać i wdrażać plany migracji dla każdej dzierżawy w oparciu o gotowość techniczną i zagadnienia biznesowe.

Microsoft Managed Desktop będzie nadal obsługiwać Windows 10 równolegle do momentu zakończenia wsparcia dla przedsiębiorstw. Zobacz [Windows 10 informacji o wersji,](/windows/release-health/release-information) aby uzyskać informacje o cyklu życia.



## <a name="assessing-pre-release-versions-of-windows-11"></a>Ocena wersji wstępnej programu Windows 11

Ponad 95% urządzeń Microsoft Managed Desktop jest uprawnionych do Windows 11, dlatego warto wypróbować uaktualnienie na urządzeniach testowych przed wdrożeniem produkcyjnym. Aby uzyskać więcej Windows wymagań systemowych do 11, [zobacz Windows 11](/windows/whats-new/windows-11-requirements) wymagań. 

W Microsoft Managed Desktop urządzeniach możesz [dodać je do grupy testowych Windows 11](/microsoft-365/managed-desktop/working-with-managed-desktop/test-win11-mmd?view=o365-worldwide#add-devices-to-the-windows-11-test-group). Ta grupa otrzymuje kompilację ogólno Windows 11 wraz z ogólną Microsoft Managed Desktop podstawową. Po dodaniu do grupy urządzeń od jednego do dwóch dni urządzenie może wybrać nowe ustawienia i uzyskać możliwość Windows 11.

W przypadku urządzeń, które nie są zarządzane przez aplikację Microsoft Managed Desktop, przeczytaj wskazówki Endpoint Manager, aby [](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/endpoint-manager-simplifies-upgrades-to-windows-11/ba-p/2771886) dowiedzieć się więcej o wdrażaniu usługi Windows 11 samodzielnie. Jeśli masz urządzenia z systemem Windows 11 lub nowszym, zarejestruj je w programie Microsoft Managed Desktop. Nie będą one ponownie Windows 10.

## <a name="support-for-pre-release-windows-11-devices"></a>Pomoc techniczna dla wersji wstępnej Windows 11 urządzeń

W przypadku osób, które zrezygnowały z Windows 11 przed ogólną dostępnością, na urządzeniach mogą być zainstalowane kompilacje w wersji Preview. Microsoft Managed Desktop w tym stanie nie będzie oferowana kompilacja ogólno Windows 11, ale nadal będzie obsługiwana w rozwiązywaniu napotkanych problemów. Ponadto program Microsoft Managed Desktop wszystkie zarządzane urządzenia pod względami bezpieczeństwa i będzie odpowiadać na alerty niezależnie od tego, czy na urządzeniu jest uruchomiona kompilacja Windows 11 w wersji Preview. 

Ponieważ staramy się pomagać Ci w migracji do firmy Windows 11, zachowując produktywność, zachęcamy do zgłaszania wad platformy. W przypadku szerokiego wdrożenia produktu Windows 11 priorytetowo określamy wady, które będą blokować produktywność użytkowników Windows 10 urządzeniach.

## <a name="testing-application-compatibility"></a>Testowanie zgodności aplikacji

Zgodność aplikacji to jeden z najbardziej typowych problemów podczas migracji platform ze względu na możliwość zakłócenia wydajności pracy. Używamy kilku proaktywnych i reaktywnych środków, aby mieć pewność, że płynne przejścia aplikacji do Windows 11.

### <a name="proactive-measures"></a>Proaktywne działania

**Typowe aplikacje:** Firma Microsoft intensywnie testuje najpopularniejsze aplikacje i pakiety w przedsiębiorstwie wdrożone na kompilacjach pakietu Windows 11. We współpracy z zewnętrznymi wydawcami oprogramowania i wewnętrznymi zespołami produktu rozwiążemy wszelkie problemy wykryte podczas testowania. Aby uzyskać więcej informacji o naszych proaktywnych testach zgodności, zobacz [blog na temat zgodności aplikacji](https://blogs.windows.com/windowsexperience/2019/01/15/application-compatibility-in-the-windows-ecosystem/).

Aplikacje biznesowe **.** [](https://www.microsoft.com/en-us/testbase) Baza testowa to zasób, za pomocą którym wydawcy aplikacji i administratorzy IT mogą przesyłać aplikacje i testować przypadki, w których firma Microsoft może uruchamiać się na maszyny wirtualnej z uruchomionymi kompilacjami programu Windows 11 w bezpiecznym środowisku platformy Azure. Wyniki, testowanie szczegółowych informacji i analiza regresji dla każdego wykonywania testowego są dostępne dla Ciebie w prywatnym portalu Azure Portal. Microsoft Managed Desktop priorytety aplikacji biznesowych na potrzeby sprawdzania poprawności na podstawie danych dotyczących użycia i niezawodności aplikacji. Aby uzyskać więcej informacji na temat bazy testowej, zobacz [Baza testowa dla Microsoft 365](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/test-base-for-microsoft-365-microsoft-ignite-2021-updates/ba-p/2185566).

### <a name="reactive-measures"></a>Środki reagowania
Jeśli napotkasz problemy ze zgodnością aplikacji w środowiskach testowych lub produkcyjnych, możesz uzyskać pomoc techniczną bez po cenie, otwierając [żądanie usługi](/microsoft-365/managed-desktop/working-with-managed-desktop/test-win11-mmd?view=o365-worldwide#report-issues). W Windows 11 ta funkcja obejmuje wszystkie funkcje Office, Microsoft Edge, Teams i aplikacji biznesowych działających w najnowszych kompilacjach systemu operacyjnego. Usługa Microsoft App Assure bezpośrednio angażuje wydawców aplikacji w celu ustalania priorytetów i rozwiązywania problemów ze zgodnością aplikacji, gdy będzie to konieczne.

