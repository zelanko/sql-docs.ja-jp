---
title: sys.sp_xtp_checkpoint_force_garbage_collection (Transact-SQL) | Microsoft Docs
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9142800590230126da882031b70e9c59f4670c3b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47636580"
---
# <a name="sysspxtpcheckpointforcegarbagecollection-transact-sql"></a>sys.sp_xtp_checkpoint_force_garbage_collection (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  ログ シーケンス番号 (LSN) に基づいて、マージ操作で使用されたソース ファイルをマークします。マークされると、ソース ファイルは不要になり、ガベージ コレクションの対象となります。 また、ファイルに関連付けられている LSN がログの切り捨てポイントよりも小さい場合、そのファイルはファイルストリーム ガベージ コレクションに移動されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
 
## <a name="syntax"></a>構文  
  
```  
sys.sp_xtp_checkpoint_force_garbage_collection [[ @dbname=database_name]  
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 ガベージ コレクションが実行されるデータベース。 既定値は現在のデータベースです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 成功した場合は 0。 失敗した場合は 0 以外の値。  
  
## <a name="result-set"></a>結果セット  
 返される行には次の情報が含まれます。  
  
|[列]|説明|  
|------------|-----------------|  
|num_collected_items|ファイルストリーム ガベージ コレクションに移動されたファイルの数を示します。 これらのファイルのログ シーケンス番号 (LSN) は、ログの切り捨てポイントの LSN よりも小さい値になっています。|  
|num_marked_for_collection_items|ログの最後の LSN のログ ブロック ID によって更新された LSN を持つデータ ファイルやデルタ ファイルの数を示します。|  
|last_collected_xact_seqno|ファイルストリーム ガベージ コレクションにファイルがすべて移動された場合、その最後のファイルに対応する LSN を返します。|  
  
## <a name="permissions"></a>アクセス許可  
 データベース所有者の権限が必要です。  
  
## <a name="sample"></a>サンプル  
  
```  
exec [sys].[sp_xtp_checkpoint_force_garbage_collection] hkdb1  
```  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
