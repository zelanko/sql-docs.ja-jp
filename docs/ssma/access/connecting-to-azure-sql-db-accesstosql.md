---
title: Azure SQL DB (AccessToSQL) への接続 |Microsoft Docs
ms.prod: sql
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
manager: craigg
ms.openlocfilehash: 6f54e23ee744f34ce3da70e1fd2a469d70b9063a
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38983934"
---
# <a name="connecting-to-azure-sql-db-accesstosql"></a>Azure SQL DB (AccessToSQL) への接続
Access データベースを SQL Azure に移行するには、SQL Azure のターゲット インスタンスに接続する必要があります。 接続するときに、SSMA は SQL Azure のインスタンスのすべてのデータベースに関するメタデータを取得し、SQL Azure メタデータ エクスプ ローラーでデータベースのメタデータを表示します。 SSMA では、SQL Azure のインスタンスについてに接続しているがパスワードを保存しない情報を格納します。  
  
プロジェクトを閉じるまで SQL Azure への接続をアクティブに保ちます。 プロジェクトを再度開くと、アクティブなサーバーに接続する場合 SQL Azure に再接続する必要があります。 SQL Azure にデータベース オブジェクトを読み込むし、データを移行するまで、オフライン使用できます。  
  
SQL Azure のインスタンスに関するメタデータは、自動的に同期されません。 代わりに、SQL Azure メタデータ エクスプ ローラー内のメタデータを更新するには、SQL Azure メタデータを手動で更新する必要があります。 詳細については、このトピックの後半の「SQL Azure メタデータの同期」セクションを参照してください。  
  
## <a name="required-sql-azure-permissions"></a>SQL Azure に必要なアクセス許可  
SQL Azure への接続に使用されるアカウントには、アカウントで実行された操作に応じてさまざまなアクセス許可が必要です。  
  
-   アクセス オブジェクトに変換する[!INCLUDE[tsql](../../includes/tsql_md.md)]スクリプトの構文は、SQL Azure からメタデータを更新するかに変換された構文を保存する、アカウントは SQL Azure のインスタンスにログオンする権限が必要です。  
  
-   を SQL Azure にデータベース オブジェクトを読み込むにはアクセス許可の最小要件、メンバーシップ、 **db_owner**ターゲット データベースのデータベース ロール。  
  
## <a name="establishing-a-sql-azure-connection"></a>SQL Azure を確立する接続  
Access データベース オブジェクトを SQL Azure の構文に変換する前に、Access データベースまたはデータベースを移行する SQL Azure のインスタンスへの接続を確立する必要があります。  
  
接続のプロパティを定義するときに、オブジェクトとデータを移行するデータベースを指定します。 SQL Azure に接続した後は、アクセス、スキーマ レベルでは、このマッピングをカスタマイズできます。 詳細については、次を参照してください[Access データベースを SQL Server スキーマへのマッピング。](http://msdn.microsoft.com/69bee937-7b2c-49ee-8866-7518c683fad4)  
  
> [!IMPORTANT]  
> SQL Azure に接続する前に、SQL Azure のインスタンスが実行されていて、接続を受け入れることを確認します。  
  
**SQL Azure に接続するには**  
  
1.  **ファイル**メニューの  **SQL Azure への接続**(このオプションは、プロジェクトの作成後に有効です)。  
  
    SQL Azure に接続されていた場合、コマンド名になります**SQL Azure に再接続**します。  
  
2.  接続ダイアログ ボックスで入力するか、SQL Azure のサーバー名を選択します。  
  
3.  入力を選択または**参照**データベース名。  
  
4.  入力または選択**UserName**します。  
  
5.  入力、**パスワード**します。  
  
6.  SSMA では、SQL Azure に暗号化された接続をお勧めします。  
  
7.  **[接続]** をクリックします。  
  
> [!IMPORTANT]  
> アクセス用の SSMA がへの接続をサポートしていません**マスター** SQL Azure データベース。  
  
使用して最初にデータベースを作成するには、SQL Azure アカウントには、データベースがない場合、 **Azure データベースの作成**のクリックで表示されるオプション**参照**ボタンをクリックします。  
  
## <a name="synchronizing-sql-azure-metadata"></a>SQL Azure の同期メタデータ  
SQL Azure データベースに関するメタデータは、自動的に更新されません。 SQL Azure メタデータ エクスプ ローラー内のメタデータは、SQL Azure に最初に接続すると、最後を手動でメタデータのスナップショットには、メタデータが更新されました。 すべてのデータベースまたは任意の 1 つのデータベースまたはデータベース オブジェクトのメタデータを手動で更新することができます。  
  
**メタデータを同期するには**  
  
1.  SQL Azure に接続していることを確認します。  
  
2.  SQL Azure メタデータ エクスプ ローラーで、データベースまたはデータベースのスキーマを更新する横のチェック ボックスを選択します。  
  
    たとえば、すべてのデータベースのメタデータを更新するには、データベースの横にあるボックスを選択します。  
  
3.  データベース、または個々 のデータベースまたはデータベースのスキーマを右クリックし、**データベースと同期する**します。  
  
## <a name="refreshing-sql-azure-metadata"></a>SQL Azure の更新のメタデータ  
SQL Azure のスキーマは、接続した後に変更する場合は、サーバーからメタデータを更新できます。  
  
**SQL Azure メタデータを更新するには**  
  
-   SQL Azure メタデータ エクスプ ローラーで右クリックして**データベース**、し、**データベースからの更新**します。  
  
## <a name="reconnecting-to-sql-azure"></a>SQL Azure への再接続  
プロジェクトを閉じるまで SQL Azure への接続をアクティブに保ちます。 プロジェクトを再度開くと、アクティブなサーバーに接続する場合 SQL Azure に再接続する必要があります。 SQL Azure にデータベース オブジェクトを読み込むし、データを移行するまで、オフライン使用できます。  
  
SQL Azure に再接続するための手順では、接続を確立するための手順と同じです。  
  
## <a name="next-step"></a>次の手順  
移行の次の手順は、プロジェクトのニーズによって異なります。  
  
-   Access スキーマと SQL Azure データベースとスキーマ間のマッピングをカスタマイズするを参照してください。 [SQL Server スキーマへのマッピングの Access データベース](http://msdn.microsoft.com/69bee937-7b2c-49ee-8866-7518c683fad4)します。  
  
-   プロジェクトの構成オプションをカスタマイズするを参照してください。[プロジェクト オプションの設定](http://msdn.microsoft.com/0a7304df-2f35-4453-96ef-7ac83dea1167)します。  
  
-   ソースとターゲットのデータ型のマッピングをカスタマイズするを参照してください。[マッピング ソースとターゲットのデータ型](http://msdn.microsoft.com/b362a075-16e7-423f-b63f-e1e9f02844a9)します。  
  
-   これらのタスクを実行する必要はありません場合、Access データベース オブジェクトの定義を SQL Azure のオブジェクトの定義に変換できます。 詳細については、次を参照してください[Access データベースの変換。](http://msdn.microsoft.com/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)  
  
## <a name="see-also"></a>参照  
[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
