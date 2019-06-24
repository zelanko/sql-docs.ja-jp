---
title: チュートリアル:SQL Server Management Studio (SSMS) | Microsoft Docs
ms.custom: sqlfreshmay19
ms.date: 05/14/2019
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: sstein
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.tutorialstart.ssms.f1
helpviewer_keywords:
- projects [SQL Server Management Studio], tutorials
- templates [SQL Server], SQL Server Management Studio
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- solutions [SQL Server Management Studio], tutorials
- SQL Server Management Studio [SQL Server], tutorials
- scripts [SQL Server], SQL Server Management Studio
ms.assetid: d2bade70-07cf-4d94-b5d2-88aecb538ed1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7756482734dac8d4d5982b0ab6d5d58942065697
ms.sourcegitcommit: a6949111461eda0cc9a71689f86b517de3c5d4c1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263534"
---
# <a name="tutorials-for-sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS) のチュートリアル
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

SQL Server Management Studio (SSMS) のチュートリアルでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインフラストラクチャを管理するための統合環境について説明します。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] には、Azure SQL Database、Azure SQL Database マネージド インスタンス、Azure SQL Data Warehouse、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを構成、監視、管理するためのグラフィカル インターフェイスが用意されています。 さらに、データベースなどの、アプリケーションで使用されるデータ層コンポーネントを配置、監視、およびアップグレードすることもできます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、スクリプトを編集およびデバッグするための [!INCLUDE[tsql](../../includes/tsql-md.md)]、MDX、DMX、XML の各言語エディターも提供します。  
  
## <a name="what-you-will-learn"></a>学習する内容  

これらのチュートリアルでは、SSMS での情報の操作方法とその機能の活用方法を学習します。
  
SSMS に慣れ親しむには、実践的な経験を積むのが最も効果的です。 これらのチュートリアルを行うと、SSMS 内で使用できるさまざまな機能に慣れることができます。  これらのチュートリアルでは、SSMS のコンポーネントを管理する方法と、頻繁に使用する機能へのアクセス方法について説明します。  

チュートリアルの内容は次のとおりです。


- [チュートリアル: SSMS を使用した SQL Server に対する接続およびクエリ](connect-query-sql-server.md)

    このチュートリアルでは、SQL Server インスタンスに接続する方法を学習します。 新しいデータベースを作成してクエリを実行するための基本的な Transact-SQL (T-SQL) コマンドについても学習します。 

- [チュートリアル: SSMS でオブジェクトのスクリプトを作成する](scripting-ssms.md)

    このチュートリアルでは、データベースやクエリなどのさまざまなオブジェクトのスクリプトを SSMS で作成する方法を学習します。 

- [チュートリアル: SSMS でテンプレートを使用する](../template/templates-ssms.md)
   
    このチュートリアルでは、SSMS で構築済みのテンプレートを使う方法を学習します。 テンプレートは、さまざまなデータベース管理タスクの Transact-SQL コード スニペットを多数格納している機能ですが、あまり知られていません。 

- [チュートリアル: SSMS を構成する](ssms-configuration.md)

    このチュートリアルでは、環境レイアウトの変更など、SSMS 環境の構成の基本を学習します。 このチュートリアルでは、さまざまな SSMS コンポーネントについても説明します。 
  

- [チュートリアル: SSMS を使用するための追加のヒントとテクニック](ssms-tricks.md)

    このチュートリアルでは、SSMS の使用に関するその他のヒントとテクニックを学習します。 チュートリアルは次のような内容です。
    - テキストのコメント化とコメント解除
    - テキストのインデント
    - オブジェクト エクスプローラーでのオブジェクトのフィルター
    - SQL Server エラー ログへのアクセス
    - インスタンスの名前の検索 
 
  
## <a name="requirements"></a>必要条件  
このチュートリアルは、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] には慣れていないが、データベースの概念と [!INCLUDE[tsql](../../includes/tsql-md.md)] を理解している、熟練のデータベース管理者およびデータベース開発者を対象としています。  
  
このチュートリアルを使用するには、以下のコンポーネントがインストールされている必要があります。  

  -   最新バージョンの [SQL Server Management Studio (SSMS)](../download-sql-server-management-studio-ssms.md) をインストールします。  

最初のセクションではデータベースを作成する手順を説明しますが、[AdventureWorks サンプル データベース](https://github.com/Microsoft/sql-server-samples/releases)に、データベースの他のサンプルもあります。 SSMS でデータベースを復元する手順については、[データベースの復元](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms)に関するページを参照してください。 


  
## <a name="see-also"></a>参照  
[データベース エンジンのチュートリアル](../../relational-databases/database-engine-tutorials.md)          
  
  
  

