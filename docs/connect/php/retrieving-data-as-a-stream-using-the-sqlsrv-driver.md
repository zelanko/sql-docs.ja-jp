---
title: SQLSRV ドライバーを使用してストリームとしてデータを取得する |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 17dc9129-04cd-430c-b5b3-82824116425d
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 32164c9beb05293249eafef76de29dcf3c356182
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="retrieving-data-as-a-stream-using-the-sqlsrv-driver"></a>SQLSRV ドライバーを使用してデータをストリームとして取得する
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

ストリームがあるだけの SQLSRV ドライバーで使用できるようにデータを取得する、 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]、し、PDO_SQLSRV ドライバーでは使用できません。  
  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] は、大量のデータを取得するためにストリームを利用します。 このセクションのトピックでは、データをストリームとして取得する方法について詳しく説明します。  
  
次の手順に、データをストリームとして取得する方法をまとめています。  
  
1.  準備し、で TRANSACT-SQL クエリを実行[sqlsrv_query](../../connect/php/sqlsrv-query.md)またはの組み合わせ[sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)/[sqlsrv_execute](../../connect/php/sqlsrv-execute.md)です。  
  
2.  [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md) を使用して、結果セットの次の行に移動します。  
  
3.  [sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md) を使用して、行からフィールドを取得します。 データを使用して、ストリームとして取得することを指定**SQLSRV_PHPTYPE_STREAM (<encoding>)** 関数呼び出しで 3 番目のパラメーターとして。 次の表は、エンコーディングおよびそれらの記述を指定するために使用する定数を示しています。  
  
    |SQLSRV 定数|Description|  
    |-------------------|---------------|  
    |SQLSRV_ENC_BINARY|データは、エンコードまたは変換されず、生のバイト ストリームとしてサーバーから返されます。|  
    |SQLSRV_ENC_CHAR|データは、システムの Windows ロケール設定のコード ページで指定されている 8 ビット文字で返されます。 任意のマルチバイト文字またはこのコード ページにマップされていない文字は、1 バイトの疑問符 (?) 文字に置き換えられます。|  
  
> [!NOTE]  
> 一部のデータ型は、既定ではストリームとして返されます。 詳細については、「 [Default PHP Data Types](../../connect/php/default-php-data-types.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|---------|---------------|  
|[SQLSRV ドライバーを使用したストリームでのデータ型のサポート](../../connect/php/data-types-with-stream-support-using-the-sqlsrv-driver.md)|ストリームとして取得できる SQL Server データ型を一覧表示します。|  
|[方法: SQLSRV ドライバーを使用したストリームとしての文字データの取得](../../connect/php/how-to-retrieve-character-data-as-a-stream-using-the-sqlsrv-driver.md)|文字データをストリームとして取得する方法を説明します。|  
|[方法: SQLSRV ドライバーを使用してバイナリ データをストリームとして取得する](../../connect/php/how-to-retrieve-binary-data-as-a-stream-using-the-sqlsrv-driver.md)|バイナリ データをストリームとして取得する方法を説明します。|  
  
## <a name="see-also"></a>参照  
[データの取得](../../connect/php/retrieving-data.md)

[定数 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
  
