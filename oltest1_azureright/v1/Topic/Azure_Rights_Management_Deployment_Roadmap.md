---
description: na
keywords: na
title: Azure Rights Management Deployment Roadmap
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
---
# Azure Rights Management-implementatieschema
Gebruik de volgende stappen uit om te voorbereiden, implementeren en beheren van Azure Rights Management (Azure RMS) voor uw organisatie.

Alleen wilt u snel probeer Azure RMS zelf, maar dan af samenvouwen in een productieomgeving Zie als [Snel starten zelfstudie voor Azure Rights Management](../Topic/Quick_Start_Tutorial_for_Azure_Rights_Management.md).

> [!IMPORTANT]
> Voordat u de volgende stappen uit, zorg ervoor dat u hebt bekeken [Vereisten voor Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md).

## Stap 1: Controleer of u hebt een abonnement van Azure Rights Management
Er is meer dan een abonnement met [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. Zie de [Cloud-abonnementen die ondersteuning van Azure RMS](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions) sectie de [Vereisten voor Azure Rights Management](../Topic/Requirements_for_Azure_Rights_Management.md) onderwerp en controleer of de functionaliteit die u in uw organisatie gebruiken wilt door te verwijzen naar de tabel in uw abonnement bevat [aanbiedingen voor vergelijking van Rights Management Services (RMS)](https://technet.microsoft.com/dn858608).

## Stap 2: Uw account tenant Rights Management gebruiken voorbereiden
Voordat u met behulp van begint [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], de voorbereiding van het volgende doen:

1.  Zorg ervoor dat uw Azure of Office 365-tenant bevat de accounts van gebruikers en groepen die door Azure RMS worden gebruikt voor het verifiëren van gebruikers van uw organisatie. Indien nodig, deze account en groepen maken of deze van uw on-premises directory synchroniseren. Zie voor meer informatie [Voorbereiden voor Azure Rights Management](../Topic/Preparing_for_Azure_Rights_Management.md).

2.  U hebt Microsoft uw tenant sleutel (standaard), beheren of genereren en beheren van uw tenant sleutel uzelf (bekend als brengt uw eigen sleutel of BYOK). Houd er rekening mee dat momenteel wordt u niet BYOK gebruiken als u Exchange Online. Zie voor meer informatie [Plannen en implementeren van uw Azure Rights Management Tenant-sleutel](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md).

3.  Installeer de Windows PowerShell-module voor [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] op ten minste één computer die toegang tot het Internet. Deze stap nu of later, kunt u doen. Zie voor meer informatie [Installatie van Windows PowerShell voor Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

4.  Als u momenteel lokale Rights Management services gebruikt: Een migratie wilt verplaatsen van de sleutels, sjablonen en URL's naar de cloud uit te voeren. Zie voor meer informatie [Migratie van AD RMS naar Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md).

5.  Rights Management activeren zodat u beginnen kunt met het gebruik van de service. Als een gefaseerde implementatie vereist is, configureert u gebruiker onboarding besturingselementen voor het gebruik aan specifieke gebruikers te beperken. Zie voor meer informatie [Azure Rights Management activeren](../Topic/Activating_Azure_Rights_Management.md).

Bekijk eventueel configureren van de volgende:

-   Aangepaste sjablonen als de standaardwaarde rights sjablonen zijn niet voldoende is voor uw organisatie. Deze stap nu of later, kunt u doen. Zie voor meer informatie [Aangepaste sjablonen configureren voor Azure Rights Management](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md).

-   Gebruik logboekregistratie zodat u kunt controleren hoe uw organisatie Rights Management worden gebruikt. Deze stap nu of later, kunt u doen. Zie voor meer informatie [Logboekregistratie en analyseren van Azure Rights Management-gebruik](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md).

## Stap 3: Configureer de toepassingen en services voor Rights Management
Configureren van uw toepassingen kunt opnemen installeren van de Rights Management-toepassing voor delen en ondersteuning voor information rights management (IRM) functies in SharePoint Online of Exchange Online in te schakelen. Zie voor meer informatie [Toepassingen voor Azure Rights Management configureren](../Topic/Configuring_Applications_for_Azure_Rights_Management.md).

Hebt u bestaande IT-services die u nodig hebt om te controleren van bestanden die Azure RMS wordt beveiligd, zoals data geheugenlek te voorkomen (DLP)-oplossingen van inhoud versleuteling gateways (CEG) en anti-malware-producten, de serviceaccounts worden Supergebruikers voor Azure RMS configureren. Zie voor meer informatie [Supergebruikers configureren voor Azure Rights Management en van detectieservices of gegevens te herstellen](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md).

Hebt u lokale services die u wilt gebruiken met Azure Rights Management, installeren en configureren van de connector Rights Management. Zie voor meer informatie [Implementatie van de Connector van de Azure Rights Management](../Topic/Deploying_the_Azure_Rights_Management_Connector.md).

## Stap 4: Publiceren en gebruik van rechten beveiligde inhoud
U kunt nu te publiceren en gebruiken van beveiligde inhoud en meld u hoe uw bedrijf Rights Management wordt gebruikt. Zie voor meer informatie [Met behulp van Azure Rights Management](../Topic/Using_Azure_Rights_Management.md).

## Stap 5: Rights Management voor uw account tenant beheren, indien nodig
Als u begint met het gebruik van [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], kan de [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] -module voor Windows PowerShell nuttig om scripts of administratieve wijzigingen automatiseren. Zie voor meer informatie [Azure Rights Management beheren met behulp van Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Zie ook
[Azure Rights Management configureren](../Topic/Configuring_Azure_Rights_Management.md)

