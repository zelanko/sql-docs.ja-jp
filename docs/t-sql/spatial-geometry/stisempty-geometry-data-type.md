---
title: STIsEmpty (geometry データ型) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STIsEmpty_TSQL
- STIsEmpty (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIsEmpty (geometry Data Type)
ms.assetid: dcbd6ae1-5d63-485f-9d58-28bfd504524e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 62419df0c6d0768924f841e2b06ec21eda1ee5e2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47667170"
---
# <a name="stisempty-geometry-data-type"></a>STIsEmpty (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

**geometry** インスタンスが空白である場合、1 を返します。 **geometry** インスタンスが空白ではない場合は、0 を返します。
  
## <a name="syntax"></a>構文  
  
```  
  
.STIsEmpty ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **bit**  
  
 CLR の戻り値の型: **SqlBoolean**  
  
## <a name="examples"></a>使用例  
 `geometry` インスタンスを作成し、`STIsEmpty()` を使用して、このインスタンスが空白かどうかをテストする例を次に示します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON EMPTY', 0);  
SELECT @g.STIsEmpty();  
```  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

