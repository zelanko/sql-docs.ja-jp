---
title: "RDS を使用して、ODBC 接続プーリング |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection pooling in RDS [ADO]
ms.assetid: e8b912c1-da5b-4e85-a000-1e6648a94237
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 26342c07b2efe10a98a1cef4ff258d7fe5715094
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-rds-with-odbc-connection-pooling"></a>RDS を使用して、ODBC 接続プール
ODBC データ ソースを使用している場合は、クライアントの負荷の処理は高パフォーマンスを実現するために、接続オプションでは、インターネット インフォメーション サービス (IIS) のプールを使用できます。 接続プールは、頻繁に使用される接続を開いた状態を維持する接続は、リソース マネージャーです。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 接続プールを有効にするのには、インターネット インフォメーション サービスのマニュアルを参照してください。  
  
 接続プールを有効にする場合がありますサブジェクト Web サーバーに他の制約では、Microsoft インターネット インフォメーション サービスのドキュメントで説明したとおりに注意してください。  
  
 接続プールが安定しパフォーマンスを向上を提供、TCP/IP ソケット ネットワーク ライブラリを使用する Microsoft SQL Server を構成する必要があります。  
  
 これを行うには、する必要があります。  
  
-   TCP/IP ソケットを使用する SQL Server コンピューターを構成します。  
  
-   TCP/IP ソケットを使用する Web サーバーを構成します。  
  
## <a name="configuring-the-sql-server-computer-to-use-tcpip-sockets"></a>TCP/IP ソケットを使用する SQL Server コンピューターを構成します。  
 SQL Server コンピューターでは、データ ソースとのやり取りが TCP/IP ソケット ネットワーク ライブラリを使用できるように、SQL Server セットアップ プログラムを実行します。  
  
### <a name="to-specify-the-tcpip-socket-network-library-on-the-sql-server-computer"></a>SQL Server コンピューターの TCP/IP ソケット ネットワーク ライブラリを指定するには  
  
### <a name="in-microsoft-sql-server-65"></a>Microsoft SQL server 6.5 の場合。  
  
1.  スタート メニューからプログラム をポイントし、Microsoft SQL Server 6.5、 をポイントおよび SQL の設定 をクリックします。  
  
2.  続行を 2 回クリックします。  
  
3.  Microsoft SQL server — オプション ダイアログ ボックスは、ネットワーク サポートの変更を選択し、続行 をクリックします。  
  
4.  TCP/IP ソケットのチェック ボックスが選択されているかどうかを確認し、[ok] をクリックします。  
  
5.  完了するには続行 をクリックし、セットアップを終了します。  
  
### <a name="in-microsoft-sql-server-70"></a>Microsoft SQL server 7.0 の場合。  
  
1.  スタート メニューからプログラム をポイントし、Microsoft SQL Server 7.0、 をポイントおよびサーバー ネットワーク ユーティリティ をクリックします。  
  
2.  ダイアログ ボックスの [全般] タブで [追加] をクリックします。  
  
3.  ネットワーク ライブラリ構成の追加 ダイアログ ボックスで TCP/IP をクリックします。  
  
4.  ポート番号とプロキシ アドレス ボックスで、ネットワーク管理者によって提供されるポート番号とプロキシのアドレスを入力します。  
  
5.  完了するには [ok] をクリックし、セットアップを終了します。  
  
## <a name="configuring-the-web-server-to-use-tcpip-sockets"></a>TCP/IP ソケットを使用する Web サーバーを構成します。  
 TCP/IP ソケットを使用する Web サーバーを構成するための 2 つのオプションがあります。 すべての SQL Server は、Web サーバーからアクセスするかどうかによって異なります何を実行または特定の SQL Server のみが、Web サーバーからアクセスします。  
  
 Web サーバーからすべての SQL Server にアクセスする場合は、Web サーバー コンピューターで SQL Server クライアント構成ユーティリティを実行する必要があります。 次の手順では、TCP/IP ソケット ネットワーク ライブラリを使用してこの IIS Web サーバーから行われるすべての SQL Server 接続の既定のネットワーク ライブラリを変更します。  
  
### <a name="to-configure-the-web-server-all-sql-servers"></a>Web サーバー (すべての SQL Server) を構成するには  
  
### <a name="for-microsoft-sql-server-65"></a>Microsoft SQL server 6.5。  
  
1.  スタート メニューからプログラム をポイントし、Microsoft SQL Server 6.5、 をポイントおよび SQL クライアント設定ユーティリティ をクリックします。  
  
2.  ネットワーク ライブラリ タブをクリックします。  
  
3.  ネットワークの既定のボックスで、TCP/IP ソケットを選択します。  
  
4.  変更を保存し、ユーティリティを終了する終了 をクリックします。  
  
### <a name="for-microsoft-sql-server-70"></a>Microsoft SQL server 7.0 の場合。  
  
1.  スタート メニューからプログラム をポイントし、Microsoft SQL Server 7.0、 をポイントおよびクライアント ネットワーク ユーティリティ をクリックします。  
  
2.  [全般] タブをクリックします。  
  
3.  [既定のネットワーク ライブラリ] ボックスに、[TCP/IP] をクリックします。  
  
4.  変更を保存し、ユーティリティを終了するには、[ok] をクリックします。  
  
 特定の SQL Server に Web サーバーからアクセスした場合は、Web サーバー コンピューターで SQL Server クライアント構成ユーティリティを実行する必要があります。 特定の SQL Server 接続のネットワーク ライブラリを変更するよう Web サーバー コンピューターに SQL Server クライアント ソフトウェアを構成します。  
  
### <a name="to-configure-the-web-server-a-specific-sql-server"></a>Web サーバー (特定の SQL Server) を構成するには  
  
### <a name="for-microsoft-sql-server-65"></a>Microsoft SQL server 6.5。  
  
1.  スタート メニューからプログラム をポイントし、Microsoft SQL Server 6.5、 をポイントおよび SQL クライアント設定ユーティリティ をクリックします。  
  
2.  詳細設定 タブをクリックします。  
  
3.  [サーバー] ボックスには、TCP/IP ソケットを使用する接続先のサーバーの名前を入力します。  
  
4.  DLL 名 ボックスで、TCP/IP ソケットを選択します。  
  
5.  追加変更 をクリックします。 このサーバーを指すすべてのデータ ソースでは TCP/IP ソケットが使用されます。  
  
6.  元に戻す をクリックします。  
  
### <a name="for-microsoft-sql-server-70"></a>Microsoft SQL server 7.0 の場合。  
  
1.  スタート メニューからプログラム をポイントし、Microsoft SQL Server 7.0、 をポイントおよび クライアント設定ユーティリティ をクリックします。  
  
2.  [全般] タブをクリックします。  
  
3.  [追加] をクリックします。  
  
4.  サーバーの別名 ボックスに、サーバーの別名を入力します。 ネットワーク ライブラリ ボックスで、[TCP/IP] をクリックします。 コンピューター名 ボックスに、クライアントの TCP/IP ソケットをリッスンしているコンピューターのコンピューター名を入力します。 [ポート番号] ボックスには、SQL Server がリッスンするポートを入力します。  
  
5.  [Ok] をクリックし、ユーティリティを終了し、もう一度 [ok] します。  
  
## <a name="see-also"></a>参照  
 [RDS の基礎](../../../ado/guide/remote-data-service/rds-fundamentals.md)























