---
title: Value プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::Value
- _Parameter::Value
helpviewer_keywords:
- Value property [ADO]
ms.assetid: 48919c74-86d4-462e-99b9-8854ceb8d683
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8c7e4d42bc58321c5b650df5e8e842290094fcf4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63043697"
---
# <a name="value-property-ado"></a>Value プロパティ (ADO)

割り当てられている値を示します、[フィールド](../../../ado/reference/ado-api/field-object.md)、[パラメーター](../../../ado/reference/ado-api/parameter-object.md)、または[プロパティ](../../../ado/reference/ado-api/property-object-ado.md)オブジェクト。
  
## <a name="settings-and-return-values"></a>設定と戻り値

設定または取得を**バリアント**オブジェクトの値を示す値。 既定値に依存、[型](../../../ado/reference/ado-api/type-property-ado.md)プロパティ。
  
## <a name="remarks"></a>コメント

使用して、**値**プロパティを設定またはからデータを返す**フィールド**オブジェクト、設定またはパラメーターの値を取得する**パラメーター**オブジェクト、またはを設定またはプロパティの設定を取得**プロパティ**オブジェクト。 かどうか、**値**プロパティが読み取り/書き込みまたは読み取り専用では、多数の要因によって異なります。 詳細については、それぞれのオブジェクトのトピックを参照してください。

ADO を使用する設定と取得と長のバイナリ データ、**値**プロパティ。
  
> [!NOTE]
> **パラメーター**オブジェクト、ADO の読み取り、**値**プロバイダーからプロパティを 1 回だけです。 コマンドに含まれる場合、**パラメーター**が**値**プロパティは空であり、作成する、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)コマンドの最初に閉じることを確認します、 **レコード セット**取得する前に、**値**プロパティ。 それ以外の場合、一部のプロバイダー、**値**プロパティが空であるし、正しい値が格納されません。
> 
> 新しい**フィールド**に追加されたオブジェクト、[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)のコレクションを[レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクト、**値**プロパティを設定する必要がありますその他の前に**フィールド**プロパティを指定できます。 最初に、特定の値を**値**プロパティが割り当てられている必要がありますと[Update](../../../ado/reference/ado-api/update-method.md)上、**フィールド**という名前のコレクション。 その他のプロパティなど、[型](../../../ado/reference/ado-api/type-property-ado.md)または[属性](../../../ado/reference/ado-api/attributes-property-ado.md)アクセスできます。
  
## <a name="applies-to"></a>適用対象
  
||||  
|-|-|-|  
|[Field オブジェクト](../../../ado/reference/ado-api/field-object.md)|[Parameter オブジェクト](../../../ado/reference/ado-api/parameter-object.md)|[Property オブジェクト (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|
  
## <a name="see-also"></a>参照

[値のプロパティの例 (VB)](../../../ado/reference/ado-api/value-property-example-vb.md)
[値のプロパティの例 (vc++)](../../../ado/reference/ado-api/value-property-example-vc.md) 
