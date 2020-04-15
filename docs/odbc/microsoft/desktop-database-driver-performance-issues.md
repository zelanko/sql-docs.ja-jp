---
title: デスクトップ データベース ドライバのパフォーマンスに関する問題 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], performance
- desktop database drivers [ODBC], performance
- Jet-based ODBC drivers [ODBC], performance
ms.assetid: 1a4c4b7e-9744-411f-9b6e-06dfdad92cf7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a819d99a995fd7b287beb66b94f1df526e05f201
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303503"
---
# <a name="desktop-database-driver-performance-issues"></a>デスクトップ データベース ドライバー パフォーマンスの問題
既存の ANSI アプリケーションとの互換性を確保するために、SQL_WCHAR、SQL_WVARCHAR、およびSQL_WLONGVARCHARデータ型は、Access 4.0 以上のデータ ソースのSQL_CHAR、SQL_VARCHAR、およびSQL_LONGVARCHARとして公開されます。 データ ソースは WIDE CHAR データ型を返しませんが、データは Wide Char 形式で Jet に送信する必要があります。 SQL_C_CHARパラメータまたは結果列が ANSI アプリケーションのSQL_CHARデータ型にバインドされている場合、変換が行われることを理解しておくことが重要です。  
  
 この変換は、SQL_C_CHAR型が LONGVARCHAR 型のパラメーターにバインドされている場合、メモリの点で特に非効率的です。 Jet 4.0 エンジンは LONGTEXT パラメータ データをストリームできないため、UNICODE 変換バッファは SQL_C_CHAR ANSI バッファの 2 倍のサイズで割り当てる必要があります。 最も効率的なメカニズムは、UNICODE 変換を実行し、型SQL_C_WCHARとしてパラメーターをバインドするアプリケーションです。 パラメーターが実行時データとしてマークされ、SQLPutData への複数の呼び出しでデータが提供される場合、長いテキストデータ バッファーが増加します。 この "Put Data" バッファの増大によるコストを回避する 1 つの方法は、SQL_DATA_AT_EXEC_LEN(x) を介してオプションの長さを指定することです。 *x* 内部 PutData バッファーのサイズを*x*バイトに初期化します。  
  
> [!NOTE]  
>  長いデータを挿入または更新する効率的な方法は **、SQLBulkOperations()** または**SQLSetPos()** を使用して、長いデータをSQL_DATA_AT_EXECに設定することで実現できます。 (この場合、EXEC_LENは無視されます。**データは、SQLPutData**を複数回呼び出すことでチャンクでストリーム配信できます。  
  
 Microsoft ODBC デスクトップ データベース ドライバを使用して Jet 3.5 データベースを使用するアプリケーションをバージョン 4.0 にアップグレードすると、パフォーマンスが低下し、ワーキング セットのサイズが増加することがあります。 これは、バージョン3の場合です。*x*データベースは、新しいバージョン 4.0 のドライバを使用して開かれ、Jet 4.0 をロードします。 Jet 4.0 がデータベースを開き、データベースが 3 であることを確認したとき。*x*バージョンでは、Jet 3.5 エンジンのロードと同等のインストール可能な ISAM ドライバを読み込みます。 パフォーマンスとサイズのペナルティを取り除くために、Jet 3.*x*データベースは Jet 4.0 形式のデータベースに圧縮する必要があります。 これにより、2 つの Jet エンジンのロードが不要になり、データへのコード パスが最小限に抑えられます。  
  
 また、Jet 4.0 エンジンはユニコード エンジンです。 すべての文字列は Unicode で格納および操作されます。 ANSI アプリケーションが Jet 3 にアクセスするとき。*x*データベースは Jet 4.0 エンジンを介して、データは ANSI から Unicode に変換され、ANSI に戻ります。 データベースがバージョン 4.0 形式に更新された場合、文字列は Unicode に変換され、1 レベルの文字列変換が削除され、1 つの Jet エンジンを通過するだけでデータへのコード パスが最小化されます。
