---
title: sp_configure (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_configure
- sp_configure_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_configure
ms.assetid: d18b251d-b37a-4f5f-b50c-502d689594c8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 23b75beb0782fc0a13155d12890cbe3a620e1733
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58530244"
---
# <a name="spconfigure-transact-sql"></a>sp_configure (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-pdw-md.md)]

  表示または現在のサーバーのグローバル構成設定を変更します。

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
`[ @configname = ] 'option_name'` 構成オプションの名前です。 *option_name* は **varchar(35)**、既定値は NULL です。 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]の構成名に含まれている一意の文字列を認識します。 指定しない場合、オプションの完全な一覧が返されます。  
  
 使用可能な構成オプションとその設定方法についてを参照してください[サーバーの構成オプション&#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)。  
  
`[ @configvalue = ] 'value'` 新しい構成の設定です。 *value* のデータ型は **int**で、既定値は NULL です。 最大値はオプションごとに異なります。  
  
 各オプションの最大値を表示するを参照してください、**最大**の列、 **sys.configurations**カタログを表示します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 パラメーターなしで実行されると**sp_configure** 5 つの列を含む結果セットを返し、次の表に示すように、昇順でアルファベット順にオプションを並べ替えます。  
  
 値は、 **config_value**と**run_value**自動的に同じではありません。 使用して、構成設定を更新した後**sp_configure**、システム管理者は、RECONFIGURE または RECONFIGURE WITH OVERRIDE のいずれかを使用して、実行中の構成値を更新する必要があります。 詳細については、「解説」を参照してください。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(35)**|構成オプションの名前。|  
|**minimum**|**int**|構成オプションの最小値。|  
|**maximum**|**int**|構成オプションの最大値。|  
|**config_value**|**int**|値を使用する構成オプションが設定された**sp_configure** (値**sys.configurations.value**)。 これらのオプションの詳細についてを参照してください[サーバーのコンフィギュレーション オプション&#40;SQL Server&#41; ](../../database-engine/configure-windows/server-configuration-options-sql-server.md)と[sys.configurations &#40;Transact SQL&#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)。|  
|**run_value**|**int**|現在実行中の構成オプションの値 (値**sys.configurations.value_in_use**)。<br /><br /> 詳細についてを参照してください[sys.configurations &#40;Transact SQL&#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)。|  
  
## <a name="remarks"></a>コメント  
 使用**sp_configure**サーバー レベルの設定を表示または変更します。 データベースレベルの設定を変更するには、ALTER DATABASE を使用します。 現在のユーザー セッションのみに影響する設定を変更するには、SET ステートメントを使用します。  
  
## <a name="updating-the-running-configuration-value"></a>実行中の構成値の更新  
 新しいを指定すると*値*の*オプション*、結果セット内でこの値には、 **config_value**列。 この値は、最初の値と異なる、 **run_value**列は、現在実行中の構成値が表示されます。 実行中の構成値を更新する、 **run_value**列、RECONFIGURE または RECONFIGURE WITH OVERRIDE のどちらか、システム管理者を実行する必要があります。  
  
 再構成し、再設定を上書きするすべての構成オプションを使用して動作します。 ただし、基本的な RECONFIGURE ステートメントでは、妥当な範囲外であるかのオプション間の競合が発生する可能性があります、オプションの値を拒否します。 たとえば、再構成エラーが発生、**復旧間隔**の値は 60 分を超える場合は、**アフィニティ マスク**と値が重複して、**アフィニティ I/O マスク**値です。 再設定を上書きする、対照的に、正しいデータ型を持つ任意のオプションの値を受け入れるし、強制的に指定した値の再設定します。  
  
> [!CAUTION]  
>  オプション値が適切でない場合、サーバー インスタンスの構成に悪影響を及ぼす可能性があります。 使用して、再設定を上書きする注意が必要です。  
  
 一部のオプションは、RECONFIGURE ステートメントにより動的に更新されます。その他のオプションを使用する場合は、サーバーの停止と再起動が必要になります。 などの**最小サーバー メモリ**と**サーバーのメモリを最大**サーバー メモリ オプションが動的に更新される、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]; したがって、サーバーを再起動することがなく変更することができます。 対照的に、実行中の値の再設定、**フィル ファクター**オプションは、再起動する必要があります、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
 構成オプションで RECONFIGURE を実行した後を実行して、オプションが動的に更新されたかどうかを確認できます**sp_configure'***option_name***'** します。 内の値、 **run_value**と**config_value**列が動的に更新されたオプションに一致する必要があります。 動的なオプションを見て確認することも、 **is_dynamic**の列、 **sys.configurations**カタログ ビューです。  
  
> [!NOTE]  
>  指定した場合*値*オプションについては、大きすぎる、 **run_value**という事実を反映する列を[!INCLUDE[ssDE](../../includes/ssde-md.md)]無効な設定を使用するのではなく、既定値が動的メモリにします。  
  
 詳細についてを参照してください[再構成&#40;Transact SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)。  
  
## <a name="advanced-options"></a>[詳細設定オプション]  
 いくつかの環境設定オプションは、次のように**アフィニティ マスク**と**復旧間隔**、高度なオプションとして指定されます。 既定では、これらのオプションは表示および変更に使用できます。 利用できるように、設定、 **ShowAdvancedOptions**構成オプションを 1 にします。  
  
 構成オプションとその設定に関する詳細についてを参照してください[サーバーのコンフィギュレーション オプション&#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)。  
  
## <a name="permissions"></a>アクセス許可  
 パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。 実行する**sp_configure**構成オプションを変更したり RECONFIGURE ステートメントを実行する両方のパラメーターを与える必要があります、ALTER SETTINGS サーバー レベル権限。 ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-listing-the-advanced-configuration-options"></a>A. 詳細設定オプションの一覧を表示  
 設定し、すべての構成オプションの一覧を次の例を次に示します。 最初の設定で詳細設定オプションが表示されます`show advanced option`を`1`。 このオプションが変更された後に実行する`sp_configure`パラメーターを指定せずにすべての構成オプションが表示されます。  
  
```  
USE master;  
GO  
EXEC sp_configure 'show advanced option', '1';  
```  
  
 メッセージを次に示します。"構成オプション 'show advanced options'、0 から 1 に変更します。 実行するインストールするのには、RECONFIGURE ステートメント。  
  
 `RECONFIGURE` を実行し、すべての構成オプションを表示します。  
  
```  
RECONFIGURE;  
EXEC sp_configure;  
```  
  
### <a name="b-changing-a-configuration-option"></a>B. 構成オプションを変更します。  
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
  
 結果は、オプションの最小値と最大値が続くオプション名を返します。 **Config_value**が値を[!INCLUDE[ssDW](../../includes/ssdw-md.md)]再構成が完了するときに使用されます。 **run_value** は、現在使用されている値です。 値が変更中のプロセスではない限り、 **config_value** と **run_value** は、通常は同じ値です。  
  
### <a name="d-list-the-configuration-settings-for-one-configuration-name"></a>D. 1 つの構成名の構成設定を一覧表示する  
  
```  
EXEC sp_configure @configname='hadoop connectivity';  
```  
  
### <a name="e-set-hadoop-connectivity"></a>E. Hadoop 接続を設定する  
 Hadoop 接続を設定するには、sp_configure を実行しているだけでなく、いくつかの手順が必要です。 完全な手順を参照してください[外部データ ソースの作成&#40;Transact SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)。  
  
## <a name="see-also"></a>参照  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)   
 [ソフト NUMA &#40;SQL Server&#41;](../../database-engine/configure-windows/soft-numa-sql-server.md)  
  
  
