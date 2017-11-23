---
title: "HOST_ID (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- HOST_ID
- HOST_ID_TSQL
dev_langs: TSQL
helpviewer_keywords:
- IDs [SQL Server], workstations
- HOST_ID function
- workstation IDs [SQL Server]
- identification numbers [SQL Server], workstations
ms.assetid: 36ba56d4-20d7-4cd1-aa2a-e40a6c0a4e39
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a2a89b0093ba92edbac81f805b35a37db8ae1e61
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="hostid-transact-sql"></a>HOST_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ワークステーションの ID 番号を返します。 ワークステーションの ID 番号とは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続しているクライアント コンピューター上のアプリケーションのプロセス ID (PID) です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
HOST_ID ()  
```  
  
## <a name="return-types"></a>戻り値の型  
 **char (10)**  
  
## <a name="remarks"></a>解説  
 システム関数のパラメーターを指定しない場合は、現在のデータベース、ホスト コンピューター、サーバー ユーザー、またはデータベース ユーザーを指定したと見なされます。 組み込み関数の後には、必ずかっこが必要です。  
  
 システム関数は、選択リストの中、WHERE 句の中、また、式を使える所ならどこにでも使用できます。  
  
## <a name="examples"></a>使用例  
 次の例を使用するテーブルを作成する`HOST_ID()`で、`DEFAULT`受注を記録テーブルに行を挿入するコンピューターの端末 ID を記録を定義します。  
  
```  
CREATE TABLE Orders  
   (OrderID     int       PRIMARY KEY,  
    CustomerID  nchar(5)  REFERENCES Customers(CustomerID),  
    TerminalID  char(8)   NOT NULL DEFAULT HOST_ID(),  
    OrderDate   datetime  NOT NULL,  
    ShipDate    datetime  NULL,  
    ShipperID   int       NULL REFERENCES Shippers(ShipperID));  
GO  
```  
  
## <a name="see-also"></a>参照  
 [式 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [システム関数 &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  
