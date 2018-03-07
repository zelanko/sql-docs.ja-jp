---
title: "ALTER VIEW (Transact SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_VIEW_TSQL
- ALTER VIEW
dev_langs:
- TSQL
helpviewer_keywords:
- indexed views [SQL Server], modifying
- views [SQL Server], modifying
- modifying views
- ALTER VIEW statement
ms.assetid: 03eba220-13e2-49e3-bd9d-ea9df84dc28c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 79d889411d7e974a6ddabd6a753b45f332f1f62a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="alter-view-transact-sql"></a>ALTER VIEW (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  以前に作成されたビューを変更します。 これにはインデックス付きビューが含まれます。 ALTER VIEW は、従属するストアド プロシージャやトリガーに影響を与えず、権限を変更することもありません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ALTER VIEW [ schema_name . ] view_name [ ( column [ ,...n ] ) ]   
[ WITH <view_attribute> [ ,...n ] ]   
AS select_statement   
[ WITH CHECK OPTION ] [ ; ]  
  
<view_attribute> ::=   
{   
    [ ENCRYPTION ]  
    [ SCHEMABINDING ]  
    [ VIEW_METADATA ]       
}   
```  
  
## <a name="arguments"></a>引数  
 *schema_name*  
 ビューが所属するスキーマの名前を指定します。  
  
 *view_name*  
 変更するビューを指定します。  
  
 *列*  
 指定したビューに含まれている列の名前を 1 つ以上指定します。列を複数指定するときは、コンマで区切ります。  
  
> [!IMPORTANT]  
>  列の権限は、ALTER VIEW の実行の前後で列の名前が変わらないときだけ維持されます。  
  
> [!NOTE]  
>  ビューの列では、列名に対する権限は、基底となるデータのソースがどこにあるかにかかわらず、CREATE VIEW ステートメントまたは ALTER VIEW ステートメントを超えて適用されます。 たとえば、アクセス許可が与えられる場合、 **SalesOrderID** CREATE VIEW ステートメントの列で、ALTER VIEW ステートメント名前を変更できます、 **SalesOrderID**など列**OrderRef**、ビューを使用して、関連付けられたアクセス許可も**SalesOrderID**です。  
  
 ENCRYPTION  
 **適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 エントリを暗号化[sys.syscomments](../../relational-databases/system-compatibility-views/sys-syscomments-transact-sql.md) ALTER VIEW ステートメントのテキストが含まれています。 WITH ENCRYPTION を指定すると、そのビューを SQL Server レプリケーションの一部としてパブリッシュできなくなります。  
  
 SCHEMABINDING  
 基になるテーブルのスキーマにビューをバインドします。 SCHEMABINDING を指定すると、ビュー定義に影響する変更をベース テーブルに加えられなくなります。 まずビュー定義を変更または削除して、変更するテーブルとの依存関係を解消する必要があります。 スキーマ バインドを使用すると、 *select_statement* 2 部構成の名前を含める必要があります (*スキーマ***.***オブジェクト*) テーブル、ビュー、またはユーザー定義関数の参照されています。 参照されるオブジェクトは、すべて同じデータベース内にあることが必要です。  
  
 SCHEMABINDING 句を指定して作成されたビューが削除または変更されて、スキーマ バインドがなくならない限り、そのビューに参加しているビューまたはテーブルは削除できません。 スキーマ バインドが残っている場合は、[!INCLUDE[ssDE](../../includes/ssde-md.md)]からエラーが返されます。 また、ALTER TABLE を実行するステートメントをスキーマ バインドを持つビューに参加しているテーブルは、これらのステートメントがビュー定義に影響する場合を失敗します。  
  
 VIEW_METADATA  
 ビューを参照するクエリ用にブラウズ モード メタデータが要求されている場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスは、DB-Library、ODBC、および OLE DB API に対して、ベース テーブルではなくビューに関するメタデータ情報を返します。 ブラウズ モード メタデータとは、[!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスがクライアント側の DB-Library、ODBC、および OLE DB API に返す追加のメタデータです。 クライアント側 API ではこのメタデータによって、更新可能なクライアント側カーソルを実装できます。 ブラウズ モード メタデータには、結果セット内の列が属するベース テーブルの情報が含まれています。  
  
 VIEW_METADATA で作成したビューの場合、ブラウズ モード メタデータでは結果セット内のビューの列の説明で、ベース テーブル名ではなくビュー名が返されます。  
  
 WITH VIEW_METADATA をすべての列を使用して、ビューを作成する場合を除く、**タイムスタンプ**列にいる場合、ビューに INSERT または UPDATE INSTEAD OF トリガーします。 詳細については、「解説」セクションを参照してください。 [CREATE VIEW &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-view-transact-sql.md).  
  
 AS  
 ビューが実行するアクションがあります。  
  
 *select_statement*  
 ビューを定義している SELECT ステートメントを指定します。  
  
 WITH CHECK OPTION  
 強制的にすべてのデータ変更ステートメント内で設定された条件に従うビューに対して実行される*select_statement*です。  
  
## <a name="remarks"></a>解説  
 ALTER VIEW の詳細についてで「解説」を参照してください。 [CREATE VIEW &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-view-transact-sql.md).  
  
> [!NOTE]  
>  以前のビュー定義が WITH ENCRYPTION または CHECK OPTION を使用して作成されている場合、これらのオプションは、ALTER VIEW で指定される場合にのみ有効となります。  
  
 現在使用されているビューを ALTER VIEW を使用して変更する場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] はビューに対して排他スキーマ ロックを設定します。 ロックが許可され、ビューのアクティブ ユーザーがいなくなると、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] はプロシージャ キャッシュからビューのすべてのコピーを削除します。 ビューを参照している既存のプランはキャッシュに残りますが、呼び出されると再コンパイルされます。  
  
 ALTER VIEW は、インデックス付きビューに適用できますが、そのビューのすべてのインデックスを無条件で削除します。  
  
## <a name="permissions"></a>Permissions  
 ALTER VIEW を実行するには、少なくとも OBJECT に対する ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、すべての従業員とその雇用日を含んだ `EmployeeHireDate` というビューを作成します。 ビューには権限が与えられますが、必要条件が変更されて、雇用日が特定の日付よりも古い従業員を選択することになりました。 そこで、`ALTER VIEW` を使用してビューを変更します。  
  
```  
USE AdventureWorks2012 ;  
GO  
CREATE VIEW HumanResources.EmployeeHireDate  
AS  
SELECT p.FirstName, p.LastName, e.HireDate  
FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
ON e.BusinessEntityID = p.BusinessEntityID ;  
GO  
  
```  
  
 ビューは、前に採用した従業員のみを含むように変更する必要があります`2002`です。 ALTER VIEW を使用せずに、ビューを削除して再作成する場合は、以前に使用されていた GRANT ステートメント、およびこのビューに関係する権限を処理するその他すべてのステートメントを再入力する必要があります。  
  
```  
ALTER VIEW HumanResources.EmployeeHireDate  
AS  
SELECT p.FirstName, p.LastName, e.HireDate  
FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
ON e.BusinessEntityID = p.BusinessEntityID  
WHERE HireDate < CONVERT(DATETIME,'20020101',101) ;  
GO  
  
```  
  
## <a name="see-also"></a>参照  
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md)   
 [DROP VIEW &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-view-transact-sql.md)   
 [ストアド プロシージャの作成](../../relational-databases/stored-procedures/create-a-stored-procedure.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [パブリケーション データベースでのスキーマの変更](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  
