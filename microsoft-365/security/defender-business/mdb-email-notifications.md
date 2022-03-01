---
title: Konfigurowanie powiadomień e-mail dla zespołu zabezpieczeń
description: Konfigurowanie powiadomień e-mail w celu powiadomienia innych osób o alertach i lukach w zabezpieczeniach w programie Microsoft Defender dla firm
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.openlocfilehash: 5a6d896b3b18b4eea0721197c0a4766add4a20b6
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2022
ms.locfileid: "63016586"
---
# <a name="set-up-email-notifications"></a>Konfigurowanie powiadomień e-mail

> [!IMPORTANT]
> Usługa Microsoft Defender dla firm jest teraz w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, którzy zarejestrują się tutaj [, aby](https://aka.ms/mdb-preview) poprosić o to. W najbliższych tygodniach nawiązemy wstępną ofertę klientów i partnerów oraz rozszerzymy jej wersja zapoznawczą, aby rozszerzyć jej dostępność do ogólnej dostępności. Pamiętaj, że wersja Preview zostanie uruchamiana z [początkowym zestawem scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a funkcje będą regularnie dodajemy.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 


Możesz skonfigurować powiadomienia e-mail dla zespołu zabezpieczeń. Następnie w przypadku wygenerowania alertów lub odkrycia nowych luk w zabezpieczeniach osoby z Twojego zespołu zabezpieczeń zostaną automatycznie powiadomione. 

## <a name="what-to-do"></a>Co należy zrobić

1. [Informacje o typach powiadomień e-mail](#types-of-email-notifications).

2. [Wyświetlanie i edytowanie ustawień powiadomień e-mail](#view-and-edit-email-notifications).

3. [Przejdź do następnych kroków](#next-steps).


## <a name="types-of-email-notifications"></a>Typy powiadomień e-mail

Podczas konfigurowanie powiadomień e-mail możesz wybrać jeden z dwóch typów, jak opisano w poniższej tabeli: <br/><br/>

| Typ powiadomienia  | Opis  |
|---------|---------|
| Luki w zabezpieczeniach  | W przypadku wykrycia nowych luk lub luk w zabezpieczeniach adresaci otrzymają wiadomość e-mail. |
| Alerty & lukami w zabezpieczeniach  | W przypadku wygenerowania alertów z powodu wykrycia zagrożeń na urządzeniach lub wykrycia nowych luk lub wykorzystania luk w zabezpieczeniach adresaci otrzymują wiadomość e-mail. |

> [!TIP]
> **Powiadomienia e-mail nie są jedynym sposobem, w jaki zespół zabezpieczeń może uzyskać informacje o nowych alertach i luki w zabezpieczeniach**.
> 
> Powiadomienia e-mail to wygodny sposób na zapewnianie zespołowi zabezpieczeń informacji w czasie rzeczywistym. Ale są też inne! Na przykład zawsze, gdy twój zespół zabezpieczeń się Microsoft 365 Defender w portalu sieciOwym ([https://security.microsoft.com](https://security.microsoft.com)), będą dosłane karty z wyróżnieniem nowych zagrożeń, alertów i luk w zabezpieczeniach. Program Defender dla firm (w wersji Preview) został zaprojektowany tak, aby podczas logowania wyróżniać ważne informacje, na które zwraca uwagę zespół zabezpieczeń.
> 
> Aby wyświetlić informacje, zespół zabezpieczeń może również wybrać pozycję **Zdarzenia** w okienku nawigacji. Aby dowiedzieć się więcej, [zobacz Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm (wersja preview).](mdb-view-manage-incidents.md)

## <a name="view-and-edit-email-notifications"></a>Wyświetlanie i edytowanie powiadomień e-mail

Aby wyświetlić lub edytować ustawienia powiadomień e-mail dla organizacji, wykonaj następujące czynności:

1. Przejdź do Microsoft 365 Defender konta ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji **wybierz pozycję Ustawienia**, a następnie wybierz **pozycję Punkty końcowe**. Następnie w obszarze **Ogólne wybierz** pozycję Powiadomienia **e-mail**. 

3. Przejrzyj informacje na kartach **Alerty** **i Luki** w zabezpieczeniach.

   - Jeśli nie widzisz żadnych elementów wymienionych na karcie Alerty,  możesz utworzyć regułę, która będzie powiadamiana o alertach. Aby uzyskać pomoc na temat tego zadania, zobacz [Tworzenie reguł dla powiadomień alertów](../defender-endpoint/configure-email-notifications.md).

   - Jeśli nie widzisz żadnych elementów wymienionych na karcie Luki w zabezpieczeniach, możesz utworzyć regułę, która będzie powiadamiana o każdej nowej lukie. Aby uzyskać pomoc na temat tego zadania, zobacz [Tworzenie reguł w celu wykorzystania luk w zabezpieczeniach](../defender-endpoint/configure-vulnerability-email-notifications.md).

   - Jeśli masz utworzone reguły, wybierz regułę, aby ją edytować. Możesz również usunąć regułę. 

## <a name="next-steps"></a>Następne kroki

Przejdź do:

- [Krok 4. Na urządzeniach w programie Microsoft Defender dla firm (wersja Preview)](mdb-onboard-devices.md)

