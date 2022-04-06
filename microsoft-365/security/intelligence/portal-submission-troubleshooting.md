---
title: Rozwiązywanie problemów z portalem MSI spowodowanych przez blokadę administratora
description: Rozwiązywanie problemów z błędami portalu MSI
ms.reviewer: ''
keywords: zabezpieczenia, przykładowa pomoc przy przesyłaniu, plik złośliwego oprogramowania, plik antywirusowy, plik trojański, prześlij, wyślij do firmy Microsoft, prześlij próbkę, wirus, trojański, robak, niezakrywony, nie wykrywa, wysyłaj wiadomości e-mail do firmy Microsoft, wysyłaj wiadomości e-mail z złośliwym oprogramowaniem, sądzę, że jest to wirus, do którego mogę wysłać wirusa, to ten wirus, MSE, nie wykrywa, nie ma podpisu, nie wykrywa, podejrzewa plik,  MMPC, Centrum firmy Microsoft ds. ochrony przed złośliwym oprogramowaniem, analityk, WDSI, analizy zabezpieczeń
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: e70eb5192a1fd6171b8e515509ad336aa99a2c63
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63705780"
---
# <a name="troubleshooting-malware-submission-errors-caused-by-administrator-block"></a>Rozwiązywanie problemów z błędami przesyłania złośliwego oprogramowania spowodowanymi przez blokadę administratora
W niektórych przypadkach blok administratora może powodować problemy z przesyłaniem, gdy próbujesz przesłać do analizy potencjalnie zainfekowany plik do witryny internetowej analizy zabezpieczeń firmy [Microsoft](https://www.microsoft.com/wdsi) . Poniżej przedstawiono proces rozwiązywania tego problemu.

## <a name="review-your-settings"></a>Przejrzyj ustawienia
Otwórz ustawienia aplikacji Azure [Enterprise.](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/UserSettings/menuId/) W **Enterprise** AplikacjeUżytkowcy  >   mogą wyrażać zgodę na uzyskiwanie przez aplikacje dostępu do danych firmy w ich imieniu, sprawdź, czy jest zaznaczona opcja Tak lub Nie.

- Jeśli **nie** jest wybrane, administrator usługi Azure AD dla dzierżawy klienta będzie musiał udzielić zgody dla organizacji. W zależności od konfiguracji usługi Azure AD użytkownicy mogą mieć możliwość przesyłania żądania bezpośrednio z tego samego okna dialogowego. Jeśli nie ma opcji prośby o zgodę administratora, użytkownicy muszą zażądać dodania tych uprawnień do swojego administratora usługi Azure AD. Przejdź do następnej sekcji, aby uzyskać więcej informacji.

- Jeśli **wybrano** pozycję Tak, upewnij się, że Windows Defender dla aplikacji do analizy zabezpieczeń Włączono logowanie dla użytkowników **?** jest ustawione na wartość **Tak** [na platformie Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Properties/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/4a918a14-4069-4108-9b7d-76486212d75d).Jeśli **nie** jest zaznaczone, musisz poprosić administratora usługi Azure AD o jej włączenie. 
  
## <a name="implement-required-enterprise-application-permissions"></a>Implementowanie wymaganych Enterprise aplikacji 
Ten proces wymaga administratora globalnego lub administratora aplikacji w dzierżawie.
 1. Otwórz [Enterprise Ustawienia aplikacji](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Permissions/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/4a918a14-4069-4108-9b7d-76486212d75d). 
 2. Wybierz **pozycję Utłań zgodę administratora dla organizacji**.
 3. Jeśli możesz to zrobić, przejrzyj uprawnienia interfejsu API wymagane dla tej aplikacji, jak pokazano na poniższej ilustracji. Ułać zgodę dzierżawy.

    ![obraz udzielenia zgody.](../../media/security-intelligence-images/msi-grant-admin-consent.jpg)

  4. Jeśli administrator otrzyma komunikat o błędzie podczas próby wyrażenia zgody ręcznie, wypróbuj ewentualne obejścia Dla opcji [1](#option-1-approve-enterprise-application-permissions-by-user-request) lub Opcja [2](#option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin) .
  
## <a name="option-1-approve-enterprise-application-permissions-by-user-request"></a>Opcja 1 Zatwierdzanie uprawnień aplikacji przedsiębiorstwa na żądanie użytkownika
> [!Note]
> To jest obecnie funkcja w wersji Preview.

Azure Active Directory będą musieli zezwolić użytkownikom na zażądanie zgody administratora na aplikacje. Sprawdź, czy ustawienie w innych aplikacjach jest [skonfigurowane Enterprise tak](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/UserSettings/menuId/).

![Enterprise ustawień użytkownika aplikacji.](../../media/security-intelligence-images/msi-enterprise-app-user-setting.jpg)

Więcej informacji zawiera przepływ pracy Konfigurowanie [zgody administratora](/azure/active-directory/manage-apps/configure-admin-consent-workflow).

Po zweryfikowaniu tego ustawienia użytkownicy mogą przejść przez proces logowania klienta przedsiębiorstwa w witrynie [Microsoft Security Intelligence](https://www.microsoft.com/wdsi/filesubmission) i przesłać prośbę o zgodę administratora, w tym o uzasadnienie.

![Przepływ logowania firmy Contoso.](../../media/security-intelligence-images/msi-contoso-approval-required.png)

Administrator będzie mógł przeglądać i zatwierdzać uprawnienia aplikacji Żądania zgody administratora [platformy Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AccessRequests/menuId/).

Po wyrażenia zgody wszyscy użytkownicy w dzierżawie będą mogli używać aplikacji.
  
## <a name="option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin"></a>Opcja 2 Wyrażenie zgody administratora przez uwierzytelnienie aplikacji jako administratora 
Ten proces wymaga, aby administratorzy globalni przechodzili przez proces logowania Enterprise się przez analizę zabezpieczeń [firmy Microsoft](https://www.microsoft.com/wdsi/filesubmission).

![Przepływ logowania zgody.](../../media/security-intelligence-images/msi-microsoft-permission-required.jpg)

Następnie administratorzy przejrzyj uprawnienia i upewnij się, że wybierasz pozycję Zgoda **w** imieniu twojej organizacji, a następnie wybierz pozycję **Zaakceptuj**.

Wszyscy użytkownicy w dzierżawie będą mogli używać tej aplikacji.

## <a name="option-3-delete-and-readd-app-permissions"></a>Opcja 3. Usuwanie i odczytywanie uprawnień aplikacji
Jeśli żadna z tych opcji nie rozwiąże problemu, spróbuj wykonać następujące czynności (jako administrator):

1. Usuń poprzednie konfiguracje aplikacji. Przejdź do [Enterprise aplikacji i](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Properties/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/982e94b2-fea9-4d1f-9fca-318cda92f90b) wybierz pozycję **usuń**.

   ![Usuń uprawnienia aplikacji.](../../media/security-intelligence-images/msi-properties.png)

2. Przechwyć tenantID z [właściwości](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).

3. Zastąp element {tenant-id} określoną dzierżawą, która musi udzielić zgody na tę aplikację, w poniższym adresie URL. Skopiuj ten adres URL do przeglądarki. Pozostałe parametry są już ukończone. 
``https://login.microsoftonline.com/{tenant-id}/v2.0/adminconsent?client_id=f0cf43e5-8a9b-451c-b2d5-7285c785684d&state=12345&redirect_uri=https%3a%2f%2fwww.microsoft.com%2fwdsi%2ffilesubmission&scope=openid+profile+email+offline_access``

   ![Potrzebne uprawnienia.](../../media/security-intelligence-images/msi-microsoft-permission-requested-your-organization.png)

4. Przejrzyj uprawnienia wymagane przez aplikację, a następnie wybierz pozycję **Zaakceptuj**. 

5. Potwierdź, że uprawnienia zostały zastosowane w [portalu Azure Portal](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Permissions/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/ce60a464-5fca-4819-8423-bcb46796b051).

   ![Sprawdź, czy uprawnienia zostały zastosowane.](../../media/security-intelligence-images/msi-permissions.jpg)
   
6. Zaloguj się do analizy [zabezpieczeń firmy Microsoft](https://www.microsoft.com/wdsi/filesubmission) jako użytkownik przedsiębiorstwa z kontem bez administratora, aby sprawdzić, czy masz dostęp.

 Jeśli po tych czynnościach rozwiązywania problemów ostrzeżenie nie zostanie rozwiązane, zadzwoń do pomocy technicznej firmy Microsoft.