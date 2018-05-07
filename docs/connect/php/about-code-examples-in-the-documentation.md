---
title: ドキュメントのコード例について |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3f035c37-0f2e-47d4-94e0-a10774402e82
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3b3f6112d56dbb8989438730f50b11e733f71ed7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="about-code-examples-in-the-documentation"></a>ドキュメントのコード例について
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

## <a name="remarks-about-the-code-examples"></a>コード例については、「解説」
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] ドキュメントのコード例を実行する際に、いくつか注意する点があります。  
  
-   ほぼすべての例では、SQL Server 2008 以降および AdventureWorks データベースがローカル コンピューターにインストールされていることを前提としています。  
  
    SQL Server の無償のエディションと評価版をダウンロードする方法については、「 [SQL Server](http://go.microsoft.com/fwlink/?LinkID=120193)」を参照してください。  
  
    ダウンロードして、AdventureWorks データベースをインストールする方法については、次を参照してください。、 [SQL Server のサンプルの Github リポジトリに AdventureWorks ページ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works)です。
  
-   このドキュメントのほぼすべてのコード例では、コマンド ラインから実行することを前提にしています。これにより、すべてのコード例は自動的にテストされます。 PHP をコマンドラインから実行する方法については、「 [コマンドラインからの PHP の使用](http://php.net/manual/en/features.commandline.php)」を参照してください。  
  
-   例については、コマンドラインから実行するものでは、それぞれの例はスクリプトに変更を加えずに、ブラウザーから呼び出すことによって実行できます。 出力を適切にフォーマットするで各"\n"を置き換えます。"\<\/br >"ブラウザーから呼び出す前に、それぞれの例にします。  
  
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
  
