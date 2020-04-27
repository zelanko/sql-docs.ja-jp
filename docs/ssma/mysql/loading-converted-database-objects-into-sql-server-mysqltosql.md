---
title: 変換されたデータベースオブジェクトを SQL Server に読み込んでいます (MySQLToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: ac993a6d-0283-4823-8793-6b217677dfa3
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: a6966209300e6959e7ba9cb1afa11eb42b855d82
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67909012"
---
# <a name="loading-converted-database-objects-into-sql-server-mysqltosql"></a>SQL Server への変換されたデータベース オブジェクトの読み込み (MySQLToSQL)
MySQL データベースをまたは SQL Azure に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換した後、結果として得ら[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]れるデータベースオブジェクトをまたは SQL Azure に読み込むことができます。 SSMA を使用してオブジェクトを作成するか、オブジェクトのスクリプトを作成して自分でスクリプトを実行することができます。 また、SSMA では、または SQL Azure データベースの実際の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]内容でターゲットメタデータを更新することもできます。  
  
## <a name="choosing-between-synchronization-and-scripts"></a>同期とスクリプトの選択  
変換されたデータベースオブジェクトを変更せず[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にまたは SQL Azure に読み込む場合は、ssma を使用してデータベースオブジェクトを直接作成または再作成することができます。 この方法は短時間で簡単ですが、オブジェクト[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure オブジェクトを定義する transact-sql コードをカスタマイズすることはできません。  
  
オブジェクトの作成に使用される Transact-sql を変更する場合、またはオブジェクトの作成をより細かく制御する場合は、SSMA を使用してスクリプトを作成します。 これらのスクリプトを変更し、各オブジェクトを個別に作成し、SQL Server エージェントを使用してこれらのオブジェクトの作成をスケジュールすることもできます。  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>SSMA を使用してオブジェクトを SQL Server と同期させる  
SSMA を使用して SQL Server または SQL Azure データベースオブジェクトを作成するには[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、または SQL Azure メタデータエクスプローラーでオブジェクトを選択[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]し、次の手順に示すように、または SQL Azure を使用してオブジェクトを同期します。 既定では、オブジェクトが既にまた[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は SQL Azure に存在する場合、ssma メタデータの一部のローカルな変更や、それらのオブジェクトの定義に対する更新がある場合、ssma はまたは SQL Azure の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクト定義を変更します。 既定の動作を変更するには、**プロジェクトの設定**を編集します。  
  
> [!NOTE]  
> MySQL データベースから変換[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]されなかった既存のデータベースオブジェクトまたは SQL Azure データベースオブジェクトを選択できます。 ただし、これらのオブジェクトは SSMA によって再作成または変更されることはありません。  
  
##### <a name="to-synchronize-objects-with-sql-server-or-sql-azure"></a>SQL Server または SQL Azure とオブジェクトを同期するには  
  
1.  また[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は SQL Azure メタデータエクスプローラーで、上部[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または [SQL Azure] ノードを展開し、[**データベース**] を展開します。  
  
2.  処理するオブジェクトを選択してください:  
  
    -   データベース全体を同期するには、データベース名の横にあるチェックボックスをオンにします。  
  
    -   個々のオブジェクトまたはオブジェクトのカテゴリを同期または除外するには、オブジェクトまたはフォルダーの横にあるチェックボックスをオンまたはオフにします。  
  
3.  SQL Server または SQL Azure メタデータエクスプローラーで処理するオブジェクトを選択したら、[**データベース**] を右クリックし、[**データベースとの同期**] をクリックします。  
  
    オブジェクトまたはオブジェクトのカテゴリを右クリックし、[**データベースとの同期**] をクリックして、個々のオブジェクトまたはオブジェクトのカテゴリを同期させることもできます。  
  
    その後、SSMA の [**データベースとの同期**] ダイアログボックスが表示され、2つのアイテムのグループが表示されます。 左側の SSMA は、ツリーで表される選択されたデータベースオブジェクトを示しています。 右側には、SSMA メタデータ内の同じオブジェクトを表すツリーが表示されます。 ツリーを展開するには、右または左の [+] ボタンをクリックします。 同期の方向は、2つのツリーの間に配置されたアクション列に表示されます。  
  
    アクションの署名には、次の3つの状態があります。  
  
    -   左矢印は、メタデータの内容がデータベースに保存されることを意味します (既定値)。  
  
    -   右矢印は、データベースの内容が SSMA メタデータを上書きすることを意味します。  
  
    -   クロス署名は、何も実行されないことを意味します。  
  
    -   操作の署名をクリックして、状態を変更します。 実際の同期は、[**データベースとの同期**] ダイアログの [ **OK** ] ボタンをクリックしたときに実行されます。  
  
## <a name="scripting-objects"></a>スクリプトオブジェクト  
変換さ[!INCLUDE[tsql](../../includes/tsql-md.md)]れたデータベースオブジェクトの定義を保存する、またはオブジェクトの定義を変更してスクリプトを実行するには、変換[!INCLUDE[tsql](../../includes/tsql-md.md)]されたデータベースオブジェクトの定義をスクリプトに保存します。  
  
**オブジェクトをスクリプトとして保存するには**  
  
1.  スクリプトに保存するオブジェクトを選択したら、[**データベース**] を右クリックし、[**スクリプトとして保存**] をクリックします。  
  
    オブジェクトまたはその親フォルダーを右クリックし、[**スクリプトとして保存**] をクリックして、個々のオブジェクトまたはオブジェクトのカテゴリをスクリプト化することもできます。  
  
2.  [名前を**付けて保存**] ダイアログボックスで、スクリプトを保存するフォルダーに移動し、[ [!INCLUDE[clickOK](../../includes/clickok-md.md)] **ファイル名**] ボックスにファイル名を入力すると、ssma によって .sql ファイル名拡張子が追加されます。  
  
### <a name="modifying-scripts"></a>スクリプトの変更  
SQL Server または SQL Azure オブジェクトの定義をスクリプトとして保存した後、SQL Server Management Studio を使用してスクリプトを変更できます。  
  
**スクリプトを変更するには**  
  
1.  [Management Studio**ファイル**] メニューの [**開く**] をポイントし、[**ファイル**] をクリックします。  
  
2.  [開く] ダイアログボックスで、スクリプトファイルを探して選択し、[ **OK**] をクリックします。  
  
3.  クエリエディターを使用して、スクリプトファイルを編集します。クエリエディターの詳細については、SQL Server オンラインブックの「エディターの便利なコマンドと機能」を参照してください。  
  
4.  スクリプトを保存するには、[ファイル] メニューの [**保存**] をクリックします。  
  
### <a name="running-scripts"></a>スクリプトの実行  
SQL Server Management Studio では、スクリプトまたは個別のステートメントを実行できます。  
  
**スクリプトを実行するには**  
  
1.  [SQL Server Management Studio**ファイル**] メニューの [**開く**] をポイントし、[**ファイル**] をクリックします。  
  
2.  [開く] ダイアログボックスで、スクリプトファイルを探して選択し、[ **OK**] をクリックします。  
  
3.  スクリプト全体を実行するには、 **F5**キーを押します。  
  
4.  一連のステートメントを実行するには、クエリエディターウィンドウでステートメントを選択し、 **F5**キーを押します。  
  
5.  クエリエディターを使用してスクリプトを実行する方法の詳細については、「SQL Server オンラインブック」の「Transact-sql クエリの SQL Server Management Studio」を参照してください。  
  
6.  また、 **sqlcmd**ユーティリティを使用してコマンドラインからスクリプトを実行したり、SQL Server エージェントからスクリプトを実行したりすることもできます。 **Sqlcmd**の詳細については、SQL Server オンラインブックの「sqlcmd ユーティリティ」を参照してください。 SQL Server エージェントの詳細については、SQL Server オンラインブックの「管理タスクの自動化 (SQL Server エージェント)」を参照してください。  
  
## <a name="securing-objects-in-sql-server"></a>SQL Server でのオブジェクトのセキュリティ保護  
変換されたデータベースオブジェクトを SQL Server に読み込むと、これらのオブジェクトに対する権限を許可したり拒否したりできます。 SQL Server にデータを移行する前に、これを行うことをお勧めします。 SQL Server でオブジェクトをセキュリティで保護する方法の詳細については、「SQL Server オンラインブック」の「データベースとデータベースアプリケーションのセキュリティに関する考慮事項」を参照してください。  
  
## <a name="next-step"></a>次の手順  
移行プロセスの次のステップでは、 [MySQL データを SQL Server に移行します。 AZURE SQL DB &#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
## <a name="see-also"></a>参照  
[MySQL データベースの SQL Server への移行-Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
