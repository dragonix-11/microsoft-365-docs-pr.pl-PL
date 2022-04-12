---
title: Skonfiguruj funkcję Podstawowa mobilność i zabezpieczenia
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
description: Skonfiguruj usługę Basic Mobility and Security, aby zabezpieczyć urządzenia przenośne użytkowników i zarządzać nimi, wykonując akcje, takie jak zdalne czyszczenie urządzenia.
ms.openlocfilehash: b26906c0f374f5dc103fe26e4619663195da6ebd
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780836"
---
# <a name="set-up-basic-mobility-and-security"></a>Skonfiguruj funkcję Podstawowa mobilność i zabezpieczenia

Wbudowana usługa Basic Mobility and Security for Microsoft 365 ułatwia zabezpieczanie urządzeń przenośnych użytkowników, takich jak telefony iPhone, iPady, androidy i telefony Windows, oraz zarządzanie nimi. Możesz tworzyć zasady zabezpieczeń urządzeń i zarządzać nimi, zdalnie czyścić urządzenie oraz wyświetlać szczegółowe raporty dotyczące urządzeń.

Masz pytania? Aby uzyskać często zadawane pytania ułatwiające odpowiedzi na typowe pytania, zobacz [Basic Mobility and Security Frequently asked Questions (Często zadawane pytania) w temacie Basic Mobility and Security Frequently asked Questions (Często zadawane pytania).](frequently-asked-questions.yml) Należy pamiętać, że do zarządzania usługą Basic Mobility and Security nie można użyć konta administratora delegowanego. Aby uzyskać więcej informacji, zobacz [Partners: Offer delegated administration (Partnerzy: delegowanie oferty).](https://support.microsoft.com/office/partners-offer-delegated-administration-26530dc0-ebba-415b-86b1-b55bc06b073e) 

Zarządzanie urządzeniami jest częścią Centrum zgodności & zabezpieczeń, więc musisz tam przejść, aby rozpocząć konfigurację usługi Basic Mobility and Security.

## <a name="activate-the-basic-mobility-and-security-service"></a>Aktywowanie usługi Basic Mobility and Security

1. Zaloguj się do Microsoft 365 przy użyciu konta administratora globalnego.

2. Przejdź do [pozycji Aktywuj podstawową mobilność i zabezpieczenia](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx).

   Aktywowanie pakietu Basic Mobility and Security może zająć trochę czasu. Po zakończeniu otrzymasz wiadomość e-mail z wyjaśnieniem kolejnych kroków do wykonania.

## <a name="set-up-mobile-device-management"></a>Konfigurowanie usługi Mobile Zarządzanie urządzeniami

Gdy usługa jest gotowa, wykonaj następujące kroki, aby zakończyć konfigurację.

### <a name="step-1-required-configure-domains-for-basic-mobility-and-security"></a>Krok 1. (Wymagane) Konfigurowanie domen dla pakietu Basic Mobility and Security

Jeśli nie masz domeny niestandardowej skojarzonej z Microsoft 365 lub nie zarządzasz Windows urządzeniami, możesz pominąć tę sekcję. W przeciwnym razie należy dodać rekordy DNS dla domeny na hoście DNS. Jeśli rekordy zostały już dodane, w ramach konfigurowania domeny przy użyciu Microsoft 365 wszystko jest ustawione. Po dodaniu rekordów Microsoft 365 użytkowników w organizacji, którzy logują się na swoim urządzeniu Windows przy użyciu adresu e-mail korzystającego z domeny niestandardowej, są przekierowywani w celu zarejestrowania się w usłudze Basic Mobility and Security.

Potrzebujesz pomocy przy konfigurowaniu rekordów? Znajdź rejestratora domen i wybierz nazwę rejestratora, aby przejść do pomocy krok po kroku dotyczącej tworzenia rekordu DNS na liście dostępnej w [temacie Dodawanie rekordów DNS w celu nawiązania połączenia z domeną](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider). Użyj tych instrukcji, aby utworzyć rekordy CNAME opisane w [temacie Upraszczanie rejestracji Windows bez Azure AD — wersja Premium](/mem/intune/enrollment/windows-enroll#simplify-windows-enrollment-without-azure-ad-premium).

Po dodaniu dwóch rekordów CNAME wróć do Centrum zgodności & zabezpieczeń i przejdź do obszaru **Ochrona przed** >  utratą **danychZarządzanie urządzeniami** w celu wykonania następnego kroku.

### <a name="step-2-required-configure-an-apns-certificate-for-ios-devices"></a>Krok 2. (Wymagane) Konfigurowanie certyfikatu usługi APNs dla urządzeń z systemem iOS

Aby zarządzać urządzeniami z systemem iOS, takimi jak iPad i iPhone, musisz utworzyć certyfikat usługi APNs.

1. Zaloguj się do Microsoft 365 przy użyciu konta administratora globalnego.

2. W przeglądarce wpisz: [https://protection.office.com](https://protection.office.com/).

3. Wybierz pozycję **Ochrona przed utratą** >  **danychZarządzanie urządzeniami** i wybierz pozycję **Certyfikat APNs dla urządzeń z systemem iOS**.

4. Na stronie Apple Push Notification Certificate Ustawienia wybierz pozycję **Dalej**.

5. Wybierz pozycję **Pobierz plik CSR** i zapisz żądanie podpisania certyfikatu w dowolnym miejscu na komputerze, który zapamiętasz. Wybierz pozycję **Dalej**.

6. Na stronie Tworzenie certyfikatu usługi APNs:

   - Wybierz pozycję Portal APNS firmy Apple, aby otworzyć portal Apple Push Certificates Portal.
   - Zaloguj się przy użyciu identyfikatora Apple ID.

     > [!IMPORTANT]
     > Użyj firmowego identyfikatora Apple ID skojarzonego z kontem e-mail, które pozostanie w Twojej organizacji, nawet jeśli użytkownik, który zarządza kontem, opuści konto. Zapisz ten identyfikator, ponieważ musisz użyć tego samego identyfikatora, gdy nadszedł czas na odnowienie certyfikatu.

   - Wybierz pozycję Utwórz certyfikat i zaakceptuj warunki użytkowania.
   - Przejdź do żądania podpisania certyfikatu pobranego na komputer z Microsoft 365 i wybierz pozycjęPrzeładuj.
   - Pobierz na komputer certyfikat APN utworzony przez portal certyfikatów wypychania firmy Apple.

     > [!TIP]
     > Jeśli masz problemy z pobraniem certyfikatu, odśwież przeglądarkę.

7. Wstecz do Microsoft 365 i wybierz przycisk **Dalej**.

8. Przejdź do certyfikatu APN pobranego z portalu apple push certificates.

9. Wybierz **Zakończ**.

### <a name="step-3-recommended-set-up-multi-factor-authentication"></a>Krok 3. (Zalecane) Konfigurowanie uwierzytelniania wieloskładnikowego

Uwierzytelnianie wieloskładnikowe pomaga zabezpieczyć logowanie do Microsoft 365 na potrzeby rejestracji urządzeń przenośnych, wymagając drugiej formy uwierzytelniania. Użytkownicy muszą potwierdzić połączenie telefoniczne, wiadomość SMS lub powiadomienie aplikacji na swoim urządzeniu przenośnym po poprawnym wprowadzeniu hasła konta służbowego. Mogą zarejestrować swoje urządzenie dopiero po ukończeniu tej drugiej formy uwierzytelniania. Po zarejestrowaniu urządzeń użytkowników w usłudze Basic Mobility and Security użytkownicy mogą uzyskiwać dostęp Microsoft 365 zasobów tylko przy użyciu konta służbowego.

Aby dowiedzieć się, jak włączyć uwierzytelnianie wieloskładnikowe w portalu usługi Azure AD, zobacz [Konfigurowanie uwierzytelniania wieloskładnikowego](../security-and-compliance/set-up-multi-factor-authentication.md).

Po skonfigurowaniu uwierzytelniania wieloskładnikowego wróć do Centrum zgodności & zabezpieczeń i przejdź do obszaru **Zapobieganie** >  **utracie danychZarządzanie** **urządzeniamiZasady** >  urządzeń, aby ukończyć następny krok.

### <a name="step-4-recommended-manage-device-security-policies"></a>Krok 4. (Zalecane) Zarządzanie zasadami zabezpieczeń urządzeń

Następnym krokiem jest utworzenie i wdrożenie zasad zabezpieczeń urządzeń w celu ochrony Microsoft 365 danych organizacji. Na przykład możesz zapobiec utracie danych, jeśli użytkownik utraci urządzenie, tworząc zasady blokowania urządzeń po pięciu minutach braku aktywności i czyszczenia urządzeń po trzech niepowodzeniach logowania.

1. Zaloguj się do Microsoft 365 przy użyciu konta administratora globalnego.

2. Wybierz pozycję [Aktywuj Zarządzanie urządzeniami mobilną](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx). Jeśli usługa zostanie aktywowana, zamiast kroków aktywacji zostanie wyświetlony link Do [zarządzania urządzeniami](https://admin.microsoft.com/adminportal/home#/MifoDevices) .

3. Przejdź do **pozycji Zasady urządzeń**.

   :::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Podstawowe ustawienia zasad zabezpieczeń i mobilności.":::

4. Utwórz i wdróż zasady zabezpieczeń urządzeń odpowiednie dla twojej organizacji, wykonując kroki opisane [w temacie Tworzenie zasad zabezpieczeń urządzeń w usłudze Basic Mobility and Security](create-device-security-policies.md).

> [!TIP]
>
> - Podczas tworzenia nowych zasad można ustawić zasady zezwalające na dostęp i zgłaszanie naruszeń zasad, gdy urządzenie użytkownika nie jest zgodne z zasadami. Dzięki temu można sprawdzić, na ile urządzeń przenośnych mają wpływ zasady bez blokowania dostępu do Microsoft 365.
>
> - Przed wdrożeniem nowych zasad dla wszystkich w organizacji zalecamy przetestowanie ich na urządzeniach używanych przez niewielką liczbę użytkowników.
>
> - Ponadto przed wdrożeniem zasad poinformuj organizację o potencjalnych skutkach rejestracji urządzenia w usłudze Basic Mobility and Security. W zależności od sposobu konfigurowania zasad dostęp urządzeń, które nie są zgodne z zasadami (niezgodnymi urządzeniami), może zostać zablokowany dostęp do Microsoft 365. Na niezgodnych urządzeniach mogą być również zainstalowane aplikacje, zdjęcia i inne dane osobowe, które na zarejestrowanym urządzeniu mogą zostać usunięte, jeśli urządzenie zostanie wyczyszczone. Aby uzyskać więcej informacji, zobacz [Czyszczenie urządzenia przenośnego w usłudze Basic Mobility and Security](wipe-mobile-device.md).

## <a name="make-sure-users-enroll-their-devices"></a>Upewnij się, że użytkownicy rejestrują swoje urządzenia

Po utworzeniu i wdrożeniu zasad zarządzania urządzeniami przenośnymi każdy licencjonowany Microsoft 365 użytkownika w organizacji, do których zostaną zastosowane zasady urządzenia, otrzyma komunikat o rejestracji przy następnym zalogowaniu się do Microsoft 365 z urządzenia przenośnego. Przed uzyskaniem dostępu do Microsoft 365 wiadomości e-mail i dokumentów muszą wykonać kroki rejestracji i aktywacji. Aby uzyskać więcej informacji, zobacz [Rejestrowanie urządzenia przenośnego przy użyciu pakietu Basic Mobility and Security](enroll-your-mobile-device.md).

> [!IMPORTANT]
> Jeśli preferowany język użytkownika nie jest obsługiwany przez proces rejestracji, użytkownicy mogą otrzymywać powiadomienia o rejestracji i kroki na swoich urządzeniach przenośnych w innym języku. Nie wszystkie języki obsługiwane w Microsoft 365 są obecnie obsługiwane w procesie rejestracji na urządzeniach przenośnych.

Użytkownicy urządzeń z systemem Android lub iOS muszą zainstalować aplikację Portal firmy w ramach procesu rejestracji.

## <a name="related-content"></a>Zawartość pokrewna

[Możliwości usługi Basic Mobility and Security](capabilities.md) (artykuł)\
[Tworzenie zasad zabezpieczeń urządzeń w usłudze Basic Mobility and Security](create-device-security-policies.md) (artykuł)
