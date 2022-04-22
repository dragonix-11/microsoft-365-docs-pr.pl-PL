---
title: Eliminowanie zagrożeń w Microsoft 365 Lighthouse przy użyciu Program antywirusowy Microsoft Defender
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
description: W przypadku dostawców usług zarządzanych korzystających z Microsoft 365 Lighthouse dowiedz się więcej o ograniczaniu zagrożeń za pomocą Program antywirusowy Microsoft Defender.
ms.openlocfilehash: da8a10b1ffc1932a6b4f84447028d2fa9b865e64
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2022
ms.locfileid: "65023662"
---
# <a name="mitigate-threats-in-microsoft-365-lighthouse-with-microsoft-defender-antivirus"></a>Eliminowanie zagrożeń w Microsoft 365 Lighthouse przy użyciu Program antywirusowy Microsoft Defender

Microsoft 365 Lighthouse umożliwia partnerom badanie i eliminowanie zagrożeń we wszystkich dzierżawach. Możesz również zainicjować skanowanie antywirusowe na urządzeniach, upewnić się, że urządzenia otrzymują najnowsze aktualizacje dla Program antywirusowy Microsoft Defender i przejrzeć oczekujące akcje po skanowaniu antywirusowym. Usługa Lighthouse obsługuje tylko urządzenia z systemem Windows 10 lub nowszym.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Microsoft 365 Lighthouse jest wdrażana tylko w dzierżawie partnera — nie w dzierżawach klientów, ale upewnij się, że Ty i Twoi dzierżawcy spełniacie wymagania wymienione w [Microsoft 365 Lighthouse wymaganiach](m365-lighthouse-requirements.md).

- Użytkownicy muszą uruchamiać Program antywirusowy Microsoft Defender (dołączone do Windows). Usługa Lighthouse nie obsługuje oprogramowania antywirusowego firmy innej niż Microsoft. Aby uzyskać więcej informacji, zobacz [Włączanie Program antywirusowy Microsoft Defender](/mem/intune/user-help/turn-on-defender-windows).

- Musisz być administratorem globalnym w dzierżawie partnera, do której się logujesz.

## <a name="investigate-active-threats"></a>Badanie aktywnych zagrożeń

Aby zbadać określone zagrożenie:

1. W okienku nawigacji po lewej stronie w usłudze Lighthouse wybierz pozycję **Zarządzanie zagrożeniami**.

2. Wybierz kartę **Zagrożenia** .

3. Z listy zagrożeń wybierz zagrożenie, które chcesz zbadać.

Okienko szczegółów zagrożenia zawiera następujące informacje:

| Kategoria                                      | Definicja                                                                                                   |
|-----------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Urządzenie i dzierżawa                             | Nazwa urządzenia i dzierżawa, w której znaleziono zagrożenie. Wybierz nazwę urządzenia, aby wyświetlić dodatkowe informacje. |
| Stan zagrożenia                                 | Stan zagrożenia.                                                                                    |
| Typ zagrożenia                                   | Typ zagrożenia.                                                                                              |
| Ważność zagrożenia                               | Ważność zagrożenia (poważne, wysokie, umiarkowane, niskie, nieznane)                                                    |
| Wystąpień                                     | Liczba wystąpień tego zagrożenia na urządzeniu.                                                    |
| Wykryto po raz pierwszy                                | Po pierwszym wykryciu zagrożenia na tym urządzeniu.                                                           |
| Dokumentacji                                 | Link do dodatkowych informacji o zagrożeniu.                                                             |
| Inne urządzenia w tej dzierżawie z tym zagrożeniem | Lista innych urządzeń w tej samej dzierżawie z tym samym aktywnym zagrożeniem.                                      |
| Inne dzierżawy z tym zagrożeniem                | Lista innych dzierżaw z tym samym aktywnym zagrożeniem.                                                         |

Aby zbadać zagrożenia na określonym urządzeniu:

1. W okienku nawigacji po lewej stronie w usłudze Lighthouse wybierz pozycję **Zarządzanie zagrożeniami**.

2. Wybierz kartę **Ochrona antywirusowa** .

3. Wybierz urządzenie z listy.

4. W okienku szczegółów urządzenia wybierz kartę **Bieżące zagrożenia** .

Usługa Lighthouse wyświetla wszystkie zagrożenia znalezione na urządzeniu. Aby wyświetlić szczegóły, wybierz zagrożenie.

## <a name="scan-for-threats-on-a-device"></a>Skanowanie pod kątem zagrożeń na urządzeniu

Szybkie skanowanie wyszukuje typowe lokalizacje, w których może znajdować się złośliwe oprogramowanie, takie jak klucze rejestru i znane foldery uruchamiania. Pełne skanowanie wyszukuje całe urządzenie. W większości przypadków szybkie skanowanie jest wystarczające i jest zalecaną opcją dla zaplanowanych skanów.

1. W okienku nawigacji po lewej stronie w usłudze Lighthouse wybierz pozycję **Zarządzanie zagrożeniami**.

2. Wybierz kartę **Ochrona antywirusowa** .

3. Z listy urządzeń wybierz urządzenie.

4. W okienku szczegółów urządzenia wybierz pozycję **Uruchom pełne skanowanie** lub **Uruchom szybkie skanowanie**.

Możesz również skanować wiele urządzeń, zaznaczając pole wyboru obok każdej nazwy urządzenia na liście, a następnie wybierając pozycję **Uruchom pełne skanowanie** lub **Uruchom szybkie skanowanie**.

## <a name="get-updates-for-microsoft-defender-antivirus"></a>Pobieranie aktualizacji dla Program antywirusowy Microsoft Defender

Aby zaktualizować Program antywirusowy Microsoft Defender na jednym urządzeniu:

1. W okienku nawigacji po lewej stronie w usłudze Lighthouse wybierz pozycję **Zarządzanie zagrożeniami**.

2. Wybierz kartę **Ochrona antywirusowa** .

3. Z listy urządzeń wybierz urządzenie.

4. W okienku szczegółów urządzenia wybierz pozycję **Aktualizuj oprogramowanie antywirusowe**.

Aktualizacje dla wielu urządzeń można uzyskać, zaznaczając pole wyboru obok każdej nazwy urządzenia na liście, a następnie wybierając pozycję **Aktualizuj oprogramowanie antywirusowe**.

Jeśli musisz utworzyć nowe zasady, wybierz pozycję **Aktualizuj zasady** w okienku szczegółów urządzenia. Lighthouse przekieruje Cię do Microsoft Endpoint Manager (MEM). Aby uzyskać więcej informacji na temat tworzenia zasad, zobacz [Tworzenie zasad zgodności w Microsoft Intune](/mem/intune/protect/create-compliance-policy).

## <a name="check-pending-antivirus-actions-on-a-device"></a>Sprawdzanie oczekujących akcji antywirusowych na urządzeniu

Po zastosowaniu kolejnych akcji do urządzenia zostanie wyświetlony komunikat oczekujący na akcję. Aby sprawdzić, które akcje oczekują na urządzeniu:

1. W okienku nawigacji po lewej stronie w usłudze Lighthouse wybierz pozycję **Zarządzanie zagrożeniami**.

2. Wybierz kartę **Ochrona antywirusowa** .

3. Z listy urządzeń wybierz urządzenie.

4. W okienku szczegółów urządzenia wybierz kartę **Stan akcji urządzenia** , aby wyświetlić oczekujące akcje.

## <a name="restart-a-device"></a>Ponowne uruchamianie urządzenia

Niektóre aktualizacje mogą wymagać ponownego uruchomienia urządzenia w celu poprawnego zainstalowania.

1. W okienku nawigacji po lewej stronie w usłudze Lighthouse wybierz pozycję **Zarządzanie zagrożeniami**.

2. Wybierz kartę **Ochrona antywirusowa** .

3. Z listy urządzeń wybierz urządzenie.

4. W okienku szczegółów urządzenia wybierz pozycję **Uruchom ponownie urządzenie**.

Możesz również ponownie uruchomić wiele urządzeń, zaznaczając pole wyboru obok każdej nazwy urządzenia na liście, a następnie wybierając pozycję **Uruchom ponownie urządzenie**.

## <a name="related-content"></a>Zawartość pokrewna

[Wymagania dotyczące Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (artykuł)\
[Omówienie strony Zarządzanie zagrożeniami w Microsoft 365 Lighthouse](m365-lighthouse-threat-management-page-overview.md) (artykuł)\
[Tworzenie zasad zgodności w Microsoft Intune](/mem/intune/protect/create-compliance-policy) (artykuł)\
[Włącz Program antywirusowy Microsoft Defender](/mem/intune/user-help/turn-on-defender-windows) (artykuł)\
[Microsoft Security Intelligence](https://www.microsoft.com/wdsi/threats) (strona internetowa)
