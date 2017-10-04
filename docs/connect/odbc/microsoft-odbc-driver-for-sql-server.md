---
title: "Microsoft ODBC Driver for SQL Server |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f2ae91b-06af-4c9a-9d24-062df7bc4662
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: bbb36ba4a739f0c7871261b61d298428ec3b2191
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="microsoft-odbc-driver-for-sql-server"></a>Microsoft SQL Server 用 ODBC Driver

![ダウンロード DownArrow 丸](../../ssdt/media/download.png)[ODBC ドライバーをダウンロードするには](../sql-connection-libraries.md#anchor-20-drivers-relational-access)

ODBC は、SQL Server の C および C++ で記述されたアプリケーションのプライマリ ネイティブ データ アクセス API です。 ほとんどのデータ ソース用の ODBC ドライバーがあります。 ODBC を使用できるその他の言語には、COBOL、Perl、PHP、および Python が含まれます。 ODBC は、データ統合のシナリオで広く使用されます。

ODBC ドライバーは、ツールが付属など[ **sqlcmd** ](../../tools/sqlcmd-utility.md)と[ **bcp**](../../tools/bcp-utility.md)です。 **Sqlcmd**ユーティリティでは、TRANSACT-SQL ステートメント、システム プロシージャ、および SQL スクリプトを実行することができます。 **Bcp**ユーティリティ一括が選択した形式で Microsoft SQL Server のインスタンスとデータ ファイル間でデータをコピーします。 使用することができます**bcp** SQL Server テーブルに大量の新規行をインポートするか、テーブルからデータ ファイルにエクスポートします。  

## <a name="code-example-in-c"></a>C++ でのコード例

ODBC を使用する C + + プログラムのソース コードを含む小さな .zip ファイルがあります。

- [ODBC を使用して、C++ コードの例](../../odbc/reference/sample-odbc-program.md)

## <a name="download"></a>ダウンロード

- ![ダウンロード DownArrow 丸](../../ssdt/media/download.png)[ODBC ドライバーをダウンロードするには](../sql-connection-libraries.md#anchor-20-drivers-relational-access)

## <a name="documentation"></a>ドキュメント  

### <a name="linux-and-macos"></a>Linux および macOS

- [ドライバーをインストールします。](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
- [使用した接続**bcp**](../../connect/odbc/linux-mac/connecting-with-bcp.md)
- [使用した接続**sqlcmd**](../../connect/odbc/linux-mac/connecting-with-sqlcmd.md)
- [統合認証 (Kerberos) を使用します。](../../connect/odbc/linux-mac/using-integrated-authentication.md)
- [接続文字列キーワードとデータ ソース名](../../connect/odbc/linux-mac/connection-string-keywords-and-data-source-names-dsns.md)
- [データ アクセスのトレース](../../connect/odbc/linux-mac/data-access-tracing-with-the-odbc-driver-on-linux.md)
- [よく寄せられる質問](../../connect/odbc/linux-mac/frequently-asked-questions-faq-for-odbc-linux.md)
- [ドライバー マネージャーのインストール](../../connect/odbc/linux-mac/installing-the-driver-manager.md)
- [既知の問題](../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)
- [プログラミング ガイドライン](../../connect/odbc/linux-mac/programming-guidelines.md)
- [リリース ノート](../../connect/odbc/linux-mac/release-notes.md)
- [高可用性と災害復旧のサポート](../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)

### <a name="windows"></a>Windows

- [非同期実行 (通知方法) の例](../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md)
- [Windows ODBC ドライバーの接続の復元性](../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)
- [ドライバー対応接続プール](../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)
- [機能および動作変更](../../connect/odbc/windows/features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md)
- [リリース ノート](../../connect/odbc/windows/release-notes.md)
- [システム要件、インストール、およびドライバー ファイル](../../connect/odbc/windows/system-requirements-installation-and-driver-files.md)

### <a name="features"></a>機能

- [カスタム キー ストア プロバイダー](../../connect/odbc/custom-keystore-providers.md)
- [SQL Server Native Client](../../relational-databases/native-client/features/sql-server-native-client-features.md) (使用可能な機能も適用、OLEDB、ODBC Driver for SQL Server になし)
- [常に暗号化を使用します。](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
- [Azure Active Directory を使用します。](../../connect/odbc/using-azure-active-directory.md)
- [透過ネットワーク IP 解決を使用してください。](../../connect/odbc/using-transparent-network-ip-resolution.md)

## <a name="community"></a>コミュニティ  
- [Microsoft ODBC Driver For SQL Server チーム ブログ](http://blogs.msdn.com/sqlnativeclient/default.aspx)  
- [SQL Server データ アクセス フォーラム](http://social.technet.microsoft.com/Forums/en/sqldataaccess/threads)  

