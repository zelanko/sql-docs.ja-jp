---
title: "ConvertToString メソッド (RDS) |Microsoft ドキュメント"
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
- ConvertToString method [ADO]
ms.assetid: b3f36bc8-6f69-49b0-83cd-2ccd3afebfbe
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b910522edc20c73164d03fd5f7f313c1eaffabd7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="converttostring-method-rds"></a>ConvertToString メソッド (RDS)
変換、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)レコード セットのデータを表す MIME 文字列にします。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
DataFactory.ConvertToString(Recordset)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *DataFactory*  
 オブジェクト変数を表す、 [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)オブジェクト。  
  
 *レコード セット*  
 オブジェクト変数を表す、 **Recordset**オブジェクト。  
  
## <a name="remarks"></a>解説  
 .Asp ファイルを使用して**ConvertToString**を埋め込むには、 **Recordset**クライアント コンピューターに転送するサーバーで生成された HTML ページにします。  
  
 **ConvertToString**が初めて読み込まれる、 **Recordset**カーソル サービスにテーブル、および MIME 形式でストリームを生成します。  
  
 クライアントでは、リモート データ サービスは、すべての機能に MIME 文字列を変換できます**Recordset**です。 400 個を超える行の行ごとの 1024 バイト幅より以上でデータを処理するためも動作します。 BLOB データをストリーミングに使用することはできませんし、大きな結果が HTTP 経由で設定します。 送信中の圧縮は実行されません、文字列でので非常に大きなデータ セットは時間がかかるトランスポートに定義され、そのネイティブ トランスポート プロトコル形式としてデータ サービスをリモートで展開されているネットワーク最適化 tablegram 形式と比較した場合、HTTP 経由でします。  
  
> [!NOTE]
>  クライアントの HTML ページに結果の MIME 文字列を埋め込むには Active Server Pages を使用している場合の VBScript バージョン 2.0 より前のバージョンが 32 K に文字列のサイズを制限することに注意してください。 この制限を超えた場合、エラーが返されます。 クエリ スコープ比較的少なく抑え .asp ファイルを使用して MIME の埋め込みを使用する場合。 これを解決するには、Microsoft Windows スクリプト テクノロジの Web サイトから VBScript の最新バージョンをダウンロードします。  
  
## <a name="applies-to"></a>適用対象  
 [DataFactory オブジェクト (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)  
  
## <a name="see-also"></a>参照  
 [ConvertToString メソッドの例 (VB)](../../../ado/reference/ado-api/converttostring-method-example-vb.md)   
 [ConvertToString メソッドの例 (VBScript)](../../../ado/reference/rds-api/converttostring-method-example-vbscript.md)



