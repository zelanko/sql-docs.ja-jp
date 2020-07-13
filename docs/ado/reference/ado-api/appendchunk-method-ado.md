---
title: AppendChunk メソッド (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::AppendChunk
- Field20::AppendChunk
helpviewer_keywords:
- AppendChunk method [ADO]
ms.assetid: c648b5a8-d4f1-4d16-836e-3957feb03617
author: rothja
ms.author: jroth
ms.openlocfilehash: 5ebf6f52e4c2ac9cc4875db26e633457915c0a5e
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762941"
---
# <a name="appendchunk-method-ado"></a>AppendChunk メソッド (ADO)
大きなテキストまたはバイナリデータ[フィールド](../../../ado/reference/ado-api/field-object.md)、または[パラメーター](../../../ado/reference/ado-api/parameter-object.md)オブジェクトにデータを追加します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.AppendChunk Data  
```  
  
#### <a name="parameters"></a>パラメーター  
 *object*  
 **フィールド**または**パラメーター**オブジェクト。  
  
 *データ*  
 オブジェクトに追加するデータを格納している**バリアント**。  
  
## <a name="remarks"></a>解説  
 **フィールド**または**パラメーター**オブジェクトに対して**appendchunk**メソッドを使用して、長いバイナリまたは文字データを格納します。 システムメモリが制限されている場合は、 **Appendchunk**メソッドを使用して、長い値を全体ではなく部分的に操作することができます。  
  
## <a name="field"></a>フィールド  
 **Field**オブジェクトの[Attributes](../../../ado/reference/ado-api/attributes-property-ado.md)プロパティの**adfldlong**ビットが**true**に設定されている場合は、そのフィールドに**appendchunk**メソッドを使用できます。  
  
 **Field**オブジェクトの最初の**appendchunk**呼び出しでは、データがフィールドに書き込まれ、既存のデータが上書きされます。 後続の**Appendchunk**呼び出しでは、を既存のデータに追加します。 1つのフィールドにデータを追加した後、現在のレコードの別のフィールドの値を設定または読み取る場合、ADO は最初のフィールドにデータを追加したことを前提としています。 最初のフィールドで**appendchunk**メソッドを再度呼び出すと、ADO は呼び出しを新しい**appendchunk**操作として解釈し、既存のデータを上書きします。 最初の**レコードセット**オブジェクトの複製ではない他の[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトのフィールドにアクセスしても、 **appendchunk**操作が中断されることはありません。  
  
 **フィールド**オブジェクトで**appendchunk**を呼び出したときに現在のレコードが存在しない場合は、エラーが発生します。  
  
> [!NOTE]
>  **Appendchunk**メソッドは、[レコードオブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)オブジェクトの**フィールド**オブジェクトに対しては動作しません。 操作は一切実行されず、実行時エラーが発生します。  
  
## <a name="parameter"></a>パラメーター  
 **Parameter**オブジェクトの**Attributes**プロパティの**adparamlong**ビットが**true**に設定されている場合は、そのパラメーターに**appendchunk**メソッドを使用できます。  
  
 **パラメーター**オブジェクトの最初の**appendchunk**呼び出しは、データをパラメーターに書き込み、既存のデータを上書きします。 **パラメーター**オブジェクトに対する後続の**appendchunk**呼び出しは、既存のパラメーターデータにを追加します。 Null 値を渡す**Appendchunk**呼び出しは、すべてのパラメーターデータを破棄します。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Field オブジェクト](../../../ado/reference/ado-api/field-object.md)|[Parameter オブジェクト](../../../ado/reference/ado-api/parameter-object.md)|  
  
## <a name="see-also"></a>参照  
 [AppendChunk および GetChunk メソッドの例 (VB)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vb.md)   
 [AppendChunk および GetChunk メソッドの例 (VC + +)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vc.md)   
 [Attributes プロパティ (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)   
 [GetChunk メソッド (ADO)](../../../ado/reference/ado-api/getchunk-method-ado.md)
