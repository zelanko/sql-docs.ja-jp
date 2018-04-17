---
title: ユーザーのライブラリでインストールされている R パッケージを使用する場合は、エラーを回避 |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 4609504044e5ef014c4a73e2c4a64a21040db717
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="avoiding-errors-on-r-packages-installed-in-user-libraries"></a>ユーザーのライブラリでインストールされている R パッケージのエラーを回避します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

既定のライブラリがブロックされているか利用できないときに、ライブラリではユーザー、R パッケージをインストールするのには、経験豊富な R ユーザーが慣れています。 ただし、SQL Server では、この方法はサポートされていないと、ユーザー ライブラリへのインストールは通常、「パッケージが見つかりません」エラーで終了します。

この記事では、このエラーを回避するための回避策について説明します。 R コードを変更する方法について説明し、SQL Server インスタンスから R パッケージを使用するため、R パッケージのインストール処理が正しいを提案します。

## <a name="why-r-user-libraries-cannot-be-accessed-from-sql-server"></a>R ユーザーのライブラリを SQL Server からアクセスできない理由

新しい R パッケージをインストールする必要がある R 開発者は、プライベート、ユーザーのライブラリを使用して、既定のライブラリが使用できないときに、または開発者が、コンピューターの管理者でない場合は、パッケージをインストールすることに慣れています。

たとえば、一般的な R 開発環境でユーザーを追加したパッケージの場所、R の環境変数に`libPath`、または次のように、完全なパッケージ パスを参照します。

```R
library("c:/Users/<username>/R/win-library/packagename")
```

機能しない SQL Server で R ソリューションを実行する場合、インスタンスに関連付けられている特定の既定のライブラリに R パッケージをインストールする必要があるためです。 パッケージが既定のライブラリで利用できない場合、パッケージを呼び出すしようとしたときにこのエラーが発生します。

*Library(xxx) でエラー: 'パッケージ名' と呼ばれるパッケージはありません*

## <a name="how-to-avoid-package-not-found-errors"></a>「パッケージが見つかりません」エラーを回避する方法

+ ユーザー ライブラリへの依存関係を排除します。 

    ソリューションは、ライブラリの場所にアクセスできない他のユーザーによって実行される場合のエラーにつながるよう、カスタム ユーザー ライブラリに必要な R パッケージをインストールする不適切な開発の手法を勧めします。

    また、パッケージが既定のライブラリでインストールされている場合、R ランタイムからパッケージを読み込みます、既定のライブラリでは、R コードで、別のバージョンを指定した場合でもです。

+ 共有環境で実行するコードを変更します。

+ ソリューションの一部としてパッケージをインストールしないようにします。 パッケージをインストールするアクセス許可を持っていない場合、コードは失敗します。 場合でも、パッケージをインストールするアクセス許可がある、これとは別に実行する他のコードから行ってください。

+ インストールされていないパッケージへの呼び出しがないよう、コードを確認します。

+ R パッケージまたは R ライブラリのパスへの直接参照を削除するコードを更新します。 

+ どのパッケージ ライブラリは、インスタンスに関連付けられたを知っています。 詳細については、次を参照してください[SQL Server と共にインストールされている R パッケージ。](installing-and-managing-r-packages.md)
