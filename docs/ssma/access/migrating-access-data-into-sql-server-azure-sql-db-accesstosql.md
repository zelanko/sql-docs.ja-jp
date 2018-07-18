---
title: SQL Server - Azure SQL DB (AccessToSQL) に移行するデータにアクセス |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- bulk loading data
- data, loading into SQL Azure
- data, loading into SQL Server
- migrating databases, loading data
- migrating databases, options
- options, migrating data
- SQL Azure, migrating data into
- SQL Server, migrating data into
ms.assetid: f3b18af7-1af0-499d-a00d-a0af94895625
caps.latest.revision: 17
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 9cb790ec1b79827b7db578001633c75ef6e1b191
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38979474"
---
# <a name="migrating-access-data-into-sql-server---azure-sql-db-accesstosql"></a>SQL Server - Azure SQL DB (AccessToSQL) に移行するデータにアクセス
データベース オブジェクトを正常に作成した後[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]へのアクセスからデータを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。  
  
## <a name="setting-migration-options"></a>移行オプションの設定  
データを移行する前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure、プロジェクトの移行オプションの確認、**プロジェクト設定** ダイアログ ボックス。 このダイアログ ボックスでは、移行のバッチ サイズ、テーブルのロック、制約チェック、挿入トリガーを起動、id および処理するには、null 値と日付のうちを処理する方法を設定できます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]範囲。 詳細については、次を参照してください。[プロジェクトの設定 (移行)](http://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d)します。  
  
## <a name="migrating-data"></a>データの移行  
移行データは、一括読み込み操作へのデータの行を移動する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure でのトランザクション。 読み込まれる行の数[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure の各トランザクションではプロジェクトの設定で構成されます。  
  
移行のメッセージを表示するには、出力ウィンドウが表示されていることを確認します。 そうでない場合に、**ビュー**メニューの **出力**します。  
  
**データを移行するには**  
  
1.  Access データベース オブジェクトが読み込まれているかどうかを確認[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。  
  
2.  アクセス メタデータ エクスプ ローラーでは、移行するデータを含むオブジェクトを選択します。  
  
    -   データベース全体のデータを移行するには、データベース名の横にあるチェック ボックスを選択します。  
  
    -   個々 のテーブルからデータを移行するデータベースを展開し、**テーブル**、テーブルの横にあるチェック ボックスを選択します。 個々 のテーブルからデータを省略するには、チェック ボックスをオフにします。  
  
3.  右クリック**データベース**選び**Migrate Data**。  
  
移行することもできます SSMA 以外のデータを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **bcp**コマンド ライン ユーティリティまたは[!INCLUDE[ssISnoversion](../../includes/ssisnoversion_md.md)]します。 これらのツールの詳細については、次を参照してください。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブックの「します。  
  
## <a name="next-step"></a>次の手順  
リンクする Access データベースのテーブルの移行後に使用を続行するデータベース アプリケーションにアクセスした場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure テーブル。 詳細については、次を参照してください。 [SQL Server への Access アプリケーションのリンク](http://msdn.microsoft.com/82374ad2-7737-4164-a489-13261ba393d4)します。  
  
## <a name="see-also"></a>参照  
[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[設定の変換と移行のオプション](http://msdn.microsoft.com/0a7304df-2f35-4453-96ef-7ac83dea1167)  
  
