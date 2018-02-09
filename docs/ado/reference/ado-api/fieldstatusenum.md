---
title: "FieldStatusEnum |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- FieldStatusEnum
helpviewer_keywords:
- FieldStatusEnum enumeration [ADO]
ms.assetid: e06da1e2-303f-41b2-a3b0-61e233da152c
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e04f98c5691a66b02a4c5daa8d745f529a9820e0
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="fieldstatusenum"></a>FieldStatusEnum
指定します、[ステータス](../../../ado/reference/ado-api/status-property-ado-field.md)の[フィールド オブジェクト](../../../ado/reference/ado-api/field-object.md)です。  
  
 **AdFieldPending\*** 値は、操作を設定できる状態の原因となったはその他の状態の値と組み合わせることを示します。  
  
|定数|[値]|Description|  
|--------------|-----------|-----------------|  
|**adFieldAlreadyExists**|26|指定したフィールドが既に存在することを示します。|  
|**adFieldBadStatus**|12|無効な状態値は、OLE DB プロバイダーに ADO から送信されたことを示します。 考えられる原因は、OLE DB 1.0 または 1.1 プロバイダーは、または、不適切な組み合わせの[値](../../../ado/reference/ado-api/value-property-ado.md)と[ステータス](../../../ado/reference/ado-api/status-property-ado-field.md)です。|  
|**adFieldCannotComplete**|20|によって、サーバーの URL が指定されていることを示します[ソース](../../../ado/reference/ado-api/source-property-ado-record.md)操作を完了できませんでした。|  
|**adFieldCannotDeleteSource**|23|示します、移動操作中にツリーまたはサブツリーを新しい場所に移動されたソースを削除できませんでした。|  
|**adFieldCantConvertValue**|2|フィールドを取得またはデータを失うことがなく保存できないことを示します。|  
|**adFieldCantCreate**|7|プロバイダーが許可されているフィールドの数) などの制限を超えたためには、フィールドを追加できませんでしたを示します。|  
|**adFieldDataOverflow**|6|プロバイダーから返されるデータがフィールドのデータ型をオーバーフローしたことを示します。|  
|**adFieldDefault**|13|フィールドの既定値がデータを設定するときに使用されることを示します。|  
|**adFieldDoesNotExist**|16|指定されたフィールドが存在しないことを示します。|  
|**adFieldIgnore**|15|このフィールドが、ソースで値のデータを設定時にスキップされたことを示します。 プロバイダーには、値は設定されません。|  
|**adFieldIntegrityViolation**|10|計算された、または派生エンティティであるため、フィールドを変更できないことを示します。|  
|**adFieldInvalidURL**|17|データ ソースの URL に無効な文字が含まれていることを示します。|  
|**adFieldIsNull**|3|プロバイダーに型 VT_ のバリアント値が返されることと、フィールドが空でないことを示します。|  
|**adFieldOK**|0|既定値です。 フィールドが正常に追加または削除することを示します。|  
|**adFieldOutOfSpace**|22|プロバイダーが、移動が完了またはコピー操作に十分な記憶域を入手することであることを示します。|  
|**adFieldPendingChange**|0x40000|いずれかを示すフィールドを削除し、もう一度追加、おそらく別のデータ型、またはを以前の状態に配置すると、フィールドの値の**adfieldok で**が変更されました。 フィールドの最終的な形式の変更は、[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)の後にコレクション、[更新](../../../ado/reference/ado-api/update-method.md)メソッドが呼び出されます。|  
|**adFieldPendingDelete**|0x20000|示します、**削除**操作の原因となった状態を設定します。 削除にマークされているフィールド、**フィールド**の後にコレクション、**更新**メソッドが呼び出されます。|  
|**adFieldPendingInsert**|0x10000|示します、 **Append**操作の原因となった状態を設定します。 **フィールド**に追加するがマークされて、**フィールド**の後にコレクション、**更新**メソッドが呼び出されます。|  
|**adFieldPendingUnknown**|0x80000|プロバイダーがどのような原因となった操作フィールドの状態を設定するを判断できないことを示します。|  
|**adFieldPendingUnknownDelete**|0x100000|プロバイダーがどのような操作の原因となったフィールドの状態を設定して、フィールドがから削除されることを判断できないことを示す、**フィールド**の後にコレクション、**更新**メソッドが呼び出されます。|  
|**adFieldPermissionDenied**|9|読み取り専用として定義されているため、フィールドを変更できないことを示します。|  
|**adFieldReadOnly**|24|読み取り専用で、データ ソースのフィールドが定義されていることを示します。|  
|**adFieldResourceExists**|19|プロバイダーがオブジェクトは、宛先 URL に既に存在して、オブジェクトを上書きすることはできませんので、操作を実行できなかったことを示します。|  
|**adFieldResourceLocked**|18|プロバイダーがデータ ソースが 1 つ以上の他のアプリケーションまたはプロセスによってロックされているため、操作を実行できなかったことを示します。|  
|**adFieldResourceOutOfScope**|25|送信元または送信先の URL が、現在のレコードのスコープ外にあることを示します。|  
|**adFieldSchemaViolation**|11|値がフィールドのデータ ソース スキーマの制約に違反したことを示します。|  
|**adFieldSignMismatch**|5|プロバイダーによって返されるデータ値は署名されましたが、ADO フィールドの値のデータ型が署名されていないことを示します。|  
|**adFieldTruncated**|4|データ ソースから読み取るときに、可変長のデータが切り捨てられたことを示します。|  
|**adFieldUnavailable**|8|あるプロバイダーを特定できませんでした、値、データ ソースからの読み取り時に示します。 たとえば、行が作成した、列の既定値が使用可能なおよび新しい値が指定されていません。|  
|**adFieldVolumeNotFound**|21|プロバイダーが URL で示されている記憶域ボリュームを特定することであることを示します。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 これらの定数には、対応する ADO/WFC はありません。  
  
## <a name="applies-to"></a>適用対象  
 [Status プロパティ (ADO Field)](../../../ado/reference/ado-api/status-property-ado-field.md)
