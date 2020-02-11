---
title: Sybase ASE データを SQL Server に移行する-Azure SQL DB |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Migrating data,Client Side Data Migration
- Migrating data,Server Side Data Migration
ms.assetid: 54a39f5e-9250-4387-a3ae-eae47c799811
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 28a07c08fd801a9d5fdcdde4206f7aa6fe7b926f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68028837"
---
# <a name="migrating-sybase-ase-data-into-sql-server---azure-sql-db--sybasetosql"></a>Sybase ASE データの SQL Server への移行-Azure SQL DB (SybaseToSQL)
Sybase Adaptive Server Enterprise (ASE) データベースオブジェクトをまたは Azure SQL DB に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]正常に読み込むと、ASE からまたは AZURE sql db [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にデータを移行できるようになります。  
  
> [!IMPORTANT]  
> 使用されているエンジンがサーバー側のデータ移行エンジンである場合は、データを移行する前に ssma for Sybase ASE 拡張パックと Sybase ASE プロバイダーを SSMA を実行しているコンピューターにインストールする必要があります。 SQL Server エージェントサービスも実行されている必要があります。 拡張パックをインストールする方法の詳細については、「 [SQL Server での SSMA コンポーネントのインストール (SybaseToSQL)](https://msdn.microsoft.com/5ad9e12c-2cdb-4dd2-8703-05a23242d19d) 」を参照してください。  
  
## <a name="setting-migration-options"></a>移行オプションの設定  
データをまたは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] AZURE SQL DB に移行する前に、[プロジェクトの**設定**] ダイアログボックスの [プロジェクトの移行] オプションを確認してください。  
  
-   このダイアログボックスを使用すると、移行バッチサイズ、テーブルロック、制約チェック、null 値処理、id 値の処理などのオプションを設定できます。 プロジェクトの移行設定の詳細については、「[プロジェクトの設定 (移行) (Sybase)](https://msdn.microsoft.com/82f8857f-7ab1-4738-ab6e-b1e95ea94924)」を参照してください。  
  
    **拡張データ移行設定**の詳細については、「[データ移行の設定](data-migration-settings-sybasetosql.md)」を参照してください。  
  
-   [**プロジェクトの設定**] ダイアログボックスの**移行エンジン**を使用すると、ユーザーは2種類のデータ移行エンジン可視化を使用して移行プロセスを実行できます。  
  
    1.  クライアント側のデータ移行エンジン  
  
    2.  サーバー側のデータ移行エンジン  
  
**クライアント側のデータ移行:**  
  
-   クライアント側でデータの移行を開始するには、[**プロジェクトの設定**] ダイアログボックスで [**クライアント側のデータ移行エンジン**] を選択します。  
  
-   [**プロジェクトの設定**] では、[**クライアント側のデータ移行エンジン**] オプションが既定で設定されています。  
  
    > [!NOTE]  
    > クライアント側のデータ移行エンジンは SSMA アプリケーション内に存在するため、拡張パックの可用性には依存しません。  
  
**サーバー側のデータ移行:**  
  
-   サーバー側のデータの移行中に、エンジンはターゲットデータベースに配置されます。 拡張機能パックを使用してインストールされます。 拡張パックをインストールする方法の詳細については、「 [SQL Server での SSMA コンポーネントのインストール (SybaseToSQL)](https://msdn.microsoft.com/5ad9e12c-2cdb-4dd2-8703-05a23242d19d) 」を参照してください。  
  
-   サーバー側で移行を開始するには、[**プロジェクトの設定**] ダイアログボックスで [**サーバー側のデータ移行エンジン**] オプションを選択します。  
  
> [!NOTE]  
> Azure SQL DB をターゲットデータベースとして使用する場合は、**クライアント側のデータの移行**のみが許可され、サーバー側のデータ移行はサポートされていません。  
  
## <a name="migrating-data-to-sql-server-or-azure-sql-db"></a>SQL Server または Azure SQL DB へのデータの移行  
データの移行は、ASE テーブルからデータの行をトランザクション内の SQL Server テーブルに移動する一括読み込み操作です。 各トランザクションで SQL Server または Azure SQL DB に読み込まれた行の数は、プロジェクトの設定で構成されます。  
  
移行メッセージを表示するには、[出力] ウィンドウが表示されていることを確認します。 それ以外の場合は、[**表示**] メニューの [**出力**] を選択します。  
  
**データを移行するには**  
  
1.  次の点を確認します。  
  
    -   ASE プロバイダーは、SSMA を実行しているコンピューターにインストールされます。  
  
    -   変換されたオブジェクトをターゲットデータベース (SQL Server または Azure SQL DB) と同期している。  
  
2.  Sybase メタデータエクスプローラーで、移行するデータを含むオブジェクトを選択します。  
  
    -   すべてのスキーマのデータを移行するには、[**スキーマ**] の横にあるチェックボックスをオンにします。  
  
    -   データを移行するか、個々のテーブルを省略するには、まずスキーマを展開し、[**テーブル**] を展開して、テーブルの横にあるチェックボックスをオンまたはオフにします。  
  
3.  データを移行するには、次の2つのケースが発生します。  
  
    **クライアント側のデータ移行:**  
  
    **クライアント側のデータ移行**を実行するには、[**プロジェクトの設定**] ダイアログボックスで [**クライアント側のデータ移行エンジン**] オプションを選択します。  
  
    **サーバー側のデータ移行:**  
  
    -   サーバー側のデータ移行を実行する前に、次のことを確認してください。  
  
        1.  SSMA for Sybase 拡張パックは SQL Server のインスタンスにインストールされます。  
  
        2.  のインスタンスで SQL Server エージェントサービスが実行されてい SQL Server  
  
    -   **サーバー側のデータ移行**を実行するには、[**プロジェクトの設定**] ダイアログボックスで [**サーバー側のデータ移行エンジン**] オプションを選択します。  
  
4.  Sybase メタデータエクスプローラーで [**スキーマ**] を右クリックし、[**データの移行**] をクリックします。 また、個々のオブジェクトまたはオブジェクトのカテゴリのデータを移行することもできます。オブジェクトまたはその親フォルダーを右クリックし、[**データの移行**] オプションを選択します。  
  
    > [!NOTE]  
    > SSMA for Sybase 拡張パックが SQL Server のインスタンスにインストールされておらず、**サーバー側のデータ移行エンジン**が選択されている場合、ターゲットデータベースへのデータの移行中に、次のエラーが発生します。 "Ssma データ移行コンポーネントが SQL Server で見つからなかったため、サーバー側のデータ移行は実行できません。 拡張パックが正しくインストールされているかどうかを確認してください。 [**キャンセル**] をクリックして、データ移行を終了します。  
  
5.  [ **SYBASE ASE への接続**] ダイアログボックスで、接続の資格情報を入力し、[**接続**] をクリックします。 Sybase ASE への接続の詳細については、「 [Connect To sybase &#40;SybaseToSQL&#41;](../../ssma/sybase/connect-to-sybase-sybasetosql.md) 」を参照してください。  
  
    ターゲットデータベースが SQL Server 場合は、[ **SQL Server への接続**] ダイアログボックスで接続資格情報を入力し、[**接続**] をクリックします。 SQL Server に接続する方法の詳細については、「 [SQL Server への接続 (SybaseToSQL)](https://msdn.microsoft.com/dd368a1a-45b0-40e9-b4d3-5cdb48c26606) 」を参照してください。  
  
    ターゲットデータベースが Azure SQL DB の場合は、[ **AZURE SQL db への接続**] ダイアログボックスで接続資格情報を入力し、[**接続**] をクリックします。 Azure SQL DB への接続の詳細については、「 [AZURE SQL db への接続 &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md) 」を参照してください。  
  
    メッセージが [**出力**] ウィンドウに表示されます。 移行が完了すると、**データ移行レポート**が表示されます。 データが移行されなかった場合は、エラーが含まれている行をクリックし、[**詳細**] をクリックします。 レポートの作成が完了したら、[**閉じる**] をクリックします。 データ移行レポートの詳細については、「[データ移行レポート (SSMA Common)](https://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241) 」を参照してください。  
  
> [!NOTE]  
> ターゲットデータベースとして SQL Express edition を使用すると、クライアント側のデータの移行のみが許可され、サーバー側のデータ移行はサポートされません。  
  
## <a name="see-also"></a>参照  
[Sybase ASE データベースの SQL Server への移行-Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
