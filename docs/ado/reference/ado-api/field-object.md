---
title: "オブジェクトのフィールド |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
- Field
helpviewer_keywords:
- Field object [ADO]
ms.assetid: b10a72fc-3c4b-4186-a70b-993dc9f7a092
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f876e76b29dbc2436d6d1dba317c5035ebbc9ca1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="field-object"></a>Field オブジェクト
一般的なデータ型のデータの列を表します。  
  
## <a name="remarks"></a>解説  
 各**フィールド**オブジェクト内の列に対応して、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。 使用する、[値](../../../ado/reference/ado-api/value-property-ado.md)プロパティ**フィールド**オブジェクトを設定または現在のレコードのデータを取得します。 機能によって、プロバイダーが公開して一部のコレクション、メソッド、またはプロパティの**フィールド**オブジェクトを使用できない可能性があります。  
  
 コレクション、メソッド、およびプロパティの使用、**フィールド**オブジェクトを次を行うことができます。  
  
-   フィールドの名前を返す、[名前](../../../ado/reference/ado-api/name-property-ado.md)プロパティです。  
  
-   表示または変更が含まれるフィールドのデータ、**値**プロパティです。 **値**の既定のプロパティは、**フィールド**オブジェクト。  
  
-   基本的な特性を含むフィールドを返す、[型](../../../ado/reference/ado-api/type-property-ado.md)、[精度](../../../ado/reference/ado-api/precision-property-ado.md)、および[NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md)プロパティです。  
  
-   フィールドの宣言されたサイズを返します、 [DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)プロパティです。  
  
-   特定のフィールドに、データの実際のサイズを返す、 [ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md)プロパティです。  
  
-   特定のフィールドがサポートされる機能の種類を判断、[属性](../../../ado/reference/ado-api/attributes-property-ado.md)プロパティおよび[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクション。  
  
-   長のバイナリまたは文字長のデータを含むフィールドの値を操作、 [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md)と[GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md)メソッドです。  
  
-   プロバイダーは、バッチ更新をサポートする場合は、フィールドの値の不一致を解決でバッチを更新中に、 [OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md)と[UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)プロパティです。  
  
 すべてのメタデータ プロパティ (**名前**、**型**、 **DefinedSize**、**精度**、および**NumericScale**) 開く前に使用できるは、**フィールド**オブジェクトの**Recordset**です。 その時点でそれらを設定することは、フォームを動的に構築するために便利です。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [フィールド オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/ado-api/field-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Fields コレクション (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [プロパティのコレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)

