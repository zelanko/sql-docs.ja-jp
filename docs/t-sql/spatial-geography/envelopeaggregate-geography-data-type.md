---
title: "EnvelopeAggregate (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EnvelopeAggregate_TSQL
- EnvelopeAggregate
dev_langs:
- TSQL
helpviewer_keywords:
- EnvelopeAggregate method (geography)
ms.assetid: 4947797f-edb8-490f-beca-37df9ec06954
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e9d50e15f644a5662af2eead65d29447af8493a9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="envelopeaggregate-geography-data-type"></a>EnvelopeAggregate (geography データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

指定されたセットの境界オブジェクトが返されます**geography**オブジェクト。 その結果、 **geography**オブジェクトには、複数の円弧セグメントが含まれています。
  
## <a name="syntax"></a>構文  
  
```  
  
EnvelopeAggregate ( geography_operand )  
```  
  
## <a name="arguments"></a>引数  
 *geography_operand*  
 **Geography**型のテーブル列のセットを保持する**geography**エンベロープを実行する対象のオブジェクトの集計操作です。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
## <a name="remarks"></a>解説  
 A **FullGlobe**結果の境界オブジェクトが半球よりも大きい場合に、オブジェクトが返されます。 このメソッドは正確ではありません。  
  
 メソッドを返します。 **null** 、入力の Srid が異なる場合。 参照してください[空間参照識別子 & #40 です。Srid &#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
 メソッドは無視**null**入力します。  
  
> [!NOTE]  
>  メソッドを返します。 **null**入力されたすべての値が場合**null**です。  
  
## <a name="examples"></a>使用例  
 次の例を実行、`EnvelopeAggregate`のセットに対して**geography**市区町村内の場所。  
  
 `USE AdventureWorks2012`  
  
 `GO`  
  
 `SELECT City,`  
  
 `geography::EnvelopeAggregate(SpatialLocation) AS SpatialLocation`  
  
 `FROM Person.Address`  
  
 `WHERE PostalCode LIKE('981%')`  
  
 `GROUP BY City;`  
  
## <a name="see-also"></a>参照  
 [拡張された静的な地理メソッド](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  

