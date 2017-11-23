---
title: "AddNew メソッド (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::AddNew
- Recordset15::raw_AddNew
helpviewer_keywords: AddNew method [ADO]
ms.assetid: a9f54be9-5763-45d0-a6eb-09981b03bc08
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: b1db70bfb438d7954a5874c80631c9a72c83e7b3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="addnew-method-ado"></a>AddNew メソッド (ADO)
作成、更新可能なに対して新しいレコード[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
recordset.AddNew FieldList, Values  
```  
  
#### <a name="parameters"></a>パラメーター  
 *レコード セット*  
 A **Recordset**オブジェクト。  
  
 *FieldList*  
 省略可。 単一の名前または名前の配列。 または、新しいレコードにフィールドの序数位置します。  
  
 *値*  
 省略可。 1 つの値。 または、新しいレコードのフィールドの値の配列。 場合*Fieldlist* 、配列は、*値*配列でなければなりませんも同じメンバーの数、それ以外のエラーが発生します。 フィールド名の順序は、各配列内のフィールド値の順序と一致する必要があります。  
  
## <a name="remarks"></a>解説  
 使用して、 **AddNew**メソッドを作成し、新しいレコードを初期化します。 使用して、[サポート](../../../ado/reference/ado-api/supports-method.md)メソッドを**adAddNew** (、 [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md)値) を現在のレコードを追加できるかどうかを確認する**Recordset**オブジェクト。  
  
 呼び出した後、 **AddNew**メソッド、新しいレコードを現在のレコードになりを呼び出した後は、[更新](../../../ado/reference/ado-api/update-method.md)メソッドです。 新しいレコードが追加されますので、 **Recordset**への呼び出し**MoveNext**の末尾を越えた移動は次の更新プログラム、 **Recordset**、 **EOF** True です。 場合、 **Recordset**オブジェクトはブックマークをサポートしていない、別のレコードに移動すると、新しいレコードにアクセスすることはできません。 カーソルの種類によってを呼び出す必要があります、 [Requery](../../../ado/reference/ado-api/requery-method.md)メソッドを新しいレコードにアクセスできるようにします。  
  
 呼び出す場合**AddNew** ADO が呼び出し、現在のレコードを編集するときに、新しいレコードを追加するときに、**更新**を保存する方法を変更し、レコードを作成して、新しいです。  
  
 動作、 **AddNew**メソッドは、の更新モードによって異なります、 **Recordset**オブジェクトとするかどうかを渡す、 *Fieldlist*と*値*引数。  
  
 *即時更新モード*(をプロバイダーに変更を書き込みます、基になるデータ ソースを呼び出すと、**更新**メソッド) を呼び出す、 **AddNew**せずメソッド引数のセット、 [EditMode](../../../ado/reference/ado-api/editmode-property.md)プロパティを**adEditAdd** (、 [EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md)値)。 プロバイダーは、ローカルでフィールド値の変更をキャッシュします。 呼び出す、**更新**メソッドは、データベースに新しいレコードをポストし、リセット、 **EditMode**プロパティを**adEditNone** (、 **EditModeEnum**値)。 渡す場合、 *Fieldlist*と*値*引数、ADO はすぐに、新しいレコードをデータベースにポスト (ありません**更新**呼び出しが必要) 以外の場合は、 **EditMode**プロパティの値は変更されません (**adEditNone**)。  
  
 *バッチ更新モード*(をプロバイダーが複数の変更をキャッシュし、呼び出した場合にのみ、基になるデータ ソースに書き込みます、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)メソッド) を呼び出す、 **AddNew**メソッドの引数を設定せず、 **EditMode**プロパティを**adEditAdd**です。 プロバイダーは、ローカルでフィールド値の変更をキャッシュします。 呼び出す、**更新**メソッドは、現在、新しいレコードを追加**Recordset**、プロバイダーが、基になるデータベースへの変更を post またはリセットしていませんが、 **EditMode****adEditNone**が呼び出されるまで、 **UpdateBatch**メソッドです。 渡す場合、 *Fieldlist*と*値*引数、ADO プロバイダーに送信、新しいレコードの記憶域のキャッシュとセット、 **EditMode**に**adEditAdd**; を呼び出す必要があります、 **UpdateBatch**メソッドを基になるデータベースに新しいレコードをポストします。  
  
## <a name="example"></a>例  
 次の例では、フィールド リストおよび含めると、フィールド一覧と値の一覧を配列として含める方法を表示する値の一覧で AddNew メソッドを使用する方法を示します。  
  
```  
create table aa1 (intf int, charf char(10))  
insert into aa1 values (2, 'aa')  
  
Dim cn As New adodb.Connection  
Dim rs As New adodb.Recordset  
Dim cmd As New adodb.Command  
  
cn.ConnectionString = "Provider=SQLOLEDB;Data Source=alexverb2;uid=sa;pwd=foo$bar00;"  
  
cn.Open  
rs.Open "select * from xxx..aa1", cn, adOpenKeyset, adLockOptimistic  
  
Dim fieldsArray(1) As Variant  
fieldsArray(0) = "intf"  
fieldsArray(1) = "charf"  
Dim values(1) As Variant  
values(0) = 4  
values(1) = "as"  
rs.AddNew fieldsArray, values  
rs.Update  
```  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [AddNew メソッドの例 (VB)](../../../ado/reference/ado-api/addnew-method-example-vb.md)   
 [AddNew メソッドの例 (VBScript)](../../../ado/reference/ado-api/addnew-method-example-vbscript.md)   
 [AddNew メソッドの例 (vc++)](../../../ado/reference/ado-api/addnew-method-example-vc.md)   
 [ただしメソッド (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [EditMode プロパティ](../../../ado/reference/ado-api/editmode-property.md)   
 [Requery メソッド](../../../ado/reference/ado-api/requery-method.md)   
 [メソッドをサポートしています](../../../ado/reference/ado-api/supports-method.md)   
 [Update メソッド](../../../ado/reference/ado-api/update-method.md)   
 [UpdateBatch メソッド](../../../ado/reference/ado-api/updatebatch-method.md)
