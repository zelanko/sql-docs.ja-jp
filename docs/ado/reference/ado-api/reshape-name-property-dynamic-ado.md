---
title: "名前のプロパティ-動的 (ADO) の形状変更 |Microsoft ドキュメント"
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
helpviewer_keywords:
- Reshape Name property [ADO]
ms.assetid: 690229d1-46cc-42e6-a57d-4438251fe248
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3b14593e427db76994976091e5916ffe49aefe82
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="reshape-name-property-dynamic-ado"></a>名前のプロパティ-動的 (ADO) の形状変更します。
名前を指定、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。  
  
## <a name="return-values"></a>戻り値  
 返します、**文字列**を表す値の名前、 **Recordset**です。  
  
## <a name="remarks"></a>解説  
 接続のまたはまでの間、名前を保持、 **Recordset**が閉じられます。  
  
 **変形名前**プロパティは、再整形の機能で使用するためのもので、主に、 [Microsoft Data Shaping Service for OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)サービス プロバイダー。 名前は、再整形に参加する一意である必要があります。  
  
 このプロパティは読み取り専用、設定することがない直接とき、 **Recordset**を作成します。 などの場合の句、図形が作成されます、**レコード セット**を使用してエイリアス名を提供し、 **AS**エイリアスが割り当てられているキーワード、**変形名前**プロパティです。 エイリアスが宣言されていない場合、**変形名前**プロパティには、データの整形を行うサービスによって生成される一意の名前が割り当てられます。 エイリアス名は、既存の名前と同じ場合**レコード セット**、どちらも**Recordset**うちの 1 つが解放されるまでに形状変更できます。 一意の名前を設定して、既定の動作を変更することができます、[変形名前](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md)プロパティを ADO 接続を**True**です。 必要に応じて、一意性を保証する場合は、割り当てられたユーザー名を変更するサービスのアクセス許可を整形するデータは、このプロパティを設定します。 形状を変更の詳細については、次を参照してください。 [OLE DB (ADO サービス プロバイダー) の Microsoft Data Shaping Service](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)です。  
  
 使用して、**変形名前**プロパティを参照するときに、**レコード セット**Shape コマンド、または Data Shaping Service によって作成されたため、名前がわからない場合。 その場合は、コマンドによって返される文字列を連結することにより図形コマンドを生成する可能性があります、**変形名前**プロパティです。  
  
 **名前の形状変更**に動的なプロパティが追加、**レコード セット**オブジェクトの[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションと、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティに設定**adUseClient**です。  
  
## <a name="applies-to"></a>適用対象  
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft データ シェイプ OLE DB (ADO サービス プロバイダー) 用サービス](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)   
 [一般的な図形コマンド](../../../ado/guide/data/shape-commands-in-general.md)   
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
