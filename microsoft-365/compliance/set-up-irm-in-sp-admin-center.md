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
description: Dowiedz się, jak chronić listy SharePoint i biblioteki dokumentów przy użyciu usługi SharePoint Online IRM za pośrednictwem usług Microsoft Azure Active Directory Rights Management Services (RMS).
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.openlocfilehash: 71881e5317153288f955c44d3c52cbf80a3f8def
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043005"
---
# <a name="set-up-information-rights-management-irm-in-sharepoint-admin-center"></a>Set up Information Rights Management (IRM) in SharePoint admin center

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

W usłudze SharePoint Online ochrona za pomocą usługi IRM jest stosowana do plików na poziomie listy i biblioteki. Aby twoja organizacja mogła korzystać z ochrony za pomocą usługi IRM, należy najpierw skonfigurować Rights Management. Usługa IRM korzysta z usługi Azure Rights Management z usługi Azure Information Protection w celu szyfrowania i przypisywania ograniczeń użycia. Niektóre plany Microsoft 365 obejmują Rights Management platformy Azure, ale nie wszystkie. Aby dowiedzieć się więcej, zobacz [Jak Office aplikacje i usługi obsługują usługę Azure Rights Management](/azure/information-protection/understand-explore/office-apps-services-support).
  
## <a name="turn-on-irm-service-using-sharepoint-admin-center"></a>Włączanie usługi IRM przy użyciu centrum administracyjnego SharePoint

Aby twoja organizacja mogła chronić SharePoint listy i biblioteki usługi IRM, musisz najpierw aktywować usługę Rights Management dla organizacji. Aby dowiedzieć się, jak to zrobić, zobacz [Aktywowanie usługi Azure Rights Management](/information-protection/deploy-use/activate-service). Aby włączyć usługę Rights Management, musisz użyć konta służbowego z uprawnieniami administratora globalnego. W przeciwnym razie nie będzie można używać funkcji IRM z usługą SharePoint Online.
  
Po aktywowaniu usługi Rights Management zaloguj się do centrum administracyjnego SharePoint, aby włączyć usługę IRM.
  
1. Zaloguj się jako administrator globalny lub administrator SharePoint.
    
2. Wybierz ikonę ![uruchamiania aplikacji Ikona uruchamiania aplikacji w Office 365.](../media/e5aee650-c566-4100-aaad-4cc2355d909f.png) w lewym górnym rogu i wybierz pozycję **Administrator**, aby otworzyć Centrum administracyjne platformy Microsoft 365. (Jeśli nie widzisz kafelka Administrator, nie masz uprawnień administratora w organizacji). 
    
3. W okienku po lewej stronie wybierz pozycję **Centra** \> administracyjne <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint centrum administracyjne</a>.
    
4. W okienku po lewej stronie wybierz **pozycję Ustawienia**, a następnie wybierz **stronę ustawień klasycznych**.
    
5. W sekcji **Informacje Rights Management (IRM)** wybierz pozycję **Użyj usługi IRM określonej w konfiguracji**, a następnie wybierz **pozycję Odśwież usługę IRM Ustawienia**. Po odświeżeniu ustawień usługi IRM osoby w organizacji mogą zacząć używać usługi IRM na listach SharePoint i bibliotekach dokumentów. Jednak wyświetlenie tych opcji może potrwać do godziny w Ustawienia biblioteki i Ustawienia listy.
    
## <a name="irm-enable-sharepoint-document-libraries-and-lists"></a>Włączanie usługi IRM SharePoint bibliotek dokumentów i list
<a name="__toc220831191"> </a>

Po odświeżeniu ustawień usługi IRM właściciele witryn mogą chronić SharePoint list i bibliotek dokumentów za pomocą usługi IRM. Aby uzyskać więcej informacji, zobacz [Stosowanie informacji Rights Management do listy lub biblioteki](apply-irm-to-a-list-or-library.md).
  
Gdy właściciele witryn włączą usługę IRM dla listy lub biblioteki, mogą chronić wszystkie obsługiwane typy plików na tej liście lub w bibliotece. Gdy usługa IRM jest włączona dla biblioteki, zarządzanie prawami ma zastosowanie do wszystkich plików w tej bibliotece. Po włączeniu usługi IRM dla listy zarządzanie prawami ma zastosowanie tylko do plików dołączonych do elementów listy, a nie do rzeczywistych elementów listy.
  
Gdy użytkownicy pobierają pliki z listy lub biblioteki z obsługą usługi IRM, pliki są szyfrowane, aby tylko autoryzowane osoby mogły je wyświetlać. Każdy plik zarządzany przez prawa zawiera również licencję wystawiania, która nakłada ograniczenia na osoby, które wyświetlają plik. Typowe ograniczenia obejmują tworzenie pliku tylko do odczytu, wyłączanie kopiowania tekstu, uniemożliwianie użytkownikom zapisywania lokalnej kopii i uniemożliwianie użytkownikom drukowania pliku. Programy klienckie, które mogą odczytywać typy plików obsługiwane przez usługę IRM, używają licencji wystawiania w pliku zarządzanym przez prawa, aby wymusić te ograniczenia. W ten sposób plik zarządzany przez prawa zachowuje ochronę nawet po pobraniu. Aby włączyć usługę IRM na liście lub w bibliotece, zobacz [Apply Information Rights Management to a list or library (Stosowanie informacji Rights Management do listy lub biblioteki](apply-irm-to-a-list-or-library.md)).
  
Nie można tworzyć ani edytować dokumentów w bibliotece z obsługą usługi IRM przy użyciu Office w przeglądarce. Zamiast tego jedna osoba naraz może pobierać i edytować pliki zaszyfrowane za pomocą usługi IRM. Użyj ewidencjonowania i wyewidencjonowania, aby zarządzać  *współautorem* lub tworzeniem wielu użytkowników. 
  
Po pobraniu pliku PDF z biblioteki chronionej przez usługę IRM Microsoft 365 tworzy chroniony plik PDF. Rozszerzenie pliku nie ulegnie zmianie, ale plik jest chroniony. Aby wyświetlić ten plik, potrzebujesz przeglądarki usługi Azure Information Protection, pełnego klienta usługi Azure Information Protection lub innej aplikacji, która obsługuje wyświetlanie chronionych plików PDF.
  
usługa SharePoint Online obsługuje szyfrowanie następujących typów plików:
  
- PDF
    
- Formaty plików 97-2003 dla następujących programów Microsoft Office: Word, Excel i PowerPoint
    
- Office formaty Open XML dla następujących programów Microsoft Office: Word, Excel i PowerPoint
    
- Format specyfikacji papieru XML (XPS)
 
> [!NOTE]
> Ochrona za pomocą usługi IRM nie może być stosowana do dokumentów chronionych (takich jak pliki PDF z podpisem cyfrowym), ponieważ SharePoint musi otworzyć dokument podczas przekazywania. 

## <a name="next-steps"></a>Następne kroki
<a name="__toc220831191"> </a>

Po włączeniu usługi IRM dla usługi SharePoint Online możesz rozpocząć stosowanie zarządzania prawami do list i bibliotek. Aby uzyskać informacje, zobacz [Apply Information Rights Management to a list or library (Stosowanie informacji Rights Management do listy lub biblioteki](apply-irm-to-a-list-or-library.md)).
  
Nowy klient synchronizacja usługi OneDrive dla Windows obsługuje teraz synchronizowanie bibliotek dokumentów SharePoint chronionych przez usługę IRM i lokalizacji OneDrive (o ile ustawienie IRM dla biblioteki nie jest ustawione na wygaśnięcie praw dostępu do dokumentów). Aby uzyskać więcej informacji lub rozpocząć wdrażanie nowego klienta synchronizacji, zobacz [Wdrażanie nowego klienta synchronizacja usługi OneDrive dla Windows](/onedrive/deploy-on-windows).
  
[Top of page](set-up-irm-in-sp-admin-center.md)
