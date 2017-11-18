---
title: "このバージョンのドライバーの既知の問題 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- known issues
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 50f9efe65f14dbd73ccbc3c6e81307c3893c469f
ms.openlocfilehash: 62fd9dd8bf2e11fe39ffaa2e893ded55b214b09c
ms.contentlocale: ja-jp
ms.lasthandoff: 11/08/2017

---
# <a name="known-issues-in-this-version-of-the-driver"></a>このバージョンのドライバーの既知の問題

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

このトピックには、Linux および macOS 上の SQL Server 用 Microsoft ODBC Driver 13 の既知の問題の一覧が含まれています。

その他の問題は、 [Microsoft ODBC ドライバー チームのブログ](http://blogs.msdn.com/b/sqlnativeclient/)に投稿されます。  

- Windows、Linux、および macOS、異なる方法で、私用領域 (PUA) またはエンドユーザー定義文字 (EUDC) から文字を変換します。 内のサーバーで実行される変換[!INCLUDE[tsql](../../../includes/tsql_md.md)]Windows 変換ライブラリを使用します。 ドライバーでの変換は、Windows、Linux、または macOS 変換ライブラリを使用します。 各ライブラリで、これらの変換を実行するときに、異なる結果が生じる場合があります。 詳細については、「 [エンド ユーザーによって定義されており、秘密の使用領域文字](http://msdn.microsoft.com/library/dd317802.aspx)」を参照してください。

- クライアントのエンコーディングが utf-8 の場合は、ドライバー マネージャーは、常に正しく変換しません utf-8 から utf-16 へ。 現時点では、1 の場合、データの破損が発生または文字列の文字が有効な utf-8 文字ではありません。 ASCII 文字は正しくマップされます。 SQLCHAR バージョンの ODBC API (たとえば、SQLDriverConnectA) を呼び出す際、ドライバー マネージャーはこの変換を試行します。 SQLWCHAR バージョンの ODBC API (たとえば、SQLDriverConnectW) を呼び出す際には、ドライバー マネージャーはこの変換を試行しません。  

- *ColumnSize*のパラメーター **SQLBindParameter** SQL 型の文字数を参照中に*BufferLength*は、アプリケーションのバイト数バッファーです。 ただし、SQL データ型が場合`varchar(n)`または`char(n)`、SQL_C_CHAR または SQL_C_VARCHAR、として、パラメーターをバインドし、クライアントの文字エンコーディング utf-8、いなくても、ドライバーから「文字列データの右側切り捨てられました」エラーが発生した可能性があります、値*ColumnSize*は、サーバーでのデータ型のサイズに揃えられます。 このエラーは、文字エン コードの間の変換がデータの長さを変更するために発生します。 正しいアポストロフィ文字 (U +0 2019) の例では、3 バイト シーケンス 0xe2 として utf-8 が、cp-1252 で 0x92 1 バイト、0x92 としてエンコードされて 0x80 0x99 です。

たとえば、utf-8 のエンコードは、両方に 1 を指定する*BufferLength*と*ColumnSize*で**SQLBindParameter** out パラメーター、およびしよう上に格納されている文字を取得、`char(1)`列 (cp-1252 を使用)、サーバーで、ドライバーは 3 バイトの utf-8 エンコードに変換しようとしていますが、1 バイトのバッファーに収まらない結果。 比較、逆方向の*ColumnSize*で、 *BufferLength*で**SQLBindParameter**上、異なるコード ページ間の変換を実行する前に、クライアントとサーバーです。 *ColumnSize* 1 が *BufferLength* (たとえば) 3 より小さいので、ドライバーはエラーを生成します。 このエラーを回避するには、ことを確認、データの長さの変換は、指定されたバッファーまたは列に収まる後。 なお*ColumnSize* 8000 よりも大きくすることはできません、`varchar(n)`型です。

## <a name="see-also"></a>参照  
[プログラミング ガイドライン](../../../connect/odbc/linux-mac/programming-guidelines.md)  
[リリース ノート](../../../connect/odbc/linux-mac/release-notes.md)  


