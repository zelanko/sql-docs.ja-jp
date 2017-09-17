---
title: "Microsoft データ シェイプ OLE DB (ADO サービス プロバイダー) 用サービス |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: H1Hack27Feb2017
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- providers [ADO], data shaping service for OLE DB
- data shaping service for OLE DB [ADO]
ms.assetid: 523009ce-e01b-4e2d-a7df-816d7688aff0
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3510664e97b64c36b7c1c7b42ca475194b6d01e2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="microsoft-data-shaping-service-for-ole-db-overview"></a>Microsoft データ シェイプ OLE DB の概要のサービス
> [!IMPORTANT]
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、アプリケーションでは、XML を使用する必要があります。

 OLE DB サービス プロバイダー用の Microsoft Data Shaping Service は、階層の構築をサポートしています (形) [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)データ プロバイダーからのオブジェクト。

## <a name="provider-keyword"></a>プロバイダーのキーワード
 OLE db Data Shaping Service を起動するには、接続文字列で、次のキーワードと値を指定します。

```
"Provider=MSDataShape"
```

## <a name="dynamic-properties"></a>動的プロパティ
 このサービス プロバイダーが呼び出されると、次の動的プロパティに追加、[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)のコレクション、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト。

|動的なプロパティ名|Description|
|---------------------------|-----------------|
|**一意の変形名**|示すかどうか**レコード セット**の重複する値を持つオブジェクト、**変形名前**プロパティは使用できません。 この動的プロパティは、する場合**True**され、新しい**レコード セット**は、同じユーザー指定の変形と名前で作成、既存**レコード セット**、し、新しい**レコード セット**オブジェクトのパス名は一意になるように変更します。 場合は、このプロパティは**False**され、新しい**レコード セット**は、ユーザー指定の変形と同じ名前で、既存作成**Recordset**の両方を**レコード セット**オブジェクトは同じ変形名前になります。 したがって、どちらも**Recordset**両方のレコード セットが存在する限り形状変更できます。<br /><br /> プロパティの既定値は**False**です。|
|**データ プロバイダー**|形状になる行を提供するプロバイダーの名前を示します。 プロバイダーは行を提供する使用しない場合は、この値は [なし] で指定できます。|

 接続文字列のキーワードとしての名前を指定することによって、書き込み可能な動的なプロパティを設定することもできます。 たとえば、Microsoft Visual Basic では、設定、**データ プロバイダー** "MSDASQL"を指定して動的なプロパティ。

```
Dim cn as New ADODB.Connection
cn.Open "Provider=MSDataShape;Data Provider=MSDASQL"
```

 設定またはのインデックスとしての名前を指定して動的なプロパティを取得することができますも、[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)プロパティです。 たとえば、次のコード例を取得しの現在の値を出力、**データ プロバイダー**動的プロパティは、場合、新しい値を設定 cn です。DataProvider は、"MSDataShape"に設定されています (直接または間接的に接続文字列を使用) し、接続が開かれていません。

```
Debug.Print cn.Properties("Data Provider")
cn.Properties("Data Provider") = "MSDASQL"
```

> [!NOTE]
>  動的なプロパティ、**データ プロバイダー**、開かれていないでのみ設定できる**接続**オブジェクト。 接続が開かれた後、**データ プロバイダー**プロパティが読み取り専用になります。

 データ シェイプの詳細については、次を参照してください。[データ シェイプ](../../../ado/guide/data/data-shaping-overview.md)です。

## <a name="see-also"></a>参照
 [付録 a: プロバイダー](../../../ado/guide/appendixes/appendix-a-providers.md)

