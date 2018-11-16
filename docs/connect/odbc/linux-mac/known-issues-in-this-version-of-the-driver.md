---
title: SQL Server に関する既知の問題では、このバージョンのドライバー |Microsoft Docs
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- known issues
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 15c0402f83dec65b6476d481b77553a037d4fa47
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2018
ms.locfileid: "51602032"
---
# <a name="known-issues-in-this-version-of-the-driver"></a>このバージョンのドライバーの既知の問題

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

この記事には、Linux と macOS で Microsoft の ODBC Driver 13、13.1、および 17 for SQL Server に関する既知の問題の一覧が含まれています。

その他の問題は、 [Microsoft ODBC ドライバー チームのブログ](https://blogs.msdn.com/b/sqlnativeclient/)に投稿されます。  

- Windows、Linux、および macOS では、私用領域 (PUA) またはエンド ユーザー定義文字 (EUDC) の文字を異なる方法で変換します。 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 内のサーバーで実行される変換では、Windows 変換ライブラリを使用します。 ドライバーの変換では、Windows、Linux、または macOS の変換ライブラリを使用します。 各ライブラリは、これらの変換を実行するときに異なる結果を生成する可能性があります。 詳細については、「[エンド ユーザーによって定義されており、秘密の使用領域文字](/windows/desktop/Intl/end-user-defined-characters)」を参照してください。

- クライアントのエンコーディングが utf-8 の場合は、ドライバー マネージャーは常に正しく変換されません utf-8 から utf-16 に。 現時点では、データの破損は、文字列内の 1 つまたは複数の文字が有効な utf-8 文字でない場合に発生します。 ASCII 文字が正しくマップされます。 SQLCHAR バージョンの ODBC API (たとえば、SQLDriverConnectA) を呼び出すときに、ドライバー マネージャーはこの変換を試行します。 SQLWCHAR バージョンの ODBC API (たとえば、SQLDriverConnectW) を呼び出す際には、ドライバー マネージャーはこの変換を試行しません。  

- *ColumnSize*パラメーターの**SQLBindParameter** SQL 型の文字数を参照中に*BufferLength*はアプリケーションのバイト数ですバッファー。 ただし、SQL データ型が `varchar(n)` または `char(n)` で、アプリケーションがパラメーターを SQL_C_CHAR または SQL_C_VARCHAR としてバインドし、クライアントの文字エン コードが UTF-8 の場合は、*ColumnSize* の値がサーバー上のデータ型のサイズに揃っていても、ドライバーから "文字列データの右側が切り捨てられました" というエラーを受け取る可能性があります。 このエラーは、文字エン コードの間の変換がデータの長さを変更するために発生します。 たとえば、正しいアポストロフィ文字を (U + 2019) 3 バイトのシーケンス 0 xe2 として utf-8 が、cp-1252 で 0x92 1 バイト、0x92 としてエンコードされて 0x80 0x99 します。

たとえば、utf-8 では、エンコードと、両方の 1 を指定すると*BufferLength*と*ColumnSize*で**SQLBindParameter** out パラメーター、およびしようとし格納されている前の文字を取得、`char(1)`列 (cp-1252 を使用して) サーバー、ドライバーは 3 バイトの utf-8 エンコードに変換しようとしていますが、1 バイトのバッファーに収まらない結果。 その他の方向を比較*ColumnSize*で、 *BufferLength*で**SQLBindParameter**に異なるコード ページ間で変換を実行する前に、クライアントとサーバーです。 *ColumnSize* 1 が *BufferLength* (たとえば) 3 より小さいので、ドライバーはエラーを生成します。 このエラーを回避するには、ことを確認、データの長さの変換は、指定したバッファー、または列に適合した後。 なお*ColumnSize* 8000 よりも大きくすることはできません、`varchar(n)`型。

## <a name="see-also"></a>参照  
[プログラミング ガイドライン](../../../connect/odbc/linux-mac/programming-guidelines.md)  
[リリース ノート](../../../connect/odbc/linux-mac/release-notes.md)  

