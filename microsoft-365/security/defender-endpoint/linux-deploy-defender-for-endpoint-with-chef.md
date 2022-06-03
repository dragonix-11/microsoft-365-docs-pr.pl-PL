---
title: Jak wdrożyć usługę Defender for Endpoint w systemie Linux za pomocą programu Chef
description: Dowiedz się, jak wdrożyć usługę Defender for Endpoint w systemie Linux za pomocą programu Chef
keywords: microsoft, defender, atp, linux, scans, antivirus, microsoft defender for endpoint (linux)
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 8f610821b6c0bef7694d6ce8acd256f59f761f06
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872941"
---
# <a name="deploy-defender-for-endpoint-on-linux-with-chef"></a>Wdrażaj usługę ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux za pomocą programu Chef

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

Przed rozpoczęciem: zainstaluj rozpakuj, jeśli nie jest jeszcze zainstalowana.

Składniki programu Chef są już zainstalowane i istnieje repozytorium Chef (chef generate repo \<reponame\>) do przechowywania książki kucharskiej, która będzie używana do wdrażania w usłudze Defender for Endpoint na serwerach z systemem Linux zarządzanych przez program Chef.

Możesz utworzyć nową książkę kucharską w istniejącym repozytorium, uruchamiając następujące polecenie z folderu książki kucharskiej znajdującego się w repozytorium chef:

```bash
chef generate cookbook mdatp
```

To polecenie utworzy nową strukturę folderów dla nowej książki kucharskiej o nazwie mdatp. Możesz również użyć istniejącej książki kucharskiej, jeśli masz już taką, która ma zostać użyta do dodania wdrożenia mde.
Po utworzeniu książki kucharskiej utwórz folder plików w folderze książki kucharskiej, który właśnie został utworzony:

```bash
mkdir mdatp/files
```

Przenieś plik zip dołączania serwera z systemem Linux, który można pobrać z portalu Microsoft 365 Defender do tego nowego folderu plików.

Na stacji roboczej chef przejdź do folderu mdatp/recipes. Ten folder jest tworzony po wygenerowaniu książki kucharskiej. Użyj preferowanego edytora tekstów (na przykład vi lub nano), aby dodać następujące instrukcje na końcu pliku default.rb:

- include_recipe "::onboard_mdatp"
- include_recipe "::install_mdatp"

Następnie zapisz i zamknij plik default.rb.

Następnie utwórz nowy plik przepisu o nazwie install_mdatp.rb w folderze recipes i dodaj ten tekst do pliku:

```powershell
#Add Microsoft Defender
Repo
case node['platform_family']
when 'debian'
 apt_repository 'MDAPRepo' do
   arch               'amd64'
   cache_rebuild      true
   cookbook           false
   deb_src            false
   key                'BC528686B50D79E339D3721CEB3E94ADBE1229CF'
   keyserver          "keyserver.ubuntu.com"
   distribution       'focal'
   repo_name          'microsoft-prod'
   components         ['main']
   trusted            true
   uri                "https://packages.microsoft.com/config/ubuntu/20.04/prod"
 end
 apt_package "mdatp"
when 'rhel'
 yum_repository 'microsoft-prod' do
   baseurl            "https://packages.microsoft.com/config/rhel/7/prod/"
   description        "Microsoft Defender for Endpoint"
   enabled            true
   gpgcheck           true
   gpgkey             "https://packages.microsoft.com/keys/microsoft.asc"
 end
 if node['platform_version'] <= 8 then
    yum_package "mdatp"
 else
    dnf_package "mdatp"
 end
end
```

Musisz zmodyfikować numer wersji, dystrybucję i nazwę repozytorium, aby była zgodna z wersją, do której wdrażasz, i kanałem, który chcesz wdrożyć.
Następnie należy utworzyć plik onboard_mdatp.rb w folderze mdatp/recipies. Dodaj następujący tekst do tego pliku:

```powershell
#Create MDATP Directory
mdatp = "/etc/opt/microsoft/mdatp"
zip_path = "/path/to/chef-repo/cookbooks/mdatp/files/WindowsDefenderATPOnboardingPackage.zip"

directory "#{mdatp}" do
  owner 'root'
  group 'root'
  mode 0755
  recursive true
end

#Extract WindowsDefenderATPOnbaordingPackage.zip into /etc/opt/microsoft/mdatp

bash 'Extract Onbaording Json MDATP' do
  code <<-EOS
  unzip #{zip_path} -d #{mdatp}
  EOS
  not_if { ::File.exist?('/etc/opt/microsoft/mdatp/mdatp_onboard.json') }
end
```

Pamiętaj, aby zaktualizować nazwę ścieżki do lokalizacji pliku dołączania.
Aby przetestować wdrożenie go na stacji roboczej programu Chef, wystarczy uruchomić polecenie ``sudo chef-client -z -o mdatp``.
Po wdrożeniu należy rozważyć utworzenie i wdrożenie pliku konfiguracji na serwerach w oparciu o [ustawienie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](/microsoft-365/security/defender-endpoint/linux-preferences).
Po utworzeniu i przetestowaniu pliku konfiguracji możesz umieścić go w folderze cookbook/mdatp/files, w którym również umieszczono pakiet dołączania. Następnie możesz utworzyć plik settings_mdatp.rb w folderze mdatp/recipies i dodać następujący tekst:

```powershell
#Copy the configuration file
cookbook_file '/etc/opt/microsoft/mdatp/managed/mdatp_managed.json' do
  source 'mdatp_managed.json'
  owner 'root'
  group 'root'
  mode '0755'
  action :create
end
```

Aby uwzględnić ten krok jako część przepisu, wystarczy dodać include_recipe ":: settings_mdatp" do pliku default.rb w folderze przepisu.
Możesz również użyć narzędzia crontab, aby zaplanować aktualizacje automatyczne [Zaplanuj aktualizację Ochrona punktu końcowego w usłudze Microsoft Defender (Linux).](linux-update-MDE-Linux.md).

Odinstaluj książkę kucharską MDATP:

```powershell
#Uninstall the Defender package
case node['platform_family']
when 'debian'
 apt_package "mdatp" do
   action :remove
 end
when 'rhel'
 if node['platform_version'] <= 8
then
    yum_package "mdatp" do
      action :remove
    end
 else
    dnf_package "mdatp" do
      action :remove
    end
 end
end
```
