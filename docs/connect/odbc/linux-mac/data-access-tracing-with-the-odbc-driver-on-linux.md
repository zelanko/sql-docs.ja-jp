---
title: Linux と macOS での ODBC ドライバーによるデータ アクセスのトレース | Microsoft Docs
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
ms.openlocfilehash: f5a22a5f4eb06e983f2bc4d81eeb786f32b78751
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785975"
---
# <a name="data-access-tracing-with-the-odbc-driver-on-linux-and-macos"></a>Linux と macOS での ODBC ドライバーによるデータ アクセスのトレース
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

MacOS および Linux では、unixODBC ドライバー マネージャーは、ODBC API 呼び出しのエントリのトレースと終了の ODBC ドライバーのサポートしています。[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。

アプリケーションの ODBC の動作をトレースするには、編集、`odbcinst.ini`ファイルの`[ODBC]`値を設定するセクション`Trace=Yes`と`TraceFile`に、トレース出力; が含まれているファイルのパスにたとえば。

```  
Trace=Yes
TraceFile=/home/myappuser/odbctrace.log
```  

(使用することも`/dev/stdout`または他のすべてのデバイス名の代わりにあると出力を永続的なファイルにトレースを送信します)。上記の設定を持つアプリケーションは、unixODBC ドライバー マネージャーを読み込むたびに出力ファイルにその解析が実行されるすべての ODBC API 呼び出しが記録されます。

アプリケーションのトレースが完了したら、削除`Trace=Yes`から、`odbcinst.ini`のトレース、パフォーマンスの低下を回避するためにファイルを開き、不要なトレース ファイルを削除してください。
  
トレースは、`odbcinst.ini` 内のドライバーを使用するすべてのアプリケーションに適用されます。 すべてのアプリケーションをトレースしない (ユーザーごとの機密情報の公開を避けるためなど) 場合は、`ODBCSYSINI` 環境変数を使用して、プライベート `odbcinst.ini` の場所を指定することにより、個々のアプリケーション インスタンスをトレースできます。 例 :  
  
```  
$ ODBCSYSINI=/home/myappuser myapp
```  
  
この場合、追加することができます`Trace=Yes`を`[ODBC Driver 13 for SQL Server]`の`/home/myappuser/odbcinst.ini`します。

## <a name="determining-which-odbcini-file-the-driver-is-using"></a>ドライバーが使用している odbc.ini ファイルを特定する

Linux と macOS の ODBC ドライバーは、わからない`odbc.ini`使用、またはへのパスでは、`odbc.ini`ファイル。 ただし、これについては`odbc.ini`ファイルが使用して、unixODBC ツールから使用可能な`odbc_config`と`odbcinst`、および unixODBC ドライバー マネージャーのドキュメントから。  
  
たとえば、次のコマンドは、(他の情報と一緒に) システム DSN とユーザー DSN をそれぞれ格納するシステムおよびユーザーの `odbc.ini` ファイルの場所を出力します。

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

[UnixODBC のドキュメント](http://www.unixodbc.org/doc/UserManual/)ユーザーおよびシステム Dsn の違いについて説明します。 概要。  

- ユーザー Dsn---これらは、Dsn、特定のユーザーに提供するだけです。 ユーザーが接続を使用して、追加変更、および、独自のユーザー Dsn を削除します。 ユーザー Dsn は、ユーザーのホーム ディレクトリ、またはそのサブディレクトリ内のファイルに格納されます。
  
- システム Dsn---これら Dsn、それらを使用して接続するシステムのすべてのユーザーは使用ことができますのみ追加、変更、およびシステム管理者によって削除します。 ユーザー DSN とシステム DSN の名前と同じにする場合は、そのユーザーが接続時に、ユーザー DSN が使用されます。

## <a name="see-also"></a>参照
[プログラミング ガイドライン](../../../connect/odbc/linux-mac/programming-guidelines.md)
