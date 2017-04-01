---
title: "default trace enabled サーバー構成オプション | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ログ [SQL Server], トレース"
  - "トレース [SQL Server], ログ"
  - "default trace enabled オプション"
ms.assetid: 1322d668-44f4-469e-8fd6-e0d02a81c8f2
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# default trace enabled サーバー構成オプション
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **default trace enabled** オプションは、既定のトレース ログ ファイルを有効または無効にする場合に使用します。 既定のトレース機能では、主に構成オプションに関連する操作および変更の詳しい永続的なログが提供されます。  
  
> [!WARNING]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 代わりに拡張イベントを使用します。  
  
## 用途  
 既定のトレース機能は、問題が初めて発生したときに、その問題を診断するために必要なログ データを提供することによって、データベース管理者によるトラブルシューティングを支援します。  
  
## 表示  
 既定のトレース ログは、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] で開いて確認するか、`fn_trace_gettable` システム関数を使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] でクエリできます。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、通常のトレース出力ファイルを開く場合と同様に、既定のトレース ログ ファイルを開くことができます。 既定のトレース ログは、ロールオーバー トレース ファイルを使用して、既定により `\MSSQL\LOG` ディレクトリに保存されます。 既定のトレース ログ ファイルのベース ファイル名は `log.trc` です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の標準インストールの場合、既定のトレースが有効になっているため、TraceID 1 になります。 インストール後や他のトレースの作成後に有効にした場合、TraceID の数値が大きくなることがあります。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler を使用してこのトレース ファイルを表示する方法については、「[トレース ファイルを開く&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)」をご覧ください。  
  
### 例:  
 次のステートメントは、既定の場所にある既定のトレース ログを開きます。  
  
```  
SELECT *   
FROM fn_trace_gettable  
('C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\LOG\log.trc', default);  
GO  
  
```  
  
## 構成  
 **default trace enabled** オプションを 1 に設定すると、**既定のトレース**が有効になります。 このオプションの既定値は 1 (ON) です。 0 に設定すると、トレースがオフになります。  
  
 **default trace enabled** オプションは拡張オプションです。 **sp_configure** システム ストアド プロシージャを使用して **default trace enabled** オプションの設定を変更するには、**show advanced options** を 1 に設定する必要があります。 新しい設定は、サーバーを再起動しなくてもすぐに有効になります。  
  
## 参照  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  