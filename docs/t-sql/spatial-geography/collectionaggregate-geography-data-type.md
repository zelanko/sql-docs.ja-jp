---
title: "CollectionAggregate (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- CollectionAggregate method (geography)
ms.assetid: e49a644a-dbf2-46c3-98f5-4b3ec197e2ad
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4c697a43ac6b79fd137da968ce5f01e49e60c105
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="collectionaggregate-geography-data-type"></a>CollectionAggregate (geography データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

作成、 **GeometryCollection**インスタンスのセットから**geography**オブジェクト。
  
## <a name="syntax"></a>構文  
  
```  
  
ConvexHullAggregate ( geography_operand )  
```  
  
## <a name="arguments"></a>引数  
 *geography_operand*  
 **Geography**型のテーブル列のセットを表す**geography**に記述するオブジェクト、 **GeometryCollection**インスタンス。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
## <a name="exception"></a>例外  
 入力値が無効である場合は、`FormatException` をスローします。 参照してください[STIsValid (& a) #40; geography データ型 &#41;](../../t-sql/spatial-geography/stisvalid-geography-data-type.md)  
  
## <a name="remarks"></a>解説  
 メソッドを返します。 **null**入力が空または入力がの Srid が異なる場合。 参照してください[空間参照識別子 &#40;です。Srid &#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
 メソッドは無視**null**入力します。  
  
> [!NOTE]  
>  メソッドを返します。 **null**入力されたすべての値が場合**null**です。  
  
## <a name="examples"></a>使用例  
 次の例を返します、`GeometryCollection`のセットを含むインスタンス**geography**オブジェクト。  
  
 ```
 USE AdventureWorks2012  
 GO  
 SELECT geography::CollectionAggregate(SpatialLocation).ToString() AS SpatialLocation  
 FROM Person.Address  
 WHERE City LIKE ('Bothell')
 ```  
  
## <a name="see-also"></a>参照  
 [拡張された静的な地理メソッド](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
