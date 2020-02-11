---
title: AbsolutePosition プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::AbsolutePosition
helpviewer_keywords:
- AbsolutePosition property [ADO]
ms.assetid: 79f8ee5e-fc70-46d8-8c29-ebf943c66592
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5b9795f962d0ead59a8d4f993e799a0ae4e2b750
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67921692"
---
# <a name="absoluteposition-property-ado"></a>AbsolutePosition プロパティ (ADO)
[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトの現在のレコードの位置を表す序数を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 32ビットコードの場合、は、1から**レコードセット**オブジェクト ([RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)) のレコード数までの**Long 型**の値を設定または返します。または、 [positionenum](../../../ado/reference/ado-api/positionenum.md)値の1つを返します。  
  
 64ビットコードの場合は、64ビット値を格納するためにに用意されているデータ型を使用します。 たとえば、Long または DBORDINAL などの64ビット長の別の値を使用することができます。 **Positionenum**値は、32ビットの長さに制限されているため、使用しないでください。  
  
## <a name="remarks"></a>解説  
 ADO では、 **AbsolutePosition**プロパティを設定するために、使用している OLE DB プロバイダーが[IRowsetLocate: IRowset](https://msdn.microsoft.com/library/windows/desktop/ms721190.aspx)インターフェイスを実装する必要があります。  
  
 順方向専用カーソルまたは動的カーソルで開かれた**レコードセット**の**AbsolutePosition**プロパティにアクセスすると、エラー **adErrFeatureNotAvailable**が発生します。 その他の種類のカーソルでは、OLE DB プロバイダーが**IRowsetScroll: IRowsetLocate**インターフェイスをサポートしている限り、正しい位置が返されます。 プロバイダーで**IRowsetScroll**インターフェイスがサポートされていない場合、プロパティは**adposunknown**に設定されます。 **IRowsetScroll**がサポートされているかどうかを判断するには、プロバイダーのドキュメントを参照してください。  
  
 **AbsolutePosition**プロパティを使用して、レコード**セット**オブジェクトの序数位置に基づいてレコードに移動するか、現在のレコードの序数位置を決定します。 このプロパティを使用できるようにするには、プロバイダーが適切な機能をサポートしている必要があります。  
  
 [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)プロパティと同様に、 **AbsolutePosition**は1から始まる、現在のレコードが**レコードセット**内の最初のレコードの場合は1になります。 レコード**セット**オブジェクト内のレコードの合計数は、 [RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)プロパティから取得できます。  
  
 **AbsolutePosition**プロパティを設定すると、現在のキャッシュ内のレコードの場合でも、ADO は、指定したレコードで始まる新しいレコードのグループを使用してキャッシュを再読み込みします。 このグループのサイズは、 [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)プロパティによって決定されます。  
  
> [!NOTE]
>  **AbsolutePosition**プロパティは、サロゲートレコード番号として使用しないでください。 前のレコードを削除すると、特定のレコードの位置が変更されます。 また、**レコードセット**オブジェクトが再クエリまたは再度開かれた場合、特定のレコードの**AbsolutePosition**が同じであることは保証されません。 ブックマークは、特定の位置を保持して返すための推奨される方法であり、すべての種類の**レコードセット**オブジェクトに対して配置する唯一の方法です。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [AbsolutePosition およびカーソルのプロパティの例 (VB)](../../../ado/reference/ado-api/absoluteposition-and-cursorlocation-properties-example-vb.md)   
 [AbsolutePosition およびカーソルのプロパティの例 (VC + +)](../../../ado/reference/ado-api/absoluteposition-and-cursorlocation-properties-example-vc.md)   
 [AbsolutePage プロパティ (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [RecordCount プロパティ (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)
