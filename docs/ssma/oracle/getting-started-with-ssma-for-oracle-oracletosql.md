---
title: SSMA for Oracle (OracleToSQL) を使用したはじめに |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- SSMA for Oracle, Metadata Explorers
- SSMA for Oracle, Toolbars
ms.assetid: df79664c-972e-4bef-865a-ce609789fee7
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: ef71a9355bc11c4d377f00a44b2b8cd2958f8656
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68264455"
---
# <a name="getting-started-with-ssma-for-oracle-oracletosql"></a>SSMA for Oracle 入門 (OracleToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Oracle 用の Migration Assistant (SSMA) を使用すると、Oracle データベース[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スキーマをスキーマに簡単に変換[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]し、その結果のスキーマ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をにアップロードし、oracle からにデータを移行することができます。  
  
このトピックでは、インストールプロセスについて説明した後、SSMA ユーザーインターフェイスについて理解することができます。  
  
## <a name="installing-ssma"></a>SSMA のインストール  
SSMA を使用するには、まず、ソース Oracle データベースとの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ターゲットインスタンスの両方にアクセスできるコンピューターに ssma クライアントプログラムをインストールする必要があります。 次に、を実行[!INCLUDE[vstecado](../../includes/vstecado_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]しているコンピューターに拡張パックと Oracle プロバイダー (OLE DB または) の少なくとも1つをインストールする必要があります。 これらのコンポーネントは、データの移行と、Oracle システム関数のエミュレーションをサポートします。 インストール手順については、「 [SSMA For Oracle &#40;OracleToSQL&#41;のインストール](../../ssma/oracle/installing-ssma-for-oracle-oracletosql.md)」を参照してください。  
  
Ssma を開始するには、[**スタート**] をクリックし、[**すべてのプログラム**] をポイントします。次に、[oracle] を** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant**ポイントし、[ ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant oracle**] をクリックします。  
  
## <a name="ssma-for-oracle-user-interface"></a>SSMA for Oracle ユーザーインターフェイス  
SSMA のインストール後、SSMA を使用して Oracle データベースをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行することができます。 これは、開始する前に SSMA ユーザーインターフェイスを理解するのに役立ちます。 次の図は、メタデータエクスプローラー、メタデータ、ツールバー、出力ウィンドウ、および [エラー一覧] ウィンドウを含む SSMA のユーザーインターフェイスを示しています。  
  
![SSMA for Oracle の UI](../../ssma/oracle/media/ssma_oracle_ui.jpg "SSMA for Oracle の UI")  
  
移行を開始するには、最初に新しいプロジェクトを作成する必要があります。 次に、Oracle データベースに接続します。 接続が成功すると、oracle スキーマが Oracle メタデータエクスプローラーに表示されます。 次に、Oracle メタデータエクスプローラーでオブジェクトを右クリックして、へ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の変換を評価するレポートの作成などのタスクを実行できます。 また、ツールバーとメニューを使用して、これらのタスクを実行することもできます。  
  
また、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに接続する必要もあります。 接続が成功すると、データベースの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]階層がメタデータ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エクスプローラーに表示されます。 Oracle スキーマをスキーマに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換したら、それらの変換さ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]れたスキーマをメタデータエクスプローラーで選択[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]し、スキーマをと同期します。  
  
変換されたスキーマを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と同期した後、Oracle メタデータエクスプローラーに戻り、oracle スキーマ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のデータをデータベースに移行できます。  
  
これらのタスクとその実行方法の詳細については、「 [SQL Server &#40;OracleToSQL&#41;への Oracle データベースの移行](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)」を参照してください。  
  
次のセクションでは、SSMA ユーザーインターフェイスの機能について説明します。  
  
### <a name="metadata-explorers"></a>メタデータエクスプローラー  
SSMA には、Oracle と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースに対する操作を参照して実行するための2つのメタデータエクスプローラーが含まれています。  
  
#### <a name="oracle-metadata-explorer"></a>Oracle メタデータエクスプローラー  
Oracle メタデータエクスプローラーには、Oracle スキーマに関する情報が表示されます。 Oracle メタデータエクスプローラーを使用すると、次のタスクを実行できます。  
  
-   各スキーマ内のオブジェクトを参照します。  
  
-   変換するオブジェクトを選択し、オブジェクトを構文に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換します。 詳細については、「 [Oracle スキーマ &#40;OracleToSQL&#41;の変換](../../ssma/oracle/converting-oracle-schemas-oracletosql.md)」を参照してください。  
  
-   データ移行用のテーブルを選択し、それらのテーブルのデータを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に移行します。 詳細については、「 [SQL Server &#40;OracleToSQL&#41;に Oracle データを移行](../../ssma/oracle/migrating-oracle-data-into-sql-server-oracletosql.md)する」を参照してください。  
  
#### <a name="sql-server-metadata-explorer"></a>SQL Server メタデータエクスプローラー  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータエクスプローラーには、のインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に関する情報が表示されます。 の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに接続すると、ssma はそのインスタンスに関するメタデータを取得し、プロジェクトファイルに格納します。  
  
メタデータエクスプローラー [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して、変換された Oracle データベースオブジェクトを選択し、そのオブジェクト[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をのインスタンスと同期させることができます。  
  
詳細については、「変換された[データベースオブジェクトを SQL Server &#40;OracleToSQL&#41;に読み込む](../../ssma/oracle/loading-converted-database-objects-into-sql-server-oracletosql.md)」を参照してください。  
  
### <a name="metadata"></a>Metadata  
各メタデータエクスプローラーの右側には、選択したオブジェクトを説明するタブがあります。 たとえば、Oracle メタデータエクスプローラーでテーブルを選択すると、**テーブル**、 **SQL**、**型マッピング、レポート**、**プロパティ**、**データ**の6つのタブが表示されます。 [**レポート**] タブには、選択したオブジェクトを含むレポートを作成した後にのみ情報が表示されます。 メタ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データエクスプローラーでテーブルを選択すると、**テーブル**、 **SQL**、**データ**の3つのタブが表示されます。  
  
ほとんどのメタデータ設定は読み取り専用です。 ただし、次のメタデータを変更できます。  
  
-   Oracle メタデータエクスプローラーでは、プロシージャと型マッピングを変更できます。 変更されたプロシージャと型マッピングを変換するには、スキーマを変換する前に変更を加えます。  
  
-   メタ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データエクスプローラーでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)]ストアドプロシージャのを変更できます。 で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]これらの変更を確認するには、スキーマをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]読み込む前に、これらの変更を行います。  
  
メタデータエクスプローラーで行った変更は、ソースまたはターゲットのデータベースではなく、プロジェクトのメタデータに反映されます。  
  
### <a name="toolbars"></a>[ツール バー]  
SSMA には、[プロジェクト] ツールバーと [移行] ツールバーの2つのツールバーがあります。  
  
#### <a name="the-project-toolbar"></a>[プロジェクト] ツールバー  
プロジェクトツールバーには、プロジェクトの操作、Oracle への接続、およびへ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の接続を行うためのボタンが含まれています。 これらのボタンは、[**ファイル**] メニューのコマンドに似ています。  
  
#### <a name="migration-toolbar"></a>移行ツールバー  
次の表は、移行ツールバーのコマンドを示しています。  
  
|Button|関数|  
|------|--------|  
|**レポートの作成**|選択した Oracle オブジェクトを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]構文に変換し、変換が成功したかどうかを示すレポートを作成します。<br /><br />このコマンドは、Oracle メタデータエクスプローラーでオブジェクトが選択されていない限り、無効になっています。|  
|**スキーマの変換**|選択した Oracle オブジェクトを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクトに変換します。<br /><br />このコマンドは、Oracle メタデータエクスプローラーでオブジェクトが選択されていない限り、無効になっています。|  
|**データの移行**|Oracle データベースのデータをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行します。 このコマンドを実行する前に、Oracle スキーマをスキーマに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換し、オブジェクトをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]読み込む必要があります。<br /><br />このコマンドは、Oracle メタデータエクスプローラーでオブジェクトが選択されていない限り、無効になっています。|  
|**Stop**|現在のプロセスを停止します。|  
  
### <a name="menus"></a>メニュー  
SSMA メニューを次の表に示します。  
  
|メニュー|説明|  
|----|-----------|  
|**[最近使ったファイル]**|プロジェクトを操作したり、Oracle に接続したり、に接続[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]したりするためのコマンドが含まれています。|  
|**[編集]**|[SQL の詳細] ペインからコピー [!INCLUDE[tsql](../../includes/tsql-md.md)]するなど、詳細ページ内のテキストを検索して操作するためのコマンドが含まれています。 には、[**ブックマークの管理**] オプションも含まれています。このオプションを使用すると、既存のブックマークの一覧を表示できます。 ダイアログの右側にあるボタンを使用して、ブックマークを管理できます。|  
|**表示**|**メタデータエクスプローラーの同期**コマンドを含みます。 これにより、Oracle メタデータエクスプローラーと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータエクスプローラーの間でオブジェクトが同期されます。 には、**出力**ペインおよび**エラー一覧**ウィンドウの表示と非表示を切り替えるコマンドと、レイアウトを管理するためのオプション**レイアウト**も含まれています。|  
|**ツール**|レポートを作成し、オブジェクトとデータを移行するためのコマンドが含まれています。 [**グローバル設定**] および [プロジェクトの**設定**] ダイアログボックスへのアクセスも提供します。|  
|**テスト担当者**|テストケース、リポジトリ、およびバックアップ管理システムを作成および操作するためのコマンドが含まれています。|  
|**ヘルプ**|SSMA ヘルプおよび [**バージョン情報**] ダイアログボックスへのアクセスを提供します。|  
  
### <a name="output-pane-and-error-list-pane"></a>出力ウィンドウとエラー一覧ペイン  
[**表示**] メニューには、[出力] ウィンドウと [エラー一覧] ウィンドウの表示を切り替えるためのコマンドが用意されています。  
  
-   [出力] ウィンドウには、オブジェクトの変換、オブジェクトの同期、およびデータ移行中に SSMA からのステータスメッセージが表示されます。  
  
-   エラー一覧ペインには、並べ替え可能な一覧にエラーメッセージ、警告メッセージ、および情報メッセージが表示されます。  
  
## <a name="see-also"></a>参照  
[Oracle データの SQL Server &#40;OracleToSQL&#41;への移行](../../ssma/oracle/migrating-oracle-data-into-sql-server-oracletosql.md)  
[ユーザーインターフェイスリファレンス &#40;OracleToSQL&#41;](../../ssma/oracle/user-interface-reference-oracletosql.md)  
  
