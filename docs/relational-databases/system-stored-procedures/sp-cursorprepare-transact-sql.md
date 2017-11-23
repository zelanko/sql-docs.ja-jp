---
title: "sp_cursorprepare (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepare_TSQL
- sp_cursor_prepare
dev_langs: TSQL
helpviewer_keywords: sp_cursor_prepare
ms.assetid: 6207e110-f4bf-4139-b3ec-b799c9cb3ad7
caps.latest.revision: "10"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 87d9a5eb64f10e07549a282dc77dc21d219b6584
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spcursorprepare-transact-sql"></a>sp_cursorprepare (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  カーソル ステートメントまたはバッチをコンパイルして実行プランを作成します。カーソルは作成しません。 コンパイルされたステートメントは、後で sp_cursorexecute で使用できます。 Sp_cursorexecute と組み合わせると、このプロシージャは、sp_cursoropen と同じ機能を持つが、2 つのフェーズに分割されました。 sp_cursorprepare は、ID を指定して呼び出される、表形式のデータ ストリーム (TDS) パケットで 3 を = です。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_cursorprepare prepared_handle OUTPUT, params , stmt , options  
    [ , scrollopt[ , ccopt]]  
```  
  
## <a name="arguments"></a>引数  
 *prepared_handle*  
 SQL Server によって生成される準備ができている*処理*整数値を返しますの識別子。  
  
> [!NOTE]  
>  *prepared_handle*カーソルをオープンするために sp_cursorexecute プロシージャに、後で提供されます。 作成されたハンドルは、ログオフするか sp_cursorunprepare プロシージャを使用して明示的に削除するまで存在します。  
  
 *params*  
 パラメーター化されたステートメントを指定します。 *Params*変数の定義は、ステートメント内のパラメーター マーカーに置き換えられます。 *params*必須パラメーターですが、 **ntext**、 **nchar**、または**nvarchar**値を入力します。 ステートメントがパラメーター化されていない場合は、NULL 値を入力します。  
  
> [!NOTE]  
>  使用して、 **ntext**の入力として文字列ときの値*stmt*がパラメーター化と*scrollopt* PARAMETERIZED_STMT の値は ON です。  
  
 *stmt*  
 カーソル結果セットを定義します。 *Stmt*パラメーターが必要です、 **ntext**、 **nchar**または**nvarchar**値を入力します。  
  
> [!NOTE]  
>  指定するための規則、 *stmt*値は、sp_cursoropen 例外の場合と同じを*stmt*文字列データ型である必要があります**ntext**です。  
  
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
  
 要求された値がによって定義されたカーソルに適していない可能性があるため*stmt*、このパラメーターは両方として機能の入力し、出力します。 このような場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって適切な値が割り当てられます。  
  
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
  
 同様に*scrollpt*、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]要求から別の値を割り当てることができます。  
  
## <a name="remarks"></a>解説  
 RPC 状態パラメーターは次のいずれかになります。  
  
|値|説明|  
|-----------|-----------------|  
|0|Success|  
|0x0001|失敗|  
|1FF6|メタデータを返すことができませんでした。<br /><br /> 注: この理由は、ステートメントが結果セットを生成できません。たとえば、INSERT または DDL ステートメントを勧めします。|  
  
## <a name="examples"></a>使用例  
 ときに*stmt*がパラメーター化と*scrollopt* PARAMETERIZED_STMT の値が ON には、次のように、文字列の形式。  
  
 { *\<ローカル変数の名前 >**\<データ型 >* } [,...*n* ]  
  
## <a name="see-also"></a>参照  
 [sp_cursorexecute と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-cursorexecute-transact-sql.md)   
 [sp_cursoropen と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [sp_cursorunprepare &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-cursorunprepare-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
