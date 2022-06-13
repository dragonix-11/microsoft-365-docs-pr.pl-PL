---
title: Użyj usługi Azure Privileged Identity Management (PIM) w Ochrona usługi Office 365 w usłudze Microsoft Defender, aby ograniczyć dostęp administratora do narzędzi do zabezpieczeń cybernetycznych.
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 09/03/2021
audience: ITPro
ms.topic: article
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 56fee1c7-dc37-470e-9b09-33fff6d94617
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się, jak zintegrować usługę Azure PIM, aby przyznać użytkownikom ograniczony czasowo dostęp do zadań z podwyższonym poziomem uprawnień w Ochrona usługi Office 365 w usłudze Microsoft Defender, co zmniejsza ryzyko związane z danymi.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 32bc21130d98687f95af2ce6664c0759a716f362
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66010239"
---
<!--A-->
# <a name="privileged-identity-management-pim-and-why-to-use-it-with-microsoft-defender-for-office-365"></a>Privileged Identity Management (PIM) i dlaczego należy go używać z Ochrona usługi Office 365 w usłudze Microsoft Defender

Privileged Identity Management (PIM) jest funkcją platformy Azure, która po skonfigurowaniu zapewnia użytkownikom dostęp do danych przez ograniczony okres czasu (czasami nazywany okresem), dzięki czemu można wykonać określone zadanie. Ten dostęp jest przyznawany "just in time" w celu wykonania wymaganej akcji, a następnie odwołania. Usługa PIM ogranicza dostęp i czas, jaki użytkownik ma do danych poufnych, zmniejszając ryzyko narażenia w porównaniu z uprzywilejowanymi kontami administracyjnymi, które mają długoterminowy dostęp do danych i innych ustawień. Jak więc można używać tej funkcji (PIM) w połączeniu z Ochrona usługi Office 365 w usłudze Microsoft Defender?

> [!TIP]
> Dostęp do usługi PIM jest ograniczony do poziomu roli i tożsamości i umożliwia wykonywanie wielu zadań. Nie należy go mylić z usługą Privileged Access Management (PAM), która ma zakres na poziomie zadania.

## <a name="steps-to-use-pim-to-grant-just-in-time-access-to-defender-for-office-365-related-tasks"></a>Procedura udzielania dostępu just in time do Ochrona usługi Office 365 w usłudze Defender powiązanych zadań przy użyciu usługi PIM

Konfigurując usługę PIM do pracy z Ochrona usługi Office 365 w usłudze Defender, administratorzy tworzą proces żądania dostępu użytkownika w celu podjęcia potrzebnych akcji. Użytkownik musi *uzasadnić* potrzebę podniesienia uprawnień.

W tym przykładzie skonfigurujemy "Alexa", członka naszego zespołu ds. zabezpieczeń, który będzie miał zerowy dostęp w ramach Office 365, ale może podnieść poziom do roli wymaganej do normalnych codziennych operacji, takich jak [wyszukiwanie zagrożeń](threat-hunting-in-threat-explorer.md), a następnie do wyższego poziomu uprawnień, gdy wymagane są rzadsze, ale wrażliwe operacje, takie jak [korygowanie złośliwych dostarczonych wiadomości e-mail](remediate-malicious-email-delivered-office-365.md).

> [!NOTE]
> Spowoduje to wykonanie kroków wymaganych do skonfigurowania usługi PIM dla analityka zabezpieczeń, który wymaga możliwości przeczyszczania wiadomości e-mail przy użyciu Eksploratora zagrożeń w Ochrona usługi Office 365 w usłudze Microsoft Defender, ale tych samych kroków można użyć w przypadku innych ról RBAC w portalu Zabezpieczenia i zgodność. Na przykład ten proces może być używany w przypadku procesu roboczego z informacjami, który wymaga codziennego dostępu zbierania elektronicznych elektronicznych materiałów dowodowych do wykonywania wyszukiwania i wykonywania spraw, ale tylko od czasu do czasu potrzebuje podwyższonego poziomu uprawnień do eksportowania danych z dzierżawy.

***Krok 1***. W konsoli usługi Azure PIM dla subskrypcji dodaj użytkownika (Alex) do roli Czytelnik zabezpieczeń platformy Azure i skonfiguruj ustawienia zabezpieczeń związane z aktywacją.

1. Zaloguj się do [centrum administracyjnego Azure AD](https://aad.portal.azure.com/) i wybierz pozycję **Azure Active Directory** >  **Role i administratorzy**.
2. Wybierz pozycję **Czytelnik zabezpieczeń** na liście ról, a następnie **Ustawienia** >  **Edytuj**
3. Ustaw wartość "**Maksymalny czas trwania aktywacji (godziny)**" na normalny dzień roboczy i wartość "Po aktywacji", aby wymagać **usługi Azure MFA**.
4. Ponieważ jest to normalny poziom uprawnień Alexa dla codziennych operacji, usuniemy **zaznaczenie pola Wymagaj uzasadnienia dla aktualizacji > aktywacji****.**
5. Wybierz pozycję **Dodaj przypisania** > **Brak wybranego elementu członkowskiego** , > wybrać lub wpisać nazwę, aby wyszukać prawidłowy element członkowski.
6. Kliknij przycisk **Wybierz** , aby wybrać element członkowski, który chcesz dodać dla uprawnień usługi PIM, > kliknij przycisk **Dalej** , > nie wprowadzaj żadnych zmian na stronie Dodawanie przypisania (zarówno typ przydziału *Kwalifikujący się* , jak i czas trwania *kwalifikowalny będzie domyślnie kwalifikowany* ) i **Przypisz**.

Nazwa użytkownika (w tym miejscu "Alex") zostanie wyświetlona w obszarze Kwalifikujące się przypisania na następnej stronie, co oznacza, że może on pim do roli z ustawieniami skonfigurowanymi wcześniej.

> [!NOTE]
> Aby uzyskać szybki przegląd Privileged Identity Management zobacz [ten film wideo](https://www.youtube.com/watch?v=VQMAg0sa_lE).

:::image type="content" source="../../media/pim-mdo-role-setting-details-for-security-reader-show-8-hr-duration.png" alt-text="Szczegóły ustawienia roli — strona Czytelnik zabezpieczeń" lightbox="../../media/pim-mdo-role-setting-details-for-security-reader-show-8-hr-duration.png":::

***Krok 2***. Utwórz wymaganą drugą grupę uprawnień (z podwyższonym poziomem uprawnień) dla dodatkowych zadań i przypisz uprawnienia.

Korzystając z [grup dostępu uprzywilejowanego](/azure/active-directory/privileged-identity-management/groups-features) , możemy teraz tworzyć własne grupy niestandardowe i łączyć uprawnienia lub zwiększać stopień szczegółowości, jeśli jest to wymagane w celu spełnienia twoich praktyk i potrzeb organizacji.

### <a name="create-a-role-group-requiring-the-permissions-we-need"></a>Tworzenie grupy ról wymagającej wymaganych uprawnień

W portalu Microsoft 365 Defender utwórz niestandardową grupę ról zawierającą żądane uprawnienia.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do pozycji **Uprawnienia & role**, a następnie wybierz pozycję **Role** w obszarze **Poczta e-mail i współpraca**. Aby przejść bezpośrednio do strony **Uprawnienia** , użyj polecenia <https://security.microsoft.com/emailandcollabpermissions>.
2. Na stronie **Uprawnienia** kliknij ikonę ![Utwórz.](../../media/m365-cc-sc-create-icon.png) **Utwórz**.
3. Nadaj grupie nazwę, aby odzwierciedlić jej przeznaczenie, takie jak "Wyszukiwanie i przeczyszczanie usługi PIM".
4. Nie dodawać członków, wystarczy zapisać grupę i przejść do następnej części!

### <a name="create-the-security-group-in-azure-ad-for-elevated-permissions"></a>Tworzenie grupy zabezpieczeń w Azure AD dla uprawnień z podwyższonym poziomem uprawnień

1. Przejdź z powrotem do [centrum administracyjnego Azure AD](https://aad.portal.azure.com/) i przejdź do **obszaru** >  Azure AD **Grupy** > **nowa grupa**.
2. Nadaj grupie Azure AD nazwę, aby odzwierciedlała jej **przeznaczenie. W tej chwili nie są wymagane żadne właściciele ani członkowie**.
3. Włącz **Azure AD role można przypisać do grupy** na **Wartość Tak**.
4. Nie dodaj żadnych ról, członków ani właścicieli, nie twórz grupy.
5. Wstecz do właśnie utworzonej grupy, a następnie wybierz pozycję **Dostęp uprzywilejowany** > **Włącz dostęp uprzywilejowany**.
6. W grupie wybierz pozycję **Kwalifikujące się przypisania** > **Dodaj przypisania** > Dodaj użytkownika, który potrzebuje funkcji Wyszukiwania & Przeczyszczanie jako roli **Członka**.
7. Skonfiguruj **Ustawienia** w okienku Uprzywilejowany dostęp grupy. Wybierz pozycję **Edytuj** ustawienia roli **Członka**.
8. Zmień czas aktywacji na odpowiedni dla Twojej organizacji. W tym przykładzie przed wybraniem pozycji **Aktualizuj** należy wymagać *usługi Azure MFA*, *uzasadnienia* i *informacji o biletach*.

### <a name="nest-the-newly-created-security-group-into-the-role-group"></a>Zagnieżdżanie nowo utworzonej grupy zabezpieczeń w grupie ról

1. [Połączenie do programu PowerShell security & Compliance](/powershell/exchange/connect-to-scc-powershell) i uruchom następujące polecenie:

   ```powershell
   Add-RoleGroupMember "<<Role Group Name>>" -Member "<<Azure Security Group>>"`
   ```

## <a name="test-your-configuration-of-pim-with-defender-for-office-365"></a>Testowanie konfiguracji usługi PIM przy użyciu Ochrona usługi Office 365 w usłudze Defender

1. Zaloguj się do użytkownika testowego (Alex), który w tym momencie nie powinien mieć dostępu administracyjnego w [portalu Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).
2. Przejdź do usługi PIM, gdzie użytkownik może aktywować swoją codzienną rolę czytelnika zabezpieczeń.
3. Jeśli spróbujesz przeczyścić wiadomość e-mail przy użyciu Eksploratora zagrożeń, zostanie wyświetlony błąd informujący, że potrzebujesz dodatkowych uprawnień.
4. PiM po raz drugi do roli bardziej podwyższone, po krótkim opóźnieniu powinno być teraz możliwe przeczyszczanie wiadomości e-mail bez problemu.

   :::image type="content" source="../../media/pim-mdo-add-the-search-and-purge-role-assignment-to-this-pim-role.PNG" alt-text="Okienko Akcje na karcie Poczta e-mail" lightbox="../../media/pim-mdo-add-the-search-and-purge-role-assignment-to-this-pim-role.PNG":::

Stałe przypisanie ról administracyjnych i uprawnień, takich jak rola wyszukiwania i przeczyszczania, nie jest obsługiwane w ramach inicjatywy zabezpieczeń Zero Trust, ale jak widać, usługa PIM może służyć do udzielania dostępu just in time do wymaganego zestawu narzędzi.

*Dziękujemy inżynierowi klienta Benowi Harrisowi za dostęp do wpisu w blogu i zasobów używanych do tej zawartości.*

<!--A-->
