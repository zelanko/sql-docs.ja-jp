---
title: SQL Server へのアクセスデータの移行-Azure SQL DB (アクセス許可 Sql) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
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
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 8f0e93efee0c57c904c32ec52fbb560f973f21b8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67907145"
---
# <a name="migrating-access-data-into-sql-server---azure-sql-db-accesstosql"></a>SQL Server へのアクセスデータの移行-Azure SQL DB (アクセス許可 Sql)
データベースオブジェクトをに正常に作成した[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]後は、アクセスからまたは SQL Azure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にデータを移行できます。  
  
## <a name="setting-migration-options"></a>移行オプションの設定  
データをまたは SQL Azure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に移行する前に、[**プロジェクトの設定**] ダイアログボックスの [プロジェクトの移行] オプションを確認してください。 このダイアログボックスでは、移行バッチサイズ、テーブルロック、制約チェック、挿入トリガーの起動、id と null 値の処理、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]範囲外の日付の処理方法を設定できます。 詳細については、「[プロジェクトの設定 (移行)](https://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d)」を参照してください。  
  
## <a name="migrating-data"></a>データの移行  
データの移行は、データの行を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]トランザクションに移動または SQL Azure する一括読み込み操作です。 各トランザクションで読み込まれる行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure される行の数は、プロジェクトの設定で構成されます。  
  
移行メッセージを表示するには、[出力] ウィンドウが表示されていることを確認します。 表示されていない場合は、[**表示**] メニューの [**出力**] を選択します。  
  
**データを移行するには**  
  
1.  Access データベースオブジェクトをまたは SQL Azure に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]読み込んでいることを確認します。  
  
2.  Access Metadata Explorer で、移行するデータを含むオブジェクトを選択します。  
  
    -   データベース全体のデータを移行するには、データベース名の横にあるチェックボックスをオンにします。  
  
    -   個々のテーブルからデータを移行するには、データベースを展開し、[**テーブル**] を展開して、テーブルの横にあるチェックボックスをオンにします。 個々のテーブルからデータを除外するには、このチェックボックスをオフにします。  
  
3.  [**データベース**] を右クリックし、[**データの移行**] を選択します。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Bcp**コマンドラインユーティリティまたは[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]を使用して、ssma の外部でデータを移行することもできます。 これらのツールの詳細について[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、オンラインブックを参照してください。  
  
## <a name="next-step"></a>次のステップ  
移行後も引き続き使用するアクセスデータベースアプリケーションがある場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、access データベーステーブルをまたは SQL Azure テーブルにリンクします。 詳細については、「 [SQL Server への Access アプリケーションのリンク](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[Access データベースの SQL Server への移行](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[変換と移行のオプションの設定](setting-conversion-and-migration-options-accesstosql.md)  
  
