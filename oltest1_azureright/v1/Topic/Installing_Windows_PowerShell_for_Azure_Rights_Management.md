---
description: na
keywords: na
title: Installing Windows PowerShell for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
---
# Installatie van Windows PowerShell voor Azure Rights Management
Gebruik de volgende informatie bij het installeren van Windows PowerShell voor Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS).

U kunt deze Windows PowerShell-module voor het beheren van [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] vanaf de opdrachtregel met behulp van een computer met een internetverbinding nodig die voldoet aan de vereisten vermeld in de volgende sectie. Windows PowerShell voor [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] scripting voor automatisering ondersteunt of voor scenario's met geavanceerde configuratie nodig kan zijn. Zie voor meer informatie over de taken voor het beheren en configuraties voor de module ondersteunt [Azure Rights Management beheren met behulp van Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Vereisten
Deze tabel bevat de vereisten om te installeren en gebruiken van Windows PowerShell voor [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

|Vereiste|Meer informatie|
|------------|-------------------|
|Een versie van Windows die ondersteunt de [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] beheermodule|Controleer de lijst met ondersteunde besturingssystemen in de **systeemvereisten** sectie van de [downloadpagina voor het beheerprogramma voor Azure Rights Management](http://go.microsoft.com/fwlink/?LinkId=257721).|
|Minimale versie van Windows PowerShell: 2.0|Ondersteuning voor de [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] de beheermodule in Windows PowerShell 2.0 is geïntroduceerd.<br /><br />Standaard de meeste Windows-besturingssystemen geïnstalleerd met ten minste versie 2.0 van Windows PowerShell. Als u nodig hebt voor het installeren van Windows PowerShell 2.0, Zie [Windows PowerShell 2.0 installeren](http://msdn.microsoft.com/library/ff637750.aspx). **Tip:** U kunt de versie van Windows PowerShell waarop u door te typen bevestigen **$PSVersionTable** in een Windows PowerShell-sessie.|
|Minimale versie van Microsoft .NET Framework: 4.5 **Tip:** Deze versie van Microsoft .NET Framework is opgenomen in latere besturingssystemen, zodat u alleen hoeft handmatig installeren als de client-besturingssysteem kleiner dan Windows 8.0 is of uw server-besturingssysteem kleiner dan Windows Server 2012 is.|Als dit nog niet is geïnstalleerd, kunt u downloaden de [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).<br /><br />Deze versie van Microsoft .NET Framework is vereist voor een van de klassen die de [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] maakt gebruik van de beheermodule.|
|Microsoft Online Services-In-assistent 7.0|De Microsoft Online Services-In-assistent is vereist voor [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] verificatie.<br /><br />Zie voor meer informatie [Downloadcentrum: Assistant voor IT-Professionals RTW voor Microsoft Online Services](http://www.microsoft.com/en-us/download/details.aspx?id=41950).|

## Het installeren van de module Rights Management-beheer

1.  Ga naar het Microsoft Download Center en [downloaden van het beheerprogramma voor Azure Rights Management](https://go.microsoft.com/fwlink/?LinkId=257721), waarin de [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] beheermodule voor Windows PowerShell.

2.  Vanuit de lokale map waarin u gedownload en opgeslagen de [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] installer-bestand, dubbelklikt u op het uitvoerbare bestand dat u hebt gedownload voor uw platform (WindowsAzureADRightsManagementAdministration_x64 of WindowsAzureADRightsManagementAdministration_x86.exe) om Azure AD Rights Management beheer Setup Wizard te starten.

3.  De wizard voltooit.

Windows PowerShell voor [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] is nu geïnstalleerd.

## Volgende stappen
Om te zien welke cmdlets beschikbaar zijn, start u Windows PowerShell met de **Als administrator uitvoeren** optie en typ het volgende:

```
Get-Command -Module aadrm
```
Gebruik `the Get-Help <cmdlet_name>` opdracht om te zien van de Help voor een specifieke cmdlet.

Voor meer informatie:

-   Volledige lijst met cmdlets beschikbaar: [Azure Rights Management-Cmdlets](https://msdn.microsoft.com/library/windowsazure/dn629398.aspx)

-   Lijst met de configuratie van de belangrijkste scenario's die ondersteuning van Windows PowerShell: [Azure Rights Management beheren met behulp van Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md)

Voordat u kunt alle opdrachten die configureren uitvoeren de [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] service, moet u verbinding maken met de service met behulp van de [Connect AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629415.aspx) cmdlet. Als u klaar bent met het uitvoeren van de configuratieopdrachten die u wilt verbreken van de service met behulp van de [verbinding verbreken AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629416.aspx) cmdlet.

> [!NOTE]
> Als u nog niet hebt geactiveerd [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], u kunt dit doen nadat u een verbinding met de service hebt gemaakt met behulp van de [Enable Aadrm](https://msdn.microsoft.com/library/windowsazure/dn629412.aspx) cmdlet.

## Zie ook
[Azure Rights Management beheren met behulp van Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md)

