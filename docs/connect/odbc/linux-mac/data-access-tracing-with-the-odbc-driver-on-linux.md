---
title: ODBC Driver on Linux and macOS によるデータ アクセスのトレース |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data access tracing
- tracing
ms.assetid: 3149173a-588e-47a0-9f50-edb8e9adf5e8
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 64a04e7c448161c22ca9a671e5fdbe706829bced
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="data-access-tracing-with-the-odbc-driver-on-linux-and-macos"></a>ODBC Driver on Linux and macOS によるデータ アクセスのトレース
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

MacOS および Linux では、unixODBC ドライバー マネージャーは、ODBC API 呼び出しのエントリのトレースと終了の ODBC ドライバーのサポートしています。[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。

アプリケーションの ODBC の動作をトレースするには、編集、`odbcinst.ini`ファイルの`[ODBC]`値を設定するセクション`Trace=Yes`と`TraceFile`出力; トレースを格納するファイルのパスに例を示します。

```  
Trace=Yes
TraceFile=/home/myappuser/odbctrace.log
```  

(使用することも`/dev/stdout`またはトレースを永続的なファイルの代わりにある出力を送信する他の任意のデバイス名です)。上記の設定で、アプリケーションは、unixODBC ドライバー マネージャーを読み込むたびに出力ファイルにその解析が実行されるすべての ODBC API 呼び出しが記録されます。

アプリケーションのトレースが終了したら、削除`Trace=Yes`から、`odbcinst.ini`のトレース、パフォーマンスの低下を避けるためにファイルし、不要なトレース ファイルが削除されたことを確認します。
  
内のドライバーを使用するすべてのアプリケーションに適用されるトレース`odbcinst.ini`です。 されません (たとえば、ユーザーごとの機密情報の開示を避けるなど) のすべてのアプリケーションをトレースするには、プライベートの場所を提供することで個々 のアプリケーション インスタンスをトレースできます`odbcinst.ini`を使用して、`ODBCSYSINI`環境変数。 以下に例を示します。  
  
```  
$ ODBCSYSINI=/home/myappuser myapp
```  
  
この場合、追加することができます`Trace=Yes`を`[ODBC Driver 13 for SQL Server]`のセクション`/home/myappuser/odbcinst.ini`です。

## <a name="determining-which-odbcini-file-the-driver-is-using"></a>ドライバーを使用している odbc.ini ファイルを決定します。

Linux および macOS ODBC ドライバーがわからないを`odbc.ini`使用、またはへのパスでは、`odbc.ini`ファイル。 ただし、情報を参照`odbc.ini`ファイルが使用して、unixODBC ツールから利用可能な`odbc_config`と`odbcinst`、および unixODBC ドライバー マネージャーのドキュメントからです。  
  
たとえば、次のコマンド出力 (その他の情報) の間でシステムおよびユーザーの場所`odbc.ini`、それぞれ、システムとユーザー Dsn が含まれるファイル。

```
$ odbcinst -j
unixODBC 2.3.1
DRIVERS............: /etc/odbcinst.ini
SYSTEM DATA SOURCES: /etc/odbc.ini
FILE DATA SOURCES..: /etc/ODBCDataSources
USER DATA SOURCES..: /home/odbcuser/.odbc.ini`
SQLULEN Size.......: 8
SQLLEN Size........: 8
SQLSETPOSIROW Size.: 8
```

[UnixODBC のドキュメント](http://www.unixodbc.org/doc/UserManual/)でユーザーとシステム Dsn の違いについて説明します。 概要。  

- ユーザー Dsn---これらは、Dsn、特定のユーザーに提供するだけです。 ユーザーを使用して接続、追加、変更、および、独自のユーザー Dsn を削除できます。 ユーザー Dsn は、ユーザーのホーム ディレクトリ、またはそのサブディレクトリ内のファイルに格納されます。
  
- システム Dsn---これら Dsn はすべてのユーザーのシステムを使用して、それらの接続に使用できるが、のみ追加、変更、および削除できますシステム管理者によってです。 ユーザーがユーザー DSN とシステム DSN の名前と同じ場合、ユーザー DSN をそのユーザーが接続時に使用されます。

## <a name="see-also"></a>参照
[プログラミング ガイドライン](../../../connect/odbc/linux-mac/programming-guidelines.md)
