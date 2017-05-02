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
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 2da0c759864e746414f8bf17388463c9a4bfdf88
ms.lasthandoff: 04/11/2017

---
# <a name="polybase-versioned-feature-summary"></a>PolyBase のバージョン管理機能の概要
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  SQL Server の製品やサービスで利用可能な PolyBase 機能の概要です。  
  
## <a name="feature-summary-for-product-releases"></a>製品リリースの機能の概要  
 PolyBase の主な機能と、これらの機能を利用できる製品をまとめた表を次に示します。  
  
### [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
 これらの機能は、オンプレミスまたは Azure 仮想マシンで実行されている [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] に適用されます。  PolyBase は、SQL Server 2014 以前のバージョンでは使用できません。  
  
|||  
|-|-|  
|**機能**|**可用性**|  
|で Hadoop データのクエリを実行する [!INCLUDE[tsql](../../includes/tsql-md.md)]|はい|  
|で Azure blob ストレージのクエリを実行する [!INCLUDE[tsql](../../includes/tsql-md.md)]|はい|  
|Hadoop からデータをインポートする|はい|  
|Azure blob ストレージからデータをインポートする|可| 
|Azure Data Lake Store からデータをインポートする|いいえ|   
|データを Hadoop にエクスポートする|はい|  
|Azure blob ストレージにデータをエクスポートする|可|  
|Azure Data Lake Store からデータをエクスポートする|いいえ|
|Microsoft BI ツールから PolyBase クエリを実行する|はい|  
|クエリの計算を Hadoop にプッシュダウンする|はい|  
  
### [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]  
 これらの機能は [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]に適用されます。  
  
|||  
|-|-|  
|**機能**|**可用性**|  
|で Hadoop データのクエリを実行する [!INCLUDE[tsql](../../includes/tsql-md.md)]|いいえ|  
|で Azure blob ストレージのクエリを実行する [!INCLUDE[tsql](../../includes/tsql-md.md)]|はい|  
|Hadoop からデータをインポートする|いいえ|  
|Azure blob ストレージからデータをインポートする|可|
|Azure Data Lake Store からデータをインポートする|可|     
|データを Hadoop にエクスポートする|いいえ|  
|Azure blob ストレージにデータをエクスポートする|可|  
|Azure Data Lake Store にデータをエクスポートする|可|
|Microsoft BI ツールから PolyBase クエリを実行する|はい|  
|クエリの計算を Hadoop にプッシュダウンする|いいえ|  
  
### [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 これらの機能は [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]に適用されます。  
  
|||  
|-|-|  
|**機能**|**可用性**|  
|で Hadoop データのクエリを実行する [!INCLUDE[tsql](../../includes/tsql-md.md)]|はい|  
|で Azure blob ストレージのクエリを実行する [!INCLUDE[tsql](../../includes/tsql-md.md)]|はい|  
|Hadoop からデータをインポートする|はい|  
|Azure blob ストレージからデータをインポートする|可|  
|Azure Data Lake Store からデータをインポートする|いいえ|   
|データを Hadoop にエクスポートする|はい|  
|Azure blob ストレージにデータをエクスポートする|可|  
|Azure Data Lake Store にデータをエクスポートする|いいえ|
|Microsoft BI ツールから PolyBase クエリを実行する|はい|  
|クエリの計算を Hadoop にプッシュダウンする|はい|  
  
## <a name="see-also"></a>参照  
 [PolyBase ガイド](../../relational-databases/polybase/polybase-guide.md)  
  
  

