---
title: 'チュートリアル: SQL Server Management Studio (SSMS) | Microsoft Docs'
ms.custom: ''
ms.date: 08/30/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-tutorial
ms.reviewer: sstein
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: ''
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Active
ms.openlocfilehash: 9a1cbac9e3eef44384313792d92f38ac90cce5e1
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2018
---
# <a name="tutorial-sql-server-management-studio"></a>チュートリアル: SQL Server Management Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

SQL Server Management Studio (SSMS) のチュートリアルでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインフラストラクチャを管理するための統合環境について説明します。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを構成、監視、および管理するためのグラフィカル インターフェイスを提供します。 さらに、データベースなどの、アプリケーションで使用されるデータ層コンポーネントを配置、監視、およびアップグレードすることもできます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、スクリプトを編集およびデバッグするための [!INCLUDE[tsql](../../includes/tsql-md.md)]、MDX、DMX、XML の各言語エディターも提供します。  
  
## <a name="what-you-will-learn"></a>学習する内容  

これらのチュートリアルでは、SSMS での情報の操作方法とその機能の活用方法を学習します。
  
SSMS に慣れ親しむには、実践的な経験を積むのが最も効果的です。 これらのチュートリアルを行うと、SSMS 内で使用できるさまざまな機能に慣れることができます。  これらのチュートリアルでは、SSMS のコンポーネントを管理する方法と、頻繁に使用する機能へのアクセス方法について説明します。  

チュートリアルの内容は次のとおりです。 

  
- [チュートリアル: SSMS を使用した SQL Server に対する接続およびクエリ](connect-query-sql-server.md)

    このセクションでは、SQL Server インスタンスに接続する方法を学習します。 新しいデータベースを作成してクエリを実行するための基本的な Transact-SQL (T-SQL) コマンドについても学習します。 

- [チュートリアル: SSMS でオブジェクトのスクリプトを作成する](scripting-ssms.md)

    このセクションでは、データベースやクエリなどのさまざまなオブジェクトのスクリプトを SSMS で作成する方法を学習します。 

- [チュートリアル: SSMS でテンプレートを使用する](templates-ssms.md)
   
    このセクションでは、SSMS で構築済みのテンプレートを使う方法を学習します。 

- [チュートリアル: SSMS を構成する](ssms-configuration.md)

    このセクションでは、SSMS 環境の構成の基礎について学習します。 
  

- [チュートリアル: SSMS を使用するためのヒントとテクニック](ssms-tricks.md)

    このセクションでは、SSMS の使用に関するその他のヒントとテクニックを学習します。 このチュートリアルは次のような内容です。
    - テキストのコメント化とコメント解除
    - テキストのインデント
    - オブジェクト エクスプローラーでのオブジェクトのフィルター
    - SQL Server エラー ログへのアクセス
    - インスタンスの名前の検索 
 
  
## <a name="requirements"></a>必要条件  
このチュートリアルは、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] には慣れていないが、データベースの概念と [!INCLUDE[tsql](../../includes/tsql-md.md)] を理解している、熟練のデータベース管理者およびデータベース開発者を対象としています。  
  
このチュートリアルを使用するには、以下のコンポーネントがインストールされている必要があります。  

  -   最新バージョンの [SQL Server Management Studio (SSMS)](../download-sql-server-management-studio-ssms.md) をインストールします。  

最初のセクションではデータベースを作成する手順を説明しますが、[AdventureWorks サンプル データベース](https://github.com/Microsoft/sql-server-samples/releases)では他のサンプル データベースが見つかります。 SSMS でデータベースを復元する手順については、[データベースの復元](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms)に関するページを参照してください。 


  
## <a name="see-also"></a>参照  
[データベース エンジンのチュートリアル](../../relational-databases/database-engine-tutorials.md)  
  
  
  

