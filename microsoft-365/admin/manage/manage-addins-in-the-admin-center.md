---
title: Zarządzanie dodatkami w centrum administracyjnym
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
description: Dowiedz się więcej o używaniu scentralizowanych dodatków do wdrażania dodatków dla użytkowników i grup w organizacji.
ms.openlocfilehash: 96bbdf5d4d9e4f1697fa0b85f902d8d758d356fa
ms.sourcegitcommit: 872ab0b6a225c20274916e07ed4cc4944be9509a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2022
ms.locfileid: "65678969"
---
# <a name="manage-add-ins-in-the-microsoft-365-admin-center"></a>Zarządzanie dodatkami w Centrum administracyjne platformy Microsoft 365

Office dodatki ułatwiają personalizację dokumentów i usprawniają sposób uzyskiwania dostępu do informacji w Internecie. Zobacz [Rozpoczynanie korzystania z dodatku Office](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862). 

Gdy administrator globalny lub administrator programu Exchange wdroży dodatki dla użytkowników w organizacji, może wyłączyć lub włączyć dodatki, edytować, usuwać i zarządzać dostępem do dodatków.

Aby uzyskać więcej informacji na temat instalowania dodatków z centrum administracyjnego, zobacz [Wdrażanie dodatków w centrum administracyjnym](./manage-deployment-of-add-ins.md).
  
## <a name="add-in-states"></a>Stany dodatku

Dodatek może mieć stan **Włączone** lub **Wyłączone** .
  
| Stan | Co oznacza stan | Wpływ |
|:-----|:-----|:-----|
|**Aktywny**  <br/> |Administrator przekazał dodatek i przypisał go do użytkowników lub grup.  <br/> |Użytkownicy i grupy przypisani do dodatku mogą go zobaczyć w odpowiednich klientach.  <br/> |
|**Wyłączony**  <br/> |Administrator wyłączył dodatek.  <br/> |Użytkownicy i grupy przypisani do dodatku nie mają już do niego dostępu.  <br/> Jeśli stan dodatku zostanie zmieniony na Aktywny, użytkownicy i grupy ponownie będą mieli do niego dostęp.  <br/> |
|**Deleted**  <br/> |Administrator usunął dodatek.  <br/> |Użytkownicy i grupy przypisani do dodatku nie będą już mieli do niego dostępu.  <br/> |
   
Rozważ usunięcie dodatku, jeśli nikt już go nie używa. Na przykład wyłączenie dodatku może mieć sens, jeśli dodatek jest używany tylko w określonych porach roku.

## <a name="delete-an-add-in"></a>Usuwanie dodatku

Możesz również usunąć wdrożony dodatek.

1. W centrum administracyjnym przejdź do strony **Ustawienia** >  **Integrated apps (Aplikacje Ustawienia Integrated).**

2. Wybierz wdrożony dodatek, a następnie wybierz kartę **Konfiguracja** .

3. W okienku **Konfiguracja** przejdź do pozycji **Zaawansowane Ustawienia** >  **Dodaj ins**.

4. Ponownie wybierz dodatek z listy.

5. Wybierz pozycję **Usuń dodatek**. Usuń przycisk Dodatek w prawym dolnym rogu.

6. Zweryfikuj wybrane opcje i wybierz pozycję **Usuń**.

## <a name="edit-add-in-access"></a>Edytowanie dostępu do dodatku

Po wdrożeniu administratorzy mogą również zarządzać dostępem użytkowników do dodatków.

1. W centrum administracyjnym przejdź do strony **Ustawienia** >  **Integrated apps (Aplikacje Ustawienia Integrated).**

2. Wybierz wdrożony dodatek.

3. Kliknij pozycję **Edytuj** **w obszarze KtoTo ma dostęp**.

4. Zapisz zmiany.

## <a name="prevent-add-in-downloads-by-turning-off-the-office-store-across-all-clients-except-outlook"></a>Zapobiegaj pobieraniu dodatków, wyłączając magazyn Office dla wszystkich klientów (z wyjątkiem Outlook)

> [!NOTE]
> Instalacja dodatków programu Outlook jest zarządzana przez [osobny proces](/exchange/clients-and-mobile-in-exchange-online/add-ins-for-outlook/specify-who-can-install-and-manage-add-ins).

Jako organizacja możesz uniemożliwić pobieranie nowych Office dodatków ze Sklepu Office. Możesz to połączyć z funkcją scentralizowanego wdrażania, aby mieć pewność, że w Twojej organizacji będą wdrażane tylko zatwierdzone dodatki.
  
**Aby wyłączyć pozyskiwanie dodatków**
  
1. W centrum administracyjnym przejdź do strony **ustawień organizacji** \> Ustawienia.[](https://go.microsoft.com/fwlink/p/?linkid=2053743)

2. Wybierz pozycję **Aplikacje i usługi należące do użytkownika**.
    
3. Wyczyść opcję zezwalania użytkownikom na dostęp do magazynu Office.

    Uniemożliwi to wszystkim użytkownikom pobieranie następujących dodatków ze sklepu.
      
    - Dodatki dla programu Word, Excel i PowerPoint 2016 z poziomu systemów:
        
      - Windows
      - Mac
      - Pakiet Office
        
        
    - Pobierania rozpoczynające się ciągiem **AppSource**
        
    - Dodatki w Microsoft 365
        
    Użytkownik, który próbuje uzyskać dostęp do sklepu, zobaczy następujący komunikat: **Niestety, Microsoft 365 został skonfigurowany tak, aby uniemożliwić indywidualne pozyskiwanie dodatków Office Store.**
  
Opcja wyłączenia dostępu do Sklepu Office jest obsługiwana w następujących wersjach:
  
- Windows: 16.0.9001 — obecnie dostępne.
    
- Mac: 16.10.18011401  obecnie dostępne.
    
- iOS: 2.9.18010804  obecnie dostępne.
    
- Sieć Web — obecnie dostępna.
    
Włączenie tej opcji nie uniemożliwia administratorowi przypisywania dodatków ze Sklepu Office za pomocą scentralizowanego wdrażania.

> [!NOTE] 
> Dodatki, takie jak Visio Data Visualizer, Mapy Bing i People Graph, będą nadal wyświetlane na wstążce, nawet jeśli administrator wyłączył Sklep. Aby usunąć te linki, administratorzy muszą wyłączyć magazyn za pośrednictwem obiektu zasady grupy (GPO).
  
Aby uniemożliwić użytkownikom logowanie się przy użyciu konta Microsoft, możesz ograniczyć logowanie tylko do kont organizacji. Aby uzyskać więcej informacji, zobacz [Identity, authentication, and authorization in Office 2016 (Tożsamość, uwierzytelnianie i autoryzacja w Office 2016 r.).](/DeployOffice/security/identity-authentication-and-authorization-in-office)  

> [!NOTE] 
> Uniemożliwienie użytkownikom dostępu do sklepu office uniemożliwi im również [ładowanie bezpośrednie Office dodatków do testowania z udziału sieciowego](/office/dev/add-ins/testing/create-a-network-shared-folder-catalog-for-task-pane-and-content-add-ins).

## <a name="more-about-the-end-user-experience-with-add-ins"></a>Więcej informacji o środowisku użytkownika końcowego z dodatkami

Po wdrożeniu dodatku użytkownicy końcowi mogą zacząć z niego korzystać w swoich aplikacjach Office. Dodatek jest wyświetlany na wszystkich platformach obsługiwanych przez dodatek. Zobacz [Rozpoczynanie korzystania z dodatku Office](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862). 
  
Jeśli dodatek obsługuje polecenia dodatku, pojawią się one na wstążce pakietu Office. W poniższym przykładzie jest widoczne polecenie **Wyszukaj cytat** dla dodatku **Cytaty**. 

![Office wstążkę z cytatami wyszukiwania.](../../media/553b0c0a-65e9-4746-b3b0-8c1b81715a86.png)
  
Jeśli wdrożony dodatek nie obsługuje poleceń dodatku lub chcesz wyświetlić wszystkie wdrożone dodatki, możesz to zrobić w obszarze **Moje dodatki**. 
  
### <a name="in-word-2016-excel-2016-or-powerpoint-2016"></a>W programie Word 2016, Excel 2016 lub PowerPoint 2016

1. Wybierz pozycję **Wstaw \> moje dodatki**. 
    
2. Wybierz kartę **Zarządzane przez administratora** w oknie Dodatki pakietu Office. 
    
3. Kliknij dwukrotnie wdrożony wcześniej dodatek (w tym przykładzie **Citations**).

    ![Administracja karta Zarządzane na stronie dodatków Office.](../../media/fd36ba81-9882-40f0-9fce-74f991aa97d5.png)
  
### <a name="in-outlook"></a>W programie Outlook

1. Na wstążce **Narzędzia** główne wybierz pozycję **Pobierz dodatki**.

    ![Przycisk Zapisz w Outlook.](../../media/getaddinsicon.png)
  
2. Wybierz pozycję **Zarządzane przez administratora** w lewym okienku nawigacji. 

## <a name="related-content"></a>Zawartość pokrewna

[Osoby niepełnoletnie i uzyskiwanie dodatków z Microsoft Store](./minors-and-acquiring-addins-from-the-store.md)

