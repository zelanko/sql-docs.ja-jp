---
title: Azure SQL DB への接続 (SybaseToSQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9e77e4b0-40c0-455c-8431-ca5d43849aa7
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 10be1dc3652c944b9de08a01b0f4cdff5ae5849a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "70176239"
---
# <a name="connecting-to-azure-sql-db-sybasetosql"></a>Azure SQL DB への接続 (SybaseToSQL)
Sybase データベースを Azure SQL DB に移行するには、Azure SQL DB のターゲットインスタンスに接続する必要があります。 接続すると、SSMA は、Azure SQL DB のインスタンス内のすべてのデータベースに関するメタデータを取得し、Azure SQL DB メタデータエクスプローラーにデータベースのメタデータを表示します。 SSMA は、接続先の Azure SQL DB インスタンスの情報を格納しますが、パスワードは保存しません。  
  
Azure SQL DB への接続は、プロジェクトを閉じるまでアクティブなままになります。 プロジェクトを再度開いたときに、サーバーへのアクティブな接続が必要な場合は、Azure SQL DB に再接続する必要があります。 データベースオブジェクトを Azure SQL DB に読み込んでデータを移行するまで、オフラインで作業することができます。  
  
Azure SQL DB のインスタンスに関するメタデータは、自動的には同期されません。 代わりに、Azure sql DB メタデータエクスプローラーでメタデータを更新するには、Azure SQL DB メタデータを手動で更新する必要があります。 詳細については、このトピックで後述する「Azure SQL DB のメタデータの同期」を参照してください。  
  
## <a name="required-azure-sql-db-permissions"></a>必要な Azure SQL DB アクセス許可  
Azure SQL DB への接続に使用するアカウントには、アカウントで実行されるアクションに応じて、異なるアクセス許可が必要です。  
  
1.  Sybase オブジェクトを構文に[!INCLUDE[tsql](../../includes/tsql-md.md)]変換したり、AZURE sql db からメタデータを更新したり、変換された構文をスクリプトに保存したりするには、アカウントに AZURE SQL DB のインスタンスにログオンするためのアクセス許可が必要です。  
  
2.  データベースオブジェクトを Azure SQL DB に読み込むには、最小権限の要件は、ターゲットデータベースの**db_owner**データベースロールのメンバーシップです。  
  
## <a name="establishing-an-azure-sql-db-connection"></a>Azure SQL DB 接続の確立  
Sybase データベースオブジェクトを Azure SQL DB 構文に変換する前に、Sybase データベースの移行先となる Azure SQL DB インスタンスへの接続を確立する必要があります。  
  
接続プロパティを定義するときに、オブジェクトとデータを移行するデータベースも指定します。 このマッピングは、Azure SQL DB に接続した後に Sybase スキーマレベルでカスタマイズできます。 詳細については、「 [SQL Server スキーマ &#40;SybaseToSQL&#41;への SYBASE ASE スキーマのマッピング](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md)」を参照してください。  
  
> [!WARNING]  
> Azure SQL DB に接続する前に、Azure SQL DB のインスタンスが実行されていて、接続を受け入れることができることを確認してください。  
  
**Azure SQL DB に接続するには**  
  
1.  [**ファイル**] メニューの [ **Azure SQL DB への接続**] を選択します (このオプションは、プロジェクトの作成後に有効になります)。  
  
    以前に Azure SQL DB に接続している場合は、コマンド名が**AZURE SQL db に再接続**されます。  
  
2.  [接続] ダイアログボックスで、Azure SQL DB のサーバー名を入力または選択します。  
  
3.  データベース名を入力、選択、または**参照**します。  
  
4.  [**ユーザー名**] を入力または選択します。  
  
5.  **パスワード**を入力します。  
  
6.  SSMA では、Azure SQL DB への暗号化接続を推奨しています。  
  
7.  **[Connect]** をクリックします。  
  
> [!IMPORTANT]  
> SSMA for Sybase は、Azure SQL DB の**master**データベースへの接続をサポートしていません。  
  
## <a name="synchronizing-azure-sql-db-metadata"></a>Azure SQL DB メタデータを同期しています  
Azure SQL DB データベースに関するメタデータは自動的に更新されません。 Azure SQL DB メタデータエクスプローラーのメタデータは、最初に Azure SQL DB に接続したとき、またはメタデータを手動で更新したときにメタデータのスナップショットになります。 すべてのデータベース、または任意の1つのデータベースまたはデータベースオブジェクトのメタデータを手動で更新できます。  
  
**メタデータを同期するには**  
  
1.  Azure SQL DB に接続していることを確認します。  
  
2.  Azure SQL DB メタデータエクスプローラーで、更新するデータベースまたはデータベーススキーマの横にあるチェックボックスをオンにします。  
  
    たとえば、すべてのデータベースのメタデータを更新するには、[データベース] の横にあるチェックボックスをオンにします。  
  
3.  [データベース]、または個々のデータベースまたはデータベーススキーマを右クリックし、[**データベースとの同期**] を選択します。  
  
## <a name="next-step"></a>次の手順  
移行の次のステップは、プロジェクトのニーズによって異なります。  
  
-   Sybase スキーマと Azure SQL DB データベースおよびスキーマ間のマッピングをカスタマイズするには、「 [SYBASE ASE スキーマを SQL Server スキーマ &#40;SybaseToSQL&#41;にマップ](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md)する」を参照してください。  
  
-   プロジェクトの構成オプションをカスタマイズするには、「 [SybaseToSQL&#41;&#40;プロジェクトオプションを設定](../../ssma/sybase/setting-project-options-sybasetosql.md)する」を参照してください。  
  
-   ソースとターゲットのデータ型のマッピングをカスタマイズするには、「 [SYBASE ASE と SQL Server のデータ型 &#40;SybaseToSQL](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md) 」を参照してください&#41;  
  
-   これらのタスクを実行する必要がない場合は、Sybase データベースオブジェクト定義を Azure SQL DB オブジェクト定義に変換できます。 詳細については、「 [SYBASE ASE データベースオブジェクトの &#40;SybaseToSQL&#41;の変換](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[Sybase ASE データベースの SQL Server への移行-Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
