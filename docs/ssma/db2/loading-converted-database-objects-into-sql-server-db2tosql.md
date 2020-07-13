---
title: 変換されたデータベースオブジェクトを SQL Server に読み込んでいます (DB2ToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f4ea1ced-9f9f-4a9d-88ab-81dbab64adc3
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 7af5566094c9cc4c40ba2aa33f27e79bae1c7445
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68141033"
---
# <a name="loading-converted-database-objects-into-sql-server-db2tosql"></a>変換されたデータベースオブジェクトを SQL Server に読み込んでいます (DB2ToSQL)
DB2 スキーマをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換した後、結果と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]して得られるデータベースオブジェクトをに読み込むことができます。 SSMA を使用してオブジェクトを作成するか、オブジェクトのスクリプトを作成して自分でスクリプトを実行することができます。 また、SSMA では、ターゲットメタデータをデータベースの実際[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の内容で更新することもできます。  
  
## <a name="choosing-between-synchronization-and-scripts"></a>同期とスクリプトの選択  
変換されたデータベースオブジェクトを変更せず[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にに読み込む場合は、ssma によってデータベースオブジェクトを直接作成または再作成することができます。 このメソッドは短時間で簡単ですが、ストアドプロシージャ以外の[!INCLUDE[tsql](../../includes/tsql-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクトを定義するコードをカスタマイズすることはできません。  
  
オブジェクトの作成に使用さ[!INCLUDE[tsql](../../includes/tsql-md.md)]れるを変更する場合、またはオブジェクトの作成をより細かく制御する場合は、ssma を使用してスクリプトを作成します。 その後、これらのスクリプトを変更し、各オブジェクトを個別に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]作成して、エージェントを使用してそれらのオブジェクトの作成をスケジュールすることもできます。  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>SSMA を使用してオブジェクトを SQL Server と同期させる  
SSMA を使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースオブジェクトを作成するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]次の手順に示すように、メタ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データエクスプローラーでオブジェクトを選択し、オブジェクトをと同期します。 既定では、オブジェクトが既にに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]存在しており、ssma メタデータがの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクトより新しい場合、ssma によっての[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクト定義が変更されます。 既定の動作を変更するには、**プロジェクトの設定**を編集します。  
  
> [!NOTE]  
> DB2 データベースから変換[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]されなかった既存のデータベースオブジェクトを選択できます。 ただし、これらのオブジェクトは SSMA によって再作成または変更されることはありません。  
  
**オブジェクトを SQL Server と同期するには**  
  
1.  メタ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データエクスプローラーで、最上位[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ノードを展開し、[**データベース**] を展開します。  
  
2.  処理するオブジェクトを選択してください:  
  
    -   データベース全体を同期するには、データベース名の横にあるチェックボックスをオンにします。  
  
    -   個々のオブジェクトまたはオブジェクトのカテゴリを同期または除外するには、オブジェクトまたはフォルダーの横にあるチェックボックスをオンまたはオフにします。  
  
3.  メタデータエクスプローラーで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]処理するオブジェクトを選択したら、[**データベース**] を右クリックし、[**データベースとの同期**] をクリックします。  
  
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
  
2.  [名前を**付けて保存**] ダイアログボックスで、スクリプトを保存するフォルダーに移動し、[**ファイル名**] ボックスにファイル名を入力[!INCLUDE[clickOK](../../includes/clickok-md.md)]して、をクリックします。 SSMA により、.sql ファイル名拡張子が追加されます。  
  
### <a name="modifying-scripts"></a>スクリプトの変更  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクト定義を1つ以上のスクリプトとして保存した後、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してスクリプトを表示および変更できます。  
  
**スクリプトを変更するには**  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **[ファイル]** メニューの **[開く]** をポイントし、 **[ファイル]** をクリックします。  
  
2.  [**開く**] ダイアログボックスで、スクリプトファイルを選択し、[OK] をクリックします。
  
3.  クエリエディターを使用して、スクリプトファイルを編集します。  
  
    クエリエディターの詳細については、オンラインブックの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 「エディターの便利なコマンドと機能」を参照してください。  
  
4.  スクリプトを保存するには、[ファイル] メニューの [**保存**] をクリックします。  
  
### <a name="running-scripts"></a>スクリプトの実行  
で[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]は、スクリプトまたは個別のステートメントを実行できます。  
  
**スクリプトを実行するには**  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **[ファイル]** メニューの **[開く]** をポイントし、 **[ファイル]** をクリックします。  
  
2.  [**開く**] ダイアログボックスで、スクリプトファイルを選択し、[!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
3.  スクリプト全体を実行するには、 **F5**キーを押します。  
  
4.  一連のステートメントを実行するには、クエリエディターウィンドウでステートメントを選択し、 **F5**キーを押します。  
  
クエリエディターを使用してスクリプトを実行する方法の詳細について[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)]は、オンライン[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ブックの「クエリ」を参照してください。  
  
また、 **sqlcmd**ユーティリティを使用してコマンドラインからスクリプトを実行したり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントからスクリプトを実行したりすることもできます。 **Sqlcmd**の詳細については、オンラインブックの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 「sqlcmd ユーティリティ」を参照してください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントの詳細については、オンラインブックの「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]管理タスク (エージェント[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ) の自動化」を参照してください。  
  
## <a name="securing-objects-in-sql-server"></a>SQL Server でのオブジェクトのセキュリティ保護  
変換されたデータベースオブジェクトをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]読み込むと、それらのオブジェクトに対する権限を許可および拒否できます。 これは、データをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行する前に行うことをお勧めします。 で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクトをセキュリティで保護する方法の詳細については、オンラインブックの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 「データベースおよびデータベースアプリケーションのセキュリティに関する考慮事項」を参照してください。  
  
## <a name="next-step"></a>次の手順  
移行プロセスの次の手順は、 [DB2 データを SQL Server に移行](https://msdn.microsoft.com/86cbd39f-6dac-409a-9ce1-7dd54403f84b)することです。  
  
## <a name="see-also"></a>参照  
[DB2 データの SQL Server &#40;DB2ToSQL&#41;への移行](../../ssma/db2/migrating-db2-data-into-sql-server-db2tosql.md)  
  
