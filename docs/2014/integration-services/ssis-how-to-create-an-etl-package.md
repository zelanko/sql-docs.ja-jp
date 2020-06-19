---
title: 'SSIS チュートリアル: 簡単な ETL パッケージの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS, tutorials
- packages [Integration Services], tutorials
- Integration Services, tutorials
- SQL Server Integration Services, tutorials
- logs [Integration Services], tutorials
- walkthroughs [Integration Services]
ms.assetid: d6d5bb1f-4cb1-4605-9cd6-f60b858382c4
author: janinezhang
ms.author: janinez
ms.openlocfilehash: b67e2308c95db109c89bd2c3ff61f311e83fb898
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84962617"
---
# <a name="ssis-tutorial-creating-a-simple-etl-package"></a>SSIS チュートリアル:簡単な ETL パッケージの作成
  [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS) は、データウェアハウスの抽出、変換、読み込み (ETL) パッケージを含む、高パフォーマンスのデータ統合ソリューションを構築するためのプラットフォームです。 SSIS には、パッケージを作成およびデバッグするためのグラフィカルなツールやウィザード、FTP 操作などのワークフロー機能の実行、SQL ステートメントの実行、および電子メール メッセージの送信を実行するためのタスク、データの抽出や読み込みに使用するデータの変換元と変換先、データのクリーニング、集計、マージ、コピーを行う変換、パッケージの実行と保存を管理するための [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービス、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] オブジェクト モデルをプログラミングするための API (アプリケーション プログラミング インターフェイス) が用意されています。  
  
 このチュートリアルでは、デザイナーを使用して [!INCLUDE[ssIS](../includes/ssis-md.md)] 簡単なパッケージを作成する方法について説明し [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ます。 作成するパッケージは、フラット ファイルからデータを取得し、そのデータを変換した後で、ファクト テーブルに挿入します。 以降のレッスンでは、このパッケージを拡張して、ループ、パッケージ構成、ログ記録、およびエラー フローについて学習します。  
  
 チュートリアルで使用するサンプル データをインストールすると、チュートリアルの各レッスンで作成するパッケージの完了した状態のバージョンもインストールされます。 完了した状態のパッケージを使用すれば、手順をとばし、後のレッスンからチュートリアルを開始することができます。 パッケージまたは新しい開発環境を初めて使用する場合は、レッスン 1 から開始することをお勧めします。  
  
## <a name="what-you-will-learn"></a>学習する内容  
 で使用できる新しいツール、コントロール、および機能について理解を深めるには、それらを使用することをお勧めし [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ます。 このチュートリアルでは、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーを使用して、ループ、構成、エラー フロー ロジック、およびログの記録を含む簡単な ETL パッケージを作成します。  
  
## <a name="requirements"></a>要件  
 このチュートリアルは、データベースの基本的な操作に慣れているユーザーを対象としていますが、で利用できる新機能にはあまり影響を与えません [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 。  
  
 このチュートリアルを使用するには、システムに次のコンポーネントがインストールされている必要があります。  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] および **AdventureWorksDW2012** データベース。 セキュリティ強化のため、既定ではサンプル データベースがインストールされません。 **AdventureWorksDW2012** データベースをダウンロードするには、「 [SQL Server 2012 用 Adventure Works](https://go.microsoft.com/fwlink/?LinkId=275026)」を参照してください。  
  
    > [!IMPORTANT]  
    >  データベース (\*.mdf ファイル) をアタッチすると、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] では、既定で .ldf ファイルが検索されます。 **[データベースのインポート]** ダイアログ ボックスで [OK] をクリックする前に、.ldf ファイルを手動で削除する必要があります。  
    >   
    >  データベースのインポートの詳細については、「 [データベースのインポート](../relational-databases/databases/attach-a-database.md)」を参照してください。  
  
-   サンプル データ。 このサンプル データは、 [!INCLUDE[ssIS](../includes/ssis-md.md)] のレッスン パッケージに含まれています。 サンプル データとレッスン パッケージをダウンロードするには、次の手順を実行します。  
  
    1.  「 [Integration Services 製品サンプル](https://go.microsoft.com/fwlink/?LinkId=275027)」に移動します。  
  
    2.  [**ダウンロード**] タブをクリックします。  
  
    3.  SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip ファイルをクリックします。  
  
## <a name="lessons-in-this-tutorial"></a>このチュートリアルで行うレッスン  
 [レッスン 1:プロジェクトと基本パッケージの作成](lesson-1-create-a-project-and-basic-package-with-ssis.md)  
 このレッスンでは、簡単な ETL パッケージを作成します。パッケージの内容は、1 つのフラット ファイルからデータを抽出し、参照変換を使用してデータを変換し、最後に結果をファクト テーブルのディメンションに読み込ませるというものです。  
  
 [レッスン 2: ループの追加](lesson-2-adding-looping-with-ssis.md)  
 このレッスンでは、レッスン 1 で作成したパッケージを拡張し、新しいループ機能を活用して、複数のフラット ファイルを単一のデータ フロー プロセスに抽出するパッケージを作成します。  
  
 [レッスン 3:ログ機能の追加](lesson-3-add-logging-with-ssis.md)  
 このレッスンでは、レッスン 2 で作成したパッケージを拡張し、新しいログ機能を活用するパッケージを作成します。  
  
 [レッスン 4:エラー フロー リダイレクトの追加](lesson-4-add-error-flow-redirection-with-ssis.md)  
 このレッスンでは、レッスン 3 で作成したパッケージを拡張し、新しいエラー出力構成を活用するパッケージを作成します。  
  
 [レッスン 5: パッケージ配置モデルのパッケージ構成の追加](lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
 このレッスンでは、レッスン 4 で作成したパッケージを拡張し、新しいパッケージ構成オプションを活用するパッケージを作成します。  
  
 [レッスン 6: プロジェクト配置モデルを持つパラメーターを使用する](lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
 このレッスンでは、レッスン 5 で作成したパッケージを拡張し、プロジェクト配置モデルで新しいパラメーターを使用します。  
  
  
