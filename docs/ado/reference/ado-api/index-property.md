---
description: Index プロパティ
title: Index プロパティ |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset21::Index
helpviewer_keywords:
- Index property
ms.assetid: 1c79e271-21ec-41a8-8163-c5e89f0001a7
author: rothja
ms.author: jroth
ms.openlocfilehash: 80d15588279e584ec4d63d4336239952f22405cc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443464"
---
# <a name="index-property"></a>Index プロパティ
[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトに現在適用されているインデックスの名前を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 インデックスの名前を設定するか、 **文字列** 値を返します。  
  
## <a name="remarks"></a>解説  
 **Index**プロパティによって指定されたインデックスは、**レコードセット**オブジェクトの基になるベーステーブルで既に宣言されている必要があります。 つまり、インデックスは、ADOX [index](../../../ado/reference/adox-api/index-object-adox.md) オブジェクトとして、またはベーステーブルが作成されたときに、プログラムによって宣言されている必要があります。  
  
 インデックスを設定できない場合は、実行時エラーが発生します。 **Index**プロパティは、次の条件下では設定できません。  
  
-   [WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)または**RecordsetChangeComplete**イベントハンドラー内。  
  
-   **レコードセット**がまだ操作を実行している ( [State](../../../ado/reference/ado-api/state-property-ado.md)プロパティによって決定できる) 場合はです。  
  
-   [フィルタープロパティを](../../../ado/reference/ado-api/filter-property.md)使用して**レコードセット**にフィルターが設定されている場合は。  
  
 **レコード**セットが閉じられていても、**レコード**セットが正常に開かれない場合、または基になるプロバイダーがインデックスをサポートしていない場合にインデックスを使用できない場合は、**インデックス**プロパティをいつでも正常に設定できます。  
  
 インデックスを設定できる場合は、現在の行の位置が変更される可能性があります。 これにより、 [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)プロパティが更新され、 **WillChangeRecordset**、 **RecordsetChangeComplete**、 [MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md) [の各](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)イベントが起動されます。  
  
 インデックスを設定でき、 [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) プロパティが **adlockpessimistic** または **adlockpessimistic**の場合、暗黙的な [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) 操作が実行されます。 これにより、現在のグループと影響を受けるグループが解放されます。 既存のフィルターがすべて解放され、現在の行の位置が、並べ替えられた **レコードセット**の最初の行に変更されます。  
  
 **Index**プロパティは、 [Seek](../../../ado/reference/ado-api/seek-method.md)メソッドと組み合わせて使用されます。 基になるプロバイダーが **Index** プロパティをサポートしていないため、 **Seek** メソッドを使用する場合は、代わりに [Find](../../../ado/reference/ado-api/find-method-ado.md) メソッドを使用することを検討してください。 **レコードセット**オブジェクトが[サポート](../../../ado/reference/ado-api/supports-method.md)**(adindex)** メソッドを使用したインデックスをサポートしているかどうかを判断します。  
  
 組み込みの **インデックス** プロパティは、動的 [最適化](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) プロパティに関連付けられていませんが、両方ともインデックスを処理します。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Seek メソッドと Index プロパティの例 (VB)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [Index オブジェクト (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)   
 [Seek メソッド](../../../ado/reference/ado-api/seek-method.md)
