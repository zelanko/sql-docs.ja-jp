---
title: SQL Server への Access アプリケーションのリンク-Azure SQL DB |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 08/17/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
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
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: 3bdd11580e1a7e57b72d2d8fe0ce5f54299555db
ms.sourcegitcommit: 66dbc3b740f4174f3364ba6b68bc8df1e941050f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73632696"
---
# <a name="linking-access-applications-to-sql-server---azure-sql-db-accesstosql"></a>SQL Server への Access アプリケーションのリンク-Azure SQL DB (アクセス許可 Sql)
既存の Access アプリケーションを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で使用する場合は、移行された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または SQL Azure のテーブルに元の Access テーブルをリンクできます。 リンクを使用すると Access データベースが変更されるため、クエリ、フォーム、レポート、およびデータアクセスページでは、Access データベースのデータではなく、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または SQL Azure データベースのデータが使用されます。  
  
> [!NOTE]  
> アクセステーブルは引き続きアクセスできますが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または SQL Azure 更新と共に更新されることはありません。 テーブルをリンクして機能を確認したら、Access テーブルを削除することができます。  
  
## <a name="linking-access-and-sql-server-tables"></a>Access テーブルと SQL Server テーブルのリンク  
Access テーブルを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または SQL Azure テーブルにリンクすると、Jet データベースエンジンは接続情報とテーブルメタデータを格納しますが、データは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または SQL Azure に格納されます。 このリンクにより、アクセスアプリケーションは、実際のテーブルとデータが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または SQL Azure にある場合でも Access テーブルに対して動作します。  
  
> [!NOTE]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合、パスワードは、リンクされた Access テーブルにクリアテキストで格納されます。 Windows 認証を使用することをお勧めします。  
  
**テーブルをリンクするには**  
  
1.  Access Metadata Explorer で、リンクするテーブルを選択します。  
  
2.  **[テーブル]** を右クリックし、 **[リンク]** を選択します。  
  
Access の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) は、元の Access テーブルをバックアップし、リンクテーブルを作成します。  
  
テーブルをリンクすると、SSMA のテーブルに小さなリンクアイコンが表示されます。 Access では、テーブルに "リンク" アイコンが表示されます。このアイコンは、矢印が付いた地球です。  
  
Access でテーブルを開くと、キーセットカーソルを使用してデータが取得されます。 その結果、大きなテーブルの場合、すべてのデータが一度に取得されることはありません。 ただし、テーブルを参照すると、アクセスによって必要に応じて追加のデータが取得されます。  
  
> [!IMPORTANT]  
> Azure データベースにアクセステーブルをリンクするには、SQL Server Native Client (SNAC) バージョン10.5 以降が必要です。   
> 最新バージョンの SNAC は、 [Microsoft® SQL Server® 2008 R2 Feature Pack](https://www.microsoft.com/en-us/download/details.aspx?id=16978)から入手できます。  
  
## <a name="unlinking-access-tables"></a>アクセステーブルのリンク解除  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または SQL Azure テーブルから Access テーブルのリンクを解除すると、SSMA によって元のアクセステーブルとそのデータが復元されます。  
  
**テーブルのリンクを解除するには**  
  
1.  Access Metadata Explorer で、リンクを解除するテーブルを選択します。  
  
2.  **[テーブル]** を右クリックし、 **[リンクの解除]** をクリックします。  
  
## <a name="linking-tables-to-a-different-server"></a>別のサーバーへのテーブルのリンク  
Access テーブルを1つの SQL Server インスタンスにリンクし、後で別のインスタンスへのリンクを変更する場合は、テーブルを再リンクする必要があります。  
  
**テーブルを別のサーバーにリンクするには**  
  
1.  Access Metadata Explorer で、リンクを解除するテーブルを選択します。  
  
2.  **[テーブル]** を右クリックし、 **[リンク解除]** を選択します。  
  
3.  **[SQL Server に再接続]** ボタンをクリックします。  
  
4.  アクセステーブルをリンクする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または SQL Azure のインスタンスに接続します。  
  
5.  Access Metadata Explorer で、リンクするテーブルを選択します。  
  
6.  **[テーブル]** を右クリックし、 **[リンク]** を選択します。  
  
## <a name="updating-linked-tables"></a>リンクテーブルの更新  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または SQL Azure テーブルの定義が変更された場合は、このトピックで前述した手順に従って、SSMA のテーブルのリンクを解除してから再リンクできます。 また、Access を使用してテーブルを更新することもできます。  
  
**Access を使用してリンクテーブルを更新するには**  
  
1.  Access データベースを開きます。  
  
2.  **[オブジェクト]** ボックスの一覧の **[テーブル]** をクリックします。  
  
3.  リンクテーブルを右クリックし、 **[リンクテーブルマネージャー]** をクリックします。  
  
4.  更新するリンクテーブルの横にあるチェックボックスをオンにし、[ **OK]** をクリックします。  
  
## <a name="possible-post-migration-issues"></a>移行後に発生する可能性のある問題  
次のセクションでは、Access から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または SQL Azure にデータベースを移行した後、テーブルをその原因と解決策と共にリンクした後に、既存の Access アプリケーションで発生する可能性がある問題を示します。  
  
### <a name="slow-performance-with-linked-tables"></a>リンクテーブルを使用したパフォーマンスの低下  
**原因:** 次の理由により、一部のクエリでは、アップサイズが遅くなる可能性があります。  
  
-   このアプリケーションは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または SQL Azure に存在しない関数に依存しています。これにより、Jet はテーブルをローカルにプルし、SELECT クエリを実行します。  
  
-   多数の行を更新または削除するクエリは、各行のパラメーター化クエリとして Jet によって送信されます。  
  
**解決策:** 実行速度の遅いクエリをパススルークエリ、ストアドプロシージャ、またはビューに変換します。 パススルークエリへの変換には、次の問題があります。  
  
-   パススルークエリは変更できません。 クエリ結果を変更したり、新しいレコードを追加したりするには、クエリにバインドされているフォームに 明示的に **[変更]** または **[追加]** ボタンを使用するなど、別の方法で行う必要があります。  
  
-   一部のクエリではユーザー入力が必要ですが、パススルークエリではユーザー入力がサポートされていません。 ユーザー入力は、パラメーターの入力を求める (VBA) コード、または入力コントロールとして使用されるフォームによって取得することができます Visual Basic for Applications ます。 どちらの場合も、VBA コードはクエリをユーザー入力と共にサーバーに送信します。  
  
### <a name="auto-increment-columns-are-not-updated-until-the-record-is-updated"></a>自動増分列は、レコードが更新されるまで更新されません。  
**原因:** Jet でレコードセットを呼び出した後、レコードが更新される前に [自動増分] 列を使用できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または SQL Azure には当てはまりません。 Id 列の新しい値は、新しいレコードを保存した後にのみ使用できます。  
  
**解決策:** Id フィールドにアクセスする前に、次の Visual Basic for Applications (VBA) コードを実行します。  
  
```  
Recordset.Update  
Recordset.Move 0,  
Recordset.LastModified  
```  
  
### <a name="new-records-are-not-available"></a>新しいレコードは使用できません  
**原因:** VBA を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または SQL Azure テーブルにレコードを追加するときに、テーブルの一意のインデックスフィールドに既定値が設定されていて、そのフィールドに値が割り当てられていない場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または SQL Azure でテーブルを再度開くまで新しいレコードは表示されません。 新しいレコードから値を取得しようとすると、次のエラーメッセージが表示されます。  
  
`Run-time error '3167' Record is deleted.`  
  
**解決策:** VBA コードを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または SQL Azure テーブルを開く場合は、次の例のように `dbSeeChanges` オプションを指定します。  
  
`Set rs = db.OpenRecordset("TestTable", dbOpenDynaset, dbSeeChanges)`  
  
### <a name="after-migration-some-queries-will-not-allow-the-user-to-add-a-new-record"></a>移行後に、ユーザーが新しいレコードを追加することを許可しないクエリもあります。  
**原因:** 一意のインデックスに含まれるすべての列がクエリに含まれていない場合は、クエリを使用して新しい値を追加することはできません。  
  
**解決策:** 少なくとも1つの一意のインデックスに含まれるすべての列がクエリの一部であることを確認します。  
  
### <a name="you-cannot-modify-a-linked-table-schema-with-access"></a>Access を使用してリンクテーブルスキーマを変更することはできません。  
**原因:** データを移行してテーブルをリンクした後、ユーザーは Access のテーブルのスキーマを変更できません。  
  
**解決策:** [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してテーブルスキーマを変更し、[アクセス] のリンクを更新します。  
  
### <a name="hyperlink-functionality-is-lost-after-migrating-data"></a>データの移行後にハイパーリンク機能が失われる  
**原因:** データを移行すると、列内のハイパーリンクの機能が失われ、単純な**nvarchar (max)** 列になります。  
  
**解決策:** 存在.  
  
### <a name="some-sql-server-data-types-are-not-supported-by-access"></a>一部の SQL Server データ型はアクセスでサポートされていません  
**原因:** Access でサポートされていないデータ型が含まれるように、後で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または SQL Azure テーブルを更新する場合は、Access でテーブルを開くことはできません。  
  
**解決策:** サポートされているデータ型の行のみを返すアクセスクエリを定義できます。  
  
## <a name="see-also"></a>参照  
[Access データベースの SQL Server への移行](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
