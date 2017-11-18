---
title: "PHP SQL ドライバーの読み込み |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- loading the driver
ms.assetid: e5c114c5-8204-49c2-94eb-62ca63f5d3ec
caps.latest.revision: 42
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cb2200b2c5d151981e9dcdf8322dd7c43b91c6ee
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="loading-the-php-sql-driver"></a>PHP SQL ドライバーの読み込み
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このトピックでは、 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] を PHP プロセス領域に読み込む手順について説明します。  
  
ドライバーの読み込みには、2 つのオプションがあります。 ドライバーは、PHP の起動時または PHP スクリプトの実行時に読み込むことができます。  
  
## <a name="moving-the-driver-file-into-your-extension-directory"></a>ドライバー ファイルを拡張機能ディレクトリに移動する  
使用する手順にかかわらず、最初の手順は、PHP ランタイムで検索できるディレクトリにドライバー ファイルを格納することです。 そのため、PHP 拡張機能ディレクトリにドライバー ファイルを格納します。 [でインストールされるドライバー ファイルの一覧については、「](../../connect/php/system-requirements-for-the-php-sql-driver.md) システム要件 (Microsoft SQL Server 用 Drivers for PHP) [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]」を参照してください。  
  
必要に応じて、PHP 構成ファイル (php.ini) にドライバー ファイルのディレクトリの場所の指定を使用して、 **extension_dir**オプション。 たとえば、c:\php\ext ディレクトリにドライバー ファイルを格納する場合は、次のオプションを使用します。  
  
```  
extension_dir = "c:\PHP\ext"  
```  
  
## <a name="loading-the-driver-at-php-startup"></a>PHP の起動時にドライバーを読み込む  
PHP の起動時に [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] を読み込むには、まずドライバー ファイルを拡張機能ディレクトリに移動します。 その後、次の操作を行います。  
  
1.  有効にする、 **SQLSRV**ドライバー、修正**php.ini**拡張機能セクションに次の行を追加するかは、既に存在する行を変更します。  
  
    On Windows (この例は、PHP 7 バージョン 4.0 のスレッド セーフ ドライバーを使用)。 
    ```  
    extension=php_sqlsrv_7_ts.dll  
    ```  
    On Linux (この例では、PECL によってインストールのバージョンを使用します)。 
    ```  
    extension=sqlsrv.so  
    ```  
    有効にする、 **PDO_SQLSRV**ドライバー、修正**php.ini**拡張機能セクションに次の行を追加するかは、既に存在する行を変更します。  
  
    On Windows (この例は、PHP 7 バージョン 4.0 のスレッド セーフ ドライバーを使用)。
    ```  
    extension=php_pdo_sqlsrv_7_ts.dll  
    ```  
    On Linux (この例では、PECL によってインストールのバージョンを使用します)。
    ```  
    extension=pdo_sqlsrv.so  
    ```  
  
2.  使用する場合、 **PDO_SQLSRV**ドライバー、PHP のデータ オブジェクト (PDO) 拡張する必要があります、使用可能な組み込みの拡張機能として、または動的に読み込まれる拡張機能として。 PDO_SQLSRV ドライバーを動的に読み込む必要がある場合、php_pdo.dll (Linux で pdo.so) は、拡張機能ディレクトリに存在する必要があり、次の行を php.ini である必要があります。

    Windows:  
    ```
    extension=php_pdo.dll  
    ```  
    Linux:  
    ```
    extension=pdo.so  
    ```  
  
3.  Web サーバーを再起動します。  
  
> [!NOTE]  
> 呼び出すスクリプトを実行、ドライバーが正常に読み込まれているかどうかを判断するのに[phpinfo()](http://go.microsoft.com/fwlink/?LinkId=108678)です。  
  
**php.ini** ディレクティブの詳細については、 [コア php.ini ディレクティブの説明](http://go.microsoft.com/fwlink/?LinkId=105817)を参照してください。  
  
## <a name="loading-the-driver-at-php-script-runtime"></a>PHP スクリプトの実行時にドライバーを読み込む  
スクリプトの実行時に [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] を読み込むには、まずドライバー ファイルを拡張機能ディレクトリに移動します。 ドライバーのファイル名に一致する PHP スクリプトの先頭に次の行を含めます。  
  
```  
dl('php_pdo_sqlsrv_7_ts.dll');  
```  
  
拡張機能の動的な読み込みに関連する PHP 関数の詳細については、次を参照してください。 [dl](http://go.microsoft.com/fwlink/?LinkId=105818)と[extension_loaded です。](http://go.microsoft.com/fwlink/?LinkId=105819)  
  
## <a name="see-also"></a>参照  
[作業の開始](../../connect/php/getting-started-with-the-php-sql-driver.md)
[でインストールされるドライバー ファイルの一覧については、「](../../connect/php/system-requirements-for-the-php-sql-driver.md)
[プログラミング ガイド](../../connect/php/programming-guide-for-php-sql-driver.md)
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  
  

