---
title: sp_db_vardecimal_storage_format (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_db_vardecimal_storage_format
- sp_db_vardecimal_storage_format_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_db_vardecimal_storage_format
- decimal data type, compressing
- compressing decimal data
- numeric data type, compressing
- database compression [SQL Server]
- table compression [SQL Server]
ms.assetid: 9920b2f7-b802-4003-913c-978c17ae4542
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6bd4332bcb13b306fb49b82dac2ed1c49ecc837b
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43024169"
---
# <a name="spdbvardecimalstorageformat-transact-sql"></a>sp_db_vardecimal_storage_format (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベースの vardecimal ストレージ形式の現在の状態を返します。または、データベースで vardecimal ストレージ形式を有効にします。  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降では、ユーザー データベースは常に有効になります。 データベースで必要なは、vardecimal ストレージ形式を有効化[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]します。  
  
> [!IMPORTANT]  
>  データベースの vardecimal ストレージ形式の状態を変更すると、バックアップとリカバリ、データベース ミラーリング、sp_attach_db、ログ配布、レプリケーションに影響が生じることがあります。  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_db_vardecimal_storage_format [ [ @dbname = ] 'database_name']   
    [ , [ @vardecimal_storage_format = ] { 'ON' | 'OFF' } ]   
[;]  
```  
  
## <a name="arguments"></a>引数  
 [ @dbname=] '*database_name*'  
 ストレージ形式を変更するデータベースの名前を指定します。 *database_name*は**sysname**、既定値はありません。 Vardecimal ストレージ形式のインスタンスのすべてのデータベースの状態をデータベース名を省略すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が返されます。  
  
 [ @vardecimal_storage_format=] {'ON' |'オフ '}  
 vardecimal ストレージ形式を有効にするかどうかを指定します。 @vardecimal_storage_format を ON または OFF にできます。 パラメーターが**varchar (3)**、既定値はありません。 データベース名が指定されている場合、@vardecimal_storage_formatは省略すると、指定されたデータベースの現在の設定が返されます。 この引数は、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンには影響しません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 データベースのストレージ形式を変更できない場合、sp_db_vardecimal_storage_format はエラーを返します。 データベースが既に指定した状態にある場合、ストアド プロシージャによる影響はありません。  
  
 場合、@vardecimal_storage_format引数が指定されていない、データベース名と Vardecimal State 列が返されます。  
  
## <a name="remarks"></a>コメント  
 sp_db_vardecimal_storage_format は vardecimal 状態を返しますが、vardecimal 状態を変更することはできません。  
  
 次の場合、sp_db_vardecimal_storage_format は失敗します。  
  
-   データベースにアクティブなユーザーがいる場合  
  
-   データベースのミラーリングが有効である場合  
  
-   エディション[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は vardecimal ストレージ形式をサポートしていません。  
  
 vardecimal ストレージ形式の状態を OFF に変更するには、データベースを単純復旧モードに設定する必要があります。 データベースを単純復旧モードに設定した場合、ログ チェーンは分断されます。 vardecimal ストレージ形式の状態を OFF に設定した後は、完全データベース バックアップを実行してください。  
  
 vardecimal データベース圧縮を使用しているテーブルがある場合、状態を OFF に変更しようとすると失敗します。 テーブルのストレージ形式を変更する[sp_tableoption](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)します。 データベースのテーブルが vardecimal ストレージ形式を使用しているかどうかを調べるには、次の例のように `OBJECTPROPERTY` 関数を使用して `TableHasVarDecimalStorageFormat` プロパティを探します。  
  
```  
USE AdventureWorks2012 ;  
GO  
SELECT name, object_id, type_desc  
FROM sys.objects   
 WHERE OBJECTPROPERTY(object_id,   
   N'TableHasVarDecimalStorageFormat') = 1 ;  
GO  
```  
  
## <a name="examples"></a>使用例  
 次のコードでは、`AdventureWorks2012` データベースで圧縮を有効にして状態を確認した後、`Sales.SalesOrderDetail` テーブルの decimal 列と numeric 列を圧縮します。  
  
```  
USE master ;  
GO  
  
EXEC sp_db_vardecimal_storage_format 'AdventureWorks2012', 'ON' ;  
GO  
  
-- Check the vardecimal storage format state for  
-- all databases in the instance.  
EXEC sp_db_vardecimal_storage_format ;  
GO  
  
USE AdventureWorks2012 ;  
GO  
  
EXEC sp_tableoption 'Sales.SalesOrderDetail', 'vardecimal storage format', 1 ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
