---
title: ALTER SECURITY POLICY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ALTER_SECURITY_POLICY_TSQL
- ALTER SECURITY POLICY
- ALTER_SECURITY_TSQL
- ALTER SECURITY
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER SECURITY POLICY statement
ms.assetid: a8efc37e-113d-489c-babc-b914fea2c316
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f40c77f8328ee93cd0e1ec8c3b17731060e88288
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="alter-security-policy-transact-sql"></a>セキュリティ ポリシーの変更 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  セキュリティ ポリシーを変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
ALTER SECURITY POLICY schema_name.security_policy_name   
    (  
        { ADD { FILTER | BLOCK } PREDICATE tvf_schema_name.security_predicate_function_name   
           ( { column_name | arguments } [ , …n ] ) ON table_schema_name.table_name   
           [ <block_dml_operation> ]  }   
        | { ALTER { FILTER | BLOCK } PREDICATE tvf_schema_name.new_security_predicate_function_name   
             ( { column_name | arguments } [ , …n ] ) ON table_schema_name.table_name   
           [ <block_dml_operation> ] }  
        | { DROP { FILTER | BLOCK } PREDICATE ON table_schema_name.table_name }   
        | [ <additional_add_alter_drop_predicate_statements> [ , ...n ] ]  
    )    [ WITH ( STATE = { ON | OFF } ]  
    [ NOT FOR REPLICATION ]  
[;]  
  
<block_dml_operation>  
    [ { AFTER { INSERT | UPDATE } }   
    | { BEFORE { UPDATE | DELETE } } ]  
```  
  
## <a name="arguments"></a>引数  
 security_policy_name  
 セキュリティ ポリシーの名前。 セキュリティ ポリシー名は識別子のルールに準拠し、データベースおよびそのスキーマで一意でなければなりません。  
  
 schema_name  
 セキュリティ ポリシーが属するスキーマの名前。 *schema_name* はスキーマのバインドのために必要です。  
  
 [フィルター | ブロック]  
 対象のテーブルにバインドされている関数のセキュリティの述語の型。 サイレント モードで、フィルター述語には、読み取り操作に使用できる行がフィルター処理します。 ブロックは述語述語の関数に違反しているブロックの書き込み操作では明示的にします。  
  
 tvf_schema_name.security_predicate_function_name  
 述語として使用され、ターゲット テーブルに対するクエリで実施されるインライン テーブル値関数。 特定のテーブルの特定の DML 操作に対して定義できるセキュリティ述語の数は 1 つです。 インライン テーブル値関数は、SCHEMABINDING オプションを使用して作成する必要があります。  
  
 { column_name | arguments }  
 セキュリティ述語関数のパラメーターとして使用される列名または式。 ターゲット テーブル上の任意の列を、述語関数の引数として使用できます。 リテラルを含む式、ビルトイン、および算術演算子を使用する式を利用できます。  
  
 *table_schema_name.table_name*  
 セキュリティ述語の適用先となるターゲット テーブル。 複数のセキュリティを無効になっているポリシーの特定の DML 操作では、1 つのテーブルを対象にできますが、任意の時点で、1 つのみを有効にすることができます。  
  
 *\<block_dml_operation>*  
 ブロックの述語を適用する特定の DML 操作します。 結局、DML 操作が実行される (INSERT または UPDATE) 後に、述語、行の値に評価することを指定します。 前に、DML の操作が実行される (更新または削除) する前に、述語は、行の値に評価することを指定します。 操作が指定されていない場合、述語は、すべての操作に適用されます。  
  
 操作は、述語を一意に識別するために使用されるためをブロックの述語を適用する、操作を変更することはできません。 代わりに、述語を削除し、新しい操作の新しいものを追加する必要があります。  
  
 WITH ( STATE = { ON | OFF } )  
 セキュリティ ポリシーによるターゲット テーブルに対するセキュリティ述語の実施を有効または無効にします。 指定しないと、作成されているセキュリティ ポリシーは無効になります。  
  
 NOT FOR REPLICATION  
 レプリケーション エージェントがターゲット オブジェクトを変更するときにセキュリティ ポリシーを実行すべきではないことを示します。 詳細については、「[同期中にトリガと制約の動作を制御する方法 &#40;レプリケーション Transact-SQL プログラミング&#41;](../../relational-databases/replication/control-behavior-of-triggers-and-constraints-in-synchronization.md)」を参照してください。  
  
 table_schema_name.table_name  
 セキュリティ述語の適用先となるターゲット テーブル。 無効な複数のセキュリティ ポリシーは単一テーブルをターゲットにできますが、有効にできるのはどの時点でも 1 つだけです。  
  
## <a name="remarks"></a>Remarks  
 ALTER SECURITY POLICY ステートメントは、トランザクションのスコープ内にあります。 トランザクションがロールバックされると、ステートメントもロールバックされます。  
  
 メモリ最適化テーブルで述語関数を使用する場合、セキュリティ ポリシーには **SCHEMABINDING** が含まれる必要があり、**WITH NATIVE_COMPILATION** コンパイル ヒントを使用する必要があります。 SCHEMABINDING の引数は、すべての述語に適用されるため、ALTER ステートメントを使用して変更できません。 スキーマ バインドを変更するには、削除して、セキュリティ ポリシーを再作成する必要があります。  
  
 ブロックの述語は、対応する DML 操作を実行した後に評価されます。 そのため、READ UNCOMMITTED のクエリでは、ロールバックは一時的な値を確認できます。  
  
## <a name="permissions"></a>アクセス許可  
 ALTER ANY SECURITY POLICY 権限が必要です。  
  
 また、追加される各述語に関しては次のアクセス許可も必要になります。  
  
-   述語として使用している関数に関する SELECT および REFERENCES 権限。  
-   ポリシーにバインドしているターゲット テーブルに対する REFERENCES 権限。  
-   引数として使用しているターゲット テーブルのすべての列に対する REFERENCES 権限。  
  
## <a name="examples"></a>使用例  
 以下の例は、**ALTER SECURITY POLICY** 構文の使用法を示しています。 詳細なセキュリティ ポリシーのシナリオ例については、「[行レベルのセキュリティ](../../relational-databases/security/row-level-security.md)」をご覧ください。  
  
### <a name="a-adding-an-additional-predicate-to-a-policy"></a>A. ポリシーに別の述語を追加する  
 以下の構文はセキュリティ ポリシーを変更します。その際、`mytable` テーブルにフィルター述語を追加します。  
  
```  
ALTER SECURITY POLICY pol1   
    ADD FILTER PREDICATE schema_preds.SecPredicate(column1)   
    ON myschema.mytable;  
```  
  
### <a name="b-enabling-an-existing-policy"></a>B. 既存のポリシーを有効にする  
 以下の例では、ALTER 構文を使用してセキュリティ ポリシーを有効にします。  
  
```  
ALTER SECURITY POLICY pol1 WITH ( STATE = ON );  
```  
  
### <a name="c-adding-and-dropping-multiple-predicates"></a>C. 複数の述語を追加または削除する  
 以下の構文ではセキュリティ ポリシーを変更します。その際、`mytable1` テーブルと `mytable3` テーブルにフィルター述語を追加し、`mytable2` テーブルからフィルター述語を削除します。  
  
```  
ALTER SECURITY POLICY pol1  
ADD FILTER PREDICATE schema_preds.SecPredicate1(column1)   
    ON myschema.mytable1,  
DROP FILTER PREDICATE   
    ON myschema.mytable2,  
ADD FILTER PREDICATE schema_preds.SecPredicate2(column2, 1)   
    ON myschema.mytable3;  
```  
  
### <a name="d-changing-the-predicate-on-a-table"></a>D. テーブルでの述語を変更します。  
 次の構文では、SecPredicate2 関数である mytable テーブルで既存のフィルター述語を変更します。  
  
```  
ALTER SECURITY POLICY pol1  
    ALTER FILTER PREDICATE schema_preds.SecPredicate2(column1)  
        ON myschema.mytable;  
```  
  
### <a name="e-changing-a-block-predicate"></a>E. ブロックの述語を変更します。  
 テーブルで操作のブロックの述語関数を変更します。  
  
```  
ALTER SECURITY POLICY rls.SecPol  
    ALTER BLOCK PREDICATE rls.tenantAccessPredicate_v2(TenantId) 
    ON dbo.Sales AFTER INSERT;  
```  
  
## <a name="see-also"></a>参照  
 [行レベルのセキュリティ](../../relational-databases/security/row-level-security.md)   
 [CREATE SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [DROP SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-security-policy-transact-sql.md)   
 [sys.security_policies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)   
 [sys.security_predicates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)  
  
  
