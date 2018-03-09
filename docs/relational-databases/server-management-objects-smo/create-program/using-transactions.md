---
title: "トランザクションを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, transactions
- transactions [SMO]
- SMO [SQL Server], transactions
ms.assetid: 399aded8-bee3-4cfb-a671-1877c7d0de9f
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 556763c88080025e967b7e85b48f5579d2eebcb8
ms.sourcegitcommit: cb2f9d4db45bef37c04064a9493ac2c1d60f2c22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2018
---
# <a name="using-transactions"></a>トランザクションの使用
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) では、トランザクション処理は、<xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトを使用し、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスへの接続を通じて行われます。 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>によってオブジェクトが参照される、<xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>のプロパティ、<xref:Microsoft.SqlServer.Management.Smo.Server>オブジェクトの接続が確立されるとします。 <xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>、<xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A>、および <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A> などのメソッドは <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> オブジェクト プロパティに属しています。  
  
## <a name="see-also"></a>参照  
 [SMO プログラムの作成](../../../relational-databases/server-management-objects-smo/create-program/creating-smo-programs.md)  
  
  
