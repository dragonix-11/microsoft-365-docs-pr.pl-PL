---
title: Przygotowywanie dostępu do zasobów lokalnych dla Microsoft Managed Desktop
description: Ważne kroki mające na celu zapewnienie, że usługa Azure AD może komunikować się z lokalną usługą AD w celu zapewnienia uwierzytelniania
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 3db3d469f7b417035e6ae11507c54c6bad871a89
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/10/2022
ms.locfileid: "63027104"
---
# <a name="prepare-on-premises-resources-access-for-microsoft-managed-desktop"></a>Przygotowywanie dostępu do zasobów lokalnych dla Microsoft Managed Desktop

W Microsoft Managed Desktop urządzenia są automatycznie dołączane do usługi Azure Active Directory (Azure AD). Z tego powodu, jeśli korzystasz z lokalnej usługi Active Directory, musisz upewnić się, że urządzenia przyłączone do usługi Azure AD mogą komunikować się z lokalną usługą Active Directory.

> [!NOTE]  
> *Hybrydowe* Dołączanie do usługi Azure AD nie jest obsługiwane przez Microsoft Managed Desktop.

Azure Active Directory umożliwia użytkownikom skorzystanie z Sign-On jednokrotnego (SSO). Logowanie pojedyncze oznacza, że zwykle nie będą one musiały poświadczeń po każdym użyciu zasobów.

Aby uzyskać informacje na temat dołączania Azure Active Directory, zobacz Jak [zaplanować implementację](/azure/active-directory/devices/azureadjoin-plan) dołączania do usługi Azure AD. Aby uzyskać podstawowe informacje na Sign-On logowania jednokrotnego na urządzeniach przyłącznych do usługi Azure AD, zobacz Jak działa logowanie jednokrotne do zasobów lokalnych na urządzeniach przyłącznych do usługi [Azure AD](/azure/active-directory/devices/azuread-join-sso#how-it-works).

W tym artykule wyjaśniono, co należy sprawdzić, aby zapewnić płynne działanie aplikacji i innych zasobów zależnych od lokalnej łączności z usługą Active Directory Microsoft Managed Desktop.

## <a name="single-sign-on-for-on-premises-resources"></a>Jeden Sign-On dla zasobów lokalnych

Funkcja Sign-On logowania jednokrotnego przy użyciu nazwy UPN i hasła jest domyślnie włączona na Microsoft Managed Desktop urządzeniach. Użytkownicy mogą jednak również korzystać z programu Windows Hello dla firm, co wymaga pewnych dodatkowych kroków konfiguracji.

### <a name="single-sign-on-by-using-upn-and-password"></a>Pojedyncze Sign-On przy użyciu nazwy UPN i hasła

W większości organizacji użytkownicy będą mogli używać logowania jednokrotnego do uwierzytelniania za pomocą nazwy UPN i hasła na Microsoft Managed Desktop urządzeniach. Aby upewnić się, że ta funkcja będzie działać, należy sprawdzić dwukrotnie następujące kwestie:

- Upewnij się, że usługa Azure AD Połączenie jest ustawiona. Musi ona korzystać z lokalnego serwera usługi Active Directory z Windows Server 2008 R2 lub nowszym.
- Upewnij się, że Połączenie usługi Azure AD dla sieci Połączenie jest uruchomiona obsługiwana wersja. Należy skonfigurować synchronizację tych trzech atrybutów z usługą Azure AD:
    - Nazwa domeny DNS lokalnej usługi Active Directory (w której znajdują się użytkownicy).
    - NetBIOS lokalnej usługi Active Directory (w której znajdują się użytkownicy).
    - Sam nazwa konta użytkownika.

### <a name="single-sign-on-by-using-windows-hello-for-business"></a>Pojedyncze Sign-On przy użyciu programu Windows Hello dla firm

Microsoft Managed Desktop zapewniają użytkownikom szybkie i mniej haseł środowisko dzięki Windows Hello dla firm. Aby upewnić się, że usługa Windows Hello dla firm będzie działać bez konieczności podania przez użytkowników odpowiedniej nazwy upn i hasła, odwiedź stronę Konfigurowanie urządzeń przyłącznych do usługi Azure AD dla lokalnego programu [Single-Sign W](/windows/security/identity-protection/hello-for-business/hello-hybrid-aadj-sso-base) przypadku używania programu Windows Hello dla firm w celu sprawdzenia wymagań, a następnie wykonaj podane tam instrukcje.

## <a name="apps-and-resources-that-use-authentication"></a>Aplikacje i zasoby, które korzystają z uwierzytelniania

Zobacz [Opis kwestii dotyczących aplikacji](/azure/active-directory/devices/azureadjoin-plan#understand-considerations-for-applications-and-resources) i zasobów w zestawie zawartości platformy Azure, aby uzyskać pełne wskazówki dotyczące konfigurowania aplikacji do współpracy z Azure Active Directory. Podsumowanie:

| Aplikacja lub usługa | Zadanie |
| ------ | ------ |
| Aplikacje oparte na chmurze | Jeśli korzystasz **z aplikacji** opartych na chmurze, takich jak te dodane do galerii aplikacji usługi Azure AD, większość z nich nie wymaga dodatkowego przygotowania się do współpracy z Microsoft Managed Desktop. Jednak wszystkie aplikacje systemu Win32, które nie używają Menedżera kont sieci Web (WAM), nadal mogą monitować użytkowników o uwierzytelnienie. |
| Aplikacje hostowane lokalnie | W przypadku aplikacji **hostowanych lokalnie** należy dodać je do listy zaufanych witryn w przeglądarkach. Ten krok umożliwi bezproblemowe Windows uwierzytelniania bez monitowania użytkowników o poświadczenia. Aby dodać aplikacje, zapoznaj się z [tematem Zaufane witryny](../working-with-managed-desktop/config-setting-ref.md#trusted-sites) w [tece Informacje dotyczące ustawień konfigurowalnych](../working-with-managed-desktop/config-setting-ref.md). |
| Usługi federowane Active Directory | Jeśli korzystasz z usług federowanych Active Directory, sprawdź, czy logowanie jednokrotne jest włączone, korzystając z procedury opisanej w tesłudze Weryfikowanie logowania jednokrotnego i zarządzanie nim za [pomocą usług AD FS](/previous-versions/azure/azure-services/jj151809(v=azure.100)). |
| Aplikacje lokalne korzystające ze starszych protokołów | W przypadku aplikacji lokalnych, które korzystają ze starszych protokołów **,** dodatkowa konfiguracja nie jest wymagana, o ile urządzenia mają dostęp do lokalnego kontrolera domeny w celu uwierzytelnienia. Jednak aby zapewnić bezpieczny dostęp do tych aplikacji, należy wdrożyć serwer proxy aplikacji Azure AD. Aby uzyskać więcej informacji, [zobacz Dostęp zdalny do aplikacji lokalnych za pośrednictwem Azure Active Directory proxy aplikacji firmy Windows](/azure/active-directory/manage-apps/application-proxy). |
| Aplikacje lokalne z uwierzytelnianiem maszynowego | Aplikacje uruchamiane lokalnie, które korzystają **z uwierzytelniania maszynowego** , nie są obsługiwane, dlatego warto rozważyć zamianę ich na nowsze wersje. |

### <a name="network-shares-that-use-authentication"></a>Udziały sieciowe, które korzystają z uwierzytelniania

Użytkownicy nie muszą nic więcej  konfigurować, aby uzyskać dostęp do udziałów sieciowych, o ile urządzenia mają dostęp do lokalnego kontrolera domeny przy użyciu ścieżki UNC.

### <a name="printers"></a>Drukarki

Microsoft Managed Desktop nie mogą łączyć się z drukarkami opublikowanymi w lokalnej usłudze Active Directory, chyba że skonfigurowano hybrydową usługę [Cloud Print](/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-deploy).

Mimo że drukarki nie mogą być automatycznie wykrywane tylko w środowisku w chmurze, użytkownicy mogą korzystać z drukarek lokalnych przy użyciu ścieżki drukarki lub ścieżki kolejki drukarek, o ile urządzenia mają dostęp do lokalnego kontrolera domeny.

<!--add fuller material on printers when available-->
## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Procedura przygotuj się do Microsoft Managed Desktop

1. Przejrzyj [wymagania wstępne dotyczące Microsoft Managed Desktop](prerequisites.md).
1. Uruchom [narzędzia do oceny gotowości](readiness-assessment-tool.md).
1. Kup [Portal firmy](../get-started/company-portal.md).
1. Przejrzyj [wymagania wstępne dotyczące kont gości](guest-accounts.md).
1. Sprawdź [konfigurację sieci](network.md).
1. [Przygotowywanie certyfikatów i profilów sieci](certs-wifi-lan.md).
1. Przygotowywanie dostępu użytkowników do danych (ten artykuł).
1. [Przygotowywanie aplikacji](apps.md).
1. [Przygotowywanie zamapowanych dysków](mapped-drives.md).
1. [Przygotowywanie zasobów do drukowania](printing.md).
1. Nazwy [urządzeń adresowych](address-device-names.md).
