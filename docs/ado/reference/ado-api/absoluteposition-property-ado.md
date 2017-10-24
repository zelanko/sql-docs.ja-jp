---
title: "AbsolutePosition プロパティ (ADO) |Microsoft ドキュメント"
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
- Recordset15::AbsolutePosition
helpviewer_keywords:
- AbsolutePosition property [ADO]
ms.assetid: 79f8ee5e-fc70-46d8-8c29-ebf943c66592
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9c8a31bd7b0fbf2809b09b10b2ebcb983d7c811c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="absoluteposition-property-ado"></a>AbsolutePosition プロパティ (ADO)
序数の位置を示す、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトの現在のレコードです。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 32 ビット コードの場合は、設定または取得、**長い**値を 1 ~ 内のレコードの数、**レコード セット**オブジェクト ([RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)) のいずれかを返しますまたは、 [PositionEnum](../../../ado/reference/ado-api/positionenum.md)値。  
  
 64 ビット コードでは、64 ビット値の記憶域を提供するデータ型を使用します。 たとえば、時間の長いまたは別のいずれかを使用可能性があります DBORDINAL などの 64 ビット長で値がします。 使用しないでください**PositionEnum**値を 32 ビットの長さに制限されているためです。  
  
## <a name="remarks"></a>解説  
 設定するために、 **AbsolutePosition**を使用している OLE DB プロバイダーを実装する必要がありますプロパティ、ADO、 [IRowsetLocate:IRowset](https://msdn.microsoft.com/library/windows/desktop/ms721190.aspx)インターフェイスです。  
  
 アクセス、 **AbsolutePosition**のプロパティ、**レコード セット**順方向専用で開かれるがいるか、動的カーソルが、エラーを発生させます**adErrFeatureNotAvailable**です。 OLE DB プロバイダーをサポートしている限り、他のカーソルの種類では、正しい位置が返される、 **IRowsetScroll:IRowsetLocate**インターフェイスです。 プロバイダーがサポートしていない場合、 **IRowsetScroll**インターフェイスのプロパティが**adPosUnknown**です。 サポートされているかどうかを決定する、プロバイダーのマニュアルを参照して**IRowsetScroll**です。  
  
 使用して、 **AbsolutePosition**内の序数位置に基づいて、レコードに移動するプロパティ、**レコード セット**オブジェクト、または現在のレコードの序数位置を決定します。 プロバイダーは、このプロパティを使用するための適切な機能をサポートする必要があります。  
  
 同様に、[と、AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)プロパティ、 **AbsolutePosition**は 1 に基づいており、現在のレコードが最初のレコードが 1 と等しい、 **Recordset**です。 内のレコードの合計数を取得することができます、 **Recordset**オブジェクトから、 [RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)プロパティです。  
  
 設定すると、 **AbsolutePosition**プロパティ、現在のキャッシュ内のレコードになっている場合でも ADO キャッシュに再読み込みする指定されたレコードで始まるレコードの新しいグループにします。 [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)プロパティは、このグループのサイズを決定します。  
  
> [!NOTE]
>  使用しないで、 **AbsolutePosition**サロゲート レコード番号としてのプロパティです。 前のレコードを削除すると、特定のレコードの位置を変更します。 特定のレコードと同じことが保証されていません**AbsolutePosition**場合、 **Recordset**オブジェクトを再クエリまたは再び開きます。 ブックマークが保持して、指定された位置を返すための推奨される方法でありのすべての種類の唯一の方法は、 **Recordset**オブジェクト。  
  
## <a name="applies-to"></a>適用対象  
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [AbsolutePosition と CursorLocation プロパティの例 (VB)](../../../ado/reference/ado-api/absoluteposition-and-cursorlocation-properties-example-vb.md)   
 [AbsolutePosition と CursorLocation プロパティの例 (vc++)](../../../ado/reference/ado-api/absoluteposition-and-cursorlocation-properties-example-vc.md)   
 [AbsolutePage プロパティ (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [RecordCount プロパティ (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)

