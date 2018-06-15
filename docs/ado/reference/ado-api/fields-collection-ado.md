---
title: フィールドのコレクション (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Fields
- Recordset15::Fields
- _Record::Fields
helpviewer_keywords:
- Fields collection [ADO]
ms.assetid: 7c371474-b88f-4730-afa5-44163a0488d5
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2641f21c0726d010990964d84f89148814e866c9
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35278491"
---
# <a name="fields-collection-ado"></a>Fields コレクション (ADO)
すべてが含まれています、[フィールド](../../../ado/reference/ado-api/field-object.md)のオブジェクト、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)または[レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクト。  
  
## <a name="remarks"></a>コメント  
 A **Recordset**オブジェクトには、**フィールド**コレクションから成る**フィールド**オブジェクト。 各**フィールド**オブジェクト内の列に対応して、 **Recordset**です。 設定できます、**フィールド**開く前にコレクション、**レコード セット**を呼び出して、[更新](../../../ado/reference/ado-api/refresh-method-ado.md)コレクション メソッド。  
  
> [!NOTE]
>  参照してください、**フィールド**オブジェクトの使用方法の詳細な説明のトピック**フィールド**オブジェクト。  
  
 **フィールド**コレクションが、[追加](../../../ado/reference/ado-api/append-method-ado.md)仮を作成し、追加するメソッド、**フィールド**オブジェクトをコレクション、および**を更新**メソッドの追加や削除を終了します。  
  
 A**レコード**オブジェクトにインデックスを作成できる 2 つの特別なフィールドには[FieldEnum](../../../ado/reference/ado-api/fieldenum.md)定数。 定数は 1 つの既定のストリームを含むフィールドにアクセスする、**レコード**、他の絶対 URL 文字列を含むフィールドにアクセスして、**レコード**です。  
  
 特定のプロバイダー (たとえば、 [Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)) 設定が、**フィールド**使用可能なフィールドのサブセットを使用してコレクション、**レコード**または**Recordset**です。 最初に名前で参照またはコードによってインデックス設定されるまで、他のフィールドは、コレクションに追加されません。  
  
 存在しないフィールドの名前で参照しようとする場合、新しい**フィールド**オブジェクトに追加されます、**フィールド**使用して、コレクション、[ステータス](../../../ado/reference/ado-api/status-property-ado-field.md)の**adFieldPendingInsert**です。 呼び出すと[更新](../../../ado/reference/ado-api/update-method.md)ADO は、プロバイダーによって許可された場合に、データ ソース内の新しいフィールドを作成ができます。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [フィールド コレクションのプロパティ、メソッド、およびイベント](../../../ado/reference/ado-api/fields-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)
