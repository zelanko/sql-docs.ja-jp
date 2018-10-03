---
title: RDS シナリオ |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: a7dcad87-aaf0-4b02-9660-472f8469761c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aaeedb6dffb992ac940eebd450c63d33badb299d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47845280"
---
# <a name="rds-scenario"></a>RDS のシナリオ
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 以降、RDS サーバー コンポーネントに含まれていない、Windows オペレーティング システム (Windows 8 を参照してくださいと[Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)の詳細)。 RDS クライアント コンポーネントは、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)します。  
  
 アドレス帳アプリケーションがリモート データ サービス (RDS) を使用して、簡単なデータ対応の Web アプリケーションを構築する方法を示すシナリオ-オンラインのコーポレート アドレス帳。 このシナリオは Microsoft Visual Basic Scripting Edition (VBScript) に役立ちますを希望する COM プログラマが RDS を使用してデータ対応の ActiveX コントロールを使用する方法について説明し開発者向けのデータ中心の Web アプリケーションのビルド経験豊富なソフトウェア。  
  
 このシナリオでは、ActiveX コントロールで基本的な HTML タグのレイアウト、DHTML データ バインディングの使用方法、およびプログラムを使用する方法がわかっている前提としています。  
  
 SDK をインストールする場合、samples\dataaccess\rds\AddressBook\AddressBook.asp、SDK のディレクトリにアドレス帳のサンプル アプリケーションの完全なソース コードを検出できます。 アドレス帳のシナリオを表示する Internet Explorer 4.0 以降が入力**http://*web サーバー*/RDS/AddressBook/AddressBook.asp**場所*web サーバー*指定された名前を指定しますWindows NT 4.0 または Windows 2000 Web サーバー コンピューターには、インターネット インフォメーション サービス (IIS) と ASP を実行されています。  
  
## <a name="introduction-to-address-book"></a>アドレス帳の概要  
 アドレス帳のサンプル アプリケーションでは、検索可能なディレクトリをイントラネット経由で発行するために使用できる単純なオンラインのアドレス帳を提供します。 アドレス帳では、ユーザーが従業員に関する情報を要求する 1 つまたは複数のフィールドで検索文字列を入力できるように設計されています。 リモート データ サービスの基本機能を説明する、サンプル アプリケーションが、オブジェクトと検索のフィールドの最小数を使用して小規模な意図的には、保持します。  
  
 アプリケーションのインターフェイスは、次の部分で構成されます。  
  
-   非ビジュアル**rds.DataControl**データベースに接続するクライアントによって使用されるデータ バインディング オブジェクト。  
  
-   従業員の属性の検索条件のフィールドを入力として機能する HTML テキスト ボックス。  
  
-   クエリを作成 HTML コマンド ボタンは、検索フィールドをクリア、従業員情報でデータベースを更新および保留中の変更をキャンセルしたうえで、グリッドに表示されるデータの行を移動します。  
  
-   バックエンド データベースに対するクエリから返されたデータを表示するデータ バインディングの DHTML (を通じて、 **rds.DataControl**データ バインド オブジェクト) をテーブルにします。  
  
-   VBScript ルーチンを以前に説明した要素のそれぞれに接続し、それらの相互作用を許可します。 初期化するために VBScript コードを使用しても、 **rds.DataControl**オブジェクトし、の名前から HTML テーブルの列見出しを動的に作成、 **rds.DataControl**レコード セット フィールド。  
  
 設定して、シナリオを実行して、シナリオのしくみの詳細についての手順にはステップからのリンクに従います。  
  
 このシナリオには、次のトピックが含まれています。  
  
-   [アドレス帳アプリケーションのシステム要件](../../../ado/guide/remote-data-service/system-requirements-for-the-address-book-application.md)  
  
-   [アドレス帳の SQL スクリプトの実行](../../../ado/guide/remote-data-service/running-the-address-book-sql-script.md)  
  
-   [アドレス帳のサンプル アプリケーションの実行](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)  
  
-   [アドレス帳のデータ バインディング オブジェクト](../../../ado/guide/remote-data-service/address-book-data-binding-object.md)  
  
-   [アドレス帳のコマンド ボタン](../../../ado/guide/remote-data-service/address-book-command-buttons.md)  
  
-   [アドレス帳のナビゲーション ボタン](../../../ado/guide/remote-data-service/address-book-navigation-buttons.md)  
  
## <a name="see-also"></a>参照  
 [アドレス帳アプリケーションのシステム要件](../../../ado/guide/remote-data-service/system-requirements-for-the-address-book-application.md)   
 [Microsoft ActiveX Data Objects (ADO)](../../../ado/microsoft-activex-data-objects-ado.md)   
 [RDS の基礎](../../../ado/guide/remote-data-service/rds-fundamentals.md)   
 [RDS チュートリアル](../../../ado/guide/remote-data-service/rds-tutorial.md)


