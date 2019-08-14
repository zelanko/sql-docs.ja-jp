---
title: SandDance for Azure Data Studio
titleSuffix: Azure Data Studio
description: Azure Data Studio での SandDance の使用方法
ms.custom: seodec18
ms.date: 07/03/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: a96bde6a66642bf02cc076c3d4d4f3ac44e02a3f
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959332"
---
# <a name="sanddance-for-azure-data-studio-preview"></a>SandDance for Azure Data Studio (プレビュー)
Azure Data Studio では、作業中の .csv ファイルと .tsv ファイルに対してクイックの視覚化を作成する方法を提供するようになりました。 これには、ご利用の SQL Server 2019 ビッグ データ クラスター内の HDFS 上にあるローカル ファイルやファイルが含まれます。 この拡張機能は、データを簡単に確認し、何が起こっているかを把握しようとするときに役立ちます。 マイクロソフト リサーチの SandDance と呼ばれるテクノロジを使用します。これにより、データのインプレース視覚化を作成することができます。

![sanddance-animation](https://user-images.githubusercontent.com/11507384/54236654-52d42800-44d1-11e9-859e-6c5d297a46d2.gif)

わかりやすいビューを使用することにより、SandDance ではデータに関する分析情報を見つけることができます。これは、データによってサポートされているストーリーの説明、証拠に基づいたケースの構築、仮説のテスト、画面の説明の詳細な調査、購入のサポートに関する意思決定の支援、またはデータのより広い現実的なコンテキストへの関連付けに役立ちます。

SandDance では、ユニットの視覚化を使用します。これにより、データベース内の行との間で一対一のマッピングが適用され、画面上にマークされます。
ビュー間の滑らかなアニメーションの切り替えは、データとやりとりするときにコンテキストを維持するのに役立ちます。

## <a name="usage"></a>使用方法

[ファイル] メニューから [フォルダーを開く] を使用するか、[Ctrl+K Ctrl+O] キーを押して、.CSV ファイルを含むディレクトリを開きます。  次に、Explorer パネル内で、.csv ファイルまたは .tsv ファイルを右クリックし、 *[View in SandDance]\(SandDance で表示\)* を選択します。

SQL Server 2019 ビッグ データ クラスターに接続している場合は、HDFS 内の .csv ファイルまたは .tsv ファイルを右クリックし、 *[View in SandDance]\(SandDance で表示\)* を選択します。

## <a name="known-issues"></a>既知の問題

現在、データでは一意識別子として最初の列が含まれているはずです。

現在、視覚化されている行数を制限することはありません。 しかし、メモリの消費量は行の数に比例して増加するので、データ セットまたはビューは約 10 万行に制限することをお勧めします。

「[既知の問題](https://microsoft.github.io/SandDance/#known-issues)」を参照してください。

## <a name="release-notes"></a>リリース ノート

### <a name="100"></a>1.0.0

azdata-sanddance の最初のリリース

## <a name="next-steps"></a>Next Steps
詳細については、[GitHub リポジトリにアクセスしてください。](https://github.com/Microsoft/SandDance)
