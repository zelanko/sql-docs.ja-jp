---
description: Source プロパティ (ADO Recordset)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 29ce12027267918822ed49185f06ab28a6448190
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777401"
---
# <a name="source-property-ado-recordset"></a>Source プロパティ (ADO Recordset)
[レコードセット](./recordset-object-ado.md)オブジェクトのデータソースを示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 **文字列**値または[コマンド](./command-object-ado.md)オブジェクト参照を設定します。**レコードセット**のソースを示す**文字列**値のみを返します。  
  
## <a name="remarks"></a>解説  
 **コマンド**オブジェクト変数、SQL ステートメント、ストアドプロシージャ、またはテーブル名のいずれかを使用して、**レコードセット**オブジェクトのデータソースを指定するには、 **Source**プロパティを使用します。  
  
 **Source**プロパティを**command**オブジェクトに設定した場合、 **Recordset**オブジェクトの[ActiveConnection](./activeconnection-property-ado.md)プロパティは、指定された**command**オブジェクトの**ActiveConnection**プロパティの値を継承します。 ただし、 **Source**プロパティを読み取ると、 **Command**オブジェクトは返されません。代わりに、 **Source**プロパティを設定する**Command**オブジェクトの[CommandText](./commandtext-property-ado.md)プロパティを返します。  
  
 **Source**プロパティが SQL ステートメント、ストアドプロシージャ、またはテーブル名の場合は、 [Open](./open-method-ado-recordset.md)メソッド呼び出しで適切な*オプション*引数を渡すことで、パフォーマンスを最適化できます。  
  
 **ソース**プロパティは、閉じた**レコードセット**オブジェクトの場合は読み取り/書き込み、開いている**レコードセット**オブジェクトの場合は読み取り専用です。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Source プロパティの例 (VB)](./source-property-example-vb.md)   
 [Source プロパティ (ADO Error)](./source-property-ado-error.md)   
 [Source プロパティ (ADO Record)](./source-property-ado-record.md)