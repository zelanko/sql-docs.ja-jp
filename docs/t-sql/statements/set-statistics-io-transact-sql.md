---
title: "STATISTICS IO (TRANSACT-SQL) を設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/10/2016
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
- SET_STATISTICS_IO_TSQL
- IO
- IO_TSQL
- SET STATISTICS IO
dev_langs:
- TSQL
helpviewer_keywords:
- disk I/O statistics [SQL Server]
- I/O [SQL Server], disk activity information
- disks [SQL Server], statement statistics
- STATISTICS IO option
- statements [SQL Server], statistical information
- SET STATISTICS IO statement
- statistical information [SQL Server], disk activity
ms.assetid: 7033aac9-a944-4156-9ff4-6ef65717a28b
caps.latest.revision: 40
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 99e1dc183844f25002057b7cebd4729ff5f1bbe5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="set-statistics-io-transact-sql"></a>SET STATISTICS IO (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  により[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のによって生成されるディスク利用状況に関する情報を表示する[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SET STATISTICS IO { ON | OFF }  
```  
  
## <a name="remarks"></a>解説  
 STATISTICS IO が ON の場合、統計情報が表示されます。 OFF の場合、情報は表示されません。  
  
 返される情報は、このオプションが ON に設定されてから OFF に設定されるまでに実行される、すべての [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントに関する統計情報です。  
  
 次の表は、出力アイテムの一覧とその説明です。  
  
|出力アイテム|意味|  
|-----------------|-------------|  
|**Table**|テーブルの名前。|  
|**スキャンの回数**|すべての値を取得して出力の最終的なデータセットを構築するために、任意の方向のリーフ レベルに達した後に開始されるシーク/スキャンの数。<br /><br /> 使用されるインデックスが主キーの一意のインデックスまたはクラスター化インデックスで、1 つの値のみシークしている場合、Scan count は 0 になります。 たとえば、 `WHERE Primary_Key_Column = <value>`があります。<br /><br /> 主キー列以外の列で定義された一意でないクラスター化インデックスを使用して 1 つの値を検索する場合 Scan count は 1 になります。 これは、検索対象のキー値の重複値を確認する場合に実行されます。 たとえば、 `WHERE Clustered_Index_Key_Column = <value>`があります。<br /><br /> N が、インデックス キーを使用してキー値を検索した後にリーフ レベルで左側または右側に向かって開始される異なるシーク/スキャンの数である場合、Scan count は N となります。|  
|**論理読み取り数**|データ キャッシュから読み取られたページ数|  
|**物理的な読み取り**|ディスクから読み取られたページ数|  
|**先行読み取り数**|クエリ用のキャッシュに読み取られたページ数|  
|**lob 論理読み取り数**|数**テキスト**、 **ntext**、**イメージ**、または大きな値型 (**varchar (max)**、 **nvarchar (max)**、**varbinary (max)**)、データ キャッシュから読み取ったページ。|  
|**lob 物理読み取り数**|数**テキスト**、 **ntext**、**イメージ**または大きな値データ型のページがディスクから読み取る。|  
|**lob 先行読み取り数**|数**テキスト**、 **ntext**、**イメージ**または大きな値をクエリ用のキャッシュに入れられたページを入力します。|  
  
 SET STATISTICS IO は、解析時ではなく実行時に設定されます。  
  
> [!NOTE]  
>  Transact-SQL ステートメントで LOB 列を取得するとき、LOB 取得操作で LOB ツリーを複数回移動することが必要になる場合があります。 その結果、SET STATISTICS IO では、予想より多くの論理読み取り数が報告されることがあります。  
  
## <a name="permissions"></a>Permissions  
 SET STATISTICS IO を使用するユーザーを実行する適切なアクセス許可が必要、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。 SHOWPLAN 権限は必要ありません。  
  
## <a name="examples"></a>使用例  
 この例では、論理的および物理的な読み取りの数がによって使用される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ようにステートメントを処理します。  
  
```  
USE AdventureWorks2012;  
GO         
SET STATISTICS IO ON;  
GO  
SELECT *   
FROM Production.ProductCostHistory  
WHERE StandardCost < 500.00;  
GO  
SET STATISTICS IO OFF;  
GO  
```  
  
 Here is the result set:  
  
```  
Table 'ProductCostHistory'. Scan count 1, logical reads 5, physical   
reads 0, read-ahead reads 0, lob logical reads 0, lob physical reads 0,   
lob read-ahead reads 0.  
```  
  
## <a name="see-also"></a>参照  
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET SHOWPLAN_ALL & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-showplan-all-transact-sql.md)   
 [STATISTICS TIME &#40; を設定します。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-statistics-time-transact-sql.md)  
  
  

