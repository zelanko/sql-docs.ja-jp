---
title: sp_scriptdynamicupdproc (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_scriptdynamicupdproc_TSQL
- sp_scriptdynamicupdproc
helpviewer_keywords:
- sp_scriptdynamicupdproc
ms.assetid: b4c18863-ed92-4aa2-a04f-7ed832fc9e07
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b548223d520696f7c7a2b48f4010247666d41597
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spscriptdynamicupdproc-transact-sql"></a>sp_scriptdynamicupdproc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  動的な更新ストアド プロシージャを作成する CREATE PROCEDURE ステートメントを生成します。 カスタム ストアド プロシージャ内の UPDATE ステートメントは、変更する列を示す MCALL 構文に基づいて動的に構築されます。 このストアド プロシージャは、サブスクライブの対象となるテーブルのインデックスの数が増加し、変更される列の数が少ない場合に使用します。 このストアド プロシージャは、パブリケーション データベースのパブリッシャーで実行します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_scriptdynamicupdproc [ @artid =] artid  
```  
  
## <a name="arguments"></a>引数  
 [  **@artid=**] *artid*  
 アーティクルの ID を指定します。 *artid*は**int**、既定値はありません。  
  
## <a name="result-sets"></a>結果セット  
 1 つので構成される結果セットを返します**nvarchar (4000)**列です。 この結果セットは、カスタム ストアド プロシージャの作成に使用される完全な CREATE PROCEDURE ステートメントを構成します。  
  
## <a name="remarks"></a>解説  
 **sp_scriptdynamicupdproc**トランザクション レプリケーションで使用します。 既定の MCALL スクリプト作成ロジックでは、UPDATE ステートメント内のすべての列を対象に、ビットマップを使用して、変更された列が特定されます。 列が変更されていなかった場合、列は元に戻され、通常は問題は発生しません。 列にインデックスが作成されている場合、追加の処理が発生します。 動的な処理では変更された列だけが対象になり、最適な UPDATE 文字列が提供されます。 ただし、動的な UPDATE ステートメントが構築されると、実行時に追加の処理が発生します。 動的な方法と静的な方法の両方をテストし、最適な方を選択することをお勧めします。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_scriptdynamicupdproc**です。  
  
## <a name="examples"></a>使用例  
 この例は、アーティクルを作成 (で*artid* 'éý' **1**) で、**作成者**テーブルに、 **pubs**データベースにありことを指定、更新プログラムステートメントが、カスタム プロシージャを実行します。  
  
```  
'MCALL sp_mupd_authors'  
```  
  
 パブリッシャー側で次のストアド プロシージャを実行し、サブスクライバー側のディストリビューション エージェントで実行するカスタム ストアド プロシージャを生成します。  
  
```  
EXEC sp_scriptdynamicupdproc @artid = '1'  
  
The statement returns:  
  
CREATE PROCEDURE [sp_mupd_authors]   
  @c1 varchar(11),@c2 varchar(40),@c3 varchar(20),@c4 char(12),@c5 varchar(40),@c6 varchar(20),  
  @c7 char(2),@c8 char(5),@c9 bit,@pkc1 varchar(11),@bitmap binary(2)  
as  
  
declare @stmt nvarchar(4000), @spacer nvarchar(1)  
SELECT @spacer =N''  
SELECT @stmt = N'UPDATE [authors] SET '  
  
if substring(@bitmap,1,1) & 2 = 2  
begin  
  select @stmt = @stmt + @spacer + N'[au_lname]' + N'=@2'  
  select @spacer = N','  
end  
if substring(@bitmap,1,1) & 4 = 4  
begin  
  select @stmt = @stmt + @spacer + N'[au_fname]' + N'=@3'  
  select @spacer = N','  
end  
if substring(@bitmap,1,1) & 8 = 8  
begin  
  select @stmt = @stmt + @spacer + N'[phone]' + N'=@4'  
  select @spacer = N','  
end  
if substring(@bitmap,1,1) & 16 = 16  
begin  
  select @stmt = @stmt + @spacer + N'[address]' + N'=@5'  
  select @spacer = N','  
end  
if substring(@bitmap,1,1) & 32 = 32  
begin  
  select @stmt = @stmt + @spacer + N'[city]' + N'=@6'  
  select @spacer = N','  
end  
if substring(@bitmap,1,1) & 64 = 64  
begin  
  select @stmt = @stmt + @spacer + N'[state]' + N'=@7'  
  select @spacer = N','  
end  
if substring(@bitmap,1,1) & 128 = 128  
begin  
  select @stmt = @stmt + @spacer + N'[zip]' + N'=@8'  
  select @spacer = N','  
end  
if substring(@bitmap,2,1) & 1 = 1  
begin  
  select @stmt = @stmt + @spacer + N'[contract]' + N'=@9'  
  select @spacer = N','  
end  
select @stmt = @stmt + N' where [au_id] = @1'  
exec sp_executesql @stmt, N' @1 varchar(11),@2 varchar(40),@3 varchar(20),@4 char(12),@5 varchar(40),  
                             @6 varchar(20),@7 char(2),@8 char(5),@9 bit',@pkc1,@c2,@c3,@c4,@c5,@c6,@c7,@c8,@c9  
  
if @@rowcount = 0  
   if @@microsoftversion>0x07320000  
      exec sp_MSreplraiserror 20598  
```  
  
 このストアド プロシージャを実行した後、結果のスクリプトを使用して、サブスクライバー側で手動でストアド プロシージャを作成できます。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
