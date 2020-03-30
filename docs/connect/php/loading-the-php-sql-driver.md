---
title: SQL Server 用 Microsoft Drivers for PHP を読み込む | Microsoft Docs
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- loading the driver
ms.assetid: e5c114c5-8204-49c2-94eb-62ca63f5d3ec
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e3c6614425cf8796bd7ec462a62f9410b9ca5857
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67936380"
---
# <a name="loading-the-microsoft-drivers-for-php-for-sql-server"></a>SQL Server 用 Microsoft Drivers for PHP を読み込む
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このトピックでは、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] を PHP プロセス領域に読み込む手順について説明します。  
  
事前に作成された、ご使用のプラットフォーム用ドライバーは、[Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) Github プロジェクト ページからダウンロードできます。 各インストール パッケージには、スレッド化および非スレッド化されたバリアント形式の SQLSRV および PDO_SQLSRV ドライバー ファイルが含まれています。 Windows では、32 ビットと 64 ビットのバリアントでも使用できます。 各パッケージに含まれるドライバー ファイルの一覧については、「[Microsoft SQL Server 用 Drivers for PHP のシステム要件](../../connect/php/system-requirements-for-the-php-sql-driver.md)」を参照してください。 ドライバー ファイルは、PHP 環境の PHP バージョン、アーキテクチャ、スレッド性と一致する必要があります。

Linux と macOS では、[インストール チュートリアル](../../connect/php/installation-tutorial-linux-mac.md)に記載されているように、PECL を使用してドライバーをインストールすることもできます。

PHP をビルドするとき、または `phpize` を使用して、ソースからドライバーをビルドすることもできます。 ソースからドライバーをビルドすることを選択した場合、`--enable-sqlsrv=static --with-pdo_sqlsrv=static` (Linux および macOS の場合) または `--enable-sqlsrv=static --with-pdo-sqlsrv=static`(Windows の場合) を `./configure` コマンドに追加することにより、共有拡張機能としてビルドするのではなく、ドライバーを PHP に静的にビルドするオプションがあります。 PHP ビルド システムおよび `phpize` の詳細については、[PHP のドキュメント](http://php.net/manual/install.php)を参照してください。
  
## <a name="moving-the-driver-file-into-your-extension-directory"></a>ドライバー ファイルを拡張機能ディレクトリに移動する  
ドライバー ファイルは、PHP ランタイムがあるディレクトリに配置する必要があります。 既定の PHP 拡張機能ディレクトリにドライバー ファイルを配置するのが最も簡単です。既定のディレクトリを検索するには、`php -i | sls extension_dir`(Windows 上) または `php -i | grep extension_dir` (Linux または macOS 上) を実行します。 既定の拡張機能ディレクトリを使用していない場合は、PHP 構成ファイル (php.ini) で、**extension_dir** オプションを使用してディレクトリを指定します。 たとえば、Windows で、ドライバーファイルを `c:\php\ext` ディレクトリに配置している場合、次の行を php.ini に追加します。
  
```  
extension_dir = "c:\PHP\ext"  
```

## <a name="loading-the-driver-at-php-startup"></a>PHP の起動時にドライバーを読み込む  
PHP の起動時に SQLSRV ドライバーを読み込むには、まずドライバー ファイルを拡張機能ディレクトリに移動します。 その後、次の操作を行います。  
  
1.  **SQLSRV** ドライバーを有効にするには、次の行を拡張機能セクションに追加して **php.ini** を変更し、必要に応じてファイル名を変更します。  
  
    Windows の場合: 
    ```  
    extension=php_sqlsrv_72_ts.dll  
    ```  
    Linux では、ディストリビューション用に事前に作成されたバイナリをダウンロードしている場合、次のようになります。 
    ```  
    extension=php_sqlsrv_72_nts.so  
    ```
    ソースから、または PECL を使用して SQLSRV バイナリをコンパイルした場合、代わりに sqlsrv.so という名前が付けられます。
    ```
    extension=sqlsrv.so
    ```
  
2.  **PDO_SQLSRV** ドライバーを有効にするには、PHP Data Objects (PDO) 拡張機能を組み込みの拡張機能として、または動的に読み込まれる拡張機能として使用できるようにする必要があります。

    Windows では、事前に作成された PHP バイナリに組み込みの PDO が付属しているため、php.ini を変更して PDO を読み込む必要はありません。 ただし、ソースから PHP をコンパイルし、ビルドする別の PDO 拡張機能を指定した場合は、PDO に `php_pdo.dll` という名前が付けられます。それを拡張ディレクトリにコピーして、php.ini に次の行を追加する必要があります。  
    ```
    extension=php_pdo.dll  
    ```
    Linux では、システムのパッケージマネージャーを使用して PHP をインストールした場合、PDO は pdo.so という名前の動的に読み込まれた拡張機能としてインストールされる可能性があります。 PDO_SQLSRV 拡張機能の前に PDO 拡張機能を読み込む必要があります。そうしなければ、読み込みは失敗します。 通常、拡張機能は個別の .ini ファイルを使用して読み込まれ、これらのファイルは php.ini の後に読み取られます。 このため、pdo.so が独自の .ini ファイルを介して読み込まれる場合は、PDO の後に PDO_SQLSRV ドライバーを読み込む別のファイルが必要です。 

    拡張機能固有の .ini ファイルが配置されているディレクトリを見つけるには、`php --ini` を実行し、[`Scan for additional .ini files in:`] の一覧に表示されているディレクトリをメモします。 pdo.so を読み込むファイルを見つけます。このファイルにはプレフィックスとして数値が付けられます (例: 10-pdo.ini)。 数値プレフィックスは、.ini ファイルの読み込み順序を示します。数値プレフィックスのないファイルはアルファベット順に読み込まれます。 PDO_SQLSRV ドライバー ファイルを読み込むファイルを作成して、30-pdo_sqlsrv.ini (pdo.ini に付いているプレフィックスより大きい数値) または pdo_sqlsrv.ini (pdo.ini に数値のプレフィックスが付いていない場合) という名前を付け、次の行を追加します。必要に応じてファイル名を変更します。  
    ```
    extension=php_pdo_sqlsrv_72_nts.so
    ```
    SQLSRV と同様、ソースから、または PECL を使用して PDO_SQLSRV バイナリをコンパイルした場合、代わりに pdo_sqlsrv.so という名前が付けられます。
    ```
    extension=pdo_sqlsrv.so
    ```
    他の .ini ファイルが格納されているディレクトリに、このファイルをコピーします。 

    組み込みの PDO サポートを使用してソースから PHP をコンパイルした場合は、別の .ini ファイルは必要ありません。また、上記の適切な行を php.ini に追加することもできます。
  
3.  Web サーバーを再起動します。  
  
> [!NOTE]  
> ドライバーが正常に読み込まれたかどうかを判断するために、[phpinfo()](https://php.net/manual/en/function.phpinfo.php) を呼び出すスクリプトを実行します。  
  
**php.ini** ディレクティブの詳細については、[コア php.ini ディレクティブ](https://php.net/manual/en/ini.core.php)に関するページを参照してください。  
  
## <a name="see-also"></a>参照  
[Microsoft Drivers for PHP for SQL Server の概要](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Microsoft SQL Server 用 Drivers for PHP のシステム要件](../../connect/php/system-requirements-for-the-php-sql-driver.md)

[SQL Server 用 Microsoft Drivers for PHP のためのプログラミング ガイド](../../connect/php/programming-guide-for-php-sql-driver.md)

[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)

[PDO_SQLSRV ドライバー API リファレンス](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
