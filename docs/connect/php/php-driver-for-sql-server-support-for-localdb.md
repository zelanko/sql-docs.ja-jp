---
title: LocalDB のサポート |Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d315ad6a-0d50-4093-80c2-2f11217237c2
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 438802c4645ff3acdc1bed42af22e4e32786e1d0
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37992914"
---
# <a name="support-for-localdb"></a>LocalDB のサポート

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

LocalDB はの軽量版[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]から使用可能なが経ち[!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]します。 ここでは、LocalDB インスタンス内のデータベースに接続する方法について説明します。

## <a name="remarks"></a>Remarks

LocalDB は、LocalDB をインストールして、LocalDB インスタンスを構成する方法などの詳細については、次を参照してください。、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブックのトピック「 [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] Express LocalDB です。

簡単に言うと、LocalDB を使用します。

-   使用**sqllocaldb.exe は**を既定のインスタンスの名前を検出します。

-   **AttachDBFilename** 接続文字列キーワードを使用して、サーバーをアタッチするデータベース ファイルを指定できます。 **AttachDBFilename** を使用するときに、**Database** 接続文字列キーワードを使用してデータベース名を指定しなかった場合、データベースはアプリケーションの終了時に LocalDB インスタンスから削除されます。

-   接続文字列では、次のように LocalDB インスタンスを指定します。 たとえば、SQLSRV 接続文字列の例を示します。

    ```php
    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array( 'Database'=>'myData'));

    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array('AttachDBFileName'=>'c:\\myData.MDF','Database'=>'myData'));

    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array('AttachDBFileName'=>'c:\\myData.MDF'));
    ```

    PDO_SQLSRV 接続文字列の例を次に示します。  

    ```php
    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'Database=myData', NULL, NULL);

    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'AttachDBFileName=c:\\myData.MDF;Database=myData ',
        NULL, NULL);

    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'AttachDBFileName=c:\\myData.MDF', NULL, NULL);  
    ```

必要に応じて、sqllocaldb.exe を使用して LocalDB インスタンスを作成できます。 また、sqlcmd.exe を使用して、LocalDB インスタンスのデータベースの追加と変更を実行できます。 たとえば、 `sqlcmd -S (localdb)\v11.0`のようにします。 (で IIS を実行するときは、コマンドライン; で実行したときと同じ結果を取得する適切なアカウントで実行する必要がありますを参照してください[を使用して完全 IIS と共に LocalDB、パート 2: インスタンスの所有権](http://blogs.msdn.com/b/sqlexpress/archive/2011/12/09/using-localdb-with-full-iis-part-2-instance-ownership.aspx)詳細についてはします。)。

次に、接続文字列の例、SQLSRV ドライバーを使用して名前付きインスタンスの myInstance と呼ばれる、LocalDB のデータベースに接続します。

```php
$conn = sqlsrv_connect( '(localdb)\\myInstance',
    array( 'Database'=>'myData'));
```

次に、接続文字列の例、PDO_SQLSRV ドライバーを使用して名前付きインスタンスの myInstance と呼ばれる、LocalDB のデータベースに接続します。  
  
```php
$conn = new PDO( 'sqlsrv:server=(localdb)\\myInstance;'
    . 'database=myData', NULL, NULL);
```

LocalDB をインストールする方法の詳細については、次を参照してください。、 [LocalDB ドキュメント](../../database-engine/configure-windows/sql-server-2016-express-localdb.md)します。 必要があります、LocalDB インスタンスのデータを変更するために sqlcmd.exe を使用する場合、 [sqlcmd ユーティリティ](../../tools/sqlcmd-utility.md)します。

## <a name="see-also"></a>参照

[サーバーへの接続](../../connect/php/connecting-to-the-server.md)
