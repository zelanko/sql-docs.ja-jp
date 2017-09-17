---
title: "Record オブジェクト (ADO) |Microsoft ドキュメント"
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
- Record
helpviewer_keywords:
- Record object [ADO]
ms.assetid: db83ed2c-a8e3-460c-8682-64667e4d5d01
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 26840ff89f61bc3c37cee2fd88c1f53e393528bf
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="record-object-ado"></a>Record オブジェクト (ADO)
行を表し、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)またはデータ プロバイダーまたはファイルやディレクトリなどの半構造化データ プロバイダーによって返されるオブジェクト。  
  
## <a name="remarks"></a>解説  
 A**レコード**オブジェクトは、データの 1 つの行を表し、1 行をいくつかの概念的な類似点を持つ**Recordset**です。 プロバイダーの機能に応じて**レコード**オブジェクトは、1 行の代わりに、プロバイダーから直接返される可能性が**レコード セット**ときに 1 行のみを選択する SQL クエリの例は、実行されます。 または、**レコード**から直接オブジェクトを取得できる、 **Recordset**オブジェクト。 または、**レコード**半構造化データは、Microsoft Exchange の OLE DB プロバイダーなどに、プロバイダーから直接返されることができます。  
  
 関連付けられているフィールドを表示することができます、**レコード**オブジェクトによって、[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)コレクションに、**レコード**オブジェクト。 ADO ではオブジェクトの値を持つ列を含む**Recordset**、 **SafeArray**とでスカラー値、**フィールド**のコレクション**レコード**オブジェクト。  
  
 場合、**レコード**オブジェクト内の行を表す、**レコード セット**はその元に返すことのできる**レコード セット**で、[ソース](../../../ado/reference/ado-api/source-property-ado-record.md)プロパティ。  
  
 **レコード**オブジェクトも使用できますの半構造化されたデータ プロバイダーでなど、 [Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)、ツリー構造の名前空間をモデル化します。 ツリー内の各ノードは、**レコード**関連付けられている列を持つオブジェクト。 列には、そのノードとその他の関連情報の属性を表すことができます。 **レコード**オブジェクトは、リーフ ノードとツリー構造での非リーフ ノードの両方を表すことができます。 非リーフ ノードはその内容として他のノードがリーフ ノードには、このような内容はありません。 リーフ ノードは、データのバイナリ ストリームを通常は、非リーフ ノードはそれらに関連付けられた既定のバイナリ ストリームにもあります。 プロパティを**レコード**オブジェクトは、ノードの種類を識別します。  
  
 **レコード**編成されたデータを階層的に移動するのにオブジェクトが別の方法にもを表します。 A**レコード**オブジェクトしてあります。 大規模なツリー構造で特定のサブツリーのルートを表すために作成された新しい**レコード**子ノードを表すオブジェクトを開くことができます。  
  
 リソース (たとえば、ファイルまたはディレクトリ) は、絶対 URL で一意に識別できます。 A[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトが暗黙的に作成され、設定、**レコード**オブジェクトと、**レコード**絶対 URL を使用して開かれました。 A**接続**オブジェクト明示的に設定する、**レコード**オブジェクトを介して、 [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)プロパティです。 ファイルとディレクトリを使用してアクセスできる、**接続**オブジェクトの定義、*コンテキスト*を**レコード**操作が発生する可能性があります。  
  
 データの変更およびナビゲーションのメソッドを**レコード**オブジェクトには、相対 URL は、絶対 URL を使用してリソースを検索もそのまま使用または**接続**開始点として、オブジェクト コンテキスト。  
  
> [!NOTE]
>  Http スキームを使用する Url が自動的に起動、 [Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)です。 詳細については、次を参照してください。[絶対と相対 Url](../../../ado/guide/data/absolute-and-relative-urls.md)です。  
  
 A**接続**オブジェクトがそれぞれに関連付けられている**レコード**オブジェクト。 したがって、**レコード**オブジェクトの操作を呼び出すことによって、トランザクションの一部を指定できます**接続**オブジェクトのトランザクション メソッドです。  
  
 **レコード**オブジェクトが ADO イベントをサポートしておらず、したがって通知に応答しません。  
  
 メソッドやプロパティと、**レコード**オブジェクトを次を行うことができます。  
  
-   設定を返したり、関連する**接続**オブジェクトを[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)プロパティです。  
  
-   使用したアクセス権限を示す、[モード](../../../ado/reference/ado-api/mode-property-ado.md)プロパティです。  
  
-   によって表されるリソースが含まれている場合、ディレクトリの URL を返す、**レコード**で、 [ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md)プロパティです。  
  
-   絶対 URL、相対 URL を指定または**Recordset**元となる、**レコード**に派生した、[ソース](../../../ado/reference/ado-api/source-property-ado-record.md)プロパティです。  
  
-   現在の状態を示す、**レコード**で、[状態](../../../ado/reference/ado-api/state-property-ado.md)プロパティです。  
  
-   種類を示す**レコード**—*単純*、*コレクション*、または*構造化ドキュメント*— で、 [RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md)プロパティです。  
  
-   使用して、非同期操作の実行を停止、[キャンセル](../../../ado/reference/ado-api/cancel-method-ado.md)メソッドです。  
  
-   関連付けの解除、**レコード**を持つデータ ソースから、[閉じる](../../../ado/reference/ado-api/close-method-ado.md)メソッドです。  
  
-   ファイルまたはディレクトリで表されるコピー、**レコード**の別の場所に、[つまり](../../../ado/reference/ado-api/copyrecord-method-ado.md)メソッドです。  
  
-   ファイルまたはディレクトリとによって表される、サブディレクトリを削除、**レコード**で、[関係する](../../../ado/reference/ado-api/deleterecord-method-ado.md)メソッドです。  
  
-   開く、 **Recordset**で表されるエンティティのファイルとサブディレクトリを表す行を格納している、**レコード**で、 [GetChildren](../../../ado/reference/ado-api/getchildren-method-ado.md)メソッドです。  
  
-   移動 (rename)、ファイルまたはディレクトリとサブディレクトリ、によって表される、**レコード**の別の場所に、[後続](../../../ado/reference/ado-api/moverecord-method-ado.md)メソッドです。  
  
-   関連付ける、**レコード**と既存のデータ ソース、または新しいファイルまたはディレクトリが作成、[開く](../../../ado/reference/ado-api/open-method-ado-record.md)メソッドです。  
  
 **レコード**オブジェクトにスクリプトを実行しても安全です。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [オブジェクトのプロパティ、メソッド、およびイベントを記録します。](../../../ado/reference/ado-api/record-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Fields コレクション (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [プロパティのコレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [レコードとストリーム](../../../ado/guide/data/records-and-streams.md)   
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
