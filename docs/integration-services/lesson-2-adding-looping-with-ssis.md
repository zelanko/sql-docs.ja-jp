---
title: "レッスン 2: SSIS によるループの追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 01f2ed61-1e5a-4ec6-b6a6-2bd070c64077
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8559dc3afb5f347555b9b21b61abc50765fd92c4
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="lesson-2-adding-looping-with-ssis"></a>レッスン 2: SSIS でのループの追加
「 [レッスン 1: SSIS によるプロジェクトと基本パッケージの作成](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md)」では、単一のフラット ファイル ソースからデータを抽出するパッケージを作成し、参照変換を使用してデータを変換しました。さらに、変換したデータを、 **AdventureWorksDW2012** サンプル データベースの **FactCurrency** ファクト テーブルに読み込みました。  
  
しかし、抽出、変換、読み込み (ETL) プロセスでフラット ファイルを 1 つだけ使用することはほとんどありません。 通常の ETL プロセスでは、複数のフラット ファイル ソースからデータを抽出します。 複数のソースからデータを抽出するには、反復型の制御フローが必要となります。 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では、反復やループをパッケージへ簡単に追加できるようになりました。  
  
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
> このチュートリアルには、 **AdventureWorksDW2012** サンプル データベースが必要です。 **AdventureWorksDW2012**をインストールしてデプロイする方法の詳細については、「 [Reporting Services Product Samples Project on CodePlex (CodePlex でのサービス製品サンプルのレポート)](http://go.microsoft.com/fwlink/p/?LinkID=526910)」をご覧ください。  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
このレッスンの内容は次のとおりです。  
  
-   [手順 1: レッスン 1 のパッケージのコピー](../integration-services/lesson-2-1-copying-the-lesson-1-package.md)  
  
-   [手順 2: Foreach ループ コンテナーの追加と構成](../integration-services/lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
-   [手順 3: フラット ファイル接続マネージャーの変更](../integration-services/lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
-   [手順 4: レッスン 2 のチュートリアル パッケージのテスト](../integration-services/lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>レッスンの開始  
[手順 1: レッスン 1 のパッケージのコピー](../integration-services/lesson-2-1-copying-the-lesson-1-package.md)  
  
## <a name="see-also"></a>参照  
[For ループ コンテナー](../integration-services/control-flow/for-loop-container.md)  
  
  
  

