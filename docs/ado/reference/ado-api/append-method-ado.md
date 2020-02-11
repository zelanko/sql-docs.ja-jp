---
title: Append メソッド (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _DynaCollection::Append
helpviewer_keywords:
- Append method [ADO]
ms.assetid: f8a9bbed-ba9c-4698-945d-317ad22d2e92
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 17fa0ff30e8dcdbf7ea67080f17c3e066bba8605
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67920670"
---
# <a name="append-method-ado"></a>Append メソッド (ADO)
オブジェクトをコレクションに追加します。 コレクションが[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)の場合は、コレクションに追加する前に新しい[Field](../../../ado/reference/ado-api/field-object.md)オブジェクトを作成できます。  
  
## <a name="syntax"></a>構文  
  
```  
  
collection.Append object  
fields.Append Name, Type, DefinedSize, Attrib, FieldValue  
```  
  
#### <a name="parameters"></a>パラメーター  
 *表す*  
 コレクションオブジェクト。  
  
 *フィールド*  
 **フィールド**コレクション。  
  
 *素材*  
 追加するオブジェクトを表すオブジェクト変数。  
  
 *名前*  
 新しい**フィールド**オブジェクトの名前を含む**文字列**値。*フィールド*内の他のオブジェクトと同じ名前にすることはできません。  
  
 *Type*  
 新しいフィールドのデータ型を指定する[DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)値 (既定値は**adEmpty**)。 次のデータ型は ADO ではサポートされていません。また、[レコードセットオブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)に新しいフィールドを追加するときには使用しないでください。この**ようなデータ**型は、実行**ディスパッチ**、指定されていない、 **advariant**です。  
  
 *DefinedSize*  
 省略可能。 新しいフィールドの定義されたサイズ (文字数またはバイト数) を表す**Long 型**の値。 このパラメーターの既定値は、*型*から派生します。 255*バイトを超える値が*設定されているフィールドは、可変長列として扱われます。 既定値は、*指定されてい*ません。  
  
 *Attrib (英語の可能性あり)*  
 省略可能。 新しいフィールドの属性を指定する[FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md)値 (既定値は**Adflddefault**)。 この値が指定されていない場合、フィールドには*型*から派生した属性が格納されます。  
  
 *FieldValue*  
 省略可能。 新しいフィールドの値を表す**バリアント**。 指定しない場合、フィールドには null 値が付加されます。  
  
## <a name="remarks"></a>解説  
  
## <a name="parameters-collection"></a>Parameters コレクション  
 [Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md)コレクションに追加する前に、 [Parameter](../../../ado/reference/ado-api/parameter-object.md)オブジェクトの[Type](../../../ado/reference/ado-api/type-property-ado.md)プロパティを設定する必要があります。 可変長データ型を選択する場合は、 [Size](../../../ado/reference/ado-api/size-property-ado-parameter.md)プロパティも0より大きい値に設定する必要があります。  
  
 パラメーターの記述によってプロバイダーの呼び出しが最小化されるため、ストアドプロシージャまたはパラメーター化クエリを使用すると、パフォーマンスが向上します。 ただし、呼び出すストアドプロシージャまたはパラメーター化クエリに関連付けられているパラメーターのプロパティを把握しておく必要があります。  
  
 [Createparameter](../../../ado/reference/ado-api/createparameter-method-ado.md)メソッドを使用して、適切なプロパティ設定を持つ**パラメーター**オブジェクトを作成し、 **Append**メソッドを使用して[Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md)コレクションに追加します。 これにより、パラメーター情報のプロバイダーを呼び出さなくても、パラメーター値を設定して返すことができます。 パラメーター情報を提供しないプロバイダーに書き込む場合は、パラメーターを使用するために、このメソッドを使用して**パラメーター**コレクションを手動で設定する必要があります。  
  
## <a name="fields-collection"></a>Fields コレクション  
 *FieldValue*パラメーターが有効なのは、レコード**セット**オブジェクトではなく、[レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクトに**フィールド**オブジェクトを追加する場合のみです。 **レコード**オブジェクトを使用すると、フィールドを追加し、同時に値を指定できます。 **レコード**セットオブジェクトを使用する場合は、**レコードセット**が閉じられている間にフィールドを作成し、**レコードセット**を開き、フィールドに値を割り当てる必要があります。  
  
> [!NOTE]
>  **レコード**オブジェクトの**Fields**コレクションに追加された新しい**Field**オブジェクトの場合は、他の**フィールド**プロパティを指定する前に、 [Value](../../../ado/reference/ado-api/value-property-ado.md)プロパティを設定する必要があります。 最初に、**値**プロパティの特定の値が割り当てられており、という**フィールド**コレクションで[更新](../../../ado/reference/ado-api/update-method.md)されている必要があります。 その後、[型](../../../ado/reference/ado-api/type-property-ado.md)や[属性](../../../ado/reference/ado-api/attributes-property-ado.md)などの他のプロパティにアクセスできます。 次のデータ型 (**DataTypeEnum**) の**フィールド**オブジェクトを**フィールド**コレクションに追加することはできません。エラーが発生します: **adarray**、 **adarray**、 **adEmpty**、 **adpropvariant**、および**adarray**。 また、ADO で**は、次**のデータ型はサポートされていません: の形式で**は、実行****できません。** これらの型では、追加されてもエラーは発生しませんが、メモリリークなどの予期しない結果が発生する可能性があります。  
  
## <a name="recordset"></a>レコードセット  
 **追加**メソッドを呼び出す前に[[カーソルの場所](../../../ado/reference/ado-api/cursorlocation-property-ado.md)] プロパティを設定しなかった場合、[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトの[Open](../../../ado/reference/ado-api/open-method-ado-recordset.md)メソッドが呼び出されると、**カーソル位置**は**adUseClient** ([カーソル位置列挙](../../../ado/reference/ado-api/cursorlocationenum.md)値) に自動的に設定されます。  
  
 開いている**レコードセット**の**Fields**コレクションまたは[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)プロパティが設定されている**レコードセット**で**Append**メソッドが呼び出されると、実行時エラーが発生します。 フィールドを追加できるのは、開かれておらず、まだデータソースに接続されていない**レコードセット**だけです。 これは、通常、**レコードセット**オブジェクトが[CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md)メソッドを使用して、またはオブジェクト変数に割り当てられている場合に当てはまります。  
  
## <a name="record"></a>Record  
 開いている**レコード**の**フィールド**コレクションで**Append**メソッドが呼び出された場合、実行時エラーは発生しません。 新しいフィールドが**レコード**オブジェクトの**フィールド**コレクションに追加されます。 **レコード**がレコード**セット**から派生した場合、新しいフィールドは**レコードセット**オブジェクトの**フィールド**コレクションに表示されません。  
  
 存在しないフィールドは、コレクションに既に存在しているかのように、フィールドオブジェクトに値を割り当てることによって作成し、**フィールド**コレクションに追加できます。 割り当てによって、 **Field**オブジェクトの自動作成と追加がトリガーされ、割り当てが完了します。  
  
 **レコード**オブジェクトの**Fields**コレクションに**フィールド**を追加した後、 **fields**コレクションの**Update**メソッドを呼び出して変更を保存します。  
  
## <a name="applies-to"></a>適用対象  
  
- [Fields コレクション (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
- [Parameters コレクション (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)  
  
## <a name="see-also"></a>参照  
 [Append および CreateParameter メソッドの例 (VB)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vb.md)   
 [Append および CreateParameter メソッドの例 (VC + +)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vc.md)   
 [CreateParameter メソッド (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Delete メソッド (ADO Fields コレクション)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete メソッド (ADO Parameters コレクション)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete メソッド (ADO Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Update メソッド](../../../ado/reference/ado-api/update-method.md)
