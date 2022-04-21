---
title: Wprowadzenie z zarządzaniem cyklem życia danych
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Chcesz rozpocząć zarządzanie danymi organizacji, ale nie wiesz, od czego zacząć? Przeczytaj niektóre wskazówki nakazowe, aby rozpocząć pracę.
ms.openlocfilehash: c5b9e931e2ab822a4d888b775de9fb8fa2acb13b
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972370"
---
# <a name="get-started-with-data-lifecycle-management"></a>Wprowadzenie z zarządzaniem cyklem życia danych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

>*[Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Chcesz rozpocząć zarządzanie danymi organizacji, zachowując zawartość, którą musisz przechowywać, i usuwając zawartość, której nie masz? Aby rozpocząć pracę, skorzystaj z poniższych wskazówek dotyczących zarządzania cyklem życia danych usługi Microsoft Purview (dawniej Microsoft Information Governance):

1. **Dowiedz się, jak działa przechowywanie i usuwanie** w Microsoft 365, a następnie zidentyfikuj obciążenia, które wymagają zasad przechowywania i czy musisz utworzyć etykiety przechowywania dla wyjątków: [Dowiedz się więcej o przechowywaniu](retention.md)
    
    > [!NOTE]
    > Jeśli musisz zarządzać elementami o wysokiej wartości dla wymagań biznesowych, prawnych lub regulacyjnych dotyczących przechowywania rekordów: użyj etykiet przechowywania z [zarządzaniem rekordami](records-management.md) , a nie zarządzaniem cyklem życia danych.

2. **Tworzenie zasad przechowywania** dla zidentyfikowanych obciążeń, określanie ustawień przechowywania i akcji wymaganych przez zasady organizacji lub przepisy branżowe: [Tworzenie zasad przechowywania](create-retention-policies.md)
    
    W razie potrzeby [utwórz i zastosuj etykiety przechowywania dla wyjątków](create-retention-labels-information-governance.md).

3. **Włącz archiwizowanie skrzynek pocztowych** , aby zapewnić użytkownikom dodatkowe miejsce do magazynowania skrzynki pocztowej: [Włącz archiwalne skrzynki pocztowe w portalu zgodności usługi Microsoft Purview](enable-archive-mailboxes.md)
    
    Jeśli jest to wymagane do obsługi archiwalnych skrzynek pocztowych:
    
    - [Włącz automatyczne rozszerzanie archiwizacji](enable-autoexpanding-archiving.md) dla skrzynek pocztowych, które potrzebują więcej niż 100 GB miejsca do magazynowania.
    
    - Użyj [tagów przechowywania z zasadami przechowywania z zarządzania rekordami obsługi komunikatów (MRM](set-up-an-archive-and-deletion-policy-for-mailboxes.md) ), jeśli chcesz dostosować sposób automatycznego przenoszenia wiadomości e-mail z podstawowej skrzynki pocztowej użytkownika do jego skrzynki pocztowej archiwum lub jeśli musisz określić ustawienia przechowywania i usuwania dla określonych folderów, a nie całej skrzynki pocztowej.

4. **Omówienie nieaktywnych skrzynek pocztowych i zarządzanie nimi** , które zachowują zawartość skrzynki pocztowej po opuszczeniu organizacji przez pracowników: [informacje o nieaktywnych skrzynkach pocztowych](inactive-mailboxes-in-office-365.md)

5. Jeśli masz pliki PST zawierające dane, które chcesz zarządzać: **Importowanie plików PST do skrzynek pocztowych online** przy użyciu przekazywania sieci lub [wysyłania dysków: Informacje o importowaniu plików PST organizacji](importing-pst-files-to-office-365.md)

## <a name="subscription-and-licensing-requirements"></a>Wymagania dotyczące subskrypcji i licencjonowania

Wiele różnych subskrypcji obsługuje możliwości zarządzania cyklem życia danych.

Aby wyświetlić opcje licencjonowania użytkowników w celu skorzystania z funkcji usługi Microsoft Purview, zobacz [wskazówki dotyczące licencjonowania Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). Aby zapoznać się z funkcjami wymienionymi na tej stronie, zobacz sekcję [Zarządzanie cyklem życia danych usługi Microsoft Purview](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-data-lifecycle-management) i powiązane [pobieranie plików PDF](https://go.microsoft.com/fwlink/?linkid=2139145) w celu uzyskania wymagań dotyczących licencjonowania na poziomie funkcji.

## <a name="permissions"></a>Uprawnienia

Zobacz następującą sekcję, aby uzyskać informacje o rolach i grupach ról, aby zarządzać przechowywaniem Microsoft 365.

W przypadku uprawnień do zarządzania skrzynkami pocztowymi na potrzeby archiwizacji, nieaktywnych skrzynek pocztowych i importowania zwykle wymagają one Exchange uprawnień, takich jak rola Adresaci poczty. Domyślnie ta rola jest przypisywana do grup ról Zarządzanie adresatami i Zarządzanie organizacją. Aby uzyskać dokładne wymagania dotyczące uprawnień dla każdego zadania zarządzania, zapoznaj się z dokumentacją dołączącą do instrukcji administratora.

### <a name="permissions-for-retention-policies-and-retention-labels"></a>Uprawnienia do zasad przechowywania i etykiet przechowywania

Członkowie zespołu ds. zgodności, którzy będą tworzyć zasady przechowywania i etykiety przechowywania oraz zarządzać nimi, potrzebują uprawnień do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portalu zgodności usługi Microsoft Purview</a>. Domyślnie administrator dzierżawy (administrator globalny) ma dostęp do tej lokalizacji i może udzielić urzędnikom zgodności i innym osobom dostępu bez udzielania im wszystkich uprawnień administratora dzierżawy. Aby udzielić uprawnień dla tej ograniczonej administracji, zalecamy dodanie użytkowników do grupy ról administratora **administratora zgodności** .

Alternatywnie do korzystania z tej roli domyślnej można utworzyć nową grupę ról i dodać rolę **Zarządzanie przechowywaniem** do tej grupy. W przypadku roli tylko do odczytu użyj funkcji **Zarządzania przechowywaniem tylko do wyświetlania**. 

Aby uzyskać instrukcje dotyczące dodawania użytkowników do ról domyślnych lub tworzenia własnych grup ról, zobacz [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md).

Te uprawnienia są wymagane tylko do tworzenia, konfigurowania i stosowania zasad przechowywania oraz etykiet przechowywania. Osoba konfigurująca te zasady i etykiety nie wymaga dostępu do zawartości.

## <a name="common-scenarios"></a>Typowe scenariusze

Poniższa tabela ułatwia mapowanie wymagań biznesowych na najbardziej typowe scenariusze zarządzania cyklem życia danych.

|Chcę...|Dokumentacji|
|----------------|---------------|
|Wydajne przechowywanie lub usuwanie danych dla usług Microsoft 365: <br />- Exchange  <br />- SharePoint  <br />- OneDrive  <br />- Grupy Microsoft 365 <br />- Teams <br />- Yammer <br />- Skype dla firm |[Tworzenie i konfigurowanie zasad przechowywania](create-retention-policies.md)|
|Zapewnianie użytkownikom dodatkowego magazynu skrzynek pocztowych |[Włączanie archiwalnych skrzynek pocztowych w portalu zgodności usługi Microsoft Purview](enable-archive-mailboxes.md)|
|Zachowywanie danych skrzynki pocztowej po opuszczeniu organizacji przez pracowników |[Twórz nieaktywne skrzynki pocztowe i zarządzaj nimi](create-and-manage-inactive-mailboxes.md)|
|Upload dane skrzynki pocztowej z plików PST |[Użyj przekazywania sieciowego w celu importu plików PST](use-network-upload-to-import-pst-files.md)|


Jeśli masz scenariusz, który wymaga zarządzania danymi poszczególnych elementów, zobacz [typowe scenariusze zarządzania rekordami](get-started-with-records-management.md#common-scenarios). 

## <a name="end-user-documentation"></a>Dokumentacja użytkownika końcowego

Zapoznaj się z następującą sekcją, aby uzyskać informacje na temat dokumentacji użytkownika końcowego, aby obsługiwać przechowywanie Microsoft 365.

Funkcje zarządzania cyklem życia danych, które obsługują zarządzanie skrzynkami pocztowymi (archiwizowanie, nieaktywne skrzynki pocztowe i importowanie) zwykle nie wymagają dokumentacji użytkownika końcowego.

### <a name="end-user-documentation-for-retention-and-deletion"></a>Dokumentacja użytkownika końcowego dotycząca przechowywania i usuwania

Większość zasad przechowywania działa dyskretnie w tle bez interakcji z użytkownikiem, dlatego wymaga małej dokumentacji dla użytkowników. Zasady przechowywania dla Teams informują użytkowników o usunięciu ich komunikatów za pomocą linku do [Teams komunikatów dotyczących zasad przechowywania](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

Jeśli jednak uzupełnisz zasady przechowywania etykietami przechowywania, etykiety te mają interfejs użytkownika w aplikacjach Microsoft 365. Przed wdrożeniem tych etykiet w sieci produkcyjnej upewnij się, że podasz informacje i instrukcje dla użytkowników końcowych i działu pomocy technicznej. Aby ułatwić użytkownikom stosowanie etykiet przechowywania w SharePoint i OneDrive, zobacz [Stosowanie etykiet przechowywania do plików w SharePoint lub OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df).

Najbardziej efektywną dokumentacją użytkownika końcowego zawsze będą dostosowane wskazówki i instrukcje podane dla wybranych nazw etykiet przechowywania i konfiguracji. Zobacz następującą stronę i pliki do pobrania, których możesz użyć, aby pomóc w szkoleniu użytkowników: [Szkolenie użytkowników końcowych dla etykiet przechowywania](https://microsoft.github.io/ComplianceCxE/enduser/retention/).

