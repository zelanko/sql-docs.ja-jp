---
title: ドキュメントのコード例について | Microsoft Docs
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
ms.openlocfilehash: dc76cee723c11d49a4d6149a7c3a1df4cedbc256
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "68015171"
---
# <a name="about-code-examples-in-the-documentation"></a>ドキュメントのコード例について
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

## <a name="remarks-about-the-code-examples"></a>コード例についての解説
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] ドキュメントのコード例を実行する際に、いくつか注意する点があります。  
  
-   ほぼすべての例では、SQL Server 2008 以降 と、AdventureWorks データベースがローカル コンピューターにインストールされていることを前提にしています。  
  
    SQL Server の無償のエディションと評価版をダウンロードする方法については、「 [SQL Server](https://go.microsoft.com/fwlink/?LinkID=120193)」を参照してください。  
  
    AdventureWorks データベースをダウンロードしてインストールする方法の詳細については、[SQL Server サンプルの Github リポジトリの AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) に関するページを参照してください。
  
-   このドキュメントのほぼすべてのコード例では、コマンド ラインから実行することを前提にしています。これにより、すべてのコード例は自動的にテストされます。 PHP をコマンドラインから実行する方法については、「 [コマンドラインからの PHP の使用](https://php.net/manual/en/features.commandline.php)」を参照してください。  
  
-   例はコマンド ラインから実行するようになっていますが、各例はスクリプトに変更を加えずに、ブラウザーから呼び出し実行することもできます。 出力を適切に書式設定するには、ブラウザーから呼び出す前に、各例において各 "\n" を "\<\/br>" に置き換えます。  
  
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
  
