---
title: sp_rxPredict |Microsoft Docs
ms.custom: ''
ms.date: 07/14/2017
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
author: jeannt
ms.author: jeannt
manager: craigg
ms.openlocfilehash: ede8232f36f42cc2b9758bdee8f50457ebd58dfe
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036050"
---
# <a name="sprxpredict"></a>sp_rxPredict  
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

格納されたモデルに基づいて予測値を生成します。

ほぼリアルタイムで機械学習モデルのスコア付けを提供します。 `sp_rxPredict` ストアド プロシージャのラッパーとして提供されるは、`rxPredict`関数[RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)と[MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)します。 C++ が書き込まれ、専用の操作をスコア付けは最適化されています。 R の両方をサポートまたは Python の機械学習モデル。

**このトピックの対象**:  
- SQL Server 2017  
- SQL Server 2016 R Services の Microsoft R Server のアップグレード  

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

次のエディションのいずれかが必要です。  
- SQL Server 2017 Machine Learning Services (Microsoft R Server 9.1.0 を含む)  
- Microsoft Machine Learning Server  
- SQL Server R Services 2016、Microsoft R Server 9.1.0 に R Services のインスタンスのアップグレードまたはそれ以降  

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

  対応する SQL 型については、次を参照してください。 [SQL-CLR 型マッピング](https://msdn.microsoft.com/library/bb386947.aspx)または[CLR パラメーター データのマッピング](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)します。

