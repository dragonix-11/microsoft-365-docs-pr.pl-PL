---
title: Zbiorcze importowanie kontaktów zewnętrznych do Exchange Online
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 6/29/2018
audience: End User
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOP150
ms.assetid: bed936bc-0969-4a6d-a7a5-66305c14e958
ms.custom: admindeeplinkEXCHANGE
description: Dowiedz się, jak administratorzy mogą używać programu Exchange Online programu PowerShell i pliku CSV do zbiorczego importowania kontaktów zewnętrznych do globalnej listy adresów.
ms.openlocfilehash: 40e8c44a45e8d8d0c416f3f00df57e24504a4e70
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633812"
---
# <a name="bulk-import-external-contacts-to-exchange-online"></a>Zbiorcze importowanie kontaktów zewnętrznych do Exchange Online

**Ten artykuł jest przeznaczony dla administratorów. Czy próbujesz zaimportować kontakty do własnej skrzynki pocztowej? Zobacz [Importowanie kontaktów do programu Outlook](https://support.office.com/article/bb796340-b58a-46c1-90c7-b549b8f3c5f8)**
   
Czy Twoja firma ma wiele istniejących kontaktów biznesowych, które chcesz uwzględnić w udostępnionej książce adresowej (nazywanej również globalną listą adresów) w Exchange Online? Czy chcesz dodać kontakty zewnętrzne jako członków grup dystrybucyjnych, tak jak w przypadku użytkowników w firmie? Jeśli tak, możesz użyć Exchange Online programu PowerShell i pliku CSV (wartości rozdzielanej przecinkami) do zbiorczego importowania kontaktów zewnętrznych do Exchange Online. Jest to proces trzyetapowy:
  
[Krok 1. Tworzenie pliku CSV zawierającego informacje o kontaktach zewnętrznych](#step-1-create-a-csv-file-that-contains-information-about-the-external-contacts)

[Krok 2. Tworzenie kontaktów zewnętrznych za pomocą programu PowerShell](#step-2-create-the-external-contacts-with-powershell) 

[Krok 3. Dodawanie informacji do właściwości kontaktów zewnętrznych](#step-3-add-information-to-the-properties-of-the-external-contacts)

Po wykonaniu tych kroków w celu zaimportowania kontaktów można wykonać następujące dodatkowe zadania:
  
- [Dodawanie większej liczby kontaktów zewnętrznych](#add-more-external-contacts)
  
- [Ukrywanie kontaktów zewnętrznych w udostępnionej książce adresowej](#hide-external-contacts-from-the-shared-address-book)
  
## <a name="step-1-create-a-csv-file-that-contains-information-about-the-external-contacts"></a>Krok 1. Tworzenie pliku CSV zawierającego informacje o kontaktach zewnętrznych

Pierwszym krokiem jest utworzenie pliku CSV zawierającego informacje o każdym kontakcie zewnętrznym, który chcesz zaimportować do Exchange Online. 
  
1. Skopiuj następujący tekst do pliku tekstowego w Notatniku i zapisz go na pulpicie jako plik CSV przy użyciu sufiksu nazwy pliku .csv; na przykład ExternalContacts.csv.
    
    > [!TIP]
    > Jeśli język zawiera znaki specjalne (takie jak **å**, **ä** i **ö** w języku szwedzkim) zapisz plik CSV z kodowaniem UTF-8 lub innym kodowaniem Unicode podczas zapisywania pliku w Notatniku. 
  
    ```text
    ExternalEmailAddress,Name,FirstName,LastName,StreetAddress,City,StateorProvince,PostalCode,Phone,MobilePhone,Pager,HomePhone,Company,Title,OtherTelephone,Department,CountryOrRegion,Fax,Initials,Notes,Office,Manager
    danp@fabrikam.com,Dan Park,Dan,Park,1234 23rd Ave,Golden,CO,80215,206-111-1234,303-900-1234,555-1212,123-456-7890,Fabrikam,Shipping clerk,555-5555,Shipping,US,123-4567,R.,Good worker,31/1663,Dan Park
    pilar@contoso.com,Pilar Pinilla,Pilar,Pinilla,1234 Main St.,Seattle,WA,98017,206-555-0100,206-555-0101,206-555-0102,206-555-1234,Contoso,HR Manager,206-555-0104,Executive,US,206-555-0105,P.,Technical decision maker,31/1000,Dan Park
    ```

    Pierwszy wiersz lub wiersz nagłówka pliku CSV zawiera listę właściwości kontaktów, których można użyć podczas importowania ich do Exchange Online. Każda nazwa właściwości jest oddzielona przecinkiem. Każdy wiersz w wierszu nagłówka reprezentuje wartości właściwości do zaimportowania pojedynczego kontaktu zewnętrznego. 
    
    > [!NOTE]
    > Ten tekst zawiera przykładowe dane, które można usunąć. Ale nie usuwaj ani nie zmieniaj pierwszego wiersza (nagłówka). Zawiera wszystkie właściwości kontaktów zewnętrznych. 
  
2. Otwórz plik CSV w programie Microsoft Excel, aby edytować plik CSV, ponieważ znacznie łatwiej jest edytować plik CSV za pomocą programu Excel.
    
3. Utwórz wiersz dla każdego kontaktu, który chcesz zaimportować do Exchange Online. Wypełnij jak najwięcej komórek. Te informacje będą wyświetlane w udostępnionej książce adresowej dla każdego kontaktu. 
    
    > [!IMPORTANT]
    >  Następujące właściwości (które są pierwszymi czterema elementami w wierszu nagłówka) są wymagane do utworzenia kontaktu zewnętrznego i muszą być wypełnione w pliku CSV: **ExternalEmailAddress**, **Name**, **FirstName**, **LastName**. Polecenie programu PowerShell uruchamiane w kroku 2 użyje wartości tych właściwości do utworzenia kontaktów. 

## <a name="step-2-create-the-external-contacts-with-powershell"></a>Krok 2. Tworzenie kontaktów zewnętrznych za pomocą programu PowerShell

Następnym krokiem jest użycie pliku CSV utworzonego w kroku 1 i programie PowerShell w celu zbiorczego zaimportowania kontaktów zewnętrznych wymienionych w pliku CSV do Exchange Online. 
  
1.  Połącz program PowerShell z organizacją Exchange Online. Aby uzyskać instrukcje krok po kroku, zobacz [Connect to Exchange Online PowerShell (Nawiązywanie połączenia z programem PowerShell).](/powershell/exchange/connect-to-exchange-online-powershell) Podczas nawiązywania połączenia z programem Exchange Online programu PowerShell należy użyć nazwy użytkownika i hasła dla konta administratora globalnego. 
    
2. Po połączeniu programu PowerShell z programem Exchange Online przejdź do folderu pulpitu, w którym zapisano plik CSV w kroku 1, na przykład `C:\Users\Administrator\desktop`.
    
3. Uruchom następujące polecenie, aby utworzyć kontakty zewnętrzne:

    ```powershell
    Import-Csv .\ExternalContacts.csv|%{New-MailContact -Name $_.Name -DisplayName $_.Name -ExternalEmailAddress $_.ExternalEmailAddress -FirstName $_.FirstName -LastName $_.LastName}
    ```

    Tworzenie nowych kontaktów może trochę potrwać, w zależności od liczby importowanych kontaktów. Po zakończeniu działania polecenia program PowerShell wyświetla listę nowych kontaktów, które zostały utworzone. 
    
4. Aby wyświetlić nowe kontakty zewnętrzne, przejdź do centrum administracyjnego programu Exchange (EAC), a następnie kliknij pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2182970" target="_blank">**Kontakty**</a> **adresatów**\>. 
    
    > [!TIP]
    > Aby uzyskać instrukcje dotyczące nawiązywania połączenia z usługą EAC, zobacz [Centrum administracyjne programu Exchange w Exchange Online](/exchange/exchange-admin-center). 
  
5. W razie potrzeby kliknij przycisk **Odśwież** , aby zaktualizować listę i wyświetlić zaimportowane kontakty zewnętrzne. 
    
    Zaimportowane kontakty zostaną wyświetlone w udostępnionej książce adresowej w programie Outlook i Outlook w sieci Web.
    
    > [!NOTE]
    > Możesz również wyświetlić kontakty w Centrum administracyjne platformy Microsoft 365, przechodząc do pozycji **Kontakty użytkowników**\>. 

## <a name="step-3-add-information-to-the-properties-of-the-external-contacts"></a>Krok 3. Dodawanie informacji do właściwości kontaktów zewnętrznych

Po uruchomieniu polecenia w kroku 2 kontakty zewnętrzne są tworzone, ale nie zawierają żadnych informacji kontaktowych ani organizacji, czyli informacji z większości komórek w pliku CSV. Dzieje się tak, ponieważ podczas tworzenia nowych kontaktów zewnętrznych wypełniane są tylko wymagane właściwości. Nie martw się, jeśli nie masz wszystkich informacji wypełnionych w pliku CSV. Jeśli go tam nie ma, nie zostanie dodany.
  
1.  Połącz program PowerShell z organizacją Exchange Online. Aby uzyskać instrukcje krok po kroku, zobacz [Connect to Exchange Online PowerShell (Nawiązywanie połączenia z programem PowerShell).](/powershell/exchange/connect-to-exchange-online-powershell)
    
2. Przejdź do folderu pulpitu, w którym zapisano plik CSV w kroku 1; na przykład `C:\Users\Administrator\desktop`.
    
3. Uruchom następujące dwa polecenia, aby dodać inne właściwości z pliku CSV do kontaktów zewnętrznych utworzonych w kroku 2.
    
    ```powershell
    $Contacts = Import-CSV .\ExternalContacts.csv
  
    ```

    ```powershell
    $contacts | ForEach {Set-Contact $_.Name -StreetAddress $_.StreetAddress -City $_.City -StateorProvince $_.StateorProvince -PostalCode $_.PostalCode -Phone $_.Phone -MobilePhone $_.MobilePhone -Pager $_.Pager -HomePhone $_.HomePhone -Company $_.Company -Title $_.Title -OtherTelephone $_.OtherTelephone -Department $_.Department -Fax $_.Fax -Initials $_.Initials -Notes  $_.Notes -Office $_.Office -Manager $_.Manager}
    ```

    > [!NOTE]
    > Parametr  _Menedżera_ może być problematyczny. Jeśli komórka jest pusta w pliku CSV, zostanie wyświetlony błąd i żadne informacje o właściwości nie zostaną dodane do kontaktu. Jeśli nie musisz określać menedżera, po prostu usuń  ` -Manager $_.Manager ` go z poprzedniego polecenia programu PowerShell. 
  
    Ponownie może upłynąć trochę czasu, aby zaktualizować kontakty, w zależności od liczby zaimportowanych w kroku 1. 
    
4. Aby sprawdzić, czy właściwości zostały dodane do kontaktów: 
    
1. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnym programu Exchange</a> przejdź do pozycji **Kontakty** **adresatów**\>.
    
2. Kliknij kontakt, a następnie kliknij ikonę **Edytuj** ![edycję.](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) aby wyświetlić właściwości kontaktu. 
    
To wszystko! Użytkownicy mogą zobaczyć kontakty i dodatkowe informacje w książce adresowej Outlook i Outlook w sieci Web.
  
## <a name="add-more-external-contacts"></a>Dodawanie większej liczby kontaktów zewnętrznych

Możesz powtórzyć kroki od 1 do kroku 3, aby dodać nowe kontakty zewnętrzne w Exchange Online. Ty lub użytkownicy w firmie możesz po prostu dodać nowy wiersz w pliku CSV dla nowego kontaktu. Następnie możesz uruchomić polecenia programu PowerShell z kroków 2 i 3, aby utworzyć i dodać informacje do nowych kontaktów.
  
> [!NOTE]
> Po uruchomieniu polecenia w celu utworzenia nowych kontaktów może wystąpić błąd informujący, że kontakty, które zostały utworzone wcześniej, już istnieją. Zostanie jednak utworzony każdy nowy kontakt dodany do pliku CSV. 
  
## <a name="hide-external-contacts-from-the-shared-address-book"></a>Ukryj kontakty zewnętrzne w udostępnionej książce adresowej>

Niektóre firmy mogą używać tylko kontaktów zewnętrznych, aby można je było dodać jako członków grup dystrybucyjnych. W tym scenariuszu mogą chcieć ukryć kontakty zewnętrzne z udostępnionej książki adresowej. W tym celu wykonaj następujące czynności:
  
1.  Połącz program PowerShell z organizacją Exchange Online. Aby uzyskać instrukcje krok po kroku, zobacz [Connect to Exchange Online PowerShell (Nawiązywanie połączenia z programem PowerShell).](/powershell/exchange/connect-to-exchange-online-powershell)
    
2. Aby ukryć pojedynczy kontakt zewnętrzny, uruchom następujące polecenie.
    
    ```powershell
    Set-MailContact <external contact> -HiddenFromAddressListsEnabled $true 
    ```

    Aby na przykład ukryć pilar Pinilla z udostępnionej książki adresowej, uruchom następujące polecenie:

    ```powershell
    Set-MailContact "Pilar Pinilla" -HiddenFromAddressListsEnabled $true
    ```

3. Aby ukryć wszystkie kontakty zewnętrzne w udostępnionej książce adresowej, uruchom następujące polecenie:

    ```powershell
    Get-Contact -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'MailContact')} | Set-MailContact -HiddenFromAddressListsEnabled $true  
    ```

Po ich ukryciu kontakty zewnętrzne nie są wyświetlane w udostępnionej książce adresowej, ale nadal można dodać je jako członków grupy dystrybucyjnej.