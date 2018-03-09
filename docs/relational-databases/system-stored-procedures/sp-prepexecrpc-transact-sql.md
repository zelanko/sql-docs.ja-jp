---
title: "sp_prepexecrpc (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepexecrpc
- sp_cursor_prepexecrpc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_prepexecrpc
ms.assetid: 35d686f2-ef31-4eaa-baa9-9cef5d6c87c2
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6d17320174703e8fc6b21d7fecb83229f80bac41
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spprepexecrpc-transact-sql"></a>sp_prepexecrpc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  RPC 識別子を使用して指定されているパラメーター化されたストアド プロシージャの呼び出しを準備して実行します。 sp_prepexecrpc は、ID によって呼び出される、表形式のデータ ストリーム (TDS) パケットで 14 の = です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_prepexecrpc handle OUTPUT, RPCCall  
    [ , bound_param ] [ ,...n]]  
```  
  
## <a name="arguments"></a>引数  
 *ハンドル*  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって生成される準備済みハンドル識別子です。 *処理*必須のパラメーターには、 **int**値を返します。  
  
 *RPCCall*  
 ODBC 標準構文を使用してストアド プロシージャ呼び出しを定義します。 *RPCCall*必須パラメーターですが、 **ntext**文字列入力値。  
  
 *bound_param*  
 追加パラメーターをオプションで使用することを示します。 *bound_param*任意のデータ型を使用して追加のパラメーターを指定する入力値を呼び出します。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
