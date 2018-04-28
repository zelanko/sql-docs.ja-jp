---
title: JDBC Driver の展開 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ad3508d-d9b1-47fb-a63b-21cdc3ed44e0
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: dc9f01dd72d96a50df220c84827bd7afb826168c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="deploying-the-jdbc-driver"></a>JDBC Driver の展開
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  依存するアプリケーションを展開するときに、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]、アプリケーションと共に JDBC ドライバーを再配布する必要があります。 コンポーネントである Windows オペレーティング システムのコンポーネントである Windows Data Access Components (Windows DAC) とは異なり、JDBC ドライバーと見なされます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
 アプリケーションと共に JDBC ドライバーを展開する方法には 2 種類あります。 1 つは、JDBC ドライバーのファイルを、独自のカスタム インストール パッケージの一部として含める方法です。 2 番目の方法では、Microsoft からダウンロードすることによって提供される JDBC インストール パッケージを使用して、 [Microsoft JDBC Driver for SQL Server デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=70166)です。  
  
 以下のセクションでは、Windows および UNIX オペレーティング システム上で JDBC インストール パッケージを使用する方法について説明します。  
  
> [!NOTE]  
>  一般的な Java アプリケーションの展開については、Java の Web サイトを参照してください。  
  
## <a name="deploying-the-jdbc-driver-on-windows-systems"></a>Windows システム上での JDBC Driver の展開  
 Windows オペレーティング システム上で JDBC ドライバーを展開する場合は、通常の名前は、インストール パッケージの実行可能な zip ファイルのバージョンを使用する必要があります`sqljdbc_<version>_<language>.exe`です。  
  
 実行可能な zip ファイルをサイレント モードで実行するを使用する必要があります、`/auto`コマンドラインまたはバッチ ファイルの次のように、コマンド ライン オプション。  
  
 `sqljdbc_<version>_<language>.exe /auto`  
  
> [!NOTE]  
>  使用すると、`/auto`は完全なサイレント インストールでは、ユーザーの画面上に WinZip ダイアログ ボックスは表示されるオプションです。 ただし、これと対話する必要はありません。解凍操作が完了すると、すぐ終了します。  
  
## <a name="deploying-the-driver-on-unix-systems"></a>UNIX システム上での JDBC Driver の展開  
 UNIX オペレーティング システム上で JDBC ドライバーを展開する場合は、通常の名前は、インストール パッケージの gzip ファイル形式を使用する必要があります`sqljdbc_<version>_<language>.tar.gz`です。  
  
 JDBC ドライバーをインストールする前に、gzip ユーティリティおよび tar ユーティリティの両方がユーザーのシステム上にインストールされ、これらのユーティリティの実行可能ファイルを含むフォルダーが PATH 環境変数に追加されていることを確認します。  
  
 zip 形式の tar ファイルをアンパックするには、ドライバーをアンパックするディレクトリに移動し、次のコマンドを入力します。  
  
 `gzip -d sqljdbc_<version>_<language>.tar.gz`  
  
 tar ファイルをアンパックするには、ドライバーをインストールするディレクトリに tar ファイルを移動し、次のコマンドを入力します。  
  
 `tar –xf sqljdbc_<version>_<language>.tar`  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
