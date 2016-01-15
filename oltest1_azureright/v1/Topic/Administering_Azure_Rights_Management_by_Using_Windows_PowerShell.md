---
description: na
keywords: na
title: Administering Azure Rights Management by Using Windows PowerShell
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a890e04a-4b70-41b5-8d5f-3c210a669faa
---
# Azure Rights Management beheren met behulp van Windows PowerShell
Hoewel u kunt Microsoft activeren [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS) met behulp van de [!INCLUDE[o365_2](../Token/o365_2_md.md)] -beheercentrum of het Azure-portal ook kunt u de Windows PowerShell-module voor [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (AADRM) om dit te doen.

Nadat u hebt geactiveerd [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], verder beheer voor de service wordt mogelijk niet vereist. Echter enkele geavanceerde configuratie scenario's mogelijk moet u de Windows PowerShell-module voor [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. De volgende tabel worden enkele van de configuratie van geavanceerde scenario's die gebruikmaken van Windows PowerShell. Zie voor een volledige lijst van de beschikbare cmdlets met meer informatie over elke [Azure Rights Management-Cmdlets](http://msdn.microsoft.com/library/azure/dn629398.aspx).

> [!NOTE]
> Als u nodig hebt voor het installeren van de Windows PowerShell-module voor [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], Zie [Installatie van Windows PowerShell voor Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

Er is ook een aanvullende Windows PowerShell-module **RMSProtection**, die ondersteuning biedt voor Azure RMS en AD RMS. Deze module biedt ondersteuning voor bescherming en beveiliging opheffen van meerdere bestanden zodat bijvoorbeeld, u bulksgewijs-alle bestanden in een map beveiligen kunt. Zie voor meer informatie de [Scriptopties voor supergebruikers](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md#BKMK_RMSProtectionModule) sectie de [Supergebruikers configureren voor Azure Rights Management en van detectieservices of gegevens te herstellen](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md) onderwerp.

|Als u wilt...|.. .zakelijke de volgende cmdlets|
|-----------------|-------------------------------------|
|On-premises Rights Management (AD RMS of Windows RMS) migreren naar [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].|[Importeer AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx)|
|Verbinding maken met of verbreken met de [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] service voor uw organisatie.|[Verbinding maken met AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx)<br /><br />[Verbinding verbreken AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx)|
|Genereren en beheren van uw eigen tenant sleutel – het Breng uw eigen scenario sleutel (BYOK).|[Voeg AadrmKey](http://msdn.microsoft.com/library/azure/dn629418.aspx)<br /><br />[Get-AadrmKeys](http://msdn.microsoft.com/library/azure/dn629420.aspx)|
|Activeren of deactiveren de [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] service voor uw organisatie.|[Inschakelen Aadrm](http://msdn.microsoft.com/library/azure/dn629412.aspx)<br /><br />[Disable-Aadrm](http://msdn.microsoft.com/library/azure/dn629422.aspx)|
|In het document site bijhouden voor Azure Rights Management- of uitschakelen.|[Disable-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548471.aspx)<br /><br />[Inschakelen AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548469.aspx)<br /><br />[Get-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548470.aspx)|
|Onboarding besturingselementen voor een gefaseerde implementatie van Azure Rights Management configureren.|[Get-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857522.aspx)<br /><br />[Set AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx)|
|Maak en beheer sjablonen voor rechten voor uw organisatie.|[Voeg AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727075.aspx)<br /><br />[Exporteren AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727078.aspx)<br /><br />[Get-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727079.aspx)<br /><br />[Get-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727081.aspx)<br /><br />[Importeer AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727077.aspx)<br /><br />[Nieuwe AadrmRightsDefinition](http://msdn.microsoft.com/library/azure/dn727080.aspx)<br /><br />[Verwijder AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727082.aspx)<br /><br />[Set AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727076.aspx)|
|Configureer het maximum aantal dagen dat inhoud die uw organisatie beschermt toegang zonder een internetverbinding (de geldigheidsperiode van de gebruik-licentie).|[Get-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932062.aspx)<br /><br />[Set AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932063.aspx)|
|De functie supergebruiker van beheren [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] voor uw organisatie.|[Inschakelen AadrmSuperUserFeature](http://msdn.microsoft.com/library/azure/dn629400.aspx)<br /><br />[Disable-AadrmSuperUserFeature](http://msdn.microsoft.com/library/azure/dn629428.aspx)<br /><br />[Voeg AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629411.aspx)<br /><br />[Get-AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629408.aspx)<br /><br />[Verwijder AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629405.aspx)|
|Beheren van gebruikers en groepen die gemachtigd zijn voor het beheren van de [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] service voor uw organisatie.|[Voeg AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629417.aspx)<br /><br />[Get-AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629407.aspx)<br /><br />[Verwijder AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629424.aspx)|
|Ophalen van een logboek van [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] administratieve taken voor uw organisatie.|[Get-AadrmAdminLog](http://msdn.microsoft.com/library/azure/dn629430.aspx)|
|Aanmelden en analyseren van gebruik logboekregistratie voor [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].|[Inschakelen AadrmUsageLogFeature](http://msdn.microsoft.com/library/azure/dn629421.aspx)<br /><br />[Get-AadrmUsageLog](http://msdn.microsoft.com/library/azure/dn629401.aspx)<br /><br />[Get-AadrmUsageLogFeature](http://msdn.microsoft.com/library/azure/dn629425.aspx)<br /><br />[Get-AadrmUsageLogLastCounterValue](http://msdn.microsoft.com/library/azure/dn629423.aspx)<br /><br />[Get-AadrmUsageLogStorageAccount](http://msdn.microsoft.com/library/azure/dn629419.aspx)<br /><br />[Set AadrmUsageLogStorageAccount](http://msdn.microsoft.com/library/azure/dn629426.aspx)<br /><br />[Disable-AadrmUsageLogFeature](http://msdn.microsoft.com/library/azure/dn629404.aspx)|
|De huidige weergegeven [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] configuratie van de service voor uw organisatie.|[Get-AadrmConfiguration](http://msdn.microsoft.com/library/azure/dn629410.aspx)|
|Migreren van uw organisatie van [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] naar een lokaal AD RMS-implementatie.|[Set AadrmMigrationUrl](http://msdn.microsoft.com/library/azure/dn629429.aspx)<br /><br />[Get-AadrmMigrationUrl](http://msdn.microsoft.com/library/azure/dn629403.aspx)|

## Zie ook
[Azure Rights Management](../Topic/Azure_Rights_Management.md)

