---
title: Konfigurowanie mobilności podstawowej i zabezpieczeń
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
description: Skonfiguruj pakiet Basic Mobility and Security, aby zabezpieczyć urządzenia przenośne twoich użytkowników i zarządzać nimi, wykonując czynności, takie jak zdalne wymywanie urządzenia.
ms.openlocfilehash: bbf7cf84dd996a0e548a76978e8fbba58f40c070
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983933"
---
# <a name="set-up-basic-mobility-and-security"></a>Konfigurowanie mobilności podstawowej i zabezpieczeń

Wbudowany pakiet Basic Mobility and Security for Microsoft 365 ułatwia zabezpieczanie urządzeń przenośnych użytkowników, takich jak telefony iPhone, tablety iPad, telefony z systemem Android Windows i zarządzanie nimi. Możesz tworzyć zasady zabezpieczeń urządzeń i zarządzać nimi, zdalnie wyczyścić urządzenie i wyświetlać szczegółowe raporty dotyczące urządzeń.

Masz pytania? Aby uzyskać odpowiedzi na często zadawane pytania, zobacz Podstawowa [mobilność](frequently-asked-questions.yml) i zabezpieczenia — często zadawane pytania. Należy pamiętać, że do zarządzania pakietem Basic Mobility and Security nie można używać konta administratora delegowanego. Aby uzyskać więcej informacji, zobacz [Partnerzy: oferuj administrację delegowaną](https://support.microsoft.com/office/partners-offer-delegated-administration-26530dc0-ebba-415b-86b1-b55bc06b073e). 

Zarządzanie urządzeniami jest częścią Centrum zabezpieczeń & zgodności, więc musisz tam wystartować z konfiguracją mobilności podstawowej i zabezpieczeń.

## <a name="activate-the-basic-mobility-and-security-service"></a>Aktywowanie usługi Basic Mobility and Security

1. Zaloguj się w Microsoft 365 konta administratora globalnego.

2. Przejdź do [aktywowania pakietu Basic Mobility and Security](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx).

   Aktywowanie pakietu Basic Mobility and Security może zająć trochę czasu. Po zakończeniu otrzymasz wiadomość e-mail z wyjaśnieniem, jakie należy wykonać.

## <a name="set-up-mobile-device-management"></a>Konfigurowanie zarządzania urządzeniami przenośnymi

Gdy usługa będzie gotowa, wykonaj następujące czynności, aby zakończyć konfigurację.

### <a name="step-1-required-configure-domains-for-basic-mobility-and-security"></a>Krok 1. (Wymagane) Konfigurowanie domen na potrzeby mobilności podstawowej i zabezpieczeń

Jeśli z usługą Microsoft 365 nie jest skojarzona domena niestandardowa lub nie zarządzasz urządzeniami Windows, możesz pominąć tę sekcję. W przeciwnym razie musisz dodać rekordy DNS dla domeny u swojego hosta DNS. Jeśli rekordy zostały już dodane w ramach konfigurowania domeny u rejestratora domen Microsoft 365, wszystko jest już tak ustawione. Po dodaniu rekordów użytkownicy Microsoft 365 w organizacji, którzy zalogują się na swoich urządzeniach z systemem Windows za pomocą adresu e-mail, w którym jest używana domena niestandardowa, są przekierowywani w celu zarejestrowania się w programie Basic Mobility and Security.

Potrzebujesz pomocy przy konfigurowaniu rekordów? Znajdź rejestratora domen i wybierz nazwę rejestratora, aby przejść do pomocy krok po kroku dotyczącej tworzenia rekordu DNS na liście dostępnej w te sposóbDadowanie rekordów DNS w celu połączenia  [Twojej domeny](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider). Skorzystaj z tych instrukcji, aby utworzyć rekordy CNAME opisane Windows [bez Azure AD — wersja Premium](/mem/intune/enrollment/windows-enroll#simplify-windows-enrollment-without-azure-ad-premium).

Po dodaniu tych dwóch rekordów CNAME wróć do Centrum & zabezpieczeń i przejdź do tematu **Ochrona** >   przed utratą danychArządznie urządzeniami, aby wykonać następny krok.

### <a name="step-2-required-configure-an-apns-certificate-for-ios-devices"></a>Krok 2. (Wymagane) Konfigurowanie certyfikatu usługi APN dla urządzeń z systemem iOS

Aby zarządzać urządzeniami z systemem iOS, iPad telefonami iPhone, musisz utworzyć certyfikat usługi APN.

1. Zaloguj się w Microsoft 365 konta administratora globalnego.

2. W przeglądarce wpisz: [https://protection.office.com](https://protection.office.com/).

3. Wybierz  **pozycję Zapobieganie utracie**  **danychZarządzajanie** > i wybierz pozycję Certyfikat **usługi APN dla urządzeń z systemem iOS**.

4. Na stronie certyfikatu powiadomień push firmy Apple Ustawienia wybierz  **pozycjęNext**.

5. Wybierz  **pozycjęPobierz plik CSR**  i zapisz żądanie podpisania certyfikatu w miejscu na komputerze, które zapamiętasz. Wybierz  **pozycjęNastępny**.

6. Na stronie Tworzenie certyfikatu usługi APN:

   - Wybierz pozycję Portal Apple APNS, aby otworzyć portal certyfikatów Push firmy Apple.
   - Zaloguj się przy użyciu identyfikatora Apple ID.

     > [!IMPORTANT]
     > Użyj firmowego identyfikatora Apple skojarzonego z kontem e-mail, który pozostanie w Twojej organizacji, nawet jeśli opuści go użytkownik, który nim zarządza. Zapisz ten identyfikator, ponieważ będzie konieczne użycie tego samego identyfikatora przy odnawianiu certyfikatu.

   - Wybierz pozycję Utwórz certyfikat i zaakceptuj warunki użytkowania.
   - Przejdź do żądania podpisania certyfikatu, które zostało pobrane na komputer z witryny Microsoft 365 wybierz pozycjęUpload.
   - Pobierz na komputer certyfikat usługi APN utworzony w portalu certyfikatów Push firmy Apple.

     > [!TIP]
     > Jeśli masz problem z pobraniem certyfikatu, odśwież przeglądarkę.

7. Wróć do Microsoft 365 i wybierz pozycję **Dalej**.

8. Przejdź do certyfikatu usługi APN pobranego z portalu certyfikatów Push firmy Apple.

9. Wybierz   **pozycjęFinisz**.

### <a name="step-3-recommended-set-up-multi-factor-authentication"></a>Krok 3. (Zalecane) Konfigurowanie uwierzytelniania wieloskładnikowego

Uwierzytelnianie MFA pomaga zabezpieczyć logowanie do aplikacji Microsoft 365 do rejestracji urządzenia przenośnego, wymagając drugiej formy uwierzytelniania. Użytkownicy muszą potwierdzić połączenie telefoniczne, wiadomość SMS lub powiadomienie aplikacji na swoich urządzeniach przenośnych po prawidłowym wprowadzeniu hasła do konta służbowego. Mogą oni zarejestrować swoje urządzenie dopiero po zakończeniu drugiej formy uwierzytelniania. Po zarejestrowaniu urządzeń użytkowników w pakietach Basic Mobility and Security użytkownicy mogą uzyskać dostęp do Microsoft 365, tylko za pomocą konta służbowego.

Aby dowiedzieć się, jak włączyć uwierzytelnianie MFA w portalu usługi Azure AD, zobacz  [Jak skonfigurować uwierzytelnianie wieloskładnikowe](../security-and-compliance/set-up-multi-factor-authentication.md).

Po skonfigurowaniu uwierzytelniania wieloskładnikowego ****   **** > > wróć do Centrum & zgodności zabezpieczeń i przejdź do tematu Ochrona przed utratą danychZarządzajanie urządzeniami, aby wykonać następny krok.

### <a name="step-4-recommended-manage-device-security-policies"></a>Krok 4. (Zalecane) Zarządzanie zasadami zabezpieczeń urządzeń

Następnym krokiem jest utworzenie i wdrożenie zasad zabezpieczeń urządzeń w celu ochrony danych Microsoft 365 organizacji. Na przykład możesz zapobiec utracie danych, jeśli użytkownik utraci swoje urządzenie, tworząc zasady blokowania urządzeń po pięciu minutach braku aktywności i czyszczenia urządzeń po trzech niepowodzeniach logowania.

1. Zaloguj się w Microsoft 365 konta administratora globalnego.

2. Wybierz  [pozycję Aktywuj zarządzanie urządzeniami przenośnymi](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx). Jeśli usługa zostanie aktywowana, zamiast tego w krokach aktywacji będzie wyświetlony link Do  [tematuUzywana obsługa urządzeń](https://admin.microsoft.com/adminportal/home#/MifoDevices) .

3. Przejdź do  **zasad programuDevice**.

   :::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Ustawienia podstawowych zasad zabezpieczeń i mobilności.":::

4. Utwórz i wdaj zasady zabezpieczeń urządzeń odpowiednie dla Twojej organizacji, zgodnie z instrukcjami w tworzenie zasad zabezpieczeń urządzeń w mobilności  [podstawowej i zabezpieczeniach](create-device-security-policies.md).

> [!TIP]
>
> - Podczas tworzenia nowych zasad można skonfigurować zasady umożliwiające uzyskiwanie dostępu i zgłaszanie naruszenia zasad, gdy urządzenie użytkownika jest z nich niezgodne. Dzięki temu możesz zobaczyć, na ile urządzeń przenośnych mają wpływ zasady, bez blokowania dostępu do Microsoft 365.
>
> - Przed wdrożeniem nowych zasad dla wszystkich osób w organizacji zalecamy przetestowanie ich na urządzeniach używanych przez małą liczbę użytkowników.
>
> - Ponadto przed wdrożeniem zasad poukaj swoją organizację o potencjalnych skutkach zarejestrowania urządzenia w pakietach Basic Mobility and Security. W zależności od sposobu skonfigurowania zasad urządzenia, które nie są zgodne z zasadami (niezgodne urządzenia), mogą mieć zablokowaną dostęp do Microsoft 365. Niezgodne urządzenia mogą również mieć zainstalowane aplikacje, zdjęcia i inne informacje osobiste, które na zarejestrowanym urządzeniu mogą zostać usunięte w razie wyczyszczenia urządzenia. Aby uzyskać więcej informacji, zobacz [Czyszczenie urządzenia przenośnego w pakietach Basic Mobility and Security](wipe-mobile-device.md).

## <a name="make-sure-users-enroll-their-devices"></a>Upewnij się, że użytkownicy zarejestrują swoje urządzenia

Po utworzeniu i wdrożeniu zasad zarządzania urządzeniami przenośnymi każdy licencjonowany użytkownik usługi Microsoft 365 w organizacji, do których mają zastosowanie zasady dotyczące urządzenia, otrzyma wiadomość o rejestracji, gdy następnym razem zaloguje się do usługi Microsoft 365 na swoim urządzeniu przenośnym. Aby uzyskać dostęp do poczty e-mail i dokumentów, muszą oni wykonać kroki rejestracji Microsoft 365 aktywacji. Aby uzyskać więcej informacji, zobacz [Rejestrowanie urządzenia przenośnego za pomocą platformy Basic Mobility and Security](enroll-your-mobile-device.md).

> [!IMPORTANT]
> Jeśli preferowany język użytkownika nie jest obsługiwany przez proces rejestracji, może on otrzymać powiadomienie o rejestracji i czynności do ich obsługi na jego urządzeniach przenośnych w innym języku. Nie wszystkie języki obsługiwane w aplikacji Microsoft 365 są obecnie obsługiwane w procesie rejestracji na urządzeniach przenośnych.

Użytkownicy urządzeń z systemem Android lub iOS muszą zainstalować aplikację Portal firmy w ramach procesu rejestracji.

## <a name="related-content"></a>Zawartość pokrewna

[Możliwości pakietu Basic Mobility and Security](capabilities.md) (artykuł)\
[Tworzenie zasad zabezpieczeń urządzeń w mobilności podstawowej i zabezpieczeniach](create-device-security-policies.md) (artykuł)