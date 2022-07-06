---
title: Set up Information Rights Management (IRM) in SharePoint admin center
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- SPO160
- MET150
ms.assetid: 239ce6eb-4e81-42db-bf86-a01362fed65c
description: Dowiedz się, jak używać usługi SharePoint Online IRM za pośrednictwem usług Microsoft Azure Active Directory Rights Management Services (RMS) do ochrony list programu SharePoint i bibliotek dokumentów.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.openlocfilehash: af8f19fe455c1aca1d6b7aab045a9aea5b5efee5
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632052"
---
# <a name="set-up-information-rights-management-irm-in-sharepoint-admin-center"></a>Set up Information Rights Management (IRM) in SharePoint admin center

W usłudze SharePoint Online ochrona za pomocą usługi IRM jest stosowana do plików na poziomie listy i biblioteki. Aby twoja organizacja mogła korzystać z ochrony za pomocą usługi IRM, musisz najpierw skonfigurować usługę Rights Management. Usługa IRM korzysta z usługi Azure Rights Management z usługi Azure Information Protection w celu szyfrowania i przypisywania ograniczeń użycia. Niektóre plany platformy Microsoft 365 obejmują usługę Azure Rights Management, ale nie wszystkie. Aby dowiedzieć się więcej, zobacz [Jak aplikacje i usługi pakietu Office obsługują usługę Azure Rights Management](/azure/information-protection/understand-explore/office-apps-services-support).
  
## <a name="turn-on-irm-service-using-sharepoint-admin-center"></a>Włączanie usługi IRM przy użyciu centrum administracyjnego programu SharePoint

Aby twoja organizacja mogła chronić listy i biblioteki programu SharePoint za pomocą usługi IRM, musisz najpierw aktywować usługę Rights Management dla swojej organizacji. Aby dowiedzieć się, jak to zrobić, zobacz [Aktywowanie usługi Azure Rights Management](/information-protection/deploy-use/activate-service). Aby włączyć usługę Rights Management, musisz użyć konta służbowego z uprawnieniami administratora globalnego. W przeciwnym razie nie będzie można używać funkcji IRM w usłudze SharePoint Online.
  
Po aktywowaniu usługi Rights Management zaloguj się do centrum administracyjnego programu SharePoint, aby włączyć usługę IRM.
  
1. Zaloguj się jako administrator globalny lub administrator programu SharePoint.
    
2. Wybierz ikonę ![uruchamiania aplikacji Ikona uruchamiania aplikacji w Office 365.](../media/e5aee650-c566-4100-aaad-4cc2355d909f.png) w lewym górnym rogu i wybierz **pozycję Administracja**, aby otworzyć Centrum administracyjne platformy Microsoft 365. (Jeśli nie widzisz kafelka Administracja, nie masz uprawnień administratora w organizacji). 
    
3. W okienku po lewej stronie wybierz **pozycję Administracja centrum** \> <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">administracyjne programu SharePoint</a>.
    
4. W okienku po lewej stronie wybierz **pozycję Ustawienia**, a następnie wybierz **stronę ustawień klasycznych**.
    
5. W sekcji **Zarządzanie prawami do informacji (IRM)** wybierz pozycję **Użyj usługi IRM określonej w konfiguracji**, a następnie wybierz pozycję **Odśwież ustawienia usługi IRM**. Po odświeżeniu ustawień usługi IRM osoby w organizacji mogą rozpocząć korzystanie z usługi IRM na listach programu SharePoint i bibliotekach dokumentów. Jednak wyświetlenie tych opcji może potrwać do godziny w obszarze Ustawienia biblioteki i Ustawienia listy.
    
## <a name="irm-enable-sharepoint-document-libraries-and-lists"></a>Włączanie bibliotek i list dokumentów programu SharePoint przez usługę IRM
<a name="__toc220831191"> </a>

Po odświeżeniu ustawień usługi IRM właściciele witryn mogą chronić swoje listy programu SharePoint i biblioteki dokumentów za pomocą usługi IRM. Aby uzyskać więcej informacji, zobacz [Stosowanie usługi Information Rights Management do listy lub biblioteki](apply-irm-to-a-list-or-library.md).
  
Gdy właściciele witryn włączą usługę IRM dla listy lub biblioteki, mogą chronić wszystkie obsługiwane typy plików na tej liście lub w bibliotece. Gdy usługa IRM jest włączona dla biblioteki, zarządzanie prawami ma zastosowanie do wszystkich plików w tej bibliotece. Po włączeniu usługi IRM dla listy zarządzanie prawami ma zastosowanie tylko do plików dołączonych do elementów listy, a nie do rzeczywistych elementów listy.
  
Gdy użytkownicy pobierają pliki z listy lub biblioteki z obsługą usługi IRM, pliki są szyfrowane, aby tylko autoryzowane osoby mogły je wyświetlać. Każdy plik zarządzany przez prawa zawiera również licencję wystawiania, która nakłada ograniczenia na osoby, które wyświetlają plik. Typowe ograniczenia obejmują tworzenie pliku tylko do odczytu, wyłączanie kopiowania tekstu, uniemożliwianie użytkownikom zapisywania lokalnej kopii i uniemożliwianie użytkownikom drukowania pliku. Programy klienckie, które mogą odczytywać typy plików obsługiwane przez usługę IRM, używają licencji wystawiania w pliku zarządzanym przez prawa, aby wymusić te ograniczenia. W ten sposób plik zarządzany przez prawa zachowuje ochronę nawet po pobraniu. Aby włączyć usługę IRM na liście lub w bibliotece, zobacz [Apply Information Rights Management to a list or library (Stosowanie usługi Information Rights Management do listy lub biblioteki](apply-irm-to-a-list-or-library.md)).
  
Nie można tworzyć ani edytować dokumentów w bibliotece z obsługą usługi IRM przy użyciu pakietu Office w przeglądarce. Zamiast tego jedna osoba naraz może pobierać i edytować pliki zaszyfrowane za pomocą usługi IRM. Użyj ewidencjonowania i wyewidencjonowania, aby zarządzać  *współautorem* lub tworzeniem wielu użytkowników. 
  
Po pobraniu pliku PDF z biblioteki chronionej przez usługę IRM platforma Microsoft 365 tworzy chroniony plik PDF. Rozszerzenie pliku nie ulegnie zmianie, ale plik jest chroniony. Aby wyświetlić ten plik, potrzebujesz przeglądarki usługi Azure Information Protection, pełnego klienta usługi Azure Information Protection lub innej aplikacji, która obsługuje wyświetlanie chronionych plików PDF.
  
Usługa SharePoint Online obsługuje szyfrowanie następujących typów plików:
  
- PDF
    
- Formaty plików 97-2003 dla następujących programów pakietu Microsoft Office: Word, Excel i PowerPoint
    
- Formaty Open XML pakietu Office dla następujących programów pakietu Microsoft Office: Word, Excel i PowerPoint
    
- Format specyfikacji papieru XML (XPS)
 
> [!NOTE]
> Ochrona za pomocą usługi IRM nie może być stosowana do dokumentów chronionych (takich jak pliki PDF z podpisem cyfrowym), ponieważ program SharePoint musi otworzyć dokument podczas przekazywania. 

## <a name="next-steps"></a>Następne kroki
<a name="__toc220831191"> </a>

Po włączeniu usługi IRM dla usługi SharePoint Online możesz rozpocząć stosowanie zarządzania prawami do list i bibliotek. Aby uzyskać informacje, zobacz [Apply Information Rights Management to a list or library (Stosowanie usługi Information Rights Management do listy lub biblioteki](apply-irm-to-a-list-or-library.md)).
  
Nowy klient synchronizacja usługi OneDrive dla systemu Windows obsługuje teraz synchronizowanie bibliotek dokumentów programu SharePoint chronionych przez usługę IRM i lokalizacji usługi OneDrive (o ile ustawienie IRM dla biblioteki nie jest ustawione na wygaśnięcie praw dostępu do dokumentów). Aby uzyskać więcej informacji lub rozpocząć wdrażanie nowego klienta synchronizacji, zobacz [Wdrażanie nowego klienta synchronizacja usługi OneDrive dla systemu Windows](/onedrive/deploy-on-windows).
  
[Top of page](set-up-irm-in-sp-admin-center.md)
