---
description: na
keywords: na
title: Configuring Applications for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ea09cbc5-b98b-444e-8b60-5bc3cb199c36
---
# Toepassingen voor Azure Rights Management configureren
> [!NOTE]
> Deze informatie is voor IT-beheerders en voor adviseurs die Azure Rights Management hebt geïmplementeerd. Als u zoekt naar Help-informatie en informatie over het gebruik van Rights Management voor een bepaalde toepassing of het openen van een bestand dat rechten wordt beveiligd, gebruikt u help en hulp bij uw toepassing.
> 
> Bijvoorbeeld voor Office-toepassingen, klikt u op het Help-pictogram en voer zoektermen zoals **Rights Management** of **IRM**. Voor de RMS sharing van toepassing voor Windows, raadpleegt u de [delen toepassing Rights Management-handleiding](http://technet.microsoft.com/library/dn339006.aspx).

Na het implementeren van Azure Rights Management (Azure RMS) voor uw organisatie, gebruikt u de volgende informatie toepassingen en services ter ondersteuning van Azure RMS configureren. Hierbij Office-toepassingen zoals Word 2013 en Word 2010 en services, zoals Exchange Online (gegevensverlies voorkomen transportregels niet doorsturen en codering) en SharePoint Online (beveiligde bibliotheken). Zie voor meer informatie over hoe deze toepassingen en services Rights Management ondersteunen [Hoe toepassingen ondersteunen Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md).

> [!IMPORTANT]
> Zie voor meer informatie over ondersteunde versies en andere vereisten [Vereisten voor Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

-   [Office 365: Configuratie voor clients en online services](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_O365)

    -   [Exchange Online: IRM-configuratie](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_ExchangeOnline)

    -   [SharePoint Online en OneDrive voor bedrijven: IRM-configuratie](#BKMK_SharePointOnline)

-   [Office 2016 en Office 2013: Configuratie voor clients](#BKMK_Office2013Configuration)

-   [Office 2010: Configuratie voor clients](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_Office2010Configuration)

-   [Rights Management-toepassing delen: Installatie en configuratie voor clients](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharingApp)

    -   [De RMS sharing van toepassing voor Windows: Installatie en configuratie](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharingAppforWindows)

    -   [De RMS sharing van toepassing voor mobiele platforms: Installatie](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharingAppMovileDevices)

-   [Andere toepassingen die ondersteuning voor de RMS APIs: Installatie en configuratie](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_RMSAPIs)

Zie het configureren van lokale servers, zoals Exchange-Server en SharePoint Server [Implementatie van de Connector van de Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

> [!TIP]
> Zie voor voorbeelden op hoog niveau en schermafdrukken van toepassingen die zijn geconfigureerd voor gebruik van Azure RMS het [Azure RMS in actie: Zie welke beheerders en gebruikers](../Topic/What_is_Azure_Rights_Management_.md#BKMK_RMSpictures) gedeelte van de [Wat is Azure Rights Management?](../Topic/What_is_Azure_Rights_Management_.md) onderwerp.

## <a name="BKMK_O365"></a>Office 365: Configuratie voor clients en online services
Office 365 ondersteunt Azure RMS, is geen configuratie van clientcomputer vereist voor de ondersteuning van de functies van information rights management (IRM) voor toepassingen zoals Word, Excel, PowerPoint, Outlook en de Outlook Web-App. Alle gebruikers hebben om te doen is aanmelden bij hun Office-toepassingen met hun [!INCLUDE[o365_1](../Token/o365_1_md.md)] referenties en ze kunnen beschermen bestanden en e-mailberichten en gebruik van bestanden en e-mailberichten die zijn beveiligd door anderen.

We raden echter aan dat u deze toepassingen aanvullen met de Rights Management delen van de toepassing, zodat gebruikers van de voordelen van het Office-invoegtoepassing profiteren. Zie voor meer informatie de [Rights Management-toepassing delen: Installatie en configuratie voor clients](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharingApp) in dit onderwerp.

### <a name="BKMK_ExchangeOnline"></a>Exchange Online: IRM-configuratie
Als u wilt configureren Exchange Online ter ondersteuning van Azure RMS, moet u de service rights management (IRM) voor Exchange Online. Dit doet u Windows PowerShell (hoeft te installeren een afzonderlijke module), gebruiken en voer [PowerShell-opdrachten voor Exchange Online](https://technet.microsoft.com/library/jj200677.aspx).

> [!NOTE]
> U kunt geen momenteel Exchange Online ter ondersteuning van Azure RMS als u een klant beheerde tenant sleutel (BYOK) in plaats van de standaardconfiguratie van een sleutel Microsoft beheerde tenant voor Azure RMS configureren. Zie voor meer informatie de [BYOK pricing and restrictions](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing) sectie de [Plannen en implementeren van uw Azure Rights Management Tenant-sleutel](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md) onderwerp.
> 
> Als u configureren Exchange Online wilt als u gebruikmaakt van Azure RMS BYOK, mislukt de opdracht voor het importeren van de sleutel (stap 5, in de volgende procedure) met het foutbericht **[FailureCategory = Cmdlet FailedToGetTrustedPublishingDomainFromRmsOnlineException]**.

De volgende stappen uit vindt u een standaardset opdrachten die u uitvoeren wilt om in te schakelen Exchange Online Azure RMS gebruiken:

1.  Als dit de eerste keer dat u Windows PowerShell voor Exchange Online hebt gebruikt op uw computer, moet u Windows PowerShell om uit te voeren ondertekende scripts configureren. Uw Windows PowerShell-sessie starten met de **Als administrator uitvoeren** optie en typ vervolgens:

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

2.  In Windows PowerShell-sessie zich aanmelden bij Exchange Online met behulp van een account dat is ingeschakeld voor externe toegang tot de Shell. Alle accounts die zijn gemaakt in Exchange Online zijn standaard ingeschakeld voor RAS Shell, maar dit kan worden uitgeschakeld (en ingeschakeld) met behulp van de   [gebruiker instellen &lt; UserIdentity &gt; - RemotePowerShellEnabled](https://technet.microsoft.com/library/jj984292%28v=exchg.160%29.aspx) opdracht.

    Als u wilt aanmelden, type:

    ```
    $Cred = Get-Credential
    ```
    In de **Windows PowerShell referentie aanvraag** dialoogvenster vak, uw Office 365-gebruikersnaam en wachtwoord opgeven.

3.  Verbinding maken met de Exchange Online-service door het uitvoeren van de volgende twee opdrachten:

    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell/ -Credential $Cred -Authentication Basic –AllowRedirection
    ```

    ```
    Import-PSSession $Session
    ```

4.  Geef de locatie van de sleutel van de tenant Azure RMS volgens uw regio:

    Noord-Amerika (en overheid van de abonnementen):

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Voor Europa:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.eu.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Voor Azië:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.ap.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Voor Zuid-Amerika:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.sa.aadrm.com/TenantManagement/ServicePartner.svc"
    ```

5.  Configuratiegegevens importeren uit Azure RMS naar Exchange Online, in de vorm van de publicatie vertrouwd domein (vertrouwde Uitgiftedomein). Dit omvat de sleutel voor Azure RMS-tenant en Azure RMS-sjablonen:

    ```
    Import-RMSTrustedPublishingDomain -RMSOnline -name "RMS Online"
    ```
    In deze opdracht gebruikt we de naam van **RMS Online** voor de algemene naam van het vertrouwde Uitgiftedomein voor Azure RMS in Exchange Online. Nadat het vertrouwde Uitgiftedomein is geïmporteerd, heet het **RMS Online - 1** in Exchange Online.

6.  Azure RMS-functionaliteit inschakelen, zodat IRM-functies beschikbaar voor Exchange Online zijn:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $true
    ```
    Nadat deze opdracht wordt uitgevoerd, wordt automatisch Rights Management ingeschakeld voor de Outlook-client, de Outlook Web-app en Exchange Active Sync.

7.  Test eventueel deze configuratie is voltooid met behulp van de volgende opdracht:

    ```
    Test-IRMConfiguration -Sender <user email address>
    ```
    Bijvoorbeeld: **Test-IRMConfiguration -Sender  adams@contoso.com**

    Met deze opdracht wordt een reeks controles dat verbinding met de service te verifiëren, bij het ophalen van de configuratie, bij het ophalen van URI's, licenties en sjablonen uitgevoerd. In de Windows PowerShell-sessie ziet u de resultaten van elk en aan het einde als alles wat deze controles voor: **HET UITEINDELIJKE RESULTAAT: DOORGEVEN**

8.  De externe PowerShell-sessie verbroken:

    ```
    Remove-PSSession $Session
    ```

Gebruikers kunnen nu hun e-mailberichten worden beveiligd door Azure RMS. Selecteer bijvoorbeeld in de Outlook Web-App **machtigingen instellen** in het menu uitgebreide (**...**), en kies **niet doorsturen** of een van de beschikbare sjablonen om toe te passen van de beveiliging van gegevens naar het e-mailbericht en eventuele bijlagen. Omdat de Outlook Web-App in de cache de gebruikersinterface voor een dag opgeslagen, wacht totdat deze periode moet verstrijken voordat u informatiebeveiliging toepast op e-mailberichten en probeert na deze configuratie opdrachten uit te voeren. Voordat u de gebruikersinterface bijgewerkt om de nieuwe configuratie weer te geven, worden er geen opties uit de **machtigingen instellen** menu.

> [!IMPORTANT]
> Als u nieuwe maakt [aangepaste sjablonen](https://technet.microsoft.com/library/dn642472.aspx) voor Azure RMS of update de sjablonen telkens wanneer u moet de volgende Exchange Online PowerShell opdracht uitvoeren (indien nodig, run stap 2 en 3 eerst) om te synchroniseren van deze wijzigingen naar Exchange Online: `Import-RMSTrustedPublishingDomain -Name "RMS Online - 1" -RefreshTemplates –RMSOnline`

Als een Exchange-beheerder, kunt u nu functies die van toepassing zijn automatisch, informatie over beveiliging configureren, zoals [regels transport](https://technet.microsoft.com/library/dd302432.aspx), [beleid voor gegevensverlies te voorkomen (DLP)](https://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx), en [Voicemail beveiligd](https://technet.microsoft.com/library/dn198211%28v=exchg.150%29.aspx) (Unified Messaging).

Zie de documentatie in de Exchange-bibliotheek voor gedetailleerde instructies voor het configureren van Exchange Online om in te schakelen IRM-functionaliteit. Bijvoorbeeld:

-   [Verbinding maken met de Exchange Online met externe PowerShell](https://technet.microsoft.com/library/jj984289%28v=exchg.160%29.aspx)

-   [IRM voor gebruik van Azure Rights Management configureren](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx)

#### Office 365 codering
Voer de stappen zoals beschreven in de vorige sectie, maar als u niet wilt dat sjablonen worden weergegeven voordat u stap 6, voer de volgende opdracht om te voorkomen dat IRM sjablonen beschikbaar in de Outlook Web-App en de Outlook-client: `Set-IRMConfiguration -ClientAccessServerEnabled $false`

Dan, bent u klaar om te configureren [regels transport](https://technet.microsoft.com/library/dd302432.aspx) automatisch wijzigen van de berichtbeveiliging wanneer ontvangers bevinden zich buiten de organisatie en selecteer de **toepassen Office 365 codering** optie.

Zie voor meer informatie over codering [codering in Office 365](https://technet.microsoft.com/library/dn569286.aspx) in de Exchange-bibliotheek.

### <a name="BKMK_SharePointOnline"></a>SharePoint Online en OneDrive voor bedrijven: IRM-configuratie
SharePoint Online en OneDrive voor zakelijke ter ondersteuning van Azure RMS configureren, moet u eerst de information rights management (IRM)-service voor SharePoint Online inschakelen met behulp van de SharePoint-beheercentrum. Vervolgens eigenaars kunnen IRM beveiligen hun SharePoint-lijsten en documentbibliotheken en kunnen gebruikers hun OneDrive voor zakelijke bibliotheek IRM beveiligen zodat documenten die worden opgeslagen en gedeeld met anderen, automatisch worden beschermd door Azure RMS.

Zie de volgende instructies van de website Office inschakelen van de service rights management (IRM) voor SharePoint Online:

-   [Instellen van Information Rights Management (IRM) in de SharePoint-beheercentrum](http://office.microsoft.com/office365-sharepoint-online-enterprise-help/set-up-information-rights-management-irm-insharepoint-online-HA102895193.aspx)

Deze configuratie wordt uitgevoerd door de beheerder van Office 365.

#### IRM configureren voor bibliotheken en lijsten
Nadat u de IRM-service voor SharePoint hebt ingeschakeld, kunnen eigenaars IRM beveiligen hun SharePoint-documentbibliotheken en lijsten. Zie de volgende van de Office-website voor instructies:

-   [Information Rights Management toepassen op een lijst of bibliotheek](http://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)

Deze configuratie wordt uitgevoerd door de beheerder van de SharePoint-site.

#### <a name="BKMK_OneDrive"></a>IRM configureren voor OneDrive voor bedrijven
Nadat u de IRM-service voor SharePoint Online hebt ingeschakeld, kan gebruikers OneDrive voor Business-documentbibliotheek voor Rights Management-beveiliging worden geconfigureerd.  Gebruikers kunnen configureren dit zelf met behulp van de **instellingen** pictogram in hun OneDrive. Hoewel beheerders kunnen niet met behulp van de SharePoint-beheercentrum Rights Management voor OneDrive voor zakelijke gebruikers configureren, kunt u dit doen met behulp van Windows PowerShell.

> [!NOTE]
> Zie de documentatie Office voor meer informatie over het configureren van OneDrive voor Business[OneDrive voor bedrijven in Office 365 instellen](https://support.office.com/article/Set-up-OneDrive-for-Business-in-Office-365-3e21f8f0-e0a1-43be-aa3e-8c0236bf11bb).

##### Configuratie voor gebruikers
Geef gebruikers deze instructies zodat ze hun OneDrive voor bedrijfs- en hun bestanden business IRM beveiligen configureren kunnen.

1.  In OneDrive, klikt u op de **instellingen** opent u het menu instellingen en klik vervolgens op het pictogram **Site-inhoud**.

2.  De muisaanwijzer op de **documenten** naast elkaar, koos het ovalen (**...**), en klik vervolgens op **instellingen.**

3.  Op de **instellingen** pagina in de **machtigingen en beheer** sectie, klikt u op **Information Rights Management**.

4.  Op de **instellingen van Information Rights Management** optie **machtigingen voor deze bibliotheek bij downloaden beperken** Geef uw keuze van naam en beschrijving voor de machtigingen in en klik eventueel op **Opties weergeven** optionele configuraties configureren en klik vervolgens op **OK**.

    Zie voor meer informatie over de configuratieopties de instructies in [Information Rights Management toepassen op een lijst of bibliotheek](https://support.office.com/article/Apply-Information-Rights-Management-to-a-list-or-library-3bdb5c4e-94fc-4741-b02f-4e7cc3c54aa1) van de documentatie van Office.

Omdat deze configuratie is afhankelijk van gebruikers in plaats van een beheerder hun OneDrive voor zakelijke bibliotheek IRM beveiligen, moet u gebruikers over de voordelen van het beschermen van hun bestanden en hoe u dit doet trainen. Bijvoorbeeld, wordt uitgelegd dat wanneer ze een document van OneDrive voor bedrijf deelt, alleen de personen die zij toestaan toegang dit met de beperkingen die ze configureren tot, zelfs als het bestand is gewijzigd en een andere locatie gekopieerd.

##### Configuratie voor beheerders
Hoewel u niet IRM voor OneDrive voor zakelijke gebruikers configureren via de SharePoint-beheercentrum, kunt u dit doen met behulp van Windows PowerShell. Schakel IRM voor deze bibliotheken door de volgende stappen uit:

1.  Download en installeer de [SharePoint Online SDK voor clientonderdelen](http://www.microsoft.com/en-us/download/details.aspx?id=42038).

2.  Download en installeer de [SharePoint Online Management Shell](http://www.microsoft.com/en-us/download/details.aspx?id=35588).

3.  Kopieer de inhoud van het volgende script en de bestandsnaam Set IRMOnOneDriveForBusiness.ps1 op uw computer.

    *&#42;&#42;Afwijzing&#42;&#42;*: In dit voorbeeld van een script wordt niet ondersteund bij een ondersteuningsprogramma van Microsoft of de service. In dit voorbeeld van een script wordt vermeld in de huidige staat zonder garantie van welke aard dan ook.

    ```
    # Requires Windows PowerShell version 3 <# Description: Configures IRM policy settings for OneDrive for Business and can also be used for SharePoint Online libraries and lists Script Installation Requirements: SharePoint Online Client Components SDK http://www.microsoft.com/en-us/download/details.aspx?id=42038 SharePoint Online Management Shell http://www.microsoft.com/en-us/download/details.aspx?id=35588 ====== #> # URL will be in the format https://<tenant-name>-admin.sharepoint.com $sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com" $tenantAdmin = "admin@contoso.com" $webUrls = @("https://contoso-my.sharepoint.com/personal/user1_contoso_com", "https://contoso-my.sharepoint.com/personal/user2_contoso_com", "https://contoso-my.sharepoint.com/personal/user3_contoso_com") <# As an alternative to specifying the URLs as an array, you can import them from a CSV file (no header, single value per row). Then, use: $webUrls = Get-Content -Path "File_path_and_name.csv" #> $listTitle = "Documents" function Load-SharePointOnlineClientComponentAssemblies { [cmdletbinding()] param() process { # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI try { Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null return $true } catch { if($_.Exception.Message -match "Could not load file or assembly") { Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=42038" } else { Write-Error -Exception $_.Exception } return $false } } } function Load-SharePointOnlineModule { [cmdletbinding()] param() process { do { # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue if(-not $spoModule) { try { Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking return $true } catch { if($_.Exception.Message -match "Could not load file or assembly") { Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=35588" } else { Write-Error -Exception $_.Exception } return $false } } else { return $true } } while(-not $spoModule) } } function Set-IrmConfiguration { [cmdletbinding()] param( [parameter(Mandatory=$true)][Microsoft.SharePoint.Client.List]$List, [parameter(Mandatory=$true)][string]$PolicyTitle, [parameter(Mandatory=$true)][string]$PolicyDescription, [parameter(Mandatory=$false)][switch]$IrmReject, [parameter(Mandatory=$false)][DateTime]$ProtectionExpirationDate, [parameter(Mandatory=$false)][switch]$DisableDocumentBrowserView, [parameter(Mandatory=$false)][switch]$AllowPrint, [parameter(Mandatory=$false)][switch]$AllowScript, [parameter(Mandatory=$false)][switch]$AllowWriteCopy, [parameter(Mandatory=$false)][int]$DocumentAccessExpireDays, [parameter(Mandatory=$false)][int]$LicenseCacheExpireDays, [parameter(Mandatory=$false)][string]$GroupName ) process { Write-Verbose "Applying IRM Configuration on '$($List.Title)'" # reset the value to the default settings $list.InformationRightsManagementSettings.Reset() $list.IrmEnabled = $true # IRM Policy title and description $list.InformationRightsManagementSettings.PolicyTitle       = $PolicyTitle $list.InformationRightsManagementSettings.PolicyDescription = $PolicyDescription # Set additional IRM library settings # Do not allow users to upload documents that do not support IRM $list.IrmReject = $IrmReject.IsPresent $parsedDate = Get-Date if([DateTime]::TryParse($ProtectionExpirationDate, [ref]$parsedDate)) { # Stop restricting access to the library at <date> $list.IrmExpire = $true $list.InformationRightsManagementSettings.DocumentLibraryProtectionExpireDate = $ProtectionExpirationDate } # Prevent opening documents in the browser for this Document Library $list.InformationRightsManagementSettings.DisableDocumentBrowserView = $DisableDocumentBrowserView.IsPresent # Configure document access rights # Allow viewers to print $list.InformationRightsManagementSettings.AllowPrint = $AllowPrint.IsPresent # Allow viewers to run script and screen reader to function on downloaded documents $list.InformationRightsManagementSettings.AllowScript = $AllowScript.IsPresent # Allow viewers to write on a copy of the downloaded document $list.InformationRightsManagementSettings.AllowWriteCopy = $AllowWriteCopy.IsPresent if($DocumentAccessExpireDays) { # After download, document access rights will expire after these number of days (1-365) $list.InformationRightsManagementSettings.EnableDocumentAccessExpire = $true $list.InformationRightsManagementSettings.DocumentAccessExpireDays   = $DocumentAccessExpireDays } # Set group protection and credentials interval if($LicenseCacheExpireDays) { # Users must verify their credentials using this interval (days) $list.InformationRightsManagementSettings.EnableLicenseCacheExpire = $true $list.InformationRightsManagementSettings.LicenseCacheExpireDays   = $LicenseCacheExpireDays } if($GroupName) { # Allow group protection. Default group: $list.InformationRightsManagementSettings.EnableGroupProtection = $true $list.InformationRightsManagementSettings.GroupName             = $GroupName } } end { if($list) { Write-Verbose "Committing IRM configuration settings on '$($list.Title)'" $list.InformationRightsManagementSettings.Update() $list.Update() $script:clientContext.Load($list) $script:clientContext.ExecuteQuery() } } } function Get-CredentialFromCredentialCache { [cmdletbinding()] param([string]$CredentialName) #if( Test-Path variable:\global:CredentialCache ) if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue ) { if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName)) { Write-Verbose "Credential Cache Hit: $CredentialName" return $global:O365TenantAdminCredentialCache[$CredentialName] } } Write-Verbose "Credential Cache Miss: $CredentialName" return $null } function Add-CredentialToCredentialCache { [cmdletbinding()] param([System.Management.Automation.PSCredential]$Credential) if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue)) { Write-Verbose "Initializing the Credential Cache" $global:O365TenantAdminCredentialCache = @{} } Write-Verbose "Adding Credential to the Credential Cache" $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential } # load the required assemblies and Windows PowerShell modules if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return } # Add the credentials to the client context and SharePoint Online service connection # check for cached credentials to use $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin if(-not $o365TenantAdminCredential) { # when credentials are not cached, prompt for the tenant admin credentials $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin" if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 ) { Write-Error -Message "Could not validate the supplied tenant admin credentials" return } # add the credentials to the cache Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential } # connect to Office365 first, required for SharePoint Online cmdlets to run Connect-SPOService -Url $sharepointAdminCenterUrl -Credential $o365TenantAdminCredential # enumerate each of the specified site URLs foreach($webUrl in $webUrls) { $grantedSiteCollectionAdmin = $false try { # establish the client context and set the credentials to connect to the site $script:clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($webUrl) $script:clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password) # initialize the site and web context $script:clientContext.Load($script:clientContext.Site) $script:clientContext.Load($script:clientContext.Web) $script:clientContext.ExecuteQuery() # load and ensure the tenant admin user account if present on the target SharePoint site $tenantAdminUser = $script:clientContext.Web.EnsureUser($o365TenantAdminCredential.UserName) $script:clientContext.Load($tenantAdminUser) $script:clientContext.ExecuteQuery() # check if the tenant admin is a site admin if( -not $tenantAdminUser.IsSiteAdmin ) { try { # grant the tenant admin temporary admin rights to the site collection Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $true | Out-Null $grantedSiteCollectionAdmin = $true } catch { Write-Error $_.Exception return } } try { # load the list orlibrary using CSOM $list = $null $list = $script:clientContext.Web.Lists.GetByTitle($listTitle) $script:clientContext.Load($list) $script:clientContext.ExecuteQuery() # **************  ADMIN INSTRUCTIONS  ************** # If necessary, modify the following Set-IrmConfiguration parameters to match your required values # The supplied options and values are for example only # Example that shows the Set-IrmConfiguration command with all parameters: Set-IrmConfiguration -List $list -PolicyTitle "Protected Files" -PolicyDescription "This policy restricts access to authorized users" -IrmReject -ProtectionExpirationDate $(Get-Date).AddDays(180) -DisableDocumentBrowserView -AllowPrint -AllowScript -AllowWriteCopy -LicenseCacheExpireDays 25 -DocumentAccessExpireDays 90 Set-IrmConfiguration -List $list -PolicyTitle "Protected Files" -PolicyDescription "This policy restricts access to authorized users" } catch { Write-Error -Message "Error setting IRM configuration on site: $webUrl.`nError Details: $($_.Exception.ToString())" } } finally { if($grantedSiteCollectionAdmin) { # remove the temporary admin rights to the site collection Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $false | Out-Null } } } Disconnect-SPOService -ErrorAction SilentlyContinue
    ```

4.  Bekijk het script en de volgende wijzigingen aanbrengen:

    1.  Zoeken naar `$sharepointAdminCenterUrl` en de waarde bijvoorbeeld vervangen door de URL van uw eigen SharePoint admin center.

        Vindt u deze waarde als de basis-URL wanneer u gaat u naar de SharePoint-beheercentrum en de volgende notatie heeft: https://*&lt; tenant_name &gt;*-admin.sharepoint.com

        Bijvoorbeeld als de naam van de tenant is 'contoso', wilt u opgeven: **https://contoso-admin.sharepoint.com**

    2.  Zoeken naar `$tenantAdmin` en de waarde bijvoorbeeld vervangen door uw eigen account volledig gekwalificeerde hoofdbeheerder voor Office 365.

        Deze waarde is hetzelfde als die u gebruikt voor aanmelding bij het Office 365-beheerportal als globale beheerder en heeft de volgende indeling: gebruikersnaam @*&lt; domeinnaam tenant &gt;*.com

        Bijvoorbeeld als de gebruikersnaam voor Office 365-hoofdbeheerder 'admin' voor het domein van de tenant 'contoso.com', dat u wilt opgeven: **admin@contoso.com**

    3.  Zoeken naar `$webUrls` en de voorbeeldwaarden vervangen door uw gebruikers OneDrive voor zakelijke web-URL's, toevoegen of verwijderen van alle items die u nodig hebt.

        U kunt ook een overzicht van opmerkingen in het script over het vervangen van deze matrix door te importeren een. CSV-bestand met alle URL's die u nodig hebt om te configureren.  We hebben een ander voorbeeld van een script om automatisch zoeken en ophalen van de URL's om in te vullen dit opgegeven. CSV-bestand. Wanneer u klaar om dit te doen bent, vouw de [Aanvullende script om alle OneDrive voor zakelijke URL naar een. CSV-bestand](#BKMK_Script_OD4B_URLS) sectie direct nadat deze stappen.

        De web-URL voor de gebruiker OneDrive voor bedrijven is in de volgende indeling: https://*&lt; tenant naam &gt;*-my.sharepoint.com/personal/*&lt; gebruikersnaam &gt;*_*&lt; tenant naam &gt;*_com

        Bijvoorbeeld als de gebruiker in de tenant contoso heeft de naam van een gebruiker van "rsimone", dat u wilt opgeven: **https://contoso-my.sharepoint.com/personal/rsimone_contoso_com**

    4.  Omdat we met behulp van het script OneDrive voor zakelijke configureren, niet de waarde van wijzigen **Documents** voor de `$listTitle` variabele.

    5.  Zoeken naar `ADMIN INSTRUCTIONS`. Als u geen wijzigingen in deze sectie aanbrengen, wordt OneDrive voor bedrijven van de gebruiker geconfigureerd voor IRM met de titel van het beleid van 'Beveiligde bestanden' en de beschrijving van "dit beleid is alleen toegankelijk voor geautoriseerde gebruikers".  Er is geen IRM-opties worden ingesteld, die is waarschijnlijk geschikt is voor de meeste omgevingen. U kunt echter de voorgestelde beleid titel en beschrijving wijzigen en eventuele andere IRM-opties die geschikt voor uw omgeving zijn ook toevoegen. Zie het voorbeeld commentaar in het script uw eigen set parameters voor de opdracht Set IrmConfiguration samenstellen.

5.  Sla het script en ondertekenen. Als u het script (veiliger) niet aanmeldt, moet u Windows PowerShell geconfigureerd op de computer niet-ondertekende scripts worden uitgevoerd. Voer hiervoor een Windows PowerShell-sessie met de **als Administrator uitvoeren** optie en typ: **Set-ExecutionPolicy Unrestricted**. Deze configuratie kan echter alle niet-ondertekende-scripts uitgevoerd (minder veilig).

    Zie voor meer informatie over het ondertekenen van Windows PowerShell-scripts [about_Signing](https://technet.microsoft.com/library/hh847874.aspx) in de Documentatiebibliotheek PowerShell.

6.  Voer het script en als u wordt gevraagd, het wachtwoord voor het Office 365-beheerdersaccount opgeven. Als u het script wijzigen en in dezelfde Windows PowerShell-sessie worden uitgevoerd, wordt u niet gevraagd om referenties.

> [!TIP]
> U kunt ook dit script IRM configureren voor een SharePoint Online bibliotheek. Voor deze configuratie wordt waarschijnlijk gewenste extra optie **kunnen gebruikers documenten uploaden die IRM niet ondersteunen geen**, om ervoor te zorgen dat de bibliotheek bevat alleen beveiligde documenten.    Toevoegen als u wilt dat de `-IrmReject` parameter voor de opdracht Set IrmConfiguration in het script.
> 
> U moet ook wijzigen de `$webUrls` variabele (bijvoorbeeld **https://contoso.sharepoint.com**) en  `$listTitle` variabele (bijvoorbeeld **$Reports**).

Als u IRM uitschakelen voor OneDrive voor zakelijke bibliotheken van de gebruiker moet, vouw de [Script IRM uitschakelen voor OneDrive voor bedrijven](#BKMK_Script_OD4B_DisableIRM) sectie.

###### <a name="BKMK_Script_OD4B_URLS"></a>Aanvullende script om alle OneDrive voor zakelijke URL naar een. CSV-bestand
Voor stap 4c hierboven, kunt u de volgende Windows PowerShell-script om op te halen van de URL's voor alle gebruikers OneDrive voor Business-bibliotheken controleert u, indien nodig bewerken en vervolgens importeren in de hoofdbibliotheek script.

Dit script moet ook de [SharePoint Online SDK voor clientonderdelen](http://www.microsoft.com/en-us/download/details.aspx?id=42038) en de [SharePoint Online Management Shell](http://www.microsoft.com/en-us/download/details.aspx?id=35588). Volg de instructies te kopiëren en plakken, sla het bestand lokaal (bijvoorbeeld ' rapport-OneDriveForBusinessSiteInfo.ps1"), wijzigen de   `$sharepointAdminCenterUrl` en `$tenantAdmin` waarden als voordat en voer het script.

*&#42;&#42;Afwijzing&#42;&#42;*: In dit voorbeeld van een script wordt niet ondersteund bij een ondersteuningsprogramma van Microsoft of de service. In dit voorbeeld van een script wordt vermeld in de huidige staat zonder garantie van welke aard dan ook.

```
# Requires Windows PowerShell version 3 <# Description: Queries the search service of an Office 365 tenant to retrieve all OneDrive for Business sites. Details of the discovered sites are written to a .CSV file (by default,"OneDriveForBusinessSiteInfo_<date>.csv"). Script Installation Requirements: SharePoint Online Client Components SDK http://www.microsoft.com/en-us/download/details.aspx?id=42038 SharePoint Online Management Shell http://www.microsoft.com/en-us/download/details.aspx?id=35588 ====== #> # URL will be in the format https://<tenant-name>-admin.sharepoint.com $sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com" $tenantAdmin = "admin@contoso.onmicrosoft.com" $reportName = "OneDriveForBusinessSiteInfo_$((Get-Date).ToString("yyyy-MM-dd_hh.mm.ss")).csv" $oneDriveForBusinessSiteUrls= @() $resultsProcessed = 0 function Load-SharePointOnlineClientComponentAssemblies { [cmdletbinding()] param() process { # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI try { Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null return $true } catch { if($_.Exception.Message -match "Could not load file or assembly") { Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=42038" } else { Write-Error -Exception $_.Exception } return $false } } } function Load-SharePointOnlineModule { [cmdletbinding()] param() process { do { # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue if(-not $spoModule) { try { Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking return $true } catch { if($_.Exception.Message -match "Could not load file or assembly") { Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=35588" } else { Write-Error -Exception $_.Exception } return $false } } else { return $true } } while(-not $spoModule) } } function Get-CredentialFromCredentialCache { [cmdletbinding()] param([string]$CredentialName) #if( Test-Path variable:\global:CredentialCache ) if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue ) { if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName)) { Write-Verbose "Credential Cache Hit: $CredentialName" return $global:O365TenantAdminCredentialCache[$CredentialName] } } Write-Verbose "Credential Cache Miss: $CredentialName" return $null } function Add-CredentialToCredentialCache { [cmdletbinding()] param([System.Management.Automation.PSCredential]$Credential) if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue)) { Write-Verbose "Initializing the Credential Cache" $global:O365TenantAdminCredentialCache = @{} } Write-Verbose "Adding Credential to the Credential Cache" $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential } # load the required assemblies and Windows PowerShell modules if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return } # Add the credentials to the client context and SharePoint Online service connection # check for cached credentials to use $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin if(-not $o365TenantAdminCredential) { # when credentials are not cached, prompt for the tenant admin credentials $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin" if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 ) { Write-Error -Message "Could not validate the supplied tenant admin credentials" return } # add the credentials to the cache Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential } # establish the client context and set the credentials to connect to the site $clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($sharepointAdminCenterUrl) $clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password) # run a query against the Office 365 tenant search service to retrieve all OneDrive for Business URLs do { # build the query object $query = New-Object Microsoft.SharePoint.Client.Search.Query.KeywordQuery($clientContext) $query.TrimDuplicates        = $false $query.RowLimit              = 500 $query.QueryText             = "SPSiteUrl:'/personal/' AND contentclass:STS_Site" $query.StartRow              = $resultsProcessed $query.TotalRowsExactMinimum = 500000 # run the query $searchExecutor = New-Object Microsoft.SharePoint.Client.Search.Query.SearchExecutor($clientContext) $queryResults = $searchExecutor.ExecuteQuery($query) $clientContext.ExecuteQuery() # enumerate the search results and store the site URLs $queryResults.Value[0].ResultRows | % { $oneDriveForBusinessSiteUrls += $_.Path $resultsProcessed++ } } while($resultsProcessed -lt $queryResults.Value.TotalRows) $oneDriveForBusinessSiteUrls | Out-File -FilePath $reportName
```

###### <a name="BKMK_Script_OD4B_DisableIRM"></a>Script IRM uitschakelen voor OneDrive voor bedrijven
Script in het volgende voorbeeld gebruiken als u IRM voor OneDrive voor zakelijke gebruikers uitschakelen.

Dit script moet ook de [SharePoint Online SDK voor clientonderdelen](http://www.microsoft.com/en-us/download/details.aspx?id=42038) en de [SharePoint Online Management Shell](http://www.microsoft.com/en-us/download/details.aspx?id=35588). Kopiëren en plakken van de inhoud, het bestand lokaal opslaan (bijvoorbeeld ' Disable-IRMOnOneDriveForBusiness.ps1") en wijzigen de   `$sharepointAdminCenterUrl` en `$tenantAdmin` waarden. Handmatig de OneDrive voor zakelijke URL's opgeven of het script in de vorige sectie gebruiken zodat deze importeren en voer het script.

*&#42;&#42;Afwijzing&#42;&#42;*: In dit voorbeeld van een script wordt niet ondersteund bij een ondersteuningsprogramma van Microsoft of de service. In dit voorbeeld van een script wordt vermeld in de huidige staat zonder garantie van welke aard dan ook.

```
# Requires Windows PowerShell version 3 <# Description: Disables IRM for OneDrive for Business and can also be used for SharePoint Online libraries and lists Script Installation Requirements: SharePoint Online Client Components SDK http://www.microsoft.com/en-us/download/details.aspx?id=42038 SharePoint Online Management Shell http://www.microsoft.com/en-us/download/details.aspx?id=35588 ====== #> $sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com" $tenantAdmin = "admin@contoso.com" $webUrls = @("https://contoso-my.sharepoint.com/personal/user1_contoso_com", "https://contoso-my.sharepoint.com/personal/user2_contoso_com", "https://contoso-my.sharepoint.com/personal/person3_contoso_com") <# As an alternative to specifying the URLs as an array, you can import them from a CSV file (no header, single value per row). Then, use: $webUrls = Get-Content -Path "File_path_and_name.csv" #> $listTitle = "Documents" function Load-SharePointOnlineClientComponentAssemblies { [cmdletbinding()] param() process { # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI try { Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null return $true } catch { if($_.Exception.Message -match "Could not load file or assembly") { Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=42038" } else { Write-Error -Exception $_.Exception } return $false } } } function Load-SharePointOnlineModule { [cmdletbinding()] param() process { do { # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue if(-not $spoModule) { try { Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking return $true } catch { if($_.Exception.Message -match "Could not load file or assembly") { Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=35588" } else { Write-Error -Exception $_.Exception } return $false } } else { return $true } } while(-not $spoModule) } } function Remove-IrmConfiguration { [cmdletbinding()] param( [parameter(Mandatory=$true)][Microsoft.SharePoint.Client.List]$List ) process { Write-Verbose "Disabling IRM Configuration on '$($List.Title)'" $List.IrmEnabled = $false $List.IrmExpire  = $false $List.IrmReject  = $false $List.InformationRightsManagementSettings.Reset() } end { if($List) { Write-Verbose "Committing IRM configuration settings on '$($list.Title)'" $list.InformationRightsManagementSettings.Update() $list.Update() $script:clientContext.Load($list) $script:clientContext.ExecuteQuery() } } } function Get-CredentialFromCredentialCache { [cmdletbinding()] param([string]$CredentialName) #if( Test-Path variable:\global:CredentialCache ) if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue ) { if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName)) { Write-Verbose "Credential Cache Hit: $CredentialName" return $global:O365TenantAdminCredentialCache[$CredentialName] } } Write-Verbose "Credential Cache Miss: $CredentialName" return $null } function Add-CredentialToCredentialCache { [cmdletbinding()] param([System.Management.Automation.PSCredential]$Credential) if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue)) { Write-Verbose "Initializing the Credential Cache" $global:O365TenantAdminCredentialCache = @{} } Write-Verbose "Adding Credential to the Credential Cache" $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential } # load the required assemblies and Windows PowerShell modules if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return } # Add the credentials to the client context and SharePoint Online service connection # check for cached credentials to use $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin if(-not $o365TenantAdminCredential) { # when credentials are not cached, prompt for the tenant admin credentials $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin" if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 ) { Write-Error -Message "Could not validate the supplied tenant admin credentials" return } # add the credentials to the cache Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential } # connect to Office365 first, required for SharePoint Online cmdlets to run Connect-SPOService -Url $sharepointAdminCenterUrl -Credential $o365TenantAdminCredential # enumerate each of the specified site URLs foreach($webUrl in $webUrls) { $grantedSiteCollectionAdmin = $false try { # establish the client context and set the credentials to connect to the site $script:clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($webUrl) $script:clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password) # initialize the site and web context $script:clientContext.Load($script:clientContext.Site) $script:clientContext.Load($script:clientContext.Web) $script:clientContext.ExecuteQuery() # load and ensure the tenant admin user account if present on the target SharePoint site $tenantAdminUser = $script:clientContext.Web.EnsureUser($o365TenantAdminCredential.UserName) $script:clientContext.Load($tenantAdminUser) $script:clientContext.ExecuteQuery() # check if the tenant admin is a site admin if( -not $tenantAdminUser.IsSiteAdmin ) { try { # grant the tenant admin temporary admin rights to the site collection Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $true | Out-Null $grantedSiteCollectionAdmin = $true } catch { Write-Error $_.Exception return } } try { # load the list orlibrary using CSOM $list = $null $list = $script:clientContext.Web.Lists.GetByTitle($listTitle) $script:clientContext.Load($list) $script:clientContext.ExecuteQuery() Remove-IrmConfiguration -List $list } catch { Write-Error -Message "Error setting IRM configuration on site: $webUrl.`nError Details: $($_.Exception.ToString())" } } finally { if($grantedSiteCollectionAdmin) { # remove the temporary admin rights to the site collection Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $false | Out-Null } } } Disconnect-SPOService -ErrorAction SilentlyContinue
```

## <a name="BKMK_Office2013Configuration"></a>Office 2016 en Office 2013: Configuratie voor clients
Azure RMS wordt standaard ondersteund door deze nieuwere versies van Office, is geen configuratie van clientcomputer vereist voor de ondersteuning van de functies van information rights management (IRM) voor toepassingen zoals Word, Excel, PowerPoint, Outlook en de Outlook Web-App. Alle gebruikers hebben om te doen is aanmelden bij hun Office-toepassingen met hun [!INCLUDE[o365_1](../Token/o365_1_md.md)] referenties en ze kunnen beschermen bestanden en e-mailberichten en gebruik van bestanden en e-mailberichten die zijn beveiligd door anderen.

We raden echter aan dat u deze toepassingen aanvullen met de Rights Management delen van de toepassing, zodat gebruikers van de voordelen van het Office-invoegtoepassing profiteren. Zie voor meer informatie de [Rights Management-toepassing delen: Installatie en configuratie voor clients](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharingApp) in dit onderwerp.

## <a name="BKMK_Office2010Configuration"></a>Office 2010: Configuratie voor clients
Voor clientcomputers Azure RMS met Office 2010 gebruiken als ze de delen Rights Management-toepassing voor Windows hebt geïnstalleerd. Er is geen verder configuratie vereist is anders dan gebruikers zich met aanmelden moeten hun [!INCLUDE[o365_1](../Token/o365_1_md.md)] referenties en ze kunnen vervolgens bestanden beveiligen en bestanden die zijn beveiligd door anderen.

Zie voor meer informatie over de Rights Management-toepassing delen, de [Rights Management-toepassing delen: Installatie en configuratie voor clients](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharingApp) in dit onderwerp.

## <a name="BKMK_SharingApp"></a>Rights Management-toepassing delen: Installatie en configuratie voor clients
De RMS (Rights Management) voor het delen van toepassing is vereist voor clientcomputers Azure RMS gebruiken met Office 2010 en aanbevolen voor alle computers en mobiele apparaten die ondersteuning van Azure RMS. De RMS sharing van toepassing is geïntegreerd met Office toepassingen door de installatie van een Office-invoegtoepassing zodat gebruikers kunnen gemakkelijk voor bestanden en de e-mailberichten rechtstreeks vanuit het lint. Biedt ook algemene beveiliging voor de verschillende bestandstypen worden niet ondersteund door Azure RMS en het bijhouden van de site voor gebruikers document bijhouden en bestanden die ze hebben beveiligd intrekken.

### <a name="BKMK_SharingAppforWindows"></a>De RMS sharing van toepassing voor Windows: Installatie en configuratie
Als u wilt installeren en configureren van de RMS sharing toepassing voor Windows voor implementatie in een onderneming, Zie de [delen toepassing Rights Management-beheerdershandleiding](http://technet.microsoft.com/library/dn339003.aspx).

> [!TIP]
> Als u wilt snel installeren en testen van de RMS sharing toepassing voor één computer, Zie [Download en installeer de Rights Management-toepassing delen](http://technet.microsoft.com/library/dn574734.aspx) van de [delen toepassing Rights Management-handleiding](http://technet.microsoft.com/library/dn339006.aspx).

### <a name="BKMK_SharingAppMovileDevices"></a>De RMS sharing van toepassing voor mobiele platforms: Installatie
Als u wilt installeren de RMS sharing toepassing voor mobiele platforms, kunt u de relevante app downloaden via de koppelingen in de [pagina Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970). Er zijn geen configuratie is Azure RMS gebruiken met deze app vereist.

## <a name="BKMK_RMSAPIs"></a>Andere toepassingen die ondersteuning voor de RMS APIs: Installatie en configuratie
Deze categorie bevat line of business-toepassingen die intern zijn geschreven met behulp van de RMS-SDK en toepassingen van softwareleveranciers die zijn geschreven met behulp van de RMS-SDK. Volg de instructies die zijn opgegeven met de toepassing voor deze toepassingen.

## Volgende stappen
Nadat u uw toepassingen ter ondersteuning van Azure Rights Management hebt geconfigureerd, gebruikt u de [Azure Rights Management-implementatieschema](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) om te controleren of er andere configuratiestappen die u kunt doen zijn voor de implementatie [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] gebruikers en beheerders. Als dit niet het geval is, Zie [Met behulp van Azure Rights Management](../Topic/Using_Azure_Rights_Management.md) voor de volgende stappen.

## Zie ook
[Azure Rights Management configureren](../Topic/Configuring_Azure_Rights_Management.md)

