---
title: "DROP LOGIN (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP LOGIN
- DROP_LOGIN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting login accounts
- logins [SQL Server], removing
- DROP LOGIN statement
- removing login accounts
- dropping login accounts
ms.assetid: acb5c3dc-7aa2-49f6-9330-573227ba9b1a
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c8c13d7800893b860b1bcaf3f631f01f190a2715
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-login-transact-sql"></a>DROP LOGIN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン アカウントを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DROP LOGIN login_name  
```  
  
## <a name="arguments"></a>引数  
 *login_name*  
 削除するログインの名前を指定します。  
  
## <a name="remarks"></a>解説  
 ログイン中のログインは削除できません。 セキュリティ保護可能なリソース、サーバー レベル オブジェクト、または SQL Server エージェント ジョブを所有するログインは削除できません。  
  
 データベース ユーザーがマップされているログインは削除できますが、その場合孤立したユーザーが残ります。 詳細については、「[孤立ユーザーのトラブルシューティング &#40;SQL Server&#41;](../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md)」を参照してください。  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]接続の認証に必要なログイン データ、およびサーバー レベルのファイアウォール ルールは、各データベースでは一時的にキャッシュします。 このキャッシュは定期的に更新されます。 認証キャッシュの更新を強制し、データベースのログインの表に、最新バージョンがあることを確認、実行[DBCC FLUSHAUTHCACHE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 サーバーに対する ALTER ANY LOGIN 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-dropping-a-login"></a>A. ログインを削除します。  
 次の例は、ログインを削除`WilliJo`です。  
  
```  
DROP LOGIN WilliJo;  
GO 
```  
 
  
## <a name="see-also"></a>参照  
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  


