---
title: "[SET textsize] (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/12/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TEXTSIZE_TSQL
- TEXTSIZE
- SET_TEXTSIZE_TSQL
- SET TEXTSIZE
dev_langs:
- TSQL
helpviewer_keywords:
- SET TEXTSIZE statement
- SELECT statement [SQL Server], text size returned
- size [SQL Server], text and image data
- TEXTSIZE option
- text size returned [SQL Server]
ms.assetid: 787154a6-39a6-4dd6-a6d0-67b4364f95d5
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2d9925b382a7d09722846ca7da583fb92fe4609c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="set-textsize-transact-sql"></a>SET TEXTSIZE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  サイズを指定**varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、**テキスト**、 **ntext**、および**イメージ**、SELECT ステートメントによって返されるデータ。  
  
> [!IMPORTANT]  
>  **ntext**、**テキスト**、および**イメージ**データ型は、将来のバージョンで削除される予定[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 新しい開発作業では、これらのデータ型の使用は避け、現在これらのデータ型を使用しているアプリケーションは修正するようにしてください。 代わりに、 **nvarchar(max)**、 **varchar(max)**、 **varbinary(max)** を使用してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
SET TEXTSIZE { number }   
```  
  
## <a name="arguments"></a>引数  
 *number*  
 長さは、 **varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、**テキスト**、 **ntext**、または**イメージ**(バイト単位) のデータ。 *数*2,147, 483,647 (2 GB) の最大値を持つ整数です。  値-1 は無制限のサイズを示します。 値 0 は、4 KB の既定値をサイズをリセットします。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (10.0 以降) および ODBC Driver for[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]自動的に指定される`-1`(無制限) の場合に接続します。  
  
 **ドライバーよりも古い[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2008:** 、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダー (バージョン 9) の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続するときに、2,147, 483,647 に TEXTSIZE を自動的に設定します。  
  
## <a name="remarks"></a>解説  
 SET TEXTSIZE に影響を設定、@@TEXTSIZE関数。  
  
 TEXTSIZE は、解析時ではなく実行時に設定されます。  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [@@TEXTSIZE &#40;Transact-SQL&#41;](../../t-sql/functions/textsize-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

