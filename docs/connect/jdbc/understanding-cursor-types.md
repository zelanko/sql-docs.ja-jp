---
title: カーソルの種類を理解する |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4f4d3db7-4f76-450d-ab63-141237a4f034
caps.latest.revision: 51
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: df4f0f6e43c0eb7184f8421d3ebeada44e74a3e4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="understanding-cursor-types"></a>カーソルの種類について
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  リレーショナル データベースで操作を実行する場合、行の完全なセットが操作の対象になります。 SELECT ステートメントでは、WHERE 句で指定した条件を満たすすべての行のセットが返されます。 このステートメントが返す行の完全なセットを結果セットと呼びます。 アプリケーションでは、必ずしも、結果セット全体をひとまとめに使用して作業することが効率的であるとは限りません。 そのため、このようなアプリケーションでは、一度に 1 行または少数の行のブロックを使用するためのメカニズムが必要になります。 カーソルはそのメカニズムを提供する結果セットの拡張機能です。  
  
 カーソルでは、次のように結果セットの処理が拡張されます。  
  
-   結果セット内の特定の行に位置付けることができます。  
  
-   結果セット内の現在位置から 1 行または 1 ブロックの行を取得します。  
  
-   結果内の現在位置の行に対する変更は設定データをサポートします。  
  
-   結果セット内のデータベース データに対して他のユーザーが行った変更をさまざまなレベルで表示できます。  
  
> [!NOTE]  
>  詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 、カーソルの種類が"カーソルの種類 (データベース エンジン)」を参照して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
 JDBC の仕様では、他のジョブによって行われた変更を認識する、または認識しない順方向専用およびスクロール可能なカーソルや、読み取り専用または更新可能なカーソルがサポートされています。 この機能は、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)クラスです。  
  
## <a name="remarks"></a>解説  
 JDBC ドライバーでは、次の種類のカーソルがサポートされています。  
  
|結果セット<br /><br /> (カーソル) の種類|SQL Server のカーソルの種類|特性|select<br /><br /> 方法|response<br /><br /> Buffering|Description|  
|------------------------------------|----------------------------|---------------------|-----------------------|----------------------------|-----------------|  
|TYPE_FORWARD_ONLY (CONCUR_READ_ONLY)|なし|順方向専用、読み取り専用|直接|完全|アプリケーションで結果セットに対して 1 回の (順方向の) パススルーを行う必要があります。 これは既定の動作です。TYPE_SS_DIRECT_FORWARD_ONLY カーソルと同じように動作します。 ステートメントの実行時には、サーバーからメモリに結果セット全体が読み込まれます。|  
|TYPE_FORWARD_ONLY (CONCUR_READ_ONLY)|なし|順方向専用、読み取り専用|直接|adaptive|アプリケーションで結果セットに対して 1 回の (順方向の) パススルーを行う必要があります。 TYPE_SS_DIRECT_FORWARD_ONLY カーソルと同じように動作します。 アプリケーションの要求に応じてサーバーから行が読み取られるため、クライアント側のメモリの使用が最小限に抑えられます。|  
|TYPE_FORWARD_ONLY (CONCUR_READ_ONLY)|高速順方向|順方向専用、読み取り専用|カーソル (cursor)|なし|アプリケーションでサーバー カーソルを使用して結果セットに対する 1 回の (順方向の) パススルーを行う必要があります。 TYPE_SS_SERVER_CURSOR_FORWARD_ONLY カーソルと同じように動作します。<br /><br /> 行は、フェッチ サイズで指定されたブロック単位でサーバーから取得されます。|  
|TYPE_FORWARD_ONLY (CONCUR_UPDATABLE)|動的 (順方向専用)|順方向専用、更新可能|なし|なし|アプリケーションで 1 行以上の行を更新するには、結果セットに対して 1 回の (順方向の) パススルーを行う必要があります。<br /><br /> 行は、フェッチ サイズで指定されたブロック単位でサーバーから取得されます。<br /><br /> 既定では、フェッチ サイズが固定アプリケーションを呼び出すとき、 [setFetchSize](../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md)のメソッド、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。<br /><br /> **注:** JDBC ドライバーからステートメントの実行結果を取得できるアダプティブ バッファリングの機能を提供する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]一度にはなく、アプリケーションの必要に応じて、します。 たとえば、アプリケーションからメモリに収まりきらないほどの大きなデータを取得する必要があっても、アダプティブ バッファリングが作用することで、クライアント アプリケーションがそのような値をストリームとして取得できるようになります。 ドライバーの既定の動作は"**アダプティブ**"です。 ただし、順方向専用の更新可能な結果セットに対するアダプティブ バッファリングを取得するために、アプリケーションが、明示的に呼び出す、 [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)のメソッド、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト提供することによって、**文字列**値"**アダプティブ"** です。 コード例では、次を参照してください。[大規模なデータの更新のサンプル](../../connect/jdbc/updating-large-data-sample.md)です。|  
|TYPE_SCROLL_INSENSITIVE|静的|スクロール可能、更新不可。<br /><br /> 外部の行の更新、挿入、および削除は参照できません。|なし|なし|アプリケーションでは、データベース スナップショットが必要です。 結果セットは更新できません。 CONCUR_READ_ONLY のみがサポートされます。  それ以外の同時実行タイプは、このカーソル タイプと組み合わせて使用すると例外が発生します。<br /><br /> 行は、フェッチ サイズで指定されたブロック単位でサーバーから取得されます。|  
|TYPE_SCROLL_SENSITIVE<br /><br /> (CONCUR_READ_ONLY)|Keyset|スクロール可能、読み取り専用です。 外部の行の更新を参照できます。削除はデータの欠落によって表されます。<br /><br /> 外部の行の挿入は参照できません。|なし|なし|アプリケーションは、既存の行にのみ変更されたデータを参照してください。<br /><br /> 行は、フェッチ サイズで指定されたブロック単位でサーバーから取得されます。|  
|TYPE_SCROLL_SENSITIVE<br /><br /> (CONCUR_UPDATABLE、CONCUR_SS_SCROLL_LOCKS、CONCUR_SS_OPTIMISTIC_CC、CONCUR_SS_OPTIMISTIC_CCVAL)|Keyset|スクロール可能、更新可能。<br /><br /> 外部および内部の行の更新を参照できます。削除はデータの欠落によって表されます。挿入は参照できません。|なし|なし|アプリケーションは、ResultSet オブジェクトを使用して、既存の行のデータを変更する可能性があります。 アプリケーションは、ResultSet オブジェクト以外から他のユーザーによって行われた行に対する変更を表示することもあります。<br /><br /> 行は、フェッチ サイズで指定されたブロック単位でサーバーから取得されます。|  
|TYPE_SS_DIRECT_FORWARD_ONLY|なし|順方向専用、読み取り専用|なし|full または adaptive|整数値 2003 です。 全体がバッファーされた、読み取り専用のクライアント側カーソルを使用できます。 サーバー カーソルは作成されません。<br /><br /> 同時実行の種類としては CONCUR_READ_ONLY のみがサポートされます。 その他のすべての同時実行の種類には、このカーソルの種類で使用する場合、例外が発生します。|  
|TYPE_SS_SERVER_CURSOR_FORWARD_ONLY|高速順方向|順方向専用|なし|なし|整数値 2004 です。 サーバー カーソルを使用して、すべてのデータに高速にアクセスできます。 同時実行の種類が CONCUR_UPDATABLE である場合にのみ更新できます。<br /><br /> 行は、フェッチ サイズで指定されたブロック単位でサーバーから取得されます。<br /><br /> この場合にアダプティブ バッファリングを取得するために、アプリケーションが明示的に呼び出すが、 [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)のメソッド、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクトを提供することによって、**文字列**値"**アダプティブ"** です。 コード例では、次を参照してください。[大規模なデータの更新のサンプル](../../connect/jdbc/updating-large-data-sample.md)です。|  
|TYPE_SS_SCROLL_STATIC|静的|他のユーザーによる更新は反映されません。|なし|なし|整数値 1004 です。 アプリケーションで、データベース スナップショットが必要になります。 これは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-JDBC TYPE_SCROLL_INSENSITIVE に対する固有のシノニム、同時実行設定の動作は同じです。<br /><br /> 行は、フェッチ サイズで指定されたブロック単位でサーバーから取得されます。|  
|TYPE_SS_SCROLL_KEYSET<br /><br /> (CONCUR_READ_ONLY)|Keyset|スクロール可能、読み取り専用。 外部の行の更新を参照できます。削除はデータの欠落によって表されます。<br /><br /> 外部の行の挿入は参照できません。|なし|なし|整数値 1005 です。 アプリケーションで、既存の行についてのみ、変更されたデータを調べる必要があります。 これは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-JDBC TYPE_SCROLL_SENSITIVE に対する固有のシノニム、同時実行設定の動作は同じです。<br /><br /> 行は、フェッチ サイズで指定されたブロック単位でサーバーから取得されます。|  
|TYPE_SS_SCROLL_KEYSET<br /><br /> (CONCUR_UPDATABLE、CONCUR_SS_SCROLL_LOCKS、CONCUR_SS_OPTIMISTIC_CC、CONCUR_SS_OPTIMISTIC_CCVAL)|Keyset|スクロール可能、更新可能。<br /><br /> 外部および内部の行の更新を参照できます。削除はデータの欠落によって表されます。挿入は参照できません。|なし|なし|整数値 1005 です。 アプリケーションは、既存の行について変更済みデータを参照したり、データを変更したりする必要があります。 これは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-JDBC TYPE_SCROLL_SENSITIVE に対する固有のシノニム、同時実行設定の動作は同じです。<br /><br /> 行は、フェッチ サイズで指定されたブロック単位でサーバーから取得されます。|  
|TYPE_SS_SCROLL_DYNAMIC<br /><br /> (CONCUR_READ_ONLY)|動的|スクロール可能、読み取り専用です。<br /><br /> 外部の行の更新と挿入を参照できます。削除は現在のフェッチ バッファー内の一時的なデータ欠落として表されます。|なし|なし|整数値 1006 です。 アプリケーションで、既存の行について、変更されたデータを調べる必要があります。また、カーソルの有効期間内に挿入および削除された行を調べる必要があります。<br /><br /> 行は、フェッチ サイズで指定されたブロック単位でサーバーから取得されます。|  
|TYPE_SS_SCROLL_DYNAMIC<br /><br /> (CONCUR_UPDATABLE、CONCUR_SS_SCROLL_LOCKS、CONCUR_SS_OPTIMISTIC_CC、CONCUR_SS_OPTIMISTIC_CCVAL)|動的|スクロール可能、更新可能。<br /><br /> 外部および内部の行の更新と挿入を参照できます。削除は現在のフェッチ バッファー内の一時的なデータ欠落として表されます。|なし|なし|整数値 1006 です。 アプリケーションは、既存の行のデータを変更、挿入または ResultSet オブジェクトを使用して行を削除か。 アプリケーションは、変更、挿入、および ResultSet オブジェクト以外から他のユーザーによって行われる削除を確認することもあります。<br /><br /> 行は、フェッチ サイズで指定されたブロック単位でサーバーから取得されます。|  
  
## <a name="cursor-positioning"></a>カーソルの行の指定  
 TYPE_FORWARD_ONLY、TYPE_SS_DIRECT_FORWARD_ONLY、および TYPE_SS_SERVER_CURSOR_FORWARD_ONLY カーソル機能だけをサポート、[次](../../connect/jdbc/reference/next-method-sqlserverresultset.md)メソッドを配置します。  
  
 TYPE_SS_SCROLL_DYNAMIC カーソルはサポートしていません、[絶対](../../connect/jdbc/reference/absolute-method-sqlserverresultset.md)と[getRow](../../connect/jdbc/reference/getrow-method-sqlserverresultset.md)メソッドです。 Absolute メソッドへの呼び出しの組み合わせによって近似できる、[最初](../../connect/jdbc/reference/first-method-sqlserverresultset.md)と[相対](../../connect/jdbc/reference/relative-method-sqlserverresultset.md)動的カーソルのメソッドです。  
  
 GetRow メソッドは、TYPE_FORWARD_ONLY、TYPE_SS_DIRECT_FORWARD_ONLY、TYPE_SS_SERVER_CURSOR_FORWARD_ONLY、TYPE_SS_SCROLL_KEYSET、および TYPE_SS_SCROLL_STATIC カーソルのみでサポートされています。 GetRow メソッドすべて順方向専用カーソルの種類では、これまでに読み取られた、カーソルによって行の数を返します。  
  
> [!NOTE]  
>  アプリケーションがサポートされていないなカーソルを呼び出し、または getRow メソッドへのサポートされていない呼び出しを配置すると、メッセージで例外がスローされます、「要求された操作はサポートされていませんこのカーソル タイプとします」  
  
 削除された行を参照できるのは、TYPE_SS_SCROLL_KEYSET および等価である TYPE_SCROLL_SENSITIVE カーソルの場合のみです。 列の値が、使用可能なカーソルが削除された行に配置されている場合、 [rowDeleted](../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md)メソッドが"true"を返します。 取得する呼び出し\<型 > メソッドは、メッセージで例外がスロー、「削除された行からに値を取得できません」です。 削除された行を更新することはできません。 更新プログラムを呼び出すしようとする場合\<型 > 削除された行に対してメソッドが、メッセージで例外がスローされます、「削除された行を更新できません」です。 TYPE_SS_SCROLL_DYNAMIC カーソルも、現在のフェッチ バッファーからカーソルが移動するまでは同じ動作です。  
  
 順方向カーソルと動的カーソルでは、フェッチ バッファー内でカーソルにアクセスできる間だけ、削除された行を同様の方法で参照することができます。 順方向カーソルの場合は単純です。 動的カーソルの場合は、フェッチ サイズが 1 より大きい場合に複雑になります。 アプリケーションでは、フェッチ バッファーによって定義された範囲内でカーソルを前後に移動できますが、更新が行われた元のフェッチ バッファーが移動した場合には、削除された行が参照できなくなります。 アプリケーションで、一時的に削除された行を動的カーソルを使用して参照しない場合は、FETCH RELATIVE (0) を使用する必要があります。  
  
 TYPE_SS_SCROLL_KEYSET または TYPE_SCROLL_SENSITIVE カーソル行のキー値がカーソルによって更新されると、更新された行がカーソルの選択基準を満たすかどうかにかかわらず、結果セット内でその行の元の位置が維持されます。 行がカーソルの外部で更新されると、削除された行がその行の元の位置に現れます。ただし、行がカーソル内に現れるのは、新しいキー値を持ちカーソル内にもともと存在していた別の行が、その時点で削除されている場合だけです。  
  
 動的カーソルの場合は、更新された行は、フェッチ バッファーで定義された範囲が移動するまでは、フェッチ バッファー内での位置が維持されます。 更新された行はその後結果セット内の異なる場所に再度現れるか、または完全に削除されます。 結果セット内での一時的な不整合を回避する必要のあるアプリケーションでは、フェッチ サイズを 1 にする必要があります (既定では、CONCUR_SS_SCROLL_LOCKS の同時実行の場合は 8 行、その他の同時実行の場合は 128 行です)。  
  
## <a name="cursor-conversion"></a>カーソルの変換  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 暗黙のカーソル変換 (またはカーソルの下位) と呼びますが、要求される異なる種類のカーソルの実装にもできます。 暗黙のカーソル変換の詳細についてで暗黙的なカーソル変換の使用」のトピックを参照してください。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
 [!INCLUDE[ssVersion2000](../../includes/ssversion2000_md.md)]ResultSet.TYPE_SCROLL_SENSITIVE および ResultSet.CONCUR_UPDATABLE の結果からデータを更新すると、メッセージ「カーソルは読み取り専用」に設定すると、例外がスローされます。 この例外が発生、[!INCLUDE[ssVersion2000](../../includes/ssversion2000_md.md)]その結果が設定され、要求された更新可能なカーソルを返しませんでしたに対して暗黙のカーソル変換が行わします。  
  
 この問題を回避するには次の 2 つの方法があります。  
  
-   基になるテーブルに主キーがあることを確認する。  
  
-   使用して[SQLServerResultSet.TYPE_SS_SCROLL_DYNAMIC](../../connect/jdbc/reference/type-ss-scroll-dynamic-field-sqlserverresultset.md)ステートメントの作成中に ResultSet.TYPE_SCROLL_SENSITIVE の代わりにします。  
  
## <a name="cursor-updating"></a>カーソルの更新  
 直接の更新は、カーソルの種類および同時実行で更新が可能なカーソルについてサポートされています。 更新可能な結果セット行にカーソルが配置されていない場合 (ありません get\<型 > メソッドの呼び出しが成功した)、更新プログラムへの呼び出し\<型 > メソッドは、メッセージで例外をスロー、「結果セットには現在の行がありません」です。 JDBC の仕様には、CONCUR_READ_ONLY であるカーソルの列に対して更新メソッドが呼び出されると、例外が発生すると記載されています。 行がない場合など、更新可能な更新または削除など、オプティミスティック同時実行の競合があるため、例外は発生しませんまで[insertRow](../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md)、 [updateRow](../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md)、または[deleteRow](../../connect/jdbc/reference/deleterow-method-sqlserverresultset.md)と呼びます。  
  
 更新への呼び出し後\<型 >、影響を受ける列は、get がアクセスできない\<型 > updateRow までまたは[cancelRowUpdates](../../connect/jdbc/reference/cancelrowupdates-method-sqlserverresultset.md)が呼び出されました。 これにより、サーバーによって返された型とは異なる型を使用して列が更新されるという問題と、その後の getter 呼び出しでクライアント側の型変換が生じ不正確な結果になるという問題が回避されます。 取得する呼び出し\<型 > メッセージで例外がスローされます、「更新された列は updateRow() までアクセスできませんまたは cancelRowUpdates() が呼び出されました」。  
  
> [!NOTE]  
>  列が更新されなかったときに、updateRow メソッドを呼び出すと、JDBC ドライバーでは、メッセージで例外をスローします。"updateRow() がない列はときに呼び出されますが、更新済みです"  
  
 後に[moveToInsertRow](../../connect/jdbc/reference/movetoinsertrow-method-sqlserverresultset.md)されましたが呼び出されると、例外がスローされます以外の任意のメソッドを取得する場合\<型 >、更新\<型 >、insertRow、およびカーソル位置メソッド (など[moveToCurrentRow](../../connect/jdbc/reference/movetocurrentrow-method-sqlserverresultset.md)) 結果セットに対して呼び出されます。 MoveToInsertRow メソッドによって結果セットが挿入モードになりカーソルの位置指定メソッドによって挿入モードが終了します。 相対的なカーソル位置の呼び出しは、相対的な位置 moveToInsertRow が呼び出される前に、では、カーソルを移動します。 カーソルの行を指定する呼び出しの後は、その結果得られたカーソルの位置が新しいカーソル位置になります。  
  
 失敗した呼び出しが moveToInsetRow 前に、の元のカーソル位置の後のカーソル位置が、カーソルを挿入モードが見つからないときに行われた呼び出しの行を指定すると、呼び出されるとします。 InsertRow が失敗する、カーソルが挿入行に残り、カーソルがのままの場合は、モードを挿入します。  
  
 挿入行の列は、最初は初期化されていない状態です。 更新プログラムへの呼び出し\<型 > メソッドを設定、列の状態初期化します。 Get 呼び出し\<型 > 初期化されていない列に対してメソッドが例外をスローします。 InsertRow メソッドへの呼び出しは、すべての列を挿入行に初期化されていない状態を返します。  
  
 すべての列は、insertRow メソッドが呼び出されたときに初期化されていない、列の既定値が挿入されます。 既定値がなく、列が null を許容する場合は、null が挿入されます。 既定値がなく、列が null を許容しない場合は、サーバーがエラーを返し、例外がスローされます。  
  
> [!NOTE]  
>  GetRow メソッドへの呼び出しでは、挿入モードのときに 0 を返します。  
>   
>  JDBC ドライバーでは、位置を指定した更新または削除はできません。 JDBC の仕様に従って、 [setCursorName](../../connect/jdbc/reference/setcursorname-method-sqlserverstatement.md)メソッドも何も起こりませんと[getCursorName](../../connect/jdbc/reference/getcursorname-method-sqlserverresultset.md)メソッドと呼ばれる場合、例外がスローされます。  
>   
>  読み取り専用および静的カーソルは更新できません。  
>   
>  SQL Server では、サーバー カーソルの使用が 1 つの結果セットに制限されています。 バッチまたはストアド プロシージャに複数のステートメントが含まれる場合は、順方向専用かつ読み取り専用のクライアント カーソルを使用する必要があります。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーによる結果セットの管理](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)  
  
  
