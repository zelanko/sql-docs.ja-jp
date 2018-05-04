---
title: sp_cursorexecute (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
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
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: d62f4fc0a950e05d461e2bfe9b7bb7aae9605fca
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spcursorexecute-transact-sql"></a>sp_cursorexecute (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  sp_cursorprepare によって作成された実行プランに基づいてカーソルを作成してデータを格納します。 、Sp_cursorprepare と組み合わせると、このプロシージャは、sp_cursoropen と同じ機能を持つが、2 つのフェーズに分割されました。 sp_cursorexecute は、ID を指定して呼び出される、表形式のデータ ストリーム (TDS) パケットで 4 を = です。  
  
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
 準備されたステートメント*処理*sp_cursorprepare から返される値。 *prepared_handle*必須パラメーターですが、 **int**値を入力します。  
  
 *カーソル (cursor)*  
 SQL Server によって生成されるカーソル識別子です。 *カーソル*sp_cursorfetch など、カーソルに対して操作を実行するすべての後続プロシージャに指定する必要がある必須パラメーターです  
  
 *scrollopt*  
 スクロール オプションです。 *scrollopt*省略可能なパラメーターが必要な**int**値を入力します。 Sp_cursorexecute*scrollopt*パラメーターは sp_cursoropen の場合と同じ値のオプションです。  
  
> [!NOTE]  
>  PARAMETERIZED_STMT 値はサポートされていません。  
  
> [!IMPORTANT]  
>  場合、 *scrollopt*値が指定されていない、既定値は KEYSET に関係なく*scrollopt* sp_cursorprepare で指定された値。  
  
 *ccopt*  
 同時実行制御のオプションです。 *ccopt*省略可能なパラメーターが必要な**int**値を入力します。 Sp_cursorexecute*ccopt*パラメーターは sp_cursoropen の場合と同じ値のオプションです。  
  
> [!IMPORTANT]  
>  場合、 *ccopt*値が指定されていない、既定値は OPTIMISTIC に関係なく*ccopt* sp_cursorprepare で指定された値。  
  
 *行数*  
 AUTO_FETCH で使用するフェッチ バッファー行の数を指定する省略可能なパラメーターです。 既定値は 20 行です。 *rowcount*と戻り値の入力値として割り当てられている場合とは異なる動作です。  
  
|入力値|戻り値として|  
|--------------------|---------------------|  
|AUTO_FETCH が FAST_FORWARD カーソルと共に指定されている場合*rowcount*はフェッチ バッファーに格納する行の数を表します。|結果セット内の行の数を表します。 ときに、 *scrollopt* AUTO_FETCH の値を指定すると、 *rowcount*はフェッチ バッファーにフェッチされた行の数を返します。|  
  
 *bound_param*  
 追加パラメーターをオプションで使用することを示します。  
  
> [!NOTE]  
>  5 番目より後のパラメーターは、入力パラメーターとしてステートメント プランに渡されます。  
  
## <a name="code-return-value"></a>コードの戻り値  
 *rowcount*次の値を返す可能性があります。  
  
|値|Description|  
|-----------|-----------------|  
|-1|行数が不明です。|  
|-n|非同期設定が有効になっています。|  
  
## <a name="remarks"></a>解説  
  
## <a name="scrollopt-and-ccopt-parameters"></a>scrollopt パラメーターと ccopt パラメーター  
 *scrollopt*と*ccopt*は、ステートメントを識別する準備済みハンドルを再コンパイルする必要があります、つまり、サーバーのキャッシュのキャッシュされたプランが割り込まれた場合に役立ちます。 *Scrollopt*と*ccopt*パラメーター値が sp_cursorprepare に対する元の要求で送信された値と一致する必要があります。  
  
> [!NOTE]  
>  PARAMETERIZED_STMT を割り当てないでください*scrollopt*です。  
  
 一致する値を指定しないと、プランが再コンパイルされて、準備して実行する操作が無効になります。  
  
## <a name="rpc-and-tds-considerations"></a>RPC と TDS に関する考慮事項  
 RPC の RETURN_METADATA 入力フラグを 1 に設定すると、カーソル選択リストのメタデータを TDS ストリームで返すように要求できます。  
  
## <a name="see-also"></a>参照  
 [sp_cursoropen &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [sp_cursorfetch &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorfetch-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
