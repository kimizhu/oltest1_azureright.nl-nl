---
description: na
keywords: na
title: Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 965581c8-be3c-43b4-8145-5cefd29c7636
---
# Azure Rights Management
<?xml version="1.0" encoding="utf-8"?>
<caps:SxS xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
  <caps:SxSTarget locale="nl-NL">
    <developerConceptualDocument xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd" xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <introduction>
        <para>
          <caps:sentence sentenceid="62b83eea4fc0746f132ff6c8d4a52b84" id="tgt1" class="tgtSentence">Deze pagina bevat de technische documentatie voor Microsoft <token>aad_rightsmanagement_1</token> (Azure RMS), kunt u van uw organisatie gevoelige informatie beveiligen tegen onbevoegde toegang en bepalen hoe deze gegevens worden gebruikt.</caps:sentence>
          <caps:sentence sentenceid="23b58def11b45727d3351702515f86af" id="tgt2" class="tgtSentence">
            <token>aad_rightsmanagement_1</token> is een cloudservice en is geïntegreerd in andere Microsoft-cloudservices en toepassingen, zoals Office 365 en Azure Active Directory.</caps:sentence>
          <caps:sentence sentenceid="145e719c453fbadadee79768f74667aa" id="tgt3" class="tgtSentence"> Het kan echter ook worden gebruikt met uw lokale toepassingen en services.</caps:sentence>
        </para>
        <para>
          <caps:sentence sentenceid="c6fa2923fc013e88430215867fa3b41f" id="tgt4" class="tgtSentence">
            <token>aad_rightsmanagement_2</token> versleuteling, identiteit en autorisatie-beleid gebruikt om te helpen beveiligen van uw bestanden en e-mailbericht.</caps:sentence>
          <caps:sentence sentenceid="6cee999ea54670dc3aaf3fa7bfdf7566" id="tgt5" class="tgtSentence"> Vergelijking met standaard toegang besturingselementen, zoals NTFS-machtigingen, beveiliging, die wordt toegepast met behulp van <token>aad_rightsmanagement_2</token> blijft op de bestanden en e-mailberichten, ongeacht de locatie, binnen of buiten uw organisatie, netwerken, bestandsservers en toepassingen.</caps:sentence>
          <caps:sentence sentenceid="3cea98f77e893eb1025f89567a366d77" id="tgt6" class="tgtSentence"> Deze informatie protection oplossing blijft u controle over uw gegevens, zelfs wanneer deze wordt gedeeld met anderen.</caps:sentence>
        </para>
        <para>
          <caps:sentence sentenceid="3d1e430f66ef0a41b3c0d4361753146d" id="tgt7" class="tgtSentence">U kunt bijvoorbeeld een bestand configureren zodat deze alleen door mensen in uw organisatie of besturingselement worden geopend of het bestand kan worden bewerkt, tot de alleen-lezen beperkt of voorkomen dat wordt afgedrukt.</caps:sentence>
          <caps:sentence sentenceid="a1d4b6ea938e5c3193bcc436be24f8c0" id="tgt8" class="tgtSentence"> U kunt op dezelfde manier configureren van e-mailberichten en bovendien voorkomen dat ze worden doorgestuurd of te voorkomen dat het gebruik van de optie Allen beantwoorden.</caps:sentence>
          <caps:sentence sentenceid="76c61c663112d6aabc8b0558688c8514" id="tgt9" class="tgtSentence"> Deze taken beveiliging kunnen worden vereenvoudigd en gestroomlijnde via gestandaardiseerde sjablonen.</caps:sentence>
        </para>
        <para>
          <caps:sentence sentenceid="31d23eeb49a60f86a1641f17c6570b72" id="tgt10" class="tgtSentence">
      Zie voor een nadere informatie over en voorbeelden <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df">What is Azure Rights Management?</link></caps:sentence>
        </para>
        <para>
          <caps:sentence sentenceid="0d618ca3ca5b0a48f105c1e37165a023" id="tgt11" class="tgtSentence">Gebruik de volgende informatie voor meer informatie over <token>aad_rightsmanagement_1</token> en deze implementeren voor uw organisatie:</caps:sentence>
        </para>
        <list class="bullet">
          <listItem>
            <para>
              <link xlink:href="5214667c-ec69-42ca-8bbf-8cb22da8c62e">Getting started with Azure AD Rights Management</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="206a0bfe-0912-4e0e-aa15-484b000b264c">Configuring rights management</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="18564e4a-9364-4ed2-8f17-89d24fc0d878">Using rights management</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="a890e04a-4b70-41b5-8d5f-3c210a669faa">Administering rights management</link>
            </para>
          </listItem>
        </list>
        <para>
          <caps:sentence sentenceid="8f8764b84fbfe3fb41a1de8bd2151a22" id="tgt12" class="tgtSentence">Zie voor aanvullende bronnen <link xlink:href="7cc73d92-27d6-49ff-a8ab-2fae73519b4b">Information and Support for Azure Rights Management</link>.</caps:sentence>
        </para>
      </introduction>
      <section>
        <title>
          <caps:sentence sentenceid="b75b1651ff8c1f6e857670d70de57727" id="tgt13" class="tgtSentence">Ook wel bekend als...</caps:sentence>
        </title>
        <content>
          <para>
            <caps:sentence sentenceid="0bb50d5ace4abd536a35235fd9cca548" id="tgt14" class="tgtSentence">Azure Rights Management wordt ook wel <legacyItalic>Azure Rights Management-service</legacyItalic>, maar omdat deze wordt uitgevoerd als een service in Azure, 'service' vaak van de naam wordt opgegeven.</caps:sentence>
            <caps:sentence sentenceid="4ec4858d185533976ae0410b2d35079b" id="tgt15" class="tgtSentence"> Dit is de cloud-versie van <legacyItalic>Active Directory Rights Management Services</legacyItalic> (AD RMS), die is uitgebracht als <legacyItalic>Windows Rights Management Services</legacyItalic> (Windows RMS).</caps:sentence>
          </para>
          <para>
            <caps:sentence sentenceid="0726a4db7b39858b6c4062cb42e94fe2" id="tgt16" class="tgtSentence">RMS is een bekende afkorting voor de voorafgaande en Azure Rights Management vaak wordt afkorting naar <legacyItalic>Azure RMS</legacyItalic>.</caps:sentence>
          </para>
          <para>
            <caps:sentence sentenceid="951d003f6152823990af843b34aa46e3" id="tgt17" class="tgtSentence">Azure Rights Management is oorspronkelijk met de naam <legacyItalic>Windows Azure Active Directory Rights Management</legacyItalic> (vaak afkorting naar <legacyItalic>Windows Azure AD Rights Management</legacyItalic>), klikt u vervolgens  <legacyItalic>Windows Azure Rights Management</legacyItalic>, en nu ten slotte <legacyItalic>Azure Rights Management</legacyItalic>.</caps:sentence>
          </para>
          <para>
            <caps:sentence sentenceid="ae8b2b285d98ab9534ef325989bd0813" id="tgt18" class="tgtSentence">U ziet ook verwijzingen naar <legacyItalic>Information Rights Management</legacyItalic> vaak afkorting naar <legacyItalic>IRM</legacyItalic>.</caps:sentence>
            <caps:sentence sentenceid="bcf8f7f6e8efe34a2816544f253dc99e" id="tgt19" class="tgtSentence"> Dit is de Office-implementatie van Rights Management kan worden ondersteund Azure RMS en AD RMS.</caps:sentence>
            <caps:sentence sentenceid="814cd385574d9159ca8935f57babd54f" id="tgt20" class="tgtSentence">  Als u Azure RMS voor het eerst is uitgebracht, dit alleen kan worden gebruikt met Office 365, bijvoorbeeld met een Office 365 E3-abonnement.</caps:sentence>
            <caps:sentence sentenceid="21c6900dba0d93d29042f515dd3cd695" id="tgt21" class="tgtSentence"> Nu Azure RMS wordt uitgebreid naar andere abonnementen, zoals Enterprise mobiliteit Suite (EMS) en ondersteuning biedt nu Office 2016, Office 2013, Office 2010, lokale versies van SharePoint en Exchange en Azure RMS elk bestandstype kunt beveiligen.</caps:sentence>
            <caps:sentence sentenceid="3ce055386165dac9a926371c350ecfed" id="tgt22" class="tgtSentence"> Zie voor meer informatie  <link xlink:href="2cdc7bde-4044-4021-b887-11476f99afd9">How Applications Support Azure Rights Management</link>.</caps:sentence>
          </para>
          <para>
            <caps:sentence sentenceid="483562e5c3f5a51c6ece6ac16a3e8b0f" id="tgt23" class="tgtSentence">U ziet ook incidenteel verwijzingen naar <legacyItalic>Microsoft Rights Management</legacyItalic>, of <legacyItalic>Microsoft Rights Management services</legacyItalic>, die is een gezamenlijke term Azure RMS en AD RMS.</caps:sentence>
            <caps:sentence sentenceid="62590b7cc80fa58960258871f90025a1" id="tgt24" class="tgtSentence">  De "<legacyItalic>nieuwe Microsoft RMS</legacyItalic>" is een populaire label waarmee u soms Azure Rights Management is officiële uitgebracht, de nieuwe gemakkelijke implementatie ten opzichte van de voorafgaande lokale benadrukken.</caps:sentence>
          </para>
          <alert class="tip">
            <para>
              <caps:sentence sentenceid="da41105f4520ac7aa5ba99aad81c8f23" id="tgt25" class="tgtSentence">Vindt u deze voorwaarden (en meer) in <link xlink:href="742877bf-26f5-40e3-b1f7-8475e7c3ce11">Terminology for Azure Rights Management</link>.</caps:sentence>
            </para>
          </alert>
          <para>
            <caps:sentence sentenceid="d2584214cdff2107001a9881c3f0d321" id="tgt26" class="tgtSentence">Als een oplossing voor enterprise informatie over beveiliging bieden Microsoft Rights Management services geen digitale rights (DRM)-managementoplossingen die doorgaans bescherming tegen illegale distributie van digitale software.</caps:sentence>
          </para>
        </content>
      </section>
      <relatedTopics></relatedTopics>
    </developerConceptualDocument>
  </caps:SxSTarget>
  <caps:SxSSource locale="en-US">
    <developerConceptualDocument xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd" xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <introduction>
        <para>
          <caps:sentence id="src1" class="srcSentence">This page introduces the technical documentation set for Microsoft <token>aad_rightsmanagement_1</token> (Azure RMS), to help you protect your organization’s sensitive information from unauthorized access, and control how this information is used.</caps:sentence>
          <caps:sentence id="src2" class="srcSentence">
            <token>aad_rightsmanagement_1</token> is a cloud service, and is integrated into other Microsoft cloud services and applications, such as Office 365 and Azure Active Directory.</caps:sentence>
          <caps:sentence id="src3" class="srcSentence"> However, it can also be used with your on-premises applications and services.</caps:sentence>
        </para>
        <para>
          <caps:sentence id="src4" class="srcSentence">
            <token>aad_rightsmanagement_2</token> uses encryption, identity, and authorization policies to help secure your files and email.</caps:sentence>
          <caps:sentence id="src5" class="srcSentence"> In comparison to standard access controls, such as NTFS permissions, protection that is applied by using <token>aad_rightsmanagement_2</token> stays with the files and emails, independently of the location—inside or outside your organization, networks, file servers, and applications.</caps:sentence>
          <caps:sentence id="src6" class="srcSentence"> This information protection solution keeps you in control of your data, even when it is shared with other people.</caps:sentence>
        </para>
        <para>
          <caps:sentence id="src7" class="srcSentence">For example, you can configure a file so that it can be accessed only by people in your organization, or control whether the file can be edited, or restricted to read-only, or prevent it from being printed.</caps:sentence>
          <caps:sentence id="src8" class="srcSentence"> You can configure emails similarly, and in addition, prevent them from being forwarded or prevent the use of the Reply All option.</caps:sentence>
          <caps:sentence id="src9" class="srcSentence"> These protection tasks can be simplified and streamlined by using standardized policy templates.</caps:sentence>
        </para>
        <para>
          <caps:sentence id="src10" class="srcSentence">
      For a deeper understanding and some examples, see <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df">What is Azure Rights Management?</link></caps:sentence>
        </para>
        <para>
          <caps:sentence id="src11" class="srcSentence">Use the following information to learn more about <token>aad_rightsmanagement_1</token> and deploy it for your organization:</caps:sentence>
        </para>
        <list class="bullet">
          <listItem>
            <para>
              <link xlink:href="5214667c-ec69-42ca-8bbf-8cb22da8c62e">Getting started with Azure AD Rights Management</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="206a0bfe-0912-4e0e-aa15-484b000b264c">Configuring rights management</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="18564e4a-9364-4ed2-8f17-89d24fc0d878">Using rights management</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="a890e04a-4b70-41b5-8d5f-3c210a669faa">Administering rights management</link>
            </para>
          </listItem>
        </list>
        <para>
          <caps:sentence id="src12" class="srcSentence">For additional resources, see <link xlink:href="7cc73d92-27d6-49ff-a8ab-2fae73519b4b">Information and Support for Azure Rights Management</link>.</caps:sentence>
        </para>
      </introduction>
      <section>
        <title>
          <caps:sentence id="src13" class="srcSentence">Also known as ...</caps:sentence>
        </title>
        <content>
          <para>
            <caps:sentence id="src14" class="srcSentence">Azure Rights Management is also known as <legacyItalic>Azure Rights Management service</legacyItalic>, but because it runs as a service in Azure, the "service" is often omitted from its name.</caps:sentence>
            <caps:sentence id="src15" class="srcSentence"> It is the cloud version of <legacyItalic>Active Directory Rights Management Services</legacyItalic> (AD RMS), which was first released as <legacyItalic>Windows Rights Management Services</legacyItalic> (Windows RMS).</caps:sentence>
          </para>
          <para>
            <caps:sentence id="src16" class="srcSentence">Because RMS is a well-known abbreviation for its predecessors, Azure Rights Management is often abbreviated to <legacyItalic>Azure RMS</legacyItalic>.</caps:sentence>
          </para>
          <para>
            <caps:sentence id="src17" class="srcSentence">Azure Rights Management was originally named <legacyItalic>Windows Azure Active Directory Rights Management</legacyItalic> (often abbreviated to <legacyItalic>Windows Azure AD Rights Management</legacyItalic>), then  <legacyItalic>Windows Azure Rights Management</legacyItalic>, and now finally <legacyItalic>Azure Rights Management</legacyItalic>.</caps:sentence>
          </para>
          <para>
            <caps:sentence id="src18" class="srcSentence">You might also see references to <legacyItalic>Information Rights Management,</legacyItalic> often abbreviated to <legacyItalic>IRM</legacyItalic>.</caps:sentence>
            <caps:sentence id="src19" class="srcSentence"> This is the Office implementation of Rights Management, which can support both Azure RMS and AD RMS.</caps:sentence>
            <caps:sentence id="src20" class="srcSentence">  When Azure RMS was first released, it could only be used with Office 365—for example, with an Office 365 E3 subscription.</caps:sentence>
            <caps:sentence id="src21" class="srcSentence"> Now, Azure RMS  is extended to other subscriptions, such as the Enterprise Mobility Suite (EMS) and support now includes Office 2016, Office 2013, Office 2010, on-premises versions of SharePoint and Exchange, and Azure RMS can protect any file type.</caps:sentence>
            <caps:sentence id="src22" class="srcSentence"> For more information, see  <link xlink:href="2cdc7bde-4044-4021-b887-11476f99afd9">How Applications Support Azure Rights Management</link>.</caps:sentence>
          </para>
          <para>
            <caps:sentence id="src23" class="srcSentence">You might also see occasional references to <legacyItalic>Microsoft Rights Management</legacyItalic>, or <legacyItalic>Microsoft Rights Management services</legacyItalic>, which is a collective term that can include both Azure RMS and AD RMS.</caps:sentence>
            <caps:sentence id="src24" class="srcSentence">  The "<legacyItalic>NEW Microsoft RMS</legacyItalic>" was a popular label that was sometimes used  when Azure Rights Management was officially released, to emphasize the new ease of deployment in comparison to its on-premises predecessors.</caps:sentence>
          </para>
          <alert class="tip">
            <para>
              <caps:sentence id="src25" class="srcSentence">You'll find these terms (and more) in <link xlink:href="742877bf-26f5-40e3-b1f7-8475e7c3ce11">Terminology for Azure Rights Management</link>.</caps:sentence>
            </para>
          </alert>
          <para>
            <caps:sentence id="src26" class="srcSentence">As an enterprise information protection solution, Microsoft Rights Management services do not provide digital rights management (DRM) solutions that typically protect against illegal distribution of digital software.</caps:sentence>
          </para>
        </content>
      </section>
      <relatedTopics></relatedTopics>
    </developerConceptualDocument>
  </caps:SxSSource>
</caps:SxS>