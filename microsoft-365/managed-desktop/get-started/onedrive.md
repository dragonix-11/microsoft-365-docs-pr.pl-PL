---
title: Microsoft OneDrive
description: Jak Microsoft Managed Desktop skonfigurować OneDrive dla zarejestrowanych urządzeń
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja, aplikacje, aplikacje biznesowe, aplikacje LOB
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 89d1851b3a2a7358a36d6a1ddd6f7db24dd2e1cf
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63015929"
---
# <a name="microsoft-onedrive"></a>Microsoft OneDrive

Microsoft Managed Desktop używa [OneDrive dla Firm](/onedrive/plan-onedrive-enterprise) jako usługi magazynu w chmurze dla wszystkich Microsoft Managed Desktop urządzeniach. Zapewnia to, że urządzenia są jak najbardziej nie stanowe. Użytkownicy będą mogli znaleźć swoje pliki niezależnie od urządzenia, do którego się logują. Jeśli na przykład zamienisz urządzenie Microsoft Managed Desktop nowym urządzeniem, pliki zostaną automatycznie zsynchronizowane z nowym urządzeniem.

Domyślnie te ustawienia są automatycznie konfigurowane na urządzeniach zarządzanych firmy Microsoft:

| Funkcja | Opis |
| ------ | ------ |
| Konfiguracja w trybie dyskretnym | OneDrive jest w trybie dyskretnym konfigurowane z kontem użytkownika. Automatycznie loguje się on do konta użytkownika użytego do zalogowania się do tego konta bez wylogowywu Windows. Aby uzyskać więcej informacji, zobacz [Dyskretne konfigurowanie kont użytkowników — OneDrive](/onedrive/use-silent-account-configuration) |
| Pliki na żądanie | Funkcja pliki na żądanie umożliwia użytkownikom uzyskiwanie dostępu do plików z magazynu w chmurze w usłudze OneDrive bez konieczności korzystania z miejsca na dysku. Aby uzyskać więcej informacji, zobacz [Oszczędzanie miejsca na dysku za OneDrive pliki na żądanie na Windows 10](https://support.microsoft.com/office/save-disk-space-with-onedrive-files-on-demand-for-windows-10-0e6860d3-d9f3-4971-b321-7092438fb38e). |
| Przenoszenie znanego folderu | Funkcja Przenoszenie znanego folderu jest włączona dyskretnie, aby  kopiować dane użytkowników w chmurze, co zapewnia im dostęp do plików z dowolnego urządzenia. Aby uzyskać więcej informacji, zobacz [Temat Kopii zapasowej folderów Dokumenty, Obrazy i Pulpit za pomocą OneDrive](https://support.microsoft.com/office/back-up-your-documents-pictures-and-desktop-folders-with-onedrive-d61a7930-a6fb-4b95-b28a-6552e77c3057). <p> Użytkownicy nie mogą wyłączyć funkcji Przenoszenie znanego folderu ani zmienić lokalizacji znanych folderów, aby zapewnić spójne środowisko na Microsoft Managed Desktop urządzeniach.</p>|

## <a name="user-experience"></a>Środowisko użytkownika

Gdy Microsoft Managed Desktop otrzymają nowe urządzenie, będą oni przechodzić przez środowisko pierwszego uruchomienia, wprowadzając swoje poświadczenia platformy Azure podczas konfigurowania urządzenia. Po zakończeniu tego procesu mogą oni uzyskać dostęp do swojego pulpitu i korzystać z OneDrive komputera.

1. System informuje użytkowników, OneDrive został skonfigurowany i że zalogowali się oni automatycznie do OneDrive.

:::image type="content" source="media/onedrive-sync.png" alt-text="Odczyt powiadomień, że teraz synchronizujesz pliki OneDrive i możesz edytować pliki w aplikacji OneDrive. Kliknij tutaj, aby wyświetlić swoje pliki.":::

2. System informuje użytkowników, OneDrive dla nich skonfigurowano przenoszenie znanego folderu.

:::image type="content" source="media/onedrive-folders.png" alt-text="Czytanie powiadomień Twój dział IT zawierał kopię zapasową ważnych folderów. Teraz będzie można wrócić do kopii zapasowej OneDrive dostępne na innych urządzeniach.":::

3. Aby zapobiec zduplikowaniu ikon na pulpicie w przypadku zresetowania lub ponownego zaimportowania urządzeń, system automatycznie usuwa Microsoft Edge i Microsoft Teams z synchronizacja usługi OneDrive. Te informacje są wyświetlane w Eksploratorze plików.

:::image type="content" source="media/onedrive-teams.png" alt-text="Eksplorator plików z listami Teams Edge z wyczyszonym polami wyboru i tekstem aktywowanym wykluczonym z synchronizacji.":::

## <a name="onedrive-sync-restrictions"></a>synchronizacja usługi OneDrive ograniczenia

Jeśli chcesz ograniczyć dostęp do synchronizacja usługi OneDrive, zalecamy kontrolowanie dostępu za pomocą Azure Active Directory dostępu warunkowego. Aby uzyskać więcej informacji, zobacz [Włączanie obsługi dostępu warunkowego w synchronizacja usługi OneDrive aplikacji](/onedrive/enable-conditional-access).

Jeśli nie możesz używać zasad dostępu warunkowego usługi Azure AD w organizacji, administrator IT powinien wykonać następujące czynności:

1. Jeśli jeszcze go nie znasz, sprawdź identyfikator dzierżawy zgodnie z opisem w te sposób: Znajdowanie identyfikatora Microsoft 365 [dzierżawy](/onedrive/find-your-office-365-tenant-id).
1. Zaloguj się do OneDrive administracyjnego.
1. W okienku po lewej stronie wybierz pozycję **Synchronizuj**.
1. Zaznacz pole **wyboru Zezwalaj na synchronizację** tylko na komputerach przyłączony do określonych domen, a następnie dodaj identyfikator dzierżawy do listy domen. Aby uzyskać więcej informacji, zobacz [Zezwalanie na synchronizację tylko na komputerach przyłączony do określonych domen](/onedrive/allow-syncing-only-on-specific-domains).

> [!NOTE]
> Te wskazówki dotyczą tylko dzierżaw w Microsoft Managed Desktop. Istnieją inne ustawienia, które nie zostały omówione w tym artykule.
