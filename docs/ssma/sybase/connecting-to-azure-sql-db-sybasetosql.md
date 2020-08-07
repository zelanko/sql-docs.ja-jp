---
title: Azure SQL Database への接続 (SybaseToSQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9e77e4b0-40c0-455c-8431-ca5d43849aa7
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: a16ade8d212d3d197b858488dde05b439d8e989f
ms.sourcegitcommit: 21bedbae28840e2f96f5e8b08bcfc794f305c8bc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2020
ms.locfileid: "87864759"
---
# <a name="connecting-to-azure-sql-database-sybasetosql"></a>Azure SQL Database への接続 (SybaseToSQL)
Sybase データベースを Azure SQL Database に移行するには、Azure SQL Database のターゲットインスタンスに接続する必要があります。 接続すると、SSMA は Azure SQL Database インスタンス内のすべてのデータベースに関するメタデータを取得し、Azure SQL Database メタデータエクスプローラーにデータベースのメタデータを表示します。 SSMA は、接続している Azure SQL Database のインスタンスの情報を格納しますが、パスワードは保存しません。  
  
Azure SQL Database への接続は、プロジェクトを閉じるまでアクティブなままになります。 プロジェクトを再度開いたときに、サーバーへのアクティブな接続が必要な場合は Azure SQL Database に再接続する必要があります。 データベースオブジェクトを Azure SQL Database に読み込んでデータを移行するまで、オフラインで作業することができます。  
  
Azure SQL Database のインスタンスに関するメタデータは、自動的には同期されません。 代わりに Azure SQL Database メタデータエクスプローラーでメタデータを更新するには、Azure SQL Database メタデータを手動で更新する必要があります。 詳細については、このトピックで後述する「Azure SQL Database メタデータの同期」を参照してください。  
  
## <a name="required-azure-sql-database-permissions"></a>必要な Azure SQL Database アクセス許可  
Azure SQL Database に接続するために使用するアカウントには、アカウントが実行するアクションに応じて、異なるアクセス許可が必要です。  
  
1.  Sybase オブジェクトを構文に変換し [!INCLUDE[tsql](../../includes/tsql-md.md)] たり、Azure SQL Database からメタデータを更新したり、変換された構文をスクリプトに保存したりするには、アカウントに Azure SQL Database のインスタンスにログオンする権限が必要です。  
  
2.  データベースオブジェクトを Azure SQL Database に読み込むには、ターゲットデータベースの**db_owner**データベースロールのメンバーシップである最低限の権限が必要です。  
  
## <a name="establishing-an-azure-sql-database-connection"></a>Azure SQL Database 接続の確立  
Sybase データベースオブジェクトを Azure SQL Database 構文に変換する前に、Sybase データベースを移行する Azure SQL Database のインスタンスへの接続を確立する必要があります。  
  
接続プロパティを定義するときに、オブジェクトとデータを移行するデータベースも指定します。 このマッピングは、Azure SQL Database に接続した後に Sybase スキーマレベルでカスタマイズできます。 詳細については、「 [SQL Server スキーマ &#40;SybaseToSQL&#41;への SYBASE ASE スキーマのマッピング](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md)」を参照してください。  
  
> [!WARNING]  
> Azure SQL Database に接続する前に、Azure SQL Database のインスタンスが実行されていて、接続を受け入れることができることを確認してください。  
  
**Azure SQL Database に接続するには**  
  
1.  [**ファイル**] メニューの [ **Azure SQL Database に接続**] を選択します (このオプションは、プロジェクトの作成後に有効になります)。  
  
    以前に Azure SQL Database に接続している場合は、コマンド名が**に再接続**され Azure SQL Database  
  
2.  [接続] ダイアログボックスで、Azure SQL Database のサーバー名を入力または選択します。  
  
3.  データベース名を入力、選択、または**参照**します。  
  
4.  [**ユーザー名**] を入力または選択します。  
  
5.  **パスワード**を入力します。  
  
6.  SSMA では、Azure SQL Database への暗号化接続を推奨しています。  
  
7.  **[接続]** をクリックします。  
  
> [!IMPORTANT]  
> SSMA for Sybase は、Azure SQL Database の**master**データベースへの接続をサポートしていません。  
  
## <a name="synchronizing-azure-sql-database-metadata"></a>Azure SQL Database メタデータの同期  
Azure SQL Database データベースに関するメタデータは自動的に更新されません。 Azure SQL Database メタデータエクスプローラーのメタデータは、最初に Azure SQL Database に接続したとき、またはメタデータを手動で更新したときにメタデータのスナップショットになります。 すべてのデータベース、または任意の1つのデータベースまたはデータベースオブジェクトのメタデータを手動で更新できます。  
  
**メタデータを同期するには**  
  
1.  Azure SQL Database に接続していることを確認します。  
  
2.  Azure SQL Database メタデータエクスプローラーで、更新するデータベースまたはデータベーススキーマの横にあるチェックボックスをオンにします。  
  
    たとえば、すべてのデータベースのメタデータを更新するには、[データベース] の横にあるチェックボックスをオンにします。  
  
3.  [データベース]、または個々のデータベースまたはデータベーススキーマを右クリックし、[**データベースとの同期**] を選択します。  
  
## <a name="next-step"></a>次の手順  
移行の次のステップは、プロジェクトのニーズによって異なります。  
  
-   Sybase スキーマと Azure SQL Database データベースおよびスキーマ間のマッピングをカスタマイズする方法については、「 [SQL Server スキーマ &#40;SybaseToSQL&#41;への SYBASE ASE スキーマのマッピング](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md)」を参照してください。  
  
-   プロジェクトの構成オプションをカスタマイズするには、「 [SybaseToSQL&#41;&#40;プロジェクトオプションを設定](../../ssma/sybase/setting-project-options-sybasetosql.md)する」を参照してください。  
  
-   ソースとターゲットのデータ型のマッピングをカスタマイズするには、「 [SYBASE ASE と SQL Server のデータ型 &#40;SybaseToSQL](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md) 」を参照してください&#41;  
  
-   これらのタスクを実行する必要がない場合は、Sybase データベースオブジェクト定義を Azure SQL Database オブジェクト定義に変換できます。 詳細については、「 [SYBASE ASE データベースオブジェクトの &#40;SybaseToSQL&#41;の変換](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[Sybase ASE データベースを SQL Server Azure SQL Database &#40;SybaseToSQL&#41;に移行する](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
