---
title: Ograniczanie zagrożeń za pomocą Program antywirusowy Microsoft Defender
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: W przypadku dostawców usług zarządzanych (MSP) używających Microsoft 365 Lighthouse, dowiedz się, jak zminimalizować zagrożenia Program antywirusowy Microsoft Defender.
ms.openlocfilehash: 297c35104ae58efb1b7c58d3d1968158d42c0fce
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63315515"
---
# <a name="mitigate-threats-with-microsoft-defender-antivirus"></a>Ograniczanie zagrożeń za pomocą Program antywirusowy Microsoft Defender

Microsoft 365 Lighthouse umożliwia partnerom badanie zagrożeń dla wszystkich dzierżaw i ich ograniczanie. Możesz również zainicjować skanowanie antywirusowe na urządzeniach, upewnić się, że na urządzeniach są zainstalowane najnowsze aktualizacje oprogramowania Program antywirusowy Microsoft Defender oraz przeglądać oczekujące akcje po skanach antywirusowych. Lighthouse obsługuje tylko urządzenia z systemem Windows 10 lub nowszym.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Microsoft 365 Lighthouse jest wdrażana tylko w dzierżawie partnerskiej — nie w dzierżawach klientów, ale upewnij się, że Ty i dzierżawy Twoich klientów spełniacie wymagania wymienione Microsoft 365 Lighthouse [wymagań](m365-lighthouse-requirements.md).

- Użytkownicy muszą mieć uruchomiony program Program antywirusowy Microsoft Defender (dołączony do Windows). Lighthouse nie obsługuje oprogramowania antywirusowego innych niż firmy Microsoft. Aby uzyskać więcej informacji, [zobacz Włączanie Program antywirusowy Microsoft Defender](/mem/intune/user-help/turn-on-defender-windows).

- Musisz być administratorem globalnym w dzierżawie partnerskiej, do których się logujesz.

## <a name="investigate-active-threats"></a>Badanie aktywnych zagrożeń

Aby zbadać konkretne zagrożenie:

1. W lewym okienku nawigacji w latarni morskiej wybierz pozycję **Zarządzanie zagrożeniami**.

2. Wybierz **kartę Zagrożenia** .

3. Z listy zagrożeń wybierz zagrożenie, które chcesz zbadać.

Okienko szczegółów zagrożeń zawiera następujące informacje:

| Kategoria                                      | Definicja                                                                                                   |
|-----------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Urządzenie i dzierżawa                             | Nazwa urządzenia i dzierżawa, w której znajduje się zagrożenie. Wybierz nazwę urządzenia, aby wyświetlić dodatkowe informacje. |
| Stan zagrożenia                                 | Stan zagrożenia.                                                                                    |
| Typ zagrożenia                                   | Typ zagrożenia.                                                                                              |
| Zagrożenia zagrożenia                               | Istotność zagrożenia (poważny, wysoki, umiarkowany, niski, nieznany)                                                    |
| Wystąpienia                                     | Liczba wystąpień tego zagrożenia na urządzeniu.                                                    |
| Wykryte po raz pierwszy                                | Po wykryciu zagrożenia na tym urządzeniu po raz pierwszy.                                                           |
| Dokumentacja                                 | Link do dodatkowych informacji o zagrożeń.                                                             |
| To zagrożenie dotyczy innych urządzeń w tej dzierżawie | Lista innych urządzeń w tej samej dzierżawie z takim samym aktywnym zagrożeniem.                                      |
| To zagrożenie dla innych dzierżaw                | Lista innych dzierżaw z takim samym aktywnym zagrożeniem.                                                         |

Aby zbadać zagrożenia na określonym urządzeniu:

1. W lewym okienku nawigacji w latarni morskiej wybierz pozycję **Zarządzanie zagrożeniami**.

2. Wybierz **kartę Ochrona antywirusowa** .

3. Wybierz urządzenie z listy.

4. W okienku szczegółów urządzenia wybierz **kartę Bieżące** zagrożenia.

Lighthouse wyświetla wszystkie zagrożenia znalezione na urządzeniu. Aby wyświetlić szczegóły, wybierz zagrożenie.

## <a name="scan-for-threats-on-a-device"></a>Skanowanie w poszukiwaniu zagrożeń na urządzeniu

Szybkie skanowanie umożliwia wyszukiwanie typowych lokalizacji, w których może się znaleźć złośliwe oprogramowanie, takie jak klucze rejestru i foldery startowe. Pełne skanowanie przeszukuje całe urządzenie. W większości przypadków szybkie skanowanie jest wystarczające i jest zalecaną opcją w przypadku zaplanowanych skanów.

1. W lewym okienku nawigacji w latarni morskiej wybierz pozycję **Zarządzanie zagrożeniami**.

2. Wybierz **kartę Ochrona antywirusowa** .

3. Wybierz urządzenie z listy urządzeń.

4. W okienku szczegółów urządzenia wybierz pozycję **Uruchom pełne skanowanie** lub **Uruchom szybkie skanowanie**.

Możesz również przeskanować wiele urządzeń, zaznaczając pola wyboru obok nazw poszczególnych urządzeń na liście, a następnie wybierając pozycję **Uruchom pełne** skanowanie lub **Uruchom szybkie skanowanie**.

## <a name="get-updates-for-microsoft-defender-antivirus"></a>Pobierz aktualizacje dla Program antywirusowy Microsoft Defender

Aby zaktualizować Program antywirusowy Microsoft Defender na jednym urządzeniu:

1. W lewym okienku nawigacji w latarni morskiej wybierz pozycję **Zarządzanie zagrożeniami**.

2. Wybierz **kartę Ochrona antywirusowa** .

3. Wybierz urządzenie z listy urządzeń.

4. W okienku szczegółów urządzenia wybierz pozycję **Aktualizuj oprogramowanie antywirusowe**.

Możesz pobrać aktualizacje dla wielu urządzeń, zaznaczając pola wyboru obok nazw poszczególnych urządzeń na liście, a następnie wybierając pozycję **Aktualizuj oprogramowanie antywirusowe**.

Jeśli chcesz utworzyć nowe zasady, wybierz pozycję **Aktualizuj zasady** w okienku szczegółów urządzenia. Lighthouse przekieruje Cię do Microsoft Endpoint Manager (MEM). Aby uzyskać więcej informacji na temat tworzenia zasad, zobacz [Tworzenie zasad zgodności w programie Microsoft Intune](/mem/intune/protect/create-compliance-policy).

## <a name="check-pending-antivirus-actions-on-a-device"></a>Sprawdzanie oczekujących akcji antywirusowych na urządzeniu

Jeśli do urządzenia zostaną zastosowane kolejne akcje, otrzymasz wiadomość oczekującą na akcję. Aby sprawdzić, które akcje oczekują na urządzeniu:

1. W lewym okienku nawigacji w latarni morskiej wybierz pozycję **Zarządzanie zagrożeniami**.

2. Wybierz **kartę Ochrona antywirusowa** .

3. Wybierz urządzenie z listy urządzeń.

4. W okienku szczegółów urządzenia wybierz kartę Stan **akcji urządzenia** , aby wyświetlić oczekujące akcje.

## <a name="restart-a-device"></a>Ponowne uruchamianie urządzenia

Niektóre aktualizacje mogą wymagać ponownego uruchomienia urządzenia w celu poprawnego zainstalowania.

1. W lewym okienku nawigacji w latarni morskiej wybierz pozycję **Zarządzanie zagrożeniami**.

2. Wybierz **kartę Ochrona antywirusowa** .

3. Wybierz urządzenie z listy urządzeń.

4. W okienku szczegółów urządzenia wybierz pozycję **Uruchom ponownie urządzenie**.

Możesz także ponownie uruchomić wiele urządzeń, zaznaczając pole wyboru obok nazwy każdego urządzenia na liście, a następnie wybierając pozycję **Uruchom ponownie urządzenie**.

## <a name="related-content"></a>Zawartość pokrewna

[Wymagania dotyczące Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (artykuł)\
[Omówienie strony zarządzania zagrożeniami ](m365-lighthouse-threat-management-page-overview.md) (artykuł)\
[Tworzenie zasad zgodności w Microsoft Intune](/mem/intune/protect/create-compliance-policy) (artykuł)\
[Włączanie Program antywirusowy Microsoft Defender](/mem/intune/user-help/turn-on-defender-windows) (artykuł)\
[Microsoft Security Intelligence](https://www.microsoft.com/wdsi/threats) (strona sieci Web)