---
title: ADO の基礎 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: d6a66928-e68f-4c38-b87a-838c5de50a28
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 75f5030f8faa5aa5d8e8a0f6bcb6d72b186c8448
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67926065"
---
# <a name="ado-fundamentals"></a>ADO の基礎
ADO を使用すると、開発者は、OLE DB システムインターフェイスを使用して、さまざまなデータソースからプログラムを使用してデータにアクセスしたり、編集したり、更新したりすることができます。 ADO の最も一般的な使用方法は、リレーショナルデータベース内の1つまたは複数のテーブルに対してクエリを実行し、その結果を取得してアプリケーションで表示し、ユーザーがデータの変更を行って保存できるようにすることです。 その他のタスクは次のとおりです。  
  
-   SQL を使用してデータベースにクエリを実行し、結果を表示します。  
  
-   インターネット経由でファイルストア内の情報にアクセスします。  
  
-   電子メールシステム内のメッセージとフォルダーを操作する。  
  
-   データベースから XML ファイルにデータを保存する。  
  
-   XML で記述されたコマンドを実行し、XML ストリームを取得します。  
  
-   バイナリまたは XML ストリームへのデータの保存。  
  
-   ユーザーがデータベーステーブルのデータを確認および変更できるようにする。  
  
-   パラメーター化されたデータベースコマンドの作成と再利用。  
  
-   ストアドプロシージャを実行しています。  
  
-   **レコードセット**と呼ばれる柔軟な構造を動的に作成し、データを保持、移動、操作します。  
  
-   トランザクションデータベース操作を実行しています。  
  
-   実行時の条件に基づいて、データベース情報のローカルコピーのフィルター処理と並べ替えを行います。  
  
-   データベースから階層の結果を作成および操作します。  
  
-   データベースフィールドをデータ対応コンポーネントにバインドしています。  
  
-   リモートの切断された**レコードセット**を作成しています。  
  
 ADO は、このような柔軟性を提供するさまざまなオプションと設定を公開しています。 そのため、アプリケーションで ADO を使用する方法を学習し、それぞれの目標を管理しやすい部分に分割することが重要です。  
  
 ADO を使用するほとんどのアプリケーションには、データの取得、データの検査、データの編集、データの更新という4つの主要な操作が含まれます。 これらの操作については、このセクションの後半で詳しく説明します。  
  
 ただし、これらの詳細について説明する前に、ADO オブジェクトモデルと単純な ADO アプリケーションの概要を説明します。このアプリケーションは、Microsoft® Visual Basic®で記述され、次の4つの主要な ADO 操作のそれぞれを実行します。  
  
-   [ADO オブジェクトとコレクション](../../../ado/guide/data/ado-objects-and-collections.md)  
  
-   [HelloData: 単純な ADO アプリケーション](../../../ado/guide/data/hellodata-a-simple-ado-application.md)  
  
-   [OLE DB プロバイダー](../../../ado/guide/data/ole-db-providers-ado.md)  
  
-   [エラー](../../../ado/guide/data/errors-ado.md)
