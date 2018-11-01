---
title: Microsoft ODBC Driver for SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9f2ae91b-06af-4c9a-9d24-062df7bc4662
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8fb8dd7b195ca94751eca51da36340ce201246d1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47669230"
---
# <a name="microsoft-odbc-driver-for-sql-server"></a>Microsoft SQL Server 用 ODBC Driver

[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

ODBC は、SQL Server の C および C++ で記述されたアプリケーションのプライマリ ネイティブ データ アクセス API です。 ほとんどのデータ ソースの ODBC ドライバーがあります。 ODBC を使用できるその他の言語には、COBOL、Perl、PHP、および Python が含まれます。 ODBC は、データ統合シナリオで広く使用されます。

ODBC ドライバーには、[**sqlcmd**](../../tools/sqlcmd-utility.md) や [**bcp**](../../tools/bcp-utility.md) などのツールが付属してします。 **sqlcmd** ユーティリティを使用すると、Transact-SQL ステートメント、システム プロシージャ、SQL スクリプトを実行できます。 **bcp** ユーティリティは、ユーザーが選択した形式で、Microsoft SQL Server インスタンスとデータ ファイルとの間でデータの一括コピーを行います。 **bcp** を使用して、大量の新規行を SQL Server テーブルにインポートしたり、データをテーブルからデータ ファイルにエクスポートしたりできます。  

## <a name="code-example-in-c"></a>C++ でのコード例

次の C++ のサンプルでは、ODBC Api を使用してに接続し、データベースにアクセスする方法を示しています。

- [ODBC を使用して、C++ のコード例](../../odbc/reference/sample-odbc-program.md)

## <a name="download"></a>ダウンロード

- ![ダウンロード下方向丸](../../ssdt/media/download.png)[ODBC ドライバーをダウンロードするには](download-odbc-driver-for-sql-server.md)

## <a name="documentation"></a>ドキュメント

### <a name="features"></a>[機能]

- [カスタム キーストア プロバイダー](../../connect/odbc/custom-keystore-providers.md)
- [DSN と接続文字列のキーワードと属性](dsn-connection-string-attribute.md)
- [SQL Server Native Client](../../relational-databases/native-client/features/sql-server-native-client-features.md) (使用できる機能も適用されます、OLEDB、ODBC Driver for SQL Server になし)
- [Always Encrypted の使用](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
- [Azure Active Directory の使用](../../connect/odbc/using-azure-active-directory.md)
- [透過的なネットワーク IP の解決の使用](../../connect/odbc/using-transparent-network-ip-resolution.md)

### <a name="linux-and-macos"></a>Linux および macOS

- [ドライバーをインストールします。](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
- [SQL Server への接続](../../connect/odbc/linux-mac/connection-string-keywords-and-data-source-names-dsns.md)
- [**bcp** による接続](../../connect/odbc/linux-mac/connecting-with-bcp.md)
- [**sqlcmd** による接続](../../connect/odbc/linux-mac/connecting-with-sqlcmd.md)
- [データ アクセスのトレース](../../connect/odbc/linux-mac/data-access-tracing-with-the-odbc-driver-on-linux.md)
- [よく寄せられる質問](../../connect/odbc/linux-mac/frequently-asked-questions-faq-for-odbc-linux.md)
- [ドライバー マネージャーのインストール](../../connect/odbc/linux-mac/installing-the-driver-manager.md)
- [既知の問題](../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)
- [プログラミング ガイドライン](../../connect/odbc/linux-mac/programming-guidelines.md)
- [リリース ノート](../../connect/odbc/linux-mac/release-notes.md)
- [高可用性とディザスター リカバリーのサポート](../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)
- [統合認証を使用する (Kerberos)](../../connect/odbc/linux-mac/using-integrated-authentication.md)

### <a name="windows"></a>Windows

- [非同期実行 (通知方法) の例](../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md)
- [Windows ODBC ドライバーの接続の復元性](../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)
- [ドライバー対応接続プール](../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)
- [機能および動作変更](../../connect/odbc/windows/features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md)
- [リリース ノート](../../connect/odbc/windows/release-notes.md)
- [システム要件、インストール、およびドライバー ファイル](../../connect/odbc/windows/system-requirements-installation-and-driver-files.md)



## <a name="community"></a>コミュニティ  
- [Microsoft ODBC Driver For SQL Server チーム ブログ](http://blogs.msdn.com/sqlnativeclient/default.aspx)  
- [SQL Server データ アクセス フォーラム](http://social.technet.microsoft.com/Forums/en/sqldataaccess/threads)  
