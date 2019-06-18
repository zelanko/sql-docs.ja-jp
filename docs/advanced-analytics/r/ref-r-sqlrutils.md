---
title: sqlrutils ヘルパー関数 - SQL Server Machine Learning サービス
description: R を使用した SQL Server 2016 R Services と SQL Server 2017 Machine Learning Services sqlrutils 関数ライブラリを使用すると、R スクリプトを含むストアド プロシージャを生成できます。
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 7ccc3ad494658fc7a8f9c67472aecb1c4cddb7da
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62641752"
---
# <a name="sqlrutils-r-library-in-sql-server"></a>sqlrutils (SQL Server での R ライブラリ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**sqlrutils** パッケージは R ユーザーに、R スクリプトを T-SQL ストアド プロシージャに配置し、そのストアド プロシージャをデータベースに登録し、R 開発環境からそのストアド プロシージャを実行するメカニズムを提供します。 

R コードを変換して 1 つのストアド プロシージャ内で実行されるようにすると、R スクリプトが [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)へのパラメーターとして埋め込まれる必要のある SQL Server R Services をより効率的に使用できるようになります。 **sqlrutils** パッケージを使用すると、この組み込みの R スクリプトを構築し、関連するパラメーターを適切に設定することができます。

**sqlrutils** パッケージは、次を行います。

- 生成された T-SQL スクリプトを R データ構造内に文字列として保存する
- オプションで、ストアド プロシージャを編集または実行できる .sql ファイルを T-SQL スクリプト用に生成する
- 新しく作成したストアド プロシージャを R 開発環境から SQL Server インスタンスに登録できる

整形されたパラメーターを渡し、結果を処理することによって、R 環境からストアド プロシージャを実行することも可能です。 または、ETL、モデルのトレーニング、大量のスコア付けなどの一般的なデータベースの統合シナリオをサポートするよう、SQL Server からストアド プロシージャを使用することも可能です。

  > [!NOTE]
  > *executeStoredProcedure* 関数を呼び出し、R 環境からストアド プロシージャを実行する場合、SQL Server 用 ODBC ドライバー 13 など、ODBC 3.8 プロバイダーを使用する必要があります。  
  
## <a name="full-reference-documentation"></a>完全なリファレンス ドキュメント

**Sqlrutils**ライブラリは、複数のマイクロソフト製品で配布されますが、使用量は同じライブラリは、SQL Server または別の製品を取得するかどうか。 関数では同じですが、ため[個々 sqlrutils 関数のドキュメントを](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)が下の 1 つの場所に発行される、 [R 参照](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference)の Microsoft Machine Learning Server。 製品固有の動作の存在、相違点は、関数のヘルプ ページに記録されます。

## <a name="functions-list"></a>関数一覧

次のセクションでから呼び出すことのできる関数の概要、 **sqlrutils**埋め込まれた R コードのパッケージを含むストアド プロシージャを開発します。 各メソッドまたは関数のパラメーターの詳細については、パッケージの R のヘルプを参照してください。 `help(package="sqlrutils")`

|関数 | 説明 |
|------|-------------|
|[executeStoredProcedure](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/executestoredprocedure)| SQL ストアド プロシージャを実行します。|
|[getInputParameters](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/getinputparameters)| ストアド プロシージャへの入力パラメーターの一覧を取得します。| 
|[InputData](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/inputdata)| R データ フレームで使用されるデータ ソースを SQL Server に定義します。 入力データを保存する data.frame 名、データまたは既定値を取得するクエリを指定します。 単純な SELECT クエリのみがサポートされています。 | 
|[InputParameter](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/inputparameter)| T-SQL スクリプトに埋め込まれる単一の入力パラメーターを定義します。 パラメーター名とその R データ型を指定する必要があります。| 
|[OutputData](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/outputdata)| R 関数で data.frame を含むリストが返される場合に必要な中間のデータ オブジェクトを生成します。 *OutputData* オブジェクトは、リストから取得された単一の data.frame の名前を格納するために使用されます。| 
|[OutputParameter](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/outputparameter) | R 関数でリストが返される場合に必要な中間のデータ オブジェクトを生成します。 *OutputParameter* オブジェクトは、メンバーがデータ フレームでは **ない** ことを想定し、リストの単一のメンバーの名前とデータ型を格納します。 |
|[registerStoredProcedure](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/registerstoredprocedure) | データベースでストアド プロシージャを登録します。|
|[setInputDataQuery](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/setinputdataquery)| ストアド プロシージャのパラメーター入力データにクエリを割り当てます。| 
|[setInputParameterValue](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/setinputparametervalue)| ストアド プロシージャの入力パラメーターに値を割り当てます。| 
|[ストアド プロシージャ](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/storedprocedure)| ストアド プロシージャ オブジェクト。|


## <a name="how-to-use-sqlrutils"></a>Sqlrutils を使用する方法

**Sqlrutils**ライブラリ関数が R と SQL Server Machine Learning を持つコンピューターで実行する必要がありますクライアント ワークステーションで作業している場合は、SQL Server に shift キーを実行するリモート コンピューティング コンテキストを設定します。 このパッケージを使用するためのワークフローには、次の手順が含まれています。

+ ストアド プロシージャのパラメーター (入力、出力、またはその両方) の定義します。 
+ 生成し、ストアド プロシージャの登録    
+ ストアド プロシージャを実行する  

R セッションで読み込む**sqlrutils** 」と入力してコマンド ラインから`library(sqlrutils)`します。

> [!Note]
> コンピューターがない SQL Server (たとえば、R クライアント インスタンス) 上に SQL Server 計算コンテキストを変更し、その計算コンテキストでコードを実行する場合は、このライブラリを読み込むことができます。


### <a name="define-stored-procedure-parameters-and-inputs"></a>ストアド プロシージャのパラメーターと入力を定義します。

`StoredProcedure` はストアド プロシージャの構築に使用されるメインのコンストラクターです。 このコンストラクターは、 *SQL Server ストアド プロシージャ* オブジェクトを生成し、オプションで T-SQL コマンドを使用したストアド プロシージャの生成に使用できるクエリを含むテキスト ファイルを作成します。 

*StoredProcedure* 関数では、オプションで、指定したインスタンスとデータベースを使用してストアド プロシージャを登録することもできます。

+ 有効な R 関数を指定するには、 `func` 引数を使用します。 この関数が使用するすべての変数は、関数内に定義するか、入力パラメーターとして渡される必要があります。 これらのパラメーターには、最大でデータ フレームを 1 つ含めることが可能です。

+ R 関数は、データ フレーム、名前付きのリスト、NULL 値のいずれかを返す必要があります。 関数がリストを返す場合、リストには最大で 1 つの data.frame のみ含めることができます。

+ 作成するストアド プロシージャの名前を指定するには、 `spName` 引数を使用します。

+ `setInputData`、 `setInputParameter`および `setOutputParameter`のヘルパー関数によって作成されるオブジェクトを使用することにより、オプションの入力および出力パラメーターに渡すことができます。

+  作成する .sql ファイルに名前とパスを提供する場合、オプションで `filePath` を使用します。 このファイルを SQL Server インスタンスで実行すると、T-SQL を使用したストアド プロシージャを生成できます。

+ ストアド プロシージャの保存先のサーバーおよびデータベースを定義するには、 `dbName` と  `connectionString`の引数を使用します。

+ 特定の *StoredProcedure* オブジェクトを作成するのに使用された *InputData* と *InputParameter* オブジェクトのリストを取得するには、 `getInputParameters`を呼び出します。 

+ 指定したデータベースにストアド プロシージャを登録するには、 `registerStoredProcedure`を使用します。

ストアド プロシージャ オブジェクトには、既定値が指定されている場合を除き、通常データや値は関連付けられていません。 ストアド プロシージャが実行されるまで、データは取得されません。 

### <a name="specify-inputs-and-execute"></a>入力を指定し、実行

+ `setInputDataQuery` を使用して、 *InputParameter* オブジェクトにクエリを割り当てます。 たとえば、R でストアド プロシージャ オブジェクトを作成した場合、必要な入力を使用してストアド プロシージャを実行するには、 `setInputDataQuery` を使用して *StoredProcedure* 関数に引数を渡します。

+ `setInputValue` InputParameter *オブジェクトとして格納されているパラメーターに特定の値を割り当てるには、* を使用します。 次に、 *StoredProcedure* 関数にパラメーター オブジェクトとその値の割り当てを渡し、ストアド プロシージャを設定値で実行します。

+ `executeStoredProcedure` StoredProcedure *オブジェクトとして定義されたストアド プロシージャを実行するには、* を使用します。 この関数は、R コードからこのストアド プロシージャを実行する場合のみ呼び出します。 T-SQL を使用して SQL Server からストアド プロシージャを実行する場合は使用しないでください。

> [!NOTE]
> *executeStoredProcedure* 関数には、SQL Server 用の ODBC ドライバー 13 などの ODBC 3.8 プロバイダーが必要です。  

## <a name="see-also"></a>関連項目

[Sqlrutils を使用してストアド プロシージャを作成する方法](how-to-create-a-stored-procedure-using-sqlrutils.md)

