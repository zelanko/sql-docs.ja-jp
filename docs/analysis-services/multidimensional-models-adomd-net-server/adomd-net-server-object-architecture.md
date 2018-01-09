---
title: "ADOMD.NET サーバー オブジェクト アーキテクチャ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- ADOMD.NET, object model
- object model [ADOMD.NET]
ms.assetid: bdc81de9-b390-4654-b62a-cd6c0c9ca10d
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8667b471ada51c0c9de24418ec140ada4d5d39ce
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="adomdnet-server-object-architecture"></a>ADOMD.NET サーバー オブジェクト アーキテクチャ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]ADOMD.NET サーバー オブジェクトは、ユーザー定義関数 (Udf) やストアド プロシージャの作成に使用できるヘルパー オブジェクト[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。  
  
> [!NOTE]  
>  使用する、 **Microsoft.AnalysisServices.AdomdServer**名前空間 (およびこれらのオブジェクト)、UDF プロジェクトやストアド プロシージャに msmgdsrv.dll への参照を追加する必要があります。  
  
 ![ADOMD.NET サーバー オブジェクトのリレーションシップが表示](../../analysis-services/multidimensional-models-adomd-net-server/media/adomdnetserverobjectmodel.gif "ADOMD.NET サーバーにおけるオブジェクトのリレーションシップを示しています。")  
ADOMD.NET オブジェクト モデル  
  
 ADOMD.NET オブジェクト階層との対話は、通常、次の表で説明するように、最上位層の 1 つまたは複数のオブジェクトで開始されます。  
  
|変換先|使用するオブジェクト|  
|--------|---------------------|  
|多次元式 (MDX) を評価する|<xref:Microsoft.AnalysisServices.AdomdServer.Expression><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Expression> オブジェクトを使用すると、MDX 式を実行して、その式を特定の組で評価できます。|  
|完全な MDX ステートメントを作成せずに MDX 関数を実行できるようにする|<xref:Microsoft.AnalysisServices.AdomdServer.MDX><br /> <xref:Microsoft.AnalysisServices.AdomdServer.MDX> オブジェクトは、あらかじめ定義された MDX 関数を <xref:Microsoft.AnalysisServices.AdomdServer.Expression> オブジェクトを使用せずに呼び出す場合に便利です。 <xref:Microsoft.AnalysisServices.AdomdServer.MDX> オブジェクトのその他の機能は今後のリリースで使用できるようになります。|  
|UDF の現在の実行コンテキストを表す|<xref:Microsoft.AnalysisServices.AdomdServer.Context><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Context> オブジェクトは、現在のキューブまたはマイニング モデルやさまざまなメタデータ コレクションなどの情報を公開します。 <xref:Microsoft.AnalysisServices.AdomdServer.Context> オブジェクトの主な使用例の 1 つが、<xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy.CurrentMember%2A> オブジェクトの <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy> プロパティです。 これにより、UDF やストアド プロシージャの作成者は、クエリが特定のディメンションのどのメンバーを処理しているかに基づいて決定を行うことができます。|  
|セットや組を作成する|<xref:Microsoft.AnalysisServices.AdomdServer.SetBuilder>, <xref:Microsoft.AnalysisServices.AdomdServer.TupleBuilder><br /> <xref:Microsoft.AnalysisServices.AdomdServer.SetBuilder> を使用すると、変更不可のセットを作成できます。<xref:Microsoft.AnalysisServices.AdomdServer.TupleBuilder> を使用すると、変更不可の組を作成できます。|  
|MDX 言語の 6 つの基本的な型の間で暗黙の変換とキャストをサポートする|<xref:Microsoft.AnalysisServices.AdomdServer.MDXValue><br /> <xref:Microsoft.AnalysisServices.AdomdServer.MDXValue> オブジェクトでは、次の型の間で暗黙の変換とキャストが行われます。<br /><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy><br /><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Level><br /><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Member><br /><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Tuple><br /><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Set><br /><br /> スカラー型 (値型)|  
  
## <a name="see-also"></a>参照  
 [ADOMD.NET サーバー プログラミング](../../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
  
