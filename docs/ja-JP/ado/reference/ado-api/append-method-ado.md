---
title: Append メソッド (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _DynaCollection::Append
helpviewer_keywords:
- Append method [ADO]
ms.assetid: f8a9bbed-ba9c-4698-945d-317ad22d2e92
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff92549b842fbc180d63e52e9576b857c476ecd3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="append-method-ado"></a>Append メソッド (ADO)
オブジェクトをコレクションに追加します。 コレクションが場合[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)、新しい[フィールド](../../../ado/reference/ado-api/field-object.md)をコレクションに追加する前に、オブジェクトを作成できます。  
  
## <a name="syntax"></a>構文  
  
```  
  
collection.Append object  
fields.Append Name, Type, DefinedSize, Attrib, FieldValue  
```  
  
#### <a name="parameters"></a>パラメーター  
 *collection*  
 コレクション オブジェクトです。  
  
 *fields*  
 A**フィールド**コレクション。  
  
 *オブジェクト*  
 追加するオブジェクトを表すオブジェクト変数です。  
  
 *名前*  
 A**文字列**の新しい名前を表す値**フィールド**オブジェクト、および同じ名であり、他のオブジェクトではない必要があります*フィールド*です。  
  
 *型*  
 A[格納](../../../ado/reference/ado-api/datatypeenum.md)値、既定値は**adEmpty**、新しいフィールドのデータ型を指定します。 ADO では、次のデータ型はサポートされていないと、必要がありますいないときに使用を追加する新しいフィールド、[レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md):**追加**、**しようとする**、 **adVariant**です。  
  
 *DefinedSize*  
 省略可。 A**長い**文字または新しいフィールドのバイト単位で定義されたサイズを表す値です。 このパラメーターの既定値はから派生*型*です。 指定されたフィールド、 *DefinedSize* 255 バイトは、可変長の列として扱われます。 より大きい。 既定の*DefinedSize*は指定されていません。  
  
 *attrib*  
 省略可。 A [FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md)値、既定値は**adFldDefault**、新しいフィールドの属性を指定します。 この値が指定されていない場合から派生した属性が、フィールドが含まれます*型*です。  
  
 *FieldValue*  
 省略可。 A**バリアント**新しいフィールドの値を表すです。 指定されていない場合は、null 値を持つフィールドが追加されます。  
  
## <a name="remarks"></a>解説  
  
## <a name="parameters-collection"></a>Parameters コレクション  
 設定する必要があります、[型](../../../ado/reference/ado-api/type-property-ado.md)のプロパティ、[パラメーター](../../../ado/reference/ado-api/parameter-object.md)オブジェクトに追加する前に、[パラメーター](../../../ado/reference/ado-api/parameters-collection-ado.md)コレクション。 可変長データ型を選択する場合、必要がありますも設定する、[サイズ](../../../ado/reference/ado-api/size-property-ado-parameter.md)プロパティを 0 より大きい値にします。  
  
 自分でパラメーターを記述する、プロバイダーへの呼び出しを最小限にし、ストアド プロシージャまたはパラメーター化クエリを使用する場合のパフォーマンスが向上します。 ただし、ストアド プロシージャに関連付けられているまたは通話を行うクエリをパラメーター化されたパラメーターのプロパティを知っている必要があります。  
  
 使用して、 [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md)メソッドを作成**パラメーター**適切なプロパティの設定および使用するオブジェクトを**Append**に追加する方法、 [パラメーター](../../../ado/reference/ado-api/parameters-collection-ado.md)コレクション。 これにより設定およびパラメーターについては、プロバイダーを呼び出さずにパラメーター値を取得できます。 手動で読み込むこのメソッドを使用する場合は、パラメーター情報を提供しないプロバイダーを作成している必要があります、**パラメーター**パラメーターを使用するためにコレクション。  
  
## <a name="fields-collection"></a>Fields コレクション  
 *FieldValue*パラメーターは、追加する場合にのみ有効です、**フィールド**オブジェクトを[レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクトしないように、 **Recordset**オブジェクト。 **レコード**オブジェクト、フィールドを追加し、同時に値を提供することができます。 **Recordset**オブジェクトの中にフィールドを作成する必要があります、**レコード セット**、終了して開き、**レコード セット**フィールドに値を割り当てるとします。  
  
> [!NOTE]
>  新しい**フィールド**に追加されたオブジェクト、**フィールド**のコレクション、**レコード**オブジェクト、[値](../../../ado/reference/ado-api/value-property-ado.md)プロパティを設定する必要がありますその他の前に**フィールド**プロパティを指定できます。 最初の特定の値、**値**プロパティが割り当てられている必要がありますと[更新](../../../ado/reference/ado-api/update-method.md)上、**フィールド**と呼ばれるコレクション。 などの他のプロパティ、[型](../../../ado/reference/ado-api/type-property-ado.md)または[属性](../../../ado/reference/ado-api/attributes-property-ado.md)アクセスできます。 **フィールド**次のデータ型のオブジェクト (**格納**) に追加することはできません、**フィールド**コレクションと、エラーが発生して: **adArray**、**adChapter**、 **adEmpty**、 **adPropVariant**、および**adUserDefined**です。 また、次のデータ型が ADO でサポートされていません:**追加**、**しようとする**、および**エラー**です。 これらの種類について、追加したときにエラーが発生ありませんが、使用量がメモリ リークをなど、予期しない結果を生成できます。  
  
## <a name="recordset"></a>レコードセット  
 設定しない場合、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティを呼び出す前に、 **Append**メソッド、 **CursorLocation**に設定されます**adUseClient** ([CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md)値) ときに自動的に、[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)のメソッド、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトが呼び出されるとします。  
  
 実行時エラーが発生、 **Append**メソッドが、**フィールド**の開いているコレクション**レコード セット**、または、**レコード セット**ここで、 [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)プロパティが設定されています。 フィールドを追加できるのみ、 **Recordset**が開かれていないと、データ ソースに接続されていません。 これは、通常、ケースと、**レコード セット**でオブジェクトを作成、 [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md)メソッドまたはオブジェクト変数に割り当てられました。  
  
## <a name="record"></a>レコード  
 場合、実行時エラーは発生しませんが、 **Append**でメソッドが呼び出さ、**フィールド**の開いているコレクション**レコード**です。 新しいフィールドに追加されます、**フィールド**のコレクション、**レコード**オブジェクト。 場合、**レコード**から派生した、**レコード セット**に、新しいフィールドは表示されません、**フィールド**のコレクション、 **Recordset**オブジェクト。  
  
 存在しないフィールドを作成およびに追加できる、**フィールド**フィールド オブジェクトをコレクションに既に存在していた場合、値を割り当てることによってコレクション。 自動的に作成し、追加の割り当てをトリガーする、**フィールド**オブジェクト、および、割り当てが完了します。  
  
 追加した後、**フィールド**を**フィールド**のコレクション、**レコード**オブジェクトを呼び出して、**更新**のメソッド、**フィールド**コレクションに変更を保存します。  
  
## <a name="applies-to"></a>適用対象  
  
- [Fields コレクション (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
- [Parameters コレクション (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)  
  
## <a name="see-also"></a>参照  
 [追加と CreateParameter メソッドの例 (VB)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vb.md)   
 [追加する方法の例を CreateParameter (vc++)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vc.md)   
 [CreateParameter メソッド (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Delete メソッド (ADO フィールドのコレクション)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete メソッド (ADO パラメーターのコレクション)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete メソッド (ADO レコード セット)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Update メソッド](../../../ado/reference/ado-api/update-method.md)
