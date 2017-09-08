---
title: "SET SHOWPLAN_XML (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET SHOWPLAN_XML
- SET_SHOWPLAN_XML_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- statements [SQL Server], estimates
- SET SHOWPLAN_XML statement
- execution information and estimates [SQL Server]
- statements [SQL Server], information without processing
- XML [SQL Server], statement execution information
- SHOWPLAN_XML option
- estimated execution information [SQL Server]
ms.assetid: a467a1b3-10a5-43c4-9085-13d8aed549c9
caps.latest.revision: 48
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3414096227310460a0a1b58a34cb0fbc4e528649
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="set-showplanxml-transact-sql"></a>SET SHOWPLAN_XML (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  により[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の実行を中止[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。 代わりに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を適切に定義された XML ドキュメントの形式で実行するステートメントを移動する方法に関する詳細な情報を返します  
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SET SHOWPLAN_XML { ON | OFF }  
```  
  
## <a name="remarks"></a>解説  
 SET SHOWPLAN_XML は、解析時ではなく実行時に設定されます。  
  
 SET SHOWPLAN_XML が ON の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を実行することがなく各ステートメントの実行プラン情報を返しますと[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントは実行されません。 返される情報は、このオプションが ON に設定されてから OFF に設定されるまでに発行されたすべての [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントに関する実行プラン情報です。 たとえば、CREATE TABLE ステートメントが実行中に SET SHOWPLAN_XML が ON、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラーを返しますが、同じテーブルに関連する後続の SELECT ステートメントからメッセージ以外の場合は、指定したテーブルが存在しません。 その後、このテーブルに対して行われる参照は失敗します。 SET SHOWPLAN_XML が OFF の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではレポートを作成せずに、ステートメントを実行します。  
  
 SET SHOWPLAN_XML のためのものとして出力を返す**nvarchar (max)**などのアプリケーション、 **sqlcmd**ユーティリティ、XML 出力が、後で使用されている他のツールで表示し、クエリの処理情報を計画します。  
  
> [!NOTE]  
>  動的管理ビュー **sys.dm_exec_query_plan**、SET SHOWPLAN_XML とで同じ情報を返す、 **xml**データ型。 この情報から返される、 **query_plan**の列**sys.dm_exec_query_plan**です。 詳細については、次を参照してください。 [sys.dm_exec_query_plan & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md).  
  
 SET SHOWPLAN_XML はストアド プロシージャ内では指定できません。 このステートメントは、バッチ内にのみ指定できます。  
  
 SET SHOWPLAN_XML では、情報が XML ドキュメントのセットとして返されます。 SET SHOWPLAN_XML を ON にした後で実行された各バッチの情報は、それぞれ 1 つの出力ドキュメントに反映されます。 各ドキュメントには、バッチ内のステートメントのテキストと実行ステップの詳細が含まれ、 推定コスト、行数、アクセスしたインデックス、実行された演算子の種類、結合順序、および実行プランに関するその他の情報が示されます。  
  
 SET SHOWPLAN_XML による XML 出力がセットアップ中にマイクロソフト上のコンピューター上のローカル ディレクトリにコピーされるため、XML スキーマを含むドキュメント[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]がインストールされています。 含む、ドライブは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インストール ファイルで。  
  
 \Microsoft SQL Server\130\Tools\Binn\schemas\sqlserver\2004\07\showplan\showplanxml.xsd  
  
 プラン表示スキーマもご覧に[この Web サイト](http://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409)です。  
  
> [!NOTE]  
>  場合**実際の実行プランを含める**で選択した[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、この SET オプションでは、XML プラン表示出力は生成されません。 クリア、**実際の実行プランを含める**オプションを設定してこれを使用する前にボタンをクリックします。  
  
## <a name="permissions"></a>Permissions  
 SET SHOWPLAN_XML を使用するには、SET SHOWPLAN_XML の実行ステートメントを実行するための適切な権限が与えられている必要があります。また、参照されるオブジェクトを含むすべてのデータベースに対して、SHOWPLAN 権限が必要です。  
  
 SELECT、INSERT、UPDATE、DELETE、EXEC の*stored_procedure*と EXEC *user_defined_function*ステートメントをユーザーはプラン表示を作成します。  
  
-   実行する適切なアクセス許可、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。  
  
-   によって参照されるオブジェクトを含むすべてのデータベースに SHOWPLAN 権限、[!INCLUDE[tsql](../../includes/tsql-md.md)]テーブルやビューなどのステートメント。  
  
 DDL、USE など、他のすべてのステートメントの*database_name*、セット、DECLARE、動的 SQL、および実行する適切な権限のみで、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントが必要です。  
  
## <a name="examples"></a>使用例  
 次の 2 つのステートメントは、SET SHOWPLAN_XML の設定を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でクエリ内のインデックスの使用状況を分析し最適化する方法を示しています。  
  
 最初のクエリでは、インデックス列の WHERE 句で = (等しい) 比較演算子を使用しています。 2 番目のクエリでは、WHERE 句で LIKE 演算子を使用します。 これにより、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をクラスター化インデックス スキャンを使用して、WHERE 句の条件を満たすデータが検索されます。 内の値、 **EstimateRows**と**EstimatedTotalSubtreeCost**属性の方が小さく、ことを示すことが非常に高速に処理されるよりも少ないリソースを使用して、最初のインデックス付きクエリ、インデックス付けされていないクエリです。  
  
```  
USE AdventureWorks2012;  
GO  
SET SHOWPLAN_XML ON;  
GO  
-- First query.  
SELECT BusinessEntityID   
FROM HumanResources.Employee  
WHERE NationalIDNumber = '509647174';  
GO  
-- Second query.  
SELECT BusinessEntityID, JobTitle  
FROM HumanResources.Employee  
WHERE JobTitle LIKE 'Production%';  
GO  
SET SHOWPLAN_XML OFF;  
```  
  
## <a name="see-also"></a>参照  
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

