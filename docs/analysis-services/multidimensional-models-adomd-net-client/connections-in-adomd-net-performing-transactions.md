---
title: "ADOMD.NET でトランザクションを実行する |Microsoft ドキュメント"
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
- transactions [ADOMD.NET]
- ADOMD.NET, transactions
- AdomdTransaction object
ms.assetid: 7978c28b-c255-43c0-ad05-f38604d4d8fe
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7491ab2b49dd08b0ed1fab4f8f645cd0ac0c66eb
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="connections-in-adomdnet---performing-transactions"></a>ADOMD.NET でのトランザクションの実行での接続
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]ADOMD.NET では、使用する、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction>のトランザクション コンテキストを管理するオブジェクト、指定された<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>オブジェクト。 この機能を使用すると、同じコンテキスト内で複数のコマンドを実行できます。 各コマンドは同じデータを読み込みます。各コマンドの実行間で読み込まれるデータは変更されません。  
  
> [!NOTE]  
>  <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction>クラスは、の実装、 **System.Data.IDbTransaction**インターフェイスの一部、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework クラス ライブラリをサポートするすべての .NET Framework データ プロバイダーによって実装されるとトランザクション。  
  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> オブジェクトは、ダーティ リードを回避するためにデータが読み込まれている間に共有ロックが保持される、READ COMMITTED トランザクションのみをサポートしています。  
  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> を使用してトランザクションを開始します。 トランザクションを使用するには、そのトランザクションを開始した接続に対してコマンドを実行します。 トランザクションが完了したら、トランザクションをロールバックまたはコミットすることができます。  
  
## <a name="starting-a-transaction"></a>トランザクションの開始  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> オブジェクトのインスタンスを作成するには、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.BeginTransaction%2A> オブジェクトの <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> メソッドを呼び出します。 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> オブジェクトのインスタンスの作成例を次に示します。  
  
```  
Dim objTransaction As AdomdTransaction = objConnection.BeginTransaction()  
AdomdTransaction objTransaction = objConnection.BeginTransaction();  
```  
  
## <a name="rolling-back-a-transaction"></a>トランザクションのロールバック  
 既存の不完全なトランザクションをロールバックするには、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction.Rollback%2A> オブジェクトの <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> メソッドを呼び出します。 既存の完全なトランザクションでこのメソッドを呼び出すと、例外がスローされます。  
  
## <a name="committing-a-transaction"></a>トランザクションをコミットします。  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.BeginTransaction%2A> メソッドを呼び出してトランザクションを開始した後で、トランザクションを完了するには、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction.Commit%2A> オブジェクトの <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> メソッドを呼び出します。 既存の完了したトランザクションに対してこのメソッドを呼び出すと、例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [ADOMD.NET で接続を確立します。](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net.md)   
 [ADOMD.NET クライアント プログラミング](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)  
  
  
