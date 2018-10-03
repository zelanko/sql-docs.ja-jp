---
title: トランザクションの使用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, transactions
- transactions [SMO]
- SMO [SQL Server], transactions
ms.assetid: 399aded8-bee3-4cfb-a671-1877c7d0de9f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d9f7984be9f48a3651d5dc804faabbc0cd9625f3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48086162"
---
# <a name="using-transactions"></a>トランザクションの使用
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) では、トランザクション処理は、<xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトを使用し、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスへの接続を通じて行われます。 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>によってオブジェクトが参照される、<xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>のプロパティ、<xref:Microsoft.SqlServer.Management.Smo.Server>オブジェクトの接続の確立時にします。 <xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>、<xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A>、および <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A> などのメソッドは <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> オブジェクト プロパティに属しています。  
  
## <a name="see-also"></a>参照  
 [SMO プログラムの作成](creating-smo-programs.md)  
  
  
