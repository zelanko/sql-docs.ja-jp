---
title: リシェイプ Name プロパティ-動的 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Reshape Name property [ADO]
ms.assetid: 690229d1-46cc-42e6-a57d-4438251fe248
author: rothja
ms.author: jroth
ms.openlocfilehash: 490a69a022c2098de1dc4ade67af484b6e50131a
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82756506"
---
# <a name="reshape-name-property-dynamic-ado"></a>Reshape Name プロパティ - 動的 (ADO)
[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトの名前を指定します。  
  
## <a name="return-values"></a>戻り値  
 **レコードセット**の名前を表す**文字列**値を返します。  
  
## <a name="remarks"></a>解説  
 名前は、接続の間、または**レコードセット**が閉じられるまで保持されます。  
  
 "**リシェイプ名**" プロパティは、主に、OLE DB サービスプロバイダー[用の Microsoft データ整形サービス](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)の再整形機能と共に使用することを目的としています。 名前は、再整形に参加するために一意である必要があります。  
  
 このプロパティは読み取り専用ですが、**レコードセット**の作成時に間接的に設定できます。 たとえば、Shape コマンドの句によって**レコードセット**が作成され、AS キーワードを使用してエイリアス名が指定され**て**いる場合、エイリアスは "**リシェイプ name** " プロパティに割り当てられます。 エイリアスが宣言されていない場合、"**リシェイプ name** " プロパティには、データシェイプサービスによって生成される一意の名前が割り当てられます。 エイリアス名が既存の**レコードセット**の名前と同じである場合、いずれかのレコードセットが解放されるまで、いずれの**レコードセット**もリシェイプできません。 既定の動作を変更するには、ADO 接続の "[リシェイプ name](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md) " プロパティで一意の名前を**True**に設定します。 このプロパティを設定すると、データシェイプサービスは、必要に応じてユーザー割り当て名を変更して一意性を保証します。 リシェイプの詳細については、「 [OLE DB 用の Microsoft データ整形サービス (ADO サービスプロバイダー)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)」を参照してください。  
  
 Shape コマンドで**レコードセット**を参照する場合、またはデータシェイプサービスによって生成されたために名前がわからない場合は、"**リシェイプ name** " プロパティを使用します。 その場合は、"**リシェイプ Name** " プロパティによって返される文字列にコマンドを連結して、SHAPE コマンドを生成できます。  
  
 **リシェイプ Name**は、[カーソル位置](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティが**adUseClient**に設定されている場合に、**レコードセット**オブジェクトの[Properties](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションに追加される動的プロパティです。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [OLE DB 用の Microsoft データ整形サービス (ADO サービスプロバイダー)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)   
 [一般的なシェイプコマンド](../../../ado/guide/data/shape-commands-in-general.md)   
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
