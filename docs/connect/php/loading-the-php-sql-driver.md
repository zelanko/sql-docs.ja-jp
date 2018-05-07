---
title: SQL server 用 Microsoft Drivers for PHP 読み込む |Microsoft ドキュメント
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
helpviewer_keywords:
- loading the driver
ms.assetid: e5c114c5-8204-49c2-94eb-62ca63f5d3ec
caps.latest.revision: 42
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7890c38877d05a69118a7c61ffe7261d1c9e91e2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="loading-the-microsoft-drivers-for-php-for-sql-server"></a>SQL Server 用 Microsoft Drivers for PHP を読み込む
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このページは読み込む手順について説明、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]を PHP プロセス領域です。  
  
構築済みのドライバーをダウンロードするには、プラットフォームからの[Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) Github プロジェクト ページ。 各インストール パッケージには、スレッドとスレッド以外のバリアントに SQLSRV および PDO_SQLSRV のドライバー ファイルが含まれています。 Windows では、ことも 32 ビットおよび 64 ビットのバリエーションで使用できます。 参照してください[Microsoft Drivers for PHP for SQL Server のシステム要件](../../connect/php/system-requirements-for-the-php-sql-driver.md)各パッケージに含まれているドライバー ファイルの一覧についてはします。 ドライバー ファイルには、PHP のバージョン、アーキテクチャ、および PHP 環境内の threadedness を一致する必要があります。

Linux および macOS、ドライバーまたはをインストールできるで見られる PECL を使用して、[インストール チュートリアル](../../connect/php/installation-tutorial-linux-mac.md)です。
  
## <a name="moving-the-driver-file-into-your-extension-directory"></a>ドライバー ファイルを拡張機能ディレクトリに移動する  
ドライバー ファイルは、PHP ランタイムが検索できる場所のディレクトリに存在する必要があります。 既定のディレクトリを検索するには、実行 - 既定 PHP 拡張機能ディレクトリにドライバー ファイルを格納する方が簡単`php -i | sls extension_dir`Windows 上または`php -i | grep extension_dir`Linux/macos です。 既定の拡張機能ディレクトリを使用していない場合は、PHP 構成ファイル (php.ini) にディレクトリを指定を使用して、 **extension_dir**オプション。 たとえば、Windows、ドライバー ファイルを配置した場合は、`c:\php\ext`ディレクトリ、php.ini に次の行を追加します。
  
```  
extension_dir = "c:\PHP\ext"  
```

## <a name="loading-the-driver-at-php-startup"></a>PHP の起動時にドライバーを読み込む  
PHP が開始されたときに、SQLSRV ドライバーを読み込む、まず、拡張機能ディレクトリにドライバー ファイルを移動します。 その後、次の操作を行います。  
  
1.  有効にする、 **SQLSRV**ドライバー、修正**php.ini**に拡張セクションを次の行を追加するには、適切なファイル名を変更します。  
  
    Windows: 
    ```  
    extension=php_sqlsrv_72_ts.dll  
    ```  
    Linux では、ディストリビューションのビルド済みのバイナリをダウンロードしている場合。 
    ```  
    extension=php_sqlsrv_72_nts.so  
    ```
    SQLSRV バイナリ ソースからまたは PECL をコンパイルした場合に代わりに名前を付ける sqlsrv.so。
    ```
    extension=sqlsrv.so
    ```
  
2.  有効にする、 **PDO_SQLSRV**ドライバー、PHP のデータ オブジェクト (PDO) 拡張する必要があります、使用可能な組み込みの拡張機能として、または動的に読み込まれる拡張機能として。

    Windows では、構築済みの PHP バイナリ付属組み込まれており、PDO のため php.ini ファイルを読み込むことを変更する必要はありません。 名前は場合、ただし、ソースからの PHP をコンパイルして構築する別個の PDO 拡張機能を指定、 `php_pdo.dll`、および拡張機能ディレクトリにコピーし、次の行を php.ini に追加する必要があります。  
    ```
    extension=php_pdo.dll  
    ```
    Linux は、システムのパッケージ マネージャーを使用して PHP がインストールされている場合、PDO は pdo.so をという名前の動的に読み込まれる拡張としてインストール可能性があります。 Pdo は、PDO_SQLSRV 拡張機能は、前に読み込む必要があるし、読み込みが失敗します。 拡張機能が通常読み込まれ、個々 の .ini ファイルを使用して php.ini 後にこれらのファイルは読み取りです。 したがって、pdo.so が独自の .ini ファイルから読み込まれている場合、PDO の後に、PDO_SQLSRV ドライバーを読み込み、別のファイルが必要です。 

    参照するディレクトリ拡張機能に固有の .ini ファイルが存在して、実行`php --ini`の下に表示されているディレクトリに注意してください、`Scan for additional .ini files in:`です。 Pdo.so に必要なファイルを検索 - 10 pdo.ini など、番号が付いて可能性があります。 数値のプレフィックスがないファイルがアルファベット順に読み込まれるときに、数値のプレフィックスは、.ini ファイルの読み込み順序を示します。 30 pdo_sqlsrv.ini (任意の数も pdo.ini works のプレフィックスを 1 より大きい) または pdo_sqlsrv.ini (pdo.ini は数値でプレフィックスが付いていない) 場合、呼び出し PDO_SQLSRV ドライバー ファイルを読み込んでとファイル名を変更するのには、次の行を追加するファイルを作成します。適切な。  
    ```
    extension=php_pdo_sqlsrv_72_nts.so
    ```
    として SQLSRV、PDO_SQLSRV バイナリ ソースからまたは PECL、コンパイルした場合に代わりにある名前付き pdo_sqlsrv.so:
    ```
    extension=pdo_sqlsrv.so
    ```
    このファイルを他の .ini ファイルを格納するディレクトリにコピーします。 

    組み込み PDO のサポートを備えたソースからの PHP をコンパイルした場合、別の .ini ファイルを必要としないし、上の適切な行を php.ini に追加することができます。
  
3.  Web サーバーを再起動します。  
  
> [!NOTE]  
> 呼び出すスクリプトを実行、ドライバーが正常に読み込まれているかどうかを判断するのに[phpinfo()](http://php.net/manual/en/function.phpinfo.php)です。  
  
詳細については**php.ini**ディレクティブを参照してください[コア php.ini ディレクティブの説明](http://php.net/manual/en/ini.core.php)です。  
  
## <a name="see-also"></a>参照  
[入門 Microsoft Drivers for PHP for SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[システム要件の Microsoft Drivers for PHP for SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md)

[For PHP for SQL Server の Microsoft drivers ガイドのプログラミング](../../connect/php/programming-guide-for-php-sql-driver.md)

[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)

[PDO_SQLSRV ドライバー API リファレンス](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
