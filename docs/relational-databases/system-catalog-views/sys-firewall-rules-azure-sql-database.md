---
title: sys.firewall_rules (Azure SQL データベース) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 090ec967e25fff1fac3761298214e0366c0f2478
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysfirewallrules-azure-sql-database"></a>sys.firewall_rules (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  関連付けられたサーバー レベルのファイアウォール設定に関する情報を返します、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 `sys.firewall_rules`ビューには、次の列が含まれています。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|id|**INT**|サーバー レベルのファイアウォール設定の識別子。|  
|name|**NVARCHAR (128)**|サーバー レベルのファイアウォール設定を説明し、区別するために選択した名前。|  
|start_ip_address|**VARCHAR (50)**|サーバー レベルのファイアウォール設定の範囲において最も小さい IP アドレス。 IP アドレスと等しいかそれ以上を指定するとこれに接続しようとしてできます、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]サーバー。 最下位の IP アドレスは`0.0.0.0`します。|  
|end_ip_address|**VARCHAR (50)**|サーバー レベルのファイアウォール設定の範囲において最も大きい IP アドレス。 これ以下の IP アドレスは、[!INCLUDE[ssSDS](../../includes/sssds-md.md)] サーバーへの接続を試みることができます。 最上位の IP アドレスは`255.255.255.255`します。<br /><br /> 注: Windows Azure の接続試行ときに許可されますこの両方のフィールドと**start_ip_address** equals をフィールド`0.0.0.0`です。|  
|create_date|**DATETIME**|サーバー レベルのファイアウォール設定が作成された UTC 日時。<br /><br /> メモ: UTC は、世界協定時刻の頭字語です。|  
|modify_date|**DATETIME**|サーバー レベルのファイアウォール設定が最後に変更された UTC 日時。|  
  
## <a name="remarks"></a>解説  
 データベースのファイアウォール ルールを削除する使用[sp_delete_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-delete-firewall-rule-azure-sql-database.md)です。 1 つのデータベース用のファイアウォール ルールを設定するを参照してください。 [sys.database_firewall_rules &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)です。 既存のファイアウォール規則の情報を返すには、するには、sys.firewall_rules (Azure SQL データベース) をクエリします。  
  
## <a name="permissions"></a>権限  
 このビューに読み取り専用のアクセスに接続する権限を持つすべてのユーザーには、**マスター**データベース。  
  
## <a name="see-also"></a>参照  
 [sys.database_firewall_rules &#40;Azure SQL データベース&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)   
 [sp_set_firewall_rule &#40;Azure SQL データベース&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [データベース エンジン アクセスの Windows ファイアウォールを構成します。](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)   
 [Configure a Firewall for FILESTREAM アクセス](../../relational-databases/blob/configure-a-firewall-for-filestream-access.md)   
 [レポート サーバー アクセスに対するファイアウォールの構成](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)   
 [方法: ファイアウォールの設定 (Azure SQL データベース) を構成します。](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)  
  
  
