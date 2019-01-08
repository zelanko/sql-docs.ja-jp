---
title: SQL Server に R を検証するためのクイック スタートが存在します
description: SQL Server で R と Machine Learning サービスが存在していることを検証するためのクイック スタートです。
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 2bd9e43232b77bc77611b0c4cd5285b69c9a6261
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046920"
---
# <a name="quickstart-verify-r-exists-in-sql-server"></a>クイック スタート:SQL Server で R が存在することを確認します。 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server には、常駐の SQL Server データでのデータ サイエンス分析のための R 言語サポートが含まれています。 R スクリプトで構成できますのオープン ソース R 関数、サード パーティ製の R ライブラリ、または Microsoft R の組み込みライブラリなど[RevoScaleR](../r/revoscaler-overview.md)規模で予測分析用です。

スクリプトの実行は、次の方法のいずれかを使用して、ストアド プロシージャです。

+ 組み込み[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)ストアド プロシージャで R スクリプトを入力パラメーターとして渡します。
+ R スクリプトをラップする[カスタム ストアド プロシージャ](sqldev-in-database-r-for-sql-developers.md)作成します。

このクイック スタートで、ことを確認は[SQL Server 2017 Machine Learning Services](../what-is-sql-server-machine-learning.md)または[SQL Server 2016 R Services](../r/sql-server-r-services.md)をインストールして構成します。

## <a name="prerequisites"></a>前提条件

この演習では、既にインストールされている、次のいずれかの SQL Server のインスタンスへのアクセスが必要です。

+ [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)、R 言語がインストールされています。
+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)

SQL Server インスタンスは、Azure の仮想マシンまたはオンプレミスにできます。 注意する必要がありますので、既定で外部のスクリプト機能は無効にされる[外部スクリプトを有効に](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature)ことを確認します**SQL Server スタート パッド サービス**が実行されているは、開始する前にします。

SQL クエリを実行するためのツールも必要です。 任意のデータベース管理を使用して R スクリプトを実行したり、ツール、SQL Server インスタンスに接続し、T-SQL クエリまたはストアド プロシージャを実行する限りのクエリを実行できます。 このクイック スタートを使用して[SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)します。

## <a name="verify-r-exists"></a>R の存在を確認します。

SQL Server インスタンスと R のバージョンがインストールされている (R) を使用した Machine Learning サービスが有効になっていることを確認できます。 次の手順に従います。

1. SQL Server Management Studio を開き、SQL Server インスタンスに接続します。

2. 次のコードを実行します。 

    ```SQL
    EXECUTE sp_execute_external_script
    @language =N'R',
    @script=N'print(version)';
    GO
    ```

3. R`print`にバージョンを返します、**メッセージ**ウィンドウ。 次の例の出力で確認できます SQL Server がここで R 3.3.3 がインストールされているバージョンであります。

    **結果**

    ```text
    platform       x86_64-w64-mingw32          
    arch           x86_64                      
    os             mingw32                     
    system         x86_64, mingw32             
    status                                     
    major          3                           
    minor          3.3                         
    year           2017                        
    month          03                          
    day            06                          
    svn rev        72310                       
    language       R                           
    version.string R version 3.3.3 (2017-03-06)
    nickname       Another Canoe               
    ```

このクエリからすべてのエラーが発生した場合のインストール問題を排除します。 インストール後の構成は、外部コード ライブラリの使用を有効にする必要があります。 参照してください[SQL Server 2017 の Machine Learning サービスをインストール](../install/sql-machine-learning-services-windows-install.md)または[SQL Server 2016 R Services のインストール](../install/sql-r-services-windows-install.md)します。 同様に、スタート パッド サービスが実行されていることを確認します。

環境によっては、SQL Server に接続するための R ワーカー アカウントの有効化、追加のネットワーク ライブラリのインストール、リモートでのコード実行の有効化、すべてを構成した後のインスタンスの再起動が必要な場合があります。 詳細については、次を参照してください。 [R Services のインストールとアップグレードに関する FAQ](../r/upgrade-and-installation-faq-sql-server-r-services.md)します。

## <a name="list-r-packages"></a>リストの R パッケージ

Microsoft では、さまざまな SQL Server インスタンスで Machine Learning サービスで事前インストールされている R パッケージを提供します。 どの R のパッケージをインストールのバージョン、依存関係、ライセンス、およびライブラリのパス情報を含む一覧を表示するには、次の手順に従います。

1. SQL Server インスタンスでは、以下のスクリプトを実行します。

    ```SQL
    EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'
    OutputDataSet <- data.frame(installed.packages()[,c("Package", "Version", "Depends", "License", "LibPath")]);'
    WITH result sets((Package NVARCHAR(255), Version NVARCHAR(100), Depends NVARCHAR(4000)
        , License NVARCHAR(1000), LibPath NVARCHAR(2000)));
    ```

2. 出力は`installed.packages()`R で、その結果セットが返されます。

    **結果**

    ![インストールされている r パッケージ](./media/rsql-installed-packages.png)

## <a name="next-steps"></a>次の手順

インスタンスが R を使用する準備が確認した後、これで、詳しく見て基本的な R 対話します。

> [!div class="nextstepaction"]
> [クイック スタート:SQL Server で R スクリプトの"hello world" ](quickstart-r-run-using-tsql.md)
