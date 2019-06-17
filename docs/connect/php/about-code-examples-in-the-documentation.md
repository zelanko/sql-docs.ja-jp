---
title: ドキュメントのコード例について |Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3f035c37-0f2e-47d4-94e0-a10774402e82
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e2b9178b057d7f8a2a4c9c663101c99df1d468df
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66795847"
---
# <a name="about-code-examples-in-the-documentation"></a>ドキュメントのコード例について
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

## <a name="remarks-about-the-code-examples"></a>コード例については、「解説」
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] ドキュメントのコード例を実行する際に、いくつか注意する点があります。  
  
-   ほぼすべての例では、SQL Server 2008 またはそれ以降、および AdventureWorks データベースがローカル コンピューターにインストールされていることを前提としています。  
  
    SQL Server の無償のエディションと評価版をダウンロードする方法については、「 [SQL Server](https://go.microsoft.com/fwlink/?LinkID=120193)」を参照してください。  
  
    ダウンロードして、AdventureWorks データベースをインストールする方法については、次を参照してください。、 [AdventureWorks SQL Server のサンプル Github リポジトリ ページ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works)します。
  
-   このドキュメントのほぼすべてのコード例では、コマンド ラインから実行することを前提にしています。これにより、すべてのコード例は自動的にテストされます。 PHP をコマンドラインから実行する方法については、「 [コマンドラインからの PHP の使用](https://php.net/manual/en/features.commandline.php)」を参照してください。  
  
-   例はコマンド ラインから実行するようになっていますが、各例はスクリプトに変更を加えずに、ブラウザーから呼び出し実行することもできます。 出力を適切に書式設定で各"\n"を置き換えます。"\<\/br >"ブラウザーから呼び出す前に、それぞれの例です。  
  
-   各例の目的を絞るため、すべての例で正しいエラー処理はされていません。 **sqlsrv** 関数または PDO メソッドへのすべての呼び出しにエラーがないか確認し、アプリケーションの要件に従って処理することが推奨されます。  
  
    エラーが発生した場合、次のコード行を使用してスクリプトを終了すると、エラー情報を簡単に得ることができます。  
  
    ```  
    die( print_r( sqlsrv_errors(), true));  
    ```  
  
    または PDO を使用している場合は、次のとおりです。  
  
    ```  
    print_r ($stmt->errorInfo());  
    die();  
    ```  
  
    エラーおよび警告の処理方法の詳細については、「 [エラーおよび警告の処理](../../connect/php/handling-errors-and-warnings.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[Microsoft SQL Server 用 Drivers for PHP の概要](../../connect/php/overview-of-the-php-sql-driver.md)
  
