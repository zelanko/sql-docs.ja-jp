---
title: "規則 (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RULE_TSQL
- CREATE RULE
- CREATE_RULE_TSQL
- RULE
dev_langs:
- TSQL
helpviewer_keywords:
- list rules [SQL Server]
- unbinding rules
- pattern rules [SQL Server]
- range rules [SQL Server]
- alias data types [SQL Server], rules
- CREATE RULE statement
- reports [SQL Server], rules
- status information [SQL Server], rules
- rules [SQL Server], precedence
- binding rules [SQL Server]
- rules [SQL Server], creating
ms.assetid: b016a289-3a74-46b1-befc-a13183be51e4
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 69cbf3b35533d0a77ae303c79040da7cb0883a4b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="create-rule-transact-sql"></a>CREATE RULE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ルールと呼ばれるオブジェクトを作成します。 ルールを列または別名データ型にバインドすると、その列に挿入できる適切な値を制限できます。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代わりに check 制約を使用することをお勧めします。 CHECK 制約は、CREATE TABLE または ALTER TABLE の CHECK キーワードを使用して作成します。 詳細については、「 [Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md)」を参照してください。  
  
 1 つの列または別名データ型にバインドできるルールは 1 つだけです。 ただし、1 つの列には 1 つのルールと複数の CHECK 制約を関連付けることができます。 この場合、すべての制限が評価されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE RULE [ schema_name . ] rule_name   
AS condition_expression  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *schema_name*  
 ルールが属しているスキーマの名前を指定します。  
  
 *rule_name*  
 新しいルールの名前を指定します。 規則名は、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。 ルールの所有者名の指定は省略可能です。  
  
 *condition_expression*  
 ルールを定義する条件を指定します。 ルールには、WHERE 句で有効な任意の式を指定できます。また、算術演算子、関係演算子、述語 (IN、LIKE、BETWEEN など) のような要素も使用できます。 ルールでは、列や別のデータベース オブジェクトを参照することはできません。 データベース オブジェクトを参照しない組み込み関数は含めることができます。 またユーザー定義関数は使用できません。  
  
 *condition_expression* 1 つの変数が含まれています。 アット マーク (**@**) 各ローカル変数の前にします。 指定する式は、UPDATE または INSERT ステートメントで入力された値を参照します。 任意の名前または記号は、そのルールを作成するときに、値を表すために使用できますが、最初の文字である必要があります、アット マーク (**@**)。  
  
> [!NOTE]  
>  別名データ型を使用する式にルールを作成することはお勧めできません。 別名データ型を使用する式にルールを作成することはできますが、ルールを列または別名データ型にバインドすると、参照時にこの式は失敗します。  
  
## <a name="remarks"></a>解説  
 規則の作成は、その他と組み合わせることはできません[!INCLUDE[tsql](../../includes/tsql-md.md)]1 つのバッチ内のステートメント。 ルールを作成した時点では、データベース内の既存のデータにルールは適用されません。また、ルールをシステム データ型にバインドすることはできません。  
  
 ルールは、現在のデータベース内でのみ作成できます。 ルールを作成する実行**sp_bindrule**に列または別名データ型にルールをバインドします。 ルールと列のデータ型の間には互換性がとれている必要があります。 たとえば、"@valueなどの %"、数値列のルールとして使用できません。 ルールをバインドできません、**テキスト**、 **ntext**、**イメージ**、 **varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、 **xml**、CLR ユーザー定義型、または**タイムスタンプ**列です。 また、計算列にもバインドできません。  
  
 文字および日付定数は、必ず単一引用符 (') で囲み、バイナリ定数は 0x で始めてください。 ルールがバインド先の列と互換性がない場合、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ルールがバインドされているときではなく、値が挿入されると、エラー メッセージが返されます。  
  
 別名データ型にバインドされたルールは、別名データ型のデータベース列に値を挿入するとき、または列を更新するときにのみアクティブになります。 ルールでは変数はテストされないため、別名データ型変数には、同じデータ型の列にバインドしたルールによって拒否されるような値を割り当てないでください。  
  
 ルールに関するレポートを取得する**sp_help**です。 ルールのテキストを表示するには実行**sp_helptext**ルール名、パラメーターを使用します。 ルールの名前を変更するには使用**sp_rename**です。  
  
 DROP RULE、同じ名前で新しいレコードが作成され、ルールがバインドされていないときにする必要がありますを使用してルールを削除する必要があります**sp_unbindrule**が削除される前にします。 列のルールをバインド解除するには使用**sp_unbindrule**です。  
  
 以前のルールのバインドを解除せずに、新しいルールを列またはデータ型にバインドすることができます。新しいルールは以前のルールよりも優先されます。 列にバインドされているルールは、別名データ型にバインドされているルールよりも常に優先されます。 ルールを列にバインドすると、その列の別名データ型に既にバインドされていたルールは新しいルールに置き換えられますが、 ルールをデータ型にバインドしても、その別名データ型の列にバインドされていたルールは新しいルールに置き換えられません。 次の表は、ルールが既に存在する列および別名データ型にルールをバインドするときの優先順位です。  
  
|新しいルールのバインド先|前のルールのバインド先が<br /><br /> 別名データ型の場合|前のルールのバインド先が<br /><br /> 列|  
|-----------------------|-------------------------------------------|----------------------------------|  
|別名データ型|前のルールが置き換えられる|変更はありません。|  
|列|前のルールが置き換えられる|前のルールが置き換えられる|  
  
 列に既定値とルールの両方が関連付けられている場合、既定値はルールによって定義されるドメイン内のものであることが必要です。 ルールに反する既定値は挿入されません。 SQL Server データベース エンジンでは、既定値の挿入が試行されるたびにエラー メッセージが生成されます。  
  
## <a name="permissions"></a>Permissions  
 CREATE RULE を実行するには、少なくとも現在のデータベースの CREATE RULE 権限と、ルールを作成するスキーマの ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-rule-with-a-range"></a>A. 範囲を指定してルールを作成する  
 次の例で作成するルールは、ルールのバインド先となる列に挿入できる整数の範囲を制限します。  
  
```  
CREATE RULE range_rule  
AS   
@range>= $1000 AND @range <$20000;  
```  
  
### <a name="b-creating-a-rule-with-a-list"></a>B. リストを指定してルールを作成する  
 次の例で作成するルールは、ルールのバインド先となる列に挿入できる値を、指定したリストの値に制限します。  
  
```  
CREATE RULE list_rule  
AS   
@list IN ('1389', '0736', '0877');  
```  
  
### <a name="c-creating-a-rule-with-a-pattern"></a>C. パターンを指定してルールを作成する  
 次の例の後にハイフン、2 つの文字のパターンに従う必要のルールを作成する (`-`) 任意の数の文字またはない文字、およびの整数で終了するまで、`0`を通じて`9`です。  
  
```  
CREATE RULE pattern_rule   
AS  
@value LIKE '__-%[0-9]'  
```  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE DEFAULT &#40;Transact-SQL&#41;](../../t-sql/statements/create-default-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [既定値 &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-default-transact-sql.md)   
 [DROP RULE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-rule-transact-sql.md)   
 [式 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [sp_bindrule &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helptext &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [sp_unbindrule &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-unbindrule-transact-sql.md)   
 [ここで &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/where-transact-sql.md)  
  
  
