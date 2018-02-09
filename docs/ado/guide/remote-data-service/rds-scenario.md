---
title: "RDS シナリオ |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: a7dcad87-aaf0-4b02-9660-472f8469761c
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 05bd95fc39fe21b5df9edfaa876a69d5935de9b2
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="rds-scenario"></a>RDS のシナリオ
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 アドレス帳アプリケーションをリモート データ サービス (RDS) を使用して単純なデータに対応する Web アプリケーションをビルドする方法を説明するシナリオは、-、会社のオンラインのアドレス帳です。 このシナリオは Microsoft Visual Basic Scripting Edition (VBScript) に役立ちする COM プログラマは、RDS を使用してデータに対応した ActiveX コントロールを使用する方法を学習する開発者向けのデータ セントリックの Web アプリケーションの構築経験豊富なソフトウェアのです。  
  
 このシナリオでは、ActiveX コントロールで基本的な HTML タグのレイアウト、DHTML データ バインディングの使用方法は、およびプログラムを使用する方法がわかっている前提としています。  
  
 SDK をインストールする場合は、samples\dataaccess\rds\AddressBook\AddressBook.asp、SDK のディレクトリにアドレス帳サンプル アプリケーションの完全なソース コードを確認できます。 表示するアドレス帳のシナリオを Internet Explorer 4.0 以降では、入力**http://*webserver*/RDS/AddressBook/AddressBook.asp**場所*webserver*指定された名前を指定しますWindows NT 4.0 または Windows 2000 Web サーバー コンピューターにインターネット インフォメーション サービス (IIS) および ASP を実行していること。  
  
## <a name="introduction-to-address-book"></a>アドレス帳の概要  
 アドレス帳のサンプル アプリケーションは、イントラネット経由での検索可能なディレクトリの発行に使用できる単純なオンラインのアドレス帳を提供します。 アドレス帳では、ユーザーが従業員に関する情報を要求の 1 つまたは複数のフィールドに検索文字列を入力できるように設計されています。 表示するには、リモートのデータ サービスの基本的な機能をサンプル アプリケーションが使用して小規模なオブジェクトと検索のフィールドの最小数意図的には保持されます。  
  
 アプリケーションのインターフェイスは、次の部分で構成されます。  
  
-   非ビジュアル**.rds ですDataControl**データベースへの接続にクライアントによって使用されるデータ バインディング オブジェクト。  
  
-   従業員の属性には、入力フィールドとして機能する HTML テキスト ボックスは、条件を検索します。  
  
-   クエリの作成、HTML コマンド ボタンは、検索のフィールドをクリア、従業員情報でデータベースを更新、保留中の変更をキャンセル、およびグリッドに表示されるデータの行を移動をします。  
  
-   バックエンド データベースに対するクエリから返されたデータを表示するデータ バインドの DHTML (を通じて、 **.rds ですDataControl**データ バインディング オブジェクト)、テーブルにします。  
  
-   既に説明したように、要素の各接続し、対話できるようにする VBScript ルーチンです。 初期化するために VBScript コードを使用しても、 **.rds ですDataControl**オブジェクトを HTML テーブルの名前に、列見出しを動的に作成、 **.rds ですDataControl**レコード セットのフィールドです。  
  
 設定し、シナリオを実行して、シナリオの動作方法の詳細についての手順にはステップからのリンクに従います。  
  
 このシナリオには、次のトピックが含まれます。  
  
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


