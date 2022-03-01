---
title: Konfigurowalne ustawienia Microsoft Managed Desktop
description: Informacje na temat konfigurowania ustawień za pomocą Microsoft Managed Desktop
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja, ustawienia, ustawienia konfigurowalne
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 910bd8d37853ce70acb6379599b0259446b0752e
ms.sourcegitcommit: 2c3b737e71038f843ef9e9ff4d5b99d6110b8ec5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2022
ms.locfileid: "63009676"
---
# <a name="configurable-settings---microsoft-managed-desktop"></a>Konfigurowanie ustawień — Microsoft Managed Desktop

Microsoft Managed Desktop wdraża ustawienia i zasady stosowane do wszystkich urządzeń zarządzanych przez Microsoft Managed Desktop. Aby uzyskać więcej informacji, zobacz [Konfiguracja urządzenia](../service-description/device-policies.md).

Konfigurowalne ustawienia Microsoft Managed Desktop administratorzy IT mogą dostosowywać i wdrażać ustawienia unikatowe dla potrzeb organizacji i firmy. Te ustawienia są nie tylko ustawieniami i zasadami konfiguracji urządzeń, które są zarządzane przez Microsoft Managed Desktop.  

Możliwość konfigurowania zmian ustawień jest wprowadzana w chmurze. Są one stosowane do Twoich Microsoft Managed Desktop w zdefiniowanych grupach wdrażania. Ten proces jest podobny do tego, Microsoft Managed Desktop zmianami w ustawieniach i zasadach konfiguracji urządzenia, zdefiniowanych i zarządzanych przez usługę. Korzystając z tego samego procesu, który jest Microsoft Managed Desktop do wdrażania zmian, kontynuując proces przenoszenia organizacji do przodu, korzystając z nowoczesnych rozwiązań do zarządzania it.

## <a name="when-to-use-configurable-settings"></a>Kiedy używać ustawień konfigurowalnych?

Ustawienia konfigurowalne należy konfigurować w następujących scenariuszach:

| Scenariusz | Opis |
| ------ | ------ |
| Proces dołączania | Microsoft Managed Desktop dostosowywanie ustawień konfigurowalnych podczas korzystania z usługi Microsoft Managed Desktop lub w przypadku korzystania z dużej liczby urządzeń (co najmniej 20). <br><br>Ustawianie kategorii jest konfigurowane w Microsoft Managed Desktop administratora. Po dojecheniu i dostępie do portalu administracyjnego możesz zdecydować, które kategorie ustawień chcesz dostosować dla organizacji. Następnie należy wprowadzić zmiany, rozmieścić zmiany we wdrożeniu, a następnie je wdrożyć. |
| Obsługa ustawień | Regularnie sprawdzaj ustawienia i w razie potrzeby je aktualizuje. Może być konieczne wprowadzić zmiany w celu obsługi zmiany w firmie. |

## <a name="setting-categories"></a>Ustawianie kategorii

Poniżej przedstawiono konfigurowalne kategorie ustawień, które można dostosowywać:

| Kategoria | Opis |
| ------ | ------ |
| [Obraz tła pulpitu](config-setting-ref.md#desktop-background-picture) | Dostosuj obraz tła pulpitu dla Microsoft Managed Desktop urządzeniach. |
| [Strony startowe przeglądarki](config-setting-ref.md#browser-start-pages) | Dodawanie stron startowych do używania z Microsoft Edge. |
| [Enterprise listy witryn w trybie online](config-setting-ref.md#enterprise-mode-site-list-location) | Dodawanie witryn i ich trybu zgodności. Witryny na liście będą rozpoczynać się w programie Internet Explorer. |
| [Zaufane witryny](config-setting-ref.md#trusted-sites) | Dodaj zaufane witryny i ustaw strefy zabezpieczeń dla każdej witryny. |
| [Wyjątki witryny serwera proxy](config-setting-ref.md#proxy) | Skonfiguruj numer adresu serwera proxy i numer portu oraz dodaj wyjątki witryny serwera proxy. |

Każdą kategorię ustawień można dostosować i wdrożyć samodzielnie. Zmiany można wdrażać jednocześnie w wielu kategoriach ustawień. W kategorii ustawień można jednak wdrożyć tylko jedną zmianę na raz.

Przykład:

- Zmiany w obrazach tła pulpitu i zaufanych witrynach można wdrażać w tym samym czasie jako własne wdrożenie.
- Nie można wdrożyć dwóch wdrożeń jednocześnie na stronach startowych przeglądarki. Najnowsze wdrożenie zatrzyma wcześniejsze wdrożenia, które nadal są w toku.

## <a name="configurable-setting-process"></a>Konfigurowalny proces konfigurowania

Microsoft Managed Desktop zaleca się stosowanie procedury podobnej do poniższej podczas konfigurowania ustawień dla organizacji:

| Krok  | Proces |
| ------ | ------ |
| **Krok 1. Planowanie** | <ol type="1"><li>Dowiedz się więcej o konfigurowaniu ustawień i decydowaniu, które kategorie ustawień mają zostać skonfigurowane dla organizacji.</li> <li>Utwórz oś czasu, gdy chcesz wdrożyć zmiany w każdej grupie.</li> <li>Zaplanuj komunikację z użytkownikami, którzy spełniają Wewnętrzne procesy zarządzania zmianami. Jeśli na przykład dodajesz strony startowe przeglądarki, poinformuj użytkowników, że po wdrożeniu będą mieli nowy zestaw stron startowych w przeglądarkach.</li></ol> |
| **Krok 2. Konfigurowanie i wdrażanie etapowe** | <ol type="1"><li>W portalu administracyjnym usługi Microsoft Managed Desktop konfigurować zmiany.</li><li>Rozmieź zmiany, aby były gotowe do wdrożenia.</li> <li>Pamiętaj, aby poinformować użytkowników o zmianach i o tym, jak te zmiany zmienią ich środowisko urządzenia.</li><li>Konfigurowanie i etapowe zmian w Microsoft Managed Desktop administratora. Aby uzyskać więcej informacji, [zobacz Dostosowywanie ustawień konfigurowalnych](config-setting-ref.md).</li></ol>|
| **Krok 3. Komunikowanie zmian** | <ol type="1"><li>Przekaż użytkownikom informacje o nadchodzących zmianach.</li> <li>W przypadku każdego wdrożenia dokończ komunikację w ramach procesu zarządzania zmianami. Należy wyraźnie zakomunikować wszelkie zmiany wpływające na sposób działania użytkownika lub na to, co zobaczy na jego urządzeniach.</li></ol> |
| **Krok 4. Wdrażanie zmian** | Wdeksuj zmiany, zaczynając od grupy Test. Grupa Test umożliwia sprawdzanie poprawności i rozwiązywanie problemów w grupie z mniejszą liczbą urządzeń przed wdrożeniem zmian na większych grupach urządzeń. <br><br>W przypadku problemów możesz przywrócić zmianę, zaktualizować ustawienie i określić etap nowego wdrożenia. Microsoft Managed Desktop, aby postępować zgodnie z podejściem strukturalnym i wdrożyć go w grupach w następującej kolejności: Test, Pierwsze, Szybkie, a następnie Szerokie. <br><br>Wszystkimi ustawieniami konfigurowalnymi zarządza się za pomocą Microsoft Managed Desktop administracyjnego. Aby uzyskać więcej informacji, zobacz [Wdrażanie zmian](config-setting-deploy.md). |
| **Krok 5. Śledzenie zmian** | Postęp zmian można śledzić w sekcji Stan wdrożenia. Dla każdego ustawienia możesz: <ul><li>**Śledzenie postępu:**  Śledzenie stanu po wdrożeniu zmiany. Stan zmieni się na W **toku**, a następnie na **pozycję Ukończono** lub **Nieudane**. Jeśli wdrożenie zakończy się niepowodzeniem, żądanie pomocy technicznej jest automatycznie otwierane na Microsoft Managed Desktop w celu zbadania problemu.</li> <li>**Zobacz wdrożoną wersję:** Każda wdrożona zmiana ma numer wersji.</li><li>**Przywróć zmiany:** Przywrócenie zmiany zatrzymuje bieżące wdrożenie. Przywróci wszystkie grupy do ostatnich zmian, które zostały wdrożone we wszystkich grupach. Wracasz do ostatniej znanej, dobrej wartości ustawienia.</li><li>**Sprawdź poprawność zmian:** Po zakończeniu wdrażania sprawdź, czy zmiany zostały zastosowane zgodnie z oczekiwaniami.</li></ul> |

Jeśli wdrożenie nie powiodło się lub nie można przywrócić zmiany, otwórz wniosek o pomoc [techniczną](admin-support.md) z Microsoft Managed Desktop operacji.

Aby uzyskać więcej informacji, zobacz [Wdrażanie i śledzenie ustawień, które można konfigurować](config-setting-deploy.md).

## <a name="additional-resources"></a>Dodatkowe materiały

- [Informacje dotyczące ustawień konfigurowalnych](config-setting-ref.md)
- [Wdrażanie ustawień konfigurowalnych](config-setting-deploy.md)
