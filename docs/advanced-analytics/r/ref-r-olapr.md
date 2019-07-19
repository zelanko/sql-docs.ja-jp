---
title: olapR R 関数のライブラリの SQL Server Machine Learning サービス
description: SQL Server 2016 R Services で R と SQL Server 2017 Machine Learning Services olapR 関数ライブラリの概要
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 431fddf870b5755691cad92e576c95d0d3a83890
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962494"
---
# <a name="olapr-r-library-in-sql-server"></a>olapR (SQL Server での R ライブラリ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**olapR**は SQL Server Analysis Services OLAP キューブに対して MDX クエリに使用される R 関数の Microsoft ライブラリです。 関数は MDX のすべての操作をサポートしていませんが、そのスライス、ダイス、ドリルダウン、ロールアップ、およびディメンションをピボットするためのクエリを作成することができます。 

このパッケージは、R セッションにプリロードされていません。 ライブラリの読み込みには、次のコマンドを実行します。

```R
library(olapR)
```

サポートされているすべてのバージョンの SQL Server Analysis Services OLAP キューブへの接続では、このライブラリを使用できます。 この時点では、表形式モデルへの接続はサポートされていません。

## <a name="package-version"></a>パッケージ バージョン

現在のバージョンでは、1.0.0 Windows 専用のすべての製品では、し、提供する、ライブラリをダウンロードします。

## <a name="full-reference-documentation"></a>完全なリファレンス ドキュメント

**Olapr**ライブラリは、複数のマイクロソフト製品で配布されますが、使用量は同じライブラリは、SQL Server または別の製品を取得するかどうか。 関数では同じですが、ため[個々 sqlrutils 関数のドキュメントを](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr)が下の 1 つの場所に発行される、 [R 参照](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference)の Microsoft Machine Learning Server。 製品固有の動作の存在、相違点は、関数のヘルプ ページに記録されます。

## <a name="availability-and-location"></a>可用性と場所

このパッケージは、次の製品と Azure の仮想マシン イメージがいくつか提供されます。 パッケージの場所でもそれに応じて異なります。

製品 | Location |
--------|----------|
(R 統合) SQL Server 2017 Machine Learning サービス | C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library | 
SQL Server 2016 R Services | C:\Program files \microsoft SQL Server\MSSQL13 します。MSSQLSERVER\R_SERVICES\library
Microsoft Machine Learning Server (R Server) | C:\Program Files\Microsoft\R_SERVER\library |
Microsoft R Client | C:\Program Files\Microsoft\R Client\R_SERVER\library |
(Azure) では、データ サイエンス仮想マシン | C:\Program Files\Microsoft\R Client\R_SERVER\library |
(Azure) では、SQL Server 仮想マシン<sup>1</sup> | C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library |

<sup>1</sup> R 統合では、SQL Server で省略可能です。 VM の構成中に、機械学習や、R の機能を追加すると、olapR ライブラリがインストールされます。


## <a name="see-also"></a>関連項目

[OlapR を使って MDX クエリを作成する方法](how-to-create-mdx-queries-using-olapr.md)
