---
title: HasM (geography データ型) | Microsoft Docs
ms.custom: ''
ms.date: 05/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- HasM_TSQL
- HasM
dev_langs:
- TSQL
helpviewer_keywords:
- HasM geography
ms.assetid: e752e97f-1619-437d-b962-48c188b4e94c
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 038610db98b647aa48b633ccd90fc6a2310c06b6
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2019
ms.locfileid: "65937746"
---
# <a name="hasm-geography-data-type"></a>HasM (geography データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

空間オブジェクトに少なくとも 1 つの M 値が含まれている場合は 1 (true)、それ以外の場合は 0 (false) が返されます。  
  
## <a name="syntax"></a>構文  
  
```sql  
  
.HasM  
```  
  
## <a name="return-types"></a>戻り値の型  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **bit**  
  
CLR の戻り値の型:**ブール値**  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>使用例  
  
```sql  
DECLARE @p GEOGRAPHY = 'Point(1 1 1 1)'  
SELECT @p.HasM   
--Returns: 1 (true)  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [M &#40;geography データ型&#41;](../../t-sql/spatial-geography/m-geography-data-type.md)  
  
  
