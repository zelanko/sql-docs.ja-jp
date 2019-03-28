---
title: R プログラミング言語の拡張機能 - SQL Server Machine Learning
description: SQL Server 2016 R Services または SQL Server 2017 Machine Learning Services での組み込みの R ライブラリと R コードの実行について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/05/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: c3f72a755d0ca75ca699465f7eb7a62ea48ff81f
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511369"
---
# <a name="r-language-extension-in-sql-server"></a>SQL Server で R 言語の拡張機能
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

R 拡張機能は、SQL Server Machine Learning サービスにアドオンをリレーショナル データベース エンジンの一部です。 追加、R の実行環境を標準的なライブラリとツール、基本の R ディストリビューションと Microsoft R ライブラリ。[RevoScaleR](../r/ref-r-revoscaler.md) 、規模の分析のため[MicrosoftML](../r/ref-r-microsoftml.md)機械学習アルゴリズム、およびデータまたは SQL Server での R コードにアクセスするための他のライブラリです。

R 統合は、SQL Server で SQL Server 2016 以降で使用できる[R Services](../r/sql-server-r-services.md)、継続の一部として転送[SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md)します。

## <a name="r-components"></a>R コンポーネント

SQL Server には、オープン ソースの独自のパッケージが含まれています。 基本の R ライブラリは、オープン ソース r: の Microsoft の配布によってインストールされます。Microsoft R Open (MRO)。 R の現在のユーザーは、R コードを移植して、ほとんどまたはまったく変更で SQL Server の外部プロセスとして実行できる必要があります。 MRO は、SQL ツールとは別にインストールされているし、機能拡張フレームワークのコア エンジン プロセスの外部で実行されます。 インストール中には、オープン ソース ライセンスの条項に同意する必要があります。 R です。 その他のオープン ソース ディストリビューションの場合と同様に、標準的な R パッケージを変更なしに実行するその後、 

SQL Server では、基本の R 実行可能ファイルでは変更しませんが、そのバージョンが独自のパッケージをビルドしてテストする 1 つであるために、セットアップでインストールする R のバージョンを使用する必要があります。 CRAN から発生する可能性のある R のベース ディストリビューションにおける MRO の違いの詳細については、次を参照してください。 [R 言語と Microsoft R 製品、機能との相互運用](https://docs.microsoft.com/r-server/what-is-r-server-interoperability)します。

セットアップによってインストールされている R 基本パッケージ ディストリビューションは、インスタンスに関連付けられたフォルダーにあります。 たとえば、SQL Server 2016 既定のインスタンスに R Services をインストールした場合、R ライブラリ内にあるこのフォルダー既定で:`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`します。 同様に、既定のインスタンスに関連付けられている R ツールがフォルダーに配置するこの既定:`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin`します。

並列および分散ワークロード用に Microsoft によって追加された R パッケージには、次のライブラリが含まれます。

| ライブラリ | 説明 |
|---------|-------------|
| [**RevoScaleR**](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | データ ソース オブジェクトとデータの探索、操作、変換、および視覚エフェクトをサポートしています。 など、さまざまなスケーラブルな機械学習モデルと同様に、リモート計算コンテキストの作成をサポート**rxLinMod**します。 これらの API は、大きすぎてメモリに収まらないデータ セットの分析と複数のコアまたはプロセッサでの分散計算を実行するように最適化されています。 RevoScaleR パッケージでは、高速移動と分析のために使用されるデータのストレージの XDF ファイルの形式もサポートします。 XDF 形式は、カラム型ストレージを使用する移植可能な形式であり、テキスト、SPSS、ODBC 接続などのさまざまなソースからデータを読み込んで操作するために使用できます。 |
| [**MicrosoftML**](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package) | 場合の速度と精度、最適化されているだけでなく行のテキストとイメージを操作するための変換を機械学習アルゴリズムが含まれています。 詳細については、次を参照してください。 [SQL Server の MicrosoftML](../r/ref-r-microsoftml.md)します。 | 

## <a name="using-r-in-sql-server"></a>SQL Server で R を使用

基本の関数を使用して R スクリプトを作成できますが、複数の処理からメリットを得る、インポートする必要があります、 **RevoScaleR**と**MicrosoftML**を作成するには、その関数をモデル化を呼び出して、R コードをモジュール並列で実行します。 
 
サポートされているデータ ソースには、他のソースまたは R ソリューションのデータを交換するには、ODBC データベース、SQL Server、および XDF ファイル形式が含まれます。 入力データを表形式にする必要があります。 R のすべての結果は、データ フレームの形式で返される必要があります。

サポートされているコンピューティング コンテキストには、ローカルまたはリモートの SQL Server 計算コンテキストが含まれます。 1 台のコンピューター、ワークステーションなどで始まるコードが実行するリモート コンピューティング コンテキストがスクリプトのリモート コンピューターに実行し、スイッチです。 コンピューティング コンテキストを切り替えるには、両方のシステムは、同じ RevoScaleR ライブラリである必要があります。

ローカル計算コンテキストは、T-SQL 内のコードで、データベース エンジンのインスタンスと同じサーバー上の R コードの実行が含まれていますご想像のとおり、またはストアド プロシージャに埋め込まれています。 ローカルの R IDE からコードを実行し、スクリプトが SQL Server コンピューターで実行される、リモートを定義することによって計算コンテキストもできます。

## <a name="execution-architecture"></a>実行のアーキテクチャ

次の図は、SQL Server コンポーネントの各サポートされているシナリオでの R ランタイムとの対話を示しています。 SQL Server のコンピューティング コンテキストを使用して、R コマンド プロンプトからスクリプトでデータベースとリモートの実行を実行しています。

### <a name="r-scripts-executed-from-sql-server-in-database"></a>SQL Server データベースから実行された R スクリプト

SQL Server がストアド プロシージャを呼び出すことによって実行される「内部」から実行される R コードです。 したがって、R コードの実行は、ストアド プロシージャを呼び出す任意のアプリケーションによって開始できます。  その後 SQL Server は、次の図にまとめるとおり、R コードの実行を管理します。

![rsql_indb780-01](../r/media/script_in-db-r.png)

1. ストアド プロシージャ ([sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)) に渡されたパラメーター _@language='R'_ によって、R ランタイムに対する要求が示されます。 SQL Server では、この要求をスタート パッド サービスに送信します。
2. スタート パッド サービスが適切なランチャーを起動します (この場合は RLauncher)。
3. RLauncher が外部の R プロセスを起動します。
4. BxlServer が R ランタイムと SQL Server データの交換と作業結果のストレージの管理を調整します。
5. SQL サテライトは、関連するタスクとプロセスを SQL Server の通信を管理します。
6. BxlServer は、SQL サテライトを使用して、状態と SQL Server に結果を通信します。
7. SQL Server では、結果を取得し、関連するタスクとプロセスを閉じます。

### <a name="r-scripts-executed-from-a-remote-client"></a>リモート クライアントから実行された R スクリプト

Microsoft R をサポートしているリモート データ サイエンス クライアントからの接続時に、RevoScaleR 関数を使用して SQL Server のコンテキストで R 関数を実行できます。 これは、上記のワークフローとは異なるものです。次の図に概要を示します。

![rsql_fromR2db-01](../r/media/remote-sqlcc-from-r2.png)

1. RevoScaleR 関数の場合は、R ランタイムは、BxlServer を呼び出しますリンク関数を呼び出します。
2. BxlServer は Microsoft R と共に提供されているもので、R ランタイムとは別個のプロセスで実行されます。
3. BxlServer は接続のターゲットを決定し、ODBC を使用して接続を開始して、R データ ソース オブジェクト内の接続文字列の一部として提供された資格情報を渡します。
4. BxlServer は、SQL Server インスタンスへの接続を開きます。
5. R 呼び出しの場合、スタート パッド サービスが呼び出されるは有効にする適切なランチャー、RLauncher を開始します。 その後の R コードの処理は、T-SQL から R コードを実行する場合のプロセスと同様です。
6. RLauncher では、SQL Server コンピューターにインストールされている R ランタイムのインスタンスへの呼び出しを実行します。
7. 結果が BxlServer に返されます。
8. SQL サテライトは、SQL Server と関連するジョブ オブジェクトのクリーンアップとの通信を管理します。
9. SQL Server は、クライアントに結果を渡します。

## <a name="see-also"></a>関連項目

+ [SQL Server の機能拡張フレームワーク](extensibility-framework.md)
+ [Python と machine learning の SQL Server の拡張機能](extension-python.md)