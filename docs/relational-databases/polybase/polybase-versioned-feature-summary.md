---
title: "PolyBase のバージョン管理機能の概要 | Microsoft Docs"
ms.custom: ""
ms.date: "04/13/2016"
ms.prod: "sql-non-specified"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6591994d-6109-4285-9c5b-ecb355f8a111
caps.latest.revision: 10
author: "barbkess"
ms.author: "barbkess"
manager: "jhubbard"
caps.handback.revision: 8
---
# PolyBase のバージョン管理機能の概要
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  SQL Server の製品やサービスで利用可能な PolyBase 機能の概要です。  
  
## 製品リリースの機能の概要  
 PolyBase の主な機能と、これらの機能を利用できる製品をまとめた表を次に示します。  
  
### [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
 これらの機能は、オンプレミスまたは Azure 仮想マシンで実行されている [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] に適用されます。  PolyBase は、SQL Server 2014 以前のバージョンでは使用できません。  
  
|||  
|-|-|  
|**機能**|**可用性**|  
|で Hadoop データのクエリを実行する [!INCLUDE[tsql](../../includes/tsql-md.md)]|はい|  
|で Azure blob ストレージのクエリを実行する [!INCLUDE[tsql](../../includes/tsql-md.md)]|はい|  
|Hadoop からデータをインポートする|はい|  
|Azure blob ストレージからデータをインポートする|はい|  
|データを Hadoop にエクスポートする|はい|  
|Azure blob ストレージにデータをエクスポートする|はい|  
|Microsoft BI ツールから PolyBase クエリを実行する|はい|  
|クエリの計算を Hadoop にプッシュダウンする|はい|  
  
### [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]  
 これらの機能は [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] に適用されます。  
  
|||  
|-|-|  
|**機能**|**可用性**|  
|で Hadoop データのクエリを実行する [!INCLUDE[tsql](../../includes/tsql-md.md)]|いいえ|  
|で Azure blob ストレージのクエリを実行する [!INCLUDE[tsql](../../includes/tsql-md.md)]|はい|  
|Hadoop からデータをインポートする|いいえ|  
|Azure blob ストレージからデータをインポートする|はい|  
|データを Hadoop にエクスポートする|いいえ|  
|Azure blob ストレージにデータをエクスポートする|はい|  
|Microsoft BI ツールから PolyBase クエリを実行する|はい|  
|クエリの計算を Hadoop にプッシュダウンする|いいえ|  
  
### [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 これらの機能は [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] に適用されます。  
  
|||  
|-|-|  
|**機能**|**可用性**|  
|で Hadoop データのクエリを実行する [!INCLUDE[tsql](../../includes/tsql-md.md)]|はい|  
|で Azure blob ストレージのクエリを実行する [!INCLUDE[tsql](../../includes/tsql-md.md)]|はい|  
|Hadoop からデータをインポートする|はい|  
|Azure blob ストレージからデータをインポートする|はい|  
|データを Hadoop にエクスポートする|はい|  
|Azure blob ストレージにデータをエクスポートする|はい|  
|Microsoft BI ツールから PolyBase クエリを実行する|はい|  
|クエリの計算を Hadoop にプッシュダウンする|はい|  
  
## 参照  
 [PolyBase ガイド](../../relational-databases/polybase/polybase-guide.md)  
  
  