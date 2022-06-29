---
title: Praca z grupami urządzeń w Microsoft 365 Business Premium
description: Dowiedz się więcej o grupach urządzeń i sposobie stosowania zasad przy użyciu Intune w Microsoft 365 Business Premium oraz zwiększ ochronę przed cyberatakami.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: a8d132669319e26adea53498e7dcf78a82a3250d
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66489731"
---
# <a name="device-groups-and-categories-in-microsoft-365-business-premium"></a>Grupy i kategorie urządzeń w Microsoft 365 Business Premium

Microsoft 365 Business Premium obejmuje ochronę punktów końcowych za pośrednictwem Microsoft Defender dla Firm i Microsoft Intune. Zasady ochrony urządzeń są stosowane do urządzeń za pośrednictwem niektórych kolekcji nazywanych grupami urządzeń. W Intune urządzenia są pogrupowane w kategorie urządzeń jako inny sposób ich organizowania. 

Ten artykuł zawiera następujące sekcje:  

- [Praca z grupami urządzeń](#working-with-device-groups)
- [Jak utworzyć nową grupę urządzeń](#create-a-device-group-in-the-microsoft-365-defender-portal)
- [Jak utworzyć nową kategorię urządzeń w Intune](#create-a-device-category-in-intune)

## <a name="working-with-device-groups"></a>Praca z grupami urządzeń

Grupa urządzeń to kolekcja urządzeń, które są pogrupowane ze względu na określone kryteria, takie jak wersja systemu operacyjnego. Urządzenia spełniające kryteria są uwzględniane w tej grupie urządzeń, chyba że zostaną wykluczone.

W przypadku Microsoft 365 Business Premium masz domyślne grupy urządzeń, których możesz użyć. Domyślne grupy urządzeń obejmują wszystkie urządzenia dołączone do usługi Defender dla Firm. Można jednak również utworzyć nowe grupy urządzeń w celu przypisania zasad ochrony urządzeń z określonymi ustawieniami do niektórych urządzeń.

Wszystkie grupy urządzeń, w tym domyślne grupy urządzeń i dowolne zdefiniowane niestandardowe grupy urządzeń, są przechowywane w [usłudze Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD).

## <a name="create-a-device-group-in-the-microsoft-365-defender-portal"></a>Tworzenie grupy urządzeń w portalu Microsoft 365 Defender

Podczas tworzenia lub edytowania zasad ochrony urządzeń można utworzyć nową grupę urządzeń.

1. Przejdź do [portalu Microsoft 365 Defender](https://security.microsoft.com) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Konfiguracja urządzenia**.

3. Wykonaj jedną z następujących akcji:

    1. Wybierz istniejące zasady, a następnie wybierz pozycję **Edytuj**.

    2. Wybierz **pozycję + Dodaj** , aby utworzyć nowe zasady.

    > [!TIP]
    > Aby uzyskać pomoc dotyczącą tworzenia lub edytowania zasad, zobacz [Wyświetlanie lub edytowanie zasad w Microsoft Defender dla Firm](m365bp-view-edit-create-mdb-policies.md).

4. W kroku **Informacje ogólne** przejrzyj informacje, w razie potrzeby edytuj, a następnie wybierz pozycję **Dalej**.

5. Wybierz **pozycję Utwórz nową grupę**.

6. Określ nazwę i opis grupy urządzeń, a następnie wybierz pozycję **Dalej**.

7. Wybierz urządzenia do uwzględnienia w grupie, a następnie wybierz pozycję **Utwórz grupę**.

8. W kroku **Grupy urządzeń** przejrzyj listę grup urządzeń dla zasad. W razie potrzeby usuń grupę z listy. Następnie wybierz pozycję **Dalej**.

9. Na stronie **Ustawienia konfiguracji** przejrzyj i edytuj ustawienia zgodnie z potrzebami, a następnie wybierz pozycję **Dalej**. Aby uzyskać więcej informacji na temat tych ustawień, zobacz [Omówienie ustawień konfiguracji nowej generacji w Microsoft Defender dla Firm](../security/defender-business/mdb-next-gen-configuration-settings.md).

10. W kroku **Przeglądanie zasad przejrzyj** wszystkie ustawienia, wprowadź wymagane zmiany, a następnie wybierz pozycję **Utwórz zasady** lub **Zaktualizuj zasady**.

## <a name="create-a-device-category-in-intune"></a>Tworzenie kategorii urządzenia w Intune

Utwórz kategorie urządzeń w Intune, z których użytkownicy muszą wybrać, kiedy zarejestrują urządzenie.

1. Zaloguj się do [centrum administracyjnego programu Microsoft Endpoint Manager](https://endpoint.microsoft.com).

2. Wybierz pozycję **Urządzenia** > **Kategorie** >  urządzeń **Utwórz kategorię urządzenia**, aby dodać nową kategorię.

3. W okienku **Tworzenie kategorii urządzenia** wprowadź nazwę nowej kategorii i opcjonalny opis.

4. Po zakończeniu wybierz pozycję **Utwórz**. Nowa kategoria jest widoczna na liście.

Użyj nazwy kategorii urządzenia podczas tworzenia grup zabezpieczeń usługi Azure Active Directory (Azure AD). Podczas rejestrowania urządzeń użytkownicy otrzymują listę kategorii skonfigurowanych w Intune. Po wybraniu kategorii i zakończeniu rejestracji urządzenie zostanie dodane do skojarzonej z nią grupy zabezpieczeń usługi Active Directory.

## <a name="create-dynamic-device-groups-in-azure-active-directory"></a>Tworzenie dynamicznych grup urządzeń w usłudze Azure Active Directory

Możesz również wprowadzić portal usługi Azure Active Directory (Azure AD) ([https://portal.azure.com](https://portal.azure.com)) z Centrum administracyjne platformy Microsoft 365. W Centrum administracyjne platformy Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com/)) wybierz pozycję **Wszystkie centra administracyjne**, a następnie wybierz pozycję **Azure Active Directory**.

W portalu Azure AD można tworzyć grupy dynamiczne na podstawie kategorii urządzenia i nazwy kategorii urządzenia. Użyj dynamicznych reguł grupy, aby automatycznie dodawać i usuwać urządzenia. Jeśli atrybuty urządzenia ulegną zmianie, system przyjrzy się dynamicznym regułom grupy katalogu, aby sprawdzić, czy urządzenie spełnia wymagania reguły (zostanie dodane) lub nie spełnia już wymagań dotyczących reguł (zostanie usunięte).

Możesz utworzyć grupę dynamiczną dla urządzeń lub użytkowników, ale nie dla obu tych urządzeń. Nie można również utworzyć grupy urządzeń na podstawie atrybutów właścicieli urządzeń. Reguły członkostwa urządzeń mogą odwoływać się tylko do przypisań urządzeń. 

## <a name="after-device-groups-are-created"></a>Po utworzeniu grup urządzeń

Teraz, gdy kategorie i grupy urządzeń zostały ustanowione, użytkownicy urządzeń z systemami iOS i Android rejestrują swoje urządzenia i w miarę ich wykonywania muszą wybrać kategorię z listy skonfigurowanych kategorii. Użytkownicy systemu Windows mogą wybrać kategorię za pomocą witryny internetowej Portal firmy lub aplikacji Portal firmy.

1. Po zarejestrowaniu urządzenia przejdź do [portalu firmy](https://portal.microsoft.com) i wybierz pozycję **Moje urządzenia**.

2. Wybierz zarejestrowane urządzenie z listy, a następnie wybierz kategorię.

Po wybraniu kategorii urządzenie zostanie automatycznie dodane do odpowiedniej grupy. Jeśli urządzenie zostało już zarejestrowane przed skonfigurowaniem kategorii, użytkownik zobaczy powiadomienie o urządzeniu w witrynie internetowej Portal firmy. Dzięki temu użytkownik może wybrać kategorię przy następnym dostępie do aplikacji Portal firmy w systemie iOS/iPadOS lub Android.

> [!NOTE]
> - Kategorię urządzenia można edytować w Azure Portal, ale należy ręcznie zaktualizować wszystkie Azure AD grupy zabezpieczeń odwołujące się do tej kategorii.
> - Jeśli usuniesz kategorię, urządzenia do niej przypisane będą wyświetlać nazwę kategorii **Nieprzypisane**.

## <a name="view-the-categories-of-devices-that-you-manage"></a>Wyświetlanie kategorii zarządzanych urządzeń

1. Zaloguj się do [centrum administracyjnego Endpoint Manager firmy Microsoft](https://endpoint.microsoft.com), wybierz pozycję **Urządzenia** > **Wszystkie urządzenia**.

2. Na liście urządzeń sprawdź kolumnę **Kategoria urządzenia** .

3. Jeśli kolumna Kategoria urządzenia nie jest wyświetlana, wybierz pozycję **Kolumny** > **Zastosuj kategorię** > .

## <a name="change-the-category-of-a-device"></a>Zmienianie kategorii urządzenia

1. Zaloguj się do [centrum administracyjnego Endpoint Manager firmy Microsoft](https://endpoint.microsoft.com), wybierz pozycję **Urządzenia** > **Wszystkie urządzenia**. 

2. Wybierz kategorię, którą chcesz wybrać z listy, aby wyświetlić jej właściwości.

## <a name="next-steps"></a>Następne kroki

Po ukończeniu podstawowych misji poświęć trochę czasu na skonfigurowanie [zespołów reagowania](m365bp-security-incident-management.md) i [utrzymanie środowiska](m365bp-maintain-environment.md).
