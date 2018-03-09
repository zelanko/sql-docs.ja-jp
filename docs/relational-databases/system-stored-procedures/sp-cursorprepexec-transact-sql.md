---
title: "sp_cursorprepexec (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- sp_cursorprepexec_TSQL
- sp_cursorprepexec
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursorprepexec
ms.assetid: 8094fa90-35b5-4cf4-8012-0570cb2ba1e6
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a5264e1c645cf1716d01e352f2b248b3b80a038d
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spcursorprepexec-transact-sql"></a>sp_cursorprepexec (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  送信済みのカーソル ステートメントまたはバッチに対応するプランをコンパイルしてカーソルを作成し、データを格納します。 sp_cursorprepexec には、sp_cursorprepare と sp_cursorexecute の機能が組み合わされています。 このプロシージャは、ID = 5 を指定した場合に表形式のデータ ストリーム (TDS) パケットで呼び出されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_cursorprepexec prepared handle OUTPUT, cursor OUTPUT, params , statement , options  
    [ , scrollopt [ , ccopt [ , rowcount ] ] ]  
```  
  
## <a name="arguments"></a>引数  
 *準備済みハンドル*  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]生成される準備ができている*処理*識別子。 *準備済みハンドル*は必須であり返します**int**です。  
  
 *カーソル (cursor)*  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]カーソル識別子を生成します。 *カーソル*渡す必要があります (sp_cursorfetch など) は、このカーソルに対して操作を実行するすべての後続プロシージャに必須パラメーターです。  
  
 *params*  
 パラメーター化されたステートメントを指定します。 *Params*変数の定義は、ステートメント内のパラメーター マーカーに置き換えられます。 *params*必須パラメーターですが、 **ntext**、 **nchar**、または**nvarchar**値を入力します。  
  
> [!NOTE]  
>  使用して、 **ntext**の入力として文字列ときの値*stmt*がパラメーター化と*scrollopt* PARAMETERIZED_STMT の値は ON です。  
  
 *statement*  
 カーソル結果セットを定義します。 *ステートメント*パラメーターが必要です、 **ntext**、 **nchar**または**nvarchar**値を入力します。  
  
> [!NOTE]  
>  Stmt の値を指定するためのルールは sp_cursoropen 例外の場合と同じを*stmt*文字列データ型である必要があります**ntext**です。  
  
 *オプション*  
 カーソル結果セット列の説明を返す省略可能なパラメーターです。 *オプション*、従う必要があります**int**値を入力します。  
  
|値|Description|  
|-----------|-----------------|  
|0x0001|RETURN_METADATA|  
  
 *scrollopt*  
 スクロール オプションです。 *scrollopt*を次のいずれかを必要とする省略可能なパラメーターは、 **int**値を入力します。  
  
|値|Description|  
|-----------|-----------------|  
|0x0001|KEYSET|  
|0x0002|DYNAMIC|  
|0x0004|FORWARD_ONLY|  
|0x0008|STATIC|  
|0x10|FAST_FORWARD|  
|0x1000|PARAMETERIZED_STMT|  
|0x2000|AUTO_FETCH|  
|0x4000|AUTO_CLOSE|  
|0x8000|CHECK_ACCEPTED_TYPES|  
|0x10000|KEYSET_ACCEPTABLE|  
|0x20000|DYNAMIC_ACCEPTABLE|  
|0x40000|FORWARD_ONLY_ACCEPTABLE|  
|0x80000|STATIC_ACCEPTABLE|  
|0x100000|FAST_FORWARD_ACCEPTABLE|  
  
 要求されたオプションがによって定義されたカーソルの不適切である可能性があるのため *\<stmt >*、このパラメーターは両方として機能の入力し、出力します。 このような場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって適切な型が割り当てられ、この値が変更されます。  
  
 *ccopt*  
 同時実行制御オプションです。 *ccopt*を次のいずれかを必要とする省略可能なパラメーターは、 **int**値を入力します。  
  
|値|Description|  
|-----------|-----------------|  
|0x0001|READ_ONLY|  
|0x0002|SCROLL_LOCKS (以前の LOCKCC)|  
|0x0004|**オプティミスティック**(以前の optcc)|  
|0x0008|OPTIMISTIC (以前の OPTCCVAL)|  
|0x2000|ALLOW_DIRECT|  
|0x4000|UPDT_IN_PLACE|  
|0x8000|CHECK_ACCEPTED_OPTS|  
|0x10000|READ_ONLY_ACCEPTABLE|  
|0x20000|SCROLL_LOCKS_ACCEPTABLE|  
|0x40000|OPTIMISTIC_ACCEPTABLE|  
|0x80000|OPTIMISITC_ACCEPTABLE|  
  
 同様に*scrollpt*、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]要求されたものと異なる値を割り当てることができます。  
  
 *行数*  
 AUTO_FETCH で使用するフェッチ バッファー行の数を指定する省略可能なパラメーターです。 既定値は 20 行です。 *rowcount*と戻り値の入力値として割り当てられている場合とは異なる動作です。  
  
|入力値|戻り値として|  
|--------------------|---------------------|  
|AUTO_FETCH が FAST_FORWARD カーソルと共に指定されている場合*rowcount*はフェッチ バッファーに格納する行の数を表します。|結果セット内の行の数を表します。 ときに、 *scrollopt* AUTO_FETCH の値を指定すると、 *rowcount*はフェッチ バッファーにフェッチされた行の数を返します。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 場合*params*ステートメントがパラメーター化されていない、NULL 値を返します。  
  
## <a name="see-also"></a>参照  
 [sp_cursoropen と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [sp_cursorexecute と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-cursorexecute-transact-sql.md)   
 [sp_cursorprepare と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-cursorprepare-transact-sql.md)   
 [sp_cursorfetch &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-cursorfetch-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
