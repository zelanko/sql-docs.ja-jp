---
title: sys.database_firewall_rules (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.database_firewall_rules_TSQL
- database_firewall_rules_TSQL
- sys.database_firewall_rules
- database_firewall_rules
dev_langs:
- TSQL
helpviewer_keywords:
- database_firewall_rules
- sys.database_firewall_rules
ms.assetid: 2e821593-3b9f-43d6-a99b-1ceffe177faf
author: VanMSFT
ms.author: vanto
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 1681c3b245da5d1abded678d54b2b7694598077b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915023"
---
# <a name="sysdatabasefirewallrules-azure-sql-database"></a>sys.database_firewall_rules (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  関連付けられたデータベース レベルのファイアウォール設定に関する情報を返します、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]します。 データベース レベルのファイアウォール設定は、包含データベース ユーザーを使用する場合に特に便利です。 詳細については、「 [包含データベース ユーザー - データベースの可搬性を確保する](../../relational-databases/security/contained-database-users-making-your-database-portable.md)」を参照してください。  
  
 `sys.database_firewall_rules`ビューには、次の列が含まれています。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|id|**INTEGER**|データベース レベルのファイアウォール設定の識別子。|  
|NAME|**NVARCHAR (128)**|データベース レベルのファイアウォール設定を説明し、区別するために選択した名前。|  
|start_ip_address|**VARCHAR(45)**|データベース レベルのファイアウォール設定の範囲の最下位の IP アドレス。 これ以上の IP アドレスは、[!INCLUDE[ssSDS](../../includes/sssds-md.md)] インスタンスへの接続を試みることができます。 最下位の IP アドレスは`0.0.0.0`します。|  
|end_ip_address|**VARCHAR(45)**|ファイアウォール設定の範囲の最上位の IP アドレス。 IP アドレス以下への接続にこれを試みる、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]インスタンス。 最上位の IP アドレスは`255.255.255.255`します。<br /><br /> 注:Windows Azure の接続試行が許可されますこの両方のフィールドと**start_ip_address** equals をフィールド`0.0.0.0`します。|  
|create_date|**DATETIME**|データベース レベルのファイアウォール設定が作成された UTC 日時。|  
|modify_date|**DATETIME**|データベース レベルのファイアウォール設定が最後に変更された UTC 日時。|  
  
## <a name="remarks"></a>コメント  
 使用して、Microsoft Azure SQL Database に関連付けられたサーバー レベルのファイアウォール設定に関する情報を返す[sys.firewall_rules (Azure SQL データベース)](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md)します。  
  
## <a name="permissions"></a>アクセス許可  
 このビューで使用できる、**マスター**データベースと、各ユーザー データベース。 このビューに読み取り専用のアクセスは、データベースに接続するアクセス許可を持つすべてのユーザーに使用できます。  
  
## <a name="see-also"></a>関連項目
[sp_set_database_firewall_rule &#40;Azure SQL データベース&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)  
[sp_delete_database_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)  
[sp_set_firewall_rule &#40;Azure SQL データベース&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)  
[sp_delete_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-delete-firewall-rule-azure-sql-database.md)   
[sys.firewall_rules &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md)  
[データベース エンジン アクセス用の Windows ファイアウォールを構成します。](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)     
[FILESTREAM アクセスのためのファイアウォールの構成](../../relational-databases/blob/configure-a-firewall-for-filestream-access.md)  
[レポート サーバー アクセスに対するファイアウォールの構成](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)  
