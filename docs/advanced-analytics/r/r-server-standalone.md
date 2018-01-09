---
title: "R Server (スタンドアロン) | Microsoft Docs"
ms.custom: SQL2016_New_Updated
ms.date: 06/22/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
vms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: ca9e48f1-67b8-4905-9b78-56752d7a4e81
caps.latest.revision: "22"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: a7a7a83a1608a4505a3af0401dc8b6ac6f9c180a
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="r-server-standalone"></a>R Server (スタンドアロン)

Microsoft SQL Server 2016 でリリースされた**R Server (スタンドアロン)**、エンタープライズ クラスの分析をサポートするためには、そのプラットフォームの一部として。  Microsoft R Server は、R 言語のスケーラビリティとセキュリティを提供し、オープン ソース r です。 のインメモリ制限に対処SQL Server R Services のようには、Microsoft R Server (スタンドアロン) は、データの並列処理とチャンクの処理に対し、メモリに収まらない非常に大きなデータを使用する R ユーザーの有効化を提供します。

SQL Server 2017、学習、マシン コミュニティの広範なサポートを楽しんでいますし、テキスト分析、深層学習のための一般的なライブラリを含む Python 言語のサポートが追加されました。  この広範な言語を反映するようにしてもを名前変更に**Microsoft Machine Learning Server (スタンドアロン)**です。

## <a name="benefits-of-microsoft-r-server"></a>Microsoft R サーバーの利点

Microsoft R Server を使用するには複数のプラットフォーム上の分散コンピューティング用です。 SQL Server のセットアップからインストールするときに発行および展開モデルの Windows ベースのサーバーとすべての必要なツールを取得します。 その他のプラットフォームの詳細については、MSDN ライブラリのリソースを参照してください。

+ [Introducing Microsoft R Server (Microsoft R Server の概要)](https://msdn.microsoft.com/microsoft-r/rserver)
+ [R Server for Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)

また、RevoScaleR ライブラリおよび SQL Server に展開できる R ソリューションを作成するために必要なツールを取得する、開発クライアントとして使用する Microsoft R Server をインストールすることができます。

## <a name="whats-new-in-microsoft-machine-learning-server"></a>Microsoft Machine Learning のサーバーの新機能

SQL Server 2017 セットアップを使用してマシン ラーニング サービス (スタンドアロン) をインストールする場合は、Python 言語を追加するオプション今すぐ必要です。 必然的に、R 言語が、サポートされているオプションと希望する場合でも、両方の言語をインストールできます。
 
SQL Server 2017 CTP 2.0 で、サーバーのインストールも含まれています、mrsdeploy パッケージおよびその他のユーティリティの運用モデルに使用します。 詳細については、次を参照してください。 [mrsdeploy と操作運用](../../advanced-analytics/operationalization-with-mrsdeploy.md)です。

SQL Server の Machine Learning のエンタープライズ ユーザーは、Microsoft R Server のダウンロード可能なインストーラーを使用して、バインディングと呼ばれるプロセスでの R コンポーネントをアップグレードできます。 詳細については、次を参照してください[をアップグレードし SQL Server のインスタンスを使用して SqlBindR。](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

## <a name="get-microsoft-r-server-or-machine-learning-server-standalone"></a>Microsoft R サーバーまたは Machine Learning Server (スタンドアロン) を取得します。

 Microsoft R Server のインストールに複数のオプションがあります。

+ SQL Server セットアップ ウィザードを使用します。

  [スタンドアロン R Server の作成](../r/create-a-standalone-r-server.md)

  インストールする SQL Server 2016 セットアップを実行して**Microsoft R Server (スタンドアロン)**です。 既定では、R 言語を追加します。
  または、SQL Server 2017 インストールするセットアップ プログラムを実行**Machine Learning Server (スタンドアロン)** R、Python またはその両方を選択します。

  > [!IMPORTANT]
  > サーバーをインストールするオプションは、**共有機能**セットアップのセクションでします。 その他のコンポーネントをインストールしません。
  >
  > 可能であれば、ここで SQL Server R Services または SQL Server マシン ラーニング サービスがインストールされているコンピューターでは、サーバーをインストールしません。

+ SQL Server セットアップのコマンド ライン オプションを使用します。

  [コマンドラインから Microsoft R Server をインストールする](../r/install-microsoft-r-server-from-the-command-line.md)

  SQL Server セットアップでは、豊富なコマンドライン引数を使用して無人インストールをサポートします。

+ スタンドアロンのインストーラーを使用します。

  [Windows 用 Microsoft R Server を実行](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)です。

  新しい Windows インストーラーを使用して、Microsoft R Server または Microsoft Machine Learning のサーバーの新しいインスタンスを設定するようになりましたことができます。  Microsoft R サーバー (および Microsoft Machine Learning サーバー) には、SQL Server のエンタープライズ契約が必要です。 ただし、スタンドアロンのインストーラーを実行すると後で既存のインストールのサポート ポリシーは更新、新しいモダン ライフ サイクル ポリシーを使用します。 このサポート オプションは、machine learning のコンポーネントの更新プログラムが SQL Server のサービス リリースを使用する場合よりも頻繁に適用されることを確認します。

  
+ SQL Server インスタンスをアップグレードします。

  [SqlBindR を使用して R Services のインスタンスをアップグレードする](./use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。
  
  R です。 最新バージョンを使用するのに SQL Server 2016 R Services のインスタンスをアップグレードするのにスタンドアロンのインストーラーを使用することができます。インストーラーを実行して最新のライフ サイクルのサポート ポリシーは、サーバーに適用されます、R コンポーネントがより頻繁に更新プログラムを取得します。
  
  > [!注} 現在この update メソッドは SQL Server 2016 の既存のインストールでのみ使用できます。 、アップグレードがサポートされる SQL Server 2017 の将来的にします。

## <a name="related-machine-learning-products"></a>関連の機械学習の製品

+ R Server と azure の仮想マシン

  [R Server の仮想マシンをプロビジョニングします。](../../advanced-analytics/r-services/provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)
  
  Azure marketplace には、R サーバーを含む複数の仮想マシン イメージが含まれています。 開発と、予測モデルの配置で使用するサーバーをセットアップする最も簡単な方法は、Microsoft Azure で新しい R Server 仮想マシンを作成します。 イメージは、ため、アプリケーション内で R の分析を埋め込むと、バックエンド システムとは、R 統合を容易に対応するスケーリングと、既に構成されている共有の機能が付属します。

+ データ サイエンス仮想マシン

  [データ サイエンス仮想マシン - Windows 2016 Preview](http://aka.ms/dsvm/win2016)

  データ サイエンス仮想マシンの最新バージョンには、R Server、SQL Server が含まれています。 plus 機械学習するための最も一般的なツールの配列のすべてをプレインストールし、テストします。 作成 Jupyter ノートブック、ジュリアは、ソリューションを開発および MXNet、CNTK、TensorFlow など深層学習の GPU が有効なライブラリを使用します。

## <a name="resources"></a>リソース

サンプル、チュートリアル、および Microsoft R Server の詳細についてを参照してください[Microsoft R 製品](https://msdn.microsoft.com/microsoft-r/microsoft-r-getting-started)です。

## <a name="see-also"></a>参照

 [SQL Server R サービス](../../advanced-analytics/r/sql-server-r-services.md)

