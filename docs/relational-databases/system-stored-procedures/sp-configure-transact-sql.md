---
title: "sp_configure (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_configure
- sp_configure_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_configure
ms.assetid: d18b251d-b37a-4f5f-b50c-502d689594c8
caps.latest.revision: "60"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: d6ff78066f307e70f37880eb57e2430774c242ae
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spconfigure-transact-sql"></a>sp_configure (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  現在のサーバーのグローバル構成設定を表示または変更します。  
  
> [!NOTE]  
>  データベース レベルの構成オプションについては、次を参照してください。 [ALTER DATABASE SCOPED CONFIGURATION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md). ソフト NUMA を構成するのを参照してください。[ソフト NUMA &#40;です。SQL Server &#41;](../../database-engine/configure-windows/soft-numa-sql-server.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server  
  
sp_configure [ [ @configname = ] 'option_name'   
    [ , [ @configvalue = ] 'value' ] ]  
```  
  
```  
-- Syntax for Parallel Data Warehouse  
  
-- List all of the configuration options  
sp_configure  
[;]  
  
-- Configure Hadoop connectivity  
sp_configure [ @configname= ] 'hadoop connectivity',  
             [ @configvalue = ] { 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 }  
[;]  
RECONFIGURE  
[;]  
```  
  
## <a name="arguments"></a>引数  
 [ **@configname=** ] **'***option_name***'**  
 構成オプションの名前を指定します。 *option_name* は **varchar(35)**、既定値は NULL です。 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]構成の名前に含まれている一意の文字列を認識します。 指定しない場合、オプションの完全な一覧が返されます。  
  
 利用可能な構成オプションとその設定については、次を参照してください。[サーバー構成オプション &#40;です。SQL Server &#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
 [ **@configvalue=** ] **'***value***'**  
 新しい構成設定を指定します。 *value* のデータ型は **int**で、既定値は NULL です。 最大値はオプションごとに異なります。  
  
 各オプションの最大値を参照してください、**最大**の列、 **sys.configurations**カタログ ビューです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 パラメーターなしで実行されたときに**sp_configure** 5 つの列を含む結果セットを返すし、次の表に示すようにアルファベット順に昇順でオプションを注文します。  
  
 値は、 **config_value**と**run_value**自動的に同じではありません。 使用して、構成の設定を更新した後に**sp_configure**、システム管理者は、RECONFIGURE または RECONFIGURE WITH OVERRIDE のいずれかを使用して実行中の構成値を更新する必要があります。 詳細については、「解説」を参照してください。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(35)**|構成オプションの名前。|  
|**minimum**|**int**|構成オプションの最小値。|  
|**maximum**|**int**|構成オプションの最大値。|  
|**config_value**|**int**|構成オプションに設定する値を使用して**sp_configure** (値**sys.configurations.value**)。 これらのオプションの詳細については、次を参照してください。[サーバー構成オプション &#40;です。SQL Server &#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)と[sys.configurations &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md).|  
|**run_value**|**int**|構成オプションの値を現在実行中 (値**sys.configurations.value_in_use**)。<br /><br /> 詳細については、次を参照してください。 [sys.configurations &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md).|  
  
## <a name="remarks"></a>解説  
 使用して**sp_configure**を表示またはサーバー レベルの設定を変更します。 データベースレベルの設定を変更するには、ALTER DATABASE を使用します。 現在のユーザー セッションのみに影響する設定を変更するには、SET ステートメントを使用します。  
  
## <a name="updating-the-running-configuration-value"></a>実行中の構成値の更新  
 新しいを指定すると*値*の*オプション*、結果セット内でこの値には、 **config_value**列です。 この値が最初の値と異なる場合、 **run_value**列で、現在実行中の構成値を示しています。 実行中の構成値を更新する、 **run_value**列、RECONFIGURE または RECONFIGURE WITH OVERRIDE のどちらか、システム管理者を実行する必要があります。  
  
 RECONFIGURE と RECONFIGURE WITH OVERRIDE は、どちらもすべての構成オプションと共に使用できます。 ただし、基本的な RECONFIGURE ステートメントでは、適切な範囲にないオプション値やオプション間の競合を招く可能性のあるオプション値は使用できません。 たとえば、RECONFIGURE はエラーを生成、**復旧間隔**値が 60 分より大きい場合や、**関係マスク**値と重複しています、 **affinity I/O mask**値。 これに対し、RECONFIGURE WITH OVERRIDE では、データ型が適切であればすべてのオプション値を使用でき、指定した値で再構成が行われます。  
  
> [!CAUTION]  
>  オプション値が適切でない場合、サーバー インスタンスの構成に悪影響を及ぼす可能性があります。 RECONFIGURE WITH OVERRIDE を使用する際は注意が必要です。  
  
 一部のオプションは、RECONFIGURE ステートメントにより動的に更新されます。その他のオプションを使用する場合は、サーバーの停止と再起動が必要になります。 たとえば、**最小サーバー メモリ**と**サーバー メモリの最大**サーバー メモリ オプションが動的に更新される、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。 したがって、サーバーを再起動しなくても変更することができます。 実行中の値をそれに対し、再構成、**の fill factor**オプションは、再起動する必要があります、[!INCLUDE[ssDE](../../includes/ssde-md.md)]です。  
  
 構成オプションで RECONFIGURE を実行後に実行することによって、オプションが動的に更新されたかどうかを確認できます**sp_configure'***option_name***'**です。 内の値、 **run_value**と**config_value**列が動的に更新されるオプションの一致する必要があります。 調べることで、動的のオプションを参照してください。 確認することも、 **is_dynamic**の列、 **sys.configurations**カタログ ビューです。  
  
> [!NOTE]  
>  指定した場合*値*が大きすぎる、オプションの**run_value**という事実を反映する列を[!INCLUDE[ssDE](../../includes/ssde-md.md)]無効な設定を使用するのではなく、動的メモリは、既定値がします。  
  
 詳細については、次を参照してください。 [RECONFIGURE と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/reconfigure-transact-sql.md).  
  
## <a name="advanced-options"></a>[詳細設定オプション]  
 などのいくつかの構成オプション**関係マスク**と**復旧間隔**、高度なオプションとして指定されます。 既定では、これらのオプションを表示や変更に使用することはできません。 使用できるように、設定、 **ShowAdvancedOptions**構成オプションを 1 です。  
  
 構成オプションとその設定の詳細については、次を参照してください。[サーバー構成オプション &#40;です。SQL Server &#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
## <a name="permissions"></a>Permissions  
 パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。 実行する**sp_configure**構成オプションを変更したり RECONFIGURE ステートメントを実行する両方のパラメーターを与える必要があります、ALTER SETTINGS サーバー レベル権限。 ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-listing-the-advanced-configuration-options"></a>A. 詳細構成オプションを一覧表示する  
 次の例では、すべての構成オプションを設定および一覧表示する方法を示します。 高度な構成オプションは、最初の設定で表示される`show advanced option`に`1`です。 このオプションが変更された後に実行する`sp_configure`パラメーターなしですべての構成オプションが表示されます。  
  
```  
USE master;  
GO  
EXEC sp_configure 'show advanced option', '1';  
```  
  
 "構成オプション 'show advanced options' が 0 から 1 に変更されました。 RECONFIGURE ステートメントを実行してインストールしてください。" というメッセージが表示されます。  
  
 `RECONFIGURE` を実行し、すべての構成オプションを表示します。  
  
```  
RECONFIGURE;  
EXEC sp_configure;  
```  
  
### <a name="b-changing-a-configuration-option"></a>B. 構成オプションを変更する  
 次の例では、システムの `recovery interval` を `3` 分に設定します。  
  
```  
USE master;  
GO  
EXEC sp_configure 'recovery interval', '3';  
RECONFIGURE WITH OVERRIDE;  
```  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-list-all-available-configuration-settings"></a>C. すべての使用可能な構成設定を一覧表示する  
 次の例では、すべての構成オプションを一覧表示する方法を示します。  
  
```  
EXEC sp_configure;  
```  
  
 結果は、オプションの最小値と最大値が続くオプション名を返します。 **Config_value**値を[!INCLUDE[ssDW](../../includes/ssdw-md.md)]再構成が完了するときに使用します。 **run_value** は、現在使用されている値です。 値が変更中のプロセスではない限り、 **config_value** と **run_value** は、通常は同じ値です。  
  
### <a name="d-list-the-configuration-settings-for-one-configuration-name"></a>D. 1 つの構成名の構成設定を一覧表示する  
  
```  
EXEC sp_configure @configname='hadoop connectivity';  
```  
  
### <a name="e-set-hadoop-connectivity"></a>E. Hadoop 接続を設定する  
 Hadoop 接続を設定するには、sp_configure を実行しているだけでなく、いくつかの手順が必要です。 完全な手順を参照してください。[外部データ ソースの作成 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-external-data-source-transact-sql.md).  
  
## <a name="see-also"></a>参照  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)   
 [ソフト NUMA &#40;SQL Server&#41;](../../database-engine/configure-windows/soft-numa-sql-server.md)  
  
  
