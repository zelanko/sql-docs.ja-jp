---
title: SQL Server Machine Learning での Python ライブラリとデータ型 |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7b977d079589dbb4c54d5c31fec644d9f984dd61
ms.sourcegitcommit: 9528843359cc43b9c66afac363f542ae343266e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "40434852"
---
# <a name="python-libraries-and-data-types"></a>Python ライブラリとデータ型
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server Machine Learning サービス (In-database) と (スタンドアロン) のインストールに含まれる Python ライブラリについて説明します。

この記事では、サポートされていないデータ型も一覧表示されます。 し、一覧データが Python と SQL Server 間のデータが渡されるときに暗黙的に実行することが変換を入力します。

## <a name="python-version"></a>Python バージョン

SQL Server 2017 の Anaconda 4.2 配布は、Python 3.6。

RevoScaleR の機能のサブセット (rxLinMod、rxLogit、rxPredict、rxDTrees、rxBTrees、おそらく他のいくつか)、新しい Python パッケージを使用して、Python Api を使用して提供**revoscalepy**します。 このパッケージを使用して、Pandas データ フレーム、XDF ファイル、または SQL データのクエリを使用してデータを操作することができます。

詳細については、次を参照してください。 [revoscalepy のとは何ですか?](what-is-revoscalepy.md)します。

## <a name="python-and-sql-data-types"></a>Python と SQL データ型

Python では、SQL Server とのデータ型の数に制限をサポートします。

データを使用する場合にその結果、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Python スクリプトでデータが暗黙的に変換を互換性のあるデータ型にします。 ただし、実際の変換を自動的に実行できない多くの場合、エラーが返されます。

このテーブルには、提供されている暗黙的な変換が一覧表示します。 他のデータ型はサポートされていません。

|SQLtype|Python の種類|
|-|-|
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



