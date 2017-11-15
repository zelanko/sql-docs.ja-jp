---
title: "PolyBase のバージョン管理機能の概要 | Microsoft Docs"
ms.custom: 
ms.date: 08/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6591994d-6109-4285-9c5b-ecb355f8a111
caps.latest.revision: "10"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2d6f0d0b4acbbcf7f1c8dc15f0fe4b64e9b1efbd
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="polybase-versioned-feature-summary"></a>PolyBase のバージョン管理機能の概要
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

SQL Server の製品やサービスで利用可能な PolyBase 機能の概要です。  
  
## <a name="feature-summary-for-product-releases"></a>製品リリースの機能の概要  
 PolyBase の主な機能と、これらの機能を利用できる製品をまとめた表を次に示します。  
  
||||||
|-|-|-|-|-|   
|**機能**|**SQL Server 2016**|**Azure SQL データベース**|**Azure SQL データ ウェアハウス**|**Parallel Data Warehouse**| 
|で Hadoop データのクエリを実行する [!INCLUDE[tsql](../../includes/tsql-md.md)]|はい|いいえ|いいえ|はい|
|Hadoop からデータをインポートする|はい|いいえ|いいえ|はい|
|データを Hadoop にエクスポートする  |はい|いいえ|いいえ| はい|
|HDInsights のクエリ、インポート、エクスポート |いいえ|いいえ|いいえ|いいえ
|クエリの計算を Hadoop にプッシュダウンする|はい|いいえ|いいえ|はい|  
|Azure blob ストレージからデータをインポートする|はい|いいえ|はい|はい| 
|Azure blob ストレージにデータをエクスポートする|はい|いいえ|はい|はい|  
|Azure Data Lake Store からデータをインポートする|いいえ|いいえ|はい|いいえ|    
|Azure Data Lake Store からデータをエクスポートする|いいえ|いいえ|はい|いいえ|
|Microsoft BI ツールから PolyBase クエリを実行する|はい|いいえ|はい|はい|   


## <a name="pushdown-computation-supported-t-sql-operators"></a>プッシュダウン計算でサポートされる T-SQL 演算子
SQL Server および APS では、すべての T-SQL 演算子を hadoop クラスターにプッシュダウンできるわけではありません。 次の表は、すべてサポートされている演算子と、サポートされていない演算子のサブセットを示しています。 

||||
|-|-|-| 
|**演算子の種類**|**Hadoop にプッシュ可能**|**Blob ストレージにプッシュ可能**|
|列のプロジェクション|はい|いいえ|
|述語|はい|いいえ|
|集計|部分的|いいえ|
|外部テーブル間の結合のみ|いいえ|いいえ|
|外部テーブルとローカル テーブル間の結合|いいえ|いいえ|
|並べ替え|いいえ|いいえ|

部分的な集計は、データが SQL Server に達しても Hadoop で集計の一部が発生した後に、最終的な集計を行う必要があることを意味します。 これは、超並列処理システムで一般的な集計の計算方法です。  
## <a name="see-also"></a>参照  
 [PolyBase ガイド](../../relational-databases/polybase/polybase-guide.md)  
  
  
