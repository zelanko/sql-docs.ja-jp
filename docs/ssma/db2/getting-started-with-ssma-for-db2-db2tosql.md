---
title: SSMA for DB2 (DB2ToSQL) でのはじめに |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 48ca32fc-1830-4d1f-add7-480ba5ad02e8
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 0eab4f23e342c95d83baa70dd03aba2f5d4bc8d1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67989640"
---
# <a name="getting-started-with-ssma-for-db2-db2tosql"></a>SSMA for DB2 (DB2ToSQL) を使用したはじめに
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Migration Assistant (SSMA) for DB2 を使用すると、DB2 データベーススキーマ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をスキーマに簡単に変換し[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、結果のスキーマをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]アップロードして、db2 からにデータを移行することができます。  
  
このトピックでは、インストールプロセスについて説明した後、SSMA ユーザーインターフェイスについて理解することができます。  
  
## <a name="installing-ssma"></a>SSMA のインストール  
SSMA を使用するには、最初に、ソースの DB2 データベースとの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ターゲットインスタンスの両方にアクセスできるコンピューターに ssma クライアントプログラムをインストールする必要があります。 を実行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]しているコンピューター上の DB2 OLEDB プロバイダー。 これらのコンポーネントは、DB2 システム関数のデータ移行とエミュレーションをサポートしています。 インストール手順については、「 [SSMA FOR DB2 &#40;DB2ToSQL&#41;のインストール](../../ssma/db2/installing-ssma-for-db2-db2tosql.md)」を参照してください。  
  
Ssma を開始するには、[**スタート**] をクリックし、[**すべてのプログラム**] をポイントします。次に、[db2] をポイントし、[ ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant for db2**] ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant**をクリックします。  
  
## <a name="ssma-for-db2-user-interface"></a>SSMA for DB2 ユーザーインターフェイス  
SSMA のインストール後、SSMA を使用して DB2 データベースをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行することができます。 これは、開始する前に SSMA ユーザーインターフェイスを理解するのに役立ちます。 次の図は、メタデータエクスプローラー、メタデータ、ツールバー、出力ウィンドウ、および [エラー一覧] ウィンドウを含む SSMA のユーザーインターフェイスを示しています。  
  
![SSMA ユーザー インターフェイス](../../ssma/db2/media/ssma_db2_ui.png "SSMA ユーザー インターフェイス")  
  
移行を開始するには、最初に新しいプロジェクトを作成する必要があります。 次に、DB2 データベースに接続します。 接続に成功すると、db2 スキーマが DB2 メタデータエクスプローラーに表示されます。 次に、DB2 メタデータエクスプローラーでオブジェクトを右クリックして、へ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の変換を評価するレポートの作成などのタスクを実行できます。 また、ツールバーとメニューを使用して、これらのタスクを実行することもできます。  
  
また、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに接続する必要もあります。 接続が成功すると、データベースの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]階層がメタデータ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エクスプローラーに表示されます。 DB2 スキーマをスキーマに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換したら、それらの変換さ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]れたスキーマをメタデータエクスプローラーで選択[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]し、スキーマをと同期します。  
  
変換されたスキーマを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と同期した後、Db2 メタデータエクスプローラーに戻り、db2 スキーマ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のデータをデータベースに移行できます。  
  
これらのタスクとその実行方法の詳細については、「 [DB2 データベースの SQL Server &#40;DB2ToSQL&#41;への移行](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)」を参照してください。  
  
次のセクションでは、SSMA ユーザーインターフェイスの機能について説明します。  
  
### <a name="metadata-explorers"></a>メタデータエクスプローラー  
SSMA には、DB2 と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースに対する操作を参照して実行するための2つのメタデータエクスプローラーが含まれています。  
  
#### <a name="db2-metadata-explorer"></a>DB2 メタデータエクスプローラー  
Db2 メタデータエクスプローラーには、DB2 スキーマに関する情報が表示されます。 DB2 メタデータエクスプローラーを使用すると、次のタスクを実行できます。  
  
-   各スキーマ内のオブジェクトを参照します。  
  
-   変換するオブジェクトを選択し、オブジェクトを構文に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換します。 詳細については、「 [DB2 スキーマ &#40;DB2ToSQL&#41;の変換](../../ssma/db2/converting-db2-schemas-db2tosql.md)」を参照してください。  
  
-   データ移行用のテーブルを選択し、それらのテーブルのデータを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に移行します。 詳細については、「 [DB2 データベースの SQL Server &#40;DB2ToSQL&#41;への移行](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)」を参照してください。  
  
#### <a name="sql-server-metadata-explorer"></a>SQL Server メタデータエクスプローラー  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータエクスプローラーには、のインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に関する情報が表示されます。 の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに接続すると、ssma はそのインスタンスに関するメタデータを取得し、プロジェクトファイルに格納します。  
  
メタデータエクスプローラー [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して、変換された DB2 データベースオブジェクトを選択し、そのオブジェクト[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をのインスタンスと同期させることができます。  
  
### <a name="metadata"></a>Metadata  
各メタデータエクスプローラーの右側には、選択したオブジェクトを説明するタブがあります。 たとえば、DB2 メタデータエクスプローラーでテーブルを選択すると、**テーブル**、 **SQL**、**型マッピング、レポート**、**プロパティ**、**データ**の6つのタブが表示されます。 [**レポート**] タブには、選択したオブジェクトを含むレポートを作成した後にのみ情報が表示されます。 メタ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データエクスプローラーでテーブルを選択すると、**テーブル**、 **SQL**、**データ**の3つのタブが表示されます。  
  
ほとんどのメタデータ設定は読み取り専用です。 ただし、次のメタデータを変更できます。  
  
-   DB2 メタデータエクスプローラーでは、プロシージャと型マッピングを変更できます。 変更されたプロシージャと型マッピングを変換するには、スキーマを変換する前に変更を加えます。  
  
-   メタ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データエクスプローラーでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)]ストアドプロシージャのを変更できます。 で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]これらの変更を確認するには、スキーマをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]読み込む前に、これらの変更を行います。  
  
メタデータエクスプローラーで行った変更は、ソースまたはターゲットのデータベースではなく、プロジェクトのメタデータに反映されます。  
  
### <a name="toolbars"></a>[ツール バー]  
SSMA には、[プロジェクト] ツールバーと [移行] ツールバーの2つのツールバーがあります。  
  
#### <a name="the-project-toolbar"></a>[プロジェクト] ツールバー  
[プロジェクト] ツールバーには、プロジェクトを操作したり、DB2 に接続[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]したり、に接続したりするためのボタンが含まれています。 これらのボタンは、[**ファイル**] メニューのコマンドに似ています。  
  
#### <a name="migration-toolbar"></a>移行ツールバー  
次の表は、移行ツールバーのコマンドを示しています。  
  
|ボタン|Function|  
|------|--------|  
|**レポートの作成**|選択した DB2 オブジェクトを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]構文に変換し、変換が成功したかどうかを示すレポートを作成します。<br /><br />このコマンドは、DB2 メタデータエクスプローラーでオブジェクトが選択されていない限り、無効になっています。|  
|**スキーマの変換**|選択した DB2 オブジェクトを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクトに変換します。<br /><br />このコマンドは、DB2 メタデータエクスプローラーでオブジェクトが選択されていない限り、無効になっています。|  
|**データの移行**|DB2 データベースからにデータを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行します。 このコマンドを実行する前に、DB2 スキーマをスキーマに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換し、オブジェクトをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]読み込む必要があります。<br /><br />このコマンドは、DB2 メタデータエクスプローラーでオブジェクトが選択されていない限り、無効になっています。|  
|**停止**|現在のプロセスを停止します。|  
  
### <a name="menus"></a>メニュー  
SSMA メニューを次の表に示します。  
  
|メニュー|[説明]|  
|----|-----------|  
|**拡張子**|プロジェクトを操作したり、DB2 に接続したり、に接続[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]したりするためのコマンドが含まれています。|  
|**[編集]**|[SQL の詳細] ペインからコピー [!INCLUDE[tsql](../../includes/tsql-md.md)]するなど、詳細ページ内のテキストを検索して操作するためのコマンドが含まれています。 には、[**ブックマークの管理**] オプションも含まれています。このオプションを使用すると、既存のブックマークの一覧を表示できます。 ダイアログの右側にあるボタンを使用して、ブックマークを管理できます。|  
|**モード**|**メタデータエクスプローラーの同期**コマンドを含みます。 これにより、DB2 メタデータエクスプローラーと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータエクスプローラーの間でオブジェクトが同期されます。 には、**出力**ペインおよび**エラー一覧**ウィンドウの表示と非表示を切り替えるコマンドと、レイアウトを管理するためのオプション**レイアウト**も含まれています。|  
|**ツール**|レポートを作成し、オブジェクトとデータを移行するためのコマンドが含まれています。 [**グローバル設定**] および [プロジェクトの**設定**] ダイアログボックスへのアクセスも提供します。|  
|**Help**|SSMA ヘルプおよび [**バージョン情報**] ダイアログボックスへのアクセスを提供します。|  
  
### <a name="output-pane-and-error-list-pane"></a>出力ウィンドウとエラー一覧ペイン  
[**表示**] メニューには、[出力] ウィンドウと [エラー一覧] ウィンドウの表示を切り替えるためのコマンドが用意されています。  
  
-   [出力] ウィンドウには、オブジェクトの変換、オブジェクトの同期、およびデータ移行中に SSMA からのステータスメッセージが表示されます。  
  
-   エラー一覧ペインには、並べ替え可能な一覧にエラーメッセージ、警告メッセージ、および情報メッセージが表示されます。  
  
## <a name="see-also"></a>参照  
[DB2 データの SQL Server &#40;DB2ToSQL&#41;への移行](../../ssma/db2/migrating-db2-data-into-sql-server-db2tosql.md)  
[ユーザーインターフェイスリファレンス &#40;DB2ToSQL&#41;](../../ssma/db2/user-interface-reference-db2tosql.md)  
  
