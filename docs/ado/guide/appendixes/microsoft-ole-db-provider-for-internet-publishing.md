---
title: インターネットへの発行の Microsoft OLE DB Provider |Microsoft ドキュメント
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
- OLE DB provider for Internet publishing [ADO]
- providers [ADO], OLE DB provider for Internet publishing
- Internet Publishing provider [ADO]
ms.assetid: 66a208d9-b580-4655-a41e-1d36e5b5bfca
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 26b77c49d4275ace0bcb95ec1495f0637e5b19f2
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="microsoft-ole-db-provider-for-internet-publishing-overview"></a>Microsoft OLE DB Provider for Internet パブリッシングの概要
Microsoft OLE DB Provider for Internet Publishing は、Microsoft や Microsoft Internet Information Server によって提供されたリソースにアクセスする ADO を使用します。 リソースには、HTML ファイル、または Windows 2000 web フォルダーなどの web ソース ファイルが含まれます。

## <a name="connection-string-parameters"></a>接続文字列パラメーター
 このプロバイダーに接続するには、設定、*プロバイダー*の引数、 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)プロパティ。

```
MSDAIPP.DSO
```

 この値も設定またはを使用して読み取る、[プロバイダー](../../../ado/reference/ado-api/provider-property-ado.md)プロパティです。

## <a name="typical-connection-string"></a>一般的な接続文字列
 このプロバイダーの一般的な接続文字列とは。

```
"Provider=MSDAIPP.DSO;Data Source=ResourceURL;User ID=MyUserID;Password=MyPassword;"
```

 -または-

```
"URL=ResourceURL;User ID=MyUserID;Password=MyPassword;"
```

 文字列は、これらのキーワードで構成されます。

|Keyword|Description|
|-------------|-----------------|
|**プロバイダー**|インターネットへの発行用の OLE DB プロバイダーを指定します。|
|**データ ソース**- または - **URL**|ファイルまたは Web フォルダーに発行されるディレクトリの URL を指定します。|
|**[ユーザー ID]**|ユーザー名を指定します。|
|**Password**|ユーザーのパスワードを指定します。|

> [!NOTE]
>  Windows 認証をサポートするデータ ソース プロバイダーに接続するかどうかは、する必要がありますを指定する**Trusted_Connection = [はい]**または**Integrated Security = SSPI**ユーザー ID とパスワードの代わりに接続文字列の情報です。

 設定した場合、 *ResourceURL*値から、"URL ="で無効な値への接続文字列、既定では、インターネット パブリッシング用プロバイダーを発生させます有効な値を要求するダイアログ ボックス。 これは、ダイアログ ボックスがオフになってされ、コンポーネントからの応答を受信していないためにを固定するのには、クライアントが表示されるまでは、プログラムの実行を中断するために、アプリケーションの中間層のコンポーネントの望ましくない動作です。

> [!NOTE]
>  場合 MSDAIPP です。DSO は、プロバイダーは、のいずれかの値として明示的に指定された、*プロバイダー*接続文字列キーワード、または**プロバイダー**プロパティは使用できません"URL ="接続文字列にします。 この場合、エラーが発生します。 代わりに、単に URL を指定のトピックで示すように[を使用する ADO、OLE DB Provider for Internet Publishing と](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md)です。

## <a name="see-also"></a>参照
 [シナリオの公開インターネット](../../../ado/guide/data/internet-publishing-scenario.md)[インターネットへの発行用の OLE DB プロバイダー](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md)
