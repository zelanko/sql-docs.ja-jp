---
title: "sp_delete_firewall_rule (Azure SQL データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/27/2016
ms.prod: 
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: 
ms.service: sql-database
ms.component: system-stored-procedures
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_delete_firewall_rule_TSQL
- sp_delete_firewall_rule
- sys.sp_delete_firewall_rule
- sys.sp_delete_firewall_rule_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_delete_firewall_rule procedure
ms.assetid: cf93eed1-ba97-4850-9fcc-b9c5a9317908
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: aa2815c27668bc680ce5da72b6713e29b517f43b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spdeletefirewallrule-azure-sql-database"></a>sp_delete_firewall_rule (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  [!INCLUDE[ssSDS](../../includes/sssds-md.md)] サーバーからサーバー レベルのファイアウォール設定を削除します。 このストアド プロシージャは、サーバー レベルのプリンシパルのログインのみが master データベースのみで使用できます。  

  
## <a name="syntax"></a>構文  
  
```  
sp_delete_firewall_rule [@name =] 'name' 
[ ; ] 
```  
  
## <a name="arguments"></a>引数  
 ストアド プロシージャの引数は次のとおりです。  
  
 [@name =] '*名前*'  
 削除するサーバー レベルのファイアウォール設定の名前。 *名前*は**nvarchar (128)**既定値はありません。  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]接続の認証に必要なログイン データ、およびサーバー レベルのファイアウォール ルールは、各データベースでは一時的にキャッシュします。 このキャッシュは定期的に更新されます。 認証キャッシュの更新を強制し、データベースのログインの表に、最新バージョンがあることを確認、実行[DBCC FLUSHAUTHCACHE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 サーバー レベルのファイアウォール ルールを削除できるのは、準備プロセスによって作成されるサーバー レベルのプリンシパルのログインだけです。 ユーザーは、sp_delete_firewall_rule を実行するマスター データベースに接続する必要があります。  
  
## <a name="example"></a>例  
 次の例は、'Example setting 1' という名前のサーバー レベルのファイアウォール設定を削除します。 仮想 master データベースでステートメントを実行します。  
  
```   
EXEC sp_delete_firewall_rule N'Example setting 1';   
```  
  
## <a name="see-also"></a>参照  
 [Azure SQL データベース ファイアウォール](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [方法: ファイアウォールの設定 (Azure SQL データベース) を構成します。](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sp_set_firewall_rule &#40;です。Azure SQL データベース &#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sys.firewall_rules &#40;です。Azure SQL データベース &#41;](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md)  
  
  


