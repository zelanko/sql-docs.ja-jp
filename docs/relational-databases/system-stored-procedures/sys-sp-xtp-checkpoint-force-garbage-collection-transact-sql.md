---
title: sp_xtp_checkpoint_force_garbage_collection (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_xtp_checkpoint_force_garbage_collection_TSQL
- sys.sp_xtp_checkpoint_force_garbage_collection
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_xtp_checkpoint_force_garbage_collection
ms.assetid: 82b35b2b-edbd-44ac-9fc8-80695f2fd1df
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 45eb999d6101902ebf9d079235f56d28e343f8e9
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82814489"
---
# <a name="syssp_xtp_checkpoint_force_garbage_collection-transact-sql"></a>sys.sp_xtp_checkpoint_force_garbage_collection (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  マージ操作で使用されるソースファイルをログシーケンス番号 (LSN) でマークします。その後、これらは不要になり、ガベージコレクションできます。 また、関連付けられている LSN がログの切り捨てポイントよりも小さいファイルを filestream ガベージコレクションに移動します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
 
## <a name="syntax"></a>構文  
  
```  
sys.sp_xtp_checkpoint_force_garbage_collection [[ @dbname=database_name]  
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 ガベージ コレクションが実行されるデータベース。 既定値は現在のデータベースです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 成功した場合は 0。 エラーの場合は0以外の。  
  
## <a name="result-set"></a>結果セット  
 返される行には次の情報が含まれます。  
  
|Column|説明|  
|------------|-----------------|  
|num_collected_items|Filestream ガベージコレクションに移動されたファイルの数を示します。 これらのファイルのログ シーケンス番号 (LSN) は、ログの切り捨てポイントの LSN よりも小さい値になっています。|  
|num_marked_for_collection_items|ログの最後の LSN のログブロック id を使用して LSN が更新されたデータ/デルタファイルの数を示します。|  
|last_collected_xact_seqno|ファイルが filestream ガベージコレクションに移動された最後の対応する LSN を返します。|  
  
## <a name="permissions"></a>アクセス許可  
 データベース所有者の権限が必要です。  
  
## <a name="sample"></a>サンプル  
  
```  
exec [sys].[sp_xtp_checkpoint_force_garbage_collection] hkdb1  
```  
  
## <a name="see-also"></a>参照  
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
