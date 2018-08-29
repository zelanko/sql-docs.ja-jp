---
title: sp_cursorexecute (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_cursorexecute
- sp_cursorexecute_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursor_execute
ms.assetid: 6a204229-0a53-4617-a57e-93d4afbb71ac
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 47c6f3a1c0356f00843ba086d1d7994071c24ba6
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43029873"
---
# <a name="spcursorexecute-transact-sql"></a>sp_cursorexecute (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  sp_cursorprepare によって作成された実行プランに基づいてカーソルを作成してデータを格納します。 、Sp_cursorprepare と組み合わせると、この手順では、sp_cursoropen と同じ機能しますが、2 つのフェーズに分割されます。 sp_cursorexecute は、ID を指定して呼び出される、表形式のデータ ストリーム (TDS) パケットで 4 を = です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_cursorexecute prepared_handle, cursor  
    [ , scrollopt[ OUTPUT ]  
    [ , ccopt[ OUTPUT ]  
    [ ,rowcount OUTPUT [ ,bound param][,...n]]]]]  
```  
  
## <a name="arguments"></a>引数  
 *prepared_handle*  
 準備されたステートメント*処理*sp_cursorprepare から返される値。 *prepared_handle*が必要なパラメーターです、 **int**値を入力します。  
  
 *カーソル (cursor)*  
 SQL Server によって生成されるカーソル識別子です。 *カーソル*sp_cursorfetch など、カーソルに対して操作を実行するすべての後続プロシージャに渡す必要がある必須のパラメーター  
  
 *scrollopt*  
 スクロール オプションです。 *scrollopt*省略可能なパラメーターが必要な**int**値を入力します。 Sp_cursorexecute*scrollopt*パラメーターには、sp_cursoropen と同じ値のオプション。  
  
> [!NOTE]  
>  PARAMETERIZED_STMT 値はサポートされていません。  
  
> [!IMPORTANT]  
>  場合、 *scrollopt*値が指定されていない、既定値は KEYSET に関係なく*scrollopt* sp_cursorprepare で指定された値。  
  
 *ccopt*  
 同時実行制御のオプションです。 *ccopt*省略可能なパラメーターが必要な**int**値を入力します。 Sp_cursorexecute*ccopt*パラメーターには、sp_cursoropen と同じ値のオプション。  
  
> [!IMPORTANT]  
>  場合、 *ccopt*値が指定されていない、既定値は OPTIMISTIC に関係なく*ccopt* sp_cursorprepare で指定された値。  
  
 *行数*  
 AUTO_FETCH で使用するフェッチ バッファー行の数を指定する省略可能なパラメーターです。 既定値は 20 行です。 *rowcount*と戻り値の入力値として割り当てられている場合に異なる動作です。  
  
|入力値|戻り値として|  
|--------------------|---------------------|  
|AUTO_FETCH が FAST_FORWARD カーソルと共に指定されている場合*rowcount*フェッチ バッファーに格納する行の数を表します。|結果セット内の行の数を表します。 ときに、 *scrollopt* AUTO_FETCH の値を指定すると、 *rowcount*フェッチ バッファーにフェッチされた行の数を返します。|  
  
 *bound_param*  
 追加パラメーターをオプションで使用することを示します。  
  
> [!NOTE]  
>  5 番目より後のパラメーターは、入力パラメーターとしてステートメント プランに渡されます。  
  
## <a name="code-return-value"></a>コードの戻り値  
 *rowcount*次の値を返す可能性があります。  
  
|値|説明|  
|-----------|-----------------|  
|-1|行数が不明です。|  
|-n|非同期設定が有効になっています。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="scrollopt-and-ccopt-parameters"></a>scrollopt パラメーターと ccopt パラメーター  
 *scrollopt*と*ccopt*は、ステートメントを識別する準備済みハンドルを再コンパイルする必要があります、つまり、サーバー キャッシュのキャッシュされたプランが割り込まれた場合に役立ちます。 *Scrollopt*と*ccopt*パラメーターの値が sp_cursorprepare に対する元の要求で送信された値と一致する必要があります。  
  
> [!NOTE]  
>  PARAMETERIZED_STMT を割り当てないでください*scrollopt*します。  
  
 一致する値を指定しないと、プランが再コンパイルされて、準備して実行する操作が無効になります。  
  
## <a name="rpc-and-tds-considerations"></a>RPC と TDS に関する考慮事項  
 RPC の RETURN_METADATA 入力フラグを 1 に設定すると、カーソル選択リストのメタデータを TDS ストリームで返すように要求できます。  
  
## <a name="see-also"></a>参照  
 [sp_cursoropen &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [sp_cursorfetch &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorfetch-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
