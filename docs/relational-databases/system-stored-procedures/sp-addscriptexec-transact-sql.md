---
title: sp_addscriptexec (Transact-sql) |Microsoft Docs
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
ms.openlocfilehash: e8ae792ba7f8422e841abbbe2f80b096497df993
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68022451"
---
# <a name="sp_addscriptexec-transact-sql"></a>sp_addscriptexec (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  SQL スクリプト (.sql ファイル) をパブリケーションのすべてのサブスクライバーにポストします。 このストアドプロシージャは、パブリッシャー側でパブリケーションデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addscriptexec [ @publication = ] publication  
    [ , [ @scriptfile = ] 'scriptfile' ]  
    [ , [ @skiperror = ] 'skiperror' ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'`パブリケーションの名前を指定します。 *publication*は**sysname**,、既定値はありません。  
  
`[ @scriptfile = ] 'scriptfile'`SQL スクリプトファイルへの完全なパスです。 *scriptfile*は**nvarchar (4000)**,、既定値はありません。  
  
`[ @skiperror = ] 'skiperror'`スクリプトの処理中にエラーが発生した場合に、ディストリビューションエージェントまたはマージエージェントを停止するかどうかを示します。 *SkipError*は**ビット**,、既定値は0です。  
  
 **0** = エージェントは停止します。  
  
 **1** = エージェントはスクリプトを続行し、エラーを無視します。  
  
`[ @publisher = ] 'publisher'`以外[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のパブリッシャーを指定します。 *publisher*は**sysname**で、既定値は NULL です。  
  
> [!NOTE]  
>  *publisher*パブリッシャーからパブリッシュする場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーを使用しないでください。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>Remarks  
 **sp_addscriptexec**は、トランザクションレプリケーションおよびマージレプリケーションで使用します。  
  
 **sp_addscriptexec**は、スナップショットレプリケーションには使用されません。  
  
 **Sp_addscriptexec**を使用するに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、サービスアカウントに、スナップショットの場所に対する読み取り権限と書き込み権限、およびスクリプトが格納されている場所に対する読み取り権限が必要です。  
  
 [Sqlcmd ユーティリティ](../../tools/sqlcmd-utility.md)は、サブスクライバーでスクリプトを実行するために使用されます。スクリプトは、サブスクリプションデータベースに接続するときに、ディストリビューションエージェントまたはマージエージェントによって使用されるセキュリティコンテキストで実行されます。 以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でエージェントを実行すると、 [sqlcmd](../../tools/sqlcmd-utility.md)ではなく[osql ユーティリティ](../../tools/osql-utility.md)が使用されます。  
  
 **sp_addscriptexec**は、スクリプトをサブスクライバーに適用する場合に役立ちます。 [sqlcmd](../../tools/sqlcmd-utility.md)を使用して、スクリプトの内容をサブスクライバーに適用します。 ただし、サブスクライバー構成は異なることがあるので、パブリッシャーにポストする前にテストしたスクリプトでも、サブスクライバーでエラーが生じる可能性があります。 *skiperror*は、ディストリビューションエージェントまたはマージエージェントエラーを無視して続行する機能を提供します。 [Sqlcmd](../../tools/sqlcmd-utility.md)を使用して、 **sp_addscriptexec**を実行する前にスクリプトをテストします。  
  
> [!NOTE]  
>  スキップされたエラーは、参照のためにエージェント履歴に引き続き記録されます。  
  
 スナップショット**sp_addscriptexec**配信に FTP を使用してパブリケーションのスクリプトファイルをポストするために sp_addscriptexec [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用することは、サブスクライバーに対してのみサポートされています。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_addscriptexec**を実行できるのは、固定サーバーロール**sysadmin**または固定データベースロール**db_owner**のメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [同期中にスクリプトを実行 &#40;レプリケーション Transact-sql プログラミング&#41;](../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)   
 [データの同期](../../relational-databases/replication/synchronize-data.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
