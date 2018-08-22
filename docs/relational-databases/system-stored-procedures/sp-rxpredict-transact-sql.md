---
title: sp_rxPredict |Microsoft Docs
ms.custom: ''
ms.date: 08/20/2018
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_rxPredict
- sp_rxPredict_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_rxPredict procedure
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8f46403afef0e2f6cf967561a8fd24ec6409fe93
ms.sourcegitcommit: 9528843359cc43b9c66afac363f542ae343266e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "40434862"
---
# <a name="sprxpredict"></a>sp_rxPredict  
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Machine learning の SQL Server データベースにバイナリ形式で格納されているモデルに基づく特定の入力に対して予測された値を生成します。

R と Python の機械学習のモデルがほぼリアルタイムでのスコア付けを提供します。 `sp_rxPredict` ストアド プロシージャのラッパーとして提供されるは、`rxPredict`で R 関数[RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)と[MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)、および[rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) でのPython関数[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package)と[microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)します。 C++ が書き込まれ、専用の操作をスコア付けは最適化されています。

**この記事は**:  
- SQL Server 2017  
- SQL Server 2016 R Services の[R コンポーネントをアップグレード](https://docs.microsoft.com/sql/advanced-analytics/r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server)

## <a name="syntax"></a>構文

```
sp_rxPredict  ( @model, @input )
```

### <a name="arguments"></a>引数

**model**

サポートされている形式で事前トレーニング済みモデル。 

**input**

有効な SQL クエリ

### <a name="return-values"></a>戻り値

入力データ ソースからのパススルー列と、スコア列が返されます。
追加、信頼区間などの列にスコアを付け、アルゴリズムがこのような値の生成をサポートするかどうかに返されることができます。

## <a name="remarks"></a>コメント

ストアド プロシージャの使用を有効にするには、インスタンスで SQLCLR を有効にする必要があります。

> [!NOTE]
> このオプションを有効にする前に、セキュリティへの影響を検討してください。

ユーザーのニーズ`EXECUTE`データベースに対する権限。

### <a name="supported-platforms"></a>サポートされているプラットフォーム
 
- SQL Server 2017 Machine Learning サービス (R Server 9.2 を含む)  
- SQL Server 2017 Machine Learning Server (スタンドアロン) 
- SQL Server R Services 2016、R server 9.1.0 R Services のインスタンスのアップグレードまたはそれ以降  

### <a name="supported-algorithms"></a>サポートされているアルゴリズム

サポートされているアルゴリズムの一覧は、次を参照してください。[リアルタイム スコアリング](../../advanced-analytics/real-time-scoring.md)します。

モデルの種類は**いない**サポートされています。  
- サポートされていない、他の種類の R の変換を含むモデル  
- モデルを使用して、`rxGlm`または`rxNaiveBayes`revoscaler アルゴリズム  
- PMML モデル  
- CRAN またはその他のリポジトリから他の R ライブラリを使用して作成されたモデル  
- R の変換は、ここに記載されている以外の他の種類を含むモデル  

## <a name="examples"></a>使用例

```sql
DECLARE @model = SELECT @model 
FROM model_table 
WHERE model_name = 'rxLogit trained';

EXEC sp_rxPredict @model = @model,
@inputData = N'SELECT * FROM data';
```

有効な SQL クエリ内の入力データだけでなく*@inputData*格納されたモデルで列と互換性のある列を含める必要があります。

`sp_rxPredict` 次の .NET の列型のみをサポートしています: float、short、ushort、double、long、ulong と文字列。 リアルタイム スコアリングのために使用する前に、入力データでサポートされていない型を除外する必要があります。 

  対応する SQL 型については、次を参照してください。 [SQL-CLR 型マッピング](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping)または[CLR パラメーター データのマッピング](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)します。

