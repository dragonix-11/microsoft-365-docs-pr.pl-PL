---
title: Opis rachunku lub faktury
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: jkinma, jmueller
audience: Admin
ms.topic: article
f1.keywords:
- MACBillingBillsPaymentsInvoices
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
description: Dowiedz się, jak odczytywać i interpretować rachunek lub fakturę za produkty biznesowe firmy Microsoft.
ms.date: 05/04/2021
ms.openlocfilehash: ce057a9a3fc72ab1ba818047112451f984894d99
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63315809"
---
# <a name="understand-your-bill-or-invoice"></a>Opis rachunku lub faktury

Faktura zawiera podsumowanie opłat i instrukcje dotyczące płatności. Możesz [wyświetlić fakturę online](#view-your-online-invoice) w centrum administracyjnym platformy Microsoft 365. Możesz również pobrać ją w formacie pdf (Portable Document Format), aby wysłać ją pocztą e-mail.

Aby wyświetlić i wydrukować fakturę:

1. Na stronie **Rozliczenia** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">Rachunki i płatności</a> wybierz zakres dat faktury.
2. Aby wydrukować lub zapisać kopię rachunku w formacie PDF, wybierz pozycję **Pobierz plik PDF faktury**, a następnie wydrukuj plik PDF.

Aby dowiedzieć się więcej, zobacz [Wyświetlanie rachunku lub faktury](view-your-bill-or-invoice.md).

Jeśli masz tylko subskrypcję platformy Microsoft 365, zobacz [Opis rachunku lub faktury za platformę Microsoft 365 dla firm](understand-your-invoice2.md).

## <a name="understand-the-invoice-header"></a>Omówienie nagłówka faktury

W górnej części pierwszej strony znajdują się informacje o tym, kto jest odpowiedzialny za płatność, gdzie jest wysyłany rachunek oraz podsumowanie opłat.

| Okres | Opis |
| --- | --- |
| Nabywca |Konto rozliczeniowe, które identyfikuje nazwę i adres osoby prawnej odpowiedzialnej za płatność. Tymi informacjami można zarządzać na stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=2084771" target="_blank">Konta rozliczeniowe</a>, gdzie możesz znaleźć umowę dotyczącą konta oraz zarządzać rolami i uprawnieniami. |
| Odbiorca faktury |Określa, kto otrzymuje fakturę. Tymi informacjami można zarządzać na stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=2103629" target="_blank">Profile rozliczeniowe</a>. Profil rozliczeniowy jest również wyświetlany na stronie faktury online w sekcji **Podsumowanie faktury**. Aby dowiedzieć się więcej o profilach rozliczeniowych i sposobie ich używania do tworzenia bardziej elastycznych opcji rozliczeń dla organizacji, zobacz [Zarządzane profilami rozliczeniowymi](manage-billing-profiles.md). |
| Profil rozliczeniowy |Nazwa profilu rozliczeniowego używanego do definiowania właściwości faktury, takich jak **Odbiorca faktury**, **Numer zamówienia zakupu** i warunki płatności. Tymi informacjami można zarządzać na stronie <a href="https://go.microsoft.com/fwlink/p/?linkid=2103629" target="_blank">Profile rozliczeniowe</a>. Aby uzyskać więcej informacji na temat profilów rozliczeniowych i sposobu ich używania do tworzenia bardziej elastycznych opcji rozliczeń dla organizacji, zobacz [Zarządzanie profilami rozliczeniowymi](manage-billing-profiles.md). |
| Numer faktury |Unikatowy, wygenerowany przez firmę Microsoft, numer faktury używany do celów śledzenia. |
| Data faktury |Data wygenerowania faktury, zazwyczaj od pięciu do 12 dni po zakończeniu cyklu rozliczeniowego. Datę faktury możesz sprawdzić na stronie szczegółów profilu rozliczeniowego. Opłaty występujące między końcem okresu rozliczeniowego a datą faktury są uwzględniane na fakturze za następny miesiąc, ponieważ należą one do następnego okresu rozliczeniowego. Daty rozpoczęcia i zakończenia okresu rozliczeniowego dla każdej faktury są wymienione w pliku PDF faktury powyżej pozycji **Podsumowanie rozliczeń**.|
| Warunki płatności |Jak opłacasz rachunek firmy Microsoft. *30 dni* oznacza, że płacisz zgodnie z instrukcjami na fakturze w ciągu 30 dni od daty wystawienia faktury. |

## <a name="understand-the-billing-summary"></a>Omówienie podsumowania rozliczeń

**Podsumowanie rozliczeń** pokazuje podsumowanie opłat od poprzedniego okresu rozliczeniowego, wszelkie zastosowane środki, podatek i łączną należną kwotę.

| Okres | Opis |
| --- | --- |
| Opłaty|Łączna liczba produktów zakupionych w tym okresie rozliczeniowym oraz powiązane z nimi opłaty i podatki. Zakupy są agregowane w celu zapewnienia zwięzłego widoku rachunku. |
| Środki |Środki otrzymane ze zwrotów |
| Zastosowane środki na platformie Azure |Środki na platformie Azure, które są automatycznie stosowane do opłat za platformę Azure w każdym okresie rozliczeniowym. Jeśli nie masz żadnych środków na platformie Azure, to pole jest ukryte. Aby uzyskać więcej informacji na temat środków na platformie Azure, zobacz [Śledzenie salda środków w ramach umowy klienta firmy Microsoft](/azure/billing/billing-mca-check-azure-credits-balance). |
| Suma częściowa |Należna kwota przed opodatkowaniem |
| Podatek |Typ i kwota podatku, który płacisz, w zależności od kraju profilu rozliczeniowego. Jeśli nie musisz płacić podatku, na fakturze nie jest wyświetlany żaden podatek. |

### <a name="understand-your-charges"></a>Informacje o opłatach

Na stronach opłat są wyświetlane koszty podzielone według produktu. W przypadku klientów platformy Azure opłaty mogą być uporządkowane według sekcji faktury. Aby uzyskać więcej informacji na temat sposobu używania sekcji faktur z produktami platformy Azure, zobacz [Sekcje faktur](/azure/billing/billing-mca-overview#invoice-sections) w artykule [Wprowadzenie do konta rozliczeniowego umowy klienta firmy Microsoft](/azure/billing/billing-mca-overview). W ramach każdego zamówienia produktu koszt jest dzielony według rodziny usług.

| Okres |Opis |
| --- | --- |
| Cena jednostkowa | Efektywna cena jednostkowa usługi (w walucie cenowej), która jest używana do obliczania opłaty. Ta cena jest unikatowa dla produktu, rodziny usług, miernika i oferty. |
| Ilość | Ilość zakupiona lub wykorzystana w okresie rozliczeniowym |
| Opłaty/środki | Kwota netto opłat po zastosowaniu środków/zwrotów |
| Środki na platformie Azure | Kwota środków na platformie Azure zastosowanych do opłat/środków |
| Stawka podatku | Stawka podatku w zależności od kraju |
| Kwota podatku | Kwota podatku zastosowana do zakupu na podstawie stawki podatku |
| Suma | Łączna kwota należności za zakup |

Szczegóły elementów wierszy różnią się w zależności od typu produktu, za który są naliczane opłaty. Na przykład w przypadku produktów platformy Azure jest wyświetlana kwota zastosowanych środków na platformie Azure. Produkty oparte na stanowiskach zawierają cenę jednostkową i ilość. Szczegóły faktury przedstawiają zakupione produkty, rabat lub środki, które zostały zastosowane, stawkę i kwotę podatku oraz sumy pozycji wierszy.

> Suma = opłaty - środki na platformie Azure + podatek

Łączna kwota należności dla każdej rodziny usług jest obliczana przez odjęcie środków na platformie Azure od środków/opłat i dodanie podatku:

> Suma = opłaty/środki — środki na platformie Azure + podatek

Jeśli na fakturze znajdują się opłaty za platformę Azure, o których chcesz uzyskać więcej informacji, zobacz [Przeglądanie faktury za umowę klienta firmy Microsoft](/azure/cost-management-billing/understand/review-customer-agreement-bill).

## <a name="understand-the-last-invoice-page"></a>Omówienie ostatniej strony faktury

### <a name="payment-instructions"></a>Instrukcje dotyczące płatności

U dołu faktury znajdują się instrukcje dotyczące sposobu płatności rachunku. Możesz płacić przelewem, czekiem lub online.

### <a name="publisher-information"></a>Informacje o wydawcy

Jeśli na rachunku znajdują się usługi innych firm, nazwa i adres każdego wystawcy są wyświetlane u dołu faktury.

## <a name="view-your-online-invoice"></a>Wyświetlanie faktury online

Faktury są dostępne online. Link do faktury online jest dostępny na fakturze w formacie PDF oraz w powiadomieniu e-mail. Fakturę online można rozszerzyć, aby wyświetlić opłaty na fakturze i zobaczyć więcej szczegółów o każdym elemencie. Faktura online obejmuje:

- **Szczegóły cennika**&mdash;Dodatkowe informacje, a w tym szczegółowe informacje o rabatach i cenach produktów.
- **Płatności online**&mdash;Z faktury możesz dokonać wyboru płatności online.
- **Zarządzanie kosztami platformy Azure**&mdash;W przypadku klientów platformy Azure faktury online zawierają link do zarządzania kosztami platformy Azure.

### <a name="to-view-your-online-invoice"></a>Aby wyświetlić fakturę online

1. W centrum administracyjnym przejdź do strony **Rachunki** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">Rachunki i płatności</a>.
2. Aby pobrać wersję PDF faktury, wybierz pozycję **Pobierz plik PDF faktury** w wierszu faktury, którą chcesz wyświetlić.
3. Aby wyświetlić fakturę online, wybierz fakturę z listy. Plik PDF można również pobrać ze strony szczegółów faktury.

## <a name="invoice-faq"></a>Faktura — często zadawane pytania

### <a name="when-is-my-invoice-available"></a>Kiedy moja faktura jest dostępna?

Niektóre faktury są generowane w ciągu 24 godzin od zakupu. Inne faktury są generowane na końcu okresu rozliczeniowego i obejmują wszystkie elementy z tego okresu.

### <a name="how-do-i-pay-the-amount-due-on-my-invoice"></a>Jak zapłacić należną kwotę na mojej fakturze?

Instrukcje dotyczące płatności zależą od metody płatności i są podane w dolnej części pliku PDF faktury. Jeśli Twoją metodą płatności jest karta kredytowa, zostanie ona automatycznie obciążona w ciągu 10 dni od daty wystawienia faktury. Jeśli metodą płatności jest czek lub przelew, zapoznaj się z informacjami w sekcji **Instrukcje płatności** w pliku PDF.

### <a name="whats-the-difference-between-sold-to-and-bill-to-addresses"></a>Jaka jest różnica między adresami w polach „Nabywca” i „Odbiorca faktury”?

- **Nabywca:** osoba prawna odpowiedzialna za płatność i wskazana na fakturze. Podany tutaj adres służy do określania stawki podatku, chyba że zdecydujesz się podać alternatywny adres wysyłkowy podczas zakupu. Aby uzyskać więcej informacji, zobacz [Informacje podatkowe](tax-information.md).
- **Odbiorca faktury:** Adres, na który jest wysyłana faktura fizyczna, jeśli ma to zastosowanie. Do każdej osoby prawnej można przypisać adresów **Odbiorca faktury**, ale tylko po jednym adresie **Odbiorca faktury** na profil rozliczeniowy.

### <a name="what-are-billed-amount-and-amount-due"></a>Co to są „Rozliczona kwota” i „Kwota należności”?

- **Rozliczona kwota:** Łączna kwota dokonanego zakupu.
- **Kwota należności:** Pozostałe saldo tego, co jest należne.

### <a name="what-is-the-difference-between-service-period-and-billing-period"></a>Jaka jest różnica między „Okresem świadczenia usługi” a „Okresem rozliczeniowym”?

- **Okres świadczenia usługi** Okres, w ramach którego są naliczane opłaty za korzystanie z usługi.
- **Okres rozliczeniowy:** Okres od daty wystawienia ostatniej faktury.

### <a name="why-dont-i-see-azure-prepayment-as-a-payment-method"></a>Dlaczego nie widzę przedpłaty na platformie Azure jako metody płatności?

Przedpłata na platformie Azure jest dostępna jako metoda płatności tylko dla kwalifikujących się produktów i usług platformy Azure

## <a name="need-help-contact-support"></a>Potrzebujesz pomocy? Kontakt z pomocą techniczną

Jeśli masz pytania lub potrzebujesz pomocy dotyczącej środków na platformie Azure, <a href="https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest" target="_blank">utwórz wniosek o pomoc techniczną do pomocy technicznej platformy Azure</a>.

Jeśli masz pytania lub potrzebujesz pomocy dotyczącej faktury w centrum administracyjnym platformy Microsoft 365, [skontaktuj się z pomocą techniczną dotyczącą produktów biznesowych](../../admin/get-help-support.md).

## <a name="related-content"></a>Zawartość pokrewna

[Opis rachunku lub faktury za platformę Microsoft 365 dla firm](understand-your-invoice2.md) (artykuł)\
[Śledzenie salda środków na platformie Azure za umowę klienta firmy Microsoft](/azure/billing/billing-mca-check-azure-credits-balance) (artykuł)\
[Przeglądanie faktury za umowę klienta firmy Microsoft](/azure/cost-management-billing/understand/review-customer-agreement-bill) (artykuł)\
[Wprowadzenie do konta rozliczeniowego umowy klienta firmy Microsoft](/azure/billing/billing-mca-overview) (artykuł)
