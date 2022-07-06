---
title: Dowiedz się więcej o archiwalnych skrzynkach pocztowych dla usługi Microsoft Purview
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.ArchivingHelp
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Dowiedz się więcej o archiwalnych skrzynkach pocztowych, aby zapewnić dodatkowy magazyn skrzynki pocztowej.
ms.openlocfilehash: 57de7c7791615e8587222de992588f1923348059
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621254"
---
# <a name="learn-about-archive-mailboxes"></a>Dowiedz się więcej o archiwalnych skrzynkach pocztowych

Archiwizowanie skrzynek pocztowych w usłudze Microsoft 365 (nazywane również *archiwizowaniem w miejscu*) zapewnia użytkownikom dodatkowe miejsce do magazynowania skrzynki pocztowej. Po włączeniu archiwalnych skrzynek pocztowych bieżąca skrzynka pocztowa użytkownika staje się jego *podstawową skrzynką pocztową* i zostanie utworzona dodatkowa skrzynka pocztowa o nazwie *archiwum skrzynki pocztowej*. Obie skrzynki pocztowe są uważane za skrzynkę pocztową użytkownika dla funkcji zgodności, takich jak wyszukiwanie zawartości z portal zgodności Microsoft Purview, przechowywanie usługi Microsoft 365 i blokada postępowania sądowego.

Użytkownicy mogą uzyskiwać dostęp do wiadomości i przechowywać je w swoich archiwalnych skrzynkach pocztowych przy użyciu programu Outlook i Outlook w sieci Web. Użytkownicy mogą również przenosić lub kopiować wiadomości między podstawową skrzynką pocztową i skrzynką pocztową archiwum. Mogą również odzyskać usunięte elementy z folderu Elementy możliwe do odzyskania w swojej skrzynce pocztowej archiwum przy użyciu narzędzia Odzyskaj usunięte elementy.

## <a name="managing-archive-mailboxes-with-messaging-records-management-mrm"></a>Zarządzanie archiwalnymi skrzynkami pocztowymi przy użyciu zarządzania rekordami obsługi komunikatów (MRM)

Wiadomości można również przenieść do skrzynki pocztowej archiwum przez [domyślne zasady przechowywania programu Exchange](/exchange/security-and-compliance/messaging-records-management/default-retention-policy) z usługi Messaging Records Management (MRM). Te zasady domyślne są automatycznie przypisywane do każdej skrzynki pocztowej i wykonuje następujące czynności:

  - Przenosi elementy, które są dwa lata lub starsze z podstawowej skrzynki pocztowej użytkownika do jego skrzynki pocztowej archiwum.

  - Przenosi elementy, które mają co najmniej 14 dni, z folderu Elementy do odzyskania w podstawowej skrzynce pocztowej użytkownika do folderu Elementy możliwe do odzyskania w skrzynce pocztowej archiwum.

Zasady MRM organizacji można dostosować przy użyciu [tagów przechowywania](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies). Przykład konfiguracji można znaleźć [w temacie Konfigurowanie archiwum i usuwanie zasad dla skrzynek pocztowych w organizacji](set-up-an-archive-and-deletion-policy-for-mailboxes.md).

> [!NOTE]
> Rozwiązanie MRM, takie jak zasady przechowywania i etykiety przechowywania platformy Microsoft 365, może również automatycznie usuwać wiadomości e-mail po określonym okresie. Jako starsza technologia niż przechowywanie na platformie Microsoft 365, rozwiązanie MRM nadal działa równolegle z zasadami przechowywania i etykietami przechowywania w usłudze Microsoft Purview. Aby uzyskać więcej informacji, zobacz [Używanie zasad przechowywania i etykiet przechowywania zamiast starszych funkcji](retention.md#use-retention-policies-and-retention-labels-instead-of-older-features).

## <a name="auto-expanding-archiving"></a>Automatyczne rozszerzanie archiwizacji 

Po włączeniu archiwum skrzynki pocztowej użytkownika dostępna jest maksymalnie 100 GB dodatkowego magazynu. Jeśli użytkownicy potrzebują więcej miejsca do magazynowania, włącz automatyczne rozszerzanie archiwizacji, aby zapewnić do 1,5 TB dodatkowego miejsca w archiwalnych skrzynkach pocztowych. Aby uzyskać więcej informacji, zobacz [Dowiedz się więcej na temat automatycznego rozszerzania archiwizacji](autoexpanding-archiving.md).

## <a name="licensing"></a>Licencjonowanie

Aby uzyskać listę licencji programu Outlook, które obsługują archiwalne skrzynki pocztowe, zobacz odwołania do In-Place Archiwizowanie [w wymaganiach licencyjnych programu Outlook dla funkcji programu Exchange](https://support.microsoft.com/office/46b6b7c5-c3ca-43e5-8424-1e2807917c99).

## <a name="next-steps"></a>Następne kroki

Zobacz [Włączanie archiwalnych skrzynek pocztowych w portal zgodności Microsoft Purview](enable-archive-mailboxes.md).
