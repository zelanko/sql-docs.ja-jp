---
title: Python、SQL データ型の変換 - SQL Server Machine Learning
description: 明示的および暗黙的なデータ型 converstions を Python と SQL Server の間でデータ サイエンスと機械学習ソリューションを確認します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/10/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 9578f81146f0dab42e7a607b9e8ab410313958d4
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2018
ms.locfileid: "53431979"
---
# <a name="data-type-mappings-between-python-and-sql-server"></a>Python と SQL Server 間のデータ型マッピング
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server Machine Learning Services での Python の統合機能を実行している Python ソリューションでは、サポートされていないデータ型、および Python と SQL Server 間のデータが渡されるときに暗黙的に実行することがあるデータ型変換の一覧を確認してください。

## <a name="python-version"></a>Python バージョン

SQL Server 2017 の Anaconda 4.2 配布は、Python 3.6。

RevoScaleR の機能のサブセット (rxLinMod、rxLogit、rxPredict、rxDTrees、rxBTrees、おそらく他のいくつか)、新しい Python パッケージを使用して、Python Api を使用して提供**revoscalepy**します。 このパッケージを使用して、Pandas データ フレーム、XDF ファイル、または SQL データのクエリを使用してデータを操作することができます。

詳細については、次を参照してください。 [SQL Server で revoscalepy モジュール](ref-py-revoscalepy.md)と[revoscalepy 関数リファレンス](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package)します。

Python では、SQL Server とのデータ型の数に制限をサポートします。 その結果、SQL Server からデータを Python スクリプトを使用するたびにデータ可能性があります暗黙的に型に変換を互換性のあるデータ。 ただし、実際の変換を自動的に実行できない多くの場合、エラーが返されます。

## <a name="python-and-sql-data-types"></a>Python と SQL データ型

このテーブルには、提供されている暗黙的な変換が一覧表示します。 他のデータ型はサポートされていません。

|SQLtype|Python の種類|
|-------|-----------|
|**bigint**|`numeric`|
|**[バイナリ]**|`raw`|
|**bit**|`bool`|
|**char**|`str`|
|**float**|`float64`|
|**int**|`int32`|
|**nchar**|`str`|
|**nvarchar**|`str`|
|**nvarchar(max)**|`str`|
|**real**|`float32`|
|**smallint**|`int16`|
|**tinyint**|`uint8`|
|**varbinary**|`bytes`|
|**varbinary(max)**|`bytes`|
|**varchar(n)**|`str`|
|**varchar(max)**|`str`|

## <a name="see-also"></a>関連項目

