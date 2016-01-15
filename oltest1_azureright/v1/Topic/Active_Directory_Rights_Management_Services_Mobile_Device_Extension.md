---
description: na
keywords: na
title: Active Directory Rights Management Services Mobile Device Extension
search: na
ms.date: na
ms.tgt_pltfrm: na
ms.assetid: a69ead9d-7dd3-4b38-9830-4728e9757341
robots: noindex,nofollow
---
# Uitbreiding voor mobiele apparaten voor Active Directory Rights Management Services
De extensie van de Active Directory Rights Management Services (AD RMS) voor mobiele apparaten wordt bovenop een bestaande AD RMS-installatie uitgevoerd. Hiermee kunnen gebruikers die mobiele apparaten hebben gevoelige gegevens beveiligen en gebruiken wanneer hun apparaat de nieuwste RMS-client ondersteunt en apps met RMS gebruikt. Gebruikers op deze apparaten kunnen bijvoorbeeld het volgende doen:

-   De RMS-app voor delen gebruiken om beveiligde tekstbestanden te gebruiken in verschillende indelingen (zoals .txt, .csv en .xml).

-   De RMS-app voor delen gebruiken om beveiligde afbeeldingsbestanden te gebruiken in verschillende indelingen (zoals .jpg, .gif en .tif).

-   De RMS-app voor delen gebruiken om bestanden te openen die algemeen beveiligd zijn (.pfile-indeling).

-   De RMS-app voor delen gebruiken om afbeeldingsbestanden op het apparaat te beveiligen.

-   Een PDF-viewer met RMS gebruiken voor mobiele apparaten om PDF-bestanden te openen die beveiligd zijn met de RMS-toepassing voor delen voor Windows, of door een andere toepassing met RMS.

-   Andere apps van softwareleveranciers gebruiken die apps leveren met RMS en bestandstypen ondersteunen die standaard RMS ondersteunen.

-   Uw eigen ontwikkelde apps met RMS gebruiken die zijn geschreven met de RMS SDK.

> [!NOTE]
> U kunt RMS-app voor delen downloaden van de pagina [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) op de website van Microsoft.
> 
> Zie voor meer informatie over de verschillende typen die RMS ondersteunt de sectie [Ondersteunde bestandstypen en bestandsnaamextensies](http://technet.microsoft.com/library/dn339003.aspx) in de Beheerdershandleiding voor de Rights Management-toepassing voor delen.

U hoeft de mobiele apparaat-extensie niet te gebruiken om beveiligde e-mail te autoriseren op apparaten als deze mailtoepassingen gebruiken die Exchange ActiveSync IRM ondersteunen. Deze ondersteuning voor RMS en mobiele apparaten is geïntroduceerd met Exchange 2010 Service Pack 1.

Gebruik de volgende secties om de Active Directory Rights Management Services (AD RMS)-extensie voor mobiele apparaten te implementeren:

-   [Prerequisites for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_Preqs)

    -   [Configuring AD FS for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS)

    -   [Configuring AD FS for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS)

-   [Specifying the DNS SRV records for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_SRV)

-   [Deploying the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_Deploy)

## <a name="BKMK_Preqs"></a>Vereisten voor de AD RMS-extensie voor mobiele apparaten
Voordat u de AD RMS-extensie voor mobiele apparaten installeert, moet u ervoor zorgen dat deze afhankelijkheden op locatie zijn.

|Vereiste|Meer informatie|
|------------|-------------------|
|Een bestaande AD RMS-implementatie op Windows Server 2012 R2 of Windows Server 2012. **Note:** AD RMS moet een volledige op Microsoft SQL Server-gebaseerde database gebruiken op een afzonderlijke server en niet Windows Internal Database, welke vaak wordt gebruikt voor het testen op dezelfde server.|Zie voor documentatie over AD RMS [Active Directory Rights Management Services](http://technet.microsoft.com/library/hh831364.aspx) in de bibliotheek voor Windows Server.|
|AD FS is geïmplementeerd op Windows Server 2012 R2|Zie voor documentatie over AD FS de [Windows Server 2012 R2 AD FS Deployment Guide](http://technet.microsoft.com/library/dn486820.aspx) in de Windows Server Library.<br /><br />AD FS moet worden geconfigureerd voor de extensie van het mobiele apparaat. Zie voor instructies de sectie [Configuring AD FS for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS) in dit onderwerp.|
|SRV-records in DNS|Een of meer SRV-records maken in uw bedrijfsdomein of -domeinen:<br /><br />-   Een record voor elk e-maildomeinachtervoegsel dat door gebruikers wordt gebruikt<br />-   Een record voor elke FQDN die wordt gebruikt door uw RMS-clusters om inhoud te beveiligen<br /><br />Wanneer gebruikers het e-mailadres van hun mobiele apparaat opgeven, wordt het domeinachtervoegsel gebruikt om te bepalen of ze een AD RMS-infrastructuur of Azure RMS moeten gebruiken. Als de SRV-record wordt gevonden, worden clients omgeleid naar de AD RMS-server die op die url reageert.<br /><br />Als gebruikers beveiligde inhoud gebruiken met een mobiel apparaat, dan zoekt de zoekt de clienttoepassing in DNS naar een record die overeenkomt met de FQDN in de url of het cluster dat de inhoud beveiligd. Het apparaat wordt vervolgens omgeleid naar het AD RMS-cluster dat is opgegeven in de DNS-record en krijgt een licentie om de inhoud te openen. In de meeste gevallen is het RMS-cluster hetzelfde als het RMS-cluster dat de inhoud beveiligt.<br /><br />Zie voor meer informatie over het opgeven van de SRV-records de sectie [Specifying the DNS SRV Records for the AD RMS mobile device extension](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_SRV) in dit onderwerp.|
|Huidige ondersteunde clients:<br /><br />-   Android-apparaten met de nieuwste versie van de RMS-app voor delen voor Android|Minimale versie van Android 4.0.3.<br /><br />Download de RMS-app voor delen voor Android van de [Microsoft Connect-site](https://connect.microsoft.com/site1170/Downloads) en sideload deze op het apparaat.|

### <a name="BKMK_ADFS"></a>AD FS voor de AD RMS-extensie voor mobiele apparaten configureren
U moet eerst de AD FS configureren en vervolgens de RMS-app voor delen voor Android autoriseren.

##### Stap 1: AD FS configureren

-   U kunt een Windows PowerShell-script uitvoeren om AD FS automatisch te configureren voor ondersteuning van de AD RMS-extensie voor mobiele apparaten, of u kunt de configuratieopties en -waarden handmatig opgeven:

    -   Kopieer en plak het volgende in een Windows PowerShell-scriptbestand om AD FS automatisch te configureren en voer het vervolgens uit:

        ```
        # This Script Configures the Microsoft Rights Management Mobile Device Extension and Claims used in the ADFS Server

        # Check if Microsoft Rights Management Mobile Device Extension is configured on the Server 
        $CheckifConfigured = Get-AdfsRelyingPartyTrust -Identifier "api.rms.rest.com"
        if ($CheckifConfigured)
        {
        Write-Host "api.rms.rest.com Identifer used for Microsoft Rights Management Mobile Device Extension is already configured on this Server"
        Write-Host $CheckifConfigured 
        }
        else
        {
        Write-Host "Configuring  Microsoft Rights Management Mobile Device Extension "

        # TransformaRules used by Microsoft Rights Management Mobile Device Extension
        # Claims: E-mail, UPN and ProxyAddresses
        $TransformRules = @"
        @RuleTemplate = "LdapClaims"
        @RuleName = "Jwt Token"
        c:[Type ==
        "http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname",
        Issuer == "AD AUTHORITY"]
         => issue(store = "Active Directory", types =
        ("http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress",
        "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn",
        "http://schemas.xmlsoap.org/claims/ProxyAddresses"), query =
        ";mail,userPrincipalName,proxyAddresses;{0}", param = c.Value);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through"
        c:[Type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress"]
         => issue(claim = c);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through"
        c:[Type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"]
         => issue(claim = c);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through Proxy addresses"
        c:[Type == "http://schemas.xmlsoap.org/claims/ProxyAddresses"]
         => issue(claim = c);
        "@

        # AuthorizationRules used by Microsoft Rights Management Mobile Device Extension
        # Allow All users
        $AuthorizationRules = @"
        @RuleTemplate = "AllowAllAuthzRule"
         => issue(Type = "http://schemas.microsoft.com/authorization/claims/permit",
        Value = "true");
        "@

        # Add a Relying Part Truest with Name -"Microsoft Rights Management Mobile Device Extension" Identifier "api.rms.rest.com"
        Add-ADFSRelyingPartyTrust -Name "Microsoft Rights Management Mobile Device Extension" -Identifier "api.rms.rest.com" -IssuanceTransformRules $TransformRules -IssuanceAuthorizationRules  $AuthorizationRules

        Write-Host "Microsoft Rights Management Mobile Device Extension Configured"
        }
        ```

    -   Gebruik deze instellingen om AD FS handmatig te configureren:

        |Configuratie|Waarde|
        |----------------|----------|
        |**Relying Party Trust**|api.rms.rest.com|
        |**Claimregel**|**Kenmerkopslag**:  Active Directory<br /><br />**E-mailadressen**:  E-mailadres<br /><br />**Principal-naam van gebruiker**:  UPN<br /><br />**Proxy-adres**:  https://schemas.xmlsoap.org/claims/ProxyAddresses|

##### Stap 2: De RMS-app voor delen voor Android autoriseren

-   Voer de volgende Windows PowerShell-opdracht uit om Android-apparaten te ondersteunen:

    ```
    Add-AdfsClient -Name "RMSsharingAndroid" -ClientId "com.microsoft.ipviewer" -RedirectUri @("com.microsoft.ipviewer://authorize")
    ```

### <a name="BKMK_SRV"></a>DNS SRV-records opgeven voor de AD RMS-extensie voor mobiele apparaten
U moet DNS SRV-records maken voor elk e-maildomein dat uw gebruikers gebruiken. Als al uw gebruikers onderliggende domeinen gebruiken voor een enkel bovenliggend domein en alle gebruikers van deze aaneengesloten naamruimte hetzelfde RMS-cluster gebruiken, dan kunt u één SRV-record gebruiken in het bovenliggend domein en RMS zal de juiste DNS-records vinden.

De SRV-records hebben de volgende indeling: _rmsdisco._http._tcp. *&lt;emailsuffix&gt;**&lt;portnumber&gt;**&lt;RMSClusterFQDN&gt;*

Als uw organisatie bijvoorbeeld gebruikers heeft met de volgende e-mailadressen:

-   user@contoso.com

-   user@sales.contoso.com

-   user@fabrikam.com

- en er zijn geen andere onderliggende domeinen voor contoso.com die gebruikmaken van een ander RMS-cluster dan de cluster met de naam **rmsserver.contoso.com**, maakt u twee DNS SRV-records die deze waarden hebben:

-   _rmsdisco._http._tcp.contoso.com 443 rmsserver.contoso.com

-   _rmsdisco._http._tcp.fabrikam.com 443 rmsserver.contoso.com

Naast deze DNS SRV-records voor uw e-maildomeinen, moet u nog een DNS SRV-record maken in de gebruikersdomeinen. Deze record moet de url's van uw RMS-cluster opgeven dat de inhoud beveiligt. Elk bestand dat wordt beveiligd door RMS bevat een url naar het cluster welke dat bestand heeft beveiligd. Mobiele apparaten gebruiken de DNS SRV-record en de url-FQDN die in de record is opgegeven om het overeenkomstige RMS-cluster te vinden dat mobiele apparaten ondersteunt.

Als uw RMS-cluster bijvoorbeeld **rmsserver.contoso.com** is, maakt u een DNS SRV-record met de volgende waarden: **_rmsdisco._http._tcp.rmsserver.contoso.com 443 rmsserver.contoso.com**

## <a name="BKMK_Deploy"></a>AD RMS-extensie voor mobiele apparaten implementeren
Zorg voordat u de AD RMS-extensie voor mobiele apparaten installeert dat de vereisten van de voorgaande sectie aanwezig zijn en dat u de url van uw AD FS-server weet. Ga als volgt verder:

1.  Download de AD RMS-extensie voor mobiele apparaten van de [Microsoft Connect-site](http://go.microsoft.com/fwlink/?LinkId=397245).

2.  Voer Setup.exe uit om de wizard Active Directory Rights Management Services Mobile Device Extension Setup te starten.

3.  Geef, wanneer u daarom wordt gevraagd, de URL op van de AD FS-server op die u eerder hebt geconfigureerd.

4.  Voltooi de wizard.

Voer deze wizard uit op alle knooppunten in uw RMS-cluster.

