---
title: sp_set_database_firewall_rule (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 08/04/2017
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sp_set_database_firewall_rule
- sp_set_database_firewall_rule_TSQL
- sys.sp_set_database_firewall_rule
- sys.sp_set_database_firewall_rule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_set_database_firewall_rule
- firewall_rules, setting database rules
ms.assetid: 8f0506b6-a4ac-4e4d-91db-8077c40cb17a
author: VanMSFT
ms.author: vanto
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: e5363e741c827a0fb16528a8b617e26a5b95f8a9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68025691"
---
# <a name="spsetdatabasefirewallrule-azure-sql-database"></a>sp_set_database_firewall_rule (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  作成または更新のデータベース レベルのファイアウォール規則、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]します。 データベースのファイアウォール規則を構成することができます、**マスター**データベース、およびユーザー データベースで[!INCLUDE[ssSDS](../../includes/sssds-md.md)]します。 データベース ファイアウォール規則は、包含データベース ユーザーを使用するときに特に便利です。 詳細については、「 [包含データベース ユーザー - データベースの可搬性を確保する](../../relational-databases/security/contained-database-users-making-your-database-portable.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_set_database_firewall_rule [@name = ] [N]'name'  
, [@start_ip_address =] 'start_ip_address'  
, [@end_ip_address =] 'end_ip_address'
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 **[@name**  =] [N]'*名前*'  
 データベース レベルのファイアウォール設定を説明し、区別するために使用される名前。 *名前*は**nvarchar (128)** で既定値はありません。 Unicode 識別子`N`は省略可能です[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]します。 
  
 **[@start_ip_address**  =] '*start_ip_address*'  
 データベース レベルのファイアウォール設定の範囲の最下位の IP アドレス。 これ以上の IP アドレスは、[!INCLUDE[ssSDS](../../includes/sssds-md.md)] インスタンスへの接続を試みることができます。 最下位の IP アドレスは`0.0.0.0`します。 *start_ip_address*は**varchar (50)** で既定値はありません。  
  
 [ **@end_ip_address** =] '*end_ip_address*'  
 データベース レベルのファイアウォール設定の範囲の最上位の IP アドレス。 IP アドレス以下への接続にこれを試みる、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]インスタンス。 最上位の IP アドレスは`255.255.255.255`します。 *end_ip_address*は**varchar (50)** で既定値はありません。  
  
 次の表は、サポートされている引数を示していて、オプション[!INCLUDE[ssSDS](../../includes/sssds-md.md)]します。  
  
> [!NOTE]  
>  Azure の接続試行が許可されますこの両方のフィールドと*start_ip_address* equals をフィールド`0.0.0.0`します。  
  
## <a name="remarks"></a>コメント  
 データベースのデータベース レベルのファイアウォール設定の名前は一意である必要があります。 ストアド プロシージャに提供されるデータベース レベルのファイアウォール設定の名前がデータベース レベルのファイアウォール設定のテーブルに既に存在する場合は、開始 IP アドレスと終了 IP アドレスが更新されます。 それ以外の場合は新しいデータベース レベルのファイアウォール設定が作成されます。  
  
 開始と終了 IP アドレスと等しいデータベース レベルのファイアウォール設定を追加すると`0.0.0.0`、内のデータベースにアクセスを有効にする、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]任意の Azure リソースからのサーバー。 値を指定、*名前*パラメーターするのに役立つは、ファイアウォール設定に注意してください。  
  
## <a name="permissions"></a>アクセス許可  
 データベースに対する **CONTROL** 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次のコード作成、データベース レベルのファイアウォール設定と呼ばれる`Allow Azure`Azure からデータベースにアクセスできるようにします。  
  
```  
-- Enable Azure connections.  
EXECUTE sp_set_database_firewall_rule N'Allow Azure', '0.0.0.0', '0.0.0.0';  
  
```  
  
 次のコード作成、データベース レベルのファイアウォール設定と呼ばれる`Example DB Setting 1`の IP アドレスのみ`0.0.0.4`します。 次に、`sp_set_database firewall_rule`に終了 IP アドレスを更新するストアド プロシージャが再度呼び出される`0.0.0.6`点で、ファイアウォールの設定。 により、IP アドレス範囲が作成されます`0.0.0.4`、 `0.0.0.5`、および`0.0.0.6`データベースにアクセスします。
  
```  
-- Create database-level firewall setting for only IP 0.0.0.4  
EXECUTE sp_set_database_firewall_rule N'Example DB Setting 1', '0.0.0.4', '0.0.0.4';  
  
-- Update database-level firewall setting to create a range of allowed IP addresses
EXECUTE sp_set_database_firewall_rule N'Example DB Setting 1', '0.0.0.4', '0.0.0.6';  
  
```  
  
## <a name="see-also"></a>関連項目  
 [Azure SQL Database ファイアウォール](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [方法:ファイアウォールの設定 (Azure SQL データベース) を構成します。](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sp_set_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sp_delete_database_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)   
 [sys.database_firewall_rules &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
  
  
