---
title: "@@SERVERNAME (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@SERVERNAME'
- '@@SERVERNAME_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@SERVERNAME function'
- local servers [SQL Server]
ms.assetid: b0ef33fb-954a-4294-b05b-a87c14ce25a3
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: 93d03e11df97075b2d608d7bfcc4e234c37971cd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40servername-transact-sql"></a>&#x40;&#x40;です。サーバー名 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  実行されているローカル サーバーの名前を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
@@SERVERNAME  
```  
  
## <a name="return-types"></a>戻り値の型  
 **nvarchar**  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップでは、インストール中に、コンピューター名に、サーバー名を設定します。 サーバーの名前を変更するには、使用**sp_addserver**、し再起動[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 複数のインスタンスで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インストールされている、@@SERVERNAMEローカル サーバー名がセットアップ以降変更されていない場合、次のローカル サーバーの名前情報を返します。  
  
|Instance|サーバー情報|  
|--------------|------------------------|  
|[既定のインスタンス]|'*servername*'|  
|[名前付きインスタンス]|'*servername*\\*instancename*'|  
|フェールオーバー クラスター インスタンス - 既定のインスタンス|'*virtualservername*'|  
|フェールオーバー クラスター インスタンス - 名前付きインスタンス|'*virtualservername*\\*instancename*'|  
  
 @@SERVERNAME関数と、SERVERPROPERTY 関数の SERVERNAME プロパティのような形式で文字列を返す可能性があります、さまざまな情報を指定できます。 SERVERNAME プロパティの場合は、コンピューターのネットワーク名の変更を自動的にレポートします。  
  
 これに対し、@@SERVERNAMEこのような変更を報告しません。 @@SERVERNAME使用してローカル サーバー名に加えられた変更を報告、 **sp_addserver**または**sp_dropserver**ストアド プロシージャです。  
  
## <a name="examples"></a>使用例  
 次に、`@@SERVERNAME` の使用例を示します。  
  
```  
SELECT @@SERVERNAME AS 'Server Name'  
```  
  
 次に結果セットの例を示します。  
  
```  
Server Name  
---------------------------------  
ACCTG  
  
```  
  
## <a name="see-also"></a>参照  
 [構成関数 &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)   
 [sp_addserver &#40;です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)  
  
  

