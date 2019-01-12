---
title: sp_addscriptexec (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addscriptexec
- sp_addscriptexec_TSQL
helpviewer_keywords:
- sp_addscriptexec
ms.assetid: 1627db41-6a80-45b6-b0b9-c0b7f9a1c886
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 00c5b4b94bc0a4347991944ccaa7898e75f244f0
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2019
ms.locfileid: "54130692"
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
 [  **@publication=** ] **'**_パブリケーション_**'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@scriptfile=** ] **'**_scriptfile_**'**  
 SQL スクリプト ファイルへの完全なパスを指定します。 *scriptfile*は**nvarchar (4000)**、既定値はありません。  
  
 [  **@skiperror=** ] **'**_skiperror_**'**  
 スクリプト処理の最中にエラーが発生したときに、ディストリビューション エージェントまたはマージ エージェントを停止させる必要があるかどうかを示します。 *SkipError*は**ビット**、既定値は 0。  
  
 **0** = は、エージェントを停止します。  
  
 **1** = エージェントはスクリプトを続行し、エラーを無視します。  
  
 [  **@publisher=** ] **'**_パブリッシャー_**'**  
 以外を指定[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*から発行するときに使用されません、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_addscriptexec**はトランザクション レプリケーションおよびマージ レプリケーションで使用します。  
  
 **sp_addscriptexec**スナップショット レプリケーションは使用されません。  
  
 使用する**sp_addscriptexec**、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービス アカウントの読み取りが必要し、いずれかのスクリプトの場所にスナップショットの場所と読み取りアクセス許可に対する書き込みアクセス許可が格納されます。  
  
 [Sqlcmd ユーティリティ](../../tools/sqlcmd-utility.md)サブスクライバーでスクリプトを実行するために使用され、スクリプトは、サブスクリプション データベースに接続するときに、ディストリビューション エージェントまたはマージ エージェントで使用されるセキュリティ コンテキストで実行されます。 以前のバージョンので、エージェントを実行するときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 [osql ユーティリティ](../../tools/osql-utility.md)の代わりに使用が[sqlcmd](../../tools/sqlcmd-utility.md)します。  
  
 **sp_addscriptexec**を使用してサブスクライバーにスクリプトを適用することで役に立ちます[sqlcmd](../../tools/sqlcmd-utility.md)サブスクライバーにスクリプトの内容を適用します。 ただし、サブスクライバー構成は異なることがあるので、パブリッシャーにポストする前にテストしたスクリプトでも、サブスクライバーでエラーが生じる可能性があります。 *skiperror*にディストリビューション エージェントまたはマージ エージェントはエラーを無視して続行する機能を提供します。 使用[sqlcmd](../../tools/sqlcmd-utility.md)を実行する前にスクリプトをテストする**sp_addscriptexec**します。  
  
> [!NOTE]  
>  スキップされたエラーは、参考情報として、引き続きエージェント履歴に記録されます。  
  
 使用して**sp_addscriptexec** FTP スナップショット配信は、に対してのみサポートを使用してパブリケーションのスクリプト ファイルをポストする[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバー。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_addscriptexec**します。  
  
## <a name="see-also"></a>参照  
 [同期中にスクリプトを実行&#40;レプリケーション TRANSACT-SQL プログラミング&#41;](../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)   
 [データの同期](../../relational-databases/replication/synchronize-data.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
