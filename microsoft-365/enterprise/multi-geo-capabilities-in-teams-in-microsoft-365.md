---
title: Funkcje multi-Geo Capabilities w Microsoft Teams
ms.reviewer: daro
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
- m365solution-scenario
- m365solution-spintranet
ms.localizationpriority: medium
description: Dowiedz się, Teams z funkcjami Microsoft 365 multi-Geo.
ms.openlocfilehash: 0315a9ff0429c5e00c662bd7345a3b6a39a591c3
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019252"
---
# <a name="multi-geo-capabilities-in-microsoft-teams"></a>Funkcje multi-Geo w Microsoft Teams

Funkcje multi-Geo w Teams umożliwiają Teams danych czatu przechowywanych w spoczynku w określonej lokalizacji geograficznej. Dane czatu obejmują wiadomości czatu, w tym wiadomości prywatne, wiadomości kanałów i obrazy używane w czatach.

Teams użytkowników i grup używa preferowanej lokalizacji danych (PDL, Preferred Data Location) do określenia miejsca przechowywania danych. Jeśli plik PDL nie jest ustawiony lub jest nieprawidłowy, dane są przechowywane w centralnej lokalizacji dzierżawy.

> [!NOTE]
> Funkcje multi-Geo w Teams w lipcu 2021 r. Wiadomości czatu i kanałów zostaną automatycznie zmigrowane do odpowiedniej lokalizacji geograficznej w ciągu następnych kilku kwartałów. Wszystkie nowe zmiany w pliku PDL zostaną przetworzone po zakończeniu synchronizacji początkowej przez dzierżawę, a nowe zmiany w pliku PDL, których nie ujmuje w kolejce i będą przetwarzane w kolejności ich odsyłki.

## <a name="user-chat"></a>Czat użytkownika

Czat użytkownika obejmuje wiadomości jeden-do-jednego, jeden-do-wielu i prywatne wiadomości o spotkaniach.

Gdy zostanie utworzony nowy użytkownik, Teams jego plik PDL i przechowuje wszystkie dane czatu w tej lokalizacji geograficznej.

W przypadku istniejących użytkowników, jeśli administrator doda lub zmodyfikuje plik PDL dla użytkownika, dane czatu tego użytkownika zostaną dodane do kolejki migracji, aby zostały przeniesione do określonej lokalizacji geograficznej.

Lokalizacja przechowywania dla czatu jeden-do-jednego lub jeden-do-wielu jest oparta na pliku PDL osoby, która utworzyła czat. Jeśli plik PDL tego użytkownika zostanie zmieniony, czat zostanie zmigrowany do nowej lokalizacji geograficznej. Miejsce do przechowywania dla czatu spotkania jest oparte na pliku PDL organizatora spotkania.

Aby znaleźć bieżącą lokalizację danych danych Teams użytkownika, połącz się z programem [Teams PowerShell](/powershell/module/teams/connect-microsoftteams) i uruchom następujące polecenie:

```PowerShell
Get-MultiGeoRegion -EntityType User -EntityId <UPN>
```

## <a name="channel-messages"></a>Wiadomości kanałów

Każda Microsoft 365 ma preferowaną lokalizację danych (PDL), która oznacza lokalizację geograficzną, w której mają być przechowywane powiązane dane. Teams pdl dla grupy skojarzonej z każdym zespołem do określenia miejsca przechowywania danych wiadomości kanału dla tego zespołu. Obejmuje to kanały prywatne i czaty, które odbywa się w ramach spotkania na kanale.

Gdy użytkownik tworzy nowy zespół, plik PDL tego użytkownika określa, jaki plik PDL jest przypisany do grupy Microsoft 365 pliku. Plik PDL grupy określa miejsce przechowywania danych zespołu. Jeśli plik PDL tego użytkownika zostanie później zmieniony, plik PDL grupy nie zostanie zmieniony.

W przypadku istniejących zespołów, jeśli administrator doda lub zmodyfikuje plik PDL grupy programu Microsoft 365, która ma kopię zapasową zespołu, dane wiadomości tego zespołu będą dodawane do kolejki migracji, aby zostały przeniesione do określonej lokalizacji geograficznej.

Zmiana pliku PDL grupy Microsoft 365 kolejkuje Teams danych do migrowania do wybranej lokalizacji. Nie spowoduje to jednak automatycznej migracji witryny SharePoint lub plików skojarzonych z grupą. Należy przenieść witrynę oddzielnie, zgodnie z procedurami w te sposób: [Przenoszenie SharePoint lokalizacji geograficznej](/microsoft-365/enterprise/move-sharepoint-between-geo-locations). Należy wykonać obie czynności, aby uniknąć Teams danych i SharePoint danych dla jednej grupy w różnych lokalizacjach.

Aby znaleźć bieżącą lokalizację danych zespołu, połącz się z [programem Teams PowerShell](/powershell/module/teams/connect-microsoftteams) i uruchom następujące polecenie:

```PowerShell
Get-MultiGeoRegion -EntityType Group -EntityId <GroupObjectId>
```

## <a name="user-experience"></a>Środowisko użytkownika

Teams wiele lokalizacji geograficznych jest bezproblemowe dla użytkownika końcowego. Po zmianie pliku PDL użytkownika lub grupy odpowiednie dane zostaną w kolejce do migracji, a migracja zostanie nastąpi automatycznie, bez wpływu na użytkownika lub klienta programu Teams, nawet jeśli są aktywni w trakcie migracji.

## <a name="see-also"></a>Zobacz też

[Microsoft 365 konfiguracji dzierżawy wielodostępnych lokalizacji geograficznych](/microsoft-365/enterprise/multi-geo-tenant-configuration)

[Administrowanie środowiskiem wielolokalowym](administering-a-multi-geo-environment.md)

[Administrowanie Exchange Online w środowisku wielolokalowym](administering-exchange-online-multi-geo.md)
