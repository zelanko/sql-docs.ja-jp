---
title: Azure SQL DB への接続 (MySQLToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Connecting to SQL Azure, SQL Azure permissions
- Connecting to SQL Azure, synchronization
ms.assetid: d0b6f16a-1880-459d-a0c7-28b7ef15c56a
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 7fb6740681c08cb915755b3362352f139e078c4c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68103189"
---
# <a name="connecting-to-azure-sql-db-mysqltosql"></a>Azure SQL DB への接続 (MySQLToSQL)
MySQL データベースを SQL Azure に移行するには、SQL Azure のターゲットインスタンスに接続する必要があります。 接続すると、SSMA は SQL Azure インスタンス内のすべてのデータベースに関するメタデータを取得し、SQL Azure メタデータエクスプローラーにデータベースのメタデータを表示します。 SSMA は、接続している SQL Azure のインスタンスの情報を格納しますが、パスワードは保存しません。  
  
SQL Azure への接続は、プロジェクトを閉じるまでアクティブなままになります。 プロジェクトを再度開いたときに、サーバーへのアクティブな接続が必要な場合は SQL Azure に再接続する必要があります。 データベースオブジェクトを SQL Azure に読み込んでデータを移行するまで、オフラインで作業することができます。  
  
SQL Azure のインスタンスに関するメタデータは、自動的には同期されません。 代わりに SQL Azure メタデータエクスプローラーでメタデータを更新するには、SQL Azure メタデータを手動で更新する必要があります。 詳細については、このトピックで後述する「SQL Azure メタデータの同期」を参照してください。  
  
## <a name="required-sql-azure-permissions"></a>必要な SQL Azure アクセス許可  
SQL Azure に接続するために使用するアカウントには、アカウントが実行するアクションに応じて、異なるアクセス許可が必要です。  
  
-   MySQL オブジェクトを構文に[!INCLUDE[tsql](../../includes/tsql-md.md)]変換したり、SQL Azure からメタデータを更新したり、変換された構文をスクリプトに保存したりするには、アカウントに SQL Azure のインスタンスにログオンする権限が必要です。  
  
-   データベースオブジェクトを SQL Azure に読み込むには、ターゲットデータベースの**db_owner**データベースロールのメンバーシップである最低限の権限が必要です。  
  
## <a name="establishing-a-sql-azure-connection"></a>SQL Azure 接続の確立  
MySQL データベースオブジェクトを SQL Azure 構文に変換する前に、MySQL データベースを移行する SQL Azure のインスタンスへの接続を確立する必要があります。  
  
接続プロパティを定義するときに、オブジェクトとデータを移行するデータベースも指定します。 このマッピングは、SQL Azure に接続した後に MySQL スキーマレベルでカスタマイズできます。 詳細については、「 [MySQL データベースを SQL Server スキーマ &#40;MySQLToSQL&#41;にマップする](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)」を参照してください。  
  
> [!IMPORTANT]  
> SQL Azure に接続する前に、SQL Azure のインスタンスが実行されていて、接続を受け入れることができることを確認してください。  
  
**SQL Azure に接続するには**  
  
1.  [**ファイル**] メニューの [ **SQL Azure に接続**] を選択します (このオプションは、プロジェクトの作成後に有効になります)。  
  
    以前に SQL Azure に接続している場合は、コマンド名が**SQL Azure に再接続**されます。  
  
2.  [接続] ダイアログボックスで、SQL Azure のサーバー名を入力または選択します。  
  
3.  データベース名を入力、選択、または**参照**します。  
  
4.  [**ユーザー名**] を入力または選択します。  
  
5.  **パスワード**を入力します。  
  
6.  SSMA では、SQL Azure への暗号化接続を推奨しています。  
  
7.  
  **[接続]** をクリックします。  
  
> [!IMPORTANT]  
> SSMA for MySQL は、SQL Azure の**master**データベースへの接続をサポートしていません。  
  
## <a name="synchronizing-sql-azure-metadata"></a>SQL Azure メタデータの同期  
SQL Azure データベースに関するメタデータは自動的に更新されません。 SQL Azure メタデータエクスプローラーのメタデータは、最初に SQL Azure に接続したとき、またはメタデータを手動で更新したときにメタデータのスナップショットになります。 すべてのデータベース、または任意の1つのデータベースまたはデータベースオブジェクトのメタデータを手動で更新できます。  
  
**メタデータを同期するには**  
  
1.  SQL Azure に接続していることを確認します。  
  
2.  SQL Azure メタデータエクスプローラーで、更新するデータベースまたはデータベーススキーマの横にあるチェックボックスをオンにします。  
  
    たとえば、すべてのデータベースのメタデータを更新するには、[データベース] の横にあるチェックボックスをオンにします。  
  
3.  [データベース]、または個々のデータベースまたはデータベーススキーマを右クリックし、[**データベースとの同期**] を選択します。  
  
## <a name="next-step"></a>次のステップ  
移行の次のステップは、プロジェクトのニーズによって異なります。  
  
-   MySQL スキーマと SQL Azure データベースおよびスキーマ間のマッピングをカスタマイズするには、「 [Mysql データベースを SQL Server スキーマ &#40;MySQLToSQL にマッピング](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)する」を参照してください&#41;  
  
-   プロジェクトの構成オプションをカスタマイズするには、「[プロジェクトオプションの設定 &#40;MySQLToSQL](../../ssma/mysql/setting-project-options-mysqltosql.md) 」を参照してください&#41;  
  
-   ソースとターゲットのデータ型のマッピングをカスタマイズするには、「 [MySQL と SQL Server のデータ型 &#40;MySQLToSQL&#41;のマッピング](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)」を参照してください。  
  
-   これらのタスクを実行する必要がない場合は、MySQL データベースオブジェクト定義を SQL Azure オブジェクト定義に変換できます。 詳細については、「 [MySQL データベース &#40;MySQLToSQL の変換](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)」を参照してください&#41;  
  
## <a name="see-also"></a>参照  
[MySQL データベースの SQL Server への移行-Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
