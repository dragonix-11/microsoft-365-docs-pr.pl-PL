---
title: Uzyskiwanie dostępu do portalu administracyjnego
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
description: Informacje na temat odnajdowania portalu administracyjnego i korzystania z niego, w tym kontrolowania dostępu do niego.
ms.service: m365-md
ms.author: tiaraquan
author: tiaraquan
ms.topic: article
audience: ITPro
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.openlocfilehash: aee590f7479119ee7e8679b1048a691f156ccc77
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63315081"
---
# <a name="access-the-admin-portal"></a>Uzyskiwanie dostępu do portalu administracyjnego

Brama do Microsoft Managed Desktop [jest Microsoft Endpoint Manager.](https://endpoint.microsoft.com/) Jeśli nie masz informacji o możliwościach tego portalu do zarządzania urządzeniami, zapoznaj się z dokumentacją Microsoft Endpoint Manager [urządzenia](/mem/).

> [!NOTE]
> Obsługiwane [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) przeglądarki:
> - Microsoft Edge (najnowsza wersja)
> - Safari (najnowsza wersja, tylko dla komputerów Mac)
> - Chrome (najnowsza wersja)
> - Firefox (najnowsza wersja)

Twoje konto administracyjne będzie potrzebowało określonych uprawnień, aby uzyskać dostęp do Microsoft Managed Desktop funkcji administracyjnych w Microsoft Endpoint Manager.

Dostępem administratora do tych funkcji w organizacji można zarządzać, korzystając z kontroli dostępu opartej na rolach. Kilka Azure Active Directory administratora usługi Azure AD oraz wbudowane role administratora usługi Microsoft Managed Desktop są dostępne w celu zapewnienia bardziej szczegółowej kontroli nad różnymi funkcjami w portalu Microsoft Managed Desktop admin. Aby uzyskać więcej informacji o Azure Active Directory, zobacz Wbudowane role [w usłudze Azure AD](/azure/active-directory/roles/permissions-reference).

W przeciwieństwie do ról administratora usługi Azure AD, które dotyczą różnych produktów i usług firmy Microsoft, wbudowane role są specyficzne dla usługi Microsoft Managed Desktop i będą zagwarantować dostęp tylko do funkcji administratora tej usługi. Administratorzy mogą przypisywać wbudowane role użytkownikom pojedynczo lub w połączeniu z rolami administratora usługi Azure AD, aby dodać Microsoft Managed Desktop do istniejących kont administratora.

## <a name="azure-active-directory-roles-with-microsoft-managed-desktop-access"></a>Azure Active Directory z dostępem Microsoft Managed Desktop użytkowników

| Rola usługi Azure AD | Microsoft Managed Desktop uprawnień |
| ----- | ----- |
| Administrator globalny | Administratorzy pełniący tę **rolę będą mieli** uprawnienia do odczytu i zapisu wszystkich funkcji w portalu Microsoft Managed Desktop administracyjnego. |
| Czytnik globalny | Administratorzy z tą rolą **będą mieli uprawnienia** tylko do odczytu do wszystkich funkcji w portalu Microsoft Managed Desktop administracyjnego. |
| Administrator usługi Intune | Administratorzy z tą rolą **będą mieli uprawnienia** do odczytu i zapisu do funkcji nie związanych z zabezpieczeniami w portalu Microsoft Managed Desktop administracyjnego. |
| Administrator pomocy technicznej usługi | Administratorzy z tą rolą będą mieli  uprawnienia tylko do odczytu do funkcji nie związanych z zabezpieczeniami  i uprawnieniami do zapisu w celu zarządzania wnioskami o pomoc techniczną, w tym żądaniami eskalacji w portalu Microsoft Managed Desktop administracyjnego. |
| Administrator zabezpieczeń | Administratorzy z tą rolą będą mieli  uprawnienia tylko do odczytu do wszystkich funkcji i  uprawnień do zapisu do funkcji związanych z zabezpieczeniami w programie Microsoft Managed Desktop w portalu administracyjnym. |
| Czytnik zabezpieczeń |Administratorzy z tą rolą **będą mieli uprawnienia** tylko do odczytu do wszystkich funkcji w portalu Microsoft Managed Desktop administracyjnego. |

Jeśli potrzebujesz pomocy dotyczącej przypisywania ról Azure Active Directory, zobacz Wbudowane role [w usłudze Azure AD](/azure/active-directory/roles/permissions-reference).

> [!IMPORTANT]
> Tylko rola administratora globalnego ma uprawnienia niezbędne do *zarejestrowania* organizacji w Microsoft Managed Desktop. Miej na Azure Active Directory, że role użytkowników będą mieć uprawnienia do kont użytkowników z różnych usługi firmy Microsoft. Po zakończeniu rejestrowania przy Microsoft Managed Desktop należy zawsze używać roli z jak najmniejszymi *uprawnieniami* niezbędnymi do wykonywania innych zadań.

## <a name="built-in-roles-provided-by-microsoft-managed-desktop"></a>Role wbudowane udostępniane przez Microsoft Managed Desktop

Poniżej przedstawiono wbudowane role udostępniane przez użytkownika Microsoft Managed Desktop:

| Rola wbudowana | Microsoft Managed Desktop uprawnień |
| ----- | ----- |
| Microsoft Managed Desktop administratora usługi | Przypisanie tej roli do użytkownika powoduje nadanie administratorowi uprawnień  do odczytu i zapisu Microsoft Managed Desktop funkcji nie związanych z zabezpieczeniami w portalu Microsoft Managed Desktop administratora. |
| Microsoft Managed Desktop service Reader | Gdy ta rola jest przypisana do użytkownika, nadaje administratorowi  uprawnienia tylko do odczytu do funkcji Microsoft Managed Desktop związanych z zabezpieczeniami w portalu Microsoft Managed Desktop administratora. |
| Microsoft Managed Desktop Menedżera zabezpieczeń | Przypisanie tej roli do użytkownika powoduje nadanie administratorowi uprawnień  do odczytu i zapisu tylko do funkcji związanych z zabezpieczeniami w portalu Microsoft Managed Desktop administracyjnego. |
| Microsoft Managed Desktop pomocy technicznej |Gdy ta rola jest przypisana do użytkownika, nadaje administratorowi  uprawnienia do odczytu i zapisu tylko do tworzenia żądań podwyższenia i zarządzania nimi oraz obsługi żądań eskalacji zaangażowaniu partnera w portalu administracyjnym usługi Microsoft Managed Desktop. |

> [!NOTE]
> Funkcje zabezpieczeń obejmują komunikację związaną z zabezpieczeniami, zarządzanie kontaktami zabezpieczeń, zarządzanie wnioskami o pomoc techniczną związaną z zabezpieczeniami oraz dostęp do raportów związanych z zabezpieczeniami.

### <a name="assigning-built-in-roles-to-user"></a>Przypisywanie ról wbudowanych do użytkownika

Aby ułatwić zarządzanie wbudowanymi rolami, dla każdej roli niestandardowej istnieje grupa zabezpieczeń o nazwie "Nowoczesne role służbowe — _nazwa roli_". Na przykład "Nowoczesne role służbowe — Menedżer zabezpieczeń").

**Aby przypisać użytkowników do jednej z tych grup zabezpieczeń:**

1. Przejdź do Microsoft Endpoint Manager portalu.
2. W okienku po lewej stronie wybierz pozycję **Grupy**.
3. Wyszukaj pozycję **Nowoczesne role miejsca pracy**, a następnie wybierz grupę skojarzoną z rolą, którą chcesz przypisać.
4. Wybierz **pozycję** Członkowie po lewej stronie, a następnie wybierz **pozycję + Dodaj członków** na pasku poleceń.
5. Wprowadź adres e-mail dodawanej osoby. Jeśli jest to gość, musisz go zaprosić, aby można było przypisać grupę.
6. Wybierz **pozycję** Wybierz u dołu.

> [!NOTE]
> Zagnieżdżanie grup zabezpieczeń dla przypisywania ról nie jest obecnie obsługiwane.

### <a name="assigning-built-in-roles-to-groups"></a>Przypisywanie wbudowanych ról do grup

**Aby przypisać jedną lub więcej z wbudowanych ról do istniejącej grupy:**

1. Przejdź do [portal.azure.com](https://portal.azure.com/).
2. Wyszukaj i otwórz Enterprise **aplikacji**.
3. Zmień filtr **Typ aplikacji na** aplikację _Microsoft Applications_ , a następnie wybierz pozycję **Zastosuj**.
4. Wyszukaj i wybierz _interfejsy API klienta nowoczesnego miejsca pracy_.
5. W **okienku po** lewej stronie wybierz pozycję Użytkownicy i grupy, a następnie wybierz **pozycję + Dodaj użytkownika/grupę**.
6. Wyszukaj grupę na stronie Użytkownicy **i grupy**.
7. Wyszukaj odpowiednie role na stronie **Wybierz rolę, a** następnie ją wybierz.
8. Wybierz **pozycję Przypisz**.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Procedura rozpoczynania pracy z Microsoft Managed Desktop

1. Portal administracyjny programu Access (ten artykuł).
1. [Dodaj i zweryfikuj kontakty administratora w portalu administracyjnym](add-admin-contacts.md).
1. [Dostosuj ustawienia po rejestracji](conditional-access.md).
1. Wdrażanie i [przypisywanie Intune — Portal firmy](company-portal.md).
1. [Przypisywanie licencji](assign-licenses.md).
1. [Wdychuj aplikacje](deploy-apps.md).
1. [Przygotowywanie urządzeń](prepare-devices.md).
1. Skonfiguruj środowisko [pierwszego uruchomienia za pomocą rozwiązania Autopilot i strony stanu rejestracji](esp-first-run.md).
1. [Włączanie funkcji pomocy technicznej dla użytkowników](enable-support.md).
1. [Przygotuj użytkowników do korzystania z urządzeń](get-started-devices.md).
1. [Wprowadzenie do sterowania aplikacją](get-started-app-control.md).
