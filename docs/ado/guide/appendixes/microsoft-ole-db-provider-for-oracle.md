---
title: Microsoft OLE DB Provider for Oracle |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], OLE DB provider for Oracle
- OLE DB provider for Oracle [ADO]
- Oracle provider [ADO]
ms.assetid: 44fae9dd-5585-4cd6-8bbd-3248a78931b4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 60510302525562d9c3007a6ef57213fc261b4c60
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926625"
---
# <a name="microsoft-ole-db-provider-for-oracle-overview"></a>Microsoft OLE DB Provider for Oracle の概要
> [!IMPORTANT]
>  この機能は、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle の OLE DB プロバイダーを使用します。

 Microsoft OLE DB Provider for Oracle により、ADO は Oracle データベースにアクセスできます。

## <a name="connection-string-parameters"></a>接続文字列パラメーター
 このプロバイダーに接続するには、 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)プロパティの*provider*引数を次のように設定します。

```vb
MSDAORA
```

 [プロバイダー](../../../ado/reference/ado-api/provider-property-ado.md)プロパティを読み取ると、この文字列も返されます。

 キーセットカーソルまたは動的カーソルを使用した結合クエリが Oracle データベースで実行されると、エラーが発生します。 Oracle では、静的な読み取り専用カーソルのみがサポートされます。

## <a name="typical-connection-string"></a>一般的な接続文字列
 このプロバイダーの一般的な接続文字列は次のとおりです。

```vb
"Provider=MSDAORA;Data Source=serverName;User ID=MyUserID; Password=MyPassword;"
```

 文字列は、次のキーワードで構成されています。

|Keyword|[説明]|
|-------------|-----------------|
|**プロバイダー**|Oracle の OLE DB プロバイダーを指定します。|
|**Data Source**|サーバーの名前を指定します。|
|**User ID**|ユーザー名を指定します。|
|**パスワード**|ユーザーのパスワードを指定します。|

> [!NOTE]
>  Windows 認証をサポートするデータソースプロバイダーに接続する場合は、接続文字列にユーザー ID とパスワードの情報ではなく、 **Trusted_Connection = yes**または**INTEGRATED Security = SSPI**を指定する必要があります。

## <a name="provider-specific-connection-parameters"></a>プロバイダー固有の接続パラメーター
 プロバイダーは、ADO によって定義されているものに加えて、いくつかのプロバイダー固有の接続パラメーターをサポートしています。 ADO の接続プロパティと同様に、これらのプロバイダー固有のプロパティは、[接続](../../../ado/reference/ado-api/connection-object-ado.md)の[properties](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションまたは**ConnectionString**の一部として設定できます。

 これらのパラメーターの詳細については[OLE DB プログラマーリファレンス](https://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8)」を参照してください。 [ADO 動的プロパティインデックス](../../../ado/reference/ado-api/ado-dynamic-property-index.md)は、これらのパラメーター名と、対応する OLE DB プロパティとの間の相互参照を提供します。

|パラメーター|[説明]|
|---------------|-----------------|
|**ウィンドウハンドル**|追加情報の入力を求めるために使用するウィンドウハンドルを示します。|
|**ロケール識別子**|ユーザーの言語に関連する設定を指定する32ビットの一意の数値 (1033 など) を示します。 これらの設定は、日付と時刻を書式設定する方法、アルファベット順に並べ替えられる項目、文字列を比較する方法などを指定します。|
|**OLE DB サービス**|有効または無効にする OLE DB サービスを指定するビットマスクを示します。|
|**プロンプト**|接続の確立中にユーザーにプロンプトを表示するかどうかを示します。|
|**Extended Properties**|プロバイダー固有の拡張接続情報を含む文字列。 このプロパティは、プロパティメカニズムでは記述できないプロバイダー固有の接続情報に対してのみ使用します。|

## <a name="see-also"></a>参照
 [ConnectionString プロパティ (ado)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [プロバイダープロパティ (ado](../../../ado/reference/ado-api/provider-property-ado.md) )[レコードセットオブジェクト (ado)](../../../ado/reference/ado-api/recordset-object-ado.md)
