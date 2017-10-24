---
title: "@@MAX_CONNECTIONS (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@MAX_CONNECTIONS'
- '@@MAX_CONNECTIONS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- simultaneous connections [SQL Server]
- maximum number of simultaneous user connections
- '@@MAX_CONNECTIONS function'
- connections [SQL Server], simultaneous
- number of simultaneous user connections
ms.assetid: 57eb9f4b-548f-4212-9684-a11d831c4732
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: 29910f9bc06335c4df10acf7663bfef92edffce2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40maxconnections-transact-sql"></a>& #x 40; & #x 40 です。MAX_CONNECTIONS (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで同時に確立できるユーザー接続の最大数を返します。 返される数値は必ずしも現在構成されている数値ではありません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
@@MAX_CONNECTIONS  
```  
  
## <a name="return-types"></a>戻り値の型  
 **整数 (integer)**  
  
## <a name="remarks"></a>解説  
 実際に可能なユーザー接続数は、インストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンと、アプリケーションおよびハードウェアの制限により異なります。  
  
 再構成する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続の数を使用して**sp_configure**です。  
  
## <a name="examples"></a>使用例  
 次の例ではのインスタンス上のユーザー接続の最大数を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 この例では、接続数が少なくなるよう [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を再構成していないことを前提としています。  
  
```  
SELECT @@MAX_CONNECTIONS AS 'Max Connections';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Max Connections  
---------------  
32767            
```  
  
## <a name="see-also"></a>参照  
 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [構成関数](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [user connections サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-user-connections-server-configuration-option.md)  
  
  

