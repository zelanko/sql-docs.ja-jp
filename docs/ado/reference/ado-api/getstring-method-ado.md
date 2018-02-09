---
title: "GetString メソッド (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset20::raw_GetString
- Recordset20::GetString
helpviewer_keywords:
- GetString method [ADO]
ms.assetid: 92452940-b2a7-456e-94fc-3780c71da33c
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 03449fb395e9c4448f7111728adb392facae9921
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="getstring-method-ado"></a>GetString メソッド (ADO)
返します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)を文字列として。  
  
## <a name="syntax"></a>構文  
  
```  
  
Variant = recordset.GetString(StringFormat, NumRows, ColumnDelimiter, RowDelimiter, NullExpr)  
```  
  
## <a name="return-value"></a>戻り値  
 返します、 **Recordset**文字列値として**バリアント**(BSTR)。  
  
#### <a name="parameters"></a>パラメーター  
 *StringFormat*  
 A [StringFormatEnum](../../../ado/reference/ado-api/stringformatenum.md)値を指定する方法、 **Recordset**を文字列に変換する必要があります。 *RowDelimiter*、 *ColumnDelimiter*、および*NullExpr*パラメーターでのみ使用されて、 *StringFormat*の**adClipString**です。  
  
 *NumRows*  
 省略可。 変換する行の数、 **Recordset**です。 場合*NumRows*が指定されていない、内の行の総数よりも大きい場合や、**レコード セット**、し、すべての行で、**レコード セット**変換されます。  
  
 *[列区切り記号]*  
 省略可。 それ以外の場合、タブ文字を指定した場合、列間で使用される区切り記号です。  
  
 *RowDelimiter*  
 省略可。 それ以外の場合、キャリッジ リターン文字を指定した場合、行の間で使用される区切り記号です。  
  
 *NullExpr*  
 省略可。 、それ以外の場合、空の文字列を指定されている場合に、null 値の代わりに使用される式。  
  
## <a name="remarks"></a>解説  
 行のデータが、スキーマ データは、文字列に保存されます。 したがって、 **Recordset**この文字列を使用してを再度開くことはできません。  
  
 このメソッドは、RDO **GetClipString**メソッドです。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [GetString メソッドの例 (VB)](../../../ado/reference/ado-api/getstring-method-example-vb.md)
