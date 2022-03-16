---
title: Definiowanie reguł przepływu poczty e-mail w celu szyfrowania wiadomości e-mail
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
description: Administratorzy mogą nauczyć się tworzenia reguł przepływu poczty e-mail (reguł transportu) do szyfrowania i odszyfrowywania wiadomości przy użyciu Szyfrowanie wiadomości usługi Office 365.
ms.openlocfilehash: bb50ed5d2b22fd74d4a6f88eba29f82d10be1f50
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2022
ms.locfileid: "63512814"
---
# <a name="define-mail-flow-rules-to-encrypt-email-messages"></a>Definiowanie reguł przepływu poczty e-mail w celu szyfrowania wiadomości e-mail

Jako administrator, który zarządza Exchange Online, możesz tworzyć reguły przepływu poczty e-mail (nazywane także regułami transportu) w celu ochrony wysyłanych i odbieranych wiadomości e-mail. Możesz skonfigurować reguły szyfrowania wszystkich wychodzących wiadomości e-mail i usuwania szyfrowania zaszyfrowanych wiadomości pochodzących z twojej organizacji lub z odpowiedzi na zaszyfrowane wiadomości wysłane z Twojej organizacji. Te reguły można <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange centrum</a> administracyjnym programu PowerShell lub centrum administracyjnego programu PowerShell Exchange Online. Oprócz ogólnych reguł szyfrowania możesz również włączyć lub wyłączyć opcje szyfrowania poszczególnych wiadomości dla użytkowników końcowych.

Nie można szyfrować poczty przychodzącej od nadawców spoza organizacji.

Jeśli ostatnio migrowałeś(-a) z usługi Active Directory RMS do usługi Azure Information Protection, musisz przejrzeć istniejące reguły przepływu poczty e-mail, aby upewnić się, że będą nadal działać w nowym środowisku. Ponadto, jeśli chcesz skorzystać z nowych funkcji usługi Szyfrowanie wiadomości usługi Office 365 (OME), dostępnych za pośrednictwem usługi Azure Information Protection, musisz zaktualizować istniejące reguły przepływu poczty e-mail. W przeciwnym razie użytkownicy nadal będą otrzymywać zaszyfrowaną pocztę z poprzednim formatem załącznika HTML, a nie nowym, bezproblemowym środowiskoM OME. Jeśli OME nie zostało jeszcze przez Ciebie ustawione, zobacz [Konfigurowanie nowych](set-up-new-message-encryption-capabilities.md) funkcji Szyfrowanie wiadomości usługi Office 365, aby uzyskać informacje.

Aby uzyskać informacje na temat składników, które zawierają reguły przepływu poczty e-mail i jak działają reguły przepływu poczty, zobacz Reguły przepływu poczty [(reguły transportu)](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) w Exchange Online. Aby uzyskać dodatkowe informacje na temat sposobu działania reguł przepływu poczty e-mail z usługą Azure Information Protection, zobacz Konfigurowanie Exchange Online [przepływu poczty e-mail dla etykiet usługi Azure Information Protection](/azure/information-protection/deploy-use/configure-exo-rules).

> [!IMPORTANT]
> W przypadku Exchange hybrydowych użytkownicy lokalni mogą wysyłać i odbierać zaszyfrowaną pocztę przy użyciu OME tylko wtedy, gdy wiadomości e-mail są kierowane przez Exchange Online. Aby skonfigurować OME w środowisku hybrydowym programu Exchange, należy najpierw skonfigurować środowisko hybrydowe [](/Exchange/exchange-hybrid) za pomocą Kreatora konfiguracji hybrydowej, a następnie skonfigurować pocztę tak, aby przepływała z programu [Office 365 do](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-1-configure-mail-to-flow-from-office-365-to-your-on-premises-email-server) serwera poczty e-mail i aby poczta przepływała z serwera poczty e-mail do [Office 365.](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-2-configure-mail-to-flow-from-your-email-server-to-office-365) Po skonfigurowaniu przepływu poczty e-mail przez Office 365 możesz skonfigurować reguły przepływu poczty dla usługi OME, używając tych wskazówek.

## <a name="create-mail-flow-rules-to-encrypt-email-messages-with-the-new-ome-capabilities"></a>Tworzenie reguł przepływu poczty e-mail w celu szyfrowania wiadomości e-mail przy użyciu nowych funkcji OME

Za pomocą Aplikacji EAC możesz zdefiniować reguły przepływu poczty e-mail wyzwalające szyfrowanie wiadomości za pomocą nowych funkcji OME.

### <a name="use-the-eac-to-create-a-rule-for-encrypting-email-messages-with-the-new-ome-capabilities"></a>Tworzenie reguły do szyfrowania wiadomości e-mail przy użyciu nowego programu OME za pomocą Aplikacji Programu użytkowania w sieci EAC

1. W przeglądarce internetowej, używając konta służbowego, które otrzymało uprawnienia administratora globalnego[, zaloguj](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser) się w celu Office 365.

2. Wybierz **kafelek Administrator** .

3. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365 wybierz</a> pozycję **Centra administracyjne** \> **Exchange**.

4. W selektorze wiadomości e-mail przejdź do **menu Reguły przepływu** \> **poczty e-mail** i wybierz **ikonę Nowy** ![nowy.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Utwórz nową regułę**. Aby uzyskać więcej informacji na temat korzystania z Centrum administracyjnego programu Exchange [centrum administracyjnego w programie Exchange Online](/exchange/exchange-admin-center).

5. W **imieniu** i nazwisku wpisz nazwę reguły, na przykład Szyfruj pocztę dla DrToniRamos@hotmail.com.

6. W **poleceni Zastosuj tę** regułę, jeśli wybierz warunek, a następnie w razie potrzeby wprowadź wartość. Aby na przykład zaszyfrować wiadomości do DrToniRamos@hotmail.com:

   1. W **polecej Zastosuj tę regułę**, jeśli wybierz **adresatem jest**.

   2. Wybierz istniejącą nazwę z listy kontaktów lub wpisz nowy adres e-mail w **polu nazw pól wyboru** .

      - Aby wybrać istniejącą nazwę, wybierz ją z listy, a następnie kliknij przycisk **OK**.

      - Aby wprowadzić nową nazwę, wpisz adres e-mail w  polu nazwy, a następnie wybierz pozycję **Sprawdź nazwy OK**\>.

7. Aby dodać więcej warunków, wybierz **pozycję Więcej opcji** , a następnie wybierz pozycję **Dodaj warunek** i wybierz pozycję z listy.

   Aby na przykład zastosować regułę tylko wtedy, gdy adresat znajduje się poza organizacją, wybierz  pozycję dodaj warunek, a następnie wybierz pozycję Adresat jest zewnętrzny **/** \> wewnętrzny Poza **organizacją** \> **OK**.

8. Aby włączyć szyfrowanie przy użyciu nowych funkcji OME, w poniższej czynności wybierz  pozycję Modyfikuj zabezpieczenia **wiadomości, a** następnie wybierz pozycję Zastosuj Szyfrowanie wiadomości usługi Office 365 **i ochronę praw**. Wybierz szablon RMS z listy, wybierz pozycję **Zapisz**, a następnie wybierz przycisk **OK**.
  
  Lista szablonów zawiera wszystkie domyślne szablony i opcje, a także wszystkie szablony niestandardowe utworzone do użycia przez Office 365. Jeśli lista jest pusta, upewnij się, że masz Szyfrowanie wiadomości usługi Office 365 z nowymi możliwościami zgodnie z opisem w te sposób: Konfigurowanie nowych Szyfrowanie wiadomości usługi Office 365 [możliwości](set-up-new-message-encryption-capabilities.md). Aby uzyskać informacje na temat szablonów domyślnych, zobacz [Konfigurowanie szablonów usługi Azure Information Protection i zarządzanie nimi](/information-protection/deploy-use/configure-policy-templates). Aby uzyskać informacje na temat **opcji Nie przesyłaj dalej** , zobacz Opcja [Nie przesyłaj dalej w wiadomościach e-mail](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Aby uzyskać informacje na **temat opcji tylko do szyfrowania** , zobacz [Opcja szyfrowania tylko dla wiadomości e-mail](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

  Jeśli chcesz określić **inną** akcję, możesz wybrać pozycję Dodaj akcję.

### <a name="use-the-eac-to-update-an-existing-mail-flow-rule-to-use-the-new-ome-capabilities"></a>Aktualizowanie istniejącej reguły przepływu poczty e-mail w celu używania nowych funkcji usługi OME za pomocą Usługi EAC

1. W przeglądarce internetowej, używając konta służbowego, które otrzymało uprawnienia administratora globalnego[, zaloguj](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser) się w celu Office 365.

2. Wybierz **kafelek Administrator** .

3. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365 wybierz</a> pozycję **Centra administracyjne** \> **Exchange**.

4. W Aplikacji EAC przejdź do reguły **przepływu poczty e-mail**\>.

5. Na liście reguł przepływu poczty wybierz regułę, którą chcesz zmodyfikować, aby używać nowych funkcji OME, a następnie wybierz **pozycję Edytuj ikonę** ![Edytuj](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).

6. Aby włączyć szyfrowanie przy użyciu nowych funkcji OME, w poniższej czynności wybierz  pozycję Modyfikuj zabezpieczenia **wiadomości, a** następnie wybierz pozycję **Zastosuj Szyfrowanie wiadomości usługi Office 365 i ochronę praw**. Wybierz szablon RMS z listy, wybierz pozycję **Zapisz** , a następnie wybierz przycisk **OK**.

   Lista szablonów zawiera wszystkie domyślne szablony i opcje, a także wszystkie szablony niestandardowe utworzone do użycia przez Office 365. Jeśli lista jest pusta, upewnij się, że masz już Szyfrowanie wiadomości usługi Office 365 z nowymi możliwościami zgodnie z opisem w tece Konfigurowanie nowych funkcji usługi [Szyfrowanie wiadomości usługi Office 365 wbudowanych w usługę Azure Information Protection](set-up-new-message-encryption-capabilities.md). Aby uzyskać informacje na temat szablonów domyślnych, zobacz [Konfigurowanie szablonów usługi Azure Information Protection i zarządzanie nimi](/information-protection/deploy-use/configure-policy-templates). Aby uzyskać informacje na temat opcji Nie przesyłaj dalej, zobacz Opcja [Nie przesyłaj dalej w wiadomościach e-mail](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Aby uzyskać informacje na temat opcji tylko do szyfrowania, zobacz Opcja [Szyfrowania tylko dla wiadomości e-mail](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

   Jeśli chcesz określić **inną** akcję, możesz wybrać pozycję Dodaj akcję.

7. Z listy **Wykonaj poniższe czynności** usuń wszystkie akcje przypisane  \> do ustawienia Modyfikuj zabezpieczenia wiadomości **Zastosuj poprzednią wersję OME**.

8. Wybierz pozycję **Zapisz**.

## <a name="create-mail-flow-rules-to-remove-encryption-for-email-messages-with-the-new-ome-capabilities"></a>Tworzenie reguł przepływu poczty e-mail w celu usunięcia szyfrowania wiadomości e-mail przy użyciu nowych funkcji OME

Za pomocą Aplikacji EAC możesz zdefiniować reguły przepływu poczty e-mail wyzwalające usuwanie szyfrowania wiadomości za pomocą nowych funkcji OME.

### <a name="use-the-eac-to-create-a-rule-to-remove-encryption-from-email-messages-with-the-new-ome-capabilities"></a>Tworzenie reguły w celu usunięcia szyfrowania z wiadomości e-mail przy użyciu Aplikacji programu EAC z nowymi możliwościami usługi OME

Możesz usunąć szyfrowanie wiadomości, które były stosowane przez Twoją organizację. Możesz również usunąć szyfrowanie z zaszyfrowanych załączników, aby zapewnić, że cała wiadomość e-mail nie będzie chronić.

1. W przeglądarce internetowej, używając konta służbowego, które otrzymało uprawnienia administratora globalnego[, zaloguj](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser) się w celu Office 365.

2. Wybierz **kafelek Administrator** .

3. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365 wybierz</a> pozycję **Centra administracyjne** \> **Exchange**.

4. W selektorze wiadomości e-mail przejdź do **menu Reguły przepływu** \> **poczty e-mail** i wybierz **ikonę Nowy** ![nowy.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Utwórz nową regułę**. Aby uzyskać więcej informacji na temat korzystania z Centrum administracyjnego programu Exchange [centrum administracyjnego w programie Exchange Online](/exchange/exchange-admin-center).

5. W **obszarze** Nazwa wpisz nazwę reguły, na przykład Usuń szyfrowanie poczty wychodzącej.

6. W **polecej Zastosuj tę regułę**, jeśli wybierz warunki, w których szyfrowanie ma zostać usunięte z wiadomości. Dodaj **Nadawca znajduje się wewnątrz** \> **organizacji w celu** wysyłania poczty _lub_ **Adresat** \> znajduje się wewnątrz organizacji **w celu** odbierania poczty.

7. W **aplikacji Wykonaj następujące czynności** wybierz pozycję Modyfikuj **zabezpieczenia** \> wiadomości Usuń **Szyfrowanie wiadomości usługi Office 365 i ochrony praw, które są stosowane w organizacji**.

8. (Opcjonalnie) W **aplikacji Wykonaj następujące czynności** wybierz pozycję **Modyfikuj zabezpieczenia** \> wiadomości Usuń ochronę przed prawami do załączników **zastosowaną przez organizację**.

Zapisz regułę.

## <a name="create-mail-flow-rules-for-office-365-message-encryption-without-the-new-capabilities"></a>Tworzenie reguł przepływu poczty e-mail Szyfrowanie wiadomości usługi Office 365 bez nowych możliwości

Jeśli Twoja organizacja nie została jeszcze przeniesiona do nowych funkcji usługi OME, firma Microsoft zaleca zaplanowanie przeniesienia się do nowych funkcji OME, gdy tylko będzie to uzasadnione dla Twojej organizacji. Aby uzyskać instrukcje, [zobacz Konfigurowanie nowych funkcji Szyfrowanie wiadomości usługi Office 365 wbudowanych w usługę Azure Information Protection](set-up-new-message-encryption-capabilities.md). W przeciwnym razie [zobacz Definiowanie reguł przepływu poczty e-Szyfrowanie wiadomości usługi Office 365, które nie korzystają z nowych funkcji OME](legacy-information-for-message-encryption.md#defining-mail-flow-rules-for-office-365-message-encryption-that-dont-use-the-new-ome-capabilities).

## <a name="related-content"></a>Zawartość pokrewna

[Szyfrowanie w Office 365](encryption.md)

[Konfigurowanie nowych funkcji Szyfrowanie wiadomości usługi Office 365 danych](set-up-new-message-encryption-capabilities.md)

[Dodawanie  marki do zaszyfrowanych wiadomości](add-your-organization-brand-to-encrypted-messages.md)

[Reguły przepływu poczty (reguły transportu) w programie Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)
