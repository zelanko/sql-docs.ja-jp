---
title: "SSMA プロジェクト (MySQLToSQL) の使用 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Working with SSMA projects, create new project
- Working with SSMA projects, customize settings
- Working with SSMA projects, Open project
- Working with SSMA projects, Save project
ms.assetid: 9e4394e9-f177-41d9-839e-5d53a9c9b840
caps.latest.revision: "20"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 94cb62f1a2c1088ce8666f3e58722016330badd9
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="working-with-ssma-projects-mysqltosql"></a>SSMA プロジェクト (MySQLToSQL) での作業
MySQL データベースを SQL Server または SQL Azure を移行するには、まず SSMA プロジェクトを作成する必要があります。 プロジェクトは、次の情報を含むファイルです。  
  
-   SQL Server または SQL Azure に移行する場合の MySQL データベースに関するメタデータ。  
  
-   SQL Server または SQL Azure 移行済みのオブジェクトとデータを受け取るのターゲット インスタンスに関するメタデータ。  
  
-   SQL Server または SQL Azure 接続情報です。  
  
-   プロジェクトの設定。  
  
プロジェクトを開くときに、MySQL および SQL Server または SQL Azure から切断されています。 オフラインで作業することができます。 SQL Server への再接続の詳細については、次を参照してください[SQL Server &#40; に接続する。MySQLToSQL &#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
## <a name="reviewing-default-project-settings"></a>既定のプロジェクト設定を確認します。  
SSMA は、変換してデータベースの読み込み、データの移行および同期 SSMA MySQL および SQL Server または SQL Azure でのいくつかの設定を格納します。 既定の設定は、多くのユーザーに適しています。 ただし、新しい SSMA プロジェクトを作成する前に、設定を確認する必要があります。 必要な場合は、すべての新しいプロジェクトに使用される既定の設定を変更できます。  
  
##### <a name="to-review-default-project-settings"></a>既定のプロジェクト設定を確認するには  
  
1.  選択**プロジェクト設定の既定の**から、**ツール**メニュー。  
  
2.  プロジェクトの種類を選択して**移行のターゲット バージョン**のどの設定を表示/変更をクリックしてドロップダウン**全般** タブ。  
  
3.  左側のウィンドウでをクリックして**変換**です。  
  
4.  右側のウィンドウで確認し、必要に応じて設定を変更します。 これらの設定の詳細については、次を参照してください。[プロジェクトの設定 &#40;です。変換&#41;&#40;です。MySQLToSQL &#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md) .  
  
5.  移行、同期、SQL Azure、GUI、および種類のマッピングのページの手順 1. ~ 3. を繰り返します。  
  
-   移行設定については、次を参照してください。[プロジェクトの設定 &#40;です。移行&#41;&#40;です。MySQLToSQL &#41;](../../ssma/mysql/project-settings-migration-mysqltosql.md).  
  
-   SQL Server への同期の設定については、次を参照してください。[プロジェクトの設定 &#40;です。同期 &#41;&#40;です。MySQLToSQL &#41;](../../ssma/mysql/project-settings-synchronization-mysqltosql.md).  
  
-   GUI の設定については、次を参照してください。[プロジェクトの設定 (GUI) (SSMA 共通)](http://msdn.microsoft.com/en-us/cf06baf1-8714-48a3-95dc-781f6ca53693)です。  
  
-   データ型マッピングの設定については、次を参照してください。[プロジェクトの設定 &#40;です。型のマッピング &#41;&#40;です。MySQLToSQL &#41;](../../ssma/mysql/project-settings-type-mapping-mysqltosql.md).  
  
-   SQL Azure の設定については、次を参照してください。[プロジェクトの設定 &#40;です。Azure SQL DB &#41;&#40;です。MySQLToSQL &#41;](../../ssma/mysql/project-settings-azure-sql-db-mysqltosql.md).  
  
> [!NOTE]  
> SQL Azure の設定が選択した場合にのみ表示されます**SQL Azure への移行**してプロジェクトを作成します。  
  
## <a name="creating-new-projects"></a>新しいプロジェクトの作成  
SQL Server または SQL Azure の MySQL データベースからデータを移行するには、プロジェクトを作成する必要があります。  
  
##### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  選択**新しいプロジェクト**から、**ファイル**メニュー。 **[新しいプロジェクト]** ダイアログ ボックスが表示されます。 **[ファイル]** メニューの **[新しいプロジェクト]** を選択します。 **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  **名前**ボックスで、プロジェクトの名前を入力します。  
  
3.  **場所**ボックス入力するか、プロジェクトのフォルダーを選択します。  
  
4.  **移行に**ドロップダウンで、対象のバージョンを選択して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]移行に使用します。 使用可能なオプションは次のとおりです。  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014  
  
    -   Azure SQL DB  
  
クリックして**OK**  
  
SSMA では、プロジェクト ファイルを作成します。  
  
## <a name="customizing-project-settings"></a>プロジェクト設定のカスタマイズ  
既定値を定義するだけでなく、すべての新しい SSMA プロジェクトに適用されるプロジェクトの設定は各プロジェクトの設定もカスタマイズできます。 詳細については、次を参照してください。[プロジェクト オプションの設定 &#40;です。MySQLToSQL &#41;](../../ssma/mysql/setting-project-options-mysqltosql.md).  
  
ソースとターゲットのデータベース間のデータ型マッピングをカスタマイズする場合は、プロジェクト、データベース、またはオブジェクト レベルでは、マッピングを定義できます。 詳細については、次を参照してください。[マッピング MySQL および SQL Server データ型 &#40;です。MySQLToSQL &#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md).  
  
## <a name="saving-projects"></a>プロジェクトの保存  
プロジェクトの保存機能は、本質的には、プロジェクトの設定と、必要に応じて、データベースのメタデータを SSMA プロジェクト ファイルに保存するユーザーを使用します。  
  
##### <a name="to-save-a-project"></a>プロジェクトを保存するには  
  
-   **ファイル**メニューの **保存**プロジェクト。  
  
プロジェクト内のデータベースが変更されたか、変換されていない場合、SSMA は読み込みおよびメタデータを保存することを求められます。 読み込みとメタデータの保存をオフラインで作業できます。 テクニカル サポート担当者など、他のユーザーに完全なプロジェクト ファイルを送信することもできます。 メタデータを保存するメッセージが表示されたら、次の操作を行います。  
  
1.  各データベースの状態を示す**メタデータがありません**データベース名の横にあるチェック ボックスをオンにします。 メタデータの保存には数分かかる場合があります。 この時点でメタデータを保存したくない場合は、チェック ボックスをオンされません。  
  
2.  **[保存]**をクリックします。  
  
SSMA は、MySQL スキーマが解析され、プロジェクト ファイルにメタデータを保存します。  
  
## <a name="opening-projects"></a>プロジェクトを開く  
プロジェクトを開くときに、MySQL および SQL Server または SQL Azure から切断されているがします。 オフラインで作業できます。 メタデータを更新するには、SQL Server または SQL Azure にデータベース オブジェクトを読み込みます。 データを移行するには、SQL Server または SQL Azure に再接続する必要があります。  
  
##### <a name="to-open-a-project"></a>プロジェクトを開くには  
  
1.  次の手順のいずれかを使用します。  
  
    1.  **ファイル** メニューのをポイント**最近使ったプロジェクト**です。  
  
    2.  開きたいプロジェクトを選択します。  
  
    3.  **ファイル**メニューの **プロジェクトを開く**.m2ssproj プロジェクト ファイルを探し、ファイルを選択し、をクリックして**開く**です。  
  
2.  MySQL への再接続、**ファイル**メニューの  **MySQL への再接続**です。  
  
3.  SQL Server に再接続する、**ファイル**メニューの  **SQL Server に再接続**です。  
  
4.  SQL Azure への再接続、**ファイル**メニューの  **SQL Azure に再接続します。**  
  
## <a name="next-step"></a>次の手順  
移行プロセスの次の手順は[MySQL &#40; に接続します。MySQLToSQL &#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
## <a name="see-also"></a>参照  
[MySQL &#40; に接続します。MySQLToSQL &#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
[SQL Server - Azure SQL DB &#40; への MySQL データベースの移行MySQLToSql &#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
[SQL Server &#40; に接続します。MySQLToSQL &#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
[Azure SQL DB &#40; に接続します。MySQLToSQL &#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
  
