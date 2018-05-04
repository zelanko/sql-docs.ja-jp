---
title: 既定の PHP データ型 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- default data types
- converting data types
ms.assetid: b66c301d-3d20-45b8-a112-225d8f01c0bd
caps.latest.revision: 40
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 85f3a11208980bffee7879806e7ee834d7bc74d5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="default-php-data-types"></a>既定の PHP データ型
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

サーバーからデータを取得するとき、ユーザーが PHP のデータ型を指定しないと、 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] はデータを既定の PHP データ型に変換します。  
  
PDO_SQLSRV ドライバーを使用してデータが返される場合、データ型は int または string になります。  
  
このトピックでは、SQLSRV ドライバーを使用するときの既定のデータ型について説明します。  
  
次の表では、SQL Server のデータ型 (サーバーから取得されるデータ型)、PHP の既定のデータ型 (データが変換されるデータ型)、およびストリームと文字列の既定のエンコードを示します。 サーバーからデータを取得するときにデータ型を指定する方法の詳細については、「 [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md)」を参照してください。  
  
|SQL Server の型|PHP の既定の型|既定のエンコード|  
|-------------------|--------------------|--------------------|  
|bigint|文字列|8 ビット文字<sup>1</sup>|  
|binary|Stream<sup>2</sup>|バイナリ<sup>3</sup>|  
|bit|Integer|8 ビット文字<sup>1</sup>|  
|char|文字列|8 ビット文字<sup>1</sup>|  
|date<sup>4</sup>|DateTime|適用なし|  
|datetime<sup>4</sup>|DateTime|適用なし|  
|datetime2<sup>4</sup>|DateTime|適用なし|  
|datetimeoffset<sup>4</sup>|DateTime|適用なし|  
|decimal|文字列|8 ビット文字<sup>1</sup>|  
|float|Float|8 ビット文字<sup>1</sup>|  
|geography|Stream|バイナリ<sup>3</sup>|  
|geometry|Stream|バイナリ<sup>3</sup>|  
|イメージ<sup>5</sup>|Stream<sup>2</sup>|バイナリ<sup>3</sup>|  
|int|Integer|8 ビット文字<sup>1</sup>|  
|money|文字列|8 ビット文字<sup>1</sup>|  
|NCHAR|文字列|8 ビット文字<sup>1</sup>|  
|numeric|文字列|8 ビット文字<sup>1</sup>|  
|nvarchar|文字列|8 ビット文字<sup>1</sup>|  
|nvarchar(MAX)|Stream<sup>2</sup>|8 ビット文字<sup>1</sup>|  
|ntext<sup>6</sup>|Stream<sup>2</sup>|8 ビット文字<sup>1</sup>|  
|real|Float|8 ビット文字<sup>1</sup>|  
|smalldatetime|DateTime|8 ビット文字<sup>1</sup>|  
|smallint|Integer|8 ビット文字<sup>1</sup>|  
|smallmoney|文字列|8 ビット文字<sup>1</sup>|  
|sql_variant<sup>7</sup>|文字列|8 ビット文字<sup>1</sup>|  
|テキスト<sup>8</sup>|Stream<sup>2</sup>|8 ビット文字<sup>1</sup>|  
|time<sup>4</sup>|DateTime|適用なし|  
|timestamp|文字列|8 ビット文字<sup>1</sup>|  
|tinyint|Integer|8 ビット文字<sup>1</sup>|  
|UDT (UDT)|Stream<sup>2</sup>|バイナリ<sup>3</sup>|  
|uniqueidentifier|文字列<sup>9</sup>|8 ビット文字<sup>1</sup>|  
|varbinary|Stream<sup>2</sup>|バイナリ<sup>3</sup>|  
|varbinary (max)|Stream<sup>2</sup>|バイナリ<sup>3</sup>|  
|varchar|文字列|8 ビット文字<sup>1</sup>|  
|varchar(MAX)|Stream<sup>2</sup>|8 ビット文字<sup>1</sup>|
|xml|Stream<sup>2</sup>|8 ビット文字<sup>1</sup>|  
  

1.  データは、システムの Windows ロケール設定のコード ページで指定されている 8 ビット文字で返されます。 任意のマルチバイト文字またはこのコード ページにマップされていない文字が 1 バイトの疑問符 (?) 文字で置き換えられます。  
  
2.  場合[sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md)または[sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md)がストリームの既定の PHP 型を持つデータを取得するために使用、データが返されますを文字列としてのストリームと同じエンコーディング。 たとえば、SQL Server の binary 型が取得した場合を使用して**sqlsrv_fetch_array**既定の戻り型がバイナリ文字列です。  
  
3.  データは、エンコードまたは変換されず、生のバイト ストリームとしてサーバーから返されます。  

4.  日付と時刻の型は、文字列として取得できます。 詳細については、「 [方法: SQLSRV ドライバーを利用し、日付/時刻型を取得する](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md)」を参照してください。  

5.  これは、varbinary(max) 型にマップされる従来の型です。

6. これは、nvarchar(max) 型にマップされる従来の型です。

7.  sql_variant 型は、双方向または出力パラメーターではサポートされていません。

8.  これは、varchar(max) 型にマップされる従来の型です。  
  
9.  UNIQUEIDENTIFIER は、次の正規表現によって表される GUID です。  
  
    [0-9a-fA-F]{8}-[0-9a-fA-F]{4}-[0-9a-fA-f]{4}-[0-9a-fA-f]{4}-[0-9a-fA-F]{12}  
 
 
## <a name="other-new-sql-server-2008-data-types-and-features"></a>SQL Server 2008 でのその他の新しいデータ型と機能  
SQL Server 2008 での新しいデータ型列 (テーブル値パラメーターの場合) などの外部に存在することはできません、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]です。 次の表は、SQL Server 2008 の新機能の PHP によるサポートをまとめたものです。  
  
|機能|PHP のサポート|  
|-----------|---------------|  
|テーブル値パラメーター|いいえ|  
|スパース列|部分的|  
|Null ビット圧縮|はい|  
|大きな CLR ユーザー定義型 (UDT)|はい|  
|サービス プリンシパル名|いいえ|  
|MERGE|はい|  
|FILESTREAM|部分的|  
  
部分的な型のサポートとは、その列の型をプログラムでクエリできないことを意味します。  
  
## <a name="see-also"></a>参照  
[定数 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[Converting Data Types](../../connect/php/converting-data-types.md)

[PHP の型](http://php.net/manual/en/language.types.php)

[データ型 (TRANSACT-SQL)](../../t-sql/data-types/data-types-transact-sql.md)

[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)  
  
