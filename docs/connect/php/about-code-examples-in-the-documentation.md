---
title: "ドキュメントのコード例について |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f035c37-0f2e-47d4-94e0-a10774402e82
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d24d29aba9db9d3626a456f87f799e00da1b42cc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="about-code-examples-in-the-documentation"></a>ドキュメントのコード例について
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] ドキュメントのコード例を実行する際に、いくつか注意する点があります。  
  
-   ほぼすべての例では、SQL Server 2005 以降 (バージョン 3.1 を使用している場合は SQL Server 2008 以降) と、AdventureWorks データベースがローカル コンピューターにインストールされていることを前提にしています。  
  
    SQL Server の無償のエディションと評価版をダウンロードする方法については、「 [SQL Server](http://go.microsoft.com/fwlink/?LinkID=120193)」を参照してください。  
  
    AdventureWorks データベースのダウンロード方法については、「 [Microsoft SQL Server のサンプルとコミュニティのプロジェクト](http://go.microsoft.com/fwlink/?LinkID=67739)」を参照してください。  
  
    AdventureWorks データベースをインストールする方法の詳細については、「 [チュートリアル: AdventureWorks データベースのインストール](http://go.microsoft.com/fwlink/?LinkID=65819)」を参照してください。  
  
-   このドキュメントのほぼすべてのコード例では、コマンド ラインから実行することを前提にしています。これにより、すべてのコード例は自動的にテストされます。 PHP をコマンドラインから実行する方法については、「 [コマンドラインからの PHP の使用](http://php.net/manual/en/features.commandline.php)」を参照してください。  
  
-   例はコマンド ラインから実行するよう記述されていますが、各例はスクリプトに変更を加えずに、ブラウザーから呼び出し実行することもできます。 Nice 出力の書式化を実現するで各"\n"を置き換えます"\<\/br >"ブラウザーから呼び出す前に、それぞれの例にします。  
  
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
[Microsoft Drivers for PHP for SQL Server の概要](../../connect/php/overview-of-the-php-sql-driver.md)
  

