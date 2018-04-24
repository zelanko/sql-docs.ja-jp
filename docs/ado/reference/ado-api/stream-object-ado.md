---
title: Stream オブジェクト (ADO) |Microsoft ドキュメント
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
apitype: COM
f1_keywords:
- Stream
helpviewer_keywords:
- Stream object [ADO]
ms.assetid: 0514531f-009d-4519-abc3-d727014a39f1
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 32d4082ed203bc789ecb7dce03ce4ecfd422ceb7
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="stream-object-ado"></a>ストリーム オブジェクト (ADO)
バイナリ データまたはテキストのストリームを表します。  
  
 ファイル システムや、電子メール システムなどのツリー構造の階層で、[レコード](../../../ado/reference/ado-api/record-object-ado.md)既定のバイナリ ストリーム bits が関連付けられているファイルや電子メールの内容を含む場合があります。 A**ストリーム**これらのデータ ストリームを含むフィールドやレコードを操作するオブジェクトを使用できます。 A**ストリーム**オブジェクトを取得するには次のようにします。  
  
-   バイナリまたはテキスト データを含むオブジェクト (通常はファイル) を指す URL です。 このオブジェクトは、単純なドキュメント、**レコード**構造化ドキュメントまたはフォルダーを表すオブジェクト。  
  
-   既定値を開くことによって**ストリーム**オブジェクトに関連付けられている、**レコード**オブジェクト。 関連付けられている既定のストリームを取得することができます、**レコード**オブジェクトときに、**レコード**が開かれて、ストリームを開くためだけのラウンド トリップを排除します。  
  
-   インスタンス化して、**ストリーム**オブジェクト。 これら**ストリーム**オブジェクトは、アプリケーションの目的でデータの格納に使用できます。 異なり、**ストリーム**URL、または既定値に関連付けられている**ストリーム**の**レコード**、インスタンス化された**ストリーム**が関連付けられていません、既定では基になります。  
  
 メソッドやプロパティと、**ストリーム**オブジェクトを次を行うことができます。  
  
-   開く、**ストリーム**オブジェクトから、**レコード**またはで URL、[開く](../../../ado/reference/ado-api/open-method-ado-stream.md)メソッドです。  
  
-   閉じる、**ストリーム**で、[閉じる](../../../ado/reference/ado-api/close-method-ado.md)メソッドです。  
  
-   入力バイトまたはテキストを**ストリーム**で、[書き込み](../../../ado/reference/ado-api/write-method.md)と[WriteText](../../../ado/reference/ado-api/writetext-method.md)メソッドです。  
  
-   バイトを読み取り、**ストリーム**で、[読み取り](../../../ado/reference/ado-api/read-method.md)と[ReadText](../../../ado/reference/ado-api/readtext-method.md)メソッドです。  
  
-   いずれかを記述**ストリーム**を持つ基になるオブジェクトに、ADO ではまだデータがバッファー、[フラッシュ](../../../ado/reference/ado-api/flush-method-ado.md)メソッドです。  
  
-   内容をコピー、**ストリーム**別**ストリーム**で、 [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md)メソッドです。  
  
-   持つソース ファイルから行を読み取る方法を制御、 [SkipLine](../../../ado/reference/ado-api/skipline-method.md)メソッドおよび[LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md)プロパティです。  
  
-   ストリームの位置の末尾を設定、 [EOS](../../../ado/reference/ado-api/eos-property.md)プロパティおよび[SetEOS](../../../ado/reference/ado-api/seteos-method.md)メソッドです。  
  
-   保存および復元とファイル内のデータ、 [SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)と[LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md)メソッドです。  
  
-   文字セットを格納するために使用される指定、**ストリーム**で、 [Charset](../../../ado/reference/ado-api/charset-property-ado.md)プロパティです。  
  
-   非同期の中断**ストリーム**と操作、[キャンセル](../../../ado/reference/ado-api/cancel-method-ado.md)メソッドです。  
  
-   内のバイト数を決定する、**ストリーム**で、[サイズ](../../../ado/reference/ado-api/size-property-ado-stream.md)プロパティです。  
  
-   内の現在位置を制御する**ストリーム**で、[位置](../../../ado/reference/ado-api/position-property-ado.md)プロパティです。  
  
-   内のデータの種類を特定、**ストリーム**で、[型](../../../ado/reference/ado-api/type-property-ado-stream.md)プロパティです。  
  
-   現在の状態を判断、**ストリーム**(を閉じると、開くを実行すると、[状態](../../../ado/reference/ado-api/state-property-ado.md)プロパティです。  
  
-   指定のアクセス モード、**ストリーム**で、[モード](../../../ado/reference/ado-api/mode-property-ado.md)プロパティです。  
  
> [!NOTE]
>  Http スキームを使用する Url が自動的に起動、 [Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)です。 詳細については、次を参照してください。[絶対と相対 Url](../../../ado/guide/data/absolute-and-relative-urls.md)です。  
  
 **ストリーム**オブジェクトにスクリプトを実行しても安全です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ストリーム オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/ado-api/stream-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [レコードとストリーム](../../../ado/guide/data/records-and-streams.md)
