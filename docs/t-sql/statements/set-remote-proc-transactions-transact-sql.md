---
title: "SET REMOTE_PROC_TRANSACTIONS (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- REMOTE_PROC_TRANSACTIONS_TSQL
- SET REMOTE_PROC_TRANSACTIONS
- REMOTE_PROC_TRANSACTIONS
- SET_REMOTE_PROC_TRANSACTIONS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- remote stored procedures [SQL Server]
- SET REMOTE_PROC_TRANSACTIONS statement
- distributed transactions [SQL Server], starting
- REMOTE_PROC_TRANSACTIONS option
- active transactions
ms.assetid: 4d284ae9-3f5f-465a-b0dd-1328a4832a03
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9ad924fa239801adb78cb391a26249cb1c2a21d1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="set-remoteproctransactions-transact-sql"></a>SET REMOTE_PROC_TRANSACTIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ローカル トランザクションがアクティブ状態のときにリモート ストアド プロシージャを実行した場合、[!INCLUDE[tsql](../../includes/tsql-md.md)] 分散トランザクション コーディネーター (MS DTC) によって管理される [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクションを開始するように指定します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]このオプションは、リモート ストアド プロシージャを使用する、旧バージョンのアプリケーションとの互換性のために用意されています。 リモート ストアド プロシージャを呼び出す代わりに、リンク サーバーを参照した分散クエリを使用してください。 これらを使用して定義されます[sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SET REMOTE_PROC_TRANSACTIONS { ON | OFF }   
```  
  
## <a name="arguments"></a>引数  
 ON | OFF  
 ON の場合、ローカル トランザクションからリモート ストアド プロシージャが実行されると、[!INCLUDE[tsql](../../includes/tsql-md.md)] 分散トランザクションが開始されます。 OFF の場合、ローカル トランザクションからリモート ストアド プロシージャを呼び出しても、[!INCLUDE[tsql](../../includes/tsql-md.md)] 分散トランザクションは開始されません。  
  
## <a name="remarks"></a>解説  
 REMOTE_PROC_TRANSACTIONS が ON の場合、リモート ストアド プロシージャを呼び出すと分散トランザクションが開始され、トランザクションは MS DTC に参加します。 リモート ストアド プロシージャを呼び出す [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスは、トランザクションを実行したインスタンスであり、このインスタンスによってトランザクションが制御されます。 この接続に対して引き続き COMMIT TRANSACTION または ROLLBACK TRANSACTION ステートメントを実行すると、制御側のインスタンスは MS DTC 対して、コンピューター間の分散トランザクションの完了を管理することを要求します。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] 分散トランザクションが開始された後は、リモート サーバーとして定義されている他の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに対し、リモート ストアド プロシージャを呼び出すことができます。 リモート サーバーのすべてに参加している、[!INCLUDE[tsql](../../includes/tsql-md.md)]分散トランザクション、および MS DTC により、各リモート サーバーで、トランザクションが完了したことです。  
  
 REMOTE_PROC_TRANSACTIONS がインスタンス レベルをオーバーライドするために使用する接続レベルの設定**sp_configure リモート proc trans**オプション。  
  
 REMOTE_PROC_TRANSACTIONS が OFF の場合、ローカル トランザクションの一部としてリモート ストアド プロシージャは呼び出されません。 リモート ストアド プロシージャによる変更は、ストアド プロシージャの完了時にコミットまたはロールバックされます。 リモート ストアド プロシージャを呼び出した接続によって実行される後続の COMMIT TRANSACTION または ROLLBACK TRANSACTION ステートメントは、ストアド プロシージャによる処理に影響を与えません。  
  
 REMOTE_PROC_TRANSACTIONS オプションのインスタンスにのみリモート ストアド プロシージャ呼び出しに影響する互換性オプション[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用してリモート サーバーとして定義されている**sp_addserver**です。 オプションは、ストアド プロシージャを使用して、リンク サーバーとして定義されているインスタンスを実行する分散クエリには適用されません**sp_addlinkedserver**です。  
  
 SET REMOTE_PROC_TRANSACTIONS は、解析時ではなく実行時に設定されます。  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [BEGIN DISTRIBUTED TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

