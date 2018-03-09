---
title: "sys.firewall_rules (Azure SQL データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7f06eef87553a1a97851a3252faaf0f8057158c2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysfirewallrules-azure-sql-database"></a>sys.firewall_rules (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  関連付けられたサーバー レベルのファイアウォール設定に関する情報を返します、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 `sys.firewall_rules`ビューには、次の列が含まれています。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|id|**INT**|サーバー レベルのファイアウォール設定の識別子。|  
|name|**NVARCHAR (128)**|サーバー レベルのファイアウォール設定を説明し、区別するために選択した名前。|  
|start_ip_address|**VARCHAR (50)**|サーバー レベルのファイアウォール設定の範囲において最も小さい IP アドレス。 IP アドレスと等しいかそれ以上を指定するとこれに接続しようとしてできます、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]サーバー。 最下位の IP アドレスは`0.0.0.0`します。|  
|end_ip_address|**VARCHAR (50)**|サーバー レベルのファイアウォール設定の範囲において最も大きい IP アドレス。 これ以下の IP アドレスは、[!INCLUDE[ssSDS](../../includes/sssds-md.md)] サーバーへの接続を試みることができます。 最上位の IP アドレスは`255.255.255.255`します。<br /><br /> 注: Windows Azure の接続試行ときに許可されますこの両方のフィールドと**start_ip_address** equals をフィールド`0.0.0.0`です。|  
|create_date|**DATETIME**|サーバー レベルのファイアウォール設定が作成された UTC 日時。<br /><br /> メモ: UTC は、世界協定時刻の頭字語です。|  
|modify_date|**DATETIME**|サーバー レベルのファイアウォール設定が最後に変更された UTC 日時。|  
  
## <a name="remarks"></a>解説  
 データベースのファイアウォール ルールを削除する使用[sp_delete_firewall_rule (& a) #40 です。Azure SQL データベース &#41;](../../relational-databases/system-stored-procedures/sp-delete-firewall-rule-azure-sql-database.md). 1 つのデータベース用のファイアウォール ルールを設定するを参照してください。 [sys.database_firewall_rules &#40;です。Azure SQL データベース &#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md). 既存のファイアウォール規則の情報を返すには、するには、sys.firewall_rules (Azure SQL データベース) をクエリします。  
  
## <a name="permissions"></a>Permissions  
 このビューに読み取り専用のアクセスに接続する権限を持つすべてのユーザーには、**マスター**データベース。  
  
## <a name="see-also"></a>参照  
 [sys.database_firewall_rules &#40;です。Azure SQL データベース &#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)   
 [sp_set_firewall_rule &#40;です。Azure SQL データベース &#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [データベース エンジン アクセスの Windows ファイアウォールを構成します。](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)   
 [Configure a Firewall for FILESTREAM アクセス](../../relational-databases/blob/configure-a-firewall-for-filestream-access.md)   
 [レポート サーバー アクセスに対してファイアウォールを構成します。](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)   
 [方法: ファイアウォールの設定 (Azure SQL データベース) を構成します。](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)  
  
  
