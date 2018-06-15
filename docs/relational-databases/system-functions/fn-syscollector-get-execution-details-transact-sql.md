---
title: fn_syscollector_get_execution_details (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_syscollector_get_execution_details_TSQL
- fn_syscollector_get_execution_details
dev_langs:
- TSQL
helpviewer_keywords:
- fn_syscollector_get_execution_details function
ms.assetid: d59ddf0c-72c0-4c57-bc83-aef260e4e105
caps.latest.revision: 15
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4336b2bd20dbfb49996f6eb4edd5826533215b89
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230103"
---
# <a name="fnsyscollectorgetexecutiondetails-transact-sql"></a>fn_syscollector_get_execution_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssIS](../../includes/ssis-md.md)] ログ (sysssislog) で、指定されたパッケージの package_execution_id と一致する部分を返します。 このテーブルは、パッケージやパッケージのタスク、およびコンテナーによって実行時に生成される各ログ エントリに対して、1 行のデータを格納します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
fn_syscollector_get_execution_details ( log_id )  
```  
  
## <a name="arguments"></a>引数  
 *log_id*  
 実行ログの一意なローカル識別子を指定します。 *log_id*は**int**です。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|id|**int**|ログ エントリの一意識別子。|  
|イベント|**sysname**|ログ エントリを生成したイベントの名前。|  
|computer|**nvarchar**|ログ エントリの生成時にパッケージが実行されていたコンピューター。|  
|演算子 (operator)|**nvarchar**|ログ エントリを生成したパッケージを実行したユーザーまたはエージェントの名前。|  
|source|**nvarchar**|ログ エントリを生成した実行可能ファイルの名前。|  
|sourceid|**uniqueidentifier**|ログ エントリを生成した実行可能ファイルの GUID。|  
|executionid|**uniqueidentifier**|ログ エントリを生成した実行可能ファイルの実行インスタンスの GUID。|  
|starttime|**datetime**|パッケージが実行を開始した時刻。|  
|endtime|**datetime**|パッケージが完了した時刻。|  
|datacode|**int**|ログ エントリと関連するイベントを識別する整数値。 "0" は、識別子が指定されていないイベントを表します。|  
|databytes|**image**|戻り値を識別するバイト配列。|  
|message|**nvarchar**|イベントおよびイベントに関連する情報の説明。|  
  
## <a name="permissions"></a>権限  
 に対する SELECT 権限が必要です**dc_operator**です。  
  
## <a name="see-also"></a>参照  
 [パッケージで SQL Server データ ツールのログ記録を有効にします。](../../integration-services/performance/integration-services-ssis-logging.md#server_logging)   
 [データ コレクション](../../relational-databases/data-collection/data-collection.md)  
  
  
