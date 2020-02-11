---
title: 変更データキャプチャテーブル (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a4372d0b-50ca-4e58-80f6-2ed3cb52a84a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7d6d87ee8b2aa05c3156acb2db9c6604380db887
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68082683"
---
# <a name="change-data-capture-tables-transact-sql"></a>変更データキャプチャテーブル (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  変更データキャプチャを使用すると、テーブルに対するデータ操作言語 (DML) およびデータ定義言語 (DDL) の変更をデータウェアハウスに増分読み込みできるように、テーブルに対する変更の追跡が有効になります。 このセクションのトピックでは、変更データキャプチャ操作で使用される情報を格納するシステムテーブルについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [cdc. <capture_instance>_CT](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md)  
 関連付けられたソーステーブル内のキャプチャ対象列に対して行われた変更ごとに1行の値を返します。  
  
 [cdc.captured_columns](../../relational-databases/system-tables/cdc-captured-columns-transact-sql.md)  
 キャプチャインスタンスで追跡されている列ごとに1行の値を返します。  
  
 [cdc.change_tables](../../relational-databases/system-tables/cdc-change-tables-transact-sql.md)  
 データベース内の変更テーブルごとに 1 行を返します。  
  
 [cdc.ddl_history](../../relational-databases/system-tables/cdc-ddl-history-transact-sql.md)  
 変更データ キャプチャが有効になっているテーブルに対して行われたデータ定義言語 (DDL) の変更について、各変更に対応する 1 行を返します。  
  
 [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)  
 変更テーブル内の行を保持しているトランザクションごとに1行の値を返します。 このテーブルは、ログシーケンス番号 (LSN) のコミット値とトランザクションがコミットされた時刻の間のマッピングに使用されます。  
  
 [cdc.index_columns](../../relational-databases/system-tables/cdc-index-columns-transact-sql.md)  
 変更テーブルに関連付けられている各インデックス列に対して1行の値を返します。  
  
 [dbo. cdc_jobs &#40;Transact-sql&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)  
 変更データ キャプチャのエージェント ジョブの構成パラメーターを返します。  
  
## <a name="see-also"></a>参照  
 [変更データキャプチャのストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/change-data-capture-stored-procedures-transact-sql.md)   
 [変更データキャプチャ関数 &#40;Transact-sql&#41;](../../relational-databases/system-functions/change-data-capture-functions-transact-sql.md)  
  
  
