---
title: "入門 SSMA for Oracle (OracleToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSMA for Oracle, Metadata Explorers
- SSMA for Oracle, Toolbars
ms.assetid: df79664c-972e-4bef-865a-ce609789fee7
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2ad25369dc4a9d9cc7a26795320050dcb583e92b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="getting-started-with-ssma-for-oracle-oracletosql"></a>入門 SSMA for Oracle (OracleToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) の Oracle できます迅速に変換する Oracle データベース スキーマ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマへの結果として得られるスキーマのアップロード[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]に Oracle からデータを移行し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
このトピックでは、インストール プロセスを導入し、し SSMA ユーザー インターフェイスを理解するために役立ちます。  
  
## <a name="installing-ssma"></a>SSMA のインストール  
SSMA を使用する必要がありますに初めてインストールする SSMA クライアント プログラム ソース Oracle データベースとのターゲット インスタンスの両方にアクセスできるコンピューター[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 必要がありますをインストールする拡張機能パックと少なくとも 1 つの Oracle プロバイダー (OLE DB または[!INCLUDE[vstecado](../../includes/vstecado_md.md)]) を実行しているコンピューターで[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 これらのコンポーネントは、データの移行と Oracle システム関数のエミュレーションをサポートします。 インストール手順については、次を参照してください。 [SSMA for Oracle (&) #40";"OracleToSQL"&"#41; にインストールする](../../ssma/oracle/installing-ssma-for-oracle-oracletosql.md)です。  
  
SSMA を起動する をクリックして**開始**、 をポイント**すべてのプログラム**、 をポイント **[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant for Oracle**、クリックして **[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant for Oracle**です。  
  
## <a name="ssma-for-oracle-user-interface"></a>SSMA for Oracle のユーザー インターフェイス  
SSMA をインストールした後に Oracle データベースを移行 SSMA を使用することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 開始する前に、SSMA ユーザー インターフェイスを理解するのに役立ちます。 次の図は、SSMA を含むメタデータ エクスプ ローラー、メタデータ、ツールバー、出力ウィンドウ、およびエラー一覧 ウィンドウのユーザー インターフェイスを示しています。  
  
![SSMA for Oracle UI](../../ssma/oracle/media/ssma_oracle_ui.jpg "SSMA for Oracle の UI")  
  
移行を開始するには、まず新しいプロジェクトを作成する必要があります。 次に、Oracle データベースに接続します。 接続に成功した後は、Oracle スキーマは、Oracle メタデータ エクスプ ローラーに表示されます。 変換を評価するレポートの作成などのタスクを実行する Oracle メタデータ エクスプ ローラーでオブジェクトを右クリックしを実行できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 ツールバーとメニューを使用して、これらのタスクを行うこともできます。  
  
インスタンスに接続することも必要があります。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 階層、接続が成功した[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースが表示されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラー。 Oracle スキーマを変換した後[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマでこれらの変換されたスキーマを選択して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラーで、しでスキーマを同期[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
使用するスキーマの変換後の同期後[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、Oracle メタデータ エクスプ ローラーに戻るしへの Oracle スキーマからデータを移行できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。  
  
これらのタスクとその実行方法の詳細については、次を参照してください。 [SQL Server (&) #40";"OracleToSQL"&"#41; への Oracle データベースの移行](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)です。  
  
次のセクションでは、SSMA ユーザー インターフェイスの機能を説明します。  
  
### <a name="metadata-explorers"></a>メタデータ エクスプ ローラー  
SSMA を参照して、Oracle に対する操作の実行の 2 つのメタデータ エクスプ ローラーを含むと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。  
  
#### <a name="oracle-metadata-explorer"></a>Oracle メタデータ エクスプ ローラー  
Oracle メタデータ エクスプ ローラーでは、Oracle スキーマについての情報が表示されます。 Oracle メタデータ エクスプ ローラーを使用すると、次のタスクを実行できます。  
  
-   各スキーマ内のオブジェクトを参照します。  
  
-   変換に、オブジェクトを選択し、オブジェクトに変換[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]構文です。 詳細については、次を参照してください。 [Oracle スキーマを変換する (&) #40";"OracleToSQL"&"#41;](../../ssma/oracle/converting-oracle-schemas-oracletosql.md)です。  
  
-   データ移行のためのテーブルを選択し、これらのテーブルからデータを移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 詳細については、次を参照してください。 [SQL Server (&) #40";"OracleToSQL"&"#41; への Oracle データの移行](../../ssma/oracle/migrating-oracle-data-into-sql-server-oracletosql.md)です。  
  
#### <a name="sql-server-metadata-explorer"></a>SQL Server メタデータ エクスプ ローラー  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラーのインスタンスに関する情報が表示[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 インスタンスに接続する場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SSMA は、そのインスタンスに関するメタデータを取得し、プロジェクト ファイルに格納します。  
  
使用することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラーを変換後の Oracle データベース オブジェクトを選択し、それらのオブジェクトのインスタンスと同期して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
詳細については、次を参照してください。[に SQL Server (&) #40";"OracleToSQL"&"#41 です。 変換されたデータベース オブジェクトの読み込み](../../ssma/oracle/loading-converted-database-objects-into-sql-server-oracletosql.md)です。  
  
### <a name="metadata"></a>メタデータ  
各メタデータ エクスプ ローラーの右側には、選択したオブジェクトを記述するタブが。 たとえば、Oracle メタデータ エクスプ ローラーでテーブルを選択する場合は、6 つのタブは表示:**テーブル**、 **SQL**、**の種類のマッピング、レポート**、**プロパティ**、および**データ**です。 **レポート** タブは、選択したオブジェクトを格納しているレポートを作成した後のみに情報を格納します。 内のテーブルを選択した場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラーで、3 つのタブが表示されます:**テーブル**、 **SQL**、および**データ**です。  
  
ほとんどのメタデータの設定とは、読み取り専用です。 ただし、次のメタデータを変更することができます。  
  
-   Oracle メタデータ エクスプ ローラーでプロシージャを変更し、マッピングを入力できます。 変更後の手順を変換して、入力のマッピングには、スキーマを変換する前に、変更をします。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラーを変更すること、[!INCLUDE[tsql](../../includes/tsql_md.md)]ストアド プロシージャの場合。 これらの変更を表示する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]へのスキーマを読み込む前に、これらの変更を行う[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
ソースまたはターゲット データベースではなく、プロジェクトのメタデータには、メタデータ エクスプ ローラーで行われた変更が反映されます。  
  
### <a name="toolbars"></a>[ツール バー]  
SSMA は 2 つのツールバー: プロジェクト ツールバー、および移行ツールバー。  
  
#### <a name="the-project-toolbar"></a>プロジェクトのツールバー  
プロジェクトのツールバーには、プロジェクトで作業し、Oracle に接続しに接続するためのボタンが含まれています。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 これらのボタンで、コマンドのように、**ファイル**メニュー。  
  
#### <a name="migration-toolbar"></a>移行のツールバー  
次の表は、移行のツール バー コマンドを示しています。  
  
|ボタン|関数|  
|------|--------|  
|**レポートを作成します。**|選択した Oracle オブジェクトに変換します[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]構文、し成功に変換されたを示すレポートを作成します。<br /><br />このコマンドは、オブジェクトが Oracle メタデータ エクスプ ローラーで選択されていない場合は無効です。|  
|**スキーマを変換します。**|選択した Oracle オブジェクトに変換します[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オブジェクト。<br /><br />このコマンドは、オブジェクトが Oracle メタデータ エクスプ ローラーで選択されていない場合は無効です。|  
|**データを移行します。**|Oracle データベースからデータを移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 このコマンドを実行する前にする Oracle スキーマに変換する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマにオブジェクトを読み込むと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。<br /><br />このコマンドは、オブジェクトが Oracle メタデータ エクスプ ローラーで選択されていない場合は無効です。|  
|**[停止]**|現在のプロセスを停止します。|  
  
### <a name="menus"></a>メニュー  
次の表は、SSMA メニューを表示します。  
  
|メニュー|Description|  
|----|-----------|  
|**ファイル**|プロジェクトで作業し、Oracle に接続しに接続するためのコマンドを含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。|  
|**[編集]**|検索して、詳細ページで、コピーするなどのテキストの操作用のコマンドを含む[!INCLUDE[tsql](../../includes/tsql_md.md)]SQL の詳細ウィンドウ。 含まれています、**管理ブックマーク**オプション、いることができますを既存のブックマークの一覧を表示します。 ダイアログ ボックスの右側にあるボタンを使用するには、それらのブックマークを管理します。|  
|**[表示]**|含まれています、**メタデータ エクスプ ローラーの同期**コマンド。 Oracle メタデータ エクスプ ローラーの間でオブジェクトを同期して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラー。 コマンドを表示/非表示を含む、**出力**と**エラー一覧**ペインおよびオプション**レイアウト**レイアウトを管理します。|  
|**ツール**|レポートを作成し、オブジェクトとデータを移行するためのコマンドが含まれています。 アクセスする、**グローバル設定**と**プロジェクト設定** ダイアログ ボックス。|  
|**テスト担当者**|テスト_ケースは、リポジトリ、およびバックアップの管理システムの作成と操作用のコマンドが含まれています。|  
|**ヘルプ**|SSMA のヘルプにされ、アクセスできるように、**に関する** ダイアログ ボックス。|  
  
### <a name="output-pane-and-error-list-pane"></a>出力ウィンドウとエラー一覧ウィンドウ  
**ビュー**メニュー コマンドの出力ウィンドウと [エラー一覧] ウィンドウの表示を切り替えるには。  
  
-   [出力] ペインは、SSMA からオブジェクトへの変換、オブジェクトの同期、およびデータの移行中にステータス メッセージを示します。  
  
-   エラー一覧 ウィンドウは、並べ替え可能な一覧で、エラー、警告、および情報メッセージを示します。  
  
## <a name="see-also"></a>参照  
[SQL Server (&) #40";"OracleToSQL"&"#41; への Oracle データの移行](../../ssma/oracle/migrating-oracle-data-into-sql-server-oracletosql.md)  
[ユーザー インターフェイス リファレンス (&) #40";"OracleToSQL"&"#41;](../../ssma/oracle/user-interface-reference-oracletosql.md)  
  

