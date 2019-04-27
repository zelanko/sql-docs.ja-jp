---
title: ユーザー ライブラリ - SQL Server Machine Learning Services にインストールされている R パッケージの使用に関するヒント
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/30/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: ee5dc9dc8b1730f26bada915d739f164a884801d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62642286"
---
# <a name="tips-for-using-r-packages-in-sql-server"></a>SQL Server で R パッケージを使用するためのヒント
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、R と SQL Server インスタンスで未知のパッケージ アクセス経験豊富な R 開発者に慣れていない Dba の個別のセクションがあります。

## <a name="new-to-r"></a>新しい r

R のインストールに管理者として R パッケージの管理について、いくつかの基本的なことができますを知ることの最初のパッケージを開始します。

### <a name="package-dependencies"></a>パッケージの依存関係

R パッケージは、頻繁に他のうちいくつか使用できないインスタンスによって使用される既定の R ライブラリに複数のパッケージに依存します。 場合があります、パッケージには、既にインストールされている依存パッケージの別のバージョンが必要です。 パッケージの依存関係は、パッケージに埋め込まれた記述ファイルに記録されますが不完全な場合があります。 という名前のパッケージを使用する[iGraph](https://igraph.org/r/)完全に依存関係グラフを明確にします。

使用することをお勧めを確実に適切なパッケージの種類とバージョンを取得、組織内のすべてのユーザーを複数のパッケージをインストールする必要がある場合、 [miniCRAN](https://mran.microsoft.com/package/miniCRAN)完全な依存関係チェーンを分析するパッケージ。 minicRAN は、複数のユーザーまたはコンピューター間で共有できるローカル リポジトリを作成します。 詳細については、次を参照してください。 [miniCRAN を使用してローカル パッケージ リポジトリを作成する](create-a-local-package-repository-using-minicran.md)します。

### <a name="package-sources-versions-and-formats"></a>パッケージ ソース、バージョン、およびフォーマット

R パッケージの複数のソースとして[CRAN](https://cran.r-project.org/)と[Bioconductor](https://www.bioconductor.org/)します。 R 言語の公式サイト (<https://www.r-project.org/>) これらのリソースを一覧表示されます。 Microsoft は[MRAN](https://mran.microsoft.com/)のオープン ソース R の配布 ([MRO](https://mran.microsoft.com/open)) と他のパッケージ。 多くのパッケージは、GitHub、開発者がソース コードを取得する場所に発行されます。

R パッケージは、複数のコンピューティング プラットフォームで実行します。 インストールするバージョンが Windows バイナリであることを確認します。

### <a name="know-which-library-you-are-installing-to-and-which-packages-are-already-installed"></a>ライブラリをインストールして、既にインストールされているパッケージを確認します。

何もインストールする前に以前のコンピューター上の R 環境を変更した場合は必ず、R 環境変数`.libPath`は 1 つのパスを使用します。

このパスは、インスタンスの R_SERVICES フォルダーを指定する必要があります。 詳細については、どのパッケージが既にインストールされているかを決定する方法などを参照してください。 [SQL Server の既定の R と Python のパッケージ](installing-and-managing-r-packages.md)します。

## <a name="new-to-sql-server"></a>SQL server

SQL Server で実行中のコードに取り組んで、R 開発者としては、サーバーを保護するセキュリティ ポリシーは、R 環境を制御する機能を制限します。

### <a name="r-user-libraries-not-supported-on-sql-server"></a>R ユーザー ライブラリ: SQL Server でサポートされていません

新しい R パッケージをインストールする必要のある R 開発者は、プライベート、ユーザー ライブラリを使用して、既定のライブラリが使用できない場合、または開発者が、コンピューターの管理者でない場合は、パッケージのインストールに慣れています。 など、一般的な R 開発環境で、ユーザーは、パッケージの場所、R 環境変数に追加`libPath`、または、次のように、パッケージの完全なパスを参照します。

```R
library("c:/Users/<username>/R/win-library/packagename")
```

これは機能しません、SQL Server で R ソリューションを実行しているため、インスタンスに関連付けられている特定の既定のライブラリに R パッケージをインストールする必要があります。 既定のライブラリでパッケージを利用できない場合、パッケージを呼び出すしようとするときにこのエラーが発生します。

*ライブラリ (xxx) でエラー: 'パッケージ名' という名前のパッケージはありません*

### <a name="avoid-package-not-found-errors"></a>「パッケージが見つかりません」エラーを回避します。

+ ユーザー ライブラリへの依存を排除します。 

    ソリューションは、ライブラリの場所にアクセスできない他のユーザーによって実行される場合のエラーにつながるよう、カスタム ユーザー ライブラリに必要な R パッケージをインストールするの不適切な開発手法を勧めします。

    また、既定のライブラリでパッケージをインストールすると場合、R ランタイム パッケージを読み込みます既定のライブラリから R コードで、別のバージョンを指定した場合でも。

+ 共有環境で実行するコードを変更します。

+ ソリューションの一部としてパッケージをインストールしないでください。 パッケージをインストールするアクセス許可を持っていない場合、コードは失敗します。 パッケージをインストールするアクセス許可を持っている場合でもを実行する他のコードからとは別にこれを行う必要があります。

+ インストールされていないパッケージへの呼び出しがないよう、コードを確認します。

+ R パッケージまたは R ライブラリのパスへの直接参照を削除するコードを更新します。 

+ パッケージ ライブラリは、インスタンスに関連付けられています。 詳細については、次を参照してください。 [SQL Server の既定の R と Python のパッケージ](installing-and-managing-r-packages.md)します。

## <a name="see-also"></a>関連項目

+ [新しい R パッケージのインストール](install-additional-r-packages-on-sql-server.md)
+ [新しい Python パッケージのインストール](../python/install-additional-python-packages-on-sql-server.md)
+ [チュートリアル、サンプル、ソリューション](../tutorials/machine-learning-services-tutorials.md)