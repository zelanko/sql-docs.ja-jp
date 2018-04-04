---
title: セキュリティに関する考慮事項 Microsoft Drivers for PHP for SQL Server |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security considerations
ms.assetid: a8c1a570-9204-454f-b94c-ba34f54d487c
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ad90c4e05168e54ce9be6b8324539db67d1ccb7e
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="security-considerations-for-the-microsoft-drivers-for-php-for-sql-server"></a>セキュリティに関する考慮事項 Microsoft Drivers for PHP for SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このトピックでは、 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]を使用するアプリケーションの開発、配置、および実行に固有のセキュリティの考慮事項について説明します。 詳細については SQL Server のセキュリティについてを参照してください。 [SQL Server のセキュリティの概要](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/overview-of-sql-server-security)です。  
  
## <a name="connect-using-windows-authentication"></a>Windows 認証を使用した接続  
次の理由のために可能な場合は、SQL Server への接続に Windows 認証を使用する必要があります。  
  
-   **認証時に、資格情報はネットワークに渡されません。** ユーザー名とパスワードは、データベース接続文字列に埋め込まれません。 そのため、悪意のあるユーザーや攻撃者ことはできません資格情報を取得または構成ファイル内の接続文字列を表示して、ネットワークを監視します。  
  
-   **ユーザーは、アカウント管理を一元化される可能性があります。** パスワードの有効期限、パスワードの最小の長さ、および複数の無効なログイン要求後のアカウント ロックアウトなど、セキュリティ ポリシーが強制されます。  
  
Windows 認証でサーバーに接続する方法については、「 [方法: Windows 認証を使用した接続](../../connect/php/how-to-connect-using-windows-authentication.md)」を参照してください。  
  
Windows 認証を使用して接続する場合、SQL Server が Kerberos 認証プロトコルを使用できるように、お客様の環境を構成することをお勧めします。 詳細については、次を参照してください。 [SQL Server 2005 のインスタンスへのリモート接続を作成するときに、Kerberos 認証を使用するかどうかを確認する方法について](https://support.microsoft.com/en-ca/help/909801/how-to-make-sure-that-you-are-using-kerberos-authentication-when-you-c)または[Kerberos 認証と SQL Server](https://msdn.microsoft.com/library/cc280744.aspx)です。  
  
## <a name="use-encrypted-connections-when-transferring-sensitive-data"></a>重要なデータの転送時に暗号化された接続を使用する  
重要なデータを送信するとき、または SQL Server から取得するときは、暗号化された接続を使用する必要があります。 暗号化された接続を有効にする方法については、次を参照してください。[データベース エンジン (SQL Server 構成マネージャー) に暗号化接続の有効化する方法](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)です。 セキュリティで保護された接続を [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]と確立するには、サーバーに接続するときに暗号化接続の属性を使用します。 接続属性の詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。  
  
## <a name="use-parameterized-queries"></a>パラメーター化クエリの使用  
パラメーター化クエリを使用して、SQL インジェクション攻撃のリスクを軽減します。 パラメーター化クエリを実行する例については、「 [How to: Perform Parameterized Queries](../../connect/php/how-to-perform-parameterized-queries.md)」を参照してください。  
  
SQL インジェクション攻撃および関連するセキュリティの考慮事項の詳細については、次を参照してください。 [SQL インジェクション](https://msdn.microsoft.com/library/ms161953.aspx)です。  
  
## <a name="do-not-accept-server-or-connection-string-information-from-end-users"></a>エンド ユーザーからのサーバーまたは接続文字列の情報を許可しない  
エンド ユーザーがアプリケーションにサーバーまたは接続文字列の情報を送信できないように、アプリケーションを作成します。 サーバーと接続文字列の情報に対する厳密な制御を維持すると、悪意のある活動の危険を回避できます。  
  
## <a name="turn-warningsaserrors-on-during-application-development"></a>アプリケーション開発時に WarningsAsErrors をオンにする  
ドライバーで発行される警告がエラーとして処理されるように、 **WarningsAsErrors** 設定を **true** に設定してアプリケーションを開発します。 この設定を行うと、アプリケーションを展開する前に、警告に対処することができます。 詳細については、「 [Handling Errors and Warnings](../../connect/php/handling-errors-and-warnings.md)」を参照してください。  
  
## <a name="secure-logs-for-deployed-application"></a>展開済みアプリケーションのログをセキュリティで保護する  
展開済みアプリケーションでは、ログがセキュリティで保護された場所に書き込まれること、またはログ記録がオフになっていることを確認します。 この確認を行うと、エンドユーザーがログ ファイルに書き込まれた情報にアクセスすることを防ぐことができます。 詳細については、「 [Logging Activity](../../connect/php/logging-activity.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[For PHP for SQL Server の Microsoft drivers ガイドのプログラミング](../../connect/php/programming-guide-for-php-sql-driver.md)
  
