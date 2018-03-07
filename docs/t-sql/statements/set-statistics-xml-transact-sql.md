---
title: "SET STATISTICS XML (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_STATISTICS_XML_TSQL
- SET STATISTICS XML
dev_langs:
- TSQL
helpviewer_keywords:
- statistical information [SQL Server], statement processing
- STATISTICS XML option
- SET STATISTICS XML statement
- statements [SQL Server], statistical information
- XML [SQL Server], statement execution information
ms.assetid: 2b6d4c5a-a7f5-4dd1-b10a-7632265b1af7
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 99ef0199258d6d4a87a041979dd0f75bbc6b835f
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="set-statistics-xml-transact-sql"></a>SET STATISTICS XML (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行し、ステートメントの実行方法に関する詳細情報を整形式の XML ドキュメント形式で生成します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SET STATISTICS XML { ON | OFF }  
```  
  
## <a name="remarks"></a>解説  
 SET STATISTICS XML は、解析時ではなく実行時に設定されます。  
  
 SET STATISTICS XML が ON の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では各ステートメントの実行に関する情報がステートメントの実行後に返されます。 このオプションを設定した後に、情報後続のすべての[!INCLUDE[tsql](../../includes/tsql-md.md)]オプションが OFF に設定されるまで、ステートメントが返されます。 SET STATISTICS XML 以外のステートメントを同時にバッチで実行することもできます。  
  
 SET STATISTICS XML が出力として返されます**nvarchar (max)**アプリケーションの場合など、 **sqlcmd**ユーティリティ、XML 出力が、後で使用されている他のツールで表示およびクエリ プランの処理情報です。  
  
 SET STATISTICS XML では、情報が XML ドキュメントのセットとして返されます。 SET STATISTICS XML を ON にした後に実行された各ステートメントの情報は、それぞれ 1 つの出力ドキュメントに反映されます。 それぞれのドキュメントには、ステートメントのテキストと、実行ステップの詳細が含まれます。 この出力では、コスト、アクセスしたインデックス、実行された操作の種類、結合順序、物理操作が実行された回数、それぞれの物理操作で作成された行の数など、実行時の情報が示されます。  
  
 SET STATISTICS XML による XML 出力用の XML スキーマを含んだドキュメントは、セットアップ時に、Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がインストールされているコンピューター上のローカル ディレクトリへコピーされます。 含む、ドライブは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インストール ファイルで。  
  
 \Microsoft SQL Server\100\Tools\Binn\schemas\sqlserver\2004\07\showplan\showplanxml.xsd  
  
 プラン表示スキーマもご覧に[この Web サイト](http://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409)です。  
  
 SET STATISTICS PROFILE と SET STATISTICS XML は、同時に使用できません。 SET STATISTICS PROFILE ではテキスト形式の出力が生成され、SET STATISTICS XML では XML 形式の出力が生成されます。 将来の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、新しいクエリ実行プラン情報は、SET STATISTICS PROFILE ステートメントではない、SET STATISTICS XML ステートメントでのみ表示されます。  
  
> [!NOTE]  
>  場合**実際の実行プランを含める**で選択した[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、この SET オプションでは、XML プラン表示出力は生成されません。 クリア、**実際の実行プランを含める**オプションを設定してこれを使用する前にボタンをクリックします。  
  
## <a name="permissions"></a>権限  
 SET STATISTICS XML を使用して出力を表示するには、次の権限が必要です。  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行するための適切な権限。  
  
-   によって参照されているオブジェクトを含むすべてのデータベースでの SHOWPLAN 権限、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] STATISTICS XML を生成しないステートメントの結果セットを実行する適切な権限のみ、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントが必要です。 [!INCLUDE[tsql](../../includes/tsql-md.md)]は STATISTICS XML を生成するステートメントの結果セット、両方のチェック、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントの実行権限と SHOWPLAN 権限が成功する必要があります、または[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントの実行を中断およびなしのプラン表示情報が生成されます。  
  
## <a name="examples"></a>使用例  
 次の 2 つのステートメントでは、SET STATISTICS XML の設定を使用する方法を示して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を分析し、クエリ内のインデックスの使用を最適化します。 最初のクエリでは、インデックス付き列の WHERE 句で = (等しい) 比較演算子を使用します。 2 番目のクエリでは、WHERE 句で LIKE 演算子を使用します。 これにより、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を WHERE 句の条件を満たすデータを検索にクラスター化インデックス スキャンを使用します。 内の値、 **EstimateRows**と**EstimatedTotalSubtreeCost**属性は、最初のインデックス付きクエリが非常に高速に処理されたより少ないリソースを使用することを示す小さな、インデックス付けされていないクエリです。  
  
```  
USE AdventureWorks2012;  
GO  
SET STATISTICS XML ON;  
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
SET STATISTICS XML OFF;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [SET SHOWPLAN_XML &#40;Transact-SQL&#41;](../../t-sql/statements/set-showplan-xml-transact-sql.md)   
 [sqlcmd Utility](../../tools/sqlcmd-utility.md)  
  
  
