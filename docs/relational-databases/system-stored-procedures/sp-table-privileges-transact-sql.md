---
title: "sp_table_privileges (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_table_privileges
- sp_table_privileges_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_table_privileges
ms.assetid: 0512e688-4fc0-4557-8dc8-016672c1e3fe
caps.latest.revision: "36"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 96e042da46762540d510e6d41f275696439f8099
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sptableprivileges-transact-sql"></a>sp_table_privileges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定した 1 つ以上のテーブルに対するテーブル権限 (INSERT、DELETE、UPDATE、SELECT、REFERENCES など) の一覧を返します。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_table_privileges [ @table_name = ] 'table_name'     
     [ , [ @table_owner = ] 'table_owner' ]   
     [ , [ @table_qualifier = ] 'table_qualifier' ]   
     [ , [ @fUsePattern = ] 'fUsePattern' ]  
```  
  
## <a name="arguments"></a>引数  
 [ @table_name=] '*table_name*'  
 カタログ情報を返すために使用するテーブルを指定します。 *table_name*は**nvarchar (**384**)**、既定値はありません。 ワイルドカードによるパターン照合がサポートされています。  
  
 [ @table_owner=] '*table_owner*'  
 カタログ情報を返すために使用するテーブルのテーブル所有者です。 *table_owner*は**nvarchar (**384**)**、既定値は NULL です。 ワイルドカードによるパターン照合がサポートされています。 所有者を指定しない場合は、基になる DBMS の既定のテーブル可視性ルールが適用されます。  
  
 現在のユーザー指定の名前を持つテーブルを所有している場合は、そのテーブルの列が返されます。 場合*所有者*が指定されていない、現在のユーザーが、指定したテーブルを所有していないと*名前*、このプロシージャは、指定したテーブルを探します*table_name*が所有する、データベース所有者です。 そのテーブルが存在する場合、そのテーブルの列が返されます。  
  
 [ @table_qualifier=] '*table_qualifier*'  
 テーブル識別子の名前です。 *table_qualifier*は**sysname**、既定値は NULL です。 さまざまな DBMS 製品は、3 部構成テーブルの名前付けをサポート (*qualifier.owner.name*)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列は、データベースの名前を表します。 一部の製品では、テーブルのデータベース環境のサーバー名を表します。  
  
 [ @fUsePattern=] '*fUsePattern*'  
 アンダー スコア (_)、パーセント (%)、および角かっこ ([または]) の文字がワイルドカードとして解釈されるかどうかを判断します。 有効な値は 0 (パターン一致がオフ) および 1 (パターン一致がオン) です。 *fUsePattern*は**ビット**、既定値は 1 です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|TABLE_QUALIFIER|**sysname**|テーブル修飾子の名前。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列は、データベースの名前を表します。 このフィールドには NULL を指定できます。|  
|TABLE_OWNER|**sysname**|テーブル所有者名です。 このフィールドは常に値を返します。|  
|TABLE_NAME|**sysname**|テーブル名です。 このフィールドは常に値を返します。|  
|GRANTOR|**sysname**|この TABLE_NAME の権限を、表示される GRANTEE に与えたデータベース ユーザーの名前。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、この列は常に TABLE_OWNER と同じです。 このフィールドは常に値を返します。 GRANTOR 列には、データベース所有者 (TABLE_OWNER) が返されます。また、データベース所有者が GRANT ステートメントで WITH GRANT OPTION 句を使用して権限を与えたユーザーが返される場合もあります。|  
|GRANTEE|**sysname**|この TABLE_NAME の権限を、表示される GRANTOR によって与えられたデータベース ユーザーの名前。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列には常に、sys.database_principalssystem ビューからのデータベース ユーザーが含まれています。 このフィールドは常に値を返します。|  
|PRIVILEGE|**sysname**|使用可能なテーブル権限の 1 つ。 テーブル権限は、次に挙げる値 (または実装が定義されるときにデータ ソースによってサポートされるその他の値) のいずれかになります。<br /><br /> SELECT。GRANTEE は、1 列以上のデータを取得できます。<br /><br /> INSERT。GRANTEE は、新しい行の 1 列以上にデータを提供できます。<br /><br /> UPDATE。GRANTEE は、1 列以上の既存のデータを修正できます。<br /><br /> DELETE。GRANTEE は、テーブルから行を削除できます。<br /><br /> REFERENCES。GRANTEE は、主キー/外部キーのリレーションシップで外部テーブル内の列を参照できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、主キー/外部キーのリレーションシップはテーブル制約で定義されます。<br /><br /> 特定のテーブル特権によって GRANTEE に与えられる操作の範囲は、データ ソースに依存します。 たとえば、UPDATE 特権の場合、GRANTEE は、あるデータ ソース上ではテーブルのすべての列を更新することが許可されても、別のデータ ソース上では、GRANTOR が UPDATE 特権を持っている列しか更新できないことがあります。|  
|IS_GRANTABLE|**sysname**|GRANTEE が他のユーザーに権限を与えることが許可されているかどうかを示します。これは "許可の許可" 権限とも呼ばれます。 YES、NO、NULL のいずれかになります。 不明 (つまり NULL) の値は、"許可の許可" が適用されないデータ ソースを示します。|  
  
## <a name="remarks"></a>解説  
 sp_table_privileges ストアド プロシージャは、ODBC の SQLTablePrivileges に相当します。 返される結果は、TABLE_QUALIFIER、TABLE_OWNER、TABLE_NAME、PRIVILEGE の値に従って並べ替えられます。  
  
## <a name="permissions"></a>Permissions  
 スキーマに対する SELECT 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、すべてのテーブルに関する特権情報を返しますという単語で始まる名前を持つ`Contact`します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_table_privileges   
   @table_name = 'Contact%';  
```  
  
## <a name="see-also"></a>参照  
 [カタログのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
