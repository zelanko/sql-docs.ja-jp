---
title: sp_removedbreplication (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_removedbreplication
- sp_removedbreplication_TSQL
helpviewer_keywords:
- sp_removedbreplication
ms.assetid: cb98d571-d1eb-467b-91f7-a6e091009672
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0965c656c5c6b0cef690bb3fbaa7bbc2a7965104
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52747694"
---
# <a name="spremovedbreplication-transact-sql"></a>sp_removedbreplication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このストアド プロシージャにより、SQL Server のパブリッシャー インスタンス側のパブリケーション データベース、または SQL Server のサブスクライバー インスタンス側のサブスクリプション データベースから、すべてのレプリケーション オブジェクトが削除されます。 適切なデータベースで実行するか、または同じインスタンスにある別のデータベースのコンテキストで実行する場合は、レプリケーション オブジェクトを削除するデータベースを指定します。 このプロシージャでは、ディストリビューション データベースなどその他のデータベースからオブジェクトが削除されることはありません。  
  
> [!NOTE]  
>  このプロシージャは、他の方法でレプリケーション オブジェクトを削除できなかった場合にのみ使用してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_removedbreplication [ [ @dbname = ] 'dbname' ]  
    [ , [ @type = ] type ]   
```  
  
## <a name="arguments"></a>引数  
 [ **@dbname=**] **'***dbname***'**  
 データベースの名前です。 *dbname* のデータ型は **sysname**で、既定値は NULL です。 NULL の場合は、現在のデータベースが使用されます。  
  
 [ **@type** =]*型*  
 データベース オブジェクトを削除するレプリケーションの種類を指定します。 *型*は**nvarchar (5)** 値は次のいずれかを指定できます。  
  
|||  
|-|-|  
|**tran**|トランザクション レプリケーション パブリッシング オブジェクトを削除。|  
|**マージ**|マージ レプリケーション パブリッシング オブジェクトを削除。|  
|**どちらも**(既定値)|すべてのレプリケーション パブリッシング オブジェクトを削除。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_removedbreplication**はあらゆる種類のレプリケーションで使用します。  
  
 **sp_removedbreplication**を復元するが必要なレプリケーション オブジェクトを持たないレプリケートされたデータベースを復元する場合に便利です。  
  
 **sp_removedbreplication**読み取り専用とマークされているデータベースに対しては使用できません。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_removedbreplication](../../relational-databases/replication/codesnippet/tsql/sp-removedbreplication-t_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_removedbreplication**します。  
  
## <a name="example"></a>例  
  
```  
-- Remove replication objects from the subscription database on MYSUB.  
DECLARE @subscriptionDB AS sysname  
SET @subscriptionDB = N'AdventureWorksReplica'  
  
-- Remove replication objects from a subscription database (if necessary).  
USE master  
EXEC sp_removedbreplication @subscriptionDB  
GO  
  
```  
  
## <a name="see-also"></a>参照  
 [パブリッシングおよびディストリビューションの無効化](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
