---
title: Wymagania wstępne dotyczące kont gości
description: Wskazówki dotyczące konfiguracji kont gości i sposobu ich dostosowania
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 80770c6c122cc4e2892c22a43f185ffbac40c637
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/10/2022
ms.locfileid: "63027105"
---
# <a name="prerequisites-for-guest-accounts"></a>Wymagania wstępne dotyczące kont gości

## <a name="external-collaboration-settings"></a>Ustawienia współpracy zewnętrznej

Microsoft Managed Desktop do uzyskiwania dostępu do konta gościa w organizacji usługi Azure AD zaleca następującą konfigurację. Możesz dostosować te ustawienia w Portalu [Azure](https://portal.azure.com) w obszarze Tożsamości **zewnętrzne / Ustawienia współpracy zewnętrznej**:

| Ustawienie | Ustaw na |
| ------ | ------ |
| Dostęp dla gości | Goście mają ograniczony dostęp do właściwości i członkostwa w obiektach katalogu. |
| Ustawienia zapraszania gościa | Użytkownicy i użytkownicy przypisani do określonych ról administratora mogą zapraszać gości, w tym gości z uprawnieniami członków |

Microsoft Managed Desktop dostępu do konta gościa w organizacji usługi Azure AD wymagana jest następująca konfiguracja. Możesz dostosować to ustawienie w portalu [Azure w](https://portal.azure.com) obszarze **Tożsamości zewnętrzne /Ustawienia współpracy zewnętrznej**:

| Ustawienie | Opcja |
| ------ | ------ |
| Ograniczenia dotyczące współpracy | Wybierz dowolną z tych opcji: <ul><li>W przypadku wybrania **opcji Zezwalaj na wysyłane** zaproszenia do dowolnej domeny (najbardziej integracyjnej) nie jest wymagana żadna inna konfiguracja.</li><li>Jeśli wybierzesz **pozycję Odmów** zaproszeń do określonych domen, upewnij się, Microsoft.com, że nie ma jej na liście w domenach docelowych.</li><li>Jeśli wybierzesz **opcję Zezwalaj** na zaproszenia tylko do określonych domen (najbardziej restrykcyjne), upewnij się, że Microsoft.com *jest* wymieniona w domenach docelowych.</li><ul>

W przypadku ustawienia ograniczeń dotyczących interakcji z tymi ustawieniami upewnij się, że nie są Azure Active Directory **kont usługi Nowoczesne miejsce pracy**. Jeśli na przykład masz zasady dostępu warunkowego uniemożliwiające kontom gości uzyskiwanie dostępu do portalu Intune, z tych zasad wyłącz grupę Kont usługi **Nowoczesne miejsce** pracy.

Aby uzyskać więcej informacji, zobacz [Włączanie współpracy zewnętrznej B2B i zarządzanie tym, kto może zapraszać gości](/azure/active-directory/external-identities/delegate-invitations#to-configure-external-collaboration-settings).

## <a name="unlicensed-intune-admin"></a>Nielicencjonowany administrator usługi Intune

Musi **być włączone ustawienie Zezwalaj na dostęp do nielicencjonowanych** administratorów. Bez tego ustawienia włączonego mogą wystąpić błędy podczas próby uzyskania dostępu do twojej organizacji usługi Azure AD w celu uzyskania dostępu do usługi. Możesz bezpiecznie włączyć to ustawienie bez obaw o wpływ na bezpieczeństwo. Zakres dostępu jest zdefiniowany przez role przypisane użytkownikom, w tym naszemu personelowi operacyjnemu.

**Aby włączyć to ustawienie:**

1. Przejdź do Microsoft Endpoint Manager [administracyjnego](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Przejdź do **administracji dzierżawy** i wybierz pozycję **Role**. Następnie wybierz pozycję **Licencjonowanie administratora**.
3. W sekcji **Zezwalaj na dostęp nielicencjonowanych administratorów** wybierz pozycję **Tak**.

> [!IMPORTANT]
> Po wybraniu przycisku Tak nie można cofnąć tego **ustawienia**.

Aby uzyskać więcej informacji, zobacz [Nielicencjonowani administratorzy w programie Microsoft Intune](/mem/intune/fundamentals/unlicensed-admins).

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Procedura przygotuj się do Microsoft Managed Desktop

1. Przejrzyj [wymagania wstępne dotyczące Microsoft Managed Desktop](prerequisites.md).
1. Uruchom [narzędzia do oceny gotowości](readiness-assessment-tool.md).
1. Kup [Portal firmy](../get-started/company-portal.md).
1. Przejrzyj wymagania wstępne dotyczące kont gości (ten artykuł).
1. Sprawdź [konfigurację sieci](network.md).
1. [Przygotowywanie certyfikatów i profilów sieci](certs-wifi-lan.md).
1. [Przygotowywanie dostępu użytkownika do danych](authentication.md).
1. [Przygotowywanie aplikacji](apps.md).
1. [Przygotowywanie zamapowanych dysków](mapped-drives.md).
1. [Przygotowywanie zasobów do drukowania](printing.md).
1. Nazwy [urządzeń adresowych](address-device-names.md).
