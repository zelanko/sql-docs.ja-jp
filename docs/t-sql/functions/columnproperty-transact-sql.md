---
title: COLUMNPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COLUMNPROPERTY
- COLUMNPROPERTY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- column properties [SQL Server]
- parameters [SQL Server], properties
- COLUMNPROPERTY function
ms.assetid: 2408c264-6eca-4120-bb71-df043c7c2792
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 61ac858e029848ef59978669112de3db7c068f67
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="columnproperty-transact-sql"></a>COLUMNPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

列またはパラメーターに関する情報を返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
COLUMNPROPERTY ( id , column , property )   
```  
  
## <a name="arguments"></a>引数  
*id*  
テーブルまたはプロシージャの識別子 (ID) を含む[式](../../t-sql/language-elements/expressions-transact-sql.md)です。
  
*column*  
列またはパラメーターの名前を含む式です。
  
*property*  
*id* として返される情報を含む式を指定します。次のいずれかの値を指定できます。
  
|ReplTest1|Description|返される値|  
|---|---|---|
|**AllowsNull**|NULL 値を許可します。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力|  
|**ColumnId**|**sys.columns.column_id** に対応する列の ID 値です。|列 ID<br /><br /> **注:** 複数の列に対してクエリを実行する場合、列の ID 値の順序にギャップが生じることがあります。|  
|**FullTextTypeColumn**|*column* のドキュメント型情報を保持する、テーブル内の TYPE COLUMN です。|このプロパティの 2 番目のパラメーターとして渡される列の、フルテキストの TYPE COLUMN の ID です。|  
|**IsComputed**|列は計算列です。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力|  
|**IsCursorType**|プロシージャ パラメーターは CURSOR 型です。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力|  
|**IsDeterministic**|列は決定的です。 このプロパティは、計算列およびビュー列にのみ適用されます。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力 (計算列またはビュー列ではありません)|  
|**IsFulltextIndexed**|列はフルテキスト インデックス作成用に登録されています。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力|  
|**IsIdentity**|列で IDENTITY プロパティを使用します。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力|  
|**IsIdNotForRepl**|列で IDENTITY_INSERT の設定が確認されます。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力|  
|**IsIndexable**|列にインデックスを作成できます。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力|  
|**IsOutParam**|プロシージャ パラメーターは出力パラメーターです。|1 = TRUE<br /><br /> 0 = FALSE NULL = 無効な入力 |  
|**IsPrecise**|列は正確です。 このプロパティは、決定的な列に対してのみ適用されます。|1 = TRUE<br /><br /> 0 = FALSE NULL = 無効な入力  (決定的な列ではありません)|  
|**IsRowGuidCol**|列は **uniqueidentifier** 型であり、ROWGUIDCOL プロパティで定義されています。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力|  
|**IsSystemVerified**|列の決定性のプロパティと有効桁数のプロパティは、[!INCLUDE[ssDE](../../includes/ssde-md.md)]で確認できます。 このプロパティは、計算列およびビュー列にのみ適用されます。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力|  
|**IsXmlIndexable**|XML 列は XML インデックスで使用できます。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力|  
|**[精度]**|列またはパラメーターのデータ型の長さです。|指定した列のデータ型の長さ<br /><br /> -1 = **xml** または大きい値の型<br /><br /> NULL = 無効な入力|  
|**[スケール]**|列またはパラメーターのデータ型の小数点以下桁数です。|小数点以下桁数<br /><br /> NULL = 無効な入力|  
|**StatisticalSemantics**|列でセマンティック インデックス作成が有効になっています。|1 = TRUE<br /><br /> 0 = FALSE|  
|**SystemDataAccess**|列は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム カタログまたは仮想システム テーブルのデータにアクセスする関数から派生します。 このプロパティは、計算列およびビュー列にのみ適用されます。|1 = TRUE (読み取り専用アクセス)<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力|  
|**UserDataAccess**|列は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンスに格納されている、ビュー テーブルおよび一時テーブルを含むユーザー テーブル内のデータにアクセスする関数から派生します。 このプロパティは、計算列およびビュー列にのみ適用されます。|1 = TRUE (読み取り専用アクセス)<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力|  
|**UsesAnsiTrim**|テーブルが最初に作成されたときに、ANSI_PADDING が ON に設定されました。 このプロパティは、**char** または **varchar** 型の列またはパラメーターにのみ適用されます。|1= TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力|  
|**IsSparse**|列はスパース列です。 詳細については、「 [スパース列の使用](../../relational-databases/tables/use-sparse-columns.md)」を参照してください。|1= TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力|  
|**IsColumnSet**|列は列セットです。 詳細については、「 [列セットの使用](../../relational-databases/tables/use-column-sets.md)」を参照してください。|1= TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力|  
|**GeneratedAlwaysType**|列の値は、システムによって生成されます。 **sys.columns.generated_always_type** に対応します|**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 0 常に生成された = なし<br /><br /> 1 = 行の先頭として常に生成されました。<br /><br /> 2 – 生成された常に行の終わりとして|  
|**IsHidden**|列の値は、システムによって生成されます。 **sys.columns.is_hidden** に対応します|**適用対象**: [!INCLUDE[ssCurrentLong](../../includes/sscurrentlong-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 0 = 非表示ではありません<br /><br /> 1 = 非表示|  
  
## <a name="return-types"></a>戻り値の型
 **int**  
  
## <a name="exceptions"></a>例外  
エラーが発生した場合、または呼び出し元にオブジェクトの表示権限がない場合は、NULL が返されます。
  
ユーザーが所有しているか、または権限を与えられている、セキュリティ保護可能なリソースのメタデータのみを表示できます。 つまり、オブジェクトに対する権限がユーザーに与えられていない場合、メタデータを生成する組み込み関数 (COLUMNPROPERTY など) が NULL を返す可能性があります。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。
  
## <a name="remarks"></a>Remarks  
列の決定的なプロパティを調べるときは、まず、その列が計算列であるかどうかをテストします。 計算列でない場合は、**IsDeterministic** によって NULL が返されます。 計算列は、インデックス列として指定できます。
  
## <a name="examples"></a>使用例  
次の例では、`LastName` 列の長さを返します。
  
```sql
USE AdventureWorks2012;  
GO  
SELECT COLUMNPROPERTY( OBJECT_ID('Person.Person'),'LastName','PRECISION')AS 'Column Length';  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
Column Length
-------------
50
```  
  
## <a name="see-also"></a>参照
[メタデータ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)  
[TYPEPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/typeproperty-transact-sql.md)
  
  
