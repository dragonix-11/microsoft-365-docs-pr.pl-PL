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
description: Dowiedz się, jak używać usługi IRM SharePoint Online za pośrednictwem usług Microsoft Azure Active Directory zarządzania prawami dostępu (RMS) w celu ochrony SharePoint list i bibliotek dokumentów.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.openlocfilehash: 8c0f60ad1a571ba13ba83e3e92c1b5aca6535bb1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63311637"
---
# <a name="set-up-information-rights-management-irm-in-sharepoint-admin-center"></a>Set up Information Rights Management (IRM) in SharePoint admin center

W SharePoint Online ochrona usługi IRM jest stosowana do plików na poziomie listy i biblioteki. Aby twoja organizacja miała możliwość korzystania z ochrony usługi IRM, musisz najpierw skonfigurować zarządzanie prawami dostępu. Usługa IRM korzysta z usługi Azure Rights Management z usługi Azure Information Protection do szyfrowania i przypisywania ograniczeń dotyczących użycia. Niektóre Microsoft 365 obejmują usługę Azure Rights Management, ale nie wszystkie. Aby dowiedzieć się więcej, zobacz [Jak Office i usługi obsługują usługę Azure Rights Management](/azure/information-protection/understand-explore/office-apps-services-support).
  
## <a name="turn-on-irm-service-using-sharepoint-admin-center"></a>Włączanie usługi IRM przy użyciu SharePoint administracyjnego

Aby Twoja organizacja miała możliwość ochrony za pomocą usługi IRM SharePoint list i bibliotek, musisz najpierw aktywować usługę zarządzania prawami dostępu w organizacji. Aby dowiedzieć się, jak [to zrobić, zobacz Aktywowanie usługi Azure Rights Management](/information-protection/deploy-use/activate-service). Aby włączyć usługę zarządzania prawami, musisz użyć konta służbowego z uprawnieniami administratora globalnego. W przeciwnym razie nie będzie można korzystać z funkcji usługi IRM z usługą SharePoint Online.
  
Po aktywowaniu usługi zarządzania prawami dostępu zaloguj się do centrum administracyjnego usługi SharePoint, aby włączyć usługę IRM.
  
1. Zaloguj się jako administrator globalny lub administrator SharePoint administratorem.
    
2. Wybierz ikonę Uruchamianie aplikacji ![Ikona Uruchamianie aplikacji w Office 365.](../media/e5aee650-c566-4100-aaad-4cc2355d909f.png) w lewym górnym rogu i wybierz pozycję **Administrator**, aby otworzyć centrum administracyjne platformy Microsoft 365. (Jeśli nie widzisz kafelka Administrator, nie masz uprawnień administratora w swojej organizacji). 
    
3. W okienku po lewej stronie wybierz pozycję **Centra** \> <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">administracyjne SharePoint centrum administracyjne.</a>
    
4. W okienku po lewej stronie wybierz **pozycję ustawienia**, a następnie wybierz stronę **ustawień klasycznych**.
    
5. W sekcji **Zarządzanie prawami do informacji (IRM)** wybierz pozycję Użyj usługi **IRM** określonej w konfiguracji, a następnie wybierz pozycję Odśwież **usługę IRM Ustawienia**. Po odświeżeniu ustawień usługi IRM osoby w Twojej organizacji mogą zacząć używać usługi IRM na swoich listach SharePoint i bibliotekach dokumentów. Jednak w Ustawienia przypadku opcji dostępnych w bibliotekach i listach może upłynie nawet godzinę Ustawienia.
    
## <a name="irm-enable-sharepoint-document-libraries-and-lists"></a>Włączanie usługi IRM SharePoint list i bibliotek dokumentów
<a name="__toc220831191"> </a>

Po odświeżeniu ustawień usługi IRM właściciele witryn mogą chronić swoje listy SharePoint i biblioteki dokumentów za pomocą usługi IRM. Aby uzyskać więcej informacji, zobacz [Stosowanie zarządzania prawami do informacji do listy lub biblioteki](apply-irm-to-a-list-or-library.md).
  
Gdy właściciele witryn włączą usługę IRM dla listy lub biblioteki, mogą chronić wszystkie obsługiwane typy plików na tej liście lub w bibliotece. Jeśli funkcja IRM jest włączona dla biblioteki, zarządzanie prawami dostępu dotyczy wszystkich plików w tej bibliotece. Po włączeniu usługi IRM dla listy zarządzanie prawami dostępu dotyczy tylko plików dołączonych do elementów listy, a nie rzeczywistych elementów listy.
  
Gdy osoby pobierają pliki z listy lub biblioteki z obsługą usługi IRM, pliki są szyfrowane, dzięki czemu mogą je wyświetlać tylko uprawnione osoby. Każdy plik zarządzania prawami dostępu zawiera również licencję wydawania, która nakłada ograniczenia na osoby, które przeglądają plik. Typowe ograniczenia obejmują tworzenie pliku tylko do odczytu, wyłączanie kopiowania tekstu, uniemożliwianie zapisywania kopii lokalnej i uniemożliwianie drukowania pliku. Programy klienckie, które mogą odczytywać typy plików obsługiwane przez usługę IRM, używają licencji wydawania w ramach pliku zarządzanego prawami do wymuszenia tych ograniczeń. W ten sposób plik zarządzany prawami dostępu zachowuje swoją ochronę nawet po jego pobraniu. Aby włączyć usługę IRM dla listy lub biblioteki, zobacz [Stosowanie usługi Zarządzanie prawami do informacji do listy lub biblioteki](apply-irm-to-a-list-or-library.md).
  
Nie można tworzyć ani edytować dokumentów w bibliotece z obsługą usługi IRM przy Office przeglądarce. Zamiast tego jedna osoba może pobierać i edytować pliki zaszyfrowane za pomocą usługi IRM. Zarządzanie współtwodaniem lub tworzeniem dla wielu użytkowników  za pomocą zaewidencjncji i wyewidencjncjowania. 
  
Po pobraniu pliku PDF z biblioteki chronionej za pomocą usługi IRM Microsoft 365 chroniony plik PDF. Rozszerzenie pliku nie zmieni się, ale plik będzie chroniony. Aby można było wyświetlić ten plik, potrzebujesz przeglądarki Azure Information Protection, pełnego klienta usługi Azure Information Protection lub innej aplikacji obsługującej wyświetlanie chronionych plików PDF. 
  
SharePoint Online obsługuje szyfrowanie następujących typów plików:
  
- PDF
    
- Formaty plików 97–2003 dla następujących Microsoft Office programów: Word, Excel i PowerPoint
    
- Formaty Office Open XML dla następujących programów Microsoft Office: Word, Excel i PowerPoint
    
- Format XPS (XML Paper Specification)
 
> [!NOTE]
> Ochrony usługi IRM nie można stosować do chronionych dokumentów (na przykład cyfrowo podpisanych plików PDF), ponieważ SharePoint otworzyć dokument podczas przekazywania. 

## <a name="next-steps"></a>Następne kroki
<a name="__toc220831191"> </a>

Po włączeniu usługi IRM dla usługi SharePoint Online możesz zacząć stosować zarządzanie prawami do list i bibliotek. Aby uzyskać informacje, [zobacz Stosowanie zarządzania prawami do informacji do listy lub biblioteki](apply-irm-to-a-list-or-library.md).
  
Nowy klient synchronizacja usługi OneDrive dla usługi Windows obsługuje teraz synchronizowanie chronionych za pomocą usługi IRM bibliotek dokumentów programu SharePoint i lokalizacji programu OneDrive (o ile ustawienie usługi IRM dla biblioteki nie jest ustawione na wygasające prawa dostępu do dokumentu). Aby uzyskać więcej informacji lub rozpocząć wdrażanie nowego klienta synchronizacji, zobacz Wdrażanie nowego synchronizacja usługi OneDrive [klienta Windows](/onedrive/deploy-on-windows).
  
[Top of page](set-up-irm-in-sp-admin-center.md)