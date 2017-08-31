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
ms.translationtype: HT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: dcfa27ad11e3027519398b9424056b52afb1617b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/28/2017

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



  
## <a name="see-also"></a>参照  
 [PolyBase ガイド](../../relational-databases/polybase/polybase-guide.md)  
  
  

