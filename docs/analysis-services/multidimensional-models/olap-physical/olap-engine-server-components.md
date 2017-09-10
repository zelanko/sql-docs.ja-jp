---
title: "OLAP エンジンのサーバー コンポーネント |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Analysis Services, architecture
- ports [Analysis Services]
- XML/A listener
- server architecture [Analysis Services]
ms.assetid: 5193c976-9dcd-459c-abba-8c3c44e7a7f2
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 86a69dc1076124377e3b916b441dd78edb9a8f82
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="olap-engine-server-components"></a>OLAP エンジンのサーバー コンポーネント
  サーバー コンポーネントの[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]は、 **msmdsrv.exe** Windows サービスとして実行されるアプリケーション。 このアプリケーションは、セキュリティ コンポーネント、XML for Analysis (XMLA) リスナー コンポーネント、クエリ プロセッサ コンポーネント、および次の機能を実行するその他多くの内部コンポーネントで構成されています。  
  
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
  
 ![Analysis Services のシステム アーキテクチャ図](../../../analysis-services/data-mining/media/analysisservicessystemarchitecture.gif "Analysis Services のシステム アーキテクチャ図")  
  
## <a name="xmla-listener"></a>XMLA リスナー  
 XMLA リスナー コンポーネントでは、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] とそのクライアントの間のすべての XMLA 通信が処理されます。 msmdsrv.ini ファイルの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] **Port** 構成設定を使用すると、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスがリッスンするポートを指定できます。 このファイルの 0 の値は、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] が既定のポートをリッスンすることを示します。 特に指定がなければ、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では次の既定の TCP ポートが使用されます。  
  
|Port|Description|  
|----------|-----------------|  
|2383|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]の既定のインスタンスです。|  
|2382|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]の他のインスタンスのリダイレクターです。|  
|サーバーの起動時に動的に割り当てられます。|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]の名前付きインスタンスです。|  
  
 参照してください[Analysis Services のアクセスを許可するための Windows ファイアウォールを構成する](../../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)詳細についてはします。  
  
## <a name="see-also"></a>参照  
 [オブジェクトの名前付けの規則と #40 です。Analysis Services &#41;](../../../analysis-services/multidimensional-models/olap-physical/object-naming-rules-analysis-services.md)   
 [物理アーキテクチャ & #40 です。Analysis Services - 多次元データ &#41;](../../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-physical-architecture.md)   
 [論理アーキテクチャと #40 です。Analysis Services - 多次元データ &#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)  
  
  
