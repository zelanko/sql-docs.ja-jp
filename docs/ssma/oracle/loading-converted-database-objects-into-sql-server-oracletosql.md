---
title: 変換されたデータベースオブジェクトを SQL Server に読み込んでいます (OracleToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Synchronization, Securing Objects in SQL Server
- Synchronization,Scripting Objects
ms.assetid: a8ae33b2-1883-4785-922b-ea0e31c0b37a
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 97c34beb0cbe27e8d3c88b922690dc369fb7103b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68262989"
---
# <a name="loading-converted-database-objects-into-sql-server-oracletosql"></a>SQL Server への変換されたデータベース オブジェクトの読み込み (OracleToSQL)
Oracle スキーマを SQL Server に変換した後、結果として得られるデータベースオブジェクトを SQL Server に読み込むことができます。 SSMA を使用してオブジェクトを作成するか、オブジェクトのスクリプトを作成して自分でスクリプトを実行することができます。 また、SSMA では、SQL Server データベースの実際の内容でターゲットメタデータを更新することもできます。  
  
## <a name="choosing-between-synchronization-and-scripts"></a>同期とスクリプトの選択  
変換されたデータベースオブジェクトを変更せずに SQL Server に読み込む場合は、SSMA を使用してデータベースオブジェクトを直接作成または再作成することができます。 このメソッドは短時間で簡単ですが、ストアドプロシージャ以外の SQL Server [!INCLUDE[tsql](../../includes/tsql-md.md)]オブジェクトを定義するコードをカスタマイズすることはできません。  
  
オブジェクトの作成に使用さ[!INCLUDE[tsql](../../includes/tsql-md.md)]れるを変更する場合、またはオブジェクトの作成をより細かく制御する場合は、ssma を使用してスクリプトを作成します。 その後、これらのスクリプトを変更し、各オブジェクトを個別に作成し、SQL Server エージェントを使用してそれらのオブジェクトの作成をスケジュールすることもできます。  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>SSMA を使用してオブジェクトを SQL Server と同期させる  
SSMA を使用して SQL Server データベースオブジェクトを作成するには SQL Server メタデータエクスプローラーでオブジェクトを選択し、次の手順に示すように、オブジェクトを SQL Server と同期します。 既定では、オブジェクトが既に SQL Server に存在し、SSMA メタデータが SQL Server のオブジェクトより新しい場合、SSMA は SQL Server 内のオブジェクト定義を変更します。 既定の動作を変更するには、**プロジェクトの設定**を編集します。  
  
> [!NOTE]  
> Oracle データベースから変換されていない既存の SQL Server データベースオブジェクトを選択できます。 ただし、これらのオブジェクトは SSMA によって再作成または変更されることはありません。  
  
**オブジェクトを SQL Server と同期するには**  
  
1.  SQL Server メタデータエクスプローラーで、上部の SQL Server] ノードを展開し、[**データベース**] を展開します。  
  
2.  処理するオブジェクトを選択してください:  
  
    -   データベース全体を同期するには、データベース名の横にあるチェックボックスをオンにします。  
  
    -   個々のオブジェクトまたはオブジェクトのカテゴリを同期または除外するには、オブジェクトまたはフォルダーの横にあるチェックボックスをオンまたはオフにします。  
  
3.  SQL Server メタデータエクスプローラーで処理するオブジェクトを選択したら、[**データベース**] を右クリックし、[**データベースとの同期**] をクリックします。  
  
    オブジェクトまたはオブジェクトのカテゴリを右クリックし、[**データベースとの同期**] をクリックして、個々のオブジェクトまたはオブジェクトのカテゴリを同期させることもできます。  
  
    その後、SSMA の [**データベースとの同期**] ダイアログボックスが表示され、2つのアイテムのグループが表示されます。 左側の SSMA は、ツリーで表される選択されたデータベースオブジェクトを示しています。 右側には、SSMA メタデータ内の同じオブジェクトを表すツリーが表示されます。 ツリーを展開するには、右または左の [+] ボタンをクリックします。 同期の方向は、2つのツリーの間に配置されたアクション列に表示されます。  
  
    アクションの署名には、次の3つの状態があります。  
  
    -   左矢印は、メタデータの内容がデータベースに保存されることを意味します (既定値)。  
  
    -   右矢印は、データベースの内容が SSMA メタデータを上書きすることを意味します。  
  
    -   クロス署名は、何も実行されないことを意味します。  
  
操作の署名をクリックして、状態を変更します。 実際の同期は、[**データベースとの同期**] ダイアログの [ **OK** ] ボタンをクリックしたときに実行されます。  
  
## <a name="scripting-objects"></a>スクリプトオブジェクト  
変換さ[!INCLUDE[tsql](../../includes/tsql-md.md)]れたデータベースオブジェクトの定義を保存する、またはオブジェクトの定義を変更してスクリプトを実行するには、変換[!INCLUDE[tsql](../../includes/tsql-md.md)]されたデータベースオブジェクトの定義をスクリプトに保存します。  
  
**オブジェクトをスクリプトとして保存するには**  
  
1.  スクリプトに保存するオブジェクトを選択したら、[**データベース**] を右クリックし、[**スクリプトとして保存**] をクリックします。  
  
    オブジェクトまたはその親フォルダーを右クリックし、[**スクリプトとして保存**] をクリックして、個々のオブジェクトまたはオブジェクトのカテゴリをスクリプト化することもできます。  
  
2.  [名前を付け**て保存**] ダイアログボックスで、スクリプトを保存するフォルダーに移動し、[**ファイル名**] ボックスにファイル名を入力して、[OK] をクリックすると、.sql ファイル名拡張子が追加されます。  
  
### <a name="modifying-scripts"></a>スクリプトの変更  
SQL Server オブジェクトの定義を1つ以上のスクリプトとして保存した後[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、を使用してスクリプトを表示および変更できます。  
  
**スクリプトを変更するには**  
  
1.  
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **[ファイル]** メニューの **[開く]** をポイントし、 **[ファイル]** をクリックします。  
  
2.  [**開く**] ダイアログボックスで、スクリプトファイルを選択し、[OK] をクリックします。
  
3.  クエリエディターを使用して、スクリプトファイルを編集します。  
  
    クエリエディターの詳細については、SQL Server オンラインブックの「エディターの便利なコマンドと機能」を参照してください。  
  
4.  スクリプトを保存するには、[ファイル] メニューの [**保存**] をクリックします。  
  
### <a name="running-scripts"></a>スクリプトの実行  
で[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]は、スクリプトまたは個別のステートメントを実行できます。  
  
**スクリプトを実行するには**  
  
1.  
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **[ファイル]** メニューの **[開く]** をポイントし、 **[ファイル]** をクリックします。  
  
2.  [**開く**] ダイアログボックスで、スクリプトファイルを選択し、[OK] をクリックします。  
  
3.  スクリプト全体を実行するには、 **F5**キーを押します。  
  
4.  一連のステートメントを実行するには、クエリエディターウィンドウでステートメントを選択し、 **F5**キーを押します。  
  
クエリエディターを使用してスクリプトを実行する方法の詳細について[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)]は、SQL Server オンラインブックの「クエリ」を参照してください。  
  
また、 **sqlcmd**ユーティリティおよび SQL Server エージェントからスクリプトを実行することもできます。 **Sqlcmd**の詳細については、SQL Server オンラインブックの「sqlcmd ユーティリティ」を参照してください。 SQL Server エージェントの詳細については、SQL Server オンラインブックの「管理タスクの自動化 (SQL Server エージェント)」を参照してください。  
  
## <a name="securing-objects-in-sql-server"></a>SQL Server でのオブジェクトのセキュリティ保護  
変換されたデータベースオブジェクトを SQL Server に読み込むと、それらのオブジェクトに対する権限を許可したり拒否したりできます。 SQL Server にデータを移行する前に、これを行うことをお勧めします。 SQL Server でオブジェクトをセキュリティで保護する方法の詳細については、「SQL Server オンラインブック」の「データベースとデータベースアプリケーションのセキュリティに関する考慮事項」を参照してください。  
  
## <a name="next-step"></a>次のステップ  
移行プロセスの次の手順では、 [SQL Server にデータを移行](migrating-oracle-data-into-sql-server-oracletosql.md)します。  
  
## <a name="see-also"></a>参照  
[Oracle データベースの SQL Server &#40;OracleToSQL&#41;への移行](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
