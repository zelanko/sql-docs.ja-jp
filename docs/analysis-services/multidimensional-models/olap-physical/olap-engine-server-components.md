---
title: OLAP エンジンのサーバー コンポーネント |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2e8acd27d64d2aaed12cffd1e05fc2faf62da044
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68208599"
---
# <a name="olap-engine-server-components"></a>OLAP エンジンのサーバー コンポーネント
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  サーバー コンポーネント[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]は、 **msmdsrv.exe**アプリケーション、Windows サービスとして実行されます。 このアプリケーションは、セキュリティ コンポーネント、XML for Analysis (XMLA) リスナー コンポーネント、クエリ プロセッサ コンポーネント、および次の機能を実行するその他多くの内部コンポーネントで構成されています。  
  
-   クライアントから受信したステートメントの解析  
  
-   メタデータの管理  
  
-   トランザクションの処理  
  
-   計算の処理  
  
-   ディメンションおよびセル データの格納  
  
-   集計の作成  
  
-   クエリのスケジュール設定  
  
-   オブジェクトのキャッシュ  
  
-   サーバー リソースの管理  
  
## <a name="architectural-diagram"></a>アーキテクチャの図  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスはスタンドアロン サービスとして実行され、サービスとの通信は、HTTP または TCP を使用して XML for Analysis (XMLA) 経由で行われます。 AMO は、ユーザー アプリケーションと [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスの間のレイヤーです。 このレイヤーは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 管理オブジェクトへのアクセスを提供します。 AMO は、クライアント アプリケーションからコマンドを受け取り、それを [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス用の XMLA メッセージに変換するクラス ライブラリです。 AMO は、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス オブジェクトをクラスとして、エンド ユーザー アプリケーションに提示します。このクラスには、コマンドを実行するメソッド メンバーと、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] オブジェクトのデータを持つプロパティ メンバーが含まれます。  
  
 次の図は、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] コンポーネントのアーキテクチャを示しており、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス内で実行されるすべての主要な要素と、インスタンスと連携するすべてのユーザー コンポーネントを含んでいます。 また、この図は、XML for Analysis (XMLA) リスナーと、HTTP または TCP のいずれかを使用する以外に、インスタンスにアクセスする方法がないことも示しています。  
  
 ![Analysis Services システムのアーキテクチャ ダイアグラム](../../../analysis-services/data-mining/media/analysisservicessystemarchitecture.gif "Analysis Services システムのアーキテクチャ ダイアグラム")  
  
## <a name="xmla-listener"></a>XMLA リスナー  
 XMLA リスナー コンポーネントでは、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] とそのクライアントの間のすべての XMLA 通信が処理されます。 msmdsrv.ini ファイルの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] **Port** 構成設定を使用すると、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスがリッスンするポートを指定できます。 このファイルの 0 の値は、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] が既定のポートをリッスンすることを示します。 特に指定がなければ、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では次の既定の TCP ポートが使用されます。  
  
|Port|説明|  
|----------|-----------------|  
|2383|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]の既定のインスタンスです。|  
|2382|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]の他のインスタンスのリダイレクターです。|  
|サーバーの起動時に動的に割り当てられます。|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]の名前付きインスタンスです。|  
  
 参照してください[Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](../../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)の詳細。  
  
## <a name="see-also"></a>関連項目  
 [オブジェクトの名前付け規則&#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/olap-physical/object-naming-rules-analysis-services.md)   
 [物理アーキテクチャ &#40;Analysis Services - 多次元データ&#41;](../../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-physical-architecture.md)   
 [論理アーキテクチャ&#40;Analysis Services - 多次元データ&#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)  
  
  
