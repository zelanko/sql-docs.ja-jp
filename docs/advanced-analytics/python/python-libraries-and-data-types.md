---
title: "Python ライブラリ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/30/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: python
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d2f1dcd37a9e620402e299565f920f479e206ae4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="python-libraries-and-data-types"></a>Python ライブラリとデータ型

このトピックでは、次の製品に含まれている Python ライブラリについて説明します。

+ SQL Server コンピューターのサービス (In-database) を学習
+ マイクロソフトの機械学習のサーバー (スタンドアロン)

このトピックは、サポートされていないデータ型も一覧表示されます。 し、リスト、データ型の Python と SQL Server の間でデータが渡されるときに暗黙的に実行することが変換します。

## <a name="python-version"></a>Python のバージョン

SQL Server 2017 CTP 2.0 には、Python 3.6、Anaconda ディストリビューションの部分が含まれています。

RevoScaleR 機能のサブセット (rxLinMod、rxLogit、rxPredict、rxDTrees、rxBTrees、状況によって異なるいくつか他のユーザー) は新しい Python パッケージを使用して、Python の API を使用して提供**RevoScalePy**です。 このパッケージを使用して、パンダ データ フレームを使用してデータを操作することができます。XDF ファイル、またはデータの SQL クエリ。

詳細については、次を参照してください。 [revoscalepy のは何ですか?](what-is-revoscalepy.md)です。

## <a name="python-and-sql-data-types"></a>Python と SQL データ型

Python は、限定された数の SQL Server と比較するとデータ型をサポートします。

データを使用する場合にその結果、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Python スクリプトでデータが暗黙的に変換を互換性のあるデータ型にします。 ただし、正確な変換が自動的に実行できない多くの場合、エラーが返されます。

このテーブルには、提供されている暗黙的な変換が一覧表示します。 他のデータ型はサポートされていません。

|SQLtype|Python の型|
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



