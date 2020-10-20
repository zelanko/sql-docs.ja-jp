---
title: Python と SQL のデータ型を変換する
description: データ サイエンスおよび機械学習のソリューションにおける Python と SQL Server の間の暗黙的および明示的なデータ型の変換について確認します。
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 10/06/2020
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: da92713dbf514e2500d0d5f8eb3e776523830041
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2020
ms.locfileid: "91891352"
---
# <a name="data-type-mappings-between-python-and-sql-server"></a>Python と SQL Server の間のデータ型マッピング
[!INCLUDE [SQL Server 2017 and later](../../includes/applies-to-version/sqlserver2017.md)]

この記事では、SQL Server Machine Learning Services の Python 統合機能を使用する場合にサポートされるデータ型および実行されるデータ型変換の一覧を示します。

Python は、SQL Server と比較して、限られた数のデータ型をサポートしています。 その結果、SQL Server のデータを Python スクリプトで使用すると、SQL データが互換性のある Python データ型に暗黙的に変換される可能性があります。 ただし、多くの場合、正確な変換を自動的に実行することができず、エラーが返されます。

## <a name="python-and-sql-data-types"></a>Python と SQL のデータ型

この表に、提供されている暗黙的な変換の一覧を示します。 他のデータ型はサポートされていません。

| SQL 型             | Python 型 | 説明 |
|----------------------|-------------|-------------|
| **bigint**           | `float64`   |
| **[バイナリ]**           | `bytes`     |
| **bit**              | `bool`      |
| **char**             | `str`       |
| **date**             | `datetime`  |
| **datetime**         |`datetime`   | SQL Server 2017 CU6 以降でサポートされています (`datetime.datetime` 型または **Pandas** `pandas.Timestamp` 型の **NumPy** 配列を使用します)。 `sp_execute_external_script` では、秒の小数部で `datetime` 型がサポートされるようになりました。|
| **float**            | `float64`   |
| **nchar**            | `str`       |
| **nvarchar**         | `str`       |
| **nvarchar(max)**    | `str`       |
| **real**             | `float64`   |
| **smalldatetime**    | `datetime`  |
| **smallint**         | `int32`     |
| **tinyint**          | `int32`     |
| **uniqueidentifier** | `str`       |
| **varbinary**        | `bytes`     |
| **varbinary(max)**   | `bytes`     |
| **varchar(n)**       | `str`       |
| **varchar(max)**     | `str`       |

## <a name="see-also"></a>関連項目

+ [R と SQL Server の間のデータ型マッピング](../r/r-libraries-and-data-types.md)
