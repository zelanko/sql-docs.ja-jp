---
title: ルール、トリガー、既定値、およびストアドプロシージャのサポートMicrosoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2fcf8e7c80b2712313cba81199489dc7cb06dce0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301139"
---
# <a name="support-for-rules-triggers-default-values-and-stored-procedures-visual-foxpro-odbc-driver"></a>ルール、トリガー、既定値、およびストアド プロシージャのサポート (Visual FoxPro ODBC ドライバー)
Visual foxpro ODBC ドライバーを使用して、Visual FoxPro の規則、トリガー、既定値、またはストアドプロシージャを作成することはできません。 ただし、アプリケーションは、データベースに格納されている Visual FoxPro データを挿入、更新、または削除するときに、既存のルール、トリガー、既定値、またはストアドプロシージャと対話する場合があります。  
  
 次の表に、コマンドまたは関数がルール、トリガー、既定値、またはストアドプロシージャに存在する場合に、Visual FoxPro ODBC ドライバーによってサポートされる Visual FoxPro のコマンドと関数を示します。  
  
 アプリケーションが、ルール、トリガー、既定値、またはストアドプロシージャが他の Visual FoxPro コマンドまたは関数を呼び出すデータと対話する場合、ドライバーはエラーを生成します。 ドライバーでサポートされていないコマンドと関数の一覧については、「サポートされていない[Visual FoxPro のコマンドと関数](../../odbc/microsoft/unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver.md)」を参照してください。  
  
> [!TIP]  
>  ルール、トリガー、またはストアドプロシージャに条件付きコードを挿入して、ドライバーによって呼び出されたときに実行するコマンドを決定する場合は、 **VERSION ()** 関数を使用できます。 **VERSION ()** 関数は、ドライバーによって呼び出された場合、"Visual FoxPro ODBC ドライバー * \<のバージョン>*" を返します。  
  
## <a name="visual-foxpro-commands-and-functions-supported-in-rules-triggers-default-values-and-stored-procedures"></a>ルール、トリガー、既定値、およびストアドプロシージャでサポートされている Visual FoxPro のコマンドと関数  
  
||||  
|-|-|-|  
|$ 演算子|% 演算子|& コマンド|  
|&& コマンド|* コマンド|= コマンド|  
  
## <a name="a"></a>A  
  
||||  
|-|-|-|  
|ABS () 関数|ACOPY) 関数|テーブルの追加コマンド|  
|ADATABASES () 関数|ADBOBJECTS () 関数|AERROR () 関数|  
|ADEL () 関数|AELEMENT () 関数|ALEN () 関数|  
|AFIELDS () 関数|すべての関数|ALTER TABLE - SQL コマンド|  
|ALIAS () 関数|ALLTRIM () 関数|配列から追加コマンド|  
|AND 演算子|コマンドの追加|メモコマンドの追加|  
|コマンドから追加|[全般コマンドの追加]|ASCAN () 関数|  
|プロシージャの追加コマンド|ASC () 関数|サブスクリプト () 関数|  
|アークサイン () 関数|ASORT () 関数|ATAN () 関数|  
|AT () 関数|AT_C () 関数|ATCLINE () 関数|  
|ATC () 関数|ATCC () 関数|AUSED () 関数|  
|ATLINE () 関数|ATN2 () 関数||  
|平均コマンド|ACOS () 関数||  
  
## <a name="b"></a>B  
  
||||  
|-|-|-|  
|BEGIN TRANSACTION コマンド|BETWEEN () 関数|BITNOT () 関数|  
|BITCLEAR () 関数|BITLSHIFT () 関数|BITSET () 関数|  
|BITOR () 関数|BITRSHIFT () 関数|BLANK コマンド|  
|BITTEST () 関数|BITXOR () 関数||  
|BOF () 関数|BITAND () 関数||  
  
## <a name="c"></a>C  
  
||||  
|-|-|-|  
|CALCULATE コマンド|候補 () 関数|CHR () 関数|  
|CDX () 関数|シーリング () 関数|コマンドを閉じる|  
|CHRTRAN () 関数|CHRTRANC () 関数|インデックスのコピーコマンド|  
|CMONTH () 関数|CONTINUE コマンド|構造のコピー拡張コマンド|  
|コピープロシージャコマンド|構造のコピーコマンド|コマンドのコピー|  
|タグのコピーコマンド|配列へのコピーコマンド|CPCONVERT () 関数|  
|COS () 関数|COUNT コマンド|CTOD () 関数|  
|CPCURRENT () 関数|CPDBF () 関数|カーソル SETPROP () 関数|  
|CTOT () 関数|カーソル GETPROP () 関数||  
|CURVAL () 関数|CDOW () 関数||  
  
## <a name="d"></a>D  
  
||||  
|-|-|-|  
|DATE () 関数|DATETIME () 関数|DAY () 関数|  
|DBC () 関数|DBF () 関数|DBGETPROP () 関数|  
|DBUSED () 関数|DELETE - SQL コマンド|DELETE コマンド|  
|DELETE TAG コマンド|DELETED () 関数|降順 () 関数|  
|相違 () 関数|DIMENSION コマンド|ディスク容量 () 関数|  
|DMY () 関数|ケース...ENDCASE コマンド|DO コマンド|  
|処理中...ENDDO コマンド|の機能|DTOC () 関数|  
|DTOR () 関数|DTO () 関数|DTOT () 関数|  
  
## <a name="e"></a>E  
  
||||  
|-|-|-|  
|EMPTY () 関数|EVALUATE () 関数|EXIT コマンド|  
|ERROR () 関数|EXP () 関数||  
|トランザクションの終了コマンド|EOF () 関数||  
  
## <a name="f"></a>F  
  
||||  
|-|-|-|  
|FCOUNT () 関数|FDATE () 関数|FIELD () 関数|  
|FILE () 関数|FILTER () 関数|FLDLIST () 関数|  
|FLOCK () 関数|FLOOR () 関数|FLUSH コマンド|  
|...ENDFOR コマンド|FOR () 関数|FOUND () 関数|  
|フリーテーブルコマンド|FSIZE () 関数|FTIME () 関数|  
|FULLPATH () 関数|FUNCTION コマンド|FV () 関数|  
  
## <a name="g"></a>G  
  
||||  
|-|-|-|  
|GATHER コマンド|GETNEXTMODIFIED () 関数|GO/GOTO コマンド|  
|GETFLDSTATE () 関数|GOMONTH () 関数||  
|GETCP () 関数|GETENV () 関数||  
  
## <a name="h"></a>H  
  
|||  
|-|-|  
|HEADER () 関数|HOUR () 関数|  
  
## <a name="i"></a>I  
  
||||  
|-|-|-|  
|IDXCOLLATE () 関数|もし。。。ENDIF コマンド|IIF () 関数|  
|INDBC () 関数|INDEX コマンド|引数 () 関数|  
|INSERT-SQL コマンド|INT () 関数|ISALPHA () 関数|  
|ISBLANK () 関数|ISDIGIT () 関数|ISEXCLUSIVE () 関数|  
|IS潜在バイト () 関数|ISLOWER () 関数|ISNULL () 関数|  
|ISREADONLY () 関数|ISUPPER () 関数||  
  
## <a name="k"></a>K  
  
||||  
|-|-|-|  
|KEY () 関数|KEYMATCH () 関数||  
  
## <a name="l"></a>L  
  
||||  
|-|-|-|  
|LEFT () 関数|LEFTC () 関数|LIKEC () 関数|  
|LENC () 関数|LIKE () 関数|LOCK () 関数|  
|ローカルコマンド|コマンドの検索|LOOKUP () 関数|  
|LOG () 関数|LOG10 () 関数|LTRIM () 関数|  
|LOWER () 関数|LPARAMETERS コマンド||  
|LUPDATE () 関数|LEN () 関数||  
  
## <a name="m"></a>M  
  
||||  
|-|-|-|  
|_MLINE システムメモリ変数|MAX () 関数|MDX () 関数|  
|MDY () 関数|MEMLINES () 関数|MESSAGE () 関数|  
|MIN () 関数|MINUTE () 関数|MLINE () 関数|  
|MOD () 関数|MONTH () 関数|MTON () 関数|  
  
## <a name="n"></a>N  
  
||||  
|-|-|-|  
|NDX () 関数|ノーマライズ () 関数|NOT 演算子|  
|メモコマンド|NTOM () 関数|NVL () 関数|  
  
## <a name="o"></a>O  
  
||||  
|-|-|-|  
|OCCURS () 関数|OLDVAL () 関数|ON ERROR コマンド|  
|キーコマンド|ON () 関数|データベースを開くコマンド|  
|OR 演算子|ORDER () 関数|OS () 関数|  
  
## <a name="p"></a>P  
  
||||  
|-|-|-|  
|パックコマンド|PARAMETERS () 関数|支払い () 関数|  
|PARAMETERS コマンド|PRIMARY () 関数|プライベートコマンド|  
|PI () 関数|PROGRAM () 関数|適切な () 関数|  
|プロシージャコマンド|PV () 関数||  
|パブリックコマンド|PADL () &#124; PADL () &#124; PADC () 関数||  
  
## <a name="r"></a>R  
  
||||  
|-|-|-|  
|RAND () 関数|RAT () 関数|RATC () 関数|  
|RATLINE () 関数|取り消しコマンド|RECCOUNT () 関数|  
|RECNO () 関数|RECSIZE () 関数|地域別コマンド|  
|RELATION () 関数|テーブルの削除コマンド|REPLACE コマンド|  
|配列から置換コマンド|REPLICATE () 関数|再試行コマンド|  
|RETURN コマンド|RIGHT () 関数|右 c () 関数|  
|RLOCK () 関数|ROLLBACK コマンド|ROUND () 関数|  
|RTOD () 関数|RTRIM () 関数||  
  
## <a name="s"></a>S  
  
||||  
|-|-|-|  
|スキャン...ENDSCAN コマンド|散布図コマンド|SEC () 関数|  
|SECONDS () 関数|SEEK コマンド|SEEK () 関数|  
|コマンドの選択|SELECT () 関数|SELECT-SQL コマンド|  
|SET BLOCKSIZE コマンド|キャリーコマンドの設定|世紀の設定コマンド|  
|SET COLLATE コマンド|データベースの設定コマンド|日付の設定コマンド|  
|既定の設定コマンド|SET DELETED コマンド|SET EXACT コマンド|  
|SET EXCLUSIVE コマンド|SET FDOW コマンド|フィールドの設定コマンド|  
|フィルターコマンドの設定|固定コマンドの設定|FULLPATH コマンドの設定|  
|SET FWEEK コマンド|時間の設定コマンド|SET INDEX コマンド|  
|LOCK コマンドの設定|MULTILOCKS コマンドの設定|NEAR コマンドの設定|  
|NOCPTRANS コマンドを設定します。|通知コマンドの設定|SET NULL コマンド|  
|OPTIMIZE コマンドの設定|ORDER コマンドの設定|SET PATH コマンド|  
|SET PROCEDURE コマンド|SET RELATION コマンド|リレーションをオフに設定コマンド|  
|SET REPROCESS コマンド|SKIP コマンドの設定|UDFPARMS コマンドの設定|  
|SET UNIQUE コマンド|ボリュームの設定コマンド|SET () 関数|  
|SETFLDSTATE () 関数|SIGN () 関数|SIN () 関数|  
|SKIP コマンド|SORT コマンド|SPACE () 関数|  
|SQRT () 関数|ストアコマンド|STR () 関数|  
|STRCONV () 関数|STRTRAN () 関数|() 関数|  
|STUFFC () 関数|SUBSTR () 関数|SUBSTRC () 関数|  
|SUM コマンド|SYS (2011) 関数||  
  
## <a name="t"></a>T  
  
||||  
|-|-|-|  
|_TALLY システムメモリ変数|_TRIGGERLEVEL システムメモリ変数|TAGCOUNT () 関数|  
|TABLEUPDATE () 関数|TAG () 関数|TARGET () 関数|  
|TAGNO () 関数|TAN () 関数|TRIM () 関数|  
|TIME () 関数|TOTAL コマンド|TXNLEVEL () 関数|  
|TTOC () 関数|TTOD () 関数||  
|TYPE () 関数|TABLEREVERT () 関数||  
  
## <a name="u"></a>U  
  
||||  
|-|-|-|  
|UNIQUE () 関数|UNLOCK コマンド|コマンドを使用する|  
|UPDATE コマンド|UPPER () 関数||  
|USED () 関数|UPDATE - SQL コマンド||  
  
## <a name="v"></a>V  
  
||||  
|-|-|-|  
|VAL () 関数|VERSION () 関数||  
  
## <a name="w"></a>W  
  
||||  
|-|-|-|  
|WEEK () 関数|||  
  
## <a name="y"></a>Y  
  
||||  
|-|-|-|  
|YEAR () 関数|||  
  
## <a name="z"></a>Z  
  
||||  
|-|-|-|  
|ZAP コマンド|||
