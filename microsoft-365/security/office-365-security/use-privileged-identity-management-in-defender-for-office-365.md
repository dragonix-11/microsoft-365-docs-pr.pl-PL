---
title: Używaj usługi Azure Privileged Identity Management (PIM) w usłudze Microsoft Defender Office 365, aby ograniczyć dostęp administratora do narzędzi do ochrony przed cyberzagrożeniami.
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
description: Dowiedz się, jak zintegrować usługę Azure PIM, aby udzielić użytkownikom dostępu na czas i w ograniczonym czasie w celu wykonania podwyższonych uprawnień zadań w usłudze Microsoft Defender Office 365, co obniża ryzyko związane z danymi.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3be90ff1113e25ea418aaf1a25b12574b3bbbe1f
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032137"
---
<!--A-->
# <a name="privileged-identity-management-pim-and-why-to-use-it-with-microsoft-defender-for-office-365"></a>Privileged Identity Management (PIM) i dlaczego warto używać go z programem Microsoft Defender dla Office 365

Privileged Identity Management (PIM) to funkcja platformy Azure, która po jej skonfigurowaniu zapewnia użytkownikom dostęp do danych przez ograniczony czas (czasami nazywany czasem czasem pokrównanym czasem), dzięki czemu można wykonać określone zadanie. Ten dostęp jest zapewniany "w czasie", aby wykonać wymaganą akcję, a następnie jest odwołany. Dane pim ograniczają dostęp i czas, przez który użytkownik ma dostęp do poufnych danych, co ogranicza ryzyko związane z ekspozycją w porównaniu z kontami administracji uprzywilejowanymi, które mają długoterminowy dostęp do danych i innych ustawień. Jak możemy korzystać z tej funkcji (PIM) w połączeniu z programem Microsoft Defender dla systemu Office 365?

> [!TIP]
> Dostęp do funkcji PIM jest ograniczony do poziomu roli i tożsamości i umożliwia wykonywanie wielu zadań. Nie należy tego mylić z zarządzaniem dostępem z uprawnieniami (PAM, Privileged Access Management), który jest ograniczony poziomem zadań.

## <a name="steps-to-use-pim-to-grant-just-in-time-access-to-defender-for-office-365-related-tasks"></a>Procedura używania funkcji zarządzania pim w celu udzielenia dostępu w czasie rzeczywistym do usługi Defender dla Office 365 zadań pokrewnych

Przez skonfigurowanie usługi PIM do współpracy z usługą Defender dla systemu Office 365 administratorzy tworzą proces, w ramach których użytkownik może zażądać dostępu do działań, których potrzebuje. Użytkownik musi *wyjustować* potrzebę podwyższenia uprawnień.

W tym przykładzie skonfigurujemy "Alexa", członka naszego zespołu zabezpieczeń, który będzie miał dostęp o zerowej pozycji w programie Office 365, ale może podnieść swoją rolę wymaganą zarówno do zwykłych operacji, jak np. chłoniania przed zagrożeniami, a następnie wyższego poziomu uprawnień, gdy są rzadziej wykonywane, ale poufne [](remediate-malicious-email-delivered-office-365.md) operacje, takie jak korygowanie złośliwych wiadomości e-mail.[](threat-hunting-in-threat-explorer.md)

> [!NOTE]
> W ten sposób możesz wykonać kroki wymagane do konfigurowania usługi zarządzania zabezpieczeniami dla analityka zabezpieczeń, który potrzebuje możliwości przeczyszczania wiadomości e-mail przy użyciu Eksploratora zagrożeń w programie Microsoft Defender dla programu Office 365, ale tych samych kroków można użyć dla innych ról RBAC w portalu zabezpieczeń i zgodności. Na przykład ten proces może być używany przez pracownika przetwarza który potrzebuje dziennego dostępu do zbierania elektronicznych materiałów dowodowych w celu wyszukiwania i pracy nad sprawą, ale tylko czasami potrzebuje podwyższonych uprawnień do eksportowania danych z dzierżawy.

***Krok 1***. W konsoli usługi Azure PIM dla subskrypcji dodaj użytkownika (Alex) do roli czytnika zabezpieczeń Azure i skonfiguruj ustawienia zabezpieczeń związane z aktywacją.

1. Zaloguj się do [Centrum administracyjnego usługi Azure AD i](https://aad.portal.azure.com/) wybierz **pozycję Azure Active Directory** >  **i administratorzy**.
2. Na **liście ról wybierz pozycję Czytnik** zabezpieczeń, a następnie wybierz **pozycję Ustawienia** >  **Edit.**
3. Ustaw "**Maksymalny czas trwania aktywacji (godziny)**" na normalny dzień roboczy, a wartość "W trakcie aktywacji" jako wymaganie uwierzytelniania **wieloskładnikowego Azure**.
4. W związku z tym, że jest to normalny poziom uprawnień Alexy w przypadku codziennie wykonywanych operacji, wyczyść pole wyboru Wymagaj uzasadnienia przy aktywacji > **aktualizacji**.
5. Wybierz **pozycję Dodaj zadaniaNo** >  **wybrany członek >** wybierz lub wpisz nazwę członka, aby wyszukać odpowiedniego członka.
6. Kliknij przycisk  Wybierz, aby wybrać członka, który ma zostać członkiem, który będzie miał uprawnienia do logowania się > kliknij pozycję **Dalej > nie** wprowadzaj żadnych zmian na stronie Dodawanie zadania (zarówno  typ zadania Kwalifikuje  się, jak i czas trwania. Automatycznie będą domyślne ) i Przypisz **.**

Na następnej stronie w obszarze Kwalifikujące się zadania pojawi się nazwa Twojego użytkownika (w tym miejscu "Alexa"), co oznacza, że może on pełnić rolę numer PIM przy wcześniej skonfigurowanych ustawieniach.

> [!NOTE]
> Aby szybko zapoznać się z Privileged Identity Management klip [wideo](https://www.youtube.com/watch?v=VQMAg0sa_lE).

:::image type="content" source="../../media/pim-mdo-role-setting-details-for-security-reader-show-8-hr-duration.png" alt-text="Upewnij się, że przeskanowane są ustawienia roli czytnika zabezpieczeń w tece Zarządzanie dostępem uprzywilejowanym. Tutaj zobaczysz, że maksymalny czas trwania aktywacji usługi pim wynosi 8 godzin.":::

***Krok 2***. Utwórz drugą (podwyższoną poziom) grupę uprawnień do dodatkowych zadań i przypisz uprawnienia.

Za [pomocą grup z uprawnieniami programu Access](/azure/active-directory/privileged-identity-management/groups-features) możemy teraz tworzyć własne grupy niestandardowe i łączyć uprawnienia lub zwiększać szczegółowość w przypadkach, gdy jest to wymagane do spełnienia wymagań i praktyk organizacji.

### <a name="create-a-role-group-requiring-the-permissions-we-need"></a>Tworzenie grupy ról wymagającej wymaganych uprawnień

W portalu Microsoft 365 Defender utwórz niestandardową grupę ról zawierającą odpowiednie uprawnienia.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do **uprawnień do & Ról, a** następnie wybierz pozycję Role w obszarze Poczta e-mail **i współpraca**. Aby przejść bezpośrednio do **strony Uprawnienia**, użyj .<https://security.microsoft.com/emailandcollabpermissions>
2. Na stronie **Uprawnienia** kliknij ikonę ![Utwórz.](../../media/m365-cc-sc-create-icon.png) **Utwórz**.
3. Nadaj grupie nazwę, tak aby odzwierciedlała jej przeznaczenie, takie jak "Wyszukaj i przeczyść dane PIM".
4. Nie dodawaj członków, po prostu zapisz grupę i przejdź do następnej części!

### <a name="create-the-security-group-in-azure-ad-for-elevated-permissions"></a>Tworzenie grupy zabezpieczeń w usłudze Azure AD w celu podwyższonych uprawnień

1. Przejdź z powrotem do [Centrum administracyjnego usługi Azure AD i](https://aad.portal.azure.com/) przejdź do pozycji **Grupa Azure** **ADGroupsNew** >  > .
2. Nadaj nazwę grupie usługi Azure AD, aby odzwierciedlała jej cel, w tej chwili nie są **wymagani** żadni właściciele ani członkowie.
3. Dla **grupy można przypisać role usługi Azure AD tak****.**
4. Nie dodawaj żadnych ról, członków ani właścicieli, utwórz grupę.
5. Wróć do właśnie utworzonej grupy i wybierz pozycję **Privileged AccessEnable** >  **Privileged Access (Dostęp z uprawnieniami**).
6. W grupie wybierz pozycję **Kwalifikujące** >  się przydziałyDaj **przypisania > Dodaj** użytkownika, który potrzebuje funkcji Wyszukiwania & Przeczyść jako **członka**.
7. Skonfiguruj **Ustawienia w** okienku Dostęp z uprawnieniami grupy. Wybierz pozycję **Edytuj** ustawienia dla roli **Członka**.
8. Zmień czas aktywacji, aby dopasować go do swojej organizacji. W tym przykładzie przed wybraniem przycisku Aktualizuj należy podać uwierzytelniania wieloskładnikowego *Azure**,* justowanie i informacje o *biletach*.

### <a name="nest-the-newly-created-security-group-into-the-role-group"></a>Zagnieżdżanie nowo utworzonej grupy zabezpieczeń w grupie ról

1. [Połączenie się z Centrum & zgodności w programie PowerShell](/powershell/exchange/connect-to-scc-powershell) i uruchom następujące polecenie:

   ```powershell
   Add-RoleGroupMember "<<Role Group Name>>" -Member "<<Azure Security Group>>"`
   ```

## <a name="test-your-configuration-of-pim-with-defender-for-office-365"></a>Przetestuj konfigurację usługi PIM za pomocą usługi Defender dla Office 365

1. Zaloguj się przy użyciu użytkownika testowego (Alex), który w tym momencie nie powinien mieć dostępu administracyjnego w [portalu Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center) sieci.
2. Przejdź do funkcji PIM, w której użytkownik może aktywować swoją codziennie rolę czytnika zabezpieczeń.
3. Podczas próby przeczyszczania wiadomości e-mail przy użyciu Eksploratora zagrożeń jest wyświetlany komunikat o błędzie z informacją, że potrzebne są dodatkowe uprawnienia.
4. Program PIM po raz drugi w bardziej podwyższonym poziomie roli, po krótkim opóźnieniu powinno być teraz możliwe oczyszczanie wiadomości e-mail bez problemów.

   :::image type="content" source="../../media/pim-mdo-add-the-search-and-purge-role-assignment-to-this-pim-role.PNG" alt-text="Jeśli użytkownik, który został dodany (Alex) za pośrednictwem roli czytnika zabezpieczeń , próbuje usunąć podejrzaną wiadomość e-mail, zostanie mu wyświetlony komunikat z informacją &quot;Do działania na tej wiadomości e-mail potrzeba roli wyszukiwania i przeczyszczania. Skontaktuj się z administratorem, aby uzyskać przypisanie roli lub dodać wiadomość e-mail do zdarzenia.":::

Trwałe przypisywanie ról administracyjnych i uprawnień, takich jak rola wyszukiwania i przeczyszczania, nie jest wstrzymane z inicjatywą zabezpieczeń Zero Trust, ale jak widać, za pomocą usługi zarządzania zabezpieczeniami (PIM) można udzielić dostępu w czasie rzeczywistym do wymaganego zestawu narzędzi.

*Dziękujemy inżynierowi klienta Benowi Harrisowi za dostęp do wpisu w blogu i zasobów używanych na potrzeby tej zawartości.*

<!--A-->