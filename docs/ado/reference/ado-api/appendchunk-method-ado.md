---
title: "AppendChunk メソッド (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Parameter::AppendChunk
- Field20::AppendChunk
helpviewer_keywords:
- AppendChunk method [ADO]
ms.assetid: c648b5a8-d4f1-4d16-836e-3957feb03617
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 812566487a453d806e1defcd7b2b7977e5f1935f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="appendchunk-method-ado"></a>AppendChunk メソッド (ADO)
大きなテキストまたはバイナリ データへのデータの追加[フィールド](../../../ado/reference/ado-api/field-object.md)、または、[パラメーター](../../../ado/reference/ado-api/parameter-object.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.AppendChunk Data  
```  
  
#### <a name="parameters"></a>パラメーター  
 *オブジェクト*  
 A**フィールド**または**パラメーター**オブジェクト。  
  
 *データ*  
 A**バリアント**オブジェクトに追加するデータを格納しています。  
  
## <a name="remarks"></a>解説  
 使用して、 **AppendChunk**メソッドを**フィールド**または**パラメーター**長いバイナリまたは文字のデータを格納するオブジェクト。 システム メモリが限られている状況で使用できます、 **AppendChunk**全体ではなく特定の部分で長い値を操作するメソッド。  
  
## <a name="field"></a>フィールド  
 場合、 **adFldLong**ビット、[属性](../../../ado/reference/ado-api/attributes-property-ado.md)のプロパティ、**フィールド**にオブジェクトが設定されている**true**、使用することができます、 **AppendChunk**そのフィールドのメソッドです。  
  
 最初の**AppendChunk**でを呼び出す、**フィールド**既存のデータを上書きするオブジェクトのフィールドにデータを書き込みます。 その後**AppendChunk**呼び出しは、既存のデータに追加します。 1 つのフィールドにデータを追加すると、設定したり、現在のレコードの別のフィールドの値を読み取る、ADO では、最初のフィールドにデータを追加操作が完了している前提としています。 呼び出す場合は、 **AppendChunk**番目のフィールドにもう一度、ADO 上のメソッドでは、解釈、新しい呼び出し**AppendChunk**操作し、既存のデータを上書きします。 他のフィールドにアクセスする[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)最初のクローンではないオブジェクトを**Recordset**オブジェクトを妨害しない**AppendChunk**操作します。  
  
 呼び出すと、現在のレコードがない場合**AppendChunk**上、**フィールド**オブジェクト、エラーが発生します。  
  
> [!NOTE]
>  **AppendChunk**についてメソッドは動作しません**フィールド**のオブジェクト、[レコード オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)オブジェクト。 任意の操作は実行されませんし、実行時エラーが生成されます。  
  
## <a name="parameter"></a>パラメーター  
 場合、 **adParamLong**ビット、**属性**のプロパティ、**パラメーター**にオブジェクトが設定されている**true**、使用することができます、 **AppendChunk**そのパラメーターのメソッドです。  
  
 最初の**AppendChunk**でを呼び出す、**パラメーター**既存のデータを上書きするオブジェクトが、パラメーターにデータを書き込みます。 その後**AppendChunk**でを呼び出す、**パラメーター**オブジェクト パラメーターの既存のデータに追加します。 **AppendChunk**のすべてのパラメーターのデータの null 値を渡す呼び出し破棄します。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Field オブジェクト](../../../ado/reference/ado-api/field-object.md)|[パラメーター オブジェクト](../../../ado/reference/ado-api/parameter-object.md)|  
  
## <a name="see-also"></a>参照  
 [AppendChunk と GetChunk メソッドの例 (VB)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vb.md)   
 [AppendChunk と GetChunk メソッドの例 (vc++)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vc.md)   
 [属性プロパティ (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)   
 [GetChunk メソッド (ADO)](../../../ado/reference/ado-api/getchunk-method-ado.md)

