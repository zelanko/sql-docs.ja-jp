---
title: "SQL Server (OracleToSQL) に Oracle のデータの移行 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Oracle Data Migration, Client-Side Migration
- Oracle Data Migration,Server-Side Migration
ms.assetid: e23c5268-41ed-4e55-9fe7-a11376202a13
caps.latest.revision: 13
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 10c7bfea3316146924544a7c76d3bc727006b694
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="migrating-oracle-data-into-sql-server-oracletosql"></a>SQL Server (OracleToSQL) に Oracle のデータの移行
使用して変換されたオブジェクトが正常に同期後[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、Oracle からデータを移行することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
> [!IMPORTANT]  
> 使用されているエンジンがサーバー側のデータ移行のエンジンの場合は、次に、データを移行する前にインストールしてください、SSMA Oracle 拡張機能パックおよび SSMA を実行しているコンピューター上の Oracle プロバイダー。 SQL Server エージェント サービスを実行する必要があります。 拡張機能パックをインストールする方法の詳細については、次を参照してください[サーバー コンポーネントをインストールする」(OracleToSQL)。](http://msdn.microsoft.com/en-us/33070e5f-4e39-4b70-ae81-b8af6e4983c5)  
  
## <a name="setting-migration-options"></a>移行オプションの設定  
移行する前にデータを[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、プロジェクトの移行オプションの確認、**プロジェクト設定** ダイアログ ボックス。  
  
-   このダイアログ ボックスを使用して、移行のバッチ サイズ、テーブルのロック、制約チェック、null 値の処理、および id 値の処理などのオプションを設定できます。 プロジェクトの移行設定の詳細については、次を参照してください。[プロジェクトの設定 (移行) (OracleToSQL)](http://msdn.microsoft.com/en-us/fcd6b988-633b-4b2b-9f36-6368b5e86b60)です。  
  
-   **移行エンジン**で、**プロジェクト設定**ダイアログ ボックスで、次の 2 つの種類のデータ移行のエンジンを使用して、移行プロセスを実行することができます。  
  
    1.  クライアント側のデータ移行のエンジン  
  
    2.  サーバー側のデータ移行のエンジン  
  
**クライアント側のデータの移行:**  
  
-   クライアント側でのデータ移行を開始するには、選択、**クライアント側のデータ移行のエンジン**オプション、**プロジェクト設定** ダイアログ ボックス。  
  
-   **プロジェクト設定**、**クライアント側のデータ移行のエンジン**オプションを設定します。  
  
    > [!NOTE]  
    > **クライアント側のデータ移行エンジン**SSMA アプリケーション内にあるし、は、そのため、拡張機能パックの可用性に依存しません。  
  
**サーバー側のデータの移行:**  
  
-   サーバー側のデータ移行中に、エンジンは、対象のデータベースに存在します。 拡張機能パックによってインストールされます。 拡張機能パックをインストールする方法の詳細については、次を参照してください[SQL サーバー上のサーバー コンポーネントのインストール。](http://msdn.microsoft.com/en-us/33070e5f-4e39-4b70-ae81-b8af6e4983c5)  
  
-   サーバー側での移行を開始するには、選択、**サーバー側のデータ移行のエンジン**オプション、**プロジェクト設定** ダイアログ ボックス。  
  
## <a name="migrating-data-to-sql-server"></a>SQL Server へのデータの移行  
移行データは、Oracle のテーブルから行のデータを移動する一括読み込み操作[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]トランザクション内のテーブルです。 読み込まれた行の数[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]各トランザクションでは、プロジェクトの設定で構成されています。  
  
移行のメッセージを表示するには、出力ウィンドウが表示されているを確認します。 それ以外の場合から、**ビュー**メニューの **出力**です。  
  
**データを移行するには**  
  
1.  次のことを確認します。  
  
    -   Oracle プロバイダーは、SSMA を実行しているコンピューターにインストールされます。  
  
    -   使用して変換されたオブジェクトを同期する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。  
  
2.  Oracle メタデータ エクスプ ローラーで、移行するデータが含まれているオブジェクトを選択します。  
  
    -   すべてのスキーマのデータを移行する場合は、横にチェック ボックスを選択して**スキーマ**です。  
  
    -   データを移行または個々 のテーブルの省略は、最初にスキーマを展開し、**テーブル**を選択するか、テーブルの横にあるチェック ボックスをオフにします。  
  
3.  データを移行するには、2 つのケースが発生します。  
  
    **クライアント側のデータの移行:**  
  
    -   実行するため**クライアント側のデータ移行**、select、**クライアント側のデータ移行のエンジン**オプション、**プロジェクト設定** ダイアログ ボックス。  
  
    **サーバー側のデータの移行:**  
  
    -   サーバー側でデータ移行を実行する前に次のように確認します。  
  
        1.  SSMA for Oracle の拡張機能パックがのインスタンスにインストールされている[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
        2.  SQL Server エージェント サービスは、SQL Server のインスタンスで実行されています。  
  
    -   実行するため**サーバー側のデータ移行**、select、**サーバー側のデータ移行のエンジン**オプション、**プロジェクト設定** ダイアログ ボックス。  
  
4.  右クリック**スキーマ**をクリックして Oracle メタデータ エクスプ ローラーで、**データの移行**です。 個々 のオブジェクトまたはオブジェクトのカテゴリのデータを移行することもできますオブジェクトまたはその親フォルダーを右クリック。選択、**データの移行**オプション。  
  
    > [!NOTE]  
    > SSMA for Oracle の拡張機能パックがのインスタンスにインストールされていないかどうかは[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、場合**サーバー側のデータ移行のエンジン**が選択されている、ターゲット データベースにデータを移行中に、次のエラーが発生しました: ' SSMA データ移行のコンポーネントが見つかりませんでした、SQL Server のサーバー側のデータ移行を実行できなくなります。 拡張機能パックが正しくインストールされているかどうかを確認してください ' です。 をクリックして**キャンセル**データ移行を終了します。  
  
5.  **Connect to Oracle**ダイアログ ボックスで、接続の資格情報を入力し、をクリックして**接続**です。 Oracle への接続の詳細については、次を参照してください[Oracle に接続 &#40;OracleToSQL"&"#41;。](../../ssma/oracle/connect-to-oracle-oracletosql.md)  
  
    ターゲット データベースに接続するため[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]で接続資格情報を入力、 **SQL Server への接続** ダイアログ ボックスをクリック**接続**です。 接続の詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]を参照してください[SQL Server への接続](http://msdn.microsoft.com/en-us/bb8c4bde-cfc2-4636-92ae-5dd24abe9536)  
  
    メッセージが表示、**出力**ウィンドウです。 移行が完了すると、**データ移行レポート**が表示されます。 すべてのデータが移行されない場合、エラーを含む行をクリックし、をクリックして**詳細**です。 レポートが終了したら、をクリックして**閉じる**です。 データ移行のレポートの詳細については、次を参照してください[データ移行レポート (SSMA 共通)。](http://msdn.microsoft.com/en-us/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> SQL Express エディションは、対象データベースとして使用される、クライアント側のデータの移行のみが許可されているし、サーバー側のデータの移行はサポートされていません。  
  
## <a name="see-also"></a>参照  
[SQL Server &#40;OracleToSQL"&"#41; への Oracle データベースの移行](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  

