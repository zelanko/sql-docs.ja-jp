---
title: "Value プロパティ (ADO) |Microsoft ドキュメント"
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
- Field20::Value
- _Parameter::Value
helpviewer_keywords:
- Value property [ADO]
ms.assetid: 48919c74-86d4-462e-99b9-8854ceb8d683
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 17e3c9f28e42dbd70118bb29a330514a9c29e013
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="value-property-ado"></a>Value プロパティ (ADO)
割り当てられた値を示す、[フィールド](../../../ado/reference/ado-api/field-object.md)、[パラメーター](../../../ado/reference/ado-api/parameter-object.md)、または[プロパティ](../../../ado/reference/ado-api/property-object-ado.md)オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**バリアント**オブジェクトの値を示す値。 既定値によって異なります、[型](../../../ado/reference/ado-api/type-property-ado.md)プロパティです。  
  
## <a name="remarks"></a>解説  
 使用して、**値**プロパティを設定またはからデータを返す**フィールド**オブジェクト、設定またはパラメーター値を取得する**パラメーター**オブジェクト、設定またはプロパティの設定を取得するか、**プロパティ**オブジェクト。 かどうか、**値**プロパティが読み取り/書き込みまたは読み取り専用では、さまざまな要因によって異なります。 詳細については、対応するオブジェクトのトピックを参照してください。  
  
 ADO では、設定と長のバイナリ データの取得、**値**プロパティです。  
  
> [!NOTE]
>  **パラメーター**オブジェクト、ADO の読み取り、**値**プロバイダーからプロパティを 1 回だけです。 コマンドが含まれている場合、**パラメーター**が**値**プロパティが空であり、作成する、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)コマンドの最初を閉じることを確認してください、 **レコード セット**取得する前に、**値**プロパティです。 それ以外の場合、プロバイダーによって、**値**プロパティが空であるし、正しい値が格納されません。  
>   
>  新しい**フィールド**に追加されたオブジェクト、[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)のコレクション、[レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクト、**値**プロパティを設定する必要がありますその他の前に**フィールド**プロパティを指定できます。 最初の特定の値、**値**プロパティが割り当てられている必要がありますと[更新](../../../ado/reference/ado-api/update-method.md)上、**フィールド**と呼ばれるコレクション。 などの他のプロパティ、[型](../../../ado/reference/ado-api/type-property-ado.md)または[属性](../../../ado/reference/ado-api/attributes-property-ado.md)アクセスできます。  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[Field オブジェクト](../../../ado/reference/ado-api/field-object.md)|[パラメーター オブジェクト](../../../ado/reference/ado-api/parameter-object.md)|[プロパティのオブジェクト (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>参照  
 [値プロパティの例 (VB)](../../../ado/reference/ado-api/value-property-example-vb.md)   
 [値プロパティの例 (vc++)](../../../ado/reference/ado-api/value-property-example-vc.md)   

