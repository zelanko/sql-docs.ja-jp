---
title: "SQL Server Migration Assistant for Access の概要 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-access
ms.custom: 
ms.date: 08/15/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
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
caps.latest.revision: "24"
author: Shamikg
ms.author: Shamikg
manager: murato
ms.workload: On Demand
ms.openlocfilehash: 92a7e496075cb7e42c09bd89a1f17e1b296b9946
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="getting-started-with-sql-server-migration-assistant-for-access-accesstosql"></a>SQL Server Migration Assistant for Access (AccessToSQL) の概要
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) のアクセスでは、すばやくアクセス使用するデータベース オブジェクトを変換することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Azure SQL DB オブジェクトに結果として得られるオブジェクトのアップロードまたは[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB へのアクセスからデータを移行および[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB します。 かどうか必要に応じて、リンクすることもアクセス テーブルを[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]既存の Access のフロント エンド アプリケーションでの使用を継続できるように Azure SQL DB がテーブルまたは[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB します。  
  
このトピックでは、インストール プロセスについて説明し、SSMA ユーザー インターフェイスを使用することを理解するのに役立ちます。  
  
## <a name="installing-ssma"></a>SSMA のインストール  
SSMA を使用する必要がありますに初めてインストールする SSMA クライアント プログラムを移行する、両方のデータベースにアクセスできるコンピューターとのターゲット インスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB します。 インストール手順については、次を参照してください。[をインストールする SQL Server Migration Assistant for Access &#40;です。AccessToSQL &#41;](../../ssma/access/installing-sql-server-migration-assistant-for-access-accesstosql.md).  
  
SSMA を起動するには、クリックして**開始**、 をポイント**すべてのプログラム**、 をポイント**SQL Server Migration Assistant for Access**、し、 **SQL Server Migration Assistant for Access**です。  
  
## <a name="using-ssma"></a>SSMA の使用  
SSMA をインストールすると役に立ちますに Access データベースを移行するツールを使用する前に、SSMA ユーザー インターフェイスに慣れる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB します。 SSMA ユーザー インターフェイスで、メタデータ エクスプ ローラー、メタデータ、ツールバー、出力ウィンドウ、およびエラー一覧ウィンドウを含む次の図に示します。  
  
![SSMA for Access のグラフィカル ユーザー インターフェイス](../../ssma/access/media/ssmaforaccessgui.gif "SSMA for Access のグラフィカル ユーザー インターフェイス")  
  
移行を開始するには、新しいプロジェクトを作成し、アクセス メタデータ エクスプ ローラーに Access データベースを追加します。 タスクを実行するようアクセス メタデータ エクスプ ローラーでオブジェクトを右クリックし、できます。
- エクスポートするデータベース オブジェクトのインベントリ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB します。
- 変換を評価するレポートを作成する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB します。
- アクセスのスキーマを変換する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB のスキーマです。

ツールバーとメニューを使用して、これらのタスクを行うこともできます。  
  
インスタンスに接続することも必要があります。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 階層、接続が成功した[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]にデータベースが表示されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラー。 アクセスのスキーマを変換した後[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマに変換されたスキーマを選択できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラーへのスキーマを読み込むと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
移行から新しいプロジェクト ダイアログ ボックスのドロップダウン リストに Azure SQL DB を選択した場合は、Azure SQL DB に接続する必要があります。 接続に成功した後は、Azure SQL DB メタデータ エクスプ ローラーで Azure SQL DB データベースの階層が表示されます。 Azure SQL DB のスキーマにアクセス スキーマを変換した後は、Azure SQL DB メタデータ エクスプ ローラーで、これらの変換されたスキーマを選択し、へのスキーマを読み込む[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]します。  
  
変換後のスキーマの読み込み後[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB アクセス メタデータ エクスプ ローラーに戻ってをしたに Access データベースからデータを移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB データベース。 かどうか必要に応じて、リンクすることもアクセス テーブルを[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB テーブル。  
  
これらのタスクとその実行方法の詳細については、次のトピックを参照してください。  
  
-   [Access データベースの移行の準備](http://msdn.microsoft.com/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)  
  
-   [SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
-   [SQL Server へのリンクの Access アプリケーション](http://msdn.microsoft.com/82374ad2-7737-4164-a489-13261ba393d4)  
  
次のセクションでは、SSMA ユーザー インターフェイスの機能を説明します。  
  
### <a name="metadata-explorers"></a>メタデータ エクスプ ローラー  
SSMA を参照してアクセスに対する操作の実行に使用できる 2 つのメタデータ エクスプ ローラーを含むと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB データベース。  
  
#### <a name="access-metadata-explorer"></a>メタデータ エクスプ ローラーにアクセスします。  
アクセス メタデータ エクスプ ローラーでは、プロジェクトに追加されている Access データベースに関する情報を表示します。 Access データベースを追加すると、SSMA は、アクセス メタデータ エクスプ ローラーで使用できるメタデータは、そのデータベースに関するメタデータを取得します。  
  
アクセス メタデータ エクスプ ローラーを使用するには、次のタスクを実行します。  
  
-   アクセスの各データベース内のテーブルを参照します。  
  
-   変換のためのオブジェクトを選択してオブジェクトを変換[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]構文です。 詳細については、次を参照してください。[データベース オブジェクトの変換へのアクセス](http://msdn.microsoft.com/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)です。  
  
-   データ移行のオブジェクトを選択してからそれらのオブジェクトをデータを移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 詳細については、次を参照してください。 [SQL Server への Access データの移行](http://msdn.microsoft.com/f3b18af7-1af0-499d-a00d-a0af94895625)です。  
  
-   リンクし、リンク解除のアクセスと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]テーブル。  
  
#### <a name="sql-server-or-azure-sql-db-metadata-explorer"></a>SQL Server または Azure SQL DB メタデータ エクスプ ローラー  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Azure SQL DB メタデータ エクスプ ローラーのインスタンスに関する情報が表示または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB します。 インスタンスに接続する場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB、SSMA そのインスタンスに関するメタデータを取得し、プロジェクト ファイルに格納します。  
  
変換されたデータベース オブジェクトを選択して読み込むこと、SQL Server または Azure SQL DB メタデータ エクスプ ローラーを使用することができます (同期) のインスタンスにそれらのオブジェクト[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB します。  
  
詳細については、次を参照してください。 [SQL Server に変換されたデータベース オブジェクトの読み込み](http://msdn.microsoft.com/4e854eee-b10c-4f0b-9d9e-d92416e6f2ba)です。  
  
### <a name="metadata"></a>メタデータ  
各メタデータ エクスプ ローラーの右側には、選択したオブジェクトを記述するタブが。 たとえば、アクセス メタデータ エクスプ ローラーでテーブルを選択する場合は、4 つのタブが表示されます。:**テーブル**、**型マッピング**、**プロパティ**、および**データ**です。 内のテーブルを選択した場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラーで、次の 3 つのタブに表示されます:**テーブル**、 **SQL**、および**データ**です。  
  
ほとんどのメタデータの設定とは、読み取り専用です。 ただし、次のメタデータを変更することができます。  
  
-   アクセス メタデータ エクスプ ローラーで、型のマッピングを変更することができます。 必ずレポートを作成またはスキーマを変換する前に、これらの変更を作成してください。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラーでテーブルとインデックスのプロパティを変更することができます、**テーブル**タブです。スキーマを読み込む前に、これらの変更を行う[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 詳細については、次を参照してください。[データベース オブジェクトの変換へのアクセス](http://msdn.microsoft.com/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)です。  
  
### <a name="toolbars"></a>[ツール バー]  
SSMA は 2 つのツールバー: プロジェクト ツールバー、および移行ツールバー。  
  
#### <a name="the-project-toolbar"></a>プロジェクトのツールバー  
プロジェクトのツールバーには、プロジェクトでの作業、Access データベース ファイルの追加、およびに接続するためのボタンが含まれています。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB します。 これらのボタンで、コマンドのように、**ファイル**メニュー。  
  
#### <a name="the-migration-toolbar"></a>移行ツールバー  
移行のツールバーには、次のコマンドが含まれています。  
  
|ボタン|機能|  
|----------|------------|  
|**変換、読み込み、および移行**|Access データベースを変換に変換されたオブジェクトを読み込みます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB にデータを移行および[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または 1 つの手順ですべての Azure SQL DB します。|  
|**レポートを作成します。**|選択したアクセスのスキーマを変換[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB 構文し成功に変換されたを示すレポートを作成します。<br /><br />このコマンドは、オブジェクトがアクセス メタデータ エクスプ ローラーで選択した場合にのみ使用できます。|  
|**スキーマを変換します。**|選択したアクセスのスキーマを変換[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB のスキーマです。<br /><br />このコマンドは、オブジェクトがアクセス メタデータ エクスプ ローラーで選択した場合にのみ使用できます。|  
|**データを移行します。**|Access データベースからデータを移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB します。 このコマンドを実行する前にするアクセス スキーマに変換する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB のスキーマにオブジェクトを読み込むと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB します。<br /><br />このコマンドは、オブジェクトがアクセス メタデータ エクスプ ローラーで選択した場合にのみ使用できます。|  
|**[停止]**|オブジェクトを変換するなど、現在のプロセスを停止する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB の構文。|  
  
### <a name="menus"></a>メニュー  
SSMA には、次のメニューが含まれています。  
  
|メニュー|Description|  
|--------|---------------|  
|**[最近使ったファイル]**|移行ウィザードは、プロジェクトでは、作業への接続の追加と Access データベース ファイルの削除のコマンドを含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB します。|  
|**[編集]**|検索して、詳細ページで、コピーするなどのテキストの操作用のコマンドを含む[!INCLUDE[tsql](../../includes/tsql_md.md)]SQL の詳細ウィンドウ。 開くには、**管理ブックマーク**ダイアログで、[編集] メニューで、[ブックマークの管理] をクリックします。 ダイアログ ボックスで、既存のブックマークの一覧が表示されます。 ダイアログ ボックスの右側にあるボタンを使用するには、それらのブックマークを管理します。|  
|**[表示]**|含まれています、**メタデータ エクスプ ローラーの同期**コマンド。 これにより、同期アクセス メタデータ エクスプ ローラーの間でオブジェクトと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB メタデータ エクスプ ローラー。 表示と非表示のコマンドを含む、**出力**と**エラー一覧**ペインおよびオプション**レイアウト**レイアウトを管理します。|  
|**ツール**|レポートを作成、データをエクスポート、オブジェクトとデータの移行、テーブルをリンクするためのコマンドを格納し、グローバルへのアクセスとプロジェクトの設定 ダイアログ ボックスを提供します。|  
|**ヘルプ**|SSMA のヘルプにされ、アクセスできるように、**に関する** ダイアログ ボックス。|  
  
### <a name="output-pane-and-error-list-pane"></a>出力ウィンドウと エラー一覧ウィンドウ  
**ビュー**メニュー コマンドの出力ウィンドウと [エラー一覧] ウィンドウの表示を切り替えるには。  
  
-   [出力] ペインは、SSMA からオブジェクトへの変換、オブジェクトの同期、およびデータの移行中にステータス メッセージを示します。  
  
-   [エラー一覧] ウィンドウでは、並べ替えることができますを一連のエラー、警告、および情報メッセージを示します。  
  
## <a name="see-also"></a>参照  
[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
