---
title: "HOST_NAME (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- HOST_NAME_TSQL
- HOST_NAME
dev_langs:
- TSQL
helpviewer_keywords:
- HOST_NAME function
- workstation names [SQL Server]
ms.assetid: 4b8b0705-c083-4b07-b954-c83ee73b2ebb
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1f10245c8a84469877d9f455c2518d7b4ba48173
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="hostname-transact-sql"></a>HOST_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ワークステーション名を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
HOST_NAME ()  
```  
  
## <a name="return-types"></a>戻り値の型  
 **nvarchar (128)**  
  
## <a name="remarks"></a>解説  
 システム関数のパラメーターを指定しない場合は、現在のデータベース、ホスト コンピューター、サーバー ユーザー、またはデータベース ユーザーを指定したと見なされます。 組み込み関数の後には、必ずかっこが必要です。  
  
 システム関数は、選択リストの中、WHERE 句の中、また、式を使える所ならどこにでも使用できます。  
  
> [!IMPORTANT]  
>  クライアント アプリケーションから返されたワークステーション名が、必ずしも正確なデータであるとは限りません。 セキュリティ機能として HOST_NAME に依存することは避けてください。  
  
## <a name="examples"></a>使用例  
 次の例を使用するテーブルを作成する`HOST_NAME()`で、`DEFAULT`受注を記録テーブルに行を挿入するコンピューターのワークステーションの名前を記録を定義します。  
  
```  
CREATE TABLE Orders  
   (OrderID     int        PRIMARY KEY,  
    CustomerID  nchar(5)   REFERENCES Customers(CustomerID),  
    Workstation nchar(30)  NOT NULL DEFAULT HOST_NAME(),  
    OrderDate   datetime   NOT NULL,  
    ShipDate    datetime   NULL,  
    ShipperID   int        NULL REFERENCES Shippers(ShipperID));  
GO  
```  
  
## <a name="see-also"></a>参照  
 [式 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [システム関数 & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  
