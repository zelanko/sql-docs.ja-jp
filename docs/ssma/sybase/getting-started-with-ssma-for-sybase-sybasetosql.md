---
title: SAP ASE (SybaseToSQL) for SSMA の概要 |Microsoft ドキュメント
ms.custom: ''
ms.date: 09/30/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: c4098516-f0fc-4690-97bb-3766dfd43156
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2b502bd5cfe2c1a7df2129294b279a2b7b3a407a
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="getting-started-with-ssma-for-sap-ase-sybasetosql"></a>SAP ASE (SybaseToSQL) for SSMA の概要
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) の SAP ASE できます迅速に変換する SAP Adaptive Server Enterprise (ASE) データベースのスキーマ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースのスキーマへの結果として得られるスキーマのアップロード[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースからデータを移行し、SAP ASE[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースです。  
  
このトピックでは、インストール プロセスを導入し、し SSMA ユーザー インターフェイスを理解するために役立ちます。  
  
## <a name="installing-and-licensing-ssma"></a>インストールとライセンス SSMA  
SSMA を使用する必要がありますに初めてインストールする SSMA クライアント プログラム SAP ASE のソース インスタンスとのターゲット インスタンスの両方にアクセスできるコンピューター[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースです。 サーバー側のデータ移行を使用する必要がありますにインストールする拡張機能パックは、および少なくとも 1 つの SAP ASE プロバイダー (OLE DB、または ADO.NET) を実行しているコンピューター[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 これらのコンポーネントは、データの移行と SAP ASE システム関数のエミュレーションをサポートします。 インストール手順については、次を参照してください。[インストール SSMA SAP ASE for &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)です。  
  
SSMA を起動するには、クリックして**開始**、 をポイント**すべてのプログラム**、 をポイント **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant for Sybase**、し、  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant for Sybase**です。 初めて、SSMA を起動するライセンスのダイアログ ボックスが表示されます。 SSMA は、SSMA を使用する前に、Windows Live ID を使用してライセンスする必要があります。 ライセンスの手順で、インストールの手順に記載されて、 [Sybase クライアントのインストールの SSMA &#40;SybaseToSQL&#41; ](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)トピックです。  
  
## <a name="ssma-for-sap-ase-user-interface"></a>SSMA for SAP ASE ユーザー インターフェイス  
SSMA がインストールされ、ライセンス後に、SAP ASE データベースを移行 SSMA を使用することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースです。 開始する前に、SSMA ユーザー インターフェイスを理解するのに役立ちます。 次の図は、SSMA を含むメタデータ エクスプ ローラー、メタデータ、ツールバー、出力ウィンドウ、およびエラー一覧 ウィンドウのユーザー インターフェイスを示しています。  
  
![SSMA for SAP ASE ユーザー インターフェイス](../../ssma/sybase/media/ssmaforsybaseuserinterface.jpg "SSMA for SAP ASE ユーザー インターフェイス")  
  
移行を開始するには、まず新しいプロジェクトを作成する必要があります。 次に、SAP ASE に接続します。 接続に成功した後は、SAP ASE データベースの階層は、Sybase メタデータ エクスプ ローラーに表示されます。 ことでタスクを実行するよう Sybase メタデータ エクスプ ローラーで右クリックしてオブジェクトへの変換を評価するレポートの作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースです。 ツールバーとメニューを通じてこれらのタスクを実行することもできます。  
  
また接続のインスタンスにする必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースです。 階層、接続が成功した[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースが表示される[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure メタデータ エクスプ ローラー。 SAP ASE スキーマに変換した後[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースのスキーマに変換されたスキーマを選択する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure メタデータ エクスプ ローラーへのスキーマを読み込むと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースです。  
  
変換後のスキーマの読み込み後[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベース、Sybase メタデータ エクスプ ローラーに戻ってをしたへの SAP ASE データベースからデータを移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースです。  
  
これらのタスクとその実行方法の詳細については、次を参照してください。 [SQL Server - Azure SQL データベースへの SAP ASE データベースの移行&#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)です。  
  
次のセクションでは、SSMA ユーザー インターフェイスの機能を説明します。  
  
### <a name="metadata-explorers"></a>メタデータ エクスプ ローラー  
SSMA を参照して、SAP ASE に対する操作の実行の 2 つのメタデータ エクスプ ローラーを含むと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースです。  
  
#### <a name="sybase-metadata-explorer"></a>Sybase メタデータ エクスプ ローラー  
Sybase メタデータ エクスプ ローラーでは、SAP ASE のソース インスタンス上のデータベースに関する情報を示します。  
  
Sybase メタデータ エクスプ ローラーを使用すると、次のタスクを実行できます。  
  
-   各データベース内のテーブルを参照します。  
  
-   変換に、オブジェクトを選択し、オブジェクトに変換[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL Database の構文。 詳細については、次を参照してください。 [SAP ASE データベース オブジェクトの変換&#40;SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)です。  
  
-   データ移行のためのオブジェクトを選択し、それらのオブジェクトをからデータを移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースです。 詳細については、次を参照してください。 [SAP ASE データを SQL Server - Azure SQL Database に移行&#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-data-into-sql-server-azure-sql-db-sybasetosql.md)です。  
  
#### <a name="sql-server-or-sql-azure-metadata-explorer"></a>SQL Server または SQL Azure メタデータ エクスプ ローラー  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SQL Azure メタデータ エクスプ ローラーのインスタンスに関する情報が表示または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースです。 インスタンスに接続する場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベース、SSMA そのインスタンスに関するメタデータを取得し、プロジェクト ファイルに格納します。  
  
使用することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または変換後の SAP ASE データベース オブジェクトを選択し、読み込む SQL Azure メタデータ エクスプ ローラー (同期) のインスタンスにそれらのオブジェクト[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースです。  
  
詳細については、次を参照してください。 [SQL Server に変換されたデータベース オブジェクトの読み込み&#40;SybaseToSQL&#41;](../../ssma/sybase/loading-converted-database-objects-into-sql-server-sybasetosql.md)です。  
  
### <a name="metadata"></a>メタデータ  
各メタデータ エクスプ ローラーの右側には、選択したオブジェクトを記述するタブが。 たとえば、Sybase メタデータ エクスプ ローラーでテーブルを選択する場合は、6 つのタブが表示されます:**テーブル**、 **SQL**、**型マッピング**、**データ**、 。**プロパティ**、および**レポート**です。 **レポート** タブには、選択したオブジェクトを含むレポートを作成した後にのみ情報が含まれます。 内のテーブルを選択した場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure メタデータ エクスプ ローラー、3 つのタブが表示される:**テーブル**、 **SQL**、および**データ**です。  
  
ほとんどのメタデータの設定とは、読み取り専用です。 ただし、次のメタデータを変更することができます。  
  
-   Sybase メタデータ エクスプ ローラーでプロシージャを変更し、マッピングを入力できます。 スキーマを変換する前に、これらの変更を行います。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SQL Azure メタデータ エクスプ ローラーを変更したりできます、[!INCLUDE[tsql](../../includes/tsql_md.md)]ストアド プロシージャの場合。 スキーマを読み込む前に、これらの変更を行う[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
ソースまたはターゲット データベースではなく、プロジェクトのメタデータには、メタデータ エクスプ ローラーで行われた変更が反映されます。  
  
### <a name="toolbars"></a>[ツール バー]  
SSMA は 2 つのツールバー: プロジェクト ツールバー、および移行ツールバー。  
  
#### <a name="the-project-toolbar"></a>プロジェクトのツールバー  
プロジェクトのツールバーには、プロジェクトで作業し、SAP ASE に接続しに接続するためのボタンが含まれています。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースです。 これらのボタンで、コマンドのように、**ファイル**メニュー。  
  
#### <a name="the-migration-toolbar"></a>移行ツールバー  
移行のツールバーには、次のコマンドが含まれています。  
  
|ボタン|関数|  
|----------|------------|  
|**レポートを作成します。**|選択した SAP ASE オブジェクトに変換します[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]構文、し成功に変換されたを示すレポートを作成します。<br /><br />このコマンドは、Sybase メタデータ エクスプ ローラーでオブジェクトが選択されている場合にのみ使用できます。|  
|**スキーマを変換します。**|選択した SAP ASE オブジェクトに変換します[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースのオブジェクト。<br /><br />このコマンドは、Sybase メタデータ エクスプ ローラーでオブジェクトが選択されている場合にのみ使用できます。|  
|**データを移行します。**|SAP ASE データベースからデータを移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースです。 このコマンドを実行する前に、SAP ASE スキーマを変換する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースのスキーマにオブジェクトを読み込むと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースです。<br /><br />このコマンドは、Sybase メタデータ エクスプ ローラーでオブジェクトが選択されている場合にのみ使用できます。|  
|**[停止]**|オブジェクトを変換するなど、現在のプロセスを停止する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL Database の構文。|  
  
### <a name="menus"></a>メニュー  
SSMA には、次のメニューが含まれています。  
  
|メニュー|Description|  
|--------|---------------|  
|**ファイル**|プロジェクトで作業し、SAP ASE に接続しに接続するためのコマンドを含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースです。|  
|**[編集]**|検索して、詳細ページで、コピーするなどのテキストの操作用のコマンドを含む[!INCLUDE[tsql](../../includes/tsql_md.md)]SQL の詳細ウィンドウ。 含まれています、**管理ブックマーク**オプション、既存のブックマークの一覧を表示できます。 ダイアログ ボックスの右側にあるボタンを使用するには、それらのブックマークを管理します。|  
|**[表示]**|含まれています、**メタデータ エクスプ ローラーの同期**コマンド。 これにより、同期 Sybase メタデータ エクスプ ローラーの間でオブジェクトと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure メタデータ エクスプ ローラー。 表示と非表示のコマンドを含む、**出力**と**エラー一覧**ペインおよびオプション**レイアウト**レイアウトを管理します。|  
|**ツール**|レポートを作成、データをエクスポートおよびオブジェクトとデータを移行するためのコマンドが含まれています。 アクセスする、**グローバル設定**と**プロジェクト設定** ダイアログ ボックス。|  
|**テスト担当者**|テスト_ケース、テスト結果を表示、およびデータベースのバックアップの管理用のコマンドを作成するコマンドが含まれています。|  
|**ヘルプ**|SSMA のヘルプにされ、アクセスできるように、**に関する** ダイアログ ボックス。|  
  
### <a name="output-pane-and-error-list-pane"></a>出力ウィンドウと エラー一覧ウィンドウ  
**ビュー**メニュー コマンドの出力ウィンドウと [エラー一覧] ウィンドウの表示を切り替えるには。  
  
-   [出力] ペインは、SSMA からオブジェクトへの変換、オブジェクトの同期、およびデータの移行中にステータス メッセージを示します。  
  
-   [エラー一覧] ウィンドウでは、並べ替えることができますを一連のエラー、警告、および情報メッセージを示します。  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL データベースへの SAP ASE データベースの移行&#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
[ユーザー インターフェイス リファレンス&#40;SybaseToSQL&#41;](../../ssma/sybase/user-interface-reference-sybasetosql.md)  
