---
title: 'レッスン 2: ループの追加 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 01f2ed61-1e5a-4ec6-b6a6-2bd070c64077
author: janinezhang
ms.author: janinez
ms.openlocfilehash: ed2089257af4f82b0bbb863731a17d396dc8795c
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968262"
---
# <a name="lesson-2-adding-looping"></a>レッスン 2: ループの追加
  「[レッスン 1: プロジェクトと基本パッケージの作成](lesson-1-create-a-project-and-basic-package-with-ssis.md)」では、単一のフラットファイルソースからデータを抽出し、参照変換を使用してデータを変換した後、最後にデータを**AdventureWorksDW2012**サンプルデータベースの**FactCurrency**ファクトテーブルに読み込むパッケージを作成しました。  
  
 しかし、抽出、変換、読み込み (ETL) プロセスでフラット ファイルを 1 つだけ使用することはほとんどありません。 通常の ETL プロセスでは、複数のフラット ファイル ソースからデータを抽出します。 複数のソースからデータを抽出するには、反復型の制御フローが必要となります。 の最も期待される機能の1つ [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] は、繰り返しまたはループをパッケージに簡単に追加できることです。  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] には、パッケージ全体をループさせる 2 種類のコンテナーがあります。1 つは Foreach ループ コンテナー、もう 1 つは For ループ コンテナーです。 Foreach ループ コンテナーが列挙子を使用してループを実行するのに対し、For ループ コンテナーは、通常、変数式を使用します。 このレッスンでは Foreach ループ コンテナーを使用します。  
  
 パッケージで Foreach ループ コンテナーを使用すれば、指定した列挙子の各メンバーについて、制御フローを繰り返すことができます。 Foreach ループ コンテナーでは、次のものを列挙できます。  
  
-   ADO レコードセット行  
  
-   ADO .Net スキーマ情報  
  
-   ファイル構造とディレクトリ構造  
  
-   システム変数、パッケージ変数、ユーザー変数  
  
-   変数に含まれる列挙可能なオブジェクト  
  
-   コレクション内のアイテム  
  
-   XML パス言語 (XPath) 式内のノード  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理オブジェクト (SMO)  
  
 このレッスンでは、レッスン 1 で作成した単純な ETL パッケージを修正し、Foreach ループ コンテナーの機能を活用します。 また、ユーザー定義のパッケージ変数を設定し、フォルダー内のすべてのフラット ファイルに対し、チュートリアル パッケージが反復処理を実行できるようにします。 前のレッスンを完了していない場合は、チュートリアルに含まれている、レッスン 1 を完了した状態のパッケージをコピーすることもできます。  
  
 このレッスンでは、データ フローは変更せずに、制御フローのみを変更します。  
  
> [!IMPORTANT]  
>  このチュートリアルには、 **AdventureWorksDW2012** サンプル データベースが必要です。 **AdventureWorksDW2012**をインストールして配置する方法の詳細については、 [CodePlex での Reporting Services 製品サンプル](https://go.microsoft.com/fwlink/p/?LinkID=526910)を参照してください。  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
 このレッスンの内容は次のとおりです。  
  
-   [手順 1:レッスン 1 のパッケージのコピー](lesson-2-1-copying-the-lesson-1-package.md)  
  
-   [手順 2:Foreach ループ コンテナーの追加と構成](lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
-   [手順 3:フラット ファイル接続マネージャーの変更](lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
-   [手順 4:レッスン 2 のチュートリアル パッケージのテスト](lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>レッスンの開始  
 [手順 1:レッスン 1 のパッケージのコピー](lesson-2-1-copying-the-lesson-1-package.md)  
  
## <a name="see-also"></a>参照  
 [For ループ コンテナー](control-flow/for-loop-container.md)  
  
  
