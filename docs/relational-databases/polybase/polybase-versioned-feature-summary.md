---
title: "PolyBase のバージョン管理機能の概要 | Microsoft Docs"
ms.custom: 
ms.date: 04/13/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6591994d-6109-4285-9c5b-ecb355f8a111
caps.latest.revision: 10
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: cf69aa2c57e86aab11974b5874039ae7f72b9917
ms.openlocfilehash: 3384d962c3765bf4feb00f957ad56a668f8d92e4
ms.contentlocale: ja-jp
ms.lasthandoff: 06/23/2017

---
# <a name="polybase-versioned-feature-summary"></a>PolyBase のバージョン管理機能の概要
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

SQL Server の製品やサービスの使用可能な PolyBase 機能の概要です。  
  
## <a name="feature-summary-for-product-releases"></a>製品リリースの機能の概要  
 PolyBase の主な機能と、これらの機能を利用できる製品をまとめた表を次に示します。  
  
||||||
|-|-|-|-|-|   
|**機能**|**SQL Server 2016**|**Azure SQL データベース**|**Azure SQL データ ウェアハウス**|**Parallel Data Warehouse**| 
|で Hadoop データのクエリを実行する [!INCLUDE[tsql](../../includes/tsql-md.md)]|可|いいえ|いいえ|可|
|Hadoop からデータをインポートする|可|いいえ|いいえ|可|
|データを Hadoop にエクスポートする  |可|いいえ|いいえ| 可|
|クエリの計算を Hadoop にプッシュダウンする|可|いいえ|いいえ|可|  
|Azure blob ストレージからデータをインポートする|はい|いいえ|はい|可| 
|Azure blob ストレージにデータをエクスポートする|はい|いいえ|はい|可|  
|Azure Data Lake Store からデータをインポートする|いいえ|いいえ|はい|いいえ|    
|Azure Data Lake Store からデータをエクスポートする|いいえ|いいえ|はい|いいえ|
|Microsoft BI ツールから PolyBase クエリを実行する|可|いいえ|はい|可|   



  
## <a name="see-also"></a>参照  
 [PolyBase ガイド](../../relational-databases/polybase/polybase-guide.md)  
  
  

