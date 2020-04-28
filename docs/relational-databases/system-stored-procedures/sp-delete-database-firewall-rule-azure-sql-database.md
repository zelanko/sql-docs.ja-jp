---
title: sp_delete_database_firewall_rule (Azure SQL Database) |Microsoft Docs
ms.custom: ''
ms.date: 08/04/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sp_delete_database_firewall_rule
- sp_delete_database_firewall_rule_TSQL
- sys.sp_delete_database_firewall_rule
- sys.sp_delete_database_firewall_rule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_database_firewall_rule procedure
ms.assetid: ed295312-e586-4fc2-9e80-806b490ee7bd
author: VanMSFT
ms.author: vanto
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 660405e7e7592557422e43655c35ec27c194aad3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68130678"
---
# <a name="sp_delete_database_firewall_rule-azure-sql-database"></a>sp_delete_database_firewall_rule (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  データベースレベルのファイアウォール設定をから[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]削除します。 データベースファイアウォール規則は、master データベース、およびのユーザーデータベースに対して構成および[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]削除できます。   
  
 
## <a name="syntax"></a>構文  
  
```    
sp_delete_database_firewall_rule [@name =] [N]'name'
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 `[@name =] [N]'name'`  
 削除されるデータベースレベルのファイアウォール設定の名前。 *名前*は**nvarchar (128)** で、既定値はありません。 Unicode 識別子`N`は、で[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]は省略可能です。 
  
## <a name="permissions"></a>アクセス許可  
 データベースレベルのファイアウォールルールを削除できるのは、プロビジョニング処理で作成されたサーバーレベルのプリンシパルログイン、または管理者として割り当てられた Azure Active Directory プリンシパルだけです。  
  
## <a name="example"></a>例  
 次の例では、という名前`Example DB Setting 1`のデータベースレベルのファイアウォール設定を削除します。
  
```  
-- Remove database-level firewall setting  
EXECUTE sp_delete_database_firewall_rule N'Example DB Setting 1';  
  
```  
  
## <a name="see-also"></a>参照  
 [Azure SQL Database ファイアウォール](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [方法: ファイアウォール設定を構成する (Azure SQL Database)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sp_set_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sp_set_database_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)   
 [database_firewall_rules &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
  
  


