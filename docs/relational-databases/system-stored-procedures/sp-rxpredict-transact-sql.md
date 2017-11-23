---
title: "sp_rxPredict |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_rxPredict
- sp_rxPredict_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_rxPredict procedure
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c150649eb7cc45de0d3587a006a58af9bb416b4c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sprxpredict"></a>sp_rxPredict  
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

保存されたモデルに基づいて予測した値を生成します。

ほぼリアルタイムでの機械学習モデルのスコアを提供します。 `sp_rxPredict`ラッパーとして指定されたストアド プロシージャは、`rxPredict`関数[RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)と[MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)です。 C + で記述され、スコア付けの操作専用に最適化します。 両方の R をサポートしている、または Python 機械学習モデルです。

**このトピックの対象**:  
- SQL Server 2017  
- Microsoft R Server へアップグレードすると SQL Server 2016 R Services  

## <a name="syntax"></a>構文

```
sp_rxPredict  ( @model, @input )
```

### <a name="arguments"></a>引数

**model**

サポートされている形式で事前トレーニング済みモデル。 

**入力**

有効な SQL クエリ

### <a name="return-values"></a>戻り値

入力データ ソースからのパススルー列だけでなく、スコア列が返されます。
追加、信頼区間などの列をスコア付け、アルゴリズムがこのような値の生成をサポートしているかどうかに返されることができます。

## <a name="remarks"></a>解説

ストアド プロシージャの使用を有効にするには、SQLCLR はインスタンスで有効にする必要があります。

> [!NOTE]
> このオプションを有効にするには、セキュリティへの影響を検討してください。

ユーザーのニーズ`EXECUTE`データベースに対する権限。

### <a name="supported-platforms"></a>サポートされているプラットフォーム

次のエディションのいずれかが必要です。  
- SQL Server 2017 Machine Learning Services (Microsoft R Server 9.1.0 が含まれています)  
- Microsoft Machine Learning サーバー  
- SQL Server R Services 2016、Microsoft R Server 9.1.0 に R Services のインスタンスのアップグレードまたはそれ以降  

### <a name="supported-algorithms"></a>サポートされるアルゴリズム

サポートされているアルゴリズムの一覧は、次を参照してください。[リアルタイム スコアリング](../../advanced-analytics/real-time-scoring.md)です。

次の種類のモデルは**いない**サポートします。  
- サポートされていない、他の種類の R の変換を含むモデル  
- 使用してモデル化、`rxGlm`または`rxNaiveBayes`RevoScaleR 内のアルゴリズム  
- PMML モデル  
- CRAN または他のリポジトリから他の R ライブラリを使用して作成されたモデル  
- 含むその他の種類は、ここに記載されている以外の R 変換のモデル  

## <a name="examples"></a>使用例

```sql
DECLARE @model = SELECT @model 
FROM model_table 
WHERE model_name = 'rxLogit trained';

EXEC sp_rxPredict @model = @model,
@inputData = N'SELECT * FROM data';
```

有効な SQL クエリ内の入力データだけでなく *@inputData* ストアドのモデル内の列と互換性のある列を含める必要があります。

`sp_rxPredict`次の .NET の列型のみをサポートしています: float、short、ushort、double、long、ulong と文字列。 リアルタイムのスコアリングのために使用する前に、入力データでサポートされていない型を除外する必要があります。 

  対応する SQL 型については、次を参照してください。 [SQL-CLR 型マッピング](https://msdn.microsoft.com/library/bb386947.aspx)または[CLR パラメーター データのマッピング](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)です。

