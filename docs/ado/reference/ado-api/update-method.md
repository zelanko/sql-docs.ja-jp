---
title: Update メソッド |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Update
helpviewer_keywords:
- Update method [ADO]
ms.assetid: 6b2a9c31-1a7e-40db-8a53-30720d0f6cc1
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2c0a5cd4e12848ecdec7c3c5168b6106dd95215c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="update-method"></a>Update メソッド
現在の行に加えたあらゆる変更を保存、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト、または[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)のコレクション、[レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
recordset.Update Fields, Values  
record.Fields.Update  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Fields*  
 省略可。 A**バリアント**、単一の名前を表す、または**バリアント**名または変更するフィールドの序数位置を表す配列。  
  
 *値*  
 省略可。 A**バリアント**、単一の値を表す、または**バリアント**フィールドまたは新しいレコードのフィールドの値を表す配列。  
  
## <a name="remarks"></a>解説  
  
## <a name="recordset"></a>レコードセット  
 使用して、**更新**の現在のレコードに加えた変更を保存する方法、 **Recordset**呼び出し元からのオブジェクト、 [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)メソッドまたは内の任意のフィールド値を変更した後、既存のレコードです。 **Recordset**オブジェクトが更新をサポートする必要があります。  
  
 フィールドの値を設定するには、次のいずれかの操作を行います。  
  
-   値を割り当てる、[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクトの[値](../../../ado/reference/ado-api/value-property-ado.md)プロパティと呼び出し、**更新**メソッドです。  
  
-   フィールド名や値を引数として渡す、**更新**呼び出します。  
  
-   フィールド名の配列および値の配列を渡す、**更新**呼び出します。  
  
 フィールドと値の配列を使用する場合は、両方の配列内の要素の数が等しい必要があります。 また、フィールド名の順序では、フィールドの値の順序を一致する必要があります。 フィールドと値の順序と数が一致しない場合は、エラーが発生します。  
  
 場合、 **Recordset**オブジェクトは、バッチ更新をサポートしている、1 つまたは複数のレコードを複数の変更をキャッシュするには、ローカルで呼び出されるまで、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)メソッドです。 現在のレコードを編集または呼び出すときに、新しいレコードを追加する場合、 **UpdateBatch**メソッド、ADO の呼び出しは自動的に、**更新**する前に現在のレコードに保留中の変更を保存する方法プロバイダーにバッチ処理された変更を送信します。  
  
 レコードから移動した場合の追加または編集する呼び出しの前に、**更新**メソッド、ADO は自動的に呼び出す**更新**変更を保存します。 呼び出す必要があります、[ただし](../../../ado/reference/ado-api/cancelupdate-method-ado.md)メソッド、現在のレコードに加えられた変更を取り消すか、新しく追加されたレコードを破棄する場合。  
  
 現在のレコードを呼び出した後、**更新**メソッドです。  
  
## <a name="record"></a>レコード  
 **更新**メソッドには、追加、削除、および内のフィールドに対する更新が終了処理として、[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)のコレクション、**レコード**オブジェクト。  
  
 削除されたフィールドなど、**削除**メソッドがすぐに削除対象としてマークが、コレクション内に保持します。 **更新**を実際には、プロバイダーのコレクションからこれらのフィールドを削除するメソッドを呼び出す必要があります。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Fields コレクション (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|[Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>参照  
 [更新プログラムとただしメソッドの例 (VB)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vb.md)   
 [更新プログラムとただしメソッドの例 (vc++)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vc.md)   
 [AddNew メソッド (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [ただしメソッド (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [EditMode プロパティ](../../../ado/reference/ado-api/editmode-property.md)   
 [UpdateBatch メソッド](../../../ado/reference/ado-api/updatebatch-method.md)
