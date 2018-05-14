---
title: DataType 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 247d13565e82f2aac4175d262ecfd0f4c94e39b1
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="datatype-element-assl"></a>DataType 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|親要素|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)、[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 値は、 **DataType**で定義されて、 **System.Data.OleDb.OleDbType**列挙します。 次の表の列挙値のみがでは有効で、 **DataType**要素。  
  
|値|Description|  
|-----------|-----------------|  
|*BigInt*|64 ビットの符号付き整数です。 このデータ型にマップ、 **Int64**のデータ型の[!INCLUDE[msCoName](../../../includes/msconame-md.md)]OLE DB に .NET Framework と DBTYPE_I8 データを入力します。|  
|*bool*|ブール値です。 このデータ型にマップ、**ブール**.NET Framework と OLE DB の DBTYPE_BOOL データ型でのデータ型。|  
|*Currency*|-2 から範囲の通貨値<sup>63</sup> (または-922,337,203,685,477.5808) を 2<sup>63</sup>精度が通貨単位の 10,000-1 (または +922,337,203,685,477.5807)。 このデータ型にマップ、 **Decimal** .NET Framework と OLE DB の DBTYPE_CY データ型でのデータ型。|  
|*日付*|倍精度浮動小数点数として保存される日付データ。 整数部分は 1899 年 12 月 30 日からの日数で、小数部分は日の端数です。 このデータ型にマップ、 **DateTime** .NET Framework と OLE DB の DBTYPE_DATE データ型でのデータ型。|  
|*Double*|倍精度浮動小数点数、範囲 - 1.79 e +308 ~ 1.79 です。 このデータ型にマップ、**二重**.NET Framework と OLE DB の DBTYPE_R8 データ型でのデータ型。|  
|*Integer*|32 ビットの符号付き整数です。 このデータ型にマップ、 **Int32** .NET Framework と OLE DB の DBTYPE_I4 データ型でのデータ型。|  
|*単一*|単精度浮動小数点数 - 3.40 e の範囲内で +38 から 3.40 e +38 です。 このデータ型にマップ、**単一**で .NET Framework と OLE DB の DBTYPE_R4 データ型のデータ型。|  
|*SmallInt*|16 ビットの符号付き整数です。 このデータ型にマップ、 **Int16** .NET Framework と OLE DB の DBTYPE_I2 データ型でのデータ型。|  
|*TinyInt*|8 ビットの符号付き整数です。 このデータ型にマップ、 **SByte**で .NET Framework と OLE DB の DBTYPE_I1 データ型のデータ型。|  
|*UnsignedBigInt*|64 ビットの符号なし整数です。 このデータ型にマップ、 **UInt64**で .NET Framework と OLE DB の DBTYPE_UI8 データ型のデータ型。|  
|*unsignedInt*|32 ビットの符号なし整数です。 このデータ型にマップ、 **UInt32** .NET Framework と OLE DB の DBTYPE_UI4 データ型でのデータ型。|  
|*UnsignedSmallInt*|16 ビットの符号なし整数です。 このデータ型にマップ、 **UInt16**で .NET Framework と OLE DB の DBTYPE_UI2 データ型のデータ型。|  
|*WChar*|Unicode 文字の NULL 終了ストリームです。 このデータ型にマップ、**文字列**.NET Framework と OLE DB の DBTYPE_WSTR データ型でのデータ型。|  
|*継承*|データ型、 **DataItem**に含まれている、[ソース](../../../analysis-services/scripting/properties/source-element-measure-assl.md)の要素、**メジャー**要素。<br /><br /> 注: のみに適用できる**メジャー**要素。|  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
