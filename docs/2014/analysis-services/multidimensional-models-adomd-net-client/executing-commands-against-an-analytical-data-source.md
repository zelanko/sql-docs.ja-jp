---
title: 分析データ ソースに対するコマンドの実行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- AdomdCommand object
- commands [ADOMD.NET]
- ADOMD.NET, commands
ms.assetid: 1a958e5f-fc18-480b-9706-fc44e3b1d534
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 36d94ba3ae75f2b3d59e0fb159ee639a5f2edb43
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37202022"
---
# <a name="executing-commands-against-an-analytical-data-source"></a>分析データ ソースに対するコマンドの実行
  分析データ ソースへの接続を確立した後、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> オブジェクトを使用して、そのデータ ソースに対してコマンドを実行し、結果を取得することができます。 これらのコマンドによるデータ取得には、多次元式 (MDX)、データ マイニング拡張機能 (DMX)、さらには SQL の一部の構文も使用できます。 また、Analysis Services Scripting Language (ASSL) コマンドを使用して、基になるデータベースを変更することもできます。  
  
## <a name="creating-a-command"></a>コマンドの作成  
 コマンドを実行するには、まず、そのコマンドを作成する必要があります。 コマンドを作成するには 2 つの方法があります。  
  
-   1 つは、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> コンストラクターを使用する方法です。この場合、データ ソースに対して実行するコマンドと、そのコマンドの実行対象となる <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトを指定します。  
  
-   もう 1 つは、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.CreateCommand%2A> オブジェクトの <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> メソッドを使用する方法です。  
  
 実行するコマンドのテキストは、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.CommandText%2A> プロパティを使用して照会および変更できます。 作成するコマンドは、実行後に必ずしもデータを返す必要はありません。  
  
## <a name="running-a-command"></a>コマンドの実行  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> オブジェクトを作成したら、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> メソッドを使用して、コマンドからさまざまな操作を実行することができます。 次の表は、実行可能な操作の一部を示しています。  
  
|変換先|使用するメソッド|  
|--------|---------------------|  
|結果をデータのストリームとして返す|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A> で <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> オブジェクトを返す|  
|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet> オブジェクトを返す|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteCellSet%2A>|  
|行を返さないコマンドを実行する|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteNonQuery%2A>|  
|XML for Analysis (XMLA) に準拠した形式のデータを含む `XMLReader` オブジェクトを返す|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A>|  
  
### <a name="example-of-running-a-command"></a>コマンドの実行例  
 この例では、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> を使用して XMLA コマンドを実行します。このコマンドは、ローカル サーバー上の `Adventure Works DW` キューブを処理し、データを返しません。  
  
 [!code-csharp[Adomd.NetClient#ExecuteXMLAProcessCommand](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#executexmlaprocesscommand)]  
  
  
