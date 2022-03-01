---
title: Zarządzanie dodatki w centrum administracyjnym
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: Dowiedz się więcej o wdrażaniu dodatków w celu ich wdrażania u użytkowników i grup w organizacji za pomocą funkcji Scentralizowane dodatki.
ms.openlocfilehash: d2d1c4d36bf37ad82ac5c720931146c0dfb2220d
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63028064"
---
# <a name="manage-add-ins-in-the-admin-center"></a>Zarządzanie dodatki w centrum administracyjnym

Office dodatki ułatwiają personalizowanie dokumentów i usprawniają uzyskiwanie dostępu do informacji w sieci Web. Zobacz [Rozpoczynanie korzystania Office dodatku](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862). 

Gdy administrator wdroży dodatki dla użytkowników w organizacji, może wyłączyć lub włączyć dodatki, edytować, usunąć dodatki i zarządzać ich dostępem.

Aby uzyskać więcej informacji na temat instalowania dodatków z centrum administracyjnego, zobacz Wdrażanie [dodatków w centrum administracyjnym](./manage-deployment-of-add-ins.md).
  
## <a name="add-in-states"></a>Stany dodatku

Dodatek może być w stanie Wyłączony lub **Wł**.
  
| Stan | Co oznacza stan | Wpływ |
|:-----|:-----|:-----|
|**Aktywny**  <br/> |Administrator przekazał dodatek i przypisał go do użytkowników lub grup.  <br/> |Użytkownicy i grupy przypisani do dodatku mogą go zobaczyć w odpowiednich klientach.  <br/> |
|**Wyłączony**  <br/> |Administrator wyłączył dodatek.  <br/> |Użytkownicy i grupy przypisani do dodatku nie mają już do niego dostępu.  <br/> Jeśli stan dodatku zostanie zmieniony na Aktywny, użytkownicy i grupy ponownie będą mieli do niego dostęp.  <br/> |
|**Usunięty**  <br/> |Administrator usunął dodatek.  <br/> |Użytkownicy i grupy przypisani do dodatku nie będą już mieli do niego dostępu.  <br/> |
   
Rozważ usunięcie dodatku, jeśli już nikt go nie używa. Na przykład wyłączenie dodatku może mieć sens, jeśli dodatek jest używany tylko w konkretnych godzinach roku.

## <a name="delete-an-add-in"></a>Usuwanie dodatku

Możesz również usunąć dodatek, który został wdrożony.

1. W centrum administracyjnym przejdź **do strony Ustawienia** >  **Uintegrowane** aplikacje.

2. Wybierz wdrożony dodatek, a następnie wybierz **kartę** Konfiguracja.

3. W **okienku** Konfiguracja przejdź do **Ustawienia** >  **Add-in.**

4. Ponownie wybierz dodatek z listy.

5. Wybierz **pozycję Usuń dodatek**. Usuń przycisk Dodatek w prawym dolnym rogu.

6. Sprawdź poprawność wybranych opcji, a następnie wybierz **pozycję Usuń**.

## <a name="edit-add-in-access"></a>Edytowanie dostępu do dodatku

Po wdrożeniu administratorzy mogą również zarządzać dostępem użytkowników do dodatków.

1. W centrum administracyjnym przejdź **do strony Ustawienia** >  **Uintegrowane** aplikacje.

2. Wybierz wdrożony dodatek.

3. Kliknij pozycję **Edytuj w** obszarze **KtoTo dostęp**.

4. Zapisz zmiany.

## <a name="prevent-add-in-downloads-by-turning-off-the-office-store-across-all-clients-except-outlook"></a>Uniemożliwiaj pobieranie dodatków przez wyłączenie sklepu Office wszystkich klientów (z wyjątkiem Outlook)

> [!NOTE]
> Instalacja dodatków programu Outlook jest zarządzana przez [osobny proces](/exchange/clients-and-mobile-in-exchange-online/add-ins-for-outlook/specify-who-can-install-and-manage-add-ins).

Być może zechcesz zablokować pobieranie nowych dodatków pakietu Office ze Sklepu Office w swojej organizacji. Możesz to połączyć z funkcją scentralizowanego wdrażania, aby mieć pewność, że w Twojej organizacji będą wdrażane tylko zatwierdzone dodatki.
  
**Aby wyłączyć zakup dodatków**
  
1. W centrum administracyjnym przejdź **do strony Ustawienia** \> [ustawienia organizacji](https://go.microsoft.com/fwlink/p/?linkid=2053743).

2. Wybierz **pozycję Aplikacje i usługi należące do użytkownika**.
    
3. Wyczyść tę opcję, aby pozwolić użytkownikom na uzyskiwanie dostępu Office sklepu.

    Uniemożliwi to wszystkim użytkownikom pobieranie następujących dodatków ze sklepu.
      
    - Dodatki dla programu Word, Excel i PowerPoint 2016 z poziomu systemów:
        
      - Windows
      - Mac
      - Pakiet Office
        
        
    - Pobierania rozpoczynające się ciągiem **AppSource**
        
    - Dodatki w obrębie Microsoft 365
        
    Użytkownik, który spróbuje uzyskać dostęp do sklepu, zobaczy następujący komunikat: Niestety **, Microsoft 365 skonfigurowano**, aby uniemożliwić indywidualne uzyskiwanie dodatków ze Sklepu Office.
  
Opcja wyłączenia dostępu do Sklepu Office jest obsługiwana w następujących wersjach:
  
- Windows: 16.0.9001 — obecnie dostępne.
    
- Mac: 16.10.18011401  obecnie dostępne.
    
- iOS: 2.9.18010804  obecnie dostępne.
    
- Sieć Web — obecnie dostępna.
    
Włączenie tej opcji nie uniemożliwia administratorowi przypisywania dodatków ze Sklepu Office za pomocą scentralizowanego wdrażania.

> [!NOTE] 
> Dodatki, takie jak Wizualizator Visio danych, Mapy Bing i Osoby Graph nadal będą widoczne na wstążce, nawet jeśli administrator wyłączył Sklep. Aby usunąć te linki, administratorzy muszą wyłączyć funkcję Przechowywania za pośrednictwem zasady grupy danych (GPO).
  
Aby uniemożliwić użytkownikom logowanie się przy użyciu konta Microsoft, możesz ograniczyć logowanie tylko do kont organizacji. Aby uzyskać więcej informacji, zobacz [Tożsamość, uwierzytelnianie i autoryzacja w programie Office 2016](/DeployOffice/security/identity-authentication-and-authorization-in-office).  

> [!NOTE] 
> Uniemożliwienie użytkownikom uzyskiwania dostępu do sklepu office uniemożliwi im również ładowanie Office dodatków w celu testowania [z udziału sieciowego](/office/dev/add-ins/testing/create-a-network-shared-folder-catalog-for-task-pane-and-content-add-ins).

## <a name="more-about-the-end-user-experience-with-add-ins"></a>Więcej informacji na temat obsługi przez użytkowników końcowych dodatków

Po wdrożeniu dodatku użytkownicy końcowi mogą zacząć go używać w swoich Office aplikacjach. Dodatek pojawi się na wszystkich platformach, które obsługuje ten dodatek. Zobacz [Rozpoczynanie korzystania z Office dodatku.](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862) 
  
Jeśli dodatek obsługuje polecenia dodatku, pojawią się one na wstążce pakietu Office. W poniższym przykładzie jest widoczne polecenie **Wyszukaj cytat** dla dodatku **Cytaty**. 

![Office wstążce z wyszukiwaniem cytatów.](../../media/553b0c0a-65e9-4746-b3b0-8c1b81715a86.png)
  
Jeśli wdrożony dodatek nie obsługuje poleceń dodatku lub chcesz wyświetlić wszystkie wdrożone dodatki, możesz to zrobić w obszarze **Moje dodatki**. 
  
### <a name="in-word-2016-excel-2016-or-powerpoint-2016"></a>W programie Word 2016, Excel 2016 lub PowerPoint 2016

1. Wybierz **pozycję \> Wstaw moje dodatki**. 
    
2. Wybierz kartę **Zarządzane przez administratora** w oknie Dodatki pakietu Office. 
    
3. Kliknij dwukrotnie dodatek wdrożony wcześniej (w tym przykładzie **Cytaty**).

    ![Karta Zarządzane przez administratora na Office Dodatki zaawansowane.](../../media/fd36ba81-9882-40f0-9fce-74f991aa97d5.png)
  
### <a name="in-outlook"></a>W programie Outlook

1. Na **wstążce Narzędzia** głównej wybierz **pozycję Pobierz dodatki**.

    ![Przycisk Sklep w Outlook.](../../media/getaddinsicon.png)
  
2. Wybierz **pozycję Administrator zarządzana** w lewym okienku narracji. 

## <a name="related-content"></a>Zawartość pokrewna

[Osoby niepełnoletnie i uzyskiwanie dodatków z Microsoft Store](./minors-and-acquiring-addins-from-the-store.md)

