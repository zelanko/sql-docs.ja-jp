---
title: SQL Server 2019 でサポートされる Java データ型 |Microsoft Docs
description: データ型をマップ Java から SQL Server への入力と出力のデータ構造体を sp_execute_external_script の入力パラメーター。
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3510b53510514daa125382fc10ea33285fe44a80
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2018
ms.locfileid: "46715265"
---
# <a name="java-and-sql-server-supported-data-types"></a>Java および SQL Server のサポートされるデータ型

この記事では、Java のデータ型のデータ構造とパラメーターを SQL Server データ型をマップに[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)します。

## <a name="data-types-for-data-sets"></a>データ セットのデータ型

入力と出力データ セットでは、次の SQL と Java のデータ型はサポートされて現在。

| SQL 型        | Java の型 | | |
| ------------- |-------------|-|-|
| bit      | boolean | | |
| Tinyint      | short      | | |
| Smallint | short      | | |
| Int | ssNoversion      | | |
| Real | FLOAT      | | |
| Bigint | long      | | |
| FLOAT | double      | | |
| nchar(n) | 文字列 (unicode)      | | |
| nvarchar (n) | 文字列 (unicode)      | | |
| binary(n) | byte[]      | | |
| varbinary (n) | byte[]      | | |

## <a name="data-types-for-input-parameters"></a>入力パラメーターのデータ型

入力パラメーターでは、次の SQL と Java のデータ型はサポートされて現在。

| SQL 型        | Java の型 | | |
| ------------- |-------------|-|-|
| bit      | boolean | | |
| Tinyint      | short      | | |
| Smallint | short      | | |
| Int | ssNoversion      | | |
| Real | FLOAT      | | |
| Bigint | long      | | |
| FLOAT | double      | | |
| nchar(n) | 文字列 (unicode)      | | |
| nvarchar (n) | 文字列 (unicode)      | | |
| binary(n) | byte[]      | | |
| varbinary (n) | byte[]      | | |
| nvarchar(max) | 文字列 (unicode)      | | |
| varbinary(max) | byte[]      | | |

## <a name="see-also"></a>関連項目

+ [SQL Server で Java を呼び出す方法](howto-call-java-from-sql.md)
+ [SQL Server での Java サンプル](java-first-sample.md)
+ [SQL Server での Java 言語の拡張機能](extension-java.md)