---
title: Python または R スクリプトから SQL Server するためのループバック接続
description: ループバック接続を使用して ODBC 経由で SQL Server に接続し、sp_execute_external_script から実行される Python または R スクリプトのデータの読み取りまたは書き込みを行う方法について説明します。 これは、sp_execute_external_script の InputDataSet 引数と OutputDataSet 引数を使用できない場合に使用できます。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/21/2019
ms.topic: conceptual
author: Aniruddh25
ms.author: anmunde
ms.reviewer: dphansen
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 62b4ce483df2d38e5e2549d054c02b6c797837f3
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69657489"
---
# <a name="loopback-connection-to-sql-server-from-a-python-or-r-script"></a>Python または R スクリプトから SQL Server するためのループバック接続
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

ループバック接続を使用して[ODBC](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md)経由で SQL Server に接続し、から`sp_execute_external_script`実行される Python または R スクリプトのデータの読み取りまたは書き込みを行う方法について説明します。 **Inputdataset**引数と**outputdataset**引数`sp_execute_external_script`を使用することはできません。

## <a name="connection-string"></a>[接続文字列]

ループバック接続を行うには、正しい接続文字列を使用する必要があります。 共通の必須引数として、 [ODBC ドライバー](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md)の名前、サーバーのアドレス、およびデータベースの名前を指定します。

### <a name="connection-string-on-windows"></a>Windows 上の接続文字列

Windows の SQL Server での認証では、Python または R スクリプトで**Trusted_Connection**接続文字列属性を使用して、sp_execute_external_script を実行したのと同じユーザーとして認証することができます。

Windows でのループバック接続文字列の例を次に示します。

``` 
"Driver=SQL Server;Server=.;Database=nameOfDatabase;Trusted_Connection=Yes;"
```

### <a name="connection-string-on-linux"></a>Linux 上の接続文字列

SQL Server on Linux での認証では、Python または R スクリプトで ODBC ドライバーの**ClientCertificate**および**clientkey**属性を使用して、実行`sp_execute_external_script`したのと同じユーザーとして認証する必要があります。 これには、[最新の ODBC ドライバー](../../connect/odbc/download-odbc-driver-for-sql-server.md)バージョン17.4.1.1 を使用する必要があります。

Linux でのループバック接続文字列の例を次に示します。

```
"Driver=ODBC Driver 17 for SQL Server;Server=fe80::8012:3df5:0:5db1%eth0;Database=nameOfDatabase;ClientCertificate=file:/var/opt/mssql-extensibility/data/baeaac72-60b3-4fae-acfd-c50eff5d34a2/sqlsatellitecert.pem;ClientKey=file:/var/opt/mssql-extensibility/data/baeaac72-60b3-4fae-acfd-c50eff5d34a2/sqlsatellitekey.pem;TrustServerCertificate=Yes;Trusted_Connection=no;Encrypt=Yes"
```

サーバーアドレス、クライアント証明書ファイルの場所、およびクライアントキーファイルの場所は、 `sp_execute_external_script`それぞれに固有であり、Python **の API rx_get_sql_loopback_connection_string () を使用して取得できます。R の rxGetSqlLoopbackConnectionString ()** 。

接続文字列の属性の詳細については、Microsoft ODBC Driver for SQL Server の[DSN および接続文字列のキーワードと属性](https://docs.microsoft.com/sql/connect/odbc/dsn-connection-string-attribute?view=sql-server-linux-ver15#new-connection-string-keywords-and-connection-attributes)に関する説明を参照してください。

## <a name="generate-connection-string-with-revoscalepy-for-python"></a>Python 用 revoscalepy を使用して接続文字列を生成する

[Revoscalepy](../python/ref-py-revoscalepy.md)の API **rx_get_sql_loopback_connection_string ()** を使用して、Python スクリプトでループバック接続用の正しい接続文字列を生成できます。

次の引数を受け取ります。

| 引数 | 説明 |
|-|-|
| name_of_database | 接続が確立されるデータベースの名前 |
| odbc_driver | Odbc ドライバーの名前 |

### <a name="examples"></a>使用例

Windows での SQL Server の例:

```sql
EXECUTE sp_execute_external_script
@language = N'Python',
@script = N'
from revoscalepy import rx_get_sql_loopback_connection_string, RxSqlServerData, rx_data_step
loopback_connection_string = rx_get_sql_loopback_connection_string(odbc_driver="SQL Server", name_of_database="DBName")
print("Connection String:{0}".format(loopback_connection_string))
data_set = RxSqlServerData(sql_query = "select col1, col2 from tableName",
                           connection_string = loopback_connection_string)
OutputDataSet = rx_data_step(data_set)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

SQL Server on Linux の例:

```sql
EXECUTE sp_execute_external_script
@language = N'Python',
@script = N'
from revoscalepy import rx_get_sql_loopback_connection_string, RxSqlServerData, rx_data_step
loopback_connection_string = rx_get_sql_loopback_connection_string(odbc_driver="ODBC Driver 17 for SQL Server",
                                                                   name_of_database="DBName")
print("Loopback Connection String:{0}".format(loopback_connection_string))
data_set = RxSqlServerData(sql_query = "select col1, col2 from tableName",
                           connection_string = loopback_connection_string)
OutputDataSet = rx_data_step(data_set)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

## <a name="generate-connection-string-with-revoscaler-for-r"></a>R の RevoScaleR を使用して接続文字列を生成する

[RevoScaleR](../r/ref-r-revoscaler.md)の API **rxGetSqlLoopbackConnectionString ()** を使用して、R スクリプトでループバック接続用の正しい接続文字列を生成できます。

次の引数を受け取ります。

| 引数 | 説明 |
|-|-|
| nameOfDatabase | 接続が確立されるデータベースの名前 |
| odbcDriver | Odbc ドライバーの名前 |

### <a name="examples"></a>使用例

Windows での SQL Server の例:

```sql
EXECUTE sp_execute_external_script
@language = N'R',
@script = N'
    loopbackConnectionString <- rxGetSqlLoopbackConnectionString(nameOfDatabase="DBName", odbcDriver ="SQL Server")
    print(paste("Connection String:", loopbackConnectionString))
    dataSet <- RxSqlServerData(sqlQuery = "select col1, col2 from tableName",
                               connectionString = loopbackConnectionString)
    OutputDataSet <- rxDataStep(dataSet)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

SQL Server on Linux の例:

```sql
EXECUTE sp_execute_external_script
@language = N'R',
@script = N'
    loopbackConnectionString <-  rxGetSqlLoopbackConnectionString(nameOfDatabase="DBName", 
                                                                  odbcDriver ="ODBC Driver 17 for SQL Server")
    print(paste("Connection String:", loopbackConnectionString))
    dataSet <- RxSqlServerData(sqlQuery = "select col1, col2 from tableName", 
                               connectionString = loopbackConnectionString)
    OutputDataSet <- rxDataStep(dataSet)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

## <a name="next-steps"></a>次の手順

+ [Microsoft ODBC driver for SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md)
+ [revoscalepy](../python/ref-py-revoscalepy.md)
+ [RevoScaleR](../r/ref-r-revoscaler.md)
