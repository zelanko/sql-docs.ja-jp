---
title: sp_stored_procedures (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_stored_procedures_TSQL
- sp_stored_procedures
dev_langs:
- TSQL
helpviewer_keywords:
- sp_stored_procedures
ms.assetid: fe52dd83-000a-4665-83fb-7a0024193dec
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 001a3476555b82c5262af4ff59cd70f5b88a0c5e
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43024668"
---
# <a name="spstoredprocedures-transact-sql"></a>sp_stored_procedures (Transact-SQL)
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
 [ **@sp_name =** ] **'***name***'**  
 カタログ情報を返すために使用するプロシージャの名前を指定します。 *名前*は**nvarchar (390)**、既定値は NULL です。 ワイルドカードによるパターン照合がサポートされています。  
  
 [  **@sp_owner =** ] **'***スキーマ***'**  
 プロシージャが所属するスキーマの名前です。 *スキーマ*は**nvarchar (384)**、既定値は NULL です。 ワイルドカードによるパターン照合がサポートされています。 場合*所有者*が指定されていない、基になる DBMS の既定のプロシージャの可視性規則が適用されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、指定した名前のプロシージャが現在のスキーマに含まれている場合、そのプロシージャが返されます。 修飾名なしでストアド プロシージャを指定した場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]では次の順序でプロシージャが検索されます。  
  
-   現在のデータベースの **sys** スキーマ。  
  
-   バッチまたは動的 SQL で実行された場合は、呼び出し側の既定のスキーマ。修飾名なしのプロシージャ名が別のプロシージャ定義内にある場合は、そのプロシージャを含むスキーマが次に検索されます。  
  
-   現在のデータベースの **dbo** スキーマ。  
  
 [  **@qualifier =** ] **'***修飾子***'**  
 プロシージャ修飾子の名前を指定します。 *修飾子*は**sysname**、既定値は NULL です。 さまざまな DBMS 製品は、3 つの部分は、フォーム内のテーブルの名前付けをサポート (*修飾子 ***.*** スキーマ ***.*** 名前*します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、*修飾子*データベース名を表します。 製品によっては、テーブルのデータベース環境のサーバー名を表す場合があります。  
  
 [  **@fUsePattern =** ] **'***fUsePattern***'**  
 アンダースコア (_)、パーセント (%)、かっこ ([ ]) をワイルドカード文字として解釈するかどうかを指定します。 *fUsePattern*は**ビット**、既定値は 1 です。  
  
 **0** = パターン照合はオフです。  
  
 **1** = パターン一致がオン。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**PROCEDURE_QUALIFIER**|**sysname**|プロシージャ修飾子の名前。 この列は、NULL の場合もあります。|  
|**PROCEDURE_OWNER**|**sysname**|プロシージャ所有者の名前。 この列は、常に値を返します。|  
|**PROCEDURE_NAME**|**nvarchar(134)**|プロシージャの名前。 この列は、常に値を返します。|  
|**NUM_INPUT_PARAMS**|**int**|将来使用するために予約されています。|  
|**NUM_OUTPUT_PARAMS**|**int**|将来使用するために予約されています。|  
|**NUM_RESULT_SETS**|**int**|将来使用するために予約されています。|  
|**「解説」**|**varchar(254)**|プロシージャの説明。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] この列の値は返されません。|  
|**PROCEDURE_TYPE**|**smallint**|プロシージャの種類。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は常に 2.0 を返します。 この値は次のいずれかになります。<br /><br /> 0 = SQL_PT_UNKNOWN<br /><br /> 1 = SQL_PT_PROCEDURE<br /><br /> 2 = SQL_PT_FUNCTION|  
  
## <a name="remarks"></a>コメント  
 相互運用性を最大限に高めるために、ゲートウェイのクライアントでは、SQL 標準のパターン照合 (パーセント (%) とアンダースコア (_) ワイルドカード文字) のみを前提としています。  
  
 特定のストアド プロシージャに対する、現在のユーザーの実行アクセスについての権限情報は必ずしもチェックされないため、アクセスは保証されません。 また、3 つの要素で構成される名前だけが使用されることに注意してください。 つまり、ローカル ストアド プロシージャのみ必要とする 4 部構成の名前付け) リモート ストアド プロシージャが返されるに対して実行したときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 かどうか、サーバー属性 ACCESSIBLE_SPROC が Y の結果セットで**sp_server_info**、現在のユーザーによって実行できるストアド プロシージャのみが返されます。  
  
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
  
  
