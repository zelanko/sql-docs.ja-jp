---
title: Azure Data Studio の sandDance
titleSuffix: Azure Data Studio
description: Azure Data Studio で SandDance を使用する方法
ms.custom: seodec18
ms.date: 07/03/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: a96bde6a66642bf02cc076c3d4d4f3ac44e02a3f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959332"
---
# <a name="sanddance-for-azure-data-studio-preview"></a>SandDance for Azure Data Studio (プレビュー)
Azure Data Studio には、.csv、.tsv ファイルで作業しているの簡単な視覚エフェクトを作成する方法を今すぐは提供します。 SQL Server 2019 ビッグ データ クラスター内のローカル ファイルまたは HDFS 上のファイルが含まれます。 迅速なデータを確認し、何が起こってを理解している場合、この拡張機能の使用をお勧めします。 データの場所で視覚化を生成できるは、Microsoft research SandDance と呼ばれるテクノロジを使用します。

![sanddance アニメーション](https://user-images.githubusercontent.com/11507384/54236654-52d42800-44d1-11e9-859e-6c5d297a46d2.gif)

SandDance 役立ちますが有効にするヘルプのデータでサポートされているストーリーを伝える証拠に基づいてケースを構築するには、データに関する洞察を検索する、わかりやすくビューを使用して仮説をテスト、サーフェスの説明に深くの購入の決定をサポートまたはデータを広い、実際のコンテキストに関連してください。

SandDance が画面に、データベース内の行とマーク間の一対一のマッピングを適用する単体の視覚エフェクトを使用します。
ビューの間で切り替えの滑らかなアニメーションを使用して、データと対話するコンテキストを維持するのに役立ちます。

## <a name="usage"></a>使用方法

含むディレクトリを開くフォルダーを開くか、[Ctrl + K Ctrl + O] を使用してファイルメニューから起動します。CSV ファイル。  次から、エクスプ ローラー パネル内で .csv ファイルまたは .tsv ファイルを右クリックし、選択*SandDance ビュー*します。

SQL Server 2019 ビッグ データ クラスターに接続し、選択した場合は、HDFS で .csv ファイルまたは .tsv ファイルを右クリックして*SandDance ビュー*します。

## <a name="known-issues"></a>既知の問題

現時点では、データは、一意の識別子として最初の列が必要です。

現時点では、視覚化される行の数キャップしません。 ただし、メモリ消費量は比例して、行の数をデータ セットまたはビューが約 100 k 行に制限されることをお勧めします。

参照してください[既知の問題](https://microsoft.github.io/SandDance/#known-issues)

## <a name="release-notes"></a>リリース ノート

### <a name="100"></a>1.0.0

Azdata sanddance の最初のリリース

## <a name="next-steps"></a>次の手順
詳細については、 [GitHub リポジトリを参照してください。](https://github.com/Microsoft/SandDance)
