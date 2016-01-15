---
description: na
keywords: na
title: Configuring Super Users for Azure Rights Management and Discovery Services or Data Recovery
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: acb4c00b-d3a9-4d74-94fe-91eeb481f7e3
---
# Supergebruikers configureren voor Azure Rights Management en van detectieservices of gegevens te herstellen
De functie supergebruiker van Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS), zorgt u ervoor gemachtigde personen en services altijd kunnen lezen en controleren van de gegevens die Azure RMS voor uw organisatie beveiligt. En indien nodig, de beveiliging opheffen of wijzig de beveiliging die eerder is toegepast. Een supergebruiker heeft altijd volledige eigendomsrechten voor alle licenties die door de organisatie RMS tenant is verleend. Deze mogelijkheid is ook wel "redeneren over gegevens" genoemd en een essentieel onderdeel is van de controle van uw organisatie gegevens te behouden. Bijvoorbeeld, gebruikt u deze functie voor een van de volgende scenario's:

-   Verlaat de organisatie van een werknemer en moet u de bestanden die ze beveiligd lezen.

-   Een IT-beheerder moet het huidige protection beleid dat is geconfigureerd om de bestanden verwijderen en toepassen van een nieuw beleid voor beveiliging.

-   Exchange-Server moet index postvakken voor zoekopdrachten.

-   U hebt een bestaande IT-services voor data gegevensverlies te voorkomen (DLP)-oplossingen, versleuteling inhoud gateways (CEG) en anti-malware-producten die u nodig hebt om te controleren van bestanden die al zijn beveiligd.

-   U moet bulksgewijs decoderen bestanden voor controle, juridische of andere redenen compatibiliteit.

Standaard, de functie super-gebruiker niet is ingeschakeld en er zijn geen gebruikers deze rol zijn toegewezen. Er wordt automatisch voor u ingeschakeld als u de connector Rights Management voor Exchange configureren en is niet vereist voor de standaard-services die Exchange Online, SharePoint Online of SharePoint-Server worden uitgevoerd.

Als u nodig hebt supergebruiker handmatig inschakelen, gebruikt u de Windows PowerShell-cmdlet [Enable AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629400.aspx), en vervolgens toewijzen gebruikers (of serviceaccounts) indien nodig met behulp van de [toevoegen AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629411.aspx) cmdlet. U kunt een of meerdere Supergebruikers hebt voor uw organisatie, maar moet u afzonderlijke gebruikers; toevoegen groepen worden niet ondersteund.

> [!NOTE]
> Als u nog niet hebt geïnstalleerd de Windows PowerShell-module voor [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)], Zie [Installatie van Windows PowerShell voor Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Aanbevolen procedures voor beveiliging voor de functie supergebruiker:

-   Beperken en te controleren van de beheerders die een globale beheerder voor uw Office 365- of Azure RMS-tenant zijn toegewezen of die de rol GlobalAdministrator zijn toegewezen met behulp van de [toevoegen AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629417.aspx) cmdlet. Deze gebruikers kunnen de supergebruiker inschakelen en gebruikers (en zelf) toewijzen als Supergebruikers en potentieel ontsleutelen van alle bestanden die uw organisatie beveiligt.

-   Om te zien welke gebruikers en serviceaccounts als Supergebruikers zijn toegewezen, gebruikt u de [van de cmdlet Get-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629408.aspx).  Als alle beheer acties inschakelen of uitschakelen van de functie super en gebruikers toevoegen of verwijderen super zich hebt aangemeld en kan worden gecontroleerd met behulp van de [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx) opdracht. Als u Supergebruikers bestanden decoderen, deze actie wordt vastgelegd en kan worden gecontroleerd met [gebruikslogboekregistratie](https://technet.microsoft.com/library/dn529121.aspx).

-   Als u niet de functie supergebruiker voor dagelijkse services hoeft, de functie alleen inschakelen wanneer u nodig hebt en opnieuw met behulp van uitschakelen de [Disable AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629428.aspx) cmdlet.

Het volgende logboekbestand extract bevat enkele voorbeelden van vermeldingen uit met de cmdlet Get-AadrmAdminLog. In dit voorbeeld bevestigt de beheerder voor Contoso Ltd dat de functie super-gebruiker is uitgeschakeld, Richard Simone toegevoegd als een gebruiker super wordt gecontroleerd of Richard het alleen supergebruiker voor Azure RMS geconfigureerd en de functie supergebruiker wordt zodat Richard kan nu enkele bestanden die zijn beveiligd door een werknemer die heeft nu het bedrijf verlaten decoderen.

`2015-08-01T18:58:20	admin@contoso.com	GetSuperUserFeatureState	Passed	Disabled`
`2015-08-01T18:59:44	admin@contoso.com	AddSuperUser -id rsimone@contoso.com	Passed	True`
`2015-08-01T19:00:51	admin@contoso.com	GetSuperUser	Passed	rsimone@contoso.com`
`2015-08-01T19:01:45	admin@contoso.com	SetSuperUserFeatureState -state Enabled	Passed	True`

## <a name="BKMK_RMSProtectionModule"></a>Scriptopties voor supergebruikers
Vaak iemand die is toegewezen supergebruiker voor [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] moet beveiliging verwijderen van meerdere bestanden op meerdere locaties. Tijdens het mogelijk om dit te doen handmatig is, is het efficiënter (en vaak betrouwbare) dit script. Hiertoe [download het hulpprogramma voor RMS beveiliging](http://www.microsoft.com/en-us/download/details.aspx?id=47256). Vervolgens gebruikt u de  [Unprotect RMSFile](https://msdn.microsoft.com/library/azure/mt433200.aspx) cmdlet, en [beveiligen RMSFile](https://msdn.microsoft.com/library/azure/mt433201.aspx)   cmdlet zoals voorgeschreven.

> [!IMPORTANT]
> Hoewel het hulpprogramma RMS beveiliging is ontworpen voor super gebruikers bulksgewijs bestanden voor de beveiliging opheffen, de huidige versie van het hulpprogramma biedt geen ondersteuning voor verificatie van de gebruiker voor Azure RMS. Totdat deze beperking is opgelost, moet u een service principal-account te verifiëren met Azure RMS voordat u de beveiliging van bestanden kunt verwijderen.  Zie voor meer informatie en instructies [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/azure/mt433202.aspx).

Zie voor meer informatie over deze cmdlets [RMS Protection Cmdlets](https://msdn.microsoft.com/library/azure/mt433195.aspx).

> [!NOTE]
> De RMSProtection Windows PowerShell-module die wordt geleverd met het hulpprogramma RMS Protection verschilt van en aanvulling op de belangrijkste [Windows PowerShell-module voor Azure Rights Management](https://technet.microsoft.com/library/jj585027.aspx). Ondersteunt Azure RMS en AD RMS.

## Zie ook
[Azure Rights Management configureren](../Topic/Configuring_Azure_Rights_Management.md)

