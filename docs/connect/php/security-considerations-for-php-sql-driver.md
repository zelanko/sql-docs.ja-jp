---
title: "PHP SQL ドライバーのセキュリティに関する考慮事項 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security considerations
ms.assetid: a8c1a570-9204-454f-b94c-ba34f54d487c
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2a7423bcfcfd28073840ad7f8c9ee2e7424507bc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="security-considerations-for-php-sql-driver"></a>セキュリティに関する考慮事項
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このトピックでは、 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]を使用するアプリケーションの開発、配置、および実行に固有のセキュリティの考慮事項について説明します。 SQL Server セキュリティの詳細については、「 [データのセキュリティと準拠](http://go.microsoft.com/fwlink/?LinkId=129225)」を参照してください。  
  
## <a name="connect-using-windows-authentication"></a>Windows 認証を使用した接続  
次の理由のために可能な場合は、SQL Server への接続に Windows 認証を使用する必要があります。  
  
-   **認証時に、資格情報はネットワークに渡されません。** ユーザー名とパスワードは、データベース接続文字列に埋め込まれません。 これは、悪意のあるユーザーや攻撃者が、ネットワークを監視したり、構成ファイル内の接続文字列を表示したりして、資格情報を取得できないことを意味します。  
  
-   **ユーザーは、アカウント管理を一元化される可能性があります。** パスワードの有効期限、パスワードの最小の長さ、および複数の無効なログイン要求後のアカウント ロックアウトなど、セキュリティ ポリシーが強制されます。  
  
Windows 認証でサーバーに接続する方法については、「 [方法: Windows 認証を使用した接続](../../connect/php/how-to-connect-using-windows-authentication.md)」を参照してください。  
  
Windows 認証を使用して接続する場合、SQL Server が Kerberos 認証プロトコルを使用できるように、お客様の環境を構成することをお勧めします。 詳細については、「 [SQL Server 2005 のインスタンスへのリモート接続を作成するときに、Kerberos 認証を使用していることを確認する方法](http://go.microsoft.com/fwlink/?LinkId=121862) 」または「 [Kerberos 認証と SQL Server](http://go.microsoft.com/fwlink/?LinkId=129226)」を参照してください。  
  
## <a name="use-encrypted-connections-when-transferring-sensitive-data"></a>重要なデータの転送時に暗号化された接続を使用する  
重要なデータを送信するとき、または SQL Server から取得するときは、暗号化された接続を使用する必要があります。 暗号化された接続を有効にする方法については、次を参照してください。[データベース エンジン (SQL Server 構成マネージャー) に暗号化接続の有効化する方法](http://go.microsoft.com/fwlink/?LinkId=121864)です。 セキュリティで保護された接続を [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]と確立するには、サーバーに接続するときに暗号化接続の属性を使用します。 接続属性の詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。  
  
## <a name="use-parameterized-queries"></a>パラメーター化クエリの使用  
パラメーター化クエリを使用して、SQL インジェクション攻撃のリスクを軽減します。 パラメーター化クエリを実行する例については、「 [How to: Perform Parameterized Queries](../../connect/php/how-to-perform-parameterized-queries.md)」を参照してください。  
  
SQL インジェクション攻撃および関連するセキュリティの考慮事項の詳細については、「 [SQL インジェクション](http://go.microsoft.com/fwlink/?LinkId=104224)」を参照してください。  
  
## <a name="do-not-accept-server-or-connection-string-information-from-end-users"></a>エンド ユーザーからのサーバーまたは接続文字列の情報を許可しない  
エンド ユーザーがアプリケーションにサーバーまたは接続文字列の情報を送信できないように、アプリケーションを作成します。 サーバーと接続文字列の情報に対する厳密な制御を維持すると、悪意のある活動の危険を回避できます。  
  
## <a name="turn-warningsaserrors-on-during-application-development"></a>アプリケーション開発時に WarningsAsErrors をオンにする  
ドライバーで発行される警告がエラーとして処理されるように、 **WarningsAsErrors** 設定を **true** に設定してアプリケーションを開発します。 この設定を行うと、アプリケーションを展開する前に、警告に対処することができます。 詳細については、「 [Handling Errors and Warnings](../../connect/php/handling-errors-and-warnings.md)」を参照してください。  
  
## <a name="secure-logs-for-deployed-application"></a>展開済みアプリケーションのログをセキュリティで保護する  
展開済みアプリケーションでは、ログがセキュリティで保護された場所に書き込まれること、またはログ記録がオフになっていることを確認します。 この確認を行うと、エンドユーザーがログ ファイルに書き込まれた情報にアクセスすることを防ぐことができます。 詳細については、「 [Logging Activity](../../connect/php/logging-activity.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[プログラミング ガイド](../../connect/php/programming-guide-for-php-sql-driver.md)
  

