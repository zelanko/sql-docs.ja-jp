---
title: SQL Server 上のユーザーのライブラリにインストールされている R パッケージを使用するためのヒント |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/30/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e52a6f4a9a3830aab01e54819804785a7069c9d2
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34708470"
---
# <a name="tips-for-using-r-packages-in-sql-server"></a>SQL Server で R パッケージを使用するためのヒント
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、R と SQL Server インスタンスで未知のパッケージのアクセスは、経験豊富な R 開発者に精通している Dba の個別のセクションがあります。

## <a name="new-to-r"></a>初めて使用する R

R をインストールする管理者として R パッケージの管理について、いくつかの基本的なことができますを知ること、初めてパッケージ作業を開始します。

### <a name="package-dependencies"></a>パッケージの依存関係

R パッケージは、多くの場合、これらのいくつかできない可能性があります、インスタンスによって使用される既定の R ライブラリで、その他の複数のパッケージに依存します。 場合もありますパッケージには、既にインストールされている依存パッケージの別のバージョンが必要です。 パッケージの依存関係は、パッケージに埋め込まれた記述ファイルに記録されますが不完全な場合があります。 呼ばれるパッケージを使用して[iGraph](http://igraph.org/r/)完全に依存関係グラフを明確にします。

使用することをお勧めを複数のパッケージをインストールまたは正しいパッケージの種類とバージョン、組織内のすべてのユーザーを取得することを確認する必要がある場合、 [miniCRAN](https://mran.microsoft.com/package/miniCRAN)完全な依存関係チェーンを分析するパッケージ。 minicRAN では、複数のユーザーまたはコンピューター間で共有できるローカル リポジトリを作成します。 詳細については、次を参照してください。 [miniCRAN を使用して、ローカルのパッケージ リポジトリを作成する](create-a-local-package-repository-using-minicran.md)です。

### <a name="package-sources-versions-and-formats"></a>パッケージ ソース、バージョン、およびフォーマット

R パッケージに複数のソースなどが[CRAN](https://cran.r-project.org/)と[Bioconductor](https://www.bioconductor.org/)です。 R 言語の公式サイト (<https://www.r-project.org/>) これらのリソースの多くを一覧表示します。 Microsoft では[MRAN](https://mran.microsoft.com/)オープン ソース R の配布の ([MRO](https://mran.microsoft.com/open)) およびその他のパッケージです。 多くのパッケージは、GitHub、開発者が、ソース コードを取得する場所に発行されます。

R パッケージは、複数のコンピューティング プラットフォームで実行します。 インストールするバージョンが Windows バイナリであることを確認します。

### <a name="know-which-library-you-are-installing-to-and-which-packages-are-already-installed"></a>ライブラリをインストールして、既にインストールされているパッケージを把握しています。

変更した場合は以前、コンピューター上の R 環境は、何もインストールする前に、いることを確認、R の環境変数`.libPath`は 1 つのパスを使用します。

このパスは、インスタンスの R_SERVICES フォルダーを指す必要があります。 詳細については、どのパッケージが既にインストールされているかを決定する方法などを参照してください。 [SQL Server で R の既定と Python パッケージ](installing-and-managing-r-packages.md)です。

## <a name="new-to-sql-server"></a>SQL Server に新しい

SQL Server で実行中のコードで作業して、R 開発者としては、サーバーを保護するセキュリティ ポリシーは、R の環境を制御する機能を制限します。

### <a name="r-user-libraries-not-supported-on-sql-server"></a>R ユーザー ライブラリ: SQL Server でサポートされていません

新しい R パッケージをインストールする必要がある R 開発者は、プライベート、ユーザーのライブラリを使用して、既定のライブラリが使用できないときに、または開発者が、コンピューターの管理者でない場合は、パッケージをインストールすることに慣れています。 たとえば、一般的な R 開発環境でユーザーを追加したパッケージの場所、R の環境変数に`libPath`、または次のように、完全なパッケージ パスを参照します。

```R
library("c:/Users/<username>/R/win-library/packagename")
```

機能しない SQL Server で R ソリューションを実行する場合、インスタンスに関連付けられている特定の既定のライブラリに R パッケージをインストールする必要があるためです。 パッケージが既定のライブラリで利用できない場合、パッケージを呼び出すしようとしたときにこのエラーが発生します。

*Library(xxx) でエラー: 'パッケージ名' と呼ばれるパッケージはありません*

### <a name="avoid-package-not-found-errors"></a>「パッケージが見つかりません」エラーを回避します。

+ ユーザー ライブラリへの依存関係を排除します。 

    ソリューションは、ライブラリの場所にアクセスできない他のユーザーによって実行される場合のエラーにつながるよう、カスタム ユーザー ライブラリに必要な R パッケージをインストールする不適切な開発の手法を勧めします。

    また、パッケージが既定のライブラリでインストールされている場合、R ランタイムからパッケージを読み込みます、既定のライブラリでは、R コードで、別のバージョンを指定した場合でもです。

+ 共有環境で実行するコードを変更します。

+ ソリューションの一部としてパッケージをインストールしないようにします。 パッケージをインストールするアクセス許可を持っていない場合、コードは失敗します。 場合でも、パッケージをインストールするアクセス許可がある、これとは別に実行する他のコードから行ってください。

+ インストールされていないパッケージへの呼び出しがないよう、コードを確認します。

+ R パッケージまたは R ライブラリのパスへの直接参照を削除するコードを更新します。 

+ どのパッケージ ライブラリは、インスタンスに関連付けられたを知っています。 詳細については、次を参照してください。 [SQL Server で R の既定と Python パッケージ](installing-and-managing-r-packages.md)です。

## <a name="see-also"></a>参照

+ [新しい R パッケージのインストール](install-additional-r-packages-on-sql-server.md)
+ [新しい Python パッケージのインストール](../python/install-additional-python-packages-on-sql-server.md)
+ [チュートリアル、サンプル、ソリューション](../tutorials/machine-learning-services-tutorials.md)