---
title: "Azure SQL DB (AccessToSQL) への接続 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- instance of SQL Azure
- metadata, refreshing
- refreshing metadata
- SQL Azure
- SQL Azure, connecting
- SQL Azure, connecting to
- SQL Azure, reconnecting
- SQL Azure, synchronizing metadata
ms.assetid: 1ba0d113-dc05-4431-8689-e14a8821bafd
caps.latest.revision: 21
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: dd42d05f0a5521b9e64742222147f584a2aaf518
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="connecting-to-azure-sql-db-accesstosql"></a>Azure SQL DB (AccessToSQL) に接続します。
Access データベースを SQL Azure に移行するには、SQL Azure のターゲット インスタンスに接続する必要があります。 接続するときに、SSMA は SQL Azure のインスタンス内のすべてのデータベースに関するメタデータを取得し、SQL Azure メタデータ エクスプ ローラーでデータベースのメタデータを表示します。 SSMA では、SQL Azure のインスタンスについてに接続しているがパスワードを保存しない情報を格納します。  
  
プロジェクトを閉じるまで、SQL Azure への接続がアクティブな保たれます。 プロジェクトを再度開くと、アクティブなサーバーに接続する場合 SQL Azure に再接続する必要があります。 SQL Azure にデータベース オブジェクトを読み込むし、データを移行するまで、オフライン作業できます。  
  
SQL Azure のインスタンスに関するメタデータが自動的に同期されていません。 代わりに、SQL Azure メタデータ エクスプ ローラー内のメタデータを更新するには、SQL Azure メタデータを手動で更新する必要があります。 詳細については、このトピックの「SQL Azure メタデータの同期」のセクションを参照してください。  
  
## <a name="required-sql-azure-permissions"></a>必要な SQL Azure の権限  
SQL Azure への接続に使用されるアカウントには、アカウントが実行する操作に応じて異なるアクセス許可が必要です。  
  
-   アクセス オブジェクトに変換する[!INCLUDE[tsql](../../includes/tsql_md.md)]スクリプトの構文は、SQL Azure からのメタデータを更新するかに変換された構文を保存する、アカウントに SQL Azure のインスタンスにログオンする権限が必要です。  
  
-   データベース オブジェクトを SQL Azure に読み込むには、最小限のアクセス許可の要件はメンバーシップ、 **db_owner**ターゲット データベースのデータベース ロール。  
  
## <a name="establishing-a-sql-azure-connection"></a>SQL を確立する Azure の接続  
データベース オブジェクトへのアクセスを SQL Azure の構文に変換する前に、Access データベースまたはデータベースを移行する SQL Azure のインスタンスへの接続を確立する必要があります。  
  
接続のプロパティを定義するときは、オブジェクトとデータを移行するデータベースを指定します。 SQL Azure に接続した後は、アクセス、スキーマ レベルでは、このマッピングをカスタマイズできます。 詳細については、次を参照してください[Access データベースを SQL Server スキーマへのマッピング。](http://msdn.microsoft.com/en-us/69bee937-7b2c-49ee-8866-7518c683fad4)  
  
> [!IMPORTANT]  
> SQL Azure に接続しようとすると、前に、SQL Azure のインスタンスを実行しているし、接続を受け入れることを確認してください。  
  
**SQL Azure に接続するには**  
  
1.  **ファイル**メニューの  **SQL Azure への接続**(プロジェクトの作成後にこのオプションは有効です)。  
  
    SQL Azure に接続されていた場合、コマンド名になります**SQL Azure への再接続**です。  
  
2.  接続ダイアログ ボックスで入力または SQL Azure のサーバー名を選択します。  
  
3.  入力を選択または**参照**データベース名。  
  
4.  入力または選択**UserName**です。  
  
5.  入力、**パスワード**です。  
  
6.  SSMA は、SQL Azure に暗号化された接続をお勧めします。  
  
7.  **[接続]**をクリックします。  
  
> [!IMPORTANT]  
> SSMA のアクセスがへの接続をサポートしていません**マスター** SQL Azure でのデータベースです。  
  
使用して最初にデータベースを作成するには SQL Azure アカウントでは、データベースはなく場合、 **Azure データベースの作成**のクリックで表示されるオプション**参照**ボタンをクリックします。  
  
## <a name="synchronizing-sql-azure-metadata"></a>同期 SQL Azure メタデータ  
SQL Azure データベースについてのメタデータは自動的に更新されません。 SQL Azure メタデータ エクスプ ローラー内のメタデータは、まず SQL Azure に接続されているか、前回を手動でときのメタデータのスナップショットには、メタデータが更新されました。 すべてのデータベース、または任意の 1 つのデータベースまたはデータベース オブジェクトのメタデータを手動で更新することができます。  
  
**メタデータを同期するには**  
  
1.  SQL Azure に接続していることを確認します。  
  
2.  SQL Azure メタデータ エクスプ ローラーで、データベースまたは更新するデータベース スキーマの横にあるチェック ボックスを選択します。  
  
    たとえば、すべてのデータベースのメタデータを更新するには、データベースの横にあるボックスを選択します。  
  
3.  データベース、または個々 のデータベースまたはデータベース スキーマを右クリックし **データベースと同期する**です。  
  
## <a name="refreshing-sql-azure-metadata"></a>更新 SQL Azure メタデータ  
SQL Azure のスキーマは、接続した後に変更する場合は、サーバーからメタデータを更新できます。  
  
**SQL Azure メタデータを更新するには**  
  
-   SQL Azure メタデータ エクスプ ローラーで、右クリックして**データベース**、し、**データベースから更新**です。  
  
## <a name="reconnecting-to-sql-azure"></a>SQL Azure への再接続  
プロジェクトを閉じるまで、SQL Azure への接続がアクティブな保たれます。 プロジェクトを再度開くと、アクティブなサーバーに接続する場合 SQL Azure に再接続する必要があります。 SQL Azure にデータベース オブジェクトを読み込むし、データを移行するまで、オフライン作業できます。  
  
SQL Azure に再接続するための手順は、接続を確立するための手順と同じです。  
  
## <a name="next-step"></a>次の手順  
次の手順では、プロジェクトのニーズによって異なります。  
  
-   アクセスのスキーマと SQL Azure データベースおよびスキーマ間のマッピングをカスタマイズするを参照してください。[マッピング Access データベースから SQL Server スキーマ](http://msdn.microsoft.com/en-us/69bee937-7b2c-49ee-8866-7518c683fad4)です。  
  
-   プロジェクトの構成オプションをカスタマイズするを参照してください。[プロジェクト オプションの設定](http://msdn.microsoft.com/en-us/0a7304df-2f35-4453-96ef-7ac83dea1167)です。  
  
-   ソースとターゲットのデータ型のマッピングをカスタマイズするを参照してください。[マッピング ソースとターゲットのデータ型](http://msdn.microsoft.com/en-us/b362a075-16e7-423f-b63f-e1e9f02844a9)です。  
  
-   場合は、次のタスクを実行する必要はありません、Access データベース オブジェクトの定義を SQL Azure オブジェクトの定義に変換できます。 詳細については、次を参照してください[Access データベースの変換。](http://msdn.microsoft.com/en-us/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)  
  
## <a name="see-also"></a>参照  
[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  

