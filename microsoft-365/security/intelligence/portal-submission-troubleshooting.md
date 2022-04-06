---
title: Rozwiązywanie problemów z błędami portalu MSI spowodowanymi przez blok administratora
description: Rozwiązywanie problemów z błędami portalu MSI
ms.reviewer: ''
keywords: zabezpieczenia, przykładowe przesyłanie pomocy, plik złośliwego oprogramowania, plik wirusa, plik trojański, przesyłanie, wysyłanie do firmy Microsoft, przesyłanie przykładu, wirus, trojan, robak, niewykryte, nie wykrywa, e-mail microsoft, złośliwe oprogramowanie e-mail, myślę, że to jest złośliwe oprogramowanie, myślę, że to wirus, gdzie mogę wysłać wirusa, jest to wirus, MSE, nie wykrywa, nie ma podpisu, nie wykrywania, podejrzany plik,  MMPC, Centrum firmy Microsoft ds. ochrony przed złośliwym oprogramowaniem, naukowcy, analityk, WDSI, analiza bezpieczeństwa
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
ms.openlocfilehash: 544e96bd0a3985856f47bc8df424a2c2932f3c7e
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665673"
---
# <a name="troubleshooting-malware-submission-errors-caused-by-administrator-block"></a>Rozwiązywanie problemów z błędami przesyłania złośliwego oprogramowania spowodowanymi przez blok administratora

W niektórych przypadkach blok administratora może powodować problemy z przesyłaniem podczas próby przesłania potencjalnie zainfekowanego pliku do [witryny internetowej analizy zabezpieczeń firmy Microsoft](https://www.microsoft.com/wdsi) w celu analizy. W poniższym procesie pokazano, jak rozwiązać ten problem.

## <a name="review-your-settings"></a>Przeglądanie ustawień

Otwórz [ustawienia aplikacji usługi Azure Enterprise](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/UserSettings/menuId/). W obszarze **Enterprise** AplikacjeUżytkownicy  >  **mogą wyrazić zgodę na aplikacje uzyskujące dostęp do danych firmy w ich imieniu**, sprawdź, czy wybrano opcję Tak lub Nie.

- Jeśli wybrano pozycję **Nie** , administrator usługi Azure AD dla dzierżawy klienta będzie musiał wyrazić zgodę dla organizacji. W zależności od konfiguracji usługi Azure AD użytkownicy mogą mieć możliwość przesłania żądania bezpośrednio z tego samego okna dialogowego. Jeśli nie ma opcji żądania zgody administratora, użytkownicy muszą zażądać dodania tych uprawnień do administratora usługi Azure AD. Przejdź do poniższej sekcji, aby uzyskać więcej informacji.

- Jeśli **wybrano** opcję Tak, upewnij się, że ustawienie aplikacji Windows Defender Security Intelligence **Włączone dla użytkowników do logowania?** jest ustawione na wartość **Tak** na [platformie Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Properties/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/4a918a14-4069-4108-9b7d-76486212d75d). Jeśli wybrano opcję **Nie** , musisz zażądać włączenia go przez administratora usługi Azure AD.

## <a name="implement-required-enterprise-application-permissions"></a>Implementowanie wymaganych uprawnień aplikacji Enterprise

Ten proces wymaga administratora globalnego lub administratora aplikacji w dzierżawie.

1. Otwórz [Enterprise Ustawienia aplikacji](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Permissions/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/4a918a14-4069-4108-9b7d-76486212d75d).
2. Wybierz pozycję **Udziel zgody administratora dla organizacji**.
3. Jeśli możesz to zrobić, przejrzyj uprawnienia interfejsu API wymagane dla tej aplikacji, jak pokazano na poniższej ilustracji. Podaj zgodę dla dzierżawy.

    ![obraz udzielania zgody.](../../media/security-intelligence-images/msi-grant-admin-consent.jpg)

4. Jeśli administrator otrzyma błąd podczas próby ręcznego udzielenia zgody, spróbuj zastosować [opcję 1](#option-1-approve-enterprise-application-permissions-by-user-request) lub [opcję 2](#option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin) jako możliwe obejścia.

## <a name="option-1-approve-enterprise-application-permissions-by-user-request"></a>Opcja 1. Zatwierdzanie uprawnień aplikacji przedsiębiorstwa według żądania użytkownika

> [!NOTE]
> Jest to obecnie funkcja w wersji zapoznawczej.

Azure Active Directory administratorzy będą musieli zezwolić użytkownikom na żądanie zgody administratora na aplikacje. Sprawdź, czy ustawienie jest skonfigurowane na **wartość Tak** w [aplikacjach Enterprise](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/UserSettings/menuId/).

![Enterprise ustawienia użytkownika aplikacji.](../../media/security-intelligence-images/msi-enterprise-app-user-setting.jpg)

Więcej informacji można znaleźć w [temacie Konfigurowanie przepływu pracy zgody administratora](/azure/active-directory/manage-apps/configure-admin-consent-workflow).

Po zweryfikowaniu tego ustawienia użytkownicy mogą przejść przez logowanie klienta przedsiębiorstwa w analizie [zabezpieczeń firmy Microsoft](https://www.microsoft.com/wdsi/filesubmission) i przesłać żądanie zgody administratora, w tym uzasadnienie.

![Przepływ logowania firmy Contoso.](../../media/security-intelligence-images/msi-contoso-approval-required.png)

Administrator będzie mógł przeglądać i zatwierdzać uprawnienia aplikacji [żądania zgody administratora platformy Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AccessRequests/menuId/).

Po wyrażeniu zgody wszyscy użytkownicy w dzierżawie będą mogli korzystać z aplikacji.

## <a name="option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin"></a>Opcja 2. Udzielanie zgody administratora przez uwierzytelnienie aplikacji jako administratora

Ten proces wymaga, aby administratorzy globalni przechodzili przez przepływ logowania Enterprise klienta w [analizie zabezpieczeń firmy Microsoft](https://www.microsoft.com/wdsi/filesubmission).

![Przepływ logowania zgody.](../../media/security-intelligence-images/msi-microsoft-permission-required.jpg)

Następnie administratorzy przejrzyj uprawnienia i upewnij się, że wybierzesz pozycję **Zgoda w imieniu organizacji**, a następnie wybierz pozycję **Akceptuj**.

Wszyscy użytkownicy w dzierżawie będą teraz mogli korzystać z tej aplikacji.

## <a name="option-3-delete-and-readd-app-permissions"></a>Opcja 3. Usuwanie i odczytywanie uprawnień aplikacji

Jeśli żadna z tych opcji nie rozwiąże problemu, spróbuj wykonać następujące kroki (jako administrator):

1. Usuń poprzednie konfiguracje aplikacji. Przejdź do [Enterprise aplikacji](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Properties/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/982e94b2-fea9-4d1f-9fca-318cda92f90b) i wybierz pozycję **usuń**.

   ![Usuń uprawnienia aplikacji.](../../media/security-intelligence-images/msi-properties.png)

2. Przechwytywanie identyfikatora TenantID z [właściwości](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).

3. Zastąp element {tenant-id} określoną dzierżawą, która musi udzielić zgody tej aplikacji w poniższym adresie URL. Skopiuj ten adres URL do przeglądarki. Pozostałe parametry są już ukończone.
``https://login.microsoftonline.com/{tenant-id}/v2.0/adminconsent?client_id=f0cf43e5-8a9b-451c-b2d5-7285c785684d&state=12345&redirect_uri=https%3a%2f%2fwww.microsoft.com%2fwdsi%2ffilesubmission&scope=openid+profile+email+offline_access``

   ![Wymagane uprawnienia.](../../media/security-intelligence-images/msi-microsoft-permission-requested-your-organization.png)

4. Przejrzyj uprawnienia wymagane przez aplikację, a następnie wybierz pozycję **Akceptuj**.

5. Upewnij się, że uprawnienia są stosowane w [Azure Portal](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Permissions/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/ce60a464-5fca-4819-8423-bcb46796b051).

   ![Sprawdź, czy są stosowane uprawnienia.](../../media/security-intelligence-images/msi-permissions.jpg)

6. Zaloguj się do [analizy zabezpieczeń firmy Microsoft](https://www.microsoft.com/wdsi/filesubmission) jako użytkownik przedsiębiorstwa z kontem nieadministracyjnym, aby sprawdzić, czy masz dostęp.

 Jeśli ostrzeżenie nie zostanie rozwiązane po wykonaniu tych kroków rozwiązywania problemów, zadzwoń do pomocy technicznej firmy Microsoft.