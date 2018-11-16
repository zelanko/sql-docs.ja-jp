---
title: LocalDB のサポート |Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d315ad6a-0d50-4093-80c2-2f11217237c2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 40c6bbf04f0c1fc5f2b4e2e360a3fcce5a68c6f7
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2018
ms.locfileid: "51600472"
---
# <a name="support-for-localdb"></a>LocalDB のサポート

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

LocalDB はの軽量版[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]から使用可能なが経ち[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]します。 ここでは、LocalDB インスタンス内のデータベースに接続する方法について説明します。

## <a name="remarks"></a>Remarks

LocalDB は、LocalDB をインストールして、LocalDB インスタンスを構成する方法などの詳細については、次を参照してください。、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オンライン ブックのトピック「 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Express LocalDB です。

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

必要に応じて、sqllocaldb.exe を使用して LocalDB インスタンスを作成できます。 また、sqlcmd.exe を使用して、LocalDB インスタンスのデータベースの追加と変更を実行できます。 たとえば、`sqlcmd -S (localdb)\v11.0` のようにします。 (で IIS を実行するときは、コマンドライン; で実行したときと同じ結果を取得する適切なアカウントで実行する必要がありますを参照してください[を使用して完全 IIS と共に LocalDB、パート 2: インスタンスの所有権](https://blogs.msdn.com/b/sqlexpress/archive/2011/12/09/using-localdb-with-full-iis-part-2-instance-ownership.aspx)詳細についてはします。)。

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
