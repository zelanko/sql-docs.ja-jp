---
title: "Microsoft ODBC Driver for SQL Server on Windows の機能 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
caps.latest.revision: "22"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 204b8ba3c81bae77c6a663e93f2b541c8aca0727
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="features-of-the-microsoft-odbc-driver-for-sql-server-on-windows"></a>Microsoft ODBC Driver for SQL Server on Windows の機能
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

    
## <a name="microsoft-odbc-driver-131-for-sql-server-on-windows"></a>SQL Server on Windows 用 Microsoft ODBC Driver 13.1

SQL Server 用 ODBC Driver 13.1 は、以前のバージョン (11) のすべての機能が含まれていて、Microsoft SQL Server 2016 と組み合わせて使用する場合は、常に暗号化および Azure Active Directory の認証のサポートを追加します。  
  
Always Encrypted を使用すると、クライアントは SQL Server に暗号化キーを開示することなく、クライアント アプリケーション内の機密データを暗号化することができます。 クライアント コンピューターにインストールされている、Always Encrypted が有効のドライバーは、SQL Server クライアント アプリケーション内の機密データを自動的に暗号化および暗号化解除することで、この処理を実行します。 ドライバーは、SQL Server にデータを渡す前に機密性の高い列のデータを暗号化し、アプリケーションに対するセマンティクスが維持されるように自動的にクエリを書き換えます。 同様に、ドライバーはクエリ結果に含まれている暗号化されたデータベース列に格納されているデータを透過的に暗号化解除します。 詳細については、次を参照してください。 [ODBC ドライバーで Always Encrypted を使用して](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)です。
 
Azure Active Directory により、Azure Active Directory (Azure AD での id を使用して、Microsoft Azure SQL Database と Microsoft SQL Server 2016 への接続のメカニズムとして Azure Active Directory 認証を使用するには、ユーザー、DBA のおよびアプリケーション プログラマ向け). 詳細については、次を参照してください。[を使用して Azure Active Directory ODBC ドライバーで](../../../connect/odbc/using-azure-active-directory.md)、および[SQL データベースまたは SQL データ ウェアハウス認証を使用して Azure Active Directory に接続する](https://azure.microsoft.com/en-us/documentation/articles/sql-database-aad-authentication/)です。   
  
## <a name="microsoft-odbc-driver-11-for-sql-server-on-windows"></a>Windows の Microsoft ODBC Driver 11 for SQL Server  

ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] には、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] に付属の [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)]Native Client ODBC ドライバーのすべての機能が含まれています。 詳細については、「 [SQL Server Native Client プログラミング](http://msdn.microsoft.com/library/ms130892.aspx)」を参照してください。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Native Client ODBC ドライバーは、Windows オペレーティング システムに付属の ODBC ドライバーに基づいています。 詳細については、「 [Windows Data Access Components SDK](http://msdn.microsoft.com/library/aa968814(VS.85).aspx)」を参照してください。  
  
ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] のこのリリースには、次の新機能が含まれています。  
  
### <a name="bcpexe-l-option-for-specifying-a-login-timeout"></a>ログイン タイムアウトを指定するための bcp.exe – l オプション
 
– L オプションが、秒数を指定する前に、`bcp.exe`へのログイン[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]がタイムアウトになるサーバーに接続しようとします。 既定のログイン タイムアウトは、15 秒です。 ログイン タイムアウトは、0 ~ 65,534 の範囲の数値でなければなりません。 指定した値が数値以外の場合、または範囲外の場合、`bcp.exe` はエラー メッセージを生成します。 値 0 は、無限のタイムアウトを指定します。 (約) 10 秒未満のログイン タイムアウトは信頼できません。  
  
### <a name="driver-aware-connection-pooling"></a>ドライバー対応接続プール  
ODBC Driver for[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]サポート[ドライバー対応接続プール](http://msdn.microsoft.com/library/hh405031(VS.85).aspx)です。 詳細については、「 [Driver-Aware Connection Pooling in the ODBC Driver for SQL Server](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)」を参照してください。  
  
### <a name="asynchronous-execution-notification-method"></a>非同期実行 (通知方法)  
ODBC Driver for[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]サポート[非同期実行 (通知方法)](http://msdn.microsoft.com/library/hh405038(VS.85).aspx)です。 使用例については、次を参照してください。[非同期実行 &#40;です。通知方法 &#41;サンプル](../../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md)です。  
  
### <a name="connection-resiliency"></a>接続の回復
アプリケーションを Microsoft Azure SQL データベースに接続されたままにするため、Windows 上の ODBC ドライバーは、アイドル状態の接続を復元できます。 詳細については、「 [Connection Resiliency in the Windows ODBC Driver](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)」を参照してください。  
  
## <a name="behavior-changes"></a>動作の変更

[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Native Client は、`-y0`オプションを`sqlcmd.exe`表示幅が 0 の場合は、1 MB で切り捨てられるように出力します。
  
以降で ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]、1 つの列で取得できるデータの量に制限はないとき`–y0`を指定します。 `sqlcmd.exe`2 GB と同じ大きさの列をストリームできるようになりました ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データ型の最大値)。  
  
別の相違点は、その両方を指定する`-h`と`-y0`これで、オプションの互換性がないことを報告するエラーを生成します。 `-h`、列見出し間に出力する行数を指定し、かつてないと互換性のある`-y0`、ヘッダーは出力されませんが、無視されました。
  
なお`-y0`サーバーと返されるデータのサイズによっては、ネットワークの両方でパフォーマンスの問題を引き起こすことができます。

## <a name="see-also"></a>参照  
[Microsoft ODBC Driver for SQL Server on Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
