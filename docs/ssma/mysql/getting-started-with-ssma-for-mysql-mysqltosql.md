---
title: SSMA for MySQL (MySQLToSQL) でのはじめに |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Getting started, MySQL metadata explorer
- Getting started, SQL Server or SQL Azure metadata explorer
- Getting started,Installing and licensing
ms.assetid: 8ebfa061-be6f-4a07-923f-8dc832a82f70
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 5a1adb6d9354dc870c11fab0a68f6c92e704ebfb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67984537"
---
# <a name="getting-started-with-ssma-for-mysql-mysqltosql"></a>SSMA for MySQL 入門 (MySQLToSQL)
SQL Server Migration Assistant (SSMA) for MySQL を使用すると、MySQL データベーススキーマを SQL Server または Azure SQL DB スキーマに簡単に変換したり、結果として得られるスキーマを SQL Server または Azure SQL db にアップロードしたり、MySQL から SQL Server または Azure SQL DB にデータを移行したりすることができます。  
  
このトピックでは、インストールプロセスについて説明した後、SSMA ユーザーインターフェイスについて理解することができます。  
  
## <a name="installing-ssma"></a>SSMA のインストール  
SSMA を使用するには、まず、ソース MySQL データベースと SQL Server または Azure SQL DB のターゲットインスタンスの両方にアクセスできるコンピューターに SSMA クライアントプログラムをインストールする必要があります。 次に、SSMA クライアントプログラムを実行しているコンピューターに MySQL プロバイダー (MySQL ODBC 5.1 ドライバー (trusted)) をインストールします。 インストール手順については、「 [SSMA For MySQL &#40;MySqlToSql のインストール](../../ssma/mysql/installing-ssma-for-mysql-mysqltosql.md)」を参照してください&#41;  
  
SSMA を開始するには、[**スタート**] をクリックし、[**すべてのプログラム**] をポイントします。次に、[mysql] をポイントし、[ **SQL Server Migration Assistant for mysql**] **SQL Server Migration Assistant**をクリックします。  
  
## <a name="ssma-for-mysql-user-interface"></a>SSMA for MySQL のユーザー インターフェイス  
SSMA のインストールとライセンス供与が完了したら、SSMA を使用して、MySQL データベースを SQL Server または Azure SQL DB に移行することができます。 これは、開始する前に SSMA ユーザーインターフェイスを理解するのに役立ちます。 次の図は、メタデータエクスプローラー、メタデータ、ツールバー、出力ウィンドウ、および [エラー一覧] ウィンドウを含む SSMA のユーザーインターフェイスを示しています。  
  
![SSMA for MySQL のグラフィカル ユーザー インターフェイス](../../ssma/mysql/media/ssmaformysqlgui.gif "SSMA for MySQL のグラフィカル ユーザー インターフェイス")  
  
移行を開始するには、次のことを行う必要があります。  
  
1.  新しいプロジェクトを作成します。  
  
2.  MySQL データベースに接続します。  
  
3.  接続が成功すると、mysql スキーマが MySQL メタデータエクスプローラーに表示されます。 MySQL メタデータエクスプローラーで [オブジェクト] を右クリックして、SQL Server/Azure SQL DB への変換を評価するレポートの作成などのタスクを実行します。  
  
また、ツールバーとメニューを使用して、これらのタスクを実行することもできます。  
  
また、SQL Server のインスタンスに接続する必要もあります。 接続に成功すると、SQL Server データベースの階層が SQL Server メタデータエクスプローラーに表示されます。 MySQL スキーマを SQL Server スキーマに変換した後 SQL Server メタデータエクスプローラーで変換されたスキーマを選択し、スキーマを SQL Server と同期します。  
  
[新しいプロジェクト] ダイアログボックスの [移行先] ドロップダウンから Azure SQL DB を選択した場合は、Azure SQL DB に接続する必要があります。 接続が成功すると、azure sql db のメタデータエクスプローラーに Azure SQL DB データベースの階層が表示されます。 MySQL スキーマを Azure SQL DB スキーマに変換した後、Azure SQL DB メタデータエクスプローラーで変換されたスキーマを選択し、スキーマを Azure SQL DB と同期します。  
  
変換されたスキーマを SQL Server または Azure SQL DB と同期した後、MySQL メタデータエクスプローラーに戻り、MySQL スキーマから SQL Server または Azure SQL DB データベースにデータを移行することができます。  
  
これらのタスクとその実行方法の詳細については、「 [SQL Server への MySQL データベースの移行-AZURE SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)」を参照してください。  
  
次のセクションでは、SSMA ユーザーインターフェイスの機能について説明します。  
  
### <a name="metadata-explorers"></a>メタデータエクスプローラー  
SSMA には、MySQL および SQL Server データベースに対する操作を参照して実行するための2つのメタデータエクスプローラーが含まれています。  
  
### <a name="mysql-metadata-explorer"></a>MySQL メタデータエクスプローラー  
Mysql メタデータエクスプローラーには、MySQL スキーマに関する情報が表示されます。 MySQL メタデータエクスプローラーを使用すると、次のタスクを実行できます。  
  
-   各スキーマ内のオブジェクトを参照します。  
  
-   変換するオブジェクトを選択し、オブジェクトを SQL Server 構文に変換します。 詳細については、「 [MySQL データベース &#40;MySQLToSQL の変換](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)」を参照してください&#41;  
  
-   データ移行用のテーブルを選択し、それらのテーブルのデータを SQL Server に移行します。 詳細については、「 [SQL Server への MySQL データの移行-AZURE SQL DB &#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md) 」を参照してください。  
  
### <a name="sql-server-or-azure-sql-db-metadata-explorer"></a>SQL Server または Azure SQL DB メタデータエクスプローラー  
SQL Server または Azure SQL DB メタデータエクスプローラーには、SQL Server または Azure SQL DB のインスタンスに関する情報が表示されます。 SQL Server または Azure SQL DB のインスタンスに接続すると、SSMA はそのインスタンスに関するメタデータを取得し、プロジェクトファイルに格納します。  
  
このメタデータエクスプローラーを使用して、変換された MySQL データベースオブジェクトを選択し、それらのオブジェクトを SQL Server または Azure SQL DB のインスタンスと同期させることができます。  
  
詳細については、「[同期 (MySQL から SQL Server/AZURE SQL DB)](https://msdn.microsoft.com/ac993a6d-0283-4823-8793-6b217677dfa3) 」を参照してください。  
  
### <a name="metadata"></a>Metadata  
各メタデータエクスプローラーの右側には、選択したオブジェクトを説明するタブがあります。 たとえば、MySQL メタデータエクスプローラーでテーブルを選択すると、**テーブル**、 **SQL**、**型マッピング**、**データ**、**設定**、**文字セットマッピング**、 **SQL モード**、**プロパティ**、および**レポート**の9つのタブが表示されます。 [**レポート**] タブには、選択したオブジェクトを含むレポートを作成した後にのみ情報が表示されます。 SQL Server メタデータエクスプローラーでテーブルを選択すると、**テーブル**、 **SQL** 、**データ**の3つのタブが表示されます。  
  
ほとんどのメタデータ設定は読み取り専用です。 ただし、次のメタデータを変更できます。  
  
-   MySQL メタデータエクスプローラーでは、型のマッピング、文字セットのマッピング、SQL モードを変更できます。 変更された型のマッピングまたは文字セットのマッピングまたは SQL モードを変換するには、スキーマを変換する前に変更を加えます。  
  
-   SQL Server メタデータエクスプローラーでは、[テーブル] タブのテーブルおよびインデックスのプロパティを変更できます。これらの変更を SQL Server で確認するには、スキーマを SQL Server に読み込む前に、これらの変更を行います。  
  
メタデータエクスプローラーで行った変更は、ソースまたはターゲットのデータベースではなく、プロジェクトのメタデータに反映されます。  
  
### <a name="toolbars"></a>[ツール バー]  
SSMA には、[プロジェクト] ツールバーと [移行] ツールバーの2つのツールバーがあります。  
  
### <a name="the-project-toolbar"></a>[プロジェクト] ツールバー  
プロジェクトツールバーには、プロジェクトの操作、MySQL への接続、SQL Server または Azure SQL DB への接続を行うためのボタンが含まれています。 これらのボタンは、[**ファイル**] メニューのコマンドに似ています。  
  
### <a name="migration-toolbar"></a>移行ツールバー  
次の表は、移行ツールバーのコマンドを示しています。  
  
|||  
|-|-|  
|**Button**|**関数**|  
|**レポートの作成**|選択した MySQL オブジェクトを SQL Server または Azure SQL DB オブジェクトに変換し、変換が成功したかどうかを示すレポートを作成します。<br /><br />MySQL メタデータエクスプローラーでオブジェクトが選択されていない場合、このコマンドは無効になります。|  
|**スキーマの変換**|選択された MySQL オブジェクトを SQL Server または Azure SQL DB オブジェクトに変換します。<br /><br />MySQL メタデータエクスプローラーでオブジェクトが選択されていない場合、このコマンドは無効になります。|  
|**データの移行**|MySQL データベースから SQL Server または Azure SQL DB にデータを移行します。 このコマンドを実行する前に、MySQL スキーマを SQL Server または Azure SQL DB スキーマに変換し、そのオブジェクトを SQL Server または Azure SQL DB に読み込む必要があります。<br /><br />MySQL メタデータエクスプローラーでオブジェクトが選択されていない場合、このコマンドは無効になります。|  
|**Stop**|現在のプロセスを停止します。|  
  
### <a name="menus"></a>メニュー  
SSMA メニューを次の表に示します。  
  
|||  
|-|-|  
|**メニュー**|**説明**|  
|**[最近使ったファイル]**|プロジェクトを操作したり、MySQL に接続したり、SQL Server または Azure SQL DB に接続したりするためのコマンドが含まれています。|  
|**[編集]**|詳細ページ内のテキストを検索して操作するためのコマンドが含まれています。 [**ブックマークの管理**] ダイアログを開くには、[編集] メニューの [ブックマークの管理] をクリックします。 ダイアログには、既存のブックマークの一覧が表示されます。 ダイアログの右側にあるボタンを使用して、ブックマークを管理できます。|  
|**表示**|**メタデータエクスプローラーの同期**コマンドを含みます。 これにより、MySQL メタデータエクスプローラーと SQL Server または Azure SQL DB メタデータエクスプローラー間でオブジェクトが同期されます。 には、**出力**ペインおよび**エラー一覧**ウィンドウの表示と非表示を切り替えるコマンドと、レイアウトで管理するオプション**レイアウト**も含まれています。|  
|**ツール**|レポートを作成したり、スキーマを変換したり、データベースから更新したり、オブジェクトとデータを移行したり、スクリプトとして保存したりするためのコマンドが含まれています。 また、[**グローバル設定]、[既定のプロジェクト設定**]、[**プロジェクトの設定**] の各ダイアログボックスへのアクセスも提供します。|  
|**ヘルプ**|SSMA ヘルプおよび [**バージョン情報**] ダイアログボックスへのアクセスを提供します。|  
  
### <a name="output-pane-and-error-list-pane"></a>出力ウィンドウとエラー一覧ペイン  
[**表示**] メニューには、[出力] ウィンドウと [エラー一覧] ウィンドウの表示を切り替えるためのコマンドが用意されています。  
  
-   [出力] ウィンドウには、オブジェクトの変換、オブジェクトの同期、およびデータ移行中に SSMA からのステータスメッセージが表示されます。  
  
-   エラー一覧ペインには、並べ替え可能な一覧にエラーメッセージ、警告メッセージ、および情報メッセージが表示されます。  
  
## <a name="see-also"></a>参照  
[ユーザーインターフェイスリファレンス &#40;MySQLToSQL&#41;](../../ssma/mysql/user-interface-reference-mysqltosql.md)  
[MySQL データの SQL Server への移行-Azure SQL DB &#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
