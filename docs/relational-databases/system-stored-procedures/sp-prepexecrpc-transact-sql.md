---
title: sp_prepexecrpc (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepexecrpc
- sp_cursor_prepexecrpc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_prepexecrpc
ms.assetid: 35d686f2-ef31-4eaa-baa9-9cef5d6c87c2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 26f298a102c69c8bc75721db531275379080005a
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830981"
---
# <a name="sp_prepexecrpc-transact-sql"></a>sp_prepexecrpc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  RPC 識別子を使用して指定されたパラメーター化されたストアドプロシージャ呼び出しを準備して実行します。 sp_prepexecrpc は、ID = 14 によって表形式のデータストリーム (TDS) パケットで呼び出されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_prepexecrpc handle OUTPUT, RPCCall  
    [ , bound_param ] [ ,...n]]  
```  
  
## <a name="arguments"></a>引数  
 *扱え*  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって生成される準備済みハンドル識別子です。 *handle*は、 **int**戻り値を持つ必須パラメーターです。  
  
 *RPCCall*  
 ODBC 標準構文を使用してストアド プロシージャ呼び出しを定義します。 *Rpccall*は、 **ntext**文字列入力値を呼び出す必須のパラメーターです。  
  
 *bound_param*  
 追加パラメーターをオプションで使用することを示します。 *bound_param*は、使用する追加パラメーターを指定するために、任意のデータ型の入力値を呼び出します。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
