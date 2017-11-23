---
title: "IsNull (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/12/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: IsNull (geometry Data Type)
dev_langs: TSQL
helpviewer_keywords: IsNull (geometry Data Type)
ms.assetid: f95813a5-26c0-48aa-bfb8-56d2a0980788
caps.latest.revision: "13"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 25b4699265ec8cc5f2db2ef7cbfb8bb9813c3626
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="isnull-geometry-data-type"></a>IsNull (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

型、 **geometry**インスタンスが null です。 インスタンスが NULL でない場合 0 を返します。
  
## <a name="syntax"></a>構文  
  
```  
.IsNull  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型:**ビット**  
  
 CLR 型: **SqlBoolean**  
  
## <a name="remarks"></a>解説  
 `IsNull`テストに使用できるかどうか、 **geometry**インスタンスが null です。 このテストの結果は若干複雑であるため注意してください。インスタンスが NULL でなければ 0 を返し、インスタンスが NULL であれば NULL を返します。  
  
 このメソッドは、主に SQL Server インフラストラクチャによって使用されます。インスタンスが NULL かどうかをテストするために `IsNull` を使用することはお勧めしません。  
  

## <a name="see-also"></a>参照  
 [Geometry インスタンスの拡張メソッド](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

