---
title: Szczególne zagadnienia dotyczące przesyłania strumienia i wydarzeń na żywo w środowiskach VPN
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: Szczególne zagadnienia dotyczące przesyłania strumienia i wydarzeń na żywo w środowiskach VPN
ms.openlocfilehash: eb2e57b844f06bc3b1e005aa1095794b176bba94
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63705260"
---
# <a name="special-considerations-for-stream-and-live-events-in-vpn-environments"></a>Szczególne zagadnienia dotyczące przesyłania strumienia i wydarzeń na żywo w środowiskach VPN

>[!NOTE]
>Ten artykuł jest częścią zestawu artykułów dotyczących optymalizacji Microsoft 365 zdalnych.

>- Aby uzyskać omówienie korzystania z rozdzielania dzielonego sieci VPN w celu zoptymalizowania Microsoft 365 dla użytkowników zdalnych, zobacz Omówienie: rozdzielanie sieci VPN dla sieci [Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Aby uzyskać szczegółowe wskazówki dotyczące implementowania rozdzielania sieci VPN, zobacz [Implementowanie](microsoft-365-vpn-implement-split-tunnel.md) rozdzielania sieci VPN na Microsoft 365.
>- Aby uzyskać szczegółową listę scenariuszy rozdzielania rozdzielania sieci VPN, zobacz Typowe scenariusze rozdzielania sieci [VPN dla sieci Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Aby uzyskać wskazówki dotyczące zabezpieczania Teams ruchu multimedialnego w środowiskach rozdzielanych sieci VPN, zobacz Zabezpieczanie sieci Teams sieci multimedialnej na Teams [sieci VPN](microsoft-365-vpn-securing-teams.md).
>- Aby uzyskać informacje na temat optymalizowania Microsoft 365 wydajności dzierżawy na całym świecie dla użytkowników w Chinach, zobacz Microsoft 365 [optymalizację wydajności dla użytkowników w Chinach](microsoft-365-networking-china.md).

Microsoft 365 w wydarzeniach na żywo (dotyczy Teams wydarzeń na żywo owanych przez uczestników, Teams także wydarzenia z zewnętrznym koderem za pośrednictwem usługi Teams, Stream lub Yammer), a ruch usługi Stream na żądanie jest obecnie kategoryzowany jako domyślny a optymalizowany na liście  adresów [URL/IP](urls-and-ip-address-ranges.md) usługi. Te punkty końcowe są kategoryzowane **jako** domyślne, ponieważ są hostowane w sieciach CDN, które mogą być również używane przez inne usługi. Klienci zazwyczaj preferują serwer proxy dla tego typu ruchu i stosują wszystkie elementy zabezpieczeń zwykle wykonywane w punktach końcowych, takich jak te.

Wielu klientów prosiło o dane adresów URL/IP potrzebne do połączenia ich użytkowników z usługą Stream/Live Events bezpośrednio z ich lokalnego połączenia internetowego, zamiast przekierowywał ruch o dużej pojemności i opóźnień za pośrednictwem infrastruktury VPN. Zazwyczaj nie jest to możliwe bez zarówno dedykowanych przestrzeni nazw, jak i dokładnych informacji o adresach IP dla punktów końcowych, które nie są dostępne dla punktów końcowych Microsoft 365 jako **domyślne**.

Aby włączyć łączność bezpośrednią usługi Stream/Live Events z klientami korzystającymi z wymuszonego połączenia VPN, należy wykonać poniższe czynności. To rozwiązanie ma na celu zapewnienie klientom opcji unikania routingu ruchu w zdarzeniach na żywo przez sieć VPN, gdy istnieje duży ruch sieciowy ze względu na scenariusze z pracy z domu. Jeśli to możliwe, zaleca się uzyskanie dostępu do usługi przez serwer proxy przeprowadzający inspekcję.

>[!NOTE]
>W przypadku użycia tego rozwiązania mogą wystąpić elementy usługi, które nie rozwiązują podanego adresu IP, przez co przechodzi przez sieć VPN, ale zbiorczy ruch o dużej pojemności, taki jak przesyłanie strumieniowe danych, powinien być przesyłany. Poza zakresem zdarzeń na żywo/strumienia mogą znajdować się inne elementy, które napawają uwagę podczas tego ładowania, ale powinny one być ograniczone, ponieważ muszą spełniać zarówno usługę _FQDN,_ jak i dopasowanie adresu IP, zanim trafią bezpośrednio.

>[!IMPORTANT]
>Zaleca się, aby klienci zważyli na ryzyko wysyłania większej liczby ruchu ominięcia sieci VPN w większej wydajności niż w przypadku wydarzeń na żywo.

Aby zaimplementować wyjątek wymuszany wyekspowania Teams wydarzeń na żywo i usługi Stream, należy zastosować następujące kroki:

## <a name="1-configure-external-dns-resolution"></a>1. Konfigurowanie rozpoznawania zewnętrznego systemu DNS

Klienci muszą mieć dostęp do zewnętrznej, rekurentywnej rozdzielczości DNS, aby można było rozpoznać następujące nazwy hostów jako adresy IP.

- \*azureedge.net
- \*media.azure.net
- \*bmc.cdn.office.net

**\*.azureedge.net** jest używana do zdarzeń usługi Stream (Konfigurowanie koderów dla przesyłania strumieniowego na żywo w [umacie Microsoft Stream — Usługa Microsoft Stream | Microsoft Docs](/stream/live-encoder-setup)).

**\*.media.azure.net** **\*i bmc.cdn.office.net** są używane do tworzenia wydarzeń na żywo Teams (wydarzeń szybkich start, wydarzeń RTMP-In obsługiwanych [Identyfikator planu 84960]) zaplanowanych w kliencie Teams klienta.

 Niektóre z tych punktów końcowych są udostępniane innym elementom poza usługą Stream/Wydarzenia na żywo. Zaleca się używanie tych FQDN do konfigurowania ładowania SIECI VPN, nawet jeśli to możliwe technicznie w rozwiązaniu VPN (np. jeśli działa ono w witrynie FQDN, a nie w adresie IP).

W konfiguracji SIECI VPN nie są wymagane sieci FQDN, mają tylko zastosowanie w plikach PAC w połączeniu z adresami IP w celu bezpośredniego wysyłania ruchu.

## <a name="2-implement-pac-file-changes-where-required"></a>2. Implementowanie zmian w plikach PAC (jeśli jest to wymagane)

W przypadku organizacji korzystających z pliku PAC w celu trasy ruchu przez serwer proxy w sieci VPN zwykle uzyskuje się to za pomocą FQDN. Jednak w przypadku wydarzeń na żywo/**\*** streamu podane nazwy hostów zawierają symbole wieloznaczne, takie jak azureedge.net, które również obejmują inne elementy, dla których nie można podać pełnych list adresów IP. Dlatego, jeśli żądanie jest wysyłane bezpośrednio na podstawie dopasowania z symbolami wieloznacznych DNS, ruch do tych punktów końcowych zostanie zablokowany, ponieważ nie istnieje trasa przez ścieżkę bezpośrednią dla tego żądania w kroku [3](#3-configure-routing-on-the-vpn-to-enable-direct-egress) w dalszej części tego artykułu.

Aby rozwiązać ten problem, możemy udostępnić następujące adresy IP i używać ich w połączeniu z nazwami hostów w przykładowym pliku PAC, jak to opisano w [kroku 1](#1-configure-external-dns-resolution). Plik PAC sprawdza, czy adres URL jest ten sam, jak używany dla zdarzeń Stream/Live, a następnie, jeśli tak, sprawdza również, czy adres IP zwrócony z odnośnika DNS jest ten sam, jak adres podany dla usługi. Jeśli _oba_ są zgodne, ruch jest kierowany bezpośrednio. Jeśli którykolwiek z elementów (FQDN/IP) nie jest zgodne, ruch jest wysyłany do serwera proxy. Dzięki temu konfiguracja zapewnia, że wszystko, co znajdzie się poza zakresem adresów IP i zdefiniowanych przestrzeni nazw, będzie przechodzić przez serwer proxy przez sieć VPN tak jak zwykle.

### <a name="gathering-the-current-lists-of-cdn-endpoints"></a>Zbieranie bieżących list punktów CDN końcowych

Wydarzenia na żywo używa wielu CDN do przesyłania strumieniowego do klientów, aby zapewnić najlepszą wydajność, jakość i odporność. Obecnie używane są Azure CDN firmy Microsoft i Verizon. Z czasem może to zostać zmienione ze względu na sytuacje, takie jak dostępność regionalna. Ten artykuł jest źródłem, dzięki którym możesz na bieżąco śledzić zakresy adresów IP.

W przypadku Azure CDN firmy Microsoft możesz pobrać listę z witryny Pobieranie zakresów [adresów IP](https://www.microsoft.com/download/details.aspx?id=56519) i tagów usług platformy Azure — chmury publicznej z oficjalnego Centrum pobierania Microsoft — musisz poszukać w szczególności tagu usługi *AzureFrontdoor.Frontend* w usłudze JSON. *AddressPrefixs* will show the IPv4/IPv6 subnets. Z czasem adresów IP mogą się zmieniać, ale lista tagów usługi jest zawsze aktualizowana przed ich użyciem.

Na Azure CDN firmy Verizon (Edgecast) [https://docs.microsoft.com/rest/api/cdn/edge-nodes/list](/rest/api/cdn/edge-nodes/list) możesz znaleźć pełną listę, używając (kliknij pozycję **Wypróbuj) —** musisz szukać w szczególności sekcji **Premium\_ Verizon**. Pamiętaj, że ten interfejs API pokazuje wszystkie ip usługi Edgecast (pochodzenie i Anycast). Obecnie nie istnieje mechanizm interfejsu API rozróżniania pochodzenia od funkcji Anycast.

Aby zaimplementować to w pliku PAC, możesz użyć poniższego przykładu, który wysyła nazwę Microsoft 365 Optimize traffic direct (co jest zalecane najlepszym rozwiązaniem) za pośrednictwem nazwy FQDN, a krytyczny ruch Stream/Live Events bezpośrednio za pośrednictwem kombinacji nazwy FQDN i zwróconego adresu IP. Nazwa zastępczą _Contoso_ należy edytować pod nazwą konkretnej dzierżawy, gdzie _contoso_ pochodzi z contoso.onmicrosoft.com

#### <a name="example-pac-file"></a>Przykładowy plik PAC

Oto przykład wygenerowania plików PAC:

1. Zapisz poniższy skrypt na lokalnym dysku twardym jako _Get-TLEPacFile.ps1_.
1. Przejdź do adresu [URL sieci Verizon](/rest/api/cdn/edge-nodes/list#code-try-0) i pobierz wynikowy kod JSON (skopiuj go do pliku, takiego jak cdnedgenodes.json)
1. Umieść plik w tym samym folderze, w którym znajduje się skrypt.
1. W oknie programu PowerShell uruchom następujące polecenie. Zmień nazwę dzierżawy na coś innego, jeśli chcesz uzyskać adresy URL usługi SPO. Jest to typ 2, więc optymalizuj **i** **zezwalaj** (typ 1 to tylko optymalizowanie).

   ```powershell
   .\Get-TLEPacFile.ps1 -Instance Worldwide -Type 2 -TenantName <contoso> -CdnEdgeNodesFilePath .\cdnedgenodes.json -FilePath TLE.pac
   ```

5. Plik TLE.pac będzie zawierać wszystkie przestrzenie nazw i adresów IP (IPv4/IPv6).

##### <a name="get-tlepacfileps1"></a>Get-TLEPacFile.ps1

```powershell
# Copyright (c) Microsoft Corporation. All rights reserved.
# Licensed under the MIT License.

<#PSScriptInfo

.VERSION 1.0.4

.AUTHOR Microsoft Corporation

.GUID 7f692977-e76c-4582-97d5-9989850a2529

.COMPANYNAME Microsoft

.COPYRIGHT
Copyright (c) Microsoft Corporation. All rights reserved.
Licensed under the MIT License.

.TAGS PAC Microsoft Microsoft365 365

.LICENSEURI

.PROJECTURI http://aka.ms/ipurlws

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES

#>

<#

.SYNOPSIS

Create a PAC file for Microsoft 365 prioritized connectivity

.DESCRIPTION

This script will access updated information to create a PAC file to prioritize Microsoft 365 Urls for
better access to the service. This script will allow you to create different types of files depending
on how traffic needs to be prioritized.

.PARAMETER Instance

The service instance inside Microsoft 365.

.PARAMETER ClientRequestId

The client request id to connect to the web service to query up to date Urls.

.PARAMETER DirectProxySettings

The direct proxy settings for priority traffic.

.PARAMETER DefaultProxySettings

The default proxy settings for non priority traffic.

.PARAMETER Type

The type of prioritization to give. Valid values are 1 and 2, which are 2 different modes of operation.
Type 1 will send Optimize traffic to the direct route. Type 2 will send Optimize and Allow traffic to
the direct route.

.PARAMETER Lowercase

Flag this to include lowercase transformation into the PAC file for the host name matching.

.PARAMETER TenantName

The tenant name to replace wildcard Urls in the webservice.

.PARAMETER ServiceAreas

The service areas to filter endpoints by in the webservice.

.PARAMETER FilePath

The file to print the content to.

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -DefaultProxySettings "PROXY 4.4.4.4:70" -FilePath type1.pac

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -Instance China -Type 2 -DefaultProxySettings "PROXY 4.4.4.4:70" -FilePath type2.pac

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -Instance WorldWide -Lowercase -TenantName tenantName -ServiceAreas Sharepoint

#>

#Requires -Version 2

[CmdletBinding(SupportsShouldProcess=$True)]
Param (
    [Parameter(Mandatory = $false)]
    [ValidateSet('Worldwide', 'Germany', 'China', 'USGovDoD', 'USGovGCCHigh')]
    [String] $Instance = "Worldwide",

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [guid] $ClientRequestId = [Guid]::NewGuid().Guid,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [String] $DirectProxySettings = 'DIRECT',

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [String] $DefaultProxySettings = 'PROXY 10.10.10.10:8080',

    [Parameter(Mandatory = $false)]
    [ValidateRange(1, 2)]
    [int] $Type = 1,

    [Parameter(Mandatory = $false)]
    [switch] $Lowercase = $false,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $TenantName,

    [Parameter(Mandatory = $false)]
    [ValidateSet('Exchange', 'SharePoint', 'Common', 'Skype')]
    [string[]] $ServiceAreas,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $FilePath,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $CdnEdgeNodesFilePath
)

##################################################################################################################
### Global constants
##################################################################################################################

$baseServiceUrl = "https://endpoints.office.com/endpoints/$Instance/?ClientRequestId={$ClientRequestId}"
$directProxyVarName = "direct"
$defaultProxyVarName = "proxyServer"
$bl = "`r`n"

##################################################################################################################
### Functions to create PAC files
##################################################################################################################

function Get-PacClauses
{
    param(
        [Parameter(Mandatory = $false)]
        [string[]] $Urls,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $ReturnVarName
    )

    if (!$Urls)
    {
        return ""
    }

    $clauses =  (($Urls | ForEach-Object { "shExpMatch(host, `"$_`")" }) -Join "$bl        || ")

@"
    if($clauses)
    {
        return $ReturnVarName;
    }
"@
}

function Get-PacString
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [array[]] $MapVarUrls
    )

@"
// This PAC file will provide proxy config to Microsoft 365 services
//  using data from the public web service for all endpoints
function FindProxyForURL(url, host)
{
    var $directProxyVarName = "$DirectProxySettings";
    var $defaultProxyVarName = "$DefaultProxySettings";

$( if ($Lowercase) { "    host = host.toLowerCase();" })

$( ($MapVarUrls | ForEach-Object { Get-PACClauses -ReturnVarName $_.Item1 -Urls $_.Item2 }) -Join "$bl$bl" )

$( if (!$ServiceAreas -or $ServiceAreas.Contains('Skype')) { Get-TLEPacConfiguration })

    return $defaultProxyVarName;
}
"@ -replace "($bl){3,}","$bl$bl" # Collapse more than one blank line in the PAC file so it looks better.
}

##################################################################################################################
### Functions to get and filter endpoints
##################################################################################################################

function Get-TLEPacConfiguration {
    param ()
    $PreBlock = @"
    // Don't Proxy Teams Live Events traffic

    if(shExpMatch(host, "*.azureedge.net")
    || shExpMatch(host, "*.bmc.cdn.office.net")
    || shExpMatch(host, "*.media.azure.net"))
    {
        var resolved_ip = dnsResolveEx(host);

"@
    $TLESb = New-Object 'System.Text.StringBuilder'
    $TLESb.Append($PreBlock) | Out-Null

    if (![string]::IsNullOrEmpty($CdnEdgeNodesFilePath) -and (Test-Path -Path $CdnEdgeNodesFilePath)) {
        $CdnData = Get-Content -Path $CdnEdgeNodesFilePath -Raw -ErrorAction SilentlyContinue | ConvertFrom-Json | Select-Object -ExpandProperty value | 
            Where-Object { $_.name -eq 'Premium_Verizon'} | Select-Object -First 1 -ExpandProperty properties | 
            Select-Object -ExpandProperty ipAddressGroups
        $CdnData | Select-Object -ExpandProperty ipv4Addresses | ForEach-Object {
            if ($TLESb.Length -eq $PreBlock.Length) {
                $TLESb.Append("        if(") | Out-Null
            }
            else {
                $TLESb.AppendLine() | Out-Null
                $TLESb.Append("        || ") | Out-Null
            }
            $TLESb.Append("isInNetEx(resolved_ip, `"$($_.BaseIpAddress)/$($_.prefixLength)`")") | Out-Null
        }
        $CdnData | Select-Object -ExpandProperty ipv6Addresses | ForEach-Object {
            if ($TLESb.Length -eq $PreBlock.Length) {
                $TLESb.Append("        if(") | Out-Null
            }
            else {
                $TLESb.AppendLine() | Out-Null
                $TLESb.Append("        || ") | Out-Null
            }
            $TLESb.Append("isInNetEx(resolved_ip, `"$($_.BaseIpAddress)/$($_.prefixLength)`")") | Out-Null
        }
    }
    $AzureIPsUrl = Invoke-WebRequest -Uri "https://www.microsoft.com/en-us/download/confirmation.aspx?id=56519" -UseBasicParsing -ErrorAction SilentlyContinue  | 
            Select-Object -ExpandProperty Links | Select-Object -ExpandProperty href | 
            Where-Object { $_.EndsWith('.json') -and $_ -match 'ServiceTags' } | Select-Object -First 1
    if ($AzureIPsUrl) {
        Invoke-RestMethod -Uri $AzureIPsUrl -ErrorAction SilentlyContinue | Select-Object -ExpandProperty values | 
            Where-Object { $_.name -eq 'AzureFrontDoor.Frontend' } | Select-Object -First 1 -ExpandProperty properties |
            Select-Object -ExpandProperty addressPrefixes | ForEach-Object {
                if ($TLESb.Length -eq $PreBlock.Length) {
                    $TLESb.Append("        if(") | Out-Null
                }
                else {
                    $TLESb.AppendLine() | Out-Null
                    $TLESb.Append("        || ") | Out-Null
                }
                $TLESb.Append("isInNetEx(resolved_ip, `"$_`")") | Out-Null
            }
    }
    if ($TLESb.Length -gt $PreBlock.Length) {
        $TLESb.AppendLine(")") | Out-Null
        $TLESb.AppendLine("        {") | Out-Null
        $TLESb.AppendLine("            return $directProxyVarName;") | Out-Null
        $TLESb.AppendLine("        }") | Out-Null
    }
    else {
        $TLESb.AppendLine("        // no addresses found for service via script") | Out-Null
    }
    $TLESb.AppendLine("    }") | Out-Null
    return $TLESb.ToString()
}

function Get-Regex
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $Fqdn
    )

    return "^" + $Fqdn.Replace(".", "\.").Replace("*", ".*").Replace("?", ".?") + "$"
}

function Match-RegexList
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $ToMatch,

        [Parameter(Mandatory = $false)]
        [string[]] $MatchList
    )

    if (!$MatchList)
    {
        return $false
    }
    foreach ($regex in $MatchList)
    {
        if ($regex -ne $ToMatch -and $ToMatch -match (Get-Regex $regex))
        {
            return $true
        }
    }
    return $false
}

function Get-Endpoints
{
    $url = $baseServiceUrl
    if ($TenantName)
    {
        $url += "&TenantName=$TenantName"
    }
    if ($ServiceAreas)
    {
        $url += "&ServiceAreas=" + ($ServiceAreas -Join ",")
    }
    return Invoke-RestMethod -Uri $url
}

function Get-Urls
{
    param(
        [Parameter(Mandatory = $false)]
        [psobject[]] $Endpoints
    )

    if ($Endpoints)
    {
        return $Endpoints | Where-Object { $_.urls } | ForEach-Object { $_.urls } | Sort-Object -Unique
    }
    return @()
}

function Get-UrlVarTuple
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $VarName,

        [Parameter(Mandatory = $false)]
        [string[]] $Urls
    )
    return New-Object 'Tuple[string,string[]]'($VarName, $Urls)
}

function Get-MapVarUrls
{
    Write-Verbose "Retrieving all endpoints for instance $Instance from web service."
    $Endpoints = Get-Endpoints

    if ($Type -eq 1)
    {
        $directUrls = Get-Urls ($Endpoints | Where-Object { $_.category -eq "Optimize" })
        $nonDirectPriorityUrls = Get-Urls ($Endpoints | Where-Object { $_.category -ne "Optimize" }) | Where-Object { Match-RegexList $_ $directUrls }
        return @(
            Get-UrlVarTuple -VarName $defaultProxyVarName -Urls $nonDirectPriorityUrls
            Get-UrlVarTuple -VarName $directProxyVarName -Urls $directUrls
        )
    }
    elseif ($Type -eq 2)
    {
        $directUrls = Get-Urls ($Endpoints | Where-Object { $_.category -in @("Optimize", "Allow")})
        $nonDirectPriorityUrls = Get-Urls ($Endpoints | Where-Object { $_.category -notin @("Optimize", "Allow") }) | Where-Object { Match-RegexList $_ $directUrls }
        return @(
            Get-UrlVarTuple -VarName $defaultProxyVarName -Urls $nonDirectPriorityUrls
            Get-UrlVarTuple -VarName $directProxyVarName -Urls $directUrls
        )
    }
}

##################################################################################################################
### Main script
##################################################################################################################

$content = Get-PacString (Get-MapVarUrls)

if ($FilePath)
{
    $content | Out-File -FilePath $FilePath -Encoding ascii
}
else
{
    $content
}
```

Skrypt automatycznie analizuje listę platformy Azure na podstawie adresu [URL](https://www.microsoft.com/download/details.aspx?id=56519) i kluczy pobierania z usługi **AzureFrontDoor.Frontend**, więc nie trzeba pobierać tego ręcznie.

Zaleca się także, aby połączenia VPN można było ładować tylko za pomocą FQDN. korzystanie **zarówno z** sieci FQDN, jak i adresów IP w funkcji pomaga ograniczyć wykorzystanie tego obciążenia do ograniczonego zestawu punktów końcowych, w tym do usługi Live Events/Stream. Struktura funkcji spowoduje, że wykonywana będzie odnośnik DNS dla nazwy FQDN, która będzie odpowiadać tym, które są wymienione bezpośrednio przez klienta, na przykład rozpoznawanie nazw DNS pozostałych przestrzeni nazw pozostaje bez zmian.

Jeśli chcesz ograniczyć ryzyko związanego z ładowaniem punktów końcowych nie związanych z wydarzeniami na żywo i usługą Stream, **\*** możesz usunąć domenę .azureedge.net z konfiguracji, gdzie większość tego ryzyka leży, ponieważ jest to domena udostępniona używana dla wszystkich klientów usługi Azure CDN. Minusem tej funkcji jest to, że żadne zdarzenie korzystające z zewnętrznego kodera nie zostanie zoptymalizowane, ale wydarzenia są organizowane/zorganizowane w ramach Teams będą.

## <a name="3-configure-routing-on-the-vpn-to-enable-direct-egress"></a>3. Konfigurowanie routingu w sieci VPN w celu włączenia bezpośredniego ruchu wychodzącego

Ostatnim krokiem jest dodanie trasy bezpośredniej do adresu IP zdarzeń na żywo opisanego w artykule Zbieranie bieżących list punktów końcowych usługi **CDN** do konfiguracji sieci VPN w celu zapewnienia, że ruch nie będzie wysyłany przez wymuszony parametr sieci VPN. Szczegółowe informacje o tym, jak to zrobić w Microsoft 365 Optymalizowanie punktów końcowych, można znaleźć w sekcji Implementowanie rozdzielania sieci VPN opisanej w sekcji Implementowanie rozdzielania sieci [VPN](microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling) dla sieci [Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md). Proces jest dokładnie taki sam w przypadku wymienionych w tym dokumencie ip zdarzeń strumienia/zdarzeń na żywo.

Pamiętaj, że do konfiguracji sieci VPN powinny być używane tylko protokoły IP (a nie FQDN) z bieżącej listy CDN punktów końcowych sieci VPN.[](#gathering-the-current-lists-of-cdn-endpoints)

## <a name="faq"></a>Często zadawane pytania

### <a name="will-this-send-all-my-traffic-to-the-service-direct"></a>Czy spowoduje to kierowanie całego ruchu do usługi?

Nie, spowoduje to wysłanie ruchu strumieniowego, w przypadku których ruch strumieniowy z opóźnieniem jest przesyłany bezpośrednio w przypadku zdarzenia na żywo lub przesyłania strumieniowego, każdy inny ruch będzie nadal korzystać z serwera vpn, jeśli nie rozpozna opublikowanych ip.

### <a name="do-i-need-to-use-the-ipv6-addresses"></a>Czy muszę używać adresów IPv6?

Nie, łączność może mieć protokół IPv4 tylko wtedy, gdy jest to wymagane.

### <a name="why-are-these-ips-not-published-in-the-microsoft-365-urlip-service"></a>Dlaczego te adresy IP nie są publikowane w usłudze Microsoft 365 URL/IP?

Firma Microsoft dysponuje rygorystycznymi mechanizmami kontroli nad formatem i typem informacji w usłudze, aby zapewnić klientom możliwość niezawodnego używania tych informacji w celu wdrożenia bezpiecznego i optymalnego routingu na podstawie kategorii punktów końcowych.

W **kategorii** Domyślny punkt końcowy nie podano informacji o adresie IP z wielu powodów (Domyślne punkty końcowe mogą być poza kontrolą firmy Microsoft, mogą zmieniać się zbyt często lub mogą być zawarte w blokach udostępnionych innym elementom). Z tego powodu domyślne punkty końcowe są przeznaczone do przesyłania za pośrednictwem usługi FQDN do serwera proxy inspekcji, takiego jak normalny ruch sieci Web.

W tym przypadku powyższe punkty końcowe to sieci CDN, które mogą być używane przez elementy inne niż zdarzenia na żywo lub strumień inne niż zdarzenia na żywo firmy Microsoft, a zatem wysyłanie bezpośredniego ruchu będzie również oznaczać wszystko, co zmieni się w tych adresach IP, zostanie również wysłane bezpośrednio z klienta. Ze względu na unikatowy charakter bieżącej globalnej kryzysowej sytuacji i w celu zaspokojenia krótkich potrzeb naszych klientów firma Microsoft dostarczyła klientom powyższe informacje do użycia zgodnie z ich potrzebami.

Firma Microsoft pracuje nad ponowne skonfigurowaniem punktów końcowych zdarzeń na żywo, aby w przyszłości umożliwić ich uwzględnianie w kategoriach punktów końcowych Zezwalaj/Optymalizuj.

### <a name="do-i-only-need-to-allow-access-to-these-ips"></a>Czy muszę zezwolić na dostęp tylko do tych ip?

Nie, dostęp do wszystkich oznaczonych  punktów końcowych wymaganych w [usłudze adresów URL/IP](urls-and-ip-address-ranges.md) jest niezbędny do działania usługi. Ponadto jest wymagany dowolny opcjonalny punkt końcowy oznaczony dla usługi Stream (IDENTYFIKATOR 41-45).

### <a name="what-scenarios-will-this-advice-cover"></a>Jakie scenariusze będą dotyczyć tych porad?

1. Wydarzenia na żywo w aplikacji Teams App
2. Wyświetlanie hostowanej zawartości usługi Stream
3. Wydarzenia są wykonywane na urządzeniach zewnętrznych (encoder)

### <a name="does-this-advice-cover-presenter-traffic"></a>Czy ta porada dotyczy ruchu osób prezentera?

Nie, powyższe porady mają tylko charakter tylko dla osób, które chłoną usługę. Prezentujejąc z poziomu usługi Teams, zobaczymy ruch prezentera trafiający do punktów końcowych Optymalizacja oznaczonych przez UDP wymienionych w wierszu 11 adresu URL/usługi IP ze szczegółowymi poradami o ładowaniu [](microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling) vpn opisanymi w sekcji Implementowanie rozdzielania vpn na poziomie sieci [Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).

### <a name="does-this-configuration-risk-traffic-other-than-live-events-amp-stream-being-sent-direct"></a>Czy ta konfiguracja powoduje ryzyko kierowania ruchu innego niż strumień &amp; wydarzeń na żywo?

Tak, ze względu na udostępnione usługi FQNS używane dla niektórych elementów usługi jest to nie da się uniknąć. Ten ruch jest zazwyczaj wysyłany za pośrednictwem firmowego serwera proxy, który może zastosować inspekcję. W scenariuszu z podziałem na scenariusz z podziałem sieci VPN użycie zarówno sieci FQDN, jak i ip spowoduje minimalne wykorzystanie tego ryzyka, ale nadal będzie istnieć. **\*** Klienci mogą usunąć domenę azureedge.net z konfiguracji ładowania i zmniejszyć to ryzyko do minimalnego poziomu, ale spowoduje Teams usunięcie ładowania zdarzeń na żywo obsługiwanych przez usługę Stream (zaplanowanych przez usługę Teams, zdarzeń kodera zewnętrznego, wydarzeń Yammer owanych w programie Teams, zdarzeń zewnętrznego kodera Yammer zaplanowanego przez usługę Yammer oraz wydarzeń planowanych przez usługę Stream lub wyświetlania ich na żądanie z poziomu usługi Stream). Wydarzenia zaplanowane i produkcji Teams pozostają nienaruszone.

## <a name="related-articles"></a>Artykuły pokrewne

[Omówienie: rozdzielanie sieci VPN na Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Implementowanie rozdzielania sieci VPN na Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Typowe scenariusze rozdzielania sieci VPN dla sieci Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Zabezpieczanie Teams multimediów na przykład przez rozdzielanie sieci VPN](microsoft-365-vpn-securing-teams.md)

[Microsoft 365 wydajności dla użytkowników w Chinach](microsoft-365-networking-china.md)

[Microsoft 365 dotyczące łączności sieciowej](microsoft-365-network-connectivity-principles.md)

[Ocenianie Microsoft 365 sieciowej](assessing-network-connectivity.md)

[Microsoft 365 sieci i dostosowywania wydajności](network-planning-and-performance.md)

[Nowoczesne mechanizmy kontroli zabezpieczeń można zapewnić specjalistom zabezpieczeń i informatykom w alternatywnych, obecnie unikatowych scenariuszach pracy zdalnej (blog zespołu zabezpieczeń firmy Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Zwiększanie wydajności sieci VPN w firmie Microsoft: Windows 10 profilów SIECI VPN w celu umożliwienia automatycznego na połączenia](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Vpn: jak firma Microsoft łączy się ze swoimi pracownikami zdalnymi](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Sieć globalna firmy Microsoft](/azure/networking/microsoft-global-network)
