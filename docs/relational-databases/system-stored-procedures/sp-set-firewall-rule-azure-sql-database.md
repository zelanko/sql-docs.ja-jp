---
title: "sp_set_firewall_rule (Azure SQL データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/28/2016
ms.prod: 
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: 
ms.service: sql-database
ms.component: system-stored-procedures
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 38ef5788aba91bfde21df091321a69dbacbeb8e9
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spsetfirewallrule-azure-sql-database"></a>sp_set_firewall_rule (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  作成するか、サーバー レベルのファイアウォール設定を更新、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]サーバー。 このストアド プロシージャは、サーバー レベル プリンシパル ログインまたは割り当てられている Azure Active Directory のプリンシパルに、master データベースにできるだけです。  
  
  
## <a name="syntax"></a>構文  
  
```
sp_set_firewall_rule [@name =] 'name', 
    [@start_ip_address =] 'start_ip_address', 
    [@end_ip_address =] 'end_ip_address'
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 次の表は、サポートされている引数を示していて、オプション[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
|名前|データ型|Description|  
|----------|--------------|-----------------|  
|[@name =] 'name'|**NVARCHAR (128)**|サーバー レベルのファイアウォール設定を説明し、区別するために使用される名前。|  
|[@start_ip_address =] 'start_ip_address'|**VARCHAR (50)**|サーバー レベルのファイアウォール設定の範囲において最も小さい IP アドレス。 IP アドレスと等しいかそれ以上を指定するとこれに接続しようとしてできます、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]サーバー。 最下位の IP アドレスは`0.0.0.0`します。|  
|[@end_ip_address =] 'end_ip_address'|**VARCHAR (50)**|サーバー レベルのファイアウォール設定の範囲において最も大きい IP アドレス。 これ以下の IP アドレスは、[!INCLUDE[ssSDS](../../includes/sssds-md.md)] サーバーへの接続を試みることができます。 最上位の IP アドレスは`255.255.255.255`します。<br /><br /> 注: Azure の接続試行ときに許可されますこの両方のフィールドと*start_ip_address* equals をフィールド`0.0.0.0`です。|  
  
## <a name="remarks"></a>解説  
 サーバー レベルのファイアウォール設定の名前は一意である必要があります。 ストアド プロシージャに提供される設定の名前がファイアウォール設定のテーブルに既に存在する場合は、開始 IP アドレスと終了 IP アドレスが更新されます。 そうでない場合は、新しいサーバー レベルのファイアウォール設定が作成されます。  
  
 最初と最後の IP アドレスに等しいサーバー レベルのファイアウォール設定を追加するときに`0.0.0.0`へのアクセスを有効にする、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Azure からのサーバー。 値を指定、*名前*を支援するパラメーターには、サーバー レベルのファイアウォール設定に注意してください。  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]接続の認証に必要なログイン データ、およびサーバー レベルのファイアウォール ルールは、各データベースでは一時的にキャッシュします。 このキャッシュは定期的に更新されます。 認証キャッシュの更新を強制し、データベースのログインの表に、最新バージョンがあることを確認、実行[DBCC FLUSHAUTHCACHE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 サーバー レベル プリンシパル ログインのみプロビジョニング処理で作成または管理者が作成または、サーバー レベルのファイアウォール ルールを変更できるように割り当てられている Azure Active Directory プリンシパル。 ユーザーは、sp_set_firewall_rule を実行するマスター データベースに接続する必要があります。  
  
## <a name="examples"></a>使用例  
 次のコードは、サーバー レベルのファイアウォール設定と呼ばれる`Allow Azure`Azure からのアクセスを有効にします。 仮想 master データベースで、次を実行します。  
  
```  
-- Enable Windows Azure connections.  
exec sp_set_firewall_rule N'Allow Azure', '0.0.0.0', '0.0.0.0';  
  
```  
  
 次のコードは、サーバー レベルのファイアウォール設定と呼ばれる`Example setting 1`の IP アドレスのみ`0.0.0.2`です。 次に、 `sp_set_firewall_rule` 、終了 IP アドレスを更新するストアド プロシージャが再度呼び出される`0.0.0.4`点で、ファイアウォールの設定。 これにより、IP アドレス範囲が作成`0.0.0.2`、 `0.0.0.3`、および`0.0.0.4`サーバーにアクセスします。  
  
```  
-- Create server-level firewall setting for only IP 0.0.0.2  
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.2';  
  
-- Update server-level firewall setting to create a range of allowed IP addresses
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.4';  
  
```  
  
## <a name="see-also"></a>参照  
 [Azure SQL データベース ファイアウォール](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [方法: ファイアウォールの設定 (Azure SQL データベース) を構成します。](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sys.firewall_rules &#40;です。Azure SQL データベース &#41;](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md)
