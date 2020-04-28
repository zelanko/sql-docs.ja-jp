---
title: SSMA for SAP ASE でのはじめに (SybaseToSQL) |Microsoft Docs
ms.custom: ''
ms.date: 09/30/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: c4098516-f0fc-4690-97bb-3766dfd43156
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: f07f230f52fee5707084c01060e92220b35cb75c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68029125"
---
# <a name="getting-started-with-ssma-for-sap-ase-sybasetosql"></a>SSMA for SAP ASE でのはじめに (SybaseToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SAP ASE 用の Migration Assistant (SSMA) を使用すると、SAP Adaptive Server Enterprise (ASE) データベース[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スキーマを簡単にまたは Azure SQL Database スキーマに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換したり、結果のスキーマをまたは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] AZURE SQL DATABASE にアップロードしたり、sap ase からまたは Azure SQL Database にデータを移行したりできます。  
  
このトピックでは、インストールプロセスについて説明した後、SSMA ユーザーインターフェイスについて理解することができます。  
  
## <a name="installing-and-licensing-ssma"></a>SSMA のインストールとライセンス  
SSMA を使用するに Azure SQL Database は、まず、SAP ASE のソースインスタンスとの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ターゲットインスタンスの両方にアクセスできるコンピューターに ssma クライアントプログラムをインストールする必要があります。 サーバー側のデータ移行を使用するには、を実行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]しているコンピューターに拡張パックと、少なくとも1つの SAP ASE プロバイダー (OLE DB または ADO.NET) をインストールする必要があります。 これらのコンポーネントは、SAP ASE システム関数のデータ移行とエミュレーションをサポートしています。 インストール手順については、「 [SSMA FOR SAP ASE &#40;SybaseToSQL&#41;のインストール](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)」を参照してください。  
  
Ssma を開始するには、[**スタート**] をクリックし、[**すべてのプログラム**] をポイントします。次に、[sybase] の [ ** [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant**] をポイントし、[ ** [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sybase の Migration Assistant**] を選択します。 SSMA を初めて起動したときに、[ライセンス] ダイアログボックスが表示されます。 SSMA を使用するには、Windows Live ID を使用して SSMA のライセンスを付与する必要があります。 ライセンスの手順については、「 [SSMA For Sybase クライアントのインストール &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md) 」のインストール手順を参照してください。  
  
## <a name="ssma-for-sap-ase-user-interface"></a>SSMA for SAP ASE のユーザーインターフェイス  
SSMA のインストールとライセンス供与が完了したら、SSMA を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SAP ASE データベースをまたは Azure SQL Database に移行することができます。 これは、開始する前に SSMA ユーザーインターフェイスを理解するのに役立ちます。 次の図は、メタデータエクスプローラー、メタデータ、ツールバー、出力ウィンドウ、および [エラー一覧] ウィンドウを含む SSMA のユーザーインターフェイスを示しています。  
  
![SSMA for SAP ASE のユーザーインターフェイス](../../ssma/sybase/media/ssmaforsybaseuserinterface.jpg "SSMA for SAP ASE のユーザーインターフェイス")  
  
移行を開始するには、最初に新しいプロジェクトを作成する必要があります。 次に、SAP ASE に接続します。 接続が成功すると、SAP ASE データベースの階層が Sybase メタデータエクスプローラーに表示されます。 Sybase メタデータエクスプローラーでオブジェクトを右クリックして、または Azure SQL Database へ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の変換を評価するレポートの作成などのタスクを実行できます。 また、ツールバーやメニューを使用して、これらのタスクを実行することもできます。  
  
また、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスまたは Azure SQL Database に接続する必要もあります。 接続が成功すると、または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Azure メタデータエクスプローラーに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または Azure SQL データベースの階層が表示されます。 SAP ASE スキーマをまたは Azure SQL Database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スキーマに変換した後、または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Azure メタデータエクスプローラーで変換されたスキーマを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]選択してから、または Azure SQL Database にスキーマを読み込みます。  
  
変換されたスキーマを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または Azure SQL Database に読み込むと、Sybase メタデータエクスプローラーに戻り、SAP ASE データベースから[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または Azure SQL データベースにデータを移行することができます。  
  
これらのタスクとその実行方法の詳細については、「SAP ASE データベースの SQL Server への移行」を参照してください。 [Azure SQL Database &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)。  
  
次のセクションでは、SSMA ユーザーインターフェイスの機能について説明します。  
  
### <a name="metadata-explorers"></a>メタデータエクスプローラー  
SSMA に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、SAP ASE または Azure SQL データベースに対する操作を参照して実行するための2つのメタデータエクスプローラーが含まれています。  
  
#### <a name="sybase-metadata-explorer"></a>Sybase メタデータエクスプローラー  
Sybase メタデータエクスプローラーには、SAP ASE のソースインスタンス上のデータベースに関する情報が表示されます。  
  
Sybase メタデータエクスプローラーを使用すると、次のタスクを実行できます。  
  
-   各データベース内のテーブルを参照します。  
  
-   変換するオブジェクトを選択し、オブジェクトをまたは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Azure SQL Database 構文に変換します。 詳細については、「 [sql&#41;&#40;の SAP ASE データベースオブジェクトの変換](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)」を参照してください。  
  
-   データ移行用のオブジェクトを選択し、それらのオブジェクトからまたは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Azure SQL Database にデータを移行します。 詳細については、「 [SQL Server Azure SQL Database &#40;SybaseToSQL&#41;への SAP ASE データの移行](../../ssma/sybase/migrating-sybase-ase-data-into-sql-server-azure-sql-db-sybasetosql.md)」を参照してください。  
  
#### <a name="sql-server-or-sql-azure-metadata-explorer"></a>SQL Server または SQL Azure メタデータエクスプローラー  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure メタデータエクスプローラーでは、また[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は Azure SQL Database のインスタンスに関する情報が表示されます。 または Azure SQL Database の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに接続すると、ssma はそのインスタンスに関するメタデータを取得し、プロジェクトファイルに格納します。  
  
または SQL Azure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータエクスプローラーを使用して、変換された SAP ASE データベースオブジェクトを選択し、それらのオブジェクトを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または Azure SQL Database のインスタンスに読み込んで (同期) できます。  
  
詳細については、「変換された[データベースオブジェクトを SQL Server &#40;SybaseToSQL&#41;に読み込む](../../ssma/sybase/loading-converted-database-objects-into-sql-server-sybasetosql.md)」を参照してください。  
  
### <a name="metadata"></a>Metadata  
各メタデータエクスプローラーの右側には、選択したオブジェクトを説明するタブがあります。 たとえば、Sybase メタデータエクスプローラーでテーブルを選択すると、**テーブル**、 **SQL**、**型マッピング**、**データ**、**プロパティ**、および**レポート**の6つのタブが表示されます。 [**レポート**] タブには、選択したオブジェクトを含むレポートを作成した後にのみ情報が表示されます。 または SQL Azure メタデータエクスプローラー [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でテーブルを選択すると、**テーブル**、 **SQL**、**データ**の3つのタブが表示されます。  
  
ほとんどのメタデータ設定は読み取り専用です。 ただし、次のメタデータを変更できます。  
  
-   Sybase Metadata Explorer では、プロシージャと型マッピングを変更できます。 スキーマを変換する前に、これらの変更を行います。  
  
-   また[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は SQL Azure メタデータエクスプローラーでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)]ストアドプロシージャのを変更できます。 スキーマをに読み込む前に、これらの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変更を行います。  
  
メタデータエクスプローラーで行った変更は、ソースまたはターゲットのデータベースではなく、プロジェクトのメタデータに反映されます。  
  
### <a name="toolbars"></a>[ツール バー]  
SSMA には、[プロジェクト] ツールバーと [移行] ツールバーの2つのツールバーがあります。  
  
#### <a name="the-project-toolbar"></a>[プロジェクト] ツールバー  
プロジェクトツールバーには、プロジェクトを操作したり、SAP ASE に接続したり[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、または Azure SQL Database に接続したりするためのボタンが含まれています。 これらのボタンは、[**ファイル**] メニューのコマンドに似ています。  
  
#### <a name="the-migration-toolbar"></a>[移行] ツールバー  
[移行] ツールバーには、次のコマンドがあります。  
  
|Button|関数|  
|----------|------------|  
|**レポートの作成**|選択した SAP ASE オブジェクトを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]構文に変換し、変換が成功したかどうかを示すレポートを作成します。<br /><br />このコマンドは、Sybase メタデータエクスプローラーでオブジェクトが選択されている場合にのみ使用できます。|  
|**スキーマの変換**|選択した SAP ASE オブジェクトを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または Azure SQL Database オブジェクトに変換します。<br /><br />このコマンドは、Sybase メタデータエクスプローラーでオブジェクトが選択されている場合にのみ使用できます。|  
|**データの移行**|SAP ASE データベースからまたは Azure SQL Database に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データを移行します。 このコマンドを実行する前に、SAP ASE スキーマをまたは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Azure SQL Database スキーマに変換し、オブジェクトをまたは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Azure SQL Database に読み込む必要があります。<br /><br />このコマンドは、Sybase メタデータエクスプローラーでオブジェクトが選択されている場合にのみ使用できます。|  
|**Stop**|オブジェクトをまたは Azure SQL Database 構文に変換する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]など、現在のプロセスを停止します。|  
  
### <a name="menus"></a>メニュー  
SSMA には、次のメニューが含まれています。  
  
|メニュー|説明|  
|--------|---------------|  
|**[最近使ったファイル]**|プロジェクトを操作したり、SAP ASE に接続したり、または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Azure SQL Database に接続したりするためのコマンドが含まれています。|  
|**[編集]**|[SQL の詳細] ペインからコピー [!INCLUDE[tsql](../../includes/tsql-md.md)]するなど、詳細ページ内のテキストを検索して操作するためのコマンドが含まれています。 には、[**ブックマークの管理**] オプションもあります。このオプションでは、既存のブックマークの一覧が表示されます。 ダイアログの右側にあるボタンを使用して、ブックマークを管理できます。|  
|**表示**|**メタデータエクスプローラーの同期**コマンドを含みます。 これにより、Sybase メタデータエクスプローラーと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Azure メタデータエクスプローラー間でオブジェクトが同期されます。 には、**出力**ペインおよび**エラー一覧**ウィンドウの表示と非表示を切り替えるコマンドと、レイアウトを管理するためのオプション**レイアウト**も含まれています。|  
|**ツール**|レポートの作成、データのエクスポート、およびオブジェクトとデータの移行を行うためのコマンドが含まれています。 [**グローバル設定**] および [プロジェクトの**設定**] ダイアログボックスへのアクセスも提供します。|  
|**テスト担当者**|テストケースを作成したり、テスト結果を表示したり、データベースバックアップ管理のコマンドを表示したりするためのコマンドが含まれています。|  
|**ヘルプ**|SSMA ヘルプおよび [**バージョン情報**] ダイアログボックスへのアクセスを提供します。|  
  
### <a name="output-pane-and-error-list-pane"></a>出力ウィンドウとエラー一覧ペイン  
[**表示**] メニューには、[出力] ウィンドウと [エラー一覧] ウィンドウの表示を切り替えるためのコマンドが用意されています。  
  
-   [出力] ウィンドウには、オブジェクトの変換、オブジェクトの同期、およびデータ移行中に SSMA からのステータスメッセージが表示されます。  
  
-   エラー一覧ペインには、エラー、警告、および情報の各メッセージが一覧に表示され、並べ替えることができます。  
  
## <a name="see-also"></a>関連項目  
[SAP ASE データベースの SQL Server Azure SQL Database &#40;SybaseToSQL&#41;への移行](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
[ユーザーインターフェイスリファレンス &#40;SybaseToSQL&#41;](../../ssma/sybase/user-interface-reference-sybasetosql.md)  
