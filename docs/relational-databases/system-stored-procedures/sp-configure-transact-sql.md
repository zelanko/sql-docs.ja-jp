---
title: sp_configure (Transact SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/16/2016
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_configure
- sp_configure_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_configure
ms.assetid: d18b251d-b37a-4f5f-b50c-502d689594c8
caps.latest.revision: 60
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 05be6cd18d0617cb327c1b964ec19b4d275b1778
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39560092"
---
# <a name="spconfigure-transact-sql"></a>sp_configure (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/t-sql-appliesto-ss-asdbmi-xxxx-pwd-md.md)]

  現在のサーバーのグローバル構成設定を表示または変更します。

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]
  
> [!NOTE]  
>  データベース レベルの構成のオプションを参照してください[データベース スコープの構成の変更&#40;Transact SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)。 ソフト NUMA を構成するのにを参照してください[ソフト NUMA &#40;SQL Server&#41;](../../database-engine/configure-windows/soft-numa-sql-server.md)。  
  
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
 構成オプションの名前を指定します。 *option_name* は **varchar(35)**、既定値は NULL です。 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]の構成名に含まれている一意の文字列を認識します。 指定しない場合、オプションの完全な一覧が返されます。  
  
 使用可能な構成オプションとその設定方法についてを参照してください[サーバーの構成オプション&#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)。  
  
 [ **@configvalue=** ] **'***value***'**  
 新しい構成設定を指定します。 *value* のデータ型は **int**で、既定値は NULL です。 最大値はオプションごとに異なります。  
  
 各オプションの最大値を表示するを参照してください、**最大**の列、 **sys.configurations**カタログを表示します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 パラメーターなしで実行すると**sp_configure** 5 つの列を持つ結果セットを返すし、次の表に示すように、アルファベットの昇順で、オプションを注文します。  
  
 値**config_value**と**run_value**に自動的に同じではありません。 使用して構成設定を更新した後**sp_configure**、システム管理者は再設定または再設定を上書きするのいずれかを使用して、実行中の構成値を更新する必要があります。 詳細については、「解説」を参照してください。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(35)**|構成オプションの名前。|  
|**minimum**|**int**|構成オプションの最小値。|  
|**maximum**|**int**|構成オプションの最大値。|  
|**config_value**|**int**|構成オプションが設定値を使用して**sp_configure** (値**sys.configurations.value**)。 これらのオプションの詳細についてを参照してください[サーバーのコンフィギュレーション オプション&#40;SQL Server&#41; ](../../database-engine/configure-windows/server-configuration-options-sql-server.md)と[sys.configurations &#40;Transact SQL&#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)。|  
|**run_value**|**int**|現在実行中の構成オプションの値 (値**sys.configurations.value_in_use**)。<br /><br /> 詳細についてを参照してください[sys.configurations &#40;Transact SQL&#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)。|  
  
## <a name="remarks"></a>コメント  
 使用**sp_configure**を表示またはサーバー レベルの設定を変更します。 データベースレベルの設定を変更するには、ALTER DATABASE を使用します。 現在のユーザー セッションのみに影響する設定を変更するには、SET ステートメントを使用します。  
  
## <a name="updating-the-running-configuration-value"></a>実行中の構成値の更新  
 新しいを指定すると*値*の*オプション*、結果セット内でこの値には、 **config_value**列です。 この値が初期状態の値と異なる、 **run_value**列で、現在実行中の設定値を示しています。 実行中の構成値を更新するのには、 **run_value**  列で、システム管理者は再設定または再設定を上書きするのいずれかを実行する必要があります。  
  
 RECONFIGURE と RECONFIGURE WITH OVERRIDE は、どちらもすべての構成オプションと共に使用できます。 ただし、基本的な RECONFIGURE ステートメントでは、適切な範囲にないオプション値やオプション間の競合を招く可能性のあるオプション値は使用できません。 たとえば、再構成エラーが発生、**復旧間隔**の値は 60 分を超える場合は、**アフィニティ マスク**と値が重複して、**アフィニティ I/O マスク**値です。 これに対し、RECONFIGURE WITH OVERRIDE では、データ型が適切であればすべてのオプション値を使用でき、指定した値で再構成が行われます。  
  
> [!CAUTION]  
>  オプション値が適切でない場合、サーバー インスタンスの構成に悪影響を及ぼす可能性があります。 RECONFIGURE WITH OVERRIDE を使用する際は注意が必要です。  
  
 一部のオプションは、RECONFIGURE ステートメントにより動的に更新されます。その他のオプションを使用する場合は、サーバーの停止と再起動が必要になります。 などの**最小サーバー メモリ**と**サーバーのメモリを最大**サーバー メモリ オプションが動的に更新される、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]; したがって、サーバーを再起動することがなく変更することができます。 対照的に、実行中の値の再設定、**フィル ファクター**オプションは、再起動する必要があります、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
 再構成を実行すると構成オプションで、実行することによって、オプションが動的に更新されているかどうかを確認できます**sp_configure'***option_name***'**。 値、 **run_value**と**config_value**オプションを動的に更新される列が一致する必要があります。 参照して動的なオプションを確認するのにチェックすることも、 **is_dynamic**の列、 **sys.configurations**カタログを表示します。  
  
> [!NOTE]  
>  指定した場合*値*が大きすぎる、オプションの**run_value**という事実を反映する列を[!INCLUDE[ssDE](../../includes/ssde-md.md)]が正しくない設定を使用するのではなく、動的なメモリをデフォルトに設定されました。  
  
 詳細についてを参照してください[再構成&#40;Transact SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)。  
  
## <a name="advanced-options"></a>[詳細設定オプション]  
 いくつかの環境設定オプションは、次のように**アフィニティ マスク**と**復旧間隔**、高度なオプションとして指定されます。 既定では、これらのオプションを表示や変更に使用することはできません。 利用できるように、設定、 **ShowAdvancedOptions**構成オプションを 1 にします。  
  
 構成オプションとその設定に関する詳細についてを参照してください[サーバーのコンフィギュレーション オプション&#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)。  
  
## <a name="permissions"></a>アクセス許可  
 パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。 実行する**sp_configure**または RECONFIGURE ステートメントを実行する構成オプションを変更するのには両方のパラメーターを与える必要がありますサーバー レベルの設定の変更アクセス許可。 ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-listing-the-advanced-configuration-options"></a>A. 詳細構成オプションを一覧表示する  
 次の例では、すべての構成オプションを設定および一覧表示する方法を示します。 最初の設定で詳細設定オプションが表示されます`show advanced option`を`1`。 このオプションが変更された後に実行する`sp_configure`パラメーターを指定せずにすべての構成オプションが表示されます。  
  
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
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-list-all-available-configuration-settings"></a>C. すべての使用可能な構成設定を一覧表示する  
 次の例では、すべての構成オプションを一覧表示する方法を示します。  
  
```  
EXEC sp_configure;  
```  
  
 結果は、オプションの最小値と最大値が続くオプション名を返します。 **Config_value**は、値を[!INCLUDE[ssDW](../../includes/ssdw-md.md)]の再構成が完了したときに使用します。 **run_value** は、現在使用されている値です。 値が変更中のプロセスではない限り、 **config_value** と **run_value** は、通常は同じ値です。  
  
### <a name="d-list-the-configuration-settings-for-one-configuration-name"></a>D. 1 つの構成名の構成設定を一覧表示する  
  
```  
EXEC sp_configure @configname='hadoop connectivity';  
```  
  
### <a name="e-set-hadoop-connectivity"></a>E. Hadoop 接続を設定する  
 Hadoop の接続を設定するには、sp_configure を実行することに加えて、いくつかの手順が必要です。 完全な手順を参照してください[外部データ ソースの作成&#40;Transact SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)。  
  
## <a name="see-also"></a>参照  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)   
 [ソフト NUMA &#40;SQL Server&#41;](../../database-engine/configure-windows/soft-numa-sql-server.md)  
  
  
