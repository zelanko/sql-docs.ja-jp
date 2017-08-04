---
title: "マスター データ マネージャー Web サービス プロキシ クラスを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 8bdab026-a0c0-41f3-9d36-f3919c23247f
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a45cd15ced90aef95feb03f8fbaafd5aa70cb746
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="create-master-data-manager-web-service-proxy-classes"></a>マスター データ マネージャー Web サービス プロキシ クラスの作成
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web サービスを使用すると、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web サイトにアクセスできる任意のコンピューターから、[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] の機能をプログラム経由で使用できます。 Web サービスにアクセスするコードの記述を開始する前に、プロキシ クラスを生成する必要があります。 Web サービス操作の実行に使用する主要なプロキシ クラスは、<xref:Microsoft.MasterDataServices.ServiceClient> クラスです。このクラスは、<xref:Microsoft.MasterDataServices.IService> インターフェイスを実装します。  
  
## <a name="enable-web-service-metadata-publishing"></a>Web サービス メタデータ パブリッシュの有効化  
 プロキシ クラスを生成する前に、Web サービス メタデータ パブリッシュを有効にする必要があります。 これを行うこれらの手順に従います。  
  
1.  開く、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]をテキスト エディターで Web.config ファイルです。 このファイルは、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] インストール パスの WebApplication フォルダーにあります。  
  
2.  検索、 **mdsWsHttpBehavior**セクション **\<serviceBehaviors >**です。  **\<ServiceMetadata >**要素設定**httpGetEnabled**に**true**です。  
  
    > [!NOTE]  
    >  Secure Sockets Layer (SSL) 経由で Web サービスを有効にする場合は、設定**httpsGetEnabled**に**true**で、 **mdsWsHttpBehavior** web.config ファイルのセクションです。 変更する必要があります**mdsWsHTTPBinding** SSL、同様に、およびコメント アウト、非 SSL セクション用に構成されているためです。  
  
3.  変更をファイルに保存します。  
  
4.  たとえば、サービスの URL を参照してメタデータの公開のテスト:`http://yourserver/MDS/service/service.svc`です。 メタデータ パブリッシュが有効化されると、   
    "サービスを作成しました。" で始まるページが表示されます。  
  
## <a name="creating-proxy-classes-by-using-visual-studio"></a>Visual Studio を使用してプロキシ クラスを作成する  
 追加するプロキシ クラスを生成する最も簡単な方法は、Visual Studio 2010 をインストールした場合、**サービス参照の**をプロジェクトにします。 サービス参照のアドレスは、[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションの URL に、/service/service.svc を付加したものです。 たとえば、 `http://yourserver/MDS/service/service.svc`のようにします。 詳細については、次を参照してください。[する方法: 追加、更新、またはサービス参照の削除](http://go.microsoft.com/fwlink/?LinkId=221167)です。  
  
## <a name="creating-proxy-classes-by-using-svcutilexe"></a>Svcutil.exe を使用してプロキシ クラスを作成する  
 いずれかをする必要があります[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]または[!INCLUDE[msCoName](../../includes/msconame-md.md)]コンピューターに Svcutil.exe を確保するために Windows SDK がインストールされています。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] を使用する場合は、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] コマンド プロンプトでコマンドを実行する必要があります。 詳細については、次を参照してください。 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](http://go.microsoft.com/fwlink/?LinkId=165027)と[WCF クライアントのサービス メタデータから生成](http://go.microsoft.com/fwlink/?LinkId=164821)です。  
  
 Svcutil.exe を使用して一連の C# プロキシ クラスを作成するには、次のようなコマンドを使用します。  
  
```  
svcutil.exe http://<server_name:port>/<virtual_path>/Service/Service.svc   
/out:<proxy_name>.cs /messageContract /tcv:Version35   
/noconfig /ct:System.Collections.ObjectModel.Collection`1   
/namespace:*,Microsoft.MasterDataServices  
```  
  
 各要素の説明は次のとおりです。  
  
-   *servername*:*ポート*はコンピューター名とポートをホストするコンピューターの番号[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]です。  
  
-   *virtual_path*の仮想パスは、[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]インターネット インフォメーション サービス (IIS) にします。  
  
-   *proxy_name*生成されるプロキシ ファイルの名前を指定します。  
  
## <a name="see-also"></a>参照  
 [Web サービス操作の分類と #40 です。マスター データ サービス &#41;](../../master-data-services/develop/categorized-web-service-operations-master-data-services.md)  
  
  
