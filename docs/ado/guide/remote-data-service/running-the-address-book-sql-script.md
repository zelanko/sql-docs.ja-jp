---
title: "アドレス帳の SQL スクリプトを実行している |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: 409b3f8b-0ced-4867-acbe-b245dcdf6702
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2ab669066b0440807a4a2475817e0dbda047cb79
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="running-the-address-book-sql-script"></a>アドレス帳の SQL スクリプトを実行します。
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 ISQL/クエリ アナライザーのコマンド ライン ユーティリティ、または、SQL Server Enterprise Manager を使用する必要があります (Sampleemp.sql)、含まれる SQL スクリプトを実行します。  
  
-   既定のデバイスを AddrBookDB、新しいデータベースを作成します。  
  
-   AddrBookDB、データベースに接続します。  
  
-   Employee テーブルを作成します。  
  
-   サンプル データを含むテーブルを追加します。  
  
-   データベース テーブルの作成を確認する場合は、単純な SELECT ステートメントを実行します。  
  
-   は、"adcdemo"パスワード"adcdemo"と呼ばれるユーザー アカウントを設定します。  
  
#### <a name="to-run-the-sampleempsql-script-in-microsoft-sql-server-65"></a>Microsoft SQL Server 6.5 の Sampleemp.sql スクリプトを実行するには  
  
1.  をクリックして**開始**、 をポイント**プログラム**、順にポイントして**Microsoft SQL Server 6.5**です。 をクリックして**SQL Enterprise Manager**です。  
  
2.  **ツール** メニューをクリックして**SQL クエリ ツール**です。  
  
3.  をクリックして**SQL スクリプトの読み込み**c:\Platform SDK\Samples\DataAccess\RDS\AddressBook を参照します。  
  
4.  Sampleemp.sql ファイルを選択します。 **[開く]**をクリックします。  
  
5.  クリックして、**クエリの実行**(ツールバーの緑色の矢印) ボタンをクリックします。  
  
6.  を実行すると、閉じる、**クエリ**と**Enterprise Manager** windows です。  
  
#### <a name="to-run-the-sampleempsql-script-in-microsoft-sql-server-70"></a>Microsoft SQL Server 7.0 で Sampleemp.sql スクリプトを実行するには  
  
1.  をクリックして**開始**、 をポイント**プログラム**、順にポイントして**Microsoft SQL Server 7.0**です。 をクリックして**Enterprise Manager**です。  
  
2.  Enterprise Manager で登録済みサーバーの一覧から使用する SQL Server が選択されていることを確認します。  
  
3.  **ツール** メニューをクリックして**SQL Server クエリ アナライザー**です。  
  
4.  クリックして、 **SQL スクリプトの読み込み**c:\Platform SDK\Samples\DataAccess\RDS\AddressBook を参照し、ボタン (ツールバーの開いているフォルダー) をクリックします。  
  
5.  Sampleemp.sql ファイルを選択します。 **[開く]**をクリックします。  
  
6.  クリックして、**クエリの実行**ボタン (ツールバーの緑色の矢印) または**f5 キーを押して**です。  
  
7.  を実行すると、閉じる、**クエリ**、**クエリ アナライザー**、および**Enterprise Manager** windows です。  
  
## <a name="see-also"></a>参照  
 [アドレス帳のサンプル アプリケーションの実行](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)


