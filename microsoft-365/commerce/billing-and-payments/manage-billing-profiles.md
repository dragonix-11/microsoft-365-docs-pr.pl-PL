---
title: Opis profilów rozliczeniowych
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: jkinma, jmueller
audience: Admin
ms.topic: article
f1.keywords:
- MACBillingBillsPaymentsBillingProfiles
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_billing
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid: MET150
description: Dowiedz się, jak profile rozliczeniowe obsługują faktury.
ms.date: 04/02/2021
ms.openlocfilehash: 472b5c4754d686877077133467e33592b5c0b85e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63311871"
---
# <a name="understand-billing-profiles"></a>Opis profilów rozliczeniowych

Profil rozliczeniowy zawiera metodę płatności, informacje o fakturze i inne ustawienia faktury, takie jak numer zamówienia zakupu i preferencja faktury e-mail. Za pomocą profilu rozliczeniowego płacisz za produkty kupowane od firmy Microsoft. Profil rozliczeniowy jest tworzony automatycznie, gdy użytkownik dokonuje zakupu samoobsługowego. Każdy profil rozliczeniowy jest fakturowany oddzielnie.

> [!NOTE]
>
> Profile rozliczeniowe nie są dostępne dla klientów, którzy kupują produkty i usługi w Microsoft.com  lub na stronie Zakup usług w centrum administracyjne platformy Microsoft 365.

## <a name="what-are-billing-profile-roles"></a>Co to są role w profilu rozliczeniowym?

Role w profilach rozliczeniowych mają uprawnienia do kontrolowania zakupów oraz wyświetlania faktur i zarządzania nimi. Przypisz te role użytkownikom, którzy będą śledzić, organizować i opłacać faktury. Na przykład członkowie zespołu zaopatrzenia w organizacji.

| Rola                         | Opis                                                                      |
|----------------------------- |--------------------------------------------------------------------------------- |
| Właściciel profilu rozliczeniowego        | Zarządzanie wszystkimi danymi profilu rozliczeniowego                                          |
| Współautor profilu rozliczeniowego  | Zarządzanie wszystkim z wyjątkiem uprawnień w profilu rozliczeniowym                        |
| Czytnik profilu rozliczeniowego       | Widok tylko do odczytu wszystkich danych w profilu rozliczeniowym                                |
| Menedżer ds. faktur              | Wyświetlanie i opłacanie rachunków oraz wyświetlanie wszystkich danych w profilu rozliczeniowym w widoku tylko do odczytu  |

## <a name="view-my-billing-profiles"></a>Wyświetl moje profile rozliczeniowe

> [!NOTE]
>
> Jeśli posuniesz te czynności, a lista profilów rozliczeń będzie pusta, oznacza to, że nie masz profilu rozliczeniowego i nie możesz korzystać z tej funkcji.

1. W centrum administracyjnym przejdź do strony **Rachunki** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">Rachunki i płatności</a>.
2. Wybierz **kartę Profil rozliczeniowy** , a następnie wybierz z listy profil rozliczeniowy.

Każdy profil rozliczeniowy zawiera następujące informacje:

- **Nazwa i stan profilu rozliczeniowego** &ndash; Unikatowa nazwa profilu rozliczeniowego oraz informacje o tym, czy profil rozliczeniowy jest aktywny, czy wyłączony na zakupy.
- **Ustawienia faktury** &ndash; Waluta oparta na kraju konta rozliczeniowego, informacje o częstotliwości i dacie faktury, opcja otrzymywania faktur jako załączników wiadomości e-mail oraz opcjonalne pole numeru zakupu
- **Metody płatności** &ndash; Pokazuje podstawową i zapasową formę płatności (jeśli jest ona wieje) dla profilu
- **Konto rozliczeniowe** &ndash; Nazwa konta rozliczeniowego, z które jest powiązany profil. Aby uzyskać więcej informacji o kontach rozliczeniowych, zobacz [Opis kont rozliczeniowych](../manage-billing-accounts.md).
- **Informacje kontaktowe** &ndash; Adres rozliczeniowy, nazwa kontaktu i adres e-mail
- **Role w profilu rozliczeniowym** &ndash; Lista osób, do których przypisano jedną z ról profilu rozliczeniowego, aby wykonać czynności dla tego profilu. Na przykład zapłać rachunki, dodaj numer zamówienia zakupu lub zastąp metodę płatności używaną do zakupów.

> [!NOTE]
>
> Role profilu rozliczeniowego możesz przypisywać tylko użytkownikom w Twojej organizacji.

## <a name="need-help-contact-support"></a>Potrzebujesz pomocy? Kontakt z pomocą techniczną

Jeśli masz pytania lub potrzebujesz pomocy dotyczącej opłat za korzystanie z systemu Azure, utwórz zgłoszenie do pomocy <a href="https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest" target="_blank">technicznej za pomocą pomocy technicznej azure</a>.

Jeśli masz pytania lub potrzebujesz pomocy dotyczącej profilu rozliczeniowego w aplikacji centrum administracyjne platformy Microsoft 365, [skontaktuj się z pomocą techniczną](../../admin/get-help-support.md).

## <a name="related-content"></a>Zawartość pokrewna

[Jak zapłacić za subskrypcję za pomocą profilu rozliczeniowego](pay-for-subscription-billing-profile.md) (artykuł)\
[Opis kont rozliczeniowych](../manage-billing-accounts.md) (artykuł)\
[Zarządzanie metodami płatności](manage-payment-methods.md) (artykuł)
