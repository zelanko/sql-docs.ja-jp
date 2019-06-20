---
title: sp_stored_procedures (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_stored_procedures_TSQL
- sp_stored_procedures
dev_langs:
- TSQL
helpviewer_keywords:
- sp_stored_procedures
ms.assetid: fe52dd83-000a-4665-83fb-7a0024193dec
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ff94284ba1f60d40697ad5a1e209b284dfaaefdf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63005868"
---
# <a name="spstoredprocedures-transact-sql"></a>sp_stored_procedures (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在の環境内にあるストアド プロシージャの一覧を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_stored_procedures [ [ @sp_name = ] 'name' ]   
    [ , [ @sp_owner = ] 'schema']   
    [ , [ @sp_qualifier = ] 'qualifier' ]  
    [ , [@fUsePattern = ] 'fUsePattern' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @sp_name = ] 'name'` カタログ情報を返すために使用するプロシージャの名前です。 *名前*は**nvarchar (390)** 、既定値は NULL です。 ワイルドカードによるパターン照合はサポートされています。  
  
`[ @sp_owner = ] 'schema'` プロシージャが所属するスキーマの名前です。 *スキーマ*は**nvarchar (384)** 、既定値は NULL です。 ワイルドカードによるパターン照合はサポートされています。 場合*所有者*が指定されていない、基になる DBMS の既定のプロシージャの可視性規則が適用されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、指定した名前のプロシージャが現在のスキーマに含まれている場合、そのプロシージャが返されます。 修飾名なしでストアド プロシージャを指定した場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]では次の順序でプロシージャが検索されます。  
  
-   現在のデータベースの **sys** スキーマ。  
  
-   バッチまたは動的 sql を実行する場合、呼び出し元の既定のスキーマまたは、そのプロシージャを含むスキーマが次に検索して別のプロシージャ定義の本体内で、プロシージャの非修飾名が表示された場合。  
  
-   現在のデータベースの **dbo** スキーマ。  
  
`[ @qualifier = ] 'qualifier'` プロシージャ修飾子の名前です。 *修飾子*は**sysname**、既定値は NULL です。 さまざまな DBMS 製品は、3 つの部分は、フォーム内のテーブルの名前付けをサポート (_修飾子_ **.** _スキーマ_ **.** _名前_します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、*修飾子*データベース名を表します。 一部の製品で、テーブルのデータベース環境のサーバー名を表します。  
  
`[ @fUsePattern = ] 'fUsePattern'` 決定かどうか、アンダー スコア (_)、パーセント (%)、または角かっこ) はワイルドカード文字として解釈されます。 *fUsePattern*は**ビット**、既定値は 1 です。  
  
 **0** = パターン照合はオフです。  
  
 **1** = パターン一致がオン。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**PROCEDURE_QUALIFIER**|**sysname**|プロシージャ修飾子の名前。 この列は NULL を指定できます。|  
|**PROCEDURE_OWNER**|**sysname**|プロシージャ所有者の名前。 この列は常に値が返されます。|  
|**PROCEDURE_NAME**|**nvarchar(134)**|プロシージャの名前。 この列は常に値が返されます。|  
|**NUM_INPUT_PARAMS**|**int**|将来使用するために予約されています。|  
|**NUM_OUTPUT_PARAMS**|**int**|将来使用するために予約されています。|  
|**NUM_RESULT_SETS**|**int**|将来使用するために予約されています。|  
|**REMARKS**|**varchar(254)**|プロシージャの説明。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] この列の値は返されません。|  
|**PROCEDURE_TYPE**|**smallint**|プロシージャの種類。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は常に 2.0 を返します。 この値には、次のいずれかを指定できます。<br /><br /> 0 = SQL_PT_UNKNOWN<br /><br /> 1 = SQL_PT_PROCEDURE<br /><br /> 2 = SQL_PT_FUNCTION|  
  
## <a name="remarks"></a>コメント  
 相互運用性を最大限に高めるために、ゲートウェイのクライアントでは、SQL 標準のパターン照合 (パーセント (%) とアンダースコア (_) ワイルドカード文字) のみを前提としています。  
  
 アクセス許可については、現在のユーザーは、必ずしもチェックされない; の特定のストアド プロシージャへのアクセスを実行します。そのため、アクセスは保証されません。 3 つの部分の名前のみが使用されることに注意してください。 つまり、ローカル ストアド プロシージャのみ必要とする 4 部構成の名前付け) リモート ストアド プロシージャが返されるに対して実行したときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 かどうか、サーバー属性 ACCESSIBLE_SPROC が Y の結果セットで**sp_server_info**、現在のユーザーによって実行できるストアド プロシージャのみが返されます。  
  
 **sp_stored_procedures**と等価**SQLProcedures** ODBC にします。 返される結果は並べ**PROCEDURE_QUALIFIER**、 **PROCEDURE_OWNER**、および**PROCEDURE_NAME**します。  
  
## <a name="permissions"></a>アクセス許可  
 スキーマに対する SELECT 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-all-stored-procedures-in-the-current-database"></a>A. 現在のデータベース内のすべてのストアド プロシージャを返す  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベース内のすべてのストアド プロシージャを返します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_stored_procedures;  
```  
  
### <a name="b-returning-a-single-stored-procedure"></a>B. 1 つのストアド プロシージャを返す  
 次の例は、結果のセットを返します、`uspLogError`ストアド プロシージャ。  
  
```  
USE AdventureWorks2012;  
GO  
sp_stored_procedures N'uspLogError', N'dbo', N'AdventureWorks2012', 1;  
```  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャ カタログ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
