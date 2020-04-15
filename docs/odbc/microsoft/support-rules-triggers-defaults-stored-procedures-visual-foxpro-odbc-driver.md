---
title: ルール、トリガ、既定値、およびストアド プロシージャのサポート |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301139"
---
# <a name="support-for-rules-triggers-default-values-and-stored-procedures-visual-foxpro-odbc-driver"></a>ルール、トリガー、既定値、およびストアド プロシージャのサポート (Visual FoxPro ODBC ドライバー)
ビジュアル フォックス プロの規則、トリガー、既定値、またはストアド プロシージャを作成するには、Visual FoxPro ODBC ドライバーを使用します。 ただし、アプリケーションは、データベースに格納されている Visual FoxPro データを挿入、更新、または削除するときに、既存のルール、トリガー、既定値、またはストアド プロシージャと対話する場合があります。  
  
 次の表は、コマンドまたは関数がルール、トリガー、既定値、またはストアド プロシージャに存在する場合に Visual FoxPro ODBC ドライバーでサポートされる Visual FoxPro コマンドと関数を一覧表示します。  
  
 アプリケーションが、ルール、トリガー、デフォルト値、またはストアド プロシージャが他の Visual FoxPro コマンドまたは関数を呼び出すデータとやり取りすると、ドライバーはエラーを生成します。 ドライバーでサポートされていないコマンドと関数の一覧については、サポートされていない[Visual FoxPro のコマンドと](../../odbc/microsoft/unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver.md)関数を参照してください。  
  
> [!TIP]  
>  条件付きコードを、ドライバーによって呼び出されたときに実行するコマンドを決定するルール、トリガー、またはストアド プロシージャに挿入する場合は **、VERSION( )** 関数を使用できます。 **VERSION( )** 関数は、ドライバーによって呼び出されたときに "Visual FoxPro ODBC ドライバー*\<のバージョン>"* を返します。  
  
## <a name="visual-foxpro-commands-and-functions-supported-in-rules-triggers-default-values-and-stored-procedures"></a>ルール、トリガー、既定値、およびストアド プロシージャでサポートされている Visual FoxPro コマンドと関数  
  
||||  
|-|-|-|  
|$ 演算子|% 演算子|&コマンド|  
|&& コマンド|*コマンド|= コマンド|  
  
## <a name="a"></a>A  
  
||||  
|-|-|-|  
|ABS( ) 機能|ACOPY( ) 機能|テーブル追加コマンド|  
|アデータベース( ) 関数|ADBOBJECTS( ) 関数|アエラー( ) 関数|  
|アデル( ) 関数|要素( ) 関数|アレン( ) 関数|  
|アフィールズ( ) 関数|AINS( ) 関数|ALTER TABLE - SQL コマンド|  
|エイリアス( ) 関数|オールトリム( ) 機能|配列コマンドから追加|  
|AND 演算子|APPEND コマンド|メモコマンドを追加|  
|コマンドから追加|一般コマンドの追加|アスキャン( ) 関数|  
|プロシージャの追加 コマンド|ASC( ) 機能|サブスクリプト( ) 関数|  
|アシン( ) 関数|アソート( ) 関数|アタン( ) 関数|  
|AT( ) 関数|AT_C( ) 関数|ATCLINE( ) 関数|  
|ATC( ) 関数|ATCC( ) 機能|AUSED( ) 関数|  
|ATLINE( ) 関数|ATN2( ) 関数||  
|平均コマンド|ACOS( ) 関数||  
  
## <a name="b"></a>B  
  
||||  
|-|-|-|  
|トランザクション開始コマンド|間( ) 関数|ビットNOT( ) 関数|  
|ビットクリア( ) 関数|ビットシフト( ) 関数|ビットセット( ) 関数|  
|ビット関数( ) 関数|ビットシフト( ) 関数|ブランクコマンド|  
|ビットテスト( ) 関数|ビットクソル( ) 関数||  
|BOF( ) 関数|ビットアンド()関数||  
  
## <a name="c"></a>C  
  
||||  
|-|-|-|  
|コマンドの計算|候補( ) 関数|CHR( ) 関数|  
|CDX( ) 関数|天井( ) 機能|CLOSE コマンド|  
|クロトラン( ) 関数|クロトラン( ) 機能|インデックスのコピー コマンド|  
|CMONTH( ) 関数|続行コマンド|コピー構造拡張コマンド|  
|手順のコピー コマンド|コピー構造コマンド|コマンドにコピー|  
|タグのコピー コマンド|配列へのコピーコマンド|CPCONVERT( ) 関数|  
|COS( ) 関数|カウント コマンド|CTOD( ) 関数|  
|CPカレント( ) 関数|CPDBF( ) 機能|カーソルセットプロップ( ) 関数|  
|CTOT( ) 関数|カーソルゲプロップ( ) 関数||  
|カーバル( ) 関数|CDOW( ) 関数||  
  
## <a name="d"></a>D  
  
||||  
|-|-|-|  
|日付( ) 関数|日時( ) 関数|デイ( ) 関数|  
|DBC( ) 関数|DBF( ) 関数|関数|  
|DBUSED( ) 関数|DELETE - SQL コマンド|コマンドの削除|  
|DELETE TAG コマンド|削除 ( ) 関数|降順( ) 関数|  
|違い( ) 関数|分析コード コマンド|ディスクスペース( ) 機能|  
|DMY( ) 関数|ケースを行います.エンドケース コマンド|DO コマンド|  
|しばらく行う..エンドド コマンド|ダウ( ) 関数|DTOC( ) 関数|  
|DTOR( ) 関数|DTOS( ) 関数|DTOT( ) 関数|  
  
## <a name="e"></a>E  
  
||||  
|-|-|-|  
|EMPTY( ) 関数|評価( ) 関数|終了コマンド|  
|エラー( ) 関数|EXP( ) 機能||  
|トランザクション終了コマンド|EOF( ) 関数||  
  
## <a name="f"></a>F  
  
||||  
|-|-|-|  
|FCOUNT( ) 関数|FDATE( ) 関数|フィールド( ) 関数|  
|ファイル( ) 関数|フィルタ( ) 機能|FLDLIST( ) 関数|  
|フロック( ) 機能|フロア( ) 機能|フラッシュコマンド|  
|のために..コマンドの終了|FOR( ) 関数|FOUND( ) 関数|  
|無料テーブルコマンド|FSIZE( ) 関数|FTIME( ) 関数|  
|フルパス( ) 関数|ファンクションコマンド|FV( ) 機能|  
  
## <a name="g"></a>G  
  
||||  
|-|-|-|  
|ギャザーコマンド|関数を変更します。|GO/GOTO コマンド|  
|関数を取得する|ゴーマンス( ) 関数||  
|GETCP( ) 関数|GETENV( ) 関数||  
  
## <a name="h"></a>H  
  
|||  
|-|-|  
|ヘッダ( ) 関数|時間( ) 関数|  
  
## <a name="i"></a>I  
  
||||  
|-|-|-|  
|IDXCOLLATE( ) 関数|もし。。。ENDIF コマンド|IIF( ) 関数|  
|INDBC( ) 関数|INDEX コマンド|インリスト( ) 関数|  
|挿入-SQL コマンド|INT( ) 関数|ISALPHA( ) 関数|  
|ISBLANK( ) 関数|ISDIGIT( ) 機能|ISEXCLUSIVE( ) 関数|  
|アイリードバイト( ) 関数|ISLOWER( ) 関数|ISNULL( ) 関数|  
|ISREADONLY( ) 関数|ISUPPER( ) 関数||  
  
## <a name="k"></a>K  
  
||||  
|-|-|-|  
|キー( ) 機能|キーマッチ( ) 関数||  
  
## <a name="l"></a>L  
  
||||  
|-|-|-|  
|左( ) 関数|左C( ) 関数|LIKEC( ) 関数|  
|LENC( ) 関数|Like( ) 関数|ロック( ) 機能|  
|ローカル コマンド|コマンドの検索|ルックアップ( ) 関数|  
|ログ( ) 関数|LOG10( ) 関数|LTRIM( ) 関数|  
|下側( ) 関数|LPARAMETERS コマンド||  
|LUPDATE( ) 関数|LEN( ) 関数||  
  
## <a name="m"></a>M  
  
||||  
|-|-|-|  
|システム メモリ変数_MLINE|MAX( ) 関数|MDX( ) 関数|  
|MDY( ) 関数|メムラインズ()関数|メッセージ( ) 関数|  
|最小関数|分( ) 関数|MLINE( ) 関数|  
|MOD( ) 関数|月( ) 関数|MTON( ) 関数|  
  
## <a name="n"></a>N  
  
||||  
|-|-|-|  
|NDX( ) 関数|正規化( ) 関数|演算子ではありません|  
|注 コマンド|NTOM( ) 関数|NVL( ) 関数|  
  
## <a name="o"></a>O  
  
||||  
|-|-|-|  
|発生する ( ) 関数|オールドヴァル( ) 関数|エラー時コマンド|  
|キーコマンド|オン( ) 機能|データベース コマンドを開く|  
|OR 演算子|ORDER( ) 関数|OS( ) 機能|  
  
## <a name="p"></a>P  
  
||||  
|-|-|-|  
|PACK コマンド|パラメータ( ) 関数|支払い( ) 機能|  
|パラメータ コマンド|プライマリー( ) 機能|プライベート コマンド|  
|PI( ) 関数|プログラム( ) 機能|適切な( ) 機能|  
|手順コマンド|PV( ) 関数||  
|パブリックコマンド|PADL( ) &#124; PADR( ) &#124; PADC( ) 関数||  
  
## <a name="r"></a>R  
  
||||  
|-|-|-|  
|ランド( ) 関数|RAT( ) 機能|RATC( ) 機能|  
|ラットライン( ) 関数|リコールコマンド|レクカウント( ) 関数|  
|レノ( ) 関数|RECサイズ( ) 関数|地域コマンド|  
|リレーション( ) 関数|テーブルの削除コマンド|置換コマンド|  
|配列コマンドから置換|レプリケート( ) 関数|再試行コマンド|  
|リターン コマンド|右( ) 関数|右関数|  
|RLOCK( ) 関数|ロールバックコマンド|ラウンド( ) 関数|  
|RTOD( ) 関数|RTRIM( ) 機能||  
  
## <a name="s"></a>S  
  
||||  
|-|-|-|  
|スキャン。。。ENDSCAN コマンド|スキャッタコマンド|SEC( ) 機能|  
|秒( ) 関数|シーク コマンド|シーク( ) 機能|  
|コマンドの選択|SELECT( ) 機能|SQL コマンドを選択します。|  
|SET BLOCKSIZE コマンド|キャリーコマンドの設定|センチュリーコマンドの設定|  
|SET COLLATE コマンド|データベース・コマンドの設定|日付の設定コマンド|  
|デフォルトコマンドの設定|SET DELETED コマンド|SET EXACT コマンド|  
|SET EXCLUSIVE コマンド|FDOW コマンドの設定|フィールドの設定コマンド|  
|フィルタ コマンドの設定|固定コマンドの設定|フルパスコマンドの設定|  
|FWEEK コマンドの設定|時間設定コマンド|インデックスコマンドの設定|  
|ロックコマンドの設定|マルチロックスの設定コマンド|近傍コマンドを設定|  
|NOCPTRANS コマンドの設定|通知コマンドの設定|SET NULL コマンド|  
|最適化コマンドの設定|[注文コマンドの設定]|SET PATH コマンド|  
|プロシージャコマンドの設定|[リレーションの設定]コマンド|リレーションオフの設定コマンド|  
|SET REPROCESS コマンド|スキップ コマンドの設定|UDFPARMS コマンドの設定|  
|SET UNIQUE コマンド|ボリュームコマンドの設定|セット( ) 関数|  
|セットフドルステート( ) 関数|符号 ( ) 関数|SIN( ) 関数|  
|スキップ コマンド|並べ替えコマンド|スペース( ) 関数|  
|SQRT( ) 関数|ストア コマンド|STR( ) 関数|  
|ストコンヴ( ) 機能|ストラン( ) 関数|STUFF( ) 機能|  
|スタッフ( ) 関数|サブSTR( ) 関数|サブストリック( ) 関数|  
|SUM コマンド|SYS(2011) 機能||  
  
## <a name="t"></a>T  
  
||||  
|-|-|-|  
|_TALLYシステム メモリ変数|システム メモリ変数_TRIGGERLEVEL|タグカウント( ) 関数|  
|テーブルアップデート( ) 関数|タグ( ) 関数|ターゲット( ) 機能|  
|タグノ( ) 関数|タン( ) 関数|トリム( ) 機能|  
|時間( ) 関数|トータルコマンド|関数|  
|TTOC( ) 関数|TTOD( ) 関数||  
|タイプ( ) 関数|テーブルの復帰( ) 関数||  
  
## <a name="u"></a>U  
  
||||  
|-|-|-|  
|ユニーク( ) 機能|アンロックコマンド|コマンドを使用する|  
|コマンドの更新|アッパー( ) 関数||  
|使用される( ) 関数|UPDATE - SQL コマンド||  
  
## <a name="v"></a>V  
  
||||  
|-|-|-|  
|VAL( ) 関数|バージョン( ) 関数||  
  
## <a name="w"></a>W  
  
||||  
|-|-|-|  
|週( ) 関数|||  
  
## <a name="y"></a>Y  
  
||||  
|-|-|-|  
|年( ) 関数|||  
  
## <a name="z"></a>Z  
  
||||  
|-|-|-|  
|ZAP コマンド|||
