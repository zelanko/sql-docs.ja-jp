---
title: sys.firewall_rules (Azure SQL データベース) |Microsoft Docs
ms.date: 03/26/2019
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.firewall_rules
- firewall_rules
- sys.firewall_rules_TSQL
- firewall_rules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- firewall_rules
- sys.firewall_rules
ms.assetid: 140d2cd8-9aa1-4cc5-870d-e1dbc873b3fe
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 2be0d498da026f386c3a89002cca621b19a2a15d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68133989"
---
# <a name="sysfirewallrules-azure-sql-database"></a>sys.firewall_rules (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  関連付けられたサーバー レベルのファイアウォール設定に関する情報を返します、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]します。  
  
 `sys.firewall_rules`ビューには、次の列が含まれています。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|id|**INT**|サーバー レベルのファイアウォール設定の識別子。|  
|NAME|**NVARCHAR (128)**|説明し、区別、サーバー レベルのファイアウォール設定を選択した名前。|  
|start_ip_address|**VARCHAR(45)**|サーバー レベルのファイアウォール設定の範囲の最下位の IP アドレス。 IP アドレスと等しいかそれへの接続にこれを試みるよりも大きい、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]サーバー。 最下位の IP アドレスは`0.0.0.0`します。|  
|end_ip_address|**VARCHAR(45)**|サーバー レベルのファイアウォール設定の範囲の最上位の IP アドレス。 これ以下の IP アドレスは、[!INCLUDE[ssSDS](../../includes/sssds-md.md)] サーバーへの接続を試みることができます。 最上位の IP アドレスは`255.255.255.255`します。<br /><br /> 注:Windows Azure の接続試行が許可されますこの両方のフィールドと**start_ip_address** equals をフィールド`0.0.0.0`します。|  
|create_date|**DATETIME**|UTC の日付と時刻のサーバー レベルのファイアウォール設定が作成された日時。<br /><br /> 注:UTC は、世界協定時刻の頭字語です。|  
|modify_date|**DATETIME**|UTC の日付と時刻の最後に、サーバー レベルのファイアウォール設定が変更されました。|  
  
## <a name="remarks"></a>コメント

 Microsoft Azure SQL Database、使用に関連するデータベース レベルのファイアウォール設定に関する情報を返します[sys.database_firewall_rules &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)します。  
  
## <a name="permissions"></a>アクセス許可

 このビューに読み取り専用のアクセスに接続する権限を持つすべてのユーザーには、**マスター**データベース。  
  
## <a name="see-also"></a>関連項目

[sp_set_firewall_rule &#40;Azure SQL データベース&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)  
[sp_delete_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-delete-firewall-rule-azure-sql-database.md)   
[sp_set_database_firewall_rule &#40;Azure SQL データベース&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)  
[sp_delete_database_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)  
[sys.database_firewall_rules &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
[データベース エンジン アクセス用の Windows ファイアウォールを構成します。](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)     
[FILESTREAM アクセスのためのファイアウォールの構成](../../relational-databases/blob/configure-a-firewall-for-filestream-access.md)  
[レポート サーバー アクセスに対するファイアウォールの構成](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md) 
