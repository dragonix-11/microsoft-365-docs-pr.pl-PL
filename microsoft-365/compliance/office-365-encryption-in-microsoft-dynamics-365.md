---
title: Szyfrowanie w uwitrynie Microsoft Dynamics 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
description: Dowiedz się, jak firma Microsoft używa technologii szyfrowania do ochrony danych klienta w u usługi Microsoft Dynamics 365, gdy są spoczynku w bazie danych firmy Microsoft i podczas przesyłania.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ba3dbef73b7674364f19e83befdbb8cdfe417ad6
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "62998831"
---
# <a name="encryption-in-microsoft-dynamics-365"></a>Szyfrowanie w uwitrynie Microsoft Dynamics 365

Firma Microsoft korzysta z technologii szyfrowania do ochrony danych klientów w uwitrynie Dynamics 365, gdy znajduje się w centrum danych firmy Microsoft i jest on podczas przesyłania między urządzeniami użytkownika a naszymi centrami danych. Połączenia ustanowione między klientami i centrami danych firmy Microsoft są szyfrowane, a wszystkie publiczne punkty końcowe są zabezpieczone przy użyciu standardu branżowego TLS. W praktyce usługi TLS ustanawiają rozszerzone połączenie między przeglądarkami i serwerami zapewniające poufność i integralność danych między pulpitami i centrami danych. Po aktywowaniu szyfrowania danych nie można go wyłączyć. Aby uzyskać więcej informacji, zobacz [Szyfrowanie danych na poziomie pola](/previous-versions/dynamicscrm-2016/developers-guide/dn481562(v=crm.8)).

Usługa Dynamics 365 używa standardowego szyfrowania na poziomie komórki Microsoft SQL Server zestaw domyślnych atrybutów encji zawierających poufne informacje, takie jak nazwy użytkowników i hasła poczty e-mail. Ta funkcja może ułatwić organizacjom spełnienie wymagań dotyczących zgodności skojarzonych z programem FIPS 140-2. Szyfrowanie danych na poziomie pola jest szczególnie ważne w scenariuszach, które wykorzystują router poczty e-mail usługi [Microsoft Dynamics CRM](/previous-versions/dynamicscrm-2016/administering-dynamics-365/hh699800(v=crm.8)), który musi przechowywać nazwy użytkowników i hasła, aby umożliwić integrację między wystąpieniem usługi Dynamics 365 a usługą poczty e-mail.

Wszystkie wystąpienia usługi Dynamics 365 używają [Microsoft SQL Server Transparent Data Encryption (](/sql/relational-databases/security/encryption/transparent-data-encryption)TDE) do szyfrowania w czasie rzeczywistym danych zapisywanych na dysku (w spoczynku). TDE szyfruje SQL Server, Azure SQL Database oraz pliki danych usługi Azure SQL magazyn danych. Domyślnie firma Microsoft przechowuje klucze szyfrowania bazy danych dla Twoich wystąpień usługi Dynamics 365 i zarządza nimi. (Klucze używane przez usługę Dynamics 365 dla instytucji finansowych są generowane przez .NET Framework API ochrony danych.

Funkcja zarządzania kluczami w Centrum  administrowania usługą Dynamics 365 umożliwia administratorom samodzielne zarządzanie kluczami szyfrowania bazy danych, które są skojarzone z wystąpieniami usługi Dynamics 365. (Klucze samodzielnego szyfrowania baz danych są dostępne tylko w aktualizacji ze stycznia 2017 r. dla usługi Microsoft Dynamics 365 i mogą nie być dostępne dla nowszych wersji. Aby uzyskać więcej informacji, zobacz [Zarządzanie kluczami szyfrowania dla wystąpienia usługi Dynamics 365 (online](/dynamics365/customer-engagement/admin/manage-encryption-keys-instance)). Funkcja zarządzania kluczami obsługuje zarówno pliki kluczy szyfrowania PFX, jak i BYOK, na przykład pliki przechowywane w hsm. Aby uzyskać więcej informacji na temat generowania i przenoszenia klucza chronionego HSM przez Internet, zobacz Jak generować i przenosić klucze chronione przez HSM dla magazynu kluczy [platformy Azure](/azure/key-vault/key-vault-hsm-protected-keys).

Aby użyć opcji klucza szyfrowania przekazywania, potrzebny jest zarówno publiczny, jak i prywatny klucz szyfrowania.

Funkcja zarządzania kluczami przenosi złożoność zarządzania kluczami szyfrowania przy użyciu magazynu kluczy platformy Azure do bezpiecznego przechowywania kluczy szyfrowania. Magazyn kluczy platformy Azure pomaga chronić klucze kryptograficzne i sekrety używane przez usługi i aplikacje w chmurze. Funkcja zarządzania kluczami nie wymaga, aby mieć subskrypcję magazynu kluczy platformy Azure i w większości przypadków nie ma potrzeby uzyskiwania dostępu do kluczy szyfrowania używanych dla usługi Dynamics 365 w ramach magazynu.
