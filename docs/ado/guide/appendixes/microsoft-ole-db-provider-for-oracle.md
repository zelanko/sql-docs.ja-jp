---
title: Microsoft OLE DB Provider for Oracle |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], OLE DB provider for Oracle
- OLE DB provider for Oracle [ADO]
- Oracle provider [ADO]
ms.assetid: 44fae9dd-5585-4cd6-8bbd-3248a78931b4
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: de312ff17a7d66bf58a5b8f1fb7a6c33aa27acec
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="microsoft-ole-db-provider-for-oracle-overview"></a>Microsoft OLE DB Provider for Oracle の概要
> [!IMPORTANT]
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle の OLE DB プロバイダーを使用します。

 Microsoft OLE DB Provider for Oracle は、ADO では Oracle データベースへのアクセスを許可します。

## <a name="connection-string-parameters"></a>接続文字列パラメーター
 このプロバイダーに接続するには、設定、*プロバイダー*の引数、 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)プロパティ。

```
MSDAORA
```

 読み取り、[プロバイダー](../../../ado/reference/ado-api/provider-property-ado.md)プロパティは同様に、この文字列を返します。

 Oracle データベースでは、キーセット カーソルまたは動的カーソルによる結合クエリを実行する場合、エラーが発生します。 Oracle では、静的な読み取り専用カーソルのみサポートされます。

## <a name="typical-connection-string"></a>一般的な接続文字列
 このプロバイダーの一般的な接続文字列とは。

```
"Provider=MSDAORA;Data Source=serverName;User ID=MyUserID; Password=MyPassword;"
```

 文字列は、これらのキーワードで構成されます。

|Keyword|Description|
|-------------|-----------------|
|**プロバイダー**|OLE DB Provider for Oracle を指定します。|
|**[データ ソース]**|サーバーの名前を指定します。|
|**[ユーザー ID]**|ユーザー名を指定します。|
|**Password**|ユーザーのパスワードを指定します。|

> [!NOTE]
>  Windows 認証をサポートするデータ ソース プロバイダーに接続するかどうかは、する必要がありますを指定する**Trusted_Connection = [はい]** または**Integrated Security = SSPI**ユーザー ID とパスワードの代わりに接続文字列の情報です。

## <a name="provider-specific-connection-parameters"></a>プロバイダー固有の接続パラメーター
 プロバイダーは、ADO で定義されているだけでなく、いくつかのプロバイダーに固有の接続パラメーターをサポートします。 ADO 接続のプロパティを持つこれらのプロバイダーに固有のプロパティを設定してを使用して、[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)のコレクション、[接続](../../../ado/reference/ado-api/connection-object-ado.md)またはの一部として、 **ConnectionString**.

 これらのパラメーターは完全に記載されている、 [OLE DB プログラマーズ リファレンス](http://msdn.microsoft.com/en-us/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8)です。 [ADO の動的プロパティ インデックス](../../../ado/reference/ado-api/ado-dynamic-property-index.md)これらのパラメーター名と対応する OLE DB プロパティの間の相互参照を提供します。

|パラメーター|Description|
|---------------|-----------------|
|**ウィンドウ ハンドル**|ウィンドウ ハンドルを使用して追加の情報を要求することを示します。|
|**[Locale Identifier]**|32 ビットの一意の番号 (1033 など)、ユーザーの言語に関連する設定を指定することを示します。 これらの設定を示す日付と時刻を書式設定方法、項目はアルファベット順に並べ替えられます、文字列を比較してなります。|
|**OLE DB サービス**|OLE DB サービスを有効または無効を指定するビットマスクを示します。|
|**プロンプト**|接続が確立されるときにユーザーに確認するかどうかを示します。|
|**拡張プロパティ**|プロバイダー固有の拡張された接続情報を含む文字列。 このプロパティを使用して、プロパティのメカニズムを通じてを記述できないプロバイダーに固有の接続情報に対してだけです。|

## <a name="see-also"></a>参照
 [ConnectionString プロパティ (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [プロバイダー プロパティ (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
