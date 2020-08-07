---
title: Azure SQL Database への接続 (SQL server への接続) |Microsoft Docs
description: Azure SQL Database のターゲットインスタンスに接続して Access データベースを移行する方法について説明します。 SSMA は Azure SQL Database のデータベースに関するメタデータを取得します。
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
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
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 3bb372b329ce516cae2ab26ece02721d7934b228
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87938931"
---
# <a name="connecting-to-azure-sql-database-accesstosql"></a>Azure SQL Database への接続 (SQL server)
Access データベースを SQL Azure に移行するには、SQL Azure のターゲットインスタンスに接続する必要があります。 接続すると、SSMA は SQL Azure インスタンス内のすべてのデータベースに関するメタデータを取得し、SQL Azure メタデータエクスプローラーにデータベースのメタデータを表示します。 SSMA には、接続している SQL Azure のインスタンスに関する情報が格納されますが、パスワードは保存されません。  
  
SQL Azure への接続は、プロジェクトを閉じるまでアクティブなままになります。 プロジェクトを再度開いたときに、サーバーへのアクティブな接続が必要な場合は SQL Azure に再接続する必要があります。 データベースオブジェクトを SQL Azure に読み込んでデータを移行するまで、オフラインで作業することができます。  
  
SQL Azure のインスタンスに関するメタデータは、自動的には同期されません。 代わりに SQL Azure メタデータエクスプローラーでメタデータを更新するには、SQL Azure メタデータを手動で更新する必要があります。 詳細については、このトピックで後述する「SQL Azure メタデータの同期」を参照してください。  
  
## <a name="required-sql-azure-permissions"></a>必要な SQL Azure アクセス許可  
SQL Azure に接続するために使用するアカウントには、アカウントが実行するアクションに応じて、異なるアクセス許可が必要です。  
  
-   Access オブジェクトを構文に変換し [!INCLUDE[tsql](../../includes/tsql-md.md)] たり、SQL Azure からメタデータを更新したり、変換された構文をスクリプトに保存したりするには、アカウントに SQL Azure のインスタンスにログオンする権限が必要です。  
  
-   データベースオブジェクトを SQL Azure に読み込むには、ターゲットデータベースの**db_owner**データベースロールのメンバーシップである最低限の権限が必要です。  
  
## <a name="establishing-a-sql-azure-connection"></a>SQL Azure 接続の確立  
Access データベースオブジェクトを SQL Azure 構文に変換する前に、Access データベースを移行する SQL Azure のインスタンスへの接続を確立する必要があります。  
  
接続プロパティを定義するときに、オブジェクトとデータを移行するデータベースも指定します。 このマッピングは、SQL Azure に接続した後、Access スキーマレベルでカスタマイズできます。 詳細については、「 [Access データベースの SQL Server スキーマへのマッピング](mapping-source-and-target-databases-accesstosql.md)」を参照してください。  
  
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
  
7.  **[接続]** をクリックします。  
  
> [!IMPORTANT]  
> SSMA for Access は、SQL Azure の**master**データベースへの接続をサポートしていません。  
  
SQL Azure アカウントにデータベースが存在しない場合は、[**参照**のクリック] ボタンに表示される [ **Azure データベースの作成**] オプションを使用して最初のデータベースを作成できます。  
  
## <a name="synchronizing-sql-azure-metadata"></a>SQL Azure メタデータの同期  
Azure SQL Database 内のデータベースに関するメタデータは、自動的に更新されません。 SQL Azure メタデータエクスプローラーのメタデータは、最初に SQL Azure に接続したとき、またはメタデータを手動で更新したときにメタデータのスナップショットになります。 すべてのデータベース、または任意の1つのデータベースまたはデータベースオブジェクトのメタデータを手動で更新できます。  
  
**メタデータを同期するには**  
  
1.  SQL Azure に接続していることを確認します。  
  
2.  SQL Azure メタデータエクスプローラーで、更新するデータベースまたはデータベーススキーマの横にあるチェックボックスをオンにします。  
  
    たとえば、すべてのデータベースのメタデータを更新するには、[データベース] の横にあるチェックボックスをオンにします。  
  
3.  [データベース]、または個々のデータベースまたはデータベーススキーマを右クリックし、[**データベースとの同期**] を選択します。  
  
## <a name="refreshing-sql-azure-metadata"></a>SQL Azure メタデータの更新  
接続後に SQL Azure スキーマが変更された場合は、サーバーからメタデータを更新できます。  
  
**SQL Azure メタデータを更新するには**  
  
-   SQL Azure メタデータエクスプローラーで、[**データベース**] を右クリックし、[**データベースから更新**] を選択します。  
  
## <a name="reconnecting-to-sql-azure"></a>SQL Azure に再接続しています  
SQL Azure への接続は、プロジェクトを閉じるまでアクティブなままになります。 プロジェクトを再度開いたときに、サーバーへのアクティブな接続が必要な場合は SQL Azure に再接続する必要があります。 データベースオブジェクトを SQL Azure に読み込んでデータを移行するまで、オフラインで作業することができます。  
  
SQL Azure に再接続する手順は、接続を確立する手順と同じです。  
  
## <a name="next-steps"></a>次のステップ  
移行の次のステップは、プロジェクトのニーズによって異なります。  
  
-   アクセススキーマと Azure SQL Database 間のマッピングをカスタマイズするには、「 [SQL Server スキーマへの Access データベースのマッピング](mapping-source-and-target-databases-accesstosql.md)」を参照してください。  
  
-   プロジェクトの構成オプションをカスタマイズするには、「[プロジェクトオプションの設定](setting-conversion-and-migration-options-accesstosql.md)」を参照してください。  
  
-   ソースとターゲットのデータ型のマッピングをカスタマイズするには、「[ソースとターゲットのデータ型のマッピング](mapping-source-and-target-data-types-accesstosql.md)」を参照してください。  
  
-   これらのタスクを実行する必要がない場合は、Access データベースオブジェクト定義を SQL Azure オブジェクト定義に変換できます。 詳細については、「 [Access データベースの変換](converting-access-database-objects-accesstosql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[Access データベースの SQL Server への移行](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
