---
title: "remote admin connections サーバー構成オプション | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- administrator connections [SQL Server]
- DAC
- connections [SQL Server], dedicated administrator
- remote admin connections option
- dedicated administrator connections [SQL Server]
ms.assetid: bf32b60a-7a48-401f-b6be-b5e2e46c413f
caps.latest.revision: "15"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: ad17a98021cf012a1d83b3b087dbd7f0760a41c8
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="remote-admin-connections-server-configuration-option"></a>remote admin connections サーバー構成オプション
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には専用管理者接続 (DAC) があります。 管理者は、DAC により、実行中のサーバーにアクセスして、診断関数や [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行したり、サーバー上の問題のトラブルシューティングを行ったりすることができます。このことは、サーバーがロックされていたり、異常状態で実行されたりしていて、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 接続に応答していない場合も同じです。 既定では、DAC はそのサーバー上のクライアントからしか使用できません。 リモート コンピューター上のクライアント アプリケーションから DAC を使用できるようにするには、sp_configure の remote admin connections オプションを使用します。  
  
 既定では、DAC はループバック IP アドレス (127.0.0.1)、ポート 1434 だけをリッスンします。 TCP ポート 1434 を使用できない場合は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] の起動時に TCP ポートが動的に割り当てられます。 複数の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスがコンピューターにインストールされている場合、TCP ポート番号についてはエラー ログを確認してください。  
  
 次の表は、remote admin connections オプションの使用可能な値の一覧です。  
  
|値|説明|  
|-----------|-----------------|  
|0|ローカル接続のみで DAC を使用できることを示します。|  
|1|リモート接続で DAC を使用できることを示します。|  
  
## <a name="example"></a>例  
 次の例では、リモート コンピューターから DAC を使用できるようにします。  
  
```  
sp_configure 'remote admin connections', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データベース管理者用の診断接続](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)  
  
  
