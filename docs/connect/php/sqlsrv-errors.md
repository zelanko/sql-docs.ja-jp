---
title: "sqlsrv_errors |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- sqlsrv_errors
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_errors
- sqlsrv_errors
- errors and warnings
ms.assetid: d1fcffec-f34f-46de-9a0e-343f3b5dbae2
caps.latest.revision: 39
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9994273b04f7928826ca5f4c7997d51a548d488e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsrverrors"></a>sqlsrv_errors
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

返します。 拡張エラーや警告について、最後は**sqlsrv**操作を実行します。  
  
**Sqlsrv_errors**関数は、以下のパラメーター セクションで指定されたパラメーター値のいずれかで呼び出すことによってエラーや警告の情報を返すことができます。  
  
既定では、いずれかの **sqlsrv** 関数の呼び出しで生成される警告はエラーとして扱われます。 **sqlsrv** 関数の呼び出しで警告が発生した場合、関数は false を返します。 ただし、SQLSTATE 値 01000、01001、01003、および 01S02 に対応する警告はエラーとして扱われません。  
  
次のコード行は、上で説明した動作を無効にします。 **sqlsrv** 関数の呼び出しによって警告が生成されても、関数は false を返しません。  
  
```  
sqlsrv_configure("WarningsReturnAsErrors", 0);  
```  
  
次のコード行は、既定の動作に戻します。(上で説明した場合を除き) 警告はエラーとして扱われます。  
  
```  
sqlsrv_configure("WarningsReturnAsErrors", 1);  
```  
  
設定に関係なく警告のみを取得できる呼び出し**sqlsrv_errors**いずれかで、 **SQLSRV_ERR_ALL**または**SQLSRV_ERR_WARNINGS**パラメーター値 (を参照してくださいパラメーター以下のセクションの詳細)。  
  
## <a name="syntax"></a>構文  
  
```  
  
sqlsrv_errors( [int $errorsAndOrWarnings] )  
```  
  
#### <a name="parameters"></a>パラメーター  
*$errorsAndOrWarnings*[省略可能]: 定義済みの定数です。 このパラメーターには、次の表に示すいずれかの値を指定できます。  
  
|値|Description|  
|---------|---------------|  
|SQLSRV_ERR_ALL|**sqlsrv** 関数の最後の呼び出しで生成されたエラーと警告が返されます。|  
|SQLSRV_ERR_ERRORS|**sqlsrv** 関数の最後の呼び出しで生成されたエラーが返されます。|  
|SQLSRV_ERR_WARNINGS|**sqlsrv** 関数の最後の呼び出しで生成された警告が返されます。|  
  
パラメーターの値を指定しないと、 **sqlsrv** 関数の最後の呼び出しで生成されたエラーと警告が返されます。  
  
## <a name="return-value"></a>戻り値  
配列の **array** 、または **null**。 各**配列**、返された**配列**3 つのキー/値ペアが含まれています。 次の表では、各キーとその説明を示します。  
  
|[キー]|説明|  
|-------|---------------|  
|SQLSTATE|ODBC ドライバー由来のエラーの場合、ODBC が返す SQLSTATE。 ODBC の SQLSTATE 値については、「 [ODBC Error Codes (ODBC エラー コード)](http://go.microsoft.com/fwlink/?linkid=119618)」を参照してください。<br /><br />[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]由来のエラーの場合、IMSSP の SQLSTATE。<br /><br />[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]由来の警告の場合、01SSP の SQLSTATE。|  
|コード|SQL Server 由来のエラーの場合、SQL Server のネイティブ エラー コード。<br /><br />ODBC ドライバー由来のエラーの場合、ODBC が返すエラー コード。<br /><br />[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]由来のエラーの場合、 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] のエラー コード。 詳細については、「 [Handling Errors and Warnings](../../connect/php/handling-errors-and-warnings.md)」を参照してください。|  
|message|エラーの説明です。|  
  
配列の値は、数値キー 0、1、および 2 でアクセスすることもできます。 エラーまたは警告が発生しなかった場合、 **null** が返されます。  
  
## <a name="example"></a>例  
次の例では、失敗したステートメント実行の間に発生したエラーを表示します (ため、ステートメントが失敗した**InvalidColumName**指定されたテーブルで有効な列名ではありません)。例では、SQL Server および[AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739)データベースがローカル コンピューターにインストールされています。 コマンド ラインからこの例を実行すると、すべての出力はコンソールに書き込まれます。  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and   
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up a query to select an invalid column name. */  
$tsql = "SELECT InvalidColumnName FROM Sales.SalesOrderDetail";  
  
/* Attempt execution. */  
/* Execution will fail because of the invalid column name. */  
$stmt = sqlsrv_query( $conn, $tsql);  
if( $stmt === false )  
{  
      if( ($errors = sqlsrv_errors() ) != null)  
      {  
         foreach( $errors as $error)  
         {  
            echo "SQLSTATE: ".$error[ 'SQLSTATE']."\n";  
            echo "code: ".$error[ 'code']."\n";  
            echo "message: ".$error[ 'message']."\n";  
         }  
      }  
}  
  
/* Free connection resources */  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>参照  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  
[ドキュメントのコード例について](../../connect/php/about-code-examples-in-the-documentation.md)  
  

