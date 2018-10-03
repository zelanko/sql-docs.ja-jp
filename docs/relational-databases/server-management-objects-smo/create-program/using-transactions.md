---
title: トランザクションの使用 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, transactions
- transactions [SMO]
- SMO [SQL Server], transactions
ms.assetid: 399aded8-bee3-4cfb-a671-1877c7d0de9f
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7d00f22d8e7cf8b01e35dc12482c8fe7dcfcde9b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47693930"
---
# <a name="using-transactions"></a>トランザクションの使用
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) では、トランザクション処理は、<xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトを使用し、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスへの接続を通じて行われます。 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>によってオブジェクトが参照される、<xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>のプロパティ、<xref:Microsoft.SqlServer.Management.Smo.Server>オブジェクトの接続の確立時にします。 <xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>、<xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A>、および <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A> などのメソッドは <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> オブジェクト プロパティに属しています。  
  
## <a name="see-also"></a>参照  
 [SMO プログラムの作成](../../../relational-databases/server-management-objects-smo/create-program/creating-smo-programs.md)  
  
  
