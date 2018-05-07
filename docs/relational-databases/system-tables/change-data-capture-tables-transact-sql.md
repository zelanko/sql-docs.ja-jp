---
title: 変更データ キャプチャ テーブル (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a4372d0b-50ca-4e58-80f6-2ed3cb52a84a
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: c0317e1c163dacac41968d9c3f17c851cd3be7b5
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="change-data-capture-tables-transact-sql"></a>変更データ キャプチャのテーブル (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  変更データ キャプチャ機能を使用すると、テーブルに対する変更を追跡できます。テーブルに対して行われたデータ操作言語 (DML) およびデータ定義言語 (DDL) の変更が増分的にデータ ウェアハウスへと読み込まれます。 ここでは、変更データ キャプチャ操作で使用される情報を格納しているシステム テーブルについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [cdc.<capture_instance>_CT](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md)  
 関連するソース テーブル内のキャプチャ対象列に対して行われた各変更について 1 行を返します。  
  
 [cdc.captured_columns](../../relational-databases/system-tables/cdc-captured-columns-transact-sql.md)  
 キャプチャ インスタンスで追跡されている各列に対して 1 つの行を返します。  
  
 [cdc.change_tables](../../relational-databases/system-tables/cdc-change-tables-transact-sql.md)  
 データベース内の変更テーブルごとに 1 行を返します。  
  
 [cdc.ddl_history](../../relational-databases/system-tables/cdc-ddl-history-transact-sql.md)  
 変更データ キャプチャが有効になっているテーブルに対して行われたデータ定義言語 (DDL) の変更について、各変更に対応する 1 行を返します。  
  
 [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)  
 変更テーブル内に行が存在する各トランザクションについて 1 行を返します。 このテーブルは、ログ シーケンス番号 (LSN) のコミット値と、トランザクションがコミットされた時刻とをマップするために使用されます。  
  
 [cdc.index_columns](../../relational-databases/system-tables/cdc-index-columns-transact-sql.md)  
 変更テーブルに関連付けられた各インデックス列について、対応する 1 行を返します。  
  
 [dbo.cdc_jobs &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)  
 変更データ キャプチャのエージェント ジョブの構成パラメーターを返します。  
  
## <a name="see-also"></a>参照  
 [変更データ キャプチャ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/change-data-capture-stored-procedures-transact-sql.md)   
 [変更データ キャプチャ関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/change-data-capture-functions-transact-sql.md)  
  
  
