---
title: DataType 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DataType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DataType
helpviewer_keywords:
- DataType element
ms.assetid: efe6f717-8288-4ca2-85ed-9b63d27c02d8
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 16bc234f74aa8d6eb80607c7d03d63da8130e8ee
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37231872"
---
# <a name="datatype-element-assl"></a>DataType 要素 (ASSL)
  関連する要素のデータ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DataItem> <!-- or Measure -->  
   ...  
   <DataType>...</DataType>  
   ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DataItem](../data-type/dataitem-data-type-assl.md)、[メジャー](../objects/measure-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `DataType` の値は、`System.Data.OleDb.OleDbType` 列挙内で定義されます。 ただし、`DataType` 要素では、次の表の列挙値のみが有効です。  
  
|値|説明|  
|-----------|-----------------|  
|*BigInt*|64 ビットの符号付き整数です。 このデータ型にマップされます、`Int64`のデータ型の[!INCLUDE[msCoName](../../../includes/msconame-md.md)]OLE DB で .NET Framework および DBTYPE_I8 データを入力します。|  
|*bool*|ブール値です。 このデータ型は、.NET Framework の `Boolean` データ型と、OLE DB の DBTYPE_BOOL データ型にマップされます。|  
|*通貨*|通貨値の-2<sup>63</sup> (または-922,337,203,685,477.5808) を 2 に<sup>63</sup>精度が通貨単位の 10,000-1 (または +922,337,203,685,477.5807)。 このデータ型は、.NET Framework の `Decimal` データ型と、OLE DB の DBTYPE_CY データ型にマップされます。|  
|*日付*|倍精度浮動小数点数として保存される日付データ。 整数部分は 1899 年 12 月 30 日からの日数で、小数部分は日の端数です。 このデータ型は、.NET Framework の `DateTime` データ型と、OLE DB の DBTYPE_DATE データ型にマップされます。|  
|*Double 型*|倍精度浮動小数点番号を範囲 - 1.79 e +308 ~ 1.79 です。 このデータ型は、.NET Framework の `Double` データ型と、OLE DB の DBTYPE_R8 データ型にマップされます。|  
|*Integer*|32 ビットの符号付き整数です。 このデータ型は、.NET Framework の `Int32` データ型と、OLE DB の DBTYPE_I4 データ型にマップされます。|  
|*単一*|単精度浮動小数点数 - 3.40 e の範囲内で +38 から 3.40 e +38 します。 このデータ型は、.NET Framework の `Single` データ型と、OLE DB の DBTYPE_R4 データ型にマップされます。|  
|*SmallInt*|16 ビットの符号付き整数です。 このデータ型は、.NET Framework の `Int16` データ型と、OLE DB の DBTYPE_I2 データ型にマップされます。|  
|*TinyInt*|8 ビットの符号付き整数です。 このデータ型は、.NET Framework の `SByte` データ型と、OLE DB の DBTYPE_I1 データ型にマップされます。|  
|*UnsignedBigInt*|64 ビットの符号なし整数です。 このデータ型は、.NET Framework の `UInt64` データ型と、OLE DB の DBTYPE_UI8 データ型にマップされます。|  
|*UnsignedInt*|32 ビットの符号なし整数です。 このデータ型は、.NET Framework の `UInt32` データ型と、OLE DB の DBTYPE_UI4 データ型にマップされます。|  
|*UnsignedSmallInt*|16 ビットの符号なし整数です。 このデータ型は、.NET Framework の `UInt16` データ型と、OLE DB の DBTYPE_UI2 データ型にマップされます。|  
|*WChar*|Unicode 文字の NULL 終了ストリームです。 このデータ型は、.NET Framework の `String` データ型と、OLE DB の DBTYPE_WSTR データ型にマップされます。|  
|*継承*|データ型、`DataItem`に含まれている、[ソース](source-element-measure-assl.md)の要素、`Measure`要素。 **注:** Applicable にのみ`Measure`要素。|  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
