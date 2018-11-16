---
title: Microsoft ODBC Driver for SQL Server on Windows | Microsoft Docs
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b10cfc22-6a2c-4707-a456-0dcec317982b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9edff1e2afead8dcec3a23fa2d89c4eb8c6a1ef2
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2018
ms.locfileid: "51602852"
---
# <a name="microsoft-odbc-driver-for-sql-server-on-windows"></a>Microsoft ODBC Driver for SQL Server on Windows
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Microsoft ODBC Drivers for[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]を Microsoft には、標準の ODBC インターフェイスを実装するアプリケーション プログラミング インターフェイス (API) を提供するスタンドアロンの ODBC ドライバーは[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。

Microsoft ODBC Driver for SQL Server を使用して、新しいアプリケーションを作成できます。 現在古いバージョンの ODBC ドライバーを使用している古いバージョンのアプリケーションをアップグレードすることもできます。 ODBC Driver for SQL Server を使用すると、Azure SQL Database、Azure SQL Data Warehouse、SQL Server 2017、SQL Server 2016、SQL Server 2014、SQL Server 2012、SQL Server 2008 R2、SQL Server 2008、SQL Server 2005 に接続できます。  

## <a name="summary"></a>[概要]

| [バージョンのオプション]       | サポートされる機能      |
| ------------- |---------------| 
| Microsoft ODBC Driver 17 for SQL Server | <ul><li>Always Encrypted のサポートの BCP API</li><li>新しい接続文字列属性 UseFMTONLY により一時テーブルを必要とする特殊なケースで以前のメタデータを使用するには</li>
| Microsoft ODBC Driver 13.1 for SQL Server     | <ul><li>Always Encrypted</li><li>Azure AD Authentication</li><li>AlwaysOn 可用性グループ (AG)</li></ul>   | 
| Microsoft ODBC Driver 13 for SQL Server      | <ul><li>国際化ドメイン名 (IDN)</li></ul> |
| Microsoft SQL Server 用 ODBC Driver 11 | <ul><li>ドライバー対応接続プール</li><li>接続の回復</li><li>非同期実行 (ポーリング メソッド)</li></ul> |    

## <a name="documentation"></a>ドキュメント  
[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用 Microsoft ODBC Driver に関するこのドキュメントの内容は次のとおりです。  
  
-   [リリース ノート](../../../connect/odbc/windows/release-notes.md)  
-   [Microsoft ODBC Driver for SQL Server on Windows の機能](../../../connect/odbc/windows/features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md)  
-   [インストール、ドライバー ファイルの基本的なシステム要件](../../../connect/odbc/windows/system-requirements-installation-and-driver-files.md)  
-   [OLE DB Provider for SQL Server のドライバー対応接続プール](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)  
-   [非同期実行 &#40;通知方法&#41; の例](../../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md)  
-   [Windows ODBC ドライバーの接続の復元性](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)  
-   [ODBC ドライバーで Always Encrypted を使用する](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
-   [ODBC ドライバーでの Azure Active Directory の使用](../../../connect/odbc/using-azure-active-directory.md) 
-   [透過的なネットワーク IP の解決の使用](../../../connect/odbc/using-transparent-network-ip-resolution.md)   

## <a name="community"></a>コミュニティ  
- [Microsoft ODBC Driver For SQL Server チーム ブログ](https://blogs.msdn.com/sqlnativeclient/default.aspx)  
- [SQL Server データ アクセス フォーラム](https://social.technet.microsoft.com/Forums/en/sqldataaccess/threads)  
  
## <a name="see-also"></a>参照  
- [SQL Server Native Client について](https://msdn.microsoft.com/sqlserver/ff658532.aspx)   
- [SQL Server Native Client を使用したアプリケーションのビルド](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)   
- [SQL Server Native Client に関する FAQ](https://msdn.microsoft.com/sqlserver/aa937707.aspx)   
- [ODBC プログラマー リファレンス](../../../odbc/reference/odbc-programmer-s-reference.md)   
- [SQL Server Native Client (ODBC)](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
