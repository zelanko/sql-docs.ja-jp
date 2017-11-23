---
title: "SET SHOWPLAN_ALL (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET SHOWPLAN_ALL
- SET_SHOWPLAN_ALL_TSQL
- SHOWPLAN_ALL
- SHOWPLAN_ALL_TSQL
dev_langs: TSQL
helpviewer_keywords:
- statements [SQL Server], estimates
- execution information and estimates [SQL Server]
- statements [SQL Server], information without processing
- SET SHOWPLAN_ALL statement
- SHOWPLAN_ALL option
- canceling statement execution
- stopping statement execution
- estimated execution information [SQL Server]
ms.assetid: a500b682-bae4-470f-9e00-47de905b851b
caps.latest.revision: "40"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: cdaf86a6eb550574b507edfba130a277fde395b4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="set-showplanall-transact-sql"></a>SET SHOWPLAN_ALL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行せず、 代わりに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ステートメントのリソース要件の見積もりを示し、ステートメントの実行方法に関する詳細情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SET SHOWPLAN_ALL { ON | OFF }  
```  
  
## <a name="remarks"></a>解説  
 SET SHOWPLAN_ALL は、解析時ではなく実行時に設定されます。  
  
 SET SHOWPLAN_ALL が ON の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を実行することがなく各ステートメントの実行情報を返しますと[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントは実行されません。 このオプションを設定した後に、情報後続のすべての[!INCLUDE[tsql](../../includes/tsql-md.md)]オプションが OFF に設定されるまで、ステートメントが返されます。 たとえば、SET SHOWPLAN_ALL が ON のときに CREATE TABLE ステートメントを実行し、その後この同じテーブルを参照する SELECT ステートメントを実行すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では指定したテーブルが存在しないというエラー メッセージが返されます。 その後、このテーブルに対して行われる参照は失敗します。 SET SHOWPLAN_ALL が OFF の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]レポートを生成せず、ステートメントを実行します。  
  
 SET SHOWPLAN_ALL は、出力処理用に作成されたアプリケーションで使用できます。 SET SHOWPLAN_TEXT を使用してをなどの Microsoft Win32 コマンド プロンプト アプリケーションでは、読みやすい出力を返す、 **osql**ユーティリティです。  
  
 SET SHOWPLAN_TEXT ステートメントと SET SHOWPLAN_ALL ステートメントは、ストアド プロシージャ内では指定できません。これらのステートメントは、バッチ内にのみ指定できます。  
  
 SET SHOWPLAN_ALL がで実行される手順を表す階層ツリーを形成する行のセットとして情報を返します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クエリ プロセッサの各ステートメントが実行されます。 出力結果には、ステートメントごとに、ステートメントのテキストを示す 1 行と、実行ステップの詳細を示す複数行が含まれます。 次の表は、出力に含まれる列の一覧です。  
  
|列名|Description|  
|-----------------|-----------------|  
|**StmtText**|この列は、種類 PLAN_ROW が行のテキストを含む、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。 PLAN_ROW 型の行の場合、この列には操作の説明が含まれます。 またこの列には物理操作と、必要に応じて論理操作が含まれます。 この列の後に説明が続くこともありますが、その説明は物理操作によって決定されます。 詳細については、次を参照してください。[プラン表示の論理および物理演算子リファレンス](../../relational-databases/showplan-logical-and-physical-operators-reference.md)です。|  
|**StmtId**|現在のバッチに含まれるステートメントの数。|  
|**NodeId**|現在のクエリ内にあるノードの ID。|  
|**Parent**|親ステップのノードの ID。|  
|**PhysicalOp**|ノードの物理的な実装アルゴリズム。 PLAN_ROWS 型の行の場合だけ返されます。|  
|**LogicalOp**|ノードが表す関係代数操作。 PLAN_ROWS 型の行の場合だけ返されます。|  
|**引数**|実行されている操作に関する補足情報。 この列の内容は、物理操作に応じて異なります。|  
|**DefinedValues**|操作によって導入される値のコンマ区切りの一覧。 これらの値は、現在のクエリ (たとえば、SELECT リストや WHERE 句) に指定された計算式であるか、またはこのクエリを処理するためにクエリ プロセッサで導入された内部値です。 定義されたこれらの値は、このクエリ内の他の場所で参照できます。 PLAN_ROWS 型の行の場合だけ返されます。|  
|**EstimateRows**|操作によって出力される行数の見積もり。 PLAN_ROWS 型の行の場合だけ返されます。|  
|**EstimateIO**|操作の I/O コスト* の見積もり。 PLAN_ROWS 型の行の場合だけ返されます。|  
|**EstimateCPU**|操作の CPU コスト* の見積もり。 PLAN_ROWS 型の行の場合だけ返されます。|  
|**AvgRowSize**|操作を介して渡される行の平均サイズ (バイト単位)。|  
|**TotalSubtreeCost**|親演算とすべての子演算に関する (累積) コスト* の見積もり。|  
|**OutputList**|現在の演算によって示される列のコンマ区切りの一覧。|  
|**Warnings**|現在の演算に関係する警告メッセージのコンマ区切りの一覧。 警告メッセージには、"NO STATS:()" という文字列と列の一覧が含まれることがあります。 この警告メッセージは、クエリ オプティマイザーが列の統計を基に判断を下そうとしたときに、使用できる統計がなかったことを意味します。 この結果、クエリ オプティマイザーでは推定値が用いられ、効率の悪いクエリ プランが作成された可能性があります。 作成または更新するのに役立つ、クエリ オプティマイザーがより効率的なクエリ プランを選択) 列ずつの統計の詳細については、次を参照してください。 [UPDATE STATISTICS](../../t-sql/statements/update-statistics-transact-sql.md)です。 場合によっては、この列には "MISSING JOIN PREDICATE" という文字列が含まれることがあります。これは、結合述語のない結合 (テーブルを含む) が実行されていることを意味します。 結合述語を誤って破棄すると、予想より実行時間が長くなり、巨大な結果セットを返すクエリが作成される可能性があります。 この警告が返された場合は、結合述語が意図的に省略されているかどうかを確認してください。|  
|**型**|ノードの種類。 これは、各クエリの親ノードに対して、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントの種類 (SELECT、INSERT、EXECUTE、およびなどなど)。 実行プランを表すサブノードの場合は、型は PLAN_ROW です。|  
|**Parallel**|**0** = 演算子が並列で実行されていません。<br /><br /> **1** = 演算子が並列で実行されています。|  
|**EstimateExecutions**|現在のクエリの実行中に、操作が実行される推定回数。|  
  
 * コスト単位は、ウォール クロック時間ではなく、内部測定時間に基づいています。 コスト単位は、プランの相対コストを他のプランと比較して決定するために使用されます。  
  
## <a name="permissions"></a>Permissions  
 SET SHOWPLAN_ALL を使用するには、SET SHOWPLAN_ALL の実行ステートメントを実行するための適切な権限が与えられている必要があります。また、参照されるオブジェクトを含むすべてのデータベースに対して、SHOWPLAN 権限が必要です。  
  
 SELECT、INSERT、UPDATE、DELETE、EXEC の*stored_procedure*と EXEC *user_defined_function*ステートメントをユーザーはプラン表示を作成します。  
  
-   実行する適切なアクセス許可、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。  
  
-   によって参照されるオブジェクトを含むすべてのデータベースに SHOWPLAN 権限、[!INCLUDE[tsql](../../includes/tsql-md.md)]テーブルやビューなどのステートメント。  
  
 DDL、USE など、他のすべてのステートメントの*database_name*、セット、DECLARE、動的 SQL、および実行する適切な権限のみで、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントが必要です。  
  
## <a name="examples"></a>使用例  
 次の 2 つのステートメントでは、SET SHOWPLAN_ALL の設定を使用する方法を示して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を分析し、クエリ内のインデックスの使用を最適化します。  
  
 最初のクエリでは、インデックス列の WHERE 句で = (等しい) 比較演算子を使用しています。 これは、結果、Clustered Index Seek 値で、 **LogicalOp**列と、インデックスの名前、**引数**列です。  
  
 2 番目のクエリでは、WHERE 句で LIKE 演算子を使用します。 これにより、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をクラスター化インデックス スキャンを使用して、WHERE 句の条件を満たすデータを検索します。 これは、結果、Clustered Index Scan 値で、 **LogicalOp**内のインデックスの名前の列、**引数**列、およびフィルター値、 **LogicalOp**列WHERE 句の条件で、**引数**列です。  
  
 内の値、 **EstimateRows**と**TotalSubtreeCost**列の方が小さく、ことを示すことが非常に高速に処理されるインデックス付けされていないクエリよりも少ないリソースを使用して、最初のインデックス付きクエリ.  
  
```  
USE AdventureWorks2012;  
GO  
SET SHOWPLAN_ALL ON;  
GO  
-- First query.  
SELECT BusinessEntityID   
FROM HumanResources.Employee  
WHERE NationalIDNumber = '509647174';  
GO  
-- Second query.  
SELECT BusinessEntityID, EmergencyContactID   
FROM HumanResources.Employee  
WHERE EmergencyContactID LIKE '1%';  
GO  
SET SHOWPLAN_ALL OFF;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET SHOWPLAN_TEXT と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-showplan-text-transact-sql.md)   
 [SET SHOWPLAN_XML と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-showplan-xml-transact-sql.md)  
  
  
