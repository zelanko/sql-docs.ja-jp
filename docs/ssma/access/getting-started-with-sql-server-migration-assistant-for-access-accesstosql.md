---
title: Access の SQL Server Migration Assistant を使ってみる |Microsoft Docs
description: SSMA を使用して Access データベースオブジェクトを SQL Server または Azure SQL Database オブジェクトに変換し、結果のオブジェクトをアップロードして、データを移行する方法については、「」をご覧ください。
ms.prod: sql
ms.custom: ''
ms.date: 08/15/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- error list pane
- getting started
- menus
- metadata explorers
- output pane
- toolbars
- user interface
- user interface overview
ms.assetid: 462a731f-08f1-44e1-9eeb-4deac6d2f6c5
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: e49e55c31e346671f7f66a42e23c39e7a64e3808
ms.sourcegitcommit: 59cda5a481cfdb4268b2744edc341172e53dede4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84293949"
---
# <a name="getting-started-with-sql-server-migration-assistant-for-access-accesstosql"></a>アクセスのための SQL Server Migration Assistant の概要 (アクセス用 SQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Access の Migration Assistant (SSMA) を使用すると、Access データベースオブジェクトをまたは Azure SQL DB オブジェクトに簡単に変換したり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 結果のオブジェクトを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE sql db にアップロードしたり、access から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または azure sql db にデータを移行したりすることができます。 必要に応じて、または azure sql db テーブルにアクセステーブルをリンクすることもでき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。これにより、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE sql db で既存のアクセスフロントエンドアプリケーションを引き続き使用することができます。  
  
このトピックでは、インストールプロセスについて説明します。 SSMA ユーザーインターフェイスについて理解するのに役立ちます。  
  
## <a name="installing-ssma"></a>SSMA のインストール  
SSMA を使用するには、まず、移行するデータベースとターゲットインスタンス [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (または AZURE SQL DB) の両方にアクセスできるコンピューターに ssma クライアントプログラムをインストールする必要があります。 インストール手順については、「 [&#41;&#40;Access の SQL Server Migration Assistant をインストールする](../../ssma/access/installing-sql-server-migration-assistant-for-access-accesstosql.md)」を参照してください。  
  
SSMA を開始するには、[**スタート**] をクリックし、[**すべてのプログラム**] をポイントします。次に、[**アクセス SQL Server Migration Assistant**] をポイントし、[**アクセス SQL Server Migration Assistant**] を選択します。  
  
## <a name="using-ssma"></a>SSMA の使用  
SSMA をインストールした後、このツールを使用して Access データベースを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE SQL DB に移行する前に、ssma ユーザーインターフェイスに慣れることができます。 SSMA ユーザーインターフェイスは、次の図に示すように、メタデータエクスプローラー、メタデータ、ツールバー、出力ウィンドウ、および [エラー一覧] ウィンドウを含みます。  
  
![SSMA for Access のグラフィカル ユーザー インターフェイス](../../ssma/access/media/ssmaforaccessgui.gif "SSMA for Access のグラフィカル ユーザー インターフェイス")  
  
移行を開始するには、新しいプロジェクトを作成し、access データベースを追加して、メタデータエクスプローラーにアクセスします。 その後、Access Metadata Explorer で [オブジェクト] を右クリックして、次のようなタスクを実行できます。
- Access データベースオブジェクトのインベントリを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE SQL DB にエクスポートする。
- または Azure SQL DB への変換を評価するレポートを作成する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。
- アクセススキーマを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE SQL DB スキーマに変換する。

また、ツールバーとメニューを使用して、これらのタスクを実行することもできます。  
  
また、のインスタンスに接続する必要もあり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 接続に成功すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メタデータエクスプローラーにデータベースの階層が表示され [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 アクセススキーマをスキーマに変換した後 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、メタデータエクスプローラーで変換されたスキーマを選択し、スキーマをに読み込むことができ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
[新しいプロジェクト] ダイアログボックスの [移行先] ドロップダウンから [Azure SQL DB] を選択した場合は、Azure SQL DB に接続する必要があります。 接続に成功すると、azure sql db メタデータエクスプローラーに Azure SQL DB データベースの階層が表示されます。 アクセススキーマを Azure SQL DB スキーマに変換した後、Azure SQL DB メタデータエクスプローラーで変換されたスキーマを選択し、スキーマをに読み込むことができ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
変換されたスキーマを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE SQL db に読み込むと、メタデータエクスプローラーにアクセスして、access データベースから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE sql db データベースにデータを移行することができます。 必要に応じて、アクセステーブルを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE SQL DB テーブルにリンクすることもできます。  
  
これらのタスクとその実行方法の詳細については、次のトピックを参照してください。  
  
-   [Access データベースの移行の準備](preparing-access-databases-for-migration-accesstosql.md)  
  
-   [Access データベースの SQL Server への移行](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
-   [Access アプリケーションの SQL Server へのリンク](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)  
  
次のセクションでは、SSMA ユーザーインターフェイスの機能について説明します。  
  
### <a name="metadata-explorers"></a>メタデータエクスプローラー  
SSMA には、Access や Azure SQL DB データベースに対する操作を参照して実行するために使用できる2つのメタデータエクスプローラーが含まれてい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
#### <a name="access-metadata-explorer"></a>メタデータ エクスプローラーにアクセスする  
Access メタデータエクスプローラーには、プロジェクトに追加された Access データベースに関する情報が表示されます。 Access データベースを追加すると、SSMA によってそのデータベースに関するメタデータが取得されます。これは Access メタデータエクスプローラーで使用できるメタデータです。  
  
Access Metadata Explorer を使用して、次のタスクを実行できます。  
  
-   各 Access データベースのテーブルを参照します。  
  
-   変換するオブジェクトを選択し、オブジェクトを構文に変換し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 詳細については、「 [Access データベースオブジェクトの変換](converting-access-database-objects-accesstosql.md)」を参照してください。  
  
-   データ移行用のオブジェクトを選択し、それらのオブジェクトからにデータを移行し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 詳細については、「SQL Server への[アクセスデータの移行](migrating-access-data-into-sql-server-azure-sql-db-accesstosql.md)」を参照してください。  
  
-   アクセスとテーブルのリンクとリンク解除を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 行います。  
  
#### <a name="sql-server-or-azure-sql-db-metadata-explorer"></a>SQL Server または Azure SQL DB メタデータエクスプローラー  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または Azure sql DB メタデータエクスプローラーには、または Azure SQL DB のインスタンスに関する情報が表示さ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] れます。 または Azure SQL DB のインスタンスに接続すると [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、SSMA はそのインスタンスに関するメタデータを取得し、プロジェクトファイルに格納します。  
  
SQL Server または Azure SQL DB メタデータエクスプローラーを使用して、変換された Access データベースオブジェクトを選択し、それらのオブジェクトを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE SQL db のインスタンスに読み込んで (同期する) ことができます。  
  
詳細については、「変換された[データベースオブジェクトの SQL Server への読み込み](loading-converted-database-objects-into-sql-server-accesstosql.md)」を参照してください。  
  
### <a name="metadata"></a>Metadata  
各メタデータエクスプローラーの右側には、選択したオブジェクトを説明するタブがあります。 たとえば、Access Metadata Explorer でテーブルを選択すると、**テーブル**、**型マッピング**、**プロパティ**、**データ**の4つのタブが表示されます。 メタデータエクスプローラーでテーブルを選択すると [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、**テーブル**、 **SQL**、**データ**の3つのタブが表示されます。  
  
ほとんどのメタデータ設定は読み取り専用です。 ただし、次のメタデータを変更できます。  
  
-   Access Metadata Explorer では、型マッピングを変更できます。 レポートを作成したりスキーマを変換したりする前に、必ずこれらの変更を行ってください。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータエクスプローラーでは、[**テーブル**] タブでテーブルおよびインデックスのプロパティを変更できます。スキーマをに読み込む前に、これらの変更を行っ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] てください。 詳細については、「 [Access データベースオブジェクトの変換](converting-access-database-objects-accesstosql.md)」を参照してください。  
  
### <a name="toolbars"></a>[ツール バー]  
SSMA には、[プロジェクト] ツールバーと [移行] ツールバーの2つのツールバーがあります。  
  
#### <a name="the-project-toolbar"></a>[プロジェクト] ツールバー  
プロジェクトツールバーには、プロジェクトを操作したり、Access データベースファイルを追加し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] たり、または AZURE SQL DB に接続したりするためのボタンが含まれています。 これらのボタンは、[**ファイル**] メニューのコマンドに似ています。  
  
#### <a name="the-migration-toolbar"></a>[移行] ツールバー  
[移行] ツールバーには、次のコマンドがあります。  
  
|Button|関数|  
|----------|------------|  
|**変換、読み込み、および移行**|Access データベースを変換し、変換されたオブジェクトを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE SQL db に読み込み、データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE sql db に移行します。すべて1回の手順で行います。|  
|**レポートの作成**|選択したアクセススキーマを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE SQL DB 構文に変換し、変換が成功したかどうかを示すレポートを作成します。<br /><br />このコマンドは、Access メタデータエクスプローラーでオブジェクトが選択されている場合にのみ使用できます。|  
|**スキーマの変換**|選択したアクセススキーマを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE SQL DB スキーマに変換します。<br /><br />このコマンドは、Access メタデータエクスプローラーでオブジェクトが選択されている場合にのみ使用できます。|  
|**データの移行**|Access データベースから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE SQL DB にデータを移行します。 このコマンドを実行する前に、アクセススキーマを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE SQL db スキーマに変換してから、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE sql db にオブジェクトを読み込む必要があります。<br /><br />このコマンドは、Access メタデータエクスプローラーでオブジェクトが選択されている場合にのみ使用できます。|  
|**Stop**|オブジェクトを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE SQL DB 構文に変換するなど、現在のプロセスを停止します。|  
  
### <a name="menus"></a>メニュー  
SSMA には、次のメニューが含まれています。  
  
|メニュー|説明|  
|--------|---------------|  
|**[最近使ったファイル]**|移行ウィザード、プロジェクトの操作、Access データベースファイルの追加と削除、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE SQL DB への接続を行うためのコマンドが含まれています。|  
|**[編集]**|[ [!INCLUDE[tsql](../../includes/tsql-md.md)] SQL の詳細] ペインからコピーするなど、詳細ページ内のテキストを検索して操作するためのコマンドが含まれています。 [ブックマークの**管理**] ダイアログを開くには、[編集] メニューの [ブックマークの管理] をクリックします。 ダイアログには、既存のブックマークの一覧が表示されます。 ダイアログの右側にあるボタンを使用して、ブックマークを管理できます。|  
|**表示**|**メタデータエクスプローラーの同期**コマンドを含みます。 これにより、Access メタデータエクスプローラー [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE SQL DB メタデータエクスプローラー間でオブジェクトが同期されます。 には、**出力**ペインおよび**エラー一覧**ウィンドウの表示と非表示を切り替えるコマンドと、レイアウトで管理するオプション**レイアウト**も含まれています。|  
|**ツール**|レポートの作成、データのエクスポート、オブジェクトとデータの移行、テーブルのリンク、および [グローバルおよびプロジェクトの設定] ダイアログボックスへのアクセスを行うためのコマンドが含まれています。|  
|**ヘルプ**|SSMA ヘルプおよび [**バージョン情報**] ダイアログボックスへのアクセスを提供します。|  
  
### <a name="output-pane-and-error-list-pane"></a>出力ウィンドウとエラー一覧ペイン  
[**表示**] メニューには、[出力] ウィンドウと [エラー一覧] ウィンドウの表示を切り替えるためのコマンドが用意されています。  
  
-   [出力] ウィンドウには、オブジェクトの変換、オブジェクトの同期、およびデータ移行中に SSMA からのステータスメッセージが表示されます。  
  
-   エラー一覧ペインには、エラー、警告、および情報の各メッセージが一覧に表示され、並べ替えることができます。  
  
## <a name="see-also"></a>関連項目  
[Access データベースの SQL Server への移行](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
