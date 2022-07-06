---
title: Zdefiniuj reguły przepływu poczty e-mail do szyfrowania wiadomości
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 9b7daf19-d5f2-415b-bc43-a0f5f4a585e8
ms.collection:
- M365-security-compliance
ms.custom:
- admindeeplinkMAC
- admindeeplinkEXCHANGE
description: Administratorzy mogą dowiedzieć się, jak tworzyć reguły przepływu poczty (reguły transportu) do szyfrowania i odszyfrowywania wiadomości przy użyciu Szyfrowanie wiadomości w Microsoft Purview.
ms.openlocfilehash: 75abd302bf661fda50b144f431572c8c6dfc8bcc
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635704"
---
# <a name="define-mail-flow-rules-to-encrypt-email-messages"></a>Zdefiniuj reguły przepływu poczty e-mail do szyfrowania wiadomości

Jako administrator, który zarządza Exchange Online, możesz tworzyć reguły przepływu poczty (nazywane również regułami transportu), aby chronić wysyłane i odbierane wiadomości e-mail. Możesz skonfigurować reguły szyfrowania wszelkich wychodzących wiadomości e-mail i usuwania szyfrowania z zaszyfrowanych wiadomości pochodzących z organizacji lub odpowiedzi na zaszyfrowane wiadomości wysyłane z organizacji. Aby utworzyć te reguły, możesz użyć <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnego programu Exchange (EAC)</a> lub Exchange Online programu PowerShell. Oprócz ogólnych reguł szyfrowania można również włączyć lub wyłączyć opcje szyfrowania poszczególnych komunikatów dla użytkowników końcowych.

Nie można szyfrować poczty przychodzącej od nadawców spoza organizacji.

Jeśli ostatnio przeprowadzono migrację z usługi Active Directory RMS do usługi Azure Information Protection, należy przejrzeć istniejące reguły przepływu poczty, aby upewnić się, że będą one nadal działać w nowym środowisku. Ponadto, aby używać Szyfrowanie wiadomości w Microsoft Purview z usługą Azure Information Protection, musisz zaktualizować istniejące reguły przepływu poczty. W przeciwnym razie użytkownicy będą nadal otrzymywać zaszyfrowaną pocztę, która używa poprzedniego formatu załącznika HTML zamiast nowego, bezproblemowego środowiska. Jeśli szyfrowanie komunikatów nie zostało jeszcze skonfigurowane, zobacz [Konfigurowanie Szyfrowanie wiadomości w Microsoft Purview](set-up-new-message-encryption-capabilities.md), aby uzyskać informacje.

Aby uzyskać informacje o składnikach, które składają się na reguły przepływu poczty i jak działają reguły przepływu poczty, zobacz [Reguły przepływu poczty (reguły transportu) w Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules). Aby uzyskać dodatkowe informacje na temat sposobu działania reguł przepływu poczty z usługą Azure Information Protection, zobacz [Konfigurowanie reguł przepływu poczty Exchange Online dla etykiet usługi Azure Information Protection](/azure/information-protection/deploy-use/configure-exo-rules).

> [!IMPORTANT]
> W przypadku hybrydowych środowisk programu Exchange użytkownicy lokalni mogą wysyłać i odbierać zaszyfrowaną pocztę przy użyciu szyfrowania wiadomości tylko wtedy, gdy poczta e-mail jest kierowana przez Exchange Online. Aby skonfigurować szyfrowanie komunikatów w hybrydowym środowisku programu Exchange, należy najpierw [skonfigurować środowisko hybrydowe przy użyciu kreatora konfiguracji hybrydowej](/Exchange/exchange-hybrid), a następnie [skonfigurować pocztę do przepływu z Office 365 do serwera poczty e-mail](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-1-configure-mail-to-flow-from-office-365-to-your-on-premises-email-server) i [skonfigurować pocztę do przepływu z serwera poczty e-mail do Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-2-configure-mail-to-flow-from-your-email-server-to-office-365). Po skonfigurowaniu poczty do przepływu przez Office 365 można skonfigurować reguły przepływu poczty na potrzeby szyfrowania wiadomości, korzystając z tych wskazówek.

## <a name="create-mail-flow-rules-to-encrypt-email-messages-with-microsoft-purview-message-encryption"></a>Tworzenie reguł przepływu poczty w celu szyfrowania wiadomości e-mail za pomocą Szyfrowanie wiadomości w Microsoft Purview

Reguły przepływu poczty można zdefiniować do wyzwalania szyfrowania wiadomości przy użyciu umowy EAC.

### <a name="use-the-eac-to-create-a-rule-for-encrypting-email-messages-with-microsoft-purview-message-encryption"></a>Użyj umowy EAC, aby utworzyć regułę szyfrowania wiadomości e-mail za pomocą Szyfrowanie wiadomości w Microsoft Purview

1. W przeglądarce internetowej przy użyciu konta służbowego, któremu przyznano uprawnienia administratora globalnego, [zaloguj się do Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Wybierz kafelek **Administracja**.

3. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a> wybierz pozycję **Administracja centers** \> **Exchange**.

4. W usłudze EAC przejdź do pozycji **Reguły** **przepływu poczty** \> i wybierz pozycję **Nowa** ![ikona.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Utwórz nową regułę**. Aby uzyskać więcej informacji na temat korzystania z usługi EAC, zobacz [Centrum administracyjne programu Exchange w Exchange Online](/exchange/exchange-admin-center).

5. W **polu Nazwa** wpisz nazwę reguły, na przykład Szyfruj pocztę dla DrToniRamos@hotmail.com.

6. W **obszarze Zastosuj tę regułę, jeśli** wybierz warunek i w razie potrzeby wprowadź wartość. Aby na przykład zaszyfrować komunikaty przechodzące do DrToniRamos@hotmail.com:

   1. W **obszarze Zastosuj tę regułę, jeśli** wybierz **adresata**.

   2. Wybierz istniejącą nazwę z listy kontaktów lub wpisz nowy adres e-mail w polu **wyboru nazwy** .

      - Aby wybrać istniejącą nazwę, wybierz ją z listy, a następnie kliknij przycisk **OK**.

      - Aby wprowadzić nową nazwę, wpisz adres e-mail w polu **wyboru nazwy** , a następnie wybierz **pozycję sprawdź nazwy** \> **OK**.

7. Aby dodać więcej warunków, wybierz pozycję **Więcej opcji** , a następnie wybierz pozycję **Dodaj warunek** i wybierz z listy.

   Aby na przykład zastosować regułę tylko wtedy, gdy adresat znajduje się poza organizacją, wybierz pozycję **Dodaj warunek** , a następnie wybierz pozycję **Adresat jest zewnętrzny/wewnętrzny** \> **Poza organizacją** \> **OK**.

8. Aby włączyć szyfrowanie komunikatów, w obszarze **Wykonaj następujące** czynności wybierz pozycję **Modyfikuj zabezpieczenia komunikatów**, a następnie wybierz pozycję **Zastosuj Office 365 szyfrowanie komunikatów i ochronę praw**. Wybierz szablon usługi RMS z listy, wybierz pozycję **Zapisz**, a następnie wybierz przycisk **OK**.
  
  Lista szablonów zawiera wszystkie domyślne szablony i opcje, a także wszystkie szablony niestandardowe utworzone do użycia przez Office 365. Jeśli lista jest pusta, upewnij się, że skonfigurowano Szyfrowanie wiadomości w Microsoft Purview zgodnie z opisem w [temacie Konfigurowanie Szyfrowanie wiadomości w Microsoft Purview](set-up-new-message-encryption-capabilities.md). Aby uzyskać informacje o szablonach domyślnych, zobacz [Konfigurowanie szablonów platformy Azure Information Protection i zarządzanie nimi](/information-protection/deploy-use/configure-policy-templates). Aby uzyskać informacje o opcji **Nie przesyłaj dalej** , zobacz [Nie przesyłaj dalej dla wiadomości e-mail](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Aby uzyskać informacje na temat opcji **tylko do szyfrowania** , zobacz [Opcja tylko szyfrowania dla wiadomości e-mail](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

  Możesz wybrać **akcję dodawania** , jeśli chcesz określić inną akcję.

### <a name="use-the-eac-to-update-an-existing-mail-flow-rule-to-use-microsoft-purview-message-encryption"></a>Użyj umowy EAC, aby zaktualizować istniejącą regułę przepływu poczty w celu używania Szyfrowanie wiadomości w Microsoft Purview

1. W przeglądarce internetowej przy użyciu konta służbowego, któremu przyznano uprawnienia administratora globalnego, [zaloguj się do Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Wybierz kafelek **Administracja**.

3. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a> wybierz pozycję **Administracja centers** \> **Exchange**.

4. W usłudze EAC przejdź do pozycji **Reguły** **przepływu poczty**\>.

5. Na liście reguł przepływu poczty wybierz regułę, którą chcesz zmodyfikować do użycia z Szyfrowanie wiadomości w Microsoft Purview, a następnie wybierz pozycję **Edytuj ikonę Edytuj**![.](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).

6. Aby włączyć szyfrowanie przy użyciu Szyfrowanie wiadomości w Microsoft Purview, w obszarze **Wykonaj następujące** czynności wybierz pozycję **Modyfikuj zabezpieczenia komunikatów**, a następnie wybierz pozycję **Zastosuj Office 365 szyfrowanie komunikatów i ochronę praw**. Wybierz szablon usługi RMS z listy, wybierz pozycję **Zapisz** , a następnie wybierz przycisk **OK**.

   Lista szablonów zawiera wszystkie domyślne szablony i opcje, a także wszystkie szablony niestandardowe utworzone do użycia przez Office 365. Jeśli lista jest pusta, upewnij się, że skonfigurowano Szyfrowanie wiadomości w Microsoft Purview zgodnie z opisem w [temacie Konfigurowanie Szyfrowanie wiadomości w Microsoft Purview](set-up-new-message-encryption-capabilities.md). Aby uzyskać informacje o szablonach domyślnych, zobacz [Konfigurowanie szablonów platformy Azure Information Protection i zarządzanie nimi](/information-protection/deploy-use/configure-policy-templates). Aby uzyskać informacje o opcji Nie przesyłaj dalej, zobacz [Nie przesyłaj dalej dla wiadomości e-mail](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Aby uzyskać informacje o opcji tylko do szyfrowania, zobacz [Opcja Tylko szyfrowanie dla wiadomości e-mail](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

   Możesz wybrać **akcję dodawania** , jeśli chcesz określić inną akcję.

7. Z **poniższej listy Wykonaj** usuń wszystkie akcje przypisane do **opcji Modyfikuj zabezpieczenia** \> **komunikatów Zastosuj poprzednią wersję protokołu OME**.

8. Wybierz pozycję **Zapisz**.

## <a name="create-mail-flow-rules-to-remove-encryption-for-email-messages-with-microsoft-purview-message-encryption"></a>Tworzenie reguł przepływu poczty w celu usunięcia szyfrowania wiadomości e-mail za pomocą Szyfrowanie wiadomości w Microsoft Purview

Reguły przepływu poczty można zdefiniować w celu usunięcia szyfrowania wiadomości przy użyciu Szyfrowanie wiadomości w Microsoft Purview przy użyciu umowy EAC.

### <a name="use-the-eac-to-create-a-rule-to-remove-encryption-from-email-messages-with-microsoft-purview-message-encryption"></a>Użyj umowy EAC, aby utworzyć regułę usuwania szyfrowania z wiadomości e-mail przy użyciu Szyfrowanie wiadomości w Microsoft Purview

Szyfrowanie można usunąć z komunikatów, które zostały zastosowane przez organizację. Możesz również usunąć szyfrowanie z wszelkich zaszyfrowanych załączników, aby upewnić się, że cała wiadomość e-mail nie jest chroniona.

1. W przeglądarce internetowej przy użyciu konta służbowego, któremu przyznano uprawnienia administratora globalnego, [zaloguj się do Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Wybierz kafelek **Administracja**.

3. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a> wybierz pozycję **Administracja centers** \> **Exchange**.

4. W usłudze EAC przejdź do pozycji **Reguły** **przepływu poczty** \> i wybierz pozycję **Nowa** ![ikona.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Utwórz nową regułę**. Aby uzyskać więcej informacji na temat korzystania z usługi EAC, zobacz [Centrum administracyjne programu Exchange w Exchange Online](/exchange/exchange-admin-center).

5. W **polu Nazwa** wpisz nazwę reguły, taką jak `Remove encryption from outgoing mail`.

6. W **obszarze Zastosuj tę regułę, jeśli** wybierz warunki, w których szyfrowanie powinno zostać usunięte z komunikatów. Dodaj **Nadawca znajduje się** \> **wewnątrz organizacji** do wysyłania poczty _lub_ **Adresat znajduje się** \> **wewnątrz organizacji** do odbierania poczty.

7. W **obszarze Wykonaj następujące** czynności wybierz pozycję **Modyfikuj zabezpieczenia** \> komunikatów **Usuń Office 365 szyfrowania komunikatów i ochrony praw stosowanych przez organizację**.

8. (Opcjonalnie) W **obszarze Wykonaj następujące** czynności wybierz pozycję **Modyfikuj zabezpieczenia** \> komunikatów **Usuń ochronę praw załącznika stosowaną przez organizację**.

Zapisz regułę.

## <a name="create-mail-flow-rules-for-office-365-message-encryption-without-microsoft-purview-message-encryption"></a>Tworzenie reguł przepływu poczty na potrzeby szyfrowania wiadomości Office 365 bez Szyfrowanie wiadomości w Microsoft Purview

Jeśli twoja organizacja nie została jeszcze przeniesiona do Szyfrowanie wiadomości w Microsoft Purview, firma Microsoft zaleca, aby zaplanować przeniesienie, gdy tylko będzie to uzasadnione dla Twojej organizacji. Aby uzyskać instrukcje, zobacz [Konfigurowanie Szyfrowanie wiadomości w Microsoft Purview](set-up-new-message-encryption-capabilities.md). W przeciwnym razie zobacz [Definiowanie reguł przepływu poczty dla szyfrowania wiadomości Office 365, które nie używają Szyfrowanie wiadomości w Microsoft Purview](legacy-information-for-message-encryption.md#defining-mail-flow-rules-for-office-365-message-encryption-that-dont-use-microsoft-purview-message-encryption).

## <a name="related-content"></a>Zawartość pokrewna

[Szyfrowanie w Office 365](encryption.md)

[Konfigurowanie szyfrowania wiadomości w usłudze Microsoft Purview](set-up-new-message-encryption-capabilities.md)

[Dodawanie znakowania do zaszyfrowanych komunikatów](add-your-organization-brand-to-encrypted-messages.md)

[Reguły przepływu (transportu) poczty e-mail w usłudze Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)
