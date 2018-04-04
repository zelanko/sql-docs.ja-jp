---
title: 既定の SQL Server データの種類 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- default data types
- converting data types
ms.assetid: 65c7c211-96d3-4e65-a1de-1fe8d21348e7
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c1facac748e24d465144f93d2e4ccdf38608e6b3
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="default-sql-server-data-types"></a>既定の SQL Server のデータ型
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

サーバーにデータを送信する際に、ユーザーが SQL Server のデータ型を指定していない場合、 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] はその PHP データ型を SQL Server のデータ型に変換します。 次の表は、PHP のデータ型 (サーバーに送信されるデータ型) と SQL Server の既定のデータ型 (データが変換されるデータ型) を示しています。 サーバーにデータを送信する際にデータ型を指定する方法の詳細については、「 [方法: SQLSRV ドライバーを使用する場合に SQL Server データ型を指定する](../../connect/php/how-to-specify-sql-server-data-types-when-using-the-sqlsrv-driver.md)」を参照してください。  
  
|PHP のデータ型|SQLSRV ドライバーの SQL Server の既定の型|PDO_SQLSRV ドライバーの SQL Server の既定の型|  
|-----------------|------------------------------------------------|-----------------------------------------------------|  
|NULL|varchar (1)|サポートされていません|  
|ブール値|bit|bit|  
|Integer|int|int|  
|Float|float(24)|サポートされていません|  
|文字列 (長さ 8000 バイト未満)|varchar(<string length>)|varchar(<string length>)|  
|文字列 (8000 バイトを超える長さ)|varchar(max)|varchar(max)|  
|リソース|サポートされていません。|サポートされていません。|  
|ストリーム (エンコード: バイナリではない)|varchar(max)|varchar(max)|  
|ストリーム (エンコード: バイナリ)|varbinary|varbinary|  
|Array|サポートされていません。|サポートされていません。|  
|オブジェクト|サポートされていません。|サポートされていません。|  
|DateTime (1)|datetime|サポートされていません。|  
  
## <a name="see-also"></a>参照  
[定数 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[データ型の変換](../../connect/php/converting-data-types.md)

[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)

[PHP の型](http://php.net/manual/language.types.php)

[データ型 (TRANSACT-SQL)](https://docs.microsoft.com/en-us/sql/t-sql/data-types/data-types-transact-sql)  
  
