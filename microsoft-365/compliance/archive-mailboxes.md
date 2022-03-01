---
title: Informacje o archiwalnych skrzynkach pocztowych na Microsoft 365 zgodności
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
description: Dowiedz się więcej o archiwalnych skrzynkach pocztowych w celu zapewnienia dodatkowego miejsca do magazynowania skrzynek pocztowych.
ms.openlocfilehash: a863df7be1b73d6a50d818bca5948f3017e3d373
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010635"
---
# <a name="learn-about-archive-mailboxes"></a>Informacje o archiwalnych skrzynkach pocztowych

Archiwizacja skrzynek pocztowych Microsoft 365 (nazywana również archiwizacją miejscową *) zapewnia* użytkownikom dodatkowe miejsce do magazynowania skrzynki pocztowej. Po włączeniu archiwalnych skrzynek pocztowych bieżąca skrzynka pocztowa użytkownika staje się  jego podstawową skrzynką pocztową i zostaje utworzona dodatkowa skrzynka pocztowa, nazywana archiwacyjną *skrzynką pocztową*. Obie skrzynki pocztowe są traktowane jako skrzynki pocztowe użytkowników w związku z funkcjami zgodności, takimi jak przeszukiwanie zawartości z witryny Centrum zgodności platformy Microsoft 365, Microsoft 365 przechowywania i Zawieszenie w związku z postępowaniem sądowym.

Użytkownicy mogą uzyskać dostęp do swoich archiwalnych skrzynek pocztowych i przechowywać je, korzystając Outlook i Outlook w sieci Web. Użytkownicy mogą również przenosić i kopiować wiadomości między podstawową skrzynką pocztową a archiwacyjną skrzynką pocztową. Za pomocą narzędzia Odzyskiwanie elementów usuniętych można również odzyskać elementy usunięte z folderu Elementy do odzyskania w archiwalnych skrzynkach pocztowych.

## <a name="managing-archive-mailboxes-with-messaging-records-management-mrm"></a>Zarządzanie archiwalnych skrzynek pocztowych za pomocą zarządzania rekordami wiadomości (MRM)

Wiadomości można również przenosić do archiwaowej skrzynki pocztowej za pomocą [domyślnych Exchange przechowywania](/exchange/security-and-compliance/messaging-records-management/default-retention-policy) z zarządzania rekordami wiadomości (MRM). Te zasady domyślne są automatycznie przypisywane do każdej skrzynki pocztowej i mają następujące zasady:

  - Przenosi elementy, które mają dwa lata lub więcej, z podstawowej skrzynki pocztowej użytkownika do jego archiwaowej skrzynki pocztowej.

  - Przenosi elementy, które mają 14 dni lub więcej, z folderu Elementy do odzyskania w podstawowej skrzynce pocztowej użytkownika do folderu Elementy do odzyskania w jego archiwaowej skrzynce pocztowej.

Zasady MRM organizacji można dostosowywać za pomocą [tagów przechowywania](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies). Aby uzyskać przykładową konfigurację, zobacz [Konfigurowanie zasad archiwizacji](set-up-an-archive-and-deletion-policy-for-mailboxes.md) i usuwania dla skrzynek pocztowych w organizacji.

> [!NOTE]
> MrM, takie Microsoft 365 przechowywania i etykiety przechowywania, mogą również automatycznie usuwać wiadomości e-mail po określonym czasie. Jako starsza technologia niż Microsoft 365 przechowywania, mrM nadal działa obok siebie z zasadami przechowywania i etykietami przechowywania na podstawie Microsoft 365 zgodności. Aby uzyskać więcej informacji, zobacz [Używanie zasad przechowywania i etykiet przechowywania zamiast starszych funkcji](retention.md#use-retention-policies-and-retention-labels-instead-of-older-features).

## <a name="auto-expanding-archiving"></a>Automatyczne rozszerzanie archiwizacji 

Po włączeniu archiwaowej skrzynki pocztowej użytkownika dostępnych jest maksymalnie 100 GB dodatkowej przestrzeni dyskowej. Jeśli użytkownicy potrzebują więcej miejsca do magazynowania, włącz automatyczne rozszerzanie archiwizacji, aby zapewnić do 1,5 TB dodatkowej przestrzeni dyskowej w archiwalnych skrzynkach pocztowych. Aby uzyskać więcej informacji, zobacz [Informacje na temat automatycznego rozszerzania archiwizacji](autoexpanding-archiving.md).

## <a name="licensing"></a>Licencjonowanie

Aby uzyskać listę licencji Outlook archiwalnych skrzynek pocztowych, zobacz odwołania do archiwizacji In-Place w te Outlook wymagań licencyjnych dotyczących [Exchange funkcji](https://support.microsoft.com/office/46b6b7c5-c3ca-43e5-8424-1e2807917c99).

## <a name="next-steps"></a>Następne kroki

Zobacz [Włączanie archiwalnych skrzynek pocztowych w centrum zgodności](enable-archive-mailboxes.md).