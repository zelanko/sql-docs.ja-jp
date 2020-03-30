---
title: Linux と macOS での ODBC ドライバーによるデータ アクセスのトレース | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data access tracing
- tracing
ms.assetid: 3149173a-588e-47a0-9f50-edb8e9adf5e8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1fa39cd11f70a661de5c284e56f2ccc0f7a5777f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "68008824"
---
# <a name="data-access-tracing-with-the-odbc-driver-on-linux-and-macos"></a>Linux と macOS での ODBC ドライバーによるデータ アクセスのトレース

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

macOS と Linux の unixODBC Driver Manager では、ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の ODBC API 呼び出しの開始と終了のトレースがサポートされます。

アプリケーションの ODBC 動作をトレースするには、`odbcinst.ini` ファイルの `[ODBC]` セクションを編集し、`Trace=Yes` と `TraceFile` の値を、トレース出力を含めるファイルのパスに設定します。例を以下に示します。

```ini
[ODBC]
Trace=Yes
TraceFile=/home/myappuser/odbctrace.log
```

(`/dev/stdout` またはその他のデバイス名を使用して、永続的なファイルではなく、そこにトレース出力を送信することもできます)。上記の設定では、アプリケーションで unixODBC Driver Manager を読み込むたびに、出力ファイルに実行されたすべての ODBC API 呼び出しが記録されます。

アプリケーションのトレースが終了した後、`odbcinst.ini` ファイルから `Trace=Yes` を削除してトレースのパフォーマンスが低下しないようにし、不要なトレース ファイルが削除されたことを確認します。

トレースは、`odbcinst.ini` 内のドライバーを使用するすべてのアプリケーションに適用されます。 すべてのアプリケーションをトレースしない (ユーザーごとの機密情報の公開を避けるためなど) 場合は、`ODBCSYSINI` 環境変数を使用して、プライベート `odbcinst.ini` の場所を指定することにより、個々のアプリケーション インスタンスをトレースできます。 次に例を示します。

```bash
$ ODBCSYSINI=/home/myappuser myapp
```

この場合、`/home/myappuser/odbcinst.ini` の `[ODBC Driver 13 for SQL Server]` セクションに `Trace=Yes` を追加できます。

## <a name="determining-which-odbcini-file-the-driver-is-using"></a>ドライバーが使用している odbc.ini ファイルを特定する

Linux および macOS の ODBC ドライバーでは、使用されている `odbc.ini` や、`odbc.ini` ファイルへのパスが認識されません。 しかし、使用されている `odbc.ini` ファイルに関する情報は、unixODBC ツールの `odbc_config` と `odbcinst` から、および unixODBC Driver Manager のドキュメントから取得できます。

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

[unixODBC のドキュメント](http://www.unixodbc.org/doc/UserManual/)では、ユーザーとシステムの DSN の違いについて説明されています。 要約すると:

- ユーザー DSN --- これらは、特定のユーザーのみが使用できる DSN です。 ユーザーは、独自のユーザー DSN を使用して、接続、追加、変更、および削除することができます。 ユーザー DSN は、ユーザーのホーム ディレクトリ、またはそのサブディレクトリ内のファイルに格納されます。

- システム DSN --- これらの DSN は、システム上のすべてのユーザーが使用して接続できますが、追加、変更、および削除できるのはシステム管理者のみとなります。 あるユーザーが、システム DSN と同じ名前のユーザー DSN を持っている場合、そのユーザーによる接続時にユーザー DSN が使用されます。

## <a name="see-also"></a>参照

- [プログラミング ガイドライン](../../../connect/odbc/linux-mac/programming-guidelines.md)
