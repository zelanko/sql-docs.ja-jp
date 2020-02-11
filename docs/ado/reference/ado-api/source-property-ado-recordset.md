---
title: Source プロパティ (ADO Recordset) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::putref_Source
- Recordset15::Source
- Recordset15::PutSource
- Recordset15::get_Source
- Recordset15::GetSource
- Recordset15::PutRefSource
- Recordset15::put_Source
helpviewer_keywords:
- Source property [ADO Recordset]
ms.assetid: a05ba2c9-2821-4343-8607-4de9b764ec91
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8f6ac84445272ae3657d4e25691dbbf150f32c5d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67930927"
---
# <a name="source-property-ado-recordset"></a>Source プロパティ (ADO Recordset)
[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトのデータソースを示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 **文字列**値または[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト参照を設定します。**レコードセット**のソースを示す**文字列**値のみを返します。  
  
## <a name="remarks"></a>解説  
 **コマンド**オブジェクト変数、SQL ステートメント、ストアドプロシージャ、またはテーブル名のいずれかを使用して、**レコードセット**オブジェクトのデータソースを指定するには、 **Source**プロパティを使用します。  
  
 **Source**プロパティを**command**オブジェクトに設定した場合、 **Recordset**オブジェクトの[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)プロパティは、指定された**command**オブジェクトの**ActiveConnection**プロパティの値を継承します。 ただし、 **Source**プロパティを読み取ると、 **Command**オブジェクトは返されません。代わりに、 **Source**プロパティを設定する**Command**オブジェクトの[CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)プロパティを返します。  
  
 **Source**プロパティが SQL ステートメント、ストアドプロシージャ、またはテーブル名の場合は、 [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md)メソッド呼び出しで適切な*オプション*引数を渡すことで、パフォーマンスを最適化できます。  
  
 **ソース**プロパティは、閉じた**レコードセット**オブジェクトの場合は読み取り/書き込み、開いている**レコードセット**オブジェクトの場合は読み取り専用です。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Source プロパティの例 (VB)](../../../ado/reference/ado-api/source-property-example-vb.md)   
 [Source プロパティ (ADO Error)](../../../ado/reference/ado-api/source-property-ado-error.md)   
 [Source プロパティ (ADO Record)](../../../ado/reference/ado-api/source-property-ado-record.md)
