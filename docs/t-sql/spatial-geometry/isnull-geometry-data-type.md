---
title: "IsNull (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IsNull (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- IsNull (geometry Data Type)
ms.assetid: f95813a5-26c0-48aa-bfb8-56d2a0980788
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9136a2caf43fea8d5cccd90d8dba85d815511afe
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="isnull-geometry-data-type"></a>IsNull (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

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
  
## <a name="examples"></a>使用例  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの拡張メソッド](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  


