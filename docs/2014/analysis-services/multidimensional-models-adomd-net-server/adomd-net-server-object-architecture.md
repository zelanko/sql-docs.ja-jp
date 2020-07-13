---
title: ADOMD.NET サーバーオブジェクトのアーキテクチャ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- ADOMD.NET, object model
- object model [ADOMD.NET]
ms.assetid: bdc81de9-b390-4654-b62a-cd6c0c9ca10d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 33a8f420f985c9e62c7d7f275e7de370a6988e8d
ms.sourcegitcommit: 04ba0ed3d860db038078609d6e348b0650739f55
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "85469057"
---
# <a name="adomdnet-server-object-architecture"></a>ADOMD.NET サーバー オブジェクト アーキテクチャ
  ADOMD.NET サーバーオブジェクトは、でユーザー定義関数 (Udf) またはストアドプロシージャを作成するために使用できるヘルパーオブジェクトです [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。  
  
> [!NOTE]  
>  `Microsoft.AnalysisServices.AdomdServer` 名前空間 (およびこれらのオブジェクト) を使用するには、UDF プロジェクトやストアド プロシージャに msmgdsrv.dll への参照を追加する必要があります。  
  
 ![ADOMD.NET サーバーにおけるオブジェクトの関係](../../analysis-services/dev-guide/media/adomdnetserverobjectmodel.gif "ADOMD.NET サーバーにおけるオブジェクトの関係")  
ADOMD.NET オブジェクト モデル  
  
 ADOMD.NET オブジェクト階層との対話は、通常、次の表で説明するように、最上位層の 1 つまたは複数のオブジェクトで開始されます。  
  
|終了|使用するオブジェクト|  
|--------|---------------------|  
|多次元式 (MDX) を評価する|[Microsoft.analysisservices.sharepoint.integration.dll を指定します。](/previous-versions/sql/sql-server-2014/ms143609(v=sql.120))<br /> [Microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/ms143609(v=sql.120))オブジェクトを使用すると、MDX 式を実行し、指定した組でその式を評価することができます。|  
|完全な MDX ステートメントを作成せずに MDX 関数を実行できるようにする|[Microsoft.analysisservices.sharepoint.integration.dll (MDX)](/previous-versions/sql/sql-server-2014/ms143616(v=sql.120))<br /> [Microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/ms143616(v=sql.120))オブジェクトは、 [microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/ms143609(v=sql.120))オブジェクトを使用せずに、定義済みの mdx 関数を呼び出す場合に便利です。 Microsoft.analysisservices.sharepoint.integration.dll オブジェクトの追加関数は、今後のリリースで使用できるようになります[。](/previous-versions/sql/sql-server-2014/ms143616(v=sql.120))|  
|UDF の現在の実行コンテキストを表す|[Microsoft.analysisservices.sharepoint.integration.dll (Microsoft. コンテキスト)](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120))<br /> [Microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120))オブジェクトは、現在のキューブまたはマイニングモデルやさまざまなメタデータコレクションなどの情報を公開します。 Microsoft.analysisservices.sharepoint.integration.dll オブジェクトの1つの主な使用方法は、Microsoft.analysisservices.sharepoint.integration.dll オブジェクトの[microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/ms137044(v=sql.120))のプロパティであるということです。この[コンテキスト](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120))オブジェクトは、 [Microsoft.AnalysisServices.AdomdServer.Hierarchy](/previous-versions/sql/sql-server-2014/ms143578(v=sql.120))のプロパティです。 これにより、UDF やストアド プロシージャの作成者は、クエリが特定のディメンションのどのメンバーを処理しているかに基づいて決定を行うことができます。|  
|セットや組を作成する|[Microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/ms144510(v=sql.120))、 [microsoft.analysisservices.sharepoint.integration.dll、TupleBuilder](/previous-versions/sql/sql-server-2014/ms145407(v=sql.120))のようになっています。<br /> Microsoft.analysisservices.sharepoint.integration.dll は、変更[でき](/previous-versions/sql/sql-server-2014/ms144510(v=sql.120))ないセットを作成する方法を提供します。 [microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/ms145407(v=sql.120))は、変更できない組を作成する方法を提供します。|  
|MDX 言語の 6 つの基本的な型の間で暗黙の変換とキャストをサポートする|[Microsoft.analysisservices.sharepoint.integration.dll です。 MDXValue](/previous-versions/sql/sql-server-2014/ms143573(v=sql.120))<br /> [Microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/ms143573(v=sql.120))オブジェクトは、次の型の間で暗黙的な変換とキャストを提供します。<br /><br /> -   [Microsoft.analysisservices.sharepoint.integration.dll (Microsoft. 階層)](/previous-versions/sql/sql-server-2014/ms143578(v=sql.120))<br />-   [Microsoft.analysisservices.sharepoint.integration.dll (レベル)](/previous-versions/sql/sql-server-2014/ms143581(v=sql.120))<br />-   [Microsoft.analysisservices.sharepoint.integration.dll (Microsoft. メンバー)](/previous-versions/sql/sql-server-2014/ms143820(v=sql.120))<br />-   [Microsoft.analysisservices.sharepoint.integration.dll (. タプル)](/previous-versions/sql/sql-server-2014/ms145330(v=sql.120))<br />-   [Microsoft.analysisservices.sharepoint.integration.dll を設定します。](/previous-versions/sql/sql-server-2014/ms144530(v=sql.120))<br />-スカラー、値型|  
  
## <a name="see-also"></a>関連項目  
 [ADOMD.NET サーバー プログラミング](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
  
