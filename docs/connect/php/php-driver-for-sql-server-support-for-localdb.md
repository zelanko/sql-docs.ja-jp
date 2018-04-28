---
title: LocalDB のサポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.prod_service: drivers
ms.component: php
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d315ad6a-0d50-4093-80c2-2f11217237c2
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 34fe16235f924c020c69b4e58cb485e0c7ff1e4b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="support-for-localdb"></a>LocalDB のサポート

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

LocalDB は、軽量バージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]これは以来、使用可能な[!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]します。 ここでは、LocalDB インスタンス内のデータベースに接続する方法について説明します。

## <a name="remarks"></a>解説

LocalDB をインストールして、LocalDB インスタンスを構成する方法を含む LocalDB の詳細については、次を参照してください。、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]でオンライン ブックの「 [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] Express LocalDB です。

簡単に説明すると、LocalDB を使用します。

-   使用して**sqllocaldb.exe すれば**を既定のインスタンスの名前を検出します。

-   使用して、 **AttachDBFilename**接続文字列キーワードを指定するデータベース サーバーのファイルを添付する必要があります。 使用する場合**AttachDBFilename**を持つデータベースの名前を指定しない場合は、**データベース**データベースは削除から接続文字列キーワード、LocalDB インスタンスの場合に、アプリケーション閉じます。

-   接続文字列に LocalDB インスタンスを指定します。 たとえば、SQLSRV 接続文字列の例を次に示します。

    ```php
    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array( 'Database'=>'myData'));

    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array('AttachDBFileName'=>'c:\\myData.MDF','Database'=>'myData'));

    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array('AttachDBFileName'=>'c:\\myData.MDF'));
    ```

    PDO_SQLSRV 接続文字列の例を次には。  

    ```php
    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'Database=myData', NULL, NULL);

    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'AttachDBFileName=c:\\myData.MDF;Database=myData ',
        NULL, NULL);

    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'AttachDBFileName=c:\\myData.MDF', NULL, NULL);  
    ```

必要に応じて、sqllocaldb.exe を使用して LocalDB インスタンスを作成できます。 また、sqlcmd.exe を使用して、LocalDB インスタンスのデータベースの追加と変更を実行できます。 たとえば、 `sqlcmd -S (localdb)\v11.0`のようにします。 (IIS を実行しているときのコマンドラインで実行したときと同じ結果を得るための正しいアカウントで実行する必要がありますを参照してください[完全な IIS と、第 2 部を使用して LocalDB: インスタンスの所有権](http://blogs.msdn.com/b/sqlexpress/archive/2011/12/09/using-localdb-with-full-iis-part-2-instance-ownership.aspx)詳細についてはします。)。

接続文字列の例、SQLSRV ドライバーを使用して名前付きインスタンスの myInstance と呼ばれる LocalDB のデータベースに接続するを次に示します。

```php
$conn = sqlsrv_connect( '(localdb)\\myInstance',
    array( 'Database'=>'myData'));
```

接続文字列の例、PDO_SQLSRV ドライバーを使用して名前付きインスタンスの myInstance と呼ばれる LocalDB のデータベースに接続するを次に示します。  
  
```php
$conn = new PDO( 'sqlsrv:server=(localdb)\\myInstance;'
    . 'database=myData', NULL, NULL);
```

LocalDB をインストールする方法の詳細については、次を参照してください。、 [LocalDB ドキュメント](../../database-engine/configure-windows/sql-server-2016-express-localdb.md)です。 必要があります sqlcmd.exe を使用して LocalDB インスタンスのデータを変更する場合、 [sqlcmd ユーティリティ](../../tools/sqlcmd-utility.md)です。

## <a name="see-also"></a>参照

[サーバーへの接続](../../connect/php/connecting-to-the-server.md)
