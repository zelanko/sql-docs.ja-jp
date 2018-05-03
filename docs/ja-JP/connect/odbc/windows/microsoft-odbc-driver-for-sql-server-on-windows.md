---
title: Microsoft ODBC Driver for SQL Server on Windows |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b10cfc22-6a2c-4707-a456-0dcec317982b
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e451d6813e85def9485d738f929ff38107bb0301
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="microsoft-odbc-driver-for-sql-server-on-windows"></a>Microsoft ODBC Driver for SQL Server on Windows
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Microsoft ODBC Driver を[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]を Microsoft に標準の ODBC インターフェイスを実装するアプリケーション プログラミング インターフェイス (API) を提供するスタンドアロンの ODBC ドライバーは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。

Microsoft ODBC Driver for SQL Server は、新しいアプリケーションの作成に使用できます。 現在古いバージョンの ODBC ドライバーを使用している古いバージョンのアプリケーションをアップグレードすることもできます。 ODBC Driver for SQL Server では、Azure SQL Database、Azure SQL Data Warehouse、SQL Server 2017、SQL Server 2016、SQL Server 2014、SQL Server 2012、SQL Server 2008 R2、SQL Server 2008、および SQL Server 2005 への接続をサポートします。  

## <a name="summary"></a>[概要]

| バージョン       | サポートされる機能      |
| ------------- |---------------| 
| SQL Server 用 Microsoft ODBC Driver 17 | <ul><li>BCP API が常に暗号化されたサポート</li><li>新しい接続文字列属性 UseFMTONLY により一時テーブルを必要とする特殊なケースで以前のメタデータを使用するドライバー</li>
| Microsoft ODBC Driver 13.1 for SQL Server     | <ul><li>Always Encrypted</li><li>Azure AD の認証</li><li>AlwaysOn 可用性グループ (AG)</li></ul>   | 
| Microsoft ODBC Driver 13 for SQL Server      | <ul><li>国際化ドメイン名 (IDN)</li></ul> |
| Microsoft SQL Server 用 ODBC Driver 11 | <ul><li>ドライバー対応接続プール</li><li>接続の回復</li><li>非同期実行 (ポーリング メソッド)</li></ul> |    

## <a name="documentation"></a>ドキュメント  
[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] 用 Microsoft ODBC Driver に関するこのドキュメントの内容は次のとおりです。  
  
-   [リリース ノート](../../../connect/odbc/windows/release-notes.md)  
-   [Microsoft ODBC Driver for SQL Server on Windows の機能](../../../connect/odbc/windows/features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md)  
-   [インストール、ドライバー ファイルの基本的なシステム要件](../../../connect/odbc/windows/system-requirements-installation-and-driver-files.md)  
-   [OLE DB Provider for SQL Server のドライバー対応接続プール](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)  
-   [非同期実行 &#40;通知方法&#41; の例](../../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md)  
-   [Windows ODBC ドライバーの接続の復元性](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)  
-   [ODBC ドライバーで Always Encrypted を使用します。](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
-   [ODBC ドライバーでの Azure Active Directory の使用](../../../connect/odbc/using-azure-active-directory.md) 
-   [透過ネットワーク IP 解決を使用してください。](../../../connect/odbc/using-transparent-network-ip-resolution.md)   

## <a name="community"></a>コミュニティ  
- [Microsoft ODBC Driver For SQL Server チーム ブログ](http://blogs.msdn.com/sqlnativeclient/default.aspx)  
- [SQL Server データ アクセス フォーラム](http://social.technet.microsoft.com/Forums/en/sqldataaccess/threads)  
  
## <a name="see-also"></a>参照  
- [SQL Server Native Client について](https://msdn.microsoft.com/sqlserver/ff658532.aspx)   
- [SQL Server Native Client でアプリケーションの構築](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)   
- [SQL Server Native Client に関する FAQ](https://msdn.microsoft.com/sqlserver/aa937707.aspx)   
- [ODBC プログラマー リファレンス](../../../odbc/reference/odbc-programmer-s-reference.md)   
- [SQL Server Native Client (ODBC)](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
