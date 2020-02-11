---
title: Stream オブジェクト (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Stream
helpviewer_keywords:
- Stream object [ADO]
ms.assetid: 0514531f-009d-4519-abc3-d727014a39f1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c70a22a3048c769aac343d51e621e4d755d3baeb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67916720"
---
# <a name="stream-object-ado"></a>Stream オブジェクト (ADO)
バイナリデータまたはテキストのストリームを表します。  
  
 ファイルシステムや電子メールシステムなどのツリー構造の階層では、[レコード](../../../ado/reference/ado-api/record-object-ado.md)には、ファイルまたは電子メールの内容を含む既定のバイナリストリームが関連付けられている場合があります。 **ストリーム**オブジェクトは、これらのデータストリームを含むフィールドまたはレコードを操作するために使用できます。 **ストリーム**オブジェクトは、次の方法で取得できます。  
  
-   バイナリまたはテキストデータを含むオブジェクト (通常はファイル) を指す URL。 このオブジェクトには、単純なドキュメント、構造化されたドキュメントを表す**レコード**オブジェクト、またはフォルダーを指定できます。  
  
-   **Record**オブジェクトに関連付けられた既定の**ストリーム**オブジェクトを開く。 レコード**を開い**たときに**レコード**オブジェクトに関連付けられた既定のストリームを取得して、ストリームを開くだけでラウンドトリップが行われないようにすることができます。  
  
-   **ストリーム**オブジェクトをインスタンス化する。 これらの**ストリーム**オブジェクトは、アプリケーションの目的でデータを格納するために使用できます。 URL に関連付けられた**ストリーム**や**レコード**の既定の**ストリーム**とは異なり、インスタンス化された**ストリーム**には、既定で基になるソースとの関連付けがありません。  
  
 **Stream**オブジェクトのメソッドとプロパティを使用して、次の操作を実行できます。  
  
-   [Open](../../../ado/reference/ado-api/open-method-ado-stream.md)メソッドを使用して、**レコード**または URL から**ストリーム**オブジェクトを開きます。  
  
-   [Close](../../../ado/reference/ado-api/close-method-ado.md)メソッドを使用して**ストリーム**を閉じます。  
  
-   [Write](../../../ado/reference/ado-api/write-method.md)および[WriteText](../../../ado/reference/ado-api/writetext-method.md)メソッドを使用して**ストリーム**にバイトまたはテキストを入力します。  
  
-   [Read](../../../ado/reference/ado-api/read-method.md)および[ReadText](../../../ado/reference/ado-api/readtext-method.md)メソッドを使用して、**ストリーム**からバイトを読み取ります。  
  
-   ADO バッファーに残っている**ストリーム**データを、 [Flush](../../../ado/reference/ado-api/flush-method-ado.md)メソッドを使用して基になるオブジェクトに書き込みます。  
  
-   [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md)メソッドを使用して**ストリーム**の内容を別の**ストリーム**にコピーします。  
  
-   [SkipLine](../../../ado/reference/ado-api/skipline-method.md)メソッドと[lineseparator](../../../ado/reference/ado-api/lineseparator-property-ado.md)プロパティを使用して、ソースファイルから行を読み取る方法を制御します。  
  
-   [EOS](../../../ado/reference/ado-api/eos-property.md)プロパティと[SetEOS](../../../ado/reference/ado-api/seteos-method.md)メソッドを使用して、ストリームの位置の終わりを確認します。  
  
-   [SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)メソッドと[LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md)メソッドを使用して、データをファイルに保存して復元します。  
  
-   [Charset](../../../ado/reference/ado-api/charset-property-ado.md)プロパティを使用して、**ストリーム**の格納に使用する文字セットを指定します。  
  
-   [Cancel](../../../ado/reference/ado-api/cancel-method-ado.md)メソッドを使用して、非同期**ストリーム**操作を停止します。  
  
-   [Size](../../../ado/reference/ado-api/size-property-ado-stream.md)プロパティを使用して、**ストリーム**内のバイト数を決定します。  
  
-   [Position](../../../ado/reference/ado-api/position-property-ado.md)プロパティを使用して、**ストリーム**内の現在位置を制御します。  
  
-   [Type](../../../ado/reference/ado-api/type-property-ado-stream.md)プロパティを使用して、**ストリーム**内のデータの種類を決定します。  
  
-   [State](../../../ado/reference/ado-api/state-property-ado.md)プロパティを使用して、**ストリーム**の現在の状態 (閉じている、開いている、または実行中) を確認します。  
  
-   [モード](../../../ado/reference/ado-api/mode-property-ado.md)プロパティを使用して、**ストリーム**のアクセスモードを指定します。  
  
> [!NOTE]
>  Http スキームを使用する Url は、[インターネット公開のために Microsoft OLE DB プロバイダー](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)を自動的に呼び出します。 詳細については、「[絶対 url と相対 url](../../../ado/guide/data/absolute-and-relative-urls.md)」を参照してください。  
  
 **ストリーム**オブジェクトは、スクリプトに対して安全です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [Stream オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/ado-api/stream-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [レコードとストリーム](../../../ado/guide/data/records-and-streams.md)
