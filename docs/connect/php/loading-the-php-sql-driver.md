---
title: SQL Server 用 Microsoft Drivers for PHP を読み込む | Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
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
ms.openlocfilehash: 8f257439fe011948ac264ac7aea33975abcf06dd
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38006752"
---
# <a name="loading-the-microsoft-drivers-for-php-for-sql-server"></a>SQL Server 用 Microsoft Drivers for PHP を読み込む
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このトピックでは、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] を PHP プロセス領域に読み込む手順について説明します。  
  
事前構築済みのドライバーをダウンロードするには、プラットフォームから、 [Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) Github プロジェクト ページ。 各インストール パッケージには、スレッドおよびスレッド以外のバリエーションで SQLSRV と PDO_SQLSRV ドライバーのファイルが含まれています。 Windows、これらは 32 ビットおよび 64 ビットのバリアントで入手できます。 参照してください[Microsoft Drivers for PHP for SQL Server のシステム要件](../../connect/php/system-requirements-for-the-php-sql-driver.md)各パッケージに含まれるドライバー ファイルの一覧についてはします。 PHP バージョン、アーキテクチャ、および PHP 環境の threadedness、ドライバー ファイルが一致する必要があります。

Linux と macOS の場合は、ドライバーまたはインストールできるで見つかった PECL を使用して、[インストール チュートリアル](../../connect/php/installation-tutorial-linux-mac.md)します。
  
## <a name="moving-the-driver-file-into-your-extension-directory"></a>ドライバー ファイルを拡張機能ディレクトリに移動する  
ドライバー ファイルは、PHP ランタイムが検索できるディレクトリである必要があります。 既定のディレクトリを見つけを実行する - 既定 PHP 拡張機能ディレクトリにドライバー ファイルを配置する最も簡単な`php -i | sls extension_dir`で Windows または`php -i | grep extension_dir`Linux/macos でします。 既定の拡張機能ディレクトリを使用していない場合は、ディレクトリを指定、PHP 構成ファイル (php.ini) を使用して、 **extension_dir**オプション。 ドライバー ファイルを配置した場合、Windows などの`c:\php\ext`ディレクトリ、次の行を php.ini に追加。
  
```  
extension_dir = "c:\PHP\ext"  
```

## <a name="loading-the-driver-at-php-startup"></a>PHP の起動時にドライバーを読み込む  
PHP の起動時に SQLSRV ドライバーを読み込むには、まずドライバー ファイルを拡張機能ディレクトリに移動します。 その後、次の操作を行います。  
  
1.  有効にする、 **SQLSRV**ドライバー、変更**php.ini**拡張機能セクションに次の行を追加することで、適切なファイル名を変更します。  
  
    Windows の場合: 
    ```  
    extension=php_sqlsrv_72_ts.dll  
    ```  
    Linux では、お使いのディストリビューションの事前構築済みのバイナリをダウンロードしている場合。 
    ```  
    extension=php_sqlsrv_72_nts.so  
    ```
    SQLSRV バイナリのソースからまたは PECL をコンパイルした場合、代わりに名前が付けられます sqlsrv.so:
    ```
    extension=sqlsrv.so
    ```
  
2.  有効にする、 **PDO_SQLSRV**ドライバー、PHP のデータ オブジェクト (PDO) 拡張できる必要があります、組み込みの拡張機能として、または動的に読み込まれた拡張機能として。

    、Windows のビルド済みの PHP バイナリ付属組み込まれており、PDO ので php.ini ファイルを読み込むことを変更する必要はありません。 ただし、コンパイルされたソースからの PHP が、構築する個別の PDO 拡張機能を指定し場合、その名前は`php_pdo.dll`、拡張機能ディレクトリにコピーされ、次の行を php.ini に追加する必要があります。  
    ```
    extension=php_pdo.dll  
    ```
    Linux は、システムのパッケージ マネージャーを使用して PHP がインストールされている場合、PDO は pdo.so という名前の動的に読み込まれた拡張機能としてインストール可能性があります。 PDO 拡張機能は、PDO_SQLSRV 拡張する前に読み込む必要があるし、読み込みが失敗します。 拡張機能の個々 の .ini ファイルを使用するが、通常は読み込まれ、php.ini 後にこれらのファイルが読み取られます。 そのため、pdo.so が独自の .ini ファイルから読み込まれると、PDO 後 PDO_SQLSRV ドライバーを読み込む別のファイルが必要です。 

    ディレクトリ拡張機能に固有の .ini ファイルが配置されているを確認するには実行`php --ini`ディレクトリの下に一覧表示に注意してくださいと`Scan for additional .ini files in:`します。 Pdo.so に読み込まれるファイルが見つかりません--10 pdo.ini などの番号付けは可能性があります。 数値のプレフィックスがないファイルがアルファベット順に読み込まれるときに、数値のプレフィックスは、.ini ファイルの読み込み順序を示します。 Pdo_sqlsrv.ini (pdo.ini は数値でプレフィックスが付いていない) 場合、または 30 pdo_sqlsrv.ini (任意の数も pdo.ini works のプレフィックスを超える) のいずれかと呼ばれる PDO_SQLSRV ドライバー ファイルを読み込んでとしてファイル名を変更するのには、次の行を追加するファイルを作成します。適切な。  
    ```
    extension=php_pdo_sqlsrv_72_nts.so
    ```
    としてでは、SQLSRV、PDO_SQLSRV バイナリまたは PECL、ソースからコンパイルした場合、代わりに名前が付けられます pdo_sqlsrv.so:
    ```
    extension=pdo_sqlsrv.so
    ```
    このファイルを別の .ini ファイルを含むディレクトリにコピーします。 

    PDO の組み込みサポートを使用してソースからの PHP をコンパイルした場合、別の .ini ファイルを必要としないし、上の適切な行を php.ini に追加することができます。
  
3.  Web サーバーを再起動します。  
  
> [!NOTE]  
> ドライバーが正常に読み込まれたかどうかを判断するために、[phpinfo()](http://php.net/manual/en/function.phpinfo.php) を呼び出すスクリプトを実行します。  
  
**php.ini** ディレクティブの詳細については、[コア php.ini ディレクティブ](http://php.net/manual/en/ini.core.php)に関するページを参照してください。  
  
## <a name="see-also"></a>参照  
[概要 Microsoft Drivers for PHP for SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Microsoft SQL Server 用 Drivers for PHP のシステム要件](../../connect/php/system-requirements-for-the-php-sql-driver.md)

[For PHP for SQL Server のプログラミング、Microsoft ドライバーのガイド](../../connect/php/programming-guide-for-php-sql-driver.md)

[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)

[PDO_SQLSRV ドライバー API リファレンス](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
