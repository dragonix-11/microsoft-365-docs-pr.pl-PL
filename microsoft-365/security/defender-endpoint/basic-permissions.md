---
title: Używanie podstawowych uprawnień w celu uzyskiwania dostępu do Centrum zabezpieczeń usługi Microsoft Defender
description: Dowiedz się, jak korzystać z podstawowych uprawnień w celu uzyskiwania dostępu do portalu programu Microsoft Defender dla punktu końcowego.
keywords: przypisywanie ról użytkowników, przypisywanie dostępu do odczytu i zapisu, przypisywanie dostępu tylko do odczytu, użytkownik, role użytkownika, role
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 27c480a0d4c95e79619e10f8fa42efb2c268b18c
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2021
ms.locfileid: "62996768"
---
# <a name="use-basic-permissions-to-access-the-portal"></a>Używanie podstawowych uprawnień w celu uzyskiwania dostępu do portalu

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- Azure Active Directory
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-basicaccess-abovefoldlink)

Skorzystaj z poniższych instrukcji, aby skorzystać z podstawowego zarządzania uprawnieniami.

Możesz użyć jednego z następujących rozwiązań:

- Azure PowerShell
- Azure Portal

Aby uzyskać szczegółową kontrolę nad uprawnieniami, [przełącz się na kontrolkę dostępu opartą na rolach](rbac.md).

## <a name="assign-user-access-using-azure-powershell"></a>Przypisywanie dostępu użytkownika przy użyciu Azure PowerShell

Możesz przypisywać użytkowników z jednym z następujących poziomów uprawnień:

- Pełny dostęp (odczyt i zapis)
- Dostęp tylko do odczytu

### <a name="before-you-begin"></a>Przed rozpoczęciem

- Instalowanie Azure PowerShell. Aby uzyskać więcej informacji, zobacz [Jak instalować i konfigurować Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/).

  > [!NOTE]
  > Należy uruchomić polecenia cmdlet programu PowerShell w wierszu polecenia z podwyższonym poziomem uprawnień.

- Połączenie do Azure Active Directory. Aby uzyskać więcej informacji, [zobacz Połączenie-MsolService](/powershell/module/msonline/connect-msolservice).

  - **Pełny dostęp**: Użytkownicy z pełnym dostępem mogą się logować, wyświetlać wszystkie informacje o systemie i rozwiązywać alerty, przesyłać pliki do szczegółowej analizy i pobierać pakiet dołączania. Przypisanie uprawnień pełnego dostępu wymaga dodania użytkowników do administratora zabezpieczeń lub administratora globalnego AAD wbudowanych ról.
  - **Dostęp tylko do odczytu**: Użytkownicy z dostępem tylko do odczytu mogą się logować, wyświetlać wszystkie alerty i informacje pokrewne.

    Nie będą mogli zmieniać stanów alertów, przesyłać plików do dogłębnej analizy ani wykonywać żadnych operacji zmiany stanu.

    Przypisanie praw dostępu tylko do odczytu wymaga dodania użytkowników do wbudowanej roli "Czytnik zabezpieczeń" usługi Azure AD.

Aby przypisać role zabezpieczeń, należy wykonać następujące czynności:

- Aby **uzyskać dostęp do odczytu i** zapisu, przypisz użytkowników do roli administratora zabezpieczeń, używając następującego polecenia:

  ```PowerShell
  Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress "secadmin@Contoso.onmicrosoft.com"
  ```

- Aby **uzyskać dostęp tylko** do odczytu, przypisz użytkowników do roli czytnika zabezpieczeń, używając następującego polecenia:

  ```PowerShell
  Add-MsolRoleMember -RoleName "Security Reader" -RoleMemberEmailAddress "reader@Contoso.onmicrosoft.com"
  ```

Aby uzyskać więcej informacji, zobacz [Dodawanie lub usuwanie członków grupy przy użyciu](/azure/active-directory/fundamentals/active-directory-groups-members-azure-portal) Azure Active Directory.

## <a name="assign-user-access-using-the-azure-portal"></a>Przypisywanie dostępu użytkowników za pomocą portalu Azure Portal

Aby uzyskać więcej informacji, zobacz [Przypisywanie ról administratora i innych użytkowników, którzy nie są administratorami, użytkownikom Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal).

## <a name="related-topic"></a>Temat pokrewny

- [Zarządzanie dostępem do portalu przy użyciu RBAC](rbac.md)
