---
title: Rozwiązywanie problemów z usługą Basic Mobility and Security
f1.keywords: NOCSH
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
ms.custom: AdminSurgePortfolio
description: Wypróbuj te kroki, aby śledzić problemy z mobilnością w warstwie Podstawowa i zabezpieczeniami
ms.openlocfilehash: c8c4fe674ff3a803659223a004e304a5779a83d7
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780742"
---
# <a name="troubleshoot-basic-mobility-and-security"></a>Rozwiązywanie problemów z usługą Basic Mobility and Security

Jeśli podczas próby zarejestrowania urządzenia w usłudze Basic Mobility and Security występują problemy, spróbuj wykonać kroki opisane tutaj, aby wytropić problem. Jeśli ogólne kroki nie rozwiążą problemu, zobacz jedną z kolejnych sekcji z określonymi krokami dotyczącymi typu urządzenia.

## <a name="steps-to-try-first"></a>Kroki, które należy wykonać w pierwszej kolejności

Aby rozpocząć, sprawdź następujące kwestie:

- Upewnij się, że urządzenie nie zostało jeszcze zarejestrowane u innego dostawcy zarządzania urządzeniami przenośnymi, takiego jak Intune.

- Upewnij się, że urządzenie jest ustawione na poprawną datę i godzinę.

- Przełącz się do innej sieci WI-FI lub sieci komórkowej na urządzeniu.

- W przypadku urządzeń z systemem Android lub iOS odinstaluj i ponownie zainstaluj aplikację Intune — Portal firmy na urządzeniu. 

## <a name="ios-phone-or-tablet"></a>Telefon lub tablet z systemem iOS

- Upewnij się, że skonfigurowano certyfikat usługi APNs. Aby uzyskać więcej informacji, zobacz [Tworzenie certyfikatu usługi APNs dla urządzeń z systemem iOS](create-an-apns-certificate-for-ios-devices.md).

- W **Ustawienia** >  **GeneralProfile** >  **(lub Zarządzanie urządzeniami)** upewnij się, że profil zarządzania nie jest jeszcze zainstalowany. Jeśli tak jest, usuń go.

- Jeśli zostanie wyświetlony komunikat o błędzie "Nie można zarejestrować urządzenia", zaloguj się do Microsoft 365 i upewnij się, że licencja zawierająca Exchange Online została przypisana do użytkownika zalogowanego na urządzeniu.

- Jeśli zostanie wyświetlony komunikat o błędzie "Nie można zainstalować profilu", spróbuj wykonać jedną z następujących czynności:

    - Upewnij się, że przeglądarka Safari jest domyślną przeglądarką na urządzeniu i że pliki cookie nie są wyłączone.

    - Uruchom ponownie urządzenie, a następnie przejdź do portal.manage.microsoft.com. Zaloguj się przy użyciu Microsoft 365 identyfikatora użytkownika i hasła oraz spróbuj zainstalować profil ręcznie.

## <a name="windows-rt"></a>Windows RT

- Upewnij się, że domena została skonfigurowana w Microsoft 365 do pracy z usługą Basic Mobility and Security. Aby uzyskać więcej informacji, zobacz [Konfigurowanie pakietu Basic Mobility and Security](set-up.md).
    
- Upewnij się, że użytkownik wybiera opcję **Włącz** zamiast wybierać pozycję **Dołącz**.

## <a name="windows-10-pc"></a>komputer Windows 10

- Upewnij się, że domena została skonfigurowana w Microsoft 365 do pracy z usługą Basic Mobility and Security. Aby uzyskać więcej informacji, zobacz [Konfigurowanie pakietu Basic Mobility and Security](set-up.md).
    
- Jeśli nie masz Azure Active Directory — wersja Premium, upewnij się, że użytkownik wybiera pozycję **Zarejestruj tylko w Zarządzanie urządzeniami** zamiast **wybierać Połączenie**.

## <a name="android-phone-or-tablet"></a>Telefon lub tablet z systemem Android

- Upewnij się, że na urządzeniu działa system Android.

- Upewnij się, że przeglądarka Chrome jest aktualna i jest ustawiona jako przeglądarka domyślna.

- Jeśli zostanie wyświetlony komunikat o błędzie "Nie można zarejestrować tego urządzenia", zaloguj się do Microsoft 365 i upewnij się, że licencja zawierająca Exchange Online została przypisana do użytkownika zalogowanego na urządzeniu.

- Sprawdź obszar powiadomień na urządzeniu, aby sprawdzić, czy wymagane akcje użytkownika końcowego są oczekujące, a jeśli są, wykonaj akcje.