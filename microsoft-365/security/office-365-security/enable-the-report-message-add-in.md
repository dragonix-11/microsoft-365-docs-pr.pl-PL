---
title: Włączanie komunikatu raportu lub dodatków wyłudzania informacji o raportach
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 4250c4bc-6102-420b-9e0a-a95064837676
ms.collection:
- M365-security-compliance
description: Dowiedz się, jak włączyć dodatki Report Message lub Report Phishing dla Outlook i Outlook w sieci Web, dla poszczególnych użytkowników lub dla całej organizacji.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 14d59cbe6f3f98aabc231da88e4f0919a3974c97
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64973228"
---
# <a name="enable-the-report-message-or-the-report-phishing-add-ins"></a>Włączanie komunikatu raportu lub dodatków wyłudzania informacji o raportach

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Jeśli jesteś administratorem w organizacji Microsoft 365 z Exchange Online skrzynkami pocztowymi, zalecamy użycie strony **Przesłane** w portalu Microsoft 365 Defender. Aby uzyskać więcej informacji, zobacz [Przesyłanie przez administratora w celu przesyłania do firmy Microsoft podejrzanych wiadomości spamowych, phish, adresów URL i plików](admin-submission.md).

Dodatek Report Message and Report Phishing dla Outlook i Outlook w sieci Web (dawniej znany jako Outlook Web App) ułatwia zgłaszanie fałszywych alarmów (dobry adres e-mail oznaczony jako zły) lub fałszywych negatywów (niedozwolona wiadomość e-mail) firmie Microsoft i jej podmiotom stowarzyszonym w celu analizy.

Firma Microsoft korzysta z tych przesłanych danych, aby zwiększyć skuteczność technologii ochrony poczty e-mail. Załóżmy na przykład, że użytkownicy zgłaszają wiele komunikatów przy użyciu dodatku Wyłudzanie informacji o raportach. Te informacje są widoczne na pulpicie nawigacyjnym zabezpieczeń i w innych raportach. Zespół ds. zabezpieczeń organizacji może użyć tych informacji jako wskazania, że konieczne może być zaktualizowanie zasad ochrony przed wyłudzaniem informacji.

Możesz zainstalować dodatek Report Message (Komunikat raportu) lub Report Phishing (Wyłudzanie informacji o raportach). Jeśli chcesz, aby użytkownicy zgłaszali spam i wiadomości wyłudzające informacje, wdróż dodatek Komunikat raportu w organizacji.

Dodatek Komunikat raportu udostępnia opcję zgłaszania wiadomości spamu i wyłudzania informacji. Administratorzy mogą włączyć dodatek Komunikat raportu dla organizacji, a poszczególni użytkownicy mogą zainstalować go samodzielnie.

Dodatek Raport wyłudzający informacje zapewnia możliwość zgłaszania tylko wiadomości wyłudzających informacje. Administratorzy mogą włączyć dodatek Wyłudzanie informacji o raportach dla organizacji, a poszczególni użytkownicy mogą zainstalować go samodzielnie.

Jeśli jesteś użytkownikiem indywidualnym, możesz włączyć oba dodatki dla siebie.

Jeśli jesteś administratorem globalnym lub administratorem Exchange Online, a Exchange jest skonfigurowany do korzystania z uwierzytelniania OAuth, możesz włączyć dodatek Komunikat raportu i dodatek Wyłudzanie informacji o raportach dla organizacji. Oba dodatki są teraz dostępne za pośrednictwem [scentralizowanego wdrożenia](../../admin/manage/centralized-deployment-of-add-ins.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Zarówno dodatek Komunikat raportu, jak i dodatek Report Phishing współpracują z większością subskrypcji Microsoft 365 i następującymi produktami:
  - Outlook on the web
  - Outlook 2013 z dodatkiem SP1 lub nowszym
  - Outlook 2016 dla komputerów Mac
  - Outlook dołączone do aplikacji Microsoft 365 dla Enterprise
  - aplikacja Outlook dla systemów iOS i Android

- Oba dodatki nie są dostępne dla udostępnionych skrzynek pocztowych.

- Oba dodatki nie są dostępne dla lokalnych Exchange skrzynek pocztowych. 

- Istniejąca przeglądarka internetowa powinna współdziałać zarówno z dodatkami Komunikat raportu, jak i Wyłudzanie informacji o raportach. Jeśli jednak zauważysz, że dodatek jest niedostępny lub nie działa zgodnie z oczekiwaniami, spróbuj użyć innej przeglądarki.

- W przypadku instalacji organizacyjnych należy skonfigurować organizację do korzystania z uwierzytelniania OAuth. Aby uzyskać więcej informacji, zobacz [Określanie, czy scentralizowane wdrażanie dodatków działa w twojej organizacji](../../admin/manage/centralized-deployment-of-add-ins.md).

- Administratorzy muszą być członkami grupy ról Administratorzy globalni. Aby uzyskać więcej informacji, zobacz [Uprawnienia w portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

- Aby uzyskać więcej informacji na temat raportowania komunikatu przy użyciu funkcji komunikatu raportu, zobacz [Report false positives and false negatives in Outlook (Zgłaszanie wyników fałszywie dodatnich i fałszywie ujemnych w Outlook](report-false-positives-and-false-negatives.md)).

- Organizacje, które mają rozwiązanie do filtrowania adresów URL lub zabezpieczeń (na przykład serwer proxy i/lub zaporę), muszą mieć ipagave.azurewebsites.net i outlook.office.com punkty końcowe mogą być osiągane za pośrednictwem protokołu HTTPS.

## <a name="get-the-report-message-add-in"></a>Pobieranie dodatku Komunikat raportu

### <a name="get-the-report-message-add-in-for-yourself"></a>Samodzielne pobieranie dodatku Komunikat raportu

1. Przejdź do witryny Microsoft AppSource pod adresem <https://appsource.microsoft.com/marketplace/apps> i wyszukaj dodatek Komunikat raportu. Aby przejść bezpośrednio do dodatku Komunikat raportu, przejdź do pozycji <https://appsource.microsoft.com/product/office/wa104381180>.

2. Kliknij **pozycję POBIERZ TERAZ**.

   :::image type="content" source="../../media/ReportMessageGETITNOW.png" alt-text="Komunikat raportu Pobierz teraz" lightbox="../../media/ReportMessageGETITNOW.png":::

3. W wyświetlonym oknie dialogowym przejrzyj warunki użytkowania i zasady ochrony prywatności, a następnie kliknij przycisk **Kontynuuj**.

4. Zaloguj się przy użyciu konta służbowego (do użytku służbowego) lub konta Microsoft (do użytku osobistego).

Po zainstalowaniu i włączeniu dodatku zostaną wyświetlone następujące ikony:

- W Outlook ikona wygląda następująco:

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/OutlookReportMessageIcon.png" alt-text="Ikona dodatku Komunikat raportu dla Outlook" lightbox="../../media/OutlookReportMessageIcon.png":::

- W Outlook w sieci Web ikona wygląda następująco:

    > [!div class="mx-imgBorder"]
    > ![Outlook w sieci Web ikona dodatku Komunikat raportu.](../../media/owa-report-message-icon.png)

### <a name="get-the-report-message-add-in-for-your-organization"></a>Pobieranie dodatku Komunikat raportu dla organizacji

> [!NOTE]
> Wyświetlenie dodatku w organizacji może potrwać do 12 godzin.

1. W [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com/AdminPortal/Home?#/homepage) przejdź do **obszaru** \> Ustawienia **Aplikacje zintegrowane**. Kliknij **pozycję Pobierz aplikacje**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-integrated-apps.png" alt-text="Aplikacje zintegrowane Centrum administracyjne platformy Microsoft 365" lightbox="../../media/microsoft-365-admin-center-integrated-apps.png":::

2. Na wyświetlonej stronie **Aplikacje Microsoft 365** kliknij w polu **Wyszukaj**, wprowadź **komunikat raportu**, a następnie kliknij ikonę **Wyszukaj**![.](../../media/search-icon.png) Na liście wyników znajdź i wybierz pozycję **Komunikat raportu**. 

3. Zostanie otwarta strona szczegółów aplikacji. Wybierz pozycję **Pobierz teraz**. 

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-report-message.png" alt-text="Dodatek Komunikat raportu" lightbox="../../media/microsoft-365-admin-center-report-message.png":::

4. Wypełnij podstawowe informacje o profilu, a następnie kliknij przycisk **Kontynuuj**. 

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-profile-info.png" alt-text="Konfiguracja profilu dodatku Komunikat raportu" lightbox="../../media/microsoft-365-admin-center-profile-info.png":::

5. Zostanie otwarte okno wysuwane **Wdrażanie nowej aplikacji** . Skonfiguruj następujące ustawienia. Kliknij **przycisk Dalej** , aby przejść do następnej strony, aby ukończyć konfigurację. 

   - **Dodaj użytkowników**: wybierz jedną z następujących wartości:
     - **Tylko ja**
     - **Cała organizacja**
     - **Określoni użytkownicy/grupy**

   - **Wdrożenie**:
     - **Akceptowanie żądań uprawnień**: przed przejściem do następnej strony uważnie przeczytaj uprawnienia i możliwości aplikacji.

        > [!div class="mx-imgBorder"]
        > :::image type="content" source="../../media/microsoft-365-admin-center-deploy-new-app.png" alt-text="Strona Akceptowanie żądań uprawnień" lightbox="../../media/microsoft-365-admin-center-deploy-new-app.png":::

     - **Zakończ wdrażanie**: przejrzyj i zakończ wdrażanie dodatku. 
     - **Wdrożenie zostało ukończone**: wybierz pozycję **Gotowe** , aby ukończyć konfigurację. 

        > [!div class="mx-imgBorder"]
        > :::image type="content" source="../../media/microsoft-365-admin-center-deployment-complete.png" alt-text="Komunikat powiadomienia o zakończeniu wdrożenia" lightbox="../../media/microsoft-365-admin-center-deployment-complete.png":::

## <a name="edit-settings-for-the-report-message-add-in"></a>Edytowanie ustawień dodatku Komunikat raportu

1. W Centrum administracyjne platformy Microsoft 365 przejdź do **obszaru Ustawienia** \> **Aplikacje zintegrowane** \. Następnie znajdź i wybierz dodatek **Komunikat raportu** .

2. W wyświetlonym wysuwie wybierz pozycję **Edytuj użytkowników** , aby edytować ustawienia użytkownika.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-report-message-edit.png" alt-text="Wysuwany komunikat raportu" lightbox="../../media/microsoft-365-admin-center-report-message-edit.png":::

3. Aby usunąć dodatek, wybierz pozycję **Usuń aplikację** w obszarze **Akcje** w tym samym wysuwnym okienku. 

## <a name="get-the-report-phishing-add-in"></a>Uzyskiwanie dodatku Wyłudzanie informacji o raportach

### <a name="get-the-report-phishing-add-in-for-yourself"></a>Samodzielne pobieranie dodatku Report Phishing

1. Przejdź do witryny Microsoft AppSource pod adresem <https://appsource.microsoft.com/marketplace/apps> i wyszukaj dodatek Wyłudzanie informacji o raportach.

2. Kliknij **pozycję POBIERZ TERAZ**.

3. W wyświetlonym oknie dialogowym przejrzyj warunki użytkowania i zasady ochrony prywatności, a następnie kliknij przycisk **Kontynuuj**.

4. Zaloguj się przy użyciu konta służbowego (do użytku służbowego) lub konta Microsoft (do użytku osobistego).

Po zainstalowaniu i włączeniu dodatku zostaną wyświetlone następujące ikony:

- W Outlook ikona wygląda następująco:

  ![Ikona dodatku Zgłaszanie wyłudzania informacji dla Outlook.](../../media/Outlook-ReportPhishing.png)

- W Outlook w sieci Web ikona wygląda następująco:

    > [!div class="mx-imgBorder"]
    > ![Outlook w sieci Web ikona dodatku Zgłaszanie wyłudzania informacji.](../../media/OWA-ReportPhishing.png)

### <a name="get-the-report-phishing-add-in-for-your-organization"></a>Uzyskiwanie dodatku Report Phishing dla organizacji

> [!NOTE]
> Wyświetlenie dodatku w organizacji może potrwać do 12 godzin.

1. W [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com/AdminPortal/Home?#/homepage) przejdź do **obszaru** \> Ustawienia **Aplikacje zintegrowane**. Kliknij **pozycję Pobierz aplikacje**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-integrated-apps.png" alt-text="Aplikacje zintegrowane Centrum administracyjne platformy Microsoft 365" lightbox="../../media/microsoft-365-admin-center-integrated-apps.png":::

2. Na wyświetlonej stronie **Aplikacje Microsoft 365** kliknij pole **Wyszukaj**, wprowadź **wyłudzanie informacji o raporcie**, a następnie kliknij ikonę **Wyszukaj**![.](../../media/search-icon.png) Na liście wyników znajdź i wybierz pozycję **Zgłoś wyłudzanie informacji**. 
 
3. Zostanie otwarta strona szczegółów aplikacji. Wybierz pozycję **Pobierz teraz**.

4. Wypełnij podstawowe informacje o profilu, a następnie kliknij przycisk **Kontynuuj**.

5. Zostanie otwarte okno wysuwane **Wdrażanie nowej aplikacji** . Wykonaj kroki [opisane powyżej](enable-the-report-message-add-in.md#get-the-report-message-add-in-for-your-organization) , aby ukończyć konfigurację. 

## <a name="edit-settings-for-the-report-phishing-add-in"></a>Edytowanie ustawień dodatku Wyłudzanie informacji o raportach

1. W Centrum administracyjne platformy Microsoft 365 przejdź do **obszaru Ustawienia** \> **Aplikacje zintegrowane** \. Następnie znajdź i wybierz dodatek **Raport wyłudzający informacje** .

2. W wyświetlonym wysuwie wybierz pozycję **Edytuj użytkowników** , aby edytować ustawienia użytkownika.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-report-phishing-edit.png" alt-text="Wysuwane wyłudzanie informacji o raporcie" lightbox="../../media/microsoft-365-admin-center-report-phishing-edit.png":::

3. Aby usunąć dodatek, wybierz pozycję **Usuń aplikację** w obszarze **Akcje** w tym samym wysuwnym okienku. 
