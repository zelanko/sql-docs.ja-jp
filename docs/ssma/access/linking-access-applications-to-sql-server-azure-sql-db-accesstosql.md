---
title: SQL Server - Azure SQL DB への Access アプリケーションのリンク |Microsoft Docs
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
ms.openlocfilehash: 115aa0db8e8d6f2fdc35718ccb60f1d0ed06b5c1
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68259898"
---
# <a name="linking-access-applications-to-sql-server---azure-sql-db-accesstosql"></a>SQL Server - Azure SQL DB (AccessToSQL) への Access アプリケーションのリンク
既存の Access アプリケーションを使用したいかどうか[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、元の Access テーブルをリンクするには、移行後に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure テーブル。 クエリ、フォーム、レポート、およびデータ アクセス ページ内のデータを使用するように、Access データベースを変更するリンク、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または Access データベース内のデータではなく SQL Azure データベース。  
  
> [!NOTE]  
> テーブルにアクセスするにはアクセスに残りますが、と共には更新されません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure で更新します。 テーブルをリンクする機能を確認すると、Access のテーブルを削除する場合があります。  
  
## <a name="linking-access-and-sql-server-tables"></a>アクセスと SQL Server のテーブルをリンクします。  
アクセス テーブルをリンクすると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続情報とテーブルのメタデータに Jet データベース エンジン、SQL Azure テーブルが格納されますでのデータが格納されているまたは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure です。 このリンクにより、Access アプリケーションは、場合でも、実際のテーブルとデータ アクセス テーブルに対して動作[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure です。  
  
> [!NOTE]  
> 使用する場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証、パスワードがクリア テキストで、リンクされた Access のテーブルに格納されています。 Windows 認証を使用することをお勧めします。  
  
**テーブルをリンクするには**  
  
1.  アクセス メタデータ エクスプ ローラーで、リンク先のテーブルを選択します。  
  
2.  右クリックして**テーブル**、し、**リンク**します。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) のアクセスは、元の Access テーブルをバックアップし、リンク テーブルを作成します。  
  
テーブルをリンクした後は、小さなリンク アイコンが付いた SSMA でテーブルが表示されます。 Access では、テーブルを指し示す矢印の付いた世界中である「リンク先」アイコンが表示されます。  
  
テーブルを開くには、Access で、キーセット カーソルを使用して、データが取得されます。 その結果、大規模なテーブルのすべてのデータは取得されません一度に 1 つ。 ただし、テーブルを参照すると、アクセスは必要に応じて、追加のデータを取得します。  
  
> [!IMPORTANT]  
> Azure のデータベースとテーブルにアクセスをリンクするには、SQL Server ネイティブ Client(SNAC) バージョン 10.5 が必要です。 以上。   
> SNAC の最新バージョンを取得する[Microsoft® SQL Server® 2008 R2 用 Feature Pack](https://go.microsoft.com/fwlink/?LinkId=196940)します。  
  
## <a name="unlinking-access-tables"></a>テーブルにアクセスするリンク解除  
Access テーブルからのリンクを解除するときに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure テーブル、SSMA が元の Access テーブルとそのデータを復元します。  
  
**テーブルのリンクを解除するには**  
  
1.  アクセス メタデータ エクスプ ローラーで、リンクを解除するテーブルを選択します。  
  
2.  右クリック**テーブル**、し、 **Unlink**します。  
  
## <a name="linking-tables-to-a-different-server"></a>別のサーバーへのリンク テーブル  
Access テーブルを 1 つの SQL Server インスタンスにリンクした後で別のインスタンスにリンクを変更する場合は、テーブルをリンクする必要があります。  
  
**別のサーバーにテーブルをリンクするには**  
  
1.  アクセス メタデータ エクスプ ローラーで、リンクを解除するテーブルを選択します。  
  
2.  右クリック**テーブル**選び**Unlink**。  
  
3.  をクリックして、 **SQL Server に再接続**ボタンをクリックします。  
  
4.  インスタンスに接続[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure の Access テーブルをリンクします。  
  
5.  アクセス メタデータ エクスプ ローラーで、リンク先のテーブルを選択します。  
  
6.  右クリックして**テーブル**、し、**リンク**します。  
  
## <a name="updating-linked-tables"></a>リンク テーブルを更新しています  
場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Azure テーブルの定義が変更されるか、リンクを解除し、このトピックで前に示した手順を使用して SSMA でテーブルを再リンクすることができます。 アクセスを使用して、テーブルを更新することもできます。  
  
**アクセスを使用して、リンク テーブルを更新するには**  
  
1.  Access データベースを開きます。  
  
2.  **オブジェクト**一覧で、**テーブル**します。  
  
3.  リンク テーブルを右クリックし、**リンク テーブル マネージャー**します。  
  
4.  更新、およびクリックするリンクされた各テーブルの横にあるチェック ボックスをオン**OK**します。  
  
## <a name="possible-post-migration-issues"></a>移行後の考えられる問題  
以下のセクションでリストの問題へのアクセスからデータベースを移行した後は、既存の Access アプリケーションで発生する可能性を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure と共に、原因と解決方法は、テーブルにリンクします。  
  
### <a name="slow-performance-with-linked-tables"></a>リンク テーブルのパフォーマンスの低下  
**原因:** 一部のクエリがあります低速アップサイズ後、次の理由。  
  
-   アプリケーションに存在しない関数に依存して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure は、SELECT クエリを実行するには、ローカル テーブルのプルダウン Jet を発生します。  
  
-   更新または多くの行を削除するクエリは、行ごとに、Jet によって、パラメーター化クエリとして送信されます。  
  
**解決方法:** パススルー クエリ、ストアド プロシージャ、またはビューには、実行速度の遅いクエリを変換します。 パススルー クエリに変換するには、次の問題があります。  
  
-   パススルー クエリを変更することはできません。 クエリの結果を変更または新しいレコードを追加する必要があります、別の方法でなど、明示的な**変更**または**追加**クエリにバインドされているフォーム上のボタン。  
  
-   一部のクエリは、ユーザー入力を必要とは、パススルー クエリはユーザー入力をサポートしていません。 Visual Basic for Applications (VBA) コード、パラメーターの入力を求めるか、入力コントロールとして使用される形式は、ユーザー入力を取得できます。 どちらの場合では、VBA コードは、ユーザー入力に、サーバーにクエリを送信します。  
  
### <a name="auto-increment-columns-are-not-updated-until-the-record-is-updated"></a>レコードが更新されるまで、自動インクリメント列は更新されません。  
**原因:** Jet で RecordSet.AddNew を呼び出した後、レコードが更新される前に、自動インクリメント列は使用できます。 True でない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure です。 Id 列の新しい値の新しい値は、新しいレコードを保存した後にのみ使用可能なは。  
  
**解決方法:** Id フィールドにアクセスする前に、次の Visual Basic for Applications (VBA) コードを実行します。  
  
```  
Recordset.Update  
Recordset.Move 0,  
Recordset.LastModified  
```  
  
### <a name="new-records-are-not-available"></a>新しいレコードは使用できません。  
**原因:** レコードを追加すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または VBA を使用して、テーブルの一意のインデックスのフィールドが既定値と割り当てない値、そのフィールドに新しいレコードが表示されないのテーブルを再び開くまで、SQL Azure テーブル[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure です。 新しいレコードから値を取得しようとすると、次のエラー メッセージが表示されます。  
  
`Run-time error '3167' Record is deleted.`  
  
**解決方法:** 開くと、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または VBA コードを使用してテーブルでは、SQL Azure、`dbSeeChanges`次の例のように、オプション。  
  
`Set rs = db.OpenRecordset("TestTable", dbOpenDynaset, dbSeeChanges)`  
  
### <a name="after-migration-some-queries-will-not-allow-the-user-to-add-a-new-record"></a>一部のクエリが新しいレコードを追加するユーザーをできません、移行後  
**原因:** クエリに一意のインデックスに含まれているすべての列が含まれていない場合、クエリを使用して新しい値を追加することはできません。  
  
**解決方法:** 少なくとも 1 つの一意のインデックスに含まれるすべての列がクエリの一部であることを確認します。  
  
### <a name="you-cannot-modify-a-linked-table-schema-with-access"></a>アクセス権を持つリンク テーブルのスキーマを変更することはできません。  
**原因:** データの移行およびリンク テーブルでは、後に、ユーザーは、Access のテーブルのスキーマを変更できません。  
  
**解決方法:** 使用して、テーブル スキーマを変更[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、し、Access でのリンクを更新します。  
  
### <a name="hyperlink-functionality-is-lost-after-migrating-data"></a>移行した後、ハイパーリンク機能が失われたデータ  
**原因:** 移行後にデータ、列内のハイパーリンクは、機能が失われ、シンプルになり**nvarchar (max)** 列。  
  
**解決方法:** [なし] :  
  
### <a name="some-sql-server-data-types-are-not-supported-by-access"></a>アクセスでは、一部の SQL Server データ型はサポートされていません。  
**原因:** 後で更新する場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure テーブルへのアクセスでサポートされていないデータ型を格納するテーブルをアクセスで開くことができません。  
  
**解決方法:** サポートされているデータ型を持つ行だけを返すアクセス クエリを定義できます。  
  
## <a name="see-also"></a>関連項目  
[SQL Server へのアクセス データベースの移行](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
