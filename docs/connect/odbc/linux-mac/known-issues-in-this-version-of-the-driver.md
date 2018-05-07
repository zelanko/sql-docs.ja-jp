---
title: SQL Server に関する既知の問題、ドライバーのこのバージョンで |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- known issues
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9cd3bb6f733b9d9cac1dc3973e65199c9357bbbb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="known-issues-in-this-version-of-the-driver"></a>このバージョンのドライバーの既知の問題

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

この記事には、Microsoft ODBC Driver 13、13.1、および SQL Server の 17 で Linux および macOS に関する既知の問題の一覧が含まれています。

その他の問題は、 [Microsoft ODBC ドライバー チームのブログ](http://blogs.msdn.com/b/sqlnativeclient/)に投稿されます。  

- Windows、Linux、および macOS、異なる方法で、私用領域 (PUA) またはエンドユーザー定義文字 (EUDC) から文字を変換します。 内のサーバーで実行される変換[!INCLUDE[tsql](../../../includes/tsql_md.md)]Windows 変換ライブラリを使用します。 ドライバーでの変換は、Windows、Linux、または macOS 変換ライブラリを使用します。 各ライブラリで、これらの変換を実行するときに、異なる結果が生じる場合があります。 詳細については、「 [エンド ユーザーによって定義されており、秘密の使用領域文字](http://msdn.microsoft.com/library/dd317802.aspx)」を参照してください。

- クライアントのエンコーディングが utf-8 の場合は、ドライバー マネージャーは、常に正しく変換しません utf-8 から utf-16 へ。 現時点では、文字列内の 1 つまたは複数の文字が有効な utf-8 文字ではない場合に、データの破損が発生します。 ASCII 文字が正しくマップされます。 ドライバー マネージャーは、SQLCHAR バージョンの ODBC API (たとえば、SQLDriverConnectA) を呼び出すときに、この変換を試行します。 SQLWCHAR バージョンの ODBC API (たとえば、SQLDriverConnectW) を呼び出す際には、ドライバー マネージャーはこの変換を試行しません。  

- *ColumnSize*のパラメーター **SQLBindParameter** SQL 型の文字数を参照中に*BufferLength*は、アプリケーションのバイト数バッファーです。 ただし、SQL データ型が場合`varchar(n)`または`char(n)`、SQL_C_CHAR または SQL_C_VARCHAR、として、パラメーターをバインドし、クライアントの文字エンコーディング utf-8、いなくても、ドライバーから「文字列データの右側切り捨てられました」エラーが発生した可能性があります、値*ColumnSize*は、サーバーでのデータ型のサイズに揃えられます。 このエラーは、文字エン コードの間の変換がデータの長さを変更するために発生します。 正しいアポストロフィ文字 (U +0 2019) の例では、3 バイト シーケンス 0xe2 として utf-8 が、cp-1252 で 0x92 1 バイト、0x92 としてエンコードされて 0x80 0x99 です。

たとえば、utf-8 のエンコードは、両方に 1 を指定する*BufferLength*と*ColumnSize*で**SQLBindParameter** out パラメーター、およびしよう格納されている直前の文字を取得、`char(1)`列 (cp-1252 を使用)、サーバーで、ドライバーは 3 バイトの utf-8 エンコードに変換しようとしていますが、1 バイトのバッファーに収まらない結果。 比較、逆方向の*ColumnSize*で、 *BufferLength*で**SQLBindParameter**上、異なるコード ページ間の変換を実行する前に、クライアントとサーバーです。 *ColumnSize* 1 が *BufferLength* (たとえば) 3 より小さいので、ドライバーはエラーを生成します。 このエラーを回避するには、ことを確認、データの長さの変換は、指定されたバッファーまたは列に収まる後。 なお*ColumnSize* 8000 よりも大きくすることはできません、`varchar(n)`型です。

## <a name="see-also"></a>参照  
[プログラミング ガイドライン](../../../connect/odbc/linux-mac/programming-guidelines.md)  
[リリース ノート](../../../connect/odbc/linux-mac/release-notes.md)  

