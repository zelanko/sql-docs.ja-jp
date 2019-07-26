---
title: Python から SQL へのデータ型の変換
description: データサイエンスと機械学習ソリューションで、Python と SQL Server の間で暗黙的および明示的なデータ型がどのようになるかを確認します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 8aea7e67f6560aa750e67601b5b6a41f7d68b47d
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470334"
---
# <a name="data-type-mappings-between-python-and-sql-server"></a>Python と SQL Server 間のデータ型マッピング
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server Machine Learning Services の Python 統合機能で実行される Python ソリューションの場合、サポートされていないデータ型の一覧と、Python と SQL Server 間でデータが渡されたときに暗黙的に実行される可能性のあるデータ型の変換を確認してください。

## <a name="python-version"></a>Python のバージョン

SQL Server 2017 Anaconda 4.2 ディストリビューションと Python 3.6。

RevoScaleR 機能 (rxLinMod、rxLogit、rxPredict、rxDTrees、rxBTrees など) のサブセットは、Python Api を使用して、新しい Python パッケージ**revoscalepy**を使用して提供されます。 このパッケージを使用して、パンダのデータフレーム、XDF ファイル、または SQL データクエリを使用してデータを操作できます。

詳細については、「 [revoscalepy module in SQL Server](ref-py-revoscalepy.md) and [revoscalepy 関数リファレンス](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package)」を参照してください。

Python では、SQL Server と比較して、限られた数のデータ型をサポートしています。 その結果、Python スクリプトで SQL Server のデータを使用する場合、データが互換性のあるデータ型に暗黙的に変換される可能性があります。 ただし、多くの場合、正確な変換を自動的に実行することはできず、エラーが返されます。

## <a name="python-and-sql-data-types"></a>Python と SQL のデータ型

次の表に、指定されている暗黙的な変換の一覧を示します。 その他のデータ型はサポートされていません。

|SQLtype|Python の種類|
|-------|-----------|
|**bigint**|`numeric`|
|**binary**|`raw`|
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

