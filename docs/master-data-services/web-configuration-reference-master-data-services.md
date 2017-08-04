---
title: "Web 設定リファレンス (Master Data Services) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web configuration file [Master Data Services]
ms.assetid: b8cc9a35-97ab-4fe0-ab4b-c07f13d9793a
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1be0e90d7d2ba9b2751677015957ca249d91119e
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="web-configuration-reference-master-data-services"></a>Web 設定リファレンス (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]Web.config ファイルを使用してホストするインターネット インフォメーション サービス (IIS) を有効にする構成設定を含む、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションと Web サービスです。 この Web.config ファイルは、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] インストール パスの WebApplication フォルダーにあります。 パスと権限の詳細については、「[フォルダーとファイルの権限 (マスター データ サービス)](../master-data-services/folder-and-file-permissions-master-data-services.md)」を参照してください。  
  
## <a name="webconfig-elements"></a>Web.Config 要素  
 Web.config ファイルを含むカスタム[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]要素、  **\<masterDataServices >**、標準 IIS、.NET Framework、ASP.NET、および Windows Communication Foundation (WCF) configuration 要素だけでなくです。 次の表では、Web.config ファイルに含まれている要素について説明します。  
  
|Configuration 要素|Description|  
|---------------------------|-----------------|  
|**masterDataServices**|Custom 要素。 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web サービスを [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースに接続します。|  
|**connectionStrings**|ASP.NET 要素。 詳細については、MSDN ライブラリの「 [connectionStrings 要素 (ASP.NET 設定スキーマ)](http://go.microsoft.com/fwlink/?LinkId=178347) 」を参照してください。|  
|**system.web**|ASP.NET 要素。 詳細については、MSDN ライブラリの「 [system.web 要素 (ASP.NET 設定スキーマ)](http://go.microsoft.com/fwlink/?LinkId=178348) 」を参照してください。|  
|**startup**|.NET Framework 要素。 詳細については、次を参照してください。 [\<スタートアップ > 要素](http://go.microsoft.com/fwlink/?LinkId=178349)、MSDN ライブラリです。|  
|**runtime**|.NET Framework 要素。 詳細については、次を参照してください。 [\<ランタイム > 要素](http://go.microsoft.com/fwlink/?LinkId=178350)、MSDN ライブラリです。|  
|**system.codedom**|.NET Framework 要素。 詳細については、次を参照してください。 [ \<system.codedom > 要素](http://go.microsoft.com/fwlink/?LinkId=178351)、MSDN ライブラリです。|  
|**system.web.extensions**|ASP.NET 要素。 詳細については、MSDN ライブラリの「 [system.web.extensions 要素 (ASP.NET 設定スキーマ)](http://go.microsoft.com/fwlink/?LinkId=178352) 」を参照してください。|  
|**system.webServer**|IIS 要素を含んだセクション グループ。 詳細については、MSDN ライブラリの「[system.webServer セクション グループ \[IIS 7 設定スキーマ\]](http://go.microsoft.com/fwlink/?LinkId=178353)」を参照してください。|  
|**system.serviceModel**|WCF 要素。 詳細については、次を参照してください。 [ \<system.serviceModel >](http://go.microsoft.com/fwlink/?LinkId=178354) 、MSDN ライブラリです。|  
|**system.diagnostics**|.NET Framework 要素。 詳細については、次を参照してください。 [ \<system.diagnostics > 要素](http://go.microsoft.com/fwlink/?LinkId=178355)、MSDN ライブラリです。|  
|**appSettings**|ASP.NET 要素。 詳細については、MSDN ライブラリの「 [appSettings 要素 (全般設定スキーマ)](http://go.microsoft.com/fwlink/?LinkId=178356) 」を参照してください。|  
  
## <a name="masterdataservices-element"></a>masterDataServices 要素  
  **\<MasterDataServices >**要素は、カスタム要素の接続に使用される、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web サービスを[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]データベース。  
  
### <a name="syntax"></a>構文  
  
```  
<masterDataServices>  
   <instance virtualPath="path" siteName="name" connectionName="name" serviceName="name" />  
</masterDataServices>  
```  
  
### <a name="elements-and-attributes"></a>要素と属性  
  
|アイテム|Description|  
|----------|-----------------|  
|**インスタンス (instance)**|子要素。 Web サービスとデータベース接続文字列の情報を指定する属性を含みます。|  
|**virtualPath**|Attribute。 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションとサービスの仮想パスを指定します。 これに対応して、**パス**の属性、 **\<アプリケーション >**要素の下、 **\<サイト >** IIS ApplicationHost.config ファイル内の要素。|  
|**SiteName**|Attribute。 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションとサービスをホストするサイトの名前を指定します。 これに対応して、**名前**の属性、 **\<サイト >**要素の下**\<サイト >** IIS ApplicationHost.config ファイルにします。|  
|**connectionName**|Attribute。 使用する接続の名前を指定します。 これに対応して、**名前**の属性、 **\<追加 >**要素の下、  **\<connectionStrings >** Web.config 内の要素。|  
|**serviceName**|Attribute。 Web サービスの名前を指定します。 これに対応して、**名前**の属性、 **\<サービス >**要素の下、  **\<services >** Web.config 内の要素。|  
  
### <a name="example"></a>例  
 次の例は、Contoso サイト上の MDS1 という名前のサービスと、MDSDB によって指定された接続文字列を使用した /MDS パスを示しています。  
  
```  
<masterDataServices>  
   <instance virtualPath="/MDS" siteName="Contoso" connectionName="MDSDB" serviceName="MDS1" />  
</masterDataServices>  
```  
  
  
