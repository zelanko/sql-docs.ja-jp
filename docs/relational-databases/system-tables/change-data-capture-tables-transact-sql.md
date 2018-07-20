---
title: 変更データ キャプチャ テーブル (TRANSACT-SQL) |Microsoft Docs
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a07c68784114879d99127cac19725481be42de2a
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39101490"
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
  
  
