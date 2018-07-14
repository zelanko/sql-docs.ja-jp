---
title: ADOMD.NET でトランザクションの実行 |Microsoft Docs
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
- transactions [ADOMD.NET]
- ADOMD.NET, transactions
- AdomdTransaction object
ms.assetid: 7978c28b-c255-43c0-ad05-f38604d4d8fe
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 04157786e3a3d9349c2f1e324291a3a0bda5928d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167598"
---
# <a name="performing-transactions-in-adomdnet"></a>ADOMD.NET でのトランザクションの実行
  ADOMD.NET では、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> オブジェクトを使用して、特定の <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトのトランザクション コンテキストを管理できます。 この機能を使用すると、同じコンテキスト内で複数のコマンドを実行できます。 各コマンドは同じデータを読み込みます。各コマンドの実行間で読み込まれるデータは変更されません。  
  
> [!NOTE]  
>  <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> クラスは `System.Data.IDbTransaction` インターフェイスの実装で、[!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework クラス ライブラリの一部であり、トランザクションをサポートするすべての .NET Framework データ プロバイダーにより実装されます。  
  
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
 [ADOMD.NET での接続を確立します。](connections-in-adomd-net.md)   
 [ADOMD.NET クライアント プログラミング](adomd-net-client-programming.md)  
  
  
