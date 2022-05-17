---
title: Wdrażanie dodatki w centrum administracyjnym
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
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: Dowiedz się, jak wdrażać dodatki dla użytkowników i grup w organizacji przy użyciu scentralizowanego wdrożenia w centrum administracyjnym.
ms.openlocfilehash: a599023db47a46baa0318e026e70627320a6b1f8
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437530"
---
# <a name="deploy-add-ins-in-the-microsoft-365-admin-center"></a>Wdrażanie dodatków w Centrum administracyjne platformy Microsoft 365

Office dodatki ułatwiają personalizację dokumentów i usprawniają sposób uzyskiwania dostępu do informacji w Internecie (zobacz [Rozpoczynanie korzystania z dodatku Office](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862)). Jako administrator możesz wdrożyć dodatki Office dla użytkowników w organizacji przy użyciu funkcji Scentralizowane wdrażanie w <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a>. Scentralizowane wdrażanie jest zalecaną dla większości administratorów, najbogatszą w funkcje metodą wdrażania dodatków dla użytkowników oraz grup w organizacji.

Aby uzyskać więcej informacji na temat sposobu określania, czy organizacja może obsługiwać wdrożenie scentralizowane, zobacz [Określanie, czy scentralizowane wdrażanie dodatków działa w twojej organizacji](centralized-deployment-of-add-ins.md).

Aby dowiedzieć się więcej na temat zarządzania dodatkami po wdrożeniu, zobacz [Zarządzanie dodatkami w centrum administracyjnym](manage-addins-in-the-admin-center.md)
  
> [!NOTE]
>  W przypadku programu Word Excel i PowerPoint używają [wykazu aplikacji SharePoint](/office/dev/add-ins/publish/publish-task-pane-and-content-add-ins-to-an-add-in-catalog) do wdrażania dodatków dla użytkowników w środowisku lokalnym bez połączenia z Microsoft 365 i/lub obsługi dodatków SharePoint. W przypadku Outlook użyj panelu sterowania Exchange do wdrożenia w środowisku lokalnym bez połączenia z Microsoft 365.
  
## <a name="recommended-approach-for-deploying-office-add-ins"></a>Zalecane podejście do wdrażania dodatków Office

Aby wdrożyć dodatki przy użyciu podejścia etapowego, zalecamy następujące czynności:
  
1. Wprowadź dodatek dla niewielkiego zestawu osób biorących udział w projekcie biznesowym i członków działu IT. Jeśli wdrożenie zakończy się pomyślnie, przejdź do kroku 2.
    
2. Wprowadź dodatek dla większej liczby osób w firmie. Ponownie oceń wyniki i, jeśli się powiedzie, kontynuuj pełne wdrożenie.
    
3. Wykonaj pełne wdrożenie dla wszystkich użytkowników.
    
W zależności od rozmiaru docelowej grupy odbiorców możesz dodać lub usunąć kroki wdrażania.
  
## <a name="deploy-an-office-add-in-using-the-admin-center"></a>Wdrażanie dodatku Office przy użyciu centrum administracyjnego

Przed rozpoczęciem zobacz [Określanie, czy scentralizowane wdrażanie dodatków działa dla Twojej organizacji](centralized-deployment-of-add-ins.md).
  
1. W centrum administracyjnym przejdź do strony **dodatków Ustawienia**\>. Jeśli strona **dodatku** nie jest widoczna, przejdź do strony **dodatki Ustawienia** \> **Aplikacje zintegrowane**\>.

2. Wybierz pozycję **Wdróż dodatek w** górnej części strony, a następnie wybierz pozycję **Dalej**.

    > [!NOTE]
    > Dodatki można również wdrażać w centrum administracyjnym za pośrednictwem [aplikacji zintegrowanych](test-and-deploy-microsoft-365-apps.md). Zintegrowane aplikacje są widoczne dla administratorów globalnych i Exchange. Jeśli nie widzisz powyższych kroków, przejdź do sekcji Scentralizowane wdrożenie, przechodząc do **pozycji Ustawienia** >  **Integrated apps (Aplikacje zesregowane**). W górnej części strony **Zintegrowane aplikacje** wybierz pozycję **Dodatki**.

3. Wybierz opcję i postępuj zgodnie z instrukcjami.
  
4. Jeśli wybrano opcję dodania dodatku ze sklepu Office Store, zaznacz dodatek. </br>

    Dostępne dodatki można wyświetlić według kategorii: **Sugerowane dla Ciebie**, **Ocena** lub **Nazwa**. W sklepie Office dostępne są tylko bezpłatne dodatki. Dodatki płatne nie są obecnie obsługiwane. Po wybraniu dodatku zaakceptuj warunki i postanowienia, aby kontynuować. <br/> 

    > [!NOTE]
    > Dzięki opcji sklepu Office aktualizacje i ulepszenia są automatycznie wdrażane dla użytkowników.

5. Na następnej stronie wybierz pozycję **Wszyscy**, **Określoni użytkownicy/grupy** lub **Po prostu ja** , aby określić, do kogo jest wdrażany dodatek. Użyj pola Wyszukiwania, aby znaleźć określonych użytkowników lub grupy. <br/>

    > [!NOTE]
    > Aby dowiedzieć się więcej o innych stanach, które mają zastosowanie do dodatku, zobacz [Stany dodatków](./manage-addins-in-the-admin-center.md).
  
6. Wybierz pozycję **Wdróż**.
  
7. Po wdrożeniu dodatku zostanie wyświetlony zielony znacznik. Postępuj zgodnie z instrukcjami na stronie, aby przetestować dodatek.

    > [!NOTE]
    > Użytkownicy mogą wymagać ponownego uruchomienia Office, aby wyświetlić ikonę dodatku na wstążce aplikacji. Outlook dodatek może potrwać do 24 godzin na wstążkach aplikacji.

8. Po zakończeniu wybierz pozycję **Dalej**. Jeśli wdrożono tylko dla siebie, możesz wybrać pozycję **Zmień, kto ma dostęp do dodatku,** aby wdrożyć go dla większej liczby użytkowników.

    Jeśli dodatek został wdrożony dla innych członków organizacji, postępuj zgodnie z instrukcjami, aby ogłosić wdrożenie dodatku. <br/>
  
    Dobrym rozwiązaniem jest informowanie użytkowników i grup, że wdrożony dodatek jest dostępny. Rozważ wysłanie wiadomości e-mail opisującej, kiedy i jak używać dodatku. Dołącz zawartość lub link do pomocy lub często zadawane pytania, które mogą pomóc użytkownikom w przypadku problemów z dodatkiem.
  
### <a name="considerations-when-assigning-an-add-in-to-users-and-groups"></a>Zagadnienia dotyczące przypisywania dodatku do użytkowników i grup

Administratorzy globalni i administratorzy Exchange mogą przypisywać dodatek wszystkim lub określonym użytkownikom i grupom. Z każdą z tych opcji wiążą się pewne konsekwencje:
  
- **Wszyscy** Ta opcja powoduje przypisanie dodatku do każdego użytkownika w organizacji. Użyj tej opcji oszczędnie i tylko w przypadku dodatków, które są naprawdę uniwersalne dla Twojej organizacji.

- **Użytkowników** Jeśli przypiszesz dodatek do pojedynczego użytkownika, a następnie wdrożysz dodatek do nowego użytkownika, musisz najpierw dodać nowego użytkownika.

- **Grupy** Jeśli przypiszesz do grupy dodatek, dodatek zostanie automatycznie przypisany do użytkowników dodanych do grupy. Gdy użytkownik zostanie usunięty z grupy, użytkownik utraci dostęp do dodatku. W obu przypadkach administrator nie wymaga żadnej dodatkowej akcji.

- **Tylko ja** Jeśli przypiszesz dodatek tylko do siebie, dodatek zostanie przypisany tylko do Twojego konta, co jest idealne do testowania dodatku.

Właściwa opcja dla organizacji zależy od konfiguracji. Zalecamy jednak wykonywanie przypisań przy użyciu grup. Jako administrator możesz łatwiej zarządzać dodatkami przy użyciu grup i kontrolować członkostwo w tych grupach, zamiast przypisywać poszczególnych użytkowników za każdym razem. W niektórych sytuacjach możesz chcieć ograniczyć dostęp do niewielkiego zestawu użytkowników, wykonując przypisania do określonych użytkowników, przypisując użytkowników ręcznie.
  
## <a name="more-about-office-add-ins-security"></a>Więcej informacji o zabezpieczeniach dodatków Office

Office dodatki łączą plik manifestu XML, który zawiera pewne metadane dotyczące dodatku, ale co najważniejsze wskazuje na aplikację internetową, która zawiera cały kod i logikę. Dodatki mogą mieć różnorodne możliwości. Na przykład dodatki mogą:
  
- wyświetlać dane,

- odczytywać dokument użytkownika w celu dostarczenia usług kontekstowych,

- odczytywać i zapisywać dane w dokumencie użytkownika w celu podania wartości dla tego użytkownika.

Aby uzyskać więcej informacji na temat typów i możliwości dodatków Office, zobacz [omówienie platformy dodatków Office](/office/dev/add-ins/overview/office-add-ins), zwłaszcza sekcję "Anatomia dodatku Office".
  
Aby współdziałać z dokumentem użytkownika, dodatek musi zadeklarować, jakich uprawnień potrzebuje, w pliku manifestu. Pięciopoziomowy model uprawnień dostępu interfejsu API języka JavaScript stanowi podstawę dla prywatności i zabezpieczeń dla użytkowników dodatków okienek zadań. Większość dodatków w witrynie Sklep Office obsługuje poziom odczytu i zapisu dokumentu, a niemal wszystkie dodatki obsługują co najmniej poziom odczytu dokumentu. Aby uzyskać więcej informacji o poziomach uprawnień, zobacz [Żądanie poświadczeń na potrzeby używania interfejsu API w dodatkach zawartości i okienek zadań](/office/dev/add-ins/develop/requesting-permissions-for-api-use-in-content-and-task-pane-add-ins).
  
Podczas aktualizowania pliku manifestu typowe zmiany dotyczą ikony i tekstu dodatku. Od czasu do czasu zmieniają się polecenia dodatku. Jednak uprawnienia dodatku nie są zmieniane. Aplikacja internetowa, gdzie jest uruchamiany cały kod i logika dla dodatku, może zmienić się w dowolnym momencie, co jest normalne w przypadku aplikacji internetowych.
  
Aktualizacje dodatków są przeprowadzane w następujący sposób:
  
- **Dodatek biznesowy:** W takim przypadku, kiedy administrator jawnie przekazał manifest, dodatek wymaga, aby administrator przekazał nowy plik manifestu w celu obsługi zmian metadanych. Przy kolejnym uruchomieniu odpowiednich aplikacji pakietu Office dodatek zostanie zaktualizowany. Aplikacja internetowa może się zmienić w dowolnym momencie.

    > [!NOTE]
    > Administrator nie musi usuwać dodatku lob do przeprowadzania aktualizacji.   W sekcji Dodatki administrator może po prostu kliknąć dodatek LOB i wybrać **przycisk Aktualizacji** w prawym dolnym rogu. Aktualizacja będzie działać tylko wtedy, gdy wersja nowego dodatku jest większa niż wersja istniejącego dodatku.

- **Dodatek ze Sklepu Office:** Jeśli administrator wybrał dodatek w witrynie Sklep Office, to w przypadku aktualizacji tego dodatku w witrynie Sklep Office zostanie on następnie zaktualizowany w funkcji Scentralizowane wdrażanie. Przy kolejnym uruchomieniu odpowiednich aplikacji pakietu Office dodatek zostanie zaktualizowany. Aplikacja internetowa może się zmienić w dowolnym momencie.
  
## <a name="related-content"></a>Zawartość pokrewna

[Zarządzanie dodatkami w centrum administracyjnym](manage-addins-in-the-admin-center.md) (artykuł)\
[Skompiluj swój pierwszy dodatek do okienka zadań programu Word](/office/dev/add-ins/quickstarts/word-quickstart?tabs=yeomangenerator) (artykuł\
[Osoby niepełnoletnie i uzyskiwanie dodatków ze sklepu](minors-and-acquiring-addins-from-the-store.md) (artykuł)\
[Używanie poleceń cmdlet programu PowerShell scentralizowanego wdrażania do zarządzania dodatkami](../../enterprise/use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md) (artykuł)\
[Rozwiązywanie problemów: Użytkownik nie widzi dodatków](/office365/troubleshoot/access-management/user-not-seeing-add-ins) (artykuł)
