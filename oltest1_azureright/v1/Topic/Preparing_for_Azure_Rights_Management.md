---
description: na
keywords: na
title: Preparing for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
---
# Voorbereiden voor Azure Rights Management
Nadat u hebt aangemeld voor een cloud-abonnement en tot stand gebracht van uw organisatie met een account voor [!INCLUDE[o365_1](../Token/o365_1_md.md)] of Azure Active Directory, bent u klaar om in te schakelen de [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] service.

Voordat u dit doet, zorg er echter dat de volgende zijn:

-   Gebruikersaccounts en groepen in de cloud die u handmatig maken of die automatisch gemaakt en gesynchroniseerd met Active Directory Domain Services (AD DS).

    Wanneer u uw lokale accounts en groepen synchroniseert, niet alle kenmerken moeten worden gesynchroniseerd. Zie voor een lijst van de kenmerken die moeten worden gesynchroniseerd voor Azure RMS [Azure RMS sectie](https://azure.microsoft.com/documentation/articles/active-directory-aadconnectsync-attributes-synchronized/) van de documentatie van Azure Active Directory. Voor gemakkelijke implementatie, raden we aan dat u gebruikt [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) uw lokale mappen met Azure Active Directory, maar u kunnen gebruiken een map synchronisatiemethode die hetzelfde resultaat bereikt.

-   E-mailadres groepen in de cloud die u met Rights Management gebruiken gaat. Dit kunnen ingebouwde groepen of het handmatig gemaakte groepen met gebruikers die Rights Management wordt gebruikt.

    Als u Exchange Online, kunt u deze kunt maken en gebruiken van e-mailadres groepen met behulp van de Exchange-beheercentrum. Als u AD DS hebt en naar Azure AD synchroniseert, kunt u maken en e-mailadres groepen die beveiligingsgroepen of distributiegroepen zijn gebruikt.

## Rights Management inschakelen
Standaard [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] wordt uitgeschakeld wanneer u zich aanmeldt voor uw [!INCLUDE[o365_2](../Token/o365_2_md.md)] of Azure AD-account. Om in te schakelen [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] voor uw organisatie, moet u de service activeren. Zie voor meer informatie [Azure Rights Management activeren](../Topic/Activating_Azure_Rights_Management.md).

## Zie ook
[Azure Rights Management configureren](../Topic/Configuring_Azure_Rights_Management.md)

