---
title: ADO を使用して、インターネットへの発行の |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, Internet publishing
- publishing to Internet [ADO]
- Internet publishing [ADO]
- urls [ADO]
ms.assetid: d399fce4-b70b-418f-8110-3deb3448863c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 642f4eb6f145b7488766688c758660521c74fa8f
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="using-ado-for-internet-publishing"></a>インターネットへの発行の ADO を使用します。
[OLE DB Provider for Internet Publishing](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md) ADO と異種データへのアクセスの具体的な例を示しています。 このセクションの例では、インターネット パブリッシング用プロバイダーを使用して特定できますは、メール ストア プロバイダーなどの異種データを他のプロバイダーと ADO を使用するときに示されている原則が生成されます。  
  
## <a name="urls"></a>URL  
 Uniform Resource Locator (Url) は、データ ソースとファイルとディレクトリの場所を指定すると、接続文字列やコマンド テキストの代わりとして使用できます。 Url を使用するには、既存の[接続](../../../ado/reference/ado-api/connection-object-ado.md)と**Recordset**オブジェクトを使用して、**レコード**と**ストリーム**オブジェクト。  
  
 Url を使用する方法の詳細については、次を参照してください。[絶対と相対 Url](../../../ado/guide/data/absolute-and-relative-urls.md)です。  
  
## <a name="record-fields"></a>レコードのフィールド  
 異種のデータや同種のデータの主な違いは、以前の行のデータ、または**レコード**、列の異なるセットを持つことができますか**フィールド**です。 同種データの場合は、各行は、同じ列のセットを持ちます。 インターネット、パブリッシング用プロバイダーに固有のフィールドの詳細については、次を参照してください。[レコードとプロバイダー提供余分なフィールド](../../../ado/guide/data/records-and-provider-supplied-fields.md)です。  
  
### <a name="appending-new-fields"></a>新しいフィールドを追加します。  
 と共に使用するいくつかの ADO オブジェクトが強化された**レコード**と**ストリーム**オブジェクト。  
  
-   [フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)コレクション[Append](../../../ado/reference/ado-api/append-method-ado.md)メソッドでは、作成し、追加、[フィールド](../../../ado/reference/ado-api/field-object.md)コレクションにオブジェクトの値を指定できますも、**フィールド**.  
  
-   [更新](../../../ado/reference/ado-api/update-method.md)メソッドが追加またはコレクションにフィールドの削除を終了します。  
  
-   ショートカットと代替手段として、 **Append**メソッド、未定義または前に削除されたフィールドに値を割り当てることでフィールドを作成することができます。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [OLE DB Provider for Internet Publishing](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md)  
  
-   [インターネットへの発行のシナリオ](../../../ado/guide/data/internet-publishing-scenario.md)  
  
-   [絶対 URL と相対 URL](../../../ado/guide/data/absolute-and-relative-urls.md)  
  
-   [レコードとプロバイダーが指定したフィールド](../../../ado/guide/data/records-and-provider-supplied-fields.md)  
  
## <a name="see-also"></a>参照  
 [Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [ストリーム オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)   
 [ADO 履歴](../../../ado/guide/ado-history.md)
