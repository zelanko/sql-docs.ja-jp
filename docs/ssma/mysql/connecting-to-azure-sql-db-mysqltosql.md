---
title: Azure SQL DB (MySQLToSQL) への接続 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Connecting to SQL Azure, SQL Azure permissions
- Connecting to SQL Azure, synchronization
ms.assetid: d0b6f16a-1880-459d-a0c7-28b7ef15c56a
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: bb49a6e0604fd3bd713857bab18cde30804b0f42
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-to-azure-sql-db-mysqltosql"></a>Azure SQL DB (MySQLToSQL) に接続します。
MySQL データベースを SQL Azure に移行するには、SQL Azure のターゲット インスタンスに接続する必要があります。 接続するときに、SSMA は SQL Azure のインスタンス内のすべてのデータベースに関するメタデータを取得し、SQL Azure メタデータ エクスプ ローラーでデータベースのメタデータを表示します。 SSMA は、SQL Azure に接続しているが、パスワードを保存しないのインスタンスの情報を格納します。  
  
プロジェクトを閉じるまで、SQL Azure への接続がアクティブな保たれます。 プロジェクトを再度開くと、アクティブなサーバーに接続する場合 SQL Azure に再接続する必要があります。 SQL Azure にデータベース オブジェクトを読み込むし、データを移行するまで、オフライン作業できます。  
  
SQL Azure のインスタンスに関するメタデータが自動的に同期されていません。 代わりに、SQL Azure メタデータ エクスプ ローラー内のメタデータを更新するには、SQL Azure メタデータを手動で更新する必要があります。 詳細については、このトピックの「SQL Azure メタデータの同期」のセクションを参照してください。  
  
## <a name="required-sql-azure-permissions"></a>必要な SQL Azure の権限  
SQL Azure への接続に使用されるアカウントには、アカウントが実行する操作に応じて異なるアクセス許可が必要です。  
  
-   MySQL オブジェクトに変換する[!INCLUDE[tsql](../../includes/tsql_md.md)]スクリプトの構文は、SQL Azure からのメタデータを更新するかに変換された構文を保存する、アカウントに SQL Azure のインスタンスにログオンする権限が必要です。  
  
-   データベース オブジェクトを SQL Azure に読み込むには、最小限のアクセス許可の要件はメンバーシップ、 **db_owner**ターゲット データベースのデータベース ロール。  
  
## <a name="establishing-a-sql-azure-connection"></a>SQL を確立する Azure の接続  
MySQL データベースのオブジェクトを SQL Azure の構文に変換する前に、または複数の MySQL データベースを移行する SQL Azure のインスタンスへの接続を確立する必要があります。  
  
接続のプロパティを定義するときは、オブジェクトとデータを移行するデータベースを指定します。 SQL Azure に接続した後、MySQL スキーマ レベルでは、このマッピングをカスタマイズすることができます。 詳細については、次を参照してください[MySQL データベースを SQL Server スキーマへのマッピング&#40;MySQLToSQL。&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
> [!IMPORTANT]  
> SQL Azure に接続しようとすると、前に、SQL Azure のインスタンスを実行しているし、接続を受け入れることを確認してください。  
  
**SQL Azure に接続するには**  
  
1.  **ファイル**メニューの  **SQL Azure への接続**(プロジェクトの作成後にこのオプションは有効です)。  
  
    SQL Azure に以前接続した場合、コマンド名になります**SQL Azure への再接続**です。  
  
2.  接続ダイアログ ボックスで入力または SQL Azure のサーバー名を選択します。  
  
3.  入力を選択または**参照**データベース名。  
  
4.  入力または選択**UserName**です。  
  
5.  入力、**パスワード**です。  
  
6.  SSMA は、SQL Azure に暗号化された接続をお勧めします。  
  
7.  **[接続]** をクリックします。  
  
> [!IMPORTANT]  
> SSMA for MySQL がへの接続をサポートしていません**マスター** SQL Azure でのデータベースです。  
  
## <a name="synchronizing-sql-azure-metadata"></a>同期 SQL Azure メタデータ  
SQL Azure データベースについてのメタデータは自動的に更新されません。 SQL Azure メタデータ エクスプ ローラー内のメタデータは、まず SQL Azure に接続されているか、前回を手動でときのメタデータのスナップショットには、メタデータが更新されました。 すべてのデータベース、または任意の 1 つのデータベースまたはデータベース オブジェクトのメタデータを手動で更新することができます。  
  
**メタデータを同期するには**  
  
1.  SQL Azure に接続していることを確認します。  
  
2.  SQL Azure メタデータ エクスプ ローラーで、データベースまたは更新するデータベース スキーマの横にあるチェック ボックスを選択します。  
  
    たとえば、すべてのデータベースのメタデータを更新するには、データベースの横にあるボックスを選択します。  
  
3.  データベース、または個々 のデータベースまたはデータベース スキーマを右クリックし **データベースと同期する**です。  
  
## <a name="next-step"></a>次の手順  
次の手順では、プロジェクトのニーズによって異なります。  
  
-   MySQL スキーマと SQL Azure データベースとスキーマの間のマッピングをカスタマイズするを参照してください[SQL Server スキーマへのマッピングの MySQL データベース&#40;MySQLToSQL。&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
-   プロジェクトの構成オプションをカスタマイズするを参照してください[プロジェクト オプションの設定&#40;MySQLToSQL。&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md)  
  
-   ソースとターゲットのデータ型のマッピングをカスタマイズするを参照してください[マッピング MySQL および SQL Server データ型&#40;MySQLToSQL。&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
-   場合は、次のタスクを実行する必要はありません、MySQL データベースのオブジェクトの定義を SQL Azure オブジェクトの定義に変換できます。 詳細については、次を参照してください[MySQL データベースを変換する&#40;MySQLToSQL。&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL DB にデータベースを移行する MySQL &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
