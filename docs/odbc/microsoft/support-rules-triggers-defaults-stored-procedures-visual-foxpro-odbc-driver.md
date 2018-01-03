---
title: "ルール、トリガー、既定値、およびストアド プロシージャのサポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], stored procedures
- FoxPro ODBC driver [ODBC], commands and functions
- commands for FoxPro ODBC driver [ODBC]
- FoxPro ODBC driver [ODBC], default values
- FoxPro ODBC driver [ODBC], triggers
- stored procedures [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], rules
- FoxPro commands and functions [ODBC]
- rules [ODBC]
- Visual FoxPro ODBC driver [ODBC], default values
- FoxPro ODBC driver [ODBC], rules
- functions [ODBC], Visual FoxPro
- default values [ODBC]
- Visual FoxPro ODBC driver [ODBC], commands and functions
- Visual FoxPro ODBC driver [ODBC], triggers
- FoxPro ODBC driver [ODBC], stored procedures
- Visual FoxPro commands and functions [ODBC]
ms.assetid: e449de20-d6ca-4902-9f8e-814eb6e86650
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c2fcdf0a9a7af2f34a2a0d87495d00ddf3373d3a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="support-for-rules-triggers-default-values-and-stored-procedures-visual-foxpro-odbc-driver"></a>ルール、トリガー、既定値、およびストアド プロシージャ (Visual FoxPro ODBC Driver) のサポート
Visual FoxPro 規則、トリガー、既定値、または、Visual FoxPro ODBC ドライバーを使用してストアド プロシージャを作成することはできません。 ただし、アプリケーションは、挿入、更新、またはデータベースに格納されている Visual FoxPro データ削除と、既存のルール、トリガー、既定値、またはストアド プロシージャと対話可能性があります。  
  
 次の表には、Visual FoxPro コマンドおよびコマンドまたは関数は、ルール、トリガー、既定値、またはストアド プロシージャが存在する場合は、Visual FoxPro ODBC ドライバーでサポートされている関数が一覧表示します。  
  
 場合は、アプリケーションがの規則、トリガー、既定値は、データと対話する。 または、ストアド プロシージャは、その他の Visual FoxPro コマンドまたは関数を呼び出す、ドライバーはエラーを生成します。 参照してください[サポートされていない Visual FoxPro コマンドと関数](../../odbc/microsoft/unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver.md)コマンドと、ドライバーでサポートされていない関数の一覧についてはします。  
  
> [!TIP]  
>  使用することができます、ルール、トリガー、またはドライバーによって呼び出されたときに実行するコマンドを決定するストアド プロシージャに条件付きのコードを挿入する場合、**バージョンに関するページ ()**関数。 **バージョンに関するページ ()**関数が返される"Visual FoxPro ODBC ドライバー *\<バージョン >*"ドライバーによって呼び出されるとします。  
  
## <a name="visual-foxpro-commands-and-functions-supported-in-rules-triggers-default-values-and-stored-procedures"></a>Visual FoxPro コマンドと規則、トリガー、既定値、およびストアド プロシージャでサポートされる関数  
  
||||  
|-|-|-|  
|$ 演算子|% 演算子|(& A) コマンド|  
|& & コマンド|* コマンド|= コマンド|  
  
## <a name="a"></a>A  
  
||||  
|-|-|-|  
|ABS () 関数|ACOPY () 関数|TABLE コマンドを追加します。|  
|ADATABASES に関するページ () 関数|ADBOBJECTS に関するページ () 関数|待ち () 関数|  
|ADEL () 関数|AELEMENT に関するページ () 関数|ALEN に関するページ () 関数|  
|AFIELDS に関するページ () 関数|AINS に関するページ () 関数|ALTER TABLE の SQL コマンド|  
|エイリアス () 関数|ALLTRIM に関するページ () 関数|配列のコマンドを追加します。|  
|AND 演算子|コマンドを追加します。|メモのコマンドを追加します。|  
|コマンドを追加します。|[全般] コマンドを追加します。|ASCAN に関するページ () 関数|  
|プロシージャのコマンドを追加します。|ASC () 関数|ASUBSCRIPT に関するページ () 関数|  
|ASIN () 関数|ASORT に関するページ () 関数|ATAN () 関数|  
|() 関数で|AT_C に関するページ () 関数|ATCLINE に関するページ () 関数|  
|ATC () 関数|ATCC に関するページ () 関数|AUSED に関するページ () 関数|  
|ATLINE に関するページ () 関数|ATN2 () 関数||  
|平均コマンド|ACOS () 関数||  
  
## <a name="b"></a>B  
  
||||  
|-|-|-|  
|トランザクション コマンドを開始します。|() 関数の間|BITNOT に関するページ () 関数|  
|BITCLEAR に関するページ () 関数|BITLSHIFT に関するページ () 関数|BITSET () 関数|  
|BITOR () 関数|BITRSHIFT に関するページ () 関数|空白のコマンド|  
|BITTEST に関するページ () 関数|BITXOR に関するページ () 関数||  
|BOF () 関数|BITAND () 関数||  
  
## <a name="c"></a>c  
  
||||  
|-|-|-|  
|コマンドを計算します。|候補 () 関数|CHR () 関数|  
|CDX () 関数|CEILING () 関数|閉じるコマンド|  
|CHRTRAN に関するページ () 関数|CHRTRANC に関するページ () 関数|インデックス [コピー] コマンド|  
|CMONTH に関するページ () 関数|コマンドを続行します。|構造体の拡張のコマンドをコピーします。|  
|プロシージャのコマンドをコピーします。|構造体 [コピー] コマンド|コマンドにコピーします。|  
|タグ コマンドをコピーします。|コマンドの配列にコピーします。|CPCONVERT に関するページ () 関数|  
|COS に関するページ () 関数|カウント コマンド|CTOD に関するページ () 関数|  
|CPCURRENT に関するページ () 関数|CPDBF に関するページ () 関数|CURSORSETPROP に関するページ () 関数|  
|CTOT に関するページ () 関数|CURSORGETPROP に関するページ () 関数||  
|CURVAL () 関数|CDOW に関するページ () 関数||  
  
## <a name="d"></a>D  
  
||||  
|-|-|-|  
|日付 () 関数|DATETIME () 関数|DAY () 関数|  
|DBC () 関数|DBF () 関数|DBGETPROP に関するページ () 関数|  
|DBUSED に関するページ () 関数|SQL コマンドを削除します。|DELETE コマンド|  
|タグ コマンドを削除します。|削除 () 関数|降順のに関するページ () 関数|  
|違いに関するページ () 関数|ディメンション コマンド|ディスク容量に関するページ () 関数|  
|DMY () 関数|ケースを実行してください...ENDCASE コマンド|コマンド操作を行います|  
|実行中にしてください...ENDDO コマンド|確定 () 関数|DTOC に関するページ () 関数|  
|DTOR () 関数|Dtos の使用に関するページ () 関数|DTOT に関するページ () 関数|  
  
## <a name="e"></a>E  
  
||||  
|-|-|-|  
|空の () 関数|() 関数を評価します。|EXIT コマンド|  
|エラーに関するページ () 関数|EXP () 関数||  
|トランザクション コマンドの終了|EOF () 関数||  
  
## <a name="f"></a>F  
  
||||  
|-|-|-|  
|FCOUNT に関するページ () 関数|FDATE に関するページ () 関数|フィールドに関するページ () 関数|  
|ファイル () 関数|フィルターに関するページ () 関数|FLDLIST に関するページ () 関数|  
|FLOCK に関するページ () 関数|FLOOR () 関数|FLUSH コマンド|  
|FOR...ENDFOR コマンド|() 関数|() 関数が見つかりました|  
|空き TABLE コマンド|FSIZE () 関数|FTIME に関するページ () 関数|  
|FULLPATH () 関数|関数のコマンド|将来のに関するページ () 関数|  
  
## <a name="g"></a>G  
  
||||  
|-|-|-|  
|コマンドを収集します。|GETNEXTMODIFIED に関するページ () 関数|移動/GOTO コマンド|  
|GETFLDSTATE に関するページ () 関数|GOMONTH に関するページ () 関数||  
|GETCP に関するページ () 関数|GETENV に関するページ () 関数||  
  
## <a name="h"></a>H  
  
|||  
|-|-|  
|ヘッダー () 関数|HOUR () 関数|  
  
## <a name="i"></a>I  
  
||||  
|-|-|-|  
|IDXCOLLATE に関するページ () 関数|もし...ENDIF コマンド|IIF () 関数|  
|INDBC に関するページ () 関数|INDEX コマンド|引数が極端に () 関数|  
|挿入 SQL コマンド|INT () 関数|ISALPHA () 関数|  
|ISBLANK () 関数|ISDIGIT () 関数|ISEXCLUSIVE に関するページ () 関数|  
|ISLEADBYTE () 関数|ISLOWER () 関数|ISNULL () 関数|  
|ISREADONLY () 関数|ISUPPER () 関数||  
  
## <a name="k"></a>K  
  
||||  
|-|-|-|  
|キー () 関数|KEYMATCH に関するページ () 関数||  
  
## <a name="l"></a>L  
  
||||  
|-|-|-|  
|左 () 関数|LEFTC に関するページ () 関数|LIKEC に関するページ () 関数|  
|LENC に関するページ () 関数|() 関数のように|ロック () 関数|  
|ローカル コマンド|コマンドを見つける|参照 () 関数|  
|LOG () 関数|LOG10 () 関数|LTRIM () 関数|  
|LOWER () 関数|LPARAMETERS コマンド||  
|LUPDATE に関するページ () 関数|LEN () 関数||  
  
## <a name="m"></a>M  
  
||||  
|-|-|-|  
|システム メモリの変数を _MLINE|MAX () 関数|MDX のに関するページ () 関数|  
|MDY () 関数|MEMLINES に関するページ () 関数|メッセージ () 関数|  
|MIN () 関数|分 () 関数|MLINE に関するページ () 関数|  
|MOD () 関数|月 () 関数|MTON に関するページ () 関数|  
  
## <a name="n"></a>×  
  
||||  
|-|-|-|  
|NDX に関するページ () 関数|() 関数を正規化します。|NOT 演算子|  
|注コマンド|NTOM に関するページ () 関数|NVL に関するページ () 関数|  
  
## <a name="o"></a>O  
  
||||  
|-|-|-|  
|発生 () 関数|ない () 関数|エラー コマンド|  
|キー コマンド|() 関数|データベースを開くコマンド|  
|OR 演算子|順序 () 関数|OS () 関数|  
  
## <a name="p"></a>P  
  
||||  
|-|-|-|  
|パック コマンド|パラメーター () 関数|支払い () 関数|  
|パラメーターのコマンド|プライマリに関するページ () 関数|プライベート コマンド|  
|PI () 関数|プログラムに関するページ () 関数|適切な () 関数|  
|PROCEDURE コマンド|PV に関するページ () 関数||  
|パブリック コマンド|PADL に関するページ () &#124;です。PADR に関するページ () &#124;です。PADC に関するページ () 関数||  
  
## <a name="r"></a>R  
  
||||  
|-|-|-|  
|RAND () 関数|RAT () 関数|RATC に関するページ () 関数|  
|RATLINE に関するページ () 関数|コマンドに注意してください。|RECCOUNT に関するページ () 関数|  
|RECNO () 関数|RECSIZE に関するページ () 関数|地域コマンド|  
|関係 () 関数|TABLE コマンドを削除します。|REPLACE コマンド|  
|配列のコマンドから置換します。|REPLICATE () 関数|コマンドを再試行してください。|  
|コマンドを返す|右 () 関数|RIGHTC に関するページ () 関数|  
|ロック () 関数|ロールバック コマンド|ROUND () 関数|  
|RTOD に関するページ () 関数|RTRIM () 関数||  
  
## <a name="s"></a>S  
  
||||  
|-|-|-|  
|スキャンしています...ENDSCAN コマンド|コマンドを散布図します。|秒 () 関数|  
|秒 () 関数|コマンドをシークします。|SEEK () 関数|  
|コマンドを選択します。|選択 () 関数|SQL コマンド|  
|SET BLOCKSIZE コマンド|SET CARRY コマンド|2 桁の年の SET コマンド|  
|SET COLLATE コマンド|データベースの SET コマンド|日付の SET コマンド|  
|セットの既定のコマンド|SET DELETED コマンド|セットの正確なコマンド|  
|排他の SET コマンド|SET FDOW コマンド|フィールドの SET コマンド|  
|フィルターの SET コマンド|固定の SET コマンド|SET FULLPATH コマンド|  
|SET FWEEK コマンド|コマンドの時間の設定|インデックスの SET コマンド|  
|SET LOCK コマンド|SET MULTILOCKS コマンド|コマンドの近くに設定します|  
|SET NOCPTRANS コマンド|通知の SET コマンド|SET NULL コマンド|  
|SET の最適化コマンド|セットの順序コマンド|SET PATH コマンド|  
|SET プロシージャ コマンド|SET 関係コマンド|関係の設定 コマンドをオフ|  
|再処理コマンドのセット|[スキップ] コマンドを設定します。|SET UDFPARMS コマンド|  
|セットの一意のコマンド|SET ボリューム コマンド|設定に関するページ () 関数|  
|SETFLDSTATE に関するページ () 関数|SIGN () 関数|SIN () 関数|  
|[スキップ] コマンド|SORT コマンド|容量に関するページ () 関数|  
|SQRT () 関数|ストアのコマンド|STR () 関数|  
|STRCONV () 関数|STRTRAN に関するページ () 関数|STUFF () 関数|  
|STUFFC に関するページ () 関数|SUBSTR () 関数|SUBSTRC に関するページ () 関数|  
|合計コマンド|SYS(2011) 関数||  
  
## <a name="t"></a>T  
  
||||  
|-|-|-|  
|システム メモリの変数を _TALLY|システム メモリの変数を _TRIGGERLEVEL|TAGCOUNT に関するページ () 関数|  
|TABLEUPDATE に関するページ () 関数|タグに関するページ () 関数|対象の () 関数|  
|TAGNO に関するページ () 関数|TAN () 関数|TRIM () 関数|  
|TIME () 関数|合計コマンド|TXNLEVEL に関するページ () 関数|  
|TTOC に関するページ () 関数|TTOD に関するページ () 関数||  
|型に関するページ () 関数|TABLEREVERT に関するページ () 関数||  
  
## <a name="u"></a>U  
  
||||  
|-|-|-|  
|一意の () 関数|UNLOCK コマンド|コマンドを使用します。|  
|更新コマンド|上のに関するページ () 関数||  
|() 関数を使用します。|更新プログラム - SQL コマンドします。||  
  
## <a name="v"></a>V  
  
||||  
|-|-|-|  
|VAL に関するページ () 関数|バージョン () 関数||  
  
## <a name="w"></a>W  
  
||||  
|-|-|-|  
|週 () 関数|||  
  
## <a name="y"></a>Y  
  
||||  
|-|-|-|  
|YEAR () 関数|||  
  
## <a name="z"></a>Z  
  
||||  
|-|-|-|  
|ZAP コマンド|||
