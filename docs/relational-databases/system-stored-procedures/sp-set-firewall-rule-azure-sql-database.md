---
title: sp_set_firewall_rule (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 07/28/2016
ms.prod: ''
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: ''
ms.service: sql-database
ms.component: system-stored-procedures
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_set_firewall_rule
- sp_set_firewall_rule_TSQL
- sys.sp_set_firewall_rule
- sys.sp_set_firewall_rule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_set_firewall_rule
- firewall_rules, setting server rules
ms.assetid: a974a561-5382-4039-8499-3a56767bcefe
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 190369a7e5d202f826197d69f09425a7a6763e21
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43026811"
---
# <a name="spsetfirewallrule-azure-sql-database"></a>sp_set_firewall_rule (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  作成または更新のサーバー レベルのファイアウォール設定、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]サーバー。 このストアド プロシージャは、サーバー レベル プリンシパル ログインまたは割り当てられている Azure Active Directory のプリンシパルに master データベースにできるだけです。  
  
  
## <a name="syntax"></a>構文  
  
```
sp_set_firewall_rule [@name =] 'name', 
    [@start_ip_address =] 'start_ip_address', 
    [@end_ip_address =] 'end_ip_address'
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 次の表は、サポートされている引数を示していて、オプション[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]します。  
  
|名前|データ型|説明|  
|----------|--------------|-----------------|  
|[@name =] 'name'|**NVARCHAR (128)**|サーバー レベルのファイアウォール設定を説明し、区別するために使用される名前。|  
|[@start_ip_address =] 'start_ip_address'|**VARCHAR (50)**|サーバー レベルのファイアウォール設定の範囲において最も小さい IP アドレス。 IP アドレスと等しいかそれへの接続にこれを試みるよりも大きい、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]サーバー。 最下位の IP アドレスは`0.0.0.0`します。|  
|[@end_ip_address =] 'end_ip_address'|**VARCHAR (50)**|サーバー レベルのファイアウォール設定の範囲において最も大きい IP アドレス。 これ以下の IP アドレスは、[!INCLUDE[ssSDS](../../includes/sssds-md.md)] サーバーへの接続を試みることができます。 最上位の IP アドレスは`255.255.255.255`します。<br /><br /> 注: Azure の接続試行が許可されますこの両方のフィールドと*start_ip_address* equals をフィールド`0.0.0.0`します。|  
  
## <a name="remarks"></a>コメント  
 サーバー レベルのファイアウォール設定の名前は一意である必要があります。 ストアド プロシージャに提供される設定の名前がファイアウォール設定のテーブルに既に存在する場合は、開始 IP アドレスと終了 IP アドレスが更新されます。 そうでない場合は、新しいサーバー レベルのファイアウォール設定が作成されます。  
  
 開始と終了 IP アドレスと等しいサーバー レベルのファイアウォール設定を追加すると`0.0.0.0`へのアクセスを有効にすると、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Azure からのサーバー。 値を指定、*名前*パラメーターするのに役立つは、サーバー レベルのファイアウォール設定に注意してください。  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] では、接続の認証に必要なログイン データおよびサーバー レベルのファイアウォール規則は、各データベースで一時的にキャッシュされます。 このキャッシュは定期的に更新されます。 認証キャッシュを強制的に更新し、データベースにログイン テーブルの最新バージョンがあることを確認するには、[DBCC FLUSHAUTHCACHE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md) を実行します。  
  
## <a name="permissions"></a>アクセス許可  
 サーバー レベル プリンシパル ログインだけ準備プロセスによって作成または管理者が作成またはサーバー レベルのファイアウォール規則を変更するように割り当てられている、Azure Active Directory のプリンシパル。 ユーザーは、sp_set_firewall_rule を実行する master データベースに接続する必要があります。  
  
## <a name="examples"></a>使用例  
 次のコード作成、サーバー レベルのファイアウォール設定と呼ばれる`Allow Azure`Azure からアクセスできるようにします。 仮想 master データベースでは、次を実行します。  
  
```  
-- Enable Windows Azure connections.  
exec sp_set_firewall_rule N'Allow Azure', '0.0.0.0', '0.0.0.0';  
  
```  
  
 次のコード作成、サーバー レベルのファイアウォール設定と呼ばれる`Example setting 1`の IP アドレスのみ`0.0.0.2`します。 次に、`sp_set_firewall_rule`に終了 IP アドレスを更新するストアド プロシージャが再度呼び出される`0.0.0.4`点で、ファイアウォールの設定。 これにより、IP アドレス範囲を作成します`0.0.0.2`、 `0.0.0.3`、および`0.0.0.4`サーバーへのアクセスします。  
  
```  
-- Create server-level firewall setting for only IP 0.0.0.2  
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.2';  
  
-- Update server-level firewall setting to create a range of allowed IP addresses
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.4';  
  
```  
  
## <a name="see-also"></a>参照  
 [Azure SQL Database ファイアウォール](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [方法: ファイアウォールの設定 (Azure SQL データベース) を構成します。](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sys.firewall_rules &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md)
