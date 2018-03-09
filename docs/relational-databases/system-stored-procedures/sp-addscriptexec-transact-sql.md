---
title: "sp_addscriptexec (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_addscriptexec
- sp_addscriptexec_TSQL
helpviewer_keywords:
- sp_addscriptexec
ms.assetid: 1627db41-6a80-45b6-b0b9-c0b7f9a1c886
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 13f3104f91c785252f573e653d3344a03091dd13
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spaddscriptexec-transact-sql"></a>sp_addscriptexec (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  SQL スクリプト (.sql file) をパブリケーションのすべてのサブスクライバーにポストします。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addscriptexec [ @publication = ] publication  
    [ , [ @scriptfile = ] 'scriptfile' ]  
    [ , [ @skiperror = ] 'skiperror' ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication=** ] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@scriptfile=** ] **'***scriptfile***'**  
 SQL スクリプト ファイルへの完全なパスを指定します。 *scriptfile*は**nvarchar (4000)**、既定値はありません。  
  
 [  **@skiperror=** ] **'***skiperror***'**  
 スクリプト処理の最中にエラーが発生したときに、ディストリビューション エージェントまたはマージ エージェントを停止させる必要があるかどうかを示します。 *SkipError*は**ビット**、既定値は 0 です。  
  
 **0** = エージェントは停止します。  
  
 **1** = エージェントはスクリプトを続行し、エラーを無視します。  
  
 [  **@publisher=** ] **'***パブリッシャー***'**  
 指定以外[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*から発行するときに使用しないで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_addscriptexec**は、トランザクション レプリケーションおよびマージ レプリケーションで使用します。  
  
 **sp_addscriptexec**スナップショット レプリケーションでは使用されません。  
  
 使用する**sp_addscriptexec**、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービス アカウントの読み取りが必要し、いずれかのスクリプトの場所にスナップショットの場所と読み取りアクセス許可に対する書き込みアクセス許可が格納されます。  
  
 [Sqlcmd ユーティリティ](../../tools/sqlcmd-utility.md)サブスクライバーでスクリプトを実行するために使用され、スクリプトは、サブスクリプション データベースに接続するときに、ディストリビューション エージェントまたはマージ エージェントによって使用されるセキュリティ コンテキストで実行します。 以前のバージョンので、エージェントを実行するときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 [osql ユーティリティ](../../tools/osql-utility.md)の代わりに使用される[sqlcmd](../../tools/sqlcmd-utility.md)です。  
  
 **sp_addscriptexec**使用してサブスクライバーにスクリプトを適用する面で役に立ちます[sqlcmd](../../tools/sqlcmd-utility.md)サブスクライバーにスクリプトの内容を適用します。 ただし、サブスクライバー構成は異なることがあるので、パブリッシャーにポストする前にテストしたスクリプトでも、サブスクライバーでエラーが生じる可能性があります。 *skiperror*にディストリビューション エージェントまたはマージ エージェントはエラーを無視して続行する機能を提供します。 使用して[sqlcmd](../../tools/sqlcmd-utility.md)を実行する前にスクリプトをテストする**sp_addscriptexec**です。  
  
> [!NOTE]  
>  スキップされたエラーは、参考情報として、引き続きエージェント履歴に記録されます。  
  
 使用して**sp_addscriptexec**パブリケーションの FTP スナップショット配信はサポートされてのみを使用してスクリプト ファイルを送信する[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバーです。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_addscriptexec**です。  
  
## <a name="see-also"></a>参照  
 [同期 &#40; の中にスクリプトを実行します。レプリケーション TRANSACT-SQL プログラミング &#41;](../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)   
 [データの同期](../../relational-databases/replication/synchronize-data.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
