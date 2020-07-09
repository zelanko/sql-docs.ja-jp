---
title: STIsEmpty (geography データ型) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STIsEmpty_TSQL
- STIsEmpty (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIsEmpty method
ms.assetid: 4cbc66e3-9035-4ecf-8f5a-6301f168c26c
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 3c4ae2f630813a97184c70eae9ddd73537f0dd1c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85736097"
---
# <a name="stisempty-geography-data-type"></a>STIsEmpty (geography データ型)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  **geography** インスタンスが空の場合 1 を返します。 **geography** インスタンスが空ではない場合 0 を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STIsEmpty ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **bit**  
  
 CLR の戻り値の型: **SqlBoolean**  
  
## <a name="examples"></a>例  
 空の `geography` インスタンスを作成し、`STIsEmpty()` を使用して、このインスタンスが空であることを確認する例を次に示します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON EMPTY', 4326);  
SELECT @g.STIsEmpty();  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
