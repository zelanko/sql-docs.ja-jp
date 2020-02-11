---
title: 変換されたデータベースオブジェクトを SQL Server に読み込む (SybaseToSQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Loading Converted Database Objects
ms.assetid: 4c59256f-99a8-4351-9559-a455813dbd06
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 5185e8b1364fe2a5bae92c40c99e8f52bcd32ba7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68028931"
---
# <a name="loading-converted-database-objects-into-sql-server-sybasetosql"></a>SQL Server への変換されたデータベース オブジェクトの読み込み (SybaseToSQL)
Sybase Adaptive Server Enterprise (ASE) データベースオブジェクトをまたは SQL Azure に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換した後、結果として得ら[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]れるデータベースオブジェクトをまたは SQL Azure に読み込むことができます。 SSMA を使用してオブジェクトを作成するか、オブジェクトのスクリプトを作成して自分でスクリプトを実行することができます。 また、SSMA では、または SQL Azure データベースの実際の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]内容でターゲットメタデータを更新することもできます。  
  
## <a name="choosing-between-synchronization-and-scripts"></a>同期とスクリプトの選択  
変換されたデータベースオブジェクトを変更せず[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にまたは SQL Azure に読み込む場合は、ssma を使用してデータベースオブジェクトを直接作成または再作成することができます。 このメソッドは短時間で簡単ですが、ストアドプロシージャ以外のオブジェクト[!INCLUDE[tsql](../../includes/tsql-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure オブジェクトを定義するコードをカスタマイズすることはできません。  
  
また[!INCLUDE[tsql](../../includes/tsql-md.md)]は SQL Azure で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクトの作成に使用されるを変更する場合、またはまたは SQL Azure で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクトを作成するタイミングと方法をより細かく制御する場合は、ssma を[!INCLUDE[tsql](../../includes/tsql-md.md)]使用してスクリプトを作成します。 これらのスクリプトを変更し、各オブジェクトを個別に作成して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、または SQL Azure エージェントを使用して、それらのオブジェクトの作成をスケジュールすることもできます。  
  
## <a name="using-ssma-to-load-objects-into-sql-server-or-sql-azure"></a>SSMA を使用して SQL Server または SQL Azure にオブジェクトを読み込む  
SSMA を使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースオブジェクトを作成または SQL Azure するには[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、次の手順に示すように、または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Azure メタデータエクスプローラーでオブジェクトを選択し、オブジェクトをまたは SQL Azure と同期します。 既定では、オブジェクトが既にまた[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は SQL Azure に存在する場合、ssma メタデータの一部のローカルな変更や、それらのオブジェクトの定義に対する更新がある場合、ssma はまたは SQL Azure の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクト定義を変更します。 既定の動作を変更するには、**プロジェクトの設定**を編集します。  
  
> [!NOTE]  
> ASE データベースから変換[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]されなかった既存のデータベースオブジェクトまたは SQL Azure データベースオブジェクトを選択できます。 ただし、これらのオブジェクトは SSMA によって再作成または変更されることはありません。  
  
**SQL Server または SQL Azure とオブジェクトを同期するには**  
  
1.  また[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は SQL Azure メタデータエクスプローラーで、上部[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または [SQL Azure] ノードを展開し、[**データベース**] を展開します。  
  
2.  処理するオブジェクトを選択してください:  
  
    -   データベース全体を同期するには、データベース名の横にあるチェックボックスをオンにします。  
  
    -   個々のオブジェクトまたはオブジェクトのカテゴリを同期または除外するには、オブジェクトまたはフォルダーの横にあるチェックボックスをオンまたはオフにします。  
  
3.  または SQL Azure メタデータエクスプローラーで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]処理するオブジェクトを選択したら、[**データベース**] を右クリックし、[**データベースとの同期**] をクリックします。  
  
    オブジェクトまたはオブジェクトのカテゴリを右クリックし、[**データベースとの同期**] をクリックして、個々のオブジェクトまたはオブジェクトのカテゴリを同期させることもできます。  
  
    その後、SSMA の [**データベースとの同期**] ダイアログボックスが表示され、2つのアイテムのグループが表示されます。 左側の SSMA は、ツリーで表される選択されたデータベースオブジェクトを示しています。 右側には、SSMA メタデータ内の同じオブジェクトを表すツリーが表示されます。 ツリーを展開するには、右または左の [+] ボタンをクリックします。 同期の方向は、2つのツリーの間に配置されたアクション列に表示されます。  
  
    アクションの署名には、次の3つの状態があります。  
  
    -   左矢印は、メタデータの内容がデータベースに保存されることを意味します (既定値)。  
  
    -   右矢印は、データベースの内容が SSMA メタデータを上書きすることを意味します。  
  
    -   クロス署名は、何も実行されないことを意味します。  
  
操作の署名をクリックして、状態を変更します。 実際の同期は、[**データベースとの同期**] ダイアログの [ **OK** ] ボタンをクリックしたときに実行されます。  
  
## <a name="scripting-objects"></a>スクリプトオブジェクト  
変換されたデータベース[!INCLUDE[tsql](../../includes/tsql-md.md)]オブジェクトの定義を保存する場合、またはオブジェクトの定義を変更して自分でスクリプトを実行する場合は、変換され[!INCLUDE[tsql](../../includes/tsql-md.md)]たデータベースオブジェクトの定義をスクリプトに保存できます。  
  
**オブジェクトをスクリプトとして保存するには**  
  
1.  スクリプトに保存するオブジェクトを選択したら、[**データベース**] を右クリックし、[**スクリプトとして保存**] を選択します。  
  
    オブジェクトまたはオブジェクトのカテゴリを右クリックし、[**スクリプトの保存**] を選択して、個々のオブジェクトまたはオブジェクトのカテゴリをスクリプト化することもできます。  
  
2.  [名前を**付けて保存**] ダイアログボックスで、スクリプトを保存するフォルダーに移動し、[**ファイル名**] ボックスにファイル名を入力して、[ **OK**] をクリックします。  
  
    SSMA により、.sql ファイル名拡張子が追加されます。  
  
### <a name="modifying-scripts"></a>スクリプトの変更  
オブジェクトまたは SQL Azure の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]定義を1つ以上のスクリプトとして保存した[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]後、を使用してスクリプトを表示および変更できます。  
  
**スクリプトを変更するには**  
  
1.  
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **[ファイル]** メニューの **[開く]** をポイントし、 **[ファイル]** をクリックします。  
  
2.  [**開く**] ダイアログボックスで、に移動してスクリプトファイルを選択し、[ **OK**] をクリックします。  
  
3.  クエリエディターを使用して、スクリプトファイルを編集します。  
  
    クエリエディターの詳細については、オンラインブックの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 「エディターの便利なコマンドと機能」を参照してください。  
  
4.  スクリプトを保存するには、[ファイル] メニューの [**保存**] をクリックします。  
  
### <a name="running-scripts"></a>スクリプトの実行  
で[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]は、スクリプトまたは個別のステートメントを実行できます。  
  
**スクリプトを実行するには**  
  
1.  
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **[ファイル]** メニューの **[開く]** をポイントし、 **[ファイル]** をクリックします。  
  
2.  [**開く**] ダイアログボックスで、に移動してスクリプトファイルを選択し、[ **OK**] をクリックします。  
  
3.  スクリプト全体を実行するには、 **F5**キーを押します。  
  
4.  一連のステートメントを実行するには、クエリエディターウィンドウでステートメントを選択し、 **F5**キーを押します。  
  
クエリエディターを使用してスクリプトを実行する方法の詳細について[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)]は、オンライン[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ブックの「クエリ」を参照してください。  
  
コマンドラインから**sqlcmd**ユーティリティおよびエージェントから[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スクリプトを実行することもできます。 **Sqlcmd**の詳細については、オンラインブックの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 「sqlcmd ユーティリティ」を参照してください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントの詳細については、オンラインブックの「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]管理タスク (エージェント[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ) の自動化」を参照してください。  
  
## <a name="securing-objects-in-sql-server"></a>SQL Server でのオブジェクトのセキュリティ保護  
変換されたデータベースオブジェクトをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]読み込むと、それらのオブジェクトに対する権限を許可および拒否できます。 これは、データをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行する前に行うことをお勧めします。 で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクトをセキュリティで保護する方法の詳細については、オンラインブックの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 「データベースおよびデータベースアプリケーションのセキュリティに関する考慮事項」を参照してください。  
  
## <a name="next-step"></a>次のステップ  
移行プロセスの次の手順では、 [SYBASE ASE データを SQL Server/SQL Azure (SybaseToSQL) に移行](https://msdn.microsoft.com/54a39f5e-9250-4387-a3ae-eae47c799811)します。  
  
## <a name="see-also"></a>参照  
[Sybase ASE データベースの SQL Server への移行-Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
