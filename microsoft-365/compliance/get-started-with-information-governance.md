---
title: Wprowadzenie do zarządzania informacjami w programie Microsoft 365
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
description: Wszystko gotowe do rozpoczęcia pracy nad danymi Twojej organizacji, ale nie wiesz, od czego zacząć? Aby rozpocząć, przeczytaj kilka wskazówek dotyczących preskrypcji.
ms.openlocfilehash: 5b30dc870389c06bd006a056127439f1ec18ac65
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010619"
---
# <a name="get-started-with-information-governance"></a>Wprowadzenie do zarządzania informacjami

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Wszystko gotowe do rozpoczęcia zarządzania danymi twojej organizacji przez zachowanie zawartości, która ma być zachowywana, i usunięcie zawartości, która nie jest już potrzebna? Aby rozpocząć, skorzystaj z następujących wskazówek:

1. **Dowiedz się,** jak działa przechowywanie i usuwanie w aplikacji Microsoft 365, a następnie zidentyfikuj obciążenia pracą, które wymagają zasad przechowywania, oraz czy musisz utworzyć etykiety przechowywania dla [wyjątków](retention.md). Dowiedz się więcej na temat przechowywania
    
    > [!NOTE]
    > Jeśli potrzebujesz zarządzania cyklem życia elementów o wysokiej wartości w przypadku wymogów przechowywania rekordów biznesowych, prawnych lub prawnych: używaj etykiet przechowywania z zarządzaniem rekordami, a nie zarządzaniem informacjami.[](records-management.md)

2. **Utwórz zasady przechowywania** dla zidentyfikowanych obciążeń, określając ustawienia i akcje przechowywania wymagane przez zasady organizacji lub przepisy branżowe: [Tworzenie zasad przechowywania](create-retention-policies.md)
    
    W razie potrzeby [utwórz i zastosuj etykiety przechowywania dla swoich wyjątków](create-retention-labels-information-governance.md).

3. **Włączanie archiwizacji skrzynek pocztowych** w celu zapewnienia użytkownikom dodatkowego miejsca do magazynowania skrzynki pocztowej: Włączanie archiwalnych skrzynek pocztowych [w centrum zgodności](enable-archive-mailboxes.md)
    
    Jeśli jest to wymagane do obsługi archiwalnych skrzynek pocztowych:
    
    - [Włącz automatyczne archiwizowanie dla](enable-autoexpanding-archiving.md) skrzynek pocztowych, które wymagają więcej niż 100 GB miejsca do magazynowania.
    
    - Za pomocą tagów przechowywania i zasad przechowywania z zarządzania rekordami wiadomości [(MRM, Messaging Records Management)](set-up-an-archive-and-deletion-policy-for-mailboxes.md) możesz dostosować sposób automatycznego przenoszenia wiadomości e-mail z podstawowej skrzynki pocztowej użytkownika do jego archiwaowej skrzynki pocztowej lub określić ustawienia przechowywania i usuwania dla określonych folderów, a nie dla całej skrzynki pocztowej.

4. **Opis nieaktywnych skrzynek pocztowych** i zarządzanie nimi, które zachowują zawartość skrzynek pocztowych po opuszczeniu organizacji przez pracowników: informacje [o nieaktywnych skrzynkach pocztowych](inactive-mailboxes-in-office-365.md)

5. Jeśli masz pliki PST zawierające dane, których chcesz zarządzać: Importowanie plików PST do skrzynek pocztowych w trybie **online** przy użyciu przekazywania sieciowego lub wysyłki dysków: Dowiedz się, jak importować pliki [PST twojej organizacji](importing-pst-files-to-office-365.md).

Niezależnie od tej **procedury użyj** łączników do importowania i archiwizowania danych innych firm, które obejmują dane z platform społecznościowych, platform wiadomości błyskawicznych i platform współpracy nad dokumentami. Po zaimportowaniu tych danych do skrzynek pocztowych w trybie online obsługuje ona nie tylko zarządzanie informacjami z zakresu zgodności z usługą Microsoft 365, ale także inne rozwiązania zgodności, takie jak zgodność komunikacji, zarządzanie ryzykiem niejawnego programu testów i zbierania elektronicznych materiałów dowodowych. Aby uzyskać więcej informacji, zobacz [Informacje o łącznikach dla danych innych firm](archiving-third-party-data.md).

## <a name="subscription-and-licensing-requirements"></a>Wymagania dotyczące subskrypcji i licencjonowania

Wiele różnych subskrypcji obsługuje funkcje zarządzania informacjami.

Aby wyświetlić opcje licencjonowania użytkowników w celu skorzystania z funkcji zgodności Microsoft 365, zobacz wskazówki Microsoft 365 dotyczące licencjonowania w zakresie zabezpieczeń [& zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). Aby uzyskać informacje na temat funkcji wymienionych na tej stronie, zobacz sekcję [Zarządzanie informacjami](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-governance) i powiązany plik [PDF](https://go.microsoft.com/fwlink/?linkid=2139145) do pobrania, aby uzyskać informacje o wymaganiach licencyjnych na poziomie funkcji.

## <a name="permissions"></a>Uprawnienia

Zobacz następującą sekcję, aby uzyskać informacje o rolach i grupach ról w celu zarządzania Microsoft 365 przechowywaniem.

Uprawnienia do zarządzania skrzynkami pocztowymi w celu archiwizacji, nieaktywnych skrzynek pocztowych i importowania wymagają Exchange, na przykład roli adresatów poczty. Domyślnie ta rola jest przypisana do grup ról Zarządzanie adresatami i Zarządzanie organizacją. Dokładne wymagania dotyczące uprawnień dla poszczególnych zadań zarządzania można znaleźć w dokumentacji dołączonej do instrukcji administratora.

### <a name="permissions-for-retention-policies-and-retention-labels"></a>Uprawnienia dotyczące zasad przechowywania i etykiet przechowywania

Członkowie Twojego zespołu zgodności, którzy będą tworzyć zasady przechowywania i etykiety przechowywania oraz zarządzać nimi, muszą mieć uprawnienia do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365.</a> Domyślnie administrator dzierżawy (administrator globalny) ma dostęp do tej lokalizacji i może udzielać służbom zgodności z przepisami i innym osobom dostępu bez nadawania im wszystkich uprawnień administratora dzierżawy. Aby przyznać uprawnienia dla tej ograniczonej administracji, zalecamy dodanie użytkowników do grupy ról **administratora** zgodności.

Zamiast używać tej roli domyślnej, możesz utworzyć nową grupę ról i dodać do tej grupy  rolę Zarządzanie przechowywaniem. Aby pełnić rolę tylko do odczytu, użyj zarządzania **przechowywaniem tylko do odczytu**. 

Aby uzyskać instrukcje dotyczące dodawania użytkowników do ról domyślnych lub tworzenia własnych grup ról, zobacz Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md).

Te uprawnienia są wymagane tylko do tworzenia, konfigurowania i stosowania zasad przechowywania i etykiet przechowywania. Osoba konfigurująca te zasady i etykiety nie wymaga dostępu do zawartości.

## <a name="common-scenarios"></a>Typowe scenariusze

Skorzystaj z poniższej tabeli, aby ułatwić zamapowanie wymagań biznesowych na najbardziej typowe scenariusze zarządzania informacjami.

|Chcę...|Dokumentacja|
|----------------|---------------|
|Efektywne zachowywanie lub usuwanie danych Microsoft 365 danych: <br />— Exchange  <br />— SharePoint  <br />— OneDrive  <br />— Microsoft 365 grupy <br />— Teams <br />- Yammer <br />— Skype dla firm |[Tworzenie i konfigurowanie zasad przechowywania](create-retention-policies.md)|
|Zapewnianie użytkownikom dodatkowego miejsca do magazynowania skrzynki pocztowej |[Włączanie archiwalnych skrzynek pocztowych w centrum zgodności](enable-archive-mailboxes.md)|
|Zachowywanie danych skrzynki pocztowej po opuszczeniu organizacji przez pracowników |[Tworzenie nieaktywnych skrzynek pocztowych i zarządzanie nimi](create-and-manage-inactive-mailboxes.md)|
|Upload danych skrzynki pocztowej z plików PST |[Importowanie plików PST za pomocą przekazywania sieciowego](use-network-upload-to-import-pst-files.md)|


Jeśli masz scenariusz wymagający zarządzania cyklem życia poszczególnych elementów, zobacz typowe [scenariusze zarządzania rekordami](get-started-with-records-management.md#common-scenarios). 

## <a name="end-user-documentation"></a>Dokumentacja użytkownika końcowego

Zobacz następującą sekcję, aby uzyskać informacje na temat dokumentacji dla użytkowników końcowych w celu Microsoft 365 przechowywania.

Funkcje zarządzania informacjami, które obsługują zarządzanie skrzynkami pocztowymi (archiwizowanie, nieaktywne skrzynki pocztowe i importowanie), zwykle nie wymagają dokumentacji użytkownika końcowego.

### <a name="end-user-documentation-for-retention-and-deletion"></a>Dokumentacja użytkownika końcowego do przechowywania i usuwania

Większość zasad przechowywania działa dyskretnie w tle bez interakcji z użytkownikiem, więc potrzeba niewielkiej dokumentacji dla użytkowników. Zasady przechowywania dla Teams informują użytkowników o usunięciu ich wiadomości oraz link [Teams dotyczące zasad przechowywania](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

Jeśli jednak zasady przechowywania są uzupełniane etykietami przechowywania, te etykiety mają informacje o interfejsie użytkownika w Microsoft 365 aplikacjach. Przed wdrożeniem tych etykiet w sieci produkcyjnej należy podać informacje oraz instrukcje dla użytkowników końcowych i pomocy technicznej. Aby ułatwić użytkownikom stosowanie etykiet przechowywania SharePoint i OneDrive, zobacz Stosowanie etykiet przechowywania do plików w SharePoint [lub OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df).

Najbardziej skuteczną dokumentacją dla użytkowników końcowych będą zawsze dostosowane wskazówki i instrukcje dotyczące wybieranych nazw etykiet przechowywania i konfiguracji. Zobacz następującą stronę i materiały do pobrania, których możesz użyć w celu przeszkolenia użytkowników: Szkolenia dla użytkowników [końcowych dotyczące etykiet przechowywania](https://microsoft.github.io/ComplianceCxE/enduser/retention/).

