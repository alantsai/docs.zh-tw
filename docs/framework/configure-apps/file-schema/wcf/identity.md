---
title: "&lt;識別&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# &lt;識別&gt;
身分識別項目允許用戶端開發人員在設計階段指定服務的預期身分識別。  在用戶端和服務之間的信號交換過程中，[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 基礎結構將確保預期服務的身分識別符合這個項目的值，因此可以通過驗證。  如需詳細資訊，請參閱[服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。  
  
## 語法  
  
```  
  
<identity>  
    <certificate encodedValue="String"/>  
    <certificateReference findValue="String"   
       isChainIncluded="Boolean"  
       storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"storeName="  
       storeLocation="LocalMachine/CurrentUser"  
       X509FindType= Enumeration./>  
    <dns value="String"/>  
    <rsa value="String"/>  
    <servicePrincipalName value="String"/>  
    <usePrincipalName value="String"/>  
</identity>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|certificate|指定 X.509 憑證的設定。  此項目的型別為 <xref:System.ServiceModel.Configuration.CertificateElement>。  它包含是字串的屬性 `encodedValue`，指定由此憑證編碼的值。|  
|certificateReference|指定 X.509 憑證驗證的設定。  此項目的型別為 <xref:System.ServiceModel.Configuration.CertificateReferenceElement>。|  
|dns|指定用來驗證服務之 X.509 憑證的 DNS。  這個項目包含是字串的屬性 `value`，而且包含實際的身分識別。|  
|rsa|指定 X.509 憑證的 RSA 欄位值，此憑證可用來驗證用戶端的服務。  這個項目包含是字串的屬性 `value`，而且包含實際的身分識別。|  
|servicePrincipalName|指定伺服器主要名稱 \(SPN\) 身分識別，也就是用戶端可唯一識別服務執行個體時所用的主要名稱。  這個項目包含是字串的屬性 `value`，而且包含實際的主要名稱。  此項目的型別為 <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>。|  
|userPrincipalName|指定使用者主要名稱 \(UPN\) 身分識別，也就是網路上使用者的登入名稱類型。  使用者主要名稱包含 Active Directory 中使用的使用者物件名稱，後面會接著 at 符號 \(@\)，然後通常是網域名稱系統父系網域。  例如，Fabrikam.com 網域樹狀結構中的 Jeff 可能會有 [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com) 的使用者主要名稱。  這個項目包含是字串的屬性 `value`，而且包含實際的主要名稱。  此項目的型別為 <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<自訂\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custom.md)|指定 netPeerTcpBinding 的自訂對等解析程式。|  
|[\<endpoint\>](http://msdn.microsoft.com/zh-tw/13aa23b7-2f08-4add-8dbf-a99f8127c017)|設定不同類型的端點。|  
|[\<issuer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|指定聯合服務的安全性權杖服務 \(STS\)。|  
|[\<issuerMetadata\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|為聯合服務的安全性權杖服務 \(STS\) 指定中繼資料端點。|  
|[\<issuedTokenParameters\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|定義自訂繫結中已發行權杖的參數。|  
|[\<localIssuer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|指定本機安全性權杖服務 \(STS\)。|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.IdentityElement>   
 <xref:System.ServiceModel.EndpointAddress>   
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>   
 [服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [端點：位址、繫結和合約](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)