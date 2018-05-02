---
title: SSIS ETL パッケージを作成する方法 | Microsoft Docs
ms.custom: ''
ms.date: 04/17/2018
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: ''
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- SSIS, tutorials
- packages [Integration Services], tutorials
- Integration Services, tutorials
- SQL Server Integration Services, tutorials
- logs [Integration Services], tutorials
- walkthroughs [Integration Services]
ms.assetid: d6d5bb1f-4cb1-4605-9cd6-f60b858382c4
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 83e51e583e0c83d8d0cbc8dbd213a78baa766ffb
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="ssis-how-to-create-an-etl-package"></a>SSIS ETL パッケージを作成する方法

 > 以前のバージョンの SQL Server に関連するコンテンツについては、「[SSIS チュートリアル: 簡単な ETL パッケージの作成](https://msdn.microsoft.com/library/ms169917(SQL.120).aspx)」を参照してください。

このチュートリアルでは、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーを使用して、簡単な [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを作成する方法を学習します。 作成するパッケージは、フラット ファイルからデータを取得し、そのデータを変換した後で、ファクト テーブルに挿入します。 以降のレッスンでは、このパッケージを拡張して、ループ、パッケージ構成、ログ記録、およびエラー フローについて学習します。  
  
チュートリアルで使用するサンプル データをインストールすると、チュートリアルの各レッスンで作成するパッケージの完了した状態のバージョンもインストールされます。 完了した状態のパッケージを使用すれば、手順をとばし、後のレッスンからチュートリアルを開始することができます。 このチュートリアルでパッケージまたは新しい開発環境を初めて使用する場合は、レッスン 1 から開始することをお勧めします。  

> [!IMPORTANT]
> 最近、このチュートリアルの実行に必要なサンプル ファイルが以前のオンラインの場所で使用できなくなりました。 ご不便をおかけして申し訳ございません。 ファイルを新しい場所に用意し、この記事のリンクを更新しました。

## <a name="what-is-sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS) とは

[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS) は、データ ウェアハウスの ETL (抽出、変換、読み込み) パッケージなど、パフォーマンスの高いデータ統合ソリューションを構築するためのプラットフォームです。 SSIS には、パッケージを作成およびデバッグするためのグラフィカルなツールやウィザード、FTP 操作などのワークフロー機能の実行、SQL ステートメントの実行、および電子メール メッセージの送信を実行するためのタスク、データの抽出や読み込みに使用するデータの変換元と変換先、データのクリーニング、集計、マージ、コピーを行う変換、パッケージの実行と保存を管理するための [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービス、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] オブジェクト モデルをプログラミングするための API (アプリケーション プログラミング インターフェイス) が用意されています。  

## <a name="what-you-learn"></a>学習する内容  
[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] の新しいツール、コントロール、機能などに慣れる最良の方法は、実際に使ってみることです。 このチュートリアルでは、[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーを使用して、ループ、構成、エラー フロー ロジック、およびログの記録を含む簡単な ETL パッケージを作成します。  
  
## <a name="requirements"></a>必要条件  
このチュートリアルは、データベースの基本的な操作を理解している一方で、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]の新機能にはほとんど触れたことがないユーザーを対象にしています。  
  
このチュートリアルを使用するには、システムに次のコンポーネントがインストールされている必要があります。  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] および **AdventureWorksDW2012** データベース。 **AdventureWorksDW2012** データベースをダウンロードするには、[AdventureWorks サンプル データベース](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)から `AdventureWorksDW2012.bak` をダウンロードし、バックアップを復元します。  

-   サンプル データ。 このサンプル データは、 [!INCLUDE[ssIS](../includes/ssis-md.md)] のレッスン パッケージに含まれています。 サンプル データとレッスン パッケージを Zip ファイルとしてダウンロードするには、[ここをクリックしてください](http://download.microsoft.com/download/3/1/4/314A4169-D540-4E9E-9776-585BFBFC2CC5/Creating a Simple ETL Package.zip)。  

## <a name="lessons-in-this-tutorial"></a>このチュートリアルで行うレッスン  
[レッスン 1: SSIS によるプロジェクトと基本パッケージの作成](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md)  
このレッスンでは、簡単な ETL パッケージを作成します。パッケージの内容は、1 つのフラット ファイルからデータを抽出し、参照変換を使用してデータを変換し、最後に結果をファクト テーブルの変換先に読み込ませるというものです。  
  
[レッスン 2: SSIS でのループの追加](../integration-services/lesson-2-adding-looping-with-ssis.md)  
このレッスンでは、レッスン 1 で作成したパッケージを拡張し、新しいループ機能を活用して、複数のフラット ファイルを単一のデータ フロー プロセスに抽出します。  
  
[レッスン 3: SSIS でのログ記録の追加](../integration-services/lesson-3-add-logging-with-ssis.md)  
このレッスンでは、レッスン 2 で作成したパッケージを拡張し、新しいログ機能を活用します。  
  
[レッスン 4: SSIS でエラー フロー リダイレクションを追加する](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md)  
このレッスンでは、レッスン 3 で作成したパッケージを拡張し、新しいエラー出力構成を活用します。  
  
[レッスン 5: パッケージ配置モデルの SSIS パッケージ構成を追加する](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
このレッスンでは、レッスン 4 で作成したパッケージを拡張し、新しいパッケージ構成オプションを活用します。  
  
[レッスン 6: SSIS でプロジェクト配置モデルを持つパラメーターを使用する](../integration-services/lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
このレッスンでは、レッスン 5 で作成したパッケージを拡張し、プロジェクト配置モデルで新しいパラメーターを使用します。  
  
  
  
