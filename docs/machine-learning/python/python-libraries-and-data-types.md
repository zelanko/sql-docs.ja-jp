---
title: Python と SQL のデータ型を変換する
description: データ サイエンスおよび機械学習のソリューションにおける Python と SQL Server の間の暗黙的および明示的なデータ型の変換について確認します。
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 06/30/2020
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ee493ec09c5cfc8a5198239cd5cafcb2579f50d8
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2020
ms.locfileid: "88178635"
---
# <a name="data-type-mappings-between-python-and-sql-server"></a>Python と SQL Server の間のデータ型マッピング
[!INCLUDE [SQL Server 2017 and later](../../includes/applies-to-version/sqlserver2017.md)]

SQL Server Machine Learning Services の Python 統合機能で実行される Python ソリューションについて、サポートされないデータ型の一覧と、Python と SQL Server の間でデータが受け渡されるときに暗黙的に実行される可能性のあるデータ型の変換について確認します。

## <a name="python-version"></a>Python バージョン

RevoScaleR 機能 (rxLinMod、rxLogit、rxPredict、rxDTrees、rxBTrees、およびその他いくつかを含む) のサブセットは、新しい Python パッケージ **revoscalepy** を使用した Python API を使用して提供されます。 このパッケージを使用することで、Pandas データ フレーム、XDF ファイル、または SQL データ クエリを使用してデータを操作できます。

詳細については、[SQL Server の revoscalepy モジュール](ref-py-revoscalepy.md)および [revoscalepy 関数参照](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package)に関するページを参照してください。

Python は、SQL Server と比較して、限られた数のデータ型をサポートしています。 その結果、SQL Server のデータを Python スクリプトで使用すると、データが互換性のあるデータ型に暗黙的に変換される可能性があります。 ただし、多くの場合、正確な変換を自動的に実行できず、エラーが返されます。

## <a name="python-and-sql-data-types"></a>Python と SQL のデータ型

この表に、提供されている暗黙的な変換の一覧を示します。 他のデータ型はサポートされていません。

|SQL 型|Python 型|説明
|-------|-----------|---------------------------------------------------------------------------------------------|
|**bigint**|`float64`|
|**[バイナリ]**|`bytes`|
|**bit**|`bool`|
|**char**|`str`|
|**date**|`datetime`|
|**datetime**|`datetime`|SQL Server 2017 CU6 以降でサポートされています (`datetime.datetime` 型または **Pandas** `pandas.Timestamp` 型の **NumPy** 配列を使用します)。 `sp_execute_external_script` では、秒の小数部で `datetime` 型がサポートされるようになりました。|
|**float**|`float64`|
|**int**|`int32`|
|**nchar**|`str`|
|**nvarchar**|`str`|
|**nvarchar(max)**|`str`|
|**real**|`float64`|
|**smalldatetime**|`datetime`|
|**smallint**|`int32`|
|**tinyint**|`int32`|
|**uniqueidentifier**|`str`|
|**varbinary**|`bytes`|
|**varbinary(max)**|`bytes`|
|**varchar(n)**|`str`|
|**varchar(max)**|`str`|
