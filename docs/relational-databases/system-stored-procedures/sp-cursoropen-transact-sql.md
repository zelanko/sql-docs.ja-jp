---
title: "sp_cursoropen (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_cursoropen
- sp_cursoropen_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_cursoropen
ms.assetid: 16462ede-4393-4293-a598-ca88c48ca70b
caps.latest.revision: "10"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3752ac2db3a8687fd44fc43c2e29f24526db7ca1
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="spcursoropen-transact-sql"></a>sp_cursoropen (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  カーソルを開きます。 sp_cursoropen は、カーソルやカーソル オプションに関連付けられている SQL ステートメントを定義し、カーソルを設定します。 sp_cursoropen の組み合わせに相当する、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントの DECLARE_CURSOR と OPEN です。 このプロシージャは、ID = 2 を指定した場合に表形式のデータ ストリーム (TDS) パケットで呼び出されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_cursoropen cursor OUTPUT, stmt  
    [, scrollopt[ OUTPUT ] [ , ccopt[ OUTPUT ]  
    [ ,rowcount OUTPUT [ ,boundparam][,...n]]] ]]  
```  
  
## <a name="arguments"></a>引数  
 *カーソル (cursor)*  
 SQL Server で生成されたカーソル識別子。 *カーソル*は、*処理*値 sp_cursorfetch など、カーソルを使用するすべての後続プロシージャに渡す必要があります。 *カーソル*必須のパラメーターには、 **int**値を返します。  
  
 *カーソル*により、複数のカーソルを 1 つのデータベースの接続上でアクティブにします。  
  
 *stmt*  
 カーソル結果セットを定義する必須パラメーターです。 有効なクエリ文字列 (構文およびバインド) 任意の文字列型 (unicode、サイズなど) が有効なとして使用できる*stmt*値の型。  
  
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
  
 要求された値がによって定義されたカーソルの不適切である可能性があるのため*stmt*、このパラメーターは両方として機能の入力し、出力します。 このような場合は、SQL Server によって適切な値が割り当てられます。  
  
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
  
 同様に*scrollopt*、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、要求されたをオーバーライドできます*ccopt*値。  
  
 *行数*  
 AUTO_FETCH で使用するフェッチ バッファー行の数です。 既定値は 20 行です。 *rowcount*と戻り値の入力値として割り当てられている場合とは異なる動作です。  
  
|入力値|戻り値として|  
|--------------------|---------------------|  
|ときに、AUTO_FETCH *scrollopt*値が指定されて*rowcount*はフェッチ バッファーに格納する行の数を表します。<br /><br /> 注: > 0 には有効な値がある場合、AUTO_FETCH が指定され、それ以外の場合は無視されます。|セットを表します結果の行の数、場合を除き、 *scrollopt* AUTO_FETCH の値を指定します。|  
  
-  
  
 *boundparam*  
 追加パラメーターを使用することを示します。 *boundparam*場合に指定する必要がある省略可能なパラメーターです、 *scrollopt* PARAMETERIZED_STMT の値が ON に設定します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 エラーが発生しなかった場合、sp_cursoropen は次のいずれかの値を返します。  
  
 0  
 プロシージャは正常に実行されました。  
  
 0x0001  
 実行中にエラーが発生しました (操作がエラーにならない程度の軽度のエラー)。  
  
 0x0002  
 非同期操作を実行中です。  
  
 0x0002  
 FETCH 操作を実行中です。  
  
 A  
 によってこのカーソルが割り当て解除されて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は使用できません。  
  
 エラーが発生した場合は、一貫性のない値が返される可能性があるため、値の正確さは保証されません。  
  
 ときに、 *rowcount*パラメーターは次の結果セットが発生した戻り値として指定します。  
  
 -1  
 行数が不明または適用外の場合に返されます。  
  
 -n  
 非同期設定が有効になっている場合に返されます。 フェッチに格納された行の数を表す場合にバッファー、 *scrollopt* AUTO_FETCH の値を指定します。  
  
 RPC が使用されている場合の戻り値を次に示します。  
  
 0  
 プロシージャは成功しました。  
  
 1  
 プロシージャは失敗しました。  
  
 2  
 キーセット カーソルが非同期に生成されています。  
  
 16  
 高速順方向カーソルが自動的に閉じられました。  
  
> [!NOTE]  
>  sp_cursoropen プロシージャの実行が成功すると、RPC の戻りパラメーターと TDS の列形式の情報 (0xa0 メッセージと 0xa1 メッセージ) を含む結果セットが送信されます。 失敗した場合は、1 つ以上の TDS エラー メッセージが送信されます。 どちらの場合、行のデータは返されません、*完了*メッセージ数は 0 になります。 バージョンを使用している場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]7.0 よりも前 0xa0 と 0xa1 (SELECT ステートメントの標準) が返されます 0xa5 および 0xa4 のトークン ストリームと共にします。 使用している場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]7.0 では、0x81、0xa5 および 0xa4 のトークン ストリームと共に (SELECT ステートメントの標準) が返されます。  
  
## <a name="remarks"></a>解説  
  
## <a name="stmt-parameter"></a>stmt パラメーター  
 場合*stmt*実行を指定し、ストアド プロシージャの入力パラメーター可能性がありますかとして定義する定数の一部として、 *stmt*文字列、またはとして指定された*boundparam*引数。 これにより、宣言された変数を、バインドされたパラメーターとして渡すことができます。  
  
 許可されている内容、 *stmt*パラメーターがかどうかによって異なります、 *ccopt* ALLOW_DIRECT がまたはの残りの値はリンクされてを返す、 *ccopt*つまり、値します。  
  
-   ALLOW_DIRECT が指定されていない場合、いずれか、[!INCLUDE[tsql](../../includes/tsql-md.md)]を選択するか、EXECUTE ステートメントを単一の SELECT ステートメントを含むストアド プロシージャを使用する必要があります。 さらに、SELECT ステートメントが; カーソルとして修飾する必要があります。つまり、キーワード SELECT INTO または FOR BROWSE は使用できません。  
  
-   ALLOW_DIRECT が指定されている場合は、これにより、1 つまたは複数[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント、ものも含め、複数のステートメントで他のストアド プロシージャを実行します。 SELECT 以外のステートメントや、キーワード SELECT INTO または FOR BROWSE を含む SELECT ステートメントは、単純に実行され、カーソルは作成されません。 複数のステートメントのバッチに含まれている SELECT ステートメントについても同様です。 カーソルのみに関連する句が SELECT ステートメントに含まれている場合、それらの句は無視されます。 インスタンスのときの値*ccopt*が 0x2002 の場合、これは、要求。  
  
    -   スクロール ロックを使用するカーソル (カーソルの条件を満たしている単一の SELECT ステートメントだけがある場合)。  
  
    -   ステートメントの直接実行 (複数のステートメントがある場合、SELECT 以外の単一のステートメントがある場合、またはカーソルの条件を満たしていない SELECT ステートメントがある場合)。  
  
## <a name="scrollopt-parameter"></a>scrollopt パラメーター  
 最初の 5 つ*scrollopt*値 (KEYSEY、DYNAMIC、FORWARD_ONLY、STATIC、および FAST_FORWARD) は相互に排他的です。  
  
 PARAMETERIZED_STMT と CHECK_ACCEPTED_TYPES は、最初の 5 つの値と OR で結合できます。  
  
 AUTO_FETCH と AUTO_CLOSE は、FAST_FORWARD と OR で結合できます。  
  
 CHECK_ACCEPTED_TYPES が ON の場合、少なくとも 1 つの最後の 5 *scrollopt*値 (KEYSET_ACCEPTABLE`,` DYNAMIC_ACCEPTABLE、FORWARD_ONLY_ACCEPTABLE、STATIC_ACCEPTABLE、または FAST_FORWARD_ACCEPTABLE) にする必要があります。  
  
 STATIC カーソルは常に READ_ONLY として開かれます。 したがって、このカーソルを使用して基になるテーブルを更新することはできません。  
  
## <a name="ccopt-parameter"></a>ccopt パラメーター  
 最初の 4 つ*ccopt*値 (READ_ONLY、SCROLL_LOCKS、および両方の OPTIMISTIC 値) は相互に排他的です。  
  
> [!NOTE]  
>  最初の 4 つのいずれかを選択する*ccopt*かどうか、カーソルが読み取り専用、またはロックやオプティミスティックの方法が更新データの喪失を防ぐために使用されるかどうかに値が決まります。 場合、 *ccopt*値が指定されていない、既定値は OPTIMISTIC です。  
  
 ALLOW_DIRECT と CHECK_ACCEPTED_TYPES は、最初の 4 つの値と OR で結合できます。  
  
 UPDT_IN_PLACE は、READ_ONLY、SCROLL_LOCKS、またはいずれかの OPTIMISTIC 値と OR で結合できます。  
  
 CHECK_ACCEPTED_TYPES が ON の場合、最後の 4 つの少なくとも 1 つ*ccopt*値 (READ_ONLY_ACCEPTABLE、SCROLL_LOCKS_ACCEPTABLE、およびそのいずれかの OPTIMISTIC_ACCEPTABLE 値) は ON にもあります。  
  
 位置指定更新関数と DELETE 関数は、場合にのみ、フェッチ バッファー内でのみ実行することがあります、 *ccopt*値が SCROLL_LOCKS または OPTIMISTIC です。 指定されている値が SCROLL_LOCKS の場合は、操作が成功することが保証されます。 指定されている値が OPTIMISTIC の場合は、行が最後にフェッチされてから変更されている場合には操作が失敗します。  
  
 指定されている値が OPTIMISTIC の場合に操作が失敗することがあるのは、タイムスタンプかチェックサム値 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって決定されます) を比較することによってオプティミスティック同時実行制御機能が実行されるためです。 一致しない行があると操作が失敗します。  
  
 戻り値として UPDT_IN_PLACE を指定すると、結果を次のように制御できます。  
  
-   一意インデックスを持つテーブルで位置指定更新を実行するときに UPDT_IN_PLACE を設定しないと、その行がカーソルの作業テーブルから削除されて、カーソルによって使用されているキー列の末尾に挿入されます。その結果、それらの列が変更されます。  
  
-   UPDT_IN_PLACE を ON に設定すると、単純に作業テーブルの元の行でキー列が更新されます。  
  
## <a name="boundparam-parameter"></a>bound_param パラメーター  
 パラメーター名を指定する必要があります*paramdef*コード内のエラー メッセージに従って PARAMETERIZED_STMT が指定するとします。 PARAMETERIZED_STMT が指定されていない場合は、エラー メッセージで名前は指定されません。  
  
## <a name="rpc-considerations"></a>RPC に関する考慮事項  
 RPC の RETURN_METADATA 入力フラグを 0x0001 に設定すると、カーソル選択リストのメタデータを TDS ストリームで返すように要求できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="boundparam-parameter"></a>bound_param パラメーター  
 5 番目より後のパラメーターは、入力パラメーターとしてステートメント プランに渡されます。 それらのパラメーターのうちの最初のパラメーターは、次の形式の文字列にする必要があります。  
  
 *{データのローカル変数の名前を入力して[、... n]。*  
  
 後続のパラメーターの置き換えられる値を渡すを使用して、*ローカル変数の名前*ステートメントでします。  
  
## <a name="see-also"></a>参照  
 [sp_cursorfetch &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-cursorfetch-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
