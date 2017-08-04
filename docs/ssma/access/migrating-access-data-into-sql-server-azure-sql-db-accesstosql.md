---
title: "SQL Server - Azure SQL DB (AccessToSQL) に移行するデータにアクセス |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
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
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f6d51cc33d972fc49352ccbf382f6b0193195d9e
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="migrating-access-data-into-sql-server---azure-sql-db-accesstosql"></a>SQL Server - Azure SQL DB (AccessToSQL) に移行するデータにアクセス
データベース オブジェクトを正常に作成した後[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]へのアクセスからデータを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。  
  
## <a name="setting-migration-options"></a>移行オプションの設定  
データを移行する前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure、プロジェクトの移行オプションの確認、**プロジェクト設定** ダイアログ ボックス。 このダイアログ ボックスで、移行のバッチ サイズ、テーブルのロック、制約チェック、挿入トリガーを起動、識別と null 値の処理、および out の日付を処理する方法を設定することができます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]範囲です。 詳細については、次を参照してください。[プロジェクトの設定 (移行)](http://msdn.microsoft.com/en-us/4caebc9c-8680-4b99-a8fa-89c43161c95d)です。  
  
## <a name="migrating-data"></a>データの移行  
移行データを一括読み込み操作へのデータの行を移動する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]またはトランザクションでの SQL Azure です。 読み込まれる行の数[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]またはプロジェクト設定で各トランザクションでの SQL Azure を構成します。  
  
移行のメッセージを表示するには、出力ウィンドウが表示されていることを確認します。 ない場合は、上、**ビュー**メニューの **出力**です。  
  
**データを移行するには**  
  
1.  アクセスのデータベース オブジェクトを読み込んだかどうかを確認[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。  
  
2.  アクセス メタデータ エクスプ ローラーで、移行するデータが含まれているオブジェクトを選択します。  
  
    -   データベース全体のデータを移行するには、データベース名の横にあるチェック ボックスを選択します。  
  
    -   個々 のテーブルからデータを移行するデータベースを展開し、**テーブル**、テーブルの横にあるチェック ボックスを選択します。 個々 のテーブルからデータを省略するには、チェック ボックスをオフにします。  
  
3.  右クリック**データベース**し、**データの移行**です。  
  
移行できます SSMA の外部のデータを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **bcp**コマンド ライン ユーティリティまたは[!INCLUDE[ssISnoversion](../../includes/ssisnoversion_md.md)]です。 これらのツールの詳細については、次を参照してください。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="next-step"></a>次の手順  
移行した後、使用を継続する Access データベースのアプリケーションがあれば、リンク、Access データベース テーブルに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure のテーブルです。 詳細については、次を参照してください。[アクセス アプリケーションを SQL Server にリンク](http://msdn.microsoft.com/en-us/82374ad2-7737-4164-a489-13261ba393d4)です。  
  
## <a name="see-also"></a>参照  
[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[設定の変換と移行オプション](http://msdn.microsoft.com/en-us/0a7304df-2f35-4453-96ef-7ac83dea1167)  
  

