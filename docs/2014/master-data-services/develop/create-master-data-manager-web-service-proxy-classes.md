---
title: マスター データ マネージャー Web サービス プロキシ クラスの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 8bdab026-a0c0-41f3-9d36-f3919c23247f
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: c44e1830b1f04b1a7686bf7db1efea4549ae143e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65479552"
---
# <a name="create-master-data-manager-web-service-proxy-classes"></a>マスター データ マネージャー Web サービス プロキシ クラスの作成
  
  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web サービスを使用すると、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web サイトにアクセスできる任意のコンピューターから、[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] の機能をプログラム経由で使用できます。 Web サービスにアクセスするコードの記述を開始する前に、プロキシ クラスを生成する必要があります。 Web サービス操作の実行に使用する主要なプロキシ クラスは、<xref:Microsoft.MasterDataServices.ServiceClient> クラスです。このクラスは、<xref:Microsoft.MasterDataServices.IService> インターフェイスを実装します。  
  
## <a name="enable-web-service-metadata-publishing"></a>Web サービス メタデータ パブリッシュの有効化  
 プロキシ クラスを生成する前に、Web サービス メタデータ パブリッシュを有効にする必要があります。 これを行うには、次の手順を実行します。  
  
1.  テキスト エディターで [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web.config ファイルを開きます。 このファイルは、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] インストール パスの WebApplication フォルダーにあります。  
  
2.  [ `mdsWsHttpBehavior` ** \<Servicebehaviors>**] の下のセクションを探します。 ServiceMetadata>要素には、を`httpGetEnabled`に`true`設定します。 ** \<**  
  
    > [!NOTE]  
    >  Web サービスを SSL (Secure Sockets Layer) を介して有効にするには、web.config ファイルの `httpsGetEnabled` セクションで、`true` を `mdsWsHttpBehavior` に設定します。 さらに、SSL 用に構成されるように `mdsWsHTTPBinding` を変更し、非 SSL セクションをコメント アウトする必要もあります。  
  
3.  変更をファイルに保存します。  
  
4.  サービス URL (たとえば、http://yourserver/MDS/service/service.svc) を参照して、メタデータのパブリッシュをテストします。 メタデータ パブリッシュが有効化されると、   
    "サービスを作成しました。" で始まるページが表示されます。  
  
## <a name="creating-proxy-classes-by-using-visual-studio"></a>Visual Studio を使用してプロキシ クラスを作成する  
 Visual Studio 2010 がインストールされている場合、プロキシ クラスを生成する最もシンプルな方法は、プロジェクトに**サービス参照**を追加することです。 サービス参照のアドレスは、[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションの URL に、/service/service.svc を付加したものです。 (例: http://yourserver/MDS/service/service.svc)。 詳細については、「[方法: サービス参照を追加、更新、または削除する](https://go.microsoft.com/fwlink/?LinkId=221167)」を参照してください。  
  
## <a name="creating-proxy-classes-by-using-svcutilexe"></a>Svcutil.exe を使用してプロキシ クラスを作成する  
 Svcutil.exe をコンピューターに[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]インストールする[!INCLUDE[msCoName](../../includes/msconame-md.md)]には、または Windows SDK がインストールされている必要があります。 
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] を使用する場合は、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] コマンド プロンプトでコマンドを実行する必要があります。 詳細については、「[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](https://go.microsoft.com/fwlink/?LinkId=165027)」および「[サービス メタデータからの WCF クライアントの生成](https://go.microsoft.com/fwlink/?LinkId=164821)」を参照してください。  
  
 Svcutil.exe を使用して一連の C# プロキシ クラスを作成するには、次のようなコマンドを使用します。  
  
```  
svcutil.exe http://<server_name:port>/<virtual_path>/Service/Service.svc   
/out:<proxy_name>.cs /messageContract /tcv:Version35   
/noconfig /ct:System.Collections.ObjectModel.Collection`1   
/namespace:*,Microsoft.MasterDataServices  
```  
  
 各値の説明:  
  
-   *servername*:*port*は、をホスト[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]するコンピューターのコンピューター名とポート番号です。  
  
-   *virtual_path*はインターネットインフォメーションサービス (IIS) [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]のの仮想パスです。  
  
-   *proxy_name*は、生成されるプロキシファイルの名前です。  
  
## <a name="see-also"></a>参照  
 [分類された Web サービス操作 &#40;マスターデータサービス&#41;](categorized-web-service-operations-master-data-services.md)  
  
  
