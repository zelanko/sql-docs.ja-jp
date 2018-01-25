---
title: "シャット ダウン (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SHUTDOWN_TSQL
- SHUTDOWN
dev_langs: TSQL
helpviewer_keywords:
- SQL Server, stopping
- shutting down SQL Server
- SHUTDOWN statement
- stopping SQL Server
- immediately stopping SQL Server
ms.assetid: c8b03ff9-688c-4fe8-86e8-bd6bd401c9a4
caps.latest.revision: "31"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: df8ef0a3cfe0ac4adb6f45bddb0bef650fea6ff3
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="shutdown-transact-sql"></a>SHUTDOWN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  SQL Server を直ちに停止します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SHUTDOWN [ WITH NOWAIT ]   
```  
  
## <a name="arguments"></a>引数  
 WITH NOWAIT  
 省略可。 シャット ダウン[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]せず、すべてのデータベースでチェックポイントを実行します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]すべてのユーザー プロセスの停止を試行した後に終了します。 サーバーが再起動すると、完了しなかったトランザクションのロールバック操作が行われます。  
  
## <a name="remarks"></a>解説  
 シャット ダウンをシャット ダウン WITHNOWAIT オプションを使用すると、しない限り、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で。  
  
1.  ログインを無効にする (のメンバーを除く、 **sysadmin**と**serveradmin**固定サーバー ロール) です。  
  
    > [!NOTE]  
    >  現在のすべてのユーザーの一覧を表示するには実行**sp_who**です。  
  
2.  現在実行中の Transact-SQL ステートメントまたはストアド プロシージャが終了するまで待機する。 すべてのアクティブなプロセスとロックの一覧を表示するには実行**sp_who**と**sp_lock**、それぞれします。  
  
3.  各データベースにチェックポイントを挿入する。  
  
 SHUTDOWN ステートメントを使用して、最小限の自動復旧作業するときの必要のメンバー、 **sysadmin**固定サーバー ロールの再起動[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 後に示すツールや方法を使用しても [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を停止できます。 いずれの停止方法でも、すべてのデータベースでチェックポイントが発行されます。 コミットされたデータをデータ キャッシュからフラッシュして、サーバーを停止できます。  
  
-   使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager です。  
  
-   実行して**net stop mssqlserver**の既定のインスタンス、またはを実行して、コマンド プロンプトから **「net stop mssql$ * * * instancename*名前付きインスタンスのコマンド プロンプトからです。  
  
-   [コントロール パネル] の [サービス] を使用する。  
  
 場合**sqlservr.exe**が起動されてから、コマンド プロンプトで ctrl キーを押しながら C キーを押してがシャット ダウン[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 Ctrl+C キーを押してもチェックポイントは挿入されません。  
  
> [!NOTE]  
>  これらのメソッドのいずれかを使用して停止する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]送信、`SERVICE_CONTROL_STOP`メッセージごとに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
## <a name="permissions"></a>権限  
 メンバーにシャット ダウンのアクセス許可が割り当てられている、 **sysadmin**と**serveradmin**は、固定サーバー ロール、およびそれらに転送できません。  
  
## <a name="see-also"></a>参照  
 [チェックポイント &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/checkpoint-transact-sql.md)   
 [sp_lock &#40;です。TRANSACT-SQL と&#41;です。](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md)   
 [sp_who &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)   
 [sqlservr アプリケーション](../../tools/sqlservr-application.md)   
 [データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
  
