---
title: SQL Server 2019 - SQL Server の言語拡張機能でサポートされる Java データ型
description: データ型をマップ Java から SQL Server への入力と出力のデータ構造体を sp_execute_external_script の入力パラメーター。
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/23/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 14a2bc5594b16610dfb8278ab82a9e7b8b22fea6
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64775002"
---
# <a name="java-and-sql-server-supported-data-types"></a>Java および SQL Server のサポートされるデータ型

この記事では、Java のデータ型のデータ構造とパラメーターを SQL Server データ型をマップに[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)します。

## <a name="data-types-for-data-sets"></a>データ セットのデータ型

入力と出力データ セットでは、次の SQL と Java のデータ型はサポートされて現在。


| SQL データ型        | Java データ型 | 解説 | |
| ------------- |-------------|-|-|
| bit      | boolean | | |
| Tinyint      | short      | | |
| Smallint | short      | | |
| Int | ssNoversion      | | |
| Real | FLOAT      | | |
| Bigint | long      | | |
| FLOAT | double      | | |
| nchar(n) | String      | | |
| nvarchar (n) | String      | | |
| binary(n) | byte[]      | | |
| varbinary (n) | byte[]      | | |
| nvarchar(max) | String      | | |
| varbinary(max) | byte[]      | | |
| UNIQUEIDENTIFIER | String | | |
| char(n) | String | UTF8 文字列のみがサポートされています | |
| varchar (n) | String | UTF8 文字列のみがサポートされています | |
| varchar(max) | String | UTF8 文字列のみがサポートされています | |

## <a name="data-types-for-input-parameters"></a>入力パラメーターのデータ型

入力パラメーターでは、次の SQL と Java のデータ型はサポートされて現在。

| SQL データ型        | Java データ型 | 解説 | |
| ------------- |-------------|-|-|
| bit      | boolean | | |
| Tinyint      | short      | | |
| Smallint | short      | | |
| Int | ssNoversion      | | |
| Real | FLOAT      | | |
| Bigint | long      | | |
| FLOAT | double      | | |
| nchar(n) | String      | | |
| nvarchar (n) | String      | | |
| binary(n) | byte[]      | | |
| varbinary (n) | byte[]      | | |
| nvarchar(max) | String      | | |
| varbinary(max) | byte[]      | | |
| UNIQUEIDENTIFIER | String | | |
| char(n) | String | UTF8 文字列のみがサポートされています | |
| varchar (n) | String | UTF8 文字列のみがサポートされています | |
| varchar(max) | String | UTF8 文字列のみがサポートされています | |

## <a name="next-steps"></a>次のステップ

+ [SQL Server で Java を呼び出す方法](howto-call-java-from-sql.md)
+ [SQL Server での Java サンプル](java-first-sample.md)
+ [SQL Server での Java 言語の拡張機能](extension-java.md)
