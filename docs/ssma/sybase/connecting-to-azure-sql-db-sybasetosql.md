---
title: Azure SQL DB (SybaseToSQL) への接続 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9e77e4b0-40c0-455c-8431-ca5d43849aa7
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 2a322f7769db5b1f2ee0de4e4e35839d63ed43b8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67948563"
---
# <a name="connecting-to-azure-sql-db-sybasetosql"></a>Azure SQL DB への接続 (SybaseToSQL)
Sybase データベースを Azure SQL DB に移行するには、Azure SQL DB のターゲット インスタンスに接続する必要があります。 接続すると、SSMA は Azure SQL DB のインスタンスのすべてのデータベースに関するメタデータを取得し、Azure SQL DB メタデータ エクスプ ローラーでデータベースのメタデータを表示します。 SSMA は、Azure SQL DB が、接続先が、パスワードを保存しないのインスタンスの情報を格納します。  
  
Azure SQL DB への接続をプロジェクトを終了するまでアクティブに保ちます。 プロジェクトを再度開くと、アクティブなサーバーに接続する場合 Azure SQL DB に再接続する必要があります。 Azure SQL DB にデータベース オブジェクトを読み込むし、データを移行するまで、オフライン使用できます。  
  
Azure SQL DB のインスタンスに関するメタデータは、自動的に同期されません。 代わりに、Azure SQL DB メタデータ エクスプ ローラー内のメタデータを更新するには、Azure SQL DB のメタデータを手動で更新する必要があります。 詳細については、このトピックの後半の「同期する Azure SQL DB メタデータ」セクションを参照してください。  
  
## <a name="required-azure-sql-db-permissions"></a>Azure SQL DB のアクセス許可が必要  
Azure SQL DB への接続に使用されるアカウントには、アカウントで実行された操作に応じてさまざまなアクセス許可が必要です。  
  
1.  Sybase オブジェクトに変換する[!INCLUDE[tsql](../../includes/tsql-md.md)]スクリプトの構文は、Azure SQL DB からメタデータを更新するかに変換された構文を保存する、アカウントは Azure SQL DB のインスタンスにログオンする権限が必要です。  
  
2.  データベース オブジェクトを Azure SQL DB に読み込む、最小限のアクセス許可の要件にはメンバーシップ、 **db_owner**ターゲット データベースのデータベース ロール。  
  
## <a name="establishing-a-azure-sql-db-connection"></a>Azure SQL DB の接続を確立します。  
Sybase データベース オブジェクトを Azure SQL DB の構文に変換する前に、Sybase データベースやデータベースを移行する Azure SQL DB のインスタンスへの接続を確立する必要があります。  
  
接続のプロパティを定義するときに、オブジェクトとデータを移行するデータベースを指定します。 Azure SQL DB に接続した後は、Sybase、スキーマ レベルでは、このマッピングをカスタマイズできます。 詳細については、次を参照してください[SQL Server スキーマへの Sybase ASE スキーマのマッピング&#40;SybaseToSQL。&#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md)  
  
> [!WARNING]  
> Azure SQL DB に接続する前に、Azure SQL DB のインスタンスが実行されていて、接続を受け入れることを確認します。  
  
**Azure SQL DB に接続するには**  
  
1.  **ファイル**メニューの  **Azure SQL DB への接続**(このオプションは、プロジェクトの作成後に有効です)。  
  
    Azure SQL DB に以前接続した場合、コマンド名になります**Azure SQL DB への再接続**  
  
2.  接続ダイアログ ボックスで入力するか、Azure SQL DB のサーバー名を選択します。  
  
3.  入力を選択または**参照**データベース名。  
  
4.  入力または選択**UserName**します。  
  
5.  入力、**パスワード**します。  
  
6.  SSMA では、Azure SQL DB に暗号化された接続をお勧めします。  
  
7.  **[接続]** をクリックします。  
  
> [!IMPORTANT]  
> SSMA for Sybase はへの接続をサポートしていません**マスター** Azure SQL DB のデータベース。  
  
## <a name="synchronizing-azure-sql-db-metadata"></a>Azure SQL DB のメタデータの同期  
Azure SQL DB のデータベースについてのメタデータは、自動的に更新されません。 Azure SQL DB メタデータ エクスプ ローラー内のメタデータは、Azure SQL DB、またはメタデータを手動で更新された最後の時刻に最初に接続するときに、メタデータのスナップショットです。 すべてのデータベースまたは任意の 1 つのデータベースまたはデータベース オブジェクトのメタデータを手動で更新することができます。  
  
**メタデータを同期するには**  
  
1.  Azure SQL DB に接続していることを確認します。  
  
2.  Azure SQL DB メタデータ エクスプ ローラーで、データベースまたはデータベースのスキーマを更新する横のチェック ボックスを選択します。  
  
    たとえば、すべてのデータベースのメタデータを更新するには、データベースの横にあるボックスを選択します。  
  
3.  データベース、または個々 のデータベースまたはデータベースのスキーマを右クリックし、**データベースと同期する**します。  
  
## <a name="next-step"></a>次の手順  
移行の次の手順は、プロジェクトのニーズによって異なります。  
  
-   Sybase スキーマと Azure SQL DB データベースとスキーマ間のマッピングをカスタマイズするを参照してください[SQL Server スキーマへのマッピングの Sybase ASE スキーマ&#40;SybaseToSQL。&#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md)  
  
-   プロジェクトの構成オプションをカスタマイズするを参照してください[プロジェクト オプションの設定&#40;SybaseToSQL。&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md)  
  
-   ソースとターゲットのデータ型のマッピングをカスタマイズするを参照してください[マッピング Sybase ASE と SQL Server データ型&#40;SybaseToSQL。&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md)  
  
-   これらのタスクを実行する必要はありません場合、Sybase データベース オブジェクトの定義を Azure SQL DB オブジェクトの定義に変換できます。 詳細については、次を参照してください[Sybase ASE データベース オブジェクトの変換&#40;SybaseToSQL。&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)  
  
## <a name="see-also"></a>関連項目  
[SQL Server - Azure SQL DB への Sybase ASE データベース移行&#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
