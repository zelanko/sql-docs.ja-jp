---
title: "(Geography データ型) を削減 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Reduce_TSQL
- Reduce
dev_langs: TSQL
helpviewer_keywords: Reduce method
ms.assetid: c5dfa8c1-6764-41d8-9150-f3cb30633d3e
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 65b9276d3feea6e72f5404fa8f4d7eef963dbe78
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="reduce-geography-data-type-"></a>Reduce (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  近似を返します、指定された**geography**インスタンス指定された許容範囲を持つインスタンスに対して Douglas-peucker アルゴリズムを実行して生成します。  
  
 これは、 **geography**データ型メソッドでサポート**FullGlobe**インスタンスまたは空間インスタンスは、半球より大きいをします。  
  
## <a name="syntax"></a>構文  
  
```  
  
.Reduce ( tolerance )  
```  
  
## <a name="arguments"></a>引数  
  
|||  
|-|-|  
|項目|定義|  
|*許容範囲*|型の値は、 **float**です。 *トレランス*は、Douglas-peucker アルゴリズムに入力するための許容範囲です。 *トレランス*正数である必要があります。|  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="remarks"></a>解説  
 コレクション型のこのアルゴリズムは個別に各**geography**インスタンスに含まれています。 このアルゴリズムは変更されません**ポイント**インスタンス。  
  
 このメソッドはのエンドポイントを保持しようとします。 **LineString**インスタンスが有効な結果を保持するために失敗する可能性があります。  
  
 場合`Reduce()`が呼び出されたこのメソッドを生成する負の値と共に、 **ArgumentException**です。 `Reduce()` で使用される許容範囲は正の数値である必要があります。  
  
 各で Douglas-peucker アルゴリズムの動作、曲線またはリング、 **geography**始点と終点を除くすべてのポイントを削除するインスタンス。 削除の各ポイントが、追加し、点がなくなるまで、遠く、外の点から始まる複数の*トレランス*結果からです。 有効な結果が保証されるように、必要に応じて結果が有効になります。  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、このメソッドが拡張されて**FullGlobe**インスタンス。  
  
 このメソッドは正確ではありません。  
  
## <a name="examples"></a>使用例  
 次の例を作成、`LineString`使用して、インスタンス`Reduce()`のインスタンスを簡略化します。  
  
```  
DECLARE @g geography = 'LineString(120 45, 120.1 45.1, 199.9 45.2, 120 46)'  
SELECT @g.Reduce(10000).ToString()  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
