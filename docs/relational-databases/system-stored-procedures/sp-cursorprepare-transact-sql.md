---
title: sp_cursorprepare (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepare_TSQL
- sp_cursor_prepare
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursor_prepare
ms.assetid: 6207e110-f4bf-4139-b3ec-b799c9cb3ad7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3b45ac37a4b2d8b37235bcf53164d6006c4ad51e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68108422"
---
# <a name="sp_cursorprepare-transact-sql"></a>sp_cursorprepare (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  カーソル ステートメントまたはバッチをコンパイルして実行プランを作成します。カーソルは作成しません。 コンパイルされたステートメントは、sp_cursorexecute で後で使用できます。 、Sp_cursorexecute と組み合わせると、この手順では、sp_cursoropen と同じ機能しますが、2 つのフェーズに分割されます。 sp_cursorprepare は、ID を指定して呼び出される、表形式データ ストリーム (TDS) パケットで 3 を = です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_cursorprepare prepared_handle OUTPUT, params , stmt , options  
    [ , scrollopt[ , ccopt]]  
```  
  
## <a name="arguments"></a>引数  
 *prepared_handle*  
 SQL Server 生成の準備*処理*識別子を整数値を返します。  
  
> [!NOTE]  
>  *prepared_handle*その後、カーソルをオープンするために sp_cursorexecute プロシージャに渡されます。 作成されたハンドルは、ログオフするか sp_cursorunprepare プロシージャを使用して明示的に削除するまで存在します。  
  
 *params*  
 パラメーター化されたステートメントを指定します。 *Params*変数の定義は、ステートメント内のパラメーター マーカーの代わりに使用します。 *params*が必要なパラメーターです、 **ntext**、 **nchar**、または**nvarchar**値を入力します。 ステートメントがパラメーター化されていない場合は、NULL 値を入力します。  
  
> [!NOTE]  
>  使用、 **ntext** 、入力として文字列ときの値*stmt*がパラメーター化と*scrollopt* PARAMETERIZED_STMT の値は ON です。  
  
 *stmt*  
 カーソル結果セットを定義します。 *Stmt*パラメーターは必須でありの呼び出し、 **ntext**、 **nchar**または**nvarchar**値を入力します。  
  
> [!NOTE]  
>  指定するための規則、 *stmt*値は、sp_cursoropen 例外の場合と同じを*stmt*文字列データ型である必要があります**ntext**します。  
  
 *options*  
 カーソルの結果の説明を返すオプションのパラメーターは、列を設定します。 *オプション*、従う必要があります**int**値を入力します。  
  
|[値]|説明|  
|-----------|-----------------|  
|0x0001|RETURN_METADATA|  
  
 *scrollopt*  
 スクロール オプションです。 *scrollopt* 、省略可能なパラメーターが、次のいずれかを必要な**int**値を入力します。  
  
|[値]|説明|  
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
|これに対して、0x80000|STATIC_ACCEPTABLE|  
|0x100000|FAST_FORWARD_ACCEPTABLE|  
  
 要求された値がによって定義されたカーソルに適していない可能性があるため*stmt*、このパラメーターは両方として機能入力し、出力します。 このような場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって適切な値が割り当てられます。  
  
 *ccopt*  
 同時実行制御オプションです。 *ccopt* 、省略可能なパラメーターが、次のいずれかを必要な**int**値を入力します。  
  
|値|説明|  
|-----------|-----------------|  
|0x0001|READ_ONLY|  
|0x0002|SCROLL_LOCKS (以前の LOCKCC)|  
|0x0004|**オプティミスティック**(以前の OPTCC)|  
|0x0008|OPTIMISTIC (以前の OPTCCVAL)|  
|0x2000|ALLOW_DIRECT|  
|0x4000|UPDT_IN_PLACE|  
|0x8000|CHECK_ACCEPTED_OPTS|  
|0x10000|READ_ONLY_ACCEPTABLE|  
|0x20000|SCROLL_LOCKS_ACCEPTABLE|  
|0x40000|OPTIMISTIC_ACCEPTABLE|  
|これに対して、0x80000|OPTIMISITC_ACCEPTABLE|  
  
 同様*scrollpt*、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]要求されたものとは別の値を割り当てることができます。  
  
## <a name="remarks"></a>コメント  
 RPC 状態パラメーターは、次のいずれか。  
  
|[値]|説明|  
|-----------|-----------------|  
|0|成功|  
|0x0001|失敗|  
|1FF6|メタデータを返しませんでした。<br /><br /> 注:この理由は、ステートメントが結果セットを生成できません。たとえば、INSERT または DDL ステートメントを勧めします。|  
  
## <a name="examples"></a>使用例  
 ときに*stmt*がパラメーター化と*scrollopt* PARAMETERIZED_STMT の値が ON に、文字列の形式は次のようには。  
  
 { *\<ローカル変数名 > **\<データ型 >* } [,...*n* ]  
  
## <a name="see-also"></a>関連項目  
 [sp_cursorexecute &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorexecute-transact-sql.md)   
 [sp_cursoropen &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [sp_cursorunprepare &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorunprepare-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
