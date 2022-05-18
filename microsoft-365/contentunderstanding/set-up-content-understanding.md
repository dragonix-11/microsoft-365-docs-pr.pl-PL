---
title: Konfigurowanie usługi SharePoint Syntex
ms.author: mikeplum
author: MikePlumleyMSFT
ms.reviewer: ssquires
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom:
- admindeeplinkMAC
search.appverid: MET150
ms.localizationpriority: high
description: Konfigurowanie usługi SharePoint Syntex
ms.openlocfilehash: 97d12527667de1583f787844da11a4ad875f34ba
ms.sourcegitcommit: 37111bc0c5a6cc4690f7144a019bbff11d44858f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2022
ms.locfileid: "65463148"
---
# <a name="set-up-sharepoint-syntex"></a>Konfigurowanie usługi SharePoint Syntex

Administratorzy mogą użyć <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a>, aby skonfigurować usługę [Microsoft SharePoint Syntex](index.md). 

Przed rozpoczęciem należy wziąć pod uwagę następujące kwestie:

- W których SharePoint lokacjach można włączyć przetwarzanie formularzy? Wszystkie z nich, niektóre lub wybrane witryny?
- Jak określisz nazwę domyślnego centrum zawartości?

Ustawienia można zmienić po początkowej konfiguracji w <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a>.

Przed rozpoczęciem instalacji upewnij się, że zaplanowano najlepszy sposób konfigurowania i konfigurowania zrozumienia zawartości w środowisku. Na przykład należy podjąć następujące decyzje:

- Witryny SharePoint, w których chcesz włączyć przetwarzanie formularzy — wszystkie z nich, niektóre lub wybrane witryny
- Nazwa i administratorzy centrum zawartości

## <a name="requirements"></a>Wymagania 

> [!NOTE]
> Aby uzyskać dostęp do Centrum administracyjne platformy Microsoft 365 i skonfigurować SharePoint Syntex, musisz mieć uprawnienia administratora globalnego lub administratora SharePoint.

Jako administrator możesz również wprowadzać zmiany w wybranych ustawieniach w dowolnym momencie po skonfigurowaniu i w całym obszarze zarządzania zawartością w <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a>.

### <a name="custom-power-platform-environments"></a>Niestandardowe środowiska platformy Power Platform

Jeśli planujesz używać niestandardowego środowiska platformy Power Platform, musisz zainstalować aplikację *AI Builder for Projekt Cortex* w tym środowisku. Zobacz [Zarządzanie aplikacjami usługi Dynamics 365](/power-platform/admin/manage-apps#install-an-app-in-the-environment-view), aby uzyskać szczegółowe informacje i wyszukaj aplikację *AI Builder for Projekt Cortex* na liście aplikacji usługi Dynamics 365.

Przed utworzeniem modeli przetwarzania [formularzy należy również przydzielić środki narzędzia AI Builder](/power-platform/admin/capacity-add-on) do środowiska niestandardowego. 

W przypadku korzystania ze środowiska niestandardowego twórcy modelu muszą mieć przypisaną rolę zabezpieczeń usługi Environment Maker, a użytkownikom modelu musi być przypisana rola Zabezpieczeń użytkownika podstawowego. Aby uzyskać więcej informacji [, zobacz Przypisywanie roli zabezpieczeń do użytkownika](/power-platform/admin/assign-security-roles) .

Użytkownicy tworzący modele w [witrynie centrum zawartości](/microsoft-365/contentunderstanding/create-a-content-center) muszą być członkami witryny. Użytkownicy tworzący modele lokalnie poza centrum zawartości muszą być właścicielami witryn.

### <a name="licensing"></a>Licencjonowanie

Aby korzystać z SharePoint Syntex, organizacja musi mieć subskrypcję do SharePoint Syntex, a każdy użytkownik musi mieć przypisane następujące licencje:

- SharePoint Syntex
- SharePoint Syntex — typ SPO
- Usługa Common Data Service dla SharePoint Syntex

Do korzystania z przetwarzania formularzy potrzebne są również środki na korzystanie z narzędzia AI Builder. Jeśli masz co najmniej 300 licencjonowanych użytkowników, co miesiąc przydzielane są środki narzędzia AI Builder.

Aby uzyskać szczegółowe informacje na temat licencjonowania SharePoint Syntex, zobacz [licencjonowanie SharePoint Syntex](syntex-licensing.md)

## <a name="to-set-up-sharepoint-syntex"></a>Aby skonfigurować SharePoint Syntex

1. W Centrum administracyjne platformy Microsoft 365 wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**Konfiguracja**</a>, a następnie wyświetl sekcję **Pliki i zawartość**.

2. W sekcji **Pliki i zawartość** wybierz pozycję **Automatyzuj zrozumienie zawartości**. Pamiętaj, że bieżąca dostępność środków narzędzia AI Builder jest **wyświetlana w sekcji Na pierwszy rzut oka** .<br/>

3. Na stronie **Automatyzowanie zrozumienia zawartości** kliknij **pozycję Wprowadzenie**, aby przejść przez proces konfiguracji. <br/>

    > [!div class="mx-imgBorder"]
    > ![Rozpocznij instalację.](../media/content-understanding/admin-content-understanding-get-started.png)</br>

4. Na stronie **Konfigurowanie przetwarzania formularzy** możesz wybrać, czy chcesz zezwolić użytkownikom na tworzenie modeli przetwarzania formularzy w określonych bibliotekach dokumentów SharePoint. Opcja menu będzie dostępna na wstążce biblioteki dokumentów, aby **utworzyć model przetwarzania formularzy** w SharePoint bibliotekach dokumentów, w których jest włączona.
 
     W obszarze **Które biblioteki SharePoint powinny wyświetlać opcję utworzenia modelu przetwarzania formularzy**, możesz wybrać następujące opcje:</br>
      - **Biblioteki we wszystkich SharePoint lokacjach**, aby udostępnić je wszystkim bibliotekom SharePoint w organizacji.</br>
      - **Biblioteki w wybranych witrynach SharePoint**, a następnie wybierz witryny, w których chcesz je udostępnić, lub przekaż listę maksymalnie 50 witryn.</br>
      - **Brak bibliotek SharePoint**, jeśli nie chcesz udostępniać ich w żadnych witrynach (możesz to zmienić po skonfigurowaniu).

   > [!div class="mx-imgBorder"]
   > ![Skonfiguruj opcje lokacji przetwarzania formularzy.](../media/content-understanding/admin-configforms.png)

   > [!Note]
   > Usunięcie lokacji po jej uwzględnieniu nie ma wpływu na istniejące modele stosowane do bibliotek w tej lokacji ani na możliwość stosowania modeli interpretacji dokumentów do biblioteki. 
    
    Jeśli masz skonfigurowane wiele środowisk platformy Power Platform, możesz wybrać, z którym środowiskiem chcesz używać do przetwarzania formularzy. (Ta opcja nie będzie wyświetlana, jeśli masz tylko jedno środowisko).

    ![Skonfiguruj opcje platformy Power Platform do przetwarzania formularzy.](../media/content-understanding/setup-power-platform-env.png)

    W **przypadku środowiska power platform** można wybrać następujące opcje:
    - **Użyj domyślnego środowiska** , aby użyć domyślnego środowiska platformy Power Platform.
    - **Używanie środowiska niestandardowego** do korzystania ze środowiska niestandardowego. Z listy wybierz środowisko, którego chcesz użyć. ([Zobacz wymagania dotyczące środowiska niestandardowego](/microsoft-365/contentunderstanding/set-up-content-understanding#requirements)).

    Kliknij **Dalej**.

5. Na stronie **Tworzenie centrum zawartości** możesz utworzyć witrynę centrum zawartości SharePoint, w której użytkownicy mogą tworzyć modele zrozumienia dokumentów i zarządzać nimi. Jeśli wcześniej utworzono centrum zawartości z centrum administracyjnego SharePoint, te informacje zostaną wyświetlone tutaj i możesz po prostu wybrać pozycję **Dalej**.

    1. W polu **Nazwa witryny** wpisz nazwę, którą chcesz nadać witrynie centrum zawartości.
    
    1. **Adres witryny** będzie wyświetlać adres URL witryny na podstawie wybranej nazwy witryny. Jeśli chcesz go zmienić, kliknij przycisk **Edytuj**.

       > [!div class="mx-imgBorder"]
       > ![Utwórz centrum zawartości.](../media/content-understanding/admin-cu-create-cc.png)</br>

       Wybierz pozycję **Dalej**.

6. Na stronie **Przeglądanie i zakończenie** możesz przyjrzeć się wybranemu ustawieniu i wybrać opcję wprowadzania zmian. Jeśli wybrane opcje są zadowalające, wybierz pozycję **Aktywuj**.

7. Na stronie potwierdzenia kliknij pozycję **Gotowe**.

8. Nastąpi powrót do strony **automatyzowania zrozumienia zawartości** . Na tej stronie możesz wybrać pozycję **Zarządzaj** , aby wprowadzić wszelkie zmiany w ustawieniach konfiguracji. 

## <a name="assign-licenses"></a>Przypisywanie licencji

Po skonfigurowaniu SharePoint Syntex należy przypisać licencje dla użytkowników, którzy będą korzystać z dowolnych funkcji SharePoint Syntex.

Aby przypisać licencje:

1. W Centrum administracyjne platformy Microsoft 365 w obszarze **Użytkownicy** wybierz pozycję <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Aktywni użytkownicy**</a>.

2. Wybierz użytkowników, na których chcesz uzyskać licencję, a następnie wybierz pozycję **Zarządzaj licencjami produktów**.

3. Z menu rozwijanego wybierz pozycję **Aplikacje** .

4. Wybierz pozycję **Pokaż aplikacje dla SharePoint Syntex**. W obszarze Aplikacje upewnij się, że **wybrano** opcję **Common Data Service for SharePoint Syntex**, **SharePoint Syntex** i **SharePoint Syntex — typ SPO**.

    > [!div class="mx-imgBorder"]
    > ![SharePoint Syntex licencji w Centrum administracyjne platformy Microsoft 365.](../media/content-understanding/sharepoint-syntex-licenses.png)

5. Kliknij przycisk **Zapisz zmiany**.

## <a name="see-also"></a>Zobacz też

[Omówienie modelu przetwarzania formularzy](/ai-builder/form-processing-model-overview)

[Krok po kroku: jak utworzyć model zrozumienia dokumentów (wideo)](https://www.youtube.com/watch?v=DymSHObD-bg)

[Tworzenie środowisk i zarządzanie nimi w centrum administracyjnym platformy Power Platform](/power-platform/admin/create-environment)
