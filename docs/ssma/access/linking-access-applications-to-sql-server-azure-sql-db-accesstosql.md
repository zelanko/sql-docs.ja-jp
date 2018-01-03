---
title: "SQL Server - Azure SQL DB への Access アプリケーションのリンク |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-access
ms.custom: 
ms.date: 08/17/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Access databases, linking to SQL Azure
- Access databases, linking to SQL Server
- auto-increment columns
- data types, unsupported
- hyperlink columns
- linking tables
- migrating databases, post-migration issues
- post-migration issues
- reference, post-migration issues
- refreshing linked tables
- slow performance
- unlinking tables
ms.assetid: 82374ad2-7737-4164-a489-13261ba393d4
caps.latest.revision: "19"
author: Shamikg
ms.author: Shamikg
manager: murato
ms.workload: On Demand
ms.openlocfilehash: aa06650106584d975c6bf45855473dc1d80a100d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="linking-access-applications-to-sql-server---azure-sql-db-accesstosql"></a>SQL Server - Azure SQL DB (AccessToSQL) へのリンクの Access アプリケーション
既存の Access アプリケーションを使用するかどうかは[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、移行後に元の Access テーブルをリンクすることができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure のテーブルです。 Access データベースが変更のリンクのクエリ、フォーム、レポート、およびデータ アクセス ページ内のデータを使用するように、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Access データベース内のデータではなく SQL Azure データベース。  
  
> [!NOTE]  
> Access のテーブルにアクセス、残りますと共には更新されません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure を更新します。 テーブルをリンクして機能を確認した後に、アクセス テーブルを削除することができます。  
  
## <a name="linking-access-and-sql-server-tables"></a>アクセスと SQL Server のテーブルをリンクします。  
Access テーブルをリンクすると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure テーブル、Jet データベース エンジンに接続情報とテーブルのメタデータが格納がでデータが格納されている[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 このリンクであっても、実際のテーブルとデータにアクセス テーブルに対して操作をアプリケーションにアクセス[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。  
  
> [!NOTE]  
> 使用する場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]認証では、パスワードはクリア テキストでリンクの Access テーブルに格納します。 Windows 認証を使用することをお勧めします。  
  
**テーブルをリンクするには**  
  
1.  メタデータ エクスプ ローラーでのアクセス、リンクを追加するテーブルを選択します。  
  
2.  右クリック**テーブル**、し、**リンク**です。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) のアクセスは、元の Access テーブルをバックアップし、リンク テーブルを作成します。  
  
テーブルをリンクした後に小さなリンク アイコンが SSMA 内のテーブルが表示されます。 Access では、テーブルは「リンク」アイコンが含まれ、それを指す矢印の付いた地球が表示されます。  
  
Access でテーブルを開くときにキーセット カーソルを使用してデータを取得します。 その結果、大規模なテーブルのすべてのデータは取得されません一度に 1 つ。 ただし、テーブルを参照すると、アクセスは必要に応じて、追加のデータを取得します。  
  
> [!IMPORTANT]  
> Azure のデータベースでの access テーブルをリンクするには、SQL Server ネイティブ Client(SNAC) バージョン 10.5 必要がありますかそれ以降。   
> SNAC の最新バージョンを取得する[Microsoft® SQL Server® 2008 R2 用 Feature Pack](http://go.microsoft.com/fwlink/?LinkId=196940)です。  
  
## <a name="unlinking-access-tables"></a>リンク解除の Access テーブル  
Access のテーブルからのリンクを解除するときに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure テーブル、SSMA は、元の Access テーブルとそのデータを復元します。  
  
**テーブルのリンクを解除するには**  
  
1.  メタデータ エクスプ ローラーでのアクセス、リンクを解除するテーブルを選択します。  
  
2.  右クリック**テーブル**、し、 **Unlink**です。  
  
## <a name="linking-tables-to-a-different-server"></a>別のサーバーにテーブルをリンクします。  
1 つの SQL Server インスタンスにアクセス テーブルをリンクするいるし、他のインスタンスへのリンクを変更することが、テーブルが再リンクする必要があります。  
  
**別のサーバーにテーブルをリンクするには**  
  
1.  メタデータ エクスプ ローラーでのアクセス、リンクを解除するテーブルを選択します。  
  
2.  右クリック**テーブル**し、 **Unlink**です。  
  
3.  クリックして、 **SQL Server に再接続**ボタンをクリックします。  
  
4.  インスタンスに接続[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure の Access テーブルをリンクします。  
  
5.  メタデータ エクスプ ローラーでのアクセス、リンクを追加するテーブルを選択します。  
  
6.  右クリック**テーブル**、し、**リンク**です。  
  
## <a name="updating-linked-tables"></a>リンク テーブルの更新  
場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SQL Azure のテーブルの定義が変更されるか、リンクを解除し、このトピックの例で示した手順を使用して SSMA 内のテーブルを再リンクすることができます。 アクセスを使用して、テーブルを更新することもできます。  
  
**アクセスを使用してリンク テーブルを更新するには**  
  
1.  Access データベースを開きます。  
  
2.  **オブジェクト**一覧で、クリックして**テーブル**です。  
  
3.  リンク テーブルを右クリックし **リンク テーブル マネージャー**です。  
  
4.  更新、およびをクリックするリンクされた各テーブルの横にあるチェック ボックスをオンに**OK**です。  
  
## <a name="possible-post-migration-issues"></a>移行後の考えられる問題  
次のセクションへのアクセスからデータベースを移行した後に既存の Access アプリケーションで発生したリストの問題[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure し、その原因と解決策と共に、テーブルをリンクします。  
  
### <a name="slow-performance-with-linked-tables"></a>リンク テーブルのパフォーマンスの低下  
**原因:**いくつかのクエリ遅くなる可能性がアップサイジング後に、次の理由。  
  
-   アプリケーションに存在しない機能に依存して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure は、これにより、SELECT クエリを実行するには、ローカル テーブルのプルダウン Jet します。  
  
-   更新または多くの行を削除するクエリは、行ごとに、Jet によって、パラメーター化されたクエリとして送信されます。  
  
**解決方法:**パススルー クエリ、ストアド プロシージャ、またはビューに、実行速度の遅いクエリを変換します。 パススルー クエリに変換するには、次の問題があります。  
  
-   パススルー クエリを変更することはできません。 クエリの結果を変更または新しいレコードを追加する行う必要があります、別の方法でなど、明示的な**変更**または**追加**クエリにバインドされているフォームのボタンです。  
  
-   一部のクエリは、ユーザー入力を必要とは、パススルー クエリはユーザー入力をサポートしていません。 Visual Basic for Applications (VBA) コード、パラメーターの入力を求めるか、入力コントロールとして使用される形式によって、ユーザー入力を取得できます。 どちらの場合は、VBA コードは、サーバーにユーザー入力のクエリを送信します。  
  
### <a name="auto-increment-columns-are-not-updated-until-the-record-is-updated"></a>レコードが更新されるまで、自動インクリメント列が更新されません。  
**原因:** RecordSet.AddNew Jet で呼び出すと、自動インクリメント列が使用可能なレコードが更新される前にします。 これは true ではありません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 Id 列の新しい値の新しい値は、新しいレコードを保存した後にのみ使用可能なです。  
  
**解決方法:** id フィールドにアクセスする前に、次の Visual Basic for Applications (VBA) コードを実行します。  
  
```  
Recordset.Update  
Recordset.Move 0,  
Recordset.LastModified  
```  
  
### <a name="new-records-are-not-available"></a>新しいレコードは使用できません。  
**原因:**にレコードを追加すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または VBA を使用して、テーブルの一意のインデックスのフィールドには既定値とを割り当てない値のフィールドに新しいレコードが表示されない内のテーブルを再び開くまで SQL Azure テーブル[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 新しいレコードから値を取得しようとすると、次のエラー メッセージが表示されます。  
  
`Run-time error '3167' Record is deleted.`  
  
**解決方法:**を開いたとき、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または VBA コードを使用してテーブルでは、SQL Azure、`dbSeeChanges`例を次のオプション。  
  
`Set rs = db.OpenRecordset("TestTable", dbOpenDynaset, dbSeeChanges)`  
  
### <a name="after-migration-some-queries-will-not-allow-the-user-to-add-a-new-record"></a>移行後に、いくつかのクエリはユーザー許可しない、新しいレコードを追加するには  
**原因:**クエリに一意のインデックスに含まれているすべての列が含まれていない場合、クエリを使用して新しい値を追加することはできません。  
  
**解決方法:**に少なくとも 1 つの一意なインデックスに含まれるすべての列がクエリの一部であることを確認します。  
  
### <a name="you-cannot-modify-a-linked-table-schema-with-access"></a>アクセス権を持つリンク テーブルのスキーマを変更することはできません。  
**原因:**後のデータの移行とリンク テーブルの場合は、ユーザーがアクセスにあるテーブルのスキーマを変更できません。  
  
**解決方法:**を使用して、テーブル スキーマを変更[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]、および Access でのリンクを更新します。  
  
### <a name="hyperlink-functionality-is-lost-after-migrating-data"></a>移行した後、ハイパーリンク機能が失われたデータ  
**原因:**移行した後、データ列内のハイパーリンクが機能しなくなり、単純な**nvarchar (max)**列です。  
  
**解決方法:**なし。  
  
### <a name="some-sql-server-data-types-are-not-supported-by-access"></a>アクセスでは、一部の SQL Server データ型はサポートされていません。  
**原因:**後で更新する場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Access によってサポートされていないデータ型を格納する SQL Azure のテーブル アクセスで、テーブルを開くことはできません。  
  
**解決方法:**サポートされているデータ型を持つ行のみを返すアクセス クエリを定義することができます。  
  
## <a name="see-also"></a>参照  
[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
