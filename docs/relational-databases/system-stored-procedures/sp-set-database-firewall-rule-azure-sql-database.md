---
title: sp_set_database_firewall_rule
titleSuffix: Azure SQL Database
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
ms.custom: seo-dt-2019
ms.openlocfilehash: dfe41ee68412414df24bc7f0bd583bbb0109b3db
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "74055088"
---
# <a name="sp_set_database_firewall_rule-azure-sql-database"></a>sp_set_database_firewall_rule (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  のデータベースレベルのファイアウォール規則を作成または[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]更新します。 データベースファイアウォール規則は、 **master**データベース、およびのユーザーデータベース用に構成[!INCLUDE[ssSDS](../../includes/sssds-md.md)]できます。 データベースファイアウォールルールは、包含データベースユーザーを使用する場合に特に便利です。 詳細については、「 [包含データベース ユーザー - データベースの可搬性を確保する](../../relational-databases/security/contained-database-users-making-your-database-portable.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_set_database_firewall_rule [@name = ] [N]'name'  
, [@start_ip_address =] 'start_ip_address'  
, [@end_ip_address =] 'end_ip_address'
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
`[ @name = ] [N]'name'`データベースレベルのファイアウォール設定を記述および区別するために使用される名前。 *名前*は**nvarchar (128)** で、既定値はありません。 Unicode 識別子`N`は、で[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]は省略可能です。 
  
`[ @start_ip_address = ] 'start_ip_address'`データベースレベルのファイアウォール設定の範囲の最小の IP アドレス。 これ以上の IP アドレスは、[!INCLUDE[ssSDS](../../includes/sssds-md.md)] インスタンスへの接続を試みることができます。 設定できる最下位の IP アドレスは `0.0.0.0` です。 *start_ip_address*は**varchar (50)** で、既定値はありません。  
  
`[ @end_ip_address = ] 'end_ip_address'`データベースレベルのファイアウォール設定の範囲の最上位の IP アドレス。 この IP アドレス以下の IP アドレスは、[!INCLUDE[ssSDS](../../includes/sssds-md.md)] インスタンスへの接続を試行できます。 設定できる最上位の IP アドレスは `255.255.255.255` です。 *end_ip_address*は**varchar (50)** で、既定値はありません。  
  
 次の表は、で[!INCLUDE[ssSDS](../../includes/sssds-md.md)]サポートされている引数とオプションを示しています。  
  
> [!NOTE]  
>  Azure の接続試行は、このフィールドと*start_ip_address*フィールドの両方が`0.0.0.0`と等しい場合に許可されます。  
  
## <a name="remarks"></a>解説  
 データベースに対するデータベースレベルのファイアウォール設定の名前は一意である必要があります。 ストアド プロシージャに提供されるデータベース レベルのファイアウォール設定の名前がデータベース レベルのファイアウォール設定のテーブルに既に存在する場合は、開始 IP アドレスと終了 IP アドレスが更新されます。 それ以外の場合、新しいデータベースレベルのファイアウォール設定が作成されます。  
  
 開始 IP アドレスと終了 IP アドレスがに`0.0.0.0`等しいデータベースレベルのファイアウォール設定を追加すると、任意の Azure リソースから[!INCLUDE[ssSDS](../../includes/sssds-md.md)]サーバー内のデータベースにアクセスできるようになります。 *名前*パラメーターに値を指定すると、ファイアウォール設定の内容を覚えやすくなります。  
  
## <a name="permissions"></a>アクセス許可  
 データベースに対する**CONTROL**権限が必要です。  
  
## <a name="examples"></a>例  
 次のコードでは、Azure からデータベースへのアクセスを有効にする、`Allow Azure` という名前のデータベースレベルのファイアウォール設定を作成します。  
  
```  
-- Enable Azure connections.  
EXECUTE sp_set_database_firewall_rule N'Allow Azure', '0.0.0.0', '0.0.0.0';  
  
```  
  
 次のコードでは、IP アドレス `Example DB Setting 1` だけを許可する、`0.0.0.4` という名前のデータベースレベルのファイアウォールの設定を作成します。 次に、 `sp_set_database firewall_rule`そのファイアウォール設定で、終了 IP アドレスをに`0.0.0.6`更新するために、ストアドプロシージャが再度呼び出されます。 これにより、IP アドレス`0.0.0.4`、 `0.0.0.5`、およびを使用`0.0.0.6`してデータベースにアクセスできる範囲が作成されます。
  
```  
-- Create database-level firewall setting for only IP 0.0.0.4  
EXECUTE sp_set_database_firewall_rule N'Example DB Setting 1', '0.0.0.4', '0.0.0.4';  
  
-- Update database-level firewall setting to create a range of allowed IP addresses
EXECUTE sp_set_database_firewall_rule N'Example DB Setting 1', '0.0.0.4', '0.0.0.6';  
  
```  
  
## <a name="see-also"></a>参照  
 [Azure SQL Database ファイアウォール](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [方法: ファイアウォール設定を構成する (Azure SQL Database)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sp_set_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sp_delete_database_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)   
 [database_firewall_rules &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
  
  
