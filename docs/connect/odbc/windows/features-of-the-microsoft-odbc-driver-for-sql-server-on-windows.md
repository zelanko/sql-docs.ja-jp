---
title: Windows での Microsoft ODBC Driver for SQL Server の機能 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e56d57cb3df19df1cbf09811ebfebca66efe51b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47677580"
---
# <a name="features-of-the-microsoft-odbc-driver-for-sql-server-on-windows"></a>Microsoft ODBC Driver for SQL Server on Windows の機能
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

    
## <a name="microsoft-odbc-driver-131-for-sql-server-on-windows"></a>Windows の Microsoft ODBC Driver 13.1 for SQL Server

ODBC Driver 13.1 for SQL Server では、以前のバージョン (11) のすべての機能が含まれていて、Microsoft SQL Server 2016 と組み合わせて使用する場合は、Always Encrypted と Azure Active Directory の認証のサポートを追加します。  
  
Always Encrypted を使用すると、クライアントは SQL Server に暗号化キーを開示することなく、クライアント アプリケーション内の機密データを暗号化することができます。 クライアント コンピューターにインストールされている、Always Encrypted が有効のドライバーは、SQL Server クライアント アプリケーション内の機密データを自動的に暗号化および暗号化解除することで、この処理を実行します。 ドライバーは、SQL Server にデータを渡す前に機密性の高い列のデータを暗号化し、アプリケーションに対するセマンティクスが維持されるように自動的にクエリを書き換えます。 同様に、ドライバーはクエリ結果に含まれている暗号化されたデータベース列に格納されているデータを透過的に暗号化解除します。 詳しくは、「[Using Always Encrypted with the ODBC Driver](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)」(ODBC ドライバーでの Always Encrypted の使用) をご覧ください。
 
Azure Active Directory を Azure Active Directory (Azure AD での id を使用して Microsoft Azure SQL Database と Microsoft SQL Server 2016 への接続のためのメカニズムとして Azure Active Directory 認証を使用するには、ユーザー、DBA が、アプリケーション プログラマ). 詳細については、次を参照してください。[を使用して Azure Active Directory と ODBC ドライバー](../../../connect/odbc/using-azure-active-directory.md)、および[への SQL Database または SQL データ ウェアハウスを使用して Azure Active Directory 認証して](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/)します。   
  
## <a name="microsoft-odbc-driver-11-for-sql-server-on-windows"></a>Windows の Microsoft ODBC Driver 11 for SQL Server  

ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] には、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に付属の [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]Native Client ODBC ドライバーのすべての機能が含まれています。 詳細については、「 [SQL Server Native Client プログラミング](../../../relational-databases/native-client/sql-server-native-client-programming.md)」を参照してください。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、Windows オペレーティング システムに付属の ODBC ドライバーに基づいています。 詳細については、「 [Windows Data Access Components SDK](http://msdn.microsoft.com/library/aa968814(VS.85).aspx)」を参照してください。  
  
ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のこのリリースには、次の新機能が含まれています。  
  
### <a name="bcpexe-l-option-for-specifying-a-login-timeout"></a>ログイン タイムアウトを指定するための bcp.exe の – l オプション
 
- l オプションでは、サーバーへの接続の試行時に、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] への `bcp.exe` のログインがタイムアウトするまでの秒数を指定します。 既定のログイン タイムアウトは、15 秒です。 ログイン タイムアウトは、0 から 65,534 の数値にする必要があります。 指定した値が数値以外の場合、または範囲外の場合、`bcp.exe` はエラー メッセージを生成します。 値 0 は、無限のタイムアウトを指定します。 (約) 10 秒未満のログイン タイムアウトは信頼できません。  
  
### <a name="driver-aware-connection-pooling"></a>ドライバー対応接続プール  
ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、[ドライバー対応の接続プール](http://msdn.microsoft.com/library/hh405031(VS.85).aspx)をサポートしています。 詳細については、「 [Driver-Aware Connection Pooling in the ODBC Driver for SQL Server](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)」を参照してください。  
  
### <a name="asynchronous-execution-notification-method"></a>非同期実行 (通知方法)  
ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、[非同期実行 (通知方法)](http://msdn.microsoft.com/library/hh405038(VS.85).aspx) をサポートしています。 使用例については、「[非同期実行 &#40;通知方法&#41; の例](../../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md)」を参照してください。  
  
### <a name="connection-resiliency"></a>接続の回復
アプリケーションを Microsoft Azure SQL データベースに接続されたままにするため、Windows 上の ODBC ドライバーは、アイドル状態の接続を復元できます。 詳細については、「 [Connection Resiliency in the Windows ODBC Driver](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)」を参照してください。  
  
## <a name="behavior-changes"></a>動作の変更

[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client の場合、`-y0`オプション`sqlcmd.exe`表示幅が 0 の場合、1 MB で切り捨てられる出力を原因となった。
  
ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以降では、`–y0` を指定したときに、1 つの列で取得できるデータの量に制限がなくなりました。 `sqlcmd.exe` は、最大 2 GB ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のデータ型の最大値) の列をストリームするようになりました。  
  
別の相違点は、その両方を指定する`-h`と`-y0`オプションは互換性がないことを報告するエラーが生成されます。 列見出し間に出力する行数を指定する `-h` は、`-y0` と互換性がなく、ヘッダーは出力されませんでしたが、無視されました。
  
`-y0` を使用すると、返されるデータのサイズによっては、サーバーとネットワークの両方に重大なパフォーマンスの問題が発生する可能性があることに注意してください。

## <a name="see-also"></a>参照  
[Microsoft ODBC Driver for SQL Server on Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
