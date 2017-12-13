---
title: "分析データ ソースに対してコマンドを実行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- AdomdCommand object
- commands [ADOMD.NET]
- ADOMD.NET, commands
ms.assetid: 1a958e5f-fc18-480b-9706-fc44e3b1d534
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 810c6e8bd489bac42a3f4d90d4dbe9990f5ca038
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="executing-commands-against-an-analytical-data-source"></a>分析データ ソースに対するコマンドの実行
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]使用することができます、分析データ ソースへの接続を確立した後、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>オブジェクトに対してコマンドを実行し、そのデータ ソースから結果を返します。 これらのコマンドによるデータ取得には、多次元式 (MDX)、データ マイニング拡張機能 (DMX)、さらには SQL の一部の構文も使用できます。 また、Analysis Services Scripting Language (ASSL) コマンドを使用して、基になるデータベースを変更することもできます。  
  
## <a name="creating-a-command"></a>コマンドの作成  
 コマンドを実行するには、まず、そのコマンドを作成する必要があります。 コマンドを作成するには 2 つの方法があります。  
  
-   1 つは、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> コンストラクターを使用する方法です。この場合、データ ソースに対して実行するコマンドと、そのコマンドの実行対象となる <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトを指定します。  
  
-   もう 1 つは、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.CreateCommand%2A> オブジェクトの <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> メソッドを使用する方法です。  
  
 実行するコマンドのテキストは、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.CommandText%2A> プロパティを使用して照会および変更できます。 作成するコマンドは、実行後に必ずしもデータを返す必要はありません。  
  
## <a name="running-a-command"></a>コマンドを実行します。  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> オブジェクトを作成したら、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> メソッドを使用して、コマンドからさまざまな操作を実行することができます。 次の表は、実行可能な操作の一部を示しています。  
  
|変換先|使用するメソッド|  
|--------|---------------------|  
|結果をデータのストリームとして返す|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A> で <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> オブジェクトを返す|  
|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet> オブジェクトを返す|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteCellSet%2A>|  
|行を返さないコマンドを実行する|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteNonQuery%2A>|  
|返す、 **XMLReader** XML for Analysis (XMLA) に準拠した形式でデータを格納しているオブジェクト|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A>|  
  
### <a name="example-of-running-a-command"></a>コマンドの実行例  
 この例では、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>を処理する XMLA コマンドを実行する、 **Adventure Works DW**データを返さずに、ローカル サーバー上のキューブです。  
  
 [!code-cs[Adomd.NetClient#ExecuteXMLAProcessCommand](../../analysis-services/multidimensional-models-adomd-net-client/codesnippet/csharp/executing-commands-again_1.cs)]  
  
  
