---
title: トランザクションを使用して |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, transactions
- transactions [SMO]
- SMO [SQL Server], transactions
ms.assetid: 399aded8-bee3-4cfb-a671-1877c7d0de9f
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2c132ac199fb6af9e0349c463d5b30954acbf8bd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174436"
---
# <a name="using-transactions"></a>トランザクションの使用
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) では、トランザクション処理は、<xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトを使用し、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスへの接続を通じて行われます。 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>によってオブジェクトが参照される、<xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>のプロパティ、<xref:Microsoft.SqlServer.Management.Smo.Server>オブジェクトの接続が確立されるとします。 <xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>、<xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A>、および <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A> などのメソッドは <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> オブジェクト プロパティに属しています。  
  
## <a name="see-also"></a>参照  
 [SMO プログラムの作成](creating-smo-programs.md)  
  
  