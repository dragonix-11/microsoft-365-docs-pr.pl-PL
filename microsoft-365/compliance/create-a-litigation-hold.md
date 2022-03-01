---
title: Tworzenie postępowania sądowego
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid: MET150
ms.assetid: 39db1659-0b12-4243-a21c-2614512dcb44
description: Dowiedz się, jak umieścić skrzynkę pocztową w związku z postępowaniem sądowym z zachowaniem całej zawartości skrzynki pocztowej podczas śledztwa.
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
ms.openlocfilehash: d105813d7e34ece7641421bc7fed10919dda618e
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021167"
---
# <a name="create-a-litigation-hold"></a>Tworzenie postępowania sądowego

Możesz umieścić skrzynkę pocztową w związku z postępowaniem sądowym w celu zachowania całej zawartości skrzynki pocztowej, w tym elementów usuniętych i oryginalnych wersji elementów zmodyfikowanych. Po włączeniu skrzynki pocztowej użytkownika do archiwizacji w związku z postępowaniem sądowym zawartość archiwacyjna skrzynka pocztowa użytkownika (jeśli jest włączona) również jest zachowywana. Podczas tworzenia blokowania można określić czas trwania (nazywany także holdm opartym na czasie), aby usunięte i zmodyfikowane elementy zostały zachowane przez określony okres, a następnie trwale usunięte ze skrzynki pocztowej. Możesz też po prostu przechowywać zawartość przez czas nieograniczony ( *nazywany nieskończonym* zawieszeniem) lub do czasu usunięcia postępowania sądowego. Jeśli określisz okres przechowywania, jest on obliczany na podstawie daty otrzymania wiadomości lub utworzenia elementu skrzynki pocztowej. 
  
Oto co się dzieje po utworzeniu sporu sądowego.
  
- Elementy trwale usunięte przez użytkownika są przechowywane w folderze Elementy do odzyskania w skrzynce pocztowej użytkownika na czas trwania zawieszonego miejsca.

- Elementy przeczyszalne z folderu Elementy do odzyskania przez użytkownika są zachowywane przez czas trwania zawieszonego okresu.

- Przydział miejsca do magazynowania w folderze Elementy do odzyskania został zwiększony z 30 GB do 110 GB.

- Elementy w podstawowej i archiwalnych skrzynkach pocztowych użytkownika są zachowywane

## <a name="assign-an-exchange-online-plan-2-license"></a>Przypisywanie licencji Exchange Online Plan 2

Aby umieścić skrzynkę pocztową Exchange Online w związku z postępowaniem sądowym, musi ona mieć przypisaną licencję Exchange Online Plan 2. Jeśli skrzynka pocztowa ma przypisaną licencję Exchange Online Plan 1, aby umieścić ją w a hold, trzeba byłoby przypisać do skrzynki pocztowej osobną licencję usługi Exchange Online — archiwum.

> [!NOTE]
> W Office 365 Education organizacji postępowanie sądowe jest obsługiwane w subskrypcjach usługi Office 365 A1, które zawierają licencję planu Exchange Online Plan 1 z funkcjami uzupełniającymi. Aby uzyskać więcej informacji, zobacz sekcję "funkcje Exchange Online" w [opisie Office 365 Education usługi](/office365/servicedescriptions/office-365-platform-service-description/office-365-education#exchange-online-features).

## <a name="place-a-mailbox-on-litigation-hold"></a>Umieść skrzynkę pocztową w przypadku postępowania sądowego

Poniżej o krokach można umieścić skrzynkę pocztową w przypadku sporu sądowego przy użyciu centrum administracyjne platformy Microsoft 365.

1. Przejdź <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">do centrum administracyjne platformy Microsoft 365 a</a> następnie kliknij pozycję **Użytkownicy** >  **Aktywuj użytkowników**.

2. Wybierz użytkownika, którego chcesz dotrzymać w przypadku sporu sądowego.

3. Na stronie wysuwu właściwości kliknij **kartę** Poczta, a następnie w obszarze **Więcej** akcji kliknij pozycję **Zarządzaj postępowaniem sądowym**.

   ![Kliknij pozycję Zarządzaj postępowaniem sądowym na karcie Poczta strony wysuwanych właściwości użytkownika.](../media/M365AdminCenterLitHold1.png)

4. Na stronie **wysuwu Zarządzanie** zawieszeniem w związku z postępowaniem sądowym zaznacz pole wyboru Włącz zawieszenie **w** związku z postępowaniem sądowym, a następnie wprowadź następujące informacje opcjonalne:

    1. **Czas trwania wstrzymywania (dni)**: to pole umożliwia utworzenie blokowania opartego na czasie i określenie, jak długo mają być przechowywane elementy skrzynki pocztowej, gdy skrzynka pocztowa jest umieszczana w związku z postępowaniem sądowym. Czas trwania jest obliczany na podstawie daty otrzymania lub utworzenia elementu skrzynki pocztowej. Po wygaśnięciu czasu trwania wstrzymywania dla określonego elementu ten element nie będzie już zachowywany. Jeśli pozostawisz to pole puste, elementy będą zachowywane przez czas nieograniczony lub do momentu usunięcia zawieszania. Dni określają czas trwania.

    2. **Notatka widoczna dla użytkownika**: To pole pozwala poinformować użytkownika, że jego skrzynka pocztowa jest w związku z postępowaniem sądowym. Notatka pojawi się na stronie Informacje o koncie w skrzynce pocztowej użytkownika, jeśli korzysta z programu Outlook 2010 lub nowszego. Aby uzyskać dostęp do tej strony, użytkownicy mogą kliknąć **pozycję** Plik w Outlook.

    3. **Strona sieci Web z większej liczby informacji dla** użytkownika: Użyj tego pola, aby skierować użytkownika do witryny sieci Web, aby uzyskać więcej informacji na temat postępowania w związku z postępowaniem sądowym. Ten adres URL jest wyświetlany na stronie Informacje o koncie w skrzynce pocztowej użytkownika, jeśli używa on programu Outlook 2010 lub nowszego. Aby uzyskać dostęp do tej strony, użytkownicy mogą kliknąć **pozycję** Plik w Outlook.

. Kliknij **pozycję Zapisz zmiany na** **wysuwanych stronie zawieszenie** w przypadku sporu sądowego, aby utworzyć hold.

   W systemie jest wyświetlany transparent z informacją, że może upłynieć do 240 minut, aby zmiana mogła zostać w mocy.

### <a name="create-a-litigation-hold-using-powershell"></a>Tworzenie postępowania sądowego za pomocą programu PowerShell

Możesz również utworzyć zawieszenie w związku z postępowaniem sądowym, uruchamiając następujące polecenie w [programie Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $true
```

Poprzednie polecenie zachowuje elementy przez czas nieograniczony, ponieważ nie jest określony czas trwania blokowania. Aby utworzyć hold oparte na czasie, przy użyciu następującego polecenia:

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $true -LitigationHoldDuration <number of days>
```

Możesz również uruchomić następujące polecenie, aby sprawdzić, czy skrzynka pocztowa jest umieszczana w związku z postępowaniem sądowym:

```powershell
Get-Mailbox <username> | FL LitigationHoldEnabled
```

Wartość Prawda oznacza *, że* skrzynka pocztowa podlega postępowaniem sądowym/

Aby uzyskać więcej informacji, zobacz [Set-Mailbox](/powershell/module/exchange/set-mailbox).

## <a name="how-does-litigation-hold-work"></a>Jak działa zawieszenie w przypadku sporu sądowego?

W normalnym przepływie pracy elementów usuniętych element skrzynki pocztowej jest przenoszony do podfolderu Usunięcia w folderze Elementy do odzyskania, gdy użytkownik trwale usunie go (Shift + Delete) lub usunie go z folderu Elementy usunięte. Zasady usuwania (czyli tag przechowywania skonfigurowane przy użyciu akcji przechowywania Usuń) przenosi również elementy do podfolderu Usunięcia po wygaśnięciu okresu przechowywania. Jeśli użytkownik przeczyści element w folderze Elementy do odzyskania lub gdy wygasa okres przechowywania elementów usuniętych dla elementu, jest on przenoszony do podfolderu Czyszczenie w folderze Elementy do odzyskania i oznaczany do trwałego usunięcia. Zostanie ona wyczyszczona Exchange następnym razem, gdy skrzynka pocztowa zostanie przetworzona przez asystenta folderów zarządzanych (MFA).

Gdy skrzynka pocztowa jest umieszczana w związku z postępowaniem sądowym, elementy w podfolderze przeczyszczania są zachowywane na czas trwania przechowywania określony przez zawieszenie w związku z postępowaniem sądowym. Czas trwania wstrzymywania jest obliczany na podstawie pierwotnej daty otrzymania lub utworzenia elementu oraz definiuje czas przechowywania elementów w podfolderze przeczyszczania. Gdy czas trwania przechowywania dla elementu w podfolderze przeczyszczania wygasa, ten element jest oznaczany do trwałego usunięcia i usuwany z usługi Exchange po następnym przetworzeniu skrzynki pocztowej przez uwierzytelniania wieloskładnikowego. Jeśli w skrzynce pocztowej zostanie umieszczona nieograniczona wstrzymanie, elementy nie będą nigdy czyszczane z podfolderu przeczyszczania.

Na poniższej ilustracji przedstawiono podfoldery w folderach Elementy do odzyskania i proces zawijania przepływu pracy.

![Cykl życia wstrzymywania sporów.](../media/LitigationHoldLifeCycle.png)

> [!NOTE]
> Jeśli w skrzynce pocztowej zostanie umieszczona sprawa zbierania elektronicznych materiałów dowodowych, przeczyszczony elementy zostaną przeniesione z podfolderu Usunięcia do podfolderu DiscoveryHolds i zachowywane, dopóki skrzynka pocztowa nie zostanie zwolniona z zawieszonego zbierania elektronicznych materiałów dowodowych.
