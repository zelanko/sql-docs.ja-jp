---
title: "ADOMD.NET クライアント プログラミング |Microsoft ドキュメント"
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
- programming [ADOMD.NET]
- ADOMD.NET, programming
ms.assetid: 55156115-ecd1-4ed9-876e-23406af9bbf9
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f8a7debab516c8f48b4184c66028c42f44d5bdd2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="adomdnet-client-programming"></a>ADOMD.NET クライアント プログラミング
  ADOMD.NET クライアント コンポーネントが内に存在、 **Microsoft.AnalysisServices.AdomdClient**名前空間 (microsoft.analysisservices.adomdclient.dll)。 これらのクライアント コンポーネントによりクライアントの機能と分析データ ストアから簡単にクエリ データおよびメタデータへの中間層アプリケーションなど[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。  
  
## <a name="using-the-adomdnet-client-objects"></a>ADOMD.NET クライアント オブジェクトの使用  
 分析データ ソースに対してクエリを実行する場合、必ず実行しなければならない共通タスクがいくつかあります。 次の表に、ADOMD.NET クライアント オブジェクトを使用してそのようなクエリを実行する際の共通タスクを示します。  
  
|タスク|Description|  
|----------|-----------------|  
|[ADOMD.NET で接続を確立します。](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net.md)|ADOMD.NET では、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトを使用して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースなどの分析データ ソースに接続します。 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトを使用して、分析データ ソースからコマンドの実行、データの取得、およびメタデータの取得を実行できます。|  
|[分析データ ソースからメタデータを取得します。](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)|分析データ ソースに接続したら、さまざまなオブジェクトを使用して、そのデータ ソースに関する情報を取得できます。 この機能を使用して、アプリケーションは、接続先のデータ ソースに適合することができます。|  
|[分析データ ソースに対してコマンドを実行します。](../../analysis-services/multidimensional-models-adomd-net-client/executing-commands-against-an-analytical-data-source.md)|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> オブジェクトには、基になる分析データ ソースに対してコマンドを実行するために必要なインターフェイスが用意されています。|  
|[分析データ ソースからデータを取得します。](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-from-an-analytical-data-source.md)|データが取得できませんでした、いずれかを使用して解析とコマンドの実行後、 <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>、 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>、または**System.XmlReader**オブジェクト。|  
|[ADOMD.NET でトランザクションを実行します。](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net-performing-transactions.md)|この表の上記に記載されているすべての操作は READ COMMITTED トランザクション内で実行できます。READ COMMITTED トランザクションでは、ダーティ リードを回避するため、データの読み込み中は共有ロックが保持されます。 ただし、その場合でも、トランザクションが終了する前にデータが変更され、反復不能読み取りやファントム データとなる場合があります。 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> オブジェクトは、ADOMD.NET でトランザクション機能を提供します。|  
  
 ADOMD.NET オブジェクト階層との対話は、通常、次の表で説明するように、最上位層の 1 つまたは複数のオブジェクトで開始されます。  
  
|変換先|使用するオブジェクト|  
|--------|---------------------|  
|分析データ ソースへの接続|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection><br /> <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトは、データ ソースへの接続とデータ ソースのメタデータの両方を表します。 接続するなど、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ローカル キューブ (.cub) ファイル、およびを調べて、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Cubes%2A>分析データ ソースにあるキューブに関するメタデータを取得するプロパティです。 このオブジェクトの実装を表すも、 **IDbConnection**インターフェイス、すべての .NET Framework データ プロバイダーで必要とされるインターフェイス。|  
|データ ソースのデータ マイニング機能の検出|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection><br /> <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトは、次に示すいくつかのマイニング コレクションを示します。<br /><br /><br /><br /> <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelCollection> には、データ ソース内のマイニング モデルの一覧が含まれています。<br /><br /><br /><br /> <xref:Microsoft.AnalysisServices.AdomdClient.MiningServiceCollection> は、使用可能なマイニング アルゴリズムに関する情報を提供します。<br /><br /><br /><br /> <xref:Microsoft.AnalysisServices.AdomdClient.MiningStructureCollection> は、サーバーのマイニング構造に関する情報を示します。|  
|データ ソースのクエリ|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand><br /> <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> オブジェクトは、サーバーに送信されるステートメントまたはクエリを表します。 データ ソースへの接続が確立したら、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> オブジェクトを使用して、多次元式 (MDX) またはデータ マイニング拡張機能 (DMX) など、サポートされる言語でステートメントを実行します。 また、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> オブジェクトを使用して、<xref:Microsoft.AnalysisServices.AdomdClient.CellSet> オブジェクトまたは <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> オブジェクトの形式で結果を返すこともできます。|  
|高速かつ効率的な方法によるデータの取得|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader><br /> <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> は、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> オブジェクトの <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A> メソッドまたは <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> メソッドへの呼び出しを使用して作成できます。 このオブジェクトを実装して、 **IDbDataReader**からインターフェイス、 **System.Data** .NET Framework クラス ライブラリの名前空間。|  
|大量のメタデータを含む分析データの取得|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet><br /> <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> は、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> の <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteCellSet%2A> メソッドまたは <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> メソッドへの呼び出しを使用して作成できます。 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> から <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> が返されたら、<xref:Microsoft.AnalysisServices.AdomdClient.CellSet> に含まれている分析データを調べることができます。|  
|使用可能なディメンション、メジャー、名前付きセットなどキューブに関するメタデータの取得|<xref:Microsoft.AnalysisServices.AdomdClient.CubeDef><br /> <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> は、キューブに関するメタデータを表します。 <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> から <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> を参照します。|  
|使用してデータを取得、 **System.Data.IDbDataAdapter**インターフェイス|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter><br /> <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter> は、既存の .NET Framework クライアント アプリケーションの読み取り専用サポートを提供します。|  
  
## <a name="see-also"></a>参照  
 [ADOMD.NET サーバー プログラミング](../../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)   
 [ADOMD.NET での開発](../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)  
  
  

